**Possible Values:**\
"greeting_category":"good_morning" / "love" / "good_night" / "shayari"\
"media_category" : "images" / "videos" / "stickers"\

\
**API Request**

curl \--location \--request POST
\'https://qa-api.myjosh.in/chatbot/whatsapp\' \--header \'Content-Type:
application/json\' \--data-raw \'{ \"greetings_category\":\"Good
Morning\", \"media_category\": \"images\" }\'

\
**API Response**

{ \"status\": { \"code\": 200, \"message\": \"OK\", \"time\": \"56\",
\"server\": \"10.12.4.112\" }, \"data\": { \"greetings_category\":
\"Good Morning\", \"media_category\": \"images\", \"media_links\": \[
\"https://qa-stream.myjosh.in/stream/qa-josh-content/chat_bot/good_morning/images/IMG_6804.JPG\",
\"https://qa-stream.myjosh.in/stream/qa-josh-content/chat_bot/good_morning/images/IMG_6805.JPG\",
\"https://qa-stream.myjosh.in/stream/qa-josh-content/chat_bot/good_morning/images/IMG_6806.JPG\",
\"https://qa-stream.myjosh.in/stream/qa-josh-content/chat_bot/good_morning/images/IMG_6807.JPG\",
\"https://qa-stream.myjosh.in/stream/qa-josh-content/chat_bot/good_morning/images/IMG_6808.JPG\"
\] }, \"code\": 200 }

\
**API Request**

curl \--location \--request POST
\'https://qa-api.myjosh.in/chatbot/whatsapp\' \--header \'Content-Type:
application/json\' \--data-raw \'{ \"greetings_category\":\"Love\",
\"media_category\": \"videos\" }\'

**API Response**

{ \"status\": { \"code\": 200, \"message\": \"OK\", \"time\": \"43\",
\"server\": \"10.12.4.112\" }, \"data\": { \"greetings_category\":
\"Love\", \"media_category\": \"videos\", \"media_links\": \[
\"https://qa-stream.myjosh.in/stream/qa-josh-content/chat_bot/love/videos/IMG_6784.mp4\",
\"https://qa-stream.myjosh.in/stream/qa-josh-content/chat_bot/love/videos/IMG_6785.mp4\",
\"https://qa-stream.myjosh.in/stream/qa-josh-content/chat_bot/love/videos/IMG_6786.mp4\",
\"https://qa-stream.myjosh.in/stream/qa-josh-content/chat_bot/love/videos/IMG_6787.mp4\",
\"https://qa-stream.myjosh.in/stream/qa-josh-content/chat_bot/love/videos/IMG_6788.mp4\"
\] }, \"code\": 200 }

**API Request**

curl \--location \--request POST
\'https://qa-api.myjosh.in/chatbot/whatsapp\' \\ \--header
\'Content-Type: application/json\' \\ \--data-raw \'{
\"greetings_category\":\"Good Night\", \"media_category\": \"stickers\"
}\'

**API Response**

{ \"status\": { \"code\": 200, \"message\": \"OK\", \"time\": \"60\",
\"server\": \"10.12.4.112\" }, \"data\": { \"greetings_category\":
\"Good Night\", \"media_category\": \"stickers\", \"media_links\": \[
\"https://qa-stream.myjosh.in/stream/qa-josh-content/chat_bot/good_night/stickers/josh_Stickers_1.png\",
\"https://qa-stream.myjosh.in/stream/qa-josh-content/chat_bot/good_night/stickers/josh_Stickers_2.png\",
\"https://qa-stream.myjosh.in/stream/qa-josh-content/chat_bot/good_night/stickers/josh_Stickers_3.png\",
\"https://qa-stream.myjosh.in/stream/qa-josh-content/chat_bot/good_night/stickers/josh_Stickers_4.png\",
\"https://qa-stream.myjosh.in/stream/qa-josh-content/chat_bot/good_night/stickers/josh_Stickers_5.png\"
\] }, \"code\": 200 }
