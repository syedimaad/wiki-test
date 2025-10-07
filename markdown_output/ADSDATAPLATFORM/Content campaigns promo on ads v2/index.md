**Current status:**

1.  Articles can be promoted using ads inventory currently. The CPPV
    pacing type is built for this use case specifically. An EOD process
    determines the ratio of clicks to hive-page-views for the
    campaign/article in consideration, and the clicks goal is calibrated
    accordingly by the pacing engine.

**Requirements for v2:**

1.  The page view number is to be pulled as close to real-time as
    possible.

    1.  **Tech update -** This has been discussed with the content team.
        Hive page view numbers can be pulled on a half-hourly basis.

    2.  **Open question -** Does billing & campaign-pacing have to be on
        GA page view numbers or will the Content hive page view numbers
        suffice?

2.  Have a capability from content side to ensure we can differentiate
    bw ads delivery and organic delivery.

    1.  If that exists, measure the pace of delivery from content side
        and use it to calculate how much to deliver from ads side.

    2.  If that doesn't exist, we can still figure it out via the
        drop-offs mentioned in 4.iii.

3.  The overall delivery of the article, including organic delivery, has
    to be taken into account. For eg: If an article has been marked to
    deliver 5mn page views in Daedalus, if the total delivery
    (organic+ads) sums up to 5mn, we pause the delivery from the ads
    side. No signal to be relayed to the news BE for now about this.

4.  Same article can be placed in different campaigns - targeted on
    different placements.

    1.  **Tech update**

        1.  For this, we need to ensure that all such campaigns are
            placed within a group. And if a campaign has a banner
            delivering to PGI, it shouldn't target any other placement.

        2.  To ensure proper delivery across campaigns, the logic for
            bifurcating impressions acrosss different grouped campaigns
            will need to take into account performance too.

            1.  PGI placement - perf_factor = (drop-off from impression
                to page-view)

            2.  Other placements - perf_factor = CTR \* (drop-off from
                click to page-view)

        3.  The drop-off numbers in point (ii) above can be computed

            1.  Real time for every campaign (If we can have a
                capability to distinguish which placement led to the
                particular page-view), or

            2.  As constants (via delivery of some experimental
                campaigns described below).

**Prerequisites for v2:**

1.  Run some test campaigns to compute the following ratios:

    1.  For PGI, compute drop-off from impression to page-view. Run
        content campaigns exclusively on PGI for this.

    2.  For non-PGI placements, compute a drop-off from clicks to
        page-view. Run content campaigns on non-PGI zones for this.

**Notes for meeting:**

1.  Confirm if we can fire this query at a 5 min frequency.

2.  What is the expected lag in this pipeline?

3.  If there\'s a lag, ensure a rate is calculated to account for the
    delay.
