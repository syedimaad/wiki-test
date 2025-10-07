**Problem Statement:**

In its current implementation, MPE does not take into account flywheel
at all while pacing a campaign and deciding which delivery slab it
should be delivering at. Due to this, if a campaign is not meeting it's
requirement, it is made to deliver at low performing delivery slabs too,
which leads to the ripple effect of the campaign not meeting its
flywheel performance thresholds and eventually not delivering at all.

The core of the pacing logic being designed now is to introduce
zone-level, or rather subslot-level delivery slabs, which would be
calculated after taking into account the historical performance on that
subslot for users lying within that delivery slab.

In essence, the pacing engine would now look to cap a campaign's
delivery slab at a subslot level to ensure that delivery keeps happening
at that subslot.

**Computation of delivery slab cap:**

1.  A table will be created which will include zone, subslot,
    engagement_ratio and user_delivery_slab. Engagement ratio will be
    computed using the cumulative sum of video engagements and vast
    events (sum(has_video_engagement) / sum(has_vast)) in order of
    increasing delivery slab.

2.  Initially, for cold start case, delivery slab cap will be computed
    zone wise. After the campaign starts delivering and reaches a
    certain threshold on number of views on ad, the campaign\'s zone
    wise delivery slab cap will be taken into account by MPE.

3.  A threshold limit on the required impressions for a campaign will be
    added to max the next rung in the flywheel.

4.  Further, MPE will take minimum of delivery slab and delivery slab
    cap for delivery.

5.  The job for computing zone wise delivery slab caps will run daily,
    while the job for campaign\'s zone wise delivery slab cap will run
    every 15 minutes.

**Example table for zone - list-ad and index - 2:**

  ------------------ --------------------
  engagement_ratio   user_delivery_slab
  29                 10
  29                 9
  29                 8
  30                 7
  31                 6
  31                 0
  31                 4
  32                 5
  32                 1
  32                 3
  33                 2
  ------------------ --------------------

Ex: To deliver 4000 views, 22 CTR is to be maintained as per the
following data, hence the delivery slab cap will be 8.

**Implementation Details**

**MySQL Table - josh_campaign_zone_flywheel_metrics **

Columns - campaign_id, placement, subslot, engagement_ratio,
delivery_slab

1.  Daily job to compute delivery_slab for overall zone wise
    engagement_ratio and delivery_slab

2.  10-minutely job to compute delivery_slab for campaign wise, zone
    wise engagement_ratio and delivery_slab - These numbers will be
    computed after a campaign meets a delivery threshold of 1000
    impressions.

In both the above jobs, engagement_ratio will be computed using the
cumulative sum of has_video_engagement and has_vast using Kudu Table -
josh_nrt_ads_events_data in order of increasing user_delivery_slab.
(Zonewise / campaign wise, zone wise respectively)

**MySQL Table - dhx_campaign_zone_priority**

Columns - campaign_id, placement, subslot, priority_factor

1.  For Josh campaigns of type contract and with zone as list-ad, this
    table will be populated. - Validity check

2.  If a campaign passes the validity check, then loop on its subslots

- Delivered_impressions will be compared to the config from perf team,
  and  the engagement_Ratio corresponding to the next max rung of
  impressions will be picked. For the trending stage, the limit should
  be set at 5000.

- This engagement_ratio will be compared to the corresponding
  engagement_ratio in MySQL table josh_campaign_zone_flywheel_metrics
  and the corresponding minimum delivery_slab will be the
  delivery_slab_cap.

- Then, min of the above delivery_slab_cap and delivery_slab computed
  will be set as the priority_factor in the table
  dhx_campaign_zone_priority.

\*For zones other than list-ad, the overall delivery_slab computed using
already existing function will serve as the priority_factor. It will be
stored in the existing table dhx_campaign_priority. For list-ad, overall
number will also be stored in the same table.

**Flywheel configs:**

**MySQL Table - josh_flywheel_configs**

CREATE TABLE `josh_flywheel_configs` (\
`id` int NOT NULL AUTO_INCREMENT,\
`placement` varchar(10),\
`subslot` varchar(10),\
`flywheel_stage` varchar(10),\
`view_count` int,\
`engagement_ratio` int,\
PRIMARY KEY (`id`)\
);

**AdEngine changes:**

Ensure that every Josh campaign configured to deliver at list-ad
delivers it's first 500 impressions only at the gt2 subslot.

**Additional change suggested by Bapu for pacing:**

1.  Communicate to adengine which subslots to not deliver a campaign in.

2.  Restrict delivery slab based on restriction of required imps number.

3.  Create new flywheel campaign type - start with contract x on a deep
    index until it qualifies (500 impressions) to deliver on a shallower
    index. One campaign should still mean one creative.

4.  Condition to trigger movement from contract x to interleaved would
    be a performing creative at any of the deeper indices.

5.  Creative shouild be elegible across all indices whose CTR eligbility
    for that index is satisfied by the observed ctr for the creative.
    (Eg: CTR 50 should be eligible for all indices that require CTR
    \<=50)

6.  No prediction applicable for the sampling stage, only contract-ex
    throttling.

**Formal steps:**

1.  Create new flywheel campaign delivery_type, calling it **flywheel**.

    1.  Ensure one-to-one mapping from campaign to creative.

    2.  Remove contract and contract-ex delivery types from the UI for
        Josh.

    3.  This delivery type is only eligible for Josh.

    4.  Start with contract-x on gt2 for the first 500 impressions
        (configurable at MPE end).

    5.  Move to contract-x on all indices for next 500 impressions.

    6.  Move to contract on all indices whose engagement_ratio
        eligbility (for that index) is satisfied by the observed
        engagement_ratio **for the entire campaign (creative)**.\
        (Eg: An engagement_ratio 50 should be eligible for all indices
        that require CTR \<=50)

2.  We start flywheel checks at 500 impressions, not before that.

3.  No prediction applicable for the sampling stage, only contract-ex
    throttling (1a & 1b).

4.  Calculate zonewise delivery slabs for campaigns in contract stage
    (1c). Populate in the new **dhx_campaign_zone_priority** table.

    1.  Upto 1000 impressions, calculate only campaign level delivery
        slabs. Populate in the indices that the campaign is eligible to
        deliver in.

    2.  After 1000 impressions, calculate zonewise delivery slabs and
        populate in the indices that the campaign is eligible to deliver
        in.

5.  Adengine can always check which indices to deliver a campaign in,
    based on the above table.

6.  Populate another column in **dhx_campaign_zone_priority** table
    saying **current_mode** or not.

    1.  If **current_mode** is 1, use the corresponding delivery slab
        number to only throttle delivery, as in Josh paced contract ex.

    2.  If **current_mode** is 0, use the corresponding delivery slab
        number to ask ranking service for user eligibility and not to
        throttle.

7.  Populate another column in **dhx_campaign_zone_priority** table
    saying **is_deliverable** or not.

    1.  If **is_deliverable** is 1, deliver this campaign in this index.

    2.  If **is_deliverable** is 0, do not deliver this campaign in this
        index.

    3.  If the row doesn't exist, fall back to the
        **dhx_campaign_priority** table.

8.  Restrict delivery slab based on the restriction of required imps
    number by next flywheel rung. - MPE only.

9.  Ensure periodic clean up of the **dhx_campaign_zone_priority**
    table.

**Scope of changes with this deployment:**

1.  There is a new delivery type - Flywheel in josh.

2.  The video engagement event for such a campaign is fired after a 50%
    view is completed.

3.  This campaign delivers like a contract-x for the first 1000
    impressions (sampling stage).

4.  Post the first 1000 impressions, it delivers like a contract
    campaign (trending stage).

5.  Usually, such a campaign would be configured to deliver in all
    subslots of the list-ad placement. In such a case:

    1.  For the first 500 impressions, delivery should be restricted
        only to the gt2 subslot. (Depth \>2)

    2.  Post the first 500 impressions, delivery opens up to all the
        depths for which the campaign is valid according to the flywheel
        configurations shared by the product team (stored in the
        josh_flywheel_configs db table)

6.  If a campaign does not have the index gt2 configured for some
    reason, delivery will happen in all the subslots it is valid in,
    based on the flywheel configs. (Same as 4b above)

7.  The flywheel configs are matched against a custom computed ratio,
    the formula for which is:

**sum(ctr + likes_ratio + shares_ratio + engagement_ratio)**

*ctr = (clicks/impressions) \* 100*\
*likes_ratio = (likes/impressions) \* 100*\
*shares_ratio = (shares/impressions) \* 100*\
*engagement_ratio = (video_engagements/video_starts) \* 100*
