Table of contents

## Product Doc Link

- Exit Splash Ad

## Jira Story

System
JIRAkey,summary,type,created,updated,due,assignee,reporter,priority,status,resolutione55da6ef-1840-3475-9293-310ba48d502dNHADSPLTL-5035

## Requirements

Implementation of Clickable Exit Splash Ads on user doing the double
back to exit the App.

## Objective

Placing the full screen ad on the double back exit from the app.

## AdEngine Changes

1.  Introducing new zone `splash-exit ( 12028 )`.

2.  Support `image/GIF/html/sdk [video via html]` type of ads.

3.  `splash-exit` zone should support adNetwork as well.

4.  Add `splash-exit` in `disableNWAdsZonewise`.

5.  Configuring required span time in `settings.php`.

6.  Addition of new field in response called
    `"backFromLpAction":"EXIT_APP"/"BACK_TO_APP"`

7.  Addition of new field in response called
    `"displayType": "FULL_SCREEN/MINI_SCREEN"`.

8.  Flag based enabling and disabling of the zone via handshake.

9.  Different new users timer/condition for this zone alone.

10. Thin/regular user targeting to be built ( Evergreen Ad Support ),
    need to add new zone to evergreen path.

11. Need to send close ad beacon in the response.

12. Capture close ad exit reason and sent to kudu for future use.

## Handshake Changes

1.  Addition of new field called

json{ \"splash-exit\": { \"enabled\": \"TRUE\" }, }

## Daedalus Changes

1.  New Zone to be added in DD called `"splash-exit ( 12028 )"`.

2.  New param for this creative `splashType`, options:
    `"FULL_SCREEN/MINI_SCREEN"`

3.  This zone should have all targeting features.

4.  This zone should have ad networks enabled.

5.  Tracking to be enabled for capturing the impressions and click. 3rd
    party trackers to be enabled.

6.  Config for `"backFromLpAction":"EXIT_APP"/"BACK_TO_APP"` for a
    creative.

## Client Changes

1.  Check handshake configs for making `splash-exit` request.

2.  Based on the `"splashType": "FULL_SCREEN/MINI_SCREEN"` display the
    Ad.

3.  Auto dismiss the ad after `spanInMS` x in milli seconds.

4.  Back from LP action should be picked from `"backFromLpAction"`
    variable sent in the response.

5.  Close button beacon with exit reason, client should take care of
    adding close button on the ad and send the reason in POST body of
    `adClosedBeaconUrl`.\

    interaction\":\"AUTO_TIMER\", // Auto Dismissible
    interaction\":\"USER_CLOSE\", // User Click on close button
    interaction\":\"USER_BACK_NAVIGATION\", // User back navigation if
    \"backFromLpAction\": \"EXIT_APP\" then
    interaction\":\"USER_CLICK\", // User click on LP if
    \"backFromLpAction\": \"BACK_TO_APP\" then
    interaction\":\"USER_CLOSE \| AUTO_TIMER \| USER_BACK_NAVIGATION\",

6.  Multiple backs should not exit the app without showing the ad.

7.  Evergreen ad support for `splash-exit` zone as well.

## Client POC

1.  BE is sending absolute wxh for mini splash. Logic is based on % wise

2.  client just rely on wxh and tries to fix creative in it.

## Request Format

As same as existing request params.

## Response Format

### ZIP Ad Response

json{ \"ads\": \[ { \"type\": \"mraid-zip\", \"typeId\": 7, \"aduid\":
\"notId=ad-1622953392\", \"srcUrlExpiry\": 60, \"width\": 1080,
\"height\": 2131, \"bannerid\": \"1011720818\", \"adTemplate\": \"L\",
\"showOnlyImage\": false, \"id\": \"251d9d5eed35e1dd5119e10738114e0c\",
\"span\": 10, \"spanInMS\":5000, \"useInternalBrowser\": \"false\",
\"useWideViewPort\": true, \"adCacheGood\": 1, \"adCacheAverage\": 1,
\"adCacheSlow\": 1, \"allowDelayedAdInsert\": true, \"adGroupId\":
\"dh.RDY1TnJiV09ACUm5zL3QzeG1KeW1xZz09A62c6c1777d7250.92139857\",
\"adContext\": null, \"isVideo\": \"false\", \"dedupId\":
\"251d9d5eed35e1dd5119e10738114e0c\", \"adTagPosition\":
\"TOP_OVERLAY_RIGHT\", \"showPlaybackControls\": false,
\"enableGyroscope\": false, \"enableAccelerometer\": false,
\"gyroscopeFreq\": 100, \"accelerometerFreq\": 100, \"showBorder\":
false, \"campaignId\": \"1011720818\", \"bannerId\": \"1622953392\",
\"isLargeAd\": false, \"errorUrl\":
\"http://qa-money.newshunt.com/beaconEvents?uniqueId=251d9d5eed35e1dd5119e10738114e0c&adId=1622953392&campaignId=1011720818&adPlacement=pgi&partnerRef=&city=chennai&state=tamil+nadu&country=india&clientId=dh.RDY1TnJiV09ACUm5zL3QzeG1KeW1xZz09A&reqTime=1657192823&eventType=AD_ERROR&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=pgi&bookedSubSlot=&contentId=&contentCreatorId=\",
\"largeAdDistance\": 8, \"position\": \"splash-exit\", \"showCount\": 1,
\"startepoch\": 1657692876, \"endepoch\": 1667068140,
\"backFromLpAction\": \"EXIT_APP\", \"displayType\": \"FULL_SCREEN\",
\"sessionCount\": 2, \"minThresholdSwipeCount\": 3,
\"firstAdSwipeCount\": 3, \"pageSwipeCount\": 9, \"maxPageSwipeCount\":
13, \"requestSwipeCountGood\": 1, \"requestSwipeCountAverage\": 1,
\"requestSwipeCountSlow\": 1, \"titleBar\": true, \"skipTimer\": 5,
\"showHTMLPgiOnlyOnVisible\": \"false\", \"interstitialDisplayType\":
\"swipeable_no_topbar\", \"beaconUrl\":
\"http://qa-money.newshunt.com/impression?uniqueId=251d9d5eed35e1dd5119e10738114e0c&adId=1622953392&campaignId=1011720818&adPlacement=pgi&partnerRef=&city=chennai&state=tamil+nadu&country=india&clientId=dh.RDY1TnJiV09ACUm5zL3QzeG1KeW1xZz09A&reqTime=1657192823&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=pgi&bookedSubSlot=&contentId=&contentCreatorId=\",
\"coolAd\": { \"autoexpand-timer\": 15, \"autoexpand-min-swipes\": 5,
\"actmethod\": \"onclick\", \"expandbackground\": \"nontransparent\",
\"title\": \"Ad Breaks\", \"tapToEng\": \"Tap to engage\",
\"titleColor\": \"#FFFFFF\", \"titleBgColor\": \"#808080\",
\"tapToEngColor\": \"#FFFFFF\", \"tapToEngBgColor\": \"#808080\",
\"zipped\": true, \"type\": \"mraidzip\", \"meta\": \"\<meta
name=\\\"viewport\\\" content=\\\"width=device-width,
initial-scale=1\\\"/\>\", \"content\": { \"mainfile\": \"index.html\",
\"link\": true, \"data\":
\"http://qa-money.newshunt.com/daedalus-banners/1622953392/1657191548_97407\_.zip\"
}, \"zipsubcontent\": { \"zipped\": false, \"name\":
\"eterno-clientuniqparams.js\", \"link\": false }, \"tracker\": {
\"redirectWebUrl\": true, \"data\":
\"https://qa-money.newshunt.com/click?clientId=dh.RDY1TnJiV09ACUm5zL3QzeG1KeW1xZz09A&uniqueId=251d9d5eed35e1dd5119e10738114e0c&adId=1622953392&campaignId=1011720818&adPlacement=pgi&billingTypeId=3&orderId=116&forceTracker=&reqTime=1657192823&leadId=&subBannerId=&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=pgi&bookedSubSlot=&contentId=&contentCreatorId=&\_\_oadest=\--USER_CLICK_URL\--\"
} }, \"action\": null, \"contentBaseUrl\":
\"http://qa-money.newshunt.com/\", \"adLPTimeSpentBeaconUrl\":
\"http://qa-money.newshunt.com/beaconEvents?uniqueId=251d9d5eed35e1dd5119e10738114e0c&adId=1622953392&campaignId=1011720818&adPlacement=pgi&partnerRef=&city=chennai&state=tamil+nadu&country=india&clientId=dh.RDY1TnJiV09ACUm5zL3QzeG1KeW1xZz09A&reqTime=1657192823&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=pgi&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adRespondedBeaconUrl\":
\"http://qa-money.newshunt.com/beaconEvents?uniqueId=251d9d5eed35e1dd5119e10738114e0c&adId=1622953392&campaignId=1011720818&adPlacement=pgi&partnerRef=&city=chennai&state=tamil+nadu&country=india&clientId=dh.RDY1TnJiV09ACUm5zL3QzeG1KeW1xZz09A&reqTime=1657192823&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=pgi&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adInflatedBeaconUrl\":
\"http://qa-money.newshunt.com/beaconEvents?uniqueId=251d9d5eed35e1dd5119e10738114e0c&adId=1622953392&campaignId=1011720818&adPlacement=pgi&partnerRef=&city=chennai&state=tamil+nadu&country=india&clientId=dh.RDY1TnJiV09ACUm5zL3QzeG1KeW1xZz09A&reqTime=1657192823&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=pgi&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adContextRules\": { \"selectionPriority\": 2, \"cacheType\":
\"session\", \"ttl\": 300, \"ruleGroup\": { \"respondedFor\": {
\"entityIds\": \[ \"nh-headlines\", \"91581308b67fdfbcd24028a0c513bc37\"
\], \"postId\": null } } }, \"content\": { \"itemSubtitle2\": {
\"color\": \"#4caf79\", \"color-night\": \"#ffffff\" }, \"reportText\":
{ \"color\": \"#FFFFFF\", \"color-night\": \"#FFFFFF\",
\"background-color\": \"#40000000\", \"background-color-night\":
\"#40000000\", \"data\": \"Ad\" } }, \"landingUrl\": null,
\"requestUrl\":
\"http://qa-money.newshunt.com/fallback?clientid=dh.RDY1TnJiV09ACUm5zL3QzeG1KeW1xZz09A&req_time=07072022+16%3A50%3A23&paper=&item_category=&Gpscountry=india&Gpsstate=tamil+nadu&Gpscity=chennai&IPcountry=&IPstate=&IPcity=&isp=others&user_os_platform=android&user_handset_maker=none&user_handset_model=none&user_id=&placement=pgi&user_app_ver=18.6.1004.2&banner_rotation_type=0&bannerSelectedBy=RankingService&bookedPlacement=pgi&banner_id=1622953392&campaign_id=1011720818&user_connection=w&connection_speed=AVERAGE&user_os_ver=10.0&encGaid=NDQ2ZDA2YTktMDQ0OS00MWY0LThlZWMtYzhhYzUyODNjMDk1&item_publisher_language=&user_languages=en&oi=1354&price_range=none&user_device_type=none&title=mraid&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=251d9d5eed35e1dd5119e10738114e0c&region=chennai&mcc=&mnc=&lac=&cellid=&ip=10.52.134.5&adGroupId=dh.RDY1TnJiV09ACUm5zL3QzeG1KeW1xZz09A62c6c1777d7250.92139857&topicId=91581308b67fdfbcd24028a0c513bc37&topicName=&ecpm=1000&audienceSegments=none&resolution=1080x2131&hostalias=dh-gcp-ads-adengine-ws-qa-az-7fh0&locationSource=IP&pincode=600119&subSlot=&bookedSubSlot=&ab=ECPM&partnerId=DH_APP&deliverySlab=1&userDeliverySlab=&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=1000&utmSource=&utmMedium=&utmCampaign=&appId=&autoPlayPref=3&installDeliverySlab=&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=1&topCampaignIds=1011720818%5E&topCampaignECPMs=1000&entityId=91581308b67fdfbcd24028a0c513bc37&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=&campaignPrdictedCtr=&productIds=&recoPolicy=&request_timestamp=1657192823&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=&variantName=&modelUuid=&networkSwitch=&topDirectCampaign=&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=&campaign_type=TEST_MODE&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=&requestIdDebug=e57c174ff0d3388d7193e3f32b841783&gender=&age=&ageRange=&orderTypeV2=0&idfa=&s2sBidId=&imputationType=&contentCreatorId=&scoringModel=&filteringModel=&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&reqTime=1657192823&\",
\"adFeedback\": { \"feedbackUrl\":
\"http://qa-money.newshunt.com/data-api/adfeedback?bannerId=1622953392&campaignId=1011720818&uniqueId=251d9d5eed35e1dd5119e10738114e0c&city=chennai\"
}, \"adClosedBeaconUrl\":
\"http://qa-money.newshunt.com/beaconEvents?uniqueId=13fe4efe5b09b14b16a6aca2ab29f799&adId=3399&campaignId=1163&adPlacement=list-masthead&partnerRef=&city=mumbai&state=maharashtra&country=india&clientId=j.dG4vakR3U3EvWG9AYNjJPc3NkZFlqdz09A&reqTime=1658380412&eventType=AD_CLOSE&partnerId=DH_APP&subSlot=&nextAdIndex=0&bookedPlacement=list-masthead&bookedSubSlot=&contentId=&contentCreatorId=\",
\"shareability\": null } \] }

## Mock Links

- <https://qa-money.newshunt.com/splashexit_image.json>

- <https://qa-money.newshunt.com/splashexit_mraid.json>

- <https://qa-money.newshunt.com/splashexit_html.json>
