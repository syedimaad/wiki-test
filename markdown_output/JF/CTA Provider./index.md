A Service which will provide the CTA to items based on Userprofile.

The packet structure :

\"custom_cta\": {

\"icon_url\" : \" \",

\"title\" : \"HTML text\",

\"subtitle\": \"HTML text\",

\"deep_link\": \"\",

\"cta\": {

\"text\": \"CTA TEXT\",

\"selected_text\": \"\",

\"icon_url\": \"CTA ICON URL\",

\"selected_icon_url\": \"\",

\"view_type\": \"1/2/3/4/5\"

},

\"action_type\" : \"LIKE/SHARE/COMMENT/GIFT/DEEPLINK\",

\"type\":\"LIKE/SHARE/COMMENT/GIFT/EFFECT/AUDIO/TEMPLATE/STICKER/CHALLENGE/CONTEST/DUET/CREATOR/ZONE\",

\"start_time\":\"start time in milli seconds\",

\"viewed_threshold\":\"value in milli second to consider it as seen like
1000 or 2000\"

`}`

view_type values:

1 -\> Button with bg

2 -\> Arrow

3 -\> Button with icon

4 -\> Text with Arrow

5 -\> Only text (Eg: Zone)
