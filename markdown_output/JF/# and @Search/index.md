  -------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Method**           Get
  **URL**              {host}/api/entity/{v3}/search?tab_id={HASHTAG/USER}&page=0&row=10
  **Request Header**   Content-Type: application/json,
  **Request Body**     json{ \"page\": 0, \"rows\": 10, \"langs\": \"en\", \"query\": \"kapil\", \"tabId\": ALL, \"cid\": \"f699c4bb-ca35\", \"uid\": \"7dd179f7-6a52-4c20-9f18-cd59475b5e67\", \"city_id\": null, \"state_id\": null }
  -------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**[Response:]{.underline}**

search type HASHTAG will return HashTags, Challenge and Zones(Non human
Zones).

search type USER will return Users and Human zones

→ Below Response is for @ search, which results
Collection\<Collection\<Discovery Feed Asset\>\>

jsonfull-width{ \"status\": { \"time\": \"121ms\", \"server\": \"\",
\"code\": \"200\", \"message\": \"OK\" } \"name\": \"SearchResults\",
\"entity_list\": \[ { \"type\": \"ZONE\", \"count\" : 2, \"heading\" :
{} \"elements\": \[ { \"zone_uuid\":
\"bf758d0c-114e-472e-9156-894219692607\", \"title\": \"Kapil Sharma
Zone\", \"sub_title\": \"Actor & comedian\", \"description\" : \"Zone
description Max twolines\" \"sub_text\": \"SameekshaSud\",
\"thumbnail_url\":
\"https://stream.coolfie.io/stream/prod-ugc-contents/profile_pictures/529f71a771f57cf9/d22e4bec933650b3/529f71a771f57cf9d22e4bec933650b3_300.jpeg\",
\"deep_link_url\":
\"https://share.myjosh.in/profile/bf758d0c-114e-472e-9156-894219692607%22\",
\"display_name\": \"Kapil Sharma\", \"allow_follow\": true,
\"follow_back\": false, \"experiment\": { \"score\": \"20000.0\",
\"algo\": \"trnding zones\", \"search_tag\": \"\" } }, { \"id\":
\"bf758d0c-114e-472e-9156-894219692607\", \"text\": \"Kapil Sharma
Zone\", \"experiment\": { \"score\": \"20000.0\", \"algo\": \"trnding
zones\", \"search_tag\": \"\" }, \"sub_text\": \"SameekshaSud\",
\"thumbnail_url\":
\"https://stream.coolfie.io/stream/prod-ugc-contents/profile_pictures/529f71a771f57cf9/d22e4bec933650b3/529f71a771f57cf9d22e4bec933650b3_300.jpeg\",
\"deep_link_url\":
\"https://share.myjosh.in/profile/bf758d0c-114e-472e-9156-894219692607%22\",
\"display_name\": \"Kapil Sharma\", \"allow_follow\": true,
\"follow_back\": false } }, { \"type\": \"USER\", \"count\" : 2,
\"heading\" : {}, \], \"next_page_url\" :
\"https://feed.coolfie.io/entity/search?tab_id=ZONE&page=1&rows=10\",
\"page_number\": 0 \] }
