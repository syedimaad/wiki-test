# Overview

This document details the new protocol between Josh App and Ads Backend.
The main intent of this change is to aid the pre-preparedness of the Ads
before the opportunity while making the design much more simpler.

# App Workflow

## Ads Handshake

1.  Ads BE will share below configurations in the Ads Handshake -

    1.  `advertisementUrl` - Endpoint to request the Ads.

    2.  `cacheControl.maxCachedAds` - Maximum number of Ads to cache on
        the App.

    3.  `cacheControl.minCachedAds` - Minimum number of Ads to cache on
        the App. If the cache counter goes beneath this threshold, the
        App will trigger the Ad request again.

## App Launch

1.  The App will trigger the `advertisementUrl` to fetch the Ads, along
    the `cachedAdsInfo` object.

2.  Ads BE will respond with `x` number of Ads according to their
    delivery priority. Where `x` = `maxCachedAds`.

3.  The order of the Ads in the response will reflect the priority in
    which the Ads will be rendered on the App.

4.  The App will start readying the Ad assets as soon as the Ad cache is
    created. The readying will happen in the same order as the cached
    Ads.

5.  The App will not care about matching the adIndex with the Ad in the
    cache. It just picks an Ad from the top of the cache list to render.

6.  The App will validate the Ad on the following basis -

    1.  Ad's `endepoch` has not yet passed.

    2.  Ad's frequency cap has not yet reached.

    3.  Ad is not deduplicated.

7.  If the top of the cache Ad is not ready (assets are still being
    downloaded), and if next Ad in the list is ready, the App will carry
    on to render the ready Ad.

8.  Once the ready Ad is found, the App will inflate the Ad into the
    slot.

9.  *Rest of the Ad flow remains the same as before.*

note

**Note**

1.  When the App skips a non-ready Ad and proceeds with next ready Ad,
    it will also take care of de-duping the Ad.

:::: {.panel .conf-macro .output-block style="background-color: rgb(234,230,255);border-color: rgb(153,141,217);border-width: 1.0px;"}
::: {.panelContent style="background-color: rgb(234,230,255);"}
**Note**

1.  When the App skips a non-ready Ad and proceeds with next ready Ad,
    it will also take care of de-duping the Ad.
:::
::::

# Ads Deduplication

1.  The Ad object will contain `dedupId` and `dedupDistance`, if
    applicable.

    1.  `dedupId` - Identifier to deduplicate the Ad.

    2.  `dedupDistance` - Number of Ads after which this Ad becomes
        eligible to be rendered again.

2.  Before picking an Ad from the cache, the App will check the dedup
    configuration of that Ad.

    1.  If there was an Ad with the same `dedupId` rendered within last
        `dedupeDistance` number of Ad slots, the App will skip that Ad.

    2.  If not, the App will pick the Ad and render it in the Ad slot.

3.  The order of the list is always maintained.

Ex:\
`Ad1` has the `dedupeKey=d123` and `dedupeDistance=3`\
`Ad2` has the `dedupeKey=d123` and `dedupeDistance=1`\
`Ad3` has the `dedupeKey=d123` and `dedupeDistance=4`\
`Ad4` has the `dedupeKey=d456` and `dedupeDistance=4`\
`Ad5` has the `dedupeKey=d123` and `dedupeDistance=0`

Let's say these are the only Ads in the cache.\
In this case,\
`slot1` `Ad1`\
`slot2` `Ad4` // based on Ad4's non matching dedupId\
`slot3` `Ad2` // based on Ad2's `dedupDistance=1`\
`slot4` `Ad5` // based on Ad5's `dedupDistance=0`\
`slot5` `empty`\
`slot6` `empty`\
`slot7` `empty`\
`slot8` `empty`\
`slot9` `Ad3` // based on Ad3's `dedupeDistance=4`

# Backend Workflow

## Ads Configuration

1.  The way the Ads are configured will remain the same.

2.  We will still continue to target Ads to the premium placements (-1,
    -2, 0, 1, 2).

## Ads Delivery

1.  Ads BE will receive `cacheSnapshot` in every Ad Request. This object
    will contain the current state of the cache.

2.  Ads BE will exclude the Ads that were already cached at the App
    side, and respond with other Ads.

# Object Signatures

## Cache Snapshot Object

Cached Ad Info Object will have the information about the zone wise ads
present in the cache.

**Field Name:** `cachedAdsInfo`

**Object Signature:**

json{ \"list-ad\": \[ { \"id\": \"409f0cc72d8823bbb505f9e7cae1b764\",
\"campaignId\": \"1024\", \"bannerId\": \"2094\", \"passThrough\": {
\"ch\": \"eoirewr8uew8rueoicfnoweiur9\", \"bh\":
\"32094u9302874983uyfoidsjflkc\" }, \"endepoch\": \"1664905285\",
\"isReady\": true }, { \"id\": \"409f0cc72d8823bbb505f9e7cae1b765\",
\"campaignId\": \"1024\", \"bannerId\": \"2094\", \"passThrough\": {
\"ch\": \"eoirewr8uew8rueoicfnoweiur9\", \"bh\":
\"32094u9302874983uyfoidsjflkc\" }, \"endepoch\": \"1664905285\",
\"isReady\": false } \] }

# Protocol Sample

Sample 1json{ \"ads\": \[ { \"type\": \"external-sdk\", \"position\":
\"list-ad\", \"campaignId\": \"1247\", \"bannerId\": \"3818\", \"id\":
\"b8bbbfaa61dc5811897a3be47488542d\", \"endepoch\": \"1670478608\",
\"span\": 0, \"passThrough\": { \"ch\": \"eoirewr8uew8rueoicfnoweiur9\",
\"bh\": \"32094u9302874983uyfoidsjflkc\" }, \"useInternalBrowser\":
\"true\", \"useWideViewPort\": true, \"beaconUrl\":
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
\"1670478608\", \"span\": 0, \"passThrough\": { \"ch\":
\"eoirewr8uew8rueoicfnoweiur9\", \"bh\":
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
\"prefetchPercentageAds\": 30 } } \] }
