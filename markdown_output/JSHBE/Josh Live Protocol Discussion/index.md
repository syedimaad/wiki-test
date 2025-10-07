- Total Jems for a User → With periodic refresh

- GET API →
  `https://stage-api.myjosh.in/apij/wallet?user_uuid={userUUID}&client_id={clientUUID}`

  - Json Below

    Jems balance: { user_uuid String jems_balance Int claps_balance Int
    }

- Total Jems for a User → With periodic refresh

- GET API →
  `https://stage-api.myjosh.in/apij/wallet/affiliate-balance?user_uuid={userUUID}`

  - Json Below

    Jems balance: { user_uuid String jems_balance Int }

- Transaction list API

- GET API →
  `http://qa-api.myjosh.in/apij/transaction/list?user_uuid=6749cab4-851a-40e5-a0e8-e930a5d22e76&type=jems`

  - Json Below

    { \"status\": { \"code\": 200, \"message\": \"ok\", \"time\":
    \"34\", \"server\": \"10.12.4.112\" }, \"data\": { \"balance\": 10,
    \"claps_balance\":10 \"rows\": \[ { \"transaction_id\":
    \"98567bb1-7ff2-4f27-aaf5-cf68424b8b49\", \"transaction_type\":
    \"CREDIT\", \"type\": \"AFFILIATE_PURCHASE\", \"text\": \"Top shares
    on 07-04-2022\", \"transaction_date\": \"Apr 11, 2022\", \"status\":
    \"SUCCESS\", \"claps_count\": 10, } \] }, \"metaData\": { \"next\":
    null }, \"code\": 200 }

- Affiliate Transaction list API

- GET API →
  `http://qa-api.myjosh.in/apij/transaction/affiliate-list?user_uuid=6749cab4-851a-40e5-a0e8-e930a5d22e76&type=jems`

  - Json Below

    { \"status\": { \"code\": 200, \"message\": \"ok\", \"time\":
    \"34\", \"server\": \"10.12.4.112\" }, \"data\": { \"balance\":
    20,(jems + claps balance) \"rows\": \[ { \"transaction_id\":
    \"98567bb1-7ff2-4f27-aaf5-cf68424b8b49\", \"transaction_type\":
    \"CREDIT\", \"type\": \"AFFILIATE_PURCHASE\", \"text\": \"Top shares
    on 07-04-2022\", \"transaction_date\": \"Apr 11, 2022\", \"status\":
    \"SUCCESS\", \"amount\": 10, } \] }, \"metaData\": { \"next\": null
    }, \"code\": 200 }

- Gift List → versioned api

  - GET API →
    <https://stage-api.myjosh.in/apij/gift/list>?entity_type={type}&entity_id={id}

  - Json below

    json\[ { gift_collection_uuid title tag thumbnail_url gift_list: \[
    { gift_element_uuid title gift_share_url gift_thumbnail_url
    orig_price discount_percentage discounted_price jems_count
    gift_animated_url } \] } \]

- Jems product list ( with offers and orig price ) → To return the
  current Live sale → with periodic refresh

  - Get API →
    <https://stage-api.myjosh.in/apij/package/active>?entity_type={type}&entity_id={id}

  - Json Below

    { package_collection_uuid collection_name start_time end_time
    sale_share_url sale_thumbnail_url package_entities : \[ {
    package_element_uuid title tag: { colour title } orig_price
    discount_percentage discounted_price jems_count package_url
    package_thumbnail_url currency default_currency product_info:\[ {
    platform: android product_id }, { platform: ios product_id } \] } \]
    }

- Purchase Jems → For tracking the purchase information with the package
  id → synchronous → Post this call immediately call jems for a user.

  - Json Below

    API: transaction/purchased Unencrypted: { \"jems_count\":10,
    \"add_type\":\"FLASH_SALE\", \"user_uuid\":\"UUID\",
    \"package_collection_uuid\":\"UUID\" } Encrypted: {
    \"payload\":\"encrypted data here\" }

- Gift Jems to the live user from the sender → Synchronous

  - Json Below

    API: transaction/gifted Unecrypted: { \"user_uuid\":\"UUID\",
    \"jems_count\":10, \"gift_id\":\"\", \"status\":\"SUCCES\",
    \"paid_to\":\"UUID\",
    \"entity_type\":\"LIVE_ROOM\"/\"USER\"/\"CONTENT\",
    \"entity_id\":\"UUID\" } Encrypted: { \"payload\":\"encrypted data
    here\" }

- Gifters list API

  - Gifts by Content UUID

    API:
    http://stage-api.myjosh.in/apij/content/gifters-list?content_id=028433c8-c858-40d3-877d-e43b55e26b84
    API Method:GET Headers: userUUID - \<\> auth-token -\<\> clientID
    -\<\> Response : { \"status\": { \"code\": 200, \"message\": \"OK\",
    \"time\": \"34\", \"server\": \"10.14.8.69\" }, \"data\": \[ {
    \"name\": \"Mayank Singh\", \"verified\": false, \"user_uuid\":
    \"af4b5b5f-d90f-4a89-a56e-2221de9b4255\", \"user_type\": \"e\",
    \"profile_url\":
    \"http://stage-api.myjosh.in/apij/user/details/v2/af4b5b5f-d90f-4a89-a56e-2221de9b4255\",
    \"profile_pic\":
    \"https://stage-stream.myjosh.in/stream/stage-josh-content/profile_pictures/default.png\",
    \"account_status\": \"ACTIVE\", \"gift_id\":
    \"5ee4c585-12f0-4e2a-bfc6-e51449f83292\" } \], \"code\": 200,
    \"metadata\": { \"next\":
    \"http://stage-api.myjosh.in/apij/content/gifters-list?content_id=028433c8-c858-40d3-877d-e43b55e26b84&rows=1&page=1\"
    } }

<!-- -->

- Gift by User UUID -

  - Group by gift uuid → order by count desc

    API:
    http://stage-api.myjosh.in/apij/user/gifters-list?user_uuid=028433c8-c858-40d3-877d-e43b55e26b84
    API Method:GET Headers: userUUID - \<\> auth-token -\<\> clientID
    -\<\> Response : { \"status\": { \"code\": 200, \"message\": \"OK\",
    \"time\": \"34\", \"server\": \"10.14.8.69\" }, \"data\": \[ {
    \"gift_id\": \"5ee4c585-12f0-4e2a-bfc6-e51449f83292\",
    \"gift_count\": \"1.1k\", \"gift_thumbnail_url\": \"\",
    \"gift_cta\":
    \"http://stage-api.myjosh.in/apij/gift/gifters-list?user_uuid=028433c8-c858-40d3-877d-e43b55e26b84&gift_uuid=5ee4c585-12f0-4e2a-bfc6-e51449f83292\"
    } \], \"code\": 200, \"metadata\": { \"next\":
    \"http://stage-api.myjosh.in/apij/content/gifters-list?content_id=028433c8-c858-40d3-877d-e43b55e26b84&rows=1&page=1\"
    } }

<!-- -->

- Gifts by Gift ID and User UUID

  - Group by user_uuid

    API:
    http://stage-api.myjosh.in/apij/gift/gifters-list?user_uuid=028433c8-c858-40d3-877d-e43b55e26b84&gift_uuid=5ee4c585-12f0-4e2a-bfc6-e51449f83292
    API Method:GET Headers: userUUID - \<\> auth-token -\<\> clientID
    -\<\> Response : { \"status\": { \"code\": 200, \"message\": \"OK\",
    \"time\": \"34\", \"server\": \"10.14.8.69\" }, \"data\": \[ {
    \"name\": \"Mayank Singh\", \"verified\": false, \"user_uuid\":
    \"af4b5b5f-d90f-4a89-a56e-2221de9b4255\", \"user_type\": \"e\",
    \"profile_url\":
    \"http://stage-api.myjosh.in/apij/user/details/v2/af4b5b5f-d90f-4a89-a56e-2221de9b4255\",
    \"profile_pic\":
    \"https://stage-stream.myjosh.in/stream/stage-josh-content/profile_pictures/default.png\",
    \"account_status\": \"ACTIVE\", \"gift_id\":
    \"5ee4c585-12f0-4e2a-bfc6-e51449f83292\". \"gift_count\":\"2.1k\" }
    \], \"code\": 200, \"metadata\": { \"next\":
    \"http://stage-api.myjosh.in/apij/content/gifters-list?content_id=028433c8-c858-40d3-877d-e43b55e26b84&rows=1&page=1\"
    } }

<!-- -->

- Begin Transaction

  - Payload: { package_id , user_uuid }

  - Response : { cost, package_id, transaction_id , status : 200 / Non
    200 }

  - Encrypt the API with RSA + AES\
    Group by user_uuid

    API: http://stage-api.myjosh.in/apij/transaction/begin Headers:
    userUUID - \<\> auth-token -\<\> clientID -\<\> Request Body:
    unecrypted { \"user_uuid\":\"\", \"text\":\"\", "package_id":"",
    \"package_collection_id\":\"\", \"ios_package_id\":\"\" } Encrypted:
    { \"payload\":\"encrypted data here\" } Response : { \"data\":{
    \"transaction_id\":\"\", \"jems_balance\":20 , \"package_cost\":45,
    \"package_id\":\"\" }, "status": { \"code\":200, "message":"OK" } }

- Affiliate begin

- Payload: { package_id , user_uuid } Response : { cost, package_id,
  transaction_id, package_type , status : 200 / Non 200 } Encrypt the
  API with RSA + AES API:
  http://stage-api.myjosh.in/apij/transaction/affiliate-begin Headers:
  userUUID - \<\> auth-token -\<\> clientID -\<\> Request Body:
  unecrypted { \"user_uuid\":\"\", \"text\":\"\", "package_id":"",
  \"package_collection_id\":\"\" } Encrypted: { \"payload\":\"encrypted
  data here\" } Response : { \"data\":{ \"transaction_id\":\"\",
  \"jems_balance\":20 , \"package_cost\":45, \"package_id\":\"\" },
  "status": { \"code\":200, "message":"OK" } }

- Update Transaction:
  `API: http://stage-api.myjosh.in/apij/transaction/update`

  - Payload: { transaction_id , razor_pay_data: , user_uuid: "" ,status:
    "BEGIN / UPDATE / END","transaction_data":{},"payment_method":"IOS"
    }

  - Response : { status : 200 / Non 200 }

  - Encrypt the API with RSA + AES

- Update Transaction : `transaction/affiliate-update`

  - Payload: { transaction_id ,`currency_type` (same as package_type in
    begin api response),claps_count (same as package_cost in begin
    response), user_uuid: "" ,status: "BEGIN / UPDATE /
    END","transaction_data":{},payment_method:"`PAYU`\" }

  - Response : { status : 200 / Non 200 }

  - Encrypt the API with RSA + AES

- Postman Collection for Gift/Package list API\
  <https://www.getpostman.com/collections/1ccffc56d4cb7ad83df2>

- Changes for user/details API\
  [https://docs.google.com/document/d/15lywW3PGufz1xqAnLL90SF9jxy8rVpcpSkBQv1_9P3U/edit#](https://docs.google.com/document/d/15lywW3PGufz1xqAnLL90SF9jxy8rVpcpSkBQv1_9P3U/edit#){card-appearance="inline"}
