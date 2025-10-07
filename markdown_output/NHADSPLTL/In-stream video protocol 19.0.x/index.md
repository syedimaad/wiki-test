## Requirements

1.  Companion banner revamp

    - Enable creative size 600 x 600 for companion banner.

    - Show configurable headline for companion banner.

2.  New ad placement `video-storypage`.

    1.  Replace `dhtv-masthead` ad placement with `video-storypage` from
        dh android version \>= 19.0.x.

    2.  It will only support image/html banner.

    3.  Supported sizes are \[ 990 x 505, 960 x 150, 600 x 600 \].

## Ads-BE Changes

1.  Companion banner

    1.  Enable 600 x 600 companion banner support.

    2.  Add `title` in `companionsMeta` tag in ad response.

    3.  \"companionsMeta\": \[ { \"id\": \"mid1\", \"title\": \"Title
        1\" }, { \"id\": \"mid2\", \"title\": \"Title 2\" } \],

    4.  Add two additional beacon urls for companion banners.

        - \"companionAdExpandBeaconUrl\":
          \"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=0123456299b233c06469.93240435&adId=1267393289&campaignId=&adPlacement=video-companion&partnerRef=&city=&state=&country=india&clientId=012345&reqTime=1654239795&eventType=AD_EXPAND&partnerId=DH_APP&nextAdIndex=&contentId=b20177788&contentCreatorId=\"
        - \"companionAdCollapseBeaconUrl\":
          \"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=0123456299b233c06469.93240435&adId=1267393289&campaignId=&adPlacement=video-companion&partnerRef=&city=&state=&country=india&clientId=012345&reqTime=1654239795&eventType=AD_COLLAPSE&partnerId=DH_APP&nextAdIndex=&contentId=b20177788&contentCreatorId=\"

    5.  instream-vdo adResponse

        { \"ads\": \[ { \"type\": \"external-sdk\", \"aduid\":
        \"notId=ad-1971046212\", \"srcUrlExpiry\": 86400, \"adGroupId\":
        \"0123456299b233bf1ff6.85801150\", \"width\": 1080, \"height\":
        607, \"card-position\": 4, \"positionWithTicker\": 4,
        \"min-ad-distance\": 4, \"bannerid\": \"1500328886\",
        \"adTemplate\": \"H\", \"showOnlyImage\": false, \"id\":
        \"5b724d09323f2d2f827d4f35c22f7b7c\", \"span\": 60,
        \"useInternalBrowser\": \"false\", \"useWideViewPort\": false,
        \"allowDelayedAdInsert\": true, \"adContext\": \"b20177788\",
        \"showTitle\": false, \"needsBackupAds\": true,
        \"ignoreVideoDuration\": 480000, \"adDistanceMs\": 180000,
        \"dedupId\": \"5b724d09323f2d2f827d4f35c22f7b7c\",
        \"adCacheGood\": 1, \"adCacheAverage\": 1, \"adCacheSlow\": 1,
        \"isLive\": false, \"showLearnMore\": true, \"adTagPosition\":
        \"BOTTOM_OVERLAY_LEFT\", \"showBorder\": false, \"campaignId\":
        \"1500328886\", \"bannerId\": \"1971046212\", \"isLargeAd\":
        false, \"errorUrl\":
        \"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=5b724d09323f2d2f827d4f35c22f7b7c&adId=1971046212&campaignId=1500328886&adPlacement=instream-vdo&partnerRef=&city=&state=&country=india&clientId=012345&reqTime=1654239795&eventType=AD_ERROR&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=instream-vdo&bookedSubSlot=&contentId=b20177788&contentCreatorId=\",
        \"largeAdDistance\": 8, \"position\": \"instream-vdo\",
        \"sdk-order\": 1, \"landingUrl\": null, \"external\": {
        \"tagURL\":
        \"http%3A%2F%2Fstage-money.dailyhunt.in%2Fgetvmap%3FuniqueId%3D5b724d09323f2d2f827d4f35c22f7b7c%26vmapPayload%3DeyJtaWQxIjp7ImEiOiIxOTcxMDQ2MjEyIiwiYyI6IjE1MDAzMjg4ODYiLCJvIjoiNTcyNDAiLCJvZmYiOiIwMDowMDoyMC4wMDAiLCJydCI6MTY1NDIzOTc5NSwiYnQiOiIzIiwiY2FwIjoiMCIsImN6IjoiMTA4MHgxMDgwIiwiY29JZCI6IjEyODU1MzIxNDAiLCJjb1VuSWQiOiIwMTIzNDU2Mjk5YjIzM2MwMDUxNy42NjMwMDU4OSJ9LCJtaWQyIjp7ImEiOiI0MDEyNDQiLCJjIjoiOTgxNTAiLCJvIjoiNTcyMzUiLCJvZmYiOiIwMDowNDowMC4wMDAiLCJydCI6MTY1NDIzOTc5NSwiYnQiOiIzIiwiY2FwIjoiMCIsImN6IjoiMTA4MHgxMDgwIiwiY29JZCI6IjEyNjczOTMyODkiLCJjb1VuSWQiOiIwMTIzNDU2Mjk5YjIzM2MwNjQ2OS45MzI0MDQzNSJ9fQ%3D%3D%26clientId%3D012345%26requestUrl%3Dhttp%253A%252F%252Fstage-money.dailyhunt.in%252Ffallback%253Fclientid%253D012345%2526req_time%253D03062022%252B12%25253A33%25253A15%2526paper%253D%2526item_category%253D%2526Gpscountry%253Dindia%2526Gpsstate%253D%2526Gpscity%253D%2526IPcountry%253D%2526IPstate%253D%2526IPcity%253D%2526isp%253D%2526user_os_platform%253Dandroid%2526user_handset_maker%253DXiaomi%2526user_handset_model%253DMi%252BA2%2526user_id%253Ddh6b47acbd888b4740a29d933236bc500c%2526placement%253Dinstream-vdo%2526user_app_ver%253D18.6.15.2%2526banner_rotation_type%253D0%2526bannerSelectedBy%253DadEngine%2526bookedPlacement%253Dinstream-vdo%2526banner_id%253D1971046212%2526campaign_id%253D1500328886%2526user_connection%253Dw%2526connection_speed%253DSLOW%2526user_os_ver%253D11.0%2526gaid%253D20ab727a-f437-4753-bbef-f030f5fd7f22%2526item_publisher_language%253D%2526user_languages%253Den%25252C%2526oi%253D1590%2526price_range%253Dnone%2526user_device_type%253Dnone%2526title%253Dvdo%2526promoVdoId%253D%2526promoTopic%253D%2526latitude%253DNA%2526longitude%253DNA%2526uniqueId%253D5b724d09323f2d2f827d4f35c22f7b7c%2526region%253D%2526mcc%253D%2526mnc%253D%2526lac%253D%2526cellid%253D%2526ip%253D157.35.92.167%2526adGroupId%253D0123456299b233bf1ff6.85801150%2526topicId%253Da3617d6e958a315152f3c08c3f2b5f1b%2526topicName%253D%2526ecpm%253D22000%2526audienceSegments%253Dnone%2526resolution%253D1080x2028%2526hostalias%253Ddh-gcp-ads-adengine-ws-stage-az-wdnq%2526locationSource%253D%2526pincode%253D%2526subSlot%253D%2526bookedSubSlot%253D%2526ab%253DECPM%2526partnerId%253DDH_APP%2526deliverySlab%253D1%2526userDeliverySlab%253D%2526dhTvChannelId%253D%2526dhTvType%253D%2526buzzContentpartner%253Dzee_news_zeenews%2526dhTvSourcekey%253Dzee_news%2526dhTvRelevance%253D%2526dhTvUrgency%253D%2526dhTvPartyLeaning%253D%2526pubName%253DDH%2526vdoGroupKey%253D%2526nthImpression%253D1%2526articleId%253Db20177788%2526vpod%253D%2526v_ecpm%253D22000%2526utmSource%253D%2526utmMedium%253D%2526utmCampaign%253D%2526appId%253D%2526autoPlayPref%253D3%2526installDeliverySlab%253D%2526installCpi%253D%2526secondBidderCampaign%253D%2526secondBidderECPM%253D%2526optimisedBy%253D1%2526topCampaignIds%253D1500328886%25255E98150%25255E%2526topCampaignECPMs%253D22000%25255E1000%2526entityId%253Da3617d6e958a315152f3c08c3f2b5f1b%2526entityType%253DHASHTAG%2526entitySubtype%253D%2526contentContext%253D%2526parentContentContext%253D%2526sourceType%253DOGC%2526isHubExclusiveAdRequest%253D%2526mastheadAdCount%253D0%2526sessionSource%253DORGANIC%2526totalAdSessions%253D16%2526totalSeenAds%253D198%2526totalSessions%253D34%2526predictedInstallProbability%253D%2526campaignPrdictedCtr%253D%2526productIds%253D%2526recoPolicy%253D%2526request_timestamp%253D1654239795%2526next_ad_index%253D%2526feed_refresh_count%253D%2526feed_type%253D%2526feed_id%253D%2526ad_extras%253D%2526sub_feed_id%253D%2526profile_type%253D%2526contentId%253Db20177788%2526event_type%253DAD_REQUEST%2526preCalibratedProbability%253D%2526variantName%253D%2526modelUuid%253D%2526networkSwitch%253D%2526topDirectCampaign%253D%2526isAdLoadEnabled%253D%2526lang_affinity%253D%2526is_interleaved%253D0%2526boost_factor%253D1%2526interleave_campaign_daedalus_config%253D0%2526expected_video_watch_duration%253D%2526campaign_type%253DTEST_MODE%2526campaign_level%253DLEVEL_1%2526interleaved_competition%253D%2526isRollUp%253D%2526requestIdDebug%253D969a598ca8b7442a9283518d48bbbccd%2526gender%253D%2526age%253D%2526ageRange%253D%2526orderTypeV2%253D0%2526idfa%253D%2526s2sBidId%253D%2526imputationType%253D%2526contentCreatorId%253D%2526scoringModel%253D%2526filteringModel%253D%2526requestData%253D%25257B%252522products%252522%25253A%25255B%25255D%25257D%2526locUpdate%253D%2526isRegUser%253D1%2526hostAppId%253DDH_APP%2526userBadge%253D%2526reqTime%253D1654239795%2526%26gaid%3D20ab727a-f437-4753-bbef-f030f5fd7f22%26gaidOptoutStatus%3D0%26adPlacement%3Dinstream-vdo%26partnerId%3DDH_APP%26resolution%3D1080x2028%26ciu_szs%3D1080x1080\",
        \"data\": \"IMA-SDK\" }, \"customTracking\": { \"tracking\": \[
        { \"id\": \"start\", \"beaconUrl\":
        \"http://stage-money.dailyhunt.in/impression?uniqueId=5b724d09323f2d2f827d4f35c22f7b7c_mid1&adId=1971046212&campaignId=1500328886&adPlacement=instream-vdo&city=&state=&country=india&clientId=012345&reqTime=1654239795&partnerId=DH_APP\",
        \"errorBeaconUrl\": null, \"adLPTimeSpentBeaconUrl\":
        \"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=5b724d09323f2d2f827d4f35c22f7b7c_mid1&adId=1971046212&campaignId=1500328886&adPlacement=instream-vdo&city=&state=&country=india&clientId=012345&reqTime=1654239795&partnerId=DH_APP&eventType=AD_LP_TIME_SPENT\",
        \"customCompanionTrackings\": {
        \"companionLPTimeSpentBeaconUrl\":
        \"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=0123456299b233c00517.66300589&adId=1285532140&campaignId=&adPlacement=video-companion&partnerRef=&city=&state=&country=india&clientId=012345&reqTime=1654239795&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&nextAdIndex=&contentId=b20177788&contentCreatorId=\",
        \"companionAdExpandBeaconUrl\":
        \"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=0123456299b233c00517.66300589&adId=1285532140&campaignId=&adPlacement=video-companion&partnerRef=&city=&state=&country=india&clientId=012345&reqTime=1654239795&eventType=AD_EXPAND&partnerId=DH_APP&nextAdIndex=&contentId=b20177788&contentCreatorId=\",
        \"companionAdCollapseBeaconUrl\":
        \"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=0123456299b233c00517.66300589&adId=1285532140&campaignId=&adPlacement=video-companion&partnerRef=&city=&state=&country=india&clientId=012345&reqTime=1654239795&eventType=AD_COLLAPSE&partnerId=DH_APP&nextAdIndex=&contentId=b20177788&contentCreatorId=\",
        \"companionClickTracking\": \[ \"https://manish/click\" \] } },
        { \"id\": \"mid1\", \"beaconUrl\":
        \"http://stage-money.dailyhunt.in/impression?uniqueId=5b724d09323f2d2f827d4f35c22f7b7c_mid1&adId=1971046212&campaignId=1500328886&adPlacement=instream-vdo&city=&state=&country=india&clientId=012345&reqTime=1654239795&partnerId=DH_APP\",
        \"errorBeaconUrl\": null, \"adLPTimeSpentBeaconUrl\":
        \"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=5b724d09323f2d2f827d4f35c22f7b7c_mid1&adId=1971046212&campaignId=1500328886&adPlacement=instream-vdo&city=&state=&country=india&clientId=012345&reqTime=1654239795&partnerId=DH_APP&eventType=AD_LP_TIME_SPENT\",
        \"customCompanionTrackings\": {
        \"companionLPTimeSpentBeaconUrl\":
        \"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=0123456299b233c00517.66300589&adId=1285532140&campaignId=&adPlacement=video-companion&partnerRef=&city=&state=&country=india&clientId=012345&reqTime=1654239795&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&nextAdIndex=&contentId=b20177788&contentCreatorId=\",
        \"companionAdExpandBeaconUrl\":
        \"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=0123456299b233c00517.66300589&adId=1285532140&campaignId=&adPlacement=video-companion&partnerRef=&city=&state=&country=india&clientId=012345&reqTime=1654239795&eventType=AD_EXPAND&partnerId=DH_APP&nextAdIndex=&contentId=b20177788&contentCreatorId=\",
        \"companionAdCollapseBeaconUrl\":
        \"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=0123456299b233c00517.66300589&adId=1285532140&campaignId=&adPlacement=video-companion&partnerRef=&city=&state=&country=india&clientId=012345&reqTime=1654239795&eventType=AD_COLLAPSE&partnerId=DH_APP&nextAdIndex=&contentId=b20177788&contentCreatorId=\",
        \"companionClickTracking\": \[ \"https://manish/click\" \] } },
        { \"id\": \"mid2\", \"beaconUrl\":
        \"http://stage-money.dailyhunt.in/impression?uniqueId=5b724d09323f2d2f827d4f35c22f7b7c_mid2&adId=401244&campaignId=98150&adPlacement=instream-vdo&city=&state=&country=india&clientId=012345&reqTime=1654239795&partnerId=DH_APP\",
        \"errorBeaconUrl\": null, \"adLPTimeSpentBeaconUrl\":
        \"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=5b724d09323f2d2f827d4f35c22f7b7c_mid2&adId=401244&campaignId=98150&adPlacement=instream-vdo&city=&state=&country=india&clientId=012345&reqTime=1654239795&partnerId=DH_APP&eventType=AD_LP_TIME_SPENT\",
        \"customCompanionTrackings\": {
        \"companionLPTimeSpentBeaconUrl\":
        \"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=0123456299b233c06469.93240435&adId=1267393289&campaignId=&adPlacement=video-companion&partnerRef=&city=&state=&country=india&clientId=012345&reqTime=1654239795&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&nextAdIndex=&contentId=b20177788&contentCreatorId=\",
        \"companionAdExpandBeaconUrl\":
        \"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=0123456299b233c06469.93240435&adId=1267393289&campaignId=&adPlacement=video-companion&partnerRef=&city=&state=&country=india&clientId=012345&reqTime=1654239795&eventType=AD_EXPAND&partnerId=DH_APP&nextAdIndex=&contentId=b20177788&contentCreatorId=\",
        \"companionAdCollapseBeaconUrl\":
        \"http://stage-money.dailyhunt.in/beaconEvents?uniqueId=0123456299b233c06469.93240435&adId=1267393289&campaignId=&adPlacement=video-companion&partnerRef=&city=&state=&country=india&clientId=012345&reqTime=1654239795&eventType=AD_COLLAPSE&partnerId=DH_APP&nextAdIndex=&contentId=b20177788&contentCreatorId=\"
        } } \] }, \"companionsMeta\": \[ { \"id\": \"mid1\", \"title\":
        \"companionTitle\" }, { \"id\": \"mid2\", \"title\":
        \"companionTitle\" } \], \"adContextRules\": {
        \"selectionPriority\": 2, \"cacheType\": \"session\", \"ttl\":
        300, \"ruleGroup\": { \"rules\": \[ { \"ruleItems\": \[ {
        \"operand\": -1, \"keys\": \[ \"unsafeForVideoAd:true\" \] } \]
        } \], \"respondedFor\": { \"entityIds\": \[
        \"dhcc595822d9d34e4b9c12a93f1fd3812a\", \"nh-headlines\",
        \"a3617d6e958a315152f3c08c3f2b5f1b\" \], \"postId\":
        \"b20177788\" } } }, \"adFeedback\": { \"feedbackUrl\":
        \"http://stage-money.dailyhunt.in/data-api/adfeedback?bannerId=1971046212&campaignId=1500328886&uniqueId=5b724d09323f2d2f827d4f35c22f7b7c&city=\"
        }, \"shareability\": null } \] }

2.  New ad placement `video-storypage`.

    1.  Adresponse for `video-storypage`.

    2.  json{ \"ads\": \[ { \"type\": \"imgLink\", \"aduid\":
        \"notId=ad-2973\", \"srcUrlExpiry\": 60, \"width\": 1080,
        \"height\": 551, \"card-position\": 4, \"positionWithTicker\":
        4, \"min-ad-distance\": 4, \"banner-fill\": \"fill-width\",
        \"bannerid\": \"1105\", \"adTemplate\": \"L\",
        \"showOnlyImage\": false, \"id\":
        \"f97559075ef153efb8062c2763a5634b\", \"span\": 60,
        \"useInternalBrowser\": \"false\", \"useWideViewPort\": true,
        \"adCacheGood\": 1, \"adCacheAverage\": 1, \"adCacheSlow\": 1,
        \"allowDelayedAdInsert\": true, \"adGroupId\":
        \"dh.aDRVYWllWG9ApRm9A3Mnkwc0xINVlyQT09A62972bc77487c0.55989452\",
        \"adContext\": \"n52696283\", \"dedupId\":
        \"f97559075ef153efb8062c2763a5634b\", \"adTagPosition\":
        \"TOP_RIGHT\", \"showBorder\": true, \"adBorderColor\":
        \"#dc1054\", \"campaignId\": \"1105\", \"bannerId\": \"2973\",
        \"isLargeAd\": false, \"errorUrl\":
        \"https://stage-money.dailyhunt.in/beaconEvents?uniqueId=f97559075ef153efb8062c2763a5634b&adId=2973&campaignId=1105&adPlacement=video-storypage&partnerRef=&city=patna&state=bihar&country=india&clientId=dh.aDRVYWllWG9ApRm9A3Mnkwc0xINVlyQT09A&reqTime=1654074311&eventType=AD_ERROR&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=video-storypage&bookedSubSlot=&contentId=n52696283&contentCreatorId=\",
        \"largeAdDistance\": 8, \"position\": \"video-storypage\",
        \"showPlayIcon\": false, \"beaconUrl\":
        \"https://stage-money.dailyhunt.in/impression?uniqueId=f97559075ef153efb8062c2763a5634b&adId=2973&campaignId=1105&adPlacement=video-storypage&partnerRef=&city=patna&state=bihar&country=india&clientId=dh.aDRVYWllWG9ApRm9A3Mnkwc0xINVlyQT09A&reqTime=1654074311&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=video-storypage&bookedSubSlot=&contentId=n52696283&contentCreatorId=\",
        \"content\": { \"imgLink\":
        \"https://stage-ads2.dailyhunt.in/daedalus-banners/401256/1653914463_48941_990x505.jpg\",
        \"itemSubtitle2\": { \"color\": \"#4caf79\", \"color-night\":
        \"#ffffff\", \"data\": \"NewQA\" }, \"reportText\": { \"color\":
        \"#798DED\", \"color-night\": \"#FFFFFF\", \"background-color\":
        \"#40000000\", \"background-color-night\": \"#40000000\",
        \"data\": \"Ad\" } }, \"action\":
        \"https://stage-money.dailyhunt.in/click?clientId=dh.aDRVYWllWG9ApRm9A3Mnkwc0xINVlyQT09A&uniqueId=f97559075ef153efb8062c2763a5634b&adId=2973&campaignId=1105&adPlacement=video-storypage&reqTime=1654074311&billingTypeId=3&orderId=281&forceTracker=&partnerRef=&city=patna&state=bihar&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=video-storypage&bookedSubSlot=&contentId=n52696283&contentCreatorId=&\_\_oadest=https%3A%2F%2Fwww.youtube.com%2F\",
        \"adLPTimeSpentBeaconUrl\":
        \"https://stage-money.dailyhunt.in/beaconEvents?uniqueId=f97559075ef153efb8062c2763a5634b&adId=2973&campaignId=1105&adPlacement=video-storypage&partnerRef=&city=patna&state=bihar&country=india&clientId=dh.aDRVYWllWG9ApRm9A3Mnkwc0xINVlyQT09A&reqTime=1654074311&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=video-storypage&bookedSubSlot=&contentId=n52696283&contentCreatorId=\",
        \"adRespondedBeaconUrl\":
        \"https://stage-money.dailyhunt.in/beaconEvents?uniqueId=f97559075ef153efb8062c2763a5634b&adId=2973&campaignId=1105&adPlacement=video-storypage&partnerRef=&city=patna&state=bihar&country=india&clientId=dh.aDRVYWllWG9ApRm9A3Mnkwc0xINVlyQT09A&reqTime=1654074311&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=video-storypage&bookedSubSlot=&contentId=n52696283&contentCreatorId=\",
        \"adInflatedBeaconUrl\":
        \"https://stage-money.dailyhunt.in/beaconEvents?uniqueId=f97559075ef153efb8062c2763a5634b&adId=2973&campaignId=1105&adPlacement=video-storypage&partnerRef=&city=patna&state=bihar&country=india&clientId=dh.aDRVYWllWG9ApRm9A3Mnkwc0xINVlyQT09A&reqTime=1654074311&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=video-storypage&bookedSubSlot=&contentId=n52696283&contentCreatorId=\",
        \"adContextRules\": { \"selectionPriority\": 2, \"cacheType\":
        \"session\", \"ttl\": 300, \"ruleGroup\": { \"rules\": \[\],
        \"respondedFor\": { \"entityIds\": \[
        \"dhb94a0041718e45b5b1eface00cdef265\",
        \"dhf849f116c1d34f51ab49e982e28afa93\", \"c5_172\" \],
        \"postId\": \"n52696283\" } } }, \"adFeedback\": {
        \"feedbackUrl\":
        \"https://stage-money.dailyhunt.in/data-api/adfeedback?bannerId=2973&campaignId=1105&uniqueId=f97559075ef153efb8062c2763a5634b&city=patna\"
        }, \"requestUrl\":
        \"https://stage-money.dailyhunt.in/fallback?clientid=dh.aDRVYWllWG9ApRm9A3Mnkwc0xINVlyQT09A&req_time=01062022+14%3A35%3A11&paper=dhb94a0041718e45b5b1eface00cdef265&item_category=&Gpscountry=india&Gpsstate=bihar&Gpscity=patna&IPcountry=&IPstate=&IPcity=&isp=airtel&user_os_platform=android&user_handset_maker=Xiaomi&user_handset_model=Mi+A2&user_id=dh6b47acbd888b4740a29d933236bc500c&placement=video-storypage&user_app_ver=18.6.15.2&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=video-storypage&banner_id=2973&campaign_id=1105&user_connection=w&connection_speed=AVERAGE&user_os_ver=11.0&gaid=20ab727a-f437-4753-bbef-f030f5fd7f22&item_publisher_language=&user_languages=en%2C&oi=1039&price_range=none&user_device_type=none&title=Banner&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=f97559075ef153efb8062c2763a5634b&region=patna&mcc=&mnc=&lac=&cellid=PyxVR4H8zW8qWwoHOw6M7w%3D%3D&ip=223.230.131.196&adGroupId=dh.aDRVYWllWG9ApRm9A3Mnkwc0xINVlyQT09A62972bc77487c0.55989452&topicId=&topicName=&ecpm=0&audienceSegments=none&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-qa-az-7fh0&locationSource=IP&pincode=800002&subSlot=&bookedSubSlot=&ab=ECPM&partnerId=DH_APP&deliverySlab=1&userDeliverySlab=&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=7&articleId=n52696283&vpod=&v_ecpm=0&utmSource=&utmMedium=&utmCampaign=&appId=&autoPlayPref=3&installDeliverySlab=&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=1&topCampaignIds=1105%5E&topCampaignECPMs=0&entityId=c5_172&entityType=LOCATION&entitySubtype=&contentContext=&parentContentContext=&sourceType=OGC&isHubExclusiveAdRequest=&mastheadAdCount=0&sessionSource=ORGANIC&totalAdSessions=5&totalSeenAds=33&totalSessions=11&predictedInstallProbability=&campaignPrdictedCtr=&productIds=&recoPolicy=&request_timestamp=1654074311&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=n52696283&event_type=AD_REQUEST&preCalibratedProbability=&variantName=&modelUuid=&networkSwitch=&topDirectCampaign=&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=&campaign_type=TEST_MODE&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=&requestIdDebug=b614108c32f97194aae0b22967eca246&gender=&age=&ageRange=&orderTypeV2=0&idfa=&s2sBidId=&imputationType=&contentCreatorId=&scoringModel=&filteringModel=&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&isRegUser=1&hostAppId=DH_APP&userBadge=&reqTime=1654074311&\",
        \"shareability\": null } \] }

## Client Changes

1.  Companion banner

    1.  Companion banner to be shown below the video and above the
        headline

    2.  Show Companion headline.

    3.  Fire `"companionAdExpandBeaconUrl"` or
        `"companionAdCollapseBeaconUrl"`when companion banner expands or
        collapse.

2.  New ad placement `video-storypage`.

    1.  Client to remove dhtv-masthead position and will not make the
        adrequest for this.

    2.  Instead make adrequest for `video-storypage` position.

    3.  Supported sizes are \[ 990 x 505, 960 x 150, 600 x 600 \].

## Daedalus Changes

1.  Companion banner revamp

    1.  Introduce a new subtype of size 600 x 600 for Companion
        Creatives.

    2.  Only eligible for dailyhunt android version \>= 19.0.x.

    3.  This banner supports customizable headline, so give an option to
        add `itemTitle` field.

2.  New ad placement `video-storypage`.

    1.  Add a new ad placement `video-storypage` under image/html
        creatives (for android dailyhunt \>= 19.0.x).

    2.  `dhtv-masthead` ad placement will not be eligible from dh
        android version \>= 19.0.x.

    3.  All functionality of `storypage` creative will be same for
        `video-storypage`.

    4.  Supported sizes are \[ 990 x 505, 960 x 150, 600 x 600 \].
