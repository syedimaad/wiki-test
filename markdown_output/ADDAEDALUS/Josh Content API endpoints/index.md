File: App\\Models\\JoshCMS\\Settings.php

GCP Prod

private static \$hostNameProd = \"http://api.coolfie.io\"; private
static \$userViewEndPointProd =
\"https://josh-users-es.myjosh.in:9200/ugc-users/\_search?pretty\";
private static \$contentListingEndPointProd =
\"https://vpc-josh-content-v2-xhjjjbo7sk66hh6ontz6ch6ljq.ap-south-1.es.amazonaws.com/ugc-contents/\_search?pretty\";
private static \$audioListingEndPointProd =
\"https://josh-audios-es.myjosh.in:9200/ugc-audio/\_search?pretty\";
private static \$challengeListingEndPointProd =
\"https://josh-challenges-es.myjosh.in:9200/ugc-challenge/\_search?pretty\";

GCP QA

private static \$hostNameQA = \"http://qa-api.coolfie.io\"; private
static \$userViewEndPointQA =
\"https://qa-eck.myjosh.in:9200/ugc-users/\_search?pretty\"; private
static \$contentListingEndPointQA =
\"https://qa-eck.myjosh.in:9200/ugc-contents/\_search?pretty\"; private
static \$audioListingEndPointQA =
\"https://qa-eck.myjosh.in:9200/ugc-audios/\_search?pretty\"; private
static \$challengeListingEndPointQA =
\"https://qa-eck.myjosh.in:9200/ugc-challenge/\_search?pretty\";

GCP Stage

private static \$hostNameStage = \"http://stage-api.coolfie.io\";
private static \$userViewEndPointStage =
\"https://stage-eck.myjosh.in:9200/ugc-users/\_search?pretty\"; private
static \$contentListingEndPointStage =
\"https://stage-eck.myjosh.in:9200/ugc-contents/\_search?pretty\";
private static \$audioListingEndPointStage =
\"https://stage-eck.myjosh.in:9200/ugc-audios/\_search?pretty\"; private
static \$challengeListingEndPointStage =
\"https://stage-eck.myjosh.in:9200/ugc-challenge/\_search?pretty\";

GCP Sandbox

private static \$userViewEndPointLocal =
\"https://qa-eck.myjosh.in:9200/ugc-users/\_search?pretty\"; private
static \$contentListingEndPointLocal =
\"https://qa-eck.myjosh.in:9200/ugc-contents/\_search?pretty\"; private
static \$audioListingEndPointLocal =
\"https://qa-eck.myjosh.in:9200/ugc-audios/\_search?pretty\"; private
static \$challengeListingEndPointLocal =
\"https://qa-eck.myjosh.in:9200/ugc-challenge/\_search?pretty\";

**App User create** \
  End point: http://api.coolfie.io/user/create\
\
  Method: POST\
 \
  Post Data:
{\"details\":\"{\\\"name\\\":\\\"test-1\\\",\\\"username\\\":\\\"test-prod-shoopable\\\",\\\"email\\\":\\\"v1@gmail.com\\\",\\\"mobile_no\\\":\\\"8851321636\\\",\\\"type\\\":\\\"ib\\\",\\\"lang_code\\\":\\\"hi\\\",\\\"gender\\\":\\\"male\\\",\\\"bio_data\\\":\\\"\\\",\\\"sponsored_text\\\":\\\"\\\",\\\"verified\\\":true,\\\"hide_stats\\\":\\\"Y\\\",\\\"allow_follow\\\":\\\"Y\\\"}\",\"file\":{\"name\":\"\\/mnt\\/vol1\\/dh-ads\\/Daedalus\\/admis_php\\/storage\\/temp\\/165872988942965sample_160x600.png\",\"mime\":\"\",\"postname\":\"\"}}\
\
  Headers: \[\"auth-token:
0407d6f966f5b7b5b340822799848549\",\"clientId:
ad_ops@dailyhunt.in\",\"user-uuid:
8a70fdde-02a3-43ea-b7a8-c3c2210b3bdb\"\]\
 \
  HTTP Code: 200\
\
  Response:
{\"status\":{\"code\":200,\"message\":\"OK\",\"time\":\"116\",\"server\":\"10.10.49.162\"},\"data\":\"15396849-390f-4ae8-95c3-2b94c8b41223\",\"code\":200}\
\
\
**App User edit**\
\
    End point:
http://api.coolfie.io/user/update?user_uuid=15396849-390f-4ae8-95c3-2b94c8b41223\
\
    Method: POST\
   \
    Post Data:
{\"details\":\"{\\\"name\\\":\\\"test-change\\\",\\\"username\\\":\\\"test-prod-shoopable\\\",\\\"gender\\\":\\\"male\\\",\\\"bio_data\\\":\\\"\\\",\\\"sponsored_text\\\":\\\"\\\",\\\"hide_stats\\\":\\\"Y\\\",\\\"allow_follow\\\":\\\"Y\\\"}\"}\
   \
    Headers: \[\"auth-token:
0407d6f966f5b7b5b340822799848549\",\"clientId:
ad_ops@dailyhunt.in\",\"user-uuid:
8a70fdde-02a3-43ea-b7a8-c3c2210b3bdb\"\]\
   \
    HTTP Code: 200\
   \
    Response:
{\"status\":{\"code\":200,\"message\":\"OK\",\"time\":\"37\",\"server\":\"10.10.39.144\"},\"code\":200}\
\
\
\
\
**Content Create**\
\
    End point: http://api.coolfie.io/content/create\
   \
    Method: POST\
   \
    Post Data:
{\"details\":\"{\\\"title\\\":\\\"test-prod\\\",\\\"hashtags\\\":\\\"test\\\",\\\"user_lang\\\":\\\"hi\\\",\\\"cms_target_langs\\\":null,\\\"targeted_locations\\\":{\\\"granularity\\\":null,\\\"city_ids\\\":\[\],\\\"state_ids\\\":\[\]},\\\"categoryTitle\\\":\\\"Viral\\\",\\\"sponsored_text\\\":\\\"\\\",\\\"src_type\\\":\\\"ads\\\",\\\"format\\\":\\\"IMAGE\\\",\\\"duetable\\\":\\\"N\\\",\\\"allow_download\\\":\\\"N\\\",\\\"allow_share\\\":\\\"N\\\",\\\"allow_like\\\":\\\"Y\\\",\\\"allow_soundboard\\\":\\\"N\\\",\\\"allow_soundboard_reuse\\\":\\\"N\\\",\\\"allow_commenting\\\":\\\"N\\\",\\\"allow_comments_view\\\":\\\"N\\\",\\\"hashtag_clickable\\\":\\\"N\\\",\\\"display_profile_name\\\":\\\"N\\\",\\\"display_profile_image\\\":\\\"N\\\",\\\"allow_profile_name_click\\\":\\\"N\\\",\\\"user_uuid\\\":\\\"823123d1-4e36-4b52-8d97-93eb7ad2cd58\\\"}\",\"file\":{\"name\":\"\\/mnt\\/vol1\\/dh-ads\\/Daedalus\\/admis_php\\/storage\\/temp\\/165873112865387sample_160x600.png\",\"mime\":\"\",\"postname\":\"\"}}\
 \
 Headers: \[\"auth-token: 0407d6f966f5b7b5b340822799848549\",\"clientId:
ad_ops@dailyhunt.in\",\"user-uuid:
8a70fdde-02a3-43ea-b7a8-c3c2210b3bdb\"\]\
   \
  HTTP Code: 200\
 \
 Response:
{\"status\":{\"code\":200,\"message\":\"OK\",\"time\":\"158\",\"server\":\"10.10.39.57\"},\"data\":{\"request_id\":null,\"content_uuid\":\"a726829c-587a-417f-b0d8-1fe6a4f961a8\",\"processing_status\":\"NOT_PROCESSED\",\"moderation_status\":\"NON_MODERATED\",\"moderation_reason\":\"\",\"status_message\":\"Beautifying\",\"allow_for_rereview\":false,\"post_publish_time_epoch\":null},\"code\":200}\
\
\
**Content Edit**\
   \
    End point: http://api.coolfie.io/content/update\
 \
  Method: POST\
   \
    Post Data:
{\"content_uuid\":\"a726829c-587a-417f-b0d8-1fe6a4f961a8\",\"content_title\":\"test-prod-2\",\"tags\":\"test\",\"lang_code\":\"hi\",\"cms_target_langs\":null,\"category_name\":\"Viral\",\"sponsored_text\":\"\",\"targeted_locations\":{\"city_ids\":\[\],\"state_ids\":\[\]},\"duetable\":\"N\",\"allow_download\":\"N\",\"allow_share\":\"N\",\"allow_like\":\"Y\",\"allow_soundboard\":\"N\",\"allow_soundboard_reuse\":\"N\",\"allow_commenting\":\"N\",\"allow_comments_view\":\"N\",\"hashtag_clickable\":\"N\",\"display_profile_name\":\"N\",\"display_profile_image\":\"N\",\"allow_profile_name_click\":\"N\"}\
 \
  Headers: \[\"auth-token:
0407d6f966f5b7b5b340822799848549\",\"clientId:
ad_ops@dailyhunt.in\",\"user-uuid:
8a70fdde-02a3-43ea-b7a8-c3c2210b3bdb\",\"Content-Type:application\\/json\"\]\
   \
    HTTP Code: 200\
 \
  Response:
{\"status\":{\"code\":200,\"message\":\"OK\",\"time\":\"47\",\"server\":\"10.10.48.9\"},\"data\":{\"duetable\":\"N\",\"content_uuid\":\"a726829c-587a-417f-b0d8-1fe6a4f961a8\",\"content_title\":\"test-prod-2\",\"prepared_content_title\":\"test-prod-2
#test\",\"rich_content_title\":\"\<html\>test-prod-2 \<strong\>\<a
href=https://feed.myjosh.in/tags/test\>#test\</a\>\</strong\>\</html\>\",\"duet_file_available\":false},\"code\":200}
