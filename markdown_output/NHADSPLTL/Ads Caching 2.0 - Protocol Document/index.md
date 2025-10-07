Table of Contents17

# Overview

To remodel the App side Ad cache and build for near realtime cache
refresh to solve the thin user DAU problem, over-delivery problem with
persisted Ads and possibly gain additional inventory that is currently
lost due to network and connectivity problems.

# High Level Design

1.  The App contains one global Ad cache which is split per Ad placement
    basis called a "Placement Cache Block".

2.  Each Placement Cache Block contains `priority` ordered list of Ad
    Objects.

3.  Each Ad Object contains the metadata of the Ad to render along with
    Expiry DateTime and Frequency Cap information.

4.  The Ad Cache's refresh time is driven by the `refreshIntervalFGSecs`
    for foreground and `refreshIntervalBGSecs` for background.

5.  Each Ad is marked either `PRIMARY` (Non-Remnant Ads) or `SECONDARY`
    (Remnant Ads).

6.  All the `PRIMARY` Ads are consumed first, then the App gives a
    chance to the Ads BE to render an Ad. If left unfilled, the App
    continues the consumption to `SECONDARY` Ads.

# App Workflow

## Background Cache Refresh

### Scheduled Job via Work-manager

1.  As per the default configuration in the App, the App makes a call to
    `/cacheRefresh` API.

2.  The `/cacheRefresh` API will relay the Ads to be cached along with
    the configuration set that defines the interval to refresh the cache
    in the background.

3.  The App schedules a work manager based background job for next
    `/cacheRefresh` hit.

### Notification Delivery Based

1.  On every notification delivery, the App checks if there are any
    cached Ads or not.

    1.  If No (empty cache), App immediately makes a call to the
        `/cacheRefresh` endpoint.

    2.  If Yes, App will check if the cache refresh interval has passed.

        1.  If Yes, App makes a `/cacheRefresh` call immediately.

        2.  If No, the App does nothing and the next refresh will still
            happen as per the scheduled job.

### Silent Notification Based

**Background**:\
The users that a notification is sent to is defined by user segment
rules at the scenario entity level. These scenario entities are stored
at Obelix, and for each notification we need to pass the scenario key
which will define the user base; we cannot send user segment rules
dynamically.

**Options for sending the silent notification:**\
(a) Assuming the users that the silent notification is supposed to be
sent to are mostly defined by the language and no other rules (or mostly
static rules), we can create one scenario per language, and the user
segment selected for the silent notification would be based on the
language-specific scenario.\
(b) If the user segment rules are going to be very dynamic, then we can
create a single scenario for sending this silent notification, and
update the user segment rules in that scenario each time before sending
the notification, based on the user rules sent by the Ads system.

One (very rare) issue that can arise in the approach (b) is that the
scenario update call may fail. We can add retries, but if those also
fail, we need to cancel sending the silent notification, or apply some
other remedy. We will log whatever decision is applied in any case, for
reporting/consumption by Ads system.

**Components**:

- Kafka topic:

  - cacheRefreshSN - For receiving message from Ads silent notification
    and to be consumed by Notification Tool.

  - notificationScale - For receiving message from Notification tool and
    consumed by Ads Scaler.

- Services:

  - Notification Tool

    - This tool will process the message from cacheRefreshSN to
      construct targeted audience notifications to be pushed to further
      pipelines.

  - Ads silent notification

    - Pushes payload to kafka topic containing which subset of users to
      be targeted depending on parameters.

  - Ads Scaler

    - This will trigger autoscaling depending upon audience segment
      received from Kafka topic.

**Communications**:

1.  Ads silent notification to cacheRefreshSN topic to Notification
    tool:

    1.  Message Protocol:

        1.  json{ \"baseInfo\": { \"subType\":
            \"refresh_now_bg_fg/refresh_older_than_bg_fg/refresh_delayed_by_bg/update_urls\",
            \"timeStamp\": 1663185011129, \"timeDurationInSec\": 3600,
            \"dedupeKey\": \"\<same_as_type\>\" },
            \"cacheRefreshEndpointFG\":
            \"http://qa-money.newshunt.com/api/v2/cacheRefresh?urlSource=silent_notification\",
            \"cacheRefreshEndpointBG\":
            \"http://qa-money.newshunt.com/api/v2/cacheRefresh?urlSource=silent_notification\",
            \"audience\": { \"criteria\": \[ {\"field\":\"lang\",
            \"op\":\"EQ\", \"value\": \"EN\"}, {\"field\":\"city_id\",
            \"op\":\"EQ\", \"value\": \"c21_567\"},
            {\"field\":\"last_delivery_date\", \"op\":\"LTE\",
            \"value\": 1664515095},
            {\"field\":\"first_activation_date\", \"op\":\"GTE\",
            \"value\": 1664515095}, {\"field\":\"last_pv_date\",
            \"op\":\"LTE\", \"value\": 1664515095},
            {\"field\":\"state_id\", \"op\":\"EQ\", \"value\": \"s21\"},
            {\"field\":\"latest_activation_date\", \"op\":\"GTE\",
            \"value\": 1664515095}, {\"field\": \"install_type\",
            \"op\":\"EQ\", \"value\": \"reinstall\"}, {\"field\":
            \"segment\", \"op\":\"IN\", \"value\":
            \[\"NG_ENTERTAINMENT\"\]}, {\"field\": \"dnd_genre\",
            \"op\":\"EQ\", \"value\": \"NG_ENTERTAINMENT\"}, {\"field\":
            \"followed_topic.0c239a072fc5b7b3e687965b91150043\",
            \"op\":\"EQ\", \"value\": \"FOLLOW\"},
            {\"field\":\"normalized_user_app_version\", \"op\":\"EQ\",
            \"value\": 19000016} \] } }

            Ads silent notification service will push the above format
            to cacheRefreshSN topic.

        2.  Intent of attributes in the Message protocol payload:

            1.  attr - This defines the ways cache refresh needs to be
                done in either of the ways as defined in silent
                notification Payload.

            2.  who - This defines the subset of parameters to be
                considered for targeting by notification tool. Ex:
                language etc.

            3.  when - Current value considered is now. This defines as
                and when the notification is received.

            4.  criteria - Atleast a single condition is expected.

            5.  cacheRefreshEndpointFG & cacheRefreshEndpointBG →
                CacheRefresh URL.

        3.  To stagger the dispatch, create multiple non-intersecting
            audience criteria and relay multiple small segments to the
            Notification Tool.

        4.  PHASE 2 - Plan for Ads prepared user base (chunked already)
            and relay to Notification Tool.

# Notification-based Ads Infra Scaling

## Escort Message communication

- Notification tool to `notificationScale` topic to Ads Scaler:

  1.  Message Protocol:

      1.  json{ \"type\": \"breaking/scheduled\", \"itemId\":
          \"n435rf545\", // Mandatory for breaking & optional for
          scheduled \"dispatchTS\": 1664189985, \"audience\": {
          \"userRules\":
          \[{\"OR\":\[{\"STRING\":{\"field\":\"\$user.a.segment\",\"op\":\"EQ\",\"value\":\"QA_TEST\"}},{\"STRING\":{\"field\":\"\$user.a.lang\",\"op\":\"EQ\",\"value\":\"EN\"}}\]},{\"AND\":\[{\"NUMERIC\":{\"field\":\"\$user.i.normalized_user_app_version\",\"op\":\"GTE\",\"value\":17001000}},{\"STRING\":{\"field\":\"\$user.a.lang\",\"op\":\"EQ\",\"value\":\"EN\"}}\]}\],
          // other param segments \"forecast\": 65374888, \"delivered\":
          \[64987867, 64987827\] // last X delivered sizes } }

          This payload will help understand the level of autoscaling
          required by Ads to serve expected cache refresh calls. This
          event is pushed to the topic before `x` seconds of the
          notification dispatch time. `x` here is the configuration at
          the notification tool side.

      2.  Sample userRules added in this doc:
          [https://docs.google.com/document/d/1GFgUq1DyxfKjX3JgbJ9Q46qVxRR6thAuY-yafNP9AC4/edit](https://docs.google.com/document/d/1GFgUq1DyxfKjX3JgbJ9Q46qVxRR6thAuY-yafNP9AC4/edit){card-appearance="inline"}

      3.  Unique parameters to consider from above mentioned doc. These
          fields will be pushed to cacheRefreshSN topic (field name →
          data type):

          1.  lang - string

          2.  city_id - string

          3.  last_delivery_date - integer

          4.  first_activation_date - integer

          5.  last_pv_date - integer

          6.  state_id - string

          7.  latest_activation_date - integer

          8.  install_type - string

          9.  segment - string

          10. dnd_genre - **Need to confirm (Vaibhav input required)**

          11. followed_topic - map of topic id to UNFOLLOW/FOLLOW

          12. normalized_user_app_version - integer

  2.  Intent of attributes in the Message protocol payload:

      1.  type: breaking or scheduled will help understand whether
          predictive autoscaling is good enough or forced autoscaling is
          required.

      2.  dispatchTS: This will state the time of notification dispatch.

      3.  audienceSize: It will define estimated size of audience for
          each segment.

  3.  to post offline data (audience size for above usecases) for a
      weekday and a weekend day.

## Phase 1 - Autoscaling Plan

### For Scheduled Notification

Based on the Escort Message from the Notification BE, trigger a CPU
stresser process that will generate an artificial load to upscale the
existing cluster until the required number of instances are spawned.

Do this just before `x` seconds of the notification dispatch, so that
the newly spawned instances are still alive in the idle state when the
actual notification traffic hits.

### For Breaking Notification

Based on the Escort Message from the Notification BE, trigger a CPU
stresser process that will generate an artificial load for `x`
milliseconds which leads to the upscale of the cluster.

Doing this for very small quantum of time is very critical, because the
breaking news escort message comes just before 1-3 seconds of
notification dispatch. Which means, the actual traffic is going to hit
the cluster almost immediately.

**Caveat:** The cluster might not be able to scale up to the extent
required to be prepared to handle the upcoming traffic, but still it is
quite a bit of scale up that helps the cluster scale quick enough to
handle the actual traffic.

# Ad Replacement Matrix

  ---------------------- --------------- ----------------- ----------------- ---------------------
  **Rendered Ad Type**   **Inflated?**   **Impression?**   **New Ad Type**   **Should Replace?**
  Non-Empty              Yes             No                Non-Empty         Yes
  Non-Empty              Yes             No                Empty             No
  Non-Empty              Yes             Yes               Non-Empty         No
  Non-Empty              Yes             Yes               Empty             No
  Empty                  Yes             No                Non-Empty         Yes
  Empty                  Yes             No                Empty             No
  Empty                  Yes             Yes               Non-Empty         Yes
  Empty                  Yes             Yes               Empty             No
  ---------------------- --------------- ----------------- ----------------- ---------------------

# Client Request Protocol

## Cache refresh api

1.  Send `adRequestParams` object as POST param.

2.  Send `refreshInfo` object as POST param.

3.  Send `cachedAdsInfo` object in POST param.

4.  Send `timestamp` object in POST param.

5.  Also send everything that is currently passed in index.php post
    body.

    1.  uses-permission

    2.  excludeBanners (to be maintained and communicated per zone
        level)

    3.  adStatistics

    4.  langInfo

    5.  fcap

    6.  fbBidderToken

    7.  amazonSdkPayload

## Ad Request api (index.php)

1.  No change in the existing query params.

2.  Send `cachedAdsInfo` object in POST param. This will be only for the
    zone being requested for.

3.  Also send everything that is currently passed in post body.

    1.  uses-permission

    2.  excludeBanners

    3.  adStatistics

    4.  langInfo

    5.  fcap

    6.  fbBidderToken

    7.  amazonSdkPayload

    8.  contentContext

    9.  parentContentContext

## Beacons

1.  `timestamp`

2.  Send `adInstanceInfo` object in POST param.

3.  Send `passThrough` object in POST param

4.  **RequestUrl (fallback):**

    1.  Send `contextInfo` object in POST param.

    2.  Send `adRequestParams` object in POST param.

    3.  Send `source` in POST param.

5.  **InflatedUrl:**

    1.  Send `replacedAdInfo` object in POST param.

    2.  Send `inflationDelayMs` in POST param.

6.  **ImpressionUrl:**

    1.  Send `replacedAdInfo` object in POST param.

    2.  Send `impressionDelayMs` in POST param.

    3.  Send `negateImpression` in POST param.

7.  **AdReady**

    1.  Send `source` in POST param.

8.  **AdError**

    1.  Send `reason` in POST param.

9.  **AdDropped**

    1.  Send `reason` in POST param.

    2.  Send `adDroppedCode` in POST param.

10. **CacheRefreshReceivedUrl:**

    1.  Send `refreshInfo` in POST param.

    2.  { \"beacons\": { \"cacheRefreshReceivedBeaconUrls\": {
        \"internal\": \[
        \"http://qa-money.newshunt.com/beaconEvents?crUniqueId=abcd1234&clientId=722000&eventType=CACHE_REFRESH_RECEIVED\"
        \] } } }

11. **CacheRefreshError**

    1.  Send `refreshInfo` in POST param.

    2.  Send `reason` in POST param.

    3.  Send `adRequestParams` in POST param.

## Repeat Ads and Frequency Cap

1.  Given the below facts -

    1.  App side cache has a per zone basis upper limit on number of
        Ads.

    2.  Campaigns can be configured in Contract Exclusive mode with some
        FCap.

    3.  Campaigns can be configured in Contract Exclusive mode without
        any FCap (Section/Topic sponsorship).

    4.  App side cache must not be filled with same repeated Ads,
        because it is a waste of the slots in the cache.

    5.  We need a solution to instruct the App to repeat certain Ads for
        certain count, without actually repeating the Ads in the cache.

2.  Ads BE will identify if an Ad needs to repeat itself, based on the
    Frequency Cap configured.

3.  Ads BE will append a new field `repeatCount` in every repeatable
    Ad's response JSON.

4.  If there are multiple repeatable Ads in the same campaign level
    (Roadblock/Linear) -

    1.  Ads BE will retain same priority.

    2.  App will round-robin between these repeatable Ads carrying same
        priority (this is to achieve the dedup).

5.  Once the `repeatCount` is reached or Frequency Cap is reached, the
    App will invalidate the cached Ad.

6.  App specific logic -

    1.  App needs to clone the repeatable Ads in order to use it
        multiple times.

    2.  App will generate a uniqueID for every Ad instance that is
        cached. This ID is relayed to AdsBE in a separate field in
        `AdInstanceInfo` object. The actual `id` field of the Ad is
        untouched.

    3.  Every time the Ad gets used from the cache (impression happens),
        the App checks if this Ad need to be repeated.

        1.  If Yes, the App will clone the Ad instance and generate new
            uniqueID for that Ad instance. App will append this Ad
            instance at the end of same priority list (for round-robin
            behaviour).

        2.  If No, the App will throw away the Ad instance.

# Fallback logic for IMA SDK Ads

1.  If the rendered Ad is an IMA SDK Ad, it might sometimes fail after
    it is inserted in the view.

2.  In such cases, the App will fallback to the next ready Ad in the
    queue.

3.  If the next Ad is -

    1.  [Not ready or No next Ad]{.underline}: Insert the fallback
        banner shared in the Ads Handshake and trigger its impression.

    2.  [Ready & Non-IMA SDK Ad]{.underline}: Render the Ad.

    3.  [Ready & IMA SDK Ad]{.underline}: Render and go to step #1.

# Amazon SDK Bids

1.  App receives the `zone` and `adUnitId` for which the bids need to be
    fetched.

2.  App fetches these bids on the App Start ONLY.

3.  App will pass the zone-subslot level bid information in the
    `cacheRefresh` and `index.php` API hits.\
    Field Name: `amazonSdkPayload` for `cacheRefresh` API

    json{ \"card-p1\": { \"default\": \[{ \"amazonBid\":
    \[\"Inmza0KV5G66pro4Rk-GCIUAAAF9uVV4JAMAAA-qAvB0wEg\"\],
    \"amazonHost\": \[\"aax-eu.amazon-adsystem.com\"\], \"amazonSlot\":
    \[\"o6gq1200_spp\"\], \"amazonp\": \[\"thle68\"\], \"dc\":
    \[\"dub\"\], \"slotUUID\": \"4761d13f-d3b8-4b1a-9297-45cbf9f4899c\"
    }\] }, \"supplement\": { \"sp1\": \[{ \"amazonBid\":
    \[\"Inmza0KV5G66pro4Rk-GCIUAAAF9uVV4JAMAAA-qAvB0wEg\"\],
    \"amazonHost\": \[\"aax-eu.amazon-adsystem.com\"\], \"amazonSlot\":
    \[\"o6gq1200_spp\"\], \"amazonp\": \[\"thle68\"\], \"dc\":
    \[\"dub\"\], \"slotUUID\": \"4761d13f-d3b8-4b1a-9297-45cbf9f4899c\"
    }\], \"sp2\": \[{ \"amazonBid\":
    \[\"Inmza0KV5G66pro4Rk-GCIUAAAF9uVV4JAMAAA-qAvB0wEg\"\],
    \"amazonHost\": \[\"aax-eu.amazon-adsystem.com\"\], \"amazonSlot\":
    \[\"o6gq1200_spp\"\], \"amazonp\": \[\"thle68\"\], \"dc\":
    \[\"dub\"\], \"slotUUID\": \"4761d13f-d3b8-4b1a-9297-45cbf9f4899c\"
    }\] } }

# Object Signatures

note

**NOTE**

1.  All the objects are communicated as the part of POST body in
    relevant API calls.

:::: {.panel .conf-macro .output-block style="background-color: rgb(234,230,255);border-color: rgb(153,141,217);border-width: 1.0px;"}
::: {.panelContent style="background-color: rgb(234,230,255);"}
**NOTE**

1.  All the objects are communicated as the part of POST body in
    relevant API calls.
:::
::::

## Cache Refresh Request Object

**Field Name:** `refreshInfo`

**Object Signature:**

json{ \"id\": \"vdsf8u4eufheduifh94er4\", \"source\" :
\"SCHEDULED\|ADS_USED\|ADS_REMAINING\|APP_LAUNCH\|NOTIFICATION_DELIVERY\|ADS_SILENT_NOTIFICATION\|APP_WAKE_UP\",
\"appState\" : \"FG/BG\", \"triggerPlacement\" : \"card-p0/storypage\",
\"timestamp\" : 1425744000000 }

## Cache Snapshot Object

Cached Ad Info Object will have the zone wise ads present in the cache.

**Field Name:** `cachedAdsInfo`

**Object Signature:**

json{ \"card-p0\": { \"DEFAULT\": \[ { \"id\":
\"409f0cc72d8823bbb505f9e7cae1b764\", \"campaignId\": \"1024\",
\"bannerId\": \"2094\", \"passThrough\": { \"ch\":
\"eoirewr8uew8rueoicfnoweiur9\", \"bh\":
\"32094u9302874983uyfoidsjflkc\" }, \"priority\": 5006, \"endepoch\":
\"1664905285\", \"isReady\": true }, { \"id\":
\"409f0cc72d8823bbb505f9e7cae1b765\", \"campaignId\": \"1024\",
\"bannerId\": \"2094\", \"passThrough\": { \"ch\":
\"eoirewr8uew8rueoicfnoweiur9\", \"bh\":
\"32094u9302874983uyfoidsjflkc\" }, \"priority\": 5004, \"endepoch\":
\"1664905285\", \"isReady\": false } \] }, \"supplement\": { \"sp1\": \[
{ \"id\": \"409f0cc72d8823bbb505f9e7cae1b766\", \"campaignId\":
\"1024\", \"bannerId\": \"2094\", \"passThrough\": { \"ch\":
\"eoirewr8uew8rueoicfnoweiur9\", \"bh\":
\"32094u9302874983uyfoidsjflkc\" }, \"priority\": 5008, \"endepoch\":
\"1664905285\", \"isReady\": false } \], \"sp2\": \[ { \"id\":
\"409f0cc72d8823bbb505f9e7cae1b769\", \"campaignId\": \"1024\",
\"bannerId\": \"2094\", \"passthrough\": { \"ch\":
\"eoirewr8uew8rueoicfnoweiur9\", \"bh\":
\"32094u9302874983uyfoidsjflkc\" }, \"priority\": 5003, \"endepoch\":
\"1664905285\", \"isReady\": false } \] } }

## Replaced Ad Info Object

**Field Name:** `replacedAdInfo`

**Object Signature:**

json{ \"id\": \"409f0cc72d8823bbb505f9e7cae1b764\", \"campaignId\":
\"1024\", \"bannerId\": \"2095\", \"prevAdState\": \"IMPR\",
\"replacedAt\": \"1663578834\", \"passThrough\": { \"ch\":
\"eoirewr8uew8rueoicfnoweiur9\", \"bh\":
\"32094u9302874983uyfoidsjflkc\", \"rt\": 1664348528 },
\"adInstanceInfo\": { \"uniqueId\" : \"\<UUID\>\", \"adPlacement\":
\"\<AD_PLACEMENT\>\", \"subslot\" : \"\<SUB_SLOT\>\", \"reqTime\" :
\"\<TIMESTAMP\>\" } }

## Negate Impression Object

Field Name: `negateImpression`

Object Signature:

{ \"id\": \"409f0cc72d8823bbb505f9e7cae1b764\", \"campaignId\":
\"1024\", \"bannerId\": \"2095\", \"replacedAt\": \"1663578834\",
\"passthrough\": { \"ch\": \"eoirewr8uew8rueoicfnoweiur9\", \"bh\":
\"32094u9302874983uyfoidsjflkc\", \"rt\": 1664348500 },
\"adInstanceInfo\": { \"uniqueId\" : \"\<UUID\>\", \"adPlacement\":
\"\<AD_PLACEMENT\>\", \"subslot\" : \"\<SUB_SLOT\>\", \"reqTime\" :
\"\<TIMESTAMP\>\" } }

## Context Info Object

Definition for the values can be referred
[here](https://evp.atlassian.net/wiki/spaces/NHADSPLTL/pages/109609309/Evergreen+Ads+-+Protocol+V1#Macro-Definition).

**Field Name:** `contextInfo`

**Object Signature:**

json{ \"contentId\": \"\<POST_ID\>\", \"entityId\": \"\<ENTITY_ID\>\",
\"entityType\": \"\<ENTITY_TYPE\>\", \"entitySubType\":
\"\<SUB_ENTITY_TYPE\>\", \"sourceType\": \"\<SOURCE_TYPE\>\",
\"sourceId\": \"\<SOURCE_ID\>\", \"sourceCatId\": \"\<SOURCE_CAT_ID\>\",
\"pageReferrer\": \"\<PAGE_REFERRER\>\" \"referrerId\":
\"\<REFERRER_ID\>\", }

## Ad Request Params Object

Definition for the values can be referred
[here](https://evp.atlassian.net/wiki/spaces/NHADSPLTL/pages/109609309/Evergreen+Ads+-+Protocol+V1#Macro-Definition).

**Field Name:** `adRequestParams`

**Object Signature:**

json{ \"clientId\" : \"\<CLIENT_ID\>\", \"os\" : \"\<USER_OS\>\",
\"appVer\" : \"\<APP_VERSION\>\", \"osVer\" : \"\<USER_OS_VERSION\>\",
\"lat\" : \"\<LATITUDE\>\", \"long\" : \"\<LONGITUDE\>\", \"cellId\" :
\"\<CELL_ID\>\", \"udId\" : \"\<UDID\>\", \"resolution\" :
\"\<DEVICE_RESOLUTION\>\", \"connectionType\" : \"\<USER_CONNECTION\>\",
\"connectionSpeed\" : \"\<CONNECTION_SPEED\>\", \"gaid\" :
\"\<ADVERTISING_ID\>\", \"userLang\" : \"\<USER_LANGUAGE\>\",
\"density\" : \"\<DENSITY\>\", \"autoPlayPref\" :
\"\<AUTO_PLAY_PREF\>\", \"isNightMode\" : true/false, \"muteState\" :
true/false, \"cardSize\" : \"large\" }

## Ad Instance Info Object

Definition for the values can be referred
[here](https://evp.atlassian.net/wiki/spaces/NHADSPLTL/pages/109609309/Evergreen+Ads+-+Protocol+V1#Macro-Definition).

**Field Name:** `adInstanceInfo`

**Object Signature:**

json{ \"uniqueId\" : \"\<UUID\>\", \"adPlacement\":
\"\<AD_PLACEMENT\>\", \"subslot\" : \"\<SUB_SLOT\>\", \"reqTime\" :
\"\<TIMESTAMP\>\" }

## Silent Notification Client-Server Payload

This payload comes as the part of silent notification meant to control
the Ads cache refresh behaviour. Silent notification payload -

json{ \"message_v6\": { \"baseInfo\": { \"subType\":
\"refresh_now_bg_fg/refresh_older_than_bg_fg/refresh_delayed_by_bg\",
\"timeStamp\": 1663185011129, \"timeDurationInSec\": 3600,
\"dedupeKey\": \"\<same_as_type\>\" }, \"cacheRefreshEndpointFG\":
\"\<fg refresh cache url\>\", \"cacheRefreshEndpointBG\": \"\<bg refresh
cache url\>\" }, \"type\": \"ads_cache_refresh\", \"version\": \"v6\" }

- `subType` - tells whats the use case the silent notification was sent
  for

- `timeStamp` - Timestamp when notification was sent from BE

- `timeDurationInSec` - Time duration in seconds for

  - the duration between last refresh and the time when notification was
    received (for notification of subType: refresh_older_than_bg_fg),
    which if exceeded will lead to an immediate refresh
    background/foreground, else refresh will be done according to
    previously scheduled refresh.

  - the duration from the time of notification delivery to client, post
    which a background refresh will be tried, any pending scheduled
    background refresh will be reset.

- `dedupeKey` key to be used to be used for deduping, will be same for
  all notifications related to ads_cache_refresh, BE controlled.

# Update Operation

1.  Ads BE will use DELETE + ADD operations instead of UPDATE in the
    following cases -

    1.  If an Ad is moving from PRIMARY to SECONDARY or vice-versa.

    2.  If the banner metadata is changing.

## Updateable Fields

1.  `startepoch`

2.  `endepoch`

3.  `priority`

4.  `impFcap`

5.  `bImpFcap`

6.  `passthrough`

# Single Ad Request

## After PRIMARY Ads

The App will utilise all the PRIMARY Ads from the appropriate placement
block and then triggers a single Ad fetch call (`getAds` API), to allow
the Ads BE to respond with a new PRIMARY Ad, if available.

The Ads BE will respond either with an available PRIMARY Ad or an Empty
Ad with SECONDARY marking and `-1` priority.

## In-eligible Ads

The App will evaluate the content context targeting, frequency cap and
campaign expiry time to consider the Ad as eligible for the opportunity
in hand. If these checks fail and none of the Ads in the cache are
eligible for the opportunity, the App makes a call to fetch a single Ad.

## No Cached Ads

It is possible sometimes that there are no cached Ads. May be the user
is opening the App for the first time or Ads BE has not responded with
any Ads to cache. In such cases, the App falls back to making the single
Ad calls instead.

However, on every trigger point of the cache refresh, the App keeps
trying the `cacheRefresh` API to fill the cache.

# Mock Responses

[Add Mock
Api](http://qa-money.newshunt.com/daedalus-banners/adengine_mock/release_20.1.x/add_mock.json)

ADD operationjson{ \"config\": { \"firstServerAdFetchTimeoutMs\": 0,
\"serverAdFetchTimeoutMs\": 0, \"zoneAssetFetchPriority\": \[
\"storypage\", \"card-p0\", \"card-pp1\" \], \"foreground\": {
\"refresh\": { \"intervalSecs\": 300, \"consumptionBased\": true,
\"remainingAdsBased\": true }, \"zoneWiseConfig\": { \"card-p0\": {
\"DEFAULT\": { \"prefetchAssets\": 2, \"thresholdAdCount\": { \"used\":
1, \"remainingPrimary\": 2 } } }, \"storypage\": { \"DEFAULT\": {
\"prefetchAssets\": 2, \"thresholdAdCount\": { \"used\": 1,
\"remainingPrimary\": 2 } } }, \"card-pp1\": { \"pp1_1\": {
\"prefetchAssets\": 2, \"thresholdAdCount\": { \"used\": 1,
\"remainingPrimary\": 2 } }, \"pp1_2\": { \"prefetchAssets\": 1,
\"thresholdAdCount\": { \"used\": 2, \"remainingPrimary\": 2 } },
\"pp1_c1\": { \"prefetchAssets\": 1, \"thresholdAdCount\": { \"used\":
2, \"remainingPrimary\": 2 } }, \"pp1_c2\": { \"prefetchAssets\": 1,
\"thresholdAdCount\": { \"used\": 2, \"remainingPrimary\": 2 } },
\"pp1_c3\": { \"prefetchAssets\": 1, \"thresholdAdCount\": { \"used\":
2, \"remainingPrimary\": 2 } } }, \"supplement\": { \"sp1\": {
\"prefetchAssets\": 1, \"thresholdAdCount\": { \"used\": 1,
\"remainingPrimary\": 2 } }, \"sp2\": { \"prefetchAssets\": 1,
\"thresholdAdCount\": { \"used\": 1, \"remainingPrimary\": 2 } },
\"sp3\": { \"prefetchAssets\": 1, \"thresholdAdCount\": { \"used\": 1,
\"remainingPrimary\": 2 } }, \"sp4\": { \"prefetchAssets\": 1,
\"thresholdAdCount\": { \"used\": 1, \"remainingPrimary\": 2 } } },
\"splash\": { \"DEFAULT\": { \"prefetchAssets\": 1,
\"thresholdAdCount\": { \"used\": 1, \"remainingPrimary\": 1 } } },
\"splash-exit\": { \"DEFAULT\": { \"prefetchAssets\": 1,
\"thresholdAdCount\": { \"used\": 1, \"remainingPrimary\": 1 } } } } },
\"background\": { \"refresh\": { \"intervalSecs\": 3600 },
\"zoneWiseConfig\": { \"card-p0\": { \"DEFAULT\": { \"prefetchAssets\":
2 } }, \"storypage\": { \"DEFAULT\": { \"prefetchAssets\": 2 } },
\"card-pp1\": { \"pp1_1\": { \"prefetchAssets\": 2 }, \"pp1_2\": {
\"prefetchAssets\": 1 } } } } }, \"ads\": { \"storypage\": {
\"DEFAULT\": { \"ADD\": \[ { \"type\": \"external-sdk\", \"aduid\":
\"notId=ad-1679957612\", \"srcUrlExpiry\": \"86400\", \"adGroupId\":
\"548000126334016f63d2f7.36206577\", \"width\": \"1080\", \"height\":
\"607.5\", \"card-position\": 1, \"positionWithTicker\": 1,
\"min-ad-distance\": 4, \"bannerid\": \"98154\", \"adTemplate\": \"H\",
\"showOnlyImage\": \"false\", \"id\":
\"ed4e9253de9d2af990a1bae65ee6fcd3\", \"span\": 60,
\"useInternalBrowser\": \"false\", \"useWideViewPort\": \"false\",
\"allowDelayedAdInsert\": \"true\", \"adContext\": null, \"showTitle\":
\"false\", \"needsBackupAds\": \"true\", \"ignoreVideoDuration\":
\"480000\", \"adDistanceMs\": \"180000\", \"dedupId\":
\"ed4e9253de9d2af990a1bae65ee6fcd3\", \"adCacheGood\": \"1\",
\"adCacheAverage\": \"1\", \"adCacheSlow\": \"1\", \"isLive\": false,
\"showLearnMore\": true, \"adTagPosition\": \"BOTTOM_OVERLAY_LEFT\",
\"showBorder\": false, \"campaignId\": \"98154\", \"priority\": 6999,
\"startepoch\": 1653503400, \"endepoch\": 1664359823, \"adCategory\":
\"PRIMARY\", \"passthrough\": { \"ch\": \"\", \"bh\": \"\" },
\"isLargeAd\": false, \"errorUrl\":
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=ed4e9253de9d2af990a1bae65ee6fcd3&adId=1679957612&campaignId=98154&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=54800012&reqTime=1664352616&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"largeAdDistance\": 8, \"position\": \"card-p0\", \"sdk-order\": 1,
\"beaconUrl\":
\"http://stage-ads2.dailyhunt.in/impression?uniqueId=ed4e9253de9d2af990a1bae65ee6fcd3&adId=1679957612&campaignId=98154&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=54800012&reqTime=1664352616&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"external\": { \"tagURL\":
\"http%3A%2F%2Fstage-ads2.dailyhunt.in%2Fgetvast%3FclientId%3D54800012%26uniqueId%3Ded4e9253de9d2af990a1bae65ee6fcd3%26adId%3D1679957612%26campaignId%3D98154%26adPlacement%3Dcard-pp1%26cap%3D0%26reset%3D0%26billingTypeId%3D3%26orderId%3D57239%26forceTracker%3D%26gaid%3D8043aad5-507a-428d-a8d5-b09c98a46d68%26gaidOptoutStatus%3D0%26reqTime%3D1664352616%26partnerId%3DDH_APP%26subSlot%3Dpp1_1%26nextAdIndex%3D%26bookedPlacement%3Dstorypage%26bookedSubSlot%3D%26clientVersions%3D16.0%26os%3Dandroid%26ucq%3Dslow%26resolution%3D1080x2028\",
\"mediaFileURL\":
\"http://video-service-stage.dailyhunt.in/video/a2-ac3e9d10e5a211ecbff9138e63d585e2_l.m3u8\",
\"vastIdentifier\": \"internal-vast\", \"data\": \"IMA-SDK\" },
\"beaconUrlAdditional\": \[ \"http://www.googl.com/imp1\" \],
\"landingUrlAdditional\": \[ \"http://www.googl.com/ck1\" \],
\"landingUrl\": null, \"content\": { \"itemSubtitle2\": { \"color\":
\"#4caf79\", \"color-night\": \"#ffffff\" }, \"itemTag\": { \"color\":
\"#757575\", \"color-night\": \"#ffffff\", \"data\": \"Promoted\" },
\"reportText\": { \"color\": \"#FFFFFF\", \"color-night\": \"#FFFFFF\",
\"background-color\": \"#40000000\", \"background-color-night\":
\"#40000000\", \"data\": \"Ad\" }, \"thumbnailImageUrl\":
\"http://stage-ads2.dailyhunt.in/daedalus-banners/1679957612/1654524737_56651_990x505.jpg\",
\"learnMoreText\": { \"color\": \"#ffffff\", \"color-night\":
\"#ffffff\", \"data\": \"Learn More\" } }, \"brand\": { \"brandTitle\":
{ \"color\": \"#202020\", \"color-night\": \"#ffffff\", \"data\":
\"Test\" }, \"brandSubTitle\": { \"color\": \"#202020\",
\"color-night\": \"#ffffff\" }, \"brandFallbackText\": { \"color\":
\"#ffffff\", \"color-night\": \"#ffffff\", \"background-color\":
\"#ebab05\", \"background-color-night\": \"#ebab05\", \"type\": \"S\",
\"data\": \"T\" } }, \"action\":
\"https://stage-ads2.dailyhunt.in/click?clientId=54800012&uniqueId=ed4e9253de9d2af990a1bae65ee6fcd3&adId=1679957612&campaignId=98154&adPlacement=card-pp1&reqTime=1664352616&billingTypeId=3&orderId=57239&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=&\_\_oadest=http%3A%2F%2Fwww.google.com\",
\"adRespondedBeaconUrl\":
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=ed4e9253de9d2af990a1bae65ee6fcd3&adId=1679957612&campaignId=98154&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=54800012&reqTime=1664352616&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adInflatedBeaconUrl\":
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=ed4e9253de9d2af990a1bae65ee6fcd3&adId=1679957612&campaignId=98154&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=54800012&reqTime=1664352616&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adContextRules\": { \"selectionPriority\": 2, \"cacheType\":
\"persist\", \"ttl\": 432000, \"ruleGroup\": { \"rules\": \[\],
\"respondedFor\": { \"entityIds\": \[\], \"postId\": null } } },
\"adFeedback\": { \"feedbackUrl\": null }, \"requestUrl\":
\"http://stage-ads2.dailyhunt.in/fallback?clientid=54800012&req_time=28092022+13%3A40%3A16&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=none&user_handset_model=none&user_id=&placement=card-pp1&user_app_ver=16.0&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=storypage&banner_id=1679957612&campaign_id=98154&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=1028&price_range=none&user_device_type=none&title=vdo+2&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=ed4e9253de9d2af990a1bae65ee6fcd3&region=&mcc=&mnc=&lac=&cellid=&ip=127.0.0.1&adGroupId=548000126334016f63d2f7.36206577&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=0.01&audienceSegments=none&resolution=1080x2028&hostalias=VER-BLR-LT2817&locationSource=&pincode=&subSlot=pp1_1&bookedSubSlot=&ab=ECPM&partnerId=DH_APP&deliverySlab=1&userDeliverySlab=&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=0.01&utmSource=&utmMedium=&utmCampaign=&appId=&autoPlayPref=3&installDeliverySlab=&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=1&topCampaignIds=&topCampaignECPMs=&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=&campaignPrdictedCtr=&productIds=&recoPolicy=&request_timestamp=1664352616&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=&variantName=&modelUuid=&networkSwitch=&topDirectCampaign=&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=&campaign_type=LINEAR&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=96d5bb06a70dcc6a22e41e5d24d2dbde&gender=&age=&ageRange=&orderTypeV2=0&idfa=&s2sBidId=&imputationType=&amazonSdkPayload=&contentCreatorId=&scoringModel=&filteringModel=&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1664352616&\",
\"shareability\": null, \"adLPTimeSpentBeaconUrl\":
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=ed4e9253de9d2af990a1bae65ee6fcd3&adId=1679957612&campaignId=98154&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=54800012&reqTime=1664352616&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\"
}, { \"type\": \"imgLink\", \"aduid\": \"notId=ad-1240633164\",
\"srcUrlExpiry\": \"60\", \"width\": \"1080\", \"height\": 551,
\"card-position\": 1, \"positionWithTicker\": 1, \"min-ad-distance\": 4,
\"banner-fill\": \"fill-width\", \"bannerid\": \"1510006294\",
\"adTemplate\": \"L\", \"showOnlyImage\": \"false\", \"id\":
\"b75e71b521cb2310bd316cee98b0e298\", \"span\": \"60\",
\"useInternalBrowser\": \"false\", \"useWideViewPort\": \"true\",
\"adCacheGood\": \"1\", \"adCacheAverage\": \"1\", \"adCacheSlow\":
\"1\", \"allowDelayedAdInsert\": \"true\", \"adGroupId\":
\"548000126334016f666401.18552557\", \"adContext\": null, \"dedupId\":
\"b75e71b521cb2310bd316cee98b0e298\", \"adTagPosition\": \"TOP_RIGHT\",
\"showBorder\": false, \"campaignId\": \"1510006294\", \"impFcap\": {
\"cap\": \"3\", \"resetTime\": 2592000 }, \"priority\": 6998,
\"startepoch\": 1654626600, \"endepoch\": 1664359823, \"adCategory\":
\"PRIMARY\", \"passthrough\": { \"ch\": \"\", \"bh\": \"\" },
\"isLargeAd\": false, \"errorUrl\":
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=b75e71b521cb2310bd316cee98b0e298&adId=1240633164&campaignId=1510006294&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=54800012&reqTime=1664352616&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"largeAdDistance\": 8, \"position\": \"card-p0\", \"showPlayIcon\":
\"false\", \"beaconUrl\":
\"http://stage-ads2.dailyhunt.in/impression?uniqueId=b75e71b521cb2310bd316cee98b0e298&adId=1240633164&campaignId=1510006294&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=54800012&reqTime=1664352616&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"content\": { \"imgLink\":
\"http://stage-ads2.dailyhunt.in/daedalus-banners/1240633164/1660131474_86901_990x505.jpg\",
\"itemSubtitle2\": { \"color\": \"#4caf79\", \"color-night\":
\"#ffffff\" }, \"itemTag\": { \"color\": \"#757575\", \"color-night\":
\"#ffffff\", \"data\": \"Sponsored\" }, \"reportText\": { \"color\":
\"#999999\", \"color-night\": \"#FFFFFF\", \"background-color\":
\"#40000000\", \"background-color-night\": \"#40000000\", \"data\":
\"Ad\" } }, \"action\":
\"https://stage-ads2.dailyhunt.in/click?clientId=54800012&uniqueId=b75e71b521cb2310bd316cee98b0e298&adId=1240633164&campaignId=1510006294&adPlacement=card-pp1&reqTime=1664352616&billingTypeId=3&orderId=57239&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=&\_\_oadest=http%3A%2F%2Fwww.google.com\",
\"adLPTimeSpentBeaconUrl\":
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=b75e71b521cb2310bd316cee98b0e298&adId=1240633164&campaignId=1510006294&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=54800012&reqTime=1664352616&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adRespondedBeaconUrl\":
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=b75e71b521cb2310bd316cee98b0e298&adId=1240633164&campaignId=1510006294&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=54800012&reqTime=1664352616&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adInflatedBeaconUrl\":
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=b75e71b521cb2310bd316cee98b0e298&adId=1240633164&campaignId=1510006294&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=54800012&reqTime=1664352616&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adContextRules\": { \"selectionPriority\": 2, \"cacheType\":
\"persist\", \"ttl\": 432000, \"ruleGroup\": { \"rules\": \[\],
\"respondedFor\": { \"entityIds\": \[\], \"postId\": null } } },
\"adFeedback\": { \"feedbackUrl\": null }, \"requestUrl\":
\"http://stage-ads2.dailyhunt.in/fallback?clientid=54800012&req_time=28092022+13%3A40%3A16&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=none&user_handset_model=none&user_id=&placement=card-pp1&user_app_ver=16.0&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=storypage&banner_id=1240633164&campaign_id=1510006294&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=1028&price_range=none&user_device_type=none&title=img&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=b75e71b521cb2310bd316cee98b0e298&region=&mcc=&mnc=&lac=&cellid=&ip=127.0.0.1&adGroupId=548000126334016f666401.18552557&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=0.01&audienceSegments=none&resolution=1080x2028&hostalias=VER-BLR-LT2817&locationSource=&pincode=&subSlot=pp1_1&bookedSubSlot=&ab=ECPM&partnerId=DH_APP&deliverySlab=1&userDeliverySlab=&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=0.01&utmSource=&utmMedium=&utmCampaign=&appId=&autoPlayPref=3&installDeliverySlab=&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=1&topCampaignIds=&topCampaignECPMs=&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=&campaignPrdictedCtr=&productIds=&recoPolicy=&request_timestamp=1664352616&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=&variantName=&modelUuid=&networkSwitch=&topDirectCampaign=&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=&campaign_type=LINEAR&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=96d5bb06a70dcc6a22e41e5d24d2dbde&gender=&age=&ageRange=&orderTypeV2=0&idfa=&s2sBidId=&imputationType=&amazonSdkPayload=&contentCreatorId=&scoringModel=&filteringModel=&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1664352616&\",
\"shareability\": null } \], \"UPDATE\": \[\], \"DELETE\": \[\] } },
\"card-p0\": { \"DEFAULT\": { \"ADD\": \[ { \"type\": \"external-sdk\",
\"aduid\": \"notId=ad-1679957612\", \"srcUrlExpiry\": \"86400\",
\"adGroupId\": \"548000126334016f6ad689.69226231\", \"width\": \"1080\",
\"height\": \"607.5\", \"card-position\": 1, \"positionWithTicker\": 1,
\"min-ad-distance\": 4, \"bannerid\": \"98154\", \"adTemplate\": \"H\",
\"showOnlyImage\": \"false\", \"id\":
\"203db4c71fe4d20449c6b467d92dcaa1\", \"span\": 60,
\"useInternalBrowser\": \"false\", \"useWideViewPort\": \"false\",
\"allowDelayedAdInsert\": \"true\", \"adContext\": null, \"showTitle\":
\"false\", \"needsBackupAds\": \"true\", \"ignoreVideoDuration\":
\"480000\", \"adDistanceMs\": \"180000\", \"dedupId\":
\"203db4c71fe4d20449c6b467d92dcaa1\", \"adCacheGood\": \"1\",
\"adCacheAverage\": \"1\", \"adCacheSlow\": \"1\", \"isLive\": false,
\"showLearnMore\": true, \"adTagPosition\": \"BOTTOM_OVERLAY_LEFT\",
\"showBorder\": false, \"campaignId\": \"98154\", \"priority\": 6999,
\"startepoch\": 1653503400, \"endepoch\": 1664359823, \"adCategory\":
\"PRIMARY\", \"passthrough\": { \"ch\": \"\", \"bh\": \"\" },
\"isLargeAd\": false, \"errorUrl\":
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=203db4c71fe4d20449c6b467d92dcaa1&adId=1679957612&campaignId=98154&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=54800012&reqTime=1664352616&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-p0&bookedSubSlot=&contentId=&contentCreatorId=\",
\"largeAdDistance\": 8, \"position\": \"card-p0\", \"sdk-order\": 1,
\"beaconUrl\":
\"http://stage-ads2.dailyhunt.in/impression?uniqueId=203db4c71fe4d20449c6b467d92dcaa1&adId=1679957612&campaignId=98154&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=54800012&reqTime=1664352616&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-p0&bookedSubSlot=&contentId=&contentCreatorId=\",
\"external\": { \"tagURL\":
\"http%3A%2F%2Fstage-ads2.dailyhunt.in%2Fgetvast%3FclientId%3D54800012%26uniqueId%3D203db4c71fe4d20449c6b467d92dcaa1%26adId%3D1679957612%26campaignId%3D98154%26adPlacement%3Dcard-pp1%26cap%3D0%26reset%3D0%26billingTypeId%3D3%26orderId%3D57239%26forceTracker%3D%26gaid%3D8043aad5-507a-428d-a8d5-b09c98a46d68%26gaidOptoutStatus%3D0%26reqTime%3D1664352616%26partnerId%3DDH_APP%26subSlot%3Dpp1_1%26nextAdIndex%3D%26bookedPlacement%3Dcard-p0%26bookedSubSlot%3D%26clientVersions%3D16.0%26os%3Dandroid%26ucq%3Dslow%26resolution%3D1080x2028\",
\"mediaFileURL\":
\"http://video-service-stage.dailyhunt.in/video/a2-ac3e9d10e5a211ecbff9138e63d585e2_l.m3u8\",
\"vastIdentifier\": \"internal-vast\", \"data\": \"IMA-SDK\" },
\"beaconUrlAdditional\": \[ \"http://www.googl.com/imp1\" \],
\"landingUrlAdditional\": \[ \"http://www.googl.com/ck1\" \],
\"landingUrl\": null, \"content\": { \"itemSubtitle2\": { \"color\":
\"#4caf79\", \"color-night\": \"#ffffff\" }, \"itemTag\": { \"color\":
\"#757575\", \"color-night\": \"#ffffff\", \"data\": \"Promoted\" },
\"reportText\": { \"color\": \"#FFFFFF\", \"color-night\": \"#FFFFFF\",
\"background-color\": \"#40000000\", \"background-color-night\":
\"#40000000\", \"data\": \"Ad\" }, \"thumbnailImageUrl\":
\"http://stage-ads2.dailyhunt.in/daedalus-banners/1679957612/1654524737_56651_990x505.jpg\",
\"learnMoreText\": { \"color\": \"#ffffff\", \"color-night\":
\"#ffffff\", \"data\": \"Learn More\" } }, \"brand\": { \"brandTitle\":
{ \"color\": \"#202020\", \"color-night\": \"#ffffff\", \"data\":
\"Test\" }, \"brandSubTitle\": { \"color\": \"#202020\",
\"color-night\": \"#ffffff\" }, \"brandFallbackText\": { \"color\":
\"#ffffff\", \"color-night\": \"#ffffff\", \"background-color\":
\"#ebab05\", \"background-color-night\": \"#ebab05\", \"type\": \"S\",
\"data\": \"T\" } }, \"action\":
\"https://stage-ads2.dailyhunt.in/click?clientId=54800012&uniqueId=203db4c71fe4d20449c6b467d92dcaa1&adId=1679957612&campaignId=98154&adPlacement=card-pp1&reqTime=1664352616&billingTypeId=3&orderId=57239&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-p0&bookedSubSlot=&contentId=&contentCreatorId=&\_\_oadest=http%3A%2F%2Fwww.google.com\",
\"adRespondedBeaconUrl\":
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=203db4c71fe4d20449c6b467d92dcaa1&adId=1679957612&campaignId=98154&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=54800012&reqTime=1664352616&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-p0&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adInflatedBeaconUrl\":
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=203db4c71fe4d20449c6b467d92dcaa1&adId=1679957612&campaignId=98154&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=54800012&reqTime=1664352616&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-p0&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adContextRules\": { \"selectionPriority\": 2, \"cacheType\":
\"persist\", \"ttl\": 432000, \"ruleGroup\": { \"rules\": \[\],
\"respondedFor\": { \"entityIds\": \[\], \"postId\": null } } },
\"adFeedback\": { \"feedbackUrl\": null }, \"requestUrl\":
\"http://stage-ads2.dailyhunt.in/fallback?clientid=54800012&req_time=28092022+13%3A40%3A16&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=none&user_handset_model=none&user_id=&placement=card-pp1&user_app_ver=16.0&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-p0&banner_id=1679957612&campaign_id=98154&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=1028&price_range=none&user_device_type=none&title=vdo+2&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=203db4c71fe4d20449c6b467d92dcaa1&region=&mcc=&mnc=&lac=&cellid=&ip=127.0.0.1&adGroupId=548000126334016f6ad689.69226231&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=0.01&audienceSegments=none&resolution=1080x2028&hostalias=VER-BLR-LT2817&locationSource=&pincode=&subSlot=pp1_1&bookedSubSlot=&ab=ECPM&partnerId=DH_APP&deliverySlab=1&userDeliverySlab=&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=0.01&utmSource=&utmMedium=&utmCampaign=&appId=&autoPlayPref=3&installDeliverySlab=&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=1&topCampaignIds=&topCampaignECPMs=&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=&campaignPrdictedCtr=&productIds=&recoPolicy=&request_timestamp=1664352616&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=&variantName=&modelUuid=&networkSwitch=&topDirectCampaign=&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=&campaign_type=LINEAR&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=&requestIdDebug=96d5bb06a70dcc6a22e41e5d24d2dbde&gender=&age=&ageRange=&orderTypeV2=0&idfa=&s2sBidId=&imputationType=&amazonSdkPayload=&contentCreatorId=&scoringModel=&filteringModel=&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1664352616&\",
\"shareability\": null, \"adLPTimeSpentBeaconUrl\":
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=203db4c71fe4d20449c6b467d92dcaa1&adId=1679957612&campaignId=98154&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=54800012&reqTime=1664352616&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-p0&bookedSubSlot=&contentId=&contentCreatorId=\"
} \], \"UPDATE\": \[ { \"id\": \"409f0cc72d8823bbb505f9e7cae1b764\",
\"priority\": 6998, \"startepoch\": 1654626600, \"endepoch\": 1664359823
} \], \"DELETE\": \[ { \"id\": \"409f0cc72d8823bbb505f9e7cae1b764\" } \]
} }, \"supplement\": { \"sp5\": { \"ADD\": \[ { \"type\":
\"native-banner\", \"aduid\": \"notId=ad-1965750258\", \"srcUrlExpiry\":
\"60\", \"width\": \"1080\", \"height\": \"550.90909090909\",
\"card-position\": 1, \"positionWithTicker\": 1, \"min-ad-distance\": 4,
\"banner-fill\": \"fill-width\", \"bannerid\": \"1510006294\",
\"adTemplate\": \"L_R\", \"showOnlyImage\": \"false\", \"id\":
\"82d6a7658a6eb855ec9546954bbb8f58\", \"span\": 60,
\"useInternalBrowser\": \"false\", \"useWideViewPort\": \"true\",
\"adCacheGood\": \"1\", \"adCacheAverage\": \"1\", \"adCacheSlow\":
\"1\", \"allowDelayedAdInsert\": \"true\", \"adGroupId\":
\"548000126334016f6c1a29.83271429\", \"adContext\": null,
\"showPlayIcon\": \"false\", \"dedupId\":
\"82d6a7658a6eb855ec9546954bbb8f58\", \"adTagPosition\": \"TOP_RIGHT\",
\"showBorder\": false, \"campaignId\": \"1510006294\", \"impFcap\": {
\"cap\": \"3\", \"resetTime\": 2592000 }, \"priority\": 6999,
\"startepoch\": 1654626600, \"endepoch\": 1664359823, \"adCategory\":
\"PRIMARY\", \"passthrough\": { \"ch\": \"\", \"bh\": \"\" },
\"isLargeAd\": false, \"errorUrl\":
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=82d6a7658a6eb855ec9546954bbb8f58&adId=1965750258&campaignId=1510006294&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=54800012&reqTime=1664352616&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=supplement&bookedSubSlot=&contentId=&contentCreatorId=\",
\"largeAdDistance\": 8, \"position\": \"card-p0\", \"beaconUrl\":
\"http://stage-ads2.dailyhunt.in/impression?uniqueId=82d6a7658a6eb855ec9546954bbb8f58&adId=1965750258&campaignId=1510006294&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=54800012&reqTime=1664352616&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=supplement&bookedSubSlot=&contentId=&contentCreatorId=\",
\"landingUrl\": null, \"content\": { \"bg-color\": \"#ffffff\",
\"bg-color-night\": \"#000000\", \"language\": \"en\",
\"sourceAlphabet\": \"A\", \"iconLink\":
\"http://stage-ads2.dailyhunt.in/daedalus-banners/1965750258/1654686465_47656_300x300.gif\",
\"itemTitle\": { \"color\": \"#000000\", \"color-night\": \"#ffffff\" },
\"itemSubtitle1\": { \"color\": \"#000000\", \"color-night\":
\"#ffffff\", \"data\": \"DESC\" }, \"itemSubtitle2\": { \"color\":
\"#4caf79\", \"color-night\": \"#ffffff\", \"data\": \"TEXT\" },
\"itemTag\": { \"color\": \"#757575\", \"color-night\": \"#ffffff\",
\"data\": \"Promoted\" }, \"reportText\": { \"color\": \"#999999\",
\"color-night\": \"#FFFFFF\", \"background-color\": \"#40000000\",
\"background-color-night\": \"#40000000\", \"data\": \"Ad\" } },
\"action\":
\"https://stage-ads2.dailyhunt.in/click?clientId=54800012&uniqueId=82d6a7658a6eb855ec9546954bbb8f58&adId=1965750258&campaignId=1510006294&adPlacement=card-pp1&reqTime=1664352616&billingTypeId=3&orderId=57239&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=supplement&bookedSubSlot=&contentId=&contentCreatorId=&\_\_oadest=http%3A%2F%2Fwww.google.com%3FdhExtras%3D\--DH_EXTRAS\--%26dhPayload%3D\--DH_PAYLOAD\--%26dhxClickId%3D\--DHX_CLICK_ID\--\",
\"adLPTimeSpentBeaconUrl\":
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=82d6a7658a6eb855ec9546954bbb8f58&adId=1965750258&campaignId=1510006294&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=54800012&reqTime=1664352616&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=supplement&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adRespondedBeaconUrl\":
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=82d6a7658a6eb855ec9546954bbb8f58&adId=1965750258&campaignId=1510006294&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=54800012&reqTime=1664352616&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=supplement&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adInflatedBeaconUrl\":
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=82d6a7658a6eb855ec9546954bbb8f58&adId=1965750258&campaignId=1510006294&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=54800012&reqTime=1664352616&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=supplement&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adContextRules\": { \"selectionPriority\": 2, \"cacheType\":
\"session\", \"ttl\": 300, \"ruleGroup\": { \"rules\": \[\],
\"respondedFor\": { \"entityIds\": \[\], \"postId\": null } } },
\"adFeedback\": { \"feedbackUrl\": null }, \"requestUrl\":
\"http://stage-ads2.dailyhunt.in/fallback?clientid=54800012&req_time=28092022+13%3A40%3A16&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=none&user_handset_model=none&user_id=&placement=card-pp1&user_app_ver=16.0&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=supplement&banner_id=1965750258&campaign_id=1510006294&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=1028&price_range=none&user_device_type=none&title=native+list&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=82d6a7658a6eb855ec9546954bbb8f58&region=&mcc=&mnc=&lac=&cellid=&ip=127.0.0.1&adGroupId=548000126334016f6c1a29.83271429&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=0.01&audienceSegments=none&resolution=1080x2028&hostalias=VER-BLR-LT2817&locationSource=&pincode=&subSlot=pp1_1&bookedSubSlot=&ab=ECPM&partnerId=DH_APP&deliverySlab=1&userDeliverySlab=&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=0.01&utmSource=&utmMedium=&utmCampaign=&appId=&autoPlayPref=3&installDeliverySlab=&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=1&topCampaignIds=&topCampaignECPMs=&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=&campaignPrdictedCtr=&productIds=&recoPolicy=&request_timestamp=1664352616&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=&variantName=&modelUuid=&networkSwitch=&topDirectCampaign=&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=&campaign_type=LINEAR&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=96d5bb06a70dcc6a22e41e5d24d2dbde&gender=&age=&ageRange=&orderTypeV2=0&idfa=&s2sBidId=&imputationType=&amazonSdkPayload=&contentCreatorId=&scoringModel=&filteringModel=&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1664352616&\",
\"beaconUrlAdditional\": \[ \"http://www.google.com/imp1\",
\"http://www.google.com/imp2\" \], \"landingUrlAdditional\": \[
\"http://www.google.com/clk1\" \], \"shareability\": null }, { \"type\":
\"external-sdk\", \"aduid\": \"notId=ad-88745\", \"srcUrlExpiry\":
\"86400\", \"adGroupId\": \"548000126334016f6ccfc4.19392040\",
\"width\": \"1080\", \"height\": \"540\", \"card-position\": 4,
\"positionWithTicker\": 4, \"min-ad-distance\": 4, \"banner-fill\":
\"fill-width\", \"bannerid\": \"62112\", \"sdk-order\": 1,
\"adTemplate\": \"H\", \"id\": \"229774c0d4a61e3533d98f160112925e\",
\"span\": 60, \"useInternalBrowser\": \"true\", \"showAutoPlayToggle\":
\"true\", \"adCacheGood\": \"1\", \"adCacheAverage\": \"1\",
\"adCacheSlow\": \"1\", \"allowDelayedAdInsert\": \"true\",
\"showOnlyImage\": \"false\", \"adContext\": null, \"needsBackupAds\":
\"false\", \"adTagPosition\": \"TOP_RIGHT\", \"showBorder\": false,
\"containerBackgroundColor\": \"#f8f7f5\", \"campaignId\": \"62112\",
\"priority\": 5999, \"startepoch\": 1512671400, \"endepoch\":
1664359823, \"adCategory\": \"PRIMARY\", \"passthrough\": { \"ch\":
\"\", \"bh\": \"\" }, \"isLargeAd\": false, \"errorUrl\":
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=229774c0d4a61e3533d98f160112925e&adId=88745&campaignId=62112&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=54800012&reqTime=1664352616&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=supplement&bookedSubSlot=&contentId=&contentCreatorId=\",
\"largeAdDistance\": 8, \"position\": \"card-p0\", \"beaconUrl\":
\"http://stage-ads2.dailyhunt.in/impression?uniqueId=229774c0d4a61e3533d98f160112925e&adId=88745&campaignId=62112&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=54800012&reqTime=1664352616&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=supplement&bookedSubSlot=&contentId=&contentCreatorId=\",
\"landingUrl\":
\"https://stage-ads2.dailyhunt.in/click?clientId=54800012&uniqueId=229774c0d4a61e3533d98f160112925e&adId=88745&campaignId=62112&adPlacement=card-pp1&reqTime=1664352616&billingTypeId=3&orderId=-2&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=supplement&bookedSubSlot=&contentId=&contentCreatorId=&\_\_oadest=\",
\"external\": { \"adsizes\": \[ \"336x280\" \], \"adunitid\":
\"/83414793/DFP_Banner_Supplement\", \"extras\":
\"c_language:en,c_ecpm:10,c_userIp:127.0.0.1,clientId:54800012,c_uniqueId:\--AD_UNIQUE_ID\--,c_city:\--LOCATION_CITY\--,topicKey:NULL,npKey:NULL,c_connectionSpeed:SLOW,ConnectionType:4G,c_placementId:\--AD_PLACEMENT\--,Autoplay:3\",
\"data\": \"DFP-Native\" }, \"action\": null,
\"adLPTimeSpentBeaconUrl\":
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=229774c0d4a61e3533d98f160112925e&adId=88745&campaignId=62112&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=54800012&reqTime=1664352616&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=supplement&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adRespondedBeaconUrl\":
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=229774c0d4a61e3533d98f160112925e&adId=88745&campaignId=62112&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=54800012&reqTime=1664352616&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=supplement&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adInflatedBeaconUrl\":
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=229774c0d4a61e3533d98f160112925e&adId=88745&campaignId=62112&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=54800012&reqTime=1664352616&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=supplement&bookedSubSlot=&contentId=&contentCreatorId=\",
\"customVideoTrackers\": { \"adVideoStart\":
\"http://stage-ads2.dailyhunt.in/vastevent?action=start&clientId=54800012&uniqueId=229774c0d4a61e3533d98f160112925e&adId=88745&campaignId=62112&adPlacement=card-pp1&reqTime=1664352616&partnerId=DH_APP&subSlot=pp1_1&bookedPlacement=supplement&bookedSubSlot=\",
\"adVideoEnd\":
\"http://stage-ads2.dailyhunt.in/vastevent?action=complete&clientId=54800012&uniqueId=229774c0d4a61e3533d98f160112925e&adId=88745&campaignId=62112&adPlacement=card-pp1&reqTime=1664352616&partnerId=DH_APP&subSlot=pp1_1&bookedPlacement=supplement&bookedSubSlot=\",
\"adVideoPause\":
\"http://stage-ads2.dailyhunt.in/vastevent?action=pause&clientId=54800012&uniqueId=229774c0d4a61e3533d98f160112925e&adId=88745&campaignId=62112&adPlacement=card-pp1&reqTime=1664352616&partnerId=DH_APP&subSlot=pp1_1&bookedPlacement=supplement&bookedSubSlot=\",
\"adVideoPlay\":
\"http://stage-ads2.dailyhunt.in/vastevent?action=resume&clientId=54800012&uniqueId=229774c0d4a61e3533d98f160112925e&adId=88745&campaignId=62112&adPlacement=card-pp1&reqTime=1664352616&partnerId=DH_APP&subSlot=pp1_1&bookedPlacement=supplement&bookedSubSlot=\",
\"adVideoMute\":
\"http://stage-ads2.dailyhunt.in/vastevent?action=mute&clientId=54800012&uniqueId=229774c0d4a61e3533d98f160112925e&adId=88745&campaignId=62112&adPlacement=card-pp1&reqTime=1664352616&partnerId=DH_APP&subSlot=pp1_1&bookedPlacement=supplement&bookedSubSlot=\",
\"adVideoUnMute\":
\"http://stage-ads2.dailyhunt.in/vastevent?action=unmute&clientId=54800012&uniqueId=229774c0d4a61e3533d98f160112925e&adId=88745&campaignId=62112&adPlacement=card-pp1&reqTime=1664352616&partnerId=DH_APP&subSlot=pp1_1&bookedPlacement=supplement&bookedSubSlot=\"
}, \"adContextRules\": { \"selectionPriority\": 2, \"cacheType\":
\"session\", \"ttl\": 300, \"ruleGroup\": { \"rules\": \[\],
\"respondedFor\": { \"entityIds\": \[\], \"postId\": null } } },
\"content\": { \"sourceAlphabet\": \"G\", \"itemSubtitle2\": {
\"color\": \"#4caf79\", \"color-night\": \"#ffffff\" }, \"itemTag\": {
\"color\": \"#757575\", \"color-night\": \"#ffffff\", \"data\":
\"Promoted\" }, \"reportText\": { \"color\": \"#999999\",
\"color-night\": \"#FFFFFF\", \"background-color\": \"#40000000\",
\"background-color-night\": \"#40000000\", \"data\": \"Ad\" } },
\"requestUrl\":
\"http://stage-ads2.dailyhunt.in/fallback?clientid=54800012&req_time=28092022+13%3A40%3A16&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=none&user_handset_model=none&user_id=&placement=card-pp1&user_app_ver=16.0&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=supplement&banner_id=88745&campaign_id=62112&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=1028&price_range=none&user_device_type=none&title=DFP_Banner_Supplement++&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=229774c0d4a61e3533d98f160112925e&region=&mcc=&mnc=&lac=&cellid=&ip=127.0.0.1&adGroupId=548000126334016f6ccfc4.19392040&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=0&audienceSegments=none&resolution=1080x2028&hostalias=VER-BLR-LT2817&locationSource=&pincode=&subSlot=pp1_1&bookedSubSlot=&ab=ECPM&partnerId=DH_APP&deliverySlab=1&userDeliverySlab=&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=&articleId=&vpod=&v_ecpm=0&utmSource=&utmMedium=&utmCampaign=&appId=&autoPlayPref=3&installDeliverySlab=&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=1&topCampaignIds=&topCampaignECPMs=&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=&campaignPrdictedCtr=&productIds=&recoPolicy=&request_timestamp=1664352616&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=&variantName=&modelUuid=&networkSwitch=&topDirectCampaign=&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=&campaign_type=ADX&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=96d5bb06a70dcc6a22e41e5d24d2dbde&gender=&age=&ageRange=&orderTypeV2=2&idfa=&s2sBidId=&imputationType=&amazonSdkPayload=&contentCreatorId=&scoringModel=&filteringModel=&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1664352616&\",
\"shareability\": null } \], \"UPDATE\": \[\], \"DELETE\": \[\] } } },
\"beacons\": { \"cacheRefreshReceivedBeaconUrls\": { \"internal\": \[
\"http://api.adengine.com/beaconEvents?crUniqueId=abcd1234&clientId=722000&eventType=CACHE_REFRESH_RECEIVED\"
\] } } }

[Update Mock
Api](https://qa-money.newshunt.com/daedalus-banners/adengine_mock/release_20.1.x/update_mock.json)

UPDATE operationjson{ \"config\": { \"firstImpressionTimeoutMs\": 500,
\"impressionTimeoutMs\": 3500, \"foreground\": { \"refresh\": {
\"intervalSecs\": 300, \"consumptionBased\": true,
\"remainingAdsBased\": true, \"zoneWiseConfig\": { \"card-p0\": {
\"DEFAULT\": { \"prefetchAssets\": 4, \"thresholdAdCount\": { \"used\":
3, \"remainingPrimary\": 2 } } } } } }, \"background\": { \"refresh\": {
\"intervalSecs\": 3600, \"zoneWiseConfig\": { \"card-p0\": {
\"DEFAULT\": { \"prefetchAssets\": 4 } } } } } }, \"ads\": {
\"card-p0\": { \"DEFAULT\": { \"update\": \[ { \"id\":
\"409f0cc72d8823bbb505f9e7cae1b764\", \"priority\": 5004, \"endepoch\":
\"1664905285\" }, { \"id\": \"9e77a7ca03d6f75895825c9cdca2d8dc\",
\"priority\": 4000, \"endepoch\": \"1664905285\" } \] } } },
\"beacons\": { \"cacheRefreshReceivedBeaconUrls\": { \"internal\": \[
\"http://api.adengine.com/beaconEvents?crUniqueId=abcd1234&clientId=722000&eventType=CACHE_REFRESH_RECEIVED\"
\] } } }

[Delete Mock
Api](https://qa-money.newshunt.com/daedalus-banners/adengine_mock/release_20.1.x/delete_mock.json)

DELETE operationjson{ \"config\": { \"firstImpressionTimeoutMs\": 500,
\"impressionTimeoutMs\": 3500, \"foreground\": { \"refresh\": {
\"intervalSecs\": 300, \"consumptionBased\": true,
\"remainingAdsBased\": true, \"zoneWiseConfig\": { \"card-p0\": {
\"DEFAULT\": { \"prefetchAssets\": 4, \"thresholdAdCount\": { \"used\":
3, \"remainingPrimary\": 2 } } } } } }, \"background\": { \"refresh\": {
\"intervalSecs\": 3600, \"zoneWiseConfig\": { \"card-p0\": {
\"DEFAULT\": { \"prefetchAssets\": 4 } } } } } }, \"ads\": {
\"card-p0\": { \"DEFAULT\": { \"delete\": \[ { \"id\":
\"409f0cc72d8823bbb505f9e7cae1b764\" } \] } } }, \"beacons\": {
\"cacheRefreshReceivedBeaconUrls\": { \"internal\": \[
\"http://api.adengine.com/beaconEvents?crUniqueId=abcd1234&clientId=722000&eventType=CACHE_REFRESH_RECEIVED\"
\] } } }

Handshake changes

Handshake Changesjson{ \"cacheRefreshEndpointFG\":
\"http://qa-money.newshunt.com/api/v2/cacheRefresh?urlSource=handshake\",
\"cacheRefreshEndpointBG\":
\"http://qa-money.newshunt.com/api/v2/cacheRefresh?urlSource=handshake\",
\"premiumAdvertisementUrl\":
\"http://qa-money.newshunt.com/api/v2/getAds?urlSource=handshake\",
\"advertisementUrl\":
\"http://qa-money.newshunt.com/api/v2/getAds?urlSource=handshake\",
\"appsOnDeviceUrl\":
\"http://qa-money.newshunt.com/api/v2/userProfile/dhDdc?urlSource=handshake\",
\"hsRefreshIntervalSec\": 1800, \"cacheRefreshErrorUrls\": {
\"internal\": \[
\"http://localhost/beaconEvents?urlSource=handshake&eventType=CACHE_REFRESH_ERROR\"
\] }, \"errorCodes\": { \"NO_INTERNET\": 1001, \"AD_LOAD_TIMEOUT\":
1002, \"AD_LOAD_ERROR\": 1003, \"AD_NO_VAST_TAG_URL\": 1004,
\"MALFORMED_CLICK_URL\": 1005, \"INSTREAM_NO_SKIP\": 1006,
\"OUTSTREAM_SKIP\": 1007 }, \"emptyAd\": { \"id\":
\"42a951682d7d34c2d04c518509719b98\", \"type\": \"empty\", \"position\":
\"storypage\", \"impressionUrls\": { \"internal\": \[
\"http://api.adengine.com/impression?uniqueId=42a951682d7d34c2d04c518509719b98&adId=53495&campaignId=-2&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1663583940&partnerId=DH_APP&subSlot=pp1_5&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_5&contentId=&contentCreatorId=\"
\] }, \"requestUrls\": { \"internal\": \[
\"http://api.adengine.com/fallback?clientid=548000&req_time=19092022+16%3A09%3A00&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=none&user_handset_model=none&user_id=&placement=card-pp1&user_app_ver=16.1.1.1&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-pp1&banner_id=53495&campaign_id=-2&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=481&price_range=none&user_device_type=none&title=Empty+Banner&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=42a951682d7d34c2d04c518509719b98&region=&mcc=&mnc=&lac=&cellid=&ip=127.0.0.1&adGroupId=548000632846c69c34a8.25901597&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=0&audienceSegments=none&resolution=1080x2028&hostalias=VER-BLR-LT2816&locationSource=&pincode=&subSlot=pp1_5&bookedSubSlot=pp1_5&ab=ECPM&partnerId=DH_APP&deliverySlab=1&userDeliverySlab=&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=&articleId=&vpod=&v_ecpm=0&utmSource=&utmMedium=&utmCampaign=&appId=&autoPlayPref=3&installDeliverySlab=&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=1&topCampaignIds=&topCampaignECPMs=&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=&campaignPrdictedCtr=&productIds=&recoPolicy=&request_timestamp=1663583940&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=&variantName=&modelUuid=&networkSwitch=&topDirectCampaign=&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=&campaign_type=&campaign_level=&interleaved_competition=&isRollUp=&requestIdDebug=016e1960e845f2325c0e63030079c1a0&gender=&age=&ageRange=&orderTypeV2=1&idfa=&s2sBidId=&imputationType=&amazonSdkPayload=&contentCreatorId=&scoringModel=&filteringModel=&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1663583940&\"
\] }, \"adInflatedBeaconUrls\": { \"internal\": \[
\"http://api.adengine.com/beaconEvents?uniqueId=42a951682d7d34c2d04c518509719b98&adId=53495&campaignId=-2&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1663583940&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_5&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_5&contentId=&contentCreatorId=\"
\] }, \"adRespondedBeaconUrls\": { \"internal\": \[
\"http://api.adengine.com/beaconEvents?uniqueId=42a951682d7d34c2d04c518509719b98&adId=53495&campaignId=-2&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1663583940&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_5&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_5&contentId=&contentCreatorId=\"
\] } } }

# Instrumentation

Please refer this sheet -\
[https://docs.google.com/spreadsheets/d/1jt-ir-WRwsTnMM9Dek-q-1wJ60Y0h4kKkEdy_ltASQc/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1jt-ir-WRwsTnMM9Dek-q-1wJ60Y0h4kKkEdy_ltASQc/edit?usp=sharing){card-appearance="inline"}

# Ads Cluster - Scaling

## Escort Message Based Scaling

Based on the Scheduled Notifications, the Notification backend will send
an Escort Message to the Ads BE before `x` seconds. This message will
also include the information about the user base for whom the
Notification is being dispatched along with the estimated user reach.

[Start with: 15 mins]{.underline}

Based on the estimated user reach and current run rate of the Ads
cluster (`no_of_requests_on_LB / no_of_active_instances`), the cluster
will be scheduled to scale appropriately. This scaling might take around
2 mins for all the instances to turn healthy.

Since the Cloud Run based service will handle all the BG refreshes, it
would be sufficient enough to scale the Cloud Run cluster alone.

# Ads Cluster - Failover

The foreground Ads Cluster will follow the below failover order -

1.  Main Serving Cluster

2.  BG Serving Cloud Run based Cluster

3.  Static Serving Cloud Storage based Response

4.  `304 Not Modified`

### Cloud Storage Based

The Cache Primer will generate a static response with the generically
targeted campaigns that can be delivered to all the users. This static
response will include contextually targeted campaigns for Ads Cache 2.0
supported App versions and non-contextually targeted campaigns for
Evergreen supported App versions.

Based on certain user criteria, let's say users who last visited the App
5 days ago, Ads BE can decide to divert the BG refresh for such users to
the cloud storage. This change in the endpoint can be relayed to such
users either via Ads Handshake or Notification payload.

note

**Note**

1.  The Ads in the static response will not go through any realtime
    targeting evaluation.

    1.  For the Ads Caching 2.0 supported App versions, the context
        targeting will be evaluated at the App. So, BE can respond with
        context targeted Ads even without evaluating the context
        targeting.

    2.  For Evergreen Ads supported App versions, the context targeting
        will NOT be evaluated at the App. So, BE will only respond with
        non-context targeted Ads.

:::: {.panel .conf-macro .output-block style="background-color: rgb(234,230,255);border-color: rgb(153,141,217);border-width: 1.0px;"}
::: {.panelContent style="background-color: rgb(234,230,255);"}
**Note**

1.  The Ads in the static response will not go through any realtime
    targeting evaluation.

    1.  For the Ads Caching 2.0 supported App versions, the context
        targeting will be evaluated at the App. So, BE can respond with
        context targeted Ads even without evaluating the context
        targeting.

    2.  For Evergreen Ads supported App versions, the context targeting
        will NOT be evaluated at the App. So, BE will only respond with
        non-context targeted Ads.
:::
::::

### 304 Not Modified

If the health check on both the backends (Main Backend and Failover
Backend) are not succeeding, the GCP LB will failover to return
`304 Not Modified` header to all the requests until next health check
succeeds on either of the backends.

On getting the `304 Not Modified` header, the App will use the existing
cached Ads until next opportunity or next API hit.

The backends can independently recover and scale without piling up the
requests and load on the cluster.

# Ads Serving - Staggered BG Refreshes

## Refresh Interval

### For Thin Users

We know that the users categorised as the thin users are least active on
the App. We can save the compute resources that is being spent on
delivering the campaigns to be cached for such users by sending out a
higher cache refresh interval. There is no point in keeping such user's
cache actively refreshed when we know that the user doesn't visit the
App often.

We can have a long running remnant campaign as the final PRIMARY Ad with
higher expiry date and also prefetch assets enabled, to address the DAU
gap. Once the user is on the App, the FG path should take over and the
Ads lifecycle should continue.

[Start with: 24 hours]{.underline}

### For Regular Users

It is important to keep the regular users' cache up to date. So the
cache refresh interval for the regular users can be considerably shorter
than that of the thin users.

[Start with: 1 hours]{.underline}

### Recency & Frequency Of The Visit

If the user has been active on our App recently and consistently for
past `x` days, it is important to keep the cache of such user up to
date, as the user is more likely to use the App again.

[Start with: 1 hours]{.underline}

## Silent Notification

### Staggered Pre-caching

In case of as scheduled notification, the Ads BE will receive the user
base info and also estimated reach from the notification BE. To handle
the upcoming notification traffic, the Ads BE can send out a silent
notification to the same set of user bases (chunked to smaller user
bases using various filters like language, last visited date, app
version, etc) that are dispatched in a staggered manner within `x`
seconds.

This will enable all the users, for whom the notification was scheduled,
to already refresh the cache (if required) and not bombard the Ads BE
endpoint with the `/cacheRefresh` calls.

We can also stagger the backends that handle the cache refreshes based
on certain user criteria (ex: thin users BG refresh can always go to
static file based response). The user bases that the Ads BE is creating
to deliver the Silent Notifications will have to account for sending out
varied endpoints for different user bases.

### Delay Background Refreshes

The Silent Notifications can also be leveraged to push the BG refreshes
away for certain time interval, if there is any load identified on the
backends. This will allow the backends to scale and recover
independently.

If there is a need to disengage the delay applied on the cache refresh,
the Ads BE can send out another Silent Notification (to the same user
bases preferably) to refresh the cache if the existing cache is older
than `x` seconds. The `x` here can also be staggered and also be based
on certain user criteria.

# Exclusive-only BG Cache Response

This is an Ads backend side setting that can be turned ON to respond
with only Exclusive Campaigns for the background cache refreshes. This
will reduce the load on the Ranking Service as the Ranking Service
doesn't have to compute the scores for non-exclusive campaigns.

# Production Configurations & Defaults

+----------------+----------------+----------------+------------------------------------------------------------------------------------------------------+
| **Config**     | **Details**    | **Control      | **Default Value**                                                                                    |
|                |                | Through**      |                                                                                                      |
+----------------+----------------+----------------+------------------------------------------------------------------------------------------------------+
| BG             | Endpoint for   | Preload, Ads   | https://bg.money.dailyhunt.in/api/v2/cacheRefresh                                                    |
| cacheRefresh   | background     | Handshake,     |                                                                                                      |
| endpoint       | cacheRefresh   | Cache          |                                                                                                      |
|                | API calls.     | Response,      |                                                                                                      |
|                |                | Silent         |                                                                                                      |
|                |                | Notification   |                                                                                                      |
+----------------+----------------+----------------+------------------------------------------------------------------------------------------------------+
| FG             | Endpoint for   | Preload, Ads   | [https://money.dailyhunt.in/api/v2/cacheRefresh](https://bg.money.dailyhunt.in/api/v2/cacheRefresh)\ |
| cacheRefresh   | foreground     | Handshake,     |                                                                                                      |
| endpoint       | cacheRefresh   | Cache          |                                                                                                      |
|                | API calls.     | Response,      |                                                                                                      |
|                |                | Silent         |                                                                                                      |
|                |                | Notification   |                                                                                                      |
+----------------+----------------+----------------+------------------------------------------------------------------------------------------------------+
| Single Ad      | Endpoint to    | Preload, Ads   | http://money.dailyhunt.in/api/v2/getAds                                                              |
| fetch endpoint | fetch a single | Handshake      |                                                                                                      |
|                | Ad from the    |                |                                                                                                      |
|                | server.        |                |                                                                                                      |
+----------------+----------------+----------------+------------------------------------------------------------------------------------------------------+
| 1st Ad fetch   | Timeout to     | Preload, Cache | Thin users: 0ms                                                                                      |
| timeout        | fetch a single | Response       |                                                                                                      |
|                | Ad from the    |                | Regular users: 500ms                                                                                 |
|                | server, for    |                |                                                                                                      |
|                | the first time |                |                                                                                                      |
|                | in a day.      |                |                                                                                                      |
+----------------+----------------+----------------+------------------------------------------------------------------------------------------------------+
| Ad fetch       | Timeout to     | Preload, Cache | Thin users: 0ms                                                                                      |
| timeout        | fetch          | Response       |                                                                                                      |
|                | subsequent     |                | Regular users: 2000ms                                                                                |
|                | single Ad from |                |                                                                                                      |
|                | the server.    |                |                                                                                                      |
+----------------+----------------+----------------+------------------------------------------------------------------------------------------------------+
| Asset fetch    | Order of the   | Preload, Cache | storypage, card-p0, card-pp1                                                                         |
| priority zones | zones to       | Response       |                                                                                                      |
|                | prioritise     |                |                                                                                                      |
|                | pre-fetching   |                |                                                                                                      |
|                | assets for.    |                |                                                                                                      |
+----------------+----------------+----------------+------------------------------------------------------------------------------------------------------+
| BG cache       | Cache Refresh  | Preload, Cache | Thin users: 3600s                                                                                    |
| refresh        | interval for   | Response       |                                                                                                      |
| interval       | the background |                | Regular users: 3600s                                                                                 |
|                | refreshes.     |                |                                                                                                      |
+----------------+----------------+----------------+------------------------------------------------------------------------------------------------------+
| FG cache       | Cache Refresh  | Preload, Cache | Thin users: 300ms                                                                                    |
| refresh        | interval for   | Response       |                                                                                                      |
| interval       | the foreground |                | Regular users: 300ms                                                                                 |
|                | refreshes.     |                |                                                                                                      |
+----------------+----------------+----------------+------------------------------------------------------------------------------------------------------+
| Consumption    | Enable/Disable | Preload, Cache | Enabled                                                                                              |
| based cache    | cache refresh  | Response       |                                                                                                      |
| refresh        | calls based on |                |                                                                                                      |
|                | Ads            |                |                                                                                                      |
|                | consumption.   |                |                                                                                                      |
+----------------+----------------+----------------+------------------------------------------------------------------------------------------------------+
| Remaining Ads  | Enable/Disable | Preload, Cache | Enabled                                                                                              |
| based cache    | cache refresh  | Response       |                                                                                                      |
| refresh        | calls based on |                |                                                                                                      |
|                | remaining      |                |                                                                                                      |
|                | primary Ads.   |                |                                                                                                      |
+----------------+----------------+----------------+------------------------------------------------------------------------------------------------------+
| Consumed Ads   | No of Ads      | Cache Response | card-p0=1\                                                                                           |
| threshold      | consumed after |                | card-p1=1\                                                                                           |
|                | which the App  |                | storypage=1\                                                                                         |
|                | makes cache    |                | pp1_1=1\                                                                                             |
|                | refresh call.\ |                | pp1_2=2\                                                                                             |
|                | FG only.       |                | pp1_c1=2\                                                                                            |
|                |                |                | pp1_c2=2\                                                                                            |
|                |                |                | pp1_c3=2\                                                                                            |
|                |                |                | sp1=1\                                                                                               |
|                |                |                | sp2=1\                                                                                               |
|                |                |                | sp3=1\                                                                                               |
|                |                |                | sp4=1\                                                                                               |
|                |                |                | sp5=1\                                                                                               |
|                |                |                | sp6=1\                                                                                               |
|                |                |                | sp7=1\                                                                                               |
|                |                |                | sp8=1\                                                                                               |
|                |                |                | sp9=1\                                                                                               |
|                |                |                | splash=1\                                                                                            |
|                |                |                | splash-exit=1                                                                                        |
+----------------+----------------+----------------+------------------------------------------------------------------------------------------------------+
| Remaining Ads  | No of primary  | Cache Response | card-p0=2\                                                                                           |
| threshold      | Ads remaining  |                | card-p1=2\                                                                                           |
|                | after which    |                | storypage=2\                                                                                         |
|                | the App makes  |                | pp1_1=2\                                                                                             |
|                | cache refresh  |                | pp1_2=2\                                                                                             |
|                | call.\         |                | pp1_c1=2\                                                                                            |
|                | FG only.       |                | pp1_c2=2\                                                                                            |
|                |                |                | pp1_c3=2\                                                                                            |
|                |                |                | sp1=2\                                                                                               |
|                |                |                | sp2=2\                                                                                               |
|                |                |                | sp3=2\                                                                                               |
|                |                |                | sp4=2\                                                                                               |
|                |                |                | sp5=2\                                                                                               |
|                |                |                | sp6=2\                                                                                               |
|                |                |                | sp7=2\                                                                                               |
|                |                |                | sp8=2\                                                                                               |
|                |                |                | sp9=2\                                                                                               |
|                |                |                | splash=1\                                                                                            |
|                |                |                | splash-exit=1                                                                                        |
+----------------+----------------+----------------+------------------------------------------------------------------------------------------------------+
| Cached Ads     | Threshold for  | Ad Server      | BG:                                                                                                  |
| threshold      | number of Ads  |                |                                                                                                      |
|                | to be cached   |                | card-p0=5\                                                                                           |
|                | in the         |                | storypage=5\                                                                                         |
|                | foreground.    |                | pp1_1=5\                                                                                             |
|                |                |                | pp1_2=2                                                                                              |
|                |                |                +------------------------------------------------------------------------------------------------------+
|                |                |                | FG:                                                                                                  |
|                |                |                |                                                                                                      |
|                |                |                | card-p0=5\                                                                                           |
|                |                |                | card-p1=5\                                                                                           |
|                |                |                | storypage=5\                                                                                         |
|                |                |                | pp1_1=5\                                                                                             |
|                |                |                | pp1_2=2\                                                                                             |
|                |                |                | pp1_c1=2\                                                                                            |
|                |                |                | pp1_c2=2\                                                                                            |
|                |                |                | pp1_c3=2\                                                                                            |
|                |                |                | sp1=2\                                                                                               |
|                |                |                | sp2=2\                                                                                               |
|                |                |                | sp3=2\                                                                                               |
|                |                |                | sp4=2\                                                                                               |
|                |                |                | sp5=2\                                                                                               |
|                |                |                | sp6=2\                                                                                               |
|                |                |                | sp7=2\                                                                                               |
|                |                |                | sp8=2\                                                                                               |
|                |                |                | sp9=2\                                                                                               |
|                |                |                | splash=1\                                                                                            |
|                |                |                | splash-exit=1                                                                                        |
+----------------+----------------+----------------+------------------------------------------------------------------------------------------------------+
| Prefetch       | Number of Ads  | Cache Response | BG:                                                                                                  |
| assets count   | to prefetch    |                |                                                                                                      |
|                | the assets     |                | card-p0=2\                                                                                           |
|                | for.           |                | storypage=2\                                                                                         |
|                |                |                | pp1_1=2\                                                                                             |
|                |                |                | pp1_2=1                                                                                              |
|                |                |                +------------------------------------------------------------------------------------------------------+
|                |                |                | FG:                                                                                                  |
|                |                |                |                                                                                                      |
|                |                |                | card-p0=2\                                                                                           |
|                |                |                | card-p1=2\                                                                                           |
|                |                |                | storypage=2\                                                                                         |
|                |                |                | pp1_1=1\                                                                                             |
|                |                |                | pp1_2=1\                                                                                             |
|                |                |                | pp1_c1=1\                                                                                            |
|                |                |                | pp1_c2=1\                                                                                            |
|                |                |                | pp1_c3=1\                                                                                            |
|                |                |                | sp1=1\                                                                                               |
|                |                |                | sp2=1\                                                                                               |
|                |                |                | sp3=1\                                                                                               |
|                |                |                | sp4=1\                                                                                               |
|                |                |                | sp5=1\                                                                                               |
|                |                |                | sp6=1\                                                                                               |
|                |                |                | sp7=1\                                                                                               |
|                |                |                | sp8=1\                                                                                               |
|                |                |                | sp9=1\                                                                                               |
|                |                |                | splash=1\                                                                                            |
|                |                |                | splash-exit=1                                                                                        |
+----------------+----------------+----------------+------------------------------------------------------------------------------------------------------+
| Campaign       | The expiry     | Ad Server      | `min(campaign_expiry, 2 hours)`                                                                      |
| Expiry         | time of the    |                |                                                                                                      |
|                | campaign to    |                |                                                                                                      |
|                | decide whether |                |                                                                                                      |
|                | the campaign   |                |                                                                                                      |
|                | is eligible to |                |                                                                                                      |
|                | render or not. |                |                                                                                                      |
+----------------+----------------+----------------+------------------------------------------------------------------------------------------------------+
| Escort Message | Advance time   | Notification   | 180s                                                                                                 |
| time           | to send the    | BE             |                                                                                                      |
|                | escort         |                |                                                                                                      |
|                | message,       |                |                                                                                                      |
|                | before the     |                |                                                                                                      |
|                | actual         |                |                                                                                                      |
|                | notification   |                |                                                                                                      |
|                | is sent out.   |                |                                                                                                      |
+----------------+----------------+----------------+------------------------------------------------------------------------------------------------------+
| BG cache new   | Interval at    | Ad Server      | Realtime based on any changes on Daedalus.                                                           |
| snapshot       | which the      |                |                                                                                                      |
| creation       | cache snapshot |                |                                                                                                      |
|                | is refreshed   |                |                                                                                                      |
|                | for the        |                |                                                                                                      |
|                | background     |                |                                                                                                      |
|                | path.          |                |                                                                                                      |
+----------------+----------------+----------------+------------------------------------------------------------------------------------------------------+
| CDN cache TTL  | CDN cache TTL. | BG Server      | 120s                                                                                                 |
|                |                | (Cloud Run)    |                                                                                                      |
+----------------+----------------+----------------+------------------------------------------------------------------------------------------------------+
| BG server      | Interval at    | BG Server      | 120s                                                                                                 |
| cache TTL      | which BG       | (Cloud Run)    |                                                                                                      |
|                | server fetches |                |                                                                                                      |
|                | the snapshot   |                |                                                                                                      |
|                | from the       |                |                                                                                                      |
|                | storage and    |                |                                                                                                      |
|                | caches into    |                |                                                                                                      |
|                | local memory.  |                |                                                                                                      |
+----------------+----------------+----------------+------------------------------------------------------------------------------------------------------+

# FAQs

What is the preference order of the cacheRefresh URL?

The cacheRefresh URLs are shared via multiple channels -

1.  Preload

2.  Ads Handshake

3.  Silent Notification

4.  Cache Response

Below is the preference order how the App picks the cacheRefresh URL -

Cache Response → Silent Notification → Ads Handshake → Preload

Are all the zones eligible for Ad replacement, in case higher priority
Ad is available?

No. `card-p0` and `card-pp1` zones are not eligible for Ad replacement.

Are all the zones eligible for background caching?

The capability from the App side to allow caching for all the zones
except `instream-vdo` in the background is provided. But the backend can
control which zones to allow caching in the background.

To start with - `card-p0`, `card-pp1` and `storypage` are enabled for
background caching.

Are all the zones eligible for foreground caching?

Except `instream-vdo`, all the zones are eligible and enabled for
foreground caching.

Does the FG cache refresh override BG cached Ads when the App comes to
the foreground?

Yes. During the App Launch, App will make the cache refresh call
mandatorily, even if the refresh interval has not been reached. The
resulting FG cache response will override the BG cached Ads. No Config
to change this at BE.
