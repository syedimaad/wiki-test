# Requirements:

- Supporting sponsored content/content boosted ads on pv

- prod
  doc:[https://docs.google.com/document/d/1RD6JEJluyZNw_f_PsUqYkYcD7zTpCWB-M0VRuy5m6p0/edit](https://docs.google.com/document/d/1RD6JEJluyZNw_f_PsUqYkYcD7zTpCWB-M0VRuy5m6p0/edit){card-appearance="inline"}

# Figma:

https://www.figma.com/file/i4IPWk7xd7I3UPxW9GgfJ5/Ads?node-id=419%3A6625&t=XLccEtSNidCF1vWZ-0

# Client changes:

- Client need to fetch details from both Ads BE and Content BE.

- ADs BE will send these content items only CTA,Item Tag, Vast Url along
  with the `contentId`

- Client will get Description,Title,Brand from respective BE based on
  `contentId`

# Adengine changes:

- Content AdHandler needs to be implemented in response creator.

# DD changes:

- Integration with pv content BE TBD.

- Introducing new content banner for home-pgi placement.

- minimum version compatibility.

- Min version targeting : **3.0.88**

- fields needed while banner creation

bannerBanner Name\* start date End date ContentType (drop down)
\"post/people/space/topic/product/discover\" ContentId\* Thumbnail image
Action text Landing Url landing page target OM Vendor Info Vendor Key
Vendor Verification Parameters Item Tag IMP Trackers Click Trackers
Video Trackers Languagesvideo banner data\"video\": { \"rawFileName\":
\"167022569965140166842255488238Video_Landscape_CocaCola_15s.mp4\",
\"salt\": \"fc140ffa606191c250c3a7c393612c8e\", \"CDNUrl\":
\"http:\\/\\/video-service-stage.dailyhunt.in\\/video\\/a2-53743530746f11edb5de716e49be95b8_auto.m3u8\",
\"mp4CDNUrl\":
\"http:\\/\\/video-service-stage.dailyhunt.in\\/video\\/a2-53ebd630746f11ed9fdf004d273f8915.mp4\",
\"updateCount\": 4, \"isReady\": true, \"fullyConverted\": false,
\"mp4FullyConverted\": false, \"mp4Variants\": \[ \"m\", \"l\", \"h\",
\], \"height\": \"720\", \"width\": \"1280\", \"videoDuration\":
\"15023\", \"variantInfo\": { \"h\": { \"width\": 1136, \"height\": 640,
\"size\": 1846701 }, \"l\": { \"width\": 426, \"height\": 240, \"size\":
388598 }, \"m\": { \"width\": 852, \"height\": 480, \"size\": 1329939 }
} },

# PV Content BE Integration on DD:

API's from PV content.

GET API

`https://stage-api.publicvibe.com/pvrest-2/restapi/v3/vposts/1670840390661144224`

POST API

curl \--location \--request POST
\'<http://api.publicvibe.com/gateway/v1/posts/get/1668088068205157306'>\
\--header \'Content-Type: application/json\'\
\--data-raw \'{\
\"device\": {\
\"id\": \"1634560410470362493\",\
\"ver\": \"239\",\
\"verName\": \"3.0.12 dev\",\
\"appOpenCount\": 29,\
\"make\": \"samsung\",\
\"deviceType\": \"2\",\
\"deviceOsType\": \"android\",\
\"deviceOsVer\": \"11\",\
\"networkType\": \"wifi\",\
\"networkSpeed\": \"veryfast\",\
\"theme\": \"1\",\
\"isDebug\": true\
},\
\"user\": {\
\"id\": \"1641488663888382901\",\
\"languageId\": \"5\",\
\"appLanguageId\": \"5\"\
},\
\"pbGlobal\": {\
\"test\": {\
\"dbg\": true\
}\
}\
}\'

## MOCK RESPONSE:

mock responsejson\[ { \"type\": \"SPONSORED_CONTENT\", \"id\":
\"a81caa91a239e0fcd99024936eb31713\", \"campaignId\": \"1359931390\",
\"bannerId\": \"1721793099\", \"content\": { \"sponsoredContentId\":
\"1670840390661144224\", \"bgColor\": \"#ffffff\", \"bgColorNight\":
\"#000000\", \"cta\": { \"url\":
\"https://stage-ads2.publicvibe.com/click?clientId=1667997741225353782&uniqueId=a81caa91a239e0fcd99024936eb31713&adId=1721793099&campaignId=1359931390&adPlacement=home-pgi&reqTime=1670503661&billingTypeId=3&orderId=1620249071&country=india&partnerId=PUBLIC_VIBE&bookedPlacement=home-pgi&appState=FG&hostAppId=PUBLIC_VIBE&adFSource=GET_ADS_API&\_\_oadest=https%3A%2F%2Fgoogle.com\",
\"data\": \"Action Text 3\", \"color\": \"#4caf79\", \"colorNight\":
\"#ffffff\", \"bgColor\": \"#52A1DD,#5282E7\", \"bgColorNight\":
\"#52A1DD,#5282E7\", \"browser\": \"EXTERNAL\" }, \"tag\": { \"color\":
\"#757575\", \"colorNight\": \"#ffffff\", \"data\": \"Promoted\" },
\"tagURL\":
\"http%3A%2F%2Fstage-ads2.publicvibe.com%2Fgetvast%3FclientId%3D1667997741225353782%26uniqueId%3Da81caa91a239e0fcd99024936eb31713%26adId%3D1721793099%26campaignId%3D1359931390%26adPlacement%3Dhome-pgi%26cap%3D0%26reset%3D0%26billingTypeId%3D3%26orderId%3D1620249071%26forceTracker%3D%26gaid%3D%26gaidOptoutStatus%3D0%26reqTime%3D1670503661%26partnerId%3DPUBLIC_VIBE%26subSlot%3D%26nextAdIndex%3D%26bookedPlacement%3Dhome-pgi%26bookedSubSlot%3D%26clientVersions%3D3.0.71.7%26os%3Dandroid%26ucq%3Dno_connection\",
\"mediaFileUrl\":
\"http://video-service-stage.dailyhunt.in/video/a2-53ebd630746f11ed9fdf004d273f8915_h.mp4\",
\"prefetchVideoBytes\": 369340 }, \"beacons\": { \"request\": {
\"internal\": \[
\"http://stage-ads2.publicvibe.com/fallback?clientid=1667997741225353782&req_time=08122022+18%3A17%3A41&request_timestamp=1670503661&Gpscountry=india&confidence=0.4&user_os_platform=android&user_handset_maker=Vivo&user_handset_model=V2065&placement=home-pgi&user_app_ver=3.0.71.7&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=home-pgi&banner_id=1721793099&campaign_id=1359931390&user_connection=wifi&connection_speed=NO_CONNECTION&user_os_ver=12.0&user_languages=en&oi=1371&price_range=none&user_device_type=none&title=Vast+Native+Video+3&latitude=NA&longitude=NA&uniqueId=a81caa91a239e0fcd99024936eb31713&cellid=YqGT+QL49bF8VRdcq5q5DA%3D%3D&ip=10.52.134.5&adGroupId=16679977412253537826391dceda5cad2.19998633&ecpm=1000&audienceSegments=none&resolution=720x1475&hostalias=dh-gcp-ads-adengine-ws-stage-az-dqfj&locationSource=IP&ab=ECPM&partnerId=PUBLIC_VIBE&deliverySlab=1&pubName=DH&nthImpression=1&v_ecpm=1000&autoPlayPref=2&optimisedBy=1&topCampaignIds=1359931390%5E&topCampaignECPMs=1000&entityType=L_NP&sourceType=OGC&event_type=AD_REQUEST&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&campaign_type=TEST_MODE&campaign_level=LEVEL_1&requestIdDebug=5cba9a71683cebf4bc810905116c4be0&orderTypeV2=0&requestData=%7B%22products%22%3A%5B%5D%7D&hostAppId=PUBLIC_VIBE&adFillSource=GET_ADS_API&appState=FG&reqTime=1670503661&\"
\] }, \"responded\": { \"internal\": \[
\"http://stage-ads2.publicvibe.com/beaconEvents?eventType=AD_RESPONDED&adPlacement=home-pgi&uniqueId=a81caa91a239e0fcd99024936eb31713&adId=1721793099&campaignId=1359931390&country=india&clientId=1667997741225353782&reqTime=1670503661&partnerId=PUBLIC_VIBE&bookedPlacement=home-pgi&appState=FG&hostAppId=PUBLIC_VIBE&adFSource=GET_ADS_API\"
\] }, \"error\": { \"internal\": \[
\"http://stage-ads2.publicvibe.com/beaconEvents?eventType=AD_ERROR&adPlacement=home-pgi&uniqueId=a81caa91a239e0fcd99024936eb31713&adId=1721793099&campaignId=1359931390&country=india&clientId=1667997741225353782&reqTime=1670503661&partnerId=PUBLIC_VIBE&bookedPlacement=home-pgi&appState=FG&hostAppId=PUBLIC_VIBE&adFSource=GET_ADS_API\"
\] }, \"inflated\": { \"internal\": \[
\"http://stage-ads2.publicvibe.com/beaconEvents?eventType=AD_INFLATED&adPlacement=home-pgi&uniqueId=a81caa91a239e0fcd99024936eb31713&adId=1721793099&campaignId=1359931390&country=india&clientId=1667997741225353782&reqTime=1670503661&partnerId=PUBLIC_VIBE&bookedPlacement=home-pgi&appState=FG&hostAppId=PUBLIC_VIBE&adFSource=GET_ADS_API\"
\] }, \"impression\": { \"internal\": \[
\"http://stage-ads2.publicvibe.com/impression?eventType=AD_IMP&adPlacement=home-pgi&uniqueId=a81caa91a239e0fcd99024936eb31713&adId=1721793099&campaignId=1359931390&country=india&clientId=1667997741225353782&reqTime=1670503661&partnerId=PUBLIC_VIBE&bookedPlacement=home-pgi&appState=FG&hostAppId=PUBLIC_VIBE&adFSource=GET_ADS_API\"
\] }, \"lpTimeSpent\": { \"internal\": \[
\"http://stage-ads2.publicvibe.com/beaconEvents?eventType=AD_LP_TIME_SPENT&adPlacement=home-pgi&uniqueId=a81caa91a239e0fcd99024936eb31713&adId=1721793099&campaignId=1359931390&country=india&clientId=1667997741225353782&reqTime=1670503661&partnerId=PUBLIC_VIBE&bookedPlacement=home-pgi&appState=FG&hostAppId=PUBLIC_VIBE&adFSource=GET_ADS_API\"
\] } }, \"adFeedback\": { \"label\": { \"color\": \"#798DED\",
\"colorNight\": \"#FFFFFF\", \"bgColor\": \"#40000000\",
\"bgColorNight\": \"#40000000\", \"data\": \"Ad\", \"position\":
\"TOP_RIGHT\" }, \"feedbackUrl\":
\"http://stage-ads2.publicvibe.com/data-api/adfeedback?bannerId=1721793099&campaignId=1359931390&uniqueId=a81caa91a239e0fcd99024936eb31713\"
}, \"noSkipTimer\": 4, \"sponsoredContentType\": \"POST\", \"fallback\":
{ \"type\": \"EMPTY\", \"id\": \"708bbbf4bd1166df54d00a43194f6db9\",
\"campaignId\": \"-2\", \"bannerId\": \"53495\", \"beacons\": {
\"request\": { \"internal\": \[
\"http://stage-ads2.publicvibe.com/fallback?clientid=1667997741225353782&req_time=08122022+18%3A17%3A41&request_timestamp=1670503661&Gpscountry=india&confidence=0.4&user_os_platform=android&user_handset_maker=Vivo&user_handset_model=V2065&placement=home-pgi&user_app_ver=3.0.71.7&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=home-pgi&banner_id=53495&campaign_id=-2&user_connection=wifi&connection_speed=NO_CONNECTION&user_os_ver=12.0&user_languages=en&oi=1371&price_range=none&user_device_type=none&title=Empty+Banner&latitude=NA&longitude=NA&uniqueId=708bbbf4bd1166df54d00a43194f6db9&cellid=YqGT+QL49bF8VRdcq5q5DA%3D%3D&ip=10.52.134.5&adGroupId=16679977412253537826391dceda5cad2.19998633&ecpm=0&audienceSegments=none&resolution=720x1475&hostalias=dh-gcp-ads-adengine-ws-stage-az-dqfj&locationSource=IP&ab=ECPM&partnerId=PUBLIC_VIBE&deliverySlab=1&pubName=DH&v_ecpm=0&autoPlayPref=2&optimisedBy=1&entityType=L_NP&sourceType=OGC&event_type=AD_REQUEST&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&requestIdDebug=5cba9a71683cebf4bc810905116c4be0&orderTypeV2=1&requestData=%7B%22products%22%3A%5B%5D%7D&hostAppId=PUBLIC_VIBE&adFillSource=GET_ADS_API&appState=FG&reqTime=1670503661&\"
\] }, \"responded\": { \"internal\": \[
\"http://stage-ads2.publicvibe.com/beaconEvents?eventType=AD_RESPONDED&adPlacement=home-pgi&uniqueId=708bbbf4bd1166df54d00a43194f6db9&adId=53495&campaignId=-2&country=india&clientId=1667997741225353782&reqTime=1670503661&partnerId=PUBLIC_VIBE&bookedPlacement=home-pgi&appState=FG&hostAppId=PUBLIC_VIBE&adFSource=GET_ADS_API\"
\] }, \"inflated\": { \"internal\": \[
\"http://stage-ads2.publicvibe.com/beaconEvents?eventType=AD_INFLATED&adPlacement=home-pgi&uniqueId=708bbbf4bd1166df54d00a43194f6db9&adId=53495&campaignId=-2&country=india&clientId=1667997741225353782&reqTime=1670503661&partnerId=PUBLIC_VIBE&bookedPlacement=home-pgi&appState=FG&hostAppId=PUBLIC_VIBE&adFSource=GET_ADS_API\"
\] }, \"impression\": { \"internal\": \[
\"http://stage-ads2.publicvibe.com/impression?eventType=AD_IMP&adPlacement=home-pgi&uniqueId=708bbbf4bd1166df54d00a43194f6db9&adId=53495&campaignId=-2&country=india&clientId=1667997741225353782&reqTime=1670503661&partnerId=PUBLIC_VIBE&bookedPlacement=home-pgi&appState=FG&hostAppId=PUBLIC_VIBE&adFSource=GET_ADS_API\"
\] } }, \"startIndex\": 1, \"minDistance\": 4, \"noSkipTimer\": 4,
\"placement\": \"home-pgi\" }, \"placement\": \"home-pgi\", \"size\": {
\"width\": 720, \"height\": 405 } } \]

## **MOCK API:**

- [[https://stage-ads2.publicvibe.com/daedalus-banners/adengine_mock/pv_releases/content_boosted_ad.json]{.underline}](https://stage-ads2.publicvibe.com/daedalus-banners/adengine_mock/pv_releases/content_boosted_ad.json)\

## MOM:

8 dec 2022:

1)tbd new adplacement will be introduced .

2)dd to integrate with pv cms and get video url generated for the
particular contenid. Adengine will generate vast url using this video
url.
