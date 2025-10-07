# Product Doc

Image Ads - CTA Animation

# Figma Link

https://www.figma.com/file/lZGqTG7GWnziqkxtM2qDvR/Josh-ads?node-id=7283%3A32849

# Requirements

With the onset of ads monetisation on Josh, it is important to grab
users\' attention to ensure that they are interacting with the ads more.
In order to increase click through rates on these branded ad campaigns,
it is important to improve the UI of the ads screen and visibility of
the CTA button. Configurable animation to control the position of the
CTA button for Only for single Image Ads.

# AdEngine Changes

- AdEngine will introduce overlay CTA config.

json{ \"content\": { \"overlayCTA\": { \"transitionDelayInMS\": 3000,
\"title\": { \"color\": \"#FFFFFF\", \"data\": \"Title\" },
\"description\": { \"color\": \"#FFFFFF\", \"data\": \"Description\" },
\"icon\": { \"data\": \"\<iconUrl\>\" }, \"action\": \"\<click url\>\",
\"itemSubtitle2\": { \"color\": \"#FFFFFF\", \"bg-color\": \"#EA4E60\",
\"data\": \"Click Here\", \"isPopupView\": true, \"dimension\": {
\"margin\": \"16\", \"fontSize\": 14, \"fontType\": \"BOLD\" } } } } }

# Client Changes

- client honours overlay CTA config from content tag.

- if config is not present means, overlay is disabled.

- client should consider clickUrl as overlay cta's action tag value.

- transitionDelayTime is in MS

# DD Changes

- DD will introduce allow overlay cta config only for image banner.

- Once this config is enable, DD needs to add below fields for
  configuration.

- DD needs to add title, description, icon and action text.

- Only action text is mandatory field.

- Icon size should be always 1:1 ratio.

- DD needs to add CTA button colour, CTA text colour, opacity, margin
  CTA, font size CTA and font size just like for R13 and pick same
  default value from R13 release.

# Response Protocol

json{ \"ads\": \[ { \"type\": \"pgi-native-article\", \"position\":
\"list-ad\", \"campaignId\": \"1214\", \"id\":
\"a46393b6f9458500f972db3e364c93f9\", \"span\": 0,
\"useInternalBrowser\": \"true\", \"useWideViewPort\": true,
\"beaconUrl\":
\"https://qa-money.myjosh.in/impression?uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&reqTime=1663822077&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=\",
\"adRespondedBeaconUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&reqTime=1663822077&eventType=AD_RESPONDED&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=\",
\"adInflatedBeaconUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&reqTime=1663822077&eventType=AD_INFLATED&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=\",
\"landingUrlAdditional\": \[ \"jgkjhkjn.com\", \"hsgjkhgf.in\",
\"dlkhlk.io\" \], \"content\": { \"itemSubtitle2\": { \"data\": \"Click
Me\", \"color\": \"#e56dee\", \"bg-color\": \"#e6090deb\",
\"isAnimated\": false, \"dimension\": { \"margin\": \"16\",
\"fontSize\": \"8\", \"fontType\": \"BOLD\" }, \"isPopupView\": true },
\"id\": \"ba09899c-2ebf-4563-9ad0-d960f891e08d\", \"itemTag\": {
\"color\": \"#0889ac\", \"color-night\": \"#a5a5a5\", \"data\":
\"Advertisement\" }, \"itemImage\": { \"data\":
\"https://qa-money.myjosh.in/daedalus-banners/3788/1645078378_59747_1080x2592.jpg\"
}, \"overlayCTA\": { \"transitionDelayInMS\": 3000, \"title\": {
\"color\": \"#FFFFFF\", \"data\": \"Title\" }, \"description\": {
\"color\": \"#FFFFFF\", \"data\": \"Description\" }, \"icon\": {
\"data\": \"\<iconUrl\>\" }, \"action\": \"\<click url\>\",
\"itemSubtitle2\": { \"color\": \"#FFFFFF\", \"bg-color\": \"#EA4E60\",
\"data\": \"Click Here\", \"isPopupView\": true, \"dimension\": {
\"margin\": \"16\", \"fontSize\": 14, \"fontType\": \"BOLD\" } } } },
\"action\":
\"https://qa-money.myjosh.in/click?clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&reqTime=1663822077&billingTypeId=3&orderId=281&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=&\_\_oadest=https%3A%2F%2Fgoogle.com\",
\"adFeedback\": { \"feedbackUrl\":
\"https://qa-money.myjosh.in/data-api/adfeedback?bannerId=3788&campaignId=1214&uniqueId=a46393b6f9458500f972db3e364c93f9&city=\"
}, \"omTrackType\": \"none\", \"omVendorsInfo\": null, \"errorUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&reqTime=1663822077&eventType=AD_ERROR&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=\",
\"brandId\": \"152\", \"removeTitle\": true, \"adGroupId\":
\"c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A632be8fd127756.85904213\",
\"adCommentBeaconUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&reqTime=1663822077&eventType=AD_COMMENT&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=\",
\"adLikeBeaconUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&reqTime=1663822077&eventType=AD_LIKE&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=\",
\"adTimeSpentBeaconUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&reqTime=1663822077&eventType=AD_TIME_SPENT&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=\",
\"adShareBeaconUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&reqTime=1663822077&eventType=AD_SHARED&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=\",
\"adLPTimeSpentBeaconUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&reqTime=1663822077&eventType=AD_LP_TIME_SPENT&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=\",
\"adDislikeBeaconUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&reqTime=1663822077&eventType=AD_DISLIKE&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=\",
\"brandFollowBeaconUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&reqTime=1663822077&eventType=BRAND_FOLLOW&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=\",
\"brandUnfollowBeaconUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&reqTime=1663822077&eventType=BRAND_UNFOLLOW&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=\",
\"adClosedBeaconUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&reqTime=1663822077&eventType=AD_CLOSE&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=\",
\"swipeUpDelay\": \"3000\", \"adTag\": \"0\", \"beaconUrlAdditional\":
\[\], \"shareability\": { \"text\": \"Share text https://google.com\",
\"subject\": \"Share Subject\" } } \] }

# [MOC LINK](https://qa-money.myjosh.in/josh_r14_image.json)
