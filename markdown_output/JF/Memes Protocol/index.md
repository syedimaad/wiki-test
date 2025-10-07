## Request

+------------------+--------------------+------------------------------+
| **Method**       | **POST**                                          |
+------------------+---------------------------------------------------+
| **URL**          | \<host\>/v1/feed/memes                            |
+------------------+--------------------+------------------------------+
| **Query Params** | collection_uuid    | source collection_uuid of    |
|                  |                    | memes (Optional)             |
|                  +--------------------+------------------------------+
|                  | page               | request page (default - 0)   |
|                  +--------------------+------------------------------+
|                  | rows               | number of elements per page  |
|                  |                    | (default - 10)               |
+------------------+--------------------+------------------------------+
| **Header**       | coolfie-debug-info | appVersion,userLang, etc -   |
|                  |                    | same as for you              |
+------------------+--------------------+------------------------------+
|                  | platform           | Only for IOS/PWA             |
+------------------+--------------------+------------------------------+
| **Payload**      | {                                                 |
|                  |                                                   |
|                  | "clientId": \<clientId\>,                         |
|                  |                                                   |
|                  | "userUuid": \<userUuid\>\>                        |
|                  |                                                   |
|                  | }                                                 |
+------------------+---------------------------------------------------+

**Known Implementation:**

1.  Meme will be a different type of element in content ES

2.  /feed/meme endpoint will take a collection_uuid as a query param
    input

3.  If collection_uuid is given then this api will give memes belonging
    to that collection only

4.  First the decked items of that collection will be served, followed
    by any items that are configured by feedApiConfig

5.  Once the collection exhausts, feed will then start filling random
    memes (foryou memes) → this is to give the feel that collection is
    infinite

6.  Point 5 behaviour needs to be configurable from DSL

**Open Questions:**

1.  Client level history (limited recent history/ session history) or
    past history to be maintained or not?

## Response

{\
\"status\":{\
\"time\":\"21ms\",\
\"server\":\"\",\
\"code\":\"200\",\
\"message\":\"OK\"\
},\
\"metadata\":{\
\"next\":\"\<host\>/feed/memes?collection_uuid=abcd&page=1&rows=10\",\
\"page_info\":{\
\"page_number\":0,\
\"page_size\":10\
}\
},\
\"data\":\[\
{\
\"experiment\":{\
\"attrA\":\"valA\",\
\"attrB\":\"valB\"\
},\
\"content_uuid\":\"String \<meme uuid\>\",\
\"share_count\":\"String \<sum of share_count + fk_shares in cool number
format\>\",\
\"content_title\":\"String \<feed item title content\>\",\
\"like_count\":\"String \<sum of like_count + fk_likes in cool number
format\>\",\
\"share_url\":\"string \<meme deep link\>\",\
\"card_type\":\"meme\",\
\"prepared_content_title\":\"string \<feed items prepared content
title\>\",\
\"icon_url\":\"string \<meme image url\>\",\
\"animated_icon_url\":\"string \<meme gif url\>\",\
\"width\":\"double \<meme width\>\",\
\"height\":\"double \<meme height\>\",\
\"report_url\":\"\<<https://share.myjosh.in/report/content/%3Cmeme%3E>
content uuid\>?reported-by-clientid=\<client
id\>&reported-by-uuid=\<user uuid\>\",\
\"tags\":\"#viral #meme #viralmeme\",\
\"rich_content_title\":\"string \<feed item rich content title\>\",\
\"item_ttl\":1659450876097\
}\
\],\
\"latest_cookie_page_number\":1,\
\"prefetch_download_config\":{\
\"disable_cache\":false,\
\"prefetch_download_count_config\":{\
\"slow\":{\
\"no_of_videos\":8,\
\"min_cache_percentage_ofl_to_onl\":100\
},\
\"average\":{\
\"no_of_videos\":8,\
\"min_cache_percentage_ofl_to_onl\":85\
},\
\"good\":{\
\"no_of_videos\":8,\
\"min_cache_percentage_ofl_to_onl\":70\
},\
\"fast\":{\
\"no_of_videos\":8,\
\"min_cache_percentage_ofl_to_onl\":50\
},\
\"veryfast\":{\
\"no_of_videos\":8,\
\"min_cache_percentage_ofl_to_onl\":50\
}\
}\
}\
}
