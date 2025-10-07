1710px

# Overview

The scope of this job is to seed the Object Store static response that
will be catered to the evergreen Ads request from the DH app.

# Workflow

Below is the workflow of different components involved in this process -

## **Daedalus**

1.  There will be a way to create evergreen campaigns, with appropriate
    identifier in the `dhx_requirements` table. Also, these evergreen
    campaigns are not eligible for regular AdRequests.

2.  For evergreen category, restrict configurable options as below:

Configurable options for Evergreen ads in Daedalus:

**[Configurable Options on Campaign creation screen:]{.underline}**

- Campaign Name

- AdPlacement

- Campaign Classification (only for reporting)

- Delivery Modes

- **Is Content Campaign?** - **[Confirm from
  Chacko]{style="color: rgb(0,102,68);"}**

- Start Date/End Date

- Campaign Execution Plan [- Not allowed
  ]{style="color: rgb(255,86,48);"}

- Creatives Type: [only "display"
  option]{style="color: rgb(76,154,255);"}

- Bill On: no change

- Billing Type: [only "CPM" option]{style="color: rgb(76,154,255);"}

- Optimization Type [- Edit Not allowed. Default value:
  Click]{style="color: rgb(255,86,48);"}

- Number of Impressions

- Billing Rate (Per 1000 Impressions)

- Total Value

- Is PG Campaign? -[ Not allowed -
  value:off]{style="color: rgb(255,86,48);"}

- Is PD Campaign? [- Not allowed -
  value:off]{style="color: rgb(255,86,48);"}

- is Adjunct Campaign? **[Discuss with
  Siva]{style="color: rgb(0,102,68);"}**

- Is Value Add (Campaign will not be billed)

- Delivery Type: [Only Contract Exclusive option
  allowed]{style="color: rgb(76,154,255);"}

- Stop Campaign After Inventory Is Met? - [Not allowed -
  value:off]{style="color: rgb(255,86,48);"}

- Impression UUs Minimum Requirement - [Not allowed -
  value:blank]{style="color: rgb(255,86,48);"}

- Enable Custom Bidding Rate - [Not allowed -
  value:off]{style="color: rgb(255,86,48);"}

- Allow Roll Up - [Not allowed -
  value:off]{style="color: rgb(255,86,48);"}

- Context Targeting - [Not allowed ]{style="color: rgb(255,86,48);"}

- Estimated Audience Reach / Targeting: [Allowed options:
  ]{style="color: rgb(76,154,255);"}`countries,states,languages,os`

**[Configurable Options on Campaign \> Manage screen:]{.underline}**

- Sub Targeting: [Allowed options:
  ]{style="color: rgb(76,154,255);"}`countries,states,languages,os`

- Soft Tag - [Not allowed ]{style="color: rgb(255,86,48);"}

- Tracker Configs

- Frequency Cap

- Version Frequency Cap - [Not allowed ]{style="color: rgb(255,86,48);"}

1.  Only *Image Banner*, *Inline HTML Banner and Mraid-zip(splash)
    Banner* types will be eligible to be configured in these type of
    campaigns.

2.  For the Image Banners, the images are also converted to WebP format
    (in order to make them lighter).

3.  Only limited targetings are allowed for such evergreen campaigns.
    Keeping it to `country` only for now.

4.  These evergreen campaigns are usually long period campaigns, in
    order to help longer cache time for thin users.

5.  DD to enable only these zones
    `CARD_P0, CARD_P1, STORYPAGE, PGI, SPLASH, CARD_PP1, SUPPLEMENT`
    with all subslots for card-pp1 and supplement.

## **MPE**

1.  The activation and deactivation of the evergreen campaigns happen
    based on the start and end dates of the campaigns.

## **Client**

1.  Client should make Ads Handshake request on notification receipt if
    and only if there was no Ads Handshake in the history.

    1.  The client can also make this request along with the pull
        notification with appropriate ttl within which no handshake
        happens (via this path).

    2.  Pull notification timer and ttl configurable from gateway BE.

2.  Client should parse the Ads Handshake response containing the global
    configurations about evergreen Ads. These will include -

    1.  `enabled=true/false`

    2.  `endpoint=http://money.dailyhunt.in/getEgAds`

    3.  Refer the exhaustive [list of configurations
        here](https://evp.atlassian.net/wiki/spaces/NHADSPLTL/pages/109609309/Evergreen+Ads+-+Protocol+V1#Response).

3.  Client should make evergreen Ad Requests on the notification
    receipt.

4.  Client should not fire evergreen adrequest till language is chosen.

5.  Client should resolve the country of the user (maybe, using ISP)?

6.  Client should parse the evergreen Ad Response and create the cache
    accordingly. Client should be able to do this only on `200 OK`
    response.

7.  Client should utilise the cached evergreen Ads based on the
    opportunity -

    1.  Evergreen substitute timer which is different for thin and
        regular users, shared in the evergreen Ad Response.

    2.  First Ad in the day substitute timer which is different for thin
        and regular users, shared in the evergreen Ad Response.

    3.  Non-200 OK Response.

8.  Client should consider the Ads based on start and end time of the
    Ads, send in the evergreen Ad Response.

9.  Client should run the probabilistic distribution on the Ads based on
    the `priority` and `weight` send in the evergreen Ad Response.

    1.  Ad with high `priority` takes precedence and get selected.

    2.  If multiple ads are having same priority, then select ad based
        on the probabilistic distribution logic using `weight`

    3.  Refer this.

10. Client should replace the macros sent in the evergreen Ad Response.

11. Just before considering an evergreen Ad to render, the client should
    trigger the `requestURL` of that Ad.

12. Client should trigger all the beacon URLs as usual.

13. Client should refresh the evergreen Ads based on the
    `ttl(apiFetchDelay)` sent in the ads handshake.

14. Client should not make any further evergreen Ad Requests until the
    `ttl` has passed, even if there are multiple notification
    receipts/app launches during this time.

15. Client should consider the value sent for `isRegUser=true` in the
    ads handshake to consider whether the user is a regular user or not.

16. Client should use the thin user timeouts only if `isRegUser` is
    false/not present in the ads handshake.

17. API Versioning

    1.  Server sends Header `ETag` in the Response.

    2.  `ETag: "33a64df551425fcc55e4d42a148795d9f25f89d4"`

    3.  Client need to send Header `If-None-Match` in the subsequent
        requests with Etag value.

    4.  `If-None-Match: "33a64df551425fcc55e4d42a148795d9f25f89d4"`

    5.  The server compares the client\'s `ETag` (sent with
        `If-None-Match`) with the `ETag` for its current version of the
        resource, and if both values match (that is, the resource has
        not changed), the server sends back a `304` `Not Modified`
        status, without a body, which tells the client that the cached
        version of the response is still good to use (*fresh*).

## Cache Primer

1.  Cache Primer should query the Daedalus DB for the evergreen Ads
    separately.

2.  Cache Primer should consider the number of banners limit from the
    application config.

3.  Cache Primer should run respective Ad Handlers to create the Ad
    Responses. *(*[*Sample Ad
    Response*](https://evp.atlassian.net/wiki/spaces/NHADSPLTL/pages/109609309/Evergreen+Ads+-+Protocol+V1#Response)*)*

4.  Cache Primer to add `eg=1` parameter in the `requestUrl`.

5.  Once the response is ready, Cache Primer should push this json into
    the Google Cloud Storage bucket.

6.  to check on how E-Tags need to be implemented and also if the
    response can be gzipped.

7.  Send empty ad in the response always with least priority so that
    empty beacons will be triggered when there are no eligible ads.

## Evergreen Ad Serving Backend

1.  We will have a new API endpoint (say - `/getEgAds`) using which the
    GTM will divert the traffic to Akamai CDN.

2.  The objects that are cached into the Google Cloud Storage are
    catered from the Akamai/Google CDN directly.

3.  The CDN or the client takes the responsibility to resolve the
    country from which the Ad Request is originating and replace the
    country code in the Ad Request params.

4.  The CDN will then query for appropriate object from the Google Cloud
    Storage if-and-only-if the ETag is different from the current
    version of the object and in case of cache-miss. Else, responds
    `304 Not Modified`.

## AdEngine

### AdInflated

1.  Log the reason for showing evergreen ads.

    1.  Post Body details

        1.  isRegularUser : Boolean regAdTimeout : Long isFirstAd :
            Boolean

    2.  Logging details for the above.

        1.  { \"isRegularUserClient\":\"1\", \"regAdTimeout\":\"3600\",
            \"isFirstAd\":\"1\" }

### AdImpression

1.  On the receipt of evergreen Ad Impression, stamp `egAdShown=true`
    cookie with expiry of 1 day.

2.  On the receipt of regular Ad Impression, increment `regAdCount`
    cookie value with the expiry of `d` days.

    1.  This cookie will contain a map of the bucket number (ex: 3days)
        and the value of count of regular Ad Impressions received during
        that bucket (ex: 3days). 3 days bucket is calculated for a
        number of year. The bucket ranges from 1-121. `ct` is number of
        regular ad impressions for 3 days. `mod` is the last modified
        timestamp.

    2.  Based on the count of regular Ad Impressions received in current
        bucket + previous `x(1)` buckets, if the total sum exceeds the
        threshold `t(1)`, then stamp a cookie with `isRegUser=true`.
        Else, stamp a cookie with `isRegUser=false` for next `d(3)`
        days.

    3.  `d` days = number of days the user is evaluated for as a
        thin/regular user.

    4.  As per dated(02-05-2022), if `regAdCount` of `currentBucket` is
        1, then the user is considered as `isRegUser=true`.

3.  Log the reason for showing evergreen ads.

    1.  Post Body details

        1.  isRegularUser : Boolean regAdTimeout : Long isFirstAd :
            Boolean

    2.  Logging details for the above.

        1.  { \"isRegularUserClient\":\"1\", \"regAdTimeout\":\"3600\",
            \"isFirstAd\": \"1\" }

json{ \"regAdCount\":{ \"20\":{ \"ct\":4, \"mod\":1652795628 } } }

[Example case
walkthrough.](https://docs.google.com/spreadsheets/d/10KQ-idbeglRfHoD-oeC8dflX24ErjWpO_EPDgl9m2wM/edit#gid=531625501)

### Ad Request

1.  On Request Url (fallback url),

    1.  Introduce decryption of parameters (gaid,lat\...) and implement
        OI number generator.

    2.  Using `request_timestamp` , log the `req_time` if it empty.

    3.  Log the `evergreen = 1` into Kudu pipeline derived from `eg=1`
        param in the URL.

    4.  `"request_timestamp": "1650351578",req_time":"19042022 12:29:38", "Gpscountry":"india","evergreen":"1`
        will be logged at fallback call and `"isRegUser":"1"` will be
        logged for request call \[index.php\]

# Client Server Protocol

## Ads Handshake

### Request

Same as the usual Ads Handshake.

### Response Params

+---------------------------------------------------+--------------+-----------------+-------------------+
| **Parameter Name**                                | **Datatype** | **Default       | **Description**   |
|                                                   |              | Value**         |                   |
+---------------------------------------------------+--------------+-----------------+-------------------+
| `enabled`                                         | boolean      | false           | Global flag to    |
|                                                   |              |                 | enable the        |
|                                                   |              |                 | evergreen         |
|                                                   |              |                 | workflow or not.  |
+---------------------------------------------------+--------------+-----------------+-------------------+
| `endpoint`                                        | string       |                 | API endpoint to   |
|                                                   |              |                 | request evergreen |
|                                                   |              |                 | Ads.              |
+---------------------------------------------------+--------------+-----------------+-------------------+
| `apiFetchDelay`                                   | integer      | 3600            | Number of seconds |
|                                                   |              |                 | to wait for the   |
|                                                   |              |                 | next evergreen ad |
|                                                   |              |                 | request.          |
+---------------------------------------------------+--------------+-----------------+-------------------+
| `substituteTimeout`                               | object       | N/A             | Object containing |
|                                                   |              |                 | timeout           |
|                                                   |              |                 | information to    |
|                                                   |              |                 | render the        |
|                                                   |              |                 | evergreen Ads by  |
|                                                   |              |                 | discarding the    |
|                                                   |              |                 | regular Ad        |
|                                                   |              |                 | request.          |
|                                                   |              |                 |                   |
|                                                   |              |                 | timeout=0 → show  |
|                                                   |              |                 | only evergreen    |
|                                                   |              |                 | ads               |
|                                                   |              |                 |                   |
|                                                   |              |                 | timeout=null -\>  |
|                                                   |              |                 | show only regular |
|                                                   |              |                 | ads               |
|                                                   |              |                 |                   |
|                                                   |              |                 | timeout=\<Greater |
|                                                   |              |                 | than zero\> →     |
|                                                   |              |                 | Wait till timeout |
|                                                   |              |                 | to show regular   |
|                                                   |              |                 | ad else show      |
|                                                   |              |                 | evergreen ad      |
|                                                   |              |                 |                   |
|                                                   |              |                 | timeout is absent |
|                                                   |              |                 | → use client      |
|                                                   |              |                 | hardcoded default |
|                                                   |              |                 | value             |
+---------------------------------------------------+--------------+-----------------+-------------------+
| `substituteTimeout.regularUser`                   | object       | N/A             | Object containing |
|                                                   |              |                 | the timeout       |
|                                                   |              |                 | information for   |
|                                                   |              |                 | regular users.    |
+---------------------------------------------------+--------------+-----------------+-------------------+
| `substituteTimeout.regularUser.firstImpressionMS` | integer      | 500             | Timeout in        |
|                                                   |              |                 | milliseconds for  |
|                                                   |              |                 | the first         |
|                                                   |              |                 | impression of a   |
|                                                   |              |                 | regular user.     |
+---------------------------------------------------+--------------+-----------------+-------------------+
| `substituteTimeout.regularUser.impressionMS`      | integer      | 1500            | Timeout in        |
|                                                   |              |                 | milliseconds for  |
|                                                   |              |                 | the non-first     |
|                                                   |              |                 | impressions of a  |
|                                                   |              |                 | regular user.     |
+---------------------------------------------------+--------------+-----------------+-------------------+
| `substituteTimeout.thinUser`                      | object       | N/A             | Object containing |
|                                                   |              |                 | the timeout       |
|                                                   |              |                 | information for   |
|                                                   |              |                 | thin users.       |
+---------------------------------------------------+--------------+-----------------+-------------------+
| `substituteTimeout.thinUser.firstImpressionMS`    | integer      | 0               | Timeout in        |
|                                                   |              |                 | milliseconds for  |
|                                                   |              |                 | the first         |
|                                                   |              |                 | impression of a   |
|                                                   |              |                 | thin user.        |
+---------------------------------------------------+--------------+-----------------+-------------------+
| `substituteTimeout.thinUser.impressionMS`         | integer      | 500             | Timeout in        |
|                                                   |              |                 | milliseconds for  |
|                                                   |              |                 | the non-first     |
|                                                   |              |                 | impressions of a  |
|                                                   |              |                 | thin user.        |
+---------------------------------------------------+--------------+-----------------+-------------------+
| `noOfAdsToProcess`                                | integer      | 3               | Number of         |
|                                                   |              |                 | evergreen Ads to  |
|                                                   |              |                 | process at once.  |
+---------------------------------------------------+--------------+-----------------+-------------------+
| `retryOnFailureAfterTimeInSec`                    | integer      | 10              | Number of seconds |
|                                                   |              |                 | to wait for       |
|                                                   |              |                 | triggering next   |
|                                                   |              |                 | evergreen ad      |
|                                                   |              |                 | request on        |
|                                                   |              |                 | failure.          |
+---------------------------------------------------+--------------+-----------------+-------------------+

### Sample Response

json{ \"evergreenAds\": { \"enabled\": true, \"endpoint\":
\"http://money.dailyhunt.in/getEgAds?countryCode=\--CL_COUNTRY_CODE\--\",
\"apiFetchDelay\": 3600, \"substituteTimeout\": { \"regularUser\": {
\"firstImpressionMS\": 500, \"impressionMS\": 1500 }, \"thinUser\": {
\"firstImpressionMS\": 0, \"impressionMS\": 500 } },
\"noOfAdsToProcess\": 3, \"isRegUser\": false,
\"retryOnFailureAfterTimeInSec\": 10 } }

## Evergreen Ads

### Request

`GET http://money.dailyhunt.in/getEgAds?countryCode=--CL_COUNTRY_CODE--`

Send all query parameters which we are sending in regular ads as it is.

### Response

json{ \"ads\": \[ { \"type\": \"imgLink\", \"width\": 1080, \"height\":
1080, \"id\": \"\--CL_UUID\--\", \"startepoch\": 169832493240,
\"endepoch\": 169832493290, \"useInternalBrowser\": \"true\",
\"allowDelayedAdInsert\": true, \"adTagPosition\": \"TOP_RIGHT\",
\"showBorder\": true, \"campaignId\": \"98400\", \"bannerId\":
\"416195\", \"isLargeAd\": true, \"adGroupId\":
\"3826976626a3aa6c14fa2.59496681\", \"supportedZones\": { \"card-p0\": {
\"DEFAULT\": { \"priority\": 0.78, \"weight\": 9, \"card-position\": 2,
\"positionWithTicker\": 4 } }, \"card-p1\": { \"DEFAULT\": {
\"priority\": 0.32, \"weight\": 2, \"card-position\": 4,
\"positionWithTicker\": 4, \"min-ad-distance\": 4, \"largeAdDistance\":
8 } }, \"storypage\": { \"DEFAULT\": { \"priority\": 0.32, \"weight\": 2
} }, \"supplement\": { \"sp1\": { \"priority\": 0.32, \"weight\": 2 },
\"sp3\": { \"priority\": 0.15, \"weight\": 2 }, \"sp4\": { \"priority\":
0.04, \"weight\": 1 } } }, \"content\": { \"imgLink\":
\"http://acdn.newshuntads.com/daedalus-banners/416195/1649678666_42317_600x600.jpg\",
\"itemSubtitle2\": { \"color\": \"#4caf79\", \"color-night\":
\"#ffffff\", \"data\": \"Know More\" }, \"reportText\": { \"color\":
\"#798DED\", \"color-night\": \"#FFFFFF\", \"background-color\":
\"#40000000\", \"background-color-night\": \"#40000000\", \"data\":
\"Ad\" } }, \"errorUrl\":
\"http://money.dailyhunt.in/beaconEvents?uniqueId=121c832075f65fa2bff429b69c64c3e3&adId=416195&campaignId=98400&adPlacement=storypage&partnerRef=&city=&state=&country=india&clientId=123456788&reqTime=1650446972&eventType=AD_ERROR&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"action\":
\"https://money.dailyhunt.in/click?clientId=123456788&uniqueId=121c832075f65fa2bff429b69c64c3e3&adId=416195&campaignId=98400&adPlacement=storypage&reqTime=1650446972&billingTypeId=3&orderId=57644&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=&\_\_oadest=https%3A%2F%2Fwidgets.dailyhunt.in%2Fstatic_ads%2Froyalenfield%2Fcanvas_lp%2Fscram_canvas%2Findex.html\",
\"adFeedback\": { \"feedbackUrl\":
\"http://money.dailyhunt.in/data-api/adfeedback?bannerId=416195&campaignId=98400&uniqueId=121c832075f65fa2bff429b69c64c3e3&city=\"
}, \"shareability\": null, \"impFcap\": { \"cap\": \"4\", \"resetTime\":
\"2591940\" }, \"bImpFcap\": { \"cap\": \"2\", \"resetTime\": \"3600\"
}, \"beaconUrl\":
\"http://qa-money.newshunt.com/impression?uniqueId=\--CL_UUID\--&adId=416196&campaignId=98400&adPlacement=\--CL_AD_PLACEMENT\--&partnerRef=&city=&state=&country=\--CL_COUNTRY\--&clientId=\--CL_CLIENT_ID\--&reqTime=1650446972&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"beaconUrlAdditional\": \[ \"http://www.google.com\" \],
\"landingUrlAdditional\": \[ \"http://www.google.com\" \],
\"requestUrl\":
\"http://qa-money.newshunt.com/fallback?clientid=\--CL_CLIENT_ID\--&req_time=20042022+14%3A59%3A32&paper=&item_category=&Gpscountry=\--CL_COUNTRY\--&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=none&user_handset_model=none&user_id=&placement=storypage&user_app_ver=18.6&banner_rotation_type=0&bookedPlacement=storypage&banner_id=416196&campaign_id=98400&user_connection=w&connection_speed=&user_os_ver=11.0&gaid=&item_publisher_language=&user_languages=en%2C&oi=1043&price_range=none&user_device_type=none&title=RE_Canvas+Innovation&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=\--CL_UUID\--&region=&mcc=&mnc=&lac=&cellid=S3vXDSAFEuQOEKNFLqX5DQ%3D%3D&ip=10.52.134.5&adGroupId=123456788625fd27ca4d9e7.95465490&topicId=57668&topicName=&ecpm=175&audienceSegments=none&resolution=1080x2257&hostalias=dh-gcp-ads-adengine-ws-az-wp03&locationSource=&pincode=&subSlot=&bookedSubSlot=&ab=ECPM_ZONE&partnerId=DH_APP&deliverySlab=0.12&userDeliverySlab=0&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=634.69970703125&utmSource=&utmMedium=&utmCampaign=&appId=&autoPlayPref=2&installDeliverySlab=&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=1&topCampaignIds=51304%5E98400%5E99687%5E94104%5E99786%5E99795%5E99418%5E99688%5E99318%5E99430%5E&topCampaignECPMs=0%5E634.69970703125%5E137.92121887207%5E135.20780944824%5E124.71224212646%5E87.632217407227%5E59.478736877441%5E55.854694366455%5E53.489944458008%5E39.430023193359&entityId=&entityType=&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=&campaignPrdictedCtr=3.6268553733826&productIds=&recoPolicy=&request_timestamp=1650446972&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=0&variantName=&modelUuid=&networkSwitch=NONE&topDirectCampaign=98400&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=0&campaign_type=STANDARD&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=&requestIdDebug=67cdd6e275c41f91fbee22f7cf7eccb7&gender=&age=&ageRange=&orderTypeV2=0&idfa=&s2sBidId=&imputationType=&contentCreatorId=&scoringModel=&filteringModel=&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&reqTime=1650446972&\",
\"adInflatedBeaconUrl\":
\"http://qa-money.newshunt.com/beaconEvents?uniqueId=\--CL_UUID\--&adId=416196&campaignId=98400&adPlacement=\--CL_AD_PLACEMENT\--&partnerRef=&city=&state=&country=\--CL_COUNTRY\--&clientId=\--CL_CLIENT_ID\--&reqTime=1650446972&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adLPTimeSpentBeaconUrl\":
\"http://qa-money.newshunt.com/beaconEvents?uniqueId=\--CL_UUID\--&adId=416196&campaignId=98400&adPlacement=\--CL_AD_PLACEMENT\--&partnerRef=&city=&state=&country=\--CL_COUNTRY\--&clientId=\--CL_CLIENT_ID\--&reqTime=1650446972&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\"
} \], \"version\": \"234987984764876132\" }

### Macro Definition

+----------------------------+----------------+-----------------+--------------------------------------+
| **Macro Name**             | **Macro        | **Description** | **Example**                          |
|                            | Value**        |                 |                                      |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_CLIENT_ID\--         | Client Id      |                 | c.U3BKTnpYTVpOSlFOUkFQWENWU3pJdz09A, |
|                            |                |                 | 4399994                              |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_UUID\--              | Unique Id      | Client          |                                      |
|                            |                | generated       |                                      |
|                            |                | unique Id       |                                      |
|                            |                | replaced before |                                      |
|                            |                | rendering       |                                      |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_AD_PLACEMENT\--      | Zone /         |                 | card-p0, card-p1,etc                 |
|                            | Placement      |                 |                                      |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_COUNTRY_CODE\--      | Country code   | Upper Case      | IN                                   |
|                            |                | value.\         |                                      |
|                            |                | Default value   |                                      |
|                            |                | will be empty   |                                      |
|                            |                | string(failure  |                                      |
|                            |                | in telephony    |                                      |
|                            |                | api).           |                                      |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_TIMESTAMP\--         | Current        | Unix Timestamp  | 1650446972                           |
|                            | Timestamp      |                 |                                      |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_SUB_SLOT\--          | Subslot        | Subslot of the  | sp1, pp_1                            |
|                            |                | Zone            |                                      |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_USER_OS\--           | Operating      |                 | android, ios                         |
|                            | system         |                 |                                      |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_APP_VERSION\--       | DH app version |                 | 18.8.0                               |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_USER_OS_VERSION\--   | User OS        |                 | 12.0                                 |
|                            | version        |                 |                                      |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_LATITUDE\--          | Encrypted      |                 |                                      |
|                            | latitude       |                 |                                      |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_LONGITUDE\--         | Encrypted      |                 |                                      |
|                            | longitude      |                 |                                      |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_CELL_ID\--           | Encrypted cell |                 |                                      |
|                            | id             |                 |                                      |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_UDID\--              | Encrypted udid |                 |                                      |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_DEVICE_RESOLUTION\-- | Device         |                 | 1080x2257                            |
|                            | Resolution     |                 |                                      |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_ENTITY_ID\--         | Entity Id      |                 | 91581308b67fdfbcd24028a0c513bc37     |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_ENTITY_TYPE\--       | Entity Type    |                 | HASHTAG                              |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_SUB_ENTITY_TYPE\--   | Entity Sub     |                 | L_NP                                 |
|                            | Type           |                 |                                      |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_SOURCE_TYPE\--       | Source Type    |                 | OGC                                  |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_USER_CONNECTION\--   | User           |                 | w,4g,3g                              |
|                            | connection     |                 |                                      |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_CONNECTION_SPEED\--  | Connection     |                 | GOOD                                 |
|                            | Speed          |                 |                                      |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_ADVERTISING_ID\--    | Encrypted      |                 |                                      |
|                            | GAID/IDFA      |                 |                                      |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_USER_LANGUAGE\--     | User selected  | Comma separated | en,ka                                |
|                            | languages      | list of         |                                      |
|                            |                | language        |                                      |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_ISP\--               | Internet       |                 | jio,airtel                           |
|                            | Service        |                 |                                      |
|                            | Provider       |                 |                                      |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_SOURCE_ID\--         | Source Id      |                 | dha713b67ac5fe4ee2a54e736722dcd237   |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_SOURCE_CAT_ID\--     | Source Cat Id  |                 | dhd3d10171847d4a028a33479b8e804bca   |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_DENSITY\--           | Density        |                 | 3.0                                  |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_POST_ID\--           | post id        | In case of      | n52706136                            |
|                            |                | story detail    |                                      |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_PAGE_REFERRER\--     | page referrer  |                 | STORY_DETAIL                         |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_REFERRER_ID\--       | referrer id    |                 | n52706136                            |
+----------------------------+----------------+-----------------+--------------------------------------+
| \--CL_AUTO_PLAY_PREF\--    | auto play      |                 | 3                                    |
|                            | preference     |                 |                                      |
+----------------------------+----------------+-----------------+--------------------------------------+

### Mock

[Mock link](https://qa-money.newshunt.com/evergreen_ads_mock.json)

note

## **Points to remember**

1.  Evergreen Ads supported app versions -

    1.  Android - v18.7.13 onwards.

    2.  IOS - Not Supported.

2.  Evergreen ads are supported only on these zones -
    `CARD_P0, CARD_P1, STORYPAGE, PGI, SPLASH, CARD_PP1, SUPPLEMENT`.

    1.  Evergreen Ads are not supported on `splash-default` zone.

3.  In addition to Frequency Cap, below targeting are supported -

    1.  Language

    2.  Geo (Country and State)

    3.  Operating System

4.  **Hub exclusivity** (exclusive, blocked, onam, etc) does not apply
    on Evergreen Ads.

5.  Evergreen Ads will be rendered for **new users** based on Evergreen
    Ads threshold timeouts.

6.  Evergreen Ads will not be blocked by BE based on the **user
    feedback**.

7.  **Network Ads**, both S2S and SDK, are not supported for Evergreen
    Ads.

8.  Evergreen Ads do not support **Ad Load** config.

9.  **Performance optimisation** is not possible for the Evergreen Ads.

10. **Pacing** is not possible for the Evergreen Ads.

11. Both the Thin Users and the Regular Users will see the **Regular Ad
    Impression** if the Regular Ad gets processed before the threshold
    timeout.

12. Both the Thin Users and the Regular Users will see the **Evergreen
    Ad Impression** if the Regular Ad fails to be processed before the
    threshold timeout.

13. It is possible that the Evergreen Ad Impression be an **Empty Ad**.
    This happens when the Regular Ad fails to be processed before the
    threshold timeout and also there are no Evergreen Ads targeted.

14. Evergreen Ads Timeout as of 28 Jun 2022.

    1.  Regular User

        1.  First impression of the day - 500 ms

        2.  Subsequent impressions of the day - 3500 ms

    2.  Thin User

        1.  First impression of the day - 0 ms

        2.  Subsequent impressions of the day - 500 ms

:::: {.panel .conf-macro .output-block style="background-color: rgb(234,230,255);border-color: rgb(153,141,217);border-width: 1.0px;"}
::: {.panelContent style="background-color: rgb(234,230,255);"}
## **Points to remember**

1.  Evergreen Ads supported app versions -

    1.  Android - v18.7.13 onwards.

    2.  IOS - Not Supported.

2.  Evergreen ads are supported only on these zones -
    `CARD_P0, CARD_P1, STORYPAGE, PGI, SPLASH, CARD_PP1, SUPPLEMENT`.

    1.  Evergreen Ads are not supported on `splash-default` zone.

3.  In addition to Frequency Cap, below targeting are supported -

    1.  Language

    2.  Geo (Country and State)

    3.  Operating System

4.  **Hub exclusivity** (exclusive, blocked, onam, etc) does not apply
    on Evergreen Ads.

5.  Evergreen Ads will be rendered for **new users** based on Evergreen
    Ads threshold timeouts.

6.  Evergreen Ads will not be blocked by BE based on the **user
    feedback**.

7.  **Network Ads**, both S2S and SDK, are not supported for Evergreen
    Ads.

8.  Evergreen Ads do not support **Ad Load** config.

9.  **Performance optimisation** is not possible for the Evergreen Ads.

10. **Pacing** is not possible for the Evergreen Ads.

11. Both the Thin Users and the Regular Users will see the **Regular Ad
    Impression** if the Regular Ad gets processed before the threshold
    timeout.

12. Both the Thin Users and the Regular Users will see the **Evergreen
    Ad Impression** if the Regular Ad fails to be processed before the
    threshold timeout.

13. It is possible that the Evergreen Ad Impression be an **Empty Ad**.
    This happens when the Regular Ad fails to be processed before the
    threshold timeout and also there are no Evergreen Ads targeted.

14. Evergreen Ads Timeout as of 28 Jun 2022.

    1.  Regular User

        1.  First impression of the day - 500 ms

        2.  Subsequent impressions of the day - 3500 ms

    2.  Thin User

        1.  First impression of the day - 0 ms

        2.  Subsequent impressions of the day - 500 ms
:::
::::
