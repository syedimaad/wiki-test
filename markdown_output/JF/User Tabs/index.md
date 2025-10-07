## Request

+------------------------------------------------+-----------------------------+-----------------------------+
| **Method**falseSystem                          | **POST**                                                  |
| JIRAe55da6ef-1840-3475-9293-310ba48d502dJF-168 |                                                           |
+------------------------------------------------+-----------------------------------------------------------+
| **URL**                                        | `/v1/user/feed/<user_uuid>/?type=<type>&order=latest`     |
+------------------------------------------------+-----------------------------+-----------------------------+
| **Path Params**                                | `user_uuid`                 | users uuid                  |
+------------------------------------------------+-----------------------------+-----------------------------+
| **Query Params**                               | `type`                      | TYPE possible values are    |
|                                                |                             |                             |
|                                                |                             | 1.  news for NEWS content   |
|                                                |                             |                             |
|                                                |                             | 2.  image for IMAGE content |
|                                                |                             |                             |
|                                                |                             | 3.  social for SOCIAL       |
|                                                |                             |     content                 |
|                                                +-----------------------------+-----------------------------+
|                                                | `page`                      | request page (default - 0)  |
|                                                +-----------------------------+-----------------------------+
|                                                | `rows`                      | number of elements per page |
|                                                |                             | (default - 10)              |
+------------------------------------------------+-----------------------------+-----------------------------+
| **Header**                                     | `coolfie-debug-info`        | appVersion, userLang, etc - |
|                                                |                             | same as for you             |
|                                                |                             |                             |
|                                                +-----------------------------+-----------------------------+
|                                                | `platform`                  | Only for IOS/PWA            |
|                                                +-----------------------------+-----------------------------+
|                                                | `user-uuid`                 | header containing user uuid |
+------------------------------------------------+-----------------------------+-----------------------------+
| **Payload**                                    | {                                                         |
|                                                |                                                           |
|                                                | "clientId": \<clientId\>,                                 |
|                                                |                                                           |
|                                                | "userUuid": \<userUuid\>\>                                |
|                                                |                                                           |
|                                                | }                                                         |
+------------------------------------------------+-----------------------------------------------------------+

 

**Known Implementation:**

1.  NEWS / SOCIAL / IMAGE should be populated from it\'s respective ES /
    Index

2.  **BC : IF type is not sent then we need to serve VIDEO content ( the
    url becomes TPV url)**

3.  This is extending existing Latest TPV to accept a type query param

4.  order values can be {latest, trending}

## Response for Type Image Feed

jsonfull-width{ \"status\": { \"time\": \"43ms\", \"server\": \"\",
\"code\": \"200\", \"message\": \"OK\" }, \"metadata\": { \"next\":
\"https://feed.myjosh.in/user/feed/latest/\<user_uuid\>?type=image&page=1&rows=10\",
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
\"https://feed.myjosh.in/user/feed/latest/\<user_uuid\>?type=\<news/social\>&page=1&rows=10\",
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
\<zones icon url\> \"cta_text\": \"More Kunal Sanghvi News/Social\"
\"cta\": \"zone deep link\" } } \] }
