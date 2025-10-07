## Request

+------------------+--------------------+------------------------------+
| **Method**       | **GET**                                           |
+------------------+---------------------------------------------------+
| **URL**          | \<host\>/zone/page/{zone_id}/                     |
+------------------+--------------------+------------------------------+
| **Path Params**  | zone_id            | zone_id of page to load      |
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
| **Payload**      | {                                                 |
|                  |                                                   |
|                  | "clientId": \<clientId\>,                         |
|                  |                                                   |
|                  | "userUuid": \<userUuid\>\>                        |
|                  |                                                   |
|                  | }                                                 |
+------------------+---------------------------------------------------+

 

## Response

{\
\"name\":\"\<Zone Page Name\>\",\
\"meta\":{\
\"next\":\"\<host\>/page/zone/{zone_id}?page=1&rows=10\",\
\"page_info\":{\
\"page_number\":0,\
\"page_size\":10\
}\
},\
\"entity_list\":\[\
{\
\"heading\":{\
\"type\":\"NAMED_COLLECTION\",\
\"title\":\"Related\"\
},\
\"elements\":\[\
{\
\"title\":\"\<zone page1 name\>\",\
\"subtitle\":\"\<zone1 subtitle\>\",\
\"follow\":\"true/false\",\
\"thumbnail\":\"\<zone page1 thumbnail\>\",\
\"element_cta\":\"\<host\>/page/zone/\<zone_id1\>?page=1&rows=10\",\
\"element_uuid\":\"\<zone_id1\>\",\
\"elements\":\[\
{\
\"element_uuid\":\"\<content1_uuid\>\",\
\"thumbnail\":\"\<content1_thumbnail\>\"\
},\
{\
\"element_uuid\":\"\<content2_uuid\>\",\
\"thumbnail\":\"\<content2_thumbnail\>\"\
}\
\],\
\"stats\":{\
\"followers\":\"\<no of followers\>\",\
\"posts\":\"\<no of posts\>\"\
}\
},\
{\
\"title\":\"\<zone page2 name\>\",\
\"subtitle\":\"\<zone page2 subtitle\>\",\
\"follow\":\"true/false\",\
\"thumbnail\":\"\<zone page2 thumbnail\>\",\
\"element_cta\":\"\<host\>/page/zone/{zone_id2}?page=1&rows=10\",\
\"element_uuid\":\"\<zone id2\>\",\
\"elements\":\[\
{\
\"element_uuid\":\"\<content1_uuid\>\",\
\"thumbnail\":\"\<content1_thumbnail\>\"\
},\
{\
\"element_uuid\":\"\<content2_uuid\>\",\
\"thumbnail\":\"\<content2_thumbnail\>\"\
}\
\],\
\"stats\":{\
\"memes\":\"\<no of memes\>\"\
}\
}\
\],\
\"experiment\":{\
\"expA\":\"valA\",\
\"expB\":\"valB\"\
},\
\"collection_uuid\":\"\<zone_id\>\",\
\"element_type\":\"ZONE\",\
\"collection_type\":\"NAMED_COLLECTION\",\
\"layout_type\":\"LAYOUT_TYPE_1\"\
},\
{\
\"elements\":\[\
{\
\"title\":\"Videos\",\
\"element_cta\":\"\<host\>/zone/video/latest/\<zone_id\>\",\
\"element_uuid\":\"\<zone_id\>\_video\"\
},\
{\
\"title\":\"Images\",\
\"element_cta\":\"\<host\>/zone/image/latest/\<zone_id\>\",\
\"element_uuid\":\"\<zone_id\>\_image\"\
},\
{\
\"title\":\"Social\",\
\"element_cta\":\"\<host\>/zone/social/latest/\<zone_id\>\",\
\"element_uuid\":\"\<zone_id\>\_social\"\
},\
{\
\"title\":\"News\",\
\"element_cta\":\"\<host\>/zone/news/latest/\<zone_id\>\",\
\"element_uuid\":\"\<zone_id\>\_news\"\
}\
\],\
\"experiment\":{\
\"expA\":\"valA\",\
\"expB\":\"valB\"\
},\
\"collection_uuid\":\"\<zone_id\>\",\
\"element_type\":\"TABS\",\
\"collection_type\":\"NAMED_COLLECTION\",\
\"layout_type\":\"LAYOUT_TYPE_1\"\
}\
\],\
\"share_url\":\"<https://share.myjosh.in/zone/page/%7Bzone_id%7D%22>\
}
