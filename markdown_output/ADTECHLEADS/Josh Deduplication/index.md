Table of Contents

# Objective

Users do not like to see the same ad again and again. This spec defines
the conditions when an Ad can show again.

**Additional requirement (Josh)**

In josh, we should prioritize high-performing campaigns/Ads to upper
placements with the assumption that it will be a good user experience.

**Note**: This requires Ops communication

### Performance focus of first three position

The first 3 ad positions can be separately targeted using flywheel
campaigns. The flywheel campaigns ensure that only well-performing
creatives are allowed to serve beyond the impression thresholds. If this
can be ensured as part of operational governance, the first few
positions can be brought in earlier in the feed.

Question: Does adEngine get session information?

# Current State

## Exclude Banners

The requests get a field "exclude-banners" which contains an ordered
list of previously shown/cached ads within a session. The ad response
contains a key that is included in subsequent requests in the
exclude-banners field. Currently, campaign ids are being sent and
received.

**Note**: **Currently, exclude-banners do not include empty banners**

## Frequency cap

The frequency cap can be specified as the number of Ad per given
milliseconds.

# Proposed Solution

## Exclude Banners

1.  Ads BE to maintain an array of Ads being responded to for Josh in
    respective order.

2.  At least "MIN_ADS_BEFORE_REPEAT" (We will start with 2 and modify if
    needed) Ad positions should be skipped before the "same ad" can be
    shown again. If there is no eligible ad, the ad opportunity should
    be skipped and an empty Ad will be sent.

3.  The **same Ad** can be determined based on an app-wide platform
    setting indicating the Ad should be treated the same if it has the
    same:

    1.  Advertiser

    2.  Order

    3.  Campaign OR

    4.  Banner

4.  The setting for de-dup is to be extended to the campaign level.

    1.  The ads system will store just banner ids for de-duplication at
        the client.

    2.  While serving it will de-duplicate all the campaigns based on
        their de-dup setting and the banners being stored in exclude
        banners for de-duplication.

### Frequency cap

Operationally use frequency cap to specify no more than 1 per x
millisecond. Initially, this can be a governance initiative, and the
operating experience can advise if there is a need to systematically
enforce any settings.

# Delivery pressure-based prioritization (Phase-2)

The above de-duplication approach will likely lead to delivery pressure
on the campaigns. It is best measured by the "priority factor" being
computed by the pacing engine. We can build to:

1.  **If the campaign delivery slab reaches above 5 for a campaign then
    we will relax the de-duplication slab less strict level for that
    campaign. Banner level de-duplication is the lowest.**

    1.  

2.  Prioritize contract-x campaigns by CTRs i.e Contract Exclusive
    Campaign with higher CTR will get selected first.

3.  We will be de-duping based on the time in Phase-2, which makes ad to
    be du-duped till x milliseconds, which would be a system-level
    property.

4.  Levels for Dedup

  ----------------- --------------------- --------------
  **Dedup Level**   **Priority Factor**   **Comments**
  Advertiser        less than 3           
  Order             3 to 5                
  Campaign          5 to 7                
  Banner            7 to 10               
  ----------------- --------------------- --------------

**Priority Factor**: The priority factor is a metric that captures
delivery pressure. It ranges from 0 to 10. A priority factor of 1 means
that the campaign can meet its delivery requirements by showing the Ad
to the **top 10% of the audience**. Similarly, 2 priority factors mean
the campaign can meet its delivery requirement by showing Ad to the top
20% of the audience.

# Components

## **AdEngine**

### **Exclude Ads Cookie**

AdEngine stamps a cookie named `excludeAds` in every Josh Ad Request.
This will contain the Ad Hash IDs of all the Ads responded to the user
until now, from the start of the session.

> **Example:**
>
> When dedup was done at Banner level -
>
> `123~234~345~456,123~234~345~457,123~234~345~458`
>
> When dedup was done at Campaign level -
>
> `123~234~346~456,123~234~347~457,123~234~348~458`

note

**Note!**

1.  `splash` zone Ad Request and Ads handshake should reset this cookie,
    in order to denote the new session.

2.  MAX number of entries in this cookie is hardcoded to `50` for now.

:::: {.panel .conf-macro .output-block style="background-color: rgb(234,230,255);border-color: rgb(153,141,217);border-width: 1.0px;"}
::: {.panelContent style="background-color: rgb(234,230,255);"}
**Note!**

1.  `splash` zone Ad Request and Ads handshake should reset this cookie,
    in order to denote the new session.

2.  MAX number of entries in this cookie is hardcoded to `50` for now.
:::
::::

### **Ad Hash ID**

Ad Hash ID will be the string constructed from the IDs of all the dedup
levels according to below format -

`ADVERTISER_ID~ORDER_ID~CAMPAIGN_ID~BANNER_ID`

> **Example:**
>
> Advertiser ID: 123
>
> Order ID: 234
>
> Campaign ID: 345
>
> Banner ID: 456
>
> Ad Hash ID: `123~234~345~456`

### Dedup Logic

1.  AdEngine to parse the `excludeAds` cookie from the Josh Ad Request
    and interpret the values according to the Ad Hash ID format
    mentioned in the above section.

2.  AdEngine to consider the AdEngine level config that denotes whether
    to repeat Ads at all or not. Let's call it `dedupMode=HARD/SOFT`.

    1.  If `dedupMode=HARD`, then filter out all the campaigns that are
        already delivered to the user. Ads are not repeated in this
        case.

    2.  If `dedupMode=SOFT` (DEFAULT), then filter out the Ads by
        deciding the dedup level based on their current delivery slabs.
        Ads can be repeated in this case.

3.  If `dedupMode=SOFT`, AdEngine to consider `MIN_ADS_BEFORE_REPEAT`
    number of entries from the `excludeAds` cookie for deduping.

4.  AdEngine to consider the dedup level configured in the campaign -

    1.  If a campaign level config is found, then dedup is to be applied
        based on the config.

    2.  If the campaign level config is not found, then AdEngine to look
        at the current delivery slab of the campaign and decide the
        current level of dedup to be applied, based on the dedup levels
        mapping mentioned
        [here](https://evp.atlassian.net/wiki/spaces/ADTECHLEADS/pages/132842254/Josh+Deduplication#Delivery-pressure-based-prioritization-(Phase-2)).

5.  AdEngine to log the `global_min_ads_before_repeat`,
    `campaign_min_ads_before_repeat`, `deduped_ads` and
    `current_dedup_level`, into KUDU.

6.  AdEngine to generate the Ad Hash ID based on the logic mentioned in
    the above section.

7.  AdEngine to append the current Ad Hash ID into `excludeAds` cookie
    on Ad Request API and Fallback Request API.

note

**Note!**

1.  AdEngine to consider the campaign setting for
    `MIN_ADS_BEFORE_REPEAT`, if not present then fallback to the global
    setting for `MIN_ADS_BEFORE_REPEAT`. Both are configured on
    Daedalus.

2.  AdEngine to hardcode the dedup level to delivery slab mapping in the
    constants. ([Refer
    this](https://evp.atlassian.net/wiki/spaces/ADTECHLEADS/pages/132842254/Josh+Deduplication#Delivery-pressure-based-prioritization-(Phase-2)))

3.  AdEngine to generate and stamp Ad Hash ID even for the empty
    banners.

4.  AdEngine to NOT dedup and also NOT append Ad Hash ID to the cookie
    for all TEST_MODE campaigns.

:::: {.panel .conf-macro .output-block style="background-color: rgb(234,230,255);border-color: rgb(153,141,217);border-width: 1.0px;"}
::: {.panelContent style="background-color: rgb(234,230,255);"}
**Note!**

1.  AdEngine to consider the campaign setting for
    [`MIN_ADS_BEFORE_REPEAT`]{.inline-comment-marker}, if not present
    then fallback to the global setting for
    [`MIN_ADS_BEFORE_REPEAT`]{.inline-comment-marker}. Both are
    configured on Daedalus.

2.  AdEngine to hardcode the dedup level to delivery slab mapping in the
    constants. ([Refer
    this](https://evp.atlassian.net/wiki/spaces/ADTECHLEADS/pages/132842254/Josh+Deduplication#Delivery-pressure-based-prioritization-(Phase-2)){rel="nofollow"})

3.  AdEngine to generate and stamp Ad Hash ID even for the empty
    banners.

4.  AdEngine to NOT dedup and also NOT append Ad Hash ID to the cookie
    for all TEST_MODE campaigns.
:::
::::

## **Data**

AdEngine will be passing `global_min_ads_before_repeat`,
`campaign_min_ads_before_repeat`, `deduped_ads` *(map of campaignId:
dedup_level)* and `current_dedup_level` in the request event and it will
get synced to kudu

## Ranking

Ranking service to prioritize performant contract exclusive campaign.

## Daedalus

Please review below requirement and suggest.

### Global setting for MIN_ADS_BEFORE_REPEAT

Daedalus to expose to Global config to set min distance across a
campaign which will be applicable for all campaigns running on Josh.

### Campaign level MIN_ADS_BEFORE_REPEAT

Daedalus to expose a config to be managed by Josh product only to set
min distance at the Campaign level. AdEngine to refer to this setting in
Phase-1

### Campaign level dedup level

To provide details of exposing a field for de-dupl level on Daedalus
that will be managed by Josh's Product team. The default value of the
dedup level will be advertisers. In Phase 2 we can plan to make it
dynamic. The new field to be added should be at the campaign level and
enum that it can have. Advertisers, Order, campaign, and banner to start
with and AdEngine to refer it for de-dup.

# Assumptions

1.  Since we would be ranking in Contract Exclusive, delivery might be
    impacted accordingly and needs ops communication since the objective
    of Contract Exclusive would change in this case.

2.  We would be solving the problem with the below order of
    prioritization. UX → Delivery → Performance

3.  Contract Exclusive campaign follows the delivery slab-based
    probabilistic distribution with the below nuances.

    1.  Any unpaced Exclusive will consider the avg of the delivery
        slabs at that level. (Roadblock/Linear)\
        Ex:\
        **Only Paced**\
        C1 (paced) → 5 → (5 / 12)\
        C2 (paced) → 7 → (7 / 12)

**A mix of Paced and unpaced**\
C1 (paced) → 5 → (5 / 18)\
C2 (paced) → 7 → (7 / 18)

C3 (unpaced) → (5 + 7 )/ 2 (Derived)\
Total = 18\
C3 (unpaced ) → 0 → (6 / 18) → Avg of paced / total

Only Unpaced

TBA

# Summary

We will be de-duplicating Ads within MIN_ADS_BEFORE_REPEAT for contract
and contract exclusive campaigns.
