1717

# Overview

This document will details about the Ads caching improvements and
feature additions for the Josh App.

The basic idea is to deal with multiple slot Ads and keep them ready
before the opportunity arises, while keeping the cache fresh and up to
date.

We will also introduce few additional features, like rollup and dedupe,
to aid the prior backend only solutions to happen on the App side owing
to the non-involvement of the BE in the App side Ads utilisation.

# Request-Response Workflow

## Handshake

1.  The App makes a handshake call to the Ads BE.

2.  Ads BE responds with cache related configurations.

3.  The App reads the below configs from the Ads Handshake -

    1.  `cacheRefreshEndpointFG` - API endpoint for foreground cache
        refreshes.

    2.  `cacheRefreshEndpointBG` - API endpoint for background cache
        refreshes.

    3.  `cacheRefreshEndpointFGMethod` - HTTP method to be used for
        foreground cache refreshes.

    4.  `cacheRefreshEndpointBGMethod` - HTTP method to be used for the
        background cache refreshes.

## Caching

1.  Based on the state of the App currently (BG or FG), the App makes a
    cache refresh request using appropriate endpoint.

2.  Ads BE responds with the map of -

    1.  `config` - Contains the configuration about the cache workflow.
        This is detailed in the separate section below.

    2.  `beacons` - Contains the beacons related to the cache refresh as
        a whole. Ad level beacons are inside respective objects as
        before.

    3.  `ads` - Contains a map of -

        1.  `organic` - Contains a list of zone-wise Ad objects to be
            used when the launch is organic.

        2.  `inorganic` - Contains a list of zone-wise Ad objects to be
            used when the launch is inorganic.

3.  The App parses the response and caches the Ads in the following
    hierarchy -\
    `organic/inorganic` → `zone` → `index` → ordered list of Ads based
    on `priority` field.

4.  The App triggers appropriate beacons depending on the status of the
    response parsing.

note

**NOTE**

1.  The App will make all the cache refresh calls in the background.

2.  The App will continue to use the available cache until the next
    successful cache refresh.

3.  The App will make a mandatory cache refresh calls in below scenarios
    -

    1.  On App launch.

    2.  When there are no eligible Ads left in the cache.

:::: {.panel .conf-macro .output-block style="background-color: rgb(234,230,255);border-color: rgb(153,141,217);border-width: 1.0px;"}
::: {.panelContent style="background-color: rgb(234,230,255);"}
**NOTE**

1.  The App will make all the cache refresh calls in the background.

2.  The App will continue to use the available cache until the next
    successful cache refresh.

3.  The App will make a mandatory cache refresh calls in below scenarios
    -

    1.  On App launch.

    2.  When there are no eligible Ads left in the cache.
:::
::::

## Assets Prefetch

1.  The App will ready `x` number of Ad assets as per the configuration
    shared in each Ad objects
    `config.zoneWiseConfig.<zone-name>.DEFAULT.prefetchAssets` field.

2.  The App will prefetch the Ad assets if the banner type of the Ad is
    [https://evp.atlassian.net/wiki/spaces/NHADSPLTL/pages/239403009/Josh+Ads+Caching#Prefetch-able-Banners](https://evp.atlassian.net/wiki/spaces/NHADSPLTL/pages/239403009/Josh+Ads+Caching#Prefetch-able-Banners){card-appearance="inline"}.

3.  The App will ignore the prefetch if the banner type of the Ad is
    [https://evp.atlassian.net/wiki/spaces/NHADSPLTL/pages/239403009/Josh+Ads+Caching#Non-Prefetch-able-Banners](https://evp.atlassian.net/wiki/spaces/NHADSPLTL/pages/239403009/Josh+Ads+Caching#Non-Prefetch-able-Banners){card-appearance="inline"}.

4.  Appropriate beacon is hit based on the Ad ready status.

## Background

1.  The background flow will kick-in when the App is not running in the
    foreground. The App might be killed or running in the background.

2.  The App considers below trigger points to trigger the cache refresh
    call -

    1.  Notification delivery

    2.  Scheduled time interval

3.  When the trigger point is hit, the App will check if the
    `config.background.refresh.intervalSecs` has been passed since the
    last successful refresh.

    1.  If No, the App ignores the trigger and does nothing.

    2.  If Yes, the App will make the cache refresh call along with
        appropriate request objects.

4.  Ads BE responds with appropriate cache response.

5.  The flow continues as per
    [https://evp.atlassian.net/wiki/spaces/NHADSPLTL/pages/239403009/Josh+Ads+Caching#Caching-Workflow](https://evp.atlassian.net/wiki/spaces/NHADSPLTL/pages/239403009/Josh+Ads+Caching#Caching-Workflow){card-appearance="inline"}.

## Foreground

1.  The foreground flow will kick-in when the App is opened via
    following sources -

    1.  Notification

    2.  Deeplink

    3.  Organic launch

2.  The App considers below trigger points to trigger the cache refresh
    call -

    1.  App launch

    2.  No. of used Ads

    3.  No. of remaining Ads

    4.  Scheduled time interval

3.  App launch -

    1.  Cache refresh call is made if the previous successful cache
        refresh was from the BG and the
        `config.foreground.refresh.intervalSecs` has been passed.

4.  No. of used Ads -

    1.  Cache refresh call is made if the
        `config.foreground.refresh.consumptionBased` is `true` and

    2.  `config.foreground.zoneWiseConfig.<zone-name>.DEFAULT.thresholdAdCount.used`
        number of Ads used from the respective zone\'s cache.

5.  No. of remaining Ads -

    1.  Cache refresh call is made if the
        `config.foreground.refresh.remainingAdsBased` is `true` and

    2.  `config.foreground.zoneWiseConfig.<zone-name>.DEFAULT.thresholdAdCount.remainingPrimary`
        number of Ads remaining in the respective zone\'s cache.

6.  Scheduled time interval -

    1.  Cache refresh call is made if the last successful cache refresh
        was before `config.foreground.refresh.intervalSecs`.

7.  Ads BE responds with appropriate cache response.

8.  The flow continues as per
    [https://evp.atlassian.net/wiki/spaces/NHADSPLTL/pages/239403009/Josh+Ads+Caching#Caching-Workflow](https://evp.atlassian.net/wiki/spaces/NHADSPLTL/pages/239403009/Josh+Ads+Caching#Caching-Workflow){card-appearance="inline"}.

# Cache Manipulation Workflow

## Cache Reordering

1.  Ads BE will always respond with the delta operations
    (`add`/`update`/`delete`/`deleteAll`).

2.  Most of the times, the Ads that are already cached on the App will
    need to be re-ordered.

3.  In such cases, the `update` object will contain the new `priority`
    value for appropriate Ads.

4.  The App will consider the new updated priorities and re-order the
    cached Ads accordingly.

## Cache Utilisation

1.  On opportunity, the App will parse through the cached Ads and
    selects one eligible Ad to be used.

2.  The App will always look for exact `adTag` Ad.

    1.  If found (empty or non-empty), the App will use that Ad.

    2.  If not found, the App will use the Ad from `DEFAULT` list.

3.  Ads are always validated based on the following rules -

    1.  `endepoch` of the Ad has not yet passed.

    2.  Frequency cap of the Ad has not yet reached.

4.  The App will always give priority to the Ad with higher `priority`
    value. This field is shared in each Ad object.

## Cache Purging

### Ad Validity Based

1.  When the App tries to find an eligible Ad for an opportunity in
    hand, some of the Ads in the cache might turn out to have expired.
    Either because of `endepoch` or frequency cap.

2.  The App will purge such expired Ads immediately from the cache.

### Delete Operation Based

1.  When the App makes a cache refresh call to the Ads BE, Ads BE might
    choose to delete certain cached Ads, based on the campaign delivery
    status.

2.  Cache refresh response will return with appropriate `delete`
    operation for such Ads.

3.  The App will honour the operation and delete appropriate Ads from
    the cache.

## Cache Nuking

1.  When the App makes a cache refresh call to the Ads BE, Ads BE might
    choose to delete all the cached Ads, if it finds the whole cache
    invalid.

2.  Cache refresh response will return with appropriate `deleteAll`
    operation for the whole cache.

3.  The App will honour the operation and delete all the Ads from the
    cache.

# Beacons Workflow

## Cache Response Received

1.  This is triggered when the App successfully parses the response
    received for the cache refresh request made.

2.  Applicable both for BG and FG.

3.  This beacon is shared in the cache response
    `config.beacons.cacheRefreshReceivedBeaconUrls` field.

## Cache Error

1.  This is triggered in the following cases -

    1.  Cache refresh request has timed out.

    2.  The App is not able to parse the response.

2.  Applicable both for BG and FG.

3.  This beacon is shared in the Ads Handshake
    `data.cacheRefreshErrorUrls` field.

4.  The App will attach an object describing the reason for the error
    `CACHE_TIMEOUT` / `CACHE_PARSE_ERROR`.

## Ad Ready

1.  This is triggered when the App makes the Ad assets ready by
    downloading them.

2.  For the
    [https://evp.atlassian.net/wiki/spaces/NHADSPLTL/pages/239403009/Josh+Ads+Caching#Non-Prefetch-able-Banners](https://evp.atlassian.net/wiki/spaces/NHADSPLTL/pages/239403009/Josh+Ads+Caching#Non-Prefetch-able-Banners){card-appearance="inline"}
    banner types, this event is triggered when the view is created and
    the App gets a ready callback from the view.

    1.  These banner types are not readied in the BG path.

3.  Applicable both for BG and FG.

4.  This beacon is shared in the respective Ad objects
    `adReadyBeaconUrls` field.

## Ad Dropped

1.  This is triggered when the Ad in the cache is discarded/dropped
    because of -

    1.  `endepoch` has been crossed. Which means the Ad has expired.

    2.  Frequency cap of the Ad has been reached.

2.  Applicable only for FG.

3.  This beacon is shared in the respective Ad objects
    `adDroppedBeaconUrls` field.

## Ad Request

1.  This is triggered when the Ad is being picked from the App to be
    inflated.

2.  For -

    1.  [https://evp.atlassian.net/wiki/spaces/NHADSPLTL/pages/239403009/Josh+Ads+Caching#Prefetch-able-Banners](https://evp.atlassian.net/wiki/spaces/NHADSPLTL/pages/239403009/Josh+Ads+Caching#Prefetch-able-Banners){card-appearance="inline"}
        banner types, this event is ideally triggered after the Ad Ready
        event.

    2.  [https://evp.atlassian.net/wiki/spaces/NHADSPLTL/pages/239403009/Josh+Ads+Caching#Non-Prefetch-able-Banners](https://evp.atlassian.net/wiki/spaces/NHADSPLTL/pages/239403009/Josh+Ads+Caching#Non-Prefetch-able-Banners){card-appearance="inline"}
        banner types, this event is ideally triggered before the Ad
        Ready event, because the Ad Ready only happens after the Ad is
        picked and inflated.

3.  Applicable only for FG.

4.  This beacon is shared in the respective Ad objects `requestUrls`
    field.

## Ad Error

1.  This is triggered when -

    1.  Ad request to the SDK failed.

    2.  Ad being responded has issues in rendering.

    3.  Any SDK side error.

    4.  Ad assets failed to download.

2.  Applicable for BG and FG.

3.  This beacon is shared in the respective Ad objects `errorUrls`
    field.

## Ad Inflated

1.  This is triggered when the Ad is rendered/inflated into the view.

2.  Applicable only for FG.

3.  This beacon is shared in the respective Ad objects
    `adInflatedBeaconUrls` field.

note

**NOTE**

1.  All other beacons will remain as it is.

2.  All the `internal` beacons should be always **POST**.

3.  All the `external` beacons should be always **GET**.

4.  `adResponded` beacon to be dropped from this release onwards, as we
    are not planning on the single Ad request call.

:::: {.panel .conf-macro .output-block style="background-color: rgb(234,230,255);border-color: rgb(153,141,217);border-width: 1.0px;"}
::: {.panelContent style="background-color: rgb(234,230,255);"}
**NOTE**

1.  All other beacons will remain as it is.

2.  All the `internal` beacons should be always **POST**.

3.  All the `external` beacons should be always **GET**.

4.  `adResponded` beacon to be dropped from this release onwards, as we
    are not planning on the single Ad request call.
:::
::::

# Beacons Batching

1.  All the beacons triggered by the App are eligible to be batched.

2.  Ads BE will append `dhBatch=<batch_name>` GET query param in the
    beacon URLs that are to be batched.

3.  The App creates distinct batches based on the `<batch_name` value
    and categorises appropriate beacons into these batches.

4.  Ads BE would have shared below config in the Ads handshake -

    json\"batchConfig\": { \"batchId\": \"bAds1\", \"batchUrl\":
    \"http://money.dailyhunt.in/api/v2/batchBeaconEvents\",
    \"batchThresholdSize\": \"20\", \"batchThresholdTimeSecs\": \"30\" }

5.  Based on the `batchThresholdSize` and `batchThresholdTimeSecs`, the
    App will trigger the batch API `batchUrl` along with the payload of
    all the beacons that are batched.

6.  When the user exits the App, if there were any batched beacons, the
    App will persist them until the next App launch.

7.  On the next App launch, the App will trigger the batch API with the
    persisted batched beacons and flush the batch.

# Passthrough Params

1.  Every Ad object carries a JSON field called `passThrough`.

2.  This object need to be passed as it is in all the beacons, as a POST
    param `passThrough`.

# Feature Additions

## Rollup Logic

> Any way to avoid server side rollup?
>
> Instead, can we have a `collapse=true` field in the empty banner and
> collapse the slot and rollup the next slot at the App side?

## Dedupe Logic

Since the App is responsible to utilise the cached Ads until the next
successful cache refresh, Ads BE will not have any control over
deduplicating the Ads that are getting rendered.

So, the App will take care of deduplicating the Ads that are chosen to
be rendered. Below are the steps -

1.  Ads BE will add 2 new fields in every Ad object -

    1.  `dedupeKey` - Identifier to deduplicate the Ad.

    2.  `dedupeDistance` - Number of Ads after which this Ad becomes
        eligible to be rendered again.

2.  Before picking an Ad from the cache, the App will check the dedupe
    configuration of that Ad.

    1.  If there was an Ad with the same dedupe key rendered within last
        Ad's `dedupeDistance` number of Ad slots, the App will ignore
        that Ad.

    2.  If not, the App will pick the Ad and render it in the Ad slot.

note

**Note**

1.  `dedupeDistance` is always for the next repetition of the Ad.

2.  It should not be used for deciding the eligibility of current Ad.\
    Ex:\
    `Ad1` has the `dedupeKey=d123` and `dedupeDistance=3`\
    `Ad2` has the `dedupeKey=d123` and `dedupeDistance=1`\
    `Ad3` has the `dedupeKey=d123` and `dedupeDistance=5`\
    \
    Let's say these are the only Ads in the cache.\
    In this case,\
    `slot1` `Ad1`\
    `slot2` `empty`\
    `slot3` `empty`\
    `slot4` `empty`\
    `slot5` `Ad2` // based on Ad1's `dedupeDistance=3`\
    `slot6` `empty`\
    `slot7` `Ad3` // based on Ad2's `dedupeDistance=1`

:::: {.panel .conf-macro .output-block style="background-color: rgb(234,230,255);border-color: rgb(153,141,217);border-width: 1.0px;"}
::: {.panelContent style="background-color: rgb(234,230,255);"}
**Note**

1.  `dedupeDistance` is always for the next repetition of the Ad.

2.  It should not be used for deciding the eligibility of current Ad.\
    Ex:\
    `Ad1` has the `dedupeKey=d123` and `dedupeDistance=3`\
    `Ad2` has the `dedupeKey=d123` and `dedupeDistance=1`\
    `Ad3` has the `dedupeKey=d123` and `dedupeDistance=5`\
    \
    Let's say these are the only Ads in the cache.\
    In this case,\
    `slot1` `Ad1`\
    `slot2` `empty`\
    `slot3` `empty`\
    `slot4` `empty`\
    `slot5` `Ad2` // based on Ad1's `dedupeDistance=3`\
    `slot6` `empty`\
    `slot7` `Ad3` // based on Ad2's `dedupeDistance=1`
:::
::::

## Beacons Array

1.  From this App version onwards, Ads BE will send all the beacons as
    the map of array of string.

2.  The map contains 2 keys -

    1.  `internal` - These are the DH internal beacons. These will
        always be via POST method. The App will append appropriate
        objects to all of these beacons, in the POST body.

    2.  `external` - These are external 3rd party beacons. These will
        always be GET method. The App should NOT append any internal
        objects or params to these beacons.

3.  Examples -\

    json\"requestUrls\": { \"internal\": \[
    \"http://money.dailyhunt.in/fallback?clientid=1233391736&req_time=08112022+16%3A54%3A16&request_timestamp=1667906656&paper=dh270e11982dfa46bb8c2f9b6c27103d59&Gpscountry=india&confidence=0.4&user_os_platform=android&user_handset_maker=realme&user_handset_model=rmx1921&user_id=dh19035fc9363d4c0783a98982a50f2ee2&placement=supplement&user_app_ver=20.1.26&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=supplement&banner_id=377062&campaign_id=94875&user_connection=w&connection_speed=AVERAGE&user_os_ver=11.0&encGaid=MTc3ZGNlN2ItZmQxZi00MTA3LWFiNTAtMDcyZTdiMDQzNTA0&user_languages=en&oi=778&price_range=mid&user_device_type=none&title=One+India+supplement+native&latitude=NA&longitude=NA&uniqueId=d965c71dd7a128c9d4d6ab3e7711bf22&ip=10.52.134.4&adGroupId=1233391736636a3c609e1fd0.70275059&topicId=91581308b67fdfbcd24028a0c513bc37&ecpm=1&audienceSegments=2+6+583+588+595+572+573+1909+2014+2078+2097+2003+2166+607+108+111+100+101+104+105+11+10+13+12+14+l&resolution=1080x2132&hostalias=dh-gcp-ads-adengine-ws-az-vmd9&locationSource=IP&subSlot=sp2&bookedSubSlot=sp2&ab=ECPM&partnerId=DH_APP&deliverySlab=1&userDeliverySlab=0&pubName=DH&nthImpression=2&articleId=n439683054&v_ecpm=1&autoPlayPref=3&optimisedBy=1&topCampaignIds=94875%5E&topCampaignECPMs=1&entityId=91581308b67fdfbcd24028a0c513bc37&entityType=HASHTAG&sourceType=OGC&mastheadAdCount=0&sessionSource=ORGANIC&totalAdSessions=1&totalSeenAds=7&totalSessions=5&contentId=n439683054&event_type=AD_REQUEST&preCalibratedProbability=0&networkSwitch=NONE&topDirectCampaign=94875&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=0&campaign_type=SPONSORED&campaign_level=LEVEL_1&requestIdDebug=39766cfbd04060f3a5b424a7f2404c77&gender=M&age=33&ageRange=3&orderTypeV2=1&s2sBidId=3ee416c049e570b6e2a551678b0a55ed&scoringModel=dynamic_meta&filteringModel=dynamic_meta&requestData=%7B%22products%22%3A%5B%5D%7D&isRegUser=1&hostAppId=DH_APP&userBadge=2&reqTime=1667906656&\"
    \] }

    json\"impressionUrls\": { \"internal\": \[
    \"http://money.dailyhunt.in/impression?eventType=AD_IMP&subSlot=sp2&adPlacement=supplement&uniqueId=a02960f672c33ac944ca0c30f2e4d859\"
    \], \"external\": \[
    \"http://example.external.com/imp?k=v123&cb=845r87ter87yr\" \] }

# Object Signatures

## Cache Refresh Request Object

**Field Name:** `refreshInfo`

**Object Signature:**

json{ \"id\": \"vdsf8u4eufheduifh94er4\", \"source\":
\"SCHEDULED\|ADS_USED\|ADS_REMAINING\|APP_LAUNCH\|NOTIFICATION_DELIVERY\|APP_WAKE_UP\",
\"appState\": \"FG\|BG\", \"triggerPlacement\": \"list-ad\",
\"timestamp\": 1425744000000 }

## Cache Snapshot Object

Cached Ad Info Object will have the zone wise ads present in the cache.

**Field Name:** `cachedAdsInfo`

**Object Signature:**

json\"organic\": { \"list-ad\": { \"DEFAULT\": \[ { \"id\":
\"409f0cc72d8823bbb505f9e7cae1b764\", \"campaignId\": \"1024\",
\"bannerId\": \"2094\", \"passThrough\": { \"ch\":
\"eoirewr8uew8rueoicfnoweiur9\", \"bh\":
\"32094u9302874983uyfoidsjflkc\" }, \"priority\": 5006, \"endepoch\":
\"1664905285\", \"isReady\": true }, { \"id\":
\"409f0cc72d8823bbb505f9e7cae1b765\", \"campaignId\": \"1024\",
\"bannerId\": \"2094\", \"passThrough\": { \"ch\":
\"eoirewr8uew8rueoicfnoweiur9\", \"bh\":
\"32094u9302874983uyfoidsjflkc\" }, \"priority\": 5004, \"endepoch\":
\"1664905285\", \"isReady\": false } \], \"-1\": \[ { \"id\":
\"409f0cc72d8823bbb505f9e7cae1b764\", \"campaignId\": \"1024\",
\"bannerId\": \"2094\", \"passThrough\": { \"ch\":
\"eoirewr8uew8rueoicfnoweiur9\", \"bh\":
\"32094u9302874983uyfoidsjflkc\" }, \"priority\": 5006, \"endepoch\":
\"1664905285\", \"isReady\": true } \] } }

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
\"density\" : \"\<DENSITY\>\", \"isNightMode\" : true/false,
\"muteState\" : true/false }

## Ad Instance Info Object

Definition for the values can be referred
[here](https://evp.atlassian.net/wiki/spaces/NHADSPLTL/pages/109609309/Evergreen+Ads+-+Protocol+V1#Macro-Definition).

**Field Name:** `adInstanceInfo`

**Object Signature:**

json{ \"uniqueId\" : \"\<UUID\>\", \"adPlacement\":
\"\<AD_PLACEMENT\>\", \"subslot\" : \"\<SUB_SLOT\>\", \"reqTime\" :
\"\<TIMESTAMP\>\" }

# Protocol Samples

Sample 1json{ \"config\": { \"foreground\": { \"refresh\": {
\"consumptionBased\": true, \"remainingAdsBased\": true, \"url\":
\"http://qa-money.newshunt.com/api/v2/cacheRefresh\", \"intervalSecs\":
300 }, \"zoneWiseConfig\": { \"list-ad\": { \"DEFAULT\": {
\"prefetchAssets\": 1, \"thresholdAdCount\": { \"used\": 1,
\"remainingPrimary\": 2 } } } } }, \"background\": { \"refresh\": {
\"url\": \"https://bg.qa-money.newshunt.com/api/v2/cacheRefresh\",
\"intervalSecs\": 31104000 }, \"zoneWiseConfig\": { \"list-ad\": {
\"DEFAULT\": { \"prefetchAssets\": 1, \"thresholdAdCount\": { \"used\":
1, \"remainingPrimary\": 2 } } } } } }, \"ads\": { \"organic\": {
\"list-ad\": { \"DEFAULT\": { \"add\": \[ { \"type\": \"external-sdk\",
\"position\": \"list-ad\", \"campaignId\": \"1247\", \"bannerId\":
\"3818\", \"id\": \"b8bbbfaa61dc5811897a3be47488542d\", \"endepoch\":
\"1670478608\", \"priority\": 5001, \"span\": 0, \"passThrough\": {
\"ch\": \"eoirewr8uew8rueoicfnoweiur9\", \"bh\":
\"32094u9302874983uyfoidsjflkc\" }, \"useInternalBrowser\": \"true\",
\"useWideViewPort\": true, \"beaconUrl\":
\"https://qa-money.coolfie.io/impression?eventType=AD_IMP&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API&impType=DISPLAY_IMP\",
\"adRespondedBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_RESPONDED&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adInflatedBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_INFLATED&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"landingUrlAdditional\": \[\], \"content\": { \"itemSubtitle2\": {
\"data\": \"external v click\", \"color\": \"#ffffff\", \"bg-color\":
\"#ff65d1e8\", \"isAnimated\": true, \"animationConfig\": {
\"initialButtonColor\": \"#660a1cf0\", \"finalButtonColor\":
\"#fffa390d\", \"initialTextColor\": \"#ffffff\", \"finalTextColor\":
\"#c5ff14\", \"startTime\": \"2000\", \"endTime\": \"3000\" },
\"dimension\": { \"margin\": \"16\", \"fontSize\": \"14\", \"fontType\":
\"REGULAR\" }, \"isPopupView\": false }, \"itemTag\": { \"color\":
\"#0889ac\", \"color-night\": \"#a5a5a5\", \"data\": \"Sponsored\" },
\"id\": \"295710e4-395e-4b6a-b4a7-238da439a006\" }, \"action\":
\"https://qa-money.coolfie.io/click?clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&adPlacement=list-ad&reqTime=1670476112&billingTypeId=3&orderId=238&city=bengaluru&state=karnataka&country=india&partnerId=JOSH_APP&subSlot=-1&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API&\_\_oadest=https%3A%2F%2Famazon.in\",
\"adFeedback\": { \"feedbackUrl\":
\"https://qa-money.coolfie.io/data-api/adfeedback?bannerId=3818&campaignId=1247&uniqueId=b8bbbfaa61dc5811897a3be47488542d&city=bengaluru\"
}, \"omTrackType\": \"none\", \"omVendorsInfo\": null, \"errorUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_ERROR&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"brandId\": \"14\", \"removeTitle\": true, \"adGroupId\":
\"c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A6391715012ec99.49691788\",
\"adCommentBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_COMMENT&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adLikeBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_LIKE&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adTimeSpentBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_TIME_SPENT&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adShareBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_SHARED&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adLPTimeSpentBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_LP_TIME_SPENT&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adDislikeBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_DISLIKE&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"brandFollowBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=BRAND_FOLLOW&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"brandUnfollowBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=BRAND_UNFOLLOW&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adClosedBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_CLOSE&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adTag\": \"DEFAULT\", \"external\": { \"tagURL\":
\"https%3A%2F%2Fqa-money.coolfie.io%2Fgetvast%3FclientId%3Dc.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A%26uniqueId%3Db8bbbfaa61dc5811897a3be47488542d%26adId%3D3818%26campaignId%3D1247%26adPlacement%3Dlist-ad%26cap%3D0%26reset%3D0%26billingTypeId%3D3%26orderId%3D238%26forceTracker%3D%26gaid%3D4134237e-2c77-45d6-a387-10ca1ad1abe1%26gaidOptoutStatus%3D0%26reqTime%3D1670476112%26partnerId%3DJOSH_APP%26subSlot%3D-1%26nextAdIndex%3D-1%2C-2%26bookedPlacement%3Dlist-ad%26bookedSubSlot%3D-1%26clientVersions%3D7.4.5.2210031611.2%26os%3Dandroid%26ucq%3Dfast\",
\"data\": \"IMA-SDK\", \"mediaFileURL\":
\"https://qa-stream.myjosh.in/stream/qa-josh-content/f0a1e02c11b57dd2/f1d7298e8821703d/f0a1e02c11b57dd2f1d7298e8821703d_good_auto_s5.m3u8\",
\"prefetchPercentageAds\": 30 } }, { \"type\": \"external-sdk\",
\"position\": \"list-ad\", \"campaignId\": \"1247\", \"bannerId\":
\"3818\", \"id\": \"65e1529bab3b5e52f325dc9ab01e7c69\", \"endepoch\":
\"1670478608\", \"priority\": 5000, \"span\": 0, \"passThrough\": {
\"ch\": \"eoirewr8uew8rueoicfnoweiur9\", \"bh\":
\"32094u9302874983uyfoidsjflkc\" }, \"useInternalBrowser\": \"true\",
\"useWideViewPort\": true, \"beaconUrl\":
\"https://qa-money.coolfie.io/impression?eventType=AD_IMP&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API&impType=DISPLAY_IMP\",
\"adRespondedBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_RESPONDED&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adInflatedBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_INFLATED&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"landingUrlAdditional\": \[\], \"content\": { \"itemSubtitle2\": {
\"data\": \"external v click\", \"color\": \"#ffffff\", \"bg-color\":
\"#ff65d1e8\", \"isAnimated\": true, \"animationConfig\": {
\"initialButtonColor\": \"#660a1cf0\", \"finalButtonColor\":
\"#fffa390d\", \"initialTextColor\": \"#ffffff\", \"finalTextColor\":
\"#c5ff14\", \"startTime\": \"2000\", \"endTime\": \"3000\" },
\"dimension\": { \"margin\": \"16\", \"fontSize\": \"14\", \"fontType\":
\"REGULAR\" }, \"isPopupView\": false }, \"itemTag\": { \"color\":
\"#0889ac\", \"color-night\": \"#a5a5a5\", \"data\": \"Sponsored\" },
\"id\": \"295710e4-395e-4b6a-b4a7-238da439a006\" }, \"action\":
\"https://qa-money.coolfie.io/click?clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&adPlacement=list-ad&reqTime=1670476112&billingTypeId=3&orderId=238&city=bengaluru&state=karnataka&country=india&partnerId=JOSH_APP&subSlot=-2&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API&\_\_oadest=https%3A%2F%2Famazon.in\",
\"adFeedback\": { \"feedbackUrl\":
\"https://qa-money.coolfie.io/data-api/adfeedback?bannerId=3818&campaignId=1247&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&city=bengaluru\"
}, \"omTrackType\": \"none\", \"omVendorsInfo\": null, \"errorUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_ERROR&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"brandId\": \"14\", \"removeTitle\": true, \"adGroupId\":
\"c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A63917150146f31.61697939\",
\"adCommentBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_COMMENT&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adLikeBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_LIKE&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adTimeSpentBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_TIME_SPENT&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adShareBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_SHARED&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adLPTimeSpentBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_LP_TIME_SPENT&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adDislikeBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_DISLIKE&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"brandFollowBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=BRAND_FOLLOW&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"brandUnfollowBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=BRAND_UNFOLLOW&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adClosedBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_CLOSE&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adTag\": \"DEFAULT\", \"external\": { \"tagURL\":
\"https%3A%2F%2Fqa-money.coolfie.io%2Fgetvast%3FclientId%3Dc.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A%26uniqueId%3D65e1529bab3b5e52f325dc9ab01e7c69%26adId%3D3818%26campaignId%3D1247%26adPlacement%3Dlist-ad%26cap%3D0%26reset%3D0%26billingTypeId%3D3%26orderId%3D238%26forceTracker%3D%26gaid%3D4134237e-2c77-45d6-a387-10ca1ad1abe1%26gaidOptoutStatus%3D0%26reqTime%3D1670476112%26partnerId%3DJOSH_APP%26subSlot%3D-2%26nextAdIndex%3D-1%2C-2%26bookedPlacement%3Dlist-ad%26bookedSubSlot%3D-2%26clientVersions%3D7.4.5.2210031611.2%26os%3Dandroid%26ucq%3Dfast\",
\"data\": \"IMA-SDK\", \"mediaFileURL\":
\"https://qa-stream.myjosh.in/stream/qa-josh-content/f0a1e02c11b57dd2/f1d7298e8821703d/f0a1e02c11b57dd2f1d7298e8821703d_good_auto_s5.m3u8\",
\"prefetchPercentageAds\": 30 } } \] }, \"-1\": { \"add\": \[ {
\"type\": \"external-sdk\", \"position\": \"list-ad\", \"campaignId\":
\"1247\", \"bannerId\": \"3818\", \"id\":
\"b8bbbfaa61dc5811897a3be47488542d\", \"endepoch\": \"1670478608\",
\"priority\": 5001, \"span\": 0, \"passThrough\": { \"ch\":
\"eoirewr8uew8rueoicfnoweiur9\", \"bh\":
\"32094u9302874983uyfoidsjflkc\" }, \"useInternalBrowser\": \"true\",
\"useWideViewPort\": true, \"beaconUrl\":
\"https://qa-money.coolfie.io/impression?eventType=AD_IMP&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API&impType=DISPLAY_IMP\",
\"adRespondedBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_RESPONDED&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adInflatedBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_INFLATED&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"landingUrlAdditional\": \[\], \"content\": { \"itemSubtitle2\": {
\"data\": \"external v click\", \"color\": \"#ffffff\", \"bg-color\":
\"#ff65d1e8\", \"isAnimated\": true, \"animationConfig\": {
\"initialButtonColor\": \"#660a1cf0\", \"finalButtonColor\":
\"#fffa390d\", \"initialTextColor\": \"#ffffff\", \"finalTextColor\":
\"#c5ff14\", \"startTime\": \"2000\", \"endTime\": \"3000\" },
\"dimension\": { \"margin\": \"16\", \"fontSize\": \"14\", \"fontType\":
\"REGULAR\" }, \"isPopupView\": false }, \"itemTag\": { \"color\":
\"#0889ac\", \"color-night\": \"#a5a5a5\", \"data\": \"Sponsored\" },
\"id\": \"295710e4-395e-4b6a-b4a7-238da439a006\" }, \"action\":
\"https://qa-money.coolfie.io/click?clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&adPlacement=list-ad&reqTime=1670476112&billingTypeId=3&orderId=238&city=bengaluru&state=karnataka&country=india&partnerId=JOSH_APP&subSlot=-1&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API&\_\_oadest=https%3A%2F%2Famazon.in\",
\"adFeedback\": { \"feedbackUrl\":
\"https://qa-money.coolfie.io/data-api/adfeedback?bannerId=3818&campaignId=1247&uniqueId=b8bbbfaa61dc5811897a3be47488542d&city=bengaluru\"
}, \"omTrackType\": \"none\", \"omVendorsInfo\": null, \"errorUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_ERROR&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"brandId\": \"14\", \"removeTitle\": true, \"adGroupId\":
\"c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A6391715012ec99.49691788\",
\"adCommentBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_COMMENT&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adLikeBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_LIKE&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adTimeSpentBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_TIME_SPENT&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adShareBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_SHARED&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adLPTimeSpentBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_LP_TIME_SPENT&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adDislikeBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_DISLIKE&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"brandFollowBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=BRAND_FOLLOW&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"brandUnfollowBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=BRAND_UNFOLLOW&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adClosedBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_CLOSE&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adTag\": \"-1\", \"external\": { \"tagURL\":
\"https%3A%2F%2Fqa-money.coolfie.io%2Fgetvast%3FclientId%3Dc.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A%26uniqueId%3Db8bbbfaa61dc5811897a3be47488542d%26adId%3D3818%26campaignId%3D1247%26adPlacement%3Dlist-ad%26cap%3D0%26reset%3D0%26billingTypeId%3D3%26orderId%3D238%26forceTracker%3D%26gaid%3D4134237e-2c77-45d6-a387-10ca1ad1abe1%26gaidOptoutStatus%3D0%26reqTime%3D1670476112%26partnerId%3DJOSH_APP%26subSlot%3D-1%26nextAdIndex%3D-1%2C-2%26bookedPlacement%3Dlist-ad%26bookedSubSlot%3D-1%26clientVersions%3D7.4.5.2210031611.2%26os%3Dandroid%26ucq%3Dfast\",
\"data\": \"IMA-SDK\", \"mediaFileURL\":
\"https://qa-stream.myjosh.in/stream/qa-josh-content/f0a1e02c11b57dd2/f1d7298e8821703d/f0a1e02c11b57dd2f1d7298e8821703d_good_auto_s5.m3u8\",
\"prefetchPercentageAds\": 30 } }, { \"type\": \"external-sdk\",
\"position\": \"list-ad\", \"campaignId\": \"1247\", \"bannerId\":
\"3818\", \"id\": \"65e1529bab3b5e52f325dc9ab01e7c69\", \"endepoch\":
\"1670478608\", \"priority\": 5000, \"span\": 0, \"passThrough\": {
\"ch\": \"eoirewr8uew8rueoicfnoweiur9\", \"bh\":
\"32094u9302874983uyfoidsjflkc\" }, \"useInternalBrowser\": \"true\",
\"useWideViewPort\": true, \"beaconUrl\":
\"https://qa-money.coolfie.io/impression?eventType=AD_IMP&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API&impType=DISPLAY_IMP\",
\"adRespondedBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_RESPONDED&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adInflatedBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_INFLATED&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"landingUrlAdditional\": \[\], \"content\": { \"itemSubtitle2\": {
\"data\": \"external v click\", \"color\": \"#ffffff\", \"bg-color\":
\"#ff65d1e8\", \"isAnimated\": true, \"animationConfig\": {
\"initialButtonColor\": \"#660a1cf0\", \"finalButtonColor\":
\"#fffa390d\", \"initialTextColor\": \"#ffffff\", \"finalTextColor\":
\"#c5ff14\", \"startTime\": \"2000\", \"endTime\": \"3000\" },
\"dimension\": { \"margin\": \"16\", \"fontSize\": \"14\", \"fontType\":
\"REGULAR\" }, \"isPopupView\": false }, \"itemTag\": { \"color\":
\"#0889ac\", \"color-night\": \"#a5a5a5\", \"data\": \"Sponsored\" },
\"id\": \"295710e4-395e-4b6a-b4a7-238da439a006\" }, \"action\":
\"https://qa-money.coolfie.io/click?clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&adPlacement=list-ad&reqTime=1670476112&billingTypeId=3&orderId=238&city=bengaluru&state=karnataka&country=india&partnerId=JOSH_APP&subSlot=-2&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API&\_\_oadest=https%3A%2F%2Famazon.in\",
\"adFeedback\": { \"feedbackUrl\":
\"https://qa-money.coolfie.io/data-api/adfeedback?bannerId=3818&campaignId=1247&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&city=bengaluru\"
}, \"omTrackType\": \"none\", \"omVendorsInfo\": null, \"errorUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_ERROR&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"brandId\": \"14\", \"removeTitle\": true, \"adGroupId\":
\"c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A63917150146f31.61697939\",
\"adCommentBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_COMMENT&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adLikeBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_LIKE&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adTimeSpentBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_TIME_SPENT&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adShareBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_SHARED&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adLPTimeSpentBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_LP_TIME_SPENT&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adDislikeBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_DISLIKE&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"brandFollowBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=BRAND_FOLLOW&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"brandUnfollowBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=BRAND_UNFOLLOW&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adClosedBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_CLOSE&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adTag\": \"-1\", \"external\": { \"tagURL\":
\"https%3A%2F%2Fqa-money.coolfie.io%2Fgetvast%3FclientId%3Dc.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A%26uniqueId%3D65e1529bab3b5e52f325dc9ab01e7c69%26adId%3D3818%26campaignId%3D1247%26adPlacement%3Dlist-ad%26cap%3D0%26reset%3D0%26billingTypeId%3D3%26orderId%3D238%26forceTracker%3D%26gaid%3D4134237e-2c77-45d6-a387-10ca1ad1abe1%26gaidOptoutStatus%3D0%26reqTime%3D1670476112%26partnerId%3DJOSH_APP%26subSlot%3D-2%26nextAdIndex%3D-1%2C-2%26bookedPlacement%3Dlist-ad%26bookedSubSlot%3D-2%26clientVersions%3D7.4.5.2210031611.2%26os%3Dandroid%26ucq%3Dfast\",
\"data\": \"IMA-SDK\", \"mediaFileURL\":
\"https://qa-stream.myjosh.in/stream/qa-josh-content/f0a1e02c11b57dd2/f1d7298e8821703d/f0a1e02c11b57dd2f1d7298e8821703d_good_auto_s5.m3u8\",
\"prefetchPercentageAds\": 30 } } \] }, \"0\": { \"add\": \[ { \"type\":
\"external-sdk\", \"position\": \"list-ad\", \"campaignId\": \"1247\",
\"bannerId\": \"3818\", \"id\": \"b8bbbfaa61dc5811897a3be47488542d\",
\"endepoch\": \"1670478608\", \"priority\": 5001, \"span\": 0,
\"passThrough\": { \"ch\": \"eoirewr8uew8rueoicfnoweiur9\", \"bh\":
\"32094u9302874983uyfoidsjflkc\" }, \"useInternalBrowser\": \"true\",
\"useWideViewPort\": true, \"beaconUrl\":
\"https://qa-money.coolfie.io/impression?eventType=AD_IMP&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API&impType=DISPLAY_IMP\",
\"adRespondedBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_RESPONDED&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adInflatedBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_INFLATED&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"landingUrlAdditional\": \[\], \"content\": { \"itemSubtitle2\": {
\"data\": \"external v click\", \"color\": \"#ffffff\", \"bg-color\":
\"#ff65d1e8\", \"isAnimated\": true, \"animationConfig\": {
\"initialButtonColor\": \"#660a1cf0\", \"finalButtonColor\":
\"#fffa390d\", \"initialTextColor\": \"#ffffff\", \"finalTextColor\":
\"#c5ff14\", \"startTime\": \"2000\", \"endTime\": \"3000\" },
\"dimension\": { \"margin\": \"16\", \"fontSize\": \"14\", \"fontType\":
\"REGULAR\" }, \"isPopupView\": false }, \"itemTag\": { \"color\":
\"#0889ac\", \"color-night\": \"#a5a5a5\", \"data\": \"Sponsored\" },
\"id\": \"295710e4-395e-4b6a-b4a7-238da439a006\" }, \"action\":
\"https://qa-money.coolfie.io/click?clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&adPlacement=list-ad&reqTime=1670476112&billingTypeId=3&orderId=238&city=bengaluru&state=karnataka&country=india&partnerId=JOSH_APP&subSlot=-1&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API&\_\_oadest=https%3A%2F%2Famazon.in\",
\"adFeedback\": { \"feedbackUrl\":
\"https://qa-money.coolfie.io/data-api/adfeedback?bannerId=3818&campaignId=1247&uniqueId=b8bbbfaa61dc5811897a3be47488542d&city=bengaluru\"
}, \"omTrackType\": \"none\", \"omVendorsInfo\": null, \"errorUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_ERROR&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"brandId\": \"14\", \"removeTitle\": true, \"adGroupId\":
\"c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A6391715012ec99.49691788\",
\"adCommentBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_COMMENT&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adLikeBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_LIKE&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adTimeSpentBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_TIME_SPENT&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adShareBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_SHARED&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adLPTimeSpentBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_LP_TIME_SPENT&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adDislikeBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_DISLIKE&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"brandFollowBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=BRAND_FOLLOW&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"brandUnfollowBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=BRAND_UNFOLLOW&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adClosedBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_CLOSE&subSlot=-1&adPlacement=list-ad&uniqueId=b8bbbfaa61dc5811897a3be47488542d&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-1&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adTag\": \"0\", \"external\": { \"tagURL\":
\"https%3A%2F%2Fqa-money.coolfie.io%2Fgetvast%3FclientId%3Dc.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A%26uniqueId%3Db8bbbfaa61dc5811897a3be47488542d%26adId%3D3818%26campaignId%3D1247%26adPlacement%3Dlist-ad%26cap%3D0%26reset%3D0%26billingTypeId%3D3%26orderId%3D238%26forceTracker%3D%26gaid%3D4134237e-2c77-45d6-a387-10ca1ad1abe1%26gaidOptoutStatus%3D0%26reqTime%3D1670476112%26partnerId%3DJOSH_APP%26subSlot%3D-1%26nextAdIndex%3D-1%2C-2%26bookedPlacement%3Dlist-ad%26bookedSubSlot%3D-1%26clientVersions%3D7.4.5.2210031611.2%26os%3Dandroid%26ucq%3Dfast\",
\"data\": \"IMA-SDK\", \"mediaFileURL\":
\"https://qa-stream.myjosh.in/stream/qa-josh-content/f0a1e02c11b57dd2/f1d7298e8821703d/f0a1e02c11b57dd2f1d7298e8821703d_good_auto_s5.m3u8\",
\"prefetchPercentageAds\": 30 } }, { \"type\": \"external-sdk\",
\"position\": \"list-ad\", \"campaignId\": \"1247\", \"bannerId\":
\"3818\", \"id\": \"65e1529bab3b5e52f325dc9ab01e7c69\", \"endepoch\":
\"1670478608\", \"priority\": 5000, \"span\": 0, \"passThrough\": {
\"ch\": \"eoirewr8uew8rueoicfnoweiur9\", \"bh\":
\"32094u9302874983uyfoidsjflkc\" }, \"useInternalBrowser\": \"true\",
\"useWideViewPort\": true, \"beaconUrl\":
\"https://qa-money.coolfie.io/impression?eventType=AD_IMP&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API&impType=DISPLAY_IMP\",
\"adRespondedBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_RESPONDED&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adInflatedBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_INFLATED&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"landingUrlAdditional\": \[\], \"content\": { \"itemSubtitle2\": {
\"data\": \"external v click\", \"color\": \"#ffffff\", \"bg-color\":
\"#ff65d1e8\", \"isAnimated\": true, \"animationConfig\": {
\"initialButtonColor\": \"#660a1cf0\", \"finalButtonColor\":
\"#fffa390d\", \"initialTextColor\": \"#ffffff\", \"finalTextColor\":
\"#c5ff14\", \"startTime\": \"2000\", \"endTime\": \"3000\" },
\"dimension\": { \"margin\": \"16\", \"fontSize\": \"14\", \"fontType\":
\"REGULAR\" }, \"isPopupView\": false }, \"itemTag\": { \"color\":
\"#0889ac\", \"color-night\": \"#a5a5a5\", \"data\": \"Sponsored\" },
\"id\": \"295710e4-395e-4b6a-b4a7-238da439a006\" }, \"action\":
\"https://qa-money.coolfie.io/click?clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&adPlacement=list-ad&reqTime=1670476112&billingTypeId=3&orderId=238&city=bengaluru&state=karnataka&country=india&partnerId=JOSH_APP&subSlot=-2&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API&\_\_oadest=https%3A%2F%2Famazon.in\",
\"adFeedback\": { \"feedbackUrl\":
\"https://qa-money.coolfie.io/data-api/adfeedback?bannerId=3818&campaignId=1247&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&city=bengaluru\"
}, \"omTrackType\": \"none\", \"omVendorsInfo\": null, \"errorUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_ERROR&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"brandId\": \"14\", \"removeTitle\": true, \"adGroupId\":
\"c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A63917150146f31.61697939\",
\"adCommentBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_COMMENT&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adLikeBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_LIKE&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adTimeSpentBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_TIME_SPENT&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adShareBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_SHARED&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adLPTimeSpentBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_LP_TIME_SPENT&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adDislikeBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_DISLIKE&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"brandFollowBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=BRAND_FOLLOW&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"brandUnfollowBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=BRAND_UNFOLLOW&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adClosedBeaconUrl\":
\"https://qa-money.coolfie.io/beaconEvents?eventType=AD_CLOSE&subSlot=-2&adPlacement=list-ad&uniqueId=65e1529bab3b5e52f325dc9ab01e7c69&adId=3818&campaignId=1247&city=bengaluru&state=karnataka&country=india&clientId=c.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A&reqTime=1670476112&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adTag\": \"0\", \"external\": { \"tagURL\":
\"https%3A%2F%2Fqa-money.coolfie.io%2Fgetvast%3FclientId%3Dc.M0VwcFpRTFhqZm9ACamcwV1dtSDUvZz09A%26uniqueId%3D65e1529bab3b5e52f325dc9ab01e7c69%26adId%3D3818%26campaignId%3D1247%26adPlacement%3Dlist-ad%26cap%3D0%26reset%3D0%26billingTypeId%3D3%26orderId%3D238%26forceTracker%3D%26gaid%3D4134237e-2c77-45d6-a387-10ca1ad1abe1%26gaidOptoutStatus%3D0%26reqTime%3D1670476112%26partnerId%3DJOSH_APP%26subSlot%3D-2%26nextAdIndex%3D-1%2C-2%26bookedPlacement%3Dlist-ad%26bookedSubSlot%3D-2%26clientVersions%3D7.4.5.2210031611.2%26os%3Dandroid%26ucq%3Dfast\",
\"data\": \"IMA-SDK\", \"mediaFileURL\":
\"https://qa-stream.myjosh.in/stream/qa-josh-content/f0a1e02c11b57dd2/f1d7298e8821703d/f0a1e02c11b57dd2f1d7298e8821703d_good_auto_s5.m3u8\",
\"prefetchPercentageAds\": 30 } } \] } } } } }

# FAQs

# References

## Prefetch-able Banners

The banner types for which the assets can be prefetched and downloaded
before the actual opportunity.

This will include -

1.  Image Banners

2.  HTML/MRAID Zip

3.  Video Banners

## Non Prefetch-able Banners

The banner types for which the assets cannot be downloaded beforehand
and only the view creation implicitly fetches the assets.

This will include -

1.  External HTML Banners

2.  SDK Banners
