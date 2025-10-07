**Package API**

Curl:

curl \--location \--request GET
\'https://qa-api.myjosh.in/apij/package/active\' \\

Response:

{ \"status\": { \"code\": 200, \"message\": \"OK\", \"time\": \"81\",
\"server\": \"10.12.4.112\" }, \"data\": { \"package_collection_uuid\":
\"705b6165-cd84-4587-b0ca-27433272c038\", \"collection_name\": \"test\",
\"start_time\": \"2022-07-05T07:36:00Z\", \"end_time\":
\"2024-10-17T06:36:00Z\", \"sale_share_url\": \"test\",
\"sale_thumbnail_url\":
\"https://qa-stream.coolfie.io/stream/qa-josh-content/package/collection/1a1aa8effe1e4cd4/8e9324c24fc52d6e/1a1aa8effe1e4cd48e9324c24fc52d6e.jpg\",
\"package_entities\": \[ { \"title\": \"100 Jems\",
\"package_element_uuid\": \"72797362-965b-477c-a115-f2ca06b045e2\",
\"package_thumbnail_url\":
\"https://qa-stream.myjosh.in/stream/qa-josh-content/package/element/168863fdc2894bfd/8e58afc8c4697bc5/168863fdc2894bfd8e58afc8c4697bc5.png\",
\"orig_price\": 50.0, \"discount_percentage\": 0.0,
\"discounted_price\": 50.0, \"jems_count\": 100, \"currency\": \"INR\",
\"default_currency\": \"INR\", \"created_date\":
\"2022-08-23T05:57:39.677Z\", \"modified_date\":
\"2022-08-23T05:57:39.677Z\" }, { \"title\": \"250 Jems\",
\"package_element_uuid\": \"9088a31b-7cd9-40c6-8cb9-4782e9fcdb82\",
\"tag\": { \"title\": \"Popular\", \"colour\": \"#65d1e8\" },
\"package_url\": \"\`\", \"package_thumbnail_url\":
\"https://qa-stream.myjosh.in/stream/qa-josh-content/package/element/2bf1f4441131474b/ab0cc92e930dfa02/2bf1f4441131474bab0cc92e930dfa02.png\",
\"orig_price\": 125.0, \"discount_percentage\": 20.0,
\"discounted_price\": 99.0, \"jems_count\": 250, \"currency\": \"INR\",
\"default_currency\": \"INR\", \"created_date\":
\"2022-08-23T05:55:29.254Z\", \"modified_date\":
\"2022-08-23T05:55:29.254Z\" }, { \"title\": \"1100\",
\"package_element_uuid\": \"0dd9ce24-2f31-49ba-aae1-832800c29aa3\",
\"package_thumbnail_url\":
\"https://qa-stream.myjosh.in/stream/qa-josh-content/package/element/27d4765b41714369/a22068fab04785f7/27d4765b41714369a22068fab04785f7.png\",
\"orig_price\": 550.0, \"discount_percentage\": 27.0,
\"discounted_price\": 399.0, \"jems_count\": 1100, \"currency\":
\"INR\", \"default_currency\": \"INR\", \"created_date\":
\"2022-08-23T06:05:41.522Z\", \"modified_date\":
\"2022-08-23T06:05:41.522Z\" } \] }, \"code\": 200 }

**Page API **

Curl:

curl \--location \--request GET
\'http://qa-api.myjosh.in/apij/spin/page\' \\ \--header \'Postman-Token:
f7086f93-a064-4abd-ad67-2c944fa66d5f\' \\ \--header \'cache-control:
no-cache\' \\ \--header \'user_uuid;\' \\ \--header \'clientID;\' \\
\--header \'auth_token;\' \\ \--header \'Cookie:
JSESSIONID=49DDAF0C9A930D8DC36D00A75FE61DCF\'

Response:

{ \"theme\": { \"bg_color\": \"#5154b2\", \"status_bar_color\":
\"#5154b2\", \"background_image\": \".jpeg\", \"overlay_image\":
\".jpeg\" }, \"jems_count\": \"12k\", \"spin_balance\":\"3\",
\"spin_config\": \[ { \"id\": 1, \"text\": \"100\", \"bg_color\":
\"#5154b2\", "image_url":"", \"text_color\":\"\" } \], \"chips_config\":
\[ { \"icon_url\": \"\", \"deeplink\": \"\", \"type\":\"\" } \],
\"text\": \"This festive season Josh brings you #DiwaliOnJosh\...\",
\"entities\": \[ { \"type\": \"banner\", \"banner_height\": 957,
\"banner_width\": 1300, \"banner_url\":
\"https://qa-stream.myjosh.in/stream/qa-josh-content/challenge_banners/64963b248114eb37/5b4665a071e9a779/64963b248114eb375b4665a071e9a779.jpeg\",
\"banner_list\": \[ { \"id\": \"7811ea85-5986-4953-8641-3a594a02a6b8\",
\"thumbnail\":
\"https://qa-stream.myjosh.in/stream/qa-josh-content/challenge_banners/64963b248114eb37/5b4665a071e9a779/64963b248114eb375b4665a071e9a779.jpeg\",
\"element_cta\": \"drop\", \"view_order\": 0 } \] }, { \"type\":
\"static_button_config\", \"buttons_list\": \[ { \"icon_url\": \"\",
\"text\": \"Won 100 Jems\" } \] }, { \"type\":\"feed\", \"feed\":\[ {
\"hashtag\":\"\", \"feed_api\": \"\" } \] } \] }

BE:\
Store json string for static configs in es properties index\
**[should we store at one common place or with different keys for
different configs??]{style="color: rgb(191,38,0);"}**

{ \"theme_bg_image\": \".jpeg\", \"spin_config\": \[ { \"id\": 1,
\"text\": \"100\", \"bg_color\": \"#5154b2\", \"text_color\":\"\" } \],
\"chips_list\": \[ { \"icon_url\": \"\", \"deeplink\": \"\",
\"type\":\"\" } \], \"text\": \"This festive season Josh brings you
#DiwaliOnJosh\...\", \"banner_height\": 957, \"banner_width\": 1300,
\"banner_url\":
\"https://qa-stream.myjosh.in/stream/qa-josh-content/challenge_banners/64963b248114eb37/5b4665a071e9a779/64963b248114eb375b4665a071e9a779.jpeg\",
\"banner_list\": \[ { \"id\": \"7811ea85-5986-4953-8641-3a594a02a6b8\",
\"thumbnail\":
\"https://qa-stream.myjosh.in/stream/qa-josh-content/challenge_banners/64963b248114eb37/5b4665a071e9a779/64963b248114eb375b4665a071e9a779.jpeg\",
\"view_order\": 0 } \], \"static_buttons_list\": \[ { \"icon_url\":
\"\", \"text\": \"Won 100 Jems\" } \] }

JSON in redis (static config)

{ \"text\": \"This festive season Josh brings you #DiwaliOnJosh, your
opportunity to be a part of Josh\'s way of celebrating this Festival
season, spin and win exciting prices\", \"theme_bg_image\":
\"https://qa-stream.coolfie.io/stream/qa-josh-content/diwali_spin_wheel/BG.jpeg\",
\"banner_height\": 1227, \"banner_width\": 2500, \"banner_url\":
\"https://qa-stream.coolfie.io/stream/qa-josh-content/diwali_spin_wheel/Banner1.jpg\",
\"banner_list\": \[ { \"id\": \"\", \"thumbnail\":
\"https://qa-stream.coolfie.io/stream/qa-josh-content/diwali_spin_wheel/Banner1.jpg\",
\"view_order\": 0, \"deeplink\":
\"https://www.youtube.com/watch?v=ox2rT1KRkFI\", \"type\": \"YOUTUBE\"
}, { \"id\": \"\", \"thumbnail\":
\"https://qa-stream.coolfie.io/stream/qa-josh-content/diwali_spin_wheel/Banner2.jpeg\",
\"view_order\": 1, \"deeplink\": \"\" }, { \"id\": \"\", \"thumbnail\":
\"https://qa-stream.coolfie.io/stream/qa-josh-content/diwali_spin_wheel/Banner3.jpeg\",
\"view_order\": 2, \"deeplink\":
\"https://qa-share.myjosh.in/hashtag/pranks\" }, { \"id\": \"\",
\"thumbnail\":
\"https://qa-stream.coolfie.io/stream/qa-josh-content/diwali_spin_wheel/Banner4.jpeg\",
\"view_order\": 3, \"deeplink\":
\"https://qa-share.myjosh.in/profile/37e072d1-6fcf-48c7-a320-45f744550c21\"
}, { \"id\": \"\", \"thumbnail\":
\"https://qa-stream.coolfie.io/stream/qa-josh-content/diwali_spin_wheel/Banner5.jpeg\",
\"view_order\": 4, \"deeplink\":
\"https://qa-share.myjosh.in/live/home\" }, { \"id\": \"\",
\"thumbnail\":
\"https://qa-stream.coolfie.io/stream/qa-josh-content/diwali_spin_wheel/Banner6.jpeg\",
\"view_order\": 5, \"deeplink\":
\"https://qa-share.myjosh.in/zone/a715a46b-c730-480b-b25e-b676c5087aa7\"
} \], \"static_buttons_list\": \[ { \"icon_url\":
\"https://qa-stream.coolfie.io/stream/qa-josh-content/diwali_spin_wheel/Staticbuton1.jpeg\",
\"text\": \"A Infant Raj Won 5 Jems\" }, { \"icon_url\":
\"https://qa-stream.coolfie.io/stream/qa-josh-content/diwali_spin_wheel/StaticButton2.png\",
\"text\": \"B A Swathi Made 10 spins today\" }, { \"icon_url\":
\"https://qa-stream.coolfie.io/stream/qa-josh-content/diwali_spin_wheel/StaticButton3.jpeg\",
\"text\": \"Catherine Earned a Free Spin\" }, { \"icon_url\":
\"https://qa-stream.coolfie.io/stream/qa-josh-content/diwali_spin_wheel/StaticButton4.jpeg\",
\"text\": \"Gurudutt Won a microwave\" } \], \"chips_list\": \[ {
\"icon_url\":
\"https://qa-stream.coolfie.io/stream/qa-josh-content/diwali_spin_wheel/Share.jpg\",
\"deeplink\":
\"https://shortvideos.page.link/JoshACTConcert?s=a&ss=null&s=a&ss=null\",
\"type\": \"SHARE\" }, { \"icon_url\":
\"https://qa-stream.coolfie.io/stream/qa-josh-content/diwali_spin_wheel/Camera.jpg\",
\"deeplink\":
\"http://qa-share.myjosh.in/camera/assets/30e7dea8-be6b-42b1-841c-3f4766191eff\",
\"type\": \"CAMERA\" }, { \"icon_url\":
\"https://qa-stream.coolfie.io/stream/qa-josh-content/diwali_spin_wheel/Music.jpg\",
\"deeplink\":
\"https://qa-share.myjosh.in/musics/playlist/5138eb47-b0e4-471b-9afe-f8f99aa44947?u=0x4039a4151435a9dd\",
\"type\": \"MUSIC\" }, { \"icon_url\":
\"https://qa-stream.coolfie.io/stream/qa-josh-content/diwali_spin_wheel/FAQ.jpg\",
\"deeplink\":
\"https://qa-share.myjosh.in/webItem/nhbrowser?webModel=%7B%22title%22%3A%22T%26C%22%2C%22url%22%3A%22https%3A%2F%2Fdocs.google.com%2Fdocument%2Fd%2F13Kq15FYNG2-9k6eVwSB5tvtwe2JC8TA9%2Fedit%3Fusp%3Dsharing%26ouid%3D109170297903623563534%26rtpof%3Dtrue%26sd%3Dtrue%22%7D\",
\"type\": \"FAQ\" } \], \"feed_hashtags\": \[ \"hashtag711\",
\"73xhashtag\", \"4.11.17audio\" \] }

Json in redis (spin tabs config)

{ \"spinConfig\": \[ { \"id\": \"0\", \"text\": \"Try again\",
\"bg_color\": \"#e65051\", \"text_color\": \"#FFFFFF\", \"icon_url\":
\"https://qa-stream.coolfie.io/stream/qa-josh-content/diwali_spin_wheel/Better_Luck_next_time.jpg\",
\"popup_text\": \"Oops better luck next time\" }, { \"id\": \"1\",
\"text\": \"5 Jems\", \"bg_color\": \"#fba629\", \"text_color\":
\"#FFFFFF\", \"icon_url\":
\"https://qa-stream.coolfie.io/stream/qa-josh-content/diwali_spin_wheel/Won_5_Jems.jpg\",
\"popup_text\": \"Received 5 Jems\" }, { \"id\": \"2\", \"text\": \"20
Jems\", \"bg_color\": \"#2faf74\", \"text_color\": \"#FFFFFF\",
\"icon_url\":
\"https://qa-stream.coolfie.io/stream/qa-josh-content/diwali_spin_wheel/Won_20_Jems.jpg\",
\"popup_text\": \"Received 20 Jems\" }, { \"id\": \"3\", \"text\":
\"Free spin\", \"bg_color\": \"#39a1e8\", \"text_color\": \"#FFFFFF\",
\"icon_url\":
\"https://qa-stream.coolfie.io/stream/qa-josh-content/diwali_spin_wheel/Earned_a_Free_Spin.jpg\",
\"popup_text\": \"Received a Free Spin\" }, { \"id\": \"4\", \"text\":
\"Rs.50 Voucher\", \"bg_color\": \"#ca3d77\", \"text_color\":
\"#FFFFFF\", \"icon_url\":
\"https://qa-stream.coolfie.io/stream/qa-josh-content/diwali_spin_wheel/Won50_voucher.jpg\",
\"popup_text\": \"Received Amazon Voucher\" }, { \"id\": \"5\",
\"text\": \"Rs.100 Voucher\", \"bg_color\": \"#f3f3e9\", \"text_color\":
\"#FFFFFF\", \"icon_url\":
\"https://qa-stream.coolfie.io/stream/qa-josh-content/diwali_spin_wheel/Won_250_voucher.jpg\",
\"popup_text\": \"Received Amazon Voucher\" }, { \"id\": \"6\",
\"text\": \"Rs.1000 Voucher\", \"bg_color\": \"#7b31aa\",
\"text_color\": \"#FFFFFF\", \"icon_url\":
\"https://qa-stream.coolfie.io/stream/qa-josh-content/diwali_spin_wheel/Won_1000_voucher.jpg\",
\"popup_text\": \"Received Amazon Voucher\" }, { \"id\": \"7\",
\"text\": \"Bumper Prize\", \"bg_color\": \"#f47e2f\", \"text_color\":
\"#FFFFFF\", \"icon_url\":
\"https://qa-stream.coolfie.io/stream/qa-josh-content/diwali_spin_wheel/Won_Bumper_Prize.jpg\",
\"popup_text\": \"Won a bumper prize for Diwali Dhamaka\" } \] }

**Transaction List API**

Response

{ \"status\": { \"code\": 200, \"message\": \"ok\", \"time\": \"15\",
\"server\": \"10.12.4.112\" }, \"data\": { \"balance\": 120936,
\"free_spins\": 3, \"rows\": \[ { \"transaction_id\":
\"7b8ed24a-0d09-4026-a6e2-802f54b619f4\", \"transaction_type\":
\"DEBIT\", \"type\": \"SPIN_WHEEL\", \"transaction_date\": \"Oct 06,
2022\", \"status\": \"SUCCESS\", \"jems_count\": 250, //can be null for
free spins \"spin_count\": 1, \"user_name\": \"testuser1\",
\"profile_pic\":
\"https://sdk.bitmoji.com/render/panel/9818df12-e707-411a-9fc9-e8500ac5fd7c-AVB4RHlDAN6\~8wYx8lxvtuo7v01cgw-v1.png?transparent=1&palette=1\"
}, { \"transaction_id\": \"468e9bf8-3a7a-43ec-a3e2-fde25ffe8983\",
\"transaction_type\": \"CREDIT\", \"type\": \"SYSTEM_GIFTS_RECEIVED\",
\"gift_type\": \"FREE_SPIN/FREE_JEMS/VOUCHER/BUMPER_PRIZE\",
\"voucher_code\": \"AMAZON500\", \"voucher_type\": \"AMAZON/PAYTM\",
\"transaction_date\": \"Oct 06, 2022\", "text":"Won bumper prize of TV",
\"status\": \"SUCCESS\", \"jems_count\" : 200, \"amount\": 500, //could
be spin count or voucher amount \"user_name\": \"testuser1\",
\"profile_pic\":
\"https://sdk.bitmoji.com/render/panel/9818df12-e707-411a-9fc9-e8500ac5fd7c-AVB4RHlDAN6\~8wYx8lxvtuo7v01cgw-v1.png?transparent=1&palette=1\"
} \] }, \"metaData\": { \"next\":
\"https://qa-api.myjosh.in/apij/transaction/list?user_uuid=9156ae8e-e418-446c-b96e-3087d1bb817c&page=1&rows=2\"
}, \"code\": 200 }

1 incomplete

**[gift_type needed or not?]{style="color: rgb(191,38,0);"}**

**System Gifts API**

Curl:

curl \--location \--request POST
\'http://qa-api.myjosh.in/apij/transaction/system-gift\' \\ \--header
\'Content-Type: application/json\' \\ \--header \'Cookie:
JSESSIONID=762AE187D1D0859E0094BC4851974679\' \\ \--data-raw \'{
\"gift_type\":\"SPIN/JEMS/VOUCHER/BUMPER_PRIZE\",
\"voucher_code\":\"AMAZON500\", \"entity_type\":\"AMAZON\",
\"amount\":500, //could be jems or spins or voucher amount
\"user_uuid\":\"7b48617c-38f2-46c6-98c9-c11e0a9e5a41\", \"text\":\"Won
bumper prize\" }\'

**SPIN API**

Case 1: user is using free spin

(If key is absent or \>0)

  -\> subtract spin from redis

  -\> no jems are deducted here

  -\> store transaction

{ \"transaction_id\":\"\", \"type\":\"SPIN_WHEEL\", \"text\":\"\",
\"status\":\"SUCCESS\", \"transaction_by\":\"\", \"start_time\":\"\",
\"end_time\":\"\", \"modified_on\":\"\" }

Case 2: user is using purchased spin

-\> subtract jems

-\> add spin_count to wallet

-\> store transaction

{ \"transaction_id\":\"\", \"type\":\"SPIN_WHEEL\", \"text\":\"\",
\"status\":\"SUCCESS\", \"transaction_by\":\"\", \"start_time\":\"\",
\"end_time\":\"\", \"modified_on\":\"\", \"jems_count\":10 }

**[Open questions:]{style="color: rgb(191,38,0);"}**\
1. we can track today_spins and total_spins, do we need to track
everyday spin data at user level?

2\. How we will track total purchase and spent data for spin wheel\
3. spin wheel response logic

Tracking

select transaction_by,count(\*) from transaction where type
=\'PURCHASE\' and modified_on between \'2022-10-20 23:59:59.0\' and
\'2022-10-21 23:59:59.0\' group by transaction_by order by count(\*)
desc limit 10;

josh_wallet=\> select transaction_by,count(\*) from transaction where
type =\'SPIN_WHEEL\' and modified_on between \'2022-10-20 23:59:59.0\'
and \'2022-10-21 23:59:59.0\' group by transaction_by order by count(\*)
desc limit 50;
