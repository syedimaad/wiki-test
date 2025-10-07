17

# Figma link

https://www.figma.com/file/i4IPWk7xd7I3UPxW9GgfJ5/Ads?node-id=1%3A58#261570783

# Request Protocol

## Base Url

The base URL of the Ads API endpoints will be provided in the ads
Handshake's response. The public vibe app is expected to use this base
URL to construct the Ads Handshake and the Ad Request URLs throughout
the session.

HandShake's Properties For base url: **advertisementUrl**

## Ad Request Protocol

The public vibe app needs to construct ad request url by appending below
params to base URL.

+-----------------+----------------+-----------------+------------------------------------------+
| **Paramater**   | **Paramater    | **Description** | **Expected Value**                       |
|                 | Type**         |                 |                                          |
+-----------------+----------------+-----------------+------------------------------------------+
| zone            | GET            | Ad placement    | home-pgi, shorts-pgi, full-card          |
|                 |                | where ad        |                                          |
|                 |                | request is made |                                          |
+-----------------+----------------+-----------------+------------------------------------------+
| client          | GET            | client OS of    | android, ios                             |
|                 |                | the user.       |                                          |
+-----------------+----------------+-----------------+------------------------------------------+
| resolution      | GET            | screen          | \<widthxheight\>                         |
|                 |                | resolution of   |                                          |
|                 |                | the phone.      | 1080x1920                                |
+-----------------+----------------+-----------------+------------------------------------------+
| clientId        | GET            | PublicVibe app  |                                          |
|                 |                | specific        |                                          |
|                 |                | clientId        |                                          |
+-----------------+----------------+-----------------+------------------------------------------+
| userId          | GET            | PublicVibe app  |                                          |
|                 |                | specific userId |                                          |
+-----------------+----------------+-----------------+------------------------------------------+
| appVer          | GET            | PublicVibe app  | 10.0.2                                   |
|                 |                | specific app    |                                          |
|                 |                | version         |                                          |
+-----------------+----------------+-----------------+------------------------------------------+
| osVersion       | GET            | User phone's os | 10.0.1                                   |
|                 |                | version         |                                          |
+-----------------+----------------+-----------------+------------------------------------------+
| long            | GET            | longitude of    | 77.5946                                  |
|                 |                | the user. This  |                                          |
|                 |                | is encrypted    |                                          |
|                 |                | value.          |                                          |
+-----------------+----------------+-----------------+------------------------------------------+
| lat             | GET            | latitude of the | 12.9716                                  |
|                 |                | user. This is   |                                          |
|                 |                | encrypted       |                                          |
|                 |                | value.          |                                          |
+-----------------+----------------+-----------------+------------------------------------------+
| cellid          | GET            | This is         | \<CellId-LCC-LAC-MNC\-\-\--NetworkType\> |
|                 |                | compound        |                                          |
|                 |                | paramater       |                                          |
|                 |                | consist of      |                                          |
|                 |                | current         |                                          |
|                 |                | location        |                                          |
|                 |                | information     |                                          |
|                 |                | from sim card   |                                          |
|                 |                | connection      |                                          |
|                 |                | information.    |                                          |
|                 |                | This is         |                                          |
|                 |                | encrypted       |                                          |
|                 |                | value.          |                                          |
+-----------------+----------------+-----------------+------------------------------------------+
| lang            | GET            | PublicVibe      | en,gu                                    |
|                 |                | specific        |                                          |
|                 |                | language. If    |                                          |
|                 |                | user selected   |                                          |
|                 |                | more than one   |                                          |
|                 |                | lang then       |                                          |
|                 |                | passes as a     |                                          |
|                 |                | comma seperated |                                          |
+-----------------+----------------+-----------------+------------------------------------------+
| conn            | GET            | client data     | 2G, 3G, 4G, 5G, W                        |
|                 |                | connection      |                                          |
+-----------------+----------------+-----------------+------------------------------------------+
| connectionSpeed | GET            | ENUM string to  | FAST, AVERAGE, SLOW                      |
|                 |                | represent       |                                          |
|                 |                | connection      |                                          |
|                 |                | speed of user.  |                                          |
+-----------------+----------------+-----------------+------------------------------------------+
| gaid            | GET            | user's google   | 7366face-d6fb-4b28-94d3-147b8141f814     |
|                 |                | advertiser Id   |                                          |
|                 |                | value. This is  |                                          |
|                 |                | encrypted       |                                          |
|                 |                | value.          |                                          |
+-----------------+----------------+-----------------+------------------------------------------+
| density         | GET            | screen display  | 2                                        |
|                 |                | density of      |                                          |
|                 |                | device.         |                                          |
+-----------------+----------------+-----------------+------------------------------------------+
| udid            | GET            | Unique          | B0EBCBF7-AC09-469B-8EBA-1E2EAFFBF59A     |
|                 |                | Identification  |                                          |
|                 |                | of the device.  |                                          |
+-----------------+----------------+-----------------+------------------------------------------+
| fbBidderToken   | POST           | token generated | FB Bidder Token                          |
|                 |                | at client       |                                          |
+-----------------+----------------+-----------------+------------------------------------------+
| feedStateId     | GET            | user selected   | INT                                      |
|                 |                | State           |                                          |
+-----------------+----------------+-----------------+------------------------------------------+
| feedDistrictId  | GET            | user selected   | INT                                      |
|                 |                | District        |                                          |
+-----------------+----------------+-----------------+------------------------------------------+
| feedTalukId     | GET            | user selected   | INT                                      |
|                 |                | Constituency    |                                          |
+-----------------+----------------+-----------------+------------------------------------------+
| feedLat         | GET            | Lat based on    | String                                   |
|                 |                | user selected   |                                          |
|                 |                | feed-location   |                                          |
+-----------------+----------------+-----------------+------------------------------------------+
| feedLong        | GET            | Long based on   | String                                   |
|                 |                | user selected   |                                          |
|                 |                | feed-location   |                                          |
+-----------------+----------------+-----------------+------------------------------------------+

## How to encrypt sensitive params ?

We're supporting double encryption combination of AES ( AES-128-CBC ) +
RSA.

In Handshake, we're sending RSA public key ( encryption.key ).

Following steps for double encryption:

1.  Client need to generate AES-128-CBC secrete key.

2.  Using AES-128-CBC secrete key, client needs to encrypt actual plain
    text.

3.  Using RSA public key which we're sending in handshake, Client need
    to encrypt AES-128-CBC secrete key.

4.  Client need to pass data into below format.

    1.  \<AES-128-CBC encrypted plain text\>\|\<RSA public key encrypted
        AES-128-CBC's secrete key\>\|RSA public key version ( from
        handshake )

5.  Below params need to encrypted.

    1.  gaid, lat, long, udid, cellid

# [Sample KUDU/SQL Json](https://docs.google.com/document/d/1fjmebyIfnlOL_TR6VmKZLyhoYZ0s2E5MVOMUKzzmzFg/edit#)

# Iteration-1 Mock Responses

## Hanshake

[Handshake Mock
API](http://qa-money.newshunt.com/publicVibe/v1/pvHandshake.json)

Sample Responsejson{ \"code\": 200, \"data\": { \"version\":
\"dc43ff2f9eb29bd46e57d89772331a18\", \"mobvista\": { \"enabled\":
false, \"adUnitId\": \"3983\", \"titleLogoImageUrl\": \"\",
\"titleImageUrl\": \"\", \"titleBackgroundColor\": \"\",
\"mainScreenBackgroundColor\": \"\", \"tabsBackgroundColor\": \"\",
\"tabsIndicatorLineColor\": \"\", \"installButtonBackgroundImageUrl\":
\"\", \"loadingProgressBarImageUrl\": \"\",
\"newTipRedisplayIntervalInSeconds\": 3600 }, \"deals-appwall\": {
\"enabled\": false }, \"buzzAd\": { \"freezeUserOperation\": \"TRUE\",
\"skipText\": \"Skip Ad\", \"skipNow\": \"You can skip ad now\",
\"skipInSec\": \"You can skip ad in %d sec\", \"ad-distance\": \"3\",
\"maxBitrateKbpsGood\": \"795\", \"maxBitrateKbpsAverage\": \"725\",
\"maxBitrateKbpsSlow\": \"465\" }, \"dhtv\": { \"adDistanceMs\":
\"180000\", \"ignoreVideoDuration\": \"480000\" }, \"card-p0\": {
\"adBlock\": { \"topicIds\": \[ \"2049\",
\"0b55aa0e72d61e4f9c299b71b4a526b4\", \"2098\",
\"9c1cdd3a2755ae52e1b221a97e53930d\" \], \"npKey\": \[ \"spon\",
\"dheea83bdde2f04ee495a2e6baab4306d7\", \"bajaj\" \], \"npCatKey\": \[ {
\"npKey\": \"kalyanen\", \"cat\": \"sanskriti\" }, { \"npKey\":
\"dh06bce753323e4544964216fbbd954e98\", \"cat\":
\"dh8002df0686bc47e4a7df585c34fb58e3\" } \] }, \"cacheFlush\": {
\"topicIds\": \[ \"2049\", \"0b55aa0e72d61e4f9c299b71b4a526b4\",
\"2098\", \"9c1cdd3a2755ae52e1b221a97e53930d\" \], \"npKey\": \[
\"spon\", \"dheea83bdde2f04ee495a2e6baab4306d7\", \"bajaj\" \],
\"npCatKey\": \[ { \"npKey\": \"fifawrld\", \"cat\":
\"magicalcelebrations\" } \] }, \"cacheTTL\": \"300\",
\"enablePrefetch\": \"TRUE\" }, \"card-p1\": { \"adBlock\": {
\"topicIds\": \[ \"2049\", \"0b55aa0e72d61e4f9c299b71b4a526b4\",
\"2098\", \"9c1cdd3a2755ae52e1b221a97e53930d\" \], \"npKey\": \[
\"spon\", \"dheea83bdde2f04ee495a2e6baab4306d7\", \"bajaj\" \],
\"npCatKey\": \[ { \"npKey\": \"kalyanen\", \"cat\": \"sanskriti\" }, {
\"npKey\": \"dh06bce753323e4544964216fbbd954e98\", \"cat\":
\"dh8002df0686bc47e4a7df585c34fb58e3\" } \] }, \"cacheFlush\": {
\"topicIds\": \[ \"2049\", \"0b55aa0e72d61e4f9c299b71b4a526b4\",
\"2098\", \"9c1cdd3a2755ae52e1b221a97e53930d\" \], \"npKey\": \[
\"spon\", \"dheea83bdde2f04ee495a2e6baab4306d7\", \"bajaj\" \],
\"npCatKey\": \[ { \"npKey\": \"fifawrld\", \"cat\":
\"magicalcelebrations\" } \] } }, \"instream-vdo\": {
\"vdoNoAdReqMinLength\": \"0\", \"minAdWaitForContent\": \"3000\",
\"adRequestForLiveVideos\": true, \"companion\": { \"expandHeading\":
\"Ad Expand\", \"collapseHeading\": \"Ad Collapse\",
\"videoAspectRatioLimit\": \"1.33\", \"showAfterVideoAd\": \"2\" } },
\"storypage\": { \"adBlock\": { \"topicIds\": \[ \"2049\",
\"0b55aa0e72d61e4f9c299b71b4a526b4\", \"2098\",
\"9c1cdd3a2755ae52e1b221a97e53930d\" \], \"npKey\": \[ \"spon\",
\"dheea83bdde2f04ee495a2e6baab4306d7\", \"bajaj\" \], \"npCatKey\": \[ {
\"npKey\": \"kalyanen\", \"cat\": \"sanskriti\" }, { \"npKey\":
\"dh06bce753323e4544964216fbbd954e98\", \"cat\":
\"dh8002df0686bc47e4a7df585c34fb58e3\" } \] }, \"cacheFlush\": {
\"topicIds\": \[ \"2049\", \"0b55aa0e72d61e4f9c299b71b4a526b4\",
\"2098\", \"9c1cdd3a2755ae52e1b221a97e53930d\" \], \"npKey\": \[
\"spon\", \"dheea83bdde2f04ee495a2e6baab4306d7\", \"bajaj\" \],
\"npCatKey\": \[ { \"npKey\": \"fifawrld\", \"cat\":
\"magicalcelebrations\" } \] }, \"position\": { \"relativePos\":
\"Above\", \"element\": \"Chunk1\" } }, \"pgi\": { \"adBlock\": {
\"topicIds\": \[ \"2049\", \"0b55aa0e72d61e4f9c299b71b4a526b4\",
\"2098\", \"9c1cdd3a2755ae52e1b221a97e53930d\" \], \"npKey\": \[
\"spon\", \"dheea83bdde2f04ee495a2e6baab4306d7\", \"bajaj\" \],
\"npCatKey\": \[ { \"npKey\": \"kalyanen\", \"cat\": \"sanskriti\" }, {
\"npKey\": \"dh06bce753323e4544964216fbbd954e98\", \"cat\":
\"dh8002df0686bc47e4a7df585c34fb58e3\" } \] }, \"cacheFlush\": {
\"topicIds\": \[ \"2049\", \"0b55aa0e72d61e4f9c299b71b4a526b4\",
\"2098\", \"9c1cdd3a2755ae52e1b221a97e53930d\" \], \"npKey\": \[
\"spon\", \"dheea83bdde2f04ee495a2e6baab4306d7\", \"bajaj\" \],
\"npCatKey\": \[ { \"npKey\": \"fifawrld\", \"cat\":
\"magicalcelebrations\" } \] }, \"requestSwipeCountGood\": \"1\",
\"requestSwipeCountAverage\": \"1\", \"requestSwipeCountSlow\": \"1\" },
\"supplement\": { \"adBlock\": { \"topicIds\": \[ \"2049\",
\"0b55aa0e72d61e4f9c299b71b4a526b4\", \"2098\",
\"9c1cdd3a2755ae52e1b221a97e53930d\" \], \"npKey\": \[ \"spon\",
\"dheea83bdde2f04ee495a2e6baab4306d7\", \"bajaj\" \], \"npCatKey\": \[ {
\"npKey\": \"kalyanen\", \"cat\": \"sanskriti\" }, { \"npKey\":
\"dh06bce753323e4544964216fbbd954e98\", \"cat\":
\"dh8002df0686bc47e4a7df585c34fb58e3\" } \] }, \"cacheFlush\": {
\"topicIds\": \[ \"54570\", \"39176\",
\"1d619f99235154f13052102bcb3fa552\",
\"320d5714d85fde31b133a63b125fc3f3\" \], \"npKey\": \[ \"53718\",
\"airtelb\", \"dh6af2bbfb49194c4d954a936a6df3c456\", \"btwinsdr\" \] },
\"useTaboolaWeb\": \"true\", \"useSupplementAds\": \"false\",
\"tagOrder\": \[ \"sp1\", \"sp2\", \"sp3\", \"sp4\", \"sp5\", \"sp6\",
\"sp7\", \"sp8\", \"sp9\" \] }, \"taboola\": { \"publisher\":
\"dailyhuntnewsappsdk\", \"mode\": \"thumbnails-a\", \"pageType\":
\"article\", \"placement\": \"App Below Article Thumbnails\",
\"sendPageUrl\": \"TRUE\" }, \"sdkTimeout\": { \"adsTimeoutGood\":
\"3\", \"adsTimeoutAverage\": \"6\", \"adsTimeoutSlow\": \"12\" },
\"videoAdFallback\": { \"action\":
\"http://m.dailyhunt.in/news/india/english/dailyhunt-topics-25662\",
\"actionText\": \"\", \"itemTag\": \"Promoted\", \"imageUrl\":
\"http://acdn.newshuntads.com/daedalus-banners/68257/1595844502_46023_990x505.jpg\",
\"verticalImageUrl\":
\"http://acdn.newshuntads.com/daedalus-banners/174094/1595846553_13742_600x600.jpg\",
\"beaconUrl\":
\"http://money.dailyhunt.in/impression?uniqueId=13578521521661365800&adId=68257&campaignId=55541&adPlacement=card-p1&cap=0&reset=0\",
\"landingUrl\":
\"http://money.dailyhunt.in/click?clientId=1357852152&uniqueId=13578521521661365800&adId=68257&campaignId=55541&adPlacement=card-p1&billingTypeId=4&forceTracker=&\_\_oadest=\"
}, \"masthead\": { \"adBlock\": { \"topicIds\": \[ \"2049\",
\"0b55aa0e72d61e4f9c299b71b4a526b4\", \"2098\",
\"9c1cdd3a2755ae52e1b221a97e53930d\" \], \"npKey\": \[ \"spon\",
\"dheea83bdde2f04ee495a2e6baab4306d7\", \"bajaj\" \], \"npCatKey\": \[ {
\"npKey\": \"dh52fca1d9357d4dc4a021a262d12181c9\", \"cat\":
\"dh5df41ae84e7b432c87a1cc34aa3a872c\" }, { \"npKey\": \"dhpromo\",
\"cat\": \"videoembed\" } \] }, \"cacheFlush\": { \"topicIds\": \[
\"2049\", \"0b55aa0e72d61e4f9c299b71b4a526b4\", \"2098\",
\"9c1cdd3a2755ae52e1b221a97e53930d\" \], \"npKey\": \[ \"spon\",
\"dheea83bdde2f04ee495a2e6baab4306d7\", \"bajaj\" \], \"npCatKey\": \[ {
\"npKey\": \"dh52fca1d9357d4dc4a021a262d12181c9\", \"cat\":
\"dh5df41ae84e7b432c87a1cc34aa3a872c\" }, { \"npKey\": \"dhpromo\",
\"cat\": \"videoembed\" } \] } }, \"selfService\": { \"ssUrl\":
\"http://direct.dailyhunt.in/ext/dailyhunt-self-serve-ads-platform-registration/index.html?cid=1357852152_DHSP&utm_source=DHSP&utm_medium=1357852152\",
\"ssEnabled\": \"TRUE\", \"useInternalBrowser\": \"FALSE\", \"ssTitle\":
\"Advertising\", \"useWideViewPort\": \"FALSE\",
\"clearHistoryOnPageLoad\": \"TRUE\" }, \"omSdkConfig\": { \"enabled\":
\"TRUE\", \"version\": \"1.3.0\", \"serviceJSUrl\":
\"http://money.dailyhunt.in/omSdk/dailyhunt/android/omsdk-v1.3.0.js\",
\"sessionClientJSUrl\":
\"http://money.dailyhunt.in/omSdk/dailyhunt/android/omid-session-client-v1.3.0.js\"
}, \"card-pp1\": { \"tagOrder\": \[ \"pp1_1\", \"pp1_c1\", \"pp1_c2\",
\"pp1_c3\", \"pp1_2\" \] }, \"immersiveView\": {
\"immersiveTransitionSpan\": \"3\", \"immersiveViewDistance\": \"2\" },
\"evergreenAds\": { \"enabled\": true, \"endpoint\":
\"https://eg.money.dailyhunt.in/getEgAds?countryCode=\--CL_COUNTRY_CODE\--\",
\"apiFetchDelay\": 3600, \"substituteTimeout\": { \"regularUser\": {
\"firstImpressionMS\": 500, \"impressionMS\": 3500 }, \"thinUser\": {
\"firstImpressionMS\": 0, \"impressionMS\": 500 } },
\"noOfAdsToProcess\": 3, \"retryOnFailureAfterTimeInSec\": 10,
\"isRegUser\": false }, \"splash-exit\": { \"enabled\": \"TRUE\" },
\"cardP0Refresh\": \"TRUE\", \"cardP1NoFillRetryDistance\": \"7\",
\"pgiNoFillRetrySwipeCount\": \"8\", \"deviceDataPostDelayMin\": \"30\",
\"deviceDataSampleSize\": \"1\", \"enableDataCollection\": \"TRUE\",
\"facebookPermissions\": \[ \"public_profile\", \"email\",
\"user_birthday\", \"user_gender\" \], \"externalBrowsers\": \[
\"com.android.chrome\", \"com.opera.mini.native\",
\"org.mozilla.firefox\" \], \"isPageLoadedBeaconNeeded\": \"FALSE\",
\"minVisibilityForAutoplay\": \"50\", \"adBorderColor\": \"#EAEAEA\",
\"viralStartAdPosition\": \"4\", \"viralMinAdDistance\": \"5\",
\"viralCardP1NoFillRetryDistance\": \"6\", \"enableOmidExperimentally\":
\"TRUE\", \"locationCredibilityPeriod\": \"2592000\",
\"buzzStartAdPosition\": \"3\", \"buzzMinAdDistance\": \"5\",
\"minAspectRatioNativeHighTemplate\": \"1.3\", \"minAspectRatioVideo\":
\"1.7\", \"sdkMinimumAutoplayPercent\": { \"dfp\": \"50\", \"fb\":
\"50\", \"appnext\": \"50\" }, \"iosVideoScriptFilePath\":
\"http://money.dailyhunt.in/ios/HTMLVideoAdScript.js\",
\"mastheadGapTimeMs\": \"6000\", \"enableFBBidding\": \"TRUE\",
\"deeplinkEnabledUrls\": \[ \"m.dailyhunt.in\",
\"profile.dailyhunt.in\", \"pwa.dailyhunt.in\", \"dhunt.in\",
\"bz.dhunt.in\", \"vh.dhunt.in\", \"shorturl.newshunt.in\",
\"stage-share.newshunt.in\" \], \"campaignSyncFgIntervalInMinutes\":
\"5\", \"campaignSyncBgIntervalInMinutes\": \"720\",
\"fetchCampaignDataUrl\":
\"http://money.dailyhunt.in/fetchCampaignData\", \"enableSoftCounter\":
\"TRUE\", \"zippedHtmlAdCacheCount\": \"15\",
\"adLpTimespentTimeoutMS\": \"300000\", \"aodCollection\": \"ENABLED\",
\"prefetchDurationAds\": \"10\", \"reportAdsMenu\": { \"url\":
\"https://money.dailyhunt.in/feedback.php\", \"title\": \"Advertisement
Feedback\", \"options\": \[ { \"id\":
\"SHOW_MORE_OF_SUCH_ADVERTISEMENTS\", \"labels\": { \"en\": \"Show more
of such advertisements\", \"hi\": \"ऐसे ही विज्ञापन अधिक दिखाएं\", \"ta\":
\"இதுபோன்ற விளம்பரங்களை அதிகமாக காட்டுங்கள்\", \"te\": \"ఇలాంటి ప్రకటనలు మరిన్ని
చూపించు\", \"ml\": \"ഇതുപോലുള്ള പരസ്യങ്ങള്‍ കൂടുതല്‍ കാണിക്കുക\", \"bn\": \"এই ধরনের
আরও বিজ্ঞাপন দেখান\", \"mr\": \"अशा प्रकारच्या अधिक जाहिराती दाखवा\",
\"kn\": \"ಇಂತಹ ಹೆಚ್ಚು ಜಾಹೀರಾತುಗಳನ್ನು ತೋರಿಸು\", \"gu\": \"આવી જાહેરાતો વધુ
દેખાડો\", \"pa\": \"ਅਜਿਹੇ ਇਸ਼ਤਿਹਾਰ ਜ਼ਿਆਦਾ ਦਿਖਾਓ\", \"or\": \"ଏପରି ବିଜ୍ଞାପନ ଅଧିକ
ଦେଖାନ୍ତୁ\", \"ur\": \"اس طرح کے زیادہ اشتہارات دکھائیں\", \"ar\": \"لرؤية
المزيد من الاعلانات المشابهة\" }, \"dataToSend\":
\"{\\\"selections\\\":{\\\"L1\\\":\\\"SHOW_MORE_OF_SUCH_ADVERTISEMENTS\\\"}}\",
\"iconUrl\":
\"http://assets-news-bcdn.dailyhunt.in/cmd/resize/#DH_EMB_IMG_REP#\_\_DHQ\_/fetchdata16/images/56/cb/6c/56cb6c5cb81f323cf4f4d30a33ba7594cc30f555925bc8cb6556cb88736ed89b.png\",
\"thankYouMessage\": { \"en\": \"Thank You\", \"hi\": \"धन्यवाद\",
\"ta\": \"நன்றி\", \"te\": \"ధన్యవాదాలు\", \"ml\": \"നന്ദി\", \"bn\":
\"ধন্যবাদ\", \"mr\": \"धन्यवाद\", \"kn\": \"ಧನ್ಯವಾದಗಳು\", \"gu\": \"આપનો
આભાર\", \"pa\": \"ਧੰਨਵਾਦ\", \"or\": \"ଆପଣଙ୍କୁ ଧନ୍ୟବାଦ\", \"ur\": \"شکریہ\",
\"ar\": \"شكراًً\" } }, { \"id\": \"SHOW_LESS_OF_SUCH_ADVERTISEMENTS\",
\"labels\": { \"en\": \"Show less of such advertisements\", \"hi\": \"ऐसे
विज्ञापन कम दिखाएं\", \"ta\": \"இதுபோன்ற விளம்பரங்களை குறைவாக காட்டுங்கள்\",
\"te\": \"ఇలాంటి ప్రకటనలు తక్కువగా చూపించు\", \"ml\": \"ഇതുപോലുള്ള പരസ്യങ്ങള്‍ കുറവ്
കാണിക്കുക\", \"bn\": \"এই দরনের বিজ্ঞাপন কম দেখান\", \"mr\": \"अशा प्रकारच्या
कमी जाहिराती दाखवा\", \"kn\": \"ಇಂತಹ ಕಡಿಮೆ ಜಾಹೀರಾತುಗಳನ್ನು ತೋರಿಸು\", \"gu\":
\"આવી જાહેરાતો ઓછી દેખાડો\", \"pa\": \"ਅਜਿਹੇ ਇਸ਼ਤਿਹਾਰ ਘੱਟ ਦਿਖਾਓ\", \"or\":
\"ଏପରି ବିଜ୍ଞାପନ କମ ଦେଖାନ୍ତୁ\", \"ur\": \"اس طرح کے کم اشتہارات دکھائیں\",
\"ar\": \"لرؤية اقل من الاعلانات المشابهة\" }, \"showWebForm\": true,
\"iconUrl\":
\"http://assets-news-bcdn.dailyhunt.in/cmd/resize/#DH_EMB_IMG_REP#\_\_DHQ\_/fetchdata16/images/0f/50/f5/0f50f56f7a6ffdaae9f21e95af14cd5345ec62f50e17557084d2384f86cbcf0d.png\"
}, { \"id\": \"REPORT_ADVERTISEMENTS\", \"labels\": { \"en\": \"Report
advertisements\", \"hi\": \"विज्ञापनों को रिपोर्ट करें\", \"ta\":
\"விளம்பரங்களை ரிப்போர்ட் செய்க\", \"te\": \"ప్రకటనలపై రిపోర్ట్ చేయి\", \"ml\":
\"പരസ്യങ്ങള്‍ റിപ്പോര്‍ട്ട് ചെയ്യുക.\", \"bn\": \"বিজ্ঞাপন নিয়ে রিপোর্ট করুন\",
\"mr\": \"जाहिराती रिपोर्ट करा\", \"kn\": \"ಜಾಹೀರಾತುಗಳನ್ನು ರಿಪೋರ್ಟ್ ಮಾಡಿ\",
\"gu\": \"જાહેરાતો રિપોર્ટ કરો\", \"pa\": \"ਇਸ਼ਤਿਹਾਰਾਂ ਦੀ ਰਿਪੋਰਟ ਕਰੋ\",
\"or\": \"ବିଜ୍ଞାପନ ବିଷୟରେ ରିପୋର୍ଟ କରନ୍ତୁ\", \"ur\": \"اشتہارات کی رپورٹ دیں\",
\"ar\": \"تبليغ عن اعلان\" }, \"showWebForm\": true, \"iconUrl\":
\"http://assets-news-bcdn.dailyhunt.in/cmd/resize/#DH_EMB_IMG_REP#\_\_DHQ\_/fetchdata16/images/6a/20/e2/6a20e2617932c31d54ccc3a01ae841a63c0e1951ba26af2f56d33769b248050e.png\"
}, { \"id\": \"REPORT_COPYRIGHT\", \"labels\": { \"en\": \"Report
Copyright\", \"hi\": \"कॉपीराइट को रिपोर्ट करें\", \"ta\": \"காப்பிரைட் பற்றி
ரிப்போர்ட் செய்க\", \"te\": \"కాపీరైట్‌పై రిపోర్ట్ చేయండి\", \"ml\": \"കോപ്പിറൈറ്റ്
റിപ്പോര്‍ട്ട് ചെയ്യുക\", \"bn\": \"কপিরাইট রিপোর্ট করুন\", \"mr\": \"कॉपीराइट
रिपोर्ट करा\", \"kn\": \"ಕಾಪಿರೈಟ್ ಅನ್ನು ರಿಪೋರ್ಟ್ ಮಾಡಿ\", \"gu\": \"કૉપીરાઈટ
રિપૉર્ટ કરો\", \"pa\": \"ਕਾਪੀਰਾਈਟ ਦੀ ਰਿਪੋਰਟ ਕਰੋ\", \"or\": \"କପିରାଇଟ୍ ରିପୋର୍ଟ
କରନ୍ତୁ\", \"ur\": \"کاپی رائٹ کو رپورٹ کریں\", \"ar\": \"تبليغ عن حقوق
النشر\" }, \"dataToSend\":
\"{\\\"selections\\\":{\\\"L1\\\":\\\"REPORT_COPYRIGHT\\\"},\\\"block\\\":true}\",
\"iconUrl\":
\"http://assets-news-bcdn.dailyhunt.in/cmd/resize/#DH_EMB_IMG_REP#\_\_DHQ\_/fetchdata16/images/51/45/79/514579f5b4966485f373498a28b84b98cae87a09acbaacc672881a38fbcbc91f.png\",
\"thankYouMessage\": { \"en\": \"Thanks for letting us know. Your
feedback helps us improve the quality of content on Dailyhunt\", \"hi\":
\"हमें बताने के लिए धन्यवाद। आपके सुझाव हमें डेलीहंट पर कॉन्टेंट की गुणवत्ता बेहतर बनाने में
मदद करते हैं।\", \"ta\": \"எங்களிடம் தெரிவித்ததற்கு நன்றி. உங்களின் கருத்துகள்,
டெய்லிஹன்ட்டில் கன்டென்ட்டுகளின் தரத்தை மேம்படுத்த, எங்களுக்கு உதவியாக இருக்கும்.\",
\"te\": \"మాకు తెలియజేసినందుకు ధన్యవాదాలు. డైలీహంట్‌లో కంటెంట్‌ యొక్క నాణ్యతను మెరుగుపరచేందుకు
మీ అభిప్రాయం మాకు సహాయపడతుంది.\", \"ml\": \"അറിയിച്ചതിന് നന്ദി. ഡെയിലി ഹണ്ടില്‍
കണ്ടെന്‍റ് മെച്ചപ്പെടുത്തുവാന്‍ നിങ്ങളുടെ പ്രതികരണം സഹായകമാകും\", \"bn\": \"আমাদের
জানানোর জন্য ধন্যবাদ। আপনার প্রতিক্রিয়া আমাদের প্রতিদিন ডেইলিহান্ট-এ কনটেন্টের
উন্নতি সাধনে সাহায্য করে।\", \"mr\": \"आम्हाला माहिती दिल्याबद्दल आभार. तुमच्या
अभिप्रायामुळे डेलिहंटवरील कंटेन्टचा दर्जा सुधारण्यासाठी आम्हाला मदत होते.\", \"kn\":
\"ನಮಗೆ ತಿಳಿಸಿದ್ದಕ್ಕಾಗಿ ಧನ್ಯವಾದಗಳು. ನಿಮ್ಮ ಪ್ರತಿಕ್ರಿಯೆಯು ಡೈಲಿಹಂಟ್‌ನಲ್ಲಿ ಕಂಟೆಂಟ್ ಗುಣಮಟ್ಟವನ್ನು
ಸುಧಾರಿಸಲು ನಮಗೆ ಸಹಾಯ ಮಾಡುತ್ತದೆ\", \"gu\": \"અમને જણાવવા બદ્દલ આભાર. તમારો
પ્રતિસાદ ડેઈલીહન્ટ પર કન્ટેન્ટની ગુણવત્તા સુધારવામાં અમારી મદદ કરે છે\", \"pa\":
\"ਸਾਨੂੰ ਜਾਣਕਾਰੀ ਦੇਣ ਲਈ ਧੰਨਵਾਦ। ਤੁਹਾਡਾ ਫੀਡਬੈਕ ਡੇਲੀਹੰਟ 'ਤੇ ਕਾਨਟੈਂਟ ਦੀ ਕਵਾਲਿਟੀ ਸੁਧਾਰਨ
ਵਿੱਚ ਸਾਡੀ ਮਦਦ ਕਰਦਾ ਹੈ।\", \"or\": \"ଆମକୁ ଜଣାଇବା ପାଇଁ ଧନ୍ୟବାଦ। ଡେଲିହଣ୍ଟରେ
କଣ୍ଟେଣ୍ଟର ଗୁଣାତ୍ମକ ମାନରେ ଉନ୍ନତି ଆଣିବା ପାଇଁ ଆପଣଙ୍କ ମତାମତ ସହାୟକ ହୋଇଥାଏ।\", \"ur\":
\"ہمیں اطلاع دینے کیلئے شکریہ۔ آپ کے تاثرات ڈیلی ہنٹ پر مواد کے معیار کو
بہتر بنانے میں ہماری مدد کرتے ہیں۔\", \"ar\": \"Dailyhunt شكراً لإعلامنا.
ان ملاحظتكم تساعدنا على تحسين جودة المحتوى على\" },
\"collapseOnSubmit\": true } \] }, \"encryption\": { \"key\":
\"LS0tLS1CRUdJTiBQVUJMSUMgS0VZLS0tLS0KTUlHZk1BMEdDU3FHU0liM0RRRUJBUVVBQTRHTkFEQ0JpUUtCZ1FDWkd2L1dncXo1OEhjOURMZUFObHRmNFVJMwp3Vkoyb0xJYzZEemRheFdaTXRSVkYzTGYySlFSZURQMTRsKzNYUGdXaC9lVlFBU1Z3QTZKaUYxemw1WXhJS1ovCmppc2NEaFRDS25idmE1dTdrYjFMb0FUTlFKQlZtZGhSOFVZbWc3dUZWMnJTVUg3UEJ3VytyLzhKcm9sOXA1SGEKckIxVlBPMEtIR0YyZ2JNS2V3SURBUUFCCi0tLS0tRU5EIFBVQkxJQyBLRVktLS0tLQo=\",
\"version\": \"1\" }, \"enableGzipCompression\": false,
\"enableErrorScreenShot\": true, \"errorCodes\": { \"NO_INTERNET\":
1001, \"AD_LOAD_TIMEOUT\": 1002, \"AD_LOAD_ERROR\": 1003,
\"AD_NO_VAST_TAG_URL\": 1004, \"MALFORMED_CLICK_URL\": 1005,
\"INSTREAM_NO_SKIP\": 1006, \"OUTSTREAM_SKIP\": 1007 }, \"amazonSDK\": {
\"banner\": { \"sizes\": \[ { \"width\": 300, \"height\": 250, \"data\":
\[ { \"adPosition\": \"card-p1\", \"slotInfo\": \[ { \"slotAdUnitId\":
\"4761d13f-d3b8-4b1a-9297-45cbf9f4899c\" } \] }, { \"adPosition\":
\"storypage\", \"slotInfo\": \[ { \"slotAdUnitId\":
\"4761d13f-d3b8-4b1a-9297-45cbf9f4899c\" } \] }, { \"adPosition\":
\"supplement\", \"slotInfo\": \[ { \"tag\": \"sp5\", \"slotAdUnitId\":
\"4761d13f-d3b8-4b1a-9297-45cbf9f4899c\" }, { \"tag\": \"sp6\",
\"slotAdUnitId\": \"4761d13f-d3b8-4b1a-9297-45cbf9f4899c\" }, { \"tag\":
\"sp7\", \"slotAdUnitId\": \"4761d13f-d3b8-4b1a-9297-45cbf9f4899c\" } \]
} \] } \] }, \"interstitial\": { \"sizes\": \[ { \"width\": 0,
\"height\": 0, \"data\": \[ { \"adPosition\": \"pgi\", \"slotInfo\": \[
{ \"slotAdUnitId\": \"4fa9fd56-ddfe-4f25-a18f-0b153996119b\" } \] } \] }
\] }, \"cacheTTL\": 600 } } }

## List-ads

### Image Ad

[Image Ad Mock
API](https://qa-money.newshunt.com/publicVibe/v1/list-ad/image.json)

Sample Responsejson{ \"ads\": \[ { \"type\": \"imgLink\", \"aduid\":
\"notId=ad-1096400437\", \"srcUrlExpiry\": 60, \"width\": 1080,
\"height\": 1080, \"card-position\": 4, \"positionWithTicker\": 4,
\"min-ad-distance\": 4, \"banner-fill\": \"fill-width\", \"bannerid\":
\"1724741649\", \"adTemplate\": \"L\", \"showOnlyImage\": false, \"id\":
\"4638720c8fb93c539c9fbf9b852c927e\", \"span\": 60,
\"useInternalBrowser\": \"false\", \"useWideViewPort\": true,
\"adCacheGood\": 1, \"adCacheAverage\": 1, \"adCacheSlow\": 1,
\"allowDelayedAdInsert\": true, \"adGroupId\":
\"4353980630764a1d25188.63691444\", \"adContext\": null, \"dedupId\":
\"4638720c8fb93c539c9fbf9b852c927e\", \"adTagPosition\": \"TOP_RIGHT\",
\"showBorder\": false, \"campaignId\": \"1724741649\", \"bannerId\":
\"1096400437\", \"isLargeAd\": true, \"errorUrl\":
\"https://qa-money.newshunt.com/beaconEvents?uniqueId=4638720c8fb93c539c9fbf9b852c927e&adId=1096400437&campaignId=1724741649&adPlacement=storypage&partnerRef=&city=&state=&country=india&clientId=4353980&reqTime=1661428896&eventType=AD_ERROR&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"largeAdDistance\": 8, \"position\": \"list-ad\", \"showPlayIcon\":
false, \"beaconUrl\":
\"https://qa-money.newshunt.com/impression?uniqueId=4638720c8fb93c539c9fbf9b852c927e&adId=1096400437&campaignId=1724741649&adPlacement=storypage&partnerRef=&city=&state=&country=india&clientId=4353980&reqTime=1661428896&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"content\": { \"imgLink\":
\"https://qa-money.newshunt.com/daedalus-banners/1096400437/1660113808_84435_600x600.jpg\",
\"itemSubtitle2\": { \"color\": \"#4caf79\", \"color-night\":
\"#ffffff\" }, \"reportText\": { \"color\": \"#999999\",
\"color-night\": \"#FFFFFF\", \"background-color\": \"#40000000\",
\"background-color-night\": \"#40000000\", \"data\": \"Ad\" } },
\"action\":
\"https://qa-money.newshunt.com/click?clientId=4353980&uniqueId=4638720c8fb93c539c9fbf9b852c927e&adId=1096400437&campaignId=1724741649&adPlacement=storypage&reqTime=1661428896&billingTypeId=3&orderId=1185215867&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=&\_\_oadest=http%3A%2F%2Fqa-dae.dailyhunt.in%2Fdaedalus-banners%2Fimage%2Fcreate%3FrequirementId%3D1724741649%26subTypeId%3D16\",
\"adLPTimeSpentBeaconUrl\":
\"https://qa-money.newshunt.com/beaconEvents?uniqueId=4638720c8fb93c539c9fbf9b852c927e&adId=1096400437&campaignId=1724741649&adPlacement=storypage&partnerRef=&city=&state=&country=india&clientId=4353980&reqTime=1661428896&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adRespondedBeaconUrl\":
\"https://qa-money.newshunt.com/beaconEvents?uniqueId=4638720c8fb93c539c9fbf9b852c927e&adId=1096400437&campaignId=1724741649&adPlacement=storypage&partnerRef=&city=&state=&country=india&clientId=4353980&reqTime=1661428896&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adInflatedBeaconUrl\":
\"https://qa-money.newshunt.com/beaconEvents?uniqueId=4638720c8fb93c539c9fbf9b852c927e&adId=1096400437&campaignId=1724741649&adPlacement=storypage&partnerRef=&city=&state=&country=india&clientId=4353980&reqTime=1661428896&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adContextRules\": { \"selectionPriority\": 2, \"cacheType\":
\"persist\", \"ttl\": 300, \"ruleGroup\": { \"respondedFor\": {
\"entityIds\": \[ \"nh-headlines\", \"91581308b67fdfbcd24028a0c513bc37\"
\], \"postId\": null } } }, \"adFeedback\": { \"feedbackUrl\":
\"https://qa-money.newshunt.com/data-api/adfeedback?bannerId=1096400437&campaignId=1724741649&uniqueId=4638720c8fb93c539c9fbf9b852c927e&city=\"
}, \"requestUrl\":
\"https://qa-money.newshunt.com/fallback?clientid=4353980&req_time=25082022+17%3A31%3A36&paper=nh-headlines&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=none&user_handset_model=none&user_id=&placement=storypage&user_app_ver=19.0.12.2&banner_rotation_type=0&bannerSelectedBy=RankingService&bookedPlacement=storypage&banner_id=1096400437&campaign_id=1724741649&user_connection=w&connection_speed=FAST&user_os_ver=11.0&encGaid=MjBhYjcyN2EtZjQzNy00NzUzLWJiZWYtZjAzMGY1ZmQ3ZjIy&item_publisher_language=&user_languages=en&oi=1362&price_range=none&user_device_type=none&title=B2&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=4638720c8fb93c539c9fbf9b852c927e&region=&mcc=&mnc=&lac=&cellid=&ip=180.179.82.12&adGroupId=4353980630764a1d25188.63691444&topicId=91581308b67fdfbcd24028a0c513bc37&topicName=&ecpm=1000&audienceSegments=none&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-qa-az-7fh0&locationSource=&pincode=&subSlot=&bookedSubSlot=&ab=ECPM&partnerId=DH_APP&deliverySlab=1&userDeliverySlab=&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=1000&utmSource=&utmMedium=&utmCampaign=&appId=&autoPlayPref=3&installDeliverySlab=&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=1&topCampaignIds=1724741649%5E&topCampaignECPMs=1000&entityId=91581308b67fdfbcd24028a0c513bc37&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=&campaignPrdictedCtr=&productIds=&recoPolicy=&request_timestamp=1661428896&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=&variantName=&modelUuid=&networkSwitch=&topDirectCampaign=&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=1&expected_video_watch_duration=&campaign_type=TEST_MODE&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=&requestIdDebug=79ccf131dddb980a1cf4cd1274ddddee&gender=&age=&ageRange=&orderTypeV2=0&idfa=&s2sBidId=&imputationType=&amazonSdkPayload=&contentCreatorId=&scoringModel=&filteringModel=&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661428896&\",
\"shareability\": { \"text\": \"Share this ad\", \"subject\": \"Check
out the ad \", \"image\":
\"https://qa-money.newshunt.com/daedalus-banners/1096400437/1661338831_37636_share_image.png\"
} } \] }

### Native Ad

[Native Ad Mock
API](https://qa-money.newshunt.com/publicVibe/v1/list-ad/native.json)

Sample Responsejson{ \"ads\": \[ { \"type\": \"native-banner\",
\"aduid\": \"notId=ad-1501683269\", \"srcUrlExpiry\": 60, \"width\":
1080, \"height\": 550, \"card-position\": 4, \"positionWithTicker\": 4,
\"min-ad-distance\": 4, \"banner-fill\": \"fill-width\", \"bannerid\":
\"1724741649\", \"adTemplate\": \"H\", \"showOnlyImage\": false, \"id\":
\"d8f10d128f44641c1b38628dde87999e\", \"span\": 60,
\"useInternalBrowser\": \"false\", \"useWideViewPort\": true,
\"adCacheGood\": 1, \"adCacheAverage\": 1, \"adCacheSlow\": 1,
\"allowDelayedAdInsert\": true, \"adGroupId\":
\"43539806307217a96ebf7.48515022\", \"adContext\": null,
\"showPlayIcon\": false, \"dedupId\":
\"d8f10d128f44641c1b38628dde87999e\", \"adTagPosition\": \"TOP_RIGHT\",
\"showBorder\": false, \"campaignId\": \"1724741649\", \"bannerId\":
\"1501683269\", \"isLargeAd\": false, \"errorUrl\":
\"https://qa-money.newshunt.com/beaconEvents?uniqueId=d8f10d128f44641c1b38628dde87999e&adId=1501683269&campaignId=1724741649&adPlacement=storypage&partnerRef=&city=&state=&country=india&clientId=4353980&reqTime=1661411704&eventType=AD_ERROR&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"largeAdDistance\": 8, \"position\": \"list-ad\", \"sdk-order\": 2,
\"beaconUrl\":
\"https://qa-money.newshunt.com/impression?uniqueId=d8f10d128f44641c1b38628dde87999e&adId=1501683269&campaignId=1724741649&adPlacement=storypage&partnerRef=&city=&state=&country=india&clientId=4353980&reqTime=1661411704&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"landingUrl\": null, \"content\": { \"bg-color\": \"#ffffff\",
\"bg-color-night\": \"#000000\", \"language\": \"en\",
\"sourceAlphabet\": \"G\", \"iconLink\":
\"https://qa-money.newshunt.com/daedalus-banners/1501683269/1660114145_75941_990x505.jpg\",
\"itemTitle\": { \"color\": \"#000000\", \"color-night\": \"#ffffff\" },
\"itemSubtitle1\": { \"color\": \"#000000\", \"color-night\":
\"#ffffff\", \"data\": \"Description\" }, \"itemSubtitle2\": {
\"color\": \"#4caf79\", \"color-night\": \"#ffffff\", \"data\": \"Action
Text\" }, \"reportText\": { \"color\": \"#999999\", \"color-night\":
\"#FFFFFF\", \"background-color\": \"#40000000\",
\"background-color-night\": \"#40000000\", \"data\": \"Ad\" } },
\"action\":
\"https://qa-money.newshunt.com/click?clientId=4353980&uniqueId=d8f10d128f44641c1b38628dde87999e&adId=1501683269&campaignId=1724741649&adPlacement=storypage&reqTime=1661411704&billingTypeId=3&orderId=1185215867&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=&\_\_oadest=http%3A%2F%2Fqa-dae.dailyhunt.in%2Fdaedalus-banners%2Fnative-big%2Fcreate%3FrequirementId%3D1724741649%26subTypeId%3D0\",
\"adLPTimeSpentBeaconUrl\":
\"https://qa-money.newshunt.com/beaconEvents?uniqueId=d8f10d128f44641c1b38628dde87999e&adId=1501683269&campaignId=1724741649&adPlacement=storypage&partnerRef=&city=&state=&country=india&clientId=4353980&reqTime=1661411704&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adRespondedBeaconUrl\":
\"https://qa-money.newshunt.com/beaconEvents?uniqueId=d8f10d128f44641c1b38628dde87999e&adId=1501683269&campaignId=1724741649&adPlacement=storypage&partnerRef=&city=&state=&country=india&clientId=4353980&reqTime=1661411704&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adInflatedBeaconUrl\":
\"https://qa-money.newshunt.com/beaconEvents?uniqueId=d8f10d128f44641c1b38628dde87999e&adId=1501683269&campaignId=1724741649&adPlacement=storypage&partnerRef=&city=&state=&country=india&clientId=4353980&reqTime=1661411704&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adContextRules\": { \"selectionPriority\": 2, \"cacheType\":
\"persist\", \"ttl\": 300, \"ruleGroup\": { \"respondedFor\": {
\"entityIds\": \[ \"nh-headlines\", \"91581308b67fdfbcd24028a0c513bc37\"
\], \"postId\": null } } }, \"adFeedback\": { \"feedbackUrl\":
\"https://qa-money.newshunt.com/data-api/adfeedback?bannerId=1501683269&campaignId=1724741649&uniqueId=d8f10d128f44641c1b38628dde87999e&city=\"
}, \"requestUrl\":
\"https://qa-money.newshunt.com/fallback?clientid=4353980&req_time=25082022+12%3A45%3A04&paper=nh-headlines&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=none&user_handset_model=none&user_id=&placement=storypage&user_app_ver=19.0.12.2&banner_rotation_type=0&bannerSelectedBy=RankingService&bookedPlacement=storypage&banner_id=1501683269&campaign_id=1724741649&user_connection=w&connection_speed=FAST&user_os_ver=11.0&encGaid=MjBhYjcyN2EtZjQzNy00NzUzLWJiZWYtZjAzMGY1ZmQ3ZjIy&item_publisher_language=&user_languages=en&oi=1305&price_range=none&user_device_type=none&title=B5&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=d8f10d128f44641c1b38628dde87999e&region=&mcc=&mnc=&lac=&cellid=&ip=180.179.82.12&adGroupId=43539806307217a96ebf7.48515022&topicId=91581308b67fdfbcd24028a0c513bc37&topicName=&ecpm=1000&audienceSegments=none&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-qa-az-7fh0&locationSource=&pincode=&subSlot=&bookedSubSlot=&ab=ECPM&partnerId=DH_APP&deliverySlab=1&userDeliverySlab=&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=1000&utmSource=&utmMedium=&utmCampaign=&appId=&autoPlayPref=3&installDeliverySlab=&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=1&topCampaignIds=1151050526%5E1724741649%5E&topCampaignECPMs=1000%5E1000&entityId=91581308b67fdfbcd24028a0c513bc37&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=&campaignPrdictedCtr=&productIds=&recoPolicy=&request_timestamp=1661411704&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=&variantName=&modelUuid=&networkSwitch=&topDirectCampaign=&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=1&expected_video_watch_duration=&campaign_type=TEST_MODE&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=&requestIdDebug=8e0a81caa3b49370cc0b292011b20b8b&gender=&age=&ageRange=&orderTypeV2=0&idfa=&s2sBidId=&imputationType=&amazonSdkPayload=&contentCreatorId=&scoringModel=&filteringModel=&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661411704&\",
\"shareability\": null } \] }

### HTML Ad

[HTML Ad Mock
API](https://qa-money.newshunt.com/publicVibe/v1/list-ad/html.json)

Sample Response json{ \"ads\": \[ { \"type\": \"mraid-external\",
\"typeId\": 6, \"aduid\": \"notId=ad-1358059656\", \"srcUrlExpiry\": 60,
\"width\": 1650, \"height\": 1650, \"bannerid\": \"1724741649\",
\"adTemplate\": \"L\", \"showOnlyImage\": false, \"id\":
\"d5924d9b07c99acc5f89ec8e0270f8f6\", \"span\": 60,
\"useInternalBrowser\": \"false\", \"useWideViewPort\": true,
\"adCacheGood\": 1, \"adCacheAverage\": 1, \"adCacheSlow\": 1,
\"allowDelayedAdInsert\": true, \"adGroupId\":
\"43539806307682cd526c7.02547310\", \"adContext\": null, \"isVideo\":
\"false\", \"dedupId\": \"d5924d9b07c99acc5f89ec8e0270f8f6\",
\"adTagPosition\": \"TOP_RIGHT\", \"showPlaybackControls\": false,
\"enableGyroscope\": false, \"enableAccelerometer\": false,
\"gyroscopeFreq\": 100, \"accelerometerFreq\": 100, \"interactiveAd\":
true, \"showBorder\": false, \"campaignId\": \"1724741649\",
\"bannerId\": \"1358059656\", \"isLargeAd\": true, \"errorUrl\":
\"http://qa-money.newshunt.com/beaconEvents?uniqueId=d5924d9b07c99acc5f89ec8e0270f8f6&adId=1358059656&campaignId=1724741649&adPlacement=storypage&partnerRef=&city=&state=&country=india&clientId=4353980&reqTime=1661429803&eventType=AD_ERROR&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"largeAdDistance\": 8, \"position\": \"list-ad\", \"card-position\": 4,
\"min-ad-distance\": 4, \"positionWithTicker\": 4, \"banner-fill\":
\"fill-width\", \"beaconUrl\":
\"http://qa-money.newshunt.com/impression?uniqueId=d5924d9b07c99acc5f89ec8e0270f8f6&adId=1358059656&campaignId=1724741649&adPlacement=storypage&partnerRef=&city=&state=&country=india&clientId=4353980&reqTime=1661429803&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"coolAd\": { \"zipped\": false, \"type\": \"mraid\", \"tapToEng\":
\"Tap to engage\", \"tapToEngColor\": \"#FFFFFF\", \"tapToEngBgColor\":
\"#808080\", \"content\": { \"link\": false, \"data\": \"\<!doctype
html\>\\n\<html\>\\n\\n\<head\>\<meta name=\\\"viewport\\\"
content=\\\"initial-scale=1.0 user-scalable=no\\\" /\>\\n \<meta
charset=\\\"utf-8\\\"\>\\n \<meta name=\\\"viewport\\\"
content=\\\"width=device-width,
initial-scale=1\\\"\>\\n\</head\>\\n\<style type=\\\"text/css\\\"
media=\\\"screen\\\"\>\\n html,\\n body {\\n height: 100%\\n }\\n \\n
#parallax {\\n background-image:
url(http://qa-dae.dailyhunt.in/uploads/daedalus-banners/1358059656/1660113874_93147_720x543.jpg);\\n
height: 100%;\\n background-size: 100% 100%;\\n background-repeat:
no-repeat;\\n }\\n\\n .circle-text {\\n width: 7%;\\n z-index: 3;\\n
position: absolute;\\n display: none;\\n right: 5px;\\n top: 2px;\\n
font-family: Arial;\\n font-weight: 900;\\n font-size: +1.5em;\\n
}\\n\\n .circle-text:after {\\n content: \\\"\\\";\\n display: block;\\n
width: 100%;\\n height: 0;\\n padding-bottom: 100%;\\n
-moz-border-radius: 50%;\\n -webkit-border-radius: 50%;\\n
border-radius: 50%;\\n }\\n\\n .circle-text div {\\n float: left;\\n
width: 100%;\\n padding-top: 50%;\\n line-height: 1em;\\n margin-top:
-0.5em;\\n text-align: center;\\n }\\n\\n .circle-text.white div {\\n
color: black;\\n }\\n\\n .circle-text.white:after {\\n background:
white;\\n }\\n\</style\>\\n\\n\<body\>\\n \<div id=\\\"parallax\\\"
onclick=\\\"onImageClick()\\\"\>\</div\>\\n \<div class=\\\"circle-text
white\\\" id=\\\"circle-text\\\" onclick=\\\"onAdClose();\\\"\>\\n
\<div\>×\</div\>\\n \</div\>\\n\\n \<script\>\\n if (mraid.getState()
=== \'loading\') {\\n mraid.addEventListener(\'ready\', ready);\\n }
else {\\n ready();\\n }\\n\\n function ready() {\\n
onAdSetInListView();\\n mraid.useCustomClose(true);\\n }\\n\\n
mraid.addEventListener(\\\"stateChange\\\", function (state) {\\n if
(state == \\\"default\\\") {\\n onAdSetInListView();\\n } else if (state
== \\\"expanded\\\") {\\n onAdEngage();\\n }\\n });\\n\\n function
onImageClick() {\\n let state = mraid.getState();\\n if (state ===
\'loading\') {\\n mraid.addEventListener(\'ready\', ready);\\n } else if
(state === \'expanded\') {\\n
mraid.open(\\\"http://qa-dae.dailyhunt.in/daedalus-banners/htmlParallax/create?requirementId=1724741649&subTypeId=9\\\");\\n
} else if (state === \'default\') {\\n mraid.expand();\\n }\\n }\\n\\n
function onAdClose() {\\n mraid.close();\\n onAdSetInListView();\\n
}\\n\\n function onAdEngage() {\\n
document.getElementById(\\\"circle-text\\\").style.display =
\'block\';\\n }\\n\\n function onAdSetInListView() {\\n
document.getElementById(\\\"circle-text\\\").style.display =
\'none\';\\n }\\n \</script\>\\n\</body\>\\n\\n\</html\>\\n\" },
\"tracker\": { \"redirectWebUrl\": true, \"data\":
\"https://qa-money.newshunt.com/click?clientId=4353980&uniqueId=d5924d9b07c99acc5f89ec8e0270f8f6&adId=1358059656&campaignId=1724741649&adPlacement=storypage&billingTypeId=3&orderId=1185215867&forceTracker=&reqTime=1661429803&leadId=&subBannerId=&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=&\_\_oadest=\--USER_CLICK_URL\--\"
} }, \"action\":
\"http://qa-dae.dailyhunt.in/daedalus-banners/htmlParallax/create?requirementId=1724741649&subTypeId=9\",
\"contentBaseUrl\": \"http://qa-money.newshunt.com/\",
\"adLPTimeSpentBeaconUrl\":
\"http://qa-money.newshunt.com/beaconEvents?uniqueId=d5924d9b07c99acc5f89ec8e0270f8f6&adId=1358059656&campaignId=1724741649&adPlacement=storypage&partnerRef=&city=&state=&country=india&clientId=4353980&reqTime=1661429803&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adRespondedBeaconUrl\":
\"http://qa-money.newshunt.com/beaconEvents?uniqueId=d5924d9b07c99acc5f89ec8e0270f8f6&adId=1358059656&campaignId=1724741649&adPlacement=storypage&partnerRef=&city=&state=&country=india&clientId=4353980&reqTime=1661429803&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adInflatedBeaconUrl\":
\"http://qa-money.newshunt.com/beaconEvents?uniqueId=d5924d9b07c99acc5f89ec8e0270f8f6&adId=1358059656&campaignId=1724741649&adPlacement=storypage&partnerRef=&city=&state=&country=india&clientId=4353980&reqTime=1661429803&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adContextRules\": { \"selectionPriority\": 2, \"cacheType\":
\"persist\", \"ttl\": 300, \"ruleGroup\": { \"respondedFor\": {
\"entityIds\": \[ \"nh-headlines\", \"91581308b67fdfbcd24028a0c513bc37\"
\], \"postId\": null } } }, \"content\": { \"itemSubtitle2\": {
\"color\": \"#4caf79\", \"color-night\": \"#ffffff\", \"data\": \"Action
Text\" }, \"reportText\": { \"color\": \"#999999\", \"color-night\":
\"#FFFFFF\", \"background-color\": \"#40000000\",
\"background-color-night\": \"#40000000\", \"data\": \"Ad\" } },
\"landingUrl\": null, \"requestUrl\":
\"http://qa-money.newshunt.com/fallback?clientid=4353980&req_time=25082022+17%3A46%3A43&paper=nh-headlines&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=none&user_handset_model=none&user_id=&placement=storypage&user_app_ver=19.0.12.2&banner_rotation_type=0&bannerSelectedBy=RankingService&bookedPlacement=storypage&banner_id=1358059656&campaign_id=1724741649&user_connection=w&connection_speed=FAST&user_os_ver=11.0&encGaid=MjBhYjcyN2EtZjQzNy00NzUzLWJiZWYtZjAzMGY1ZmQ3ZjIy&item_publisher_language=&user_languages=en&oi=1365&price_range=none&user_device_type=none&title=Test_b3&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=d5924d9b07c99acc5f89ec8e0270f8f6&region=&mcc=&mnc=&lac=&cellid=&ip=180.179.82.12&adGroupId=43539806307682cd526c7.02547310&topicId=91581308b67fdfbcd24028a0c513bc37&topicName=&ecpm=1000&audienceSegments=none&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-qa-az-7fh0&locationSource=&pincode=&subSlot=&bookedSubSlot=&ab=ECPM&partnerId=DH_APP&deliverySlab=1&userDeliverySlab=&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=1000&utmSource=&utmMedium=&utmCampaign=&appId=&autoPlayPref=3&installDeliverySlab=&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=1&topCampaignIds=1724741649%5E1151050526%5E&topCampaignECPMs=1000%5E1000&entityId=91581308b67fdfbcd24028a0c513bc37&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=&campaignPrdictedCtr=&productIds=&recoPolicy=&request_timestamp=1661429803&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=&variantName=&modelUuid=&networkSwitch=&topDirectCampaign=&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=1&expected_video_watch_duration=&campaign_type=TEST_MODE&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=&requestIdDebug=488042d2d3ef042c630969b17ad5a229&gender=&age=&ageRange=&orderTypeV2=0&idfa=&s2sBidId=&imputationType=&amazonSdkPayload=&contentCreatorId=&scoringModel=&filteringModel=&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661429803&\",
\"adFeedback\": { \"feedbackUrl\":
\"http://qa-money.newshunt.com/data-api/adfeedback?bannerId=1358059656&campaignId=1724741649&uniqueId=d5924d9b07c99acc5f89ec8e0270f8f6&city=\"
}, \"shareability\": null } \] }

### Video Ad

[Video Ad Mock
API](http://qa-money.newshunt.com/publicVibe/v1/list-ad/video.json)

Sample Responsejson{ \"ads\": \[ { \"type\": \"external-sdk\",
\"aduid\": \"notId=ad-1557247623\", \"srcUrlExpiry\": 86400,
\"adGroupId\": \"43539806307217a96ebf7.48515022\", \"width\": 1080,
\"height\": 607, \"card-position\": 4, \"positionWithTicker\": 4,
\"min-ad-distance\": 4, \"bannerid\": \"1151050526\", \"adTemplate\":
\"H\", \"showOnlyImage\": false, \"id\":
\"72ffa9be64d08fde832df447db42466c\", \"span\": 60,
\"useInternalBrowser\": \"false\", \"useWideViewPort\": false,
\"allowDelayedAdInsert\": true, \"adContext\": null, \"showTitle\":
false, \"needsBackupAds\": true, \"ignoreVideoDuration\": 480000,
\"adDistanceMs\": 180000, \"dedupId\":
\"72ffa9be64d08fde832df447db42466c\", \"adCacheGood\": 1,
\"adCacheAverage\": 1, \"adCacheSlow\": 1, \"isLive\": false,
\"showLearnMore\": true, \"adTagPosition\": \"BOTTOM_OVERLAY_LEFT\",
\"showBorder\": false, \"campaignId\": \"1151050526\", \"bannerId\":
\"1557247623\", \"isLargeAd\": false, \"errorUrl\":
\"https://qa-money.newshunt.com/beaconEvents?uniqueId=72ffa9be64d08fde832df447db42466c&adId=1557247623&campaignId=1151050526&adPlacement=storypage&partnerRef=&city=&state=&country=india&clientId=4353980&reqTime=1661411704&eventType=AD_ERROR&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"largeAdDistance\": 8, \"position\": \"list-ad\", \"sdk-order\": 1,
\"beaconUrl\":
\"https://qa-money.newshunt.com/impression?uniqueId=72ffa9be64d08fde832df447db42466c&adId=1557247623&campaignId=1151050526&adPlacement=storypage&partnerRef=&city=&state=&country=india&clientId=4353980&reqTime=1661411704&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"external\": { \"tagURL\":
\"https%3A%2F%2Fqa-money.newshunt.com%2Fgetvast%3FclientId%3D4353980%26uniqueId%3D72ffa9be64d08fde832df447db42466c%26adId%3D1557247623%26campaignId%3D1151050526%26adPlacement%3Dstorypage%26cap%3D0%26reset%3D0%26billingTypeId%3D3%26orderId%3D294%26forceTracker%3D%26gaid%3D20ab727a-f437-4753-bbef-f030f5fd7f22%26gaidOptoutStatus%3D0%26reqTime%3D1661411704%26partnerId%3DDH_APP%26subSlot%3D%26nextAdIndex%3D%26bookedPlacement%3Dstorypage%26bookedSubSlot%3D%26clientVersions%3D19.0.12.2%26os%3Dandroid%26ucq%3Dfast%26resolution%3D1080x2028\",
\"mediaFileURL\":
\"http://video-service-qa.dailyhunt.in/video/a2-e5b5a6e0e7ca11ec9ffbf36001778489_vh.m3u8\",
\"vastIdentifier\": \"internal-vast\", \"data\": \"IMA-SDK\" },
\"landingUrl\": null, \"content\": { \"itemSubtitle2\": { \"color\":
\"#4caf79\", \"color-night\": \"#ffffff\" }, \"reportText\": {
\"color\": \"#FFFFFF\", \"color-night\": \"#FFFFFF\",
\"background-color\": \"#40000000\", \"background-color-night\":
\"#40000000\", \"data\": \"Ad\" }, \"thumbnailImageUrl\":
\"https://qa-money.newshunt.com/daedalus-banners/1557247623/1654761916_66813_990x505.jpg\",
\"learnMoreText\": { \"color\": \"#ffffff\", \"color-night\":
\"#ffffff\", \"data\": \"Learn More\" } }, \"brand\": { \"brandTitle\":
{ \"color\": \"#202020\", \"color-night\": \"#ffffff\", \"data\": \"DH\"
}, \"brandSubTitle\": { \"color\": \"#202020\", \"color-night\":
\"#ffffff\" }, \"brandFallbackText\": { \"color\": \"#ffffff\",
\"color-night\": \"#ffffff\", \"background-color\": \"#ebab05\",
\"background-color-night\": \"#ebab05\", \"type\": \"S\", \"data\":
\"D\" } }, \"action\":
\"https://qa-money.newshunt.com/click?clientId=4353980&uniqueId=72ffa9be64d08fde832df447db42466c&adId=1557247623&campaignId=1151050526&adPlacement=storypage&reqTime=1661411704&billingTypeId=3&orderId=294&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=&\_\_oadest=https%3A%2F%2Fgoogle.com\",
\"adRespondedBeaconUrl\":
\"https://qa-money.newshunt.com/beaconEvents?uniqueId=72ffa9be64d08fde832df447db42466c&adId=1557247623&campaignId=1151050526&adPlacement=storypage&partnerRef=&city=&state=&country=india&clientId=4353980&reqTime=1661411704&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adInflatedBeaconUrl\":
\"https://qa-money.newshunt.com/beaconEvents?uniqueId=72ffa9be64d08fde832df447db42466c&adId=1557247623&campaignId=1151050526&adPlacement=storypage&partnerRef=&city=&state=&country=india&clientId=4353980&reqTime=1661411704&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adContextRules\": { \"selectionPriority\": 2, \"cacheType\":
\"persist\", \"ttl\": 300, \"ruleGroup\": { \"respondedFor\": {
\"entityIds\": \[ \"nh-headlines\", \"91581308b67fdfbcd24028a0c513bc37\"
\], \"postId\": null } } }, \"adFeedback\": { \"feedbackUrl\":
\"https://qa-money.newshunt.com/data-api/adfeedback?bannerId=1557247623&campaignId=1151050526&uniqueId=72ffa9be64d08fde832df447db42466c&city=\"
}, \"requestUrl\":
\"https://qa-money.newshunt.com/fallback?clientid=4353980&req_time=25082022+12%3A45%3A04&paper=nh-headlines&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=none&user_handset_model=none&user_id=&placement=storypage&user_app_ver=19.0.12.2&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=storypage&banner_id=1557247623&campaign_id=1151050526&user_connection=w&connection_speed=FAST&user_os_ver=11.0&encGaid=MjBhYjcyN2EtZjQzNy00NzUzLWJiZWYtZjAzMGY1ZmQ3ZjIy&item_publisher_language=&user_languages=en&oi=1305&price_range=none&user_device_type=none&title=vast+vdo&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=72ffa9be64d08fde832df447db42466c&region=&mcc=&mnc=&lac=&cellid=&ip=180.179.82.12&adGroupId=43539806307217a96ebf7.48515022&topicId=91581308b67fdfbcd24028a0c513bc37&topicName=&ecpm=1000&audienceSegments=none&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-qa-az-7fh0&locationSource=&pincode=&subSlot=&bookedSubSlot=&ab=ECPM&partnerId=DH_APP&deliverySlab=1&userDeliverySlab=&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=1000&utmSource=&utmMedium=&utmCampaign=&appId=&autoPlayPref=3&installDeliverySlab=&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=1&topCampaignIds=1151050526%5E1724741649%5E&topCampaignECPMs=1000%5E1000&entityId=91581308b67fdfbcd24028a0c513bc37&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=&campaignPrdictedCtr=&productIds=&recoPolicy=&request_timestamp=1661411704&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=&variantName=&modelUuid=&networkSwitch=&topDirectCampaign=&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=&campaign_type=TEST_MODE&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=&requestIdDebug=8e0a81caa3b49370cc0b292011b20b8b&gender=&age=&ageRange=&orderTypeV2=0&idfa=&s2sBidId=&imputationType=&amazonSdkPayload=&contentCreatorId=&scoringModel=&filteringModel=&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661411704&\",
\"shareability\": null, \"adLPTimeSpentBeaconUrl\":
\"https://qa-money.newshunt.com/beaconEvents?uniqueId=72ffa9be64d08fde832df447db42466c&adId=1557247623&campaignId=1151050526&adPlacement=storypage&partnerRef=&city=&state=&country=india&clientId=4353980&reqTime=1661411704&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=storypage&bookedSubSlot=&contentId=&contentCreatorId=\"
} \] }

## Pgi Ads

### Image Ad

[Image Ad Mock
API](https://qa-money.newshunt.com/publicVibe/v1/pgi/image.json)

Sample Responsejson{ \"ads\": \[ { \"type\": \"pgi-native-article\",
\"aduid\": \"notId=ad-1380928919\", \"srcUrlExpiry\": 60, \"width\":
1080, \"height\": 2028, \"sessionCount\": 2, \"minThresholdSwipeCount\":
3, \"firstAdSwipeCount\": 3, \"pageSwipeCount\": 9,
\"maxPageSwipeCount\": 13, \"requestSwipeCountGood\": 1,
\"requestSwipeCountAverage\": 1, \"requestSwipeCountSlow\": 1,
\"titleBar\": true, \"skipTimer\": 5, \"bannerid\": \"1166133189\",
\"adTemplate\": \"L\", \"showOnlyImage\": false, \"id\":
\"cb92554ebd09e99e5dfd6cb1d205c5aa\", \"span\": 60,
\"useInternalBrowser\": \"false\", \"useWideViewPort\": true,
\"allowDelayedAdInsert\": true, \"adGroupId\":
\"4353987630765cfa84bb2.65853367\", \"adContext\": null,
\"interstitialDisplayType\": \"swipeable_no_topbar\", \"dedupId\":
\"cb92554ebd09e99e5dfd6cb1d205c5aa\", \"dedupDistance\": 1,
\"adCacheGood\": 1, \"adCacheAverage\": 1, \"adCacheSlow\": 1,
\"adTagPosition\": \"TOP_OVERLAY_RIGHT\", \"showBorder\": true,
\"campaignId\": \"1166133189\", \"bannerId\": \"1380928919\",
\"isLargeAd\": true, \"errorUrl\":
\"https://money.dailyhunt.in/beaconEvents?uniqueId=cb92554ebd09e99e5dfd6cb1d205c5aa&adId=1380928919&campaignId=1166133189&adPlacement=pgi&partnerRef=&city=&state=&country=india&clientId=4353987&reqTime=1661429199&eventType=AD_ERROR&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=pgi&bookedSubSlot=&contentId=&contentCreatorId=\",
\"largeAdDistance\": 8, \"position\": \"pgi\", \"beaconUrl\":
\"https://money.dailyhunt.in/impression?uniqueId=cb92554ebd09e99e5dfd6cb1d205c5aa&adId=1380928919&campaignId=1166133189&adPlacement=pgi&partnerRef=&city=&state=&country=india&clientId=4353987&reqTime=1661429199&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=pgi&bookedSubSlot=&contentId=&contentCreatorId=\",
\"content\": { \"language\": \"en\", \"shortInfo\": null, \"iconLink\":
null, \"itemTitle\": { \"color\": \"#000000\", \"color-night\":
\"#ffffff\" }, \"itemImage\": { \"width\": 1080, \"height\": 1962,
\"data\":
\"https://acdn.newshuntads.com/daedalus-banners/1380928919/1661336647_20379_1080x2592.jpg\"
}, \"htmlBody\": null, \"itemRating\": null, \"actionText\": null,
\"reportText\": { \"color\": \"#FFFFFF\", \"color-night\": \"#FFFFFF\",
\"background-color\": \"#40000000\", \"background-color-night\":
\"#40000000\", \"data\": \"Ad\" } }, \"action\":
\"https://money.dailyhunt.in/click?clientId=4353987&uniqueId=cb92554ebd09e99e5dfd6cb1d205c5aa&adId=1380928919&campaignId=1166133189&adPlacement=pgi&reqTime=1661429199&billingTypeId=3&orderId=1898928132&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=pgi&bookedSubSlot=&contentId=&contentCreatorId=&\_\_oadest=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN839696.2059904DAILYHUNT%2FB28292020.344354370%3Bdc_trk_aid%3D536076790%3Bdc_trk_cid%3D176077429%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D%3Btfua%3D%3Bltd%3D\",
\"adLPTimeSpentBeaconUrl\":
\"https://money.dailyhunt.in/beaconEvents?uniqueId=cb92554ebd09e99e5dfd6cb1d205c5aa&adId=1380928919&campaignId=1166133189&adPlacement=pgi&partnerRef=&city=&state=&country=india&clientId=4353987&reqTime=1661429199&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=pgi&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adRespondedBeaconUrl\":
\"https://money.dailyhunt.in/beaconEvents?uniqueId=cb92554ebd09e99e5dfd6cb1d205c5aa&adId=1380928919&campaignId=1166133189&adPlacement=pgi&partnerRef=&city=&state=&country=india&clientId=4353987&reqTime=1661429199&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=pgi&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adInflatedBeaconUrl\":
\"https://money.dailyhunt.in/beaconEvents?uniqueId=cb92554ebd09e99e5dfd6cb1d205c5aa&adId=1380928919&campaignId=1166133189&adPlacement=pgi&partnerRef=&city=&state=&country=india&clientId=4353987&reqTime=1661429199&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=pgi&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adContextRules\": { \"selectionPriority\": 2, \"cacheType\":
\"session\", \"ttl\": 300, \"ruleGroup\": { \"respondedFor\": {
\"entityIds\": \[ \"nh-headlines\", \"91581308b67fdfbcd24028a0c513bc37\"
\], \"postId\": null } } }, \"adFeedback\": { \"feedbackUrl\":
\"https://money.dailyhunt.in/data-api/adfeedback?bannerId=1380928919&campaignId=1166133189&uniqueId=cb92554ebd09e99e5dfd6cb1d205c5aa&city=\"
}, \"requestUrl\":
\"https://money.dailyhunt.in/fallback?clientid=4353987&req_time=25082022+17%3A36%3A39&paper=nh-headlines&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=none&user_handset_model=none&user_id=&placement=pgi&user_app_ver=19.0.12.2&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=pgi&banner_id=1380928919&campaign_id=1166133189&user_connection=w&connection_speed=FAST&user_os_ver=11.0&encGaid=MjBhYjcyN2EtZjQzNy00NzUzLWJiZWYtZjAzMGY1ZmQ3ZjIy&item_publisher_language=&user_languages=en&oi=1363&price_range=none&user_device_type=none&title=1080x2592&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=cb92554ebd09e99e5dfd6cb1d205c5aa&region=&mcc=&mnc=&lac=&cellid=&ip=10.52.134.5&adGroupId=4353987630765cfa84bb2.65853367&topicId=91581308b67fdfbcd24028a0c513bc37&topicName=&ecpm=22.39999961853&audienceSegments=none&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-az-b320&locationSource=&pincode=&subSlot=&bookedSubSlot=&ab=ECPM&partnerId=DH_APP&deliverySlab=1&userDeliverySlab=0&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=22.39999961853&utmSource=&utmMedium=&utmCampaign=&appId=&autoPlayPref=3&installDeliverySlab=&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=1&topCampaignIds=1166133189%5E&topCampaignECPMs=22.39999961853&entityId=91581308b67fdfbcd24028a0c513bc37&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=&campaignPrdictedCtr=&productIds=&recoPolicy=&request_timestamp=1661429199&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=0&variantName=&modelUuid=&networkSwitch=NONE&topDirectCampaign=1166133189&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=0&campaign_type=SPONSORED&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=&requestIdDebug=3e2990cb2317d19ee13acb1abdd1653f&gender=&age=&ageRange=&orderTypeV2=0&idfa=&s2sBidId=&imputationType=&amazonSdkPayload=&contentCreatorId=&scoringModel=&filteringModel=&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661429199&\",
\"beaconUrlAdditional\": \[
\"https://ad.doubleclick.net/ddm/trackimp/N839696.2059904DAILYHUNT/B28292020.344354370;dc_trk_aid=536076790;dc_trk_cid=176077429;ord=1661429199.6931;dc_lat=;dc_rdid=;tag_for_child_directed_treatment=;tfua=;ltd=?\"
\], \"shareability\": null } \] }

### HTML Ad

[HTML Ad Mock
API](http://qa-money.newshunt.com/publicVibe/v1/pgi/html.json)

Sample Responsejson{ \"ads\": \[ { \"type\": \"pgi-external\",
\"typeId\": 6, \"aduid\": \"notId=ad-1774008698\", \"srcUrlExpiry\": 60,
\"width\": 1080, \"height\": 2028, \"bannerid\": \"1151050526\",
\"adTemplate\": \"L\", \"showOnlyImage\": false, \"id\":
\"0161bd7367a80240752dc263f0ecdf25\", \"span\": 60,
\"useInternalBrowser\": \"false\", \"useWideViewPort\": true,
\"adCacheGood\": 1, \"adCacheAverage\": 1, \"adCacheSlow\": 1,
\"allowDelayedAdInsert\": true, \"adGroupId\":
\"4353980630767e1a6cc78.10073140\", \"adContext\": null, \"isVideo\":
\"false\", \"dedupId\": \"0161bd7367a80240752dc263f0ecdf25\",
\"adTagPosition\": \"TOP_OVERLAY_RIGHT\", \"showPlaybackControls\":
false, \"enableGyroscope\": false, \"enableAccelerometer\": false,
\"gyroscopeFreq\": 100, \"accelerometerFreq\": 100, \"showBorder\":
false, \"campaignId\": \"1151050526\", \"bannerId\": \"1774008698\",
\"isLargeAd\": false, \"errorUrl\":
\"http://qa-money.newshunt.com/beaconEvents?uniqueId=0161bd7367a80240752dc263f0ecdf25&adId=1774008698&campaignId=1151050526&adPlacement=pgi&partnerRef=&city=&state=&country=india&clientId=4353980&reqTime=1661429729&eventType=AD_ERROR&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=pgi&bookedSubSlot=&contentId=&contentCreatorId=\",
\"largeAdDistance\": 8, \"position\": \"pgi\", \"sessionCount\": 2,
\"minThresholdSwipeCount\": 3, \"firstAdSwipeCount\": 3,
\"pageSwipeCount\": 9, \"maxPageSwipeCount\": 13,
\"requestSwipeCountGood\": 1, \"requestSwipeCountAverage\": 1,
\"requestSwipeCountSlow\": 1, \"titleBar\": true, \"skipTimer\": 5,
\"showHTMLPgiOnlyOnVisible\": \"false\", \"interstitialDisplayType\":
\"swipeable_no_topbar\", \"beaconUrl\":
\"http://qa-money.newshunt.com/impression?uniqueId=0161bd7367a80240752dc263f0ecdf25&adId=1774008698&campaignId=1151050526&adPlacement=pgi&partnerRef=&city=&state=&country=india&clientId=4353980&reqTime=1661429729&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=pgi&bookedSubSlot=&contentId=&contentCreatorId=\",
\"coolAd\": { \"zipped\": false, \"type\": \"pgi\", \"content\": {
\"link\": false, \"data\": \"\<meta name=\\\"viewport\\\"
content=\\\"initial-scale=1.0 user-scalable=no\\\" /\>\<h1\>Hello
World\</h1\>\" }, \"tracker\": { \"redirectWebUrl\": true, \"data\":
\"https://qa-money.newshunt.com/click?clientId=4353980&uniqueId=0161bd7367a80240752dc263f0ecdf25&adId=1774008698&campaignId=1151050526&adPlacement=pgi&billingTypeId=3&orderId=294&forceTracker=&reqTime=1661429729&leadId=&subBannerId=&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=pgi&bookedSubSlot=&contentId=&contentCreatorId=&\_\_oadest=\--USER_CLICK_URL\--\"
} }, \"action\": null, \"contentBaseUrl\":
\"http://qa-money.newshunt.com/\", \"adLPTimeSpentBeaconUrl\":
\"http://qa-money.newshunt.com/beaconEvents?uniqueId=0161bd7367a80240752dc263f0ecdf25&adId=1774008698&campaignId=1151050526&adPlacement=pgi&partnerRef=&city=&state=&country=india&clientId=4353980&reqTime=1661429729&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=pgi&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adRespondedBeaconUrl\":
\"http://qa-money.newshunt.com/beaconEvents?uniqueId=0161bd7367a80240752dc263f0ecdf25&adId=1774008698&campaignId=1151050526&adPlacement=pgi&partnerRef=&city=&state=&country=india&clientId=4353980&reqTime=1661429729&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=pgi&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adInflatedBeaconUrl\":
\"http://qa-money.newshunt.com/beaconEvents?uniqueId=0161bd7367a80240752dc263f0ecdf25&adId=1774008698&campaignId=1151050526&adPlacement=pgi&partnerRef=&city=&state=&country=india&clientId=4353980&reqTime=1661429729&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=&nextAdIndex=&bookedPlacement=pgi&bookedSubSlot=&contentId=&contentCreatorId=\",
\"adContextRules\": { \"selectionPriority\": 2, \"cacheType\":
\"session\", \"ttl\": 300, \"ruleGroup\": { \"respondedFor\": {
\"entityIds\": \[ \"nh-headlines\", \"91581308b67fdfbcd24028a0c513bc37\"
\], \"postId\": null } } }, \"content\": { \"itemSubtitle2\": {
\"color\": \"#4caf79\", \"color-night\": \"#ffffff\" }, \"reportText\":
{ \"color\": \"#FFFFFF\", \"color-night\": \"#FFFFFF\",
\"background-color\": \"#40000000\", \"background-color-night\":
\"#40000000\", \"data\": \"Ad\" } }, \"landingUrl\": null,
\"requestUrl\":
\"http://qa-money.newshunt.com/fallback?clientid=4353980&req_time=25082022+17%3A45%3A29&paper=nh-headlines&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=none&user_handset_model=none&user_id=&placement=pgi&user_app_ver=19.0.12.2&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=pgi&banner_id=1774008698&campaign_id=1151050526&user_connection=w&connection_speed=FAST&user_os_ver=11.0&encGaid=MjBhYjcyN2EtZjQzNy00NzUzLWJiZWYtZjAzMGY1ZmQ3ZjIy&item_publisher_language=&user_languages=en&oi=1365&price_range=none&user_device_type=none&title=test&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=0161bd7367a80240752dc263f0ecdf25&region=&mcc=&mnc=&lac=&cellid=&ip=180.179.82.12&adGroupId=4353980630767e1a6cc78.10073140&topicId=91581308b67fdfbcd24028a0c513bc37&topicName=&ecpm=1000&audienceSegments=none&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-qa-az-7fh0&locationSource=&pincode=&subSlot=&bookedSubSlot=&ab=ECPM&partnerId=DH_APP&deliverySlab=1&userDeliverySlab=&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=1000&utmSource=&utmMedium=&utmCampaign=&appId=&autoPlayPref=3&installDeliverySlab=&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=1&topCampaignIds=1151050526%5E&topCampaignECPMs=1000&entityId=91581308b67fdfbcd24028a0c513bc37&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=&campaignPrdictedCtr=&productIds=&recoPolicy=&request_timestamp=1661429729&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=&variantName=&modelUuid=&networkSwitch=&topDirectCampaign=&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=&campaign_type=TEST_MODE&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=&requestIdDebug=a9f1b3515c82c5ac411e2849c16be1f6&gender=&age=&ageRange=&orderTypeV2=0&idfa=&s2sBidId=&imputationType=&amazonSdkPayload=&contentCreatorId=&scoringModel=&filteringModel=&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661429729&\",
\"adFeedback\": { \"feedbackUrl\":
\"http://qa-money.newshunt.com/data-api/adfeedback?bannerId=1774008698&campaignId=1151050526&uniqueId=0161bd7367a80240752dc263f0ecdf25&city=\"
}, \"shareability\": null } \] }

# Iteration-2 Mock Responses

## Handshake

[Handshake Mock
API](https://qa-money.newshunt.com/publicVibe/v2/pvHandshake.json)

Sample Responsejson{ \"code\": 200, \"data\": { \"version\":
\"a8d6d073e262f8f9e9ac69118662ef83\", \"adCache\": { \"list-ad\": {
\"prefetch\": true, \"cacheTTL\": 300, \"cacheCountGood\": 1,
\"cacheCountAverage\": 1, \"cacheCountSlow\": 1 }, \"interstitial\": {
\"prefetch\": true, \"cacheTTL\": 300, \"cacheCountGood\": 1,
\"cacheCountAverage\": 1, \"cacheCountSlow\": 1 } },
\"minAspectRatioNativeHighTemplate\": 1.3, \"minAspectRatioVideo\": 1.7,
\"iosVideoScriptFilePath\":
\"http://money.dailyhunt.in/ios/HTMLVideoAdScript.js\",
\"fetchCampaignData\": { \"syncInterval\": { \"foreground\": 300,
\"background\": 43200 }, \"url\":
\"http://money.dailyhunt.in/fetchCampaignData\", \"enableSoftCounter\":
true }, \"adLpTimespentTimeout\": 300, \"reportAdsMenu\": { \"url\":
\"https://money.dailyhunt.in/feedback.php\", \"title\": \"Advertisement
Feedback\", \"options\": \[ { \"id\":
\"SHOW_MORE_OF_SUCH_ADVERTISEMENTS\", \"labels\": { \"en\": \"Show more
of such advertisements\", \"hi\": \"ऐसे ही विज्ञापन अधिक दिखाएं\", \"ta\":
\"இதுபோன்ற விளம்பரங்களை அதிகமாக காட்டுங்கள்\", \"te\": \"ఇలాంటి ప్రకటనలు మరిన్ని
చూపించు\", \"ml\": \"ഇതുപോലുള്ള പരസ്യങ്ങള്‍ കൂടുതല്‍ കാണിക്കുക\", \"bn\": \"এই ধরনের
আরও বিজ্ঞাপন দেখান\", \"mr\": \"अशा प्रकारच्या अधिक जाहिराती दाखवा\",
\"kn\": \"ಇಂತಹ ಹೆಚ್ಚು ಜಾಹೀರಾತುಗಳನ್ನು ತೋರಿಸು\", \"gu\": \"આવી જાહેરાતો વધુ
દેખાડો\", \"pa\": \"ਅਜਿਹੇ ਇਸ਼ਤਿਹਾਰ ਜ਼ਿਆਦਾ ਦਿਖਾਓ\", \"or\": \"ଏପରି ବିଜ୍ଞାପନ ଅଧିକ
ଦେଖାନ୍ତୁ\", \"ur\": \"اس طرح کے زیادہ اشتہارات دکھائیں\", \"ar\": \"لرؤية
المزيد من الاعلانات المشابهة\" }, \"dataToSend\":
\"{\\\"selections\\\":{\\\"L1\\\":\\\"SHOW_MORE_OF_SUCH_ADVERTISEMENTS\\\"}}\",
\"iconUrl\":
\"http://assets-news-bcdn.dailyhunt.in/cmd/resize/#DH_EMB_IMG_REP#\_\_DHQ\_/fetchdata16/images/56/cb/6c/56cb6c5cb81f323cf4f4d30a33ba7594cc30f555925bc8cb6556cb88736ed89b.png\",
\"thankYouMessage\": { \"en\": \"Thank You\", \"hi\": \"धन्यवाद\",
\"ta\": \"நன்றி\", \"te\": \"ధన్యవాదాలు\", \"ml\": \"നന്ദി\", \"bn\":
\"ধন্যবাদ\", \"mr\": \"धन्यवाद\", \"kn\": \"ಧನ್ಯವಾದಗಳು\", \"gu\": \"આપનો
આભાર\", \"pa\": \"ਧੰਨਵਾਦ\", \"or\": \"ଆପଣଙ୍କୁ ଧନ୍ୟବାଦ\", \"ur\": \"شکریہ\",
\"ar\": \"شكراًً\" } }, { \"id\": \"SHOW_LESS_OF_SUCH_ADVERTISEMENTS\",
\"labels\": { \"en\": \"Show less of such advertisements\", \"hi\": \"ऐसे
विज्ञापन कम दिखाएं\", \"ta\": \"இதுபோன்ற விளம்பரங்களை குறைவாக காட்டுங்கள்\",
\"te\": \"ఇలాంటి ప్రకటనలు తక్కువగా చూపించు\", \"ml\": \"ഇതുപോലുള്ള പരസ്യങ്ങള്‍ കുറവ്
കാണിക്കുക\", \"bn\": \"এই দরনের বিজ্ঞাপন কম দেখান\", \"mr\": \"अशा प्रकारच्या
कमी जाहिराती दाखवा\", \"kn\": \"ಇಂತಹ ಕಡಿಮೆ ಜಾಹೀರಾತುಗಳನ್ನು ತೋರಿಸು\", \"gu\":
\"આવી જાહેરાતો ઓછી દેખાડો\", \"pa\": \"ਅਜਿਹੇ ਇਸ਼ਤਿਹਾਰ ਘੱਟ ਦਿਖਾਓ\", \"or\":
\"ଏପରି ବିଜ୍ଞାପନ କମ ଦେଖାନ୍ତୁ\", \"ur\": \"اس طرح کے کم اشتہارات دکھائیں\",
\"ar\": \"لرؤية اقل من الاعلانات المشابهة\" }, \"showWebForm\": true,
\"iconUrl\":
\"http://assets-news-bcdn.dailyhunt.in/cmd/resize/#DH_EMB_IMG_REP#\_\_DHQ\_/fetchdata16/images/0f/50/f5/0f50f56f7a6ffdaae9f21e95af14cd5345ec62f50e17557084d2384f86cbcf0d.png\"
}, { \"id\": \"REPORT_ADVERTISEMENTS\", \"labels\": { \"en\": \"Report
advertisements\", \"hi\": \"विज्ञापनों को रिपोर्ट करें\", \"ta\":
\"விளம்பரங்களை ரிப்போர்ட் செய்க\", \"te\": \"ప్రకటనలపై రిపోర్ట్ చేయి\", \"ml\":
\"പരസ്യങ്ങള്‍ റിപ്പോര്‍ട്ട് ചെയ്യുക.\", \"bn\": \"বিজ্ঞাপন নিয়ে রিপোর্ট করুন\",
\"mr\": \"जाहिराती रिपोर्ट करा\", \"kn\": \"ಜಾಹೀರಾತುಗಳನ್ನು ರಿಪೋರ್ಟ್ ಮಾಡಿ\",
\"gu\": \"જાહેરાતો રિપોર્ટ કરો\", \"pa\": \"ਇਸ਼ਤਿਹਾਰਾਂ ਦੀ ਰਿਪੋਰਟ ਕਰੋ\",
\"or\": \"ବିଜ୍ଞାପନ ବିଷୟରେ ରିପୋର୍ଟ କରନ୍ତୁ\", \"ur\": \"اشتہارات کی رپورٹ دیں\",
\"ar\": \"تبليغ عن اعلان\" }, \"showWebForm\": true, \"iconUrl\":
\"http://assets-news-bcdn.dailyhunt.in/cmd/resize/#DH_EMB_IMG_REP#\_\_DHQ\_/fetchdata16/images/6a/20/e2/6a20e2617932c31d54ccc3a01ae841a63c0e1951ba26af2f56d33769b248050e.png\"
}, { \"id\": \"REPORT_COPYRIGHT\", \"labels\": { \"en\": \"Report
Copyright\", \"hi\": \"कॉपीराइट को रिपोर्ट करें\", \"ta\": \"காப்பிரைட் பற்றி
ரிப்போர்ட் செய்க\", \"te\": \"కాపీరైట్‌పై రిపోర్ట్ చేయండి\", \"ml\": \"കോപ്പിറൈറ്റ്
റിപ്പോര്‍ട്ട് ചെയ്യുക\", \"bn\": \"কপিরাইট রিপোর্ট করুন\", \"mr\": \"कॉपीराइट
रिपोर्ट करा\", \"kn\": \"ಕಾಪಿರೈಟ್ ಅನ್ನು ರಿಪೋರ್ಟ್ ಮಾಡಿ\", \"gu\": \"કૉપીરાઈટ
રિપૉર્ટ કરો\", \"pa\": \"ਕਾਪੀਰਾਈਟ ਦੀ ਰਿਪੋਰਟ ਕਰੋ\", \"or\": \"କପିରାଇଟ୍ ରିପୋର୍ଟ
କରନ୍ତୁ\", \"ur\": \"کاپی رائٹ کو رپورٹ کریں\", \"ar\": \"تبليغ عن حقوق
النشر\" }, \"dataToSend\":
\"{\\\"selections\\\":{\\\"L1\\\":\\\"REPORT_COPYRIGHT\\\"},\\\"block\\\":true}\",
\"iconUrl\":
\"http://assets-news-bcdn.dailyhunt.in/cmd/resize/#DH_EMB_IMG_REP#\_\_DHQ\_/fetchdata16/images/51/45/79/514579f5b4966485f373498a28b84b98cae87a09acbaacc672881a38fbcbc91f.png\",
\"thankYouMessage\": { \"en\": \"Thanks for letting us know. Your
feedback helps us improve the quality of content on Dailyhunt\", \"hi\":
\"हमें बताने के लिए धन्यवाद। आपके सुझाव हमें डेलीहंट पर कॉन्टेंट की गुणवत्ता बेहतर बनाने में
मदद करते हैं।\", \"ta\": \"எங்களிடம் தெரிவித்ததற்கு நன்றி. உங்களின் கருத்துகள்,
டெய்லிஹன்ட்டில் கன்டென்ட்டுகளின் தரத்தை மேம்படுத்த, எங்களுக்கு உதவியாக இருக்கும்.\",
\"te\": \"మాకు తెలియజేసినందుకు ధన్యవాదాలు. డైలీహంట్‌లో కంటెంట్‌ యొక్క నాణ్యతను మెరుగుపరచేందుకు
మీ అభిప్రాయం మాకు సహాయపడతుంది.\", \"ml\": \"അറിയിച്ചതിന് നന്ദി. ഡെയിലി ഹണ്ടില്‍
കണ്ടെന്‍റ് മെച്ചപ്പെടുത്തുവാന്‍ നിങ്ങളുടെ പ്രതികരണം സഹായകമാകും\", \"bn\": \"আমাদের
জানানোর জন্য ধন্যবাদ। আপনার প্রতিক্রিয়া আমাদের প্রতিদিন ডেইলিহান্ট-এ কনটেন্টের
উন্নতি সাধনে সাহায্য করে।\", \"mr\": \"आम्हाला माहिती दिल्याबद्दल आभार. तुमच्या
अभिप्रायामुळे डेलिहंटवरील कंटेन्टचा दर्जा सुधारण्यासाठी आम्हाला मदत होते.\", \"kn\":
\"ನಮಗೆ ತಿಳಿಸಿದ್ದಕ್ಕಾಗಿ ಧನ್ಯವಾದಗಳು. ನಿಮ್ಮ ಪ್ರತಿಕ್ರಿಯೆಯು ಡೈಲಿಹಂಟ್‌ನಲ್ಲಿ ಕಂಟೆಂಟ್ ಗುಣಮಟ್ಟವನ್ನು
ಸುಧಾರಿಸಲು ನಮಗೆ ಸಹಾಯ ಮಾಡುತ್ತದೆ\", \"gu\": \"અમને જણાવવા બદ્દલ આભાર. તમારો
પ્રતિસાદ ડેઈલીહન્ટ પર કન્ટેન્ટની ગુણવત્તા સુધારવામાં અમારી મદદ કરે છે\", \"pa\":
\"ਸਾਨੂੰ ਜਾਣਕਾਰੀ ਦੇਣ ਲਈ ਧੰਨਵਾਦ। ਤੁਹਾਡਾ ਫੀਡਬੈਕ ਡੇਲੀਹੰਟ 'ਤੇ ਕਾਨਟੈਂਟ ਦੀ ਕਵਾਲਿਟੀ ਸੁਧਾਰਨ
ਵਿੱਚ ਸਾਡੀ ਮਦਦ ਕਰਦਾ ਹੈ।\", \"or\": \"ଆମକୁ ଜଣାଇବା ପାଇଁ ଧନ୍ୟବାଦ। ଡେଲିହଣ୍ଟରେ
କଣ୍ଟେଣ୍ଟର ଗୁଣାତ୍ମକ ମାନରେ ଉନ୍ନତି ଆଣିବା ପାଇଁ ଆପଣଙ୍କ ମତାମତ ସହାୟକ ହୋଇଥାଏ।\", \"ur\":
\"ہمیں اطلاع دینے کیلئے شکریہ۔ آپ کے تاثرات ڈیلی ہنٹ پر مواد کے معیار کو
بہتر بنانے میں ہماری مدد کرتے ہیں۔\", \"ar\": \"Dailyhunt شكراً لإعلامنا.
ان ملاحظتكم تساعدنا على تحسين جودة المحتوى على\" },
\"collapseOnSubmit\": true } \] }, \"encryption\": { \"key\":
\"LS0tLS1CRUdJTiBQVUJMSUMgS0VZLS0tLS0KTUlHZk1BMEdDU3FHU0liM0RRRUJBUVVBQTRHTkFEQ0JpUUtCZ1FDWkd2L1dncXo1OEhjOURMZUFObHRmNFVJMwp3Vkoyb0xJYzZEemRheFdaTXRSVkYzTGYySlFSZURQMTRsKzNYUGdXaC9lVlFBU1Z3QTZKaUYxemw1WXhJS1ovCmppc2NEaFRDS25idmE1dTdrYjFMb0FUTlFKQlZtZGhSOFVZbWc3dUZWMnJTVUg3UEJ3VytyLzhKcm9sOXA1SGEKckIxVlBPMEtIR0YyZ2JNS2V3SURBUUFCCi0tLS0tRU5EIFBVQkxJQyBLRVktLS0tLQo=\",
\"version\": \"1\" }, \"enableGzipCompression\": false,
\"enableErrorScreenShot\": true, \"errorCodes\": { \"NO_INTERNET\":
1001, \"AD_LOAD_TIMEOUT\": 1002, \"AD_LOAD_ERROR\": 1003,
\"AD_NO_VAST_TAG_URL\": 1004, \"MALFORMED_CLICK_URL\": 1005,
\"INSTREAM_NO_SKIP\": 1006, \"OUTSTREAM_SKIP\": 1007 } } }

## List Ads

### Empty Ad

[Empty Ad Mock
API](https://qa-money.newshunt.com/publicVibe/v2/list-ad/empty.json)

Sample Responsejson\[ { \"type\": \"EMPTY\", \"id\":
\"b276436a8fbfb5a764f056c31f7bfc82\", \"campaignId\": \"1688073950\",
\"bannerId\": \"1687409206\", \"beacons\": { \"request\": {
\"internal\": \[
\"http://money.dailyhunt.in/fallback?clientid=548000&req_time=23082022+15%3A48%3A28&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=realme&user_handset_model=rmx1921&user_id=&placement=card-pp1&user_app_ver=16.1.1.1&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-pp1&banner_id=1131504889&campaign_id=1857226745&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=765&price_range=mid&user_device_type=none&title=Betway_KP_SOB_1_Native_990x505++English&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&region=&mcc=&mnc=&lac=&cellid=&ip=10.52.134.5&adGroupId=5480006304a97413bf59.38480371&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=40&audienceSegments=2+5+1782+1854+1865+1873+11+13+12+l&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-az-52dk&locationSource=IP_DFP&pincode=&subSlot=pp1_1&bookedSubSlot=pp1_1&ab=CAMP&partnerId=DH_APP&deliverySlab=5.24&userDeliverySlab=3.3360824584961&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=294.30322265625&utmSource=&utmMedium=&utmCampaign=&appModelType=APPBRAND&preCalibratedDownfunnelProbability=0.037273090332747&downfunnelVariantName=prod&downfunnelModelUuid=77508219&appId=226&autoPlayPref=3&installDeliverySlab=0.30528157949448&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=2&topCampaignIds=1857226745%5E&topCampaignECPMs=294.30322265625&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=3.7273089885712&campaignPrdictedCtr=0.34096893668175&productIds=&recoPolicy=&request_timestamp=1661249908&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=0.0034096892923117&variantName=prod&modelUuid=77433289&networkSwitch=NONE&topDirectCampaign=1857226745&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=0&campaign_type=STANDARD&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=bbf18a3d229cdce690a141fc0b77a2d0&gender=M&age=28&ageRange=3&orderTypeV2=0&idfa=&s2sBidId=&imputationType=IMPUTED&amazonSdkPayload=&contentCreatorId=&scoringModel=prod&filteringModel=prod&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661249908&\"
\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"responded\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"inflated\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"impression\": { \"internal\": \[
\"http://money.dailyhunt.in/impression?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&partnerId=DH_APP&appId=226&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"https://impression.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] } } } \]

### HTML Ad

[HTML Ad Mock
API](https://qa-money.newshunt.com/publicVibe/v2/list-ad/html.json)

Sample Responsejson\[ { \"type\": \"HTML\", \"id\":
\"7143f51a7795873e58fa7c5e94a5efa7\", \"campaignId\": \"1724741649\",
\"bannerId\": \"1358059656\", \"content\": { \"isVideo\": false,
\"showPlaybackControls\": false, \"width\": 329, \"height\": 84,
\"data\": \"\<!doctype html\>\\n\<html\>\\n\\n\<head\>\<meta
name=\\\"viewport\\\" content=\\\"initial-scale=1.0 user-scalable=no\\\"
/\>\\n \<meta charset=\\\"utf-8\\\"\>\\n \<meta name=\\\"viewport\\\"
content=\\\"width=device-width,
initial-scale=1\\\"\>\\n\</head\>\\n\<style type=\\\"text/css\\\"
media=\\\"screen\\\"\>\\n html,\\n body {\\n height: 100%\\n }\\n \\n
#parallax {\\n background-image:
url(http://qa-dae.dailyhunt.in/uploads/daedalus-banners/1358059656/1660113874_93147_720x543.jpg);\\n
height: 100%;\\n background-size: 100% 100%;\\n background-repeat:
no-repeat;\\n }\\n\\n .circle-text {\\n width: 7%;\\n z-index: 3;\\n
position: absolute;\\n display: none;\\n right: 5px;\\n top: 2px;\\n
font-family: Arial;\\n font-weight: 900;\\n font-size: +1.5em;\\n
}\\n\\n .circle-text:after {\\n content: \\\"\\\";\\n display: block;\\n
width: 100%;\\n height: 0;\\n padding-bottom: 100%;\\n
-moz-border-radius: 50%;\\n -webkit-border-radius: 50%;\\n
border-radius: 50%;\\n }\\n\\n .circle-text div {\\n float: left;\\n
width: 100%;\\n padding-top: 50%;\\n line-height: 1em;\\n margin-top:
-0.5em;\\n text-align: center;\\n }\\n\\n .circle-text.white div {\\n
color: black;\\n }\\n\\n .circle-text.white:after {\\n background:
white;\\n }\\n\</style\>\\n\\n\<body\>\\n \<div id=\\\"parallax\\\"
onclick=\\\"onImageClick()\\\"\>\</div\>\\n \<div class=\\\"circle-text
white\\\" id=\\\"circle-text\\\" onclick=\\\"onAdClose();\\\"\>\\n
\<div\>×\</div\>\\n \</div\>\\n\\n \<script\>\\n if (mraid.getState()
=== \'loading\') {\\n mraid.addEventListener(\'ready\', ready);\\n }
else {\\n ready();\\n }\\n\\n function ready() {\\n
onAdSetInListView();\\n mraid.useCustomClose(true);\\n }\\n\\n
mraid.addEventListener(\\\"stateChange\\\", function (state) {\\n if
(state == \\\"default\\\") {\\n onAdSetInListView();\\n } else if (state
== \\\"expanded\\\") {\\n onAdEngage();\\n }\\n });\\n\\n function
onImageClick() {\\n let state = mraid.getState();\\n if (state ===
\'loading\') {\\n mraid.addEventListener(\'ready\', ready);\\n } else if
(state === \'expanded\') {\\n
mraid.open(\\\"http://qa-dae.dailyhunt.in/daedalus-banners/htmlParallax/create?requirementId=1724741649&subTypeId=9\\\");\\n
} else if (state === \'default\') {\\n mraid.expand();\\n }\\n }\\n\\n
function onAdClose() {\\n mraid.close();\\n onAdSetInListView();\\n
}\\n\\n function onAdEngage() {\\n
document.getElementById(\\\"circle-text\\\").style.display =
\'block\';\\n }\\n\\n function onAdSetInListView() {\\n
document.getElementById(\\\"circle-text\\\").style.display =
\'none\';\\n }\\n \</script\>\\n\</body\>\\n\\n\</html\>\\n\" },
\"adFeedback\": { \"label\": { \"color\": \"#000000\", \"colorNight\":
\"#FFFFFF\", \"bgColor\": \"#40000000\", \"bgColorNight\":
\"#40000000\", \"data\": \"Ad\", \"position\": \"TOP_RIGHT\" },
\"feedbackUrl\":
\"http://money.dailyhunt.in/data-api/adfeedback?bannerId=1131504889&campaignId=1857226745&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&city=\"
}, \"beacons\": { \"request\": { \"internal\": \[
\"http://money.dailyhunt.in/fallback?clientid=548000&req_time=23082022+15%3A48%3A28&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=realme&user_handset_model=rmx1921&user_id=&placement=card-pp1&user_app_ver=16.1.1.1&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-pp1&banner_id=1131504889&campaign_id=1857226745&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=765&price_range=mid&user_device_type=none&title=Betway_KP_SOB_1_Native_990x505++English&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&region=&mcc=&mnc=&lac=&cellid=&ip=10.52.134.5&adGroupId=5480006304a97413bf59.38480371&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=40&audienceSegments=2+5+1782+1854+1865+1873+11+13+12+l&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-az-52dk&locationSource=IP_DFP&pincode=&subSlot=pp1_1&bookedSubSlot=pp1_1&ab=CAMP&partnerId=DH_APP&deliverySlab=5.24&userDeliverySlab=3.3360824584961&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=294.30322265625&utmSource=&utmMedium=&utmCampaign=&appModelType=APPBRAND&preCalibratedDownfunnelProbability=0.037273090332747&downfunnelVariantName=prod&downfunnelModelUuid=77508219&appId=226&autoPlayPref=3&installDeliverySlab=0.30528157949448&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=2&topCampaignIds=1857226745%5E&topCampaignECPMs=294.30322265625&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=3.7273089885712&campaignPrdictedCtr=0.34096893668175&productIds=&recoPolicy=&request_timestamp=1661249908&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=0.0034096892923117&variantName=prod&modelUuid=77433289&networkSwitch=NONE&topDirectCampaign=1857226745&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=0&campaign_type=STANDARD&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=bbf18a3d229cdce690a141fc0b77a2d0&gender=M&age=28&ageRange=3&orderTypeV2=0&idfa=&s2sBidId=&imputationType=IMPUTED&amazonSdkPayload=&contentCreatorId=&scoringModel=prod&filteringModel=prod&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661249908&\"
\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"responded\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"error\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"inflated\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"impression\": { \"internal\": \[
\"http://money.dailyhunt.in/impression?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&partnerId=DH_APP&appId=226&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"https://impression.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"click\": { \"internal\": \[\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"lpTimeSpent\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] } } } \]

### MRAID zip Ad

mraid zip Moc Api

Sample Response\[ { \"type\":\"MRAID_ZIP\",
\"id\":\"7143f51a7795873e58fa7c5e94a5efa7\",
\"campaignId\":\"1724741649\", \"bannerId\":\"1358059656\",
\"content\":{ \"isVideo\":false, \"showPlaybackControls\":false,
\"width\":329, \"height\":84, \"rootFile\":\"index.html\",
\"data\":\"https://qa-money.newshunt.com/daedalus-banners/3531/1626780922_66849\_.zip\"
}, \"adFeedback\":{ \"label\":{ \"color\":\"#000000\",
\"colorNight\":\"#FFFFFF\", \"bgColor\":\"#40000000\",
\"bgColorNight\":\"#40000000\", \"data\":\"Ad\",
\"position\":\"TOP_RIGHT\" },
\"feedbackUrl\":\"http://money.dailyhunt.in/data-api/adfeedback?bannerId=1131504889&campaignId=1857226745&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&city=\"
}, \"beacons\":{ \"request\":{ \"internal\":\[
\"http://money.dailyhunt.in/fallback?clientid=548000&req_time=23082022+15%3A48%3A28&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=realme&user_handset_model=rmx1921&user_id=&placement=card-pp1&user_app_ver=16.1.1.1&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-pp1&banner_id=1131504889&campaign_id=1857226745&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=765&price_range=mid&user_device_type=none&title=Betway_KP_SOB_1_Native_990x505++English&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&region=&mcc=&mnc=&lac=&cellid=&ip=10.52.134.5&adGroupId=5480006304a97413bf59.38480371&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=40&audienceSegments=2+5+1782+1854+1865+1873+11+13+12+l&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-az-52dk&locationSource=IP_DFP&pincode=&subSlot=pp1_1&bookedSubSlot=pp1_1&ab=CAMP&partnerId=DH_APP&deliverySlab=5.24&userDeliverySlab=3.3360824584961&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=294.30322265625&utmSource=&utmMedium=&utmCampaign=&appModelType=APPBRAND&preCalibratedDownfunnelProbability=0.037273090332747&downfunnelVariantName=prod&downfunnelModelUuid=77508219&appId=226&autoPlayPref=3&installDeliverySlab=0.30528157949448&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=2&topCampaignIds=1857226745%5E&topCampaignECPMs=294.30322265625&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=3.7273089885712&campaignPrdictedCtr=0.34096893668175&productIds=&recoPolicy=&request_timestamp=1661249908&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=0.0034096892923117&variantName=prod&modelUuid=77433289&networkSwitch=NONE&topDirectCampaign=1857226745&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=0&campaign_type=STANDARD&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=bbf18a3d229cdce690a141fc0b77a2d0&gender=M&age=28&ageRange=3&orderTypeV2=0&idfa=&s2sBidId=&imputationType=IMPUTED&amazonSdkPayload=&contentCreatorId=&scoringModel=prod&filteringModel=prod&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661249908&\"
\], \"external\":\[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"responded\":{ \"internal\":\[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\":\[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"error\":{ \"internal\":\[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\":\[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"inflated\":{ \"internal\":\[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\":\[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"impression\":{ \"internal\":\[
\"http://money.dailyhunt.in/impression?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&partnerId=DH_APP&appId=226&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\":\[
\"https://impression.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"click\":{ \"internal\":\[ \], \"external\":\[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"lpTimeSpent\":{ \"internal\":\[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\":\[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] } } } \]

### Image Ad

[Image Ad Mock
API](http://qa-money.newshunt.com/publicVibe/v2/list-ad/image.json)

Sample Responsejson\[ { \"type\": \"IMAGE\", \"id\":
\"b276436a8fbfb5a764f056c31f7bfc82\", \"campaignId\": \"1688073950\",
\"bannerId\": \"1687409206\", \"content\": { \"image\": { \"url\":
\"http://acdn.newshuntads.com/daedalus-banners/1687409206/1661148424_65680_600x600.jpg\",
\"width\": 329, \"height\": 84 }, \"cta\": { \"url\":
\"https://money.dailyhunt.in/click?clientId=548000&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&reqTime=1661249908&billingTypeId=3&orderId=60632&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=&\_\_oadest=https%3A%2F%2Fapp.appsflyer.com%2Fcom.betway.sports-direct%3Fpid%3Dnewshunt_int%26af_r%3Dhttps%253A%252F%252Fbetway.com%252Fdownload%252Fandroid-sports%26af_siteid%3Ddailyhunt%26c%3Dsustenance%26af_dp%3Dbetwaysports%253A%252F%252F%26af_sub_siteid%3Dcard-pp1%26af_sub3%3D1661249908.0849%26af_c_id%3D\--CAMPAIGN_ID\--%26af_sub4%3Ds%25253Dbw210554%252526a%25253DDB3488520822146189%26af_ad_id%3D\--BANNER_ID\--%26af_sub2%3D548000%26af_click_lookback%3D7d%26trackerProvider%3Dappsflyer%26clickid%3D4b4d28ded973a24c29c566aa5f3766a8%26dhExtras%3D\--DH_EXTRAS\--%26advertising_id%3D8043aad5-507a-428d-a8d5-b09c98a46d68\",
\"browser\": \"INTERNAL\" } }, \"adFeedback\": { \"label\": { \"color\":
\"#000000\", \"colorNight\": \"#FFFFFF\", \"bgColor\": \"#40000000\",
\"bgColorNight\": \"#40000000\", \"data\": \"Ad\", \"position\":
\"TOP_RIGHT\" }, \"feedbackUrl\":
\"http://money.dailyhunt.in/data-api/adfeedback?bannerId=1131504889&campaignId=1857226745&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&city=\"
}, \"beacons\": { \"request\": { \"internal\": \[
\"http://money.dailyhunt.in/fallback?clientid=548000&req_time=23082022+15%3A48%3A28&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=realme&user_handset_model=rmx1921&user_id=&placement=card-pp1&user_app_ver=16.1.1.1&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-pp1&banner_id=1131504889&campaign_id=1857226745&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=765&price_range=mid&user_device_type=none&title=Betway_KP_SOB_1_Native_990x505++English&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&region=&mcc=&mnc=&lac=&cellid=&ip=10.52.134.5&adGroupId=5480006304a97413bf59.38480371&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=40&audienceSegments=2+5+1782+1854+1865+1873+11+13+12+l&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-az-52dk&locationSource=IP_DFP&pincode=&subSlot=pp1_1&bookedSubSlot=pp1_1&ab=CAMP&partnerId=DH_APP&deliverySlab=5.24&userDeliverySlab=3.3360824584961&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=294.30322265625&utmSource=&utmMedium=&utmCampaign=&appModelType=APPBRAND&preCalibratedDownfunnelProbability=0.037273090332747&downfunnelVariantName=prod&downfunnelModelUuid=77508219&appId=226&autoPlayPref=3&installDeliverySlab=0.30528157949448&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=2&topCampaignIds=1857226745%5E&topCampaignECPMs=294.30322265625&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=3.7273089885712&campaignPrdictedCtr=0.34096893668175&productIds=&recoPolicy=&request_timestamp=1661249908&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=0.0034096892923117&variantName=prod&modelUuid=77433289&networkSwitch=NONE&topDirectCampaign=1857226745&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=0&campaign_type=STANDARD&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=bbf18a3d229cdce690a141fc0b77a2d0&gender=M&age=28&ageRange=3&orderTypeV2=0&idfa=&s2sBidId=&imputationType=IMPUTED&amazonSdkPayload=&contentCreatorId=&scoringModel=prod&filteringModel=prod&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661249908&\"
\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"responded\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"error\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"inflated\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"impression\": { \"internal\": \[
\"http://money.dailyhunt.in/impression?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&partnerId=DH_APP&appId=226&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"https://impression.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"click\": { \"internal\": \[\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"lpTimeSpent\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] } } } \]

### Native Ad

[Native Ad Mock
API](http://qa-money.newshunt.com/publicVibe/v2/list-ad/native.json)

Sample Responsejson\[ { \"type\": \"NATIVE\", \"id\":
\"4b4d28ded973a24c29c566aa5f3766a8\", \"campaignId\": \"1857226745\",
\"bannerId\": \"1131504889\", \"content\": { \"bgColor\": \"#ffffff\",
\"bgColorNight\": \"#000000\", \"brand\": { \"logo\":
\"https://icon-library.com/images/next-button-icon/next-button-icon-19.jpg\",
\"color\": \"#000000\", \"colorNight\": \"#ffffff\", \"data\":
\"Freshmart\" }, \"title\": { \"color\": \"#000000\", \"colorNight\":
\"#ffffff\", \"data\": \"Your neighbourhood grocer. A collection of
local brands, here for you.\" }, \"description\": { \"color\":
\"#545454\", \"colorNight\": \"#ffffff\", \"data\": \"Your neighbourhood
grocer. A collection of local brands, here for you. Your neighbourhood
grocer. A collection of local brands, here for you.Your neighbourhood
grocer. A collection of local brands\" }, \"cta\": { \"url\":
\"https://money.dailyhunt.in/click?clientId=548000&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&reqTime=1661249908&billingTypeId=3&orderId=60632&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=&\_\_oadest=https%3A%2F%2Fapp.appsflyer.com%2Fcom.betway.sports-direct%3Fpid%3Dnewshunt_int%26af_r%3Dhttps%253A%252F%252Fbetway.com%252Fdownload%252Fandroid-sports%26af_siteid%3Ddailyhunt%26c%3Dsustenance%26af_dp%3Dbetwaysports%253A%252F%252F%26af_sub_siteid%3Dcard-pp1%26af_sub3%3D1661249908.0849%26af_c_id%3D\--CAMPAIGN_ID\--%26af_sub4%3Ds%25253Dbw210554%252526a%25253DDB3488520822146189%26af_ad_id%3D\--BANNER_ID\--%26af_sub2%3D548000%26af_click_lookback%3D7d%26trackerProvider%3Dappsflyer%26clickid%3D4b4d28ded973a24c29c566aa5f3766a8%26dhExtras%3D\--DH_EXTRAS\--%26advertising_id%3D8043aad5-507a-428d-a8d5-b09c98a46d68\",
\"data\": \"Download Now\", \"color\": \"#4caf79\", \"colorNight\":
\"#ffffff\", \"bgColor\": \"#52A1DD,#5282E7\", \"bgColorNight\":
\"#52A1DD,#5282E7\", \"browser\": \"INTERNAL\" } }, \"adFeedback\": {
\"label\": { \"color\": \"#000000\", \"colorNight\": \"#FFFFFF\",
\"bgColor\": \"#40000000\", \"bgColorNight\": \"#40000000\", \"data\":
\"Ad\", \"position\": \"TOP_RIGHT\" }, \"feedbackUrl\":
\"http://money.dailyhunt.in/data-api/adfeedback?bannerId=1131504889&campaignId=1857226745&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&city=\"
}, \"beacons\": { \"request\": { \"internal\": \[
\"http://money.dailyhunt.in/fallback?clientid=548000&req_time=23082022+15%3A48%3A28&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=realme&user_handset_model=rmx1921&user_id=&placement=card-pp1&user_app_ver=16.1.1.1&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-pp1&banner_id=1131504889&campaign_id=1857226745&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=765&price_range=mid&user_device_type=none&title=Betway_KP_SOB_1_Native_990x505++English&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&region=&mcc=&mnc=&lac=&cellid=&ip=10.52.134.5&adGroupId=5480006304a97413bf59.38480371&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=40&audienceSegments=2+5+1782+1854+1865+1873+11+13+12+l&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-az-52dk&locationSource=IP_DFP&pincode=&subSlot=pp1_1&bookedSubSlot=pp1_1&ab=CAMP&partnerId=DH_APP&deliverySlab=5.24&userDeliverySlab=3.3360824584961&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=294.30322265625&utmSource=&utmMedium=&utmCampaign=&appModelType=APPBRAND&preCalibratedDownfunnelProbability=0.037273090332747&downfunnelVariantName=prod&downfunnelModelUuid=77508219&appId=226&autoPlayPref=3&installDeliverySlab=0.30528157949448&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=2&topCampaignIds=1857226745%5E&topCampaignECPMs=294.30322265625&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=3.7273089885712&campaignPrdictedCtr=0.34096893668175&productIds=&recoPolicy=&request_timestamp=1661249908&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=0.0034096892923117&variantName=prod&modelUuid=77433289&networkSwitch=NONE&topDirectCampaign=1857226745&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=0&campaign_type=STANDARD&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=bbf18a3d229cdce690a141fc0b77a2d0&gender=M&age=28&ageRange=3&orderTypeV2=0&idfa=&s2sBidId=&imputationType=IMPUTED&amazonSdkPayload=&contentCreatorId=&scoringModel=prod&filteringModel=prod&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661249908&\"
\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"responded\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"error\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"inflated\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"impression\": { \"internal\": \[
\"http://money.dailyhunt.in/impression?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&partnerId=DH_APP&appId=226&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"https://impression.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"click\": { \"internal\": \[\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"lpTimeSpent\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] } } } \]

### SDK Ad

[SDK Ad Mock
API](https://qa-money.newshunt.com/publicVibe/v2/list-ad/sdk.json)

Sample Responsejson\[ { \"type\": \"SDK\", \"id\":
\"b276436a8fbfb5a764f056c31f7bfc82\", \"campaignId\": \"1688073950\",
\"bannerId\": \"1687409206\", \"content\": { \"network\": {
\"identifier\": \"GOOGLE\", \"adunitId\":
\"/83414793/Common_Card_premium\", \"extras\": \"c_language:en,c_ecpm:
500,c_userIp: 10.52.134.4,clientId:
155362483,c_uniqueId:b095ee12c812399361112b4f20c40c44,c_city:\--LOCATION_CITY\--,topicKey:NULL,npKey:nh-headlines,c_connectionSpeed:FAST,ConnectionType:w,c_placementId:storypage,utm_source:\--UTM_SOURCE\--,Autoplay:
3\", \"adsizes\": \[ \"320x100\" \] }, \"cta\": { \"color\":
\"#ffffff\", \"colorNight\": \"#ffffff\", \"bgColor\":
\"#52A1DD,#5282E7\", \"bgColorNight\": \"#52A1DD,#5282E7\", \"browser\":
\"INTERNAL\" } }, \"adFeedback\": { \"label\": { \"color\": \"#000000\",
\"colorNight\": \"#FFFFFF\", \"bgColor\": \"#40000000\",
\"bgColorNight\": \"#40000000\", \"data\": \"Ad\", \"position\":
\"TOP_RIGHT\" } }, \"beacons\": { \"request\": { \"internal\": \[
\"http://money.dailyhunt.in/fallback?clientid=548000&req_time=23082022+15%3A48%3A28&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=realme&user_handset_model=rmx1921&user_id=&placement=card-pp1&user_app_ver=16.1.1.1&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-pp1&banner_id=1131504889&campaign_id=1857226745&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=765&price_range=mid&user_device_type=none&title=Betway_KP_SOB_1_Native_990x505++English&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&region=&mcc=&mnc=&lac=&cellid=&ip=10.52.134.5&adGroupId=5480006304a97413bf59.38480371&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=40&audienceSegments=2+5+1782+1854+1865+1873+11+13+12+l&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-az-52dk&locationSource=IP_DFP&pincode=&subSlot=pp1_1&bookedSubSlot=pp1_1&ab=CAMP&partnerId=DH_APP&deliverySlab=5.24&userDeliverySlab=3.3360824584961&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=294.30322265625&utmSource=&utmMedium=&utmCampaign=&appModelType=APPBRAND&preCalibratedDownfunnelProbability=0.037273090332747&downfunnelVariantName=prod&downfunnelModelUuid=77508219&appId=226&autoPlayPref=3&installDeliverySlab=0.30528157949448&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=2&topCampaignIds=1857226745%5E&topCampaignECPMs=294.30322265625&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=3.7273089885712&campaignPrdictedCtr=0.34096893668175&productIds=&recoPolicy=&request_timestamp=1661249908&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=0.0034096892923117&variantName=prod&modelUuid=77433289&networkSwitch=NONE&topDirectCampaign=1857226745&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=0&campaign_type=STANDARD&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=bbf18a3d229cdce690a141fc0b77a2d0&gender=M&age=28&ageRange=3&orderTypeV2=0&idfa=&s2sBidId=&imputationType=IMPUTED&amazonSdkPayload=&contentCreatorId=&scoringModel=prod&filteringModel=prod&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661249908&\"
\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"responded\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"error\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"inflated\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"impression\": { \"internal\": \[
\"http://money.dailyhunt.in/impression?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&partnerId=DH_APP&appId=226&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"https://impression.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"click\": { \"internal\": \[
\"https://money.dailyhunt.in/click?clientId=548000&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&reqTime=1661249908&billingTypeId=3&orderId=60632&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=&\_\_oadest=\"
\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"lpTimeSpent\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] } }, \"fallback\": { \"type\": \"SDK\", \"id\":
\"b276436a8fbfb5a764f056c31f7bfc82\", \"campaignId\": \"1688073950\",
\"bannerId\": \"1687409206\", \"content\": { \"network\": {
\"identifier\": \"FACEBOOK\", \"adunitId\":
\"131285656905938_1204641569570336\" }, \"cta\": { \"color\":
\"#ffffff\", \"colorNight\": \"#ffffff\", \"bgColor\":
\"#52A1DD,#5282E7\", \"bgColorNight\": \"#52A1DD,#5282E7\", \"browser\":
\"INTERNAL\" } }, \"adFeedback\": { \"label\": { \"color\": \"#000000\",
\"colorNight\": \"#FFFFFF\", \"bgColor\": \"#40000000\",
\"bgColorNight\": \"#40000000\", \"data\": \"Ad\", \"position\":
\"TOP_RIGHT\" } }, \"beacons\": { \"request\": { \"internal\": \[
\"http://money.dailyhunt.in/fallback?clientid=548000&req_time=23082022+15%3A48%3A28&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=realme&user_handset_model=rmx1921&user_id=&placement=card-pp1&user_app_ver=16.1.1.1&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-pp1&banner_id=1131504889&campaign_id=1857226745&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=765&price_range=mid&user_device_type=none&title=Betway_KP_SOB_1_Native_990x505++English&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&region=&mcc=&mnc=&lac=&cellid=&ip=10.52.134.5&adGroupId=5480006304a97413bf59.38480371&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=40&audienceSegments=2+5+1782+1854+1865+1873+11+13+12+l&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-az-52dk&locationSource=IP_DFP&pincode=&subSlot=pp1_1&bookedSubSlot=pp1_1&ab=CAMP&partnerId=DH_APP&deliverySlab=5.24&userDeliverySlab=3.3360824584961&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=294.30322265625&utmSource=&utmMedium=&utmCampaign=&appModelType=APPBRAND&preCalibratedDownfunnelProbability=0.037273090332747&downfunnelVariantName=prod&downfunnelModelUuid=77508219&appId=226&autoPlayPref=3&installDeliverySlab=0.30528157949448&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=2&topCampaignIds=1857226745%5E&topCampaignECPMs=294.30322265625&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=3.7273089885712&campaignPrdictedCtr=0.34096893668175&productIds=&recoPolicy=&request_timestamp=1661249908&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=0.0034096892923117&variantName=prod&modelUuid=77433289&networkSwitch=NONE&topDirectCampaign=1857226745&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=0&campaign_type=STANDARD&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=bbf18a3d229cdce690a141fc0b77a2d0&gender=M&age=28&ageRange=3&orderTypeV2=0&idfa=&s2sBidId=&imputationType=IMPUTED&amazonSdkPayload=&contentCreatorId=&scoringModel=prod&filteringModel=prod&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661249908&\"
\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"responded\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"error\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"inflated\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"impression\": { \"internal\": \[
\"http://money.dailyhunt.in/impression?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&partnerId=DH_APP&appId=226&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"https://impression.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"click\": { \"internal\": \[
\"https://money.dailyhunt.in/click?clientId=548000&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&reqTime=1661249908&billingTypeId=3&orderId=60632&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=&\_\_oadest=\"
\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"lpTimeSpent\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] } }, \"fallback\": { \"type\": \"IMAGE\", \"id\":
\"b276436a8fbfb5a764f056c31f7bfc82\", \"campaignId\": \"1688073950\",
\"bannerId\": \"1687409206\", \"content\": { \"image\":
\"http://acdn.newshuntads.com/daedalus-banners/1687409206/1661148424_65680_600x600.jpg\",
\"cta\": { \"url\":
\"https://money.dailyhunt.in/click?clientId=548000&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&reqTime=1661249908&billingTypeId=3&orderId=60632&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=&\_\_oadest=https%3A%2F%2Fapp.appsflyer.com%2Fcom.betway.sports-direct%3Fpid%3Dnewshunt_int%26af_r%3Dhttps%253A%252F%252Fbetway.com%252Fdownload%252Fandroid-sports%26af_siteid%3Ddailyhunt%26c%3Dsustenance%26af_dp%3Dbetwaysports%253A%252F%252F%26af_sub_siteid%3Dcard-pp1%26af_sub3%3D1661249908.0849%26af_c_id%3D\--CAMPAIGN_ID\--%26af_sub4%3Ds%25253Dbw210554%252526a%25253DDB3488520822146189%26af_ad_id%3D\--BANNER_ID\--%26af_sub2%3D548000%26af_click_lookback%3D7d%26trackerProvider%3Dappsflyer%26clickid%3D4b4d28ded973a24c29c566aa5f3766a8%26dhExtras%3D\--DH_EXTRAS\--%26advertising_id%3D8043aad5-507a-428d-a8d5-b09c98a46d68\",
\"data\": \"Download Now\", \"color\": \"#ffffff\", \"colorNight\":
\"#ffffff\", \"bgColor\": \"#52A1DD,#5282E7\", \"bgColorNight\":
\"#52A1DD,#5282E7\", \"browser\": \"INTERNAL\" } }, \"adFeedback\": {
\"label\": { \"color\": \"#000000\", \"colorNight\": \"#FFFFFF\",
\"bgColor\": \"#40000000\", \"bgColorNight\": \"#40000000\", \"data\":
\"Ad\", \"position\": \"TOP_RIGHT\" }, \"feedbackUrl\":
\"http://money.dailyhunt.in/data-api/adfeedback?bannerId=1131504889&campaignId=1857226745&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&city=\"
}, \"beacons\": { \"request\": { \"internal\": \[
\"http://money.dailyhunt.in/fallback?clientid=548000&req_time=23082022+15%3A48%3A28&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=realme&user_handset_model=rmx1921&user_id=&placement=card-pp1&user_app_ver=16.1.1.1&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-pp1&banner_id=1131504889&campaign_id=1857226745&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=765&price_range=mid&user_device_type=none&title=Betway_KP_SOB_1_Native_990x505++English&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&region=&mcc=&mnc=&lac=&cellid=&ip=10.52.134.5&adGroupId=5480006304a97413bf59.38480371&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=40&audienceSegments=2+5+1782+1854+1865+1873+11+13+12+l&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-az-52dk&locationSource=IP_DFP&pincode=&subSlot=pp1_1&bookedSubSlot=pp1_1&ab=CAMP&partnerId=DH_APP&deliverySlab=5.24&userDeliverySlab=3.3360824584961&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=294.30322265625&utmSource=&utmMedium=&utmCampaign=&appModelType=APPBRAND&preCalibratedDownfunnelProbability=0.037273090332747&downfunnelVariantName=prod&downfunnelModelUuid=77508219&appId=226&autoPlayPref=3&installDeliverySlab=0.30528157949448&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=2&topCampaignIds=1857226745%5E&topCampaignECPMs=294.30322265625&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=3.7273089885712&campaignPrdictedCtr=0.34096893668175&productIds=&recoPolicy=&request_timestamp=1661249908&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=0.0034096892923117&variantName=prod&modelUuid=77433289&networkSwitch=NONE&topDirectCampaign=1857226745&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=0&campaign_type=STANDARD&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=bbf18a3d229cdce690a141fc0b77a2d0&gender=M&age=28&ageRange=3&orderTypeV2=0&idfa=&s2sBidId=&imputationType=IMPUTED&amazonSdkPayload=&contentCreatorId=&scoringModel=prod&filteringModel=prod&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661249908&\"
\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"responded\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"error\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"inflated\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"impression\": { \"internal\": \[
\"http://money.dailyhunt.in/impression?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&partnerId=DH_APP&appId=226&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"https://impression.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"click\": { \"internal\": \[\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"lpTimeSpent\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] } } } } } \]

## Pgi Ads

### Empty Ad

[Empty Ad Mock
API](https://qa-money.newshunt.com/publicVibe/v2/pgi/empty.json)

Sample Response\[ { \"type\": \"EMPTY\", \"startIndex\": 1,
\"minDistance\": 4, \"id\": \"b276436a8fbfb5a764f056c31f7bfc82\",
\"campaignId\": \"1688073950\", \"bannerId\": \"1687409206\",
\"beacons\": { \"request\": { \"internal\": \[
\"http://money.dailyhunt.in/fallback?clientid=548000&req_time=23082022+15%3A48%3A28&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=realme&user_handset_model=rmx1921&user_id=&placement=card-pp1&user_app_ver=16.1.1.1&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-pp1&banner_id=1131504889&campaign_id=1857226745&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=765&price_range=mid&user_device_type=none&title=Betway_KP_SOB_1_Native_990x505++English&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&region=&mcc=&mnc=&lac=&cellid=&ip=10.52.134.5&adGroupId=5480006304a97413bf59.38480371&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=40&audienceSegments=2+5+1782+1854+1865+1873+11+13+12+l&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-az-52dk&locationSource=IP_DFP&pincode=&subSlot=pp1_1&bookedSubSlot=pp1_1&ab=CAMP&partnerId=DH_APP&deliverySlab=5.24&userDeliverySlab=3.3360824584961&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=294.30322265625&utmSource=&utmMedium=&utmCampaign=&appModelType=APPBRAND&preCalibratedDownfunnelProbability=0.037273090332747&downfunnelVariantName=prod&downfunnelModelUuid=77508219&appId=226&autoPlayPref=3&installDeliverySlab=0.30528157949448&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=2&topCampaignIds=1857226745%5E&topCampaignECPMs=294.30322265625&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=3.7273089885712&campaignPrdictedCtr=0.34096893668175&productIds=&recoPolicy=&request_timestamp=1661249908&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=0.0034096892923117&variantName=prod&modelUuid=77433289&networkSwitch=NONE&topDirectCampaign=1857226745&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=0&campaign_type=STANDARD&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=bbf18a3d229cdce690a141fc0b77a2d0&gender=M&age=28&ageRange=3&orderTypeV2=0&idfa=&s2sBidId=&imputationType=IMPUTED&amazonSdkPayload=&contentCreatorId=&scoringModel=prod&filteringModel=prod&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661249908&\"
\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"responded\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"inflated\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"impression\": { \"internal\": \[
\"http://money.dailyhunt.in/impression?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&partnerId=DH_APP&appId=226&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"https://impression.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] } } } \]

### HTML Ad

[HTML Mock
API](https://qa-money.newshunt.com/publicVibe/v2/pgi/html.json)

Sample Responsejson\[ { \"type\": \"HTML\", \"startIndex\": 1,
\"minDistance\": 4, \"noSkipTimer\": 5, \"id\":
\"7143f51a7795873e58fa7c5e94a5efa7\", \"campaignId\": \"1724741649\",
\"bannerId\": \"1358059656\", \"content\": { \"isVideo\": false,
\"showPlaybackControls\": false, \"data\": \"\<!doctype
html\>\\n\<html\>\\n\\n\<head\>\<meta name=\\\"viewport\\\"
content=\\\"initial-scale=1.0 user-scalable=no\\\" /\>\\n \<meta
charset=\\\"utf-8\\\"\>\\n \<meta name=\\\"viewport\\\"
content=\\\"width=device-width,
initial-scale=1\\\"\>\\n\</head\>\\n\<style type=\\\"text/css\\\"
media=\\\"screen\\\"\>\\n html,\\n body {\\n height: 100%\\n }\\n \\n
#parallax {\\n background-image:
url(http://qa-dae.dailyhunt.in/uploads/daedalus-banners/1358059656/1660113874_93147_720x543.jpg);\\n
height: 100%;\\n background-size: 100% 100%;\\n background-repeat:
no-repeat;\\n }\\n\\n .circle-text {\\n width: 7%;\\n z-index: 3;\\n
position: absolute;\\n display: none;\\n right: 5px;\\n top: 2px;\\n
font-family: Arial;\\n font-weight: 900;\\n font-size: +1.5em;\\n
}\\n\\n .circle-text:after {\\n content: \\\"\\\";\\n display: block;\\n
width: 100%;\\n height: 0;\\n padding-bottom: 100%;\\n
-moz-border-radius: 50%;\\n -webkit-border-radius: 50%;\\n
border-radius: 50%;\\n }\\n\\n .circle-text div {\\n float: left;\\n
width: 100%;\\n padding-top: 50%;\\n line-height: 1em;\\n margin-top:
-0.5em;\\n text-align: center;\\n }\\n\\n .circle-text.white div {\\n
color: black;\\n }\\n\\n .circle-text.white:after {\\n background:
white;\\n }\\n\</style\>\\n\\n\<body\>\\n \<div id=\\\"parallax\\\"
onclick=\\\"onImageClick()\\\"\>\</div\>\\n \<div class=\\\"circle-text
white\\\" id=\\\"circle-text\\\" onclick=\\\"onAdClose();\\\"\>\\n
\<div\>×\</div\>\\n \</div\>\\n\\n \<script\>\\n if (mraid.getState()
=== \'loading\') {\\n mraid.addEventListener(\'ready\', ready);\\n }
else {\\n ready();\\n }\\n\\n function ready() {\\n
onAdSetInListView();\\n mraid.useCustomClose(true);\\n }\\n\\n
mraid.addEventListener(\\\"stateChange\\\", function (state) {\\n if
(state == \\\"default\\\") {\\n onAdSetInListView();\\n } else if (state
== \\\"expanded\\\") {\\n onAdEngage();\\n }\\n });\\n\\n function
onImageClick() {\\n let state = mraid.getState();\\n if (state ===
\'loading\') {\\n mraid.addEventListener(\'ready\', ready);\\n } else if
(state === \'expanded\') {\\n
mraid.open(\\\"http://qa-dae.dailyhunt.in/daedalus-banners/htmlParallax/create?requirementId=1724741649&subTypeId=9\\\");\\n
} else if (state === \'default\') {\\n mraid.expand();\\n }\\n }\\n\\n
function onAdClose() {\\n mraid.close();\\n onAdSetInListView();\\n
}\\n\\n function onAdEngage() {\\n
document.getElementById(\\\"circle-text\\\").style.display =
\'block\';\\n }\\n\\n function onAdSetInListView() {\\n
document.getElementById(\\\"circle-text\\\").style.display =
\'none\';\\n }\\n \</script\>\\n\</body\>\\n\\n\</html\>\\n\", \"cta\":
{ \"proxy\": true, \"browser\": \"INTERNAL\", \"url\":
\"http://qa-dae.dailyhunt.in/daedalus-banners/htmlParallax/create?requirementId=1724741649&subTypeId=9\",
\"data\": \"Download Now\" }, \"tag\": { \"color\": \"#757575\",
\"colorNight\": \"#ffffff\", \"data\": \"Promoted\" } }, \"adFeedback\":
{ \"label\": { \"color\": \"#000000\", \"colorNight\": \"#FFFFFF\",
\"bgColor\": \"#40000000\", \"bgColorNight\": \"#40000000\", \"data\":
\"Ad\", \"position\": \"TOP_RIGHT\" }, \"feedbackUrl\":
\"http://money.dailyhunt.in/data-api/adfeedback?bannerId=1131504889&campaignId=1857226745&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&city=\"
}, \"beacons\": { \"request\": { \"internal\": \[
\"http://money.dailyhunt.in/fallback?clientid=548000&req_time=23082022+15%3A48%3A28&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=realme&user_handset_model=rmx1921&user_id=&placement=card-pp1&user_app_ver=16.1.1.1&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-pp1&banner_id=1131504889&campaign_id=1857226745&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=765&price_range=mid&user_device_type=none&title=Betway_KP_SOB_1_Native_990x505++English&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&region=&mcc=&mnc=&lac=&cellid=&ip=10.52.134.5&adGroupId=5480006304a97413bf59.38480371&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=40&audienceSegments=2+5+1782+1854+1865+1873+11+13+12+l&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-az-52dk&locationSource=IP_DFP&pincode=&subSlot=pp1_1&bookedSubSlot=pp1_1&ab=CAMP&partnerId=DH_APP&deliverySlab=5.24&userDeliverySlab=3.3360824584961&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=294.30322265625&utmSource=&utmMedium=&utmCampaign=&appModelType=APPBRAND&preCalibratedDownfunnelProbability=0.037273090332747&downfunnelVariantName=prod&downfunnelModelUuid=77508219&appId=226&autoPlayPref=3&installDeliverySlab=0.30528157949448&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=2&topCampaignIds=1857226745%5E&topCampaignECPMs=294.30322265625&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=3.7273089885712&campaignPrdictedCtr=0.34096893668175&productIds=&recoPolicy=&request_timestamp=1661249908&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=0.0034096892923117&variantName=prod&modelUuid=77433289&networkSwitch=NONE&topDirectCampaign=1857226745&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=0&campaign_type=STANDARD&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=bbf18a3d229cdce690a141fc0b77a2d0&gender=M&age=28&ageRange=3&orderTypeV2=0&idfa=&s2sBidId=&imputationType=IMPUTED&amazonSdkPayload=&contentCreatorId=&scoringModel=prod&filteringModel=prod&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661249908&\"
\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"responded\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"error\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"inflated\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"impression\": { \"internal\": \[
\"http://money.dailyhunt.in/impression?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&partnerId=DH_APP&appId=226&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"https://impression.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"click\": { \"internal\": \[\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"lpTimeSpent\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] } } } \]

### MRAID Zip Ad

MRAID Ad Mock API

Sample Responsejson\[ { \"type\": \"MRAID_ZIP\", \"startIndex\": 1,
\"minDistance\": 4, \"noSkipTimer\": 5, \"id\":
\"7143f51a7795873e58fa7c5e94a5efa7\", \"campaignId\": \"1724741649\",
\"bannerId\": \"1358059656\", \"content\": { \"isVideo\": false,
\"showPlaybackControls\": false, \"rootFile\": \"index.html\", \"data\":
\"https://qa-money.newshunt.com/daedalus-banners/3531/1626780922_66849\_.zip\"
\"cta\": { \"proxy\": true, \"browser\": \"INTERNAL\", \"url\":
\"http://qa-dae.dailyhunt.in/daedalus-banners/htmlParallax/create?requirementId=1724741649&subTypeId=9\",
\"data\": \"Download Now\" }, \"tag\": { \"color\": \"#757575\",
\"colorNight\": \"#ffffff\", \"data\": \"Promoted\" } }, \"adFeedback\":
{ \"label\": { \"color\": \"#000000\", \"colorNight\": \"#FFFFFF\",
\"bgColor\": \"#40000000\", \"bgColorNight\": \"#40000000\", \"data\":
\"Ad\", \"position\": \"TOP_RIGHT\" }, \"feedbackUrl\":
\"http://money.dailyhunt.in/data-api/adfeedback?bannerId=1131504889&campaignId=1857226745&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&city=\"
}, \"beacons\": { \"request\": { \"internal\": \[
\"http://money.dailyhunt.in/fallback?clientid=548000&req_time=23082022+15%3A48%3A28&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=realme&user_handset_model=rmx1921&user_id=&placement=card-pp1&user_app_ver=16.1.1.1&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-pp1&banner_id=1131504889&campaign_id=1857226745&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=765&price_range=mid&user_device_type=none&title=Betway_KP_SOB_1_Native_990x505++English&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&region=&mcc=&mnc=&lac=&cellid=&ip=10.52.134.5&adGroupId=5480006304a97413bf59.38480371&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=40&audienceSegments=2+5+1782+1854+1865+1873+11+13+12+l&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-az-52dk&locationSource=IP_DFP&pincode=&subSlot=pp1_1&bookedSubSlot=pp1_1&ab=CAMP&partnerId=DH_APP&deliverySlab=5.24&userDeliverySlab=3.3360824584961&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=294.30322265625&utmSource=&utmMedium=&utmCampaign=&appModelType=APPBRAND&preCalibratedDownfunnelProbability=0.037273090332747&downfunnelVariantName=prod&downfunnelModelUuid=77508219&appId=226&autoPlayPref=3&installDeliverySlab=0.30528157949448&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=2&topCampaignIds=1857226745%5E&topCampaignECPMs=294.30322265625&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=3.7273089885712&campaignPrdictedCtr=0.34096893668175&productIds=&recoPolicy=&request_timestamp=1661249908&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=0.0034096892923117&variantName=prod&modelUuid=77433289&networkSwitch=NONE&topDirectCampaign=1857226745&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=0&campaign_type=STANDARD&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=bbf18a3d229cdce690a141fc0b77a2d0&gender=M&age=28&ageRange=3&orderTypeV2=0&idfa=&s2sBidId=&imputationType=IMPUTED&amazonSdkPayload=&contentCreatorId=&scoringModel=prod&filteringModel=prod&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661249908&\"
\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"responded\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"error\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"inflated\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"impression\": { \"internal\": \[
\"http://money.dailyhunt.in/impression?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&partnerId=DH_APP&appId=226&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"https://impression.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"click\": { \"internal\": \[\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"lpTimeSpent\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] } } } \]

### Image Ad

[Image Ad Mock
API](https://qa-money.newshunt.com/publicVibe/v2/pgi/image.json)

Sample Responsejson\[ { \"type\": \"IMAGE\", \"startIndex\": 1,
\"minDistance\": 4, \"noSkipTimer\": 5, \"id\":
\"b276436a8fbfb5a764f056c31f7bfc82\", \"campaignId\": \"1688073950\",
\"bannerId\": \"1687409206\", \"content\": { \"image\": { \"url\":
\"http://acdn.newshuntads.com/daedalus-banners/1687409206/1661148424_65680_600x600.jpg\",
\"width\": 329, \"height\": 84 }, \"cta\": { \"url\":
\"https://money.dailyhunt.in/click?clientId=548000&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&reqTime=1661249908&billingTypeId=3&orderId=60632&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=&\_\_oadest=https%3A%2F%2Fapp.appsflyer.com%2Fcom.betway.sports-direct%3Fpid%3Dnewshunt_int%26af_r%3Dhttps%253A%252F%252Fbetway.com%252Fdownload%252Fandroid-sports%26af_siteid%3Ddailyhunt%26c%3Dsustenance%26af_dp%3Dbetwaysports%253A%252F%252F%26af_sub_siteid%3Dcard-pp1%26af_sub3%3D1661249908.0849%26af_c_id%3D\--CAMPAIGN_ID\--%26af_sub4%3Ds%25253Dbw210554%252526a%25253DDB3488520822146189%26af_ad_id%3D\--BANNER_ID\--%26af_sub2%3D548000%26af_click_lookback%3D7d%26trackerProvider%3Dappsflyer%26clickid%3D4b4d28ded973a24c29c566aa5f3766a8%26dhExtras%3D\--DH_EXTRAS\--%26advertising_id%3D8043aad5-507a-428d-a8d5-b09c98a46d68\",
\"data\": \"Download Now\", \"color\": \"#ffffff\", \"colorNight\":
\"#ffffff\", \"bgColor\": \"#52A1DD,#5282E7\", \"bgColorNight\":
\"#52A1DD,#5282E7\", \"browser\": \"INTERNAL\" } }, \"adFeedback\": {
\"label\": { \"color\": \"#000000\", \"colorNight\": \"#FFFFFF\",
\"bgColor\": \"#40000000\", \"bgColorNight\": \"#40000000\", \"data\":
\"Ad\", \"position\": \"TOP_RIGHT\" }, \"feedbackUrl\":
\"http://money.dailyhunt.in/data-api/adfeedback?bannerId=1131504889&campaignId=1857226745&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&city=\"
}, \"beacons\": { \"request\": { \"internal\": \[
\"http://money.dailyhunt.in/fallback?clientid=548000&req_time=23082022+15%3A48%3A28&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=realme&user_handset_model=rmx1921&user_id=&placement=card-pp1&user_app_ver=16.1.1.1&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-pp1&banner_id=1131504889&campaign_id=1857226745&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=765&price_range=mid&user_device_type=none&title=Betway_KP_SOB_1_Native_990x505++English&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&region=&mcc=&mnc=&lac=&cellid=&ip=10.52.134.5&adGroupId=5480006304a97413bf59.38480371&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=40&audienceSegments=2+5+1782+1854+1865+1873+11+13+12+l&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-az-52dk&locationSource=IP_DFP&pincode=&subSlot=pp1_1&bookedSubSlot=pp1_1&ab=CAMP&partnerId=DH_APP&deliverySlab=5.24&userDeliverySlab=3.3360824584961&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=294.30322265625&utmSource=&utmMedium=&utmCampaign=&appModelType=APPBRAND&preCalibratedDownfunnelProbability=0.037273090332747&downfunnelVariantName=prod&downfunnelModelUuid=77508219&appId=226&autoPlayPref=3&installDeliverySlab=0.30528157949448&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=2&topCampaignIds=1857226745%5E&topCampaignECPMs=294.30322265625&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=3.7273089885712&campaignPrdictedCtr=0.34096893668175&productIds=&recoPolicy=&request_timestamp=1661249908&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=0.0034096892923117&variantName=prod&modelUuid=77433289&networkSwitch=NONE&topDirectCampaign=1857226745&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=0&campaign_type=STANDARD&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=bbf18a3d229cdce690a141fc0b77a2d0&gender=M&age=28&ageRange=3&orderTypeV2=0&idfa=&s2sBidId=&imputationType=IMPUTED&amazonSdkPayload=&contentCreatorId=&scoringModel=prod&filteringModel=prod&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661249908&\"
\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"responded\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"error\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"inflated\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"impression\": { \"internal\": \[
\"http://money.dailyhunt.in/impression?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&partnerId=DH_APP&appId=226&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"https://impression.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"click\": { \"internal\": \[\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"lpTimeSpent\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] } } } \]

### Native Carousel Ad

[Native Carousel Ad Mock
API](https://qa-money.newshunt.com/publicVibe/v2/pgi/native_carousel.json)

Sample Responsejson\[ { \"type\": \"NATIVE\", \"template\":
\"NATIVE_CAROUSEL\", \"startIndex\": 1, \"minDistance\": 4, \"id\":
\"4b4d28ded973a24c29c566aa5f3766a8\", \"campaignId\": \"1857226745\",
\"bannerId\": \"1131504889\", \"content\": { \"bgColor\": \"#ffffff\",
\"bgColorNight\": \"#000000\", \"brand\": { \"logo\":
\"https://icon-library.com/images/next-button-icon/next-button-icon-19.jpg\",
\"color\": \"#000000\", \"colorNight\": \"#ffffff\", \"data\":
\"Freshmart\" }, \"tag\": { \"color\": \"#757575\", \"colorNight\":
\"#ffffff\", \"data\": \"Promoted\" }, \"items\": \[ { \"image\": {
\"url\":
\"http://acdn.newshuntads.com/daedalus-banners/1687409206/1661148424_65680_600x600.jpg\",
\"width\": 329, \"height\": 84 }, \"title\": { \"color\": \"#000000\",
\"colorNight\": \"#ffffff\", \"bgColor\": \"#373737cc\",
\"bgColorNight\": \"#373737cc\", \"data\": \"Your neighbourhood grocer.
A collection of local brands, here for you.\" }, \"cta\": { \"url\":
\"https://money.dailyhunt.in/click?clientId=548000&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&reqTime=1661249908&billingTypeId=3&orderId=60632&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=&\_\_oadest=https%3A%2F%2Fapp.appsflyer.com%2Fcom.betway.sports-direct%3Fpid%3Dnewshunt_int%26af_r%3Dhttps%253A%252F%252Fbetway.com%252Fdownload%252Fandroid-sports%26af_siteid%3Ddailyhunt%26c%3Dsustenance%26af_dp%3Dbetwaysports%253A%252F%252F%26af_sub_siteid%3Dcard-pp1%26af_sub3%3D1661249908.0849%26af_c_id%3D\--CAMPAIGN_ID\--%26af_sub4%3Ds%25253Dbw210554%252526a%25253DDB3488520822146189%26af_ad_id%3D\--BANNER_ID\--%26af_sub2%3D548000%26af_click_lookback%3D7d%26trackerProvider%3Dappsflyer%26clickid%3D4b4d28ded973a24c29c566aa5f3766a8%26dhExtras%3D\--DH_EXTRAS\--%26advertising_id%3D8043aad5-507a-428d-a8d5-b09c98a46d68\",
\"color\": \"#ffffff\", \"colorNight\": \"#ffffff\", \"bgColor\":
\"#000000\", \"bgColorNight\": \"#000000\", \"browser\": \"INTERNAL\" },
\"beacons\": { \"carouselItemView\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=CAROUSEL_ITEM_VIEW&itemId=2345&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=CAROUSEL_ITEM_VIEW&itemId=2346&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] } } }, { \"image\": { \"url\":
\"http://acdn.newshuntads.com/daedalus-banners/1687409206/1661148424_65680_600x600.jpg\",
\"width\": 329, \"height\": 84 }, \"title\": { \"color\": \"#000000\",
\"colorNight\": \"#ffffff\", \"bgColor\": \"#373737cc\",
\"bgColorNight\": \"#373737cc\", \"data\": \"Your neighbourhood grocer.
A collection of local brands, here for you.\" }, \"cta\": { \"url\":
\"https://money.dailyhunt.in/click?clientId=548000&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&reqTime=1661249908&billingTypeId=3&orderId=60632&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=&\_\_oadest=https%3A%2F%2Fapp.appsflyer.com%2Fcom.betway.sports-direct%3Fpid%3Dnewshunt_int%26af_r%3Dhttps%253A%252F%252Fbetway.com%252Fdownload%252Fandroid-sports%26af_siteid%3Ddailyhunt%26c%3Dsustenance%26af_dp%3Dbetwaysports%253A%252F%252F%26af_sub_siteid%3Dcard-pp1%26af_sub3%3D1661249908.0849%26af_c_id%3D\--CAMPAIGN_ID\--%26af_sub4%3Ds%25253Dbw210554%252526a%25253DDB3488520822146189%26af_ad_id%3D\--BANNER_ID\--%26af_sub2%3D548000%26af_click_lookback%3D7d%26trackerProvider%3Dappsflyer%26clickid%3D4b4d28ded973a24c29c566aa5f3766a8%26dhExtras%3D\--DH_EXTRAS\--%26advertising_id%3D8043aad5-507a-428d-a8d5-b09c98a46d68\",
\"color\": \"#ffffff\", \"colorNight\": \"#ffffff\", \"bgColor\":
\"#000000\", \"bgColorNight\": \"#000000\", \"browser\": \"INTERNAL\" },
\"beacons\": { \"carouselItemView\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=CAROUSEL_ITEM_VIEW&itemId=2345&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=CAROUSEL_ITEM_VIEW&itemId=2346&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] } } } \] }, \"adFeedback\": { \"label\": { \"color\": \"#000000\",
\"colorNight\": \"#FFFFFF\", \"bgColor\": \"#40000000\",
\"bgColorNight\": \"#40000000\", \"data\": \"Ad\", \"position\":
\"TOP_RIGHT\" }, \"feedbackUrl\":
\"http://money.dailyhunt.in/data-api/adfeedback?bannerId=1131504889&campaignId=1857226745&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&city=\"
}, \"beacons\": { \"request\": { \"internal\": \[
\"http://money.dailyhunt.in/fallback?clientid=548000&req_time=23082022+15%3A48%3A28&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=realme&user_handset_model=rmx1921&user_id=&placement=card-pp1&user_app_ver=16.1.1.1&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-pp1&banner_id=1131504889&campaign_id=1857226745&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=765&price_range=mid&user_device_type=none&title=Betway_KP_SOB_1_Native_990x505++English&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&region=&mcc=&mnc=&lac=&cellid=&ip=10.52.134.5&adGroupId=5480006304a97413bf59.38480371&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=40&audienceSegments=2+5+1782+1854+1865+1873+11+13+12+l&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-az-52dk&locationSource=IP_DFP&pincode=&subSlot=pp1_1&bookedSubSlot=pp1_1&ab=CAMP&partnerId=DH_APP&deliverySlab=5.24&userDeliverySlab=3.3360824584961&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=294.30322265625&utmSource=&utmMedium=&utmCampaign=&appModelType=APPBRAND&preCalibratedDownfunnelProbability=0.037273090332747&downfunnelVariantName=prod&downfunnelModelUuid=77508219&appId=226&autoPlayPref=3&installDeliverySlab=0.30528157949448&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=2&topCampaignIds=1857226745%5E&topCampaignECPMs=294.30322265625&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=3.7273089885712&campaignPrdictedCtr=0.34096893668175&productIds=&recoPolicy=&request_timestamp=1661249908&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=0.0034096892923117&variantName=prod&modelUuid=77433289&networkSwitch=NONE&topDirectCampaign=1857226745&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=0&campaign_type=STANDARD&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=bbf18a3d229cdce690a141fc0b77a2d0&gender=M&age=28&ageRange=3&orderTypeV2=0&idfa=&s2sBidId=&imputationType=IMPUTED&amazonSdkPayload=&contentCreatorId=&scoringModel=prod&filteringModel=prod&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661249908&\"
\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"responded\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"error\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"inflated\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"impression\": { \"internal\": \[
\"http://money.dailyhunt.in/impression?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&partnerId=DH_APP&appId=226&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"https://impression.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"click\": { \"internal\": \[\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"lpTimeSpent\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] } } } \]

### Native Fullscreen Ad

[Native Fullscreen Mock
API](http://qa-money.newshunt.com/publicVibe/v2/pgi/native_fullscreen.json)

Sample Responsejson\[ { \"type\": \"NATIVE\", \"template\":
\"NATIVE_FULLSCREEN\", \"startIndex\": 1, \"minDistance\": 4, \"id\":
\"4b4d28ded973a24c29c566aa5f3766a8\", \"campaignId\": \"1857226745\",
\"bannerId\": \"1131504889\", \"content\": { \"bgColor\": \"#ffffff\",
\"bgColorNight\": \"#000000\", \"image\": { \"url\":
\"http://acdn.newshuntads.com/daedalus-banners/1687409206/1661148424_65680_600x600.jpg\",
\"width\": 329, \"height\": 84 }, \"brand\": { \"logo\":
\"https://icon-library.com/images/next-button-icon/next-button-icon-19.jpg\",
\"color\": \"#000000\", \"colorNight\": \"#ffffff\", \"data\":
\"Freshmart\" }, \"title\": { \"color\": \"#000000\", \"colorNight\":
\"#ffffff\", \"data\": \"Your neighbourhood grocer. A collection of
local brands, here for you.\" }, \"description\": { \"color\":
\"#545454\", \"colorNight\": \"#ffffff\", \"data\": \"Your neighbourhood
grocer. A collection of local brands, here for you. Your neighbourhood
grocer. A collection of local brands, here for you.Your neighbourhood
grocer. A collection of local brands\" }, \"cta\": { \"url\":
\"https://money.dailyhunt.in/click?clientId=548000&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&reqTime=1661249908&billingTypeId=3&orderId=60632&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=&\_\_oadest=https%3A%2F%2Fapp.appsflyer.com%2Fcom.betway.sports-direct%3Fpid%3Dnewshunt_int%26af_r%3Dhttps%253A%252F%252Fbetway.com%252Fdownload%252Fandroid-sports%26af_siteid%3Ddailyhunt%26c%3Dsustenance%26af_dp%3Dbetwaysports%253A%252F%252F%26af_sub_siteid%3Dcard-pp1%26af_sub3%3D1661249908.0849%26af_c_id%3D\--CAMPAIGN_ID\--%26af_sub4%3Ds%25253Dbw210554%252526a%25253DDB3488520822146189%26af_ad_id%3D\--BANNER_ID\--%26af_sub2%3D548000%26af_click_lookback%3D7d%26trackerProvider%3Dappsflyer%26clickid%3D4b4d28ded973a24c29c566aa5f3766a8%26dhExtras%3D\--DH_EXTRAS\--%26advertising_id%3D8043aad5-507a-428d-a8d5-b09c98a46d68\",
\"data\": \"Download Now\", \"color\": \"#4caf79\", \"colorNight\":
\"#ffffff\", \"bgColor\": \"#52A1DD,#5282E7\", \"bgColorNight\":
\"#52A1DD,#5282E7\", \"browser\": \"INTERNAL\" }, \"tag\": { \"color\":
\"#757575\", \"colorNight\": \"#ffffff\", \"data\": \"Promoted\" } },
\"adFeedback\": { \"label\": { \"color\": \"#000000\", \"colorNight\":
\"#FFFFFF\", \"bgColor\": \"#40000000\", \"bgColorNight\":
\"#40000000\", \"data\": \"Ad\", \"position\": \"TOP_RIGHT\" },
\"feedbackUrl\":
\"http://money.dailyhunt.in/data-api/adfeedback?bannerId=1131504889&campaignId=1857226745&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&city=\"
}, \"beacons\": { \"request\": { \"internal\": \[
\"http://money.dailyhunt.in/fallback?clientid=548000&req_time=23082022+15%3A48%3A28&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=realme&user_handset_model=rmx1921&user_id=&placement=card-pp1&user_app_ver=16.1.1.1&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-pp1&banner_id=1131504889&campaign_id=1857226745&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=765&price_range=mid&user_device_type=none&title=Betway_KP_SOB_1_Native_990x505++English&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&region=&mcc=&mnc=&lac=&cellid=&ip=10.52.134.5&adGroupId=5480006304a97413bf59.38480371&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=40&audienceSegments=2+5+1782+1854+1865+1873+11+13+12+l&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-az-52dk&locationSource=IP_DFP&pincode=&subSlot=pp1_1&bookedSubSlot=pp1_1&ab=CAMP&partnerId=DH_APP&deliverySlab=5.24&userDeliverySlab=3.3360824584961&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=294.30322265625&utmSource=&utmMedium=&utmCampaign=&appModelType=APPBRAND&preCalibratedDownfunnelProbability=0.037273090332747&downfunnelVariantName=prod&downfunnelModelUuid=77508219&appId=226&autoPlayPref=3&installDeliverySlab=0.30528157949448&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=2&topCampaignIds=1857226745%5E&topCampaignECPMs=294.30322265625&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=3.7273089885712&campaignPrdictedCtr=0.34096893668175&productIds=&recoPolicy=&request_timestamp=1661249908&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=0.0034096892923117&variantName=prod&modelUuid=77433289&networkSwitch=NONE&topDirectCampaign=1857226745&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=0&campaign_type=STANDARD&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=bbf18a3d229cdce690a141fc0b77a2d0&gender=M&age=28&ageRange=3&orderTypeV2=0&idfa=&s2sBidId=&imputationType=IMPUTED&amazonSdkPayload=&contentCreatorId=&scoringModel=prod&filteringModel=prod&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661249908&\"
\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"responded\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"error\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"inflated\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"impression\": { \"internal\": \[
\"http://money.dailyhunt.in/impression?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&partnerId=DH_APP&appId=226&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"https://impression.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"click\": { \"internal\": \[\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"lpTimeSpent\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] } } } \]

### Native Image Ad

[Native Image Mock
API](https://qa-money.newshunt.com/publicVibe/v2/pgi/native_image.json)

Sample Responsejson\[ { \"type\": \"NATIVE\", \"template\":
\"NATIVE_IMAGE\", \"startIndex\": 1, \"minDistance\": 4, \"id\":
\"4b4d28ded973a24c29c566aa5f3766a8\", \"campaignId\": \"1857226745\",
\"bannerId\": \"1131504889\", \"content\": { \"bgColor\": \"#ffffff\",
\"bgColorNight\": \"#000000\", \"image\": { \"url\":
\"http://acdn.newshuntads.com/daedalus-banners/1687409206/1661148424_65680_600x600.jpg\",
\"width\": 329, \"height\": 84 }, \"brand\": { \"logo\":
\"https://icon-library.com/images/next-button-icon/next-button-icon-19.jpg\",
\"color\": \"#000000\", \"colorNight\": \"#ffffff\", \"data\":
\"Freshmart\" }, \"title\": { \"color\": \"#000000\", \"colorNight\":
\"#ffffff\", \"data\": \"Your neighbourhood grocer. A collection of
local brands, here for you.\" }, \"description\": { \"color\":
\"#545454\", \"colorNight\": \"#ffffff\", \"data\": \"Your neighbourhood
grocer. A collection of local brands, here for you. Your neighbourhood
grocer. A collection of local brands, here for you.Your neighbourhood
grocer. A collection of local brands\" }, \"cta\": { \"url\":
\"https://money.dailyhunt.in/click?clientId=548000&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&reqTime=1661249908&billingTypeId=3&orderId=60632&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=&\_\_oadest=https%3A%2F%2Fapp.appsflyer.com%2Fcom.betway.sports-direct%3Fpid%3Dnewshunt_int%26af_r%3Dhttps%253A%252F%252Fbetway.com%252Fdownload%252Fandroid-sports%26af_siteid%3Ddailyhunt%26c%3Dsustenance%26af_dp%3Dbetwaysports%253A%252F%252F%26af_sub_siteid%3Dcard-pp1%26af_sub3%3D1661249908.0849%26af_c_id%3D\--CAMPAIGN_ID\--%26af_sub4%3Ds%25253Dbw210554%252526a%25253DDB3488520822146189%26af_ad_id%3D\--BANNER_ID\--%26af_sub2%3D548000%26af_click_lookback%3D7d%26trackerProvider%3Dappsflyer%26clickid%3D4b4d28ded973a24c29c566aa5f3766a8%26dhExtras%3D\--DH_EXTRAS\--%26advertising_id%3D8043aad5-507a-428d-a8d5-b09c98a46d68\",
\"data\": \"Download Now\", \"color\": \"#4caf79\", \"colorNight\":
\"#ffffff\", \"bgColor\": \"#52A1DD,#5282E7\", \"bgColorNight\":
\"#52A1DD,#5282E7\", \"browser\": \"INTERNAL\" }, \"tag\": { \"color\":
\"#757575\", \"colorNight\": \"#ffffff\", \"data\": \"Promoted\" } },
\"adFeedback\": { \"label\": { \"color\": \"#000000\", \"colorNight\":
\"#FFFFFF\", \"bgColor\": \"#40000000\", \"bgColorNight\":
\"#40000000\", \"data\": \"Ad\", \"position\": \"TOP_RIGHT\" },
\"feedbackUrl\":
\"http://money.dailyhunt.in/data-api/adfeedback?bannerId=1131504889&campaignId=1857226745&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&city=\"
}, \"beacons\": { \"request\": { \"internal\": \[
\"http://money.dailyhunt.in/fallback?clientid=548000&req_time=23082022+15%3A48%3A28&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=realme&user_handset_model=rmx1921&user_id=&placement=card-pp1&user_app_ver=16.1.1.1&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-pp1&banner_id=1131504889&campaign_id=1857226745&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=765&price_range=mid&user_device_type=none&title=Betway_KP_SOB_1_Native_990x505++English&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&region=&mcc=&mnc=&lac=&cellid=&ip=10.52.134.5&adGroupId=5480006304a97413bf59.38480371&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=40&audienceSegments=2+5+1782+1854+1865+1873+11+13+12+l&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-az-52dk&locationSource=IP_DFP&pincode=&subSlot=pp1_1&bookedSubSlot=pp1_1&ab=CAMP&partnerId=DH_APP&deliverySlab=5.24&userDeliverySlab=3.3360824584961&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=294.30322265625&utmSource=&utmMedium=&utmCampaign=&appModelType=APPBRAND&preCalibratedDownfunnelProbability=0.037273090332747&downfunnelVariantName=prod&downfunnelModelUuid=77508219&appId=226&autoPlayPref=3&installDeliverySlab=0.30528157949448&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=2&topCampaignIds=1857226745%5E&topCampaignECPMs=294.30322265625&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=3.7273089885712&campaignPrdictedCtr=0.34096893668175&productIds=&recoPolicy=&request_timestamp=1661249908&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=0.0034096892923117&variantName=prod&modelUuid=77433289&networkSwitch=NONE&topDirectCampaign=1857226745&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=0&campaign_type=STANDARD&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=bbf18a3d229cdce690a141fc0b77a2d0&gender=M&age=28&ageRange=3&orderTypeV2=0&idfa=&s2sBidId=&imputationType=IMPUTED&amazonSdkPayload=&contentCreatorId=&scoringModel=prod&filteringModel=prod&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661249908&\"
\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"responded\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"error\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"inflated\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"impression\": { \"internal\": \[
\"http://money.dailyhunt.in/impression?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&partnerId=DH_APP&appId=226&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"https://impression.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"click\": { \"internal\": \[\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"lpTimeSpent\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] } } } \]

### Native Portrait Ad

[Native Portrait Mock
API](http://qa-money.newshunt.com/publicVibe/v2/pgi/native_portrait.json)

Sample Responsejson\[ { \"type\": \"NATIVE\", \"template\":
\"NATIVE_PORTRAIT\", \"startIndex\": 1, \"minDistance\": 4, \"id\":
\"4b4d28ded973a24c29c566aa5f3766a8\", \"campaignId\": \"1857226745\",
\"bannerId\": \"1131504889\", \"content\": { \"bgColor\": \"#ffffff\",
\"bgColorNight\": \"#000000\", \"image\": { \"url\":
\"http://acdn.newshuntads.com/daedalus-banners/1687409206/1661148424_65680_600x600.jpg\",
\"width\": 329, \"height\": 84 }, \"brand\": { \"logo\":
\"https://icon-library.com/images/next-button-icon/next-button-icon-19.jpg\",
\"color\": \"#000000\", \"colorNight\": \"#ffffff\", \"data\":
\"Freshmart\" }, \"title\": { \"color\": \"#000000\", \"colorNight\":
\"#ffffff\", \"data\": \"Your neighbourhood grocer. A collection of
local brands, here for you.\" }, \"description\": { \"color\":
\"#545454\", \"colorNight\": \"#ffffff\", \"data\": \"Your neighbourhood
grocer. A collection of local brands, here for you. Your neighbourhood
grocer. A collection of local brands, here for you.Your neighbourhood
grocer. A collection of local brands\" }, \"cta\": { \"url\":
\"https://money.dailyhunt.in/click?clientId=548000&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&reqTime=1661249908&billingTypeId=3&orderId=60632&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=&\_\_oadest=https%3A%2F%2Fapp.appsflyer.com%2Fcom.betway.sports-direct%3Fpid%3Dnewshunt_int%26af_r%3Dhttps%253A%252F%252Fbetway.com%252Fdownload%252Fandroid-sports%26af_siteid%3Ddailyhunt%26c%3Dsustenance%26af_dp%3Dbetwaysports%253A%252F%252F%26af_sub_siteid%3Dcard-pp1%26af_sub3%3D1661249908.0849%26af_c_id%3D\--CAMPAIGN_ID\--%26af_sub4%3Ds%25253Dbw210554%252526a%25253DDB3488520822146189%26af_ad_id%3D\--BANNER_ID\--%26af_sub2%3D548000%26af_click_lookback%3D7d%26trackerProvider%3Dappsflyer%26clickid%3D4b4d28ded973a24c29c566aa5f3766a8%26dhExtras%3D\--DH_EXTRAS\--%26advertising_id%3D8043aad5-507a-428d-a8d5-b09c98a46d68\",
\"data\": \"Download Now\", \"color\": \"#4caf79\", \"colorNight\":
\"#ffffff\", \"bgColor\": \"#52A1DD,#5282E7\", \"bgColorNight\":
\"#52A1DD,#5282E7\", \"browser\": \"INTERNAL\" }, \"tag\": { \"color\":
\"#757575\", \"colorNight\": \"#ffffff\", \"data\": \"Promoted\" } },
\"adFeedback\": { \"label\": { \"color\": \"#000000\", \"colorNight\":
\"#FFFFFF\", \"bgColor\": \"#40000000\", \"bgColorNight\":
\"#40000000\", \"data\": \"Ad\", \"position\": \"TOP_RIGHT\" },
\"feedbackUrl\":
\"http://money.dailyhunt.in/data-api/adfeedback?bannerId=1131504889&campaignId=1857226745&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&city=\"
}, \"beacons\": { \"request\": { \"internal\": \[
\"http://money.dailyhunt.in/fallback?clientid=548000&req_time=23082022+15%3A48%3A28&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=realme&user_handset_model=rmx1921&user_id=&placement=card-pp1&user_app_ver=16.1.1.1&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-pp1&banner_id=1131504889&campaign_id=1857226745&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=765&price_range=mid&user_device_type=none&title=Betway_KP_SOB_1_Native_990x505++English&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&region=&mcc=&mnc=&lac=&cellid=&ip=10.52.134.5&adGroupId=5480006304a97413bf59.38480371&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=40&audienceSegments=2+5+1782+1854+1865+1873+11+13+12+l&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-az-52dk&locationSource=IP_DFP&pincode=&subSlot=pp1_1&bookedSubSlot=pp1_1&ab=CAMP&partnerId=DH_APP&deliverySlab=5.24&userDeliverySlab=3.3360824584961&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=294.30322265625&utmSource=&utmMedium=&utmCampaign=&appModelType=APPBRAND&preCalibratedDownfunnelProbability=0.037273090332747&downfunnelVariantName=prod&downfunnelModelUuid=77508219&appId=226&autoPlayPref=3&installDeliverySlab=0.30528157949448&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=2&topCampaignIds=1857226745%5E&topCampaignECPMs=294.30322265625&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=3.7273089885712&campaignPrdictedCtr=0.34096893668175&productIds=&recoPolicy=&request_timestamp=1661249908&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=0.0034096892923117&variantName=prod&modelUuid=77433289&networkSwitch=NONE&topDirectCampaign=1857226745&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=0&campaign_type=STANDARD&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=bbf18a3d229cdce690a141fc0b77a2d0&gender=M&age=28&ageRange=3&orderTypeV2=0&idfa=&s2sBidId=&imputationType=IMPUTED&amazonSdkPayload=&contentCreatorId=&scoringModel=prod&filteringModel=prod&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661249908&\"
\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"responded\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"error\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"inflated\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"impression\": { \"internal\": \[
\"http://money.dailyhunt.in/impression?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&partnerId=DH_APP&appId=226&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"https://impression.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"click\": { \"internal\": \[\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"lpTimeSpent\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] } } } \]

### SDK Ad

[SDK Ad Mock
API](https://qa-money.newshunt.com/publicVibe/v2/pgi/sdk.json)

Sample Responsejson\[ { \"type\": \"SDK\", \"startIndex\": 1,
\"minDistance\": 4, \"noSkipTimer\": 5, \"id\":
\"b276436a8fbfb5a764f056c31f7bfc82\", \"campaignId\": \"1688073950\",
\"bannerId\": \"1687409206\", \"content\": { \"network\": {
\"identifier\": \"GOOGLE\", \"adunitId\":
\"/83414793/Common_PageInsert\", \"extras\": \"c_language:en,c_ecpm:
500,c_userIp: 10.52.134.4,clientId:
155362483,c_uniqueId:b095ee12c812399361112b4f20c40c44,c_city:\--LOCATION_CITY\--,topicKey:NULL,npKey:nh-headlines,c_connectionSpeed:FAST,ConnectionType:w,c_placementId:storypage,utm_source:\--UTM_SOURCE\--,Autoplay:
3\" }, \"cta\": { \"color\": \"#ffffff\", \"colorNight\": \"#ffffff\",
\"bgColor\": \"#52A1DD,#5282E7\", \"bgColorNight\": \"#52A1DD,#5282E7\",
\"browser\": \"INTERNAL\" } }, \"adFeedback\": { \"label\": { \"color\":
\"#000000\", \"colorNight\": \"#FFFFFF\", \"bgColor\": \"#40000000\",
\"bgColorNight\": \"#40000000\", \"data\": \"Ad\", \"position\":
\"TOP_RIGHT\" } }, \"beacons\": { \"request\": { \"internal\": \[
\"http://money.dailyhunt.in/fallback?clientid=548000&req_time=23082022+15%3A48%3A28&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=realme&user_handset_model=rmx1921&user_id=&placement=card-pp1&user_app_ver=16.1.1.1&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-pp1&banner_id=1131504889&campaign_id=1857226745&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=765&price_range=mid&user_device_type=none&title=Betway_KP_SOB_1_Native_990x505++English&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&region=&mcc=&mnc=&lac=&cellid=&ip=10.52.134.5&adGroupId=5480006304a97413bf59.38480371&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=40&audienceSegments=2+5+1782+1854+1865+1873+11+13+12+l&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-az-52dk&locationSource=IP_DFP&pincode=&subSlot=pp1_1&bookedSubSlot=pp1_1&ab=CAMP&partnerId=DH_APP&deliverySlab=5.24&userDeliverySlab=3.3360824584961&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=294.30322265625&utmSource=&utmMedium=&utmCampaign=&appModelType=APPBRAND&preCalibratedDownfunnelProbability=0.037273090332747&downfunnelVariantName=prod&downfunnelModelUuid=77508219&appId=226&autoPlayPref=3&installDeliverySlab=0.30528157949448&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=2&topCampaignIds=1857226745%5E&topCampaignECPMs=294.30322265625&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=3.7273089885712&campaignPrdictedCtr=0.34096893668175&productIds=&recoPolicy=&request_timestamp=1661249908&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=0.0034096892923117&variantName=prod&modelUuid=77433289&networkSwitch=NONE&topDirectCampaign=1857226745&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=0&campaign_type=STANDARD&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=bbf18a3d229cdce690a141fc0b77a2d0&gender=M&age=28&ageRange=3&orderTypeV2=0&idfa=&s2sBidId=&imputationType=IMPUTED&amazonSdkPayload=&contentCreatorId=&scoringModel=prod&filteringModel=prod&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661249908&\"
\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"responded\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"error\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"inflated\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"impression\": { \"internal\": \[
\"http://money.dailyhunt.in/impression?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&partnerId=DH_APP&appId=226&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"https://impression.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"click\": { \"internal\": \[
\"https://money.dailyhunt.in/click?clientId=548000&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&reqTime=1661249908&billingTypeId=3&orderId=60632&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=&\_\_oadest=\"
\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"lpTimeSpent\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] } }, \"fallback\": { \"type\": \"SDK\", \"startIndex\": 1,
\"minDistance\": 4, \"noSkipTimer\": 5, \"id\":
\"b276436a8fbfb5a764f056c31f7bfc82\", \"campaignId\": \"1688073950\",
\"bannerId\": \"1687409206\", \"content\": { \"network\": {
\"identifier\": \"FACEBOOK\", \"adunitId\":
\"131285656905938_1204641569570336\" }, \"cta\": { \"color\":
\"#ffffff\", \"colorNight\": \"#ffffff\", \"bgColor\":
\"#52A1DD,#5282E7\", \"bgColorNight\": \"#52A1DD,#5282E7\", \"browser\":
\"INTERNAL\" } }, \"adFeedback\": { \"label\": { \"color\": \"#000000\",
\"colorNight\": \"#FFFFFF\", \"bgColor\": \"#40000000\",
\"bgColorNight\": \"#40000000\", \"data\": \"Ad\", \"position\":
\"TOP_RIGHT\" } }, \"beacons\": { \"request\": { \"internal\": \[
\"http://money.dailyhunt.in/fallback?clientid=548000&req_time=23082022+15%3A48%3A28&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=realme&user_handset_model=rmx1921&user_id=&placement=card-pp1&user_app_ver=16.1.1.1&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-pp1&banner_id=1131504889&campaign_id=1857226745&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=765&price_range=mid&user_device_type=none&title=Betway_KP_SOB_1_Native_990x505++English&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&region=&mcc=&mnc=&lac=&cellid=&ip=10.52.134.5&adGroupId=5480006304a97413bf59.38480371&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=40&audienceSegments=2+5+1782+1854+1865+1873+11+13+12+l&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-az-52dk&locationSource=IP_DFP&pincode=&subSlot=pp1_1&bookedSubSlot=pp1_1&ab=CAMP&partnerId=DH_APP&deliverySlab=5.24&userDeliverySlab=3.3360824584961&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=294.30322265625&utmSource=&utmMedium=&utmCampaign=&appModelType=APPBRAND&preCalibratedDownfunnelProbability=0.037273090332747&downfunnelVariantName=prod&downfunnelModelUuid=77508219&appId=226&autoPlayPref=3&installDeliverySlab=0.30528157949448&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=2&topCampaignIds=1857226745%5E&topCampaignECPMs=294.30322265625&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=3.7273089885712&campaignPrdictedCtr=0.34096893668175&productIds=&recoPolicy=&request_timestamp=1661249908&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=0.0034096892923117&variantName=prod&modelUuid=77433289&networkSwitch=NONE&topDirectCampaign=1857226745&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=0&campaign_type=STANDARD&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=bbf18a3d229cdce690a141fc0b77a2d0&gender=M&age=28&ageRange=3&orderTypeV2=0&idfa=&s2sBidId=&imputationType=IMPUTED&amazonSdkPayload=&contentCreatorId=&scoringModel=prod&filteringModel=prod&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661249908&\"
\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"responded\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"error\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"inflated\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"impression\": { \"internal\": \[
\"http://money.dailyhunt.in/impression?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&partnerId=DH_APP&appId=226&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"https://impression.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"click\": { \"internal\": \[
\"https://money.dailyhunt.in/click?clientId=548000&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&reqTime=1661249908&billingTypeId=3&orderId=60632&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=&\_\_oadest=\"
\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"lpTimeSpent\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] } }, \"fallback\": { \"type\": \"IMAGE\", \"startIndex\": 1,
\"minDistance\": 4, \"noSkipTimer\": 5, \"id\":
\"b276436a8fbfb5a764f056c31f7bfc82\", \"campaignId\": \"1688073950\",
\"bannerId\": \"1687409206\", \"content\": { \"image\": { \"url\":
\"http://acdn.newshuntads.com/daedalus-banners/1687409206/1661148424_65680_600x600.jpg\",
\"width\": 329, \"height\": 84 }, \"cta\": { \"url\":
\"https://money.dailyhunt.in/click?clientId=548000&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&reqTime=1661249908&billingTypeId=3&orderId=60632&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=&\_\_oadest=https%3A%2F%2Fapp.appsflyer.com%2Fcom.betway.sports-direct%3Fpid%3Dnewshunt_int%26af_r%3Dhttps%253A%252F%252Fbetway.com%252Fdownload%252Fandroid-sports%26af_siteid%3Ddailyhunt%26c%3Dsustenance%26af_dp%3Dbetwaysports%253A%252F%252F%26af_sub_siteid%3Dcard-pp1%26af_sub3%3D1661249908.0849%26af_c_id%3D\--CAMPAIGN_ID\--%26af_sub4%3Ds%25253Dbw210554%252526a%25253DDB3488520822146189%26af_ad_id%3D\--BANNER_ID\--%26af_sub2%3D548000%26af_click_lookback%3D7d%26trackerProvider%3Dappsflyer%26clickid%3D4b4d28ded973a24c29c566aa5f3766a8%26dhExtras%3D\--DH_EXTRAS\--%26advertising_id%3D8043aad5-507a-428d-a8d5-b09c98a46d68\",
\"data\": \"Download Now\", \"color\": \"#ffffff\", \"colorNight\":
\"#ffffff\", \"bgColor\": \"#52A1DD,#5282E7\", \"bgColorNight\":
\"#52A1DD,#5282E7\", \"browser\": \"INTERNAL\" } }, \"adFeedback\": {
\"label\": { \"color\": \"#000000\", \"colorNight\": \"#FFFFFF\",
\"bgColor\": \"#40000000\", \"bgColorNight\": \"#40000000\", \"data\":
\"Ad\", \"position\": \"TOP_RIGHT\" }, \"feedbackUrl\":
\"http://money.dailyhunt.in/data-api/adfeedback?bannerId=1131504889&campaignId=1857226745&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&city=\"
}, \"beacons\": { \"request\": { \"internal\": \[
\"http://money.dailyhunt.in/fallback?clientid=548000&req_time=23082022+15%3A48%3A28&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=realme&user_handset_model=rmx1921&user_id=&placement=card-pp1&user_app_ver=16.1.1.1&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-pp1&banner_id=1131504889&campaign_id=1857226745&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=765&price_range=mid&user_device_type=none&title=Betway_KP_SOB_1_Native_990x505++English&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&region=&mcc=&mnc=&lac=&cellid=&ip=10.52.134.5&adGroupId=5480006304a97413bf59.38480371&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=40&audienceSegments=2+5+1782+1854+1865+1873+11+13+12+l&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-az-52dk&locationSource=IP_DFP&pincode=&subSlot=pp1_1&bookedSubSlot=pp1_1&ab=CAMP&partnerId=DH_APP&deliverySlab=5.24&userDeliverySlab=3.3360824584961&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=294.30322265625&utmSource=&utmMedium=&utmCampaign=&appModelType=APPBRAND&preCalibratedDownfunnelProbability=0.037273090332747&downfunnelVariantName=prod&downfunnelModelUuid=77508219&appId=226&autoPlayPref=3&installDeliverySlab=0.30528157949448&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=2&topCampaignIds=1857226745%5E&topCampaignECPMs=294.30322265625&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=3.7273089885712&campaignPrdictedCtr=0.34096893668175&productIds=&recoPolicy=&request_timestamp=1661249908&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=0.0034096892923117&variantName=prod&modelUuid=77433289&networkSwitch=NONE&topDirectCampaign=1857226745&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=0&campaign_type=STANDARD&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=bbf18a3d229cdce690a141fc0b77a2d0&gender=M&age=28&ageRange=3&orderTypeV2=0&idfa=&s2sBidId=&imputationType=IMPUTED&amazonSdkPayload=&contentCreatorId=&scoringModel=prod&filteringModel=prod&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661249908&\"
\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"responded\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"error\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"inflated\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"impression\": { \"internal\": \[
\"http://money.dailyhunt.in/impression?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&partnerId=DH_APP&appId=226&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"https://impression.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"click\": { \"internal\": \[\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"lpTimeSpent\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] } } } } } \]

### Native Video Ad

[Video Ad Mock
API](https://qa-money.newshunt.com/publicVibe/v2/pgi/video.json)

Sample Responsejson\[ { \"type\": \"VIDEO\", \"template\":
\"NATIVE_VIDEO\", \"startIndex\": 1, \"minDistance\": 4,
\"noSkipTimer\": 5, \"id\": \"7143f51a7795873e58fa7c5e94a5efa7\",
\"campaignId\": \"1724741649\", \"bannerId\": \"1358059656\",
\"content\": { \"vastUrl\":
\"https%3A%2F%2Fqa-money.newshunt.com%2Fgetvast%3FclientId%3D4353980%26uniqueId%3D72ffa9be64d08fde832df447db42466c%26adId%3D1557247623%26campaignId%3D1151050526%26adPlacement%3Dstorypage%26cap%3D0%26reset%3D0%26billingTypeId%3D3%26orderId%3D294%26forceTracker%3D%26gaid%3D20ab727a-f437-4753-bbef-f030f5fd7f22%26gaidOptoutStatus%3D0%26reqTime%3D1661411704%26partnerId%3DDH_APP%26subSlot%3D%26nextAdIndex%3D%26bookedPlacement%3Dstorypage%26bookedSubSlot%3D%26clientVersions%3D19.0.12.2%26os%3Dandroid%26ucq%3Dfast%26resolution%3D1080x2028\",
\"image\": { \"url\":
\"https://qa-money.newshunt.com/daedalus-banners/1557247623/1654761916_66813_990x505.jpg\"
}, \"cta\": { \"url\":
\"https://money.dailyhunt.in/click?clientId=548000&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&reqTime=1661249908&billingTypeId=3&orderId=60632&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=&\_\_oadest=https%3A%2F%2Fapp.appsflyer.com%2Fcom.betway.sports-direct%3Fpid%3Dnewshunt_int%26af_r%3Dhttps%253A%252F%252Fbetway.com%252Fdownload%252Fandroid-sports%26af_siteid%3Ddailyhunt%26c%3Dsustenance%26af_dp%3Dbetwaysports%253A%252F%252F%26af_sub_siteid%3Dcard-pp1%26af_sub3%3D1661249908.0849%26af_c_id%3D\--CAMPAIGN_ID\--%26af_sub4%3Ds%25253Dbw210554%252526a%25253DDB3488520822146189%26af_ad_id%3D\--BANNER_ID\--%26af_sub2%3D548000%26af_click_lookback%3D7d%26trackerProvider%3Dappsflyer%26clickid%3D4b4d28ded973a24c29c566aa5f3766a8%26dhExtras%3D\--DH_EXTRAS\--%26advertising_id%3D8043aad5-507a-428d-a8d5-b09c98a46d68\",
\"data\": \"Download Now\", \"color\": \"#4caf79\", \"colorNight\":
\"#ffffff\", \"bgColor\": \"#52A1DD,#5282E7\", \"bgColorNight\":
\"#52A1DD,#5282E7\", \"browser\": \"INTERNAL\" }, \"tag\": { \"color\":
\"#757575\", \"colorNight\": \"#ffffff\", \"data\": \"Promoted\" },
\"brand\": { \"logo\":
\"https://icon-library.com/images/next-button-icon/next-button-icon-19.jpg\",
\"color\": \"#000000\", \"colorNight\": \"#ffffff\", \"data\":
\"Freshmart\" }, \"title\": { \"color\": \"#000000\", \"colorNight\":
\"#ffffff\", \"data\": \"Your neighbourhood grocer. A collection of
local brands, here for you.\" }, \"description\": { \"color\":
\"#545454\", \"colorNight\": \"#ffffff\", \"data\": \"Your neighbourhood
grocer. A collection of local brands, here for you. Your neighbourhood
grocer. A collection of local brands, here for you.Your neighbourhood
grocer. A collection of local brands\" } }, \"adFeedback\": { \"label\":
{ \"color\": \"#000000\", \"colorNight\": \"#FFFFFF\", \"bgColor\":
\"#40000000\", \"bgColorNight\": \"#40000000\", \"data\": \"Ad\",
\"position\": \"TOP_RIGHT\" }, \"feedbackUrl\":
\"http://money.dailyhunt.in/data-api/adfeedback?bannerId=1131504889&campaignId=1857226745&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&city=\"
}, \"beacons\": { \"request\": { \"internal\": \[
\"http://money.dailyhunt.in/fallback?clientid=548000&req_time=23082022+15%3A48%3A28&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=realme&user_handset_model=rmx1921&user_id=&placement=card-pp1&user_app_ver=16.1.1.1&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-pp1&banner_id=1131504889&campaign_id=1857226745&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=765&price_range=mid&user_device_type=none&title=Betway_KP_SOB_1_Native_990x505++English&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&region=&mcc=&mnc=&lac=&cellid=&ip=10.52.134.5&adGroupId=5480006304a97413bf59.38480371&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=40&audienceSegments=2+5+1782+1854+1865+1873+11+13+12+l&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-az-52dk&locationSource=IP_DFP&pincode=&subSlot=pp1_1&bookedSubSlot=pp1_1&ab=CAMP&partnerId=DH_APP&deliverySlab=5.24&userDeliverySlab=3.3360824584961&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=294.30322265625&utmSource=&utmMedium=&utmCampaign=&appModelType=APPBRAND&preCalibratedDownfunnelProbability=0.037273090332747&downfunnelVariantName=prod&downfunnelModelUuid=77508219&appId=226&autoPlayPref=3&installDeliverySlab=0.30528157949448&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=2&topCampaignIds=1857226745%5E&topCampaignECPMs=294.30322265625&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=3.7273089885712&campaignPrdictedCtr=0.34096893668175&productIds=&recoPolicy=&request_timestamp=1661249908&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=0.0034096892923117&variantName=prod&modelUuid=77433289&networkSwitch=NONE&topDirectCampaign=1857226745&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=0&campaign_type=STANDARD&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=bbf18a3d229cdce690a141fc0b77a2d0&gender=M&age=28&ageRange=3&orderTypeV2=0&idfa=&s2sBidId=&imputationType=IMPUTED&amazonSdkPayload=&contentCreatorId=&scoringModel=prod&filteringModel=prod&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661249908&\"
\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"responded\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"error\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"inflated\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"impression\": { \"internal\": \[
\"http://money.dailyhunt.in/impression?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&partnerId=DH_APP&appId=226&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"https://impression.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"click\": { \"internal\": \[\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"lpTimeSpent\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] } }, \"fallback\": { \"type\": \"IMAGE\", \"startIndex\": 1,
\"minDistance\": 4, \"noSkipTimer\": 5, \"id\":
\"b276436a8fbfb5a764f056c31f7bfc82\", \"campaignId\": \"1688073950\",
\"bannerId\": \"1687409206\", \"content\": { \"image\": { \"url\":
\"http://acdn.newshuntads.com/daedalus-banners/1687409206/1661148424_65680_600x600.jpg\"
}, \"cta\": { \"url\":
\"https://money.dailyhunt.in/click?clientId=548000&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&reqTime=1661249908&billingTypeId=3&orderId=60632&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=&\_\_oadest=https%3A%2F%2Fapp.appsflyer.com%2Fcom.betway.sports-direct%3Fpid%3Dnewshunt_int%26af_r%3Dhttps%253A%252F%252Fbetway.com%252Fdownload%252Fandroid-sports%26af_siteid%3Ddailyhunt%26c%3Dsustenance%26af_dp%3Dbetwaysports%253A%252F%252F%26af_sub_siteid%3Dcard-pp1%26af_sub3%3D1661249908.0849%26af_c_id%3D\--CAMPAIGN_ID\--%26af_sub4%3Ds%25253Dbw210554%252526a%25253DDB3488520822146189%26af_ad_id%3D\--BANNER_ID\--%26af_sub2%3D548000%26af_click_lookback%3D7d%26trackerProvider%3Dappsflyer%26clickid%3D4b4d28ded973a24c29c566aa5f3766a8%26dhExtras%3D\--DH_EXTRAS\--%26advertising_id%3D8043aad5-507a-428d-a8d5-b09c98a46d68\",
\"data\": \"Download Now\", \"color\": \"#ffffff\", \"colorNight\":
\"#ffffff\", \"bgColor\": \"#52A1DD,#5282E7\", \"bgColorNight\":
\"#52A1DD,#5282E7\", \"browser\": \"INTERNAL\" } }, \"adFeedback\": {
\"label\": { \"color\": \"#000000\", \"colorNight\": \"#FFFFFF\",
\"bgColor\": \"#40000000\", \"bgColorNight\": \"#40000000\", \"data\":
\"Ad\", \"position\": \"TOP_RIGHT\" }, \"feedbackUrl\":
\"http://money.dailyhunt.in/data-api/adfeedback?bannerId=1131504889&campaignId=1857226745&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&city=\"
}, \"beacons\": { \"request\": { \"internal\": \[
\"http://money.dailyhunt.in/fallback?clientid=548000&req_time=23082022+15%3A48%3A28&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=realme&user_handset_model=rmx1921&user_id=&placement=card-pp1&user_app_ver=16.1.1.1&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-pp1&banner_id=1131504889&campaign_id=1857226745&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=765&price_range=mid&user_device_type=none&title=Betway_KP_SOB_1_Native_990x505++English&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&region=&mcc=&mnc=&lac=&cellid=&ip=10.52.134.5&adGroupId=5480006304a97413bf59.38480371&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=40&audienceSegments=2+5+1782+1854+1865+1873+11+13+12+l&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-az-52dk&locationSource=IP_DFP&pincode=&subSlot=pp1_1&bookedSubSlot=pp1_1&ab=CAMP&partnerId=DH_APP&deliverySlab=5.24&userDeliverySlab=3.3360824584961&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=294.30322265625&utmSource=&utmMedium=&utmCampaign=&appModelType=APPBRAND&preCalibratedDownfunnelProbability=0.037273090332747&downfunnelVariantName=prod&downfunnelModelUuid=77508219&appId=226&autoPlayPref=3&installDeliverySlab=0.30528157949448&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=2&topCampaignIds=1857226745%5E&topCampaignECPMs=294.30322265625&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=3.7273089885712&campaignPrdictedCtr=0.34096893668175&productIds=&recoPolicy=&request_timestamp=1661249908&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=0.0034096892923117&variantName=prod&modelUuid=77433289&networkSwitch=NONE&topDirectCampaign=1857226745&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=0&campaign_type=STANDARD&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=bbf18a3d229cdce690a141fc0b77a2d0&gender=M&age=28&ageRange=3&orderTypeV2=0&idfa=&s2sBidId=&imputationType=IMPUTED&amazonSdkPayload=&contentCreatorId=&scoringModel=prod&filteringModel=prod&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661249908&\"
\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"responded\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"error\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"inflated\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"impression\": { \"internal\": \[
\"http://money.dailyhunt.in/impression?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&partnerId=DH_APP&appId=226&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"https://impression.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"click\": { \"internal\": \[\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"lpTimeSpent\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] } } } } \]

### Native Short Video

[Native Video Mock
API](https://qa-money.newshunt.com/publicVibe/v2/pgi/native_short_video.json)

Sample Respoinsejson\[ { \"type\": \"VIDEO\", \"template\":
\"NATIVE_SHORT_VIDEO\", \"startIndex\": 1, \"minDistance\": 4,
\"noSkipTimer\": 5, \"id\": \"7143f51a7795873e58fa7c5e94a5efa7\",
\"campaignId\": \"1724741649\", \"bannerId\": \"1358059656\",
\"content\": { \"vastUrl\":
\"https%3A%2F%2Fqa-money.newshunt.com%2Fgetvast%3FclientId%3D4353980%26uniqueId%3D72ffa9be64d08fde832df447db42466c%26adId%3D1557247623%26campaignId%3D1151050526%26adPlacement%3Dstorypage%26cap%3D0%26reset%3D0%26billingTypeId%3D3%26orderId%3D294%26forceTracker%3D%26gaid%3D20ab727a-f437-4753-bbef-f030f5fd7f22%26gaidOptoutStatus%3D0%26reqTime%3D1661411704%26partnerId%3DDH_APP%26subSlot%3D%26nextAdIndex%3D%26bookedPlacement%3Dstorypage%26bookedSubSlot%3D%26clientVersions%3D19.0.12.2%26os%3Dandroid%26ucq%3Dfast%26resolution%3D1080x2028\",
\"image\": { \"url\":
\"https://qa-money.newshunt.com/daedalus-banners/1557247623/1654761916_66813_990x505.jpg\"
}, \"cta\": { \"url\":
\"https://money.dailyhunt.in/click?clientId=548000&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&reqTime=1661249908&billingTypeId=3&orderId=60632&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=&\_\_oadest=https%3A%2F%2Fapp.appsflyer.com%2Fcom.betway.sports-direct%3Fpid%3Dnewshunt_int%26af_r%3Dhttps%253A%252F%252Fbetway.com%252Fdownload%252Fandroid-sports%26af_siteid%3Ddailyhunt%26c%3Dsustenance%26af_dp%3Dbetwaysports%253A%252F%252F%26af_sub_siteid%3Dcard-pp1%26af_sub3%3D1661249908.0849%26af_c_id%3D\--CAMPAIGN_ID\--%26af_sub4%3Ds%25253Dbw210554%252526a%25253DDB3488520822146189%26af_ad_id%3D\--BANNER_ID\--%26af_sub2%3D548000%26af_click_lookback%3D7d%26trackerProvider%3Dappsflyer%26clickid%3D4b4d28ded973a24c29c566aa5f3766a8%26dhExtras%3D\--DH_EXTRAS\--%26advertising_id%3D8043aad5-507a-428d-a8d5-b09c98a46d68\",
\"data\": \"Download Now\", \"color\": \"#4caf79\", \"colorNight\":
\"#ffffff\", \"bgColor\": \"#52A1DD,#5282E7\", \"bgColorNight\":
\"#52A1DD,#5282E7\", \"browser\": \"INTERNAL\" }, \"tag\": { \"color\":
\"#757575\", \"colorNight\": \"#ffffff\", \"data\": \"Promoted\" },
\"brand\": { \"logo\":
\"https://icon-library.com/images/next-button-icon/next-button-icon-19.jpg\",
\"color\": \"#000000\", \"colorNight\": \"#ffffff\", \"data\":
\"Freshmart\" }, \"title\": { \"color\": \"#000000\", \"colorNight\":
\"#ffffff\", \"data\": \"Your neighbourhood grocer. A collection of
local brands, here for you.\" }, \"description\": { \"color\":
\"#545454\", \"colorNight\": \"#ffffff\", \"data\": \"Your neighbourhood
grocer. A collection of local brands, here for you. Your neighbourhood
grocer. A collection of local brands, here for you.Your neighbourhood
grocer. A collection of local brands\" } }, \"adFeedback\": { \"label\":
{ \"color\": \"#000000\", \"colorNight\": \"#FFFFFF\", \"bgColor\":
\"#40000000\", \"bgColorNight\": \"#40000000\", \"data\": \"Ad\",
\"position\": \"TOP_RIGHT\" }, \"feedbackUrl\":
\"http://money.dailyhunt.in/data-api/adfeedback?bannerId=1131504889&campaignId=1857226745&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&city=\"
}, \"beacons\": { \"request\": { \"internal\": \[
\"http://money.dailyhunt.in/fallback?clientid=548000&req_time=23082022+15%3A48%3A28&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=realme&user_handset_model=rmx1921&user_id=&placement=card-pp1&user_app_ver=16.1.1.1&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-pp1&banner_id=1131504889&campaign_id=1857226745&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=765&price_range=mid&user_device_type=none&title=Betway_KP_SOB_1_Native_990x505++English&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&region=&mcc=&mnc=&lac=&cellid=&ip=10.52.134.5&adGroupId=5480006304a97413bf59.38480371&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=40&audienceSegments=2+5+1782+1854+1865+1873+11+13+12+l&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-az-52dk&locationSource=IP_DFP&pincode=&subSlot=pp1_1&bookedSubSlot=pp1_1&ab=CAMP&partnerId=DH_APP&deliverySlab=5.24&userDeliverySlab=3.3360824584961&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=294.30322265625&utmSource=&utmMedium=&utmCampaign=&appModelType=APPBRAND&preCalibratedDownfunnelProbability=0.037273090332747&downfunnelVariantName=prod&downfunnelModelUuid=77508219&appId=226&autoPlayPref=3&installDeliverySlab=0.30528157949448&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=2&topCampaignIds=1857226745%5E&topCampaignECPMs=294.30322265625&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=3.7273089885712&campaignPrdictedCtr=0.34096893668175&productIds=&recoPolicy=&request_timestamp=1661249908&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=0.0034096892923117&variantName=prod&modelUuid=77433289&networkSwitch=NONE&topDirectCampaign=1857226745&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=0&campaign_type=STANDARD&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=bbf18a3d229cdce690a141fc0b77a2d0&gender=M&age=28&ageRange=3&orderTypeV2=0&idfa=&s2sBidId=&imputationType=IMPUTED&amazonSdkPayload=&contentCreatorId=&scoringModel=prod&filteringModel=prod&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661249908&\"
\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"responded\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"error\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"inflated\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"impression\": { \"internal\": \[
\"http://money.dailyhunt.in/impression?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&partnerId=DH_APP&appId=226&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"https://impression.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"click\": { \"internal\": \[\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"lpTimeSpent\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] } }, \"shareability\": { \"text\": \"Share this ad\", \"subject\":
\"Check out the ad \", \"image\":
\"https://money.dailyhunt.in/daedalus-banners/1096400437/1661338831_37636_share_image.png\"
}, \"fallback\": { \"type\": \"IMAGE\", \"startIndex\": 1,
\"minDistance\": 4, \"noSkipTimer\": 5, \"id\":
\"b276436a8fbfb5a764f056c31f7bfc82\", \"campaignId\": \"1688073950\",
\"bannerId\": \"1687409206\", \"content\": { \"image\": { \"url\":
\"http://acdn.newshuntads.com/daedalus-banners/1687409206/1661148424_65680_600x600.jpg\",
\"width\": 329, \"height\": 84 }, \"cta\": { \"url\":
\"https://money.dailyhunt.in/click?clientId=548000&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&reqTime=1661249908&billingTypeId=3&orderId=60632&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=&\_\_oadest=https%3A%2F%2Fapp.appsflyer.com%2Fcom.betway.sports-direct%3Fpid%3Dnewshunt_int%26af_r%3Dhttps%253A%252F%252Fbetway.com%252Fdownload%252Fandroid-sports%26af_siteid%3Ddailyhunt%26c%3Dsustenance%26af_dp%3Dbetwaysports%253A%252F%252F%26af_sub_siteid%3Dcard-pp1%26af_sub3%3D1661249908.0849%26af_c_id%3D\--CAMPAIGN_ID\--%26af_sub4%3Ds%25253Dbw210554%252526a%25253DDB3488520822146189%26af_ad_id%3D\--BANNER_ID\--%26af_sub2%3D548000%26af_click_lookback%3D7d%26trackerProvider%3Dappsflyer%26clickid%3D4b4d28ded973a24c29c566aa5f3766a8%26dhExtras%3D\--DH_EXTRAS\--%26advertising_id%3D8043aad5-507a-428d-a8d5-b09c98a46d68\",
\"data\": \"Download Now\", \"color\": \"#ffffff\", \"colorNight\":
\"#ffffff\", \"bgColor\": \"#52A1DD,#5282E7\", \"bgColorNight\":
\"#52A1DD,#5282E7\", \"browser\": \"INTERNAL\" } }, \"adFeedback\": {
\"label\": { \"color\": \"#000000\", \"colorNight\": \"#FFFFFF\",
\"bgColor\": \"#40000000\", \"bgColorNight\": \"#40000000\", \"data\":
\"Ad\", \"position\": \"TOP_RIGHT\" }, \"feedbackUrl\":
\"http://money.dailyhunt.in/data-api/adfeedback?bannerId=1131504889&campaignId=1857226745&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&city=\"
}, \"beacons\": { \"request\": { \"internal\": \[
\"http://money.dailyhunt.in/fallback?clientid=548000&req_time=23082022+15%3A48%3A28&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=realme&user_handset_model=rmx1921&user_id=&placement=card-pp1&user_app_ver=16.1.1.1&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-pp1&banner_id=1131504889&campaign_id=1857226745&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=765&price_range=mid&user_device_type=none&title=Betway_KP_SOB_1_Native_990x505++English&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&region=&mcc=&mnc=&lac=&cellid=&ip=10.52.134.5&adGroupId=5480006304a97413bf59.38480371&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=40&audienceSegments=2+5+1782+1854+1865+1873+11+13+12+l&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-az-52dk&locationSource=IP_DFP&pincode=&subSlot=pp1_1&bookedSubSlot=pp1_1&ab=CAMP&partnerId=DH_APP&deliverySlab=5.24&userDeliverySlab=3.3360824584961&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=294.30322265625&utmSource=&utmMedium=&utmCampaign=&appModelType=APPBRAND&preCalibratedDownfunnelProbability=0.037273090332747&downfunnelVariantName=prod&downfunnelModelUuid=77508219&appId=226&autoPlayPref=3&installDeliverySlab=0.30528157949448&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=2&topCampaignIds=1857226745%5E&topCampaignECPMs=294.30322265625&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=3.7273089885712&campaignPrdictedCtr=0.34096893668175&productIds=&recoPolicy=&request_timestamp=1661249908&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=0.0034096892923117&variantName=prod&modelUuid=77433289&networkSwitch=NONE&topDirectCampaign=1857226745&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=0&campaign_type=STANDARD&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=bbf18a3d229cdce690a141fc0b77a2d0&gender=M&age=28&ageRange=3&orderTypeV2=0&idfa=&s2sBidId=&imputationType=IMPUTED&amazonSdkPayload=&contentCreatorId=&scoringModel=prod&filteringModel=prod&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661249908&\"
\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"responded\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"error\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"inflated\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"impression\": { \"internal\": \[
\"http://money.dailyhunt.in/impression?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&partnerId=DH_APP&appId=226&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"https://impression.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"click\": { \"internal\": \[\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"lpTimeSpent\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] } } } } \]

### Native Portrait Video Ad

[Native Portrait Video
API](https://qa-money.newshunt.com/publicVibe/v2/pgi/native_portrait_video.json)

Sample Responsejson\[ { \"type\": \"VIDEO\", \"template\":
\"NATIVE_PORTRAIT_VIDEO\", \"startIndex\": 1, \"minDistance\": 4,
\"noSkipTimer\": 5, \"id\": \"7143f51a7795873e58fa7c5e94a5efa7\",
\"campaignId\": \"1724741649\", \"bannerId\": \"1358059656\",
\"content\": { \"vastUrl\":
\"https%3A%2F%2Fqa-money.newshunt.com%2Fgetvast%3FclientId%3D4353980%26uniqueId%3D72ffa9be64d08fde832df447db42466c%26adId%3D1557247623%26campaignId%3D1151050526%26adPlacement%3Dstorypage%26cap%3D0%26reset%3D0%26billingTypeId%3D3%26orderId%3D294%26forceTracker%3D%26gaid%3D20ab727a-f437-4753-bbef-f030f5fd7f22%26gaidOptoutStatus%3D0%26reqTime%3D1661411704%26partnerId%3DDH_APP%26subSlot%3D%26nextAdIndex%3D%26bookedPlacement%3Dstorypage%26bookedSubSlot%3D%26clientVersions%3D19.0.12.2%26os%3Dandroid%26ucq%3Dfast%26resolution%3D1080x2028\",
\"image\": { \"url\":
\"https://qa-money.newshunt.com/daedalus-banners/1557247623/1654761916_66813_990x505.jpg\"
}, \"cta\": { \"url\":
\"https://money.dailyhunt.in/click?clientId=548000&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&reqTime=1661249908&billingTypeId=3&orderId=60632&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=&\_\_oadest=https%3A%2F%2Fapp.appsflyer.com%2Fcom.betway.sports-direct%3Fpid%3Dnewshunt_int%26af_r%3Dhttps%253A%252F%252Fbetway.com%252Fdownload%252Fandroid-sports%26af_siteid%3Ddailyhunt%26c%3Dsustenance%26af_dp%3Dbetwaysports%253A%252F%252F%26af_sub_siteid%3Dcard-pp1%26af_sub3%3D1661249908.0849%26af_c_id%3D\--CAMPAIGN_ID\--%26af_sub4%3Ds%25253Dbw210554%252526a%25253DDB3488520822146189%26af_ad_id%3D\--BANNER_ID\--%26af_sub2%3D548000%26af_click_lookback%3D7d%26trackerProvider%3Dappsflyer%26clickid%3D4b4d28ded973a24c29c566aa5f3766a8%26dhExtras%3D\--DH_EXTRAS\--%26advertising_id%3D8043aad5-507a-428d-a8d5-b09c98a46d68\",
\"data\": \"Download Now\", \"color\": \"#4caf79\", \"colorNight\":
\"#ffffff\", \"bgColor\": \"#52A1DD,#5282E7\", \"bgColorNight\":
\"#52A1DD,#5282E7\", \"browser\": \"INTERNAL\" }, \"tag\": { \"color\":
\"#757575\", \"colorNight\": \"#ffffff\", \"data\": \"Promoted\" },
\"brand\": { \"logo\":
\"https://icon-library.com/images/next-button-icon/next-button-icon-19.jpg\",
\"color\": \"#000000\", \"colorNight\": \"#ffffff\", \"data\":
\"Freshmart\" }, \"title\": { \"color\": \"#000000\", \"colorNight\":
\"#ffffff\", \"data\": \"Your neighbourhood grocer. A collection of
local brands, here for you.\" }, \"description\": { \"color\":
\"#545454\", \"colorNight\": \"#ffffff\", \"data\": \"Your neighbourhood
grocer. A collection of local brands, here for you. Your neighbourhood
grocer. A collection of local brands, here for you.Your neighbourhood
grocer. A collection of local brands\" } }, \"adFeedback\": { \"label\":
{ \"color\": \"#000000\", \"colorNight\": \"#FFFFFF\", \"bgColor\":
\"#40000000\", \"bgColorNight\": \"#40000000\", \"data\": \"Ad\",
\"position\": \"TOP_RIGHT\" }, \"feedbackUrl\":
\"http://money.dailyhunt.in/data-api/adfeedback?bannerId=1131504889&campaignId=1857226745&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&city=\"
}, \"beacons\": { \"request\": { \"internal\": \[
\"http://money.dailyhunt.in/fallback?clientid=548000&req_time=23082022+15%3A48%3A28&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=realme&user_handset_model=rmx1921&user_id=&placement=card-pp1&user_app_ver=16.1.1.1&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-pp1&banner_id=1131504889&campaign_id=1857226745&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=765&price_range=mid&user_device_type=none&title=Betway_KP_SOB_1_Native_990x505++English&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&region=&mcc=&mnc=&lac=&cellid=&ip=10.52.134.5&adGroupId=5480006304a97413bf59.38480371&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=40&audienceSegments=2+5+1782+1854+1865+1873+11+13+12+l&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-az-52dk&locationSource=IP_DFP&pincode=&subSlot=pp1_1&bookedSubSlot=pp1_1&ab=CAMP&partnerId=DH_APP&deliverySlab=5.24&userDeliverySlab=3.3360824584961&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=294.30322265625&utmSource=&utmMedium=&utmCampaign=&appModelType=APPBRAND&preCalibratedDownfunnelProbability=0.037273090332747&downfunnelVariantName=prod&downfunnelModelUuid=77508219&appId=226&autoPlayPref=3&installDeliverySlab=0.30528157949448&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=2&topCampaignIds=1857226745%5E&topCampaignECPMs=294.30322265625&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=3.7273089885712&campaignPrdictedCtr=0.34096893668175&productIds=&recoPolicy=&request_timestamp=1661249908&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=0.0034096892923117&variantName=prod&modelUuid=77433289&networkSwitch=NONE&topDirectCampaign=1857226745&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=0&campaign_type=STANDARD&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=bbf18a3d229cdce690a141fc0b77a2d0&gender=M&age=28&ageRange=3&orderTypeV2=0&idfa=&s2sBidId=&imputationType=IMPUTED&amazonSdkPayload=&contentCreatorId=&scoringModel=prod&filteringModel=prod&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661249908&\"
\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"responded\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"error\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"inflated\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"impression\": { \"internal\": \[
\"http://money.dailyhunt.in/impression?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&partnerId=DH_APP&appId=226&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"https://impression.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"click\": { \"internal\": \[\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"lpTimeSpent\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] } }, \"fallback\": { \"type\": \"IMAGE\", \"startIndex\": 1,
\"minDistance\": 4, \"noSkipTimer\": 5, \"id\":
\"b276436a8fbfb5a764f056c31f7bfc82\", \"campaignId\": \"1688073950\",
\"bannerId\": \"1687409206\", \"content\": { \"image\": { \"url\":
\"http://acdn.newshuntads.com/daedalus-banners/1687409206/1661148424_65680_600x600.jpg\",
\"width\": 329, \"height\": 84 }, \"cta\": { \"url\":
\"https://money.dailyhunt.in/click?clientId=548000&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&reqTime=1661249908&billingTypeId=3&orderId=60632&forceTracker=&partnerRef=&city=&state=&country=india&leadId=&subBannerId=&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=&\_\_oadest=https%3A%2F%2Fapp.appsflyer.com%2Fcom.betway.sports-direct%3Fpid%3Dnewshunt_int%26af_r%3Dhttps%253A%252F%252Fbetway.com%252Fdownload%252Fandroid-sports%26af_siteid%3Ddailyhunt%26c%3Dsustenance%26af_dp%3Dbetwaysports%253A%252F%252F%26af_sub_siteid%3Dcard-pp1%26af_sub3%3D1661249908.0849%26af_c_id%3D\--CAMPAIGN_ID\--%26af_sub4%3Ds%25253Dbw210554%252526a%25253DDB3488520822146189%26af_ad_id%3D\--BANNER_ID\--%26af_sub2%3D548000%26af_click_lookback%3D7d%26trackerProvider%3Dappsflyer%26clickid%3D4b4d28ded973a24c29c566aa5f3766a8%26dhExtras%3D\--DH_EXTRAS\--%26advertising_id%3D8043aad5-507a-428d-a8d5-b09c98a46d68\",
\"data\": \"Download Now\", \"color\": \"#ffffff\", \"colorNight\":
\"#ffffff\", \"bgColor\": \"#52A1DD,#5282E7\", \"bgColorNight\":
\"#52A1DD,#5282E7\", \"browser\": \"INTERNAL\" } }, \"adFeedback\": {
\"label\": { \"color\": \"#000000\", \"colorNight\": \"#FFFFFF\",
\"bgColor\": \"#40000000\", \"bgColorNight\": \"#40000000\", \"data\":
\"Ad\", \"position\": \"TOP_RIGHT\" }, \"feedbackUrl\":
\"http://money.dailyhunt.in/data-api/adfeedback?bannerId=1131504889&campaignId=1857226745&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&city=\"
}, \"beacons\": { \"request\": { \"internal\": \[
\"http://money.dailyhunt.in/fallback?clientid=548000&req_time=23082022+15%3A48%3A28&paper=&item_category=&Gpscountry=india&Gpsstate=&Gpscity=&IPcountry=&IPstate=&IPcity=&isp=&user_os_platform=android&user_handset_maker=realme&user_handset_model=rmx1921&user_id=&placement=card-pp1&user_app_ver=16.1.1.1&banner_rotation_type=0&bannerSelectedBy=adEngine&bookedPlacement=card-pp1&banner_id=1131504889&campaign_id=1857226745&user_connection=4G&connection_speed=SLOW&user_os_ver=9.0&encGaid=ODA0M2FhZDUtNTA3YS00MjhkLWE4ZDUtYjA5Yzk4YTQ2ZDY4&item_publisher_language=&user_languages=en&oi=765&price_range=mid&user_device_type=none&title=Betway_KP_SOB_1_Native_990x505++English&promoVdoId=&promoTopic=&latitude=NA&longitude=NA&uniqueId=4b4d28ded973a24c29c566aa5f3766a8&region=&mcc=&mnc=&lac=&cellid=&ip=10.52.134.5&adGroupId=5480006304a97413bf59.38480371&topicId=a3617d6e958a315152f3c08c3f2b5f1b&topicName=&ecpm=40&audienceSegments=2+5+1782+1854+1865+1873+11+13+12+l&resolution=1080x2028&hostalias=dh-gcp-ads-adengine-ws-az-52dk&locationSource=IP_DFP&pincode=&subSlot=pp1_1&bookedSubSlot=pp1_1&ab=CAMP&partnerId=DH_APP&deliverySlab=5.24&userDeliverySlab=3.3360824584961&dhTvChannelId=&dhTvType=&buzzContentpartner=&dhTvSourcekey=&dhTvRelevance=&dhTvUrgency=&dhTvPartyLeaning=&pubName=DH&vdoGroupKey=&nthImpression=1&articleId=&vpod=&v_ecpm=294.30322265625&utmSource=&utmMedium=&utmCampaign=&appModelType=APPBRAND&preCalibratedDownfunnelProbability=0.037273090332747&downfunnelVariantName=prod&downfunnelModelUuid=77508219&appId=226&autoPlayPref=3&installDeliverySlab=0.30528157949448&installCpi=&secondBidderCampaign=&secondBidderECPM=&optimisedBy=2&topCampaignIds=1857226745%5E&topCampaignECPMs=294.30322265625&entityId=a3617d6e958a315152f3c08c3f2b5f1b&entityType=HASHTAG&entitySubtype=&contentContext=&parentContentContext=&sourceType=&isHubExclusiveAdRequest=&predictedInstallProbability=3.7273089885712&campaignPrdictedCtr=0.34096893668175&productIds=&recoPolicy=&request_timestamp=1661249908&next_ad_index=&feed_refresh_count=&feed_type=&feed_id=&ad_extras=&sub_feed_id=&profile_type=&contentId=&event_type=AD_REQUEST&preCalibratedProbability=0.0034096892923117&variantName=prod&modelUuid=77433289&networkSwitch=NONE&topDirectCampaign=1857226745&isAdLoadEnabled=&lang_affinity=&is_interleaved=0&boost_factor=1&interleave_campaign_daedalus_config=0&expected_video_watch_duration=0&campaign_type=STANDARD&campaign_level=LEVEL_1&interleaved_competition=&isRollUp=1&requestIdDebug=bbf18a3d229cdce690a141fc0b77a2d0&gender=M&age=28&ageRange=3&orderTypeV2=0&idfa=&s2sBidId=&imputationType=IMPUTED&amazonSdkPayload=&contentCreatorId=&scoringModel=prod&filteringModel=prod&requestData=%7B%22products%22%3A%5B%5D%7D&locUpdate=&hostAppId=DH_APP&userBadge=&rejectedAdxBannerIds=&reqTime=1661249908&\"
\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"responded\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_RESPONDED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"error\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_ERROR&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"inflated\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_INFLATED&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] }, \"impression\": { \"internal\": \[
\"http://money.dailyhunt.in/impression?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&partnerId=DH_APP&appId=226&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"https://impression.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"click\": { \"internal\": \[\], \"external\": \[
\"https://click.appsflyer.com/com.betway.sports-direct?pid=newshunt_int&af_r=https%3A%2F%2Fbetway.com%2Fdownload%2Fandroid-sports&af_siteid=dailyhunt&c=sustenance&af_dp=betwaysports%3A%2F%2F&af_sub_siteid=card-pp1&af_sub3=1661249908.0849&af_c_id=1857226745&af_sub4=s%253Dbw210554%2526a%253DDB3488520822146189&af_ad_id=1131504889&af_sub2=548000&af_viewthrough_lookback=24h&trackerProvider=appsflyer&clickid=\--AD_UNIQUE\--&dhExtras=\--DH_EXTRAS\--&advertising_id=8043aad5-507a-428d-a8d5-b09c98a46d68\"
\] }, \"lpTimeSpent\": { \"internal\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\], \"external\": \[
\"http://money.dailyhunt.in/beaconEvents?uniqueId=4b4d28ded973a24c29c566aa5f3766a8&adId=1131504889&campaignId=1857226745&adPlacement=card-pp1&partnerRef=&city=&state=&country=india&clientId=548000&reqTime=1661249908&appId=226&eventType=AD_LP_TIME_SPENT&partnerId=DH_APP&subSlot=pp1_1&nextAdIndex=&bookedPlacement=card-pp1&bookedSubSlot=pp1_1&contentId=&contentCreatorId=\"
\] } } } } \]

# MOM 30th-SEP-2022

1.  Explained FC

2.  Explained about AppsOnDevice

3.  fetchCampaignData API - aligned

4.  Explained about handshake and request params / post body

5.  BE need to comeback for aod format

6.  Double layer enc not supporting

7.  PV doesn\'t have secondary language concepts

8.  first time body params are plain but once inget enc key pv will
    start sending enc data

9.  discuss handshake body

10. gaid, android, cellid, lat,long =\> enc supported value

11. modify confluent for gaid, android, cellid, lat,long

12. strict fcap need to share

13. check on appsondevice format

# MOM 6th-OCT-2022

1.  we\'re not going ahed with custom native format

2.  we\'re going ahed with google standard native format

3.  BE will introduce new field called nativeType if my \`formatType\`
    is native.

# **MOM 14th Nov 2022**

**Ad Request params:** current implementation: if current location is
not available, we are passing feed location in latlong\
**Change:**\
1. If current location is not available, do not pass lat long\
2. Pass feed location info in the following additional fields feedState,
feedDistrict, feedConstituency, feedTaluk, feedLat, feedLong

**Handshake request params:** current implementation: if current
location is not available, we are passing feed location in latlong.
IsGPSLocation is true when current location available\
**Change:**\
1. If current location is not available, do not pass lat long. set
IsGPSLocation true only when current location is available\
2. Pass feed location info in the following additional fields feedState,
feedDistrict, feedConstituency, feedTaluk, feedLat, feedLong

Note: From Pavan :\
\<\*\>please change feedState to feedStateId, feedDistrict to
feedDistrictId, feedTaluk to feedTalukId

feedConstituency you can remove taluk and constituency are same \</\*\>
