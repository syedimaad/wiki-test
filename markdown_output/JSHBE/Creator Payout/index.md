1.  payout balance API

curl \--location \--request GET
\'qa-api.myjosh.in/apij/wallet/payout-balance?user_uuid=Akshay\' \\
\--header \'Cookie: JSESSIONID=E4A20EBC9F099DEF93CAEB504469D925\'
Response: { \"status\": { \"code\": 200, \"message\": \"OK\" },
\"data\": { \"performance_payout_jems\": 2, \"fans_gifted_jems\": 4,
\"misc_jems\": 4, \"conversion_rate\":0.1 }, \"code\": 200 }

1 (b)

curl \--location \--request GET
\'qa-api.myjosh.in/apij/wallet/earnings?user_uuid=Akshay&type=PERFORMANCE_PAYOUT/FANS_GIFT\'
\\ \--header \'Cookie: JSESSIONID=E4A20EBC9F099DEF93CAEB504469D925\'
Response: { \"status\": { \"code\": 200, \"message\": \"OK\" },
\"data\": { \"type\": \"PERFORMANCE_PAYOUT/FANS_GIFT\", \"balance\":
\"22.5k\", \"total_earnings\": \"3.4k\", \"today_earnings\":\"200\" },
\"code\": 200 }

2\. Performance payout of a given user

curl \--location \--request GET
\'http://qa-api.myjosh.in/apij/transaction/user-content-performance?type=\'EXPIRED/ONGOING\'
\\ \--header \'userUUID;\' \\ \--header \'clientID;\' \\ \--header
\'auth-token;\' \\ \--header \'Cookie:
JSESSIONID=E4A20EBC9F099DEF93CAEB504469D925\' Response: { \"status\": {
\"code\": 200, \"message\": \"OK\" }, \"data\":\[ { \"entity_id\": \"\",
\"entity_type\":\"\", \"title\": \"\", \"thumbnail_url\": \"\",
\"share_url\": \"\", \"like_count\": \"23.1k\", \"share_count\": \"\",
\"comments_count\": \"\", \"total_jems\": \"3k\", \"today_jems\":
\"200\" } \], \"metadata\":{ \"next\":\"\" }, \"code\": 200 }

3\. Performance payout on a given content

curl \--location \--request GET
\'http://qa-api.myjosh.in/apij/transaction/content-performance-payout?entity_type=CONTENT/ROOM/PROFILE&entity_id=\<id\>\'
\\ \--header \'userUUID;\' \\ \--header \'clientID;\' \\ \--header
\'auth-token;\' \\ \--header \'Cookie:
JSESSIONID=E4A20EBC9F099DEF93CAEB504469D925\' Response: { \"status\": {
\"code\": 200, \"message\": \"OK\" }, \"data\": \[ {
\"transaction_date\":\"\", \"jems_earned\":\"22.3k\", \"gifts\":\[ {
\"gift_id\":\"\", \"gift_url\":\"\", \"gift_count\":2 } \] } \],
\"metadata\":{ \"next\":\"\" }, \"code\": 200 }

4\. User fan gifts API

API:
http://stage-api.myjosh.in/apij/user/fan-gifts?user_id=028433c8-c858-40d3-877d-e43b55e26b84
API Method:GET Headers: userUUID - \<\> auth-token -\<\> clientID -\<\>
Response : { \"status\": { \"code\": 200, \"message\": \"OK\", \"time\":
\"34\", \"server\": \"10.14.8.69\" }, \"data\": \[ { \"gift_id\":
\"5ee4c585-12f0-4e2a-bfc6-e51449f83292\", \"gift_count\": \"1.1k\",
\"gift_thumbnail_url\": \"\", \"gift_cta\":
\"http://stage-api.myjosh.in/apij/gift/gifters-list?user_uuid=028433c8-c858-40d3-877d-e43b55e26b84&gift_uuid=5ee4c585-12f0-4e2a-bfc6-e51449f83292\",
\"jems_earned\":\"300\" } \], \"code\": 200, \"metadata\": { \"next\":
\"http://stage-api.myjosh.in/apij/content/gifters-list?content_id=028433c8-c858-40d3-877d-e43b55e26b84&rows=1&page=1\"
} }

5\. Gifts by Gift ID and User UUID

API:
http://stage-api.myjosh.in/apij/gift/fan-gifters-list?user_uuid=028433c8-c858-40d3-877d-e43b55e26b84&gift_id=5ee4c585-12f0-4e2a-bfc6-e51449f83292
API Method:GET Headers: userUUID - \<\> auth-token -\<\> clientID -\<\>
Response : { \"status\": { \"code\": 200, \"message\": \"OK\", \"time\":
\"34\", \"server\": \"10.14.8.69\" }, \"data\": \[ { \"name\": \"Mayank
Singh\", \"verified\": false, \"user_uuid\":
\"af4b5b5f-d90f-4a89-a56e-2221de9b4255\", \"user_type\": \"e\",
\"profile_url\":
\"http://stage-api.myjosh.in/apij/user/details/v2/af4b5b5f-d90f-4a89-a56e-2221de9b4255\",
\"profile_pic\":
\"https://stage-stream.myjosh.in/stream/stage-josh-content/profile_pictures/default.png\",
\"account_status\": \"ACTIVE\", \"gift_id\":
\"5ee4c585-12f0-4e2a-bfc6-e51449f83292\". \"gift_count\":\"2.1k\",
\"jems_earned\":\"2.2k\" } \], \"code\": 200, \"metadata\": { \"next\":
\"http://stage-api.myjosh.in/apij/content/gifters-list?content_id=028433c8-c858-40d3-877d-e43b55e26b84&rows=1&page=1\"
} }

6\. Pipeline API

curl \--location \--request GET
\'http://qa-api.myjosh.in/apij/transaction/system-gift\' \\ \--header
\'userUUID;\' \\ \--header \'clientID;\' \\ \--header \'auth-token;\' \\
\--header \'Content-Type: application/json\' \\ \--header \'Cookie:
JSESSIONID=E4A20EBC9F099DEF93CAEB504469D925\' \\ \--data-raw \'{
\"text\":\"gift name\", \"gift_count\":6, \"gift_jems\":200,
\"gift_id\":\"\", \"user_uuid\":\"\", \"entity_type\":\"\",
\"entity_id\":\"\" }\'Queries for Transaction/list type \`all\` select
sum(jems_count),entity_type,entity_id,count(gift_id),gift_id,DATE(modified_on)
modifiedOn from transaction where
transaction_by=\'3dfb98fd-b9a1-4624-8318-bb995d403a46\' group by
entity_type,entity_id,gift_id,DATE(modified_on) order by modifiedOnfrom
desc;

7\. Transaction history

curl \--location \--request GET
\'http://qa-api.myjosh.in/apij/transaction/history?type=PERFORMANCE_PAYOUT/MISC/FANS_GIFT\'
\\ \--header \'userUUID;\' \\ \--header \'clientID;\' \\ \--header
\'auth-token;\' { \"status\": { \"code\": 200, \"message\": \"OK\",
\"time\": \"34\", \"server\": \"10.14.8.69\" }, \"data\": \[ {
\"entity_id\": \"\", \"entity_type\": \"PROFILE/ROOM/CONTENT\",
\"jems_earned\": \"222\", \"transaction_date\": \"\", \"gifts\":\[ {
\"gift_id\": \"\", \"gift_count\": \"2\", \"gift_thumbnail_url\": \"\",
\"gift_bg_color\":\"\", \"gift_name\":\"\" } \] } \], \"code\": 200,
\"metadata\": { \"next\": \"\" } }

8\. Wallet balance

GET API →
`https://stage-api.myjosh.in/apij/wallet?user_uuid={userUUID}&client_id={clientUUID}`

{ \"status\": { \"code\": 200, \"message\": \"OK\" }, \"data\": {
\"wallet_of\": \"ccdff68a-c786-4c8d-9378-7303fef659e6\",
\"kyc_details\": { \"status\": \"SUCCESS\", \"pan_card\": \"PAN_CARD\",
\"name\": \"XYZ\" }, \"beneficiary_details\": \[ { \"account_type\":
\"UPI\", \"beneficiary_id\": \"639751355bd0ab381b42ba66\", \"status\":
\"SUCCESS\", \"account_number\": \"8920886795@paytm\" } \] }, \"code\":
200 }

9\. To get bank names

curl \--location \--request GET
\'[qa-api.myjosh.in/apij/josh-payment/bank-list](http://qa-api.myjosh.in/apij/josh-payment/bank-list)\'
\\ \--header \'userUUID: c5f8ecf3-adb5-45e1-b228-dcd388a2033d\' \\
\--header \'auth-token: 370a5c1d21ddad4906ea8357339076aa\' \\ \--header
\'clientID;\' \\ \--header \'Cookie:
JSESSIONID=B7E4229722C86284C2279B35199CF468\'

\[ { \"id\": \"1\", \"name\": \"HDFC BANK\", \"icon_url\":
\"https://qa-stream.myjosh.in/stream/qa-josh-content/wallet/hdfc_bank.png\"
} \]

10\. Create beneficiary

curl \--location \--request POST
\'qa-api.myjosh.in/apij/josh-payment/create-beneficiary\' \\ \--header
\'Content-Type: application/json\' \\ \--data-raw \'{ \"type\":
\"UPI/BANK_ACCOUNT\", \"vpa\": \"8920886795@ybl\", \"email\":
\"singh.monika.23.1998@gmail.com\", \"name\": \"Monika Singh\",
\"telephone\": \"+918920886795\", \"shortName\":\"Monika\",
\"isDefault\": true, \"isActive\": true,
\"user_id\":\"738005a8-9ea6-4e02-8162-8f2721fba517\",
\"accountNumber\":\"\", \"ifscCode\":\"\", \"refno\":\"\" }\'

11\. To check validity of ifsc code

curl \--location \--request GET
\'qa-api.myjosh.in/apij/josh-payment/validate-ifsc?ifsc_code=120304\' \\
\--header \'userUUID: c5f8ecf3-adb5-45e1-b228-dcd388a2033d\' \\
\--header \'auth-token: 370a5c1d21ddad4906ea8357339076aa\' \\ \--header
\'clientID;\' \\ \--header \'Cookie:
JSESSIONID=95C614F053824137676A9F665E048DC9\'{ \"ifsc_code\":
\"120304\", \"is_valid\": \"Y\", \"bank_name\": \"Sarjapur Road, HDFC
Bank\", \"partial_ifsc_codes\": null }

12\. List of beneficiaries

curl \--location \--request GET
\'qa-api.myjosh.in/apij/josh-payment/beneficiary-list?user_id\' \\
\--header \'Cookie: JSESSIONID=C6E2ED413BA40A55F19278F5CDE1EBD2\'{
\"kyc_status\": { \"status\": \"SUCCESS/IN_PROGESS/FAILED\",
\"pan_card\": \"\", \"name\": \"\" }, \"beneficiaries\": \[ {
\"account_type\": \"BANK_ACCOUNT/UPI\", \"account_number\": \"bank
name + last 4 digits/UPI id\", \"status\": \"IN_PROGESS/VERIFIED\",
\"profile_pic\": \"\", \"beneficiary_id\": \"\" } \] }

13\. Slider blocks available

curl \--location \--request GET
\'qa-wallet-internal.myjosh.in/api/v1/josh-payment/slider\' \\ \--header
\'userUUID;\' \\ \--header \'clientID;\' \\ \--header \'auth-token;\'{
jems_balance: 865, start_point: 170, end_point : 860,
primary_checkpoint: 100, secondary_checkpoint: 50, tertiary_checkpoint:
10 }

14\. Redeem calculation API

curl \--location \--request POST
\'qa-api.myjosh.in/apij/transaction/redeem-calculation\' \\ \--header
\'Content-Type: application/json\' \\ \--header \'userUUID;\' \\
\--header \'clientID;\' \\ \--header \'auth-token;\' \\ \--header
\'Cookie: JSESSIONID=48E516594415B3FFC618A3B95798CEF3\' \\ \--data-raw
\'{ \"fg_jems_used\":12, \"pp_jems_used\":24,
\"transaction_id\":\"sban\" }\' { \"fg_jems\":12, \"fg_inr\":10,
\"pp_jems\":12, \"pp_inr\":10, \"total_amount\":123,
\"bonus_percent\":16, \"bonus_amount\":123, \"total_with_bonus\":246,
\"pf_percent\":16, \"pf_amount\":123, \"net_amount\":123,
\"tds_percent\":10, \"tds_amount\":123, \"final_amount\":100,
\"transaction_id\":\"59a393c6-7041-4bcd-b60b-2f930c4d8400\",
\"user_id\":\"fbaa882d-cfc6-4ebd-ae44-a3b8c1c1fw148\" }

15\. create order

curl \--location \--request POST
\'qa-api.myjosh.in/apij/josh-payment/redeem\' \\ \--header \'userUUID;\'
\\ \--header \'clientID;\' \\ \--header \'auth-token;\' \\ \--header
\'Content-Type: application/json\' \\ \--header \'Cookie:
JSESSIONID=A1050FBE8740B722057384112D8E12AC\' \\ \--data-raw \'{
\"payload\":\"{\\\"redeem_amount\\\":1,\\\"beneficiary_id\\\":\\\"639751355bd0ab381b42ba66\\\",\\\"jems_count\\\":1,\\\"fg_jems_used\\\":1,\\\"transaction_id\\\":\\\"2596cd75-d0bd-4b3c-8652-888a04197706\\\"}\"
}\'

16\. Redeem Breakup

curl \--location \--request POST
\'qa-wallet-internal.myjosh.in/api/v1/josh-payment/redeem-breakup\' \\
\--header \'userUUID;\' \\ \--header \'clientID;\' \\ \--header
\'auth-token;\' \\ \--header \'Content-Type: application/json\' \\
\--data-raw \'{ selected_jems : 450 }\'{ fan_jems : 300,
performance_jems : 150 }

**[Doubts]{style="color: rgb(255,86,48);"}**

1.  Transaction history is all clubbed up now → how to handle that

2.  gifts by gift id and user id → how do i club them based on date?

3.  
