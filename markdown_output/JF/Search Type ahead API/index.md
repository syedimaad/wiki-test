+--------------------+-------------------------------------------------+
| **able Method**    | Post                                            |
+--------------------+-------------------------------------------------+
| **URL**            | {host}/v3/entity/search/typeahead?query=xyz     |
|                    |                                                 |
|                    | Note : For normal search query=xyz, For user    |
|                    | search query=@xyz, For search query=#xyz        |
+--------------------+-------------------------------------------------+
| **Request Header** | Content-Type: application/json, collfieDebug :  |
|                    | version Lang , ClientiD, and userId is present  |
|                    | in Headers                                      |
+--------------------+-------------------------------------------------+
| **Request Body**   | json{ \"query\" : \"queryText\" \"langs\":      |
|                    | \"en\", \"cid\": \"f699c4bb-ca35\", \"uid\":    |
|                    | \"7dd179f7-6a52-4c20-9f18-cd59475b5e67\",       |
|                    | \"city_id\": null, \"state_id\": null }         |
+--------------------+-------------------------------------------------+

**[Response :]{.underline}**

~~The Response will contain Three type of Objects : Search terms, Users
and Hashcode.~~

The Response will contain five type of Objects: Users, Hashtag,
Challenges, Contests and Zones.

The count of items for SearchTerm, Entities will be configured, If
matching entity does not found for query, Then in that case the
Searchterms will fill all resultSet.

Ex: config : searchTerm: 5, Entity : 5. Total PageSize = 10

If 5 searchTerms and 5 entity are found. Result will be having
searchTerm: 5, Entity : 5 as defined in Config.

else if Entity does not match 10 search ter will make the complete
result.

**New Requirements :-**

There will be 3 cases :

1.) Normal Search

2.) @ Search

3.) \# Search

All three consist of the following order and count -

1.) Normal Search

> Search Term(1) + Zones(1) + Users(3) + Contest(1) + Challenges(1) +
> Hashtags(3)

2.) @ Search Search -

> Search Term(1) + Humanized Zones(2) + Users(7)

3.) \# Search Search -

> Search Term(1) + Non Humanized Zones(1) + Contest(1) + Challenges(1) +
> Hashtags(6)

Note : No pagination required as of now

jsonfull-width{ \"status\": { \"server\": \"localhost\", \"code\":
\"200\", \"time\": \"26ms\", \"message\": \"OK\" }, \"data\": \[ {
\"format\": \"HINT\", \"query\": \"tes\" }, { \"format\": \"USER\",
\"experiment\": { \"score\": \"2.0\", \"algo\": \"algoName\",
\"search_tag\": \"tes\" }, \"id\":
\"d4dfc010-879f-4623-965d-0c0ad2334174\", \"text\": \"Techno Freak\",
\"verified\": false, \"type\": \"USER\", \"tagging\": true,
\"sub_text\": \"JoshUser_1625045317820\", \"thumbnail_url\":
\"https://stage-stream.coolfie.io/stream/stage-josh-content/profile_pictures/a867b85d3ca58dd8/9011da109780e2c2/a867b85d3ca58dd89011da109780e2c2.png\",
\"deep_link_url\":
\"https://stage-share.myjosh.in/profile/d4dfc010-879f-4623-965d-0c0ad2334174\",
\"is_author\": false, \"display_name\": \"Techno Freak\",
\"allow_follow\": true, \"user_type\": \"e\" }, { \"format\":
\"CONTEST\", \"experiment\": { \"score\": \"2.0\", \"algo\":
\"algoName\", \"search_tag\": \"tes\" }, \"id\":
\"50590f4c-7c79-47c6-b82e-4fe8a01b6ac6\", \"text\": \"test-1-page\",
\"type\": \"CONTEST\", \"label\": \"0 Views\", \"tagging\": true,
\"sub_text\": \"test-1-page\", \"sub_title\": \"Contest\",
\"deep_link_url\":
\"https://stage-share.myjosh.in/contest/50590f4c-7c79-47c6-b82e-4fe8a01b6ac6/all/all\",
\"is_author\": false, \"allow_follow\": true, \"meta_url\":
\"https://stage-api.coolfie.io/contest_category/list-v2\", \"icon_url\":
\"https://stage-stream.myjosh.in/stream/stage-josh-content/josh_version_content/GLOBAL_SEARCH_TABS_V3/Contest.png\"
}, { \"format\": \"CHALLENGE\", \"experiment\": { \"score\": \"4.0\",
\"algo\": \"algoName\", \"search_tag\": \"chall\" }, \"id\":
\"a74f8da9-e11b-4677-857a-a511b349f355\", \"text\":
\"challenge_azure_aws_test\", \"type\": \"CHALLENGE\", \"label\": \"0
Views\", \"tagging\": true, \"sub_text\": \"challenge_azure_aws_test\",
\"sub_title\": \"Challenge\", \"deep_link_url\":
\"https://stage-share.myjosh.in/challenge/a74f8da9-e11b-4677-857a-a511b349f355\",
\"is_author\": false, \"allow_follow\": true, \"icon_url\":
\"https://stage-stream.myjosh.in/stream/stage-josh-content/josh_version_content/GLOBAL_SEARCH_TABS_V3/Challenge.png\"
}, { \"format\": \"ZONE\", \"layout_type\": \"LAYOUT_ZONE\",
\"card_type\": \"ZONE_CARD\", \"text\": \"Testing\", \"sub_title\":
\"test\", \"thumbnail_url\":
\"https://stage-stream.myjosh.in/stream/stage-josh-content/zone/c0c9b1181dd24a08/9e8d421d2dfe3c52/zone_icon.jpg\",
\"deep_link_url\":
\"https://stage-share.myjosh.in/zone/c0c9b118-1dd2-4a08-9e8d-421d2dfe3c52\",
\"id\": \"c0c9b118-1dd2-4a08-9e8d-421d2dfe3c52\", \"stats_html\":
\"\<span\> 0 Followers &nbsp;.&nbsp;0 Posts\</span\>\",
\"allow_follow\": true, \"strip_url\":
\"https://stage-stream.myjosh.in/stream/stage-josh-content/zone/c0c9b1181dd24a08/9e8d421d2dfe3c52/c0c9b118-1dd2-4a08-9e8d-421d2dfe3c52_zone_strip.webp\",
\"icon_url\":
\"https://stage-stream.myjosh.in/stream/stage-josh-content/zone/c0c9b1181dd24a08/9e8d421d2dfe3c52/zone_icon_1656414933_en_icon.webp\",
\"sub_text\": \"test\", \"category\": \"Testing\", \"label\": \"0
Views\", \"zone_follow_url\":
\"https://stage-api.myjosh.in/apij/zone/follow\" }, { \"format\":
\"HASHTAG\", \"experiment\": { \"score\": \"2.0\", \"algo\":
\"algoName\", \"search_tag\": \"tes\" }, \"id\": \"test\", \"text\":
\"test\", \"type\": \"HASHTAG\", \"label\": \"0 Views\", \"tagging\":
true, \"sub_text\": \"test\", \"deep_link_url\":
\"https://stage-feed.coolfie.io/tags/test\", \"is_author\": false,
\"allow_follow\": true } \] }
