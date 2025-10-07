# Requirements

Introduce a new ad slot `sticky-notification` for sticky notifications
in dailyhunt app.

# Ads BE Change

- Ad Response for `sticky-notification` zone

- { \"ads\": \[{ \"type\": \"imgLink\", \"aduid\": \"notId=ad-4083\",
  \"srcUrlExpiry\": 60, \"width\": 1080, \"height\": 169,
  \"adTemplate\": \"L\", \"showOnlyImage\": false, \"id\":
  \"1c008f5d7f3cf5550df8e746d9686836\", \"span\": 60, \"adContext\":
  null, \"allowDelayedAdInsert\": true, \"useInternalBrowser\":
  \"false\", \"useWideViewPort\": true, \"dedupId\":
  \"1c008f5d7f3cf5550df8e746d9686836\", \"card-position\": 1,
  \"positionWithTicker\": 1, \"min-ad-distance\": 4, \"showBorder\":
  false, \"campaignId\": \"1245\", \"bannerId\": \"4083\",
  \"isLargeAd\": false, \"errorUrl\":
  \"http:\\/\\/qa-money.newshunt.com\\/beaconEvents?uniqueId=1c008f5d7f3cf5550df8e746d9686836&adId=4083&campaignId=1245&adPlacement=sticky-notification&partnerRef=&city=patna&state=bihar&country=india&clientId=dh.aDRVYWllWG9ApRm9A3Mnkwc0xINVlyQT09A&reqTime=1654078182&eventType=AD_ERROR&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=sticky-notification&bookedSubSlot=&contentId=&contentCreatorId=\",
  \"largeAdDistance\": 8, \"position\": \"sticky-notification\",
  \"showPlayIcon\": false, \"beaconUrl\":
  \"http:\\/\\/qa-money.newshunt.com\\/impression?uniqueId=1c008f5d7f3cf5550df8e746d9686836&adId=4083&campaignId=1245&adPlacement=sticky-notification&partnerRef=&city=patna&state=bihar&country=india&clientId=dh.aDRVYWllWG9ApRm9A3Mnkwc0xINVlyQT09A&reqTime=1654078182&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=sticky-notification&bookedSubSlot=&contentId=&contentCreatorId=\",
  \"content\": { \"imgLink\":
  \"http:\\/\\/qa-money.newshunt.com\\/daedalus-banners\\/4083\\/1653644786_79374_960x150.jpg\",
  \"itemSubtitle2\": { \"color\": \"#4caf79\", \"color-night\":
  \"#ffffff\" }, \"reportText\": { \"color\": \"#798DED\",
  \"color-night\": \"#FFFFFF\", \"background-color\": \"#40000000\",
  \"background-color-night\": \"#40000000\", \"data\": \"Ad\" } },
  \"action\":
  \"https:\\/\\/qa-money.newshunt.com\\/click?clientId=dh.aDRVYWllWG9ApRm9A3Mnkwc0xINVlyQT09A&uniqueId=1c008f5d7f3cf5550df8e746d9686836&adId=4083&campaignId=1245&adPlacement=sticky-notification&reqTime=1654078182&billingTypeId=3&orderId=281&forceTracker=&partnerRef=&city=patna&state=bihar&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=sticky-notification&bookedSubSlot=&contentId=&contentCreatorId=&\_\_oadest=https%3A%2F%2Fgoogle.com\",
  \"adLPTimeSpentBeaconUrl\":
  \"http:\\/\\/qa-money.newshunt.com\\/beaconEvents?uniqueId=1c008f5d7f3cf5550df8e746d9686836&adId=4083&campaignId=1245&adPlacement=sticky-notification&partnerRef=&city=patna&state=bihar&country=india&clientId=dh.aDRVYWllWG9ApRm9A3Mnkwc0xINVlyQT09A&reqTime=1654078182&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=sticky-notification&bookedSubSlot=&contentId=&contentCreatorId=\",
  \"adRespondedBeaconUrl\":
  \"http:\\/\\/qa-money.newshunt.com\\/beaconEvents?uniqueId=1c008f5d7f3cf5550df8e746d9686836&adId=4083&campaignId=1245&adPlacement=sticky-notification&partnerRef=&city=patna&state=bihar&country=india&clientId=dh.aDRVYWllWG9ApRm9A3Mnkwc0xINVlyQT09A&reqTime=1654078182&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=sticky-notification&bookedSubSlot=&contentId=&contentCreatorId=\",
  \"adInflatedBeaconUrl\":
  \"http:\\/\\/qa-money.newshunt.com\\/beaconEvents?uniqueId=1c008f5d7f3cf5550df8e746d9686836&adId=4083&campaignId=1245&adPlacement=sticky-notification&partnerRef=&city=patna&state=bihar&country=india&clientId=dh.aDRVYWllWG9ApRm9A3Mnkwc0xINVlyQT09A&reqTime=1654078182&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=sticky-notification&bookedSubSlot=&contentId=&contentCreatorId=\",
  \"adContextRules\": { \"selectionPriority\": 2, \"cacheType\":
  \"session\", \"ttl\": 300, \"ruleGroup\": { \"respondedFor\": {
  \"entityIds\": \[\"nh-headlines\",
  \"91581308b67fdfbcd24028a0c513bc37\"\], \"postId\": null } } },
  \"adFeedback\": { \"feedbackUrl\":
  \"http:\\/\\/qa-money.newshunt.com\\/data-api\\/adfeedback?bannerId=4083&campaignId=1245&uniqueId=1c008f5d7f3cf5550df8e746d9686836&city=patna\"
  }, \"requestUrl\":
  \"http:\\/\\/qa-money.newshunt.com\\/fallback?clientid=dh.aDRVYWllWG9ApRm9A3Mnkwc0xINVlyQT09A&req_time=01062022+15%3A39%3A42&paper=&item_category=&Gpscountry=india&Gpsstate=bihar&Gpscity=patna&IPcountry=&IPstate=&IPcity=&isp=airtel&user_os_platform=android&user_handset_maker=Xiaomi&user_handset_model=Mi+A2&user_id=dh6b47acbd888b4740a29d933236bc500c&placement=sticky-notification&user_app_ver=18.6.15.2&banner_rotation_type=0&bannerSelectedBy=RankingService&bookedPlacement=sticky-notification&banner_id=4083&campaign_id=1245&user_connection=w&connection_speed=FAST&user_os_ver=11.0&gaid=20ab727a-f437-4753-bbef-f030f5fd7f22&item_publisher_language=&user_languages=en%2C&oi=1051&price_range=none&user_device_type=none&title=dhtv-masthead&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=1c008f5d7f3cf5550df8e746d9686836&region=patna&mcc=&mnc=&lac=&cellid=&ip=223.230.131.196&adGroupId=dh.aDRVYWllWG9ApRm9A3Mnkwc0xINVlyQT09A62973ae6f28930.08031017&topicId=91581308b67fdfbcd24028a0c513bc37&topicName=&ecpm=10000&audienceSegments=none&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-qa-az-7fh0&locationSource=IP&pincode=800002&subSlot=&bookedSubSlot=&ab=ECPM&partnerId=DH_APP&deliverySlab=1&userDeliverySlab=&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=4&articleId=&vpod=&v_ecpm=10000&utmSource=&utmMedium=&utmCampaign=&appId=&autoPlayPref=3&installDeliverySlab=&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=1&topCampaignIds=1245%5E&topCampaignECPMs=10000&entityId=91581308b67fdfbcd24028a0c513bc37&entityType=HASHTAG&entitySubtype=unknown&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&mastheadAdCount=0&sessionSource=&totalAdSessions=6&totalSeenAds=35&totalSessions=12&predictedInstallProbability=&campaignPrdictedCtr=&productIds=&recoPolicy=&request_timestamp=1654078182&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=&variantName=&modelUuid=&networkSwitch=&topDirectCampaign=&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=&campaign_type=TEST_MODE&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=&requestIdDebug=2671197e69d53d599b3d95c636d424dd&gender=&age=&ageRange=&orderTypeV2=0&idfa=&s2sBidId=&imputationType=&contentCreatorId=&scoringModel=&filteringModel=&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&isRegUser=1&hostAppId=DH_APP&userBadge=&reqTime=1654078182&\",
  \"shareability\": null }\] }

# Handshake change

- BE will add a bool flag `adsOnNewsSticky` in handshake.

- If `adsOnNewsSticky` flag is set to true then only client will make an
  adrequest for `sticky-notification`.

- `"adsOnNewsSticky": true,`

# Daedalus Change

- Enable a new zone `sticky-notification` under image creative type.

- Supported sizes are 990 x 505, 960 x 150.

- Restrict landing page target to internal browser only.

- This zone is only eligible for dh android version \>= 19.0.x.

# Client Change

- Client to check `adsOnNewsSticky` flag in handshake.

- If `adsOnNewsSticky` is set to true then only make an adrequest for
  `sticky-notification` ad-slot.

- Click on the ad should open the deeplink in the internal browser of
  the app.
