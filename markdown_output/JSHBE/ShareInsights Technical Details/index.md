https://www.figma.com/file/SWfkbuRYnkTQ8GcNtyBBrU/Notification?node-id=5610-19538

**Changes in the Services**

Gateway

Onboard API

Social Notification Service

**Gateway Service**

1.  User profiles section to have the Share Insights for the Logged in
    Users

**Onboard API**

1.  /beacon/share

    1.  When a user clicks on shared content -\>

        1.  Storing the user id with timestamp corresponding to the
            respective client id (shared_by_client_id) and content id in
            Redis\
            Redis key →
            share_entity_click_info\_{client_id}\_{content_id}

        2.  for the above Redis key, a limited user uuid data is being
            stored (10, as of now)

curl \--location \--request POST
\'https://qa-api.myjosh.in/apij/beacon/share\' \\ \--header \'app-id:
JOSH_APP\' \\ \--header \'auth-token: 2fb46f12b6c9b115e108d8be62a995af\'
\\ \--header \'clientID: j.SlJGWlcyaVRUVjZ0TEJyZlJ5cENQZz09A\' \\
\--header \'userUUID: 441fe978-1399-46f9-8c86-7ed165485b7e\' \\
\--header \'Content-Type: application/json\' \\ \--header \'Cookie:
JSESSIONID=9CAB08C4C0E8EF49C58689D3186EE7B3\' \\ \--data-raw \'{
\"opened_by_cid\": \"monika.singh@verse.in\", \"share_token\":
\"0x7335015276aba188\", \"entity_id\":
\"597c0dab-0b6b-49ea-b553-513ec9067476\", \"entity_type\": \"VIDEO\",
\"ts\": 1679899320307 }\'

2\. /activity/share/content-list

1.  To get the list of contents shared by the user with count (no. of
    times, the shared video was clicked by a user)

    curl \--location \--request GET
    \'https://qa-api.myjosh.in/apij/activity/share/content-list?page=0&rows=10\'
    \\ \--header \'app-id: JOSH_APP\' \\ \--header \'auth-token:
    bcfdf60ac18c21f2f37a20a35d0de674\' \\ \--header \'clientID:
    j.SlJGWlcyaVRUVjZ0TEJyZlJ5cENQZz09A\' \\ \--header \'userUUID:
    ccdff68a-c786-4c8d-9378-7303fef659e6\' \\ \--header \'Cookie:
    JSESSIONID=36D262BE1A576CAA4606D2334231C227\'

3\. /activity/share/content-visitors-list

1.  To get the list of visitor details who have clicked the shared
    content

    curl \--location \--request GET
    \'https://qa-api.myjosh.in/apij/activity/share/content-visitors-list?id=c78f3b06-9f50-46e9-adf9-b42f07346f69&page=0&rows=10\'
    \\ \--header \'Cookie: JSESSIONID=3F87CD2FE83A2B390319AF38B0C6853E;
    JSESSIONID=36D262BE1A576CAA4606D2334231C227\' \\ \--header \'app-id:
    JOSH_APP\' \\ \--header \'auth-token:
    bcfdf60ac18c21f2f37a20a35d0de674\' \\ \--header \'clientID:
    j.SlJGWlcyaVRUVjZ0TEJyZlJ5cENQZz09A\' \\ \--header \'userUUID:
    ccdff68a-c786-4c8d-9378-7303fef659e6\'

**Social Notification Service**
