## Request

+------------------+----------------------+----------------------------+
| **Method**       | **POST**                                          |
+------------------+---------------------------------------------------+
| **URL**          | `/v1/feed/zone/<zone_id>/<type>`                  |
+------------------+----------------------+----------------------------+
| **Path Params**  | `type`               | TYPE possible values are   |
|                  |                      |                            |
|                  |                      | 1.  feed/video for VIDEO   |
|                  |                      |     content                |
|                  |                      |                            |
|                  |                      | 2.  news for NEWS content  |
|                  |                      |                            |
|                  |                      | 3.  image for IMAGE        |
|                  |                      |     content                |
|                  |                      |                            |
|                  |                      | 4.  social for SOCIAL      |
|                  |                      |     content                |
+------------------+----------------------+----------------------------+
|                  | `zone_id`            | zone id of entity          |
+------------------+----------------------+----------------------------+
| **Query Params** | `page`               | request page (default - 0) |
|                  +----------------------+----------------------------+
|                  | `rows`               | number of elements per     |
|                  |                      | page (default - 10)        |
+------------------+----------------------+----------------------------+
| **Header**       | `coolfie-debug-info` | appVersion, userLang,      |
|                  |                      | etc - same as for you      |
|                  |                      |                            |
|                  +----------------------+----------------------------+
|                  | `platform`           | Only for IOS/PWA           |
|                  +----------------------+----------------------------+
|                  | `user-uuid`          | header containing user     |
|                  |                      | uuid                       |
+------------------+----------------------+----------------------------+
| **Payload**      | {                                                 |
|                  |                                                   |
|                  | "clientId": \<clientId\>,                         |
|                  |                                                   |
|                  | "userUuid": \<userUuid\>\>                        |
|                  |                                                   |
|                  | }                                                 |
+------------------+---------------------------------------------------+

 

**Known Implementation:**

1.  News / Social / IMAGE should be populated from it\'s respective ES /
    Index

2.  **share_url**, **card_type** and **url** will come for all three
    types of contents, rest will come only for image type

## Response for Video Feed

jsonfull-width{ \"status\": { \"time\": \"43ms\", \"server\": \"\",
\"code\": \"200\", \"message\": \"OK\" }, \"metadata\": { \"next\":
\"https://feed.myjosh.in/v1/feed/zone/\<zone_id\>/video?page=1&rows=10\",
\"page_info\": { \"page_number\": 0, \"page_size\": 1 } }, \"data\": \[
{ \"reactions\": \[ { \"count\": \"4k\", \"reaction_icon_url\":
\"https://vectorlogo4u.com/wp-content/uploads/2016/09/facebook-like-icon.png\",
\"reaction_type\": 0, \"reaction_name\": \"Unlike\" } \], \"url\":
\"https://stream.myjosh.in/stream/prod-ugc-contents/6efd66c4e0660997/259e18b432fe40a1/6efd66c4e0660997259e18b432fe40a1_auto_s5.m3u8\",
\"orientation\": \"0\", \"experiment\": { \"expA\": \"valA\", \"expB\":
\"valB\" }, \"user_profile\": { \"name\": \"Kunal Sanghvi\",
\"user_bias_score\": 0, \"user_uuid\":
\"abcdabcd-abcd-abcd-abcd-abcdabcdabcd\", \"profile_pic\":
\"https://stream.myjosh.in/stream/prod-ugc-contents/profile_pictures/6cae43010b118ca4/7705f9716dffa493/6cae43010b118ca47705f9716dffa493_icon.jpeg\",
\"user_name\": \"KunalSanghvi\", \"verified\": true,
\"moderation_level\": 1, \"user_type\": \"e\" }, \"video_duration\":
14.76, \"content_uuid\": \"efabefab-efab-efab-efab-efabefabefab\",
\"content_category\": \"Glamour\", \"share_count\": \"512\",
\"content_title\": \"#RealHai #RealEntertainer\", \"pixel_size\":
\"720x1280\", \"like_count\": \"4k\", \"prefetch_cache_percentage\":
100.0, \"share_url\":
\"https://share.myjosh.in/video/efabefab-efab-efab-efab-efabefabefab\",
\"card_type\": \"video\", \"view_count\": \"49.3k\", \"lang_code\":
\"en\", \"prepared_content_title\": \"#RealHai #RealEntertainer
#specialcontent\", \"thumbnail\":
\"https://stream.myjosh.in/stream/prod-ugc-contents/6efd66c4e0660997/259e18b432fe40a1/6efd66c4e0660997259e18b432fe40a1\_{thumbnail_type}\_{quality}\_{resolution}.webp\",
\"report_url\":
\"https://share.myjosh.in/report/content/efabefab-efab-efab-efab-efabefabefab?reported-by-clientid=efabcd&reported-by-uuid=12341234-1234-1234-1234-123412341234\",
\"tags\": \"#RealHai #RealEntertainer #specialcontent\",
\"download_url\":
\"https://stream.myjosh.in/stream/prod-ugc-contents/6efd66c4e0660997/259e18b432fe40a1/6efd66c4e0660997259e18b432fe40a1_wmj_480.mp4\",
\"download_count\": \"515\", \"request_id\":
\"01d8be04-1b63-4f43-b000-0de73125e949\", \"audio_track_meta\": {
\"title\": \"Original sound by (SUSHREESABITA)\", \"id\":
\"8aae32cf-59b0-47f6-aec1-94f69c59246d\", \"artist\": \"SUSHREESABITA\",
\"url\":
\"https://stream.myjosh.in/stream/prod-ugc-contents/audio_files_extracted/d234c5a6fec89180/fa010392700021e3/d234c5a6fec89180fa010392700021e3.aac\",
\"audio_amplitudes\": \[ 220, 277, 221, 219 \], \"album_art\":
\"https://stream.myjosh.in/stream/prod-ugc-contents/profile_pictures/6cae43010b118ca4/7705f9716dffa493/6cae43010b118ca47705f9716dffa493_icon.jpeg\",
\"duration_ms\": 14832, \"format_type\": \"aac\", \"mime_type\":
\"aac\", \"uploaded_by\": { \"uuid\": \"\", \"name\": \"\",
\"user_name\": \"SUSHREESABITA\" }, \"deep_link\": { \"type\":
\"audio\", \"text\": \"See Videos\", \"url\":
\"https://share.myjosh.in/audio/8aae32cf-59b0-47f6-aec1-94f69c59246d\"
}, \"transcoding_status\": \"SUCCESS\", \"not_active\": false,
\"not_visible\": true, \"source\": \"EXTRACTED\",
\"max_selection_duration_ms\": 30000, \"label_info\": { \"id\":
\"fad1f021-41a7-40cd-9950-b77efee3d983\", \"label\": \"Saregama\",
\"thumbnail\":
\"https://stream.coolfie.io/stream/prod-ugc-contents/zerosearch/thumbnails/eecc81e76d684e39/b3a709cf39a4f1c1/eecc81e76d684e39b3a709cf39a4f1c1.png\"
}, \"album_info\": { \"id\": \"0815d326-c4e2-4c79-b97c-f95a01a90229\",
\"name\": \"Souten\" }, \"genre\": \"World,Films/Games,Bollywood\" },
\"challenge_meta\": { \"display\": \"realhai\", \"id\":
\"81670cc7-95e2-4f1b-84bc-e6a39b060160\", \"deep_link\": { \"type\":
\"challenge\", \"text\": null, \"url\":
\"https://share.myjosh.in/challenge/81670cc7-95e2-4f1b-84bc-e6a39b060160\"
} }, \"m3u8_profiles\": \[ \"average\", \"slow\", \"betteraverage\" \],
\"ucq_url\":
\"https://stream.myjosh.in/stream/prod-ugc-contents/6efd66c4e0660997/259e18b432fe40a1/6efd66c4e0660997259e18b432fe40a1\_{ucq}\_auto_s5.m3u8\",
\"rich_content_title\": \"\<html\>\<strong\>\<a
href=https://feed.myjosh.in/tags/RealHai\>#RealHai\</a\>\</strong\>
\<strong\>\<a
href=https://feed.myjosh.in/tags/RealEntertainer\>#RealEntertainer\</a\>\</strong\>\</html\>\",
\"duet_file_available\": false, \"not_cacheable\": true, \"format\":
\"VIDEO\", \"comments_count\": 0, \"comments_reply_count\": 0,
\"comments_reply_count_update_time_millis\": 0, \"item_ttl\":
1659944708927, \"is_voted\": false, \"is_votable\": false, \"icon_url\":
\"https://stream.myjosh.in/stream/prod-ugc-contents/6efd66c4e0660997/259e18b432fe40a1/6efd66c4e0660997259e18b432fe40a1_icon.webp\",
\"animated_icon_url\":
\"https://stream.myjosh.in/stream/prod-ugc-contents/6efd66c4e0660997/259e18b432fe40a1/6efd66c4e0660997259e18b432fe40a1_animated_icon.webp\",
\"mp4_url\":
\"https://stream.myjosh.in/stream/prod-ugc-contents/6efd66c4e0660997/259e18b432fe40a1/6efd66c4e0660997259e18b432fe40a1\_{quality}\_{resolution}.mp4\",
\"zone_meta\": { \"id\": \<zone_id\>, \"icon_url\": \<zones icon url\>
\"cta_text\": \"More Kunal Sanghvi Videos\" \"cta\": \"zone deep link\"
} } \] }

## Response for Images Feed

jsonfull-width{ \"status\": { \"time\": \"43ms\", \"server\": \"\",
\"code\": \"200\", \"message\": \"OK\" }, \"metadata\": { \"next\":
\"https://feed.myjosh.in/v1/feed/zone/\<zone_id\>/image?page=1&rows=10\",
\"page_info\": { \"page_number\": 0, \"page_size\": 1 } }, \"data\": \[
{ \"reactions\": \[ { \"count\": \"4k\", \"reaction_icon_url\":
\"https://vectorlogo4u.com/wp-content/uploads/2016/09/facebook-like-icon.png\",
\"reaction_type\": 0, \"reaction_name\": \"Unlike\" } \],
\"experiment\": { \"expA\": \"valA\", \"expB\": \"valB\" },
\"user_profile\": { \"name\": \"Kunal Sanghvi\", \"user_bias_score\": 0,
\"user_uuid\": \"abcdabcd-abcd-abcd-abcd-abcdabcdabcd\",
\"profile_pic\":
\"https://stream.myjosh.in/stream/prod-ugc-contents/profile_pictures/6cae43010b118ca4/7705f9716dffa493/6cae43010b118ca47705f9716dffa493_icon.jpeg\",
\"user_name\": \"KunalSanghvi\", \"verified\": true,
\"moderation_level\": 1, \"user_type\": \"e\" }, \"content_uuid\":
\"dfabefab-efab-efab-efab-efabefabefab\", \"content_category\":
\"Glamour\", \"share_count\": \"512\", \"content_title\": \"#RealHai
#RealEntertainer\", \"pixel_size\": \"720x1280\", \"like_count\":
\"4k\", \"prefetch_cache_percentage\": 100.0, \"share_url\":
\"https://share.myjosh.in/image/dfabefab-efab-efab-efab-efabefabefab\",
\"card_type\": \"image\", \"view_count\": \"49.3k\", \"lang_code\":
\"en\", \"prepared_content_title\": \"#RealHai #RealEntertainer
#specialcontent\", \"thumbnail\": \"\<selected image thumbnail / first
image thumbnail\>\", \"report_url\":
\"https://share.myjosh.in/report/content/efabefab-efab-efab-efab-efabefabefab?reported-by-clientid=efabcd&reported-by-uuid=12341234-1234-1234-1234-123412341234\",
\"tags\": \"#RealHai #RealEntertainer #specialcontent\",
\"download_url\": \"\<image download url\>\", \"download_count\":
\"515\", \"request_id\": \"01d8be04-1b63-4f43-b000-0de73125e949\",
\"rich_content_title\": \"\<html\>\<strong\>\<a
href=https://feed.myjosh.in/tags/RealHai\>#RealHai\</a\>\</strong\>
\<strong\>\<a
href=https://feed.myjosh.in/tags/RealEntertainer\>#RealEntertainer\</a\>\</strong\>\</html\>\",
\"not_cacheable\": true, \"format\": \"IMAGE/GIF\", \"comments_count\":
0, \"comments_reply_count\": 0,
\"comments_reply_count_update_time_millis\": 0, \"item_ttl\":
1659944708927, \"images\": \[ { \"thumbnail\": \"\<first image
thumbnail\>\", \"icon_url\": \"\<first image icon url\>\", \"url\":
\"\<first image url\>\", }, { \"thumbnail\": \"\<second image
thumbnail\>\", \"icon_url\": \"\<second image icon url\>\", \"url\":
\"\<second image url\>\", } \], \"zone_meta\": { \"id\": \<zone_id\>,
\"icon_url\": \<zones icon url\> \"cta_text\": \"More Kunal Sanghvi
Images\" \"cta\": \"zone deep link\" } } \] }

## Response for News/Social Feed

jsonfull-width{ \"status\": { \"time\": \"43ms\", \"server\": \"\",
\"code\": \"200\", \"message\": \"OK\" }, \"metadata\": { \"next\":
\"https://feed.myjosh.in/v1/feed/zone/\<zone_id\>/news?page=1&rows=10\",
\"page_info\": { \"page_number\": 0, \"page_size\": 1 } }, \"data\": \[
{ \"experiment\": { \"expA\": \"valA\", \"expB\": \"valB\" },
\"user_profile\": { \"name\": \"Kunal Sanghvi\", \"user_bias_score\": 0,
\"user_uuid\": \"abcdabcd-abcd-abcd-abcd-abcdabcdabcd\",
\"profile_pic\":
\"https://stream.myjosh.in/stream/prod-ugc-contents/profile_pictures/6cae43010b118ca4/7705f9716dffa493/6cae43010b118ca47705f9716dffa493_icon.jpeg\",
\"user_name\": \"KunalSanghvi\", \"verified\": true,
\"moderation_level\": 1, \"user_type\": \"e\" }, \"content_uuid\":
\"dfabefab-efab-efab-efab-efabefabefab\", \"content_category\":
\"Glamour\", \"share_count\": \"512\", \"content_title\": \"#RealHai
#RealEntertainer\", \"pixel_size\": \"720x1280\", \"like_count\":
\"4k\", \"prefetch_cache_percentage\": 100.0, \"share_url\":
\"https://share.myjosh.in/news/dfabefab-efab-efab-efab-efabefabefab\",
\"card_type\": \"\<news/social\>\", \"view_count\": \"49.3k\",
\"lang_code\": \"en\", \"prepared_content_title\": \"#RealHai
#RealEntertainer #specialcontent\", \"report_url\":
\"https://share.myjosh.in/report/content/efabefab-efab-efab-efab-efabefabefab?reported-by-clientid=efabcd&reported-by-uuid=12341234-1234-1234-1234-123412341234\",
\"tags\": \"#RealHai #RealEntertainer #specialcontent\", \"request_id\":
\"01d8be04-1b63-4f43-b000-0de73125e949\", \"rich_content_title\":
\"\<html\>\<strong\>\<a
href=https://feed.myjosh.in/tags/RealHai\>#RealHai\</a\>\</strong\>
\<strong\>\<a
href=https://feed.myjosh.in/tags/RealEntertainer\>#RealEntertainer\</a\>\</strong\>\</html\>\",
\"not_cacheable\": true, \"format\": \"\<NEWS/SOCIAL\>\",
\"comments_count\": 0, \"comments_reply_count\": 0,
\"comments_reply_count_update_time_millis\": 0, \"item_ttl\":
1659944708927, \"zone_meta\": { \"id\": \<zone_id\>, \"icon_url\":
\<zones icon url\> \"cta_text\": \"More Kunal Sanghvi \<News/Social\>\"
\"cta\": \"zone deep link\" } } \] }
