## Requirement:

Need sdk banner support for **list-ad** placement.

# AdEngine Changes

- AdEngine Whitelist SDK banner and prepare response.

- Introduce `Google-Native-Interstitial` ENUM inside `external.data`
  field to initialise google ad manager SDK.

- Introduce `adunitid` and `extras`

- Introduce `adVideoStart`, `adVideoEnd`, `adVideoPause`, `adVideoPlay`,
  `adVideoMute`, `adVideoUnMute` inside `customVideoTrackers` for video
  tracking events since SDK may gives video that is not IMA SDK Hence.

- CTA configurability is not needed so itemsubtitle2 json block is not
  needed.

# Handshake Changes

- Introduce SDK timeout. It is in seconds.

- Error code for sdk failure.

json{ \"sdkTimeout\":{ \"adsTimeoutGood\": 3, \"adsTimeoutAverage\": 6,
\"adsTimeoutSlow\":12 }, \"errorCodes\": { \"NO_INTERNET\": 1001,
\"AD_LOAD_TIMEOUT\": 1002, \"AD_LOAD_ERROR\": 1003,
\"AD_NO_VAST_TAG_URL\": 1004, \"MALFORMED_CLICK_URL\": 1005,
\"SDK_AD_FAILED\": 1009 } }

# Client Changes

- Initialise Google Ad Manager SDK only if type is `external-sdk` and
  external.data is `Google-Native-Interstitial`.

- Pass `adunitid` and `extras` to SDK and fetch ad and render ad
  according to FIGMA.

- For SDK video ad, Client need to fire `adVideoStart`, `adVideoEnd`,
  `adVideoPause`, `adVideoPlay`, `adVideoMute`, `adVideoUnMute` inside
  `customVideoTrackers` for video tracking events since IMA SDK is not
  comes into picture.

- When SDK ads click event is triggered client need to trigger
  Adengine's click url(`landingUrl`) along with `landingUrlAdditional`.

- Impression need not to be fired when there is no fill and No need to
  request for next list ad if sdk gives any error.

- Post body of errorUrl should be in below format

  - json{ \"errorCode\": int, \"playerErrorCode\": int,
    \"playerErrorMessage\": string, \"playerErrorType\": string, }

  - errorCode will be the code shared in the handshake `errorCodes`.
    `"SDK_AD_FAILED": 1009`

    - errorCode - error code from handshake response.

    - playerErrorCode - error code from sdk

    - playerErrorMessage - error message from sdk

    - playerErrorType - error type from sdk

  - jsonplayerErrorType { NO_FILL TIMEOUT TYPE_NOT_SUPPORTED }

# DD Changes

- DD need to whitelist SDK banner for josh.

- DD need to allow only `SDK Identifier` as `Google` which is drop down.

- DD Need to allow only `Format Identifer` as `Native-Interstitial`,
  which is also drop down.

- Minimum version compatibility check (7.6).

# Response Protocol

Responsejson{ \"ads\": \[ { \"type\": \"empty\", \"endepoch\":
\"1670977913\", \"position\": \"list-ad\", \"id\":
\"828f02eaf9509625518c77cb718422a8\", \"span\": 0, \"beaconUrl\":
\"http://qa-money.myjosh.in/impression?eventType=AD_IMP&subSlot=-2&adPlacement=list-ad&uniqueId=828f02eaf9509625518c77cb718422a8&adId=80580&campaignId=-2&country=india&clientId=8f7702c0-f5f8&reqTime=1670329856&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"postId\": \"\", \"adTag\": \"-2\", \"adGroupId\":
\"8f7702c0-f5f8638f3600cbed07.91590387\" }, { \"type\": \"carousel\",
\"endepoch\": \"1670977913\", \"position\": \"list-ad\", \"campaignId\":
\"1021834156\", \"bannerId\": \"1358733094\", \"id\":
\"1c4e7a97440c394a8f1113d5f731e9fb\", \"span\": 5, \"useWideViewPort\":
true, \"beaconUrl\":
\"http://qa-money.myjosh.in/impression?eventType=AD_IMP&subSlot=-2&adPlacement=list-ad&uniqueId=1c4e7a97440c394a8f1113d5f731e9fb&adId=1358733094&campaignId=1021834156&city=bengaluru&state=karnataka&country=india&clientId=8f7702c0-f5f8&reqTime=1670573644&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adRespondedBeaconUrl\":
\"http://qa-money.myjosh.in/beaconEvents?eventType=AD_RESPONDED&subSlot=-2&adPlacement=list-ad&uniqueId=1c4e7a97440c394a8f1113d5f731e9fb&adId=1358733094&campaignId=1021834156&city=bengaluru&state=karnataka&country=india&clientId=8f7702c0-f5f8&reqTime=1670573644&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adInflatedBeaconUrl\":
\"http://qa-money.myjosh.in/beaconEvents?eventType=AD_INFLATED&subSlot=-2&adPlacement=list-ad&uniqueId=1c4e7a97440c394a8f1113d5f731e9fb&adId=1358733094&campaignId=1021834156&city=bengaluru&state=karnataka&country=india&clientId=8f7702c0-f5f8&reqTime=1670573644&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"content\": { \"id\": \"ca7de432-a7ad-4161-9d63-ec6213df639d\",
\"items\": \[ { \"itemSubtitle2\": { \"itemTitle\": \"Item Title \*1\",
\"data\": \"Install App\", \"color\": \"#000000\", \"bg-color\":
\"#FFffffff\", \"isAnimated\": true, \"animationConfig\": {
\"initialButtonColor\": \"#66ffffff\", \"finalButtonColor\":
\"#FFea4e60\", \"initialTextColor\": \"#ffffff\", \"finalTextColor\":
\"#ffffff\", \"startTime\": \"2000\", \"endTime\": \"3000\" },
\"dimension\": { \"margin\": \"16\", \"fontSize\": \"14\", \"fontType\":
\"BOLD\" }, \"isPopupView\": false }, \"itemTag\": { \"color\":
\"#0889ac\", \"color-night\": \"#a5a5a5\", \"data\": \"Promoted\" },
\"ctaOnlyClick\": true, \"itemImage\": { \"data\":
\"http://qa-money.myjosh.in/daedalus-banners/1358733094/1667906202_49099_1080x2592.jpg\"
}, \"carouselItemViewUrl\":
\"http://qa-money.myjosh.in/beaconEvents?uniqueId=1c4e7a97440c394a8f1113d5f731e9fb_1&adId=1358733094&campaignId=1021834156&subBannerId=1755791617&adPlacement=list-ad&city=bengaluru&state=karnataka&country=india&clientId=8f7702c0-f5f8&reqTime=1670573644&itemIndex=1&parentUniqueId=1c4e7a97440c394a8f1113d5f731e9fb&eventType=CAROUSEL_ITEM_VIEW&partnerId=JOSH_APP&subSlot=-2&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2\",
\"action\":
\"https://qa-money.myjosh.in/click?clientId=8f7702c0-f5f8&uniqueId=1c4e7a97440c394a8f1113d5f731e9fb&adId=1358733094&campaignId=1021834156&adPlacement=list-ad&reqTime=1670573644&billingTypeId=3&orderId=116&city=bengaluru&state=karnataka&country=india&subBannerId=1755791617&partnerId=JOSH_APP&subSlot=-2&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API&\_\_oadest=https%253A%252F%252Fwww.google.com%253Fagerange%253D%26gender%3D\",
\"carouselItemClickUrl\":
\"http://qa-money.myjosh.in/beaconEvents?uniqueId=1c4e7a97440c394a8f1113d5f731e9fb_1&adId=1358733094&campaignId=1021834156&subBannerId=1755791617&adPlacement=list-ad&city=bengaluru&state=karnataka&country=india&clientId=8f7702c0-f5f8&reqTime=1670573644&itemIndex=1&parentUniqueId=1c4e7a97440c394a8f1113d5f731e9fb&eventType=CAROUSEL_ITEM_CLICK&partnerId=JOSH_APP&subSlot=-2&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2\",
\"carouselItemTimeSpentUrl\":
\"http://qa-money.myjosh.in/beaconEvents?uniqueId=1c4e7a97440c394a8f1113d5f731e9fb_1&adId=1358733094&campaignId=1021834156&subBannerId=1755791617&adPlacement=list-ad&city=bengaluru&state=karnataka&country=india&clientId=8f7702c0-f5f8&reqTime=1670573644&itemIndex=1&parentUniqueId=1c4e7a97440c394a8f1113d5f731e9fb&eventType=CAROUSEL_ITEM_TIME_SPENT&partnerId=JOSH_APP&subSlot=-2&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2\",
\"carouselItemLPTimeSpentUrl\":
\"http://qa-money.myjosh.in/beaconEvents?uniqueId=1c4e7a97440c394a8f1113d5f731e9fb_1&adId=1358733094&campaignId=1021834156&subBannerId=1755791617&adPlacement=list-ad&city=bengaluru&state=karnataka&country=india&clientId=8f7702c0-f5f8&reqTime=1670573644&itemIndex=1&parentUniqueId=1c4e7a97440c394a8f1113d5f731e9fb&eventType=CAROUSEL_ITEM_LP_TIME_SPENT&partnerId=JOSH_APP&subSlot=-2&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2\",
\"useInternalBrowser\": \"false\", \"landingUrlAdditional\": \[
\"http://click3.com\" \], \"shareability\": { \"text\": \"Share Text
\*1\", \"subject\": \"Share Subject \*2\", \"image\":
\"http://qa-money.myjosh.in/daedalus-banners/1358733094/1667906202_97480_300x300.jpg\"
} }, { \"itemSubtitle2\": { \"itemTitle\": \"Item Title \*\", \"data\":
\"Participate Now\", \"color\": \"#000000\", \"bg-color\":
\"#FFffffff\", \"isAnimated\": true, \"animationConfig\": {
\"initialButtonColor\": \"#66ffffff\", \"finalButtonColor\":
\"#FFea4e60\", \"initialTextColor\": \"#ffffff\", \"finalTextColor\":
\"#ffffff\", \"startTime\": \"2000\", \"endTime\": \"3000\" },
\"dimension\": { \"margin\": \"16\", \"fontSize\": \"14\", \"fontType\":
\"BOLD\" }, \"isPopupView\": false }, \"itemTag\": { \"color\":
\"#0889ac\", \"color-night\": \"#a5a5a5\", \"data\": \"Promoted\" },
\"ctaOnlyClick\": true, \"itemImage\": { \"data\":
\"http://qa-money.myjosh.in/daedalus-banners/1358733094/1667907052_28208_1080x2592.jpg\"
}, \"carouselItemViewUrl\":
\"http://qa-money.myjosh.in/beaconEvents?uniqueId=1c4e7a97440c394a8f1113d5f731e9fb_2&adId=1358733094&campaignId=1021834156&subBannerId=1606502233&adPlacement=list-ad&city=bengaluru&state=karnataka&country=india&clientId=8f7702c0-f5f8&reqTime=1670573644&itemIndex=2&parentUniqueId=1c4e7a97440c394a8f1113d5f731e9fb&eventType=CAROUSEL_ITEM_VIEW&partnerId=JOSH_APP&subSlot=-2&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2\",
\"action\":
\"https://qa-money.myjosh.in/click?clientId=8f7702c0-f5f8&uniqueId=1c4e7a97440c394a8f1113d5f731e9fb&adId=1358733094&campaignId=1021834156&adPlacement=list-ad&reqTime=1670573644&billingTypeId=3&orderId=116&city=bengaluru&state=karnataka&country=india&subBannerId=1606502233&partnerId=JOSH_APP&subSlot=-2&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API&\_\_oadest=https%3A%2F%2Fwww.google.com%2F\",
\"carouselItemClickUrl\":
\"http://qa-money.myjosh.in/beaconEvents?uniqueId=1c4e7a97440c394a8f1113d5f731e9fb_2&adId=1358733094&campaignId=1021834156&subBannerId=1606502233&adPlacement=list-ad&city=bengaluru&state=karnataka&country=india&clientId=8f7702c0-f5f8&reqTime=1670573644&itemIndex=2&parentUniqueId=1c4e7a97440c394a8f1113d5f731e9fb&eventType=CAROUSEL_ITEM_CLICK&partnerId=JOSH_APP&subSlot=-2&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2\",
\"carouselItemTimeSpentUrl\":
\"http://qa-money.myjosh.in/beaconEvents?uniqueId=1c4e7a97440c394a8f1113d5f731e9fb_2&adId=1358733094&campaignId=1021834156&subBannerId=1606502233&adPlacement=list-ad&city=bengaluru&state=karnataka&country=india&clientId=8f7702c0-f5f8&reqTime=1670573644&itemIndex=2&parentUniqueId=1c4e7a97440c394a8f1113d5f731e9fb&eventType=CAROUSEL_ITEM_TIME_SPENT&partnerId=JOSH_APP&subSlot=-2&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2\",
\"carouselItemLPTimeSpentUrl\":
\"http://qa-money.myjosh.in/beaconEvents?uniqueId=1c4e7a97440c394a8f1113d5f731e9fb_2&adId=1358733094&campaignId=1021834156&subBannerId=1606502233&adPlacement=list-ad&city=bengaluru&state=karnataka&country=india&clientId=8f7702c0-f5f8&reqTime=1670573644&itemIndex=2&parentUniqueId=1c4e7a97440c394a8f1113d5f731e9fb&eventType=CAROUSEL_ITEM_LP_TIME_SPENT&partnerId=JOSH_APP&subSlot=-2&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2\",
\"useInternalBrowser\": \"false\", \"landingUrlAdditional\": \[
\"http://click3.com\" \], \"shareability\": { \"text\": \"Share Text
\*3\", \"subject\": \"Share Subject \*4\", \"image\":
\"http://qa-money.myjosh.in/daedalus-banners/1358733094/1667907052_48050_600x600.jpg\"
} }, { \"itemSubtitle2\": { \"itemTitle\": \"Item Title \*\", \"data\":
\"Install App\", \"color\": \"#000000\", \"bg-color\": \"#FFffffff\",
\"isAnimated\": true, \"animationConfig\": { \"initialButtonColor\":
\"#66ffffff\", \"finalButtonColor\": \"#FFea4e60\",
\"initialTextColor\": \"#ffffff\", \"finalTextColor\": \"#ffffff\",
\"startTime\": \"2000\", \"endTime\": \"3000\" }, \"dimension\": {
\"margin\": \"16\", \"fontSize\": \"14\", \"fontType\": \"BOLD\" },
\"isPopupView\": false }, \"overlayCTA\": { \"transitionDelayInMS\":
3000, \"title\": { \"data\": \"Title\", \"color\": \"#FFFFFF;\" },
\"description\": { \"data\": \"Description\", \"color\": \"#FFFFFF;\" },
\"itemSubtitle2\": { \"data\": \"Action Text \*\", \"color\":
\"#000000\", \"bg-color\": \"#FFffffff\", \"dimension\": { \"margin\":
\"16\", \"fontSize\": \"14\", \"fontType\": \"BOLD\" } }, \"icon\": {
\"data\":
\"http://qa-money.myjosh.in/daedalus-banners/1358733094/1667906802_40853_600x600.png\"
}, \"action\":
\"https://qa-money.myjosh.in/click?clientId=8f7702c0-f5f8&uniqueId=1c4e7a97440c394a8f1113d5f731e9fb&adId=1358733094&campaignId=1021834156&adPlacement=list-ad&reqTime=1670573644&billingTypeId=3&orderId=116&city=bengaluru&state=karnataka&country=india&partnerId=JOSH_APP&subSlot=-2&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\"
}, \"itemTag\": { \"color\": \"#0889ac\", \"color-night\": \"#a5a5a5\",
\"data\": \"Promoted\" }, \"ctaOnlyClick\": true, \"itemImage\": {
\"data\":
\"http://qa-money.myjosh.in/daedalus-banners/1358733094/1667906803_31833_1080x2592.jpg\"
}, \"carouselItemViewUrl\":
\"http://qa-money.myjosh.in/beaconEvents?uniqueId=1c4e7a97440c394a8f1113d5f731e9fb_3&adId=1358733094&campaignId=1021834156&subBannerId=1232564108&adPlacement=list-ad&city=bengaluru&state=karnataka&country=india&clientId=8f7702c0-f5f8&reqTime=1670573644&itemIndex=3&parentUniqueId=1c4e7a97440c394a8f1113d5f731e9fb&eventType=CAROUSEL_ITEM_VIEW&partnerId=JOSH_APP&subSlot=-2&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2\",
\"action\":
\"https://qa-money.myjosh.in/click?clientId=8f7702c0-f5f8&uniqueId=1c4e7a97440c394a8f1113d5f731e9fb&adId=1358733094&campaignId=1021834156&adPlacement=list-ad&reqTime=1670573644&billingTypeId=3&orderId=116&city=bengaluru&state=karnataka&country=india&subBannerId=1232564108&partnerId=JOSH_APP&subSlot=-2&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API&\_\_oadest=https%3A%2F%2Fwww.google.com%2F\",
\"carouselItemClickUrl\":
\"http://qa-money.myjosh.in/beaconEvents?uniqueId=1c4e7a97440c394a8f1113d5f731e9fb_3&adId=1358733094&campaignId=1021834156&subBannerId=1232564108&adPlacement=list-ad&city=bengaluru&state=karnataka&country=india&clientId=8f7702c0-f5f8&reqTime=1670573644&itemIndex=3&parentUniqueId=1c4e7a97440c394a8f1113d5f731e9fb&eventType=CAROUSEL_ITEM_CLICK&partnerId=JOSH_APP&subSlot=-2&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2\",
\"carouselItemTimeSpentUrl\":
\"http://qa-money.myjosh.in/beaconEvents?uniqueId=1c4e7a97440c394a8f1113d5f731e9fb_3&adId=1358733094&campaignId=1021834156&subBannerId=1232564108&adPlacement=list-ad&city=bengaluru&state=karnataka&country=india&clientId=8f7702c0-f5f8&reqTime=1670573644&itemIndex=3&parentUniqueId=1c4e7a97440c394a8f1113d5f731e9fb&eventType=CAROUSEL_ITEM_TIME_SPENT&partnerId=JOSH_APP&subSlot=-2&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2\",
\"carouselItemLPTimeSpentUrl\":
\"http://qa-money.myjosh.in/beaconEvents?uniqueId=1c4e7a97440c394a8f1113d5f731e9fb_3&adId=1358733094&campaignId=1021834156&subBannerId=1232564108&adPlacement=list-ad&city=bengaluru&state=karnataka&country=india&clientId=8f7702c0-f5f8&reqTime=1670573644&itemIndex=3&parentUniqueId=1c4e7a97440c394a8f1113d5f731e9fb&eventType=CAROUSEL_ITEM_LP_TIME_SPENT&partnerId=JOSH_APP&subSlot=-2&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2\",
\"useInternalBrowser\": \"false\", \"landingUrlAdditional\": \[
\"http://click3.com\" \], \"shareability\": { \"text\": \"Share Text
\*\", \"subject\": \"Share Subject \*\", \"image\":
\"http://qa-money.myjosh.in/daedalus-banners/1358733094/1667906802_32670_300x250.jpg\"
} } \] }, \"adFeedback\": { \"feedbackUrl\":
\"http://qa-money.myjosh.in/data-api/adfeedback?bannerId=1358733094&campaignId=1021834156&uniqueId=1c4e7a97440c394a8f1113d5f731e9fb&city=bengaluru\"
}, \"omTrackType\": \"none\", \"omVendorsInfo\": null, \"errorUrl\":
\"http://qa-money.myjosh.in/beaconEvents?eventType=AD_ERROR&subSlot=-2&adPlacement=list-ad&uniqueId=1c4e7a97440c394a8f1113d5f731e9fb&adId=1358733094&campaignId=1021834156&city=bengaluru&state=karnataka&country=india&clientId=8f7702c0-f5f8&reqTime=1670573644&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"brandId\": \"1511\", \"removeTitle\": false, \"adGroupId\":
\"8f7702c0-f5f86392ee4cbb5826.85995134\", \"adTag\": \"-2\",
\"adCommentBeaconUrl\":
\"http://qa-money.myjosh.in/beaconEvents?eventType=AD_COMMENT&subSlot=-2&adPlacement=list-ad&uniqueId=1c4e7a97440c394a8f1113d5f731e9fb&adId=1358733094&campaignId=1021834156&city=bengaluru&state=karnataka&country=india&clientId=8f7702c0-f5f8&reqTime=1670573644&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adLikeBeaconUrl\":
\"http://qa-money.myjosh.in/beaconEvents?eventType=AD_LIKE&subSlot=-2&adPlacement=list-ad&uniqueId=1c4e7a97440c394a8f1113d5f731e9fb&adId=1358733094&campaignId=1021834156&city=bengaluru&state=karnataka&country=india&clientId=8f7702c0-f5f8&reqTime=1670573644&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adTimeSpentBeaconUrl\":
\"http://qa-money.myjosh.in/beaconEvents?eventType=AD_TIME_SPENT&subSlot=-2&adPlacement=list-ad&uniqueId=1c4e7a97440c394a8f1113d5f731e9fb&adId=1358733094&campaignId=1021834156&city=bengaluru&state=karnataka&country=india&clientId=8f7702c0-f5f8&reqTime=1670573644&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adShareBeaconUrl\":
\"http://qa-money.myjosh.in/beaconEvents?eventType=AD_SHARED&subSlot=-2&adPlacement=list-ad&uniqueId=1c4e7a97440c394a8f1113d5f731e9fb&adId=1358733094&campaignId=1021834156&city=bengaluru&state=karnataka&country=india&clientId=8f7702c0-f5f8&reqTime=1670573644&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adLPTimeSpentBeaconUrl\":
\"http://qa-money.myjosh.in/beaconEvents?eventType=AD_LP_TIME_SPENT&subSlot=-2&adPlacement=list-ad&uniqueId=1c4e7a97440c394a8f1113d5f731e9fb&adId=1358733094&campaignId=1021834156&city=bengaluru&state=karnataka&country=india&clientId=8f7702c0-f5f8&reqTime=1670573644&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adDislikeBeaconUrl\":
\"http://qa-money.myjosh.in/beaconEvents?eventType=AD_DISLIKE&subSlot=-2&adPlacement=list-ad&uniqueId=1c4e7a97440c394a8f1113d5f731e9fb&adId=1358733094&campaignId=1021834156&city=bengaluru&state=karnataka&country=india&clientId=8f7702c0-f5f8&reqTime=1670573644&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"brandFollowBeaconUrl\":
\"http://qa-money.myjosh.in/beaconEvents?eventType=BRAND_FOLLOW&subSlot=-2&adPlacement=list-ad&uniqueId=1c4e7a97440c394a8f1113d5f731e9fb&adId=1358733094&campaignId=1021834156&city=bengaluru&state=karnataka&country=india&clientId=8f7702c0-f5f8&reqTime=1670573644&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"brandUnfollowBeaconUrl\":
\"http://qa-money.myjosh.in/beaconEvents?eventType=BRAND_UNFOLLOW&subSlot=-2&adPlacement=list-ad&uniqueId=1c4e7a97440c394a8f1113d5f731e9fb&adId=1358733094&campaignId=1021834156&city=bengaluru&state=karnataka&country=india&clientId=8f7702c0-f5f8&reqTime=1670573644&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adClosedBeaconUrl\":
\"http://qa-money.myjosh.in/beaconEvents?eventType=AD_CLOSE&subSlot=-2&adPlacement=list-ad&uniqueId=1c4e7a97440c394a8f1113d5f731e9fb&adId=1358733094&campaignId=1021834156&city=bengaluru&state=karnataka&country=india&clientId=8f7702c0-f5f8&reqTime=1670573644&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"shareability\": { \"text\": \"Share Text \*\", \"subject\": \"Share
Subject \*\", \"image\":
\"http://qa-money.myjosh.in/daedalus-banners/1358733094/1668509690_46556_share_image.jpg\"
}, \"beaconUrlAdditional\": \[ \"http://imp1.com\" \] }, { \"type\":
\"external-sdk\", \"endepoch\": \"1670977913\", \"position\":
\"list-ad\", \"campaignId\": \"1471594006\", \"id\":
\"81492fa6f3e65611007e218e6e51588e\", \"useInternalBrowser\": \"false\",
\"useWideViewPort\": true, \"beaconUrl\":
\"http://qa-money.myjosh.in/impression?eventType=AD_IMP&subSlot=0&adPlacement=list-ad&uniqueId=81492fa6f3e65611007e218e6e51588e&adId=1501196591&campaignId=1471594006&city=bengaluru&state=karnataka&country=india&clientId=j.a3FtRVpiVnRuQzBaRDFLWDNoSkUrUT09A&reqTime=1669176830&partnerId=JOSH_APP&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API&impType=DISPLAY_IMP\",
\"adRespondedBeaconUrl\":
\"http://qa-money.myjosh.in/beaconEvents?eventType=AD_RESPONDED&subSlot=0&adPlacement=list-ad&uniqueId=81492fa6f3e65611007e218e6e51588e&adId=1501196591&campaignId=1471594006&city=bengaluru&state=karnataka&country=india&clientId=j.a3FtRVpiVnRuQzBaRDFLWDNoSkUrUT09A&reqTime=1669176830&partnerId=JOSH_APP&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adInflatedBeaconUrl\":
\"http://qa-money.myjosh.in/beaconEvents?eventType=AD_INFLATED&subSlot=0&adPlacement=list-ad&uniqueId=81492fa6f3e65611007e218e6e51588e&adId=1501196591&campaignId=1471594006&city=bengaluru&state=karnataka&country=india&clientId=j.a3FtRVpiVnRuQzBaRDFLWDNoSkUrUT09A&reqTime=1669176830&partnerId=JOSH_APP&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"landingUrlAdditional\": \[\], \"landingUrl\":
\"http://qa-money.myjosh.in/click?clientId=j.a3FtRVpiVnRuQzBaRDFLWDNoSkUrUT09A&uniqueId=81492fa6f3e65611007e218e6e51588e&adId=1501196591&campaignId=1471594006&adPlacement=list-ad&reqTime=1669176830&billingTypeId=3&orderId=1&city=bengaluru&state=karnataka&country=india&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API&\_\_oadest=https%3A%2F%2Fapp.appsflyer.com%2Fin.sportscafe.nostragamus.pro%3Fpid%3Djosh_int%26af_r%3Dhttps%253A%252F%252Fnostragamus.in%252Fdownloadnostrapro.html%26af_siteid%3Ddailyhunt%26c%3Djosh%26af_c_id%3D\--CAMPAIGN_ID\--%26af_ad_id%3D\--BANNER_ID\--%26af_sub1%3Dlist-ad%26af_sub2%3Dj.a3FtRVpiVnRuQzBaRDFLWDNoSkUrUT09A%26af_sub3%3D1669176830.5291%26af_click_lookback%3D7d%26trackerProvider%3Dappsflyer%26clickid%3D81492fa6f3e65611007e218e6e51588e%26dhExtras%3D\--DH_EXTRAS\--%26af_param_forwarding%3Dfalse%26advertising_id%3D20ab727a-f437-4753-bbef-f030f5fd7f22%26idfa%3D%26dhPayload%3D\--DH_PAYLOAD\--Cname%3DNostragamus+%7C%7C+Josh+%7C%7C+VideoNostr+Pro+%7C%7C+Hindi\",
\"adFeedback\": { \"feedbackUrl\":
\"http://qa-money.myjosh.in/data-api/adfeedback?bannerId=1501196591&campaignId=1471594006&uniqueId=81492fa6f3e65611007e218e6e51588e&city=bengaluru\"
}, \"omTrackType\": \"none\", \"omVendorsInfo\": null, \"errorUrl\":
\"http://qa-money.myjosh.in/beaconEvents?eventType=AD_ERROR&subSlot=0&adPlacement=list-ad&uniqueId=81492fa6f3e65611007e218e6e51588e&adId=1501196591&campaignId=1471594006&city=bengaluru&state=karnataka&country=india&clientId=j.a3FtRVpiVnRuQzBaRDFLWDNoSkUrUT09A&reqTime=1669176830&partnerId=JOSH_APP&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"adTimeSpentBeaconUrl\":
\"http://qa-money.myjosh.in/beaconEvents?eventType=AD_TIME_SPENT&subSlot=-2&adPlacement=list-ad&uniqueId=1c4e7a97440c394a8f1113d5f731e9fb&adId=1358733094&campaignId=1021834156&city=bengaluru&state=karnataka&country=india&clientId=8f7702c0-f5f8&reqTime=1670573644&partnerId=JOSH_APP&nextAdIndex=-1%2C-2&bookedPlacement=list-ad&bookedSubSlot=-2&appState=FG&hostAppId=JOSH_APP&adFSource=GET_ADS_API\",
\"removeTitle\": false, \"adGroupId\":
\"j.a3FtRVpiVnRuQzBaRDFLWDNoSkUrUT09A637d9dfe804e07.14778839\",
\"customVideoTrackers\": { \"adVideoStart\":
\"http://qa-money.myjosh.in/vastevent?action=start&clientId=231&uniqueId=e1ef1e181dfabb04a6a807eccf3ebb3b&adId=51530&campaignId=51304&adPlacement=storypage&reqTime=1669176725&partnerId=DH_APP&bookedPlacement=storypage\",
\"adVideoEnd\":
\"http://qa-money.myjosh.in/vastevent?action=complete&clientId=231&uniqueId=e1ef1e181dfabb04a6a807eccf3ebb3b&adId=51530&campaignId=51304&adPlacement=storypage&reqTime=1669176725&partnerId=DH_APP&bookedPlacement=storypage\",
\"adVideoPause\":
\"http://qa-money.myjosh.in/vastevent?action=pause&clientId=231&uniqueId=e1ef1e181dfabb04a6a807eccf3ebb3b&adId=51530&campaignId=51304&adPlacement=storypage&reqTime=1669176725&partnerId=DH_APP&bookedPlacement=storypage\",
\"adVideoPlay\":
\"http://qa-money.myjosh.in/vastevent?action=resume&clientId=231&uniqueId=e1ef1e181dfabb04a6a807eccf3ebb3b&adId=51530&campaignId=51304&adPlacement=storypage&reqTime=1669176725&partnerId=DH_APP&bookedPlacement=storypage\",
\"adVideoMute\":
\"http://qa-money.myjosh.in/vastevent?action=mute&clientId=231&uniqueId=e1ef1e181dfabb04a6a807eccf3ebb3b&adId=51530&campaignId=51304&adPlacement=storypage&reqTime=1669176725&partnerId=DH_APP&bookedPlacement=storypage\",
\"adVideoUnMute\":
\"http://qa-money.myjosh.in/vastevent?action=unmute&clientId=231&uniqueId=e1ef1e181dfabb04a6a807eccf3ebb3b&adId=51530&campaignId=51304&adPlacement=storypage&reqTime=1669176725&partnerId=DH_APP&bookedPlacement=storypage\"
}, \"adTag\": \"0\", \"external\": { \"data\":
\"Google-Native-Interstitial\", \"adunitid\":
\"/83414793/Josh_ListAd_Dec22\", \"extras\":
\"c_language:en,c_ecpm:67,c_userIp:10.50.34.66,clientId:231,c_uniqueId:e1ef1e181dfabb04a6a807eccf3ebb3b,c_city:\--LOCATION_CITY\--,topicKey:NULL,npKey:NULL,c_connectionSpeed:AVERAGE,ConnectionType:w,c_placementId:storypage,utm_source:\--UTM_SOURCE\--,Autoplay:3,oxBannerId:000111\"
} } \] }

# [Response Mock](https://qa-money.myjosh.in/daedalus-banners/adengine_mock/josh_releases/josh_multi_ads_mock.json)

## **[FIGMA]{style="color: rgb(7,71,166);"}**:

https://www.figma.com/file/lZGqTG7GWnziqkxtM2qDvR/Josh-ads?node-id=7235%3A32500&t=J3AZYdVcIpGmS8y8-0
