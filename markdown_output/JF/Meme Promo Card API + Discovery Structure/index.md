+-------------+--------------------+-----------------------------------+
| **Method**  | **POST**                                               |
+-------------+--------------------------------------------------------+
| **URL**     | \<host\>/v1/feed/promo/memes                           |
+-------------+--------------------+-----------------------------------+
| **Header**  | coolfie-debug-info | appVersion,userLang, etc - same   |
|             |                    | as for you                        |
|             |                    |                                   |
|             +--------------------+-----------------------------------+
|             | platform           | Only for IOS/PWA                  |
+-------------+--------------------+-----------------------------------+
| **Payload** | {                                                      |
|             |                                                        |
|             | "clientId": \<clientId\>,                              |
|             |                                                        |
|             | "userUuid": \<userUuid\>\>                             |
|             |                                                        |
|             | }                                                      |
+-------------+--------------------------------------------------------+

**Known Implementation:**

1.  There will one service which would return a list of paginated memes
    (ugc feed assets) from a specific/random collection

2.  These memes will be converted to discovery asset for serving as
    promo card or in discovery

3.  Push/Pull promo card will this service and create a promo card out
    of it

**Open Questions:**

1.  Should we consider userHistory before presenting Card (like not show
    same collection again as promo card) ? Suggestion : Recent Actions
    should be consider for start.

**[Response:]{.underline}**

{\
\"status\":{\
\"time\":\"20ms\",\
\"server\":\"\",\
\"code\":\"200\",\
\"message\":\"OK\"\
},\
\"data\":\[\
{\
\"heading\":{\
\"type\":\"NAMED_COLLECTION\",\
\"title\":\"Trending Memes\",\
\"subtitle\":\"Check out these memes\",\
\"data\":{\
\"inline_cta_text\":\"See all\",\
\"inline_cta\":\"\<host\>/v1/feed/memes?collection_uuid=\<collection_uuid\>&page=1&rows=15\"\
}\
},\
\"elements\":\[\
{\
\"title\":\"string meme content title\",\
\"thumbnail\":\"string \<meme picture url\>\",\
\"animated_thumbnail\":\"string \<meme gif url\>\",\
\"element_uuid\":\"string \<meme content uuid\>\",\
\"elementCta\":\"string \<meme deeplink\>\",\
\"is_trending\":\"boolean \<if meme is trending or not\>\",\
\"label\":\"string \<placeholder to display tag on top of meme\>\",\
\"like_count\":\"String \<sum of like_count + fk_likes in cool number
format\>\",\
\"share_count\":\"String \<sum of share_count + fk_shares in cool number
format\>\",\
\"width\":\"double \<meme width\>\",\
\"height\":\"double \<meme height\>\",\
\"cta_data\":{\
\"inline_cta\":\"\<meme deeplink\>\",\
\"inline_cta_text\":\"Share on whatsapp\"\
},\
\"experiment\":{\
\"attrA\":\"valA\",\
\"attrB\":\"valB\"\
}\
}\
\],\
\"card_type\":\"MEME_CARD\",\
\"element_type\":\"MEME\",\
\"collection_type\":\"NAMED_COLLECTION\",\
\"layout_type\":\"MEME_LIST_CARD\",\
\"is_trending\":false,\
\"swipe_stream_url\":\"\<host\>/v1/feed/memes?collection_uuid=\<collection_uuid\>&page=0&rows=15\"\
}\
\]\
}

**Notes:**

1.  Same object will be served in discovery as a collection having
    heading, elements and other attributes
