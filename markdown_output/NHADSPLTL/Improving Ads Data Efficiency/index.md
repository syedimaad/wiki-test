17

# Requirement:

[https://docs.google.com/document/d/1ChudXsqXkicjJPLjDtVYc3YUF8RQsAT2RWQyPn9PxnY/edit#heading=h.awnd6ethl36o](https://docs.google.com/document/d/1ChudXsqXkicjJPLjDtVYc3YUF8RQsAT2RWQyPn9PxnY/edit#heading=h.awnd6ethl36o){card-appearance="inline"}

# Overview:

The motive of this task is to improve the ads event efficiency.

# Tasks:

1.  Convert 1st impression to event- today it is API driven **[(FE
    Only)]{style="color: rgb(0,102,68);"}**

2.  Allow retry for impression firing on every ad; It is fails allow for
    adding to queue and re trial- not only impression all tracking.
    **[(FE Only)]{style="color: rgb(0,102,68);"}**

    1.  Get Pre-impression events: Retrial in case of failure

3.  Pre-impression events for empty too **[(FE and
    BE)]{style="color: rgb(0,102,68);"}**

4.  All beacons to array **[(FE and
    BE)]{style="color: rgb(0,102,68);"}**

5.  ~~Ad Request Triggered- New Event as a beacon to content + Ads~~

# Scope:

Scope is both regular and evergreen ads. All the beacons will be changed
to objects to have more flexibility at the backend.

Components needs changes

- client

- adEngine

- cache-primer (response-creator) - cache two sets of response

- CDN (akamai) - consider app version for key

- cloud function - send response based on the app version

# Protocol:

- All the beacons will be changed to object as below.

  - Landing page url (action / tracker.data) remains same as there can
    be only one url.

- Post body data need to be sent in all the urls inside `internal`
  object.

- Changing param names for better naming convention.

- Empty ads need to support inflated and responded beacon urls.

- ~~A new event Ad Request Triggered to content + Ads BE~~

Sample Objectjson{ \"impressionUrls\":{ \"internal\":\[
\"https://qa-money.newshunt.com/impression?uniqueId=09d089d898d471e4574853f7356a9ff9&adId=4087&campaignId=1278&adPlacement=card-p1&partnerRef=&city=mumbai&state=maharashtra&country=india&clientId=3826976&reqTime=1653984720&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=card-p1&bookedSubSlot=&contentId=&contentCreatorId=\"
\], \"external\":\[ \"http://www.google.com\" \] } }

# BE Changes:

- Convert all beacons to object.

- Evergreen ads

  - Sending responded beacon in the `requestUrls` array.

  - Sending inflated and responded beacons for empty ads.

- Regular Ads

  - Sending inflated and responded beacons for empty and content ads.

# Handshake Changes:

1.  maxBeaconRetries

    1.  No of times to retry beacons on failure.

    2.  Failure will be non 200 status code.

2.  beaconRetryTimeOut

    1.  Time to wait for next retry attempt

    2.  Value will be in seconds

3.  ~~adRequestTriggeredBeaconUrl~~

    1.  ~~Add Ad request triggered beacon url & log to kudu~~

    2.  json{ \"genericAdEvents\": { \"adRequestTriggeredBeaconUrl\":
        \"http://qa-tr.dailyhunt.in/track/dailyhunt?eventName=AD_REQUEST_TRIGGERED\"
        } }

# Client Changes:

1.  Support beacons array for all the beacon events.

2.  ~~Ad Request Triggered event~~

    1.  ~~Fire~~ `adRequestTriggeredBeaconUrl` ~~to ads BE before an ad
        request.~~

    2.  ~~Send~~ `clientId , adPlacement, subslot, timestamp` ~~in post
        body params.~~

# Params Changes:

Below table contains the list of params changing.

  ------------------------------- ---------------------------------- ---------------------------------- ------------------------------------------
  **Event Name**                  **Current params**                 **New params**                     **Notes**
  AD_REQUEST                      requestUrl                         requestUrls                        
  AD_RESPONDED                    adRespondedBeaconUrl               adRespondedBeaconUrls              
  AD_INFLATED                     adInflatedBeaconUrl                adInflatedBeaconUrls               
  AD_IMPRESSION                   beaconUrl, beaconUrlAdditional     impressionUrls                     
  AD_CLICK                        landingUrl, landingUrlAdditional   clickUrls                          
  AD_LP_TIME_SPENT                adLPTimeSpentBeaconUrl             adLPTimeSpentBeaconUrls            
  AD_FEEDBACK                     feedbackUrl                        feedbackUrls                       
  AD_SHARE                        adShareBeaconUrl                   adShareBeaconUrls                  
  AD_REACTION                     adReactionBeaconUrl                adReactionBeaconUrls               
  AD_ERROR                        errorUrl                           errorUrls                          
  AD_IMMERSIVE_VIEW_ENTER         immersiveViewEnter                 immersiveViewEnter                 
  AD_IMMERSIVE_VIEW_EXIT          immersiveViewExit                  immersiveViewExit                  
  AD_IMMERSIVE_VIEW_CLICK         immersiveViewClick                 immersiveViewClick                 
  AD_NON_IMMERSIVE_VIEW_CLICK     nonImmersiveViewClick              nonImmersiveViewClick              
  AD_COMPANION_CLICK              companionClickTracking             companionClickUrls                 customCompanionTrackings, customTracking
  AD_COMPANION_IMPRESSION         companionBeaconTracking            companionImpressionUrls            customCompanionTrackings, customTracking
  AD_COMPANION_LP_TIME_SPENT      companionLPTimeSpentBeaconUrl      companionAdLPTimeSpentBeaconUrls   customCompanionTrackings, customTracking
  AD_INSTREAM_VDO_ERROR           errorBeaconUrl                     errorUrls                          customTracking
  AD_INSTREAM_VDO_LP_TIME_SPENT   adLPTimeSpentBeaconUrl             adLPTimeSpentBeaconUrls            customTracking
  AD_SDK_VIDEO_START              adVideoStart                       adVideoStart                       SDK native video events
  AD_SDK_VIDEO_END                adVideoEnd                         adVideoEnd                         SDK native video events
  AD_SDK_VIDEO_PAUSE              adVideoPause                       adVideoPause                       SDK native video events
  AD_SDK_VIDEO_PLAY               adVideoPlay                        adVideoPlay                        SDK native video events
  AD_SDK_VIDEO_MUTE               adVideoMute                        adVideoMute                        SDK native video events
  AD_SDK_VIDEO_UN_MUTE            adVideoUnMute                      adVideoUnMute                      SDK native video events
  AD_CLOSED                       adClosedBeaconUrl                  adClosedBeaconUrls                 
  ------------------------------- ---------------------------------- ---------------------------------- ------------------------------------------

# Regular Ad Response:

## Static Ads

json{ \"ads\": \[ { \"type\": \"imgLink\", \"aduid\": \"notId=ad-2525\",
\"srcUrlExpiry\": 60, \"width\": 1080, \"height\": 551,
\"card-position\": 1, \"positionWithTicker\": 1, \"min-ad-distance\": 4,
\"banner-fill\": \"fill-width\", \"bannerid\": \"1024\", \"adTemplate\":
\"L\", \"showOnlyImage\": false, \"id\":
\"fb2b41ccd92c69799c8c875a3935f9f0\", \"span\": 60,
\"useInternalBrowser\": \"false\", \"useWideViewPort\": true,
\"adCacheGood\": 1, \"adCacheAverage\": 1, \"adCacheSlow\": 1,
\"allowDelayedAdInsert\": true, \"adGroupId\":
\"38269766295d180e325c8.76577551\", \"adContext\": null, \"dedupId\":
\"fb2b41ccd92c69799c8c875a3935f9f0\", \"adTagPosition\": \"TOP_RIGHT\",
\"showBorder\": false, \"campaignId\": \"1024\", \"bannerId\": \"2525\",
\"isLargeAd\": false, \"errorUrls\": { \"internal\": \[
\"http://qa-money.newshunt.com/beaconEvents?uniqueId=fb2b41ccd92c69799c8c875a3935f9f0&adId=2525&campaignId=1024&adPlacement=card-p0&partnerRef=&city=mumbai&state=maharashtra&country=india&clientId=3826976&reqTime=1653985664&eventType=AD_ERROR&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=card-p0&bookedSubSlot=&contentId=&contentCreatorId=\"
\] }, \"largeAdDistance\": 8, \"position\": \"card-p0\",
\"showPlayIcon\": false, \"impressionUrls\": { \"internal\": \[
\"http://qa-money.newshunt.com/impression?uniqueId=fb2b41ccd92c69799c8c875a3935f9f0&adId=2525&campaignId=1024&adPlacement=card-p0&partnerRef=&city=mumbai&state=maharashtra&country=india&clientId=3826976&reqTime=1653985664&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=card-p0&bookedSubSlot=&contentId=&contentCreatorId=\"
\], \"external\": \[ \"http://www.google.com\" \] }, \"content\": {
\"imgLink\":
\"http://qa-money.newshunt.com/daedalus-banners/2525/1600780608_44389_990x505.jpg\",
\"itemSubtitle2\": { \"color\": \"#4caf79\", \"color-night\":
\"#ffffff\" }, \"reportText\": { \"color\": \"#798DED\",
\"color-night\": \"#FFFFFF\", \"background-color\": \"#40000000\",
\"background-color-night\": \"#40000000\", \"data\": \"Ad\" } },
\"action\":
\"https://qa-money.newshunt.com/click?clientId=3826976&uniqueId=fb2b41ccd92c69799c8c875a3935f9f0&adId=2525&campaignId=1024&adPlacement=card-p0&reqTime=1653985664&billingTypeId=2&orderId=127&forceTracker=&partnerRef=&city=mumbai&state=maharashtra&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=card-p0&bookedSubSlot=&contentId=&contentCreatorId=&\_\_oadest=http%3A%2F%2Fwww.google.com\",
\"clickUrls\": { \"external\": \[ \"http://www.google.com?click\" \] },
\"adLPTimeSpentBeaconUrls\": { \"internal\": \[
\"http://qa-money.newshunt.com/beaconEvents?uniqueId=fb2b41ccd92c69799c8c875a3935f9f0&adId=2525&campaignId=1024&adPlacement=card-p0&partnerRef=&city=mumbai&state=maharashtra&country=india&clientId=3826976&reqTime=1653985664&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=card-p0&bookedSubSlot=&contentId=&contentCreatorId=\"
\], \"external\": \[ \"http://www.google.com?lptime\" \] },
\"adRespondedBeaconUrls\": { \"internal\": \[
\"http://qa-money.newshunt.com/beaconEvents?uniqueId=fb2b41ccd92c69799c8c875a3935f9f0&adId=2525&campaignId=1024&adPlacement=card-p0&partnerRef=&city=mumbai&state=maharashtra&country=india&clientId=3826976&reqTime=1653985664&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=card-p0&bookedSubSlot=&contentId=&contentCreatorId=\"
\], \"external\": \[ \"http://www.google.com?responded\" \] },
\"adInflatedBeaconUrls\": { \"internal\": \[
\"http://qa-money.newshunt.com/beaconEvents?uniqueId=fb2b41ccd92c69799c8c875a3935f9f0&adId=2525&campaignId=1024&adPlacement=card-p0&partnerRef=&city=mumbai&state=maharashtra&country=india&clientId=3826976&reqTime=1653985664&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=card-p0&bookedSubSlot=&contentId=&contentCreatorId=\"
\], \"external\": \[ \"http://www.google.com?inflated\" \] },
\"adContextRules\": { \"selectionPriority\": 2, \"cacheType\":
\"session\", \"ttl\": 300, \"ruleGroup\": { \"respondedFor\": {
\"entityIds\": \[ \"nh-headlines\", \"91581308b67fdfbcd24028a0c513bc37\"
\], \"postId\": null } } }, \"adFeedback\": { \"feedbackUrls\": {
\"internal\": \[
\"http://qa-money.newshunt.com/data-api/adfeedback?bannerId=2525&campaignId=1024&uniqueId=fb2b41ccd92c69799c8c875a3935f9f0&city=mumbai\"
\], \"external\": \[ \"http://www.google.com?feedback\" \] } },
\"requestUrls\": { \"internal\": \[
\"http://qa-money.newshunt.com/fallback?clientid=3826976&req_time=31052022+13%3A57%3A44&paper=nh-headlines&item_category=&Gpscountry=india&Gpsstate=maharashtra&Gpscity=mumbai&IPcountry=&IPstate=&IPcity=&isp=others&user_os_platform=android&user_handset_maker=none&user_handset_model=none&user_id=&placement=card-p0&user_app_ver=18.3.1.2&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-p0&banner_id=2525&campaign_id=1024&user_connection=w&connection_speed=GOOD&user_os_ver=11.0&gaid=4401e561-39de-42ec-a2e2-4b4d56b5b8b0&item_publisher_language=&user_languages=en&oi=743&price_range=none&user_device_type=none&title=test+card-pp1&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=fb2b41ccd92c69799c8c875a3935f9f0&region=mumbai&mcc=&mnc=&lac=&cellid=&ip=180.179.82.9&adGroupId=38269766295d180e325c8.76577551&topicId=91581308b67fdfbcd24028a0c513bc37&topicName=&ecpm=0&audienceSegments=none&resolution=1080x2132&hostalias=dh-gcp-ads-adengine-ws-qa-az-7fh0&locationSource=IP&pincode=400024&subSlot=&bookedSubSlot=&ab=ECPM&partnerId=DH_APP&deliverySlab=1&userDeliverySlab=&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=0&utmSource=&utmMedium=&utmCampaign=&appId=&autoPlayPref=3&installDeliverySlab=&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=1&topCampaignIds=1024%5E&topCampaignECPMs=0&entityId=91581308b67fdfbcd24028a0c513bc37&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=&campaignPrdictedCtr=&productIds=&recoPolicy=&request_timestamp=1653985664&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=&variantName=&modelUuid=&networkSwitch=&topDirectCampaign=&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=&campaign_type=TEST_MODE&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=&requestIdDebug=cb54fba703715828ad9763ee9e60d726&gender=&age=&ageRange=&orderTypeV2=0&idfa=&s2sBidId=&imputationType=&contentCreatorId=&scoringModel=&filteringModel=&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&isRegUser=&hostAppId=DH_APP&userBadge=&reqTime=1653985664&\"
\], \"external\": \[ \"http://www.google.com?request\" \] },
\"shareability\": null }, { \"id\":
\"77d4ab01a3beb63e75e030ab88fcbdb5\", \"type\": \"empty\", \"position\":
\"supplement\", \"card-position\": 4, \"min-ad-distance\": 4,
\"largeAdDistance\": 8, \"banner-fill\": \"center\",
\"positionWithTicker\": 4, \"span\": 60, \"adGroupId\":
\"38269766295e4de526f05.70065732\", \"adTag\": \"sp1\",
\"adContextRules\": { \"selectionPriority\": 2, \"cacheType\":
\"session\", \"ttl\": 300, \"ruleGroup\": { \"respondedFor\": {
\"entityIds\": \[ \"nh-headlines\", \"91581308b67fdfbcd24028a0c513bc37\"
\], \"postId\": null } } }, \"impressionUrls\": { \"internal\": \[
\"http://qa-money.newshunt.com/impression?uniqueId=fb2b41ccd92c69799c8c875a3935f9f0&adId=2525&campaignId=1024&adPlacement=card-p0&partnerRef=&city=mumbai&state=maharashtra&country=india&clientId=3826976&reqTime=1653985664&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=card-p0&bookedSubSlot=&contentId=&contentCreatorId=\"
\], \"external\": \[ \"http://www.google.com\" \] },
\"adRespondedBeaconUrls\": { \"internal\": \[
\"http://qa-money.newshunt.com/beaconEvents?uniqueId=fb2b41ccd92c69799c8c875a3935f9f0&adId=2525&campaignId=1024&adPlacement=card-p0&partnerRef=&city=mumbai&state=maharashtra&country=india&clientId=3826976&reqTime=1653985664&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=card-p0&bookedSubSlot=&contentId=&contentCreatorId=\"
\], \"external\": \[ \"http://www.google.com?responded\" \] },
\"adInflatedBeaconUrls\": { \"internal\": \[
\"http://qa-money.newshunt.com/beaconEvents?uniqueId=fb2b41ccd92c69799c8c875a3935f9f0&adId=2525&campaignId=1024&adPlacement=card-p0&partnerRef=&city=mumbai&state=maharashtra&country=india&clientId=3826976&reqTime=1653985664&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=card-p0&bookedSubSlot=&contentId=&contentCreatorId=\"
\], \"external\": \[ \"http://www.google.com?inflated\" \] },
\"requestUrls\": { \"internal\": \[
\"http://qa-money.newshunt.com/fallback?clientid=3826976&req_time=31052022+13%3A57%3A44&paper=nh-headlines&item_category=&Gpscountry=india&Gpsstate=maharashtra&Gpscity=mumbai&IPcountry=&IPstate=&IPcity=&isp=others&user_os_platform=android&user_handset_maker=none&user_handset_model=none&user_id=&placement=card-p0&user_app_ver=18.3.1.2&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-p0&banner_id=2525&campaign_id=1024&user_connection=w&connection_speed=GOOD&user_os_ver=11.0&gaid=4401e561-39de-42ec-a2e2-4b4d56b5b8b0&item_publisher_language=&user_languages=en&oi=743&price_range=none&user_device_type=none&title=test+card-pp1&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=fb2b41ccd92c69799c8c875a3935f9f0&region=mumbai&mcc=&mnc=&lac=&cellid=&ip=180.179.82.9&adGroupId=38269766295d180e325c8.76577551&topicId=91581308b67fdfbcd24028a0c513bc37&topicName=&ecpm=0&audienceSegments=none&resolution=1080x2132&hostalias=dh-gcp-ads-adengine-ws-qa-az-7fh0&locationSource=IP&pincode=400024&subSlot=&bookedSubSlot=&ab=ECPM&partnerId=DH_APP&deliverySlab=1&userDeliverySlab=&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=0&utmSource=&utmMedium=&utmCampaign=&appId=&autoPlayPref=3&installDeliverySlab=&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=1&topCampaignIds=1024%5E&topCampaignECPMs=0&entityId=91581308b67fdfbcd24028a0c513bc37&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=&campaignPrdictedCtr=&productIds=&recoPolicy=&request_timestamp=1653985664&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=&variantName=&modelUuid=&networkSwitch=&topDirectCampaign=&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=&campaign_type=TEST_MODE&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=&requestIdDebug=cb54fba703715828ad9763ee9e60d726&gender=&age=&ageRange=&orderTypeV2=0&idfa=&s2sBidId=&imputationType=&contentCreatorId=&scoringModel=&filteringModel=&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&isRegUser=&hostAppId=DH_APP&userBadge=&reqTime=1653985664&\"
\], \"external\": \[ \"http://www.google.com?request\" \] } } \] }

## Out-stream Ads

json{ \"ads\": \[ { \"type\": \"external-sdk\", \"aduid\":
\"notId=ad-1679957612\", \"srcUrlExpiry\": 86400, \"adGroupId\":
\"123339173662a0a464e4dac0.35550495\", \"width\": 1080, \"height\": 607,
\"card-position\": 1, \"positionWithTicker\": 1, \"min-ad-distance\": 4,
\"bannerid\": \"98154\", \"adTemplate\": \"H\", \"showOnlyImage\":
false, \"id\": \"8352fba207c8e07ad143e7bf4685589d\", \"span\": 60,
\"useInternalBrowser\": \"false\", \"useWideViewPort\": false,
\"allowDelayedAdInsert\": true, \"adContext\": null, \"showTitle\":
false, \"needsBackupAds\": true, \"ignoreVideoDuration\": 480000,
\"adDistanceMs\": 180000, \"dedupId\":
\"8352fba207c8e07ad143e7bf4685589d\", \"adCacheGood\": 1,
\"adCacheAverage\": 1, \"adCacheSlow\": 1, \"isLive\": false,
\"showLearnMore\": true, \"adTagPosition\": \"BOTTOM_OVERLAY_LEFT\",
\"enableImmersiveView\": true, \"immersiveTransitionSpan\": 3,
\"immersiveViewDistance\": 2, \"showBorder\": false, \"campaignId\":
\"98154\", \"bannerId\": \"1679957612\", \"isLargeAd\": false,
\"largeAdDistance\": 8, \"position\": \"card-p0\", \"impressionUrls\": {
\"internal\": \[
\"http://stage-money.dailyhunt.in/impression?uniqueId=8352fba207c8e07ad143e7bf4685589d&adId=1679957612&campaignId=98154&adPlacement=card-p0&partnerRef=&city=&state=&country=india&clientId=1233391736&reqTime=1654695011&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=card-p0&bookedSubSlot=&contentId=&contentCreatorId=\"
\], \"external\": \[ \"http://www.googl.com/imp1\" \] }, \"clickUrls\":
{ \"external\": \[ \"http://www.googl.com/ck1\" \] },
\"customImmersiveViewEventTrackers\": { \"immersiveViewEnter\": {
\"internal\": \[
\"http://stage-money.dailyhunt.in/tracker?eventName=ImmersiveViewEnter&dhPayload=eyJjaWQiOiI5ODE1NCIsImFpZCI6IjE2Nzk5NTc2MTIiLCJ1aWQiOiI4MzUyZmJhMjA3YzhlMDdhZDE0M2U3YmY0Njg1NTg5ZCIsImFkeiI6ImNhcmQtcDAiLCJ1c3JpZCI6IjEyMzMzOTE3MzYiLCJydCI6MTY1NDY5NTAxMSwiaCI6IjRlYTFiOWYyNzY0YTk0ZDI5NzM4MTRlOWY5M2VjYmM5IiwicGFydG5lcklkIjoiREhfQVBQIiwic3ViU2xvdCI6bnVsbCwibmV4dEFkSW5kZXgiOm51bGx9\"
\] }, \"immersiveViewExit\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/tracker?eventName=ImmersiveViewExit&dhPayload=eyJjaWQiOiI5ODE1NCIsImFpZCI6IjE2Nzk5NTc2MTIiLCJ1aWQiOiI4MzUyZmJhMjA3YzhlMDdhZDE0M2U3YmY0Njg1NTg5ZCIsImFkeiI6ImNhcmQtcDAiLCJ1c3JpZCI6IjEyMzMzOTE3MzYiLCJydCI6MTY1NDY5NTAxMSwiaCI6IjRlYTFiOWYyNzY0YTk0ZDI5NzM4MTRlOWY5M2VjYmM5IiwicGFydG5lcklkIjoiREhfQVBQIiwic3ViU2xvdCI6bnVsbCwibmV4dEFkSW5kZXgiOm51bGx9\"
\] }, \"immersiveViewClick\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/tracker?eventName=ImmersiveViewClick&dhPayload=eyJjaWQiOiI5ODE1NCIsImFpZCI6IjE2Nzk5NTc2MTIiLCJ1aWQiOiI4MzUyZmJhMjA3YzhlMDdhZDE0M2U3YmY0Njg1NTg5ZCIsImFkeiI6ImNhcmQtcDAiLCJ1c3JpZCI6IjEyMzMzOTE3MzYiLCJydCI6MTY1NDY5NTAxMSwiaCI6IjRlYTFiOWYyNzY0YTk0ZDI5NzM4MTRlOWY5M2VjYmM5IiwicGFydG5lcklkIjoiREhfQVBQIiwic3ViU2xvdCI6bnVsbCwibmV4dEFkSW5kZXgiOm51bGx9\"
\] }, \"nonImmersiveViewClick\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/tracker?eventName=NonImmersiveViewClick&dhPayload=eyJjaWQiOiI5ODE1NCIsImFpZCI6IjE2Nzk5NTc2MTIiLCJ1aWQiOiI4MzUyZmJhMjA3YzhlMDdhZDE0M2U3YmY0Njg1NTg5ZCIsImFkeiI6ImNhcmQtcDAiLCJ1c3JpZCI6IjEyMzMzOTE3MzYiLCJydCI6MTY1NDY5NTAxMSwiaCI6IjRlYTFiOWYyNzY0YTk0ZDI5NzM4MTRlOWY5M2VjYmM5IiwicGFydG5lcklkIjoiREhfQVBQIiwic3ViU2xvdCI6bnVsbCwibmV4dEFkSW5kZXgiOm51bGx9\"
\] } }, \"customTracking\": { \"customCompanionTrackings\": {
\"1080x551\": { \"companionClickUrls\": { \"external\": \[
\"http://www.google.com/clk1\" \], \"internal\": \[
\"https://stage-money.dailyhunt.in/click?clientId=1233391736&uniqueId=123339173662a0a464ee7b37.71107294&adId=1943334868&campaignId=98154&adPlacement=video-companion&reqTime=&billingTypeId=3&orderId=57239&forceTracker=&partnerId=&\_\_oadest=\"
\] }, \"companionImpressionUrls\": { \"external\": \[
\"http://www.google.com/imp1\" \], \"internal\": \[
\"http://stage-money.dailyhunt.in/fallback?clientid=1233391736&req_time=08062022+19%3A00%3A11&paper=nh-headlines&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=Realme&user_handset_model=RMX1921&user_id=&placement=video-companion&user_app_ver=18.7.9&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedplacement=video-companion&banner_id=1943334868&campaign_id=98154&user_connection=w&connection_speed=GOOD&user_os_ver=11.0&gaid=af164412-b4d8-42dc-8e09-8c8a51c80a98&item_publisher_language=&user_languages=en%2C&oi=1092&price_range=none&user_device_type=none&title=vdo+2&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=123339173662a0a464ee7b37.71107294&region=&mcc=&mnc=&lac=&cellid=&ip=127.0.0.1&adGroupId=123339173662a0a464e4dac0.35550495&topicId=91581308b67fdfbcd24028a0c513bc37&topicName=&ecpm=0.01&audienceSegments=none&resolution=1080x2132&hostalias=VER-BLR-LT2816&locationSource=&pincode=&subSlot=&bookedSubSlot=&ab=ECPM&partnerId=DH_APP&deliverySlab=1&userDeliverySlab=&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=0.01&utmSource=&utmMedium=&utmCampaign=&appId=&autoPlayPref=3&installDeliverySlab=&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=1&topCampaignIds=98154%5E&topCampaignECPMs=0.01&entityId=91581308b67fdfbcd24028a0c513bc37&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&mastheadAdCount=0&sessionSource=ORGANIC&totalAdSessions=1&totalSeenAds=1&totalSessions=1&predictedInstallProbability=&campaignPrdictedCtr=&productIds=&recoPolicy=&request_timestamp=1654695011&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=&variantName=&modelUuid=&networkSwitch=&topDirectCampaign=&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=&campaign_type=LINEAR&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=&requestIdDebug=226c9aba32620805b104063c3b7bd88e&gender=&age=&ageRange=&orderTypeV2=0&idfa=&s2sBidId=&imputationType=&contentCreatorId=&scoringModel=&filteringModel=&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&isRegUser=&hostAppId=DH_APP&userBadge=&reqTime=1654695011&\",
\"http://stage-money.dailyhunt.in/impression?uniqueId=123339173662a0a464ee7b37.71107294&adId=1943334868&campaignId=98154&adPlacement=video-companion&reqTime=1654695011&partnerRef=&city=&state=&country=india&clientId=1233391736&partnerId=\"
\] }, \"companionAdLPTimeSpentBeaconUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=123339173662a0a464ee7b37.71107294&adId=1943334868&campaignId=98154&adPlacement=video-companion&partnerRef=&city=&state=&country=india&clientId=1233391736&reqTime=1654695011&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&nextAdIndex=&contentId=&contentCreatorId=\"
\] } } } }, \"adInflatedBeaconUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=8352fba207c8e07ad143e7bf4685589d&adId=1679957612&campaignId=98154&adPlacement=card-p0&partnerRef=&city=&state=&country=india&clientId=1233391736&reqTime=1654695011&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=card-p0&bookedSubSlot=&contentId=&contentCreatorId=\"
\] }, \"adRespondedBeaconUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=8352fba207c8e07ad143e7bf4685589d&adId=1679957612&campaignId=98154&adPlacement=card-p0&partnerRef=&city=&state=&country=india&clientId=1233391736&reqTime=1654695011&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=card-p0&bookedSubSlot=&contentId=&contentCreatorId=\"
\] }, \"errorUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=8352fba207c8e07ad143e7bf4685589d&adId=1679957612&campaignId=98154&adPlacement=card-p0&partnerRef=&city=&state=&country=india&clientId=1233391736&reqTime=1654695011&eventType=AD_ERROR&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=card-p0&bookedSubSlot=&contentId=&contentCreatorId=\"
\] }, \"adFeedback\": { \"feedbackUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/data-api/adfeedback?bannerId=1679957612&campaignId=98154&uniqueId=8352fba207c8e07ad143e7bf4685589d&city=\"
\] } }, \"requestUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/fallback?clientid=1233391736&req_time=08062022+19%3A00%3A11&paper=nh-headlines&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=Realme&user_handset_model=RMX1921&user_id=&placement=card-p0&user_app_ver=18.7.9&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-p0&banner_id=1679957612&campaign_id=98154&user_connection=w&connection_speed=GOOD&user_os_ver=11.0&gaid=af164412-b4d8-42dc-8e09-8c8a51c80a98&item_publisher_language=&user_languages=en%2C&oi=1092&price_range=none&user_device_type=none&title=vdo+2&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=8352fba207c8e07ad143e7bf4685589d&region=&mcc=&mnc=&lac=&cellid=&ip=127.0.0.1&adGroupId=123339173662a0a464e4dac0.35550495&topicId=91581308b67fdfbcd24028a0c513bc37&topicName=&ecpm=0.01&audienceSegments=none&resolution=1080x2132&hostalias=VER-BLR-LT2816&locationSource=&pincode=&subSlot=&bookedSubSlot=&ab=ECPM&partnerId=DH_APP&deliverySlab=1&userDeliverySlab=&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=0.01&utmSource=&utmMedium=&utmCampaign=&appId=&autoPlayPref=3&installDeliverySlab=&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=1&topCampaignIds=98154%5E&topCampaignECPMs=0.01&entityId=91581308b67fdfbcd24028a0c513bc37&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&mastheadAdCount=0&sessionSource=ORGANIC&totalAdSessions=1&totalSeenAds=1&totalSessions=1&predictedInstallProbability=&campaignPrdictedCtr=&productIds=&recoPolicy=&request_timestamp=1654695011&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=&variantName=&modelUuid=&networkSwitch=&topDirectCampaign=&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=&campaign_type=LINEAR&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=&requestIdDebug=226c9aba32620805b104063c3b7bd88e&gender=&age=&ageRange=&orderTypeV2=0&idfa=&s2sBidId=&imputationType=&contentCreatorId=&scoringModel=&filteringModel=&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&isRegUser=&hostAppId=DH_APP&userBadge=&reqTime=1654695011&\"
\] }, \"adLPTimeSpentBeaconUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=8352fba207c8e07ad143e7bf4685589d&adId=1679957612&campaignId=98154&adPlacement=card-p0&partnerRef=&city=&state=&country=india&clientId=1233391736&reqTime=1654695011&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=card-p0&bookedSubSlot=&contentId=&contentCreatorId=\"
\] }, \"sdk-order\": 1, \"external\": \[ { \"tagURL\":
\"http%3A%2F%2Fstage-money.dailyhunt.in%2Fgetvast%3FclientId%3D1233391736%26uniqueId%3D8352fba207c8e07ad143e7bf4685589d%26adId%3D1679957612%26campaignId%3D98154%26adPlacement%3Dcard-p0%26cap%3D0%26reset%3D0%26billingTypeId%3D3%26orderId%3D57239%26forceTracker%3D%26gaid%3Daf164412-b4d8-42dc-8e09-8c8a51c80a98%26gaidOptoutStatus%3D0%26reqTime%3D1654695011%26partnerId%3DDH_APP%26subSlot%3D%26nextAdIndex%3D%26bookedPlacement%3Dcard-p0%26bookedSubSlot%3D%26clientVersions%3D18.7.9%26os%3Dandroid%26ucq%3Dgood%26resolution%3D1080x2132%26ciu_szs%3D1080x551%26companionId%3D1943334868\",
\"data\": \"IMA-SDK\" } \], \"landingUrl\": null, \"content\": {
\"itemSubtitle2\": { \"color\": \"#4caf79\", \"color-night\":
\"#ffffff\" }, \"reportText\": { \"color\": \"#FFFFFF\",
\"color-night\": \"#FFFFFF\", \"background-color\": \"#40000000\",
\"background-color-night\": \"#40000000\", \"data\": \"Ad\" },
\"thumbnailImageUrl\":
\"http://adenginestage.dailyhunt.in/daedalus-banners/1679957612/1654524737_56651_990x505.jpg\",
\"learnMoreText\": { \"color\": \"#ffffff\", \"color-night\":
\"#ffffff\", \"data\": \"Learn More\" } }, \"brand\": { \"brandTitle\":
{ \"color\": \"#202020\", \"color-night\": \"#ffffff\", \"data\":
\"Test\" }, \"brandSubTitle\": { \"color\": \"#202020\",
\"color-night\": \"#ffffff\" }, \"brandFallbackText\": { \"color\":
\"#ffffff\", \"color-night\": \"#ffffff\", \"background-color\":
\"#ebab05\", \"background-color-night\": \"#ebab05\", \"type\": \"S\",
\"data\": \"T\" } }, \"action\":
\"https://stage-money.dailyhunt.in/click?clientId=1233391736&uniqueId=8352fba207c8e07ad143e7bf4685589d&adId=1679957612&campaignId=98154&adPlacement=card-p0&reqTime=1654695011&billingTypeId=3&orderId=57239&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=card-p0&bookedSubSlot=&contentId=&contentCreatorId=&\_\_oadest=http%3A%2F%2Fwww.google.com\",
\"adContextRules\": { \"selectionPriority\": 2, \"cacheType\":
\"session\", \"ttl\": 300, \"ruleGroup\": { \"rules\": \[ {
\"ruleItems\": \[ { \"operand\": -1, \"keys\": \[
\"unsafeForVideoAd:true\" \] } \] } \], \"respondedFor\": {
\"entityIds\": \[ \"nh-headlines\", \"91581308b67fdfbcd24028a0c513bc37\"
\], \"postId\": null } } }, \"shareability\": null }, { \"id\":
\"6fcade40421abe611c8f7391a4ac16d3\", \"type\": \"empty\", \"position\":
\"card-p0\", \"card-position\": 1, \"min-ad-distance\": 4,
\"largeAdDistance\": 8, \"banner-fill\": \"center\",
\"positionWithTicker\": 1, \"span\": 60, \"adGroupId\":
\"123339173662a0a464e4dac0.35550495\", \"impressionUrls\": {
\"internal\": \[
\"http://stage-money.dailyhunt.in/impression?uniqueId=6fcade40421abe611c8f7391a4ac16d3&adId=53495&campaignId=-2&adPlacement=card-p0&partnerRef=&city=&state=&country=india&clientId=1233391736&reqTime=1654695011&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=card-p0&bookedSubSlot=&contentId=&contentCreatorId=\"
\] }, \"requestUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/fallback?clientid=1233391736&req_time=08062022+19%3A00%3A11&paper=nh-headlines&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=Realme&user_handset_model=RMX1921&user_id=&placement=card-p0&user_app_ver=18.7.9&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-p0&banner_id=53495&campaign_id=-2&user_connection=w&connection_speed=GOOD&user_os_ver=11.0&gaid=af164412-b4d8-42dc-8e09-8c8a51c80a98&item_publisher_language=&user_languages=en%2C&oi=1092&price_range=none&user_device_type=none&title=Empty+Banner&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=6fcade40421abe611c8f7391a4ac16d3&region=&mcc=&mnc=&lac=&cellid=&ip=127.0.0.1&adGroupId=123339173662a0a464e4dac0.35550495&topicId=91581308b67fdfbcd24028a0c513bc37&topicName=&ecpm=0&audienceSegments=none&resolution=1080x2132&hostalias=VER-BLR-LT2816&locationSource=&pincode=&subSlot=&bookedSubSlot=&ab=ECPM&partnerId=DH_APP&deliverySlab=1&userDeliverySlab=&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=&articleId=&vpod=&v_ecpm=0&utmSource=&utmMedium=&utmCampaign=&appId=&autoPlayPref=3&installDeliverySlab=&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=1&topCampaignIds=&topCampaignECPMs=&entityId=91581308b67fdfbcd24028a0c513bc37&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&mastheadAdCount=0&sessionSource=ORGANIC&totalAdSessions=1&totalSeenAds=1&totalSessions=1&predictedInstallProbability=&campaignPrdictedCtr=&productIds=&recoPolicy=&request_timestamp=1654695011&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=&variantName=&modelUuid=&networkSwitch=&topDirectCampaign=&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=&campaign_type=&campaign_level=&interleaved_competition=&isRollUp=&requestIdDebug=226c9aba32620805b104063c3b7bd88e&gender=&age=&ageRange=&orderTypeV2=1&idfa=&s2sBidId=&imputationType=&contentCreatorId=&scoringModel=&filteringModel=&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&isRegUser=&hostAppId=DH_APP&userBadge=&reqTime=1654695011&\"
\] }, \"adInflatedBeaconUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=6fcade40421abe611c8f7391a4ac16d3&adId=53495&campaignId=-2&adPlacement=card-p0&partnerRef=&city=&state=&country=india&clientId=1233391736&reqTime=1654695011&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=card-p0&bookedSubSlot=&contentId=&contentCreatorId=\"
\] }, \"adRespondedBeaconUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=6fcade40421abe611c8f7391a4ac16d3&adId=53495&campaignId=-2&adPlacement=card-p0&partnerRef=&city=&state=&country=india&clientId=1233391736&reqTime=1654695011&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=card-p0&bookedSubSlot=&contentId=&contentCreatorId=\"
\] }, \"sdk-order\": 2, \"adContextRules\": { \"selectionPriority\": 2,
\"cacheType\": \"session\", \"ttl\": 300, \"ruleGroup\": { \"rules\":
\[\], \"respondedFor\": { \"entityIds\": \[ \"nh-headlines\",
\"91581308b67fdfbcd24028a0c513bc37\" \], \"postId\": null } } } } \] }

## Instream-vdo Ads

json{ \"ads\": \[ { \"type\": \"external-sdk\", \"aduid\":
\"notId=ad-1679957612\", \"srcUrlExpiry\": 86400, \"adGroupId\":
\"123339173662a0a47010fb45.34181855\", \"width\": 1080, \"height\": 607,
\"card-position\": 4, \"positionWithTicker\": 4, \"min-ad-distance\": 4,
\"bannerid\": \"98154\", \"adTemplate\": \"H\", \"showOnlyImage\":
false, \"id\": \"4f102cba93fc772a7b71fadaea34a8e5\", \"span\": 60,
\"useInternalBrowser\": \"false\", \"useWideViewPort\": false,
\"allowDelayedAdInsert\": true, \"adContext\": \"b32038204\",
\"showTitle\": false, \"needsBackupAds\": true, \"ignoreVideoDuration\":
480000, \"adDistanceMs\": 180000, \"dedupId\":
\"4f102cba93fc772a7b71fadaea34a8e5\", \"adCacheGood\": 1,
\"adCacheAverage\": 1, \"adCacheSlow\": 1, \"isLive\": false,
\"showLearnMore\": true, \"adTagPosition\": \"BOTTOM_OVERLAY_LEFT\",
\"showBorder\": false, \"campaignId\": \"98154\", \"bannerId\":
\"1679957612\", \"isLargeAd\": false, \"largeAdDistance\": 8,
\"position\": \"instream-vdo\", \"customTracking\": { \"tracking\": \[ {
\"id\": \"start\", \"impressionUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/impression?uniqueId=4f102cba93fc772a7b71fadaea34a8e5_mid1&adId=1679957612&campaignId=98154&adPlacement=instream-vdo&city=&state=&country=india&clientId=1233391736&reqTime=1654695014&partnerId=DH_APP\"
\] }, \"adLPTimeSpentBeaconUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=4f102cba93fc772a7b71fadaea34a8e5_mid1&adId=1679957612&campaignId=98154&adPlacement=instream-vdo&city=&state=&country=india&clientId=1233391736&reqTime=1654695014&partnerId=DH_APP&eventType=AD_LP_TIME_SPENT\"
\] }, \"customCompanionTrackings\": {
\"companionAdLPTimeSpentBeaconUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=123339173662a0a4701b79a3.66517760&adId=1943334868&campaignId=98154&adPlacement=video-companion&partnerRef=&city=&state=&country=india&clientId=1233391736&reqTime=1654695014&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&nextAdIndex=&contentId=b32038204&contentCreatorId=\"
\] }, \"companionClickUrls\": { \"external\": \[
\"http://www.google.com/clk1\" \] } } }, { \"id\": \"mid1\",
\"impressionUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/impression?uniqueId=4f102cba93fc772a7b71fadaea34a8e5_mid1&adId=1679957612&campaignId=98154&adPlacement=instream-vdo&city=&state=&country=india&clientId=1233391736&reqTime=1654695014&partnerId=DH_APP\"
\] }, \"adLPTimeSpentBeaconUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=4f102cba93fc772a7b71fadaea34a8e5_mid1&adId=1679957612&campaignId=98154&adPlacement=instream-vdo&city=&state=&country=india&clientId=1233391736&reqTime=1654695014&partnerId=DH_APP&eventType=AD_LP_TIME_SPENT\"
\] }, \"customCompanionTrackings\": {
\"companionAdLPTimeSpentBeaconUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=123339173662a0a4701b79a3.66517760&adId=1943334868&campaignId=98154&adPlacement=video-companion&partnerRef=&city=&state=&country=india&clientId=1233391736&reqTime=1654695014&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&nextAdIndex=&contentId=b32038204&contentCreatorId=\"
\] }, \"companionClickUrls\": { \"external\": \[
\"http://www.google.com/clk1\" \] } } }, { \"id\": \"mid2\",
\"impressionUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/impression?uniqueId=4f102cba93fc772a7b71fadaea34a8e5_mid2&adId=1679957612&campaignId=98154&adPlacement=instream-vdo&city=&state=&country=india&clientId=1233391736&reqTime=1654695014&partnerId=DH_APP\"
\] }, \"adLPTimeSpentBeaconUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=4f102cba93fc772a7b71fadaea34a8e5_mid2&adId=1679957612&campaignId=98154&adPlacement=instream-vdo&city=&state=&country=india&clientId=1233391736&reqTime=1654695014&partnerId=DH_APP&eventType=AD_LP_TIME_SPENT\"
\] }, \"customCompanionTrackings\": {
\"companionAdLPTimeSpentBeaconUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=123339173662a0a4701c9a95.67677085&adId=1943334868&campaignId=98154&adPlacement=video-companion&partnerRef=&city=&state=&country=india&clientId=1233391736&reqTime=1654695014&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&nextAdIndex=&contentId=b32038204&contentCreatorId=\"
\] }, \"companionClickUrls\": { \"external\": \[
\"http://www.google.com/clk1\" \] } } }, { \"id\": \"mid3\",
\"impressionUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/impression?uniqueId=4f102cba93fc772a7b71fadaea34a8e5_mid3&adId=1679957612&campaignId=98154&adPlacement=instream-vdo&city=&state=&country=india&clientId=1233391736&reqTime=1654695014&partnerId=DH_APP\"
\] }, \"adLPTimeSpentBeaconUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=4f102cba93fc772a7b71fadaea34a8e5_mid3&adId=1679957612&campaignId=98154&adPlacement=instream-vdo&city=&state=&country=india&clientId=1233391736&reqTime=1654695014&partnerId=DH_APP&eventType=AD_LP_TIME_SPENT\"
\] }, \"customCompanionTrackings\": {
\"companionAdLPTimeSpentBeaconUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=123339173662a0a4701d6936.36248057&adId=1943334868&campaignId=98154&adPlacement=video-companion&partnerRef=&city=&state=&country=india&clientId=1233391736&reqTime=1654695014&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&nextAdIndex=&contentId=b32038204&contentCreatorId=\"
\] }, \"companionClickUrls\": { \"external\": \[
\"http://www.google.com/clk1\" \] } } }, { \"id\": \"mid4\",
\"impressionUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/impression?uniqueId=4f102cba93fc772a7b71fadaea34a8e5_mid4&adId=1679957612&campaignId=98154&adPlacement=instream-vdo&city=&state=&country=india&clientId=1233391736&reqTime=1654695014&partnerId=DH_APP\"
\] }, \"adLPTimeSpentBeaconUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=4f102cba93fc772a7b71fadaea34a8e5_mid4&adId=1679957612&campaignId=98154&adPlacement=instream-vdo&city=&state=&country=india&clientId=1233391736&reqTime=1654695014&partnerId=DH_APP&eventType=AD_LP_TIME_SPENT\"
\] }, \"customCompanionTrackings\": {
\"companionAdLPTimeSpentBeaconUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=123339173662a0a4701e38b2.07095736&adId=1943334868&campaignId=98154&adPlacement=video-companion&partnerRef=&city=&state=&country=india&clientId=1233391736&reqTime=1654695014&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&nextAdIndex=&contentId=b32038204&contentCreatorId=\"
\] }, \"companionClickUrls\": { \"external\": \[
\"http://www.google.com/clk1\" \] } } }, { \"id\": \"mid5\",
\"impressionUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/impression?uniqueId=4f102cba93fc772a7b71fadaea34a8e5_mid5&adId=1679957612&campaignId=98154&adPlacement=instream-vdo&city=&state=&country=india&clientId=1233391736&reqTime=1654695014&partnerId=DH_APP\"
\] }, \"adLPTimeSpentBeaconUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=4f102cba93fc772a7b71fadaea34a8e5_mid5&adId=1679957612&campaignId=98154&adPlacement=instream-vdo&city=&state=&country=india&clientId=1233391736&reqTime=1654695014&partnerId=DH_APP&eventType=AD_LP_TIME_SPENT\"
\] }, \"customCompanionTrackings\": {
\"companionAdLPTimeSpentBeaconUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=123339173662a0a4701ee945.65812775&adId=1943334868&campaignId=98154&adPlacement=video-companion&partnerRef=&city=&state=&country=india&clientId=1233391736&reqTime=1654695014&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&nextAdIndex=&contentId=b32038204&contentCreatorId=\"
\] }, \"companionClickUrls\": { \"external\": \[
\"http://www.google.com/clk1\" \] } } }, { \"id\": \"mid6\",
\"impressionUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/impression?uniqueId=4f102cba93fc772a7b71fadaea34a8e5_mid6&adId=1679957612&campaignId=98154&adPlacement=instream-vdo&city=&state=&country=india&clientId=1233391736&reqTime=1654695014&partnerId=DH_APP\"
\] }, \"adLPTimeSpentBeaconUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=4f102cba93fc772a7b71fadaea34a8e5_mid6&adId=1679957612&campaignId=98154&adPlacement=instream-vdo&city=&state=&country=india&clientId=1233391736&reqTime=1654695014&partnerId=DH_APP&eventType=AD_LP_TIME_SPENT\"
\] }, \"customCompanionTrackings\": {
\"companionAdLPTimeSpentBeaconUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=123339173662a0a4701f5a78.44565239&adId=1943334868&campaignId=98154&adPlacement=video-companion&partnerRef=&city=&state=&country=india&clientId=1233391736&reqTime=1654695014&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&nextAdIndex=&contentId=b32038204&contentCreatorId=\"
\] }, \"companionClickUrls\": { \"external\": \[
\"http://www.google.com/clk1\" \] } } } \] }, \"errorUrls\": {
\"internal\": \[
\"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=4f102cba93fc772a7b71fadaea34a8e5&adId=1679957612&campaignId=98154&adPlacement=instream-vdo&partnerRef=&city=&state=&country=india&clientId=1233391736&reqTime=1654695014&eventType=AD_ERROR&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=instream-vdo&bookedSubSlot=&contentId=b32038204&contentCreatorId=\"
\] }, \"adFeedback\": { \"feedbackUrls\": { \"internal\": \[
\"http://stage-money.dailyhunt.in/data-api/adfeedback?bannerId=1679957612&campaignId=98154&uniqueId=4f102cba93fc772a7b71fadaea34a8e5&city=\"
\] } }, \"sdk-order\": 1, \"landingUrl\": null, \"external\": \[ {
\"tagURL\":
\"http%3A%2F%2Fstage-money.dailyhunt.in%2Fgetvmap%3FuniqueId%3D4f102cba93fc772a7b71fadaea34a8e5%26vmapPayload%3DeyJtaWQxIjp7ImEiOiIxNjc5OTU3NjEyIiwiYyI6Ijk4MTU0IiwibyI6IjU3MjM5Iiwib2ZmIjoiMDA6MDA6MjAuMDAwIiwicnQiOjE2NTQ2OTUwMTQsImJ0IjoiMyIsImNhcCI6IjAiLCJjeiI6IjEwODB4NTUxIiwiY29JZCI6IjE5NDMzMzQ4NjgiLCJjb1VuSWQiOiIxMjMzMzkxNzM2NjJhMGE0NzAxYjc5YTMuNjY1MTc3NjAifSwibWlkMiI6eyJhIjoiMTY3OTk1NzYxMiIsImMiOiI5ODE1NCIsIm8iOiI1NzIzOSIsIm9mZiI6IjAwOjA0OjAwLjAwMCIsInJ0IjoxNjU0Njk1MDE0LCJidCI6IjMiLCJjYXAiOiIwIiwiY3oiOiIxMDgweDU1MSIsImNvSWQiOiIxOTQzMzM0ODY4IiwiY29VbklkIjoiMTIzMzM5MTczNjYyYTBhNDcwMWM5YTk1LjY3Njc3MDg1In0sIm1pZDMiOnsiYSI6IjE2Nzk5NTc2MTIiLCJjIjoiOTgxNTQiLCJvIjoiNTcyMzkiLCJvZmYiOiIwMDowODowMC4wMDAiLCJydCI6MTY1NDY5NTAxNCwiYnQiOiIzIiwiY2FwIjoiMCIsImN6IjoiMTA4MHg1NTEiLCJjb0lkIjoiMTk0MzMzNDg2OCIsImNvVW5JZCI6IjEyMzMzOTE3MzY2MmEwYTQ3MDFkNjkzNi4zNjI0ODA1NyJ9LCJtaWQ0Ijp7ImEiOiIxNjc5OTU3NjEyIiwiYyI6Ijk4MTU0IiwibyI6IjU3MjM5Iiwib2ZmIjoiMDA6MTI6MDAuMDAwIiwicnQiOjE2NTQ2OTUwMTQsImJ0IjoiMyIsImNhcCI6IjAiLCJjeiI6IjEwODB4NTUxIiwiY29JZCI6IjE5NDMzMzQ4NjgiLCJjb1VuSWQiOiIxMjMzMzkxNzM2NjJhMGE0NzAxZTM4YjIuMDcwOTU3MzYifSwibWlkNSI6eyJhIjoiMTY3OTk1NzYxMiIsImMiOiI5ODE1NCIsIm8iOiI1NzIzOSIsIm9mZiI6IjAwOjE2OjAwLjAwMCIsInJ0IjoxNjU0Njk1MDE0LCJidCI6IjMiLCJjYXAiOiIwIiwiY3oiOiIxMDgweDU1MSIsImNvSWQiOiIxOTQzMzM0ODY4IiwiY29VbklkIjoiMTIzMzM5MTczNjYyYTBhNDcwMWVlOTQ1LjY1ODEyNzc1In0sIm1pZDYiOnsiYSI6IjE2Nzk5NTc2MTIiLCJjIjoiOTgxNTQiLCJvIjoiNTcyMzkiLCJvZmYiOiIwMDoyMDowMC4wMDAiLCJydCI6MTY1NDY5NTAxNCwiYnQiOiIzIiwiY2FwIjoiMCIsImN6IjoiMTA4MHg1NTEiLCJjb0lkIjoiMTk0MzMzNDg2OCIsImNvVW5JZCI6IjEyMzMzOTE3MzY2MmEwYTQ3MDFmNWE3OC40NDU2NTIzOSJ9fQ%3D%3D%26clientId%3D1233391736%26requestUrl%3Dhttp%253A%252F%252Fstage-money.dailyhunt.in%252Ffallback%253Fclientid%253D1233391736%2526req_time%253D08062022%252B19%25253A00%25253A14%2526paper%253D%2526item_category%253D%2526Gpscountry%253Dindia%2526Gpsstate%253D%2526Gpscity%253D%2526IPcountry%253D%2526IPstate%253D%2526IPcity%253D%2526isp%253D%2526user_os_platform%253Dandroid%2526user_handset_maker%253DRealme%2526user_handset_model%253DRMX1921%2526user_id%253D%2526placement%253Dinstream-vdo%2526user_app_ver%253D18.7.9%2526banner_rotation_type%253D0%2526bannerSelectedBy%253DadEngine%2526bookedPlacement%253Dinstream-vdo%2526banner_id%253D1679957612%2526campaign_id%253D98154%2526user_connection%253Dw%2526connection_speed%253DGOOD%2526user_os_ver%253D11.0%2526gaid%253Daf164412-b4d8-42dc-8e09-8c8a51c80a98%2526item_publisher_language%253D%2526user_languages%253Den%25252C%2526oi%253D1092%2526price_range%253Dnone%2526user_device_type%253Dnone%2526title%253Dvdo%252B2%2526promoVdoId%253D%2526promoTopic%253D%2526latitude%253DNA%2526longitude%253DNA%2526uniqueId%253D4f102cba93fc772a7b71fadaea34a8e5%2526region%253D%2526mcc%253D%2526mnc%253D%2526lac%253D%2526cellid%253D%2526ip%253D127.0.0.1%2526adGroupId%253D123339173662a0a47010fb45.34181855%2526topicId%253D91581308b67fdfbcd24028a0c513bc37%2526topicName%253D%2526ecpm%253D0.01%2526audienceSegments%253Dnone%2526resolution%253D1080x2132%2526hostalias%253DVER-BLR-LT2816%2526locationSource%253D%2526pincode%253D%2526subSlot%253D%2526bookedSubSlot%253D%2526ab%253DECPM%2526partnerId%253DDH_APP%2526deliverySlab%253D1%2526userDeliverySlab%253D%2526dhTvChannelId%253D%2526dhTvType%253D%2526buzzContentpartner%253Dtheprint_theprint%2526dhTvSourcekey%253Dtheprint%2526dhTvRelevance%253D%2526dhTvUrgency%253D%2526dhTvPartyLeaning%253D%2526pubName%253DDH%2526vdoGroupKey%253D%2526nthImpression%253D1%2526articleId%253Db32038204%2526vpod%253D%2526v_ecpm%253D0.01%2526utmSource%253D%2526utmMedium%253D%2526utmCampaign%253D%2526appId%253D%2526autoPlayPref%253D3%2526installDeliverySlab%253D%2526installCpi%253D%2526secondBidderCampaign%253D%2526secondBidderECPM%253D%2526optimisedBy%253D1%2526topCampaignIds%253D98154%25255E%2526topCampaignECPMs%253D0.01%2526entityId%253D91581308b67fdfbcd24028a0c513bc37%2526entityType%253DHASHTAG%2526entitySubtype%253D%2526contentContext%253D%2526parentContentContext%253D%2526sourceType%253DOGC%2526isHubExclusiveAdRequest%253D%2526mastheadAdCount%253D0%2526sessionSource%253DORGANIC%2526totalAdSessions%253D1%2526totalSeenAds%253D6%2526totalSessions%253D1%2526predictedInstallProbability%253D%2526campaignPrdictedCtr%253D%2526productIds%253D%2526recoPolicy%253D%2526request_timestamp%253D1654695014%2526next_ad_index%253D%2526feed_refresh_count%253D%2526feed_type%253D%2526feed_id%253D%2526ad_extras%253D%2526sub_feed_id%253D%2526profile_type%253D%2526contentId%253Db32038204%2526event_type%253DAD_REQUEST%2526preCalibratedProbability%253D%2526variantName%253D%2526modelUuid%253D%2526networkSwitch%253D%2526topDirectCampaign%253D%2526isAdLoadEnabled%253D%2526lang_affinity%253D%2526is_interleaved%253D0%2526boost_factor%253D1%2526interleave_campaign_daedalus_config%253D0%2526expected_video_watch_duration%253D%2526campaign_type%253DLINEAR%2526campaign_level%253DLEVEL_1%2526interleaved_competition%253D%2526isRollUp%253D%2526requestIdDebug%253D550425b590af0e0ed67c905172af8ada%2526gender%253D%2526age%253D%2526ageRange%253D%2526orderTypeV2%253D0%2526idfa%253D%2526s2sBidId%253D%2526imputationType%253D%2526contentCreatorId%253D%2526scoringModel%253D%2526filteringModel%253D%2526requestData%253D%25257B%252522products%252522%25253A%25255B%25255D%25257D%2526locUpdate%253D%2526isRegUser%253D%2526hostAppId%253DDH_APP%2526userBadge%253D%2526reqTime%253D1654695014%2526%26gaid%3Daf164412-b4d8-42dc-8e09-8c8a51c80a98%26gaidOptoutStatus%3D0%26adPlacement%3Dinstream-vdo%26partnerId%3DDH_APP%26resolution%3D1080x2132%26ciu_szs%3D1080x551\",
\"data\": \"IMA-SDK\" } \], \"adContextRules\": { \"selectionPriority\":
2, \"cacheType\": \"session\", \"ttl\": 300, \"ruleGroup\": { \"rules\":
\[ { \"ruleItems\": \[ { \"operand\": -1, \"keys\": \[
\"unsafeForVideoAd:true\" \] } \] } \], \"respondedFor\": {
\"entityIds\": \[ \"dhbddd828ebcc2462c931b6986dfe492c8\",
\"nh-headlines\", \"91581308b67fdfbcd24028a0c513bc37\" \], \"postId\":
\"b32038204\" } } }, \"shareability\": null } \] }

# Evergreen Ad Response:

json{ \"ads\": \[ { \"supportedZones\": { \"card-p0\": { \"DEFAULT\": {
\"priority\": 10, \"weight\": 5, \"card-position\": 1,
\"positionWithTicker\": 1 } }, \"card-p1\": { \"DEFAULT\": {
\"priority\": 10, \"weight\": 5, \"card-position\": 7,
\"positionWithTicker\": 7, \"min-ad-distance\": 7, \"largeAdDistance\":
7 } }, \"card-pp1\": { \"pp1_1\": { \"priority\": 10, \"weight\": 5,
\"card-position\": 3, \"positionWithTicker\": 3, \"min-ad-distance\": 3,
\"largeAdDistance\": 3 }, \"pp1_2\": { \"priority\": 10, \"weight\": 5,
\"card-position\": 4, \"positionWithTicker\": 4, \"min-ad-distance\": 4,
\"largeAdDistance\": 4 }, \"pp1_3\": { \"priority\": 10, \"weight\": 5,
\"card-position\": 5, \"positionWithTicker\": 5, \"min-ad-distance\": 5,
\"largeAdDistance\": 5 }, \"pp1_4\": { \"priority\": 10, \"weight\": 5,
\"card-position\": 5, \"positionWithTicker\": 5, \"min-ad-distance\": 5,
\"largeAdDistance\": 5 } }, \"storypage\": { \"DEFAULT\": {
\"priority\": 10, \"weight\": 5 } } }, \"type\": \"imgLink\",
\"startepoch\": 1652745600, \"endepoch\": 1672509540, \"width\":
\"1080\", \"height\": \"551\", \"id\": \"\--CL_UUID\--\", \"adGroupId\":
\"755a37403932dcd9d215298febefd772\", \"useInternalBrowser\": \"false\",
\"allowDelayedAdInsert\": true, \"adTagPosition\": \"TOP_RIGHT\",
\"campaignId\": \"1285\", \"bannerId\": \"4022\", \"isLargeAd\": false,
\"adBorderColor\": \"#33dea1\", \"containerBackgroundColor\":
\"#e84ea2\", \"content\": { \"imgLink\":
\"http://qa-money.newshunt.com/daedalus-banners/4022/1653295501_69477_990x505.webp\",
\"itemSubtitle2\": { \"color\": \"#4caf79\", \"color-night\":
\"#ffffff\", \"data\": \"click\" }, \"reportText\": { \"color\":
\"#798DED\", \"color-night\": \"#FFFFFF\", \"background-color\":
\"#40000000\", \"background-color-night\": \"#40000000\", \"data\":
\"Ad\" } }, \"action\":
\"http://qa-money.newshunt.com/click?\_\_oadest=https%3A%2F%2Fqa-dae.dailyhunt.in%2Fdaedalus-banners%2Fimage%2Fcreate%3FrequirementId%3D1285%26subTypeId%3D1&adId=4022&adPlacement=\--CL_AD_PLACEMENT\--&billingTypeId=3&bookedPlacement=\--CL_AD_PLACEMENT\--&bookedSubSlot=\--CL_SUB_SLOT\--&campaignId=1285&clientId=\--CL_CLIENT_ID\--&eg=1&orderId=238&partnerId=DH_APP&reqTime=\--CL_TIMESTAMP\--&subSlot=\--CL_SUB_SLOT\--&uniqueId=\--CL_UUID\--\",
\"errorUrls\": { \"internal\": \[
\"http://qa-money.newshunt.com/beaconEvents?adId=4022&adPlacement=\--CL_AD_PLACEMENT\--&bookedPlacement=\--CL_AD_PLACEMENT\--&bookedSubSlot=\--CL_SUB_SLOT\--&campaignId=1285&clientId=\--CL_CLIENT_ID\--&eventType=AD_ERROR&partnerId=DH_APP&reqTime=\--CL_TIMESTAMP\--&subSlot=\--CL_SUB_SLOT\--&uniqueId=\--CL_UUID\--\"
\] }, \"adInflatedBeaconUrls\": { \"internal\": \[
\"http://qa-money.newshunt.com/beaconEvents?adId=4022&adPlacement=\--CL_AD_PLACEMENT\--&bookedPlacement=\--CL_AD_PLACEMENT\--&bookedSubSlot=\--CL_SUB_SLOT\--&campaignId=1285&clientId=\--CL_CLIENT_ID\--&eventType=AD_INFLATED&partnerId=DH_APP&reqTime=\--CL_TIMESTAMP\--&subSlot=\--CL_SUB_SLOT\--&uniqueId=\--CL_UUID\--\"
\], \"external\": \[ \"http://www.google.com?inflated\" \] },
\"requestUrls\": { \"internal\": \[
\"http://qa-money.newshunt.com/fallback?adGroupId=755a37403932dcd9d215298febefd772&banner_id=4022&bookedPlacement=\--CL_AD_PLACEMENT\--&bookedSubSlot=\--CL_SUB_SLOT\--&campaign_id=1285&campaign_type=EVERGREEN&clientid=\--CL_CLIENT_ID\--&connection_speed=\--CL_CONNECTION_SPEED\--&countryCode=\--CL_COUNTRY_CODE\--&ecpm=10&eg=1&encCellid=\--CL_CELL_ID\--&encGaid=\--CL_ADVERTISING_ID\--&encLat=\--CL_LATITUDE\--&encLong=\--CL_LONGITUDE\--&encUdid=\--CL_UDID\--&entityId=\--CL_ENTITY_ID\--&entitySubtype=\--CL_SUB_ENTITY_TYPE\--&entityType=\--CL_ENTITY_TYPE\--&event_type=AD_REQUEST&isp=\--CL_ISP\--&optimisedBy=1&orderTypeV2=0&partnerId=DH_APP&placement=\--CL_AD_PLACEMENT\--&pubName=DH&reqTime=\--CL_TIMESTAMP\--&request_timestamp=\--CL_TIMESTAMP\--&resolution=\--CL_DEVICE_RESOLUTION\--&sourceType=\--CL_SOURCE_TYPE\--&subSlot=\--CL_SUB_SLOT\--&title=banner+990x505&uniqueId=\--CL_UUID\--&user_app_ver=\--CL_APP_VERSION\--&user_connection=\--CL_USER_CONNECTION\--&user_languages=\--CL_USER_LANGUAGE\--&user_os_platform=\--CL_USER_OS\--&user_os_ver=\--CL_USER_OS_VERSION\--\"
\], \"external\": \[ \"http://www.google.com?request\" \] },
\"impressionUrls\": { \"internal\": \[
\"http://qa-money.newshunt.com/impression?adId=4022&adPlacement=\--CL_AD_PLACEMENT\--&bookedPlacement=\--CL_AD_PLACEMENT\--&bookedSubSlot=\--CL_SUB_SLOT\--&campaignId=1285&clientId=\--CL_CLIENT_ID\--&eg=1&partnerId=DH_APP&reqTime=\--CL_TIMESTAMP\--&subSlot=\--CL_SUB_SLOT\--&uniqueId=\--CL_UUID\--\"
\], \"external\": \[ \"http://www.google.com\" \] },
\"adLPTimeSpentBeaconUrls\": { \"internal\": \[
\"http://qa-money.newshunt.com/beaconEvents?adId=4022&adPlacement=\--CL_AD_PLACEMENT\--&bookedPlacement=\--CL_AD_PLACEMENT\--&bookedSubSlot=\--CL_SUB_SLOT\--&campaignId=1285&clientId=\--CL_CLIENT_ID\--&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&reqTime=\--CL_TIMESTAMP\--&subSlot=\--CL_SUB_SLOT\--&uniqueId=\--CL_UUID\--\"
\], \"external\": \[ \"http://www.google.com?lptime\" \] },
\"adFeedback\": { \"feedbackUrls\": { \"internal\": \[
\"http://qa-money.newshunt.com/data-api/adfeedback?bannerId=4022&campaignId=1285&uniqueId=\--CL_UUID\--\"
\], \"external\": \[ \"http://www.google.com?feedback\" \] } },
\"useWideViewPort\": true, \"interactiveAd\": false, \"isVideo\": false
}, { \"supportedZones\": { \"card-p0\": { \"DEFAULT\": { \"priority\":
10, \"weight\": 5, \"card-position\": 1, \"positionWithTicker\": 1 } },
\"card-p1\": { \"DEFAULT\": { \"priority\": 10, \"weight\": 5,
\"card-position\": 7, \"positionWithTicker\": 7, \"min-ad-distance\": 7,
\"largeAdDistance\": 7 } }, \"card-pp1\": { \"pp1_1\": { \"priority\":
10, \"weight\": 5, \"card-position\": 3, \"positionWithTicker\": 3,
\"min-ad-distance\": 3, \"largeAdDistance\": 3 }, \"pp1_2\": {
\"priority\": 10, \"weight\": 5, \"card-position\": 4,
\"positionWithTicker\": 4, \"min-ad-distance\": 4, \"largeAdDistance\":
4 }, \"pp1_3\": { \"priority\": 10, \"weight\": 5, \"card-position\": 5,
\"positionWithTicker\": 5, \"min-ad-distance\": 5, \"largeAdDistance\":
5 }, \"pp1_4\": { \"priority\": 10, \"weight\": 5, \"card-position\": 5,
\"positionWithTicker\": 5, \"min-ad-distance\": 5, \"largeAdDistance\":
5 } }, \"storypage\": { \"DEFAULT\": { \"priority\": 10, \"weight\": 5 }
} }, \"type\": \"mraid-external\", \"startepoch\": 1652745600,
\"endepoch\": 1672509540, \"width\": \"2524\", \"height\": \"1287\",
\"id\": \"\--CL_UUID\--\", \"adGroupId\":
\"7ad3e9c2fc66f764c543aa2a15ee7487\", \"useInternalBrowser\": \"false\",
\"allowDelayedAdInsert\": true, \"adTagPosition\": \"TOP_RIGHT\",
\"campaignId\": \"1285\", \"bannerId\": \"4053\", \"isLargeAd\": false,
\"content\": { \"itemSubtitle2\": { \"color\": \"#4caf79\",
\"color-night\": \"#ffffff\", \"data\": \"Notify Me\" }, \"reportText\":
{ \"color\": \"#798DED\", \"color-night\": \"#FFFFFF\",
\"background-color\": \"#40000000\", \"background-color-night\":
\"#40000000\", \"data\": \"Ad\" } }, \"coolAd\": { \"zipped\": false,
\"type\": \"mraid\", \"content\": { \"link\": false, \"data\":
\"\<html\>\<head\>\\r\\n\<meta charset=\\\"utf-8\\\"\>\\r\\n\<meta
name=\\\"viewport\\\" content=\\\"width=990,
user-scalable=0\\\"\>\\r\\n\\r\\n\<title\>OP
Oscar\</title\>\\r\\n\<style type=\\\"text/css\\\"\>\\r\\n \@font-face
{font-family: \\\"digital\\\"; src:
url(https://widgets.dailyhunt.in/static_ads/timer/op_oscar/fonts/Barlow-Medium.ttf);}\\r\\n
\\r\\n \*{margin:0; padding:0; box-sizing:border-box;}\\r\\n
body{font:16px \\\"digital\\\"; color:#333; }\\r\\n a, a:link,
a:hover,a:visited{text-decoration: none; color:#333;}\\r\\n
.container{background:#111213
url(https://widgets.dailyhunt.in/static_ads/timer/op_oscar/images/990x505.jpg)
0 0 no-repeat; background-size:100% 100%; position:absolute; left:0;
top:0; height:100%; width:100%;overflow:hidden}\\r\\n .container
h1{font-size:16px; font-weight:normal; text-align:center;
padding-top:15px;}\\r\\n \\r\\n .container P{text-align:center;
font-size:0.8em; color:#d2d2d2; }\\r\\n .container a{position:absolute;
bottom:13px; right:5px; padding:3px 6px; font-size:0.8em; border:1px
#ccc solid; text-decoration:none; display:inline-block;}\\r\\n
.tblCell{width:100%; height:auto; position:absolute; top:44%; left:0;
text-align:left;}\\r\\n .timerBox{ width:410px; display:inline-block;
text-align:center;}\\r\\n \\r\\n ul#timer{ width:340px;margin-top:25px;
height:120px; display:inline-block}\\r\\n ul#timer li{list-style:none;
width:24%; float:left; text-align:center; font-size:4em;}\\r\\n ul#timer
li.bgImg{background:
url(https://widgets.dailyhunt.in/static_ads/timer/op_oscar/images/timer-bg.png)
0 0/cover no-repeat; height: 70%; color:#fff;}\\r\\n li +
li{margin-left: 1%;}\\r\\n ul#timer
li:nth-child(5){margin-left:0;}\\r\\n /\* ul#timer li:nth-child(2),
ul#timer li:nth-child(4){width: 2%;} \*/\\r\\n ul#timer
li.txtSmall{font-size:1em;text-transform:uppercase;
margin-top:4px;}\\r\\n .expiredTxt{ font-size:
3.6em;}\\r\\n\</style\>\\r\\n\</head\>\\r\\n\\r\\n\<body\>\\r\\n\<a
href=\\\"https://ad.doubleclick.net/ddm/trackclk/N4322.2059904DAILYHUNT/B27684563.334815541;dc_trk_aid=526435940;dc_trk_cid=154334690;dc_lat=;dc_rdid=;tag_for_child_directed_treatment=;tfua=;ltd=\\\"
target=\\\"\_blank\\\"\>\\r\\n \<div class=\\\"container\\\"\>\\r\\n
\<div class=\\\"tblCell\\\"\>\\r\\n \<div class=\\\"timerBox\\\"\>\\r\\n
\<ul id=\\\"timer\\\" class=\\\"setTime\\\"\>\<li class=\\\"days
bgImg\\\"\>01\</li\>\<li class=\\\"hrs bgImg\\\"\>22\</li\>\<li
class=\\\"min bgImg\\\"\>43\</li\>\<li class=\\\"sec
bgImg\\\"\>46\</li\>\<li class=\\\"txtSmall\\\"\>Days\</li\>\<li
class=\\\"txtSmall\\\"\>Hrs\</li\>\<li
class=\\\"txtSmall\\\"\>Min\</li\>\<li
class=\\\"txtSmall\\\"\>Sec\</li\>\</ul\>\\r\\n \</div\>\\r\\n
\</div\>\\r\\n \</div\>\\r\\n\</a\>\\r\\n\\r\\n\<script\>\\r\\nvar
countDownDate = new Date(\\\"May 28 2022,
19:00:00\\\").getTime();\\r\\nvar x = setInterval(function() {\\r\\n var
now = new Date().getTime();\\r\\n var distance = countDownDate -
now;\\r\\n\\r\\n var days = Math.floor(distance / (1000 \* 60 \* 60 \*
24));\\r\\n var hours = Math.floor((distance % (1000 \* 60 \* 60 \* 24))
/ (1000 \* 60 \* 60)); \\r\\n // var hours = Math.floor((distance %
(1000 \* 60 \* 60 \* 144)) / (1000 \* 60 \* 60));\\r\\n var minutes =
Math.floor((distance % (1000 \* 60 \* 60)) / (1000 \* 60));\\r\\n var
seconds = Math.floor((distance % (1000 \* 60)) / 1000);\\r\\n\\r\\n
if(days \< 10){days = \\\"0\\\" + days;}\\r\\n if(hours \< 10){hours =
\\\"0\\\" + hours;}\\r\\n if(minutes \< 10){minutes = \\\"0\\\" +
minutes;}\\r\\n if(seconds \< 10){seconds = \\\"0\\\" +
seconds;}\\r\\n\\r\\n\\r\\n
document.getElementById(\\\"timer\\\").innerHTML = \\\"\<li class=\'days
bgImg\'\>\\\"+ days +\\\"\</li\>\<li class=\'hrs bgImg\'\>\\\" + hours +
\\\"\</li\>\<li class=\'min bgImg\'\>\\\" + minutes + \\\"\</li\>\<li
class=\'sec bgImg\'\>\\\" + seconds + \\\"\</li\>\<li
class=\'txtSmall\'\>Days\</li\>\<li class=\'txtSmall\'\>Hrs\</li\>\<li
class=\'txtSmall\'\>Min\</li\>\<li
class=\'txtSmall\'\>Sec\</li\>\\\";\\r\\n\\r\\n\\r\\n\\r\\n\\r\\n // If
the count down is finished, write some text \\r\\n if (distance \< 0)
{\\r\\n clearInterval(x);\\r\\n
document.getElementById(\\\"timer\\\").innerHTML = \\\"\<li
class=\'expiredTxt\'\>00:00:00\</li\>\\\";\\r\\n }\\r\\n},
1000);\\r\\n\\r\\n\\r\\n\</script\>\\r\\n\\r\\n\\r\\n\</body\>\</html\>\"
}, \"tracker\": { \"redirectWebUrl\": true, \"data\":
\"http://qa-money.newshunt.com/click?\_\_oadest=\--USER_CLICK_URL\--&adId=4053&adPlacement=\--CL_AD_PLACEMENT\--&billingTypeId=3&bookedPlacement=\--CL_AD_PLACEMENT\--&bookedSubSlot=\--CL_SUB_SLOT\--&campaignId=1285&clientId=\--CL_CLIENT_ID\--&eg=1&orderId=238&partnerId=DH_APP&reqTime=\--CL_TIMESTAMP\--&subSlot=\--CL_SUB_SLOT\--&uniqueId=\--CL_UUID\--\"
} }, \"errorUrls\": { \"internal\": \[
\"http://qa-money.newshunt.com/beaconEvents?adId=4022&adPlacement=\--CL_AD_PLACEMENT\--&bookedPlacement=\--CL_AD_PLACEMENT\--&bookedSubSlot=\--CL_SUB_SLOT\--&campaignId=1285&clientId=\--CL_CLIENT_ID\--&eventType=AD_ERROR&partnerId=DH_APP&reqTime=\--CL_TIMESTAMP\--&subSlot=\--CL_SUB_SLOT\--&uniqueId=\--CL_UUID\--\"
\] }, \"requestUrls\": { \"internal\": \[
\"http://qa-money.newshunt.com/fallback?adGroupId=755a37403932dcd9d215298febefd772&banner_id=4022&bookedPlacement=\--CL_AD_PLACEMENT\--&bookedSubSlot=\--CL_SUB_SLOT\--&campaign_id=1285&campaign_type=EVERGREEN&clientid=\--CL_CLIENT_ID\--&connection_speed=\--CL_CONNECTION_SPEED\--&countryCode=\--CL_COUNTRY_CODE\--&ecpm=10&eg=1&encCellid=\--CL_CELL_ID\--&encGaid=\--CL_ADVERTISING_ID\--&encLat=\--CL_LATITUDE\--&encLong=\--CL_LONGITUDE\--&encUdid=\--CL_UDID\--&entityId=\--CL_ENTITY_ID\--&entitySubtype=\--CL_SUB_ENTITY_TYPE\--&entityType=\--CL_ENTITY_TYPE\--&event_type=AD_REQUEST&isp=\--CL_ISP\--&optimisedBy=1&orderTypeV2=0&partnerId=DH_APP&placement=\--CL_AD_PLACEMENT\--&pubName=DH&reqTime=\--CL_TIMESTAMP\--&request_timestamp=\--CL_TIMESTAMP\--&resolution=\--CL_DEVICE_RESOLUTION\--&sourceType=\--CL_SOURCE_TYPE\--&subSlot=\--CL_SUB_SLOT\--&title=banner+990x505&uniqueId=\--CL_UUID\--&user_app_ver=\--CL_APP_VERSION\--&user_connection=\--CL_USER_CONNECTION\--&user_languages=\--CL_USER_LANGUAGE\--&user_os_platform=\--CL_USER_OS\--&user_os_ver=\--CL_USER_OS_VERSION\--\"
\], \"external\": \[ \"http://www.google.com?request\" \] },
\"adInflatedBeaconUrls\": { \"internal\": \[
\"http://qa-money.newshunt.com/beaconEvents?adId=4022&adPlacement=\--CL_AD_PLACEMENT\--&bookedPlacement=\--CL_AD_PLACEMENT\--&bookedSubSlot=\--CL_SUB_SLOT\--&campaignId=1285&clientId=\--CL_CLIENT_ID\--&eventType=AD_INFLATED&partnerId=DH_APP&reqTime=\--CL_TIMESTAMP\--&subSlot=\--CL_SUB_SLOT\--&uniqueId=\--CL_UUID\--\"
\], \"external\": \[ \"http://www.google.com?inflated\" \] },
\"impressionUrls\": { \"internal\": \[
\"http://qa-money.newshunt.com/impression?adId=4022&adPlacement=\--CL_AD_PLACEMENT\--&bookedPlacement=\--CL_AD_PLACEMENT\--&bookedSubSlot=\--CL_SUB_SLOT\--&campaignId=1285&clientId=\--CL_CLIENT_ID\--&eg=1&partnerId=DH_APP&reqTime=\--CL_TIMESTAMP\--&subSlot=\--CL_SUB_SLOT\--&uniqueId=\--CL_UUID\--\"
\], \"external\": \[ \"http://www.google.com\" \] },
\"adLPTimeSpentBeaconUrls\": { \"internal\": \[
\"http://qa-money.newshunt.com/beaconEvents?adId=4022&adPlacement=\--CL_AD_PLACEMENT\--&bookedPlacement=\--CL_AD_PLACEMENT\--&bookedSubSlot=\--CL_SUB_SLOT\--&campaignId=1285&clientId=\--CL_CLIENT_ID\--&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&reqTime=\--CL_TIMESTAMP\--&subSlot=\--CL_SUB_SLOT\--&uniqueId=\--CL_UUID\--\"
\], \"external\": \[ \"http://www.google.com?lptime\" \] },
\"adFeedback\": { \"feedbackUrls\": { \"internal\": \[
\"http://qa-money.newshunt.com/data-api/adfeedback?bannerId=4022&campaignId=1285&uniqueId=\--CL_UUID\--\"
\], \"external\": \[ \"http://www.google.com?feedback\" \] } },
\"contentBaseUrl\": \"http://qa-money.newshunt.com/\",
\"useWideViewPort\": true, \"showHTMLPgiOnlyOnVisible\": \"false\",
\"interactiveAd\": false, \"isVideo\": false }, { \"supportedZones\": {
\"card-p0\": { \"DEFAULT\": { \"priority\": -1, \"weight\": 5,
\"card-position\": 1, \"positionWithTicker\": 1 } }, \"card-p1\": {
\"DEFAULT\": { \"priority\": -1, \"weight\": 5, \"card-position\": 7,
\"positionWithTicker\": 7, \"min-ad-distance\": 7, \"largeAdDistance\":
7 } }, \"card-pp1\": { \"pp1_1\": { \"priority\": -1, \"weight\": 5,
\"card-position\": 3, \"positionWithTicker\": 3, \"min-ad-distance\": 3,
\"largeAdDistance\": 3 }, \"pp1_2\": { \"priority\": -1, \"weight\": 5,
\"card-position\": 4, \"positionWithTicker\": 4, \"min-ad-distance\": 4,
\"largeAdDistance\": 4 }, \"pp1_3\": { \"priority\": -1, \"weight\": 5,
\"card-position\": 5, \"positionWithTicker\": 5, \"min-ad-distance\": 5,
\"largeAdDistance\": 5 }, \"pp1_4\": { \"priority\": -1, \"weight\": 5,
\"card-position\": 5, \"positionWithTicker\": 5, \"min-ad-distance\": 5,
\"largeAdDistance\": 5 }, \"pp1_c1\": { \"priority\": -1, \"weight\": 5,
\"card-position\": 3, \"positionWithTicker\": 3, \"min-ad-distance\": 3,
\"largeAdDistance\": 3 }, \"pp1_c2\": { \"priority\": -1, \"weight\": 5,
\"card-position\": 2, \"positionWithTicker\": 2, \"min-ad-distance\": 2,
\"largeAdDistance\": 2 }, \"pp1_c3\": { \"priority\": -1, \"weight\": 5,
\"card-position\": 2, \"positionWithTicker\": 2, \"min-ad-distance\": 2,
\"largeAdDistance\": 2 } }, \"pgi\": { \"DEFAULT\": { \"priority\": -1,
\"weight\": 5, \"sessionCount\": 2, \"minThresholdSwipeCount\": 3,
\"requestSwipeCountGood\": 1, \"requestSwipeCountAverage\": 1,
\"requestSwipeCountSlow\": 1, \"firstAdSwipeCount\": 3,
\"pageSwipeCount\": 9, \"maxPageSwipeCount\": 13, \"useWideViewPort\":
true } }, \"splash\": { \"DEFAULT\": { \"priority\": -1, \"weight\": 5,
\"span\": 5 } }, \"storypage\": { \"DEFAULT\": { \"priority\": -1,
\"weight\": 5 } }, \"supplement\": { \"sp1\": { \"priority\": -1,
\"weight\": 5 }, \"sp2\": { \"priority\": -1, \"weight\": 5 }, \"sp3\":
{ \"priority\": -1, \"weight\": 5 }, \"sp4\": { \"priority\": -1,
\"weight\": 5 }, \"sp5\": { \"priority\": -1, \"weight\": 5 }, \"sp6\":
{ \"priority\": -1, \"weight\": 5 }, \"sp7\": { \"priority\": -1,
\"weight\": 5 } } }, \"type\": \"empty\", \"startepoch\": 1640998800,
\"endepoch\": 1704070800, \"id\": \"\--CL_UUID\--\", \"adGroupId\":
\"cc788935fd3cb66a216d63be2e714903\", \"allowDelayedAdInsert\": false,
\"campaignId\": \"-2\", \"bannerId\": \"167\", \"isLargeAd\": false,
\"requestUrls\": { \"internal\": \[
\"http://qa-money.newshunt.com/fallback?adGroupId=755a37403932dcd9d215298febefd772&banner_id=4022&bookedPlacement=\--CL_AD_PLACEMENT\--&bookedSubSlot=\--CL_SUB_SLOT\--&campaign_id=1285&campaign_type=EVERGREEN&clientid=\--CL_CLIENT_ID\--&connection_speed=\--CL_CONNECTION_SPEED\--&countryCode=\--CL_COUNTRY_CODE\--&ecpm=10&eg=1&encCellid=\--CL_CELL_ID\--&encGaid=\--CL_ADVERTISING_ID\--&encLat=\--CL_LATITUDE\--&encLong=\--CL_LONGITUDE\--&encUdid=\--CL_UDID\--&entityId=\--CL_ENTITY_ID\--&entitySubtype=\--CL_SUB_ENTITY_TYPE\--&entityType=\--CL_ENTITY_TYPE\--&event_type=AD_REQUEST&isp=\--CL_ISP\--&optimisedBy=1&orderTypeV2=0&partnerId=DH_APP&placement=\--CL_AD_PLACEMENT\--&pubName=DH&reqTime=\--CL_TIMESTAMP\--&request_timestamp=\--CL_TIMESTAMP\--&resolution=\--CL_DEVICE_RESOLUTION\--&sourceType=\--CL_SOURCE_TYPE\--&subSlot=\--CL_SUB_SLOT\--&title=banner+990x505&uniqueId=\--CL_UUID\--&user_app_ver=\--CL_APP_VERSION\--&user_connection=\--CL_USER_CONNECTION\--&user_languages=\--CL_USER_LANGUAGE\--&user_os_platform=\--CL_USER_OS\--&user_os_ver=\--CL_USER_OS_VERSION\--\"
\], \"external\": \[ \"http://www.google.com?request\" \] },
\"impressionUrls\": { \"internal\": \[
\"http://qa-money.newshunt.com/impression?adId=4022&adPlacement=\--CL_AD_PLACEMENT\--&bookedPlacement=\--CL_AD_PLACEMENT\--&bookedSubSlot=\--CL_SUB_SLOT\--&campaignId=1285&clientId=\--CL_CLIENT_ID\--&eg=1&partnerId=DH_APP&reqTime=\--CL_TIMESTAMP\--&subSlot=\--CL_SUB_SLOT\--&uniqueId=\--CL_UUID\--\"
\], \"external\": \[ \"http://www.google.com\" \] }, \"errorUrls\": {
\"internal\": \[
\"http://qa-money.newshunt.com/beaconEvents?adId=4022&adPlacement=\--CL_AD_PLACEMENT\--&bookedPlacement=\--CL_AD_PLACEMENT\--&bookedSubSlot=\--CL_SUB_SLOT\--&campaignId=1285&clientId=\--CL_CLIENT_ID\--&eventType=AD_ERROR&partnerId=DH_APP&reqTime=\--CL_TIMESTAMP\--&subSlot=\--CL_SUB_SLOT\--&uniqueId=\--CL_UUID\--\"
\] }, \"adInflatedBeaconUrls\": { \"internal\": \[
\"http://qa-money.newshunt.com/beaconEvents?adId=4022&adPlacement=\--CL_AD_PLACEMENT\--&bookedPlacement=\--CL_AD_PLACEMENT\--&bookedSubSlot=\--CL_SUB_SLOT\--&campaignId=1285&clientId=\--CL_CLIENT_ID\--&eventType=AD_INFLATED&partnerId=DH_APP&reqTime=\--CL_TIMESTAMP\--&subSlot=\--CL_SUB_SLOT\--&uniqueId=\--CL_UUID\--\"
\], \"external\": \[ \"http://www.google.com?inflated\" \] },
\"useWideViewPort\": false, \"interactiveAd\": false, \"isVideo\": false
} \], \"Version\": \"821a00a1fef342e1e16a720ecb458a5d\" }

# Carousel AD Response 

{ \"ads\": \[ { \"type\": \"appDownload\", \"aduid\":
\"notId=ad-1593977478\", \"srcUrlExpiry\": 60, \"card-position\": 7,
\"positionWithTicker\": 7, \"min-ad-distance\": 7, \"adGroupId\":
\"453100063280344292864.26891027\", \"width\": 1080, \"height\": 551,
\"adTemplate\": \"L\", \"showOnlyImage\": false, \"id\":
\"61f79f593894be52006b2d91148d4b6b\", \"span\": 60, \"bannerid\":
\"1542981624\", \"adContext\": null, \"showPlayIcon\": false,
\"useInternalBrowser\": \"false\", \"dedupId\":
\"61f79f593894be52006b2d91148d4b6b\", \"adCacheGood\": 1,
\"adCacheAverage\": 1, \"adCacheSlow\": 1, \"adTagPosition\":
\"TOP_RIGHT\", \"timeOffset\": 0, \"clubType\": \"sequence\",
\"showBorder\": false, \"campaignId\": \"1542981624\", \"bannerId\":
\"1593977478\", \"isLargeAd\": false, \"largeAdDistance\": 7,
\"position\": \"card-p1\", \"impressionUrls\": { \"internal\": \[
\"http://stage-ads2.dailyhunt.in/impression?uniqueId=61f79f593894be52006b2d91148d4b6b&adId=1593977478&campaignId=1542981624&adPlacement=card-p1&partnerRef=&city=&state=&country=india&clientId=4531000&reqTime=1663566654&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=card-p1&bookedSubSlot=&contentId=&contentCreatorId=\"
\], \"external\": \[ \"abc.com\", \"abcd.com\" \] },
\"adInflatedBeaconUrls\": { \"internal\": \[
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=61f79f593894be52006b2d91148d4b6b&adId=1593977478&campaignId=1542981624&adPlacement=card-p1&partnerRef=&city=&state=&country=india&clientId=4531000&reqTime=1663566654&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=card-p1&bookedSubSlot=&contentId=&contentCreatorId=\"
\] }, \"adRespondedBeaconUrls\": { \"internal\": \[
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=61f79f593894be52006b2d91148d4b6b&adId=1593977478&campaignId=1542981624&adPlacement=card-p1&partnerRef=&city=&state=&country=india&clientId=4531000&reqTime=1663566654&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=card-p1&bookedSubSlot=&contentId=&contentCreatorId=\"
\] }, \"clickUrls\": { \"external\": \[ \"clk.com\", \"clk2.com\" \] },
\"adLPTimeSpentBeaconUrls\": { \"internal\": \[
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=61f79f593894be52006b2d91148d4b6b&adId=1593977478&campaignId=1542981624&adPlacement=card-p1&partnerRef=&city=&state=&country=india&clientId=4531000&reqTime=1663566654&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=card-p1&bookedSubSlot=&contentId=&contentCreatorId=\"
\] }, \"requestUrls\": { \"internal\": \[
\"http://stage-ads2.dailyhunt.in/fallback?clientid=4531000&req_time=19092022+11%3A20%3A54&paper=nh-headlines&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=Xiaomi&user_handset_model=Mi+A2&user_id=dh6b47acbd888b4740a29d933236bc500c&placement=card-p1&user_app_ver=20.0.10.2&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-p1&banner_id=1593977478&campaign_id=1542981624&user_connection=w&connection_speed=FAST&user_os_ver=11.0&encGaid=MjBhYjcyN2EtZjQzNy00NzUzLWJiZWYtZjAzMGY1ZmQ3ZjIy&item_publisher_language=&user_languages=en%2C&oi=424&price_range=none&user_device_type=none&title=carousel+img&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=61f79f593894be52006b2d91148d4b6b&region=&mcc=&mnc=&lac=&cellid=&ip=127.0.0.1&adGroupId=453100063280344292864.26891027&topicId=91581308b67fdfbcd24028a0c513bc37&topicName=&ecpm=2000&audienceSegments=none&resolution=1080x2028&hostalias=VER-BLR-LT2660&locationSource=&pincode=&subSlot=&bookedSubSlot=&ab=ECPM&partnerId=DH_APP&deliverySlab=1&userDeliverySlab=&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=2000&utmSource=&utmMedium=&utmCampaign=&appId=&autoPlayPref=3&installDeliverySlab=&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=1&topCampaignIds=1542981624%5E&topCampaignECPMs=2000&entityId=91581308b67fdfbcd24028a0c513bc37&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&mastheadAdCount=0&sessionSource=&totalAdSessions=3&totalSeenAds=10&totalSessions=4&predictedInstallProbability=&campaignPrdictedCtr=&productIds=&recoPolicy=&request_timestamp=1663566654&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=&variantName=&modelUuid=&networkSwitch=&topDirectCampaign=&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=&campaign_type=TEST_MODE&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=&requestIdDebug=00785c760ae5d6a53126e470eb02d60c&gender=&age=&ageRange=&orderTypeV2=0&idfa=&s2sBidId=&imputationType=&amazonSdkPayload=&contentCreatorId=&scoringModel=&filteringModel=&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&isRegUser=1&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1663566654&\"
\] }, \"errorUrls\": { \"internal\": \[
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=61f79f593894be52006b2d91148d4b6b&adId=1593977478&campaignId=1542981624&adPlacement=card-p1&partnerRef=&city=&state=&country=india&clientId=4531000&reqTime=1663566654&eventType=AD_ERROR&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=card-p1&bookedSubSlot=&contentId=&contentCreatorId=\"
\] }, \"adFeedback\": { \"feedbackUrls\": { \"internal\": \[
\"http://stage-ads2.dailyhunt.in/data-api/adfeedback?bannerId=1593977478&campaignId=1542981624&uniqueId=61f79f593894be52006b2d91148d4b6b&city=\"
\] } }, \"content\": { \"bg-color\": \"#ffffff\", \"bg-color-night\":
\"#000000\", \"language\": \"en\", \"itemTitle\": { \"color\":
\"#000000\", \"color-night\": \"#ffffff\", \"maxLines\": 1, \"data\":
\"Item Title 1\" }, \"itemDescription\": null, \"itemRating\": null,
\"packageName\": null, \"actionText\": \"Buy Now\", \"reportText\": {
\"color\": \"#999999\", \"color-night\": \"#FFFFFF\",
\"background-color\": \"#40000000\", \"background-color-night\":
\"#40000000\", \"data\": \"Ad\" }, \"itemImage\": { \"width\": 990,
\"height\": 505, \"data\":
\"http://daedalusstage.dailyhunt.in/uploads/daedalus-banners/1593977478/1663566417_10725_990x505.jpg\"
} }, \"action\":
\"https://stage-ads2.dailyhunt.in/click?clientId=4531000&uniqueId=61f79f593894be52006b2d91148d4b6b&adId=1593977478&campaignId=1542981624&adPlacement=card-p1&reqTime=1663566654&billingTypeId=3&orderId=1069181135&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=card-p1&bookedSubSlot=&contentId=&contentCreatorId=&\_\_oadest=https%3A%2F%2Fgoogle.com\",
\"adContextRules\": { \"selectionPriority\": 2, \"cacheType\":
\"session\", \"ttl\": 300, \"ruleGroup\": { \"rules\": \[\],
\"respondedFor\": { \"entityIds\": \[\], \"postId\": null } } },
\"shareability\": null }, { \"type\": \"appDownload\", \"aduid\":
\"notId=ad-1593977478\", \"srcUrlExpiry\": 60, \"card-position\": 7,
\"positionWithTicker\": 7, \"min-ad-distance\": 7, \"adGroupId\":
\"453100063280344292864.26891027\", \"width\": 1080, \"height\": 551,
\"adTemplate\": \"L\", \"showOnlyImage\": false, \"id\":
\"61f79f593894be52006b2d91148d4b6b\", \"span\": 60, \"bannerid\":
\"1542981624\", \"adContext\": null, \"showPlayIcon\": false,
\"useInternalBrowser\": \"false\", \"dedupId\":
\"61f79f593894be52006b2d91148d4b6b\", \"adCacheGood\": 1,
\"adCacheAverage\": 1, \"adCacheSlow\": 1, \"adTagPosition\":
\"TOP_RIGHT\", \"timeOffset\": 1, \"clubType\": \"sequence\",
\"showBorder\": false, \"campaignId\": \"1542981624\", \"bannerId\":
\"1593977478\", \"isLargeAd\": false, \"largeAdDistance\": 7,
\"position\": \"card-p1\", \"clickUrls\": { \"external\": \[
\"clk.com\", \"clk2.com\" \] }, \"adLPTimeSpentBeaconUrls\": {
\"internal\": \[
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=61f79f593894be52006b2d91148d4b6b&adId=1593977478&campaignId=1542981624&adPlacement=card-p1&partnerRef=&city=&state=&country=india&clientId=4531000&reqTime=1663566654&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=card-p1&bookedSubSlot=&contentId=&contentCreatorId=\"
\] }, \"requestUrls\": { \"internal\": \[
\"http://stage-ads2.dailyhunt.in/fallback?clientid=4531000&req_time=19092022+11%3A20%3A54&paper=nh-headlines&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=Xiaomi&user_handset_model=Mi+A2&user_id=dh6b47acbd888b4740a29d933236bc500c&placement=card-p1&user_app_ver=20.0.10.2&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-p1&banner_id=1593977478&campaign_id=1542981624&user_connection=w&connection_speed=FAST&user_os_ver=11.0&encGaid=MjBhYjcyN2EtZjQzNy00NzUzLWJiZWYtZjAzMGY1ZmQ3ZjIy&item_publisher_language=&user_languages=en%2C&oi=424&price_range=none&user_device_type=none&title=carousel+img&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=61f79f593894be52006b2d91148d4b6b&region=&mcc=&mnc=&lac=&cellid=&ip=127.0.0.1&adGroupId=453100063280344292864.26891027&topicId=91581308b67fdfbcd24028a0c513bc37&topicName=&ecpm=2000&audienceSegments=none&resolution=1080x2028&hostalias=VER-BLR-LT2660&locationSource=&pincode=&subSlot=&bookedSubSlot=&ab=ECPM&partnerId=DH_APP&deliverySlab=1&userDeliverySlab=&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=2000&utmSource=&utmMedium=&utmCampaign=&appId=&autoPlayPref=3&installDeliverySlab=&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=1&topCampaignIds=1542981624%5E&topCampaignECPMs=2000&entityId=91581308b67fdfbcd24028a0c513bc37&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&mastheadAdCount=0&sessionSource=&totalAdSessions=3&totalSeenAds=10&totalSessions=4&predictedInstallProbability=&campaignPrdictedCtr=&productIds=&recoPolicy=&request_timestamp=1663566654&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=&variantName=&modelUuid=&networkSwitch=&topDirectCampaign=&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=&campaign_type=TEST_MODE&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=&requestIdDebug=00785c760ae5d6a53126e470eb02d60c&gender=&age=&ageRange=&orderTypeV2=0&idfa=&s2sBidId=&imputationType=&amazonSdkPayload=&contentCreatorId=&scoringModel=&filteringModel=&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&isRegUser=1&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1663566654&\"
\] }, \"errorUrls\": { \"internal\": \[
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=61f79f593894be52006b2d91148d4b6b&adId=1593977478&campaignId=1542981624&adPlacement=card-p1&partnerRef=&city=&state=&country=india&clientId=4531000&reqTime=1663566654&eventType=AD_ERROR&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=card-p1&bookedSubSlot=&contentId=&contentCreatorId=\"
\] }, \"adFeedback\": { \"feedbackUrls\": { \"internal\": \[
\"http://stage-ads2.dailyhunt.in/data-api/adfeedback?bannerId=1593977478&campaignId=1542981624&uniqueId=61f79f593894be52006b2d91148d4b6b&city=\"
\] } }, \"content\": { \"bg-color\": \"#ffffff\", \"bg-color-night\":
\"#000000\", \"language\": \"en\", \"itemTitle\": { \"color\":
\"#000000\", \"color-night\": \"#ffffff\", \"maxLines\": 1, \"data\":
\"Item Title 2\" }, \"itemDescription\": null, \"itemRating\": null,
\"packageName\": null, \"actionText\": \"Stream Now\", \"reportText\": {
\"color\": \"#999999\", \"color-night\": \"#FFFFFF\",
\"background-color\": \"#40000000\", \"background-color-night\":
\"#40000000\", \"data\": \"Ad\" }, \"itemImage\": { \"width\": 990,
\"height\": 505, \"data\":
\"http://daedalusstage.dailyhunt.in/uploads/daedalus-banners/1593977478/1663566483_31817_990x505.jpg\"
} }, \"action\":
\"https://stage-ads2.dailyhunt.in/click?clientId=4531000&uniqueId=61f79f593894be52006b2d91148d4b6b&adId=1593977478&campaignId=1542981624&adPlacement=card-p1&reqTime=1663566654&billingTypeId=3&orderId=1069181135&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=card-p1&bookedSubSlot=&contentId=&contentCreatorId=&\_\_oadest=https%3A%2F%2Fgoogle.com\",
\"adContextRules\": { \"selectionPriority\": 2, \"cacheType\":
\"session\", \"ttl\": 300, \"ruleGroup\": { \"rules\": \[\],
\"respondedFor\": { \"entityIds\": \[\], \"postId\": null } } },
\"shareability\": null } \] }

## HTML AD

json{ \"ads\": \[ { \"type\": \"mraid-external\", \"typeId\": 6,
\"aduid\": \"notId=ad-1675844708\", \"srcUrlExpiry\": 60, \"width\":
1080, \"height\": 540, \"bannerid\": \"1542981624\", \"adTemplate\":
\"L\", \"showOnlyImage\": false, \"id\":
\"7370dcdc4e7d31b7b0a1463aee2d1229\", \"span\": 60,
\"useInternalBrowser\": \"false\", \"useWideViewPort\": true,
\"adCacheGood\": 1, \"adCacheAverage\": 1, \"adCacheSlow\": 1,
\"allowDelayedAdInsert\": true, \"adGroupId\":
\"4531000632abe0473c020.25794481\", \"adContext\": null, \"isVideo\":
\"false\", \"dedupId\": \"7370dcdc4e7d31b7b0a1463aee2d1229\",
\"adTagPosition\": \"TOP_OVERLAY_LEFT\", \"showPlaybackControls\":
false, \"enableGyroscope\": false, \"enableAccelerometer\": false,
\"gyroscopeFreq\": 100, \"accelerometerFreq\": 100, \"showBorder\":
false, \"campaignId\": \"1542981624\", \"bannerId\": \"1675844708\",
\"isLargeAd\": false, \"largeAdDistance\": 8, \"position\":
\"splash-exit\", \"backFromLpAction\": \"EXIT_APP\", \"displayType\":
\"FULL_SCREEN\", \"spanInMS\": 5000, \"enablePreLoad\": true,
\"card-position\": 4, \"min-ad-distance\": 4, \"positionWithTicker\": 4,
\"banner-fill\": \"fill-width\", \"adFeedback\": { \"feedbackUrls\": {
\"internal\": \[
\"http://stage-ads2.dailyhunt.in/data-api/adfeedback?bannerId=1675844708&campaignId=1542981624&uniqueId=7370dcdc4e7d31b7b0a1463aee2d1229&city=\"
\] } }, \"errorUrls\": { \"internal\": \[
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=7370dcdc4e7d31b7b0a1463aee2d1229&adId=1675844708&campaignId=1542981624&adPlacement=splash-exit&partnerRef=&city=&state=&country=india&clientId=4531000&reqTime=1663745539&eventType=AD_ERROR&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=splash-exit&bookedSubSlot=&contentId=&contentCreatorId=\"
\] }, \"impressionUrls\": { \"internal\": \[
\"http://stage-ads2.dailyhunt.in/impression?uniqueId=7370dcdc4e7d31b7b0a1463aee2d1229&adId=1675844708&campaignId=1542981624&adPlacement=splash-exit&partnerRef=&city=&state=&country=india&clientId=4531000&reqTime=1663745539&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=splash-exit&bookedSubSlot=&contentId=&contentCreatorId=\"
\] }, \"adLPTimeSpentBeaconUrls\": { \"internal\": \[
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=7370dcdc4e7d31b7b0a1463aee2d1229&adId=1675844708&campaignId=1542981624&adPlacement=splash-exit&partnerRef=&city=&state=&country=india&clientId=4531000&reqTime=1663745539&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=splash-exit&bookedSubSlot=&contentId=&contentCreatorId=\"
\] }, \"requestUrls\": { \"internal\": \[
\"http://stage-ads2.dailyhunt.in/fallback?clientid=4531000&req_time=21092022+13%3A02%3A19&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=Xiaomi&user_handset_model=Mi+A2&user_id=dhd1e4d3900aa343439104593c8688b436&placement=splash-exit&user_app_ver=20.0.28&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=splash-exit&banner_id=1675844708&campaign_id=1542981624&user_connection=w&connection_speed=AVERAGE&user_os_ver=11.0&encGaid=MjBhYjcyN2EtZjQzNy00NzUzLWJiZWYtZjAzMGY1ZmQ3ZjIy&item_publisher_language=&user_languages=en%2C&oi=1020&price_range=none&user_device_type=none&title=html&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=7370dcdc4e7d31b7b0a1463aee2d1229&region=&mcc=&mnc=&lac=&cellid=&ip=127.0.0.1&adGroupId=4531000632abe0473c020.25794481&topicId=&topicName=&ecpm=2000&audienceSegments=none&resolution=1080x2028&hostalias=VER-BLR-LT2660&locationSource=&pincode=&subSlot=&bookedSubSlot=&ab=ECPM&partnerId=DH_APP&deliverySlab=1&userDeliverySlab=&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=2000&utmSource=&utmMedium=&utmCampaign=&appId=&autoPlayPref=3&installDeliverySlab=&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=1&topCampaignIds=1542981624%5E&topCampaignECPMs=2000&entityId=&entityType=&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&mastheadAdCount=0&sessionSource=&totalAdSessions=0&totalSeenAds=0&totalSessions=1&predictedInstallProbability=&campaignPrdictedCtr=&productIds=&recoPolicy=&request_timestamp=1663745539&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=&variantName=&modelUuid=&networkSwitch=&topDirectCampaign=&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=&campaign_type=TEST_MODE&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=&requestIdDebug=9cb6c0091126e2f72789d3b23c920c64&gender=&age=&ageRange=&orderTypeV2=0&idfa=&s2sBidId=&imputationType=&amazonSdkPayload=&contentCreatorId=&scoringModel=&filteringModel=&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1663745539&\"
\] }, \"adInflatedBeaconUrls\": { \"internal\": \[
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=7370dcdc4e7d31b7b0a1463aee2d1229&adId=1675844708&campaignId=1542981624&adPlacement=splash-exit&partnerRef=&city=&state=&country=india&clientId=4531000&reqTime=1663745539&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=splash-exit&bookedSubSlot=&contentId=&contentCreatorId=\"
\] }, \"adRespondedBeaconUrls\": { \"internal\": \[
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=7370dcdc4e7d31b7b0a1463aee2d1229&adId=1675844708&campaignId=1542981624&adPlacement=splash-exit&partnerRef=&city=&state=&country=india&clientId=4531000&reqTime=1663745539&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=splash-exit&bookedSubSlot=&contentId=&contentCreatorId=\"
\] }, \"adClosedBeaconUrls\": { \"internal\": \[
\"http://stage-ads2.dailyhunt.in/beaconEvents?uniqueId=7370dcdc4e7d31b7b0a1463aee2d1229&adId=1675844708&campaignId=1542981624&adPlacement=splash-exit&partnerRef=&city=&state=&country=india&clientId=4531000&reqTime=1663745539&eventType=AD_CLOSE&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=splash-exit&bookedSubSlot=&contentId=&contentCreatorId=\"
\] }, \"coolAd\": { \"zipped\": false, \"type\": \"mraid\", \"content\":
{ \"link\": false, \"data\": \"\<meta name=\\\"viewport\\\"
content=\\\"initial-scale=1.0 user-scalable=no\\\" /\>Splash - Exit\" },
\"tracker\": { \"redirectWebUrl\": true, \"data\":
\"https://stage-ads2.dailyhunt.in/click?clientId=4531000&uniqueId=7370dcdc4e7d31b7b0a1463aee2d1229&adId=1675844708&campaignId=1542981624&adPlacement=splash-exit&billingTypeId=3&orderId=1069181135&forceTracker=&reqTime=1663745539&leadId=&subBannerId=&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=splash-exit&bookedSubSlot=&contentId=&contentCreatorId=&\_\_oadest=\--USER_CLICK_URL\--\"
} }, \"action\": \"https://google.com\", \"contentBaseUrl\":
\"http://stage-ads2.dailyhunt.in/\", \"adContextRules\": {
\"selectionPriority\": 2, \"cacheType\": \"session\", \"ttl\": 300,
\"ruleGroup\": { \"respondedFor\": { \"entityIds\": \[\], \"postId\":
null } } }, \"content\": { \"itemSubtitle2\": { \"color\": \"#4caf79\",
\"color-night\": \"#ffffff\", \"data\": \"Click\" }, \"reportText\": {
\"color\": \"#FFFFFF\", \"color-night\": \"#FFFFFF\",
\"background-color\": \"#40000000\", \"background-color-night\":
\"#40000000\", \"data\": \"Ad\" } }, \"shareability\": null } \] }

# Verification:

1.  All beacons firing test.

2.  Inflated and responded beacons in content ad and empty ad.

3.  Companion beacons.

4.  Sdk and s2s beacons.

5.  BC for webitem and pwa

6.  ~~adRequestTriggeredBeaconUrl~~

note

**Note:**

1.  This change will be only for native-app ad responses. Web-item and
    pwa will remain same.

:::: {.panel .conf-macro .output-block style="background-color: rgb(234,230,255);border-color: rgb(153,141,217);border-width: 1.0px;"}
::: {.panelContent style="background-color: rgb(234,230,255);"}
**Note:**

1.  This change will be only for native-app ad responses. Web-item and
    pwa will remain same.
:::
::::
