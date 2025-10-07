# Product Doc

# Figma

https://www.figma.com/file/lZGqTG7GWnziqkxtM2qDvR/Josh-ads?node-id=8032%3A48317

# AdEngine Changes

- AdEngine whitelist carousel banner type and prepare response.

- Please check response protocol section.

- new beacons added for each item.

- Third party imp/click at banner level will be picked from first item's
  third party click and imp.

# Client Changes

- Client parse carousel response and render accordingly.

- we have shareability data for each item.

# DD Changes

- DD introduce new banner type called image carousel

- Image size will be 1080x2592

- Each carousel item ( image item ), will be same as static image
  banner.

- Parent carousel banner has contentId, CTA margin, font size and font
  type.

- Ads ops can change/play carousel item's position.

- Only last carousel item will be eligible for overlay CTA config.

# Response Protocol

Responsejson{ \"ads\": \[ { \"type\": \"carousel\", \"position\":
\"list-ad\", \"campaignId\": \"1214\", \"id\":
\"a46393b6f9458500f972db3e364c93f9\", \"useInternalBrowser\": \"true\",
\"useWideViewPort\": true, \"beaconUrl\":
\"https://qa-money.myjosh.in/impression?uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&reqTime=1663822077&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=\",
\"adRespondedBeaconUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&reqTime=1663822077&eventType=AD_RESPONDED&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=\",
\"adInflatedBeaconUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&reqTime=1663822077&eventType=AD_INFLATED&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=\",
\"content\": { \"items\": \[ { \"index\": 1, \"itemSubtitle2\": {
\"data\": \"Click Me\", \"color\": \"#e56dee\", \"bg-color\":
\"#e6090deb\", \"isAnimated\": false, \"dimension\": { \"margin\":
\"16\", \"fontSize\": \"8\", \"fontType\": \"BOLD\" }, \"isPopupView\":
true }, \"itemTag\": { \"color\": \"#0889ac\", \"color-night\":
\"#a5a5a5\", \"data\": \"Advertisement\" }, \"itemImage\": { \"data\":
\"https://qa-money.myjosh.in/daedalus-banners/3788/1645078378_59747_1080x2592.jpg\"
}, \"carouselItemViewUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&reqTime=1663822077&eventType=CAROUSEL_ITEM_VIEW&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=\",
\"action\":
\"https://qa-money.myjosh.in/click?clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&reqTime=1663822077&billingTypeId=3&orderId=281&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=&\_\_oadest=https%3A%2F%2Fgoogle.com\",
\"carouselItemClickUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&reqTime=1663822077&eventType=CAROUSEL_ITEM_CLICK&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=\",
\"carouselItemTimeSpentUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&reqTime=1663822077&eventType=CAROUSEL_ITEM_TIME_SPENT&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=\",
\"ctaOnlyClick\": true, \"carouselItemLPTimeSpentUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&reqTime=1663822077&eventType=CAROUSEL_ITEM_LP_TIME_SPENT&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=\",
}, { \"index\": 2, \"itemSubtitle2\": { \"data\": \"Click Me\",
\"color\": \"#e56dee\", \"bg-color\": \"#e6090deb\", \"isAnimated\":
false, \"dimension\": { \"margin\": \"16\", \"fontSize\": \"8\",
\"fontType\": \"BOLD\" }, \"isPopupView\": true }, \"itemTag\": {
\"color\": \"#0889ac\", \"color-night\": \"#a5a5a5\", \"data\":
\"Advertisement\" }, \"itemImage\": { \"data\":
\"https://qa-money.myjosh.in/daedalus-banners/3788/1645078378_59747_1080x2592.jpg\"
}, \"beaconUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&reqTime=1663822077&eventType=CAROUSEL_ITEM_VIEW&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=\",
\"action\":
\"https://qa-money.myjosh.in/click?clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&reqTime=1663822077&billingTypeId=3&orderId=281&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=&\_\_oadest=https%3A%2F%2Fgoogle.com\",
\"carouselItemClickUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&reqTime=1663822077&eventType=CAROUSEL_ITEM_CLICK&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=\",
\"carouselItemTimeSpentUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&reqTime=1663822077&eventType=CAROUSEL_ITEM_TIME_SPENT&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=\",
\"ctaOnlyClick\": true, \"carouselItemLPTimeSpentUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&reqTime=1663822077&eventType=CAROUSEL_ITEM_LP_TIME_SPENT&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=\",
}, { \"index\": 3, \"itemSubtitle2\": { \"data\": \"Click Me\",
\"color\": \"#e56dee\", \"bg-color\": \"#e6090deb\", \"isAnimated\":
false, \"dimension\": { \"margin\": \"16\", \"fontSize\": \"8\",
\"fontType\": \"BOLD\" }, \"isPopupView\": true }, \"itemTag\": {
\"color\": \"#0889ac\", \"color-night\": \"#a5a5a5\", \"data\":
\"Advertisement\" }, \"itemImage\": { \"data\":
\"https://qa-money.myjosh.in/daedalus-banners/3788/1645078378_59747_1080x2592.jpg\"
}, \"beaconUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&reqTime=1663822077&eventType=CAROUSEL_ITEM_VIEW&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=\",
\"action\":
\"https://qa-money.myjosh.in/click?clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&reqTime=1663822077&billingTypeId=3&orderId=281&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=&\_\_oadest=https%3A%2F%2Fgoogle.com\",
\"carouselItemClickUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&reqTime=1663822077&eventType=CAROUSEL_ITEM_CLICK&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=\",
\"carouselItemTimeSpentUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&reqTime=1663822077&eventType=CAROUSEL_ITEM_TIME_SPENT&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=\",
\"ctaOnlyClick\": true, \"carouselItemLPTimeSpentUrl\":
\"https://qa-money.myjosh.in/beaconEvents?uniqueId=a46393b6f9458500f972db3e364c93f9&adId=3788&campaignId=1214&adPlacement=list-ad&partnerRef=&city=&state=&country=india&clientId=c.ZytmeXhqVVdjSjR1Q0hORUxSTExKZz09A&reqTime=1663822077&eventType=CAROUSEL_ITEM_LP_TIME_SPENT&partnerId=JOSH_APP&subSlot=0&nextAdIndex=0&bookedPlacement=list-ad&bookedSubSlot=0&contentId=&contentCreatorId=\",
} \], \"id\": \"ba09899c-2ebf-4563-9ad0-d960f891e08d\", },
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

# [MOC](https://qa-money.myjosh.in/carousel_josh.json)

------------------------------------------------------------------------

BEACON EVENTS need to be tested(QA):

1.  Beacon url/impression url at banner level.

2.  Adresponded.

3.  Adinflated.

4.  `adCommentBeaconUrl`

5.  `adLikeBeaconUrl`

6.  `adTimeSpentBeaconUrl`

7.  `adLPTimeSpentBeaconUrl`

8.  `adDislikeBeaconUrl`

9.  `adClosedBeaconUrl`

10. `errorUrl`

11. `brandFollowBeaconUrl`

12. `brandUnfollowBeaconUrl`

13. Third party clicks and imps

Item level:

1)`carouselItemViewUrl`

2)`action`

3)`carouselItemClickUrl`

4)`carouselItemTimeSpentUrl`

5)`carouselItemLPTimeSpentUrl`

Features:

1)overlaycta for last item.

2)CTA animation.

3)Shareblility.

4)Item tag from BE.
