**This documentation is no more valid. This is only for archival
purpose.**

# Overview

The scope of this requirement is to dedup the Ads in the same page. The
Ad can repeat itself after certain gap.

# Assumption

1.  There is 1 order `o1` with 2 campaigns `c1` and `c2` with -

    1.  4 per day frequency cap.

    2.  targeted to `card-p0`, `card-pp1` (all slots) and `card-p1`

# Dedup Logic

1.  On the app launch, app makes AdRequests for `card-p0` and `card-pp1`
    -

    1.  Let's say AdEngine responds with `c1` for `card-p0`.

    2.  AdEngine will set fCap as `1 in x seconds` (irrespective of
        configured fCap).

    3.  Let's say AdEngine responds with `c1` for `card-pp1` as well.

    4.  AdEngine will set fCap as `1 in x seconds` (irrespective of
        configured fCap).

2.  On the impression of `card-p0` Ad -

    1.  AdEngine will set/increment the cookie for campaign `c1` and set
        the expiry as configured, if any (for the first time).

    2.  Do the above point, only if the campaign has some ops configured
        fCap. Else, it is unnecessary.

3.  On the further AdRequests -

    1.  If the same campaign `c1` is selected,

        1.  The frequency cap is validated in addition to the cookie
            value set during the `card-p0` impression.

        2.  The frequency cap information sent in the AdResponse will be
            = `configured_fCap - cookie_value`.

    2.  AdEngine to consider the `excludeBanners` list in order to
        determine if the same campaign `c1` has been delivered to the
        App in the recent `x` responses.

        1.  If delivered, then filter out the `c1` campaign for the
            current request.

        2.  If not delivered, then consider `c1` again and deliver with
            `configured_fCap - cookie_value` fCap info in the response.

4.  On the `fetchCampaignData` API -

    1.  Since this API responds with the configured fCap information, we
        need to tweak it in-order to consider the extra impressions
        delivered in the `card-p0` slot.

    2.  This can be done using the cookie stamped at the time of
        `card-p0` impression.

    3.  The formula is same as point `3.a.ii`.
