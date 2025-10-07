## Objective:

To show user generated content relevant to campaign as advertisement on
josh app where relevance criteria will be based on selected hashtags for
campaign.

## Design:

1.  **Campaign configuration in deadalus**

    1.  we have to create an APN for a campaign with content targeting
        (key-value pairs)

        1.  lang : en,hi, hashtags : hastag1,hashtag2,

        2.  Sample APN with contentids as key

    2.  S2SJosh campaign with content targeting (banner has to be linked
        with created APN)

jsonSample Banner Meta { \"identifier\": \"josh\", \"itemTag\":
\"Promoted\", \"landingPageTarget\": \"2\", \"autoPlayPreferences\":
\"2\", \"enableBorder\": false, \"borderColor\": \"\",
\"redirectWebUrl\": true, \"adType\": \"video-native\",
\"s2sDriverProfileEnable\": true, \"adFeedBackDisabled\": false,
\"s2sDriverProfileName\": \"josh:video:bangla\", \"subSlots\": {
\"web\": \[\], \"supplement\": \[\], \"card-pp1\": \[ \"pp1_c1\" \],
\"wsupplement\": \[\], \"wcard-pp1\": \[\] }, \"languages\": \[\],
\"enableShareability\": false, \"sourceAlphabet\": null,
\"userPermissionsMetaData\": { \"requireUserPermission\": false },
\"userPermissionsData\": { \"requireUserPermission\": false },
\"adTagPosition\": \"TOP_RIGHT\", \"defaultImpTrackers\": \[\],
\"clickTrackers\": \[\], \"customParameters\": \[\],
\"androidGoCompatible\": \[ \"card-p0\", \"card-p1\", \"card-pp1\",
\"p1\", \"storypage\", \"supplement\", \"pgi\", \"promo\", \"web\",
\"pgipromo\", \"dh-partner\", \"splash\" \], \"impTrackers\": \[\],
\"isBillable\": false, \"customImpTrackerList\": \[\] }

2\. **Fetch content meta relevant to campaign / request (Candidate
Generation)**

- S2SV2 system pulls all videos for the hashtag from the content system

a\. Construct ElasticSearch query from given key value pairs in APN and
get top post_ids meta data for each eligible campaign for a request

b\. Also store following from ElasticSearch

1\. Video metrics like views, frequency distribution of
video_watch_duration .

2\. Hashtag level aggregated metrics

c\. S2SV2 keeps the josh content data updated every 5 mins

3\. **Ad Request Flow**

1.  AdEngine Calls the S2S service for any request

    - S2S always returns S2S Josh(if present) + the highest other bid. 

2.  Creative Selection (S2S)

    1.  Phase 0: Randomly choose 1 creative out of all. 

    2.  Phase 1: Score the creatives using a simple formula. 

    3.  Phase 1.5: Expose the Banner DCO service.

    4.  Phase 2: Ranking exposes an API for choosing creatives. 

    5.  Ranking 

        1.  Score the S2S Josh campaign and sort and select.

            1.  Based on stored metadata of the creatives 

            2.  Dynamic atts.

            3.  User atts

            4.  Video parameters (features from the video)

**Questions** ?

1.  How and where these ads will be run

    1.  josh videos on josh app

2.  What will be bid value for the S2S Josh campaign? 

    1.  One India? → 1rs hardcoded and we ensure no competition.

    2.  Make this comparable with bids from other Networks. 
