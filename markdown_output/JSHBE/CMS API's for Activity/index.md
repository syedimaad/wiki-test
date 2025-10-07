## Activity Detail APIs (Onboard Java)

#### 1. Get All Activities {#get-all-activities style="margin-left: 30.0px;"}

GET `apij/activities`

#### **Sample Curl** {#sample-curl style="margin-left: 60.0px;"}

`curl --location --request GET 'https://stage-api.coolfie.io/apij/activities'`

#### 2. Get a single Activity info {#get-a-single-activity-info style="margin-left: 30.0px;"}

GET `apij/activities/{activityId}`

#### **Sample Curl** {#sample-curl-1 style="margin-left: 60.0px;"}

`curl --location --request GET 'https://stage-api.coolfie.io/apij/activities/70b9e2cd-603c-4c74-90c9-f06e2c0ab23e'`

#### 3. Create an Activity {#create-an-activity style="margin-left: 30.0px;"}

POST `apij/activities`

#### **Sample Curl** {#sample-curl-2 style="margin-left: 60.0px;"}

jsoncurl \--location \--request POST
\'https://stage-api.coolfie.io/apij/activities\' \\ \--header
\'auth-token: a19def55e0df6f2b7475ea1e96dff610\' \\ \--header
\'clientID: josh.bulk.user@verse.in\' \\ \--header \'user-uuid:
7e50660b-8b72-447d-8dfc-8920981b289c\' \\ \--header \'Cookie:
JSESSIONID=1DD92E6AB5C43B15BC6CAB9741FD51F9\' \\ \--form
\'title=\"Sab-1\"\' \\ \--form \'subTitle=\"Sab-1\"\' \\ \--form
\'description=\"Sab is a something-1\"\' \\ \--form
\'status=\"ACTIVE\"\' \\ \--form \'activityType=\"WATCH\"\' \\ \--form
\'intervalType=\"DAILY\"\' \\ \--form \'reReward=\"false\"\' \\ \--form
\'jemsCount=\"50\"\' \\ \--form \'requiredStatsCount=\"10\"\' \\ \--form
\'startTime=\"1645015896000\"\' \\ \--form
\'expireTime=\"1645707096000\"\' \\ \--form
\'rewardExpression=\"userActivityImpression.impressionCount \> 400 ?
\`MILESTONE\_!\` : userActivityImpression.impressionCount \> 50 &&
userActivityImpression.impressionCount \< 200 ? \`MILESTONE_2\` :
userActivityImpression.impressionCount \< 50 ?
\`BOOSTER_1\`:\'\\\'\'\'\\\'\'\"\' \\ \--form
\'iosRewardExpression=\"userActivityImpression.impressionCount \> 400 ?
\`MILESTONE\_!\` : userActivityImpression.impressionCount \> 50 &&
userActivityImpression.impressionCount \< 200 ? \`MILESTONE_2\` :
userActivityImpression.impressionCount \< 50 ?
\`BOOSTER_1\`:\'\\\'\'\'\\\'\'\"\' \\ \--form
\'nudgeExpression=\"userActivityImpression.impressionCount \> 400 ?
\`MILESTONE\_!\` : userActivityImpression.impressionCount \> 50 &&
userActivityImpression.impressionCount \< 200 ? \`MILESTONE_2\` :
userActivityImpression.impressionCount \< 50 ?
\`BOOSTER_1\`:\'\\\'\'\'\\\'\'\"\' \\ \--form
\'iosNudgeExpression=\'nudgeExpression=\"userActivityImpression.impressionCount
\> 400 ? \`MILESTONE\_!\` : userActivityImpression.impressionCount \> 50
&& userActivityImpression.impressionCount \< 200 ? \`MILESTONE_2\` :
userActivityImpression.impressionCount \< 50 ?
\`BOOSTER_1\`:\'\\\'\'\'\\\'\'\"\' \\ \--form
\'resetImpressions=\"true\"\' \\ \--form \'viewOrder=\"10\"\' \\ \--form
\'version=\"V1\"\' \\ \--form \'deeplinkUrl=\"url\"\' \\ \--form
\'deeplinkCta=\"cta\"\' \\ \--form
\'iconUrl=@\"/home/varikutitheja/Desktop/sample-files/test1.jpg\"\'

#### 4. Update an Activity {#update-an-activity style="margin-left: 30.0px;"}

POST `apij/activities/{activityId}`

#### **Sample Curl** {#sample-curl-3 style="margin-left: 60.0px;"}

jsoncurl \--location \--request POST
\'https://stage-api.coolfie.io/apij/activities/70b9e2cd-603c-4c74-90c9-f06e2c0ab23e\'
\\ \--header \'auth-token: a19def55e0df6f2b7475ea1e96dff610\' \\
\--header \'clientID: josh.bulk.user@verse.in\' \\ \--header
\'user-uuid: 7e50660b-8b72-447d-8dfc-8920981b289c\' \\ \--header
\'Cookie: JSESSIONID=1DD92E6AB5C43B15BC6CAB9741FD51F9\' \\ \--form
\'title=\"Sab-4\"\' \\ \--form \'subTitle=\"Sab-4\"\' \\ \--form
\'description=\"Sab is a something-4\"\' \\ \--form
\'status=\"ACTIVE\"\' \\ \--form \'activityType=\"WATCH\"\' \\ \--form
\'intervalType=\"DAILY\"\' \\ \--form \'reReward=\"false\"\' \\ \--form
\'intervalTime=\"1\"\' \\ \--form \'jemsCount=\"50\"\' \\ \--form
\'requiredStatsCount=\" 5\"\' \\ \--form \'startTime=\"1645015896000\"\'
\\ \--form \'expireTime=\"1645707096000\"\' \\ \--form
\'rewardExpression=\"userActivityImpression.impressionCount \> 400 ?
\`MILESTONE\_!\` : userActivityImpression.impressionCount \> 50 &&
userActivityImpression.impressionCount \< 200 ? \`MILESTONE_2\` :
userActivityImpression.impressionCount \< 50 ?
\`BOOSTER_1\`:\'\\\'\'\'\\\'\'\"\' \\ \--form
\'nudgeExpression=\"userActivityImpression.impressionCount \> 400 ?
\`MILESTONE\_!\` : userActivityImpression.impressionCount \> 50 &&
userActivityImpression.impressionCount \< 200 ? \`MILESTONE_2\` :
userActivityImpression.impressionCount \< 50 ?
\`BOOSTER_1\`:\'\\\'\'\'\\\'\'\"\' \\ \--form
\'resetImpressions=\"true\"\' \\ \--form \'viewOrder=\"40\"\' \\ \--form
\'version=\"V2\"\'

## Activity Nudge APIs (Gateway Java)

#### 1. Get All Activity Nudges {#get-all-activity-nudges style="margin-left: 30.0px;"}

GET `api/v1/activity/nudge?langCode={langCode}`

#### **Sample Curl** {#sample-curl-4 style="margin-left: 60.0px;"}

`curl --location --request GET 'https://stage-gateway.coolfie.io/api/v1/activity/nudge?langCode=en'`

#### 2. Get a single Activity Nudge info {#get-a-single-activity-nudge-info style="margin-left: 30.0px;"}

GET `api/v1/activity/nudge/{activityNudgeId}`

#### **Sample Curl** {#sample-curl-5 style="margin-left: 60.0px;"}

`curl --location --request GET 'https://stage-gateway.coolfie.io/api/v1/activity/nudge/3'`

#### 3. Create an Activity Nudge {#create-an-activity-nudge style="margin-left: 30.0px;"}

POST `api/v1/activity/nudge`

#### **Sample Curl** {#sample-curl-6 style="margin-left: 60.0px;"}

jsoncurl \--location \--request POST
\'https://stage-gateway.coolfie.io/api/v1/activity/nudge\' \\ \--form
\'title=\"Sab-3\"\' \\ \--form \'subTitle=\"Sab-3\"\' \\ \--form
\'activityType=\"Something\"\' \\ \--form \'templateName=\"Some
template\"\' \\ \--form \'templateType=\"TYpe\"\' \\ \--form
\'templatePlacement=\"middle\"\' \\ \--form \'isMacroEnabled=\"false\"\'
\\ \--form
\'iconUrl=@\"/home/varikutitheja/Desktop/sample-files/test\*multiply.jpg\"\'
\\ \--form \'pageType=\"ForYou\"\' \\ \--form
\'triggerPointToShow=\"VideoWatch\"\' \\ \--form
\'controllerPoint=\"Home\"\' \\ \--form \'deeplinkCta=\"cta\"\' \\
\--form \'deeplinkUrl=\"url\"\' \\ \--form \'viewOrder=\"10\"\' \\
\--form \'displayTime=\"3\"\' \\ \--form \'maxNoOfDisplayTimes=\"5\"\'
\\ \--form \'intervalTime=\"0.5\"\' \\ \--form \'isActive=\"true\"\' \\
\--form \'langCode=\"hi\"\'

#### 4. Update an Activity {#update-an-activity-1 style="margin-left: 30.0px;"}

POST `api/v1/activity/nudge/{activityNudgeId}`

#### **Sample Curl** {#sample-curl-7 style="margin-left: 60.0px;"}

jsoncurl \--location \--request POST
\'https://stage-gateway.coolfie.io/api/v1/activity/nudge/3\' \\ \--form
\'title=\"Sab-4\"\' \\ \--form \'subTitle=\"Sab-4\"\' \\ \--form
\'iconUrl=@\"/home/varikutitheja/Desktop/sample-files/test1.jpg\"\' \\
\--form \'langCode=\"te\"\'

#### 5. Version update for the Activity Nudge {#version-update-for-the-activity-nudge style="margin-left: 30.0px;"}

POST `api/v1/activity/nudge/version/update?langCode={langCode}`

#### **Sample Curl** {#sample-curl-8 style="margin-left: 60.0px;"}

`curl --location --request POST 'https://stage-gateway.coolfie.io/api/v1/activity/nudge/version/update?langCode=en'`
