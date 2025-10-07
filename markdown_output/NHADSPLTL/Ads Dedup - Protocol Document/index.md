# Workflows

## Daedalus

1.  Daedalus to create a new configuration page to enable
    configurability of dedup algos for below targeting -

    1.  language

    2.  state

    3.  city

2.  Daedalus to store this config in a new MySQL table for the AdEngine
    to pickup.

## Aggressive Cacher

1.  Aggressive cacher to query the MySQL table and cache all the active
    configs.

## AdEngine

During the Ads Handshake -

1.  AdEngine to parse the request params and rename them appropriately
    for DL validation.

2.  AdEngine to consider `commonDH` cookie for location information. DO
    NOT CALL REDIS.

    1.  If the `commonDH` cookie is not present, then open targeted or
        language targeted dedup configs will be picked.

    2.  After the `commonDH` cookie is set, which ideally happens in the
        first AdRequest, the next handshake will pick the location
        targeted dedup configs as well.

3.  AdEngine to fetch all the dedup configs from the cache.

4.  AdEngine to arrive at the eligible dedup config by validating the
    dedup configs using DL validation logic.

5.  AdEngine to send the dedup algo ENUM + Handshake refresh time in
    handshake response.

6.  AdEngine will also stamp the selected dedup algo ENUM in the cookie,
    in every handshake response.

During the Ad Request -

1.  AdEngine to parse the incoming `adHashes` field from the post body
    containing information in [this
    format](https://evp.atlassian.net/wiki/spaces/NHADSPLTL/pages/131727466/Ads+Dedup+-+Protocol+Document#Ad-Request).

2.  AdEngine to also parse the `dedup` cookie set during the Ads
    handshake.

3.  AdEngine to consider the dedup algo ENUM and lookup the `adHashes`
    information to get the recently served Ads.

4.  AdEngine to filter out the ineligible campaigns based on the dedup
    algo and `adHashes` information.

5.  AdEngine to log the current dedup algo ENUM in the Kudu, for every
    request.

6.  AdEngine to log why the dedup algo was overriden for the selected
    campaign, in Kudu (`dedup_override=UD/RB`). This happens when a
    campaign is marked as underdelivering (UB) or is configured as
    roadblock (RB).

## Client

Ads Handshake -

1.  On the App launch, client triggers the Ads Handshake (existing
    flow).

2.  AdsBE will respond with the targeted dedup algo ENUM + Handshake
    refresh frequency (in seconds).

3.  Client will parse the ENUM and also the handshake refresh frequency
    `refresh`, after which the client will retrigger the Ads Handshake
    and refresh the App side variables.

note

**Note**

1.  App launch can happen via -

    1.  Clicking the notification

    2.  Clicking the deeplink

    3.  Organic

2.  Client should trigger the Ads Handshake in all these above cases,
    during the launch + after every `refresh` seconds.

:::: {.panel .conf-macro .output-block style="background-color: rgb(234,230,255);border-color: rgb(153,141,217);border-width: 1.0px;"}
::: {.panelContent style="background-color: rgb(234,230,255);"}
**Note**

1.  App launch can happen via -

    1.  Clicking the notification

    2.  Clicking the deeplink

    3.  Organic

2.  Client should trigger the Ads Handshake in all these above cases,
    during the launch + after every `refresh` seconds.
:::
::::

Ad Request and Deduping -

1.  Client will maintain the list of Ads in the cache + previously
    rendered, along with below information -

    1.  adHashId

    2.  placement

    3.  subslot

    4.  impression done

    5.  discarded

2.  Client will send this information in every Ad request, in the post
    body in the array named `recentAds`. [Exact format
    here](https://evp.atlassian.net/wiki/spaces/NHADSPLTL/pages/131727466/Ads+Dedup+-+Protocol+Document#Ad-Request).

3.  Client will parse the `adHashId` field being sent in the Ad
    response.

4.  Before inserting the Ad into the view, client will check if the Ad's
    `adHashId` matches any of the previously rendered Ads (depending on
    the dedup algo sent in the Ads handshake).

    1.  If the `adHashId` matches, then the Ad is discarded and the new
        Ad is requested.

    2.  If the `adHashId` does not match, then the Ad is inserted into
        the view.

5.  If the Ad is discarded due to the dedup logic, then App should make
    the `discarded` field as true in the Ad's object in the `recentAds`
    array.

note

**Note**

1.  The `dedupAlgo` field in the Ads handshake might contain below
    possible values -

    1.  `null` or `""` - no dedup should be done.

    2.  `"ALGO_ENUM"` - respective dedup algo to be used.

    3.  `"ALGO_ENUM_1,ALGO_ENUM_2"` - respective dedup algos to be used
        (multiple).

2.  The client should ignore the empty Ad's object to be put in the
    `recentAds` array.

3.  The maximum number of objects to be maintained in the `recentAds`
    array is communicated in the Ads handshake response, in the field
    named `maxRecentAds`.

4.  If possible, the client should maintain the timeline order of the
    objects in the `recentAds` array. Starting with the recent Ad info
    at the top. This makes it computationally a lot easier for the
    backend to pick the right info.

:::: {.panel .conf-macro .output-block style="background-color: rgb(234,230,255);border-color: rgb(153,141,217);border-width: 1.0px;"}
::: {.panelContent style="background-color: rgb(234,230,255);"}
**Note**

1.  The `dedupAlgo` field in the Ads handshake might contain below
    possible values -

    1.  `null` or `""` - no dedup should be done.

    2.  `"ALGO_ENUM"` - respective dedup algo to be used.

    3.  `"ALGO_ENUM_1,ALGO_ENUM_2"` - respective dedup algos to be used
        (multiple).

2.  The client should ignore the empty Ad's object to be put in the
    `recentAds` array.

3.  The maximum number of objects to be maintained in the `recentAds`
    array is communicated in the Ads handshake response, in the field
    named `maxRecentAds`.

4.  If possible, the client should maintain the timeline order of the
    objects in the `recentAds` array. Starting with the recent Ad info
    at the top. This makes it computationally a lot easier for the
    backend to pick the right info.
:::
::::

# Protocols

## Ads Handshake

Below are the new fields getting added in the Ads handshake response -

json{ \"dedupAlgo\": \"DEDUP_ALGO_1\", \"refresh\": 300,
\"maxRecentAds\": 20 }

## Dedup Algo ENUMs

+-------------------+------------------------+------------------------+
| **ENUM**          | **Zones Involved**     | **Flow**               |
+-------------------+------------------------+------------------------+
| DEDUP_CP_ST       | `card-p0` and          | `card-p0` →            |
|                   | `storypage`            | `storypage`            |
|                   |                        |                        |
|                   |                        | `storypage` →          |
|                   |                        | `card-p0`              |
+-------------------+------------------------+------------------------+
| DEDUP_LIST_PAGE   | `card-p0`, `card-pp1`  | `card-p0` → `card-pp1` |
|                   | and `card-p1`          | → `card-p1`            |
+-------------------+------------------------+------------------------+
| DEDUP_CP1         | `card-p1`              | `card-p1` → `card-p1`  |
+-------------------+------------------------+------------------------+
| DEDUP_DETAIL_PAGE | `storypage` and        | `stotrypage` →         |
|                   | `supplement`           | `supplement`           |
+-------------------+------------------------+------------------------+
| DEDUP_SP          | `supplement`           | `supplement sp1` →     |
|                   |                        | `supplement sp2` → ... |
+-------------------+------------------------+------------------------+

## Ad Request

Below is the structure `recentAds` field that is to be sent in the post
body of every Ad request -

json\[ { \"placement\": \"card-pp1\", \"subslot\": \"pp1_2\",
\"adHashId\": \"1eldnweofi3029rodaflkm\", \"impression\": true,
\"discarded\": false, \"timestamp\": 1658769235 }, { \"placement\":
\"card-pp1\", \"subslot\": \"pp1_1\", \"adHashId\":
\"1eldnweofi3029rodaflkm\", \"impression\": false, \"discarded\": true,
\"timestamp\": 1658769227 }, { \"placement\": \"storypage\",
\"subslot\": \"\", \"adHashId\": \"1eldnweofi3029rodaflkm\",
\"impression\": false, \"discarded\": false, \"timestamp\": 1658769201 }
\]

## Ad Response

Below are the new fields getting added to the Ad response -

json{ \"ads\": \[ { \... \"adHashId\": \"1eldnweofi3029rodaflkm\", \...
} \] }
