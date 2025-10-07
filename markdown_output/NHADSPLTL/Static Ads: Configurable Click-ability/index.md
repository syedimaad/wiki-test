# Requirement

Implement configurable click-ability for static ads on following rules
config availability:

- Click-ability only on CTA

<!-- -->

- Click-ability on entire Image

# AdEngine Changes

- AdEngine will add `ctaOnlyClick: <bool>` into response

# Client Changes

- Client check for `ctaOnlyClick` flag.

- When this flag is `true`, client make only CTA bar to be clickable.

- When this flag is `false`, client make full page clickable including
  CTA.

- When this flag is `not present`, client defaults to CTA only clickable

# DD Changes

- DD will add `ctaOnlyClick` flag for image banner.

- Default Value: true

# Response Protocol

json{ \"ads\": \[ { \"type\": \"pgi-native-article\", \"position\":
\"list-ad\", \"campaignId\": \"1151\", \"id\":
\"22324cc60b8f3f9163969d62b354ab56\", \"span\": 0,
\"useInternalBrowser\": \"true\", \"useWideViewPort\": true,
\"beaconUrl\":
\"https://qa-money.myjosh.in/impression?uniqueId=22324cc60b8f3f9163969d62b354ab56&adId=3297&campaignId=1151&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=j.a3FtRVpiVnRuQzBaRDFLWDNoSkUrUT09A&reqTime=1663914254&partnerId=JOSH_APP&subSlot=%3E2&nextAdIndex=4&bookedPlacement=list-ad&bookedSubSlot=%3E2&contentId=&contentCreatorId=\",
\"adRespondedBeaconUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=22324cc60b8f3f9163969d62b354ab56&adId=3297&campaignId=1151&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=j.a3FtRVpiVnRuQzBaRDFLWDNoSkUrUT09A&reqTime=1663914254&eventType=AD_RESPONDED&partnerId=JOSH_APP&subSlot=%3E2&nextAdIndex=4&bookedPlacement=list-ad&bookedSubSlot=%3E2&contentId=&contentCreatorId=\",
\"adInflatedBeaconUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=22324cc60b8f3f9163969d62b354ab56&adId=3297&campaignId=1151&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=j.a3FtRVpiVnRuQzBaRDFLWDNoSkUrUT09A&reqTime=1663914254&eventType=AD_INFLATED&partnerId=JOSH_APP&subSlot=%3E2&nextAdIndex=4&bookedPlacement=list-ad&bookedSubSlot=%3E2&contentId=&contentCreatorId=\",
\"landingUrlAdditional\": \[\], \"content\": { \"itemSubtitle2\": {
\"data\": \"Install Now\", \"color\": \"#ffffff\", \"bg-color\":
\"#ffea4e60\", \"isAnimated\": true, \"animationConfig\": {
\"initialButtonColor\": \"#66ffffff\", \"finalButtonColor\":
\"#ffea4e60\", \"initialTextColor\": \"#ffffff\", \"finalTextColor\":
\"#ffffff\", \"startTime\": \"2000\", \"endTime\": \"3000\" },
\"dimension\": { \"margin\": \"16\", \"fontSize\": \"14\", \"fontType\":
\"BOLD\" }, \"isPopupView\": true }, \"id\":
\"6f70b701-1137-4599-9ea9-9de932551792\", \"itemTag\": { \"color\":
\"#0889ac\", \"color-night\": \"#a5a5a5\", \"data\": \"Sponsored\" },
\"itemImage\": { \"data\":
\"https://qa-money.myjosh.in/daedalus-banners/3297/1655278486_95388_1080x2592.jpg\"
} }, \"action\":
\"https://qa-money.myjosh.in/click?clientId=j.a3FtRVpiVnRuQzBaRDFLWDNoSkUrUT09A&uniqueId=22324cc60b8f3f9163969d62b354ab56&adId=3297&campaignId=1151&adPlacement=list-ad&reqTime=1663914254&billingTypeId=2&orderId=238&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=JOSH_APP&subSlot=%3E2&nextAdIndex=4&bookedPlacement=list-ad&bookedSubSlot=%3E2&contentId=&contentCreatorId=&\_\_oadest=https%3A%2F%2Fplay.google.com%2Fstore%2Fapps%2Fdetails%3Fid%3Dcom.mobidia.android.mdm\",
\"adFeedback\": { \"feedbackUrl\":
\"https://qa-money.myjosh.in/data-api/adfeedback?bannerId=3297&campaignId=1151&uniqueId=22324cc60b8f3f9163969d62b354ab56&city=\"
}, \"omTrackType\": \"none\", \"omVendorsInfo\": null, \"errorUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=22324cc60b8f3f9163969d62b354ab56&adId=3297&campaignId=1151&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=j.a3FtRVpiVnRuQzBaRDFLWDNoSkUrUT09A&reqTime=1663914254&eventType=AD_ERROR&partnerId=JOSH_APP&subSlot=%3E2&nextAdIndex=4&bookedPlacement=list-ad&bookedSubSlot=%3E2&contentId=&contentCreatorId=\",
\"brandId\": \"14\", \"removeTitle\": true, \"ctaOnlyClick\": true,
\"adGroupId\":
\"j.a3FtRVpiVnRuQzBaRDFLWDNoSkUrUT09A632d510e3eaf24.65967719\",
\"adCommentBeaconUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=22324cc60b8f3f9163969d62b354ab56&adId=3297&campaignId=1151&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=j.a3FtRVpiVnRuQzBaRDFLWDNoSkUrUT09A&reqTime=1663914254&eventType=AD_COMMENT&partnerId=JOSH_APP&subSlot=%3E2&nextAdIndex=4&bookedPlacement=list-ad&bookedSubSlot=%3E2&contentId=&contentCreatorId=\",
\"adLikeBeaconUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=22324cc60b8f3f9163969d62b354ab56&adId=3297&campaignId=1151&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=j.a3FtRVpiVnRuQzBaRDFLWDNoSkUrUT09A&reqTime=1663914254&eventType=AD_LIKE&partnerId=JOSH_APP&subSlot=%3E2&nextAdIndex=4&bookedPlacement=list-ad&bookedSubSlot=%3E2&contentId=&contentCreatorId=\",
\"adTimeSpentBeaconUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=22324cc60b8f3f9163969d62b354ab56&adId=3297&campaignId=1151&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=j.a3FtRVpiVnRuQzBaRDFLWDNoSkUrUT09A&reqTime=1663914254&eventType=AD_TIME_SPENT&partnerId=JOSH_APP&subSlot=%3E2&nextAdIndex=4&bookedPlacement=list-ad&bookedSubSlot=%3E2&contentId=&contentCreatorId=\",
\"adShareBeaconUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=22324cc60b8f3f9163969d62b354ab56&adId=3297&campaignId=1151&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=j.a3FtRVpiVnRuQzBaRDFLWDNoSkUrUT09A&reqTime=1663914254&eventType=AD_SHARED&partnerId=JOSH_APP&subSlot=%3E2&nextAdIndex=4&bookedPlacement=list-ad&bookedSubSlot=%3E2&contentId=&contentCreatorId=\",
\"adLPTimeSpentBeaconUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=22324cc60b8f3f9163969d62b354ab56&adId=3297&campaignId=1151&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=j.a3FtRVpiVnRuQzBaRDFLWDNoSkUrUT09A&reqTime=1663914254&eventType=AD_LP_TIME_SPENT&partnerId=JOSH_APP&subSlot=%3E2&nextAdIndex=4&bookedPlacement=list-ad&bookedSubSlot=%3E2&contentId=&contentCreatorId=\",
\"adDislikeBeaconUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=22324cc60b8f3f9163969d62b354ab56&adId=3297&campaignId=1151&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=j.a3FtRVpiVnRuQzBaRDFLWDNoSkUrUT09A&reqTime=1663914254&eventType=AD_DISLIKE&partnerId=JOSH_APP&subSlot=%3E2&nextAdIndex=4&bookedPlacement=list-ad&bookedSubSlot=%3E2&contentId=&contentCreatorId=\",
\"brandFollowBeaconUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=22324cc60b8f3f9163969d62b354ab56&adId=3297&campaignId=1151&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=j.a3FtRVpiVnRuQzBaRDFLWDNoSkUrUT09A&reqTime=1663914254&eventType=BRAND_FOLLOW&partnerId=JOSH_APP&subSlot=%3E2&nextAdIndex=4&bookedPlacement=list-ad&bookedSubSlot=%3E2&contentId=&contentCreatorId=\",
\"brandUnfollowBeaconUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=22324cc60b8f3f9163969d62b354ab56&adId=3297&campaignId=1151&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=j.a3FtRVpiVnRuQzBaRDFLWDNoSkUrUT09A&reqTime=1663914254&eventType=BRAND_UNFOLLOW&partnerId=JOSH_APP&subSlot=%3E2&nextAdIndex=4&bookedPlacement=list-ad&bookedSubSlot=%3E2&contentId=&contentCreatorId=\",
\"adClosedBeaconUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=22324cc60b8f3f9163969d62b354ab56&adId=3297&campaignId=1151&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=j.a3FtRVpiVnRuQzBaRDFLWDNoSkUrUT09A&reqTime=1663914254&eventType=AD_CLOSE&partnerId=JOSH_APP&subSlot=%3E2&nextAdIndex=4&bookedPlacement=list-ad&bookedSubSlot=%3E2&contentId=&contentCreatorId=\",
\"adTag\": \"\>2\", \"beaconUrlAdditional\": \[\], \"shareability\": {
\"text\": \"My Data Transfer\", \"subject\": \"Data Usage\", \"image\":
\"https://qa-money.myjosh.in/daedalus-banners/3297/1619080669_59997_share_image.jpg\"
} } \] }

# [MOC LINK](https://qa-money.myjosh.in/ctaOnlyClick.json)
