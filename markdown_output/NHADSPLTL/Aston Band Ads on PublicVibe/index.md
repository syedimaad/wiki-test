17

## Requirements

- Supporting Aston Band

- Doc:
  [https://docs.google.com/document/d/1idAYSrRSaE5ZArg8FxXpTvjenGtPW9YfDkaoQtmBqJs/edit](https://docs.google.com/document/d/1idAYSrRSaE5ZArg8FxXpTvjenGtPW9YfDkaoQtmBqJs/edit){card-appearance="inline"}

## Figma

https://www.figma.com/file/i4IPWk7xd7I3UPxW9GgfJ5/Ads?node-id=419%3A6625&t=aZd1ebUwYZoh3U6o-0

## Client changes

- Client need to fetch details from both Ads Handshake for PublicVibe

- Ads Handshake will have parameters to support Aston band behaviour.

- Client will use the Ads Handshake parameters to transition image along
  the video.

- Client will pass parameter enclosedEntityId, enclosedEntityType for
  tracking post related params.

## Adengine changes

- Ads Handshake for PublicVibe needs to be updated with supportive
  params.

## DD changes

- Introducing new placement type.

## Sample Responses

Sample Handshake Responsejson{ \"code\": 200, \"data\": {
\"placementConfig\": { \"aston-band\": { \"enable\": true,
\"identifier\": \"aston-band\", \"distancingConfig\": { \"startIndex\":
1, \"minDistance\": 1 }, \"cacheConfig\": { \"cacheTTLInSeconds\": 300,
\"minCacheCount\": 1 }, \"reRenderAds\": true, \"timeDistancingConfig\":
{ \"startTimeInSeconds\": 5, \"minIntervalInSeconds\": 10,
\"displayTimeInSeconds\": 5, \"noOfAds\": 3 } } } } }Aston band Image
Responsejson\[{ \"type\": \"IMAGE\", \"id\":
\"ca39d57a2267e7843a7ac76dac8d306d\", \"campaignId\": \"1641436735\",
\"bannerId\": \"1622944211\", \"content\": { \"image\": { \"url\":
\"http://stage-ads2.publicvibe.com/daedalus-banners/1622944211/1670846281_67063_320x100.jpg\"
}, \"cta\": { \"url\":
\"https://stage-ads2.publicvibe.com/click?clientId=1669804100638365545\\u0026uniqueId=ca39d57a2267e7843a7ac76dac8d306d\\u0026adId=1622944211\\u0026campaignId=1641436735\\u0026adPlacement=full-card\\u0026reqTime=1670927542\\u0026billingTypeId=3\\u0026orderId=1994297891\\u0026city=bengaluru\\u0026state=karnataka\\u0026country=india\\u0026partnerId=PUBLIC_VIBE\\u0026bookedPlacement=full-card\\u0026appState=FG\\u0026hostAppId=PUBLIC_VIBE\\u0026adFSource=GET_ADS_API\\u0026\_\_oadest=https%3A%2F%2Fwww.google.com\",
\"browser\": \"EXTERNAL\" } }, \"beacons\": { \"request\": {
\"internal\":
\[\"http://stage-ads2.publicvibe.com/fallback?clientid=1669804100638365545\\u0026req_time=13122022+16%3A02%3A22\\u0026request_timestamp=1670927542\\u0026Gpscountry=india\\u0026Gpsstate=karnataka\\u0026Gpscity=bengaluru\\u0026Gpsconstituency=shivajinagar\\u0026confidence=0.4\\u0026user_os_platform=android\\u0026user_handset_maker=none\\u0026user_handset_model=none\\u0026placement=full-card\\u0026user_app_ver=3.0.75\\u0026banner_rotation_type=0\\u0026bannerSelectedBy=adEngine\\u0026bookedPlacement=full-card\\u0026banner_id=1622944211\\u0026campaign_id=1641436735\\u0026user_connection=wifi\\u0026connection_speed=NO_CONNECTION\\u0026user_os_ver=12.0\\u0026encGaid=MTdkZGY0YWEtNTAxZi00Nzc5LTg0MzItNmZkM2Y1NzhmMGU5\\u0026user_languages=en\\u0026oi=768\\u0026price_range=none\\u0026user_device_type=none\\u0026title=Full+Card+PV\\u0026latitude=NA\\u0026longitude=NA\\u0026uniqueId=ca39d57a2267e7843a7ac76dac8d306d\\u0026ip=122.172.87.152\\u0026adGroupId=1669804100638365545639854b693f343.07107084\\u0026ecpm=1000\\u0026audienceSegments=none\\u0026resolution=1080x2168\\u0026hostalias=dh-gcp-ads-adengine-ws-stage-az-dqfj\\u0026locationSource=IP\\u0026ab=ECPM\\u0026partnerId=PUBLIC_VIBE\\u0026deliverySlab=1\\u0026pubName=DH\\u0026nthImpression=8\\u0026v_ecpm=1000\\u0026autoPlayPref=2\\u0026optimisedBy=1\\u0026topCampaignIds=1641436735%5E\\u0026topCampaignECPMs=1000\\u0026entityType=L_NP\\u0026sourceType=OGC\\u0026event_type=AD_REQUEST\\u0026is_interleaved=0\\u0026boost_factor=1\\u0026interleave_campaign_daedalus_config=0\\u0026campaign_type=TEST_MODE\\u0026campaign_level=LEVEL_1\\u0026requestIdDebug=82dd3db158843c219b0a59ec7f3e1a49\\u0026orderTypeV2=0\\u0026requestData=%7B%22products%22%3A%5B%5D%7D\\u0026isRegUser=1\\u0026hostAppId=PUBLIC_VIBE\\u0026adFillSource=GET_ADS_API\\u0026appState=FG\\u0026feedLong=77.2274\\u0026feedLat=28.6619\\u0026feedTalukId=6622\\u0026feedStateId=17\\u0026feedDistrictId=1026\\u0026reqTime=1670927542\\u0026\"\]
}, \"responded\": { \"internal\":
\[\"http://stage-ads2.publicvibe.com/beaconEvents?eventType=AD_RESPONDED\\u0026adPlacement=full-card\\u0026uniqueId=ca39d57a2267e7843a7ac76dac8d306d\\u0026adId=1622944211\\u0026campaignId=1641436735\\u0026city=bengaluru\\u0026state=karnataka\\u0026country=india\\u0026clientId=1669804100638365545\\u0026reqTime=1670927542\\u0026partnerId=PUBLIC_VIBE\\u0026bookedPlacement=full-card\\u0026appState=FG\\u0026hostAppId=PUBLIC_VIBE\\u0026adFSource=GET_ADS_API\"\]
}, \"error\": { \"internal\":
\[\"http://stage-ads2.publicvibe.com/beaconEvents?eventType=AD_ERROR\\u0026adPlacement=full-card\\u0026uniqueId=ca39d57a2267e7843a7ac76dac8d306d\\u0026adId=1622944211\\u0026campaignId=1641436735\\u0026city=bengaluru\\u0026state=karnataka\\u0026country=india\\u0026clientId=1669804100638365545\\u0026reqTime=1670927542\\u0026partnerId=PUBLIC_VIBE\\u0026bookedPlacement=full-card\\u0026appState=FG\\u0026hostAppId=PUBLIC_VIBE\\u0026adFSource=GET_ADS_API\"\]
}, \"inflated\": { \"internal\":
\[\"http://stage-ads2.publicvibe.com/beaconEvents?eventType=AD_INFLATED\\u0026adPlacement=full-card\\u0026uniqueId=ca39d57a2267e7843a7ac76dac8d306d\\u0026adId=1622944211\\u0026campaignId=1641436735\\u0026city=bengaluru\\u0026state=karnataka\\u0026country=india\\u0026clientId=1669804100638365545\\u0026reqTime=1670927542\\u0026partnerId=PUBLIC_VIBE\\u0026bookedPlacement=full-card\\u0026appState=FG\\u0026hostAppId=PUBLIC_VIBE\\u0026adFSource=GET_ADS_API\"\]
}, \"impression\": { \"internal\":
\[\"http://stage-ads2.publicvibe.com/impression?eventType=AD_IMP\\u0026adPlacement=full-card\\u0026uniqueId=ca39d57a2267e7843a7ac76dac8d306d\\u0026adId=1622944211\\u0026campaignId=1641436735\\u0026city=bengaluru\\u0026state=karnataka\\u0026country=india\\u0026clientId=1669804100638365545\\u0026reqTime=1670927542\\u0026partnerId=PUBLIC_VIBE\\u0026bookedPlacement=full-card\\u0026appState=FG\\u0026hostAppId=PUBLIC_VIBE\\u0026adFSource=GET_ADS_API\"\]
}, \"lpTimeSpent\": { \"internal\":
\[\"http://stage-ads2.publicvibe.com/beaconEvents?eventType=AD_LP_TIME_SPENT\\u0026adPlacement=full-card\\u0026uniqueId=ca39d57a2267e7843a7ac76dac8d306d\\u0026adId=1622944211\\u0026campaignId=1641436735\\u0026city=bengaluru\\u0026state=karnataka\\u0026country=india\\u0026clientId=1669804100638365545\\u0026reqTime=1670927542\\u0026partnerId=PUBLIC_VIBE\\u0026bookedPlacement=full-card\\u0026appState=FG\\u0026hostAppId=PUBLIC_VIBE\\u0026adFSource=GET_ADS_API\"\]
} }, \"adFeedback\": { \"label\": { \"color\": \"#798DED\",
\"colorNight\": \"#FFFFFF\", \"bgColor\": \"#40000000\",
\"bgColorNight\": \"#40000000\", \"data\": \"Ad\", \"position\":
\"TOP_RIGHT\" }, \"feedbackUrl\":
\"http://stage-ads2.publicvibe.com/data-api/adfeedback?bannerId=1622944211\\u0026campaignId=1641436735\\u0026uniqueId=ca39d57a2267e7843a7ac76dac8d306d\\u0026city=bengaluru\"
}, \"placement\": \"aston-band\" }\]

## **MOCK API**

- <https://stage-ads2.publicvibe.com/daedalus-banners/adengine_mock/pv_releases/handShake.json>

## MOM

8th Dec, 2022

Initial PRD discussion

- Figma for Aston Band

- Behaviour of the Image Ads on Video

- Placement to be created newly or existing

13th Dec, 2022

Walkthrough and QA on PRD document

- Placement name finalization

- Functional behaviour simulation with respect to Figma.

- Pending: Creative size, No of Ads to be shown for various video sizes.

12th Jan, 2022

Inclusion of params to tag ad to post.

- enclosedEntityId

- enclosedEntityType
