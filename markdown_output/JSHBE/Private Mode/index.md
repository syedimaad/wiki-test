1.  **Private Client Register**

End Point: qa-**api.mypjosh.in**/apij/private/onboard

curl:

curl \--location \--request POST
\'qa-api.myjosh.in/apij/private/onboard\' \\ \--header
\'coolfie-debug-info:
appVersion=7.8.0.2303311309.2&osVersion=8.1.0&clientId=p.RlZZbGQ4L0s2L2RZd0lCdlA0c0Nsdz09A&androidId=&installSource=CoolfieHome\^7.8.0\^PLAYSTORE&user_lang=en&nav_lang=en&width=720&height=1280&user_interest=&app_install_date=1680255302839&clv=\'
\\ \--header \'Content-Type: application/json; charset=UTF-8\' \\
\--header \'Connection: Keep-Alive\' \\ \--header \'Cookie:
JSESSIONID=25FA3C6C14744167CCDE1EBC9F95EF78\' \\ \--data-raw \'{
\"clientId\":\"p.RlZZbGQ4L0s2L2RZd0lCdlA0c0Nsdz09B\", \"markedDelete\":
true // If user is deleted create new user }\'

Response:

{ \"status\": { \"code\": 200, \"message\": \"OK\", \"time\": \"20129\",
\"server\": \"172.16.41.255\" }, \"data\": { \"handle\": \"nTko9339\",
\"user_id\": \"b1cf6e71-3df4-4eb0-b000-bbf30ba12fd2\",
\"profile_image\":
\"https://qa-stream.myjosh.in/stream/qa-josh-content/JoshProfilePics/image_9_default.png\",
\"user_name\": \"nTko9339\", \"client_id\":
\"p.RlZZbGQ4L0s2L2RZd0lCdlA0c0Nsdz09B\", \"auth_token\":
\"1b3829d5192602f4f3a9b40667f6fc33\" }, \"code\": 200 }

Conditions:

→ If user is deleted `"markedDelete": true` create new user.

→ If client Id already present fetch user data

→ If new client Id, create new user and entry in Cid table

Note: No entry in kinesis

**2. POST backup**

curl:

curl \--location \--request POST
\'qa-api.mypjosh.in/apij/private/client/backup\' \\ \--header
\'coolfie-debug-info:
appVersion=7.8.0.2303311309.2&osVersion=8.1.0&clientId=p.RPZZbGQ4L0s2L2RZd0lCdlA0c0Nsdz09A&androidId=&installSource=CoolfieHome\^7.8.0\^PLAYSTORE&user_lang=en&nav_lang=en&width=720&height=1280&user_interest=&app_install_date=1680255302839&clv=\'
\\ \--header \'Content-Type: application/json\' \\ \--header \'Cookie:
JSESSIONID=DA89F8EA096312AB39286C521697D091\' \\ \--data-raw \'{
\"backup\":{ \"passcode\":\"dummy\", \"questions\":\"dummy\" } }\'

Response:

{ \"status\": { \"code\": 200, \"message\": \"OK\", \"time\": \"154\",
\"server\": \"10.12.4.112\" }, \"code\": 200 }

**3. GET Backup**

curl:

curl \--location \--request GET
\'qa-api.myjosh.in/apij/private/client/backup\' \\ \--header
\'coolfie-debug-info:
appVersion=7.8.0.2303311309.2&osVersion=8.1.0&clientId=p.RPZZbGQ4L0s2L2RZd0lCdlA0c0Nsdz09A&androidId=&installSource=CoolfieHome\^7.8.0\^PLAYSTORE&user_lang=en&nav_lang=en&width=720&height=1280&user_interest=&app_install_date=1680255302839&clv=\'
\\ \--header \'Cookie: JSESSIONID=9353B759DF4FB67F0ADDCC4D517D048D\' \\
\--data-raw \'\'

Response:

{ \"status\": { \"code\": 200, \"message\": \"OK\", \"time\": \"41\",
\"server\": \"10.12.4.112\" }, \"data\": { \"backup\": { \"questions\":
\"dummy\", \"passcode\": \"dummy\" }, \"client_id\":
\"p.RPZZbGQ4L0s2L2RZd0lCdlA0c0Nsdz09A\" }, \"code\": 200 }

**Share Path Changes:**

share_url -\>
https://share.myjosh.in/content/76d3cdb6-d840-4fd7-b40f-b4c04237d083
private_share_url -\>
https://share.myjosh.in/private/content/76d3cdb6-d840-4fd7-b40f-b4c04237d083
https://api.myjosh.in/share/content/76d3cdb6-d840-4fd7-b40f-b4c04237d083
if( content.private_content){ if( platform == PWA ){ return message =
\"Private Content\" {code-200} } if( platform == ANDROID){ if(
appversion \> 8.0.0){ return message = \"Private Content\" {code-200}
}else { return 204 } } if( platform == IOS){ if( appversion \> 7.0.0){
return message = \"Private Content\" {code-200} }else { return 204 } } }
https://api.myjosh.in/share/private/content/76d3cdb6-d840-4fd7-b40f-b4c04237d083
if( content.private_content){ if( platform == PWA ){ return message =
\"Private Content\" {code-200} } if( platform == ANDROID){ if(
appversion \> 8.0.0){ return data {code-200} }else { return 204 } } if(
platform == IOS){ if( appversion \> 7.0.0){ return data {code-200} }else
{ return 204 } } }

**Private Account Delete:**

→ User will be deleted permanently instantly

curl \--location \--request POST
\'http://localhost:8080/apij/user/private/delete-account\' \\ \--header
\'userUUID: 25b0d2e6-0ea3-4c45-a7f2-eb2a66b5cb03\' \\ \--header
\'clientID: p.N2RvNzNoVEdGckNobUL2ZNUT09A\' \\ \--header \'auth-token:
ed88f60799397976b6215c4e5fe2fbfa\' \\ \--header \'Cookie:
JSESSIONID=97C19F3148A17280C8893A8301584E5E\'

**Reaction flow changes -\>**

{/activity/reaction} -\> In case the user is in private mode and
performs a reaction, private_mode field is set TRUE for the reaction and
stored in db. {/activity/reaction/user-list} -\> if user is not in
private mode -\> {response -\> user-list for reactions for which
private_mode!=TRUE}

**Comment flow changes -\>**

{/comments/create} -\> In case the user is in private mode and does a
comment, private_mode field is set TRUE for the comment and stored in
db. {/comments/list} -\> if user is not in private mode -\> {response
-\> user-list for comments for which private_mode!=TRUE} {/comments/get}
-\> if user is not in private mode -\> {response -\> user-list for
replies to a comment for which private_mode!=TRUE}

**Feed API Changes:-**

\`show_private_nudge\` -\> Flag for glamour content (To show Private
Nudge)

**TODO:**

1.  Testing: Prod share path
