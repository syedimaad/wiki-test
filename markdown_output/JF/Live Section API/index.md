+------------------+--------------------+------------------------------+
| **Method**       | **GET**                                           |
+------------------+---------------------------------------------------+
| **URL**          | \<host\>/**feed/live?lang_code=en**               |
+------------------+--------------------+------------------------------+
| **Path Params**  | lang_code          | en                           |
+------------------+--------------------+------------------------------+
| **Query Params** | page               | request page (default - 0)   |
|                  +--------------------+------------------------------+
|                  | rows               | number of elements per page  |
|                  |                    | (default - 10)               |
+------------------+--------------------+------------------------------+
| **Header**       | coolfie-debug-info | appVersion,userLang, etc -   |
|                  |                    | same as for you              |
|                  |                    |                              |
|                  +--------------------+------------------------------+
|                  | platform           | Only for IOS/PWA             |
|                  +--------------------+------------------------------+
|                  | user-uuid          | header containing user uuid  |
+------------------+--------------------+------------------------------+
| **Payload**      |                                                   |
+------------------+---------------------------------------------------+

**[Response:]{.underline}**

wide{ \"status\": { \"time\": \"155ms\", \"server\": \"\", \"code\":
\"200\", \"message\": \"OK\" }, \"metadata\": { \"next\":
\"https://feed.myjosh.in/feed/live?lang_code=hi&page=1&rows=7\",
\"page_info\": { \"page_number\": 0, \"page_size\": 10 } }, \"data\": \[
{ \"user_profile\": { \"name\": \"tijara_vines01\", \"user_bias_score\":
0, \"user_uuid\": \"e15bc132-a30a-4249-864d-83ca4d9bdf44\",
\"profile_pic\":
\"https://stream.myjosh.in/stream/prod-ugc-contents/profile_pictures/fd66a799fa478c4d/6aa1427b86fa2b45/fd66a799fa478c4d6aa1427b86fa2b45_icon.jpeg\",
\"user_name\": \"tijara_vines01\", \"verified\": false,
\"moderation_level\": 1, \"user_type\": \"g\" }, \"content_uuid\":
\"8538d9e4-c4f1-422d-a656-f88906f95f34\", \"card_type\": \"LIVE\",
\"format\": \"LIVE\", \"live_meta\" : { \"event_time\": \"long, UTC+5:30
hours in milliseconds)\", \"refresh_time\" : \"1200000, // (long -
milliseconds)\", \"status\" : \"true, // Live status\", \"room_url\": \"
// Josh Live deeplink\" }, \"room_meta\" : { \"id\":
\"039c907c-49fe-408b-b3b9-cdd6bed8f3ea\", \"roomId\": \"583511113\",
\"title\": \"Rahul6\'s Room\", \"topic\": null, \"hashTags\": \[\],
\"allowReplay\": true, \"allowComments\": true,
\"raiseHandPrivacyEnabled\": true, \"privacyType\": \"PUBLIC\",
\"startDateTime\": \"2022-07-04 16:02:54\", \"endDateTime\":
\"2022-07-04 17:02:54\", \"deepLink\":
\"https://qa-share.myjosh.in/live/room/039c907c-49fe-408b-b3b9-cdd6bed8f3ea\",
\"interestCategoryName\": null, \"interestSubCategoryName\": null,
\"shutRoom\": false, \"shutFromTencent\": false, \"replayUrl\": null,
\"speakers\": \[\], \"friendsList\": \[\], \"host\": { \"id\":
\"e467c0d7-aead-4cbb-ab53-c313dd308885\", \"name\": \"Sarthak sarthak
sarthak sartha\", \"avatar\":
\"https://qa-stream.coolfie.io/stream/qa-josh-content/profile_pictures/d77fa667cfb99780/93aa71c6672513b9/d77fa667cfb9978093aa71c6672513b9.jpg\",
\"userProfileLink\":
\"https://qa-share.myjosh.in/profile/e467c0d7-aead-4cbb-ab53-c313dd308885\"
}, \"videoThumb\": null, \"featuredIndex\": 65500, \"count\": 2,
\"verified\": false, \"appId\": \"JOSH_APP\", \"notified\": false,
\"videoEnabled\": true } } \], \"latest_cookie_page_number\": 1 }
