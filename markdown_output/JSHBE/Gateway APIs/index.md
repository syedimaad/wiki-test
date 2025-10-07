**1. Versioned Entity List**

Gives the versioned entities list

- **Request Method and URL:**

GET : https://qa-gateway.coolfie.io/api/v1/cms/entity/list

- **Curl Request:**

curl \--location \--request GET
\'https://qa-gateway.coolfie.io/api/v1/cms/entity/list\'

- **Success Response:**

json{ \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
\"10.12.1.83\", \"code\": 200 }, \"data\": \[ { \"versionEntity\":
\"DEMO_ENTITY\", \"langSpecific\": false }, { \"versionEntity\":
\"JOSH_STATIC_CONFIG\", \"langSpecific\": false }, { \"versionEntity\":
\"ASTRO_SIGNS\", \"langSpecific\": false }, { \"versionEntity\":
\"PLAYER_INFO\", \"langSpecific\": false }, { \"versionEntity\":
\"LIVE_CATEGORY_INTERESTS\", \"langSpecific\": false }, {
\"versionEntity\": \"PROFILE_VIEW\", \"langSpecific\": false }, {
\"versionEntity\": \"GLOBAL_SEARCH_TABS\", \"langSpecific\": true }, {
\"versionEntity\": \"STATIC_CONFIG\", \"langSpecific\": false }, {
\"versionEntity\": \"WIDGET_ORDER\", \"langSpecific\": false }, {
\"versionEntity\": \"WATERMARK\", \"langSpecific\": false }, {
\"versionEntity\": \"GLOBAL_SEARCH_TABS_V2\", \"langSpecific\": true },
{ \"versionEntity\": \"APP_MULTIPROCESS\", \"langSpecific\": false }, {
\"versionEntity\": \"GLOBAL_SEARCH_TABS_V3\", \"langSpecific\": true },
{ \"versionEntity\": \"MUSIC_SEARCH_TABS\", \"langSpecific\": true }, {
\"versionEntity\": \"HASHTAG_ONBOARD\", \"langSpecific\": false }, {
\"versionEntity\": \"SSO\", \"langSpecific\": false }, {
\"versionEntity\": \"AI_PROCESSOR\", \"langSpecific\": false }, {
\"versionEntity\": \"CAMERA_EFFECT_TABS_V3\", \"langSpecific\": false },
{ \"versionEntity\": \"CONTACT_SYNC\", \"langSpecific\": false }, {
\"versionEntity\": \"AI_PROCESSOR_NEW\", \"langSpecific\": false }, {
\"versionEntity\": \"GIFTS_LIST\", \"langSpecific\": false }, {
\"versionEntity\": \"DEVICE_LIST\", \"langSpecific\": false }, {
\"versionEntity\": \"QUICK_COMMENTS\", \"langSpecific\": false } \] }

**2. Version Info**

get the version info of versioned entity

- **Request Method and URL:**

GET : https://qa-gateway.coolfie.io/api/v1/cms/info/{versionEntity}

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/cms/info/JOSH_STATIC_CONFIG\'\
  \--header \'Content-Type: application/json\'\
  \--data-raw \'\'

- **Success Response:**

json{ \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
\"10.12.1.83\", \"code\": 200 }, \"data\": { \"version\": \"969\",
\"data\": { \"supportedMimetypes\": \[ \"video/mp4\",
\"video/quicktime\", \"video/x-ms-wmv\", \"video/mov\", \"video/mpg\"
\], \"reaction_sync_interval_in_seconds\": 86400,
\"vote_interval_in_seconds\": 86400, \"maxCommentCharLimit\": 50,
\"max_recent_cache_action_count\": 30, \"splashTime\": 3000,
\"showDataSaverMode\": true, \"enable_youtube_connect\": true,
\"enable_instagram_connect\": true, \"splash_ad_request_launch\": 2,
\"softRelaunchDelay\": 5000, \"hardRelaunchDelay\": 10000,
\"repeated_launch_api_request_delay\": 60000,
\"show_share_nudge_loop_count\": 2, \"max_share_nudge_show_count\": 3,
\"max_lifetime_show_share_nudge_count\": 10, \"max_edit_nudge_count\":
3, \"grid_item_count\": 3, \"animated_icon_duration_in_ms\": 500,
\"create_post_max_char\": 120, \"precache_interest_icons\": true,
\"video_edit_resolution\": 720,
\"max_sticker_comment_nudge_show_count\": 1,
\"is_apply_for_verification_enabled\": true,
\"create_video_nudge_dismissal\": 3000, \"vote_nudge_dismissal\": 3000,
\"share_voted_video_nudge_dismissal\": 3000, \"effectsExpiryMaxDays\":
30, \"enable_lite_sync_once\": false, \"disable_experiment_api\": false,
\"items_toshow_in_inbox\": 7, \"max_tpv_profile_suggestions\": 5,
\"experiment_incorrect_otp_max_attempts\": 2,
\"experiment_resend_otp_max_attempts\": 2,
\"max_event_videos_to_download\": 2, \"max_event_videos_to_show\": 2,
\"max_selected_videos_gallery\": 15, \"reduced_percent_volume_dub\": 20,
\"enableAutoSaveVideos\": true, \"loginScreenSubTitle\": \"Find friends
& family, like & comment,\\npersonalise your interests & watch
the\\nbest videos!\", \"loginScreenTitle\": \"Login to Josh\",
\"threshold_prefetch_stream_percentage\": 1,
\"num_of_item_check_for_prefetch\": 1, \"device_wake_up_flag\": true,
\"hide_block_user_option\": false, \"allow_masthead_ad\": true,
\"refresh_wait_time_ms\": 1500, \"allow_splash_ad\": true,
\"image_share_url\": \"/image/\", \"images_auto_scroll_duration_in_ms\":
5000, \"send_tip_page_url\":
\"https://qa-share.myjosh.in/webview/pay-tips?tip_to={0}&tip_by={1}&tip_to_image_url={2}&tip_to_user_name={3}&tip_by_user_name={4}\",
\"tip_transactions_page_url\":
\"https://qa-share.myjosh.in/webview/tip-transactions?user_id={0}\",
\"cs_ttl_duration_in_minutes\": 30, \"wait_on_cs_page_in_seconds\": 3,
\"contact_sync_message_config\": { \"zero_state_message\": \"Contact
sync successful, no friends were found but you can always invite them
later.\", \"after_follow_message\": \"You\'ve followed %d people from
your contact book\", \"sync_in_bg\": \"Enjoy videos while we sync your
contacts.\", \"with_contacts_state\": \"Contacts synced successfully.
Tap to find your friends.\", \"action_text\": \"Find Friends\" },
\"profile_rejected_show_count\": 2, \"max_photo_upload_limit\": 10,
\"bottom_bar_tab_sequence\": \[ \"HOME\", \"EXPLORE\", \"LIVE\",
\"SHOP\", \"NOTIFICATIONINBOX\", \"PROFILE\" \],
\"like_comment_tab_list\": \[ \"LIKE\", \"COMMENT\", \"GIFT\" \],
\"camera_tab_sequence\": \[ \"DUETS\", \"CAMERA\", \"PHOTOS\",
\"TEMPLATES\", \"MEMES\" \], \"disable_custom_tab_social_auth\": false,
\"is_seekbar_enabled\": true, \"is_tabbar_swiping_enabled\": true,
\"educational_nudge_count_per_session\": 3,
\"educational_nudge_duration_in_ms\": 3000, \"mute_ab_test_variant\":
\"PERSISTENT_MUTE\", \"zone_info_dialog_data\": { \"title\":
\"\<h1\>Content on this page is community managed.\</h1\>\",
\"message\": \"\<p\>Josh does not make any warranties about the
completeness, reliability and accuracy of this information. \<a
href=\'https://www.google.com\'\>Read TnC\</a\>\</p\>\", \"ctaText\":
\"\<strong\>Okay\</strong\>\" }, \"image_card_config\": {
\"min_time_threshold_in_ms\": 5000, \"max_count_per_session\": 3,
\"animation_list\": \[ 0, 1, 2, 5, 6, 8 \] },
\"recent_search_item_count\": 25, \"search_default_popular_feed_url\":
\"https://qa-feed.myjosh.in/search/?q=viral\", \"buy_jems_page_url\":
\"https://qa-share.myjosh.in/webview/pay-tips-v1?tip_to={0}&tip_by={1}&tip_to_image_url={2}&tip_to_user_name={3}&tip_by_user_name={4}&package_id={5}&package_collection_id={6}\",
\"jems_wallet_page_url\":
\"https://qa-share.myjosh.in/webview/jems-wallet?user_uuid={0}&client_id={1}\",
\"zero_page\": { \"zone\": { \"1\": { \"title\": \"No Followers\" },
\"2\": { \"title\": \"No Suggestions\" } }, \"user_tpv\": { \"1\": {
\"title\": \"No Mutual Followers\" }, \"2\": { \"title\": \"No Fans\" },
\"3\": { \"title\": \"No Followers\" }, \"4\": { \"title\": \"No Pages\"
}, \"5\": { \"title\": \"No Suggestions\" } }, \"user_fpv\": { \"2\": {
\"title\": \"No Fans\", \"description\": \"Try posting more content and
invite your friends\" }, \"3\": { \"title\": \"Not Following Anyone\",
\"description\": \"Explore discover section and follow creators and
other users\", \"cta_text\": \"Discovery\", \"cta_deeplink\":
\"http://qa-share.myjosh.in/page/discovery/main-discovery-page\" },
\"4\": { \"title\": \"Not Following Any Pages\", \"description\":
\"Explore discover section and follow pages\", \"cta_text\":
\"Discovery\", \"cta_deeplink\":
\"http://qa-share.myjosh.in/page/discovery/main-discovery-page\" },
\"5\": { \"title\": \"No Suggestion\" } }, \"like_comment_tpv\": {
\"LIKE\": { \"title\": \"No Likes\" }, \"COMMENT\": { \"title\": \"No
Comments\" }, \"GIFT\": { \"title\": \"No Gift Received\",
\"description\": \"Explore gift section and be the first one to send
gift\", \"cta_text\": \"Send Gifts\" } }, \"like_comment_fpv\": {
\"LIKE\": { \"title\": \"No Likes\" }, \"COMMENT\": { \"title\": \"No
Comments\" }, \"GIFT\": { \"title\": \"No Gift Received\",
\"description\": \"Explore gift section and be the first one to send
gift\" } } }, \"discovery_tab_list\": \[ { \"id\":
\"main-discovery-page\", \"name\": \"Discovery\", \"tab_icon_url\":
\"discovery_icon\", \"url\":
\"https://qa-feed.myjosh.in/page/discovery/main-discovery-page\",
\"type\": \"DISCOVERY\" }, { \"id\": \"main-audio-page\", \"name\":
\"Music\", \"tab_icon_url\": \"audio_icon\", \"url\":
\"https://qa-feed.myjosh.in/page/audio/main-audio-page\", \"type\":
\"AUDIO\" } \], \"bookmark_webview_url\":
\"https://qa-share.myjosh.in/webview/bookmarks\", \"game_center_url\":
\"https://qa-feed.myjosh.in/page_collection/game/main-game-page\",
\"global_leaderboard_url\":
\"https://qa-api.myjosh.in/apij/leaderboard/global\",
\"extended_radius_msg\": \"No videos available for the selected
location. Showing videos from nearby areas\",
\"syncRewardIntervalTime\": 30, \"bloomFilterSyncIntervalTime\": 3,
\"bloomFilterMaxFiles\": 2, \"bloomFilterRenewalSize\": 100,
\"is_user_rewards_enabled\": true,
\"wokenUpServiceForegroundNotificationDuration\": 5000,
\"api_sequencing_config\": { \"api_sequencing_max_delay_ms\": 180000,
\"api_hit_interval_time_ms\": 4000, \"fl_api_hit_interval_time_ms\":
2000, \"delay_max_video_count\": 10,
\"delay_cache_api_max_video_count\": 2, \"delay_after_handshake\": 3000
}, \"notification_filters\": { \"available_filters\": \[ { \"label\":
\"All\", \"isDefault\": \"true\", \"params\": { \"filter\": \"\" } }, {
\"label\": \"Social\", \"params\": { \"filter\": \"SOCIAL\" } }, {
\"label\": \"Content\", \"params\": { \"filter\": \"CONTENT\" } } \],
\"notification_filters_heading\": \"Filter notifications by\" },
\"wakeUpPartnerInformation\": { \"minimumBatteryRequired\": 15,
\"partnerPackages\": \[ { \"packageName\": \"com.eterno\", \"action\":
\"com.eterno.intent.woken_up_service_start\",
\"foregroundServiceSupport\": true, \"wakeupsections\": \[
\"Notification\", \"Deeplink\", \"Splash\", \"App Controller\" \],
\"dndStartTime\": 82800, \"dndEndTime\": 21300, \"wakeDelay\": 86400000,
\"disabledManufacturer\": \[\] }, { \"packageName\":
\"com.newsdistill.mobile\", \"action\":
\"com.newsdistill.mobile.intent.ACTION_WAKEUP\",
\"foregroundServiceSupport\": true, \"wakeupsections\": \[
\"Notification\", \"Deeplink\", \"Splash\", \"App Controller\" \],
\"dndStartTime\": 82800, \"dndEndTime\": 21300, \"wakeDelay\": 86400000,
\"disabledManufacturer\": \[\] } \] }, \"deviceWakeUpConfiguration\": {
\"minimumBatteryRequired\": 15, \"dndStartTime\": 82800, \"dndEndTime\":
21300, \"wakeDelay\": 86400000 }, \"appsflyer_events\": { \"C2\": 180,
\"C3\": 180, \"C4\": 180, \"C5\": 180, \"C6\": 180, \"C7\": 180, \"C8\":
180, \"C9\": 180, \"C10\": 180, \"C11\": 180, \"C12\": 540, \"C13\":
540, \"C14\": 540, \"C15\": 540, \"C16\": 1000, \"C17\": 1, \"C18\": 1,
\"C19\": 180, \"C20\": 180, \"C22\": 540, \"C23\": 540, \"C24\": 540,
\"C25\": 540, \"C26\": 540, \"C27\": 180, \"C28\": 180, \"C29\": 180,
\"C30\": 180, \"C31\": 180, \"C32\": 180, \"C33\": 180, \"C34\": 180,
\"C35\": 180, \"C36\": 180, \"C37\": 180, \"C38\": 180, \"C39\": 180,
\"C40\": 180, \"C41\": 180, \"C42\": 180, \"C43\": 180, \"C44\": 180,
\"C45\": 180, \"C46\": 180, \"C47\": 180, \"C48\": 180, \"C49\": 180,
\"C50\": 180 }, \"wa_status_sent_config\": \[ { \"min_version\": 30,
\"max_version\": 2147483647, \"enable\": true, \"path_wa_status\":
\"/Android/media/com.whatsapp/WhatsApp/Media/.Statuses\",
\"path_wa_sent_video\":
\"/Android/media/com.whatsapp/WhatsApp/Media/WhatsApp Video/Sent\",
\"path_wa_sent_image\":
\"/Android/media/com.whatsapp/WhatsApp/Media/WhatsApp Images/Sent\" }, {
\"min_version\": 0, \"max_version\": 29, \"enable\": true,
\"path_wa_status\": \"WhatsApp/Media/.Statuses\",
\"path_wa_sent_video\": \"WhatsApp/Media/WhatsApp Video/Sent\",
\"path_wa_sent_image\": \"WhatsApp/Media/WhatsApp Images/Sent\" } \],
\"myelin_config\": { \"enable\": true, \"disable_for_verified\": \[
\"k\", \"m\", \"l\" \], \"sync_time\": 86400000, \"quality\": {
\"fast\": \"average\", \"good\": \"average\", \"average\": \"average\" }
}, \"pullNotificationConfig\": { \"pull_notifications_enabled\": true,
\"firstTimePullDelay\": 120 }, \"lp_gotosetting_dialog_config\": {
\"lp_gotosetting_dialog_title\": \"Allow Josh to access this device's
location?\", \"lp_gotosetting_dialog_desc\": \"This will help you reach
a more relevant audience &amp; gain followers, Please go to settings and
allow location permission\", \"lp_gotosetting_dialog_pos_action\": \"Go
To Settings\", \"lp_gotosetting_dialog_neg_action\": \"Later\",
\"lp_gotosetting_dialog_show_after_x_post\": 4 }, \"compilation_rules\":
{ \"default\": 720, \"resolutions\": \[ { \"max\": 2147483647, \"min\":
2048, \"result\": 2048 }, { \"max\": 2047, \"min\": 1024, \"result\":
1024 }, { \"max\": 1023, \"min\": 641, \"result\": 720 }, { \"max\":
640, \"min\": 481, \"result\": 640 }, { \"max\": 480, \"min\": 361,
\"result\": 480 }, { \"max\": 360, \"min\": 1, \"result\": 360 } \] },
\"data_saver_cache_config\": {
\"cache_offline_directory_max_size_in_mb\": 100,
\"cache_prefetch_directory_max_size_in_mb\": 200,
\"cache_directory_max_size_in_mb\": 100, \"clear_session_data\": false,
\"recommended_profile\": \"average\", \"enable_notification_prefetch\":
true, \"min_cache_item_to_fetch_api\": 5, \"session_start_config\": {
\"slow\": { \"from_offline_back_to_back\": 5 }, \"average\": {
\"from_offline_back_to_back\": 3 }, \"good\": {
\"from_offline_back_to_back\": 2 }, \"fast\": {
\"from_offline_back_to_back\": 2 }, \"veryfast\": {
\"from_offline_back_to_back\": 2 } }, \"prefetch_download_config\": {
\"disable_cache\": false, \"prefetch_download_count_config\": {
\"slow\": { \"no_of_videos\": 3, \"min_cache_percentage_ofl_to_onl\":
100 }, \"average\": { \"no_of_videos\": 3,
\"min_cache_percentage_ofl_to_onl\": 80 }, \"good\": { \"no_of_videos\":
3, \"min_cache_percentage_ofl_to_onl\": 60 }, \"fast\": {
\"no_of_videos\": 3, \"min_cache_percentage_ofl_to_onl\": 40 },
\"veryfast\": { \"no_of_videos\": 3,
\"min_cache_percentage_ofl_to_onl\": 25 } } },
\"offline_download_config\": { \"sort_type\": \"recency\",
\"disable_cache\": true, \"global_cache_ttl_days\": 15,
\"max_cache_item\": 10, \"recommended_video_quality\": \"good\",
\"ucq_download_config\": { \"average\": { \"exit\": 0, \"minimise\": 0,
\"notification\": 0 }, \"fast\": { \"exit\": 0, \"minimise\": 0,
\"notification\": 0 }, \"slow\": { \"exit\": 0, \"minimise\": 0,
\"notification\": 0 }, \"good\": { \"exit\": 0, \"minimise\": 0,
\"notification\": 0 }, \"veryfast\": { \"exit\": 0, \"minimise\": 0,
\"notification\": 0 } }, \"cache_api_sync_time_secs\": 86400,
\"app_inactivity_duration_days\": 10 }, \"buffer_threshold_config\": {
\"average\": { \"organic\": { \"buffer_threshold_initial_videos_secs\":
1, \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
\"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
\"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } },
\"fast\": { \"organic\": { \"buffer_threshold_initial_videos_secs\": 1,
\"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
\"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
\"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } },
\"slow\": { \"organic\": { \"buffer_threshold_initial_videos_secs\": 1,
\"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
\"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
\"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } },
\"good\": { \"organic\": { \"buffer_threshold_initial_videos_secs\": 1,
\"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
\"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
\"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } },
\"veryfast\": { \"organic\": { \"buffer_threshold_initial_videos_secs\":
1, \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
\"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
\"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } } } },
\"postLangMapping\": \[ { \"languageGroup\": \[ \"na\" \], \"values\":
\[ \"hi\", \"en\", \"te\", \"ta\", \"ml\", \"kn\", \"mr\", \"gj\",
\"bn\", \"or\", \"pa\", \"bh\" \] }, { \"languageGroup\": \[ \"hi\",
\"mr\", \"pa\", \"gj\", \"bh\", \"or\", \"bn\" \], \"values\": \[
\"hi\", \"mr\", \"pa\", \"gj\", \"bh\", \"or\", \"bn\", \"en\", \"te\",
\"ta\", \"ml\", \"kn\" \] }, { \"languageGroup\": \[ \"te\", \"ta\",
\"ml\", \"kn\" \], \"values\": \[ \"te\", \"ta\", \"ml\", \"kn\",
\"hi\", \"en\", \"mr\", \"pa\", \"gj\", \"bh\", \"or\", \"bn\" \] } \],
\"uploadShareConfig\": { \"shareChannels\": \[ { \"pkgName\":
\"com.twitter.android\", \"iconUrl\": \"twitter\", \"name\": \"TWITTER\"
}, { \"pkgName\": \"com.instagram.android\", \"iconUrl\": \"instagram\",
\"name\": \"INSTAGRAM\" }, { \"pkgName\": \"com.facebook.katana\",
\"iconUrl\": \"facebook\", \"name\": \"FACEBOOK\" }, { \"pkgName\":
\"com.whatsapp\", \"iconUrl\": \"whatsapp\", \"name\": \"WHATSAPP\" }
\], \"initialPollingDelayMs\": 5000, \"pollingDelayMs\": 5000,
\"maxPollingAttempts\": 10, \"shareNudgeCount\": 7,
\"delaySharePromptHideMs\": 3000, \"delayPIPSuccessHideMs\": 5000 },
\"profileBlockedConfig\": { \"pb_config_title\": \"Profile Blocked!\",
\"pb_config_subtitle\": \"This profile has been blocked due to violation
of community guidelines.\", \"pb_config_cta\": \"Learn more\",
\"pb_config_cta_link\":
\"https://qa-share.myjosh.in/help/community-violation-guidelines\",
\"pb_config_subtitle_dialog\": \"You cannot post a video\",
\"pb_config_cta_neg_dialog\": \"Dismiss\" },
\"fpv_profile_quality_config\": \[ { \"network_quality\": \"veryfast\",
\"profile_quality\": \"veryfast\" }, { \"network_quality\": \"fast\",
\"profile_quality\": \"veryfast\" }, { \"network_quality\": \"good\",
\"profile_quality\": \"veryfast\" }, { \"network_quality\": \"average\",
\"profile_quality\": \"good\" }, { \"network_quality\": \"slow\",
\"profile_quality\": \"average\" } \], \"fpv_quality_nudge_config\": {
\"network_quality\": \"average\", \"message\": \"Slow Internet! Playing
Video in Low Quality\", \"duration\": 3000, \"per_session_count\": 1 },
\"quality_mapping\": \[ { \"network_quality\": \"veryfast\",
\"profile_quality\": \"fast\" }, { \"network_quality\": \"fast\",
\"profile_quality\": \"fast\" }, { \"network_quality\": \"good\",
\"profile_quality\": \"good\" }, { \"network_quality\": \"average\",
\"profile_quality\": \"average\" }, { \"network_quality\": \"slow\",
\"profile_quality\": \"slow\" } \], \"cache_config\": {
\"cache_offline_directory_max_size_in_mb\": 200,
\"cache_prefetch_directory_max_size_in_mb\": 250,
\"cache_directory_max_size_in_mb\": 100, \"clear_session_data\": false,
\"min_cache_item_to_fetch_api\": 5, \"hard_start_config\": {
\"disableHardStart\": true, \"file_download_percentage\": 100,
\"download_high_bitrate_variant\": true,
\"min_stream_download_on_average_network\": 2,
\"min_stream_download_on_fast_network\": 2,
\"min_stream_download_on_good_network\": 2,
\"min_stream_download_on_slow_network\": 2 }, \"session_start_config\":
{ \"slow\": { \"from_offline_back_to_back\": 3 }, \"average\": {
\"from_offline_back_to_back\": 3 }, \"good\": {
\"from_offline_back_to_back\": 3 }, \"fast\": {
\"from_offline_back_to_back\": 3 }, \"veryfast\": {
\"from_offline_back_to_back\": 3 } }, \"prefetch_download_config\": {
\"disable_cache\": false, \"prefetch_download_count_config\": {
\"slow\": { \"no_of_videos\": 3, \"min_cache_percentage_ofl_to_onl\":
100 }, \"average\": { \"no_of_videos\": 3,
\"min_cache_percentage_ofl_to_onl\": 85 }, \"good\": { \"no_of_videos\":
5, \"min_cache_percentage_ofl_to_onl\": 70 }, \"fast\": {
\"no_of_videos\": 2, \"min_cache_percentage_ofl_to_onl\": 50 },
\"veryfast\": { \"no_of_videos\": 2,
\"min_cache_percentage_ofl_to_onl\": 50 } } },
\"offline_download_config\": { \"sort_type\": \"recency\",
\"disable_cache\": false, \"global_cache_ttl_days\": 15,
\"max_cache_item\": 40, \"recommended_video_quality\": \"good\",
\"ucq_download_config\": { \"average\": { \"exit\": 2, \"minimise\": 2,
\"notification\": 2 }, \"fast\": { \"exit\": 2, \"minimise\": 2,
\"notification\": 2 }, \"slow\": { \"exit\": 2, \"minimise\": 2,
\"notification\": 2 }, \"good\": { \"exit\": 2, \"minimise\": 2,
\"notification\": 2 }, \"veryfast\": { \"exit\": 2, \"minimise\": 2,
\"notification\": 2 } }, \"cache_api_sync_time_secs\": 86400,
\"app_inactivity_duration_days\": 10 }, \"buffer_threshold_config\": {
\"average\": { \"organic\": { \"buffer_threshold_initial_videos_secs\":
1, \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
\"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
\"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } },
\"fast\": { \"organic\": { \"buffer_threshold_initial_videos_secs\": 1,
\"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
\"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
\"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } },
\"slow\": { \"organic\": { \"buffer_threshold_initial_videos_secs\": 1,
\"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
\"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
\"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } },
\"good\": { \"organic\": { \"buffer_threshold_initial_videos_secs\": 1,
\"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
\"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
\"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } },
\"veryfast\": { \"organic\": { \"buffer_threshold_initial_videos_secs\":
1, \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
\"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
\"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } } } },
\"duet_config\": { \"camera_portrait_min_height_to_width\": { \"h\": 16,
\"w\": 9 }, \"camera_portrait_max_height_to_width\": { \"h\": 21, \"w\":
9 }, \"camera_landscape_min_width_to_height\": { \"h\": 8, \"w\": 9 },
\"camera_landscape_max_width_to_height\": { \"h\": 9, \"w\": 21 },
\"video_download_url\": \"\", \"create_and_edit_configs\": {
\"duetable_config_for_verified\": { \"default_value\": \"OFF\",
\"aspect_ratio\": { \"allow_for_portrait\": true, \"allow_for_square\":
true, \"allow_for_landscape\": false }, \"video_source\": {
\"camera_with_josh_library\": true, \"camera_without_josh_library\":
true, \"gallery_with_josh_library\": true,
\"gallery_without_josh_library\": true, \"duet\": false },
\"video_source_v2\": \[ { \"srcType\": \"camera\", \"josh_library\":
true, \"non_josh_library\": true }, { \"srcType\": \"gallery\",
\"josh_library\": true, \"non_josh_library\": true }, { \"srcType\":
\"multi_segment_camera\", \"josh_library\": true, \"non_josh_library\":
true }, { \"srcType\": \"multi_segment_gallery\", \"josh_library\":
true, \"non_josh_library\": true }, { \"srcType\":
\"multi_segment_camera_gallery\", \"josh_library\": true,
\"non_josh_library\": true }, { \"srcType\": \"external_did\",
\"josh_library\": true, \"non_josh_library\": true }, { \"srcType\":
\"external\", \"josh_library\": true, \"non_josh_library\": true }, {
\"srcType\": \"duet\", \"josh_library\": false, \"non_josh_library\":
false } \] }, \"duetable_config_for_nonverified\": { \"default_value\":
\"OFF\", \"aspect_ratio\": { \"allow_for_portrait\": true,
\"allow_for_square\": true, \"allow_for_landscape\": false },
\"video_source\": { \"camera_with_josh_library\": true,
\"camera_without_josh_library\": true, \"gallery_with_josh_library\":
true, \"gallery_without_josh_library\": true, \"duet\": false },
\"video_source_v2\": \[ { \"srcType\": \"camera\", \"josh_library\":
true, \"non_josh_library\": true }, { \"srcType\": \"gallery\",
\"josh_library\": true, \"non_josh_library\": true }, { \"srcType\":
\"multi_segment_camera\", \"josh_library\": true, \"non_josh_library\":
true }, { \"srcType\": \"multi_segment_gallery\", \"josh_library\":
true, \"non_josh_library\": true }, { \"srcType\":
\"multi_segment_camera_gallery\", \"josh_library\": true,
\"non_josh_library\": true }, { \"srcType\": \"external_did\",
\"josh_library\": true, \"non_josh_library\": true }, { \"srcType\":
\"external\", \"josh_library\": true, \"non_josh_library\": true }, {
\"srcType\": \"duet\", \"josh_library\": false, \"non_josh_library\":
false } \] } } }, \"duet_video_volume_config\": {
\"dueted_video_volume\": 20, \"recorded_video_volume\": 100 },
\"fire_track_from_cache\": true, \"handshake_version\": \"470\",
\"performance_analytics_enabled\": false, \"upload_duration\": 120,
\"disable_error_event\": false, \"disable_slow_network_prompts\": false,
\"speed_quality_map\": { \"100\": \"slow\", \"500\": \"average\",
\"1000\": \"good\", \"10000\": \"fast\", \"50000\": \"veryfast\" },
\"record_duration\": 15, \"first_time_pull_delay\": 300,
\"first_chunk_request_params\": { \"cdn\": \"Y\", \"src\": \"app\" },
\"max_upload_size\": 200, \"upgrade\": \"LATEST\", \"rateConfig\": {
\"enable\": true, \"preActivitySessionWaitTimeInSeconds\": 600,
\"minNumberOfStoriesViewedPerSession\": 10, \"minNumberOfBooksRead\": 4,
\"maxNumberOfTimesToShowRateScreen\": 3,
\"minNumberOfDaysToWaitShowingRateScreen\": 30,
\"maxWaitDaysForNewUsersToShowRateScreen\": 7,
\"minLaunchesForNewUsersToShowRateScreen\": 3,
\"minNumberOfDaysUserToWaitAfterLastSeen\": 10,
\"minNumberOfAppLaunchesToWaitAfterLastSeen\": 10 },
\"maxHistoryCount\": 50, \"enable_reactions_api_hit\": true,
\"max_recent_interaction_count\": 50,
\"location_fetch_interval_in_seconds\": 86400,
\"min_gap_between_app_update_prompt_secs\": 172800,
\"video_views_in_session_for_update_prompt\": 5, \"permission\": {
\"id\": 24, \"event\": \"appLaunch\", \"activity\": { \"type\":
\"permission\", \"attributes\": { \"gapCount\": \"4\", \"permDesc\":
\"Josh needs access to the following\", \"permTitle\": \"Permissions
required\", \"openSettings\": \"Josh needs storage access to perform
this action. To enable it, please visit your app settings.\",
\"settingsAction\": \"Settings\", \"storagePermDesc\": \"We need this
for critical features like downloading a video.\", \"locationPermDesc\":
\"We need this to show you videos being posted by users around you.\",
\"storagePermSubtitle\": \"Storage Access\", \"locationPermSubtitle\":
\"Location Access\", \"permissionNegativeBtn\": \"LATER\",
\"permissionPositiveBtn\": \"Allow\" } }, \"resource\": \"coolfie\",
\"precondition\": { \"minItemsViewed\": 7, \"minTimeEngaged\": 0,
\"maxNumberOfDisplay\": 0, \"minNumberOfOccurences\": 5 } },
\"fire_comscore_from_cache\": true, \"max_notifications_in_tray\": 4,
\"thumbnail_qualities\": { \"fast\": { \"quality\": \"h\",
\"resolution\": 480 }, \"good\": { \"quality\": \"h\", \"resolution\":
480 }, \"slow\": { \"quality\": \"h\", \"resolution\": 480 },
\"average\": { \"quality\": \"h\", \"resolution\": 480 } },
\"default_notification_duration\": 120, \"max_upload_bitrate\": 1500,
\"pull_notifications_enabled\": true, \"video_qualities\": { \"fast\": {
\"quality\": \"h\", \"resolution\": 480 }, \"good\": { \"quality\":
\"h\", \"resolution\": 480 }, \"slow\": { \"quality\": \"h\",
\"resolution\": 480 }, \"average\": { \"quality\": \"h\",
\"resolution\": 480 } }, \"disable_firebase_perf\": false,
\"google_play_url\": { \"share_video_text\": \"Download Josh for more
videos like this!\", \"download_video_text\": \"Download Josh for more
videos like this!\", \"download_live_stream_text\": \"Download Josh for
more livestreams like this!\", \"share_google_play_url\":
\"https://m.myjosh.in/6OaT/32e07bf\", \"setting_google_play_url\":
\"https://m.myjosh.in/6OaT/568901e6\", \"download_google_play_url\":
\"https://m.myjosh.in/6OaT/6d76ce25\", \"duet_share_text\": \"Create and
watch amazing duets with %1\$s! \\n%2\$s \\nDownload Josh now to watch &
even create more great videos like this!
\\nhttps://play.google.com/store/apps/details?id=com.eterno.shortvideos\"
}, \"default_notification_text\": \"Welcome to Josh! Check out the
latest news in your preferred language.\",
\"story_detail_error_page_url\":
\"https://m.dailyhunt.in/webItem/errorPage.html\",
\"share_floating_icon_type\": \"floatingIconBentArrow\",
\"upload_format_list\": \[ \"3gp\", \"mp4\" \], \"nlfc_config\": {
\"disable_nlfc\": false, \"min_time_spent_to_trigger\": 6000,
\"min_time_spent_to_trigger_with_social\": 6000,
\"min_percentage_completion\": 75, \"skip_nlfc_for_session_on_failure\":
3, \"min_offset_to_append\": 0 }, \"moderationNsfwReportUrl\":
\"https://qa-share.myjosh.in/report/machine-moderation/1\",
\"moderationDuplicateReportUrl\":
\"https://qa-share.myjosh.in/report/ownership-content/1\",
\"joshCam1Config\": { \"licenseUrl\":
\"https://qa-stream.myjosh.in/stream/qa-josh-content/joshCam1Config/license/android/20986-269-8619db07c55966e42c2f42acfa3e187d.lic\",
\"licenseUrliOS\":
\"https://qa-stream.myjosh.in/stream/qa-josh-content/joshCam1Config/license/ios/MeisheSDKLicense.lic\"
}, \"sdkType\": \"JOSH_CAM1\", \"followersTabName\": \"Top Fans\",
\"handshakeDefaultInterval\": 43200000, \"maxApiDelay\": 2000,
\"maxErrorEventPerInterval\": 10, \"upload_duration_v2\": 60,
\"min_upload_duration\": 5, \"max_recent_navigable_action_count\": 30,
\"timerPeriodInSeconds\": 60, \"firstTimePullDelay\": 60,
\"enable_whatsapp_share\": true, \"enable_video_download_on_share\":
true, \"hit_firebase_event_once\": true, \"enableGzip_v2\": true,
\"allowEmptyTitleInCreatePost\": false, \"is_firebase_event_enabled\":
true, \"dev_error_for_2xxTo4xx_enabled\": false,
\"location_prompt_for_max_time_count\": 3,
\"location_prompt_after_max_post_count\": 0, \"video_resources\": {
\"1\": \"https://qa-gateway.myjosh.in/api/v1/materialinfo/1?version=1\",
\"2\":
\"https://qa-gateway.myjosh.in/api/v1/materialinfo/2?version=19\",
\"3\": \"https://qa-gateway.myjosh.in/api/v1/materialinfo/3?version=1\",
\"4\": \"https://qa-gateway.myjosh.in/api/v1/materialinfo/4?version=1\",
\"5\": \"https://qa-gateway.myjosh.in/api/v1/materialinfo/5?version=3\",
\"6\": \"https://qa-gateway.myjosh.in/api/v1/materialinfo/6?version=1\",
\"7\": \"https://qa-gateway.myjosh.in/api/v1/materialinfo/7?version=1\",
\"8\": \"https://qa-gateway.myjosh.in/api/v1/materialinfo/8?version=1\",
\"9\": \"https://qa-gateway.myjosh.in/api/v1/materialinfo/9?version=1\",
\"10\":
\"https://qa-gateway.myjosh.in/api/v1/materialinfo/10?version=1\",
\"11\":
\"https://qa-gateway.myjosh.in/api/v1/materialinfo/11?version=1\",
\"12\":
\"https://qa-gateway.myjosh.in/api/v1/materialinfo/12?version=1\",
\"13\":
\"https://qa-gateway.myjosh.in/api/v1/materialinfo/13?version=1\",
\"14\":
\"https://qa-gateway.myjosh.in/api/v1/materialinfo/14?version=11\",
\"15\":
\"https://qa-gateway.myjosh.in/api/v1/materialinfo/15?version=1\",
\"16\":
\"https://qa-gateway.myjosh.in/api/v1/materialinfo/16?version=1\",
\"17\":
\"https://qa-gateway.myjosh.in/api/v1/materialinfo/17?version=1\",
\"24\":
\"https://qa-gateway.myjosh.in/api/v1/materialinfo/24?version=1\",
\"25\":
\"https://qa-gateway.myjosh.in/api/v1/materialinfo/25?version=6\",
\"26\":
\"https://qa-gateway.myjosh.in/api/v1/materialinfo/26?version=4\",
\"27\":
\"https://qa-gateway.myjosh.in/api/v1/materialinfo/27?version=1\",
\"28\":
\"https://qa-gateway.myjosh.in/api/v1/materialinfo/28?version=4\",
\"29\":
\"https://qa-gateway.myjosh.in/api/v1/materialinfo/29?version=1\",
\"30\":
\"https://qa-gateway.myjosh.in/api/v1/materialinfo/30?version=2\",
\"31\":
\"https://qa-gateway.myjosh.in/api/v1/materialinfo/31?version=4\",
\"32\":
\"https://qa-gateway.myjosh.in/api/v1/materialinfo/32?version=1\",
\"33\":
\"https://qa-gateway.myjosh.in/api/v1/materialinfo/33?version=1\",
\"34\":
\"https://qa-gateway.myjosh.in/api/v1/materialinfo/34?version=2\",
\"35\":
\"https://qa-gateway.myjosh.in/api/v1/materialinfo/35?version=1\",
\"36\":
\"https://qa-gateway.myjosh.in/api/v1/materialinfo/36?version=1\",
\"37\":
\"https://qa-gateway.myjosh.in/api/v1/materialinfo/37?version=1\" },
\"following_sync_interval_in_seconds\": 86400, \"appsOnDeviceEnabled\":
false, \"appsOnDeviceEnabledV2\": true, \"cleanupConfig\": {
\"maxMusicDownloads\": 20, \"maxStickerDownloads\": 100 },
\"network_config\": { \"exo_weightage_double\": 0.8,
\"network_weightage_double\": 2, \"sliding_percentile_percentile\": 0.5,
\"bitrate_expression\": { \"id\": \"1\", \"formula\":
\"(e\*0.8)+(n\*2)\" }, \"bitrate_expression_v2\": { \"id\": \"3\",
\"formula\": \"function f42(e,n){ \\n if(e\<n) return e\*0.8+n\*0.7; \\n
else { var wa=e\*e/(e+n)+n\*n/(e+n); return Math.min(wa,e);};\\n};\" },
\"bitrate_expression_exception\": { \"id\": \"2\", \"formula\":
\"(e\*0.8)+(n\*0.7)\" }, \"lifetime_bitrate_capture_window_sec\":
604800, \"coldstart_transition_threshold_sec\": 10,
\"coldstart_network_provider_mapping\": \[ { \"network\": \"4G\",
\"provider\": \"Jio 4G\", \"quality\": \"good\" }, { \"network\":
\"4G\", \"provider\": \"airtel\", \"quality\": \"good\" }, {
\"network\": \"4G\", \"provider\": \"Vi India\", \"quality\": \"good\"
}, { \"network\": \"4G\", \"provider\": \"IND airtel\", \"quality\":
\"good\" }, { \"network\": \"4G\", \"provider\": \"Vodafone IN\",
\"quality\": \"good\" }, { \"network\": \"4G\", \"provider\":
\"Airtel\", \"quality\": \"good\" }, { \"network\": \"4G\",
\"provider\": \"Idea\", \"quality\": \"good\" }, { \"network\": \"4G\",
\"provider\": \"JIO 4G\", \"quality\": \"good\" }, { \"network\": \"w\",
\"provider\": \"Jio 4G\", \"quality\": \"fast\" }, { \"network\": \"w\",
\"provider\": \"airtel\", \"quality\": \"fast\" }, { \"network\":
\"4G\", \"provider\": \"JIO\", \"quality\": \"good\" }, { \"network\":
\"4G\", \"provider\": \"AIRTEL\", \"quality\": \"good\" }, {
\"network\": \"3G\", \"provider\": \"Vi India\", \"quality\":
\"average\", \"maxQuality\": \"average\" }, { \"network\": \"w\",
\"provider\": \"Vi India\", \"quality\": \"fast\" }, { \"network\":
\"4G\", \"provider\": \"VIL\", \"quality\": \"good\" }, { \"network\":
\"4G\", \"provider\": \"Vodafone\", \"quality\": \"good\" }, {
\"network\": \"w\", \"provider\": \"Vodafone IN\", \"quality\": \"fast\"
}, { \"network\": \"w\", \"provider\": \"IND airtel\", \"quality\":
\"fast\" }, { \"network\": \"2G\", \"provider\": \"airtel\",
\"quality\": \"slow\", \"maxQuality\": \"slow\" }, { \"network\":
\"4G\", \"provider\": \"Airtel \| airtel\", \"quality\": \"good\" }, {
\"network\": \"4G\", \"provider\": \"IND AirTel\", \"quality\": \"good\"
}, { \"network\": \"3G\", \"provider\": \"Vodafone IN\", \"quality\":
\"average\", \"maxQuality\": \"average\" }, { \"network\": \"w\",
\"provider\": \"Idea\", \"quality\": \"fast\" }, { \"network\": \"4G\",
\"provider\": \"JIO 4G \| Jio 4G\", \"quality\": \"good\" }, {
\"network\": \"4G\", \"provider\": \"AirTel\", \"quality\": \"good\" },
{ \"network\": \"3G\", \"provider\": \"Idea\", \"quality\": \"average\",
\"maxQuality\": \"average\" }, { \"network\": \"4G\", \"provider\": \"Vi
India \| Vodafone IN\", \"quality\": \"good\" }, { \"network\": \"2G\",
\"provider\": \"Vi India\", \"quality\": \"slow\", \"maxQuality\":
\"slow\" }, { \"network\": \"w\", \"provider\": \"Airtel\", \"quality\":
\"fast\" }, { \"network\": \"3G\", \"provider\": \"BSNL MOBILE\",
\"quality\": \"average\", \"maxQuality\": \"average\" }, { \"network\":
\"4G\", \"provider\": \"BSNL MOBILE\", \"quality\": \"good\" }, {
\"network\": \"4G\", \"provider\": \"Vi India \| Idea\", \"quality\":
\"good\" }, { \"network\": \"3G\", \"provider\": \"BSNL Mobile\",
\"quality\": \"average\", \"maxQuality\": \"average\" }, { \"network\":
\"4G\", \"provider\": \"BSNL Mobile\", \"quality\": \"good\" }, {
\"network\": \"4G\", \"provider\": \"IDEA\", \"quality\": \"good\" }, {
\"network\": \"w\", \"provider\": \"JIO 4G\", \"quality\": \"fast\" }, {
\"network\": \"w\", \"provider\": \"BSNL MOBILE\", \"quality\": \"fast\"
}, { \"network\": \"4G\", \"provider\": \"Jio\", \"quality\": \"good\"
}, { \"network\": \"4G\", \"provider\": \"Airtel_BH\", \"quality\":
\"good\" }, { \"network\": \"w\", \"provider\": \"BSNL Mobile\",
\"quality\": \"fast\" }, { \"network\": \"2G\", \"provider\": \"Idea\",
\"quality\": \"slow\", \"maxQuality\": \"slow\" }, { \"network\":
\"2G\", \"provider\": \"Vodafone IN\", \"quality\": \"slow\",
\"maxQuality\": \"slow\" }, { \"network\": \"4G\", \"provider\":
\"!dea\", \"quality\": \"good\" }, { \"network\": \"3G\", \"provider\":
\"CellOne\", \"quality\": \"average\", \"maxQuality\": \"average\" }, {
\"network\": \"4G\", \"provider\": \"JIO4G\", \"quality\": \"good\" }, {
\"network\": \"4G\", \"provider\": \"Airtel Stay Home\", \"quality\":
\"good\" }, { \"network\": \"2G\", \"provider\": \"Airtel\",
\"quality\": \"slow\", \"maxQuality\": \"slow\" }, { \"network\": \"w\",
\"provider\": \"JIO\", \"quality\": \"fast\" }, { \"network\": \"2G\",
\"provider\": \"IND airtel\", \"quality\": \"slow\", \"maxQuality\":
\"slow\" }, { \"network\": \"0\", \"provider\": \"Jio 4G\", \"quality\":
\"fast\", \"maxQuality\": \"fast\" }, { \"network\": \"3G\",
\"provider\": \"airtel\", \"quality\": \"average\", \"maxQuality\":
\"average\" }, { \"network\": \"WiFi\", \"provider\": \"AirTel\",
\"quality\": \"fast\" }, { \"network\": \"4G\", \"provider\":
\"unknown\", \"quality\": \"good\" }, { \"network\": \"WiFi\",
\"provider\": \"unknown\", \"quality\": \"fast\" }, { \"network\":
\"WiFi\", \"provider\": \"Jio\", \"quality\": \"fast\" }, { \"network\":
\"4G\", \"provider\": \"CellOne\", \"quality\": \"good\" }, {
\"network\": \"3G\", \"provider\": \"!dea\", \"quality\": \"average\",
\"maxQuality\": \"average\" }, { \"network\": \"w\", \"provider\":
\"VIL\", \"quality\": \"fast\" }, { \"network\": \"4G\", \"provider\":
\"Ind-Jio\", \"quality\": \"good\" }, { \"network\": \"w\",
\"provider\": \"Vi India \| Vodafone IN\", \"quality\": \"fast\" }, {
\"network\": \"3G\", \"provider\": \"VIL\", \"quality\": \"average\",
\"maxQuality\": \"average\" }, { \"network\": \"4G\", \"provider\":
\"Emergency calls only\", \"quality\": \"good\" }, { \"network\":
\"2G\", \"provider\": \"Jio 4G\", \"quality\": \"slow\", \"maxQuality\":
\"slow\" }, { \"network\": \"3G\", \"provider\": \"Vodafone\",
\"quality\": \"average\", \"maxQuality\": \"average\" }, { \"network\":
\"3G\", \"provider\": \"Jio 4G\", \"quality\": \"average\",
\"maxQuality\": \"average\" }, { \"network\": \"w\", \"provider\":
\"AIRTEL\", \"quality\": \"fast\" }, { \"network\": \"4G\",
\"provider\": \"No service\", \"quality\": \"good\" }, { \"network\":
\"w\", \"provider\": \"Vi India \| Idea\", \"quality\": \"fast\" }, {
\"network\": \"0\", \"provider\": \"airtel\", \"quality\": \"fast\",
\"maxQuality\": \"fast\" }, { \"network\": \"w\", \"provider\":
\"Vodafone\", \"quality\": \"fast\" }, { \"network\": \"w\",
\"provider\": \"Any\", \"quality\": \"fast\" }, { \"network\": \"4G\",
\"provider\": \"Any\", \"quality\": \"good\" }, { \"network\": \"3G\",
\"provider\": \"Any\", \"quality\": \"average\", \"maxQuality\":
\"average\" }, { \"network\": \"2G\", \"provider\": \"Any\",
\"quality\": \"slow\", \"maxQuality\": \"slow\" }, { \"network\":
\"Any\", \"provider\": \"Any\", \"quality\": \"good\", \"maxQuality\":
\"good\" } \], \"exo_sliding_percentile_max_weight\": 1000 },
\"speed_quality_map_v2\": { \"200\": \"slow\", \"1000\": \"average\",
\"2000\": \"betteraverage\", \"4000\": \"good\", \"8000\": \"fast\",
\"16000\": \"veryfast\" }, \"cameraProperties\": {
\"videoCaptureResolution\": \"EXTREMELY_HIGH\", \"recordBitrate\":
\"3000000\", \"fps\": \"30\", \"audioSampleRate\": \"44100\",
\"autoFocus\": \"Y\", \"autoExposure\": \"Y\", \"sharpness\": \"Y\",
\"beautify\": \"Y\", \"Intensity\": \"0.2\", \"videoStabilization\":
\"MODE_SUPER\", \"continuousFocus\": \"Y\", \"zoom\": \"Y\",
\"maxZoom\": \"99\", \"bitDepth\": \"8\", \"compileBitrate\":
\"3000000\", \"audioBitrate\": \"160000\", \"losslessAudio\": \"true\",
\"encoderPreset\": \"MEDIUM\", \"encodedCRF\": \"21\", \"encoderName\":
\"H.265\", \"encoderProfile\": \"high\", \"HDR\": \"st2084\" },
\"max_consumed_cache_items_count\": 30, \"attRules\": {
\"enableATTPrompt\": true, \"attPromptConfig\": {
\"minInstallLaunchCount\": 2, \"minUpgradeLaunchCount\": 3,
\"coolOffLaunchCount\": 2, \"maxAttemptCount\": 30, \"title\":
\"Personalized Ads\", \"message\": \"Josh would like permission to serve
personalized ads to you\" } }, \"uploadConfig\": {
\"resumableUploadsEnabled\": true, \"failureAutoRetryThreshold\": 5,
\"connectTimeout\": 60000, \"readTimeout\": 60000, \"writeTimeout\":
60000, \"tusChunkSize\": 1048576, \"tusRequestPayloadSize\": -1,
\"tusExtendedRetryDelays\": \[ 10000, 10000, 10000, 10000, 20000 \],
\"tusNormalRetryDelays\": \[ 500, 1000, 2000, 3000 \] }, \"quicHints\":
\[ { \"host\": \"qa-stream.myjosh.in\", \"port\": 443,
\"alternatePort\": 443 } \], \"bookmarkConfig\": {
\"musicTrimNudgeCount\": 5, \"bookMarkNudgeCount\": 5,
\"bookmarkSyncMinimumGap\": 86400000, \"bookmarkFetchItemLimit\": 10,
\"bookmarkItemMaxLimit\": 500 }, \"reactivate_account_config\": {
\"temporarily_deactivated_title\": \"We missed you\...\",
\"temporarily_deactivated_sub_title\": \"Tap the button below to
reactivate\\nyour account\", \"temporarily_deactivated_cta_text\":
\"Reactivate Account\", \"permanently_deactivated_title\": \"This
account has been permanently deleted\",
\"permanently_deactivated_sub_title\": \"To use Josh, create a new
account.\", \"permanently_deactivated_cta_text\": \"Create New Account\"
}, \"createPostConfig\": { \"noOfHashTagAllowed\": 5,
\"noOfUserHandleAllowed\": 3, \"maxNumKeywords\": 5 }, \"csConfig\": {
\"enabled\": true, \"frequencyTimeMS\": 86400000, \"bucketSizeNew\":
2000 }, \"encryption\": { \"version\": 1, \"key\":
\"LS0tLS1CRUdJTiBQVUJMSUMgS0VZLS0tLS0KTUlHZk1BMEdDU3FHU0liM0RRRUJBUVVBQTRHTkFEQ0JpUUtCZ1FDWkd2L1dncXo1OEhjOURMZUFObHRmNFVJMwp3Vkoyb0xJYzZEemRheFdaTXRSVkYzTGYySlFSZURQMTRsKzNYUGdXaC9lVlFBU1Z3QTZKaUYxemw1WXhJS1ovCmppc2NEaFRDS25idmE1dTdrYjFMb0FUTlFKQlZtZGhSOFVZbWc3dUZWMnJTVUg3UEJ3VytyLzhKcm9sOXA1SGEKckIxVlBPMEtIR0YyZ2JNS2V3SURBUUFCCi0tLS0tRU5EIFBVQkxJQyBLRVktLS0tLQo=\"
}, \"profile_wizard_config\": { \"completeMsgDismissTimeInMills\": 3000,
\"setUpProfileMsgShowTimeInDays\": 360 }, \"snapchatLogoutIconUrl\":
\"https://sdk.bitmoji.com/me/sticker/#AVATAR_ID#/204d8f0d-50e5-4db5-a810-f6525a68dc39\",
\"fileUploads\": { \"twitter\":
\"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/Twitter-Logo.webp\",
\"instagram\":
\"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/Instagram-Logo.webp\",
\"facebook\":
\"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/Facebook-Logo.webp\",
\"whatsapp\":
\"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/Whatsapp-Logo.webp\",
\"uploads\": \"VmlkZW8=.png\", \"trending\": \"VHJlbmRpbmdfMQ==.png\",
\"likes\": \"TGlrZV8x.png\", \"drafts\": \"ZHJhZnRz.png\", \"tagged\":
\"TWVudGlvbl8x.png\", \"discovery_icon\":
\"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/ZGlzY292ZXJ5.png\",
\"audio_icon\":
\"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/bXVzaWM=.png\",
\"hello\":
\"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/YmdfY3VzdG9t.png\",
\"trending_icon\":
\"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/VHJlbmRpbmc=.png\",
\"photos\": \"Sm9zaCAoMyk=.png\", \"social\": \"U29jaWFsXzE=.png\",
\"uploads_selected\": \"dXBsb2Fkc19zZWxlY3RlZA==.png\",
\"likes_selected\": \"Sm9zaEAyeF8=.png\", \"trending_selected\":
\"Sm9zaEAyeA==.png\", \"social_selected\": \"TmV3cy0xLjU=.png\",
\"tagged_selected\": \"QA==.png\", \"photos_selected\":
\"Sm9zaA==.png\", \"drafts_selected\": \"UGFwZXI=.png\",
\"gifting_icon_url\": \"Z2lmdF9pY29u.png\", \"tipping_icon_url\":
\"Z2lmdF9pY29u.png\" } } } }

**3. Update Version Entity**

update the version entity

- **Request Method and URL:**

POST :
<https://qa-gateway.coolfie.io/api/v1/cms/update/JOSH_STATIC_CONFIG>

- **cURL:**

jsoncurl \--location \--request POST
\'https://qa-gateway.coolfie.io/api/v1/cms/update/JOSH_STATIC_CONFIG\'
\\ \--header \'Content-Type: application/json\' \\ \--data-raw \'{
\"data\": { \"jems_wallet_page_url\":
\"https://share.myjosh.in/webview/jems-wallet?user_uuid={0}&client_id={1}\",
\"profile_rejected_show_count\": 2, \"gifters_list_api\":
\"http://api.myjosh.in/apij/gift/gifters-list\",
\"bookmark_webview_url\": \"https://share.myjosh.in/webview/bookmarks\",
\"search_default_popular_feed_url\":
\"https://feed.myjosh.in/search/?q=viral\", \"tipping_icon_url\":
\"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/Z2lmdF9pY29u.png\",
\"gifting_icon_url\":
\"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/Z2lmdF9pY29u.png\",
\"recent_search_item_count\": 25, \"bottom_bar_tab_sequence\": \[
\"HOME\", \"EXPLORE\", \"LIVE\", \"SHOP\", \"NOTIFICATIONINBOX\",
\"PROFILE\" \], \"disable_custom_tab_social_auth\": false,
\"is_seekbar_enabled\": true, \"educational_nudge_count_per_session\":
3, \"educational_nudge_duration_in_ms\": 3000,
\"is_tabbar_swiping_enabled\": true, \"like_comment_tab_list\": \[
\"LIKE\", \"COMMENT\", \"GIFT\" \], \"contact_sync_message_config\": {
\"zero_state_message\": \"Contact sync successful, no friends were found
but you can always invite them later.\", \"after_follow_message\":
\"You\'\\\'\'ve followed %d people from your contact book\",
\"sync_in_bg\": \"Enjoy videos while we sync your contacts.\",
\"with_contacts_state\": \"Contacts synced successfully. Tap to find
your friends.\", \"action_text\": \"Find Friends\" },
\"camera_tab_sequence\": \[ \"CAMERA\", \"PHOTOS\", \"MEMES\",
\"TEMPLATES\", \"DUETS\" \], \"sticky_notif_refresh_interval_in_mins\":
15, \"cs_ttl_duration_in_minutes\": \"30\",
\"wait_on_cs_page_in_seconds\": \"3\", \"max_photo_upload_limit\": 10,
\"supportedMimetypes\": \[ \"video/mp4\", \"video/quicktime\",
\"video/x-ms-wmv\", \"video/mov\", \"video/mpg\" \],
\"reaction_sync_interval_in_seconds\": 86400, \"maxCommentCharLimit\":
150, \"max_recent_cache_action_count\": 30, \"showDataSaverMode\": true,
\"splash_ad_request_launch\": 2, \"repeated_launch_api_request_delay\":
10000, \"show_share_nudge_loop_count\": 2,
\"max_share_nudge_show_count\": 3,
\"max_lifetime_show_share_nudge_count\": 7, \"max_edit_nudge_count\": 3,
\"grid_item_count\": 3, \"enable_youtube_connect\": true,
\"enable_instagram_connect\": true, \"softRelaunchDelay\": 600000,
\"hardRelaunchDelay\": 1800000, \"animated_icon_duration_in_ms\": 500,
\"create_post_max_char\": 120, \"precache_interest_icons\": true,
\"video_edit_resolution\": 720,
\"max_sticker_comment_nudge_show_count\": 1,
\"is_apply_for_verification_enabled\": true,
\"create_video_nudge_dismissal\": 3000, \"vote_nudge_dismissal\": 3000,
\"share_voted_video_nudge_dismissal\": 3000, \"effectsExpiryMaxDays\":
30, \"items_toshow_in_inbox\": 7, \"max_tpv_profile_suggestions\": 5,
\"reduced_percent_volume_dub\": 20, \"vote_interval_in_seconds\": 86400,
\"experiment_incorrect_otp_max_attempts\": 2,
\"experiment_resend_otp_max_attempts\": 2, \"snapchatLogoutIconUrl\":
\"https://sdk.bitmoji.com/me/sticker/#AVATAR_ID#/204d8f0d-50e5-4db5-a810-f6525a68dc39\",
\"enable_lite_sync_once\": false, \"disable_experiment_api\": false,
\"enableAutoSaveVideos\": true, \"max_selected_videos_gallery\": 15,
\"max_event_videos_to_download\": 2, \"max_event_videos_to_show\": 2,
\"game_center_url\":
\"https://feed.myjosh.in/page_collection/game/main-game-page\",
\"allow_splash_ad\": false, \"allow_masthead_ad\": false,
\"disable_josh_live\": false, \"jl_enable_room_options\": false,
\"jl_is_default_video_enabled\": true,
\"noti_display_on_tray_event_enable\": true, \"device_wake_up_flag\":
false, \"refresh_wait_time_ms\": 1500, \"hide_block_user_option\":
false, \"image_share_url\": \"https://api.myjosh.in/image/\",
\"social_share_url\": \"https://api.myjosh.in/social/\",
\"images_auto_scroll_duration_in_ms\": 5000, \"send_tip_page_url\":
\"https://share.myjosh.in/webview/pay-tips?tip_to={0}&tip_by={1}&tip_to_image_url={2}&tip_to_user_name={3}&tip_by_user_name={4}\",
\"tip_transactions_page_url\":
\"https://share.myjosh.in/webview/tip-transactions?user_id={0}\",
\"buy_jems_page_url\":
\"https://share.myjosh.in/webview/pay-tips-v1?tip_to={0}&tip_by={1}&tip_to_image_url={2}&tip_to_user_name={3}&tip_by_user_name={4}&package_id={5}&package_collection_id={6}\",
\"disable_buffer_settings_for_ads\": false, \"mute_ab_test_variant\":
\"SESSION_MUTE\", \"zone_info_dialog_data\": { \"title\":
\"\<h1\>Content on this page is community managed.\</h1\>\",
\"message\": \"\<p\>Josh does not make any warranties about the
completeness, reliability and accuracy of this information. \<a
href=\'\\\'\'https://share.myjosh.in/terms-conditions\'\\\'\'\>Read
TnC\</a\>\</p\>\", \"ctaText\": \"\<strong\>Okay\</strong\>\" },
\"template_search_hints\": \[ \"Good Morning\", \"Love\" \],
\"image_card_config\": { \"min_time_threshold_in_ms\": 5000,
\"max_count_per_session\": 3, \"animation_list\": \[ 0, 1, 5, 6, 8 \] },
\"appsflyer_events\": { \"C2\": 180, \"C3\": 180, \"C4\": 180, \"C5\":
180, \"C6\": 180, \"C7\": 180, \"C8\": 180, \"C9\": 180, \"C10\": 180,
\"C11\": 180, \"C12\": 540, \"C13\": 540, \"C14\": 540, \"C15\": 540,
\"C16\": 1000, \"C17\": 1, \"C18\": 1, \"C19\": 180, \"C20\": 180,
\"C22\": 540, \"C23\": 540, \"C24\": 540, \"C25\": 540, \"C26\": 540,
\"C27\": 180, \"C28\": 180, \"C29\": 180, \"C30\": 180, \"C31\": 180,
\"C32\": 180, \"C33\": 180, \"C34\": 180, \"C35\": 180, \"C36\": 180,
\"C37\": 180, \"C38\": 180, \"C39\": 180, \"C40\": 180, \"C41\": 180,
\"C42\": 180, \"C43\": 180, \"C44\": 180, \"C45\": 180, \"C46\": 180,
\"C47\": 180, \"C48\": 180, \"C49\": 180, \"C50\": 180 }, \"zero_page\":
{ \"like_comment_fpv\": { \"COMMENT\": { \"title\": \"No Comments\" },
\"GIFT\": { \"description\": \"Explore gift section and be the first one
to send gift\", \"title\": \"No Gift Received\" }, \"LIKE\": {
\"title\": \"No Likes\" } }, \"like_comment_tpv\": { \"COMMENT\": {
\"title\": \"No Comments\" }, \"GIFT\": { \"cta_text\": \"Send Gifts\",
\"description\": \"Explore gift section and be the first one to send
gift\", \"title\": \"No Gift Received\" }, \"LIKE\": { \"title\": \"No
Likes\" } }, \"user_fpv\": { \"2\": { \"description\": \"Try posting
more content and invite your friends\", \"title\": \"No Fans\" }, \"3\":
{ \"cta_deeplink\":
\"http://share.myjosh.in/page/discovery/main-discovery-page\",
\"cta_text\": \"Discovery\", \"description\": \"Explore discover section
and follow creators and other users\", \"title\": \"Not Following
Anyone\" }, \"4\": { \"cta_deeplink\":
\"http://share.myjosh.in/page/discovery/main-discovery-page\",
\"cta_text\": \"Discovery\", \"description\": \"Explore discover section
and follow pages\", \"title\": \"Not Following Any Pages\" }, \"5\": {
\"title\": \"No Suggestion\" } }, \"user_tpv\": { \"1\": { \"title\":
\"No Mutual Followers\" }, \"2\": { \"title\": \"No Fans\" }, \"3\": {
\"title\": \"No Followers\" }, \"4\": { \"title\": \"No Pages\" },
\"5\": { \"title\": \"No Suggestions\" } }, \"zone\": { \"1\": {
\"title\": \"No Followers\" }, \"2\": { \"title\": \"No Suggestions\" }
} }, \"nlfc_embed_config\": { \"disable_nlfc\": false,
\"min_time_spent_to_trigger\": 3000, \"social_interactions_trigger\": \[
\"like\", \"share\", \"comment\", \"click\" \],
\"skip_nlfc_for_session_on_failure\": 3, \"min_offset_to_append\": 1 },
\"nlfc_image_config\": { \"disable_nlfc\": false,
\"min_time_spent_to_trigger\": 3000, \"social_interactions_trigger\": \[
\"like\", \"share\", \"comment\" \],
\"skip_nlfc_for_session_on_failure\": 3, \"min_offset_to_append\": 1 },
\"pullNotificationConfig\": { \"pull_notifications_enabled\": true,
\"firstTimePullDelay\": 300 }, \"api_sequencing_config\": {
\"api_sequencing_max_delay_ms\": 180000, \"api_hit_interval_time_ms\":
4000, \"fl_api_hit_interval_time_ms\": 2000, \"delay_max_video_count\":
10, \"cache_api_delay_time_ms\": 10000, \"delay_after_handshake\": 3000
}, \"myelin_config\": { \"enable\": false, \"disable_for_verified\": \[
\"k\", \"m\", \"l\" \], \"sync_time\": 86400000, \"quality\": {
\"fast\": \"average\", \"good\": \"average\", \"average\": \"average\" }
}, \"wakeUpPartnerInformation\": { \"minimumBatteryRequired\": 15,
\"partnerPackages\": \[ { \"packageName\": \"com.eterno\", \"action\":
\"com.eterno.intent.woken_up_service_start\",
\"foregroundServiceSupport\": true, \"wakeupsections\": \[
\"Notification\", \"Deeplink\", \"Splash\", \"App Controller\" \],
\"dndStartTime\": 82800, \"dndEndTime\": 21300, \"wakeDelay\": 86400000,
\"disabledManufacturer\": \[\] }, { \"packageName\":
\"com.newsdistill.mobile\", \"action\":
\"com.newsdistill.mobile.intent.ACTION_WAKEUP\",
\"foregroundServiceSupport\": true, \"wakeupsections\": \[
\"Notification\", \"Deeplink\", \"Splash\", \"App Controller\" \],
\"dndStartTime\": 82800, \"dndEndTime\": 21300, \"wakeDelay\": 86400000,
\"disabledManufacturer\": \[\] } \] }, \"discovery_tab_list\": \[ {
\"id\": \"main-discovery-page\", \"name\": \"Discovery\",
\"tab_icon_url\": \"discovery_icon\", \"url\":
\"https://feed.myjosh.in/page/discovery/main-discovery-page\", \"type\":
\"DISCOVERY\" }, { \"id\": \"main-audio-page\", \"name\": \"Music\",
\"tab_icon_url\": \"audio_icon\", \"url\":
\"https://feed.myjosh.in/page/audio/main-audio-page\", \"type\":
\"AUDIO\" } \], \"duet_video_volume_config\": { \"dueted_video_volume\":
20, \"recorded_video_volume\": 100 }, \"wa_status_sent_config\": \[ {
\"min_version\": 30, \"max_version\": 2147483647, \"enable\": true,
\"path_wa_status\":
\"/Android/media/com.whatsapp/WhatsApp/Media/.Statuses\",
\"path_wa_sent_video\":
\"/Android/media/com.whatsapp/WhatsApp/Media/WhatsApp Video/Sent\",
\"path_wa_sent_image\":
\"/Android/media/com.whatsapp/WhatsApp/Media/WhatsApp Images/Sent\" }, {
\"min_version\": 0, \"max_version\": 29, \"enable\": true,
\"path_wa_status\": \"WhatsApp/Media/.Statuses\",
\"path_wa_sent_video\": \"WhatsApp/Media/WhatsApp Video/Sent\",
\"path_wa_sent_image\": \"WhatsApp/Media/WhatsApp Images/Sent\" } \],
\"compilation_rules\": { \"default\": 720, \"resolutions\": \[ {
\"max\": 2147483647, \"min\": 2160, \"result\": 2160 }, { \"max\": 2059,
\"min\": 1080, \"result\": 1080 }, { \"max\": 1079, \"min\": 641,
\"result\": 720 }, { \"max\": 640, \"min\": 481, \"result\": 640 }, {
\"max\": 480, \"min\": 361, \"result\": 480 }, { \"max\": 360, \"min\":
1, \"result\": 360 } \] }, \"createPostConfig\": {
\"noOfHashTagAllowed\": 5, \"noOfUserHandleAllowed\": 3,
\"maxNumKeywords\": 5 }, \"uploadConfig\": {
\"resumableUploadsEnabled\": true, \"failureAutoRetryThreshold\": 5,
\"connectTimeout\": 60000, \"readTimeout\": 60000, \"writeTimeout\":
60000, \"tusChunkSize\": 1048576, \"tusRequestPayloadSize\": -1,
\"tusExtendedRetryDelays\": \[ 10000, 10000, 10000, 10000, 20000 \],
\"tusNormalRetryDelays\": \[ 500, 1000, 2000, 3000 \] },
\"lp_gotosetting_dialog_config\": { \"lp_gotosetting_dialog_title\":
\"Allow Josh to access this device's location?\",
\"lp_gotosetting_dialog_desc\": \"This will help you reach a more
relevant audience &amp; gain followers, Please go to settings and allow
location permission\", \"lp_gotosetting_dialog_pos_action\": \"Go To
Settings\", \"lp_gotosetting_dialog_neg_action\": \"Later\",
\"lp_gotosetting_dialog_show_after_x_post\": 4 }, \"postLangMapping\":
\[ { \"languageGroup\": \[ \"na\" \], \"values\": \[ \"hi\", \"en\",
\"te\", \"ta\", \"ml\", \"kn\", \"mr\", \"gu\", \"bn\", \"or\", \"pa\",
\"bh\" \] }, { \"languageGroup\": \[ \"hi\", \"mr\", \"pa\", \"gu\",
\"bh\", \"or\", \"bn\" \], \"values\": \[ \"hi\", \"mr\", \"pa\",
\"gu\", \"bh\", \"or\", \"bn\", \"en\", \"te\", \"ta\", \"ml\", \"kn\"
\] }, { \"languageGroup\": \[ \"te\", \"ta\", \"ml\", \"kn\" \],
\"values\": \[ \"te\", \"ta\", \"ml\", \"kn\", \"hi\", \"en\", \"mr\",
\"pa\", \"gu\", \"bh\", \"or\", \"bn\" \] } \], \"uploadShareConfig\": {
\"shareChannels\": \[ { \"pkgName\": \"com.twitter.android\",
\"iconUrl\": \"twitter\", \"name\": \"TWITTER\" }, { \"pkgName\":
\"com.instagram.android\", \"iconUrl\": \"instagram\", \"name\":
\"INSTAGRAM\" }, { \"pkgName\": \"com.facebook.katana\", \"iconUrl\":
\"facebook\", \"name\": \"FACEBOOK\" }, { \"pkgName\": \"com.whatsapp\",
\"iconUrl\": \"whatsapp\", \"name\": \"WHATSAPP\" } \],
\"initialPollingDelayMs\": 10000, \"pollingDelayMs\": 7000,
\"maxPollingAttempts\": 15, \"shareNudgeCount\": 7,
\"delaySharePromptHideMs\": 3000, \"delayPIPSuccessHideMs\": 5000 },
\"profileBlockedConfig\": { \"pb_config_title\": \"Profile Blocked!\",
\"pb_config_subtitle\": \"This profile has been blocked due to violation
of community guidelines.\", \"pb_config_cta\": \"Learn more\",
\"pb_config_cta_link\":
\"https://share.myjosh.in/help/community-violation-guidelines\",
\"pb_config_subtitle_dialog\": \"You cannot post a video\",
\"pb_config_cta_neg_dialog\": \"Dismiss\" },
\"fpv_profile_quality_config\": \[ { \"network_quality\": \"veryfast\",
\"profile_quality\": \"veryfast\" }, { \"network_quality\": \"fast\",
\"profile_quality\": \"veryfast\" }, { \"network_quality\": \"good\",
\"profile_quality\": \"veryfast\" }, { \"network_quality\": \"average\",
\"profile_quality\": \"good\" }, { \"network_quality\": \"slow\",
\"profile_quality\": \"average\" } \], \"fpv_quality_nudge_config\": {
\"network_quality\": \"average\", \"message\": \"Slow Internet! Playing
Video in Low Quality\", \"duration\": 3000, \"per_session_count\": 1 },
\"deviceWakeUpConfiguration\": { \"minimumBatteryRequired\": 15,
\"dndStartTime\": 82800, \"dndEndTime\": 21300, \"wakeDelay\": 86400000
}, \"quality_mapping\": \[ { \"network_quality\": \"veryfast\",
\"profile_quality\": \"fast\" }, { \"network_quality\": \"fast\",
\"profile_quality\": \"fast\" }, { \"network_quality\": \"good\",
\"profile_quality\": \"good\" }, { \"network_quality\": \"average\",
\"profile_quality\": \"average\" }, { \"network_quality\": \"slow\",
\"profile_quality\": \"slow\" } \], \"cache_config\": {
\"cache_offline_directory_max_size_in_mb\": 200,
\"cache_prefetch_directory_max_size_in_mb\": 250,
\"cache_directory_max_size_in_mb\": 100, \"clear_session_data\": false,
\"min_cache_item_to_fetch_api\": 5, \"hard_start_config\": {
\"disableHardStart\": true, \"file_download_percentage\": 100,
\"download_high_bitrate_variant\": true,
\"min_stream_download_on_average_network\": 2,
\"min_stream_download_on_fast_network\": 2,
\"min_stream_download_on_good_network\": 2,
\"min_stream_download_on_slow_network\": 2 }, \"session_start_config\":
{ \"slow\": { \"from_offline_back_to_back\": 10 }, \"average\": {
\"from_offline_back_to_back\": 7 }, \"good\": {
\"from_offline_back_to_back\": 7 }, \"fast\": {
\"from_offline_back_to_back\": 5 }, \"veryfast\": {
\"from_offline_back_to_back\": 5 } }, \"prefetch_download_config\": {
\"disable_cache\": false, \"prefetch_download_count_config\": {
\"slow\": { \"no_of_videos\": 8, \"min_cache_percentage_ofl_to_onl\":
100 }, \"average\": { \"no_of_videos\": 8,
\"min_cache_percentage_ofl_to_onl\": 85 }, \"good\": { \"no_of_videos\":
8, \"min_cache_percentage_ofl_to_onl\": 70 }, \"fast\": {
\"no_of_videos\": 8, \"min_cache_percentage_ofl_to_onl\": 50 },
\"veryfast\": { \"no_of_videos\": 8,
\"min_cache_percentage_ofl_to_onl\": 50 } } },
\"offline_download_config\": { \"sort_type\": \"recency\",
\"disable_cache\": false, \"global_cache_ttl_days\": 180,
\"max_cache_item\": 40, \"recommended_video_quality\": \"good\",
\"ucq_download_config\": { \"average\": { \"exit\": 2, \"minimise\": 1,
\"notification\": 2 }, \"fast\": { \"exit\": 3, \"minimise\": 2,
\"notification\": 2 }, \"slow\": { \"exit\": 2, \"minimise\": 1,
\"notification\": 2 }, \"good\": { \"exit\": 3, \"minimise\": 2,
\"notification\": 2 }, \"veryfast\": { \"exit\": 3, \"minimise\": 2,
\"notification\": 2 } }, \"cache_api_sync_time_secs\": 259200,
\"app_inactivity_duration_days\": 30 }, \"buffer_threshold_config\": {
\"average\": { \"organic\": { \"buffer_threshold_initial_videos_secs\":
4, \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 4 },
\"inorganic\": { \"buffer_threshold_initial_videos_secs\": 4,
\"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 4 } },
\"fast\": { \"organic\": { \"buffer_threshold_initial_videos_secs\": 4,
\"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 4 },
\"inorganic\": { \"buffer_threshold_initial_videos_secs\": 4,
\"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 4 } },
\"slow\": { \"organic\": { \"buffer_threshold_initial_videos_secs\": 4,
\"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 4 },
\"inorganic\": { \"buffer_threshold_initial_videos_secs\": 4,
\"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 4 } },
\"good\": { \"organic\": { \"buffer_threshold_initial_videos_secs\": 4,
\"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 4 },
\"inorganic\": { \"buffer_threshold_initial_videos_secs\": 4,
\"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 4 } },
\"veryfast\": { \"organic\": { \"buffer_threshold_initial_videos_secs\":
4, \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 4 },
\"inorganic\": { \"buffer_threshold_initial_videos_secs\": 4,
\"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 4 } } } },
\"data_saver_cache_config\": {
\"cache_offline_directory_max_size_in_mb\": 100,
\"cache_prefetch_directory_max_size_in_mb\": 200,
\"cache_directory_max_size_in_mb\": 100, \"clear_session_data\": false,
\"recommended_profile\": \"average\", \"enable_notification_prefetch\":
true, \"min_cache_item_to_fetch_api\": 5, \"session_start_config\": {
\"slow\": { \"from_offline_back_to_back\": 1 }, \"average\": {
\"from_offline_back_to_back\": 1 }, \"good\": {
\"from_offline_back_to_back\": 1 }, \"fast\": {
\"from_offline_back_to_back\": 1 }, \"veryfast\": {
\"from_offline_back_to_back\": 1 } }, \"prefetch_download_config\": {
\"disable_cache\": true, \"prefetch_download_count_config\": { \"slow\":
{ \"no_of_videos\": 0, \"min_cache_percentage_ofl_to_onl\": 100 },
\"average\": { \"no_of_videos\": 0, \"min_cache_percentage_ofl_to_onl\":
80 }, \"good\": { \"no_of_videos\": 0,
\"min_cache_percentage_ofl_to_onl\": 60 }, \"fast\": { \"no_of_videos\":
0, \"min_cache_percentage_ofl_to_onl\": 40 }, \"veryfast\": {
\"no_of_videos\": 0, \"min_cache_percentage_ofl_to_onl\": 25 } } },
\"offline_download_config\": { \"sort_type\": \"recency\",
\"disable_cache\": true, \"global_cache_ttl_days\": 15,
\"max_cache_item\": 40, \"recommended_video_quality\": \"good\",
\"ucq_download_config\": { \"average\": { \"exit\": 0, \"minimise\": 0,
\"notification\": 0 }, \"fast\": { \"exit\": 0, \"minimise\": 0,
\"notification\": 0 }, \"slow\": { \"exit\": 0, \"minimise\": 0,
\"notification\": 0 }, \"good\": { \"exit\": 0, \"minimise\": 0,
\"notification\": 0 }, \"veryfast\": { \"exit\": 0, \"minimise\": 0,
\"notification\": 0 } }, \"cache_api_sync_time_secs\": 86400,
\"app_inactivity_duration_days\": 10 }, \"buffer_threshold_config\": {
\"average\": { \"organic\": { \"buffer_threshold_initial_videos_secs\":
6, \"initial_videos_max_index\": 7, \"buffer_threshold_secs\": 6 },
\"inorganic\": { \"buffer_threshold_initial_videos_secs\": 6,
\"initial_videos_max_index\": 7, \"buffer_threshold_secs\": 6 } },
\"fast\": { \"organic\": { \"buffer_threshold_initial_videos_secs\": 6,
\"initial_videos_max_index\": 7, \"buffer_threshold_secs\": 6 },
\"inorganic\": { \"buffer_threshold_initial_videos_secs\": 6,
\"initial_videos_max_index\": 7, \"buffer_threshold_secs\": 6 } },
\"slow\": { \"organic\": { \"buffer_threshold_initial_videos_secs\": 6,
\"initial_videos_max_index\": 7, \"buffer_threshold_secs\": 6 },
\"inorganic\": { \"buffer_threshold_initial_videos_secs\": 6,
\"initial_videos_max_index\": 7, \"buffer_threshold_secs\": 6 } },
\"good\": { \"organic\": { \"buffer_threshold_initial_videos_secs\": 6,
\"initial_videos_max_index\": 7, \"buffer_threshold_secs\": 6 },
\"inorganic\": { \"buffer_threshold_initial_videos_secs\": 6,
\"initial_videos_max_index\": 7, \"buffer_threshold_secs\": 6 } },
\"veryfast\": { \"organic\": { \"buffer_threshold_initial_videos_secs\":
6, \"initial_videos_max_index\": 7, \"buffer_threshold_secs\": 6 },
\"inorganic\": { \"buffer_threshold_initial_videos_secs\": 6,
\"initial_videos_max_index\": 7, \"buffer_threshold_secs\": 6 } } } },
\"duet_config\": { \"camera_portrait_min_height_to_width\": { \"h\": 16,
\"w\": 9 }, \"camera_portrait_max_height_to_width\": { \"h\": 21, \"w\":
9 }, \"camera_landscape_min_width_to_height\": { \"h\": 8, \"w\": 9 },
\"camera_landscape_max_width_to_height\": { \"h\": 9, \"w\": 21 },
\"video_download_url\": \"\", \"create_and_edit_configs\": {
\"duetable_config_for_verified\": { \"default_value\": \"OFF\",
\"aspect_ratio\": { \"allow_for_portrait\": true, \"allow_for_square\":
true, \"allow_for_landscape\": false }, \"video_source\": {
\"camera_with_josh_library\": true, \"camera_without_josh_library\":
true, \"gallery_with_josh_library\": true,
\"gallery_without_josh_library\": true, \"duet\": false },
\"video_source_v2\": \[ { \"srcType\": \"camera\", \"josh_library\":
true, \"non_josh_library\": true }, { \"srcType\": \"gallery\",
\"josh_library\": true, \"non_josh_library\": true }, { \"srcType\":
\"multi_segment_camera\", \"josh_library\": true, \"non_josh_library\":
true }, { \"srcType\": \"multi_segment_gallery\", \"josh_library\":
true, \"non_josh_library\": true }, { \"srcType\":
\"multi_segment_camera_gallery\", \"josh_library\": true,
\"non_josh_library\": true }, { \"srcType\": \"external_d-id\",
\"josh_library\": true, \"non_josh_library\": true }, { \"srcType\":
\"external\", \"josh_library\": true, \"non_josh_library\": true }, {
\"srcType\": \"duet\", \"josh_library\": false, \"non_josh_library\":
false } \] }, \"duetable_config_for_nonverified\": { \"default_value\":
\"OFF\", \"aspect_ratio\": { \"allow_for_portrait\": true,
\"allow_for_square\": true, \"allow_for_landscape\": false },
\"video_source\": { \"camera_with_josh_library\": true,
\"camera_without_josh_library\": true, \"gallery_with_josh_library\":
true, \"gallery_without_josh_library\": true, \"duet\": false },
\"video_source_v2\": \[ { \"srcType\": \"camera\", \"josh_library\":
true, \"non_josh_library\": true }, { \"srcType\": \"gallery\",
\"josh_library\": true, \"non_josh_library\": true }, { \"srcType\":
\"multi_segment_camera\", \"josh_library\": true, \"non_josh_library\":
true }, { \"srcType\": \"multi_segment_gallery\", \"josh_library\":
true, \"non_josh_library\": true }, { \"srcType\":
\"multi_segment_camera_gallery\", \"josh_library\": true,
\"non_josh_library\": true }, { \"srcType\": \"external_d-id\",
\"josh_library\": true, \"non_josh_library\": true }, { \"srcType\":
\"external\", \"josh_library\": true, \"non_josh_library\": true }, {
\"srcType\": \"duet\", \"josh_library\": false, \"non_josh_library\":
false } \] } } }, \"splash_time\": 2000, \"splashTime\": 1000,
\"fire_track_from_cache\": true, \"handshake_version\": \"470\",
\"performance_analytics_enabled\": false, \"upload_duration\": 120,
\"disable_error_event\": false, \"disable_slow_network_prompts\": false,
\"speed_quality_map\": { \"100\": \"slow\", \"500\": \"average\",
\"1000\": \"good\", \"10000\": \"fast\", \"50000\": \"veryfast\" },
\"record_duration\": 15, \"first_time_pull_delay\": 300,
\"first_chunk_request_params\": { \"cdn\": \"Y\", \"src\": \"app\" },
\"max_upload_size\": 200, \"upgrade\": \"LATEST\", \"rateConfig\": {
\"enable\": true, \"preActivitySessionWaitTimeInSeconds\": 600,
\"minNumberOfStoriesViewedPerSession\": 10, \"minNumberOfBooksRead\": 4,
\"maxNumberOfTimesToShowRateScreen\": 3,
\"minNumberOfDaysToWaitShowingRateScreen\": 30,
\"maxWaitDaysForNewUsersToShowRateScreen\": 7,
\"minLaunchesForNewUsersToShowRateScreen\": 3,
\"minNumberOfDaysUserToWaitAfterLastSeen\": 10,
\"minNumberOfAppLaunchesToWaitAfterLastSeen\": 10 },
\"maxHistoryCount\": 50, \"enable_reactions_api_hit\": true,
\"max_recent_interaction_count\": 50,
\"location_fetch_interval_in_seconds\": 86400,
\"min_gap_between_app_update_prompt_secs\": 172800,
\"video_views_in_session_for_update_prompt\": 5, \"permission\": {
\"id\": 24, \"event\": \"appLaunch\", \"activity\": { \"type\":
\"permission\", \"attributes\": { \"gapCount\": \"4\", \"permDesc\":
\"Josh needs access to the following\", \"permTitle\": \"Permissions
required\", \"openSettings\": \"Josh needs storage access to perform
this action. To enable it, please visit your app settings.\",
\"settingsAction\": \"Settings\", \"storagePermDesc\": \"We need this
for critical features like downloading a video.\", \"locationPermDesc\":
\"We need this to show you videos being posted by users around you.\",
\"storagePermSubtitle\": \"Storage Access\", \"locationPermSubtitle\":
\"Location Access\", \"permissionNegativeBtn\": \"LATER\",
\"permissionPositiveBtn\": \"Allow\" } }, \"resource\": \"coolfie\",
\"precondition\": { \"minItemsViewed\": 7, \"minTimeEngaged\": 0,
\"maxNumberOfDisplay\": 0, \"minNumberOfOccurences\": 5 } },
\"fire_comscore_from_cache\": true, \"max_notifications_in_tray\": 6,
\"thumbnail_qualities\": { \"fast\": { \"quality\": \"h\",
\"resolution\": 480 }, \"good\": { \"quality\": \"h\", \"resolution\":
480 }, \"slow\": { \"quality\": \"h\", \"resolution\": 480 },
\"average\": { \"quality\": \"h\", \"resolution\": 480 } },
\"default_notification_duration\": 120, \"max_upload_bitrate\": 1500,
\"pull_notifications_enabled\": true, \"video_qualities\": { \"fast\": {
\"quality\": \"h\", \"resolution\": 480 }, \"good\": { \"quality\":
\"h\", \"resolution\": 480 }, \"slow\": { \"quality\": \"h\",
\"resolution\": 480 }, \"average\": { \"quality\": \"h\",
\"resolution\": 480 } }, \"disable_firebase_perf\": false,
\"google_play_url\": { \"share_video_text\": \"Download Josh for more
videos like this!\", \"download_video_text\": \"Download Josh for more
videos like this!\", \"share_google_play_url\":
\"https://m.myjosh.in/6OaT/32e07bf\", \"setting_google_play_url\":
\"https://m.myjosh.in/6OaT/568901e6\", \"download_google_play_url\":
\"https://m.myjosh.in/6OaT/6d76ce25\", \"download_live_stream_text\":
\"Download Josh for more livestreams like this!\", \"duet_share_text\":
\"Create and watch amazing duets with %1\$s! \\n%2\$s \\nDownload Josh
now to watch & even create more great videos like this!
\\nhttps://play.google.com/store/apps/details?id=com.eterno.shortvideos\"
}, \"default_notification_text\": \"Welcome to Josh! Check out the
latest news in your preferred language.\",
\"story_detail_error_page_url\":
\"https://m.dailyhunt.in/webItem/errorPage.html\",
\"share_floating_icon_type\": \"floatingIconBentArrow\",
\"upload_format_list\": \[ \"3gp\", \"mp4\" \], \"nlfc_config\": {
\"disable_nlfc\": false, \"min_time_spent_to_trigger\": 9000,
\"min_time_spent_to_trigger_with_social\": 9000,
\"min_percentage_completion\": 85, \"skip_nlfc_for_session_on_failure\":
3, \"min_offset_to_append\": 1 }, \"moderationNsfwReportUrl\":
\"https://share.myjosh.in/report/machine-moderation/1\",
\"moderationDuplicateReportUrl\":
\"https://share.myjosh.in/report/ownership-content/1\",
\"joshCam1Config\": { \"licenseUrl\":
\"https://stream.myjosh.in/stream/prod-ugc-contents/joshCam1Config/license/android/20986-269-0d067db8c6410857b82bc96e5405a5e9.lic\",
\"licenseUrliOS\":
\"https://stream.myjosh.in/stream/prod-ugc-contents/joshCam1Config/license/ios/20986-316-98dbba5e3c21614641960fd652004345.lic\"
}, \"sdkType\": \"JOSH_CAM1\", \"followersTabName\": \"Top Fans\",
\"handshakeDefaultInterval\": 86400000, \"maxApiDelay\": 2000,
\"maxErrorEventPerInterval\": 10, \"upload_duration_v2\": 60,
\"min_upload_duration\": 5, \"max_recent_navigable_action_count\": 30,
\"timerPeriodInSeconds\": 60, \"firstTimePullDelay\": 60,
\"enable_whatsapp_share\": true, \"enable_video_download_on_share\":
true, \"hit_firebase_event_once\": true, \"enableGzip_v2\": true,
\"allowEmptyTitleInCreatePost\": false, \"is_firebase_event_enabled\":
true, \"dev_error_for_2xxTo4xx_enabled\": false,
\"location_prompt_for_max_time_count\": 3,
\"location_prompt_after_max_post_count\": 0, \"video_resources\": {
\"1\": \"https://gateway.myjosh.in/api/v1/materialinfo/1?version=1\",
\"2\": \"https://gateway.myjosh.in/api/v1/materialinfo/2?version=410\",
\"3\": \"https://gateway.myjosh.in/api/v1/materialinfo/3?version=1\",
\"4\": \"https://gateway.myjosh.in/api/v1/materialinfo/4?version=1\",
\"5\": \"https://gateway.myjosh.in/api/v1/materialinfo/5?version=1\",
\"6\": \"https://gateway.myjosh.in/api/v1/materialinfo/6?version=1\",
\"7\": \"https://gateway.myjosh.in/api/v1/materialinfo/7?version=1\",
\"8\": \"https://gateway.myjosh.in/api/v1/materialinfo/8?version=1\",
\"9\": \"https://gateway.myjosh.in/api/v1/materialinfo/9?version=1\",
\"10\": \"https://gateway.myjosh.in/api/v1/materialinfo/10?version=1\",
\"11\": \"https://gateway.myjosh.in/api/v1/materialinfo/11?version=1\",
\"12\": \"https://gateway.myjosh.in/api/v1/materialinfo/12?version=1\",
\"13\": \"https://gateway.myjosh.in/api/v1/materialinfo/13?version=1\",
\"14\":
\"https://gateway.myjosh.in/api/v1/materialinfo/14?version=114\",
\"15\": \"https://gateway.myjosh.in/api/v1/materialinfo/15?version=1\",
\"16\": \"https://gateway.myjosh.in/api/v1/materialinfo/16?version=1\",
\"17\": \"https://gateway.myjosh.in/api/v1/materialinfo/17?version=1\",
\"24\": \"https://gateway.myjosh.in/api/v1/materialinfo/24?version=1\",
\"25\": \"https://gateway.myjosh.in/api/v1/materialinfo/25?version=6\",
\"26\":
\"https://gateway.myjosh.in/api/v1/materialinfo/26?version=113\",
\"27\": \"https://gateway.myjosh.in/api/v1/materialinfo/27?version=1\",
\"28\": \"https://gateway.myjosh.in/api/v1/materialinfo/28?version=1\",
\"29\": \"https://gateway.myjosh.in/api/v1/materialinfo/29?version=1\",
\"30\": \"https://gateway.myjosh.in/api/v1/materialinfo/30?version=7\",
\"31\": \"https://gateway.myjosh.in/api/v1/materialinfo/31?version=10\",
\"32\": \"https://gateway.myjosh.in/api/v1/materialinfo/32?version=1\",
\"33\": \"https://gateway.myjosh.in/api/v1/materialinfo/33?version=1\",
\"34\": \"https://gateway.myjosh.in/api/v1/materialinfo/34?version=17\",
\"35\": \"https://gateway.myjosh.in/api/v1/materialinfo/35?version=2\",
\"36\": \"https://gateway.myjosh.in/api/v1/materialinfo/36?version=1\",
\"37\": \"https://gateway.myjosh.in/api/v1/materialinfo/37?version=2\"
}, \"following_sync_interval_in_seconds\": 86400,
\"appsOnDeviceEnabled\": false, \"appsOnDeviceEnabledV2\": true,
\"cleanupConfig\": { \"maxMusicDownloads\": 20, \"maxStickerDownloads\":
100, \"maxCommentStickerDownloads\": 100, \"maEffectsDownloads\": 50 },
\"network_config\": { \"exo_weightage_double\": 0.8,
\"network_weightage_double\": 2, \"sliding_percentile_percentile\": 0.5,
\"bitrate_expression\": { \"id\": \"1\", \"formula\":
\"(e\*0.8)+(n\*2)\" }, \"bitrate_expression_exception\": { \"id\":
\"2\", \"formula\": \"(e\*0.8)+(n\*0.7)\" }, \"bitrate_expression_v2\":
{ \"id\": \"3\", \"formula\": \"function f42(e,n){ \\n if(e\<n) return
e\*0.8+n\*0.7; \\n else { var wa=e\*e/(e+n)+n\*n/(e+n); return
Math.min(wa,e);};\\n};\" }, \"lifetime_bitrate_capture_window_sec\":
604800, \"coldstart_transition_threshold_sec\": 10,
\"coldstart_network_provider_mapping\": \[ { \"network\": \"4G\",
\"provider\": \"Jio 4G\", \"quality\": \"good\" }, { \"network\":
\"4G\", \"provider\": \"airtel\", \"quality\": \"good\" }, {
\"network\": \"4G\", \"provider\": \"Vi India\", \"quality\": \"good\"
}, { \"network\": \"4G\", \"provider\": \"IND airtel\", \"quality\":
\"good\" }, { \"network\": \"4G\", \"provider\": \"Vodafone IN\",
\"quality\": \"good\" }, { \"network\": \"4G\", \"provider\":
\"Airtel\", \"quality\": \"good\" }, { \"network\": \"4G\",
\"provider\": \"Idea\", \"quality\": \"good\" }, { \"network\": \"4G\",
\"provider\": \"JIO 4G\", \"quality\": \"good\" }, { \"network\": \"w\",
\"provider\": \"Jio 4G\", \"quality\": \"fast\" }, { \"network\": \"w\",
\"provider\": \"airtel\", \"quality\": \"fast\" }, { \"network\":
\"4G\", \"provider\": \"JIO\", \"quality\": \"good\" }, { \"network\":
\"4G\", \"provider\": \"AIRTEL\", \"quality\": \"good\" }, {
\"network\": \"3G\", \"provider\": \"Vi India\", \"quality\": \"avg\",
\"maxQuality\": \"good\" }, { \"network\": \"w\", \"provider\": \"Vi
India\", \"quality\": \"fast\" }, { \"network\": \"4G\", \"provider\":
\"VIL\", \"quality\": \"good\" }, { \"network\": \"4G\", \"provider\":
\"Vodafone\", \"quality\": \"good\" }, { \"network\": \"w\",
\"provider\": \"Vodafone IN\", \"quality\": \"fast\" }, { \"network\":
\"w\", \"provider\": \"IND airtel\", \"quality\": \"fast\" }, {
\"network\": \"2G\", \"provider\": \"airtel\", \"quality\": \"slow\",
\"maxQuality\": \"avg\" }, { \"network\": \"4G\", \"provider\": \"Airtel
\| airtel\", \"quality\": \"good\" }, { \"network\": \"4G\",
\"provider\": \"IND AirTel\", \"quality\": \"good\" }, { \"network\":
\"3G\", \"provider\": \"Vodafone IN\", \"quality\": \"avg\",
\"maxQuality\": \"good\" }, { \"network\": \"w\", \"provider\":
\"Idea\", \"quality\": \"fast\" }, { \"network\": \"4G\", \"provider\":
\"JIO 4G \| Jio 4G\", \"quality\": \"good\" }, { \"network\": \"4G\",
\"provider\": \"AirTel\", \"quality\": \"good\" }, { \"network\":
\"3G\", \"provider\": \"Idea\", \"quality\": \"avg\", \"maxQuality\":
\"good\" }, { \"network\": \"4G\", \"provider\": \"Vi India \| Vodafone
IN\", \"quality\": \"good\" }, { \"network\": \"2G\", \"provider\": \"Vi
India\", \"quality\": \"slow\", \"maxQuality\": \"avg\" }, {
\"network\": \"w\", \"provider\": \"Airtel\", \"quality\": \"fast\" }, {
\"network\": \"3G\", \"provider\": \"BSNL MOBILE\", \"quality\":
\"avg\", \"maxQuality\": \"good\" }, { \"network\": \"4G\",
\"provider\": \"BSNL MOBILE\", \"quality\": \"good\" }, { \"network\":
\"4G\", \"provider\": \"Vi India \| Idea\", \"quality\": \"good\" }, {
\"network\": \"3G\", \"provider\": \"BSNL Mobile\", \"quality\":
\"avg\", \"maxQuality\": \"good\" }, { \"network\": \"4G\",
\"provider\": \"BSNL Mobile\", \"quality\": \"good\" }, { \"network\":
\"4G\", \"provider\": \"IDEA\", \"quality\": \"good\" }, { \"network\":
\"w\", \"provider\": \"JIO 4G\", \"quality\": \"fast\" }, { \"network\":
\"w\", \"provider\": \"BSNL MOBILE\", \"quality\": \"fast\" }, {
\"network\": \"4G\", \"provider\": \"Jio\", \"quality\": \"good\" }, {
\"network\": \"4G\", \"provider\": \"Airtel_BH\", \"quality\": \"good\"
}, { \"network\": \"w\", \"provider\": \"BSNL Mobile\", \"quality\":
\"fast\" }, { \"network\": \"2G\", \"provider\": \"Idea\", \"quality\":
\"slow\", \"maxQuality\": \"avg\" }, { \"network\": \"2G\",
\"provider\": \"Vodafone IN\", \"quality\": \"slow\", \"maxQuality\":
\"avg\" }, { \"network\": \"4G\", \"provider\": \"!dea\", \"quality\":
\"good\" }, { \"network\": \"3G\", \"provider\": \"CellOne\",
\"quality\": \"avg\", \"maxQuality\": \"good\" }, { \"network\": \"4G\",
\"provider\": \"JIO4G\", \"quality\": \"good\" }, { \"network\": \"4G\",
\"provider\": \"Airtel Stay Home\", \"quality\": \"good\" }, {
\"network\": \"2G\", \"provider\": \"Airtel\", \"quality\": \"slow\",
\"maxQuality\": \"avg\" }, { \"network\": \"w\", \"provider\": \"JIO\",
\"quality\": \"fast\" }, { \"network\": \"2G\", \"provider\": \"IND
airtel\", \"quality\": \"slow\", \"maxQuality\": \"avg\" }, {
\"network\": \"0\", \"provider\": \"Jio 4G\", \"quality\": \"fast\" }, {
\"network\": \"3G\", \"provider\": \"airtel\", \"quality\": \"avg\",
\"maxQuality\": \"good\" }, { \"network\": \"WiFi\", \"provider\":
\"AirTel\", \"quality\": \"fast\" }, { \"network\": \"4G\",
\"provider\": \"unknown\", \"quality\": \"good\" }, { \"network\":
\"WiFi\", \"provider\": \"unknown\", \"quality\": \"fast\" }, {
\"network\": \"WiFi\", \"provider\": \"Jio\", \"quality\": \"fast\" }, {
\"network\": \"4G\", \"provider\": \"CellOne\", \"quality\": \"good\" },
{ \"network\": \"3G\", \"provider\": \"!dea\", \"quality\": \"avg\",
\"maxQuality\": \"good\" }, { \"network\": \"w\", \"provider\": \"VIL\",
\"quality\": \"fast\" }, { \"network\": \"4G\", \"provider\":
\"Ind-Jio\", \"quality\": \"good\" }, { \"network\": \"w\",
\"provider\": \"Vi India \| Vodafone IN\", \"quality\": \"fast\" }, {
\"network\": \"3G\", \"provider\": \"VIL\", \"quality\": \"avg\",
\"maxQuality\": \"good\" }, { \"network\": \"4G\", \"provider\":
\"Emergency calls only\", \"quality\": \"good\" }, { \"network\":
\"2G\", \"provider\": \"Jio 4G\", \"quality\": \"slow\", \"maxQuality\":
\"avg\" }, { \"network\": \"3G\", \"provider\": \"Vodafone\",
\"quality\": \"avg\", \"maxQuality\": \"good\" }, { \"network\": \"3G\",
\"provider\": \"Jio 4G\", \"quality\": \"avg\", \"maxQuality\": \"good\"
}, { \"network\": \"w\", \"provider\": \"AIRTEL\", \"quality\": \"fast\"
}, { \"network\": \"4G\", \"provider\": \"No service\", \"quality\":
\"good\" }, { \"network\": \"w\", \"provider\": \"Vi India \| Idea\",
\"quality\": \"fast\" }, { \"network\": \"0\", \"provider\": \"airtel\",
\"quality\": \"fast\" }, { \"network\": \"w\", \"provider\":
\"Vodafone\", \"quality\": \"fast\" }, { \"network\": \"4G\",
\"provider\": \"Any\", \"quality\": \"good\" }, { \"network\": \"3G\",
\"provider\": \"Any\", \"quality\": \"avg\", \"maxQuality\": \"good\" },
{ \"network\": \"2G\", \"provider\": \"Any\", \"quality\": \"slow\",
\"maxQuality\": \"avg\" }, { \"network\": \"Any\", \"provider\":
\"Any\", \"quality\": \"good\" } \],
\"exo_sliding_percentile_max_weight\": 1000 }, \"speed_quality_map_v2\":
{ \"200\": \"slow\", \"2000\": \"average\", \"4000\": \"good\",
\"8000\": \"fast\", \"16000\": \"veryfast\" }, \"cameraProperties\": {
\"videoCaptureResolution\": \"EXTREMELY_HIGH\", \"recordBitrate\":
\"3000000\", \"fps\": \"30\", \"audioSampleRate\": \"44100\",
\"autoFocus\": \"Y\", \"autoExposure\": \"Y\", \"sharpness\": \"Y\",
\"beautify\": \"Y\", \"Intensity\": \"0.2\", \"videoStabilization\":
\"Y\", \"continuousFocus\": \"Y\", \"zoom\": \"Y\", \"maxZoom\": \"99\",
\"bitDepth\": \"8\", \"compileBitrate\": \"3000000\", \"audioBitrate\":
\"160000\", \"losslessAudio\": \"true\", \"encoderPreset\": \"MEDIUM\",
\"encoderCRF\": \"17\", \"encoderName\": \"H.265\", \"encoderProfile\":
\"high\", \"HDR\": \"none\" }, \"cameraPropertiesiOS\": {
\"videoCaptureResolution\": \"SUPER_HIGH\", \"recordBitrate\":
\"3000000\", \"fps\": \"30\", \"audioSampleRate\": \"44100\",
\"autoFocus\": \"Y\", \"autoExposure\": \"Y\", \"sharpness\": \"Y\",
\"beautify\": \"Y\", \"Intensity\": \"0.2\", \"videoStabilization\":
\"Y\", \"continuousFocus\": \"Y\", \"zoom\": \"Y\", \"maxZoom\": \"99\",
\"bitDepth\": \"8\", \"compileBitrate\": \"3000000\", \"audioBitrate\":
\"160000\", \"losslessAudio\": \"true\", \"encoderPreset\": \"MEDIUM\",
\"encoderCRF\": \"17\", \"encoderName\": \"H.265\", \"encoderProfile\":
\"high\", \"HDR\": \"none\" }, \"max_consumed_cache_items_count\": 30,
\"attRules\": { \"enableATTPrompt\": true, \"attPromptConfig\": {
\"minInstallLaunchCount\": 2, \"minUpgradeLaunchCount\": 3,
\"coolOffLaunchCount\": 2, \"maxAttemptCount\": 30, \"title\":
\"Personalized Ads\", \"message\": \"Josh would like permission to serve
personalized ads to you\" } }, \"quicHints\": \[ { \"host\":
\"stream-g.myjosh.in\", \"port\": 443, \"alternatePort\": 443 } \],
\"bookmarkConfig\": { \"musicTrimNudgeCount\": 5,
\"bookMarkNudgeCount\": 5, \"bookmarkSyncMinimumGap\": 86400000 },
\"reactivate_account_config\": { \"temporarily_deactivated_title\": \"We
missed you\...\", \"temporarily_deactivated_sub_title\": \"Tap the
button below to reactivate\\nyour account\",
\"temporarily_deactivated_cta_text\": \"Reactivate Account\",
\"permanently_deactivated_title\": \"This account has been permanently
deleted\", \"permanently_deactivated_sub_title\": \"To use Josh, create
a new account.\", \"permanently_deactivated_cta_text\": \"Create New
Account\" }, \"csConfig\": { \"enabled\": true, \"frequencyTimeMS\":
86400000, \"bucketSizeNew\": 2000 }, \"profile_wizard_config\": {
\"completeMsgDismissTimeInMills\": 3000,
\"setUpProfileMsgShowTimeInDays\": 360 }, \"fileUploads\": {
\"twitter\":
\"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/Twitter-Logo.webp\",
\"instagram\":
\"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/Instagram-Logo.webp\",
\"facebook\":
\"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/Facebook-Logo.webp\",
\"whatsapp\":
\"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/Whatsapp-Logo.webp\",
\"uploads\": \"VmlkZW8=.png\", \"trending\": \"VHJlbmRpbmdfMQ==.png\",
\"likes\": \"TGlrZV8x.png\", \"drafts\": \"ZHJhZnRz.png\", \"tagged\":
\"TWVudGlvbl8x.png\", \"audio_icon\":
\"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/bXVzaWM=.png\",
\"discovery_icon\":
\"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/ZGlzY292ZXJ5.png\",
\"trending_icon\": \"TmV3X1RyZW5kaW5nX0ljb25fMQ==.png\", \"photos\":
\"UGhvdG9fTmV3XzE=.png\", \"tipping_icon_url\": \"Z2lmdF9pY29u.png\",
\"gifting_icon_url\": \"Z2lmdF9pY29u.png\", \"uploads_selected\":
\"dXBsb2Fkc19zZWxlY3RlZA==.png\", \"trending_selected\":
\"dHJlbmRpbmdfc2VsZWN0ZWQ=.png\", \"tagged_selected\":
\"dGFnZ2VkX3NlbGVjdGVk.png\", \"social_selected\":
\"c29jaWFsX3NlbGVjdGVk.png\", \"photos_selected\":
\"cGhvdG9zX3NlbGVjdGVk.png\", \"likes_selected\":
\"bGlrZXNfc2VsZWN0ZWQ=.png\", \"drafts_selected\":
\"ZHJhZnRzX3NlbGVjdGVk.png\", \"social\": \"c29jaWFs.png\" } } }\'

- **Success Response:**

{ \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
\"10.10.34.160\", \"code\": 200 }, \"data\": true }

**4. File Upload**

Uploading the file icon in static config

- **Request Method and URL:**

POST:
https://qa-gateway.coolfie.io/api/v1/cms/fileUpload/JOSH_STATIC_CONFIG?key=trending_icon

- **Curl Request:**

curl \--location \--request POST
\'https://qa-gateway.coolfie.io/api/v1/cms/fileUpload/JOSH_STATIC_CONFIG?key=trending_icon\'\
\--header \'Content-Type: application/json\'\
\--form
\'multipartFile=@\"/home/varikutitheja/Desktop/10.d1/trending_icon.png\"\'

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.10.34.160\", \"code\": 200 }, \"data\": true }

**5. Delete File Upload**

Delete the uploaded file

- **Request Method and URL:**

  POST:
  https://qa-gateway.coolfie.io/api/v1/cms/fileUpload/SSO/deleteKey?key=guddi

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/cms/fileUpload/SSO/deleteKey?key=guddi\'
  \\

  \--header \'Content-Type: application/json\' \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.10.34.160\", \"code\": 200 }, \"data\": true }

**6. Update cache**

updating the cache of version entity

- **Request Method and URL:**

- **Curl Request:**

- **Success Response:**

- **Request Method and URL:**\
  GET :
  https://qa-gateway.coolfie.io/api/v1/internal/cache?keys=josh/v2/camera/effect/tabs/assetType/map&region=CAMERA_EFFECT_TABS

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/internal/cache?keys=josh/v2/camera/effect/tabs/assetType/map&region=CAMERA_EFFECT_TABS\'\
  \--header \'Content-Type: application/json\'

- **Success Response:**

  json{ \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { \"distributedMemory\":
  {}, \"inMemory\": {} } }

- **Request Method and URL:**

  GET :
  https://qa-gateway.coolfie.io/api/v1/internal/cache/regions/CAMERA_EFFECT_TABS/keys

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/internal/cache/regions/CAMERA_EFFECT_TABS/keys\'\
  \--header \'Content-Type: application/json\'

- **Success Response:**

  json{ \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.14.11.40\", \"code\": 200 }, \"data\": \[\] }

- **Request Method and URL:**

  GET :
  https://qa-gateway.coolfie.io/api/v1/internal/cache/regions/VERSION_CMS_INFO/stats

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/internal/cache/regions/VERSION_CMS_INFO/stats\'\
  \--header \'Content-Type: application/json\'\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { \"name\":
  \"VERSION_CMS_INFO\", \"hitCount\": 3633, \"missCount\": 260,
  \"evictionCount\": 0, \"totalItems\": 13, \"isSentinelAware\": false,
  \"hitPercent\": 93 } }

- **Request Method and URL:**

  GET :
  https://qa-gateway.coolfie.io/api/v1/internal/cache/regions/VERSION_CMS_INFO/stats

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/internal/cache/regions/VERSION_CMS_INFO/stats\'\
  \--header \'Content-Type: application/json\'

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { \"name\":
  \"VERSION_CMS_INFO\", \"hitCount\": 3633, \"missCount\": 260,
  \"evictionCount\": 0, \"totalItems\": 13, \"isSentinelAware\": false,
  \"hitPercent\": 93 } }

- **Request Method and URL:**

  POST : https://qa-gateway.coolfie.io/api/v1/internal/cache/delete/keys

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/internal/cache/delete/keys\'\
  \--header \'Content-Type: application/json\'\
  \--data-raw \'{\
  \"cacheRegionKeysMap\": {\
  \"VERSION_CMS_INFO\":
  \[\"josh/v2/version/cms/JOSH_STATIC_CONFIG/null\"\]\
  }\
  }\'

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.14.11.40\", \"code\": 200 }, \"data\": {
  \"josh/v2/version/cms/JOSH_STATIC_CONFIG/null\": true } }

- **Request Method and URL:**

  GET :
  https://qa-gateway.coolfie.io/api/v1/audio/tabs?version=322&langCode=te,en

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/audio/tabs?version=322&langCode=te,en\'\
  \--header \'Content-Type: application/json\'

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.14.11.40\", \"code\": 200 }, \"data\": { \"tabs\": \[ {
  \"audioTabId\": 2253, \"displayName\": \"Trending\", \"tabType\":
  \"REMOTE\", \"contentUrl\":
  \"https://stage-feed.myjosh.in/audio/list?categoryId=Trending&lang=te,en\",
  \"tabId\": 0, \"langCode\": \"en\", \"status\": \"Active\",
  \"categoryKey\": \"Trending\", \"updatedDate\": 1619691273976 } \],
  \"version\": \"322\" } }

- **Request Method and URL:**

  GET : https://qa-gateway.coolfie.io/api/v1/upgrade/dns?version=34

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/upgrade/dns?version=34\' \\

  \--header \'Content-Type: application/json\' \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { \"dnsLookupTimeout\":
  \"5000\", \"disableDNSCaching\": \"false\",
  \"scheduleHeartbeatInterval\": \"900000\", \"firstLevelCacheTTL\":
  \"86400000\", \"dnsEntries\": \[ { \"hostname\":
  \"qa-gateway.myjosh.in\", \"ip\": \[ \"180.179.92.138\" \],
  \"heartbeatUrl\": \"https://qa-gateway.myjosh.in/api/v1/health\" }, {
  \"hostname\": \"qa-api.myjosh.in\", \"ip\": \[ \"180.179.92.137\" \],
  \"heartbeatUrl\": \"http://qa-api.myjosh.in/admin/healthcheck\" }, {
  \"hostname\": \"qa-feed.myjosh.in\", \"ip\": \[ \"180.179.92.136\" \],
  \"heartbeatUrl\": \"https://qa-feed.myjosh.in/health\" }, {
  \"hostname\": \"josh-notif-inbox-qa.myjosh.in\", \"ip\": \[
  \"180.179.92.135\" \], \"heartbeatUrl\":
  \"http://josh-notif-inbox-qa.myjosh.in/api/obelix/oor\" }, {
  \"hostname\": \"qa-stream.myjosh.in\", \"ip\": \[ \"180.179.92.134\"
  \], \"heartbeatUrl\": \"https://qa-stream.myjosh.in/healthcheck\" }, {
  \"hostname\": \"qa-share.myjosh.in\", \"ip\": \[ \"180.179.92.133\"
  \], \"heartbeatUrl\": \"https://qa-share.myjosh.in/hc.html\" } \],
  \"version\": \"34\", \"secondLevelCacheTTL\": \"86400000\" } }

- **Request Method and URL:**

  GET :
  https://qa-gateway.coolfie.io/api/v1/upgrade/discovery/search?version=1258

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/upgrade/discovery/search?version=1258\'
  \\

  \--header \'Content-Type: application/json\' \\

- **Success Response:**

- **Request Method and URL:**

  GET :
  https://qa-gateway.coolfie.io/api/v1/upgrade/version/info/HASHTAG_ONBOARD/9?langCode=en

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/upgrade/version/info/HASHTAG_ONBOARD/9?langCode=en\'\
  \--header \'Content-Type: application/json\'

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { \"version\": \"12\",
  \"hashtag\": \[ { \"displayName\": \"हिंदी\", \"translation\": \"हिंदी
  (Hindi)\", \"categories\": \[ { \"text\": \"QA_जोश\", \"tags\": \[ {
  \"text\": \"QA_जोश\", \"translation\": \"QA_Josh\", \"isChallenge\":
  true } \], \"translation\": \"QA_Josh\" }, { \"text\": \"पन्द्रह अगस्त\",
  \"tags\": \[ { \"text\": \"पन्द्रह अगस्त\", \"translation\": \"15th
  August\", \"isChallenge\": true } \], \"translation\": \"15th August\"
  }, { \"text\": \"QA_जोश1\", \"tags\": \[ { \"text\": \"QA_जोश1\",
  \"translation\": \"QA_Josh1\", \"isChallenge\": true } \],
  \"translation\": \"QA_Josh1\" }, { \"text\": \"स्वतंत्रतादिवस\",
  \"tags\": \[ { \"text\": \"स्वतंत्रतादिवस\", \"translation\":
  \"Independenceday\", \"isChallenge\": false } \], \"translation\":
  \"Independenceday\" }, { \"category_id\": 21, \"text\": \"वायरल\",
  \"tags\": \[ { \"tag_id\": 21, \"text\": \"वायरल\", \"translation\":
  \"Viral\", \"isChallenge\": false } \], \"translation\": \"Viral\" },
  { \"text\": \"फनी\", \"tags\": \[ { \"text\": \"फनी\",
  \"translation\": \"Funny\", \"isChallenge\": true } \],
  \"translation\": \"Funny\" }, { \"category_id\": 23, \"text\":
  \"ग्लैमर\", \"tags\": \[ { \"tag_id\": 23, \"text\": \"ग्लैमर\",
  \"translation\": \"Glamour\", \"isChallenge\": false } \],
  \"translation\": \"Glamour\" }, { \"category_id\": 24, \"text\":
  \"म्यूजिक\", \"tags\": \[ { \"tag_id\": 24, \"text\": \"म्यूजिक\",
  \"translation\": \"Music\", \"isChallenge\": false } \],
  \"translation\": \"Music\" }, { \"category_id\": 25, \"text\":
  \"क्यूट\", \"tags\": \[ { \"tag_id\": 25, \"text\": \"क्यूट\",
  \"translation\": \"Cute\", \"isChallenge\": true } \],
  \"translation\": \"Cute\" }, { \"category_id\": 26, \"text\": \"फेल\",
  \"tags\": \[ { \"tag_id\": 26, \"text\": \"फेल\", \"translation\":
  \"Fail\", \"isChallenge\": false } \], \"translation\": \"Fail\" }, {
  \"category_id\": 27, \"text\": \"लाइफ\", \"tags\": \[ { \"tag_id\":
  27, \"text\": \"लाइफ\", \"translation\": \"Life\", \"isChallenge\":
  true } \], \"translation\": \"Life\" }, { \"category_id\": 28,
  \"text\": \"डांस\", \"tags\": \[ { \"tag_id\": 28, \"text\": \"डांस\",
  \"translation\": \"Dance\", \"isChallenge\": true } \],
  \"translation\": \"Dance\" }, { \"category_id\": 29, \"text\":
  \"स्टेटस\", \"tags\": \[ { \"tag_id\": 29, \"text\": \"स्टेटस\",
  \"translation\": \"Status\", \"isChallenge\": false } \],
  \"translation\": \"Status\" }, { \"category_id\": 30, \"text\":
  \"भक्ति\", \"tags\": \[ { \"tag_id\": 30, \"text\": \"भक्ति\",
  \"translation\": \"Devotional\", \"isChallenge\": false } \],
  \"translation\": \"Devotional\" } \], \"splashImageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/splash_icons/665fb35acd24938738c854ec06ac5f79_baseq_orig.webp\",
  \"key\": 1, \"iconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/language_icons/0529786d8390658ab29eb4b8babbfecd_baseq_orig.webp\",
  \"code\": \"hi\", \"position\": 1, \"primaryColor\": \"#FF619C\" }, {
  \"displayName\": \"தமிழ்\", \"translation\": \"தமிழ் (Tamil)\",
  \"categories\": \[ { \"text\": \"சுதந்திரதினம்\", \"tags\": \[ {
  \"text\": \"சுதந்திரதினம்\", \"translation\": \"Independenceday\" } \],
  \"translation\": \"Independenceday\" }, { \"category_id\": 48,
  \"text\": \"வாழ்க்கை\", \"tags\": \[ { \"tag_id\": 48, \"text\":
  \"வாழ்க்கை\", \"translation\": \"Life\", \"isChallenge\": true } \],
  \"translation\": \"Life\" }, { \"category_id\": 49, \"text\":
  \"பக்தி\", \"tags\": \[ { \"tag_id\": 49, \"text\": \"பக்தி\",
  \"translation\": \"Devotional\", \"isChallenge\": false } \],
  \"translation\": \"Devotional\" }, { \"category_id\": 50, \"text\":
  \"ஸ்டேட்டஸ்\", \"tags\": \[ { \"tag_id\": 50, \"text\": \"ஸ்டேட்டஸ்\",
  \"translation\": \"Status\", \"isChallenge\": false } \],
  \"translation\": \"Status\" }, { \"category_id\": 41, \"text\":
  \"வைரல்\", \"tags\": \[ { \"tag_id\": 41, \"text\": \"வைரல்\",
  \"translation\": \"Viral\", \"isChallenge\": false } \],
  \"translation\": \"Viral\" }, { \"category_id\": 42, \"text\":
  \"வேடிக்கை\", \"tags\": \[ { \"tag_id\": 42, \"text\": \"வேடிக்கை\",
  \"translation\": \"Funny\", \"isChallenge\": true } \],
  \"translation\": \"Funny\" }, { \"category_id\": 43, \"text\":
  \"கிளாமர்\", \"tags\": \[ { \"tag_id\": 43, \"text\": \"கிளாமர்\",
  \"translation\": \"Glamour\", \"isChallenge\": false } \],
  \"translation\": \"Glamour\" }, { \"category_id\": 44, \"text\":
  \"மியூசிக்\", \"tags\": \[ { \"tag_id\": 44, \"text\": \"மியூசிக்\",
  \"translation\": \"Music\", \"isChallenge\": false } \],
  \"translation\": \"Music\" }, { \"category_id\": 45, \"text\":
  \"டான்ஸ்\", \"tags\": \[ { \"tag_id\": 45, \"text\": \"டான்ஸ்\",
  \"translation\": \"Dance\", \"isChallenge\": true } \],
  \"translation\": \"Dance\" }, { \"category_id\": 46, \"text\":
  \"அழகு\", \"tags\": \[ { \"tag_id\": 46, \"text\": \"அழகு\",
  \"translation\": \"Cute\", \"isChallenge\": true } \],
  \"translation\": \"Cute\" }, { \"category_id\": 47, \"text\":
  \"தோல்வி\", \"tags\": \[ { \"tag_id\": 47, \"text\": \"தோல்வி\",
  \"translation\": \"Fail\", \"isChallenge\": false } \],
  \"translation\": \"Fail\" } \], \"splashImageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/splash_icons/5c494514452afaf11cc5a64fd1686b1f_baseq_orig.webp\",
  \"key\": 4, \"iconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/language_icons/0d7e8e4dda9f5075648282813b61f478_baseq_orig.webp\",
  \"code\": \"ta\", \"position\": 4, \"primaryColor\": \"#569FFF\" }, {
  \"displayName\": \"తెలుగు\", \"translation\": \"తెలుగు (Telugu)\",
  \"categories\": \[ { \"text\": \"స్వాతంత్య్ర దినోత్సవం\", \"tags\": \[ {
  \"text\": \"స్వాతంత్య్ర దినోత్సవం\", \"translation\": \"Independenceday\" }
  \], \"translation\": \"Independenceday\" }, { \"category_id\": 32,
  \"text\": \"ఫన్నీ\", \"tags\": \[ { \"tag_id\": 32, \"text\": \"ఫన్నీ\",
  \"translation\": \"Funny\", \"isChallenge\": true } \],
  \"translation\": \"Funny\" }, { \"category_id\": 33, \"text\":
  \"గ్ల్యామర్\", \"tags\": \[ { \"tag_id\": 33, \"text\": \"గ్ల్యామర్\",
  \"translation\": \"Glamour\", \"isChallenge\": false } \],
  \"translation\": \"Glamour\" }, { \"category_id\": 34, \"text\":
  \"మ్యూజిక్\", \"tags\": \[ { \"tag_id\": 34, \"text\": \"మ్యూజిక్\",
  \"translation\": \"Music\", \"isChallenge\": false } \],
  \"translation\": \"Music\" }, { \"category_id\": 35, \"text\":
  \"డాన్స్\", \"tags\": \[ { \"tag_id\": 35, \"text\": \"డాన్స్\",
  \"translation\": \"Dance\", \"isChallenge\": true } \],
  \"translation\": \"Dance\" }, { \"category_id\": 36, \"text\":
  \"క్యూట్\", \"tags\": \[ { \"tag_id\": 36, \"text\": \"క్యూట్\",
  \"translation\": \"Cute\", \"isChallenge\": true } \],
  \"translation\": \"Cute\" }, { \"category_id\": 37, \"text\":
  \"విఫలం\", \"tags\": \[ { \"tag_id\": 37, \"text\": \"విఫలం\",
  \"translation\": \"Fail\", \"isChallenge\": false } \],
  \"translation\": \"Fail\" }, { \"category_id\": 38, \"text\": \"లైఫ్\",
  \"tags\": \[ { \"tag_id\": 38, \"text\": \"లైఫ్\", \"translation\":
  \"Life\", \"isChallenge\": true } \], \"translation\": \"Life\" }, {
  \"category_id\": 39, \"text\": \"భక్తి\", \"tags\": \[ { \"tag_id\": 39,
  \"text\": \"భక్తి\", \"translation\": \"Devotional\", \"isChallenge\":
  false } \], \"translation\": \"Devotional\" }, { \"category_id\": 40,
  \"text\": \"స్టేటస్\", \"tags\": \[ { \"tag_id\": 40, \"text\": \"స్టేటస్\",
  \"translation\": \"Status\", \"isChallenge\": false } \],
  \"translation\": \"Status\" }, { \"category_id\": 31, \"text\":
  \"వైరల్\", \"tags\": \[ { \"tag_id\": 31, \"text\": \"వైరల్\",
  \"translation\": \"Viral\", \"isChallenge\": false } \],
  \"translation\": \"Viral\" } \], \"splashImageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/splash_icons/756180df5f6ea69a50a613beba672040_baseq_orig.webp\",
  \"key\": 2, \"iconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/language_icons/2525506d472def7c572b2a781a9e3ad7_baseq_orig.webp\",
  \"code\": \"te\", \"position\": 2, \"primaryColor\": \"#FFBC50\" }, {
  \"displayName\": \"മലയാളം\", \"translation\": \"മലയാളം (Malayalam)\",
  \"categories\": \[ { \"text\": \"സ്വാതന്ത്ര്യദിനം\", \"tags\": \[ {
  \"text\": \"സ്വാതന്ത്ര്യദിനം\", \"translation\": \"Independenceday\" } \],
  \"translation\": \"Independenceday\" }, { \"category_id\": 51,
  \"text\": \"വൈറല്‍\", \"tags\": \[ { \"tag_id\": 51, \"text\": \"വൈറല്‍\",
  \"translation\": \"Viral\", \"isChallenge\": false } \],
  \"translation\": \"Viral\" }, { \"category_id\": 52, \"text\":
  \"തമാശകള്‍\", \"tags\": \[ { \"tag_id\": 52, \"text\": \"തമാശകള്‍\",
  \"translation\": \"Funny\", \"isChallenge\": true } \],
  \"translation\": \"Funny\" }, { \"category_id\": 53, \"text\":
  \"ഗ്ലാമര്‍\", \"tags\": \[ { \"tag_id\": 53, \"text\": \"ഗ്ലാമര്‍\",
  \"translation\": \"Glamour\", \"isChallenge\": false } \],
  \"translation\": \"Glamour\" }, { \"category_id\": 54, \"text\":
  \"ഗാനങ്ങള്‍\", \"tags\": \[ { \"tag_id\": 54, \"text\": \"ഗാനങ്ങള്‍\",
  \"translation\": \"Music\", \"isChallenge\": false } \],
  \"translation\": \"Music\" }, { \"category_id\": 55, \"text\":
  \"ഡാന്‍സ്\", \"tags\": \[ { \"tag_id\": 55, \"text\": \"ഡാന്‍സ്\",
  \"translation\": \"Dance\", \"isChallenge\": true } \],
  \"translation\": \"Dance\" }, { \"category_id\": 56, \"text\":
  \"ക്യൂട്ട്\", \"tags\": \[ { \"tag_id\": 56, \"text\": \"ക്യൂട്ട്\",
  \"translation\": \"Cute\", \"isChallenge\": true } \],
  \"translation\": \"Cute\" }, { \"category_id\": 57, \"text\":
  \"ഫെയില്‍\", \"tags\": \[ { \"tag_id\": 57, \"text\": \"ഫെയില്‍\",
  \"translation\": \"Fail\", \"isChallenge\": false } \],
  \"translation\": \"Fail\" }, { \"category_id\": 58, \"text\": \"ലൈഫ്\",
  \"tags\": \[ { \"tag_id\": 58, \"text\": \"ലൈഫ്\", \"translation\":
  \"Life\", \"isChallenge\": true } \], \"translation\": \"Life\" }, {
  \"category_id\": 59, \"text\": \"ഭക്തി\", \"tags\": \[ { \"tag_id\":
  59, \"text\": \"ഭക്തി\", \"translation\": \"Devotional\",
  \"isChallenge\": false } \], \"translation\": \"Devotional\" }, {
  \"category_id\": 60, \"text\": \"സ്റ്റാറ്റസ്\", \"tags\": \[ { \"tag_id\":
  60, \"text\": \"സ്റ്റാറ്റസ്\", \"translation\": \"Status\",
  \"isChallenge\": false } \], \"translation\": \"Status\" } \],
  \"splashImageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/splash_icons/811e612695d9236243251a0046d9e79e_baseq_orig.webp\",
  \"key\": 3, \"iconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/language_icons/daca04a6697cf07688602a39f02dbd52_baseq_orig.webp\",
  \"code\": \"ml\", \"position\": 3, \"primaryColor\": \"#20CBC8\" }, {
  \"displayName\": \"English\", \"translation\": \"English\",
  \"categories\": \[ { \"text\": \"motivationchallenge\", \"tags\": \[ {
  \"text\": \"motivationchallenge\", \"translation\":
  \"motivationchallenge\" } \], \"translation\": \"motivationchallenge\"
  }, { \"text\": \"dancechallenge\", \"tags\": \[ { \"text\":
  \"dancechallenge\", \"translation\": \"dancechallenge\" } \],
  \"translation\": \"dancechallenge\" }, { \"text\": \"artchallenge\",
  \"tags\": \[ { \"text\": \"artchallenge\", \"translation\":
  \"artchallenge\" } \], \"translation\": \"artchallenge\" }, {
  \"text\": \"photochallennge\", \"tags\": \[ { \"text\":
  \"photochallennge\", \"translation\": \"photochallennge\" } \],
  \"translation\": \"photochallennge\" }, { \"text\":
  \"wearamaskchallenge\", \"tags\": \[ { \"text\":
  \"wearamaskchallenge\", \"translation\": \"wearamaskchallenge\" } \],
  \"translation\": \"wearamaskchallenge\" }, { \"text\":
  \"bottleflipchallenge\", \"tags\": \[ { \"text\":
  \"bottleflipchallenge\", \"translation\": \"bottleflipchallenge\" }
  \], \"translation\": \"bottleflipchallenge\" }, { \"text\":
  \"babypicchallenge\", \"tags\": \[ { \"text\": \"babypicchallenge\",
  \"translation\": \"babypicchallenge\" } \], \"translation\":
  \"babypicchallenge\" }, { \"text\": \"myfavrajnisong\", \"tags\": \[ {
  \"text\": \"myfavrajnisong\", \"translation\": \"myfavrajnisong\" }
  \], \"translation\": \"myfavrajnisong\" }, { \"text\":
  \"iheartshahrukh\", \"tags\": \[ { \"text\": \"iheartshahrukh\",
  \"translation\": \"iheartshahrukh\" } \], \"translation\":
  \"iheartshahrukh\" }, { \"text\": \"QA_Josh\", \"tags\": \[ {
  \"text\": \"QA_Josh\", \"translation\": \"QA_Josh\", \"isChallenge\":
  true } \], \"translation\": \"QA_Josh\" }, { \"text\": \"15th
  August\", \"tags\": \[ { \"text\": \"15th August\", \"translation\":
  \"15th August\", \"isChallenge\": true } \], \"translation\": \"15th
  August\" }, { \"text\": \"QA_Josh1\", \"tags\": \[ { \"text\":
  \"QA_Josh1\", \"translation\": \"QA_Josh1\", \"isChallenge\": true }
  \], \"translation\": \"QA_Josh1\" }, { \"category_id\": 19, \"text\":
  \"Status\", \"tags\": \[ { \"tag_id\": 19, \"text\": \"Status\",
  \"translation\": \"Status\", \"isChallenge\": false } \],
  \"translation\": \"Status\" }, { \"category_id\": 1, \"text\":
  \"Viral\", \"tags\": \[ { \"tag_id\": 1, \"text\": \"Viral\",
  \"translation\": \"Viral\", \"isChallenge\": false } \],
  \"translation\": \"Viral\" }, { \"category_id\": 2, \"text\":
  \"Funny\", \"tags\": \[ { \"tag_id\": 2, \"text\": \"Funny\",
  \"translation\": \"Funny\", \"isChallenge\": true } \],
  \"translation\": \"Funny\" }, { \"category_id\": 3, \"text\":
  \"Glamour\", \"tags\": \[ { \"tag_id\": 3, \"text\": \"Glamour\",
  \"translation\": \"Glamour\", \"isChallenge\": false } \],
  \"translation\": \"Glamour\" }, { \"category_id\": 4, \"text\":
  \"Music\", \"tags\": \[ { \"tag_id\": 4, \"text\": \"Music\",
  \"translation\": \"Music\", \"isChallenge\": false } \],
  \"translation\": \"Music\" }, { \"category_id\": 6, \"text\":
  \"Cute\", \"tags\": \[ { \"tag_id\": 6, \"text\": \"Cute\",
  \"translation\": \"Cute\", \"isChallenge\": true } \],
  \"translation\": \"Cute\" }, { \"category_id\": 7, \"text\": \"Fail\",
  \"tags\": \[ { \"tag_id\": 7, \"text\": \"Fail\", \"translation\":
  \"Fail\", \"isChallenge\": false } \], \"translation\": \"Fail\" }, {
  \"category_id\": 8, \"text\": \"Life\", \"tags\": \[ { \"tag_id\": 8,
  \"text\": \"Life\", \"translation\": \"Life\", \"isChallenge\": true }
  \], \"translation\": \"Life\" }, { \"category_id\": 20, \"text\":
  \"Devotional\", \"tags\": \[ { \"tag_id\": 20, \"text\":
  \"Devotional\", \"translation\": \"Devotional\", \"isChallenge\":
  false } \], \"translation\": \"Devotional\" }, { \"category_id\": 10,
  \"text\": \"Dance\", \"tags\": \[ { \"tag_id\": 10, \"text\":
  \"Dance\", \"translation\": \"Dance\", \"isChallenge\": true } \],
  \"translation\": \"Dance\" } \], \"splashImageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/splash_icons/bd073a1e468fff1a70665316030ce925_baseq_orig.webp\",
  \"key\": 6, \"iconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/language_icons/e559695905668fb472e6a3fea0855007_baseq_orig.webp\",
  \"code\": \"en\", \"position\": 6, \"primaryColor\": \"#967BDC\" }, {
  \"displayName\": \"ಕನ್ನಡ\", \"translation\": \"ಕನ್ನಡ (Kannada)\",
  \"categories\": \[ { \"text\": \"ಸ್ವಾತಂತ್ರ್ಯದಿನೋತ್ಸವ\", \"tags\": \[ {
  \"text\": \"ಸ್ವಾತಂತ್ರ್ಯದಿನೋತ್ಸವ\", \"translation\": \"Independenceday\" }
  \], \"translation\": \"Independenceday\" }, { \"category_id\": 80,
  \"text\": \"ಭಕ್ತಿ\", \"tags\": \[ { \"tag_id\": 80, \"text\": \"ಭಕ್ತಿ\",
  \"translation\": \"Devotional\", \"isChallenge\": false } \],
  \"translation\": \"Devotional\" }, { \"category_id\": 71, \"text\":
  \"ವೈರಲ್\", \"tags\": \[ { \"tag_id\": 71, \"text\": \"ವೈರಲ್\",
  \"translation\": \"Viral\", \"isChallenge\": false } \],
  \"translation\": \"Viral\" }, { \"category_id\": 72, \"text\":
  \"ಫನ್ನಿ\", \"tags\": \[ { \"tag_id\": 72, \"text\": \"ಫನ್ನಿ\",
  \"translation\": \"Funny\", \"isChallenge\": true } \],
  \"translation\": \"Funny\" }, { \"category_id\": 73, \"text\":
  \"ಗ್ಲಾಮರ್\", \"tags\": \[ { \"tag_id\": 73, \"text\": \"ಗ್ಲಾಮರ್\",
  \"translation\": \"Glamour\", \"isChallenge\": false } \],
  \"translation\": \"Glamour\" }, { \"category_id\": 74, \"text\":
  \"ಮ್ಯೂಸಿಕ್\", \"tags\": \[ { \"tag_id\": 74, \"text\": \"ಮ್ಯೂಸಿಕ್\",
  \"translation\": \"Music\", \"isChallenge\": false } \],
  \"translation\": \"Music\" }, { \"category_id\": 75, \"text\":
  \"ಕ್ಯೂಟ್\", \"tags\": \[ { \"tag_id\": 75, \"text\": \"ಕ್ಯೂಟ್\",
  \"translation\": \"Cute\", \"isChallenge\": true } \],
  \"translation\": \"Cute\" }, { \"category_id\": 76, \"text\": \"ಫೇಲ್\",
  \"tags\": \[ { \"tag_id\": 76, \"text\": \"ಫೇಲ್\", \"translation\":
  \"Fail\", \"isChallenge\": false } \], \"translation\": \"Fail\" }, {
  \"category_id\": 77, \"text\": \"ಜೀವನ\", \"tags\": \[ { \"tag_id\":
  77, \"text\": \"ಜೀವನ\", \"translation\": \"Life\", \"isChallenge\":
  true } \], \"translation\": \"Life\" }, { \"category_id\": 78,
  \"text\": \"ಡಾನ್ಸ್\", \"tags\": \[ { \"tag_id\": 78, \"text\": \"ಡಾನ್ಸ್\",
  \"translation\": \"Dance\", \"isChallenge\": true } \],
  \"translation\": \"Dance\" }, { \"category_id\": 79, \"text\":
  \"ಸ್ಟೇಟಸ್\", \"tags\": \[ { \"tag_id\": 79, \"text\": \"ಸ್ಟೇಟಸ್\",
  \"translation\": \"Status\", \"isChallenge\": false } \],
  \"translation\": \"Status\" } \], \"splashImageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/splash_icons/bd073a1e468fff1a70665316030ce925_baseq_orig.webp\",
  \"key\": 5, \"iconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/language_icons/bd8d487bf516104169ac59e831cf7079_baseq_orig.webp\",
  \"code\": \"kn\", \"position\": 5, \"primaryColor\": \"#967BDC\" }, {
  \"displayName\": \"All\", \"translation\": \"All\", \"categories\": \[
  { \"text\": \"Independenceday\", \"tags\": \[ { \"text\":
  \"Independenceday\", \"translation\": \"Independenceday\" } \],
  \"translation\": \"Independenceday\" }, { \"category_id\": 64,
  \"text\": \"Music\", \"tags\": \[ { \"tag_id\": 64, \"text\":
  \"Music\", \"translation\": \"Music\", \"isChallenge\": false } \],
  \"translation\": \"Music\" }, { \"category_id\": 65, \"text\":
  \"Cute\", \"tags\": \[ { \"tag_id\": 65, \"text\": \"Cute\",
  \"translation\": \"Cute\", \"isChallenge\": true } \],
  \"translation\": \"Cute\" }, { \"category_id\": 66, \"text\":
  \"Fail\", \"tags\": \[ { \"tag_id\": 66, \"text\": \"Fail\",
  \"translation\": \"Fail\", \"isChallenge\": false } \],
  \"translation\": \"Fail\" }, { \"category_id\": 67, \"text\":
  \"Life\", \"tags\": \[ { \"tag_id\": 67, \"text\": \"Life\",
  \"translation\": \"Life\", \"isChallenge\": true } \],
  \"translation\": \"Life\" }, { \"category_id\": 68, \"text\":
  \"Dance\", \"tags\": \[ { \"tag_id\": 68, \"text\": \"Dance\",
  \"translation\": \"Dance\", \"isChallenge\": true } \],
  \"translation\": \"Dance\" }, { \"category_id\": 69, \"text\":
  \"Status\", \"tags\": \[ { \"tag_id\": 69, \"text\": \"Status\",
  \"translation\": \"Status\", \"isChallenge\": false } \],
  \"translation\": \"Status\" }, { \"category_id\": 70, \"text\":
  \"Devotional\", \"tags\": \[ { \"tag_id\": 70, \"text\":
  \"Devotional\", \"translation\": \"Devotional\", \"isChallenge\":
  false } \], \"translation\": \"Devotional\" }, { \"category_id\": 61,
  \"text\": \"Viral\", \"tags\": \[ { \"tag_id\": 61, \"text\":
  \"Viral\", \"translation\": \"Viral\", \"isChallenge\": false } \],
  \"translation\": \"Viral\" }, { \"category_id\": 62, \"text\":
  \"Funny\", \"tags\": \[ { \"tag_id\": 62, \"text\": \"Funny\",
  \"translation\": \"Funny\", \"isChallenge\": true } \],
  \"translation\": \"Funny\" }, { \"category_id\": 63, \"text\":
  \"Glamour\", \"tags\": \[ { \"tag_id\": 63, \"text\": \"Glamour\",
  \"translation\": \"Glamour\", \"isChallenge\": false } \],
  \"translation\": \"Glamour\" } \], \"splashImageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/splash_icons/d1797b43340587ac4d4d2b2f97023ac4_baseq_orig.webp\",
  \"key\": 11, \"iconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/language_icons/67bf593ece0e9c65784192f41f7317f4_baseq_orig.webp\",
  \"code\": \"All\", \"position\": 11, \"primaryColor\": \"#F23E08\" },
  { \"displayName\": \"मराठी\", \"translation\": \"मराठी (Marathi)\",
  \"categories\": \[ { \"text\": \"व्हायरल\", \"tags\": \[ { \"text\":
  \"व्हायरल\", \"translation\": \"Viral\" } \], \"translation\":
  \"Viral\" }, { \"text\": \"ट्रेंडिंग \", \"tags\": \[ { \"text\": \"ट्रेंडिंग
  \", \"translation\": \"Trending\" } \], \"translation\": \"Trending\"
  }, { \"text\": \"ग्लॅमर\", \"tags\": \[ { \"text\": \"ग्लॅमर\",
  \"translation\": \"Glamour\" } \], \"translation\": \"Glamour\" }, {
  \"text\": \"भक्ती\", \"tags\": \[ { \"text\": \"भक्ती\",
  \"translation\": \"Devotional\" } \], \"translation\": \"Devotional\"
  }, { \"text\": \"क्युट \", \"tags\": \[ { \"text\": \"क्युट \",
  \"translation\": \"Cute\" } \], \"translation\": \"Cute\" }, {
  \"text\": \"स्थिती\", \"tags\": \[ { \"text\": \"स्थिती\",
  \"translation\": \"Status\" } \], \"translation\": \"Status\" }, {
  \"text\": \"मजेदार\", \"tags\": \[ { \"text\": \"मजेदार\",
  \"translation\": \"Funny\" } \], \"translation\": \"Funny\" }, {
  \"text\": \"विनोद\", \"tags\": \[ { \"text\": \"विनोद\",
  \"translation\": \"Comedy\" } \], \"translation\": \"Comedy\" }, {
  \"text\": \"नृत्य\", \"tags\": \[ { \"text\": \"नृत्य\", \"translation\":
  \"Dance\" } \], \"translation\": \"Dance\" }, { \"text\": \"जीवन\",
  \"tags\": \[ { \"text\": \"जीवन\", \"translation\": \"Life\" } \],
  \"translation\": \"Life\" } \], \"key\": 7, \"iconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/language_icons/Marathi.webp\",
  \"code\": \"mr\", \"position\": 7, \"primaryColor\": \"#9E521E\" }, {
  \"displayName\": \"ગુજરાતી\", \"translation\": \"ગુજરાતી (Gujarati)\",
  \"categories\": \[ { \"text\": \"વાયરલ\", \"tags\": \[ { \"text\":
  \"વાયરલ\", \"translation\": \"Viral\" } \], \"translation\": \"Viral\"
  }, { \"text\": \"ટ્રેન્ડિંગ\", \"tags\": \[ { \"text\": \"ટ્રેન્ડિંગ\",
  \"translation\": \"Trending\" } \], \"translation\": \"Trending\" }, {
  \"text\": \"ગ્લેમર\", \"tags\": \[ { \"text\": \"ગ્લેમર\",
  \"translation\": \"Glamour\" } \], \"translation\": \"Glamour\" }, {
  \"text\": \"ભક્તિ\", \"tags\": \[ { \"text\": \"ભક્તિ\",
  \"translation\": \"Devotional\" } \], \"translation\": \"Devotional\"
  }, { \"text\": \"ક્યૂટ\", \"tags\": \[ { \"text\": \"ક્યૂટ\",
  \"translation\": \"Cute\" } \], \"translation\": \"Cute\" }, {
  \"text\": \"સ્ટેટસ\", \"tags\": \[ { \"text\": \"સ્ટેટસ\",
  \"translation\": \"Status\" } \], \"translation\": \"Status\" }, {
  \"text\": \"રમૂજી\", \"tags\": \[ { \"text\": \"રમૂજી\",
  \"translation\": \"Funny\" } \], \"translation\": \"Funny\" }, {
  \"text\": \"કૉમેડી\", \"tags\": \[ { \"text\": \"કૉમેડી\",
  \"translation\": \"Comedy\" } \], \"translation\": \"Comedy\" }, {
  \"text\": \"ડાન્સ\", \"tags\": \[ { \"text\": \"ડાન્સ\",
  \"translation\": \"Dance\" } \], \"translation\": \"Dance\" }, {
  \"text\": \"જીવન\", \"tags\": \[ { \"text\": \"જીવન\",
  \"translation\": \"Life\" } \], \"translation\": \"Life\" } \],
  \"key\": 8, \"iconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/language_icons/gujarati.webp\",
  \"code\": \"gu\", \"position\": 8, \"primaryColor\": \"#4B7D00\" }, {
  \"displayName\": \"বাংলা\", \"translation\": \"বাংলা (Bengali)\",
  \"categories\": \[ { \"text\": \"ভাইরাল\", \"tags\": \[ { \"text\":
  \"ভাইরাল\", \"translation\": \"Viral\" } \], \"translation\":
  \"Viral\" }, { \"text\": \"চলমান\", \"tags\": \[ { \"text\":
  \"চলমান\", \"translation\": \"Trending\" } \], \"translation\":
  \"Trending\" }, { \"text\": \"গ্ল্যামার \", \"tags\": \[ { \"text\":
  \"গ্ল্যামার \", \"translation\": \"Glamour\" } \], \"translation\":
  \"Glamour\" }, { \"text\": \"ভক্তিমুলক\", \"tags\": \[ { \"text\":
  \"ভক্তিমুলক\", \"translation\": \"Devotional\" } \], \"translation\":
  \"Devotional\" }, { \"text\": \"কিউট\", \"tags\": \[ { \"text\":
  \"কিউট\", \"translation\": \"Cute\" } \], \"translation\": \"Cute\" },
  { \"text\": \"স্টেটাস \", \"tags\": \[ { \"text\": \"স্টেটাস \",
  \"translation\": \"Status\" } \], \"translation\": \"Status\" }, {
  \"text\": \"হাস্যকর\", \"tags\": \[ { \"text\": \"হাস্যকর\",
  \"translation\": \"Funny\" } \], \"translation\": \"Funny\" }, {
  \"text\": \"কমেডি\", \"tags\": \[ { \"text\": \"কমেডি\",
  \"translation\": \"Comedy\" } \], \"translation\": \"Comedy\" }, {
  \"text\": \"নাচ\", \"tags\": \[ { \"text\": \"নাচ\", \"translation\":
  \"Dance\" } \], \"translation\": \"Dance\" }, { \"text\": \"জীবন\",
  \"tags\": \[ { \"text\": \"জীবন\", \"translation\": \"Life\" } \],
  \"translation\": \"Life\" } \], \"key\": 9, \"iconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/language_icons/Bengali.webp\",
  \"code\": \"bn\", \"position\": 9, \"primaryColor\": \"#D65428\" }, {
  \"displayName\": \"ଓଡିଆ\", \"translation\": \"ଓଡିଆ (Odia)\",
  \"categories\": \[ { \"text\": \"ଭାଇରାଲ୍ \|\", \"tags\": \[ { \"text\":
  \"ଭାଇରାଲ୍ \|\", \"translation\": \"Viral\" } \], \"translation\":
  \"Viral\" }, { \"text\": \"ଟ୍ରେଣ୍ଡିଙ୍ଗ \", \"tags\": \[ { \"text\":
  \"ଟ୍ରେଣ୍ଡିଙ୍ଗ \", \"translation\": \"Trending\" } \], \"translation\":
  \"Trending\" }, { \"text\": \"ଗ୍ଲାମର\", \"tags\": \[ { \"text\":
  \"ଗ୍ଲାମର\", \"translation\": \"Glamour\" } \], \"translation\":
  \"Glamour\" }, { \"text\": \"ଭକ୍ତି\", \"tags\": \[ { \"text\": \"ଭକ୍ତି\",
  \"translation\": \"Devotional\" } \], \"translation\": \"Devotional\"
  }, { \"text\": \"ସୁନ୍ଦର\", \"tags\": \[ { \"text\": \"ସୁନ୍ଦର\",
  \"translation\": \"Cute\" } \], \"translation\": \"Cute\" }, {
  \"text\": \"ସ୍ଥିତି\", \"tags\": \[ { \"text\": \"ସ୍ଥିତି\", \"translation\":
  \"Status\" } \], \"translation\": \"Status\" }, { \"text\": \"ମଜାଳିଆ\",
  \"tags\": \[ { \"text\": \"ମଜାଳିଆ\", \"translation\": \"Funny\" } \],
  \"translation\": \"Funny\" }, { \"text\": \"କମେଡି\", \"tags\": \[ {
  \"text\": \"କମେଡି\", \"translation\": \"Comedy\" } \], \"translation\":
  \"Comedy\" }, { \"text\": \"ନୃତ୍ୟ\", \"tags\": \[ { \"text\": \"ନୃତ୍ୟ\",
  \"translation\": \"Dance\" } \], \"translation\": \"Dance\" }, {
  \"text\": \"ଜୀବନ\", \"tags\": \[ { \"text\": \"ଜୀବନ\",
  \"translation\": \"Life\" } \], \"translation\": \"Life\" } \],
  \"key\": 10, \"iconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/language_icons/oriya.webp\",
  \"code\": \"or\", \"position\": 10, \"primaryColor\": \"#5865F2\" }, {
  \"displayName\": \"ਪੰਜਾਬੀ\", \"translation\": \"ਪੰਜਾਬੀ (Punjabi)\",
  \"categories\": \[ { \"text\": \"ਵਾਇਰਲ\", \"tags\": \[ { \"text\":
  \"ਵਾਇਰਲ\", \"translation\": \"Viral\" } \], \"translation\": \"Viral\"
  }, { \"text\": \" ਟਰੇਂਡਿੰਗ\", \"tags\": \[ { \"text\": \" ਟਰੇਂਡਿੰਗ\",
  \"translation\": \"Trending\" } \], \"translation\": \"Trending\" }, {
  \"text\": \"ਗਲੈਮਰ \", \"tags\": \[ { \"text\": \"ਗਲੈਮਰ \",
  \"translation\": \"Glamour\" } \], \"translation\": \"Glamour\" }, {
  \"text\": \"ਭਗਤੀ \", \"tags\": \[ { \"text\": \"ਭਗਤੀ \",
  \"translation\": \"Devotional\" } \], \"translation\": \"Devotional\"
  }, { \"text\": \"ਪਿਆਰਾ \", \"tags\": \[ { \"text\": \"ਪਿਆਰਾ \",
  \"translation\": \"Cute\" } \], \"translation\": \"Cute\" }, {
  \"text\": \"ਸਥਿਤੀ \", \"tags\": \[ { \"text\": \"ਸਥਿਤੀ \",
  \"translation\": \"Status\" } \], \"translation\": \"Status\" }, {
  \"text\": \"ਮਜ਼ਾਕੀਆ \", \"tags\": \[ { \"text\": \"ਮਜ਼ਾਕੀਆ \",
  \"translation\": \"Funny\" } \], \"translation\": \"Funny\" }, {
  \"text\": \"ਕਮੇਡੀ \", \"tags\": \[ { \"text\": \"ਕਮੇਡੀ \",
  \"translation\": \"Comedy\" } \], \"translation\": \"Comedy\" }, {
  \"text\": \"ਡਾਂਸ \", \"tags\": \[ { \"text\": \"ਡਾਂਸ \",
  \"translation\": \"Dance\" } \], \"translation\": \"Dance\" }, {
  \"text\": \"ਜਿੰਦਗੀ\", \"tags\": \[ { \"text\": \"ਜਿੰਦਗੀ\",
  \"translation\": \"Life\" } \], \"translation\": \"Life\" } \],
  \"key\": 10, \"iconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/language_icons/Punjabi.webp\",
  \"code\": \"pa\", \"position\": 10, \"primaryColor\": \"#f46b45\" } \]
  } }

- **Request Method and URL:**

  GET :
  https://qa-gateway.coolfie.io/api/v1/upgrade/version/info/JOSH_STATIC_CONFIG/6

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/upgrade/version/info/JOSH_STATIC_CONFIG/6\'\
  \--header \'Content-Type: application/json\'

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { \"version\": 1447,
  \"data\": { \"supportedMimetypes\": \[ \"video/mp4\",
  \"video/quicktime\", \"video/x-ms-wmv\", \"video/mov\", \"video/mpg\"
  \], \"reaction_sync_interval_in_seconds\": 86400,
  \"vote_interval_in_seconds\": 86400, \"maxCommentCharLimit\": 50,
  \"max_recent_cache_action_count\": 30, \"splashTime\": 3000,
  \"showDataSaverMode\": true, \"enable_youtube_connect\": true,
  \"enable_instagram_connect\": true, \"splash_ad_request_launch\": 2,
  \"softRelaunchDelay\": 5000, \"hardRelaunchDelay\": 10000,
  \"repeated_launch_api_request_delay\": 60000,
  \"show_share_nudge_loop_count\": 2, \"max_share_nudge_show_count\": 3,
  \"max_lifetime_show_share_nudge_count\": 10, \"max_edit_nudge_count\":
  3, \"grid_item_count\": 3, \"animated_icon_duration_in_ms\": 500,
  \"create_post_max_char\": 120, \"precache_interest_icons\": true,
  \"video_edit_resolution\": 720,
  \"max_sticker_comment_nudge_show_count\": 1,
  \"is_apply_for_verification_enabled\": true,
  \"create_video_nudge_dismissal\": 3000, \"vote_nudge_dismissal\":
  3000, \"share_voted_video_nudge_dismissal\": 3000,
  \"effectsExpiryMaxDays\": 30, \"enable_lite_sync_once\": false,
  \"disable_experiment_api\": false, \"items_toshow_in_inbox\": 7,
  \"max_tpv_profile_suggestions\": 5,
  \"experiment_incorrect_otp_max_attempts\": 2,
  \"experiment_resend_otp_max_attempts\": 2,
  \"max_event_videos_to_download\": 2, \"max_event_videos_to_show\": 2,
  \"max_selected_videos_gallery\": 15, \"reduced_percent_volume_dub\":
  20, \"enableAutoSaveVideos\": true, \"loginScreenSubTitle\": \"Find
  friends & family, like & comment,\\npersonalise your interests & watch
  the\\nbest videos!\", \"loginScreenTitle\": \"Login to Josh\",
  \"threshold_prefetch_stream_percentage\": 1,
  \"num_of_item_check_for_prefetch\": 1, \"device_wake_up_flag\": true,
  \"hide_block_user_option\": false, \"allow_masthead_ad\": true,
  \"refresh_wait_time_ms\": 1500, \"allow_splash_ad\": true,
  \"image_share_url\": \"/image/\",
  \"images_auto_scroll_duration_in_ms\": 5000, \"send_tip_page_url\":
  \"https://qa-share.myjosh.in/webview/pay-tips?tip_to={0}&tip_by={1}&tip_to_image_url={2}&tip_to_user_name={3}&tip_by_user_name={4}\",
  \"tip_transactions_page_url\":
  \"https://qa-share.myjosh.in/webview/tip-transactions?user_id={0}\",
  \"cs_ttl_duration_in_minutes\": 30, \"wait_on_cs_page_in_seconds\": 3,
  \"contact_sync_message_config\": { \"zero_state_message\": \"Contact
  sync successful, no friends were found but you can always invite them
  later.\", \"after_follow_message\": \"You\'ve followed %d people from
  your contact book\", \"sync_in_bg\": \"Enjoy videos while we sync your
  contacts.\", \"with_contacts_state\": \"Contacts synced successfully.
  Tap to find your friends.\", \"action_text\": \"Find Friends\" },
  \"profile_rejected_show_count\": 2, \"max_photo_upload_limit\": 10,
  \"bottom_bar_tab_sequence\": \[ \"HOME\", \"EXPLORE\", \"LIVE\",
  \"SHOP\", \"NOTIFICATIONINBOX\", \"PROFILE\" \],
  \"like_comment_tab_list\": \[ \"LIKE\", \"COMMENT\", \"GIFT\" \],
  \"camera_tab_sequence\": \[ \"DUETS\", \"CAMERA\", \"PHOTOS\",
  \"TEMPLATES\", \"MEMES\" \], \"disable_custom_tab_social_auth\":
  false, \"is_seekbar_enabled\": true, \"is_tabbar_swiping_enabled\":
  true, \"educational_nudge_count_per_session\": 3,
  \"educational_nudge_duration_in_ms\": 3000, \"mute_ab_test_variant\":
  \"PERSISTENT_MUTE\", \"zone_info_dialog_data\": { \"title\":
  \"\<h1\>Content on this page is community managed.\</h1\>\",
  \"message\": \"\<p\>Josh does not make any warranties about the
  completeness, reliability and accuracy of this information. \<a
  href=\'https://www.google.com\'\>Read TnC\</a\>\</p\>\", \"ctaText\":
  \"\<strong\>Okay\</strong\>\" }, \"image_card_config\": {
  \"min_time_threshold_in_ms\": 5000, \"max_count_per_session\": 3,
  \"animation_list\": \[ 0, 1, 2, 5, 6, 8 \] },
  \"recent_search_item_count\": 25, \"search_default_popular_feed_url\":
  \"https://qa-feed.myjosh.in/search/?q=viral\", \"buy_jems_page_url\":
  \"https://qa-share.myjosh.in/webview/pay-tips-v1?tip_to={0}&tip_by={1}&tip_to_image_url={2}&tip_to_user_name={3}&tip_by_user_name={4}&package_id={5}&package_collection_id={6}\",
  \"jems_wallet_page_url\":
  \"https://qa-share.myjosh.in/webview/jems-wallet?user_uuid={0}&client_id={1}\",
  \"zero_page\": { \"zone\": { \"1\": { \"title\": \"No Followers\" },
  \"2\": { \"title\": \"No Suggestions\" } }, \"user_tpv\": { \"1\": {
  \"title\": \"No Mutual Followers\" }, \"2\": { \"title\": \"No Fans\"
  }, \"3\": { \"title\": \"No Followers\" }, \"4\": { \"title\": \"No
  Pages\" }, \"5\": { \"title\": \"No Suggestions\" } }, \"user_fpv\": {
  \"2\": { \"title\": \"No Fans\", \"description\": \"Try posting more
  content and invite your friends\" }, \"3\": { \"title\": \"Not
  Following Anyone\", \"description\": \"Explore discover section and
  follow creators and other users\", \"cta_text\": \"Discovery\",
  \"cta_deeplink\":
  \"http://qa-share.myjosh.in/page/discovery/main-discovery-page\" },
  \"4\": { \"title\": \"Not Following Any Pages\", \"description\":
  \"Explore discover section and follow pages\", \"cta_text\":
  \"Discovery\", \"cta_deeplink\":
  \"http://qa-share.myjosh.in/page/discovery/main-discovery-page\" },
  \"5\": { \"title\": \"No Suggestion\" } }, \"like_comment_tpv\": {
  \"LIKE\": { \"title\": \"No Likes\" }, \"COMMENT\": { \"title\": \"No
  Comments\" }, \"GIFT\": { \"title\": \"No Gift Received\",
  \"description\": \"Explore gift section and be the first one to send
  gift\", \"cta_text\": \"Send Gifts\" } }, \"like_comment_fpv\": {
  \"LIKE\": { \"title\": \"No Likes\" }, \"COMMENT\": { \"title\": \"No
  Comments\" }, \"GIFT\": { \"title\": \"No Gift Received\",
  \"description\": \"Explore gift section and be the first one to send
  gift\" } } }, \"discovery_tab_list\": \[ { \"id\":
  \"main-discovery-page\", \"name\": \"Discovery\", \"tab_icon_url\":
  \"discovery_icon\", \"url\":
  \"https://qa-feed.myjosh.in/page/discovery/main-discovery-page\",
  \"type\": \"DISCOVERY\" }, { \"id\": \"main-audio-page\", \"name\":
  \"Music\", \"tab_icon_url\": \"audio_icon\", \"url\":
  \"https://qa-feed.myjosh.in/page/audio/main-audio-page\", \"type\":
  \"AUDIO\" } \], \"bookmark_webview_url\":
  \"https://qa-share.myjosh.in/webview/bookmarks\", \"game_center_url\":
  \"https://qa-feed.myjosh.in/page_collection/game/main-game-page\",
  \"global_leaderboard_url\":
  \"https://qa-api.myjosh.in/apij/leaderboard/global\",
  \"extended_radius_msg\": \"No videos available for the selected
  location. Showing videos from nearby areas\",
  \"syncRewardIntervalTime\": 30, \"bloomFilterSyncIntervalTime\": 3,
  \"bloomFilterMaxFiles\": 2, \"bloomFilterRenewalSize\": 100,
  \"is_user_rewards_enabled\": true,
  \"wokenUpServiceForegroundNotificationDuration\": 5000,
  \"api_sequencing_config\": { \"api_sequencing_max_delay_ms\": 180000,
  \"api_hit_interval_time_ms\": 4000, \"fl_api_hit_interval_time_ms\":
  2000, \"delay_max_video_count\": 10,
  \"delay_cache_api_max_video_count\": 2, \"delay_after_handshake\":
  3000 }, \"notification_filters\": { \"available_filters\": \[ {
  \"label\": \"All\", \"isDefault\": \"true\", \"params\": { \"filter\":
  \"\" } }, { \"label\": \"Social\", \"params\": { \"filter\":
  \"SOCIAL\" } }, { \"label\": \"Content\", \"params\": { \"filter\":
  \"CONTENT\" } } \], \"notification_filters_heading\": \"Filter
  notifications by\" }, \"wakeUpPartnerInformation\": {
  \"minimumBatteryRequired\": 15, \"partnerPackages\": \[ {
  \"packageName\": \"com.eterno\", \"action\":
  \"com.eterno.intent.woken_up_service_start\",
  \"foregroundServiceSupport\": true, \"wakeupsections\": \[
  \"Notification\", \"Deeplink\", \"Splash\", \"App Controller\" \],
  \"dndStartTime\": 82800, \"dndEndTime\": 21300, \"wakeDelay\":
  86400000, \"disabledManufacturer\": \[\] }, { \"packageName\":
  \"com.newsdistill.mobile\", \"action\":
  \"com.newsdistill.mobile.intent.ACTION_WAKEUP\",
  \"foregroundServiceSupport\": true, \"wakeupsections\": \[
  \"Notification\", \"Deeplink\", \"Splash\", \"App Controller\" \],
  \"dndStartTime\": 82800, \"dndEndTime\": 21300, \"wakeDelay\":
  86400000, \"disabledManufacturer\": \[\] } \] },
  \"deviceWakeUpConfiguration\": { \"minimumBatteryRequired\": 15,
  \"dndStartTime\": 82800, \"dndEndTime\": 21300, \"wakeDelay\":
  86400000 }, \"appsflyer_events\": { \"C2\": 180, \"C3\": 180, \"C4\":
  180, \"C5\": 180, \"C6\": 180, \"C7\": 180, \"C8\": 180, \"C9\": 180,
  \"C10\": 180, \"C11\": 180, \"C12\": 540, \"C13\": 540, \"C14\": 540,
  \"C15\": 540, \"C16\": 1000, \"C17\": 1, \"C18\": 1, \"C19\": 180,
  \"C20\": 180, \"C22\": 540, \"C23\": 540, \"C24\": 540, \"C25\": 540,
  \"C26\": 540, \"C27\": 180, \"C28\": 180, \"C29\": 180, \"C30\": 180,
  \"C31\": 180, \"C32\": 180, \"C33\": 180, \"C34\": 180, \"C35\": 180,
  \"C36\": 180, \"C37\": 180, \"C38\": 180, \"C39\": 180, \"C40\": 180,
  \"C41\": 180, \"C42\": 180, \"C43\": 180, \"C44\": 180, \"C45\": 180,
  \"C46\": 180, \"C47\": 180, \"C48\": 180, \"C49\": 180, \"C50\": 180
  }, \"wa_status_sent_config\": \[ { \"min_version\": 30,
  \"max_version\": 2147483647, \"enable\": true, \"path_wa_status\":
  \"/Android/media/com.whatsapp/WhatsApp/Media/.Statuses\",
  \"path_wa_sent_video\":
  \"/Android/media/com.whatsapp/WhatsApp/Media/WhatsApp Video/Sent\",
  \"path_wa_sent_image\":
  \"/Android/media/com.whatsapp/WhatsApp/Media/WhatsApp Images/Sent\" },
  { \"min_version\": 0, \"max_version\": 29, \"enable\": true,
  \"path_wa_status\": \"WhatsApp/Media/.Statuses\",
  \"path_wa_sent_video\": \"WhatsApp/Media/WhatsApp Video/Sent\",
  \"path_wa_sent_image\": \"WhatsApp/Media/WhatsApp Images/Sent\" } \],
  \"myelin_config\": { \"enable\": true, \"disable_for_verified\": \[
  \"k\", \"m\", \"l\" \], \"sync_time\": 86400000, \"quality\": {
  \"fast\": \"average\", \"good\": \"average\", \"average\": \"average\"
  } }, \"pullNotificationConfig\": { \"pull_notifications_enabled\":
  true, \"firstTimePullDelay\": 120 }, \"lp_gotosetting_dialog_config\":
  { \"lp_gotosetting_dialog_title\": \"Allow Josh to access this
  device's location?\", \"lp_gotosetting_dialog_desc\": \"This will help
  you reach a more relevant audience &amp; gain followers, Please go to
  settings and allow location permission\",
  \"lp_gotosetting_dialog_pos_action\": \"Go To Settings\",
  \"lp_gotosetting_dialog_neg_action\": \"Later\",
  \"lp_gotosetting_dialog_show_after_x_post\": 4 },
  \"compilation_rules\": { \"default\": 720, \"resolutions\": \[ {
  \"max\": 2147483647, \"min\": 2048, \"result\": 2048 }, { \"max\":
  2047, \"min\": 1024, \"result\": 1024 }, { \"max\": 1023, \"min\":
  641, \"result\": 720 }, { \"max\": 640, \"min\": 481, \"result\": 640
  }, { \"max\": 480, \"min\": 361, \"result\": 480 }, { \"max\": 360,
  \"min\": 1, \"result\": 360 } \] }, \"data_saver_cache_config\": {
  \"cache_offline_directory_max_size_in_mb\": 100,
  \"cache_prefetch_directory_max_size_in_mb\": 200,
  \"cache_directory_max_size_in_mb\": 100, \"clear_session_data\":
  false, \"recommended_profile\": \"average\",
  \"enable_notification_prefetch\": true,
  \"min_cache_item_to_fetch_api\": 5, \"session_start_config\": {
  \"slow\": { \"from_offline_back_to_back\": 5 }, \"average\": {
  \"from_offline_back_to_back\": 3 }, \"good\": {
  \"from_offline_back_to_back\": 2 }, \"fast\": {
  \"from_offline_back_to_back\": 2 }, \"veryfast\": {
  \"from_offline_back_to_back\": 2 } }, \"prefetch_download_config\": {
  \"disable_cache\": false, \"prefetch_download_count_config\": {
  \"slow\": { \"no_of_videos\": 3, \"min_cache_percentage_ofl_to_onl\":
  100 }, \"average\": { \"no_of_videos\": 3,
  \"min_cache_percentage_ofl_to_onl\": 80 }, \"good\": {
  \"no_of_videos\": 3, \"min_cache_percentage_ofl_to_onl\": 60 },
  \"fast\": { \"no_of_videos\": 3, \"min_cache_percentage_ofl_to_onl\":
  40 }, \"veryfast\": { \"no_of_videos\": 3,
  \"min_cache_percentage_ofl_to_onl\": 25 } } },
  \"offline_download_config\": { \"sort_type\": \"recency\",
  \"disable_cache\": true, \"global_cache_ttl_days\": 15,
  \"max_cache_item\": 10, \"recommended_video_quality\": \"good\",
  \"ucq_download_config\": { \"average\": { \"exit\": 0, \"minimise\":
  0, \"notification\": 0 }, \"fast\": { \"exit\": 0, \"minimise\": 0,
  \"notification\": 0 }, \"slow\": { \"exit\": 0, \"minimise\": 0,
  \"notification\": 0 }, \"good\": { \"exit\": 0, \"minimise\": 0,
  \"notification\": 0 }, \"veryfast\": { \"exit\": 0, \"minimise\": 0,
  \"notification\": 0 } }, \"cache_api_sync_time_secs\": 86400,
  \"app_inactivity_duration_days\": 10 }, \"buffer_threshold_config\": {
  \"average\": { \"organic\": {
  \"buffer_threshold_initial_videos_secs\": 1,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } },
  \"fast\": { \"organic\": { \"buffer_threshold_initial_videos_secs\":
  1, \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } },
  \"slow\": { \"organic\": { \"buffer_threshold_initial_videos_secs\":
  1, \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } },
  \"good\": { \"organic\": { \"buffer_threshold_initial_videos_secs\":
  1, \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } },
  \"veryfast\": { \"organic\": {
  \"buffer_threshold_initial_videos_secs\": 1,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } } } },
  \"postLangMapping\": \[ { \"languageGroup\": \[ \"na\" \], \"values\":
  \[ \"hi\", \"en\", \"te\", \"ta\", \"ml\", \"kn\", \"mr\", \"gj\",
  \"bn\", \"or\", \"pa\", \"bh\" \] }, { \"languageGroup\": \[ \"hi\",
  \"mr\", \"pa\", \"gj\", \"bh\", \"or\", \"bn\" \], \"values\": \[
  \"hi\", \"mr\", \"pa\", \"gj\", \"bh\", \"or\", \"bn\", \"en\",
  \"te\", \"ta\", \"ml\", \"kn\" \] }, { \"languageGroup\": \[ \"te\",
  \"ta\", \"ml\", \"kn\" \], \"values\": \[ \"te\", \"ta\", \"ml\",
  \"kn\", \"hi\", \"en\", \"mr\", \"pa\", \"gj\", \"bh\", \"or\", \"bn\"
  \] } \], \"uploadShareConfig\": { \"shareChannels\": \[ { \"pkgName\":
  \"com.twitter.android\", \"iconUrl\": \"twitter\", \"name\":
  \"TWITTER\" }, { \"pkgName\": \"com.instagram.android\", \"iconUrl\":
  \"instagram\", \"name\": \"INSTAGRAM\" }, { \"pkgName\":
  \"com.facebook.katana\", \"iconUrl\": \"facebook\", \"name\":
  \"FACEBOOK\" }, { \"pkgName\": \"com.whatsapp\", \"iconUrl\":
  \"whatsapp\", \"name\": \"WHATSAPP\" } \], \"initialPollingDelayMs\":
  5000, \"pollingDelayMs\": 5000, \"maxPollingAttempts\": 10,
  \"shareNudgeCount\": 7, \"delaySharePromptHideMs\": 3000,
  \"delayPIPSuccessHideMs\": 5000 }, \"profileBlockedConfig\": {
  \"pb_config_title\": \"Profile Blocked!\", \"pb_config_subtitle\":
  \"This profile has been blocked due to violation of community
  guidelines.\", \"pb_config_cta\": \"Learn more\",
  \"pb_config_cta_link\":
  \"https://qa-share.myjosh.in/help/community-violation-guidelines\",
  \"pb_config_subtitle_dialog\": \"You cannot post a video\",
  \"pb_config_cta_neg_dialog\": \"Dismiss\" },
  \"fpv_profile_quality_config\": \[ { \"network_quality\":
  \"veryfast\", \"profile_quality\": \"veryfast\" }, {
  \"network_quality\": \"fast\", \"profile_quality\": \"veryfast\" }, {
  \"network_quality\": \"good\", \"profile_quality\": \"veryfast\" }, {
  \"network_quality\": \"average\", \"profile_quality\": \"good\" }, {
  \"network_quality\": \"slow\", \"profile_quality\": \"average\" } \],
  \"fpv_quality_nudge_config\": { \"network_quality\": \"average\",
  \"message\": \"Slow Internet! Playing Video in Low Quality\",
  \"duration\": 3000, \"per_session_count\": 1 }, \"quality_mapping\":
  \[ { \"network_quality\": \"veryfast\", \"profile_quality\": \"fast\"
  }, { \"network_quality\": \"fast\", \"profile_quality\": \"fast\" }, {
  \"network_quality\": \"good\", \"profile_quality\": \"good\" }, {
  \"network_quality\": \"average\", \"profile_quality\": \"average\" },
  { \"network_quality\": \"slow\", \"profile_quality\": \"slow\" } \],
  \"cache_config\": { \"cache_offline_directory_max_size_in_mb\": 200,
  \"cache_prefetch_directory_max_size_in_mb\": 250,
  \"cache_directory_max_size_in_mb\": 100, \"clear_session_data\":
  false, \"min_cache_item_to_fetch_api\": 5, \"hard_start_config\": {
  \"disableHardStart\": true, \"file_download_percentage\": 100,
  \"download_high_bitrate_variant\": true,
  \"min_stream_download_on_average_network\": 2,
  \"min_stream_download_on_fast_network\": 2,
  \"min_stream_download_on_good_network\": 2,
  \"min_stream_download_on_slow_network\": 2 },
  \"session_start_config\": { \"slow\": { \"from_offline_back_to_back\":
  3 }, \"average\": { \"from_offline_back_to_back\": 3 }, \"good\": {
  \"from_offline_back_to_back\": 3 }, \"fast\": {
  \"from_offline_back_to_back\": 3 }, \"veryfast\": {
  \"from_offline_back_to_back\": 3 } }, \"prefetch_download_config\": {
  \"disable_cache\": false, \"prefetch_download_count_config\": {
  \"slow\": { \"no_of_videos\": 3, \"min_cache_percentage_ofl_to_onl\":
  100 }, \"average\": { \"no_of_videos\": 3,
  \"min_cache_percentage_ofl_to_onl\": 85 }, \"good\": {
  \"no_of_videos\": 5, \"min_cache_percentage_ofl_to_onl\": 70 },
  \"fast\": { \"no_of_videos\": 2, \"min_cache_percentage_ofl_to_onl\":
  50 }, \"veryfast\": { \"no_of_videos\": 2,
  \"min_cache_percentage_ofl_to_onl\": 50 } } },
  \"offline_download_config\": { \"sort_type\": \"recency\",
  \"disable_cache\": false, \"global_cache_ttl_days\": 15,
  \"max_cache_item\": 40, \"recommended_video_quality\": \"good\",
  \"ucq_download_config\": { \"average\": { \"exit\": 2, \"minimise\":
  2, \"notification\": 2 }, \"fast\": { \"exit\": 2, \"minimise\": 2,
  \"notification\": 2 }, \"slow\": { \"exit\": 2, \"minimise\": 2,
  \"notification\": 2 }, \"good\": { \"exit\": 2, \"minimise\": 2,
  \"notification\": 2 }, \"veryfast\": { \"exit\": 2, \"minimise\": 2,
  \"notification\": 2 } }, \"cache_api_sync_time_secs\": 86400,
  \"app_inactivity_duration_days\": 10 }, \"buffer_threshold_config\": {
  \"average\": { \"organic\": {
  \"buffer_threshold_initial_videos_secs\": 1,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } },
  \"fast\": { \"organic\": { \"buffer_threshold_initial_videos_secs\":
  1, \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } },
  \"slow\": { \"organic\": { \"buffer_threshold_initial_videos_secs\":
  1, \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } },
  \"good\": { \"organic\": { \"buffer_threshold_initial_videos_secs\":
  1, \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } },
  \"veryfast\": { \"organic\": {
  \"buffer_threshold_initial_videos_secs\": 1,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } } } },
  \"duet_config\": { \"camera_portrait_min_height_to_width\": { \"h\":
  16, \"w\": 9 }, \"camera_portrait_max_height_to_width\": { \"h\": 21,
  \"w\": 9 }, \"camera_landscape_min_width_to_height\": { \"h\": 8,
  \"w\": 9 }, \"camera_landscape_max_width_to_height\": { \"h\": 9,
  \"w\": 21 }, \"video_download_url\": \"\",
  \"create_and_edit_configs\": { \"duetable_config_for_verified\": {
  \"default_value\": \"OFF\", \"aspect_ratio\": {
  \"allow_for_portrait\": true, \"allow_for_square\": true,
  \"allow_for_landscape\": false }, \"video_source\": {
  \"camera_with_josh_library\": true, \"camera_without_josh_library\":
  true, \"gallery_with_josh_library\": true,
  \"gallery_without_josh_library\": true, \"duet\": false },
  \"video_source_v2\": \[ { \"srcType\": \"camera\", \"josh_library\":
  true, \"non_josh_library\": true }, { \"srcType\": \"gallery\",
  \"josh_library\": true, \"non_josh_library\": true }, { \"srcType\":
  \"multi_segment_camera\", \"josh_library\": true,
  \"non_josh_library\": true }, { \"srcType\":
  \"multi_segment_gallery\", \"josh_library\": true,
  \"non_josh_library\": true }, { \"srcType\":
  \"multi_segment_camera_gallery\", \"josh_library\": true,
  \"non_josh_library\": true }, { \"srcType\": \"external_did\",
  \"josh_library\": true, \"non_josh_library\": true }, { \"srcType\":
  \"external\", \"josh_library\": true, \"non_josh_library\": true }, {
  \"srcType\": \"duet\", \"josh_library\": false, \"non_josh_library\":
  false } \] }, \"duetable_config_for_nonverified\": {
  \"default_value\": \"OFF\", \"aspect_ratio\": {
  \"allow_for_portrait\": true, \"allow_for_square\": true,
  \"allow_for_landscape\": false }, \"video_source\": {
  \"camera_with_josh_library\": true, \"camera_without_josh_library\":
  true, \"gallery_with_josh_library\": true,
  \"gallery_without_josh_library\": true, \"duet\": false },
  \"video_source_v2\": \[ { \"srcType\": \"camera\", \"josh_library\":
  true, \"non_josh_library\": true }, { \"srcType\": \"gallery\",
  \"josh_library\": true, \"non_josh_library\": true }, { \"srcType\":
  \"multi_segment_camera\", \"josh_library\": true,
  \"non_josh_library\": true }, { \"srcType\":
  \"multi_segment_gallery\", \"josh_library\": true,
  \"non_josh_library\": true }, { \"srcType\":
  \"multi_segment_camera_gallery\", \"josh_library\": true,
  \"non_josh_library\": true }, { \"srcType\": \"external_did\",
  \"josh_library\": true, \"non_josh_library\": true }, { \"srcType\":
  \"external\", \"josh_library\": true, \"non_josh_library\": true }, {
  \"srcType\": \"duet\", \"josh_library\": false, \"non_josh_library\":
  false } \] } } }, \"duet_video_volume_config\": {
  \"dueted_video_volume\": 20, \"recorded_video_volume\": 100 },
  \"fire_track_from_cache\": true, \"handshake_version\": \"470\",
  \"performance_analytics_enabled\": false, \"upload_duration\": 120,
  \"disable_error_event\": false, \"disable_slow_network_prompts\":
  false, \"speed_quality_map\": { \"100\": \"slow\", \"500\":
  \"average\", \"1000\": \"good\", \"10000\": \"fast\", \"50000\":
  \"veryfast\" }, \"record_duration\": 15, \"first_time_pull_delay\":
  300, \"first_chunk_request_params\": { \"cdn\": \"Y\", \"src\":
  \"app\" }, \"max_upload_size\": 200, \"upgrade\": \"LATEST\",
  \"rateConfig\": { \"enable\": true,
  \"preActivitySessionWaitTimeInSeconds\": 600,
  \"minNumberOfStoriesViewedPerSession\": 10, \"minNumberOfBooksRead\":
  4, \"maxNumberOfTimesToShowRateScreen\": 3,
  \"minNumberOfDaysToWaitShowingRateScreen\": 30,
  \"maxWaitDaysForNewUsersToShowRateScreen\": 7,
  \"minLaunchesForNewUsersToShowRateScreen\": 3,
  \"minNumberOfDaysUserToWaitAfterLastSeen\": 10,
  \"minNumberOfAppLaunchesToWaitAfterLastSeen\": 10 },
  \"maxHistoryCount\": 50, \"enable_reactions_api_hit\": true,
  \"max_recent_interaction_count\": 50,
  \"location_fetch_interval_in_seconds\": 86400,
  \"min_gap_between_app_update_prompt_secs\": 172800,
  \"video_views_in_session_for_update_prompt\": 5, \"permission\": {
  \"id\": 24, \"event\": \"appLaunch\", \"activity\": { \"type\":
  \"permission\", \"attributes\": { \"gapCount\": \"4\", \"permDesc\":
  \"Josh needs access to the following\", \"permTitle\": \"Permissions
  required\", \"openSettings\": \"Josh needs storage access to perform
  this action. To enable it, please visit your app settings.\",
  \"settingsAction\": \"Settings\", \"storagePermDesc\": \"We need this
  for critical features like downloading a video.\",
  \"locationPermDesc\": \"We need this to show you videos being posted
  by users around you.\", \"storagePermSubtitle\": \"Storage Access\",
  \"locationPermSubtitle\": \"Location Access\",
  \"permissionNegativeBtn\": \"LATER\", \"permissionPositiveBtn\":
  \"Allow\" } }, \"resource\": \"coolfie\", \"precondition\": {
  \"minItemsViewed\": 7, \"minTimeEngaged\": 0, \"maxNumberOfDisplay\":
  0, \"minNumberOfOccurences\": 5 } }, \"fire_comscore_from_cache\":
  true, \"max_notifications_in_tray\": 4, \"thumbnail_qualities\": {
  \"fast\": { \"quality\": \"h\", \"resolution\": 480 }, \"good\": {
  \"quality\": \"h\", \"resolution\": 480 }, \"slow\": { \"quality\":
  \"h\", \"resolution\": 480 }, \"average\": { \"quality\": \"h\",
  \"resolution\": 480 } }, \"default_notification_duration\": 120,
  \"max_upload_bitrate\": 1500, \"pull_notifications_enabled\": true,
  \"video_qualities\": { \"fast\": { \"quality\": \"h\", \"resolution\":
  480 }, \"good\": { \"quality\": \"h\", \"resolution\": 480 },
  \"slow\": { \"quality\": \"h\", \"resolution\": 480 }, \"average\": {
  \"quality\": \"h\", \"resolution\": 480 } },
  \"disable_firebase_perf\": false, \"google_play_url\": {
  \"share_video_text\": \"Download Josh for more videos like this!\",
  \"download_video_text\": \"Download Josh for more videos like this!\",
  \"download_live_stream_text\": \"Download Josh for more livestreams
  like this!\", \"share_google_play_url\":
  \"https://m.myjosh.in/6OaT/32e07bf\", \"setting_google_play_url\":
  \"https://m.myjosh.in/6OaT/568901e6\", \"download_google_play_url\":
  \"https://m.myjosh.in/6OaT/6d76ce25\", \"duet_share_text\": \"Create
  and watch amazing duets with %1\$s! \\n%2\$s \\nDownload Josh now to
  watch & even create more great videos like this!
  \\nhttps://play.google.com/store/apps/details?id=com.eterno.shortvideos\"
  }, \"default_notification_text\": \"Welcome to Josh! Check out the
  latest news in your preferred language.\",
  \"story_detail_error_page_url\":
  \"https://m.dailyhunt.in/webItem/errorPage.html\",
  \"share_floating_icon_type\": \"floatingIconBentArrow\",
  \"upload_format_list\": \[ \"3gp\", \"mp4\" \], \"nlfc_config\": {
  \"disable_nlfc\": false, \"min_time_spent_to_trigger\": 6000,
  \"min_time_spent_to_trigger_with_social\": 6000,
  \"min_percentage_completion\": 75,
  \"skip_nlfc_for_session_on_failure\": 3, \"min_offset_to_append\": 0
  }, \"moderationNsfwReportUrl\":
  \"https://qa-share.myjosh.in/report/machine-moderation/1\",
  \"moderationDuplicateReportUrl\":
  \"https://qa-share.myjosh.in/report/ownership-content/1\",
  \"joshCam1Config\": { \"licenseUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/joshCam1Config/license/android/20986-269-8619db07c55966e42c2f42acfa3e187d.lic\",
  \"licenseUrliOS\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/joshCam1Config/license/ios/MeisheSDKLicense.lic\"
  }, \"sdkType\": \"JOSH_CAM1\", \"followersTabName\": \"Top Fans\",
  \"handshakeDefaultInterval\": 43200000, \"maxApiDelay\": 2000,
  \"maxErrorEventPerInterval\": 10, \"upload_duration_v2\": 60,
  \"min_upload_duration\": 5, \"max_recent_navigable_action_count\": 30,
  \"timerPeriodInSeconds\": 60, \"firstTimePullDelay\": 60,
  \"enable_whatsapp_share\": true, \"enable_video_download_on_share\":
  true, \"hit_firebase_event_once\": true, \"enableGzip_v2\": true,
  \"allowEmptyTitleInCreatePost\": false, \"is_firebase_event_enabled\":
  true, \"dev_error_for_2xxTo4xx_enabled\": false,
  \"location_prompt_for_max_time_count\": 3,
  \"location_prompt_after_max_post_count\": 0, \"video_resources\": {
  \"1\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/1?version=26\",
  \"2\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/2?version=197\",
  \"3\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/3?version=1\",
  \"4\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/4?version=1\",
  \"5\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/5?version=1\",
  \"6\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/6?version=1\",
  \"7\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/7?version=1\",
  \"8\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/8?version=1\",
  \"9\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/9?version=1\",
  \"10\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/10?version=1\",
  \"11\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/11?version=1\",
  \"12\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/12?version=1\",
  \"13\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/13?version=2\",
  \"14\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/14?version=112\",
  \"15\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/15?version=13\",
  \"16\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/16?version=1\",
  \"17\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/17?version=1\",
  \"25\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/25?version=10\",
  \"26\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/26?version=6\",
  \"27\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/27?version=10\",
  \"28\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/28?version=21\",
  \"29\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/29?version=9\",
  \"30\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/30?version=9\",
  \"31\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/31?version=17\",
  \"32\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/32?version=27\",
  \"33\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/33?version=4\",
  \"34\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/34?version=18\",
  \"35\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/35?version=27\",
  \"36\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/36?version=1\",
  \"37\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/37?version=1\",
  \"24\":
  \"https://qa-gateway.myjosh.in/api/v1/materialinfo/24?version=1\" },
  \"following_sync_interval_in_seconds\": 86400,
  \"appsOnDeviceEnabled\": false, \"appsOnDeviceEnabledV2\": true,
  \"cleanupConfig\": { \"maxMusicDownloads\": 20,
  \"maxStickerDownloads\": 100 }, \"network_config\": {
  \"exo_weightage_double\": 0.8, \"network_weightage_double\": 2,
  \"sliding_percentile_percentile\": 0.5, \"bitrate_expression\": {
  \"id\": \"1\", \"formula\": \"(e\*0.8)+(n\*2)\" },
  \"bitrate_expression_v2\": { \"id\": \"3\", \"formula\": \"function
  f42(e,n){ \\n if(e\<n) return e\*0.8+n\*0.7; \\n else { var
  wa=e\*e/(e+n)+n\*n/(e+n); return Math.min(wa,e);};\\n};\" },
  \"bitrate_expression_exception\": { \"id\": \"2\", \"formula\":
  \"(e\*0.8)+(n\*0.7)\" }, \"lifetime_bitrate_capture_window_sec\":
  604800, \"coldstart_transition_threshold_sec\": 10,
  \"coldstart_network_provider_mapping\": \[ { \"network\": \"4G\",
  \"provider\": \"Jio 4G\", \"quality\": \"good\" }, { \"network\":
  \"4G\", \"provider\": \"airtel\", \"quality\": \"good\" }, {
  \"network\": \"4G\", \"provider\": \"Vi India\", \"quality\": \"good\"
  }, { \"network\": \"4G\", \"provider\": \"IND airtel\", \"quality\":
  \"good\" }, { \"network\": \"4G\", \"provider\": \"Vodafone IN\",
  \"quality\": \"good\" }, { \"network\": \"4G\", \"provider\":
  \"Airtel\", \"quality\": \"good\" }, { \"network\": \"4G\",
  \"provider\": \"Idea\", \"quality\": \"good\" }, { \"network\":
  \"4G\", \"provider\": \"JIO 4G\", \"quality\": \"good\" }, {
  \"network\": \"w\", \"provider\": \"Jio 4G\", \"quality\": \"fast\" },
  { \"network\": \"w\", \"provider\": \"airtel\", \"quality\": \"fast\"
  }, { \"network\": \"4G\", \"provider\": \"JIO\", \"quality\": \"good\"
  }, { \"network\": \"4G\", \"provider\": \"AIRTEL\", \"quality\":
  \"good\" }, { \"network\": \"3G\", \"provider\": \"Vi India\",
  \"quality\": \"average\", \"maxQuality\": \"average\" }, {
  \"network\": \"w\", \"provider\": \"Vi India\", \"quality\": \"fast\"
  }, { \"network\": \"4G\", \"provider\": \"VIL\", \"quality\": \"good\"
  }, { \"network\": \"4G\", \"provider\": \"Vodafone\", \"quality\":
  \"good\" }, { \"network\": \"w\", \"provider\": \"Vodafone IN\",
  \"quality\": \"fast\" }, { \"network\": \"w\", \"provider\": \"IND
  airtel\", \"quality\": \"fast\" }, { \"network\": \"2G\",
  \"provider\": \"airtel\", \"quality\": \"slow\", \"maxQuality\":
  \"slow\" }, { \"network\": \"4G\", \"provider\": \"Airtel \| airtel\",
  \"quality\": \"good\" }, { \"network\": \"4G\", \"provider\": \"IND
  AirTel\", \"quality\": \"good\" }, { \"network\": \"3G\",
  \"provider\": \"Vodafone IN\", \"quality\": \"average\",
  \"maxQuality\": \"average\" }, { \"network\": \"w\", \"provider\":
  \"Idea\", \"quality\": \"fast\" }, { \"network\": \"4G\",
  \"provider\": \"JIO 4G \| Jio 4G\", \"quality\": \"good\" }, {
  \"network\": \"4G\", \"provider\": \"AirTel\", \"quality\": \"good\"
  }, { \"network\": \"3G\", \"provider\": \"Idea\", \"quality\":
  \"average\", \"maxQuality\": \"average\" }, { \"network\": \"4G\",
  \"provider\": \"Vi India \| Vodafone IN\", \"quality\": \"good\" }, {
  \"network\": \"2G\", \"provider\": \"Vi India\", \"quality\":
  \"slow\", \"maxQuality\": \"slow\" }, { \"network\": \"w\",
  \"provider\": \"Airtel\", \"quality\": \"fast\" }, { \"network\":
  \"3G\", \"provider\": \"BSNL MOBILE\", \"quality\": \"average\",
  \"maxQuality\": \"average\" }, { \"network\": \"4G\", \"provider\":
  \"BSNL MOBILE\", \"quality\": \"good\" }, { \"network\": \"4G\",
  \"provider\": \"Vi India \| Idea\", \"quality\": \"good\" }, {
  \"network\": \"3G\", \"provider\": \"BSNL Mobile\", \"quality\":
  \"average\", \"maxQuality\": \"average\" }, { \"network\": \"4G\",
  \"provider\": \"BSNL Mobile\", \"quality\": \"good\" }, { \"network\":
  \"4G\", \"provider\": \"IDEA\", \"quality\": \"good\" }, {
  \"network\": \"w\", \"provider\": \"JIO 4G\", \"quality\": \"fast\" },
  { \"network\": \"w\", \"provider\": \"BSNL MOBILE\", \"quality\":
  \"fast\" }, { \"network\": \"4G\", \"provider\": \"Jio\", \"quality\":
  \"good\" }, { \"network\": \"4G\", \"provider\": \"Airtel_BH\",
  \"quality\": \"good\" }, { \"network\": \"w\", \"provider\": \"BSNL
  Mobile\", \"quality\": \"fast\" }, { \"network\": \"2G\",
  \"provider\": \"Idea\", \"quality\": \"slow\", \"maxQuality\":
  \"slow\" }, { \"network\": \"2G\", \"provider\": \"Vodafone IN\",
  \"quality\": \"slow\", \"maxQuality\": \"slow\" }, { \"network\":
  \"4G\", \"provider\": \"!dea\", \"quality\": \"good\" }, {
  \"network\": \"3G\", \"provider\": \"CellOne\", \"quality\":
  \"average\", \"maxQuality\": \"average\" }, { \"network\": \"4G\",
  \"provider\": \"JIO4G\", \"quality\": \"good\" }, { \"network\":
  \"4G\", \"provider\": \"Airtel Stay Home\", \"quality\": \"good\" }, {
  \"network\": \"2G\", \"provider\": \"Airtel\", \"quality\": \"slow\",
  \"maxQuality\": \"slow\" }, { \"network\": \"w\", \"provider\":
  \"JIO\", \"quality\": \"fast\" }, { \"network\": \"2G\", \"provider\":
  \"IND airtel\", \"quality\": \"slow\", \"maxQuality\": \"slow\" }, {
  \"network\": \"0\", \"provider\": \"Jio 4G\", \"quality\": \"fast\",
  \"maxQuality\": \"fast\" }, { \"network\": \"3G\", \"provider\":
  \"airtel\", \"quality\": \"average\", \"maxQuality\": \"average\" }, {
  \"network\": \"WiFi\", \"provider\": \"AirTel\", \"quality\": \"fast\"
  }, { \"network\": \"4G\", \"provider\": \"unknown\", \"quality\":
  \"good\" }, { \"network\": \"WiFi\", \"provider\": \"unknown\",
  \"quality\": \"fast\" }, { \"network\": \"WiFi\", \"provider\":
  \"Jio\", \"quality\": \"fast\" }, { \"network\": \"4G\", \"provider\":
  \"CellOne\", \"quality\": \"good\" }, { \"network\": \"3G\",
  \"provider\": \"!dea\", \"quality\": \"average\", \"maxQuality\":
  \"average\" }, { \"network\": \"w\", \"provider\": \"VIL\",
  \"quality\": \"fast\" }, { \"network\": \"4G\", \"provider\":
  \"Ind-Jio\", \"quality\": \"good\" }, { \"network\": \"w\",
  \"provider\": \"Vi India \| Vodafone IN\", \"quality\": \"fast\" }, {
  \"network\": \"3G\", \"provider\": \"VIL\", \"quality\": \"average\",
  \"maxQuality\": \"average\" }, { \"network\": \"4G\", \"provider\":
  \"Emergency calls only\", \"quality\": \"good\" }, { \"network\":
  \"2G\", \"provider\": \"Jio 4G\", \"quality\": \"slow\",
  \"maxQuality\": \"slow\" }, { \"network\": \"3G\", \"provider\":
  \"Vodafone\", \"quality\": \"average\", \"maxQuality\": \"average\" },
  { \"network\": \"3G\", \"provider\": \"Jio 4G\", \"quality\":
  \"average\", \"maxQuality\": \"average\" }, { \"network\": \"w\",
  \"provider\": \"AIRTEL\", \"quality\": \"fast\" }, { \"network\":
  \"4G\", \"provider\": \"No service\", \"quality\": \"good\" }, {
  \"network\": \"w\", \"provider\": \"Vi India \| Idea\", \"quality\":
  \"fast\" }, { \"network\": \"0\", \"provider\": \"airtel\",
  \"quality\": \"fast\", \"maxQuality\": \"fast\" }, { \"network\":
  \"w\", \"provider\": \"Vodafone\", \"quality\": \"fast\" }, {
  \"network\": \"w\", \"provider\": \"Any\", \"quality\": \"fast\" }, {
  \"network\": \"4G\", \"provider\": \"Any\", \"quality\": \"good\" }, {
  \"network\": \"3G\", \"provider\": \"Any\", \"quality\": \"average\",
  \"maxQuality\": \"average\" }, { \"network\": \"2G\", \"provider\":
  \"Any\", \"quality\": \"slow\", \"maxQuality\": \"slow\" }, {
  \"network\": \"Any\", \"provider\": \"Any\", \"quality\": \"good\",
  \"maxQuality\": \"good\" } \], \"exo_sliding_percentile_max_weight\":
  1000 }, \"speed_quality_map_v2\": { \"200\": \"slow\", \"2000\":
  \"average\", \"6000\": \"good\", \"8000\": \"fast\", \"16000\":
  \"veryfast\" }, \"cameraProperties\": { \"videoCaptureResolution\":
  \"EXTREMELY_HIGH\", \"recordBitrate\": \"3000000\", \"fps\": \"30\",
  \"audioSampleRate\": \"44100\", \"autoFocus\": \"Y\",
  \"autoExposure\": \"Y\", \"sharpness\": \"Y\", \"beautify\": \"Y\",
  \"Intensity\": \"0.2\", \"videoStabilization\": \"MODE_SUPER\",
  \"continuousFocus\": \"Y\", \"zoom\": \"Y\", \"maxZoom\": \"99\",
  \"bitDepth\": \"8\", \"compileBitrate\": \"3000000\",
  \"audioBitrate\": \"160000\", \"losslessAudio\": \"true\",
  \"encoderPreset\": \"MEDIUM\", \"encodedCRF\": \"21\",
  \"encoderName\": \"H.265\", \"encoderProfile\": \"high\", \"HDR\":
  \"st2084\" }, \"max_consumed_cache_items_count\": 30, \"attRules\": {
  \"enableATTPrompt\": true, \"attPromptConfig\": {
  \"minInstallLaunchCount\": 2, \"minUpgradeLaunchCount\": 3,
  \"coolOffLaunchCount\": 2, \"maxAttemptCount\": 30, \"title\":
  \"Personalized Ads\", \"message\": \"Josh would like permission to
  serve personalized ads to you\" } }, \"uploadConfig\": {
  \"resumableUploadsEnabled\": true, \"failureAutoRetryThreshold\": 5,
  \"connectTimeout\": 60000, \"readTimeout\": 60000, \"writeTimeout\":
  60000, \"tusChunkSize\": 1048576, \"tusRequestPayloadSize\": -1,
  \"tusExtendedRetryDelays\": \[ 10000, 10000, 10000, 10000, 20000 \],
  \"tusNormalRetryDelays\": \[ 500, 1000, 2000, 3000 \] },
  \"quicHints\": \[ { \"host\": \"qa-stream.myjosh.in\", \"port\": 443,
  \"alternatePort\": 443 } \], \"bookmarkConfig\": {
  \"musicTrimNudgeCount\": 5, \"bookMarkNudgeCount\": 5,
  \"bookmarkSyncMinimumGap\": 86400000, \"bookmarkFetchItemLimit\": 10,
  \"bookmarkItemMaxLimit\": 500 }, \"reactivate_account_config\": {
  \"temporarily_deactivated_title\": \"We missed you\...\",
  \"temporarily_deactivated_sub_title\": \"Tap the button below to
  reactivate\\nyour account\", \"temporarily_deactivated_cta_text\":
  \"Reactivate Account\", \"permanently_deactivated_title\": \"This
  account has been permanently deleted\",
  \"permanently_deactivated_sub_title\": \"To use Josh, create a new
  account.\", \"permanently_deactivated_cta_text\": \"Create New
  Account\" }, \"createPostConfig\": { \"noOfHashTagAllowed\": 5,
  \"noOfUserHandleAllowed\": 3, \"maxNumKeywords\": 5 }, \"csConfig\": {
  \"enabled\": true, \"frequencyTimeMS\": 86400000, \"bucketSizeNew\":
  2000 }, \"encryption\": { \"version\": 1, \"key\":
  \"LS0tLS1CRUdJTiBQVUJMSUMgS0VZLS0tLS0KTUlHZk1BMEdDU3FHU0liM0RRRUJBUVVBQTRHTkFEQ0JpUUtCZ1FDWkd2L1dncXo1OEhjOURMZUFObHRmNFVJMwp3Vkoyb0xJYzZEemRheFdaTXRSVkYzTGYySlFSZURQMTRsKzNYUGdXaC9lVlFBU1Z3QTZKaUYxemw1WXhJS1ovCmppc2NEaFRDS25idmE1dTdrYjFMb0FUTlFKQlZtZGhSOFVZbWc3dUZWMnJTVUg3UEJ3VytyLzhKcm9sOXA1SGEKckIxVlBPMEtIR0YyZ2JNS2V3SURBUUFCCi0tLS0tRU5EIFBVQkxJQyBLRVktLS0tLQo=\"
  }, \"profile_wizard_config\": { \"completeMsgDismissTimeInMills\":
  3000, \"setUpProfileMsgShowTimeInDays\": 360 },
  \"snapchatLogoutIconUrl\":
  \"https://sdk.bitmoji.com/me/sticker/#AVATAR_ID#/204d8f0d-50e5-4db5-a810-f6525a68dc39\",
  \"fileUploads\": { \"twitter\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/Twitter-Logo.webp\",
  \"instagram\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/Instagram-Logo.webp\",
  \"facebook\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/Facebook-Logo.webp\",
  \"whatsapp\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/Whatsapp-Logo.webp\",
  \"uploads\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/VmlkZW8=.png\",
  \"trending\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/VHJlbmRpbmdfMQ==.png\",
  \"likes\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/TGlrZV8x.png\",
  \"drafts\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/ZHJhZnRz.png\",
  \"tagged\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/TWVudGlvbl8x.png\",
  \"discovery_icon\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/ZGlzY292ZXJ5.png\",
  \"audio_icon\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/bXVzaWM=.png\",
  \"hello\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/YmdfY3VzdG9t.png\",
  \"trending_icon\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/VHJlbmRpbmc=.png\",
  \"photos\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/Sm9zaCAoMyk=.png\",
  \"social\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/U29jaWFsXzE=.png\",
  \"uploads_selected\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/dXBsb2Fkc19zZWxlY3RlZA==.png\",
  \"likes_selected\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/Sm9zaEAyeF8=.png\",
  \"trending_selected\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/Sm9zaEAyeA==.png\",
  \"social_selected\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/TmV3cy0xLjU=.png\",
  \"tagged_selected\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/QA==.png\",
  \"photos_selected\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/Sm9zaA==.png\",
  \"drafts_selected\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/UGFwZXI=.png\",
  \"gifting_icon_url\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/Z2lmdF9pY29u.png\",
  \"tipping_icon_url\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_version_content/JOSH_STATIC_CONFIG/Z2lmdF9pY29u.png\"
  } } } }

- **Request Method and URL:**

  GET : https://qa-gateway.coolfie.io/api/v1/materialinfo/1?version=1

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/materialinfo/1?version=1\' \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"version\": 26, \"errNo\": 0,
  \"hasNext\": true, \"list\": \[ { \"id\":
  \"75F9024F-6DFA-4167-BF4D-F18D04891F3C\", \"category\": 2, \"name\":
  \"DreamWorld\", \"version\": 2, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/theme_1/75F9024F-6DFA-4167-BF4D-F18D04891F3C.2.theme\",
  \"packageSize\": 6361147, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/theme_1/4D20BDFB-8160-005A-A756-C3B5A4042CDB.jpg\",
  \"supportedAspectRatio\": 3, \"idx\": 21, \"hasSound\": true,
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"30908B3C-B591-4F27-9449-7672397C456E\", \"category\": 2, \"name\":
  \"Joyous Kidhood\", \"desc\": \"\", \"tags\": \"\", \"version\": 2,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/theme_1/30908B3C-B591-4F27-9449-7672397C456E.2.theme\",
  \"packageSize\": 2612701, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/theme_1/58E1C978-9DB6-E6DE-FF27-EC76FE4A0D20.jpg\",
  \"supportedAspectRatio\": 3, \"idx\": 22, \"pass_through\": \"EFFECT\"
  }, { \"id\": \"E530AC44-8AC5-4489-94D6-59D1D555D5A9\", \"category\":
  1, \"name\": \"Lovelylace\", \"desc\": \"\", \"tags\": \"\",
  \"version\": 2, \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/theme_1/E530AC44-8AC5-4489-94D6-59D1D555D5A9.2.theme\",
  \"packageSize\": 2836857, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/theme_1/E8577E20-3625-E2A5-202A-F605EB3C547D.jpg\",
  \"supportedAspectRatio\": 3, \"idx\": 24, \"pass_through\": \"EFFECT\"
  }, { \"id\": \"A501BB98-0728-4B34-A6BC-27BEFE2DC94C\", \"category\":
  1, \"name\": \"GreenMood\", \"desc\": \"\", \"tags\": \"\",
  \"version\": 2, \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/theme_1/A501BB98-0728-4B34-A6BC-27BEFE2DC94C.2.theme\",
  \"packageSize\": 5273807, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/theme_1/ACB71A82-233A-E8CB-8E78-E7ABD69460B3.jpg\",
  \"supportedAspectRatio\": 3, \"idx\": 25, \"pass_through\": \"EFFECT\"
  }, { \"id\": \"2C0978FA-3686-4C21-AA2B-A68815C91386\", \"category\":
  2, \"name\": \"Simple fashion\", \"desc\": \"\", \"tags\": \"\",
  \"version\": 3, \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/theme_1/2C0978FA-3686-4C21-AA2B-A68815C91386.3.theme\",
  \"packageSize\": 1213775, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/theme_1/20A5AD28-633D-8475-F92C-BC5992383FC9.jpg\",
  \"supportedAspectRatio\": 127, \"idx\": 26, \"pass_through\":
  \"EFFECT\" }, { \"id\": \"F7D905A7-3BA4-4ED8-8E8E-DC79C509A15A\",
  \"category\": 2, \"name\": \"Melody Of Youth\", \"desc\": \"\",
  \"tags\": \"\", \"version\": 3, \"minAppVersion\": \"\",
  \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/theme_1/F7D905A7-3BA4-4ED8-8E8E-DC79C509A15A.3.theme\",
  \"packageSize\": 3225549, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/theme_1/5077D10B-0E19-0853-6BF6-DF85237F0C78.png\",
  \"supportedAspectRatio\": 31, \"idx\": 27, \"pass_through\":
  \"EFFECT\" }, { \"id\": \"B2D69406-A22C-424F-ADFA-336174CF1E9D\",
  \"category\": 2, \"name\": \"Romance\", \"desc\": \"\", \"tags\":
  \"\", \"version\": 3, \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/theme_1/B2D69406-A22C-424F-ADFA-336174CF1E9D.3.theme\",
  \"packageSize\": 4364854, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/theme_1/246D9B85-08DF-F3D6-A163-4108D4150235.jpg\",
  \"supportedAspectRatio\": 31, \"idx\": 29, \"pass_through\":
  \"EFFECT\" }, { \"id\": \"78A09AEC-3363-4CF8-9B6D-2BB632F893EA\",
  \"category\": 2, \"name\": \"Painting\", \"desc\": \"\", \"tags\":
  \"\", \"version\": 5, \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/theme_1/78A09AEC-3363-4CF8-9B6D-2BB632F893EA.5.theme\",
  \"packageSize\": 4491097, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/theme_1/0EEBDEA9-D997-0B23-9D5C-92193A48767B.jpg\",
  \"supportedAspectRatio\": 31, \"idx\": 31, \"pass_through\":
  \"EFFECT\" }, { \"id\": \"D9BCC4B9-ECDE-468F-B2EA-305CAA8B92CF\",
  \"category\": 1, \"name\": \"Visual Journaling\", \"desc\": \"\",
  \"tags\": \"\", \"version\": 3, \"minAppVersion\": \"\",
  \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/theme_1/D9BCC4B9-ECDE-468F-B2EA-305CAA8B92CF.3.theme\",
  \"packageSize\": 1969870, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/theme_1/47DFED20-2527-ABBD-0A3D-9F3867FD7EEA.jpg\",
  \"supportedAspectRatio\": 127, \"idx\": 32, \"pass_through\":
  \"EFFECT\" }, { \"id\": \"4723F533-CC88-4CCB-BF40-1E8F1DDA6F04\",
  \"category\": 2, \"name\": \"Fashion Vane\", \"desc\": \"\", \"tags\":
  \"\", \"version\": 4, \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/theme_1/4723F533-CC88-4CCB-BF40-1E8F1DDA6F04.4.theme\",
  \"packageSize\": 1942655, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/theme_1/91B048A2-E9F5-9B83-15F6-2D3678F69334.png\",
  \"supportedAspectRatio\": 7, \"idx\": 61, \"pass_through\": \"EFFECT\"
  } \] }

- **Request Method and URL:**

  GET : https://qa-gateway.coolfie.io/api/v1/langlist?version=1

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/langlist?version=1\'

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": \[ { \"key\": 2,
  \"position\": 1, \"displayName\": \"हिंदी\", \"code\": \"hi\",
  \"translation\": \"हिंदी (Hindi)\", \"iconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/language_icons/0529786d8390658ab29eb4b8babbfecd_baseq_orig.webp\",
  \"splashImageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/splash_icons/665fb35acd24938738c854ec06ac5f79_baseq_orig.webp\",
  \"primaryColor\": \"#FF619C\", \"langIconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/lang_icons/char_hi.webp\",
  \"name\": \"Hindi\", \"newIconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/new_lang_icons/Hindi.png\"
  }, { \"key\": 3, \"position\": 2, \"displayName\": \"తెలుగు\",
  \"code\": \"te\", \"translation\": \"తెలుగు (Telugu)\", \"iconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/language_icons/2525506d472def7c572b2a781a9e3ad7_baseq_orig.webp\",
  \"splashImageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/splash_icons/756180df5f6ea69a50a613beba672040_baseq_orig.webp\",
  \"primaryColor\": \"#FFBC50\", \"langIconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/lang_icons/char_te.webp\",
  \"name\": \"Telugu\", \"newIconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/new_lang_icons/Telugu.png\"
  }, { \"key\": 5, \"position\": 3, \"displayName\": \"മലയാളം\",
  \"code\": \"ml\", \"translation\": \"മലയാളം (Malayalam)\",
  \"iconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/language_icons/daca04a6697cf07688602a39f02dbd52_baseq_orig.webp\",
  \"splashImageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/splash_icons/811e612695d9236243251a0046d9e79e_baseq_orig.webp\",
  \"primaryColor\": \"#20CBC8\", \"langIconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/lang_icons/char_ml.webp\",
  \"name\": \"Malayalam\", \"newIconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/new_lang_icons/Malayalam.png\"
  }, { \"key\": 4, \"position\": 4, \"displayName\": \"தமிழ்\", \"code\":
  \"ta\", \"translation\": \"தமிழ் (Tamil)\", \"iconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/language_icons/0d7e8e4dda9f5075648282813b61f478_baseq_orig.webp\",
  \"splashImageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/splash_icons/5c494514452afaf11cc5a64fd1686b1f_baseq_orig.webp\",
  \"primaryColor\": \"#569FFF\", \"langIconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/lang_icons/char_ta.webp\",
  \"name\": \"Tamil\", \"newIconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/new_lang_icons/Tamil.png\"
  }, { \"key\": 10, \"position\": 5, \"displayName\": \"ಕನ್ನಡ\",
  \"code\": \"kn\", \"translation\": \"ಕನ್ನಡ (Kannada)\", \"iconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/language_icons/bd8d487bf516104169ac59e831cf7079_baseq_orig.webp\",
  \"splashImageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/splash_icons/bd073a1e468fff1a70665316030ce925_baseq_orig.webp\",
  \"primaryColor\": \"#967BDC\", \"langIconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/lang_icons/char_kn.webp\",
  \"name\": \"Kannada\", \"newIconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/new_lang_icons/Kannada.png\"
  }, { \"key\": 13, \"position\": 7, \"displayName\": \"मराठी\",
  \"code\": \"mr\", \"translation\": \"मराठी (Marathi)\", \"iconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/language_icons/Marathi.webp\",
  \"splashImageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/splash_icons/none.webp\",
  \"primaryColor\": \"#9E521E\", \"langIconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/lang_icons/char_mr.webp\",
  \"name\": \"Marathi\", \"newIconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/new_lang_icons/Marathi.png\"
  }, { \"key\": 12, \"position\": 8, \"displayName\": \"ગુજરાતી\",
  \"code\": \"gu\", \"translation\": \"ગુજરાતી (Gujarati)\", \"iconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/language_icons/gujarati.webp\",
  \"splashImageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/splash_icons/none.webp\",
  \"primaryColor\": \"#4B7D00\", \"langIconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/lang_icons/char_gu.webp\",
  \"name\": \"Gujarati\", \"newIconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/new_lang_icons/Gujarati.png\"
  }, { \"key\": 11, \"position\": 9, \"displayName\": \"বাংলা\",
  \"code\": \"bn\", \"translation\": \"বাংলা (Bangla)\", \"iconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/language_icons/Bengali.webp\",
  \"splashImageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/splash_icons/d1797b43340587ac4d4d2b2f97023ac4_baseq_orig.webp\",
  \"primaryColor\": \"#F23E08\", \"langIconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/lang_icons/char_bn.webp\",
  \"name\": \"Bengali\", \"newIconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/new_lang_icons/Bengali.png\"
  }, { \"key\": 14, \"position\": 10, \"displayName\": \"ଓଡିଆ\",
  \"code\": \"or\", \"translation\": \"ଓଡିଆ (Odia)\", \"iconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/language_icons/oriya.webp\",
  \"splashImageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/splash_icons/none.webp\",
  \"primaryColor\": \"#5865F2\", \"langIconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/lang_icons/char_or.webp\",
  \"name\": \"Odia\", \"newIconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/new_lang_icons/Odia.png\\n\"
  }, { \"key\": 15, \"position\": 11, \"displayName\": \"ਪੰਜਾਬੀ \",
  \"code\": \"pa\", \"translation\": \"ਪੰਜਾਬੀ (Punjabi)\", \"iconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/language_icons/Punjabi.webp\",
  \"splashImageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/splash_icons/none.webp\",
  \"primaryColor\": \"#f46b45\", \"langIconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/lang_icons/char_pa.webp\",
  \"name\": \"Punjabi\", \"newIconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/new_lang_icons/Punjabi.png\"
  }, { \"key\": 21, \"position\": 12, \"displayName\": \"भोजपुरी\",
  \"code\": \"bh\", \"translation\": \"भोजपुरी (Bhojpuri)\", \"iconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/language_icons/Bhojpuri.webp\",
  \"splashImageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/splash_icons/none.webp\",
  \"primaryColor\": \"#f46b45\", \"langIconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/lang_icons/char_bh.webp\",
  \"name\": \"Bhojpuri\", \"newIconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/new_lang_icons/Bhojpuri.png\"
  }, { \"key\": 9, \"position\": 13, \"displayName\": \"All\", \"code\":
  \"All\", \"translation\": \"All\", \"iconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/language_icons/67bf593ece0e9c65784192f41f7317f4_baseq_orig.webp\",
  \"splashImageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/splash_icons/d1797b43340587ac4d4d2b2f97023ac4_baseq_orig.webp\",
  \"primaryColor\": \"#F23E08\" }, { \"key\": 1, \"position\": 14,
  \"displayName\": \"English\", \"code\": \"en\", \"translation\":
  \"English\", \"iconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/language_icons/e559695905668fb472e6a3fea0855007_baseq_orig.webp\",
  \"splashImageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/splash_icons/bd073a1e468fff1a70665316030ce925_baseq_orig.webp\",
  \"primaryColor\": \"#967BDC\", \"langIconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/lang_icons/char_en.webp\",
  \"name\": \"English\", \"newIconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/icons/new_lang_icons/English.png\"
  } \], \"version\": 69, \"title\": \"Select your languages\",
  \"subtitle\": \"See videos made in this language\" }

- **Request Method and URL:**

  GET :
  https://qa-gateway.coolfie.io/api/v1/upgrade/version/info/JOSH_STATIC_CONFIG/217?cacheReadDisabled=true

- **Curl Request:**

  curl \--location \--request GET
  \'https://stage-gateway.coolfie.io/api/v1/upgrade/version/info/JOSH_STATIC_CONFIG/217?cacheReadDisabled=true\'
  \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.14.11.40\", \"code\": 200 }, \"data\": { \"version\": 171,
  \"data\": { \"supportedMimetypes\": \[ \"video/mp4\",
  \"video/quicktime\", \"video/x-ms-wmv\", \"video/mov\", \"video/mpg\"
  \], \"reaction_sync_interval_in_seconds\": 86400,
  \"vote_interval_in_seconds\": 86400, \"maxCommentCharLimit\": 50,
  \"max_recent_cache_action_count\": 30, \"splashTime\": 3000,
  \"profile_rejected_show_count\": 2, \"showDataSaverMode\": true,
  \"enable_youtube_connect\": true, \"enable_instagram_connect\": true,
  \"splash_ad_request_launch\": 2, \"softRelaunchDelay\": 6000,
  \"hardRelaunchDelay\": 12000, \"repeated_launch_api_request_delay\":
  60000, \"show_share_nudge_loop_count\": 2,
  \"max_share_nudge_show_count\": 3,
  \"max_lifetime_show_share_nudge_count\": 10, \"max_edit_nudge_count\":
  3, \"grid_item_count\": 3, \"animated_icon_duration_in_ms\": 500,
  \"create_post_max_char\": 120, \"precache_interest_icons\": true,
  \"video_edit_resolution\": 720,
  \"max_sticker_comment_nudge_show_count\": 1,
  \"is_apply_for_verification_enabled\": true,
  \"create_video_nudge_dismissal\": 3000, \"vote_nudge_dismissal\":
  3000, \"share_voted_video_nudge_dismissal\": 3000,
  \"effectsExpiryMaxDays\": 30, \"enable_lite_sync_once\": false,
  \"disable_experiment_api\": false, \"items_toshow_in_inbox\": 7,
  \"max_tpv_profile_suggestions\": 5,
  \"experiment_incorrect_otp_max_attempts\": 2,
  \"experiment_resend_otp_max_attempts\": 2,
  \"max_event_videos_to_download\": 2, \"max_event_videos_to_show\": 2,
  \"max_selected_videos_gallery\": 15, \"reduced_percent_volume_dub\":
  20, \"enableAutoSaveVideos\": true, \"loginScreenSubTitle\": \"Find
  friends & family, like & comment,\\npersonalise your interests & watch
  the\\nbest videos!\", \"loginScreenTitle\": \"Login to Josh\",
  \"threshold_prefetch_stream_percentage\": 1,
  \"num_of_item_check_for_prefetch\": 1, \"device_wake_up_flag\": true,
  \"hide_block_user_option\": false, \"allow_masthead_ad\": false,
  \"refresh_wait_time_ms\": 1500, \"allow_splash_ad\": false,
  \"image_share_url\": \"/image/\",
  \"images_auto_scroll_duration_in_ms\": 5000, \"send_tip_page_url\":
  \"https://stage-share.myjosh.in/webview/pay-tips?tip_to={0}&tip_by={1}&tip_to_image_url={2}&tip_to_user_name={3}&tip_by_user_name={4}\",
  \"tip_transactions_page_url\":
  \"https://stage-share.myjosh.in/webview/tip-transactions?user_id={0}\",
  \"cs_ttl_duration_in_minutes\": 30, \"wait_on_cs_page_in_seconds\": 3,
  \"contact_sync_message_config\": { \"zero_state_message\": \"Contact
  sync successful, no friends were found but you can always invite them
  later.\", \"after_follow_message\": \"You\'ve followed %d people from
  your contact book\", \"sync_in_bg\": \"Enjoy videos while we sync your
  contacts.\", \"with_contacts_state\": \"Contacts synced successfully.
  Tap to find your friends.\", \"action_text\": \"Find Friends\" },
  \"max_photo_upload_limit\": 10, \"bottom_bar_tab_sequence\": \[
  \"HOME\", \"EXPLORE\", \"LIVE\", \"SHOP\", \"NOTIFICATIONINBOX\",
  \"PROFILE\" \], \"like_comment_tab_list\": \[ \"LIKE\", \"COMMENT\",
  \"GIFT\" \], \"camera_tab_sequence\": \[ \"CAMERA\", \"TEMPLATES\",
  \"PHOTOS\", \"MEMES\", \"DUETS\" \],
  \"disable_custom_tab_social_auth\": false, \"is_seekbar_enabled\":
  true, \"is_tabbar_swiping_enabled\": true,
  \"educational_nudge_count_per_session\": 3,
  \"educational_nudge_duration_in_ms\": 3000, \"mute_ab_test_variant\":
  \"PERSISTENT_MUTE\", \"zone_info_dialog_data\": { \"title\":
  \"\<h1\>Content on this page is community managed.\</h1\>\",
  \"message\": \"\<p\>Josh does not make any warranties about the
  completeness, reliability and accuracy of this information. \<a
  href=\'https://www.google.com\'\>Read TnC\</a\>\</p\>\", \"ctaText\":
  \"\<strong\>Okay\</strong\>\" }, \"image_card_config\": {
  \"min_time_threshold_in_ms\": 5000, \"max_count_per_session\": 3,
  \"animation_list\": \[ 0, 1, 2, 5, 6, 8 \] },
  \"recent_search_item_count\": 25, \"search_default_popular_feed_url\":
  \"https://stage-feed.myjosh.in/search/?q=viral\",
  \"buy_jems_page_url\":
  \"https://stage-share.myjosh.in/webview/pay-tips-v1?tip_to={0}&tip_by={1}&tip_to_image_url={2}&tip_to_user_name={3}&tip_by_user_name={4}&package_id={5}&package_collection_id={6}\",
  \"zero_page\": { \"zone\": { \"1\": { \"title\": \"No Followers\" },
  \"2\": { \"title\": \"No Suggestions\" } }, \"user_tpv\": { \"1\": {
  \"title\": \"No Mutual Followers\" }, \"2\": { \"title\": \"No Fans\"
  }, \"3\": { \"title\": \"No Followers\" }, \"4\": { \"title\": \"No
  Pages\" }, \"5\": { \"title\": \"No Suggestions\" } }, \"user_fpv\": {
  \"2\": { \"title\": \"No Fans\", \"description\": \"Try posting more
  content and invite your friends\" }, \"3\": { \"title\": \"Not
  Following Anyone\", \"description\": \"Explore discover section and
  follow creators and other users\", \"cta_text\": \"Discovery\",
  \"cta_deeplink\":
  \"http://stage-share.myjosh.in/page/discovery/main-discovery-page\" },
  \"4\": { \"title\": \"Not Following Any Pages\", \"description\":
  \"Explore discover section and follow pages\", \"cta_text\":
  \"Discovery\", \"cta_deeplink\":
  \"http://stage-share.myjosh.in/page/discovery/main-discovery-page\" },
  \"5\": { \"title\": \"No Suggestion\" } }, \"like_comment_tpv\": {
  \"LIKE\": { \"title\": \"No Likes\" }, \"COMMENT\": { \"title\": \"No
  Comments\" }, \"GIFT\": { \"title\": \"No Gift Received\",
  \"description\": \"Explore gift section and be the first one to send
  gift\", \"cta_text\": \"Send Gifts\" } }, \"like_comment_fpv\": {
  \"LIKE\": { \"title\": \"No Likes\" }, \"COMMENT\": { \"title\": \"No
  Comments\" }, \"GIFT\": { \"title\": \"No Gift Received\",
  \"description\": \"Explore gift section and be the first one to send
  gift\" } } }, \"discovery_tab_list\": \[ { \"id\":
  \"main-discovery-page\", \"name\": \"Discovery\", \"tab_icon_url\":
  \"discovery_icon\", \"url\":
  \"https://stage-feed.myjosh.in/page/discovery/main-discovery-page\",
  \"type\": \"DISCOVERY\" }, { \"id\": \"main-audio-page\", \"name\":
  \"Music\", \"tab_icon_url\": \"audio_icon\", \"url\":
  \"https://stage-feed.myjosh.in/page/audio/main-audio-page\", \"type\":
  \"AUDIO\" } \], \"bookmark_webview_url\":
  \"https://stage-share.myjosh.in/webview/bookmarks\",
  \"game_center_url\":
  \"https://stage-feed.myjosh.in/page_collection/game/main-game-page\",
  \"global_leaderboard_url\":
  \"https://stage-api.myjosh.in/apij/leaderboard/global\",
  \"extended_radius_msg\": \"No videos available for the selected
  location. Showing videos from nearby areas\",
  \"syncRewardIntervalTime\": 30, \"bloomFilterSyncIntervalTime\": 3,
  \"bloomFilterMaxFiles\": 2, \"bloomFilterRenewalSize\": 100,
  \"is_user_rewards_enabled\": true,
  \"wokenUpServiceForegroundNotificationDuration\": 5000,
  \"api_sequencing_config\": { \"api_sequencing_max_delay_ms\": 180000,
  \"api_hit_interval_time_ms\": 4000, \"fl_api_hit_interval_time_ms\":
  2000, \"delay_max_video_count\": 10,
  \"delay_cache_api_max_video_count\": 2, \"delay_after_handshake\":
  3000 }, \"notification_filters\": { \"available_filters\": \[ {
  \"label\": \"All\", \"isDefault\": \"true\", \"params\": { \"filter\":
  \"\" } }, { \"label\": \"Social\", \"params\": { \"filter\":
  \"SOCIAL\" } }, { \"label\": \"Content\", \"params\": { \"filter\":
  \"CONTENT\" } } \], \"notification_filters_heading\": \"Filter
  notifications by\" }, \"wakeUpPartnerInformation\": {
  \"minimumBatteryRequired\": 15, \"partnerPackages\": \[ {
  \"packageName\": \"com.eterno\", \"action\":
  \"com.eterno.intent.woken_up_service_start\",
  \"foregroundServiceSupport\": true, \"wakeupsections\": \[
  \"Notification\", \"Deeplink\", \"Splash\", \"App Controller\" \],
  \"dndStartTime\": 82800, \"dndEndTime\": 21300, \"wakeDelay\":
  86400000, \"disabledManufacturer\": \[\] }, { \"packageName\":
  \"com.newsdistill.mobile\", \"action\":
  \"com.newsdistill.mobile.intent.ACTION_WAKEUP\",
  \"foregroundServiceSupport\": true, \"wakeupsections\": \[
  \"Notification\", \"Deeplink\", \"Splash\", \"App Controller\" \],
  \"dndStartTime\": 82800, \"dndEndTime\": 21300, \"wakeDelay\":
  86400000, \"disabledManufacturer\": \[\] } \] },
  \"deviceWakeUpConfiguration\": { \"minimumBatteryRequired\": 15,
  \"dndStartTime\": 82800, \"dndEndTime\": 21300, \"wakeDelay\":
  86400000 }, \"appsflyer_events\": { \"C2\": 180, \"C3\": 180, \"C4\":
  180, \"C5\": 180, \"C6\": 180, \"C7\": 180, \"C8\": 180, \"C9\": 180,
  \"C10\": 180, \"C11\": 180, \"C12\": 540, \"C13\": 540, \"C14\": 540,
  \"C15\": 540, \"C16\": 1000, \"C17\": 1, \"C18\": 1, \"C19\": 180,
  \"C20\": 180, \"C22\": 540, \"C23\": 540, \"C24\": 540, \"C25\": 540,
  \"C26\": 540, \"C27\": 180, \"C28\": 180, \"C29\": 180, \"C30\": 180,
  \"C31\": 180, \"C32\": 180, \"C33\": 180, \"C34\": 180, \"C35\": 180,
  \"C36\": 180, \"C37\": 180, \"C38\": 180, \"C39\": 180, \"C40\": 180,
  \"C41\": 180, \"C42\": 180, \"C43\": 180, \"C44\": 180, \"C45\": 180,
  \"C46\": 180, \"C47\": 180, \"C48\": 180, \"C49\": 180, \"C50\": 180
  }, \"wa_status_sent_config\": \[ { \"min_version\": 30,
  \"max_version\": 2147483647, \"enable\": true, \"path_wa_status\":
  \"/Android/media/com.whatsapp/WhatsApp/Media/.Statuses\",
  \"path_wa_sent_video\":
  \"/Android/media/com.whatsapp/WhatsApp/Media/WhatsApp Video/Sent\",
  \"path_wa_sent_image\":
  \"/Android/media/com.whatsapp/WhatsApp/Media/WhatsApp Images/Sent\" },
  { \"min_version\": 0, \"max_version\": 29, \"enable\": true,
  \"path_wa_status\": \"WhatsApp/Media/.Statuses\",
  \"path_wa_sent_video\": \"WhatsApp/Media/WhatsApp Video/Sent\",
  \"path_wa_sent_image\": \"WhatsApp/Media/WhatsApp Images/Sent\" } \],
  \"myelin_config\": { \"enable\": true, \"disable_for_verified\": \[
  \"k\", \"m\", \"l\" \], \"sync_time\": 86400000, \"quality\": {
  \"fast\": \"average\", \"good\": \"average\", \"average\": \"average\"
  } }, \"pullNotificationConfig\": { \"pull_notifications_enabled\":
  true, \"firstTimePullDelay\": 120 }, \"lp_gotosetting_dialog_config\":
  { \"lp_gotosetting_dialog_title\": \"Allow Josh to access this
  device's location?\", \"lp_gotosetting_dialog_desc\": \"This will help
  you reach a more relevant audience &amp; gain followers, Please go to
  settings and allow location permission\",
  \"lp_gotosetting_dialog_pos_action\": \"Go To Settings\",
  \"lp_gotosetting_dialog_neg_action\": \"Later\",
  \"lp_gotosetting_dialog_show_after_x_post\": 4 },
  \"compilation_rules\": { \"default\": 720, \"resolutions\": \[ {
  \"max\": 2147483647, \"min\": 2048, \"result\": 2048 }, { \"max\":
  2047, \"min\": 1024, \"result\": 1024 }, { \"max\": 1023, \"min\":
  641, \"result\": 720 }, { \"max\": 640, \"min\": 481, \"result\": 640
  }, { \"max\": 480, \"min\": 361, \"result\": 480 }, { \"max\": 360,
  \"min\": 1, \"result\": 360 } \] }, \"data_saver_cache_config\": {
  \"cache_offline_directory_max_size_in_mb\": 100,
  \"cache_prefetch_directory_max_size_in_mb\": 200,
  \"cache_directory_max_size_in_mb\": 100, \"clear_session_data\":
  false, \"recommended_profile\": \"average\",
  \"enable_notification_prefetch\": true,
  \"min_cache_item_to_fetch_api\": 5, \"session_start_config\": {
  \"slow\": { \"from_offline_back_to_back\": 5 }, \"average\": {
  \"from_offline_back_to_back\": 3 }, \"good\": {
  \"from_offline_back_to_back\": 2 }, \"fast\": {
  \"from_offline_back_to_back\": 2 }, \"veryfast\": {
  \"from_offline_back_to_back\": 2 } }, \"prefetch_download_config\": {
  \"disable_cache\": false, \"prefetch_download_count_config\": {
  \"slow\": { \"no_of_videos\": 3, \"min_cache_percentage_ofl_to_onl\":
  100 }, \"average\": { \"no_of_videos\": 3,
  \"min_cache_percentage_ofl_to_onl\": 80 }, \"good\": {
  \"no_of_videos\": 3, \"min_cache_percentage_ofl_to_onl\": 60 },
  \"fast\": { \"no_of_videos\": 3, \"min_cache_percentage_ofl_to_onl\":
  40 }, \"veryfast\": { \"no_of_videos\": 3,
  \"min_cache_percentage_ofl_to_onl\": 25 } } },
  \"offline_download_config\": { \"sort_type\": \"recency\",
  \"disable_cache\": true, \"global_cache_ttl_days\": 15,
  \"max_cache_item\": 10, \"recommended_video_quality\": \"good\",
  \"ucq_download_config\": { \"average\": { \"exit\": 0, \"minimise\":
  0, \"notification\": 0 }, \"fast\": { \"exit\": 0, \"minimise\": 0,
  \"notification\": 0 }, \"slow\": { \"exit\": 0, \"minimise\": 0,
  \"notification\": 0 }, \"good\": { \"exit\": 0, \"minimise\": 0,
  \"notification\": 0 }, \"veryfast\": { \"exit\": 0, \"minimise\": 0,
  \"notification\": 0 } }, \"cache_api_sync_time_secs\": 86400,
  \"app_inactivity_duration_days\": 10 }, \"buffer_threshold_config\": {
  \"average\": { \"organic\": {
  \"buffer_threshold_initial_videos_secs\": 1,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } },
  \"fast\": { \"organic\": { \"buffer_threshold_initial_videos_secs\":
  1, \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } },
  \"slow\": { \"organic\": { \"buffer_threshold_initial_videos_secs\":
  1, \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } },
  \"good\": { \"organic\": { \"buffer_threshold_initial_videos_secs\":
  1, \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } },
  \"veryfast\": { \"organic\": {
  \"buffer_threshold_initial_videos_secs\": 1,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } } } },
  \"postLangMapping\": \[ { \"languageGroup\": \[ \"na\" \], \"values\":
  \[ \"hi\", \"en\", \"te\", \"ta\", \"ml\", \"kn\", \"mr\", \"gj\",
  \"bn\", \"or\", \"pa\", \"bh\" \] }, { \"languageGroup\": \[ \"hi\",
  \"mr\", \"pa\", \"gj\", \"bh\", \"or\", \"bn\" \], \"values\": \[
  \"hi\", \"mr\", \"pa\", \"gj\", \"bh\", \"or\", \"bn\", \"en\",
  \"te\", \"ta\", \"ml\", \"kn\" \] }, { \"languageGroup\": \[ \"te\",
  \"ta\", \"ml\", \"kn\" \], \"values\": \[ \"te\", \"ta\", \"ml\",
  \"kn\", \"hi\", \"en\", \"mr\", \"pa\", \"gj\", \"bh\", \"or\", \"bn\"
  \] } \], \"uploadShareConfig\": { \"shareChannels\": \[ { \"pkgName\":
  \"com.twitter.android\", \"iconUrl\": \"twitter\", \"name\":
  \"TWITTER\" }, { \"pkgName\": \"com.instagram.android\", \"iconUrl\":
  \"instagram\", \"name\": \"INSTAGRAM\" }, { \"pkgName\":
  \"com.facebook.katana\", \"iconUrl\": \"facebook\", \"name\":
  \"FACEBOOK\" }, { \"pkgName\": \"com.whatsapp\", \"iconUrl\":
  \"whatsapp\", \"name\": \"WHATSAPP\" } \], \"initialPollingDelayMs\":
  5000, \"pollingDelayMs\": 5000, \"maxPollingAttempts\": 10,
  \"shareNudgeCount\": 7, \"delaySharePromptHideMs\": 3000,
  \"delayPIPSuccessHideMs\": 5000 }, \"profileBlockedConfig\": {
  \"pb_config_title\": \"Profile Blocked!\", \"pb_config_subtitle\":
  \"This profile has been blocked due to violation of community
  guidelines.\", \"pb_config_cta\": \"Learn more\",
  \"pb_config_cta_link\":
  \"https://stage-share.myjosh.in/help/community-violation-guidelines\",
  \"pb_config_subtitle_dialog\": \"You cannot post a video\",
  \"pb_config_cta_neg_dialog\": \"Dismiss\" },
  \"fpv_profile_quality_config\": \[ { \"network_quality\":
  \"veryfast\", \"profile_quality\": \"veryfast\" }, {
  \"network_quality\": \"fast\", \"profile_quality\": \"veryfast\" }, {
  \"network_quality\": \"good\", \"profile_quality\": \"veryfast\" }, {
  \"network_quality\": \"average\", \"profile_quality\": \"good\" }, {
  \"network_quality\": \"slow\", \"profile_quality\": \"average\" } \],
  \"fpv_quality_nudge_config\": { \"network_quality\": \"average\",
  \"message\": \"Slow Internet! Playing Video in Low Quality\",
  \"duration\": 3000, \"per_session_count\": 1 }, \"quality_mapping\":
  \[ { \"network_quality\": \"veryfast\", \"profile_quality\": \"fast\"
  }, { \"network_quality\": \"fast\", \"profile_quality\": \"fast\" }, {
  \"network_quality\": \"good\", \"profile_quality\": \"good\" }, {
  \"network_quality\": \"average\", \"profile_quality\": \"average\" },
  { \"network_quality\": \"slow\", \"profile_quality\": \"slow\" } \],
  \"cache_config\": { \"cache_offline_directory_max_size_in_mb\": 200,
  \"cache_prefetch_directory_max_size_in_mb\": 250,
  \"cache_directory_max_size_in_mb\": 100, \"clear_session_data\":
  false, \"min_cache_item_to_fetch_api\": 5, \"hard_start_config\": {
  \"disableHardStart\": true, \"file_download_percentage\": 100,
  \"download_high_bitrate_variant\": true,
  \"min_stream_download_on_average_network\": 2,
  \"min_stream_download_on_fast_network\": 2,
  \"min_stream_download_on_good_network\": 2,
  \"min_stream_download_on_slow_network\": 2 },
  \"session_start_config\": { \"slow\": { \"from_offline_back_to_back\":
  3 }, \"average\": { \"from_offline_back_to_back\": 3 }, \"good\": {
  \"from_offline_back_to_back\": 3 }, \"fast\": {
  \"from_offline_back_to_back\": 3 }, \"veryfast\": {
  \"from_offline_back_to_back\": 3 } }, \"prefetch_download_config\": {
  \"disable_cache\": false, \"prefetch_download_count_config\": {
  \"slow\": { \"no_of_videos\": 3, \"min_cache_percentage_ofl_to_onl\":
  100 }, \"average\": { \"no_of_videos\": 3,
  \"min_cache_percentage_ofl_to_onl\": 85 }, \"good\": {
  \"no_of_videos\": 5, \"min_cache_percentage_ofl_to_onl\": 70 },
  \"fast\": { \"no_of_videos\": 2, \"min_cache_percentage_ofl_to_onl\":
  50 }, \"veryfast\": { \"no_of_videos\": 2,
  \"min_cache_percentage_ofl_to_onl\": 50 } } },
  \"offline_download_config\": { \"sort_type\": \"recency\",
  \"disable_cache\": false, \"global_cache_ttl_days\": 15,
  \"max_cache_item\": 40, \"recommended_video_quality\": \"good\",
  \"ucq_download_config\": { \"average\": { \"exit\": 2, \"minimise\":
  2, \"notification\": 2 }, \"fast\": { \"exit\": 2, \"minimise\": 2,
  \"notification\": 2 }, \"slow\": { \"exit\": 2, \"minimise\": 2,
  \"notification\": 2 }, \"good\": { \"exit\": 2, \"minimise\": 2,
  \"notification\": 2 }, \"veryfast\": { \"exit\": 2, \"minimise\": 2,
  \"notification\": 2 } }, \"cache_api_sync_time_secs\": 86400,
  \"app_inactivity_duration_days\": 10 }, \"buffer_threshold_config\": {
  \"average\": { \"organic\": {
  \"buffer_threshold_initial_videos_secs\": 1,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } },
  \"fast\": { \"organic\": { \"buffer_threshold_initial_videos_secs\":
  1, \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } },
  \"slow\": { \"organic\": { \"buffer_threshold_initial_videos_secs\":
  1, \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } },
  \"good\": { \"organic\": { \"buffer_threshold_initial_videos_secs\":
  1, \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } },
  \"veryfast\": { \"organic\": {
  \"buffer_threshold_initial_videos_secs\": 1,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 1,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 1 } } } },
  \"duet_config\": { \"camera_portrait_min_height_to_width\": { \"h\":
  16, \"w\": 9 }, \"camera_portrait_max_height_to_width\": { \"h\": 21,
  \"w\": 9 }, \"camera_landscape_min_width_to_height\": { \"h\": 8,
  \"w\": 9 }, \"camera_landscape_max_width_to_height\": { \"h\": 9,
  \"w\": 21 }, \"video_download_url\": \"\",
  \"create_and_edit_configs\": { \"duetable_config_for_verified\": {
  \"default_value\": \"OFF\", \"aspect_ratio\": {
  \"allow_for_portrait\": true, \"allow_for_square\": true,
  \"allow_for_landscape\": false }, \"video_source\": {
  \"camera_with_josh_library\": true, \"camera_without_josh_library\":
  true, \"gallery_with_josh_library\": true,
  \"gallery_without_josh_library\": true, \"duet\": false },
  \"video_source_v2\": \[ { \"srcType\": \"camera\", \"josh_library\":
  true, \"non_josh_library\": true }, { \"srcType\": \"gallery\",
  \"josh_library\": true, \"non_josh_library\": true }, { \"srcType\":
  \"multi_segment_camera\", \"josh_library\": true,
  \"non_josh_library\": true }, { \"srcType\":
  \"multi_segment_gallery\", \"josh_library\": true,
  \"non_josh_library\": true }, { \"srcType\":
  \"multi_segment_camera_gallery\", \"josh_library\": true,
  \"non_josh_library\": true }, { \"srcType\": \"external_did\",
  \"josh_library\": true, \"non_josh_library\": true }, { \"srcType\":
  \"external\", \"josh_library\": true, \"non_josh_library\": true }, {
  \"srcType\": \"duet\", \"josh_library\": true, \"non_josh_library\":
  true } \] }, \"duetable_config_for_nonverified\": { \"default_value\":
  \"OFF\", \"aspect_ratio\": { \"allow_for_portrait\": true,
  \"allow_for_square\": true, \"allow_for_landscape\": false },
  \"video_source\": { \"camera_with_josh_library\": true,
  \"camera_without_josh_library\": true, \"gallery_with_josh_library\":
  true, \"gallery_without_josh_library\": true, \"duet\": false },
  \"video_source_v2\": \[ { \"srcType\": \"camera\", \"josh_library\":
  true, \"non_josh_library\": true }, { \"srcType\": \"gallery\",
  \"josh_library\": true, \"non_josh_library\": true }, { \"srcType\":
  \"multi_segment_camera\", \"josh_library\": true,
  \"non_josh_library\": true }, { \"srcType\":
  \"multi_segment_gallery\", \"josh_library\": true,
  \"non_josh_library\": true }, { \"srcType\":
  \"multi_segment_camera_gallery\", \"josh_library\": true,
  \"non_josh_library\": true }, { \"srcType\": \"external_did\",
  \"josh_library\": true, \"non_josh_library\": true }, { \"srcType\":
  \"external\", \"josh_library\": true, \"non_josh_library\": true }, {
  \"srcType\": \"duet\", \"josh_library\": true, \"non_josh_library\":
  true } \] } } }, \"duet_video_volume_config\": {
  \"dueted_video_volume\": 20, \"recorded_video_volume\": 100 },
  \"fire_track_from_cache\": true, \"handshake_version\": \"470\",
  \"performance_analytics_enabled\": false, \"upload_duration\": 120,
  \"disable_error_event\": false, \"disable_slow_network_prompts\":
  false, \"speed_quality_map\": { \"100\": \"slow\", \"500\":
  \"average\", \"1000\": \"good\", \"10000\": \"fast\", \"50000\":
  \"veryfast\" }, \"record_duration\": 15, \"first_time_pull_delay\":
  300, \"first_chunk_request_params\": { \"cdn\": \"Y\", \"src\":
  \"app\" }, \"max_upload_size\": 200, \"upgrade\": \"LATEST\",
  \"rateConfig\": { \"enable\": true,
  \"preActivitySessionWaitTimeInSeconds\": 600,
  \"minNumberOfStoriesViewedPerSession\": 10, \"minNumberOfBooksRead\":
  4, \"maxNumberOfTimesToShowRateScreen\": 3,
  \"minNumberOfDaysToWaitShowingRateScreen\": 30,
  \"maxWaitDaysForNewUsersToShowRateScreen\": 7,
  \"minLaunchesForNewUsersToShowRateScreen\": 3,
  \"minNumberOfDaysUserToWaitAfterLastSeen\": 10,
  \"minNumberOfAppLaunchesToWaitAfterLastSeen\": 10 },
  \"maxHistoryCount\": 50, \"enable_reactions_api_hit\": true,
  \"max_recent_interaction_count\": 50,
  \"location_fetch_interval_in_seconds\": 86400,
  \"min_gap_between_app_update_prompt_secs\": 172800,
  \"video_views_in_session_for_update_prompt\": 5, \"permission\": {
  \"id\": 24, \"event\": \"appLaunch\", \"activity\": { \"type\":
  \"permission\", \"attributes\": { \"gapCount\": \"4\", \"permDesc\":
  \"Josh needs access to the following\", \"permTitle\": \"Permissions
  required\", \"openSettings\": \"Josh needs storage access to perform
  this action. To enable it, please visit your app settings.\",
  \"settingsAction\": \"Settings\", \"storagePermDesc\": \"We need this
  for critical features like downloading a video.\",
  \"locationPermDesc\": \"We need this to show you videos being posted
  by users around you.\", \"storagePermSubtitle\": \"Storage Access\",
  \"locationPermSubtitle\": \"Location Access\",
  \"permissionNegativeBtn\": \"LATER\", \"permissionPositiveBtn\":
  \"Allow\" } }, \"resource\": \"coolfie\", \"precondition\": {
  \"minItemsViewed\": 7, \"minTimeEngaged\": 0, \"maxNumberOfDisplay\":
  0, \"minNumberOfOccurences\": 5 } }, \"fire_comscore_from_cache\":
  true, \"max_notifications_in_tray\": 4, \"thumbnail_qualities\": {
  \"fast\": { \"quality\": \"h\", \"resolution\": 480 }, \"good\": {
  \"quality\": \"h\", \"resolution\": 480 }, \"slow\": { \"quality\":
  \"h\", \"resolution\": 480 }, \"average\": { \"quality\": \"h\",
  \"resolution\": 480 } }, \"default_notification_duration\": 120,
  \"max_upload_bitrate\": 1500, \"pull_notifications_enabled\": true,
  \"video_qualities\": { \"fast\": { \"quality\": \"h\", \"resolution\":
  480 }, \"good\": { \"quality\": \"h\", \"resolution\": 480 },
  \"slow\": { \"quality\": \"h\", \"resolution\": 480 }, \"average\": {
  \"quality\": \"h\", \"resolution\": 480 } },
  \"disable_firebase_perf\": false, \"google_play_url\": {
  \"share_video_text\": \"Download Josh for more videos like this!\",
  \"download_video_text\": \"Download Josh for more videos like this!\",
  \"download_live_stream_text\": \"Download Josh for more livestreams
  like this!\", \"share_google_play_url\":
  \"https://m.myjosh.in/6OaT/32e07bf\", \"setting_google_play_url\":
  \"https://m.myjosh.in/6OaT/568901e6\", \"download_google_play_url\":
  \"https://m.myjosh.in/6OaT/6d76ce25\", \"duet_share_text\": \"Create
  and watch amazing duets with %1\$s! \\n%2\$s \\nDownload Josh now to
  watch & even create more great videos like this!
  \\nhttps://play.google.com/store/apps/details?id=com.eterno.shortvideos\"
  }, \"default_notification_text\": \"Welcome to Josh! Check out the
  latest news in your preferred language.\",
  \"story_detail_error_page_url\":
  \"https://m.dailyhunt.in/webItem/errorPage.html\",
  \"share_floating_icon_type\": \"floatingIconBentArrow\",
  \"upload_format_list\": \[ \"3gp\", \"mp4\" \], \"nlfc_config\": {
  \"disable_nlfc\": false, \"min_time_spent_to_trigger\": 6000,
  \"min_time_spent_to_trigger_with_social\": 6000,
  \"min_percentage_completion\": 75,
  \"skip_nlfc_for_session_on_failure\": 3, \"min_offset_to_append\": 0
  }, \"moderationNsfwReportUrl\":
  \"https://stage-share.myjosh.in/report/machine-moderation/1\",
  \"moderationDuplicateReportUrl\":
  \"https://stage-share.myjosh.in/report/ownership-content/1\",
  \"joshCam1Config\": { \"licenseUrl\":
  \"https://stage-stream.myjosh.in/stream/stage-josh-content/joshCam1Config/license/android/20986-269-8619db07c55966e42c2f42acfa3e187d.lic\",
  \"licenseUrliOS\":
  \"https://stage-stream.myjosh.in/stream/stage-josh-content/joshCam1Config/license/ios/MeisheSDKLicense.lic\"
  }, \"sdkType\": \"JOSH_CAM1\", \"followersTabName\": \"Top Fans\",
  \"handshakeDefaultInterval\": 43200000, \"maxApiDelay\": 2000,
  \"maxErrorEventPerInterval\": 10, \"upload_duration_v2\": 60,
  \"min_upload_duration\": 5, \"max_recent_navigable_action_count\": 30,
  \"timerPeriodInSeconds\": 60, \"firstTimePullDelay\": 60,
  \"enable_whatsapp_share\": true, \"enable_video_download_on_share\":
  true, \"hit_firebase_event_once\": true, \"enableGzip_v2\": true,
  \"allowEmptyTitleInCreatePost\": false, \"is_firebase_event_enabled\":
  true, \"dev_error_for_2xxTo4xx_enabled\": false,
  \"location_prompt_for_max_time_count\": 3,
  \"location_prompt_after_max_post_count\": 0, \"video_resources\": {
  \"1\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/1?version=1\",
  \"2\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/2?version=19\",
  \"3\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/3?version=1\",
  \"4\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/4?version=1\",
  \"5\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/5?version=3\",
  \"6\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/6?version=1\",
  \"7\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/7?version=1\",
  \"8\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/8?version=1\",
  \"9\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/9?version=1\",
  \"10\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/10?version=1\",
  \"11\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/11?version=1\",
  \"12\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/12?version=1\",
  \"13\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/13?version=1\",
  \"14\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/14?version=11\",
  \"15\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/15?version=1\",
  \"16\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/16?version=1\",
  \"17\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/17?version=1\",
  \"24\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/24?version=1\",
  \"25\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/25?version=6\",
  \"26\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/26?version=4\",
  \"27\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/27?version=1\",
  \"28\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/28?version=4\",
  \"29\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/29?version=1\",
  \"30\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/30?version=2\",
  \"31\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/31?version=4\",
  \"32\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/32?version=1\",
  \"33\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/33?version=1\",
  \"34\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/34?version=2\",
  \"35\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/35?version=1\",
  \"36\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/36?version=1\",
  \"37\":
  \"https://stage-gateway.myjosh.in/api/v1/materialinfo/37?version=1\"
  }, \"following_sync_interval_in_seconds\": 86400,
  \"appsOnDeviceEnabled\": false, \"appsOnDeviceEnabledV2\": true,
  \"cleanupConfig\": { \"maxMusicDownloads\": 20,
  \"maxStickerDownloads\": 100 }, \"network_config\": {
  \"exo_weightage_double\": 0.8, \"network_weightage_double\": 2,
  \"sliding_percentile_percentile\": 0.5, \"bitrate_expression\": {
  \"id\": \"1\", \"formula\": \"(e\*0.8)+(n\*2)\" },
  \"bitrate_expression_v2\": { \"id\": \"3\", \"formula\": \"function
  f42(e,n){ \\n if(e\<n) return e\*0.8+n\*0.7; \\n else { var
  wa=e\*e/(e+n)+n\*n/(e+n); return Math.min(wa,e);};\\n};\" },
  \"bitrate_expression_exception\": { \"id\": \"2\", \"formula\":
  \"(e\*0.8)+(n\*0.7)\" }, \"lifetime_bitrate_capture_window_sec\":
  604800, \"coldstart_transition_threshold_sec\": 10,
  \"coldstart_network_provider_mapping\": \[ { \"network\": \"4G\",
  \"provider\": \"Jio 4G\", \"quality\": \"good\" }, { \"network\":
  \"4G\", \"provider\": \"airtel\", \"quality\": \"good\" }, {
  \"network\": \"4G\", \"provider\": \"Vi India\", \"quality\": \"good\"
  }, { \"network\": \"4G\", \"provider\": \"IND airtel\", \"quality\":
  \"good\" }, { \"network\": \"4G\", \"provider\": \"Vodafone IN\",
  \"quality\": \"good\" }, { \"network\": \"4G\", \"provider\":
  \"Airtel\", \"quality\": \"good\" }, { \"network\": \"4G\",
  \"provider\": \"Idea\", \"quality\": \"good\" }, { \"network\":
  \"4G\", \"provider\": \"JIO 4G\", \"quality\": \"good\" }, {
  \"network\": \"w\", \"provider\": \"Jio 4G\", \"quality\": \"fast\" },
  { \"network\": \"w\", \"provider\": \"airtel\", \"quality\": \"fast\"
  }, { \"network\": \"4G\", \"provider\": \"JIO\", \"quality\": \"good\"
  }, { \"network\": \"4G\", \"provider\": \"AIRTEL\", \"quality\":
  \"good\" }, { \"network\": \"3G\", \"provider\": \"Vi India\",
  \"quality\": \"average\", \"maxQuality\": \"average\" }, {
  \"network\": \"w\", \"provider\": \"Vi India\", \"quality\": \"fast\"
  }, { \"network\": \"4G\", \"provider\": \"VIL\", \"quality\": \"good\"
  }, { \"network\": \"4G\", \"provider\": \"Vodafone\", \"quality\":
  \"good\" }, { \"network\": \"w\", \"provider\": \"Vodafone IN\",
  \"quality\": \"fast\" }, { \"network\": \"w\", \"provider\": \"IND
  airtel\", \"quality\": \"fast\" }, { \"network\": \"2G\",
  \"provider\": \"airtel\", \"quality\": \"slow\", \"maxQuality\":
  \"slow\" }, { \"network\": \"4G\", \"provider\": \"Airtel \| airtel\",
  \"quality\": \"good\" }, { \"network\": \"4G\", \"provider\": \"IND
  AirTel\", \"quality\": \"good\" }, { \"network\": \"3G\",
  \"provider\": \"Vodafone IN\", \"quality\": \"average\",
  \"maxQuality\": \"average\" }, { \"network\": \"w\", \"provider\":
  \"Idea\", \"quality\": \"fast\" }, { \"network\": \"4G\",
  \"provider\": \"JIO 4G \| Jio 4G\", \"quality\": \"good\" }, {
  \"network\": \"4G\", \"provider\": \"AirTel\", \"quality\": \"good\"
  }, { \"network\": \"3G\", \"provider\": \"Idea\", \"quality\":
  \"average\", \"maxQuality\": \"average\" }, { \"network\": \"4G\",
  \"provider\": \"Vi India \| Vodafone IN\", \"quality\": \"good\" }, {
  \"network\": \"2G\", \"provider\": \"Vi India\", \"quality\":
  \"slow\", \"maxQuality\": \"slow\" }, { \"network\": \"w\",
  \"provider\": \"Airtel\", \"quality\": \"fast\" }, { \"network\":
  \"3G\", \"provider\": \"BSNL MOBILE\", \"quality\": \"average\",
  \"maxQuality\": \"average\" }, { \"network\": \"4G\", \"provider\":
  \"BSNL MOBILE\", \"quality\": \"good\" }, { \"network\": \"4G\",
  \"provider\": \"Vi India \| Idea\", \"quality\": \"good\" }, {
  \"network\": \"3G\", \"provider\": \"BSNL Mobile\", \"quality\":
  \"average\", \"maxQuality\": \"average\" }, { \"network\": \"4G\",
  \"provider\": \"BSNL Mobile\", \"quality\": \"good\" }, { \"network\":
  \"4G\", \"provider\": \"IDEA\", \"quality\": \"good\" }, {
  \"network\": \"w\", \"provider\": \"JIO 4G\", \"quality\": \"fast\" },
  { \"network\": \"w\", \"provider\": \"BSNL MOBILE\", \"quality\":
  \"fast\" }, { \"network\": \"4G\", \"provider\": \"Jio\", \"quality\":
  \"good\" }, { \"network\": \"4G\", \"provider\": \"Airtel_BH\",
  \"quality\": \"good\" }, { \"network\": \"w\", \"provider\": \"BSNL
  Mobile\", \"quality\": \"fast\" }, { \"network\": \"2G\",
  \"provider\": \"Idea\", \"quality\": \"slow\", \"maxQuality\":
  \"slow\" }, { \"network\": \"2G\", \"provider\": \"Vodafone IN\",
  \"quality\": \"slow\", \"maxQuality\": \"slow\" }, { \"network\":
  \"4G\", \"provider\": \"!dea\", \"quality\": \"good\" }, {
  \"network\": \"3G\", \"provider\": \"CellOne\", \"quality\":
  \"average\", \"maxQuality\": \"average\" }, { \"network\": \"4G\",
  \"provider\": \"JIO4G\", \"quality\": \"good\" }, { \"network\":
  \"4G\", \"provider\": \"Airtel Stay Home\", \"quality\": \"good\" }, {
  \"network\": \"2G\", \"provider\": \"Airtel\", \"quality\": \"slow\",
  \"maxQuality\": \"slow\" }, { \"network\": \"w\", \"provider\":
  \"JIO\", \"quality\": \"fast\" }, { \"network\": \"2G\", \"provider\":
  \"IND airtel\", \"quality\": \"slow\", \"maxQuality\": \"slow\" }, {
  \"network\": \"0\", \"provider\": \"Jio 4G\", \"quality\": \"fast\",
  \"maxQuality\": \"fast\" }, { \"network\": \"3G\", \"provider\":
  \"airtel\", \"quality\": \"average\", \"maxQuality\": \"average\" }, {
  \"network\": \"WiFi\", \"provider\": \"AirTel\", \"quality\": \"fast\"
  }, { \"network\": \"4G\", \"provider\": \"unknown\", \"quality\":
  \"good\" }, { \"network\": \"WiFi\", \"provider\": \"unknown\",
  \"quality\": \"fast\" }, { \"network\": \"WiFi\", \"provider\":
  \"Jio\", \"quality\": \"fast\" }, { \"network\": \"4G\", \"provider\":
  \"CellOne\", \"quality\": \"good\" }, { \"network\": \"3G\",
  \"provider\": \"!dea\", \"quality\": \"average\", \"maxQuality\":
  \"average\" }, { \"network\": \"w\", \"provider\": \"VIL\",
  \"quality\": \"fast\" }, { \"network\": \"4G\", \"provider\":
  \"Ind-Jio\", \"quality\": \"good\" }, { \"network\": \"w\",
  \"provider\": \"Vi India \| Vodafone IN\", \"quality\": \"fast\" }, {
  \"network\": \"3G\", \"provider\": \"VIL\", \"quality\": \"average\",
  \"maxQuality\": \"average\" }, { \"network\": \"4G\", \"provider\":
  \"Emergency calls only\", \"quality\": \"good\" }, { \"network\":
  \"2G\", \"provider\": \"Jio 4G\", \"quality\": \"slow\",
  \"maxQuality\": \"slow\" }, { \"network\": \"3G\", \"provider\":
  \"Vodafone\", \"quality\": \"average\", \"maxQuality\": \"average\" },
  { \"network\": \"3G\", \"provider\": \"Jio 4G\", \"quality\":
  \"average\", \"maxQuality\": \"average\" }, { \"network\": \"w\",
  \"provider\": \"AIRTEL\", \"quality\": \"fast\" }, { \"network\":
  \"4G\", \"provider\": \"No service\", \"quality\": \"good\" }, {
  \"network\": \"w\", \"provider\": \"Vi India \| Idea\", \"quality\":
  \"fast\" }, { \"network\": \"0\", \"provider\": \"airtel\",
  \"quality\": \"fast\", \"maxQuality\": \"fast\" }, { \"network\":
  \"w\", \"provider\": \"Vodafone\", \"quality\": \"fast\" }, {
  \"network\": \"w\", \"provider\": \"Any\", \"quality\": \"fast\" }, {
  \"network\": \"4G\", \"provider\": \"Any\", \"quality\": \"good\" }, {
  \"network\": \"3G\", \"provider\": \"Any\", \"quality\": \"average\",
  \"maxQuality\": \"average\" }, { \"network\": \"2G\", \"provider\":
  \"Any\", \"quality\": \"slow\", \"maxQuality\": \"slow\" }, {
  \"network\": \"Any\", \"provider\": \"Any\", \"quality\": \"good\",
  \"maxQuality\": \"good\" } \], \"exo_sliding_percentile_max_weight\":
  1000 }, \"speed_quality_map_v2\": { \"200\": \"slow\", \"2000\":
  \"average\", \"6000\": \"good\", \"8000\": \"fast\", \"16000\":
  \"veryfast\" }, \"cameraProperties\": { \"videoCaptureResolution\":
  \"EXTREMELY_HIGH\", \"recordBitrate\": \"3000\", \"fps\": \"30\",
  \"audioSampleRate\": \"44100\", \"autoFocus\": \"Y\",
  \"autoExposure\": \"Y\", \"sharpness\": \"Y\", \"beautify\": \"Y\",
  \"Intensity\": \"0.2\", \"videoStabilization\": \"MODE_SUPER\",
  \"continuousFocus\": \"Y\", \"zoom\": \"Y\", \"maxZoom\": \"99\",
  \"bitDepth\": \"8\", \"compileBitrate\": \"3000\", \"audioBitrate\":
  \"3000\", \"losslessAudio\": \"true\", \"encoderPreset\": \"MEDIUM\",
  \"encodedCRF\": \"21\", \"encoderName\": \"H.265\",
  \"encoderProfile\": \"high\", \"HDR\": \"st2084\" },
  \"max_consumed_cache_items_count\": 30, \"attRules\": {
  \"enableATTPrompt\": true, \"attPromptConfig\": {
  \"minInstallLaunchCount\": 2, \"minUpgradeLaunchCount\": 3,
  \"coolOffLaunchCount\": 2, \"maxAttemptCount\": 30, \"title\":
  \"Personalized Ads\", \"message\": \"Josh would like permission to
  serve personalized ads to you\" } }, \"uploadConfig\": {
  \"resumableUploadsEnabled\": true, \"failureAutoRetryThreshold\": 5,
  \"connectTimeout\": 60000, \"readTimeout\": 60000, \"writeTimeout\":
  60000, \"tusChunkSize\": 1048576, \"tusRequestPayloadSize\": -1,
  \"tusExtendedRetryDelays\": \[ 10000, 10000, 10000, 10000, 20000 \],
  \"tusNormalRetryDelays\": \[ 500, 1000, 2000, 3000 \] },
  \"quicHints\": \[ { \"host\": \"stage-stream.myjosh.in\", \"port\":
  443, \"alternatePort\": 443 } \], \"bookmarkConfig\": {
  \"musicTrimNudgeCount\": 5, \"bookMarkNudgeCount\": 5,
  \"bookmarkSyncMinimumGap\": 86400000, \"bookmarkFetchItemLimit\": 10,
  \"bookmarkItemMaxLimit\": 500 }, \"reactivate_account_config\": {
  \"temporarily_deactivated_title\": \"We missed you\...\",
  \"temporarily_deactivated_sub_title\": \"Tap the button below to
  reactivate\\nyour account\", \"temporarily_deactivated_cta_text\":
  \"Reactivate Account\", \"permanently_deactivated_title\": \"This
  account has been permanently deleted\",
  \"permanently_deactivated_sub_title\": \"To use Josh, create a new
  account.\", \"permanently_deactivated_cta_text\": \"Create New
  Account\" }, \"createPostConfig\": { \"noOfHashTagAllowed\": 5,
  \"noOfUserHandleAllowed\": 3, \"maxNumKeywords\": 5 }, \"csConfig\": {
  \"enabled\": true, \"frequencyTimeMS\": 86400000, \"bucketSizeNew\":
  2000 }, \"encryption\": { \"version\": 1, \"key\":
  \"LS0tLS1CRUdJTiBQVUJMSUMgS0VZLS0tLS0KTUlHZk1BMEdDU3FHU0liM0RRRUJBUVVBQTRHTkFEQ0JpUUtCZ1FDWkd2L1dncXo1OEhjOURMZUFObHRmNFVJMwp3Vkoyb0xJYzZEemRheFdaTXRSVkYzTGYySlFSZURQMTRsKzNYUGdXaC9lVlFBU1Z3QTZKaUYxemw1WXhJS1ovCmppc2NEaFRDS25idmE1dTdrYjFMb0FUTlFKQlZtZGhSOFVZbWc3dUZWMnJTVUg3UEJ3VytyLzhKcm9sOXA1SGEKckIxVlBPMEtIR0YyZ2JNS2V3SURBUUFCCi0tLS0tRU5EIFBVQkxJQyBLRVktLS0tLQo=\"
  }, \"profile_wizard_config\": { \"completeMsgDismissTimeInMills\":
  3000, \"setUpProfileMsgShowTimeInDays\": 360 },
  \"snapchatLogoutIconUrl\":
  \"https://sdk.bitmoji.com/me/sticker/#AVATAR_ID#/204d8f0d-50e5-4db5-a810-f6525a68dc39\",
  \"fileUploads\": { \"twitter\":
  \"https://stage-stream.myjosh.in/stream/stage-josh-content/josh_version_content/JOSH_STATIC_CONFIG/Twitter-Logo.webp\",
  \"instagram\":
  \"https://stage-stream.myjosh.in/stream/stage-josh-content/josh_version_content/JOSH_STATIC_CONFIG/Instagram-Logo.webp\",
  \"facebook\":
  \"https://stage-stream.myjosh.in/stream/stage-josh-content/josh_version_content/JOSH_STATIC_CONFIG/Facebook-Logo.webp\",
  \"whatsapp\":
  \"https://stage-stream.myjosh.in/stream/stage-josh-content/josh_version_content/JOSH_STATIC_CONFIG/Whatsapp-Logo.webp\",
  \"uploads\":
  \"https://stage-stream.myjosh.in/stream/stage-josh-content/josh_version_content/JOSH_STATIC_CONFIG/VmlkZW8=.png\",
  \"trending\":
  \"https://stage-stream.myjosh.in/stream/stage-josh-content/josh_version_content/JOSH_STATIC_CONFIG/VHJlbmRpbmdfMQ==.png\",
  \"likes\":
  \"https://stage-stream.myjosh.in/stream/stage-josh-content/josh_version_content/JOSH_STATIC_CONFIG/TGlrZV8x.png\",
  \"drafts\":
  \"https://stage-stream.myjosh.in/stream/stage-josh-content/josh_version_content/JOSH_STATIC_CONFIG/RHJhZnRfMQ==.png\",
  \"tagged\":
  \"https://stage-stream.myjosh.in/stream/stage-josh-content/josh_version_content/JOSH_STATIC_CONFIG/TWVudGlvbl8x.png\",
  \"discovery_icon\":
  \"https://stage-stream.myjosh.in/stream/stage-josh-content/josh_version_content/JOSH_STATIC_CONFIG/ZGlzY292ZXJ5.png\",
  \"audio_icon\":
  \"https://stage-stream.myjosh.in/stream/stage-josh-content/josh_version_content/JOSH_STATIC_CONFIG/bXVzaWM=.png\",
  \"hello\":
  \"https://stage-stream.myjosh.in/stream/stage-josh-content/josh_version_content/JOSH_STATIC_CONFIG/YmdfY3VzdG9t.png\",
  \"trending_icon\":
  \"https://stage-stream.myjosh.in/stream/stage-josh-content/josh_version_content/JOSH_STATIC_CONFIG/VHJlbmRpbmc=.png\",
  \"photos\":
  \"https://stage-stream.myjosh.in/stream/stage-josh-content/josh_version_content/JOSH_STATIC_CONFIG/UGhvdG9fMQ==.png\",
  \"social\":
  \"https://stage-stream.myjosh.in/stream/stage-josh-content/josh_version_content/JOSH_STATIC_CONFIG/U29jaWFsXzE=.png\",
  \"uploads_selected\":
  \"https://stage-stream.myjosh.in/stream/stage-josh-content/josh_version_content/JOSH_STATIC_CONFIG/Sm9zaA==.png\",
  \"likes_selected\":
  \"https://stage-stream.myjosh.in/stream/stage-josh-content/josh_version_content/JOSH_STATIC_CONFIG/Sm9zaEAyeF8=.png\",
  \"trending_selected\":
  \"https://stage-stream.myjosh.in/stream/stage-josh-content/josh_version_content/JOSH_STATIC_CONFIG/Sm9zaEAyeA==.png\",
  \"social_selected\":
  \"https://stage-stream.myjosh.in/stream/stage-josh-content/josh_version_content/JOSH_STATIC_CONFIG/TmV3cy0xLjU=.png\",
  \"tagged_selected\":
  \"https://stage-stream.myjosh.in/stream/stage-josh-content/josh_version_content/JOSH_STATIC_CONFIG/QA==.png\",
  \"photos_selected\":
  \"https://stage-stream.myjosh.in/stream/stage-josh-content/josh_version_content/JOSH_STATIC_CONFIG/Sm9zaA==.png\",
  \"drafts_selected\":
  \"https://stage-stream.myjosh.in/stream/stage-josh-content/josh_version_content/JOSH_STATIC_CONFIG/UGFwZXI=.png\",
  \"gifting_icon_url\":
  \"https://stage-stream.myjosh.in/stream/stage-josh-content/josh_version_content/JOSH_STATIC_CONFIG/Z2lmdF9pY29u.png\",
  \"tipping_icon_url\":
  \"https://stage-stream.myjosh.in/stream/stage-josh-content/josh_version_content/JOSH_STATIC_CONFIG/Z2lmdF9pY29u.png\"
  } } } }

- **Request Method and URL:**

  GET : https://qa-gateway.coolfie.io/api/v1/version/entity/add

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/version/entity/add\' \\

  \--header \'Content-Type: application/json\' \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 } }

- **Request Method and URL:**

  POST :
  https://qa-gateway.coolfie.io/api/v1/version/entity/cache/trigger?versionEntity=DEVICE_LIST

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/version/entity/cache/trigger?versionEntity=DEVICE_LIST\'
  \\

  \--header \'Content-Type: application/json; charset=UTF-8\' \\

  \--header \'coolfie-debug-info:
  appVersion=4.9.0&osVersion=10&clientId=bda58994-7e91&androidId=4cb6f567da56f774&installSource=CoolfieHome&user_lang=en&nav_lang=hi&width=1080&height=2034\'
  \\

  \--header \'content-uuids-seen:
  d02658a7-d9a0-4a71-9d49-1be017e64483,c6c9d78e-00e7-4ca6-908a-a1962fc45cef,ace416ad-6cf5-4134-94d0-8eface2fc965,87292574-0ae4-4670-ac11-98ac41f6f6fa,32b9ab35-97a7-4b88-99d3-3d74e6f34b62\'
  \\

  \--header \'history-policy: 2\' \\

  \--header \'user-uuid;\' \\

  \--header \'auth-token;\' \\

  \--header \'install-referrer;\' \\

  \--header \'User-Agent: Dalvik/2.1.0 (Linux; U; Android 10; ONEPLUS
  A5010 Build/QKQ1.191014.012)\' \\

  \--data-raw \'{

  \"android_id\": \"4cb6f567da56f774\",

  \"appOpenEvent\": false,

  \"client_info\": {

  \"app_language\": \"hi\",

  \"app_version\": \"4.4.0\",

  \"brand\": \"Josh\",

  \"default_notification_lang\": \"hi\",

  \"device\": \"android\",

  \"gaid\": \"\",

  \"gaid_opt_out_status\": false,

  \"height\": 2034,

  \"manufacturer\": \"OnePlus\",

  \"model\": \"ONEPLUS A5010\",

  \"os_version\": \"10\",

  \"width\": 1080,

  \"android_id\": \"4cb6f567da56f774\",

  \"client_id\": \"1231\",

  \"udid\": \"4cb6f567da56f774\"

  },

  \"connection_info\": {

  \"cellid\": \"&cellid=\-\-\-\-\-\--Gsm\",

  \"connection\": \"w\"

  },

  \"handshake_version\": \"421\",

  \"install_type\": \"NA\",

  \"location_info\": {

  \"is_GPS_location\": false,

  \"lat\": \"\",

  \"lon\": \"\"

  },

  \"packageName\": \"com.eterno.shortvideos\",

  \"referrer\": \"utm_source=CoolfieHome\",

  \"isCronetEnabled\": true

  }\'

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 } }

- **Request Method and URL:**

  POST : https://qa-gateway.coolfie.io/api/v1/upgrade/keyvalue

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/upgrade/keyvalue\' \\

  \--header \'Content-Type: application/json\' \\

  \--data-raw \'{

  \"key\": \"reward.anonymous\",

  \"value\":
  \"{\\\"activitySync\\\":\\\"abc/dfe\\\",\\\"rewardTrigger\\\":\\\"cdd/dww\\\"}\"

  }\'

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 } }

- **Request Method and URL:**

  POST : https://qa-gateway.coolfie.io/api/v1/upgrade/anonymous

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/upgrade/anonymous\' \\

  \--header \'Content-Type: application/json\' \\

  \--data-raw \'{

  \"key\": \"reward.anonymous.urls\",

  \"value\":
  \"{\\\"redeem_voucher\\\":\\\"/voucher/redeemVoucher\\\",\\\"set_active_pair\\\":\\\"/reward/setActivePair\\\",\\\"eligible_vouchers\\\":\\\"/voucher/store\\\",\\\"token_generate\\\":\\\"/reward/generateToken\\\",\\\"token_refresh\\\":\\\"/reward/tokenRefresh\\\",\\\"pwa_landing_page\\\":\\\"/reward/landingPage\\\",\\\"reward_trigger\\\":\\\"/reward/earnMilestoneJems\\\",\\\"pwa_static_links\\\":\\\"/reward/staticLink\\\",\\\"pwa_today_tab\\\":\\\"/reward/todayTab\\\",\\\"user_vouchers\\\":\\\"/voucher/userVouchers\\\",\\\"pwa_milestone_tab\\\":\\\"/reward/milestoneTab\\\",\\\"synced_user_activities\\\":\\\"/activities/getListByUser\\\",\\\"register_device\\\":\\\"/reward/registerDevice\\\",\\\"user_activities_sync\\\":\\\"/activities/userSync\\\",\\\"user_bloomfilter_sync\\\":\\\"/activities/userBloomfilterSync\\\",\\\"synced_user_bloomfilter\\\":\\\"/activities/getBFByUser\\\"}\"

  }\'

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 } }

- **Request Method and URL:**

  GET : http://localhost:8080/api/v1/materialinfo/2?version=93

- **Curl Request:**

  curl \--location \--request GET
  \'http://localhost:8080/api/v1/materialinfo/2?version=93\' \\

  \--header \'Content-Type: application/json\'

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 } }

- **Request Method and URL:**

  POST : https://qa-gateway.coolfie.io/api/v1/material/2/version/update

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/material/2/version/update\'\
  \--header \'Content-Type: application/json\'

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 } }

- **Request Method and URL:**

  GET : https://qa-gateway.coolfie.io/api/v1/material/2/amritsar/info

- **Curl Request:**

  curl \--location \--request GET
  \'<https://qa-gateway.coolfie.io/api/v1/material/2/amritsar/info'>

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { \"id\": \"amritsar\",
  \"category\": 0, \"name\": \"amritsar\", \"desc\": \"\", \"tags\":
  \"\", \"version\": 0, \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/amritsar.videofx\",
  \"packageSize\": 0, \"supportedAspectRatio\": 0, \"idx\": 0,
  \"filterType\": \"SIMPLE_FILTER\", \"userAction\": \"\",
  \"assetType\": \"FILTER\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=amritsar\",
  \"pass_through\": \"EFFECT\" } }

- **Request Method and URL:**

  GET :
  https://qa-gateway.coolfie.io/api/v1/materialinfo/2?version=94&pageSize=200

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/materialinfo/2?version=94&pageSize=200\'
  \\

  \--header \'Content-Type: application/json\' \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"version\": 197, \"errNo\": 0,
  \"hasNext\": false, \"list\": \[ { \"id\":
  \"9585FCC7-C5E3-41CE-A341-D121DFE87744\", \"category\": 0, \"name\":
  \"2x Menthol\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/2xmenthol.jpg\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/2xmenthol.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"hasSound\": true, \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=9585FCC7-C5E3-41CE-A341-D121DFE87744\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"619DFD51-DE42-4F39-BF4A-24EC9F01C99E\", \"category\": 0, \"name\":
  \"2X\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/619DFD51-DE42-4F39-BF4A-24EC9F01C99E.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/619DFD51-DE42-4F39-BF4A-24EC9F01C99E.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=619DFD51-DE42-4F39-BF4A-24EC9F01C99E\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"30638A40-F007-42A7-A411-EABF2AFBE5D2\", \"category\": 0, \"name\":
  \"Malik\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/30638A40-F007-42A7-A411-EABF2AFBE5D2.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/30638A40-F007-42A7-A411-EABF2AFBE5D2.1.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=30638A40-F007-42A7-A411-EABF2AFBE5D2\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"177F591D-5F0E-4321-BFFD-F2A79D50D91F\", \"category\": 0, \"name\":
  \"Water Bucket\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/177F591D-5F0E-4321-BFFD-F2A79D50D91F.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/177F591D-5F0E-4321-BFFD-F2A79D50D91F.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"alias\": \"Water Image\", \"assetType\": \"EFFECT\",
  \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=177F591D-5F0E-4321-BFFD-F2A79D50D91F\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"60CED887-CF60-4C58-8756-C9B8C5AFFBCC\", \"category\": 0, \"name\":
  \"Dettol Looped\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/60CED887-CF60-4C58-8756-C9B8C5AFFBCC.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/60CED887-CF60-4C58-8756-C9B8C5AFFBCC.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=60CED887-CF60-4C58-8756-C9B8C5AFFBCC\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"94FE2DD3-1794-4DDD-9887-291FA0536B6A\", \"category\": 0, \"name\":
  \"Dettol V1\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/94FE2DD3-1794-4DDD-9887-291FA0536B6A.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/94FE2DD3-1794-4DDD-9887-291FA0536B6A.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=94FE2DD3-1794-4DDD-9887-291FA0536B6A\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"50CED887-CF60-4C58-8756-C9B8C5AFFBCC\", \"category\": 0, \"name\":
  \"Dettol V2\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/50CED887-CF60-4C58-8756-C9B8C5AFFBCC.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/50CED887-CF60-4C58-8756-C9B8C5AFFBCC.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=50CED887-CF60-4C58-8756-C9B8C5AFFBCC\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"9F06B9A5-EC3A-4282-B597-4A6810137C85\", \"category\": 0, \"name\":
  \"Dettol\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/9F06B9A5-EC3A-4282-B597-4A6810137C85.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/9F06B9A5-EC3A-4282-B597-4A6810137C85.png\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=9F06B9A5-EC3A-4282-B597-4A6810137C85\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"2215EC1E-A9EE-4B5C-89CB-BF488178C910\", \"category\": 0, \"name\":
  \"Aesth\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/2215EC1E-A9EE-4B5C-89CB-BF488178C910.2.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/2215EC1E-A9EE-4B5C-89CB-BF488178C910.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\":
  \"SIMPLE_FILTER\", \"userAction\": \"\", \"assetType\": \"FILTER\",
  \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=2215EC1E-A9EE-4B5C-89CB-BF488178C910\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"B3B3FDE1-727F-4C41-A506-3F095FF9C5D3\", \"category\": 0, \"name\":
  \"Dizzy\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/B3B3FDE1-727F-4C41-A506-3F095FF9C5D3.2.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/B3B3FDE1-727F-4C41-A506-3F095FF9C5D3.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=B3B3FDE1-727F-4C41-A506-3F095FF9C5D3\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"61B3A8B9-C843-450D-AB93-56FF082FF120\", \"category\": 0, \"name\":
  \"Warm\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/61B3A8B9-C843-450D-AB93-56FF082FF120.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/61B3A8B9-C843-450D-AB93-56FF082FF120.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\":
  \"SIMPLE_FILTER\", \"assetType\": \"FILTER\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=61B3A8B9-C843-450D-AB93-56FF082FF120\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"C8C90F0B-2120-4D1A-A538-F59BA39D8F52\", \"category\": 0, \"name\":
  \"Smile\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/C8C90F0B-2120-4D1A-A538-F59BA39D8F52.2.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/C8C90F0B-2120-4D1A-A538-F59BA39D8F52.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\":
  \"SIMPLE_FILTER\", \"assetType\": \"FILTER\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=C8C90F0B-2120-4D1A-A538-F59BA39D8F52\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"CA1D1AAD-8408-4204-986F-F28565D9729B\", \"category\": 0, \"name\":
  \"B/W Shake\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/CA1D1AAD-8408-4204-986F-F28565D9729B.2.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/CA1D1AAD-8408-4204-986F-F28565D9729B.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=CA1D1AAD-8408-4204-986F-F28565D9729B\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"553463AB-6F40-4CAF-B0D8-DB3AD3AA6B24\", \"category\": 1, \"name\":
  \"Swiss\", \"desc\": \"\", \"tags\": \"\", \"version\": 2,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/553463AB-6F40-4CAF-B0D8-DB3AD3AA6B24.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/553463AB-6F40-4CAF-B0D8-DB3AD3AA6B24.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\":
  \"SIMPLE_FILTER\", \"userAction\": \"\", \"assetType\": \"FILTER\",
  \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=553463AB-6F40-4CAF-B0D8-DB3AD3AA6B24\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"A8A4344D-45DA-460F-A18F-C0E2355FE864\", \"category\": 0, \"name\":
  \"Glitch Zoom\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/A8A4344D-45DA-460F-A18F-C0E2355FE864.5.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/A8A4344D-45DA-460F-A18F-C0E2355FE864.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=A8A4344D-45DA-460F-A18F-C0E2355FE864\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"DE535DD7-91A3-4AC2-89DE-2BA94C32BFB2\", \"category\": 0, \"name\":
  \"Moscow\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/DE535DD7-91A3-4AC2-89DE-2BA94C32BFB2.8.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/DE535DD7-91A3-4AC2-89DE-2BA94C32BFB2.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\":
  \"SIMPLE_FILTER\", \"userAction\": \"\", \"assetType\": \"FILTER\",
  \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=DE535DD7-91A3-4AC2-89DE-2BA94C32BFB2\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"B199E719-D58B-4AB3-8ED6-8DEB9832612C\", \"category\": 0, \"name\":
  \"F2\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/B199E719-D58B-4AB3-8ED6-8DEB9832612C.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/B199E719-D58B-4AB3-8ED6-8DEB9832612C.png\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=B199E719-D58B-4AB3-8ED6-8DEB9832612C\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"D1AC10BD-39F9-407D-8277-895E52066392\", \"category\": 0, \"name\":
  \"Bahamas\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/D1AC10BD-39F9-407D-8277-895E52066392.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/D1AC10BD-39F9-407D-8277-895E52066392.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\":
  \"SIMPLE_FILTER\", \"assetType\": \"FILTER\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=D1AC10BD-39F9-407D-8277-895E52066392\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"E1877C68-4610-41F6-B0F3-432CA468FE3E\", \"category\": 0, \"name\":
  \"Earth Shatter\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/E1877C68-4610-41F6-B0F3-432CA468FE3E.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/E1877C68-4610-41F6-B0F3-432CA468FE3E.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=E1877C68-4610-41F6-B0F3-432CA468FE3E\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"D9226363-B1E4-4144-880A-EDAB6ED2E654\", \"category\": 2, \"name\":
  \"Alpine\", \"desc\": \"\", \"tags\": \"\", \"version\": 2,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/D9226363-B1E4-4144-880A-EDAB6ED2E654.2.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/D9226363-B1E4-4144-880A-EDAB6ED2E654.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\":
  \"SIMPLE_FILTER\", \"userAction\": \"\", \"assetType\": \"FILTER\",
  \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=D9226363-B1E4-4144-880A-EDAB6ED2E654\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"E0CD6EBA-7D95-4F83-B9F8-79FE55C2979E\", \"category\": 0, \"name\":
  \"Energy Lines\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/E0CD6EBA-7D95-4F83-B9F8-79FE55C2979E.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/E0CD6EBA-7D95-4F83-B9F8-79FE55C2979E.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=E0CD6EBA-7D95-4F83-B9F8-79FE55C2979E\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"7625B430-0E06-446C-A558-A18F33FA4FCE\", \"category\": 0, \"name\":
  \"Energy Swirl\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/7625B430-0E06-446C-A558-A18F33FA4FCE.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/7625B430-0E06-446C-A558-A18F33FA4FCE.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"hasSound\": false, \"alias\": \"\",
  \"sdkType\": \"\", \"assetType\": \"EFFECT\", \"categoryName\": \"\",
  \"showAnimation\": false, \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=7625B430-0E06-446C-A558-A18F33FA4FCE\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"E25437B0-80F8-4515-91E0-1AB7D087D438\", \"category\": 0, \"name\":
  \"Rio\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/E25437B0-80F8-4515-91E0-1AB7D087D438.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/E25437B0-80F8-4515-91E0-1AB7D087D438.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\":
  \"SIMPLE_FILTER\", \"userAction\": \"\", \"assetType\": \"FILTER\",
  \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=E25437B0-80F8-4515-91E0-1AB7D087D438\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"6BDB176F-D105-49A7-98D2-3A0D98103F2C\", \"category\": 0, \"name\":
  \"Mocktail\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/6BDB176F-D105-49A7-98D2-3A0D98103F2C.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/6BDB176F-D105-49A7-98D2-3A0D98103F2C.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\":
  \"SIMPLE_FILTER\", \"hasSound\": false, \"assetType\": \"FILTER\",
  \"categoryName\": \"\", \"showAnimation\": false, \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=6BDB176F-D105-49A7-98D2-3A0D98103F2C\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"7FFCF99A-5336-4464-BACD-9D32D5D2DC5E\", \"category\": 0, \"name\":
  \"Star Fall\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/7FFCF99A-5336-4464-BACD-9D32D5D2DC5E.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/7FFCF99A-5336-4464-BACD-9D32D5D2DC5E.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=7FFCF99A-5336-4464-BACD-9D32D5D2DC5E\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"1AACCE79-7EAB-4B2E-AE9B-E53A02AFC055\", \"category\": 0, \"name\":
  \"Petal Shower\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/1AACCE79-7EAB-4B2E-AE9B-E53A02AFC055.3.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/1AACCE79-7EAB-4B2E-AE9B-E53A02AFC055.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=1AACCE79-7EAB-4B2E-AE9B-E53A02AFC055\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"4EFE3455-C58D-499C-B311-D445F752D567\", \"category\": 0, \"name\":
  \"Caffeine\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/4EFE3455-C58D-499C-B311-D445F752D567.3.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/4EFE3455-C58D-499C-B311-D445F752D567.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\":
  \"SIMPLE_FILTER\", \"userAction\": \"\", \"assetType\": \"FILTER\",
  \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=4EFE3455-C58D-499C-B311-D445F752D567\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"3B145FE8-E780-403F-A7B2-A061CB56243F\", \"category\": 0, \"name\":
  \"Bubbles\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/3B145FE8-E780-403F-A7B2-A061CB56243F.3.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/3B145FE8-E780-403F-A7B2-A061CB56243F.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=3B145FE8-E780-403F-A7B2-A061CB56243F\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"FAE50247-F14C-40CE-AD43-29CA3E604838\", \"category\": 0, \"name\":
  \"Citrus\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/FAE50247-F14C-40CE-AD43-29CA3E604838.3.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/FAE50247-F14C-40CE-AD43-29CA3E604838.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\":
  \"SIMPLE_FILTER\", \"userAction\": \"\", \"assetType\": \"FILTER\",
  \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=FAE50247-F14C-40CE-AD43-29CA3E604838\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"7D8A1839-B7D3-4C91-AD7A-8FB920322818\", \"category\": 0, \"name\":
  \"Vanilla\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/7D8A1839-B7D3-4C91-AD7A-8FB920322818.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/7D8A1839-B7D3-4C91-AD7A-8FB920322818.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\":
  \"SIMPLE_FILTER\", \"userAction\": \"\", \"assetType\": \"FILTER\",
  \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=7D8A1839-B7D3-4C91-AD7A-8FB920322818\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"ABAAD551-6E94-4F1C-B8D1-12209BEBBB6D\", \"category\": 0, \"name\":
  \"Disco Lights\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/ABAAD551-6E94-4F1C-B8D1-12209BEBBB6D.2.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/ABAAD551-6E94-4F1C-B8D1-12209BEBBB6D.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=ABAAD551-6E94-4F1C-B8D1-12209BEBBB6D\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"163DE520-95FC-4CF3-B847-C43F1D474587\", \"category\": 0, \"name\":
  \"Vintage\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/163DE520-95FC-4CF3-B847-C43F1D474587.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/163DE520-95FC-4CF3-B847-C43F1D474587.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\":
  \"SIMPLE_FILTER\", \"userAction\": \"\", \"assetType\": \"FILTER\",
  \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=163DE520-95FC-4CF3-B847-C43F1D474587\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"BCD1FAAD-D5C5-468F-A4F2-1C2138F485C0\", \"category\": 0, \"name\":
  \"Color Seperation\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/BCD1FAAD-D5C5-468F-A4F2-1C2138F485C0.3.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/BCD1FAAD-D5C5-468F-A4F2-1C2138F485C0.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=BCD1FAAD-D5C5-468F-A4F2-1C2138F485C0\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"259D1CBF-2A20-4A2C-AFDD-185B05B0B07D\", \"category\": 0, \"name\":
  \"Retro TV\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/259D1CBF-2A20-4A2C-AFDD-185B05B0B07D.2.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/259D1CBF-2A20-4A2C-AFDD-185B05B0B07D.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=259D1CBF-2A20-4A2C-AFDD-185B05B0B07D\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"F4071666-225C-4ACE-B0E5-60C9F7E940F1\", \"category\": 0, \"name\":
  \"Sepia\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/F4071666-225C-4ACE-B0E5-60C9F7E940F1.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/F4071666-225C-4ACE-B0E5-60C9F7E940F1.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\":
  \"SIMPLE_FILTER\", \"userAction\": \"\", \"assetType\": \"FILTER\",
  \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=F4071666-225C-4ACE-B0E5-60C9F7E940F1\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"35B954E1-8D38-40BC-A567-F6DA1D557950\", \"category\": 0, \"name\":
  \"RGB Glitch\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/35B954E1-8D38-40BC-A567-F6DA1D557950.2.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/35B954E1-8D38-40BC-A567-F6DA1D557950.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=35B954E1-8D38-40BC-A567-F6DA1D557950\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"73844D15-405B-4B3F-AC71-403B7E069166\", \"category\": 1, \"name\":
  \"Retro\", \"desc\": \"\", \"tags\": \"\", \"version\": 2,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/73844D15-405B-4B3F-AC71-403B7E069166.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/73844D15-405B-4B3F-AC71-403B7E069166.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\":
  \"SIMPLE_FILTER\", \"userAction\": \"\", \"assetType\": \"FILTER\",
  \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=73844D15-405B-4B3F-AC71-403B7E069166\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"381869EE-F40D-4F4D-A641-ED2B59DD18AE\", \"category\": 0, \"name\":
  \"Dreamy\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/381869EE-F40D-4F4D-A641-ED2B59DD18AE.3.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/381869EE-F40D-4F4D-A641-ED2B59DD18AE.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=381869EE-F40D-4F4D-A641-ED2B59DD18AE\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"D50DC3F9-1995-4B08-8D75-88DEBDC33E28\", \"category\": 0, \"name\":
  \"Bleak\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/D50DC3F9-1995-4B08-8D75-88DEBDC33E28.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/D50DC3F9-1995-4B08-8D75-88DEBDC33E28.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\":
  \"SIMPLE_FILTER\", \"userAction\": \"\", \"assetType\": \"FILTER\",
  \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=D50DC3F9-1995-4B08-8D75-88DEBDC33E28\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"C6EDD0D4-845A-4D5F-9022-349343B5DEAE\", \"category\": 0, \"name\":
  \"Cosmos\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/C6EDD0D4-845A-4D5F-9022-349343B5DEAE.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/C6EDD0D4-845A-4D5F-9022-349343B5DEAE.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=C6EDD0D4-845A-4D5F-9022-349343B5DEAE\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"18C6DAA7-0776-4D72-AB6D-8C195FA17617\", \"category\": 0, \"name\":
  \"Moody\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/18C6DAA7-0776-4D72-AB6D-8C195FA17617.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/18C6DAA7-0776-4D72-AB6D-8C195FA17617.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\":
  \"SIMPLE_FILTER\", \"userAction\": \"\", \"assetType\": \"FILTER\",
  \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=18C6DAA7-0776-4D72-AB6D-8C195FA17617\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"35716E29-D415-442E-9837-B4202EA6A465\", \"category\": 1, \"name\":
  \"Glitterfall\", \"desc\": \"\", \"tags\": \"\", \"version\": 2,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/35716E29-D415-442E-9837-B4202EA6A465.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/35716E29-D415-442E-9837-B4202EA6A465.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=35716E29-D415-442E-9837-B4202EA6A465\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"914AECF6-D404-4EC9-8C80-4B463BA4E33C\", \"category\": 0, \"name\":
  \"Golden Shower\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/914AECF6-D404-4EC9-8C80-4B463BA4E33C.2.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/914AECF6-D404-4EC9-8C80-4B463BA4E33C.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=914AECF6-D404-4EC9-8C80-4B463BA4E33C\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"3C1C1944-117F-4D4C-8432-22D165CB27BC\", \"category\": 0, \"name\":
  \"Classic\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/3C1C1944-117F-4D4C-8432-22D165CB27BC.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/3C1C1944-117F-4D4C-8432-22D165CB27BC.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\":
  \"SIMPLE_FILTER\", \"userAction\": \"\", \"assetType\": \"FILTER\",
  \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=3C1C1944-117F-4D4C-8432-22D165CB27BC\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"FCBB591F-7502-48AF-93BC-4B4A094A660E\", \"category\": 0, \"name\":
  \"Golden Burst\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/FCBB591F-7502-48AF-93BC-4B4A094A660E.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/FCBB591F-7502-48AF-93BC-4B4A094A660E.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=FCBB591F-7502-48AF-93BC-4B4A094A660E\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"8B952A30-CD2F-4E77-ABED-EC1DDF4AA67E\", \"category\": 2, \"name\":
  \"Film Reel\", \"desc\": \"\", \"tags\": \"\", \"version\": 2,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/8B952A30-CD2F-4E77-ABED-EC1DDF4AA67E.2.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/8B952A30-CD2F-4E77-ABED-EC1DDF4AA67E.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=8B952A30-CD2F-4E77-ABED-EC1DDF4AA67E\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"D4C889D0-423A-4A3D-A141-7BA74063AE35\", \"category\": 0, \"name\":
  \"Poser\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/D4C889D0-423A-4A3D-A141-7BA74063AE35.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/D4C889D0-423A-4A3D-A141-7BA74063AE35.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\":
  \"SIMPLE_FILTER\", \"userAction\": \"\", \"assetType\": \"FILTER\",
  \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=D4C889D0-423A-4A3D-A141-7BA74063AE35\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"DA06CB37-BD38-454A-B868-34B8ABC4BECC\", \"category\": 0, \"name\":
  \"Punch\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/DA06CB37-BD38-454A-B868-34B8ABC4BECC.2.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/DA06CB37-BD38-454A-B868-34B8ABC4BECC.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\":
  \"SIMPLE_FILTER\", \"userAction\": \"\", \"assetType\": \"FILTER\",
  \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=DA06CB37-BD38-454A-B868-34B8ABC4BECC\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"DDBA78BB-9B83-4E29-B39B-4152AF1AFD00\", \"category\": 0, \"name\":
  \"Polaroid\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/DDBA78BB-9B83-4E29-B39B-4152AF1AFD00.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/DDBA78BB-9B83-4E29-B39B-4152AF1AFD00.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=DDBA78BB-9B83-4E29-B39B-4152AF1AFD00\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"A298F02A-1E80-96BE-20F0-6ED3831D9CFE\", \"category\": 0, \"name\":
  \"VHS\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/A298F02A-1E80-96BE-20F0-6ED3831D9CFE.2.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/A298F02A-1E80-96BE-20F0-6ED3831D9CFE.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=A298F02A-1E80-96BE-20F0-6ED3831D9CFE\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"11DD8ED9-880F-4017-B973-6A6B708129F7\", \"category\": 0, \"name\":
  \"Daylight\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/11DD8ED9-880F-4017-B973-6A6B708129F7.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/11DD8ED9-880F-4017-B973-6A6B708129F7.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=11DD8ED9-880F-4017-B973-6A6B708129F7\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"D3953EDC-CC71-4C63-B1A9-D905180F562D\", \"category\": 0, \"name\":
  \"Disco Leaks\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/D3953EDC-CC71-4C63-B1A9-D905180F562D.2.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/D3953EDC-CC71-4C63-B1A9-D905180F562D.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=D3953EDC-CC71-4C63-B1A9-D905180F562D\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"CD50AE6B-0BD0-4AFD-B122-7D1E33A2C76A\", \"category\": 0, \"name\":
  \"9 Grid Marque\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/CD50AE6B-0BD0-4AFD-B122-7D1E33A2C76A.2.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/CD50AE6B-0BD0-4AFD-B122-7D1E33A2C76A.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=CD50AE6B-0BD0-4AFD-B122-7D1E33A2C76A\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"617B0867-099D-417A-985C-59C6EE7B75ED\", \"category\": 2, \"name\":
  \"6 Grid\", \"desc\": \"\", \"tags\": \"\", \"version\": 2,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/617B0867-099D-417A-985C-59C6EE7B75ED.2.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/617B0867-099D-417A-985C-59C6EE7B75ED.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=617B0867-099D-417A-985C-59C6EE7B75ED\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"B8D91810-03C7-4100-BEC6-3B832C0A3D01\", \"category\": 0, \"name\":
  \"2 Grid\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/B8D91810-03C7-4100-BEC6-3B832C0A3D01.2.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/B8D91810-03C7-4100-BEC6-3B832C0A3D01.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=B8D91810-03C7-4100-BEC6-3B832C0A3D01\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"895EFE2F-C116-4DBE-A244-67C6C26DC864\", \"category\": 0, \"name\":
  \"4 Grid\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/895EFE2F-C116-4DBE-A244-67C6C26DC864.3.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/895EFE2F-C116-4DBE-A244-67C6C26DC864.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=895EFE2F-C116-4DBE-A244-67C6C26DC864\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"ce551302-7216-11ec-873b-4b6e5aaa9440\", \"category\": 0, \"name\":
  \"Dummy\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/ce551302-7216-11ec-873b-4b6e5aaa9440.2.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/ce551302-7216-11ec-873b-4b6e5aaa9440.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\":
  \"SIMPLE_FILTER\", \"assetType\": \"FILTER\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=ce551302-7216-11ec-873b-4b6e5aaa9440\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"548F5513-648C-4FDD-8025-BDB006C86803\", \"category\": 0, \"name\":
  \"3 Grid\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/548F5513-648C-4FDD-8025-BDB006C86803.2.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/548F5513-648C-4FDD-8025-BDB006C86803.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=548F5513-648C-4FDD-8025-BDB006C86803\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"B69DAD3B-8113-4E92-8BFD-12EF0D8AED20\", \"category\": 2, \"name\":
  \"Camera Focus\", \"desc\": \"\", \"tags\": \"\", \"version\": 2,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/B69DAD3B-8113-4E92-8BFD-12EF0D8AED20.2.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/B69DAD3B-8113-4E92-8BFD-12EF0D8AED20.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=B69DAD3B-8113-4E92-8BFD-12EF0D8AED20\",
  \"pass_through\": \"EFFECT\" }, { \"id\": \"amritsar\", \"category\":
  0, \"name\": \"amritsar\", \"desc\": \"\", \"tags\": \"\",
  \"version\": 0, \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/amritsar.videofx\",
  \"packageSize\": 0, \"supportedAspectRatio\": 0, \"idx\": 0,
  \"filterType\": \"SIMPLE_FILTER\", \"userAction\": \"\",
  \"assetType\": \"FILTER\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=amritsar\",
  \"pass_through\": \"EFFECT\" }, { \"id\": \"mathura\", \"category\":
  0, \"name\": \"mathura\", \"desc\": \"\", \"tags\": \"\", \"version\":
  0, \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/mathura.videofx\",
  \"packageSize\": 0, \"supportedAspectRatio\": 0, \"idx\": 0,
  \"filterType\": \"SIMPLE_FILTER\", \"userAction\": \"\",
  \"assetType\": \"FILTER\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=mathura\",
  \"pass_through\": \"EFFECT\" }, { \"id\": \"vrindavan\", \"category\":
  0, \"name\": \"vrindavan\", \"desc\": \"\", \"tags\": \"\",
  \"version\": 0, \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/vrindavan.videofx\",
  \"packageSize\": 0, \"supportedAspectRatio\": 0, \"idx\": 0,
  \"filterType\": \"SIMPLE_FILTER\", \"userAction\": \"\",
  \"assetType\": \"FILTER\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=vrindavan\",
  \"pass_through\": \"EFFECT\" }, { \"id\": \"varanasi\", \"category\":
  0, \"name\": \"varanasi\", \"desc\": \"\", \"tags\": \"\",
  \"version\": 0, \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/varanasi.videofx\",
  \"packageSize\": 0, \"supportedAspectRatio\": 0, \"idx\": 0,
  \"filterType\": \"SIMPLE_FILTER\", \"userAction\": \"\",
  \"assetType\": \"FILTER\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=varanasi\",
  \"pass_through\": \"EFFECT\" }, { \"id\": \"barsana\", \"category\":
  0, \"name\": \"barsana\", \"desc\": \"\", \"tags\": \"\", \"version\":
  0, \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/barsana.videofx\",
  \"packageSize\": 0, \"supportedAspectRatio\": 0, \"idx\": 0,
  \"filterType\": \"SIMPLE_FILTER\", \"userAction\": \"\",
  \"assetType\": \"FILTER\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=barsana\",
  \"pass_through\": \"EFFECT\" }, { \"id\": \"baldeo\", \"category\": 0,
  \"name\": \"baldeo\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/baldeo.videofx\",
  \"packageSize\": 0, \"supportedAspectRatio\": 0, \"idx\": 0,
  \"filterType\": \"SIMPLE_FILTER\", \"userAction\": \"\",
  \"assetType\": \"FILTER\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=baldeo\",
  \"pass_through\": \"EFFECT\" }, { \"id\": \"jaipur\", \"category\": 0,
  \"name\": \"jaipur\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/jaipur.videofx\",
  \"packageSize\": 0, \"supportedAspectRatio\": 0, \"idx\": 0,
  \"filterType\": \"SIMPLE_FILTER\", \"userAction\": \"\",
  \"assetType\": \"FILTER\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=jaipur\",
  \"pass_through\": \"EFFECT\" }, { \"id\": \"udaipur\", \"category\":
  0, \"name\": \"udaipur\", \"desc\": \"\", \"tags\": \"\", \"version\":
  0, \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/udaipur.videofx\",
  \"packageSize\": 0, \"supportedAspectRatio\": 0, \"idx\": 0,
  \"filterType\": \"SIMPLE_FILTER\", \"userAction\": \"\",
  \"assetType\": \"FILTER\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=udaipur\",
  \"pass_through\": \"EFFECT\" }, { \"id\": \"pushkar\", \"category\":
  0, \"name\": \"pushkar\", \"desc\": \"\", \"tags\": \"\", \"version\":
  0, \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/pushkar.videofx\",
  \"packageSize\": 0, \"supportedAspectRatio\": 0, \"idx\": 0,
  \"filterType\": \"SIMPLE_FILTER\", \"userAction\": \"\",
  \"assetType\": \"FILTER\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=pushkar\",
  \"pass_through\": \"EFFECT\" }, { \"id\": \"anandapur_sahib\",
  \"category\": 0, \"name\": \"anandapur_sahib\", \"desc\": \"\",
  \"tags\": \"\", \"version\": 0, \"minAppVersion\": \"\",
  \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/anandapur_sahib.videofx\",
  \"packageSize\": 0, \"supportedAspectRatio\": 0, \"idx\": 0,
  \"filterType\": \"SIMPLE_FILTER\", \"userAction\": \"\",
  \"assetType\": \"FILTER\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=anandapur_sahib\",
  \"pass_through\": \"EFFECT\" }, { \"id\": \"shahpura_bagh\",
  \"category\": 0, \"name\": \"shahpura_bagh\", \"desc\": \"\",
  \"tags\": \"\", \"version\": 0, \"minAppVersion\": \"\",
  \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/shahpura_bagh.videofx\",
  \"packageSize\": 0, \"supportedAspectRatio\": 0, \"idx\": 0,
  \"filterType\": \"SIMPLE_FILTER\", \"userAction\": \"\",
  \"assetType\": \"FILTER\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=shahpura_bagh\",
  \"pass_through\": \"EFFECT\" }, { \"id\": \"ramathra_fort\",
  \"category\": 0, \"name\": \"ramathra_fort\", \"desc\": \"\",
  \"tags\": \"\", \"version\": 0, \"minAppVersion\": \"\",
  \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/ramathra_fort.videofx\",
  \"packageSize\": 0, \"supportedAspectRatio\": 0, \"idx\": 0,
  \"filterType\": \"SIMPLE_FILTER\", \"userAction\": \"\",
  \"assetType\": \"FILTER\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=ramathra_fort\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"2257D45D-D909-458B-8004-04CB20CDAA12\", \"category\": 0, \"name\":
  \"Lucknow a large city in northern India and capital of UP\",
  \"desc\": \"\", \"tags\": \"\", \"version\": 0, \"minAppVersion\":
  \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/2257D45D-D909-458B-8004-04CB20CDAA12.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/blank.png\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=2257D45D-D909-458B-8004-04CB20CDAA12\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"ce551302-7216-11ec-873b-4b6e5aaa9440\", \"category\": 0, \"name\":
  \"Dummy Filter\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/ce551302-7216-11ec-873b-4b6e5aaa9440.2.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/ce551302-7216-11ec-873b-4b6e5aaa9440.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\":
  \"SIMPLE_FILTER\", \"assetType\": \"FILTER\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=ce551302-7216-11ec-873b-4b6e5aaa9440\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"A8ABB71-3ED4-4339-9052-25B9D35E4ADA\", \"category\": 0, \"name\":
  \"TestQA1\", \"desc\": \"TestQA1\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/A8ABB71-3ED4-4339-9052-25B9D35E4ADA.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/F4071666-225C-4ACE-B0E5-60C9F7E940F1.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\":
  \"SIMPLE_FILTER\", \"assetType\": \"FILTER\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=A8ABB71-3ED4-4339-9052-25B9D35E4ADA\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"4562EDA7-26D9-4179-8E5B-D24B041FC789\", \"category\": 0, \"name\":
  \"Pongal\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/4562EDA7-26D9-4179-8E5B-D24B041FC789.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/Pongal.png\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\":
  \"SIMPLE_FILTER\", \"assetType\": \"FILTER\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=4562EDA7-26D9-4179-8E5B-D24B041FC789\",
  \"pass_through\": \"EFFECT\" } \] }

- **Request Method and URL:**

  POST : https://qa-gateway.coolfie.io/api/v1/material/2/create

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/material/2/create\' \\

  \--form \'id=\"11DD8ED9-880F-4017-B973-6A6B708129F7V2\"\' \\

  \--form \'name=\"testing\"\' \\

  \--form
  \'packageUrl=@\"/home/varikutitheja/Desktop/11DD8ED9-880F-4017-B973-6A6B708129F7.1.videofx\"\'
  \\

  \--form
  \'coverUrl=@\"/home/varikutitheja/Desktop/11DD8ED9-880F-4017-B973-6A6B708129F7.jpg\"\'
  \\

  \--form \'viewOrder=\"268\"\' \\

  \--form \'filterType=\"EFFECT\"\' \\

  \--form \'assetType=\"2\"\' \\

  \--form
  \'license=@\"/home/varikutitheja/Desktop/sample-files/sample_640×426.jpeg\"\'

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 } }

- **Request Method and URL:**

  POST : https://qa-gateway.coolfie.io/api/v1/FACE_UNITY/cms/assets/list

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/FACE_UNITY/cms/assets/list\' \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 } }

- **Request Method and URL:**

  GET : https://qa-gateway.coolfie.io/api/v1/FACE_UNITY/cms/assets/list

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/FACE_UNITY/cms/assets/list\' \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 } }

- **Request Method and URL:**

  DELETE : https://qa-gateway.coolfie.io/api/v1/material/14//delete

- **Curl Request:**

  curl \--location \--request DELETE
  \'https://qa-gateway.coolfie.io/api/v1/material/14//delete\' \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 } }

- **Request Method and URL:**

  PUT :
  https://qa-gateway.coolfie.io/api/v1/material/1/61B3A8B9-C843-450D-AB93-56FF082FF120/update

- **Curl Request:**

  curl \--location \--request PUT
  \'https://qa-gateway.coolfie.io/api/v1/material/1/61B3A8B9-C843-450D-AB93-56FF082FF120/update\'
  \\

  \--header \'Content-Type: application/json\' \\

  \--data-raw \'{

  \"viewOrder\": 30

  }\'

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 } }

- **Request Method and URL:**

  GET :
  https://qa-gateway.coolfie.io/api/v1/zerosearch/get?lang_code=en&status=ACTIVE

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/zerosearch/get?lang_code=en&status=ACTIVE\'
  \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { \"MUSIC\": { \"MUSIC\": {
  \"sectionName\": \"MUSIC\", \"sectionTitle\": \"Music\",
  \"sectionIsActive\": true, \"sectionId\": 7, \"sectionDepth\": 10,
  \"sectionRecords\": \[ { \"recordId\": 748, \"title\": \"music_pg3\",
  \"description\": \"des-music-pg3\", \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/c88fc8e5b00e5f09304cbfe85874c189.png\",
  \"viewOrder\": 3, \"subtitle\": \"sub-music-pg3\", \"isActive\": true,
  \"itemId\": \"a003a284-3103-4115-bac8-e5575d162126\",
  \"showInAndroid\": true, \"showInIos\": true, \"showInPwa\": true,
  \"deeplink_url\":
  \"https://qa-share.myjosh.in/audio/a003a284-3103-4115-bac8-e5575d162126\",
  \"feed_type\": \"MUSIC\", \"rich_deeplink\":
  \"https://qa-share.myjosh.in/audio/a003a284-3103-4115-bac8-e5575d162126\"
  }, { \"recordId\": 1007, \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/acb638a74b929f0082dcdd643270a152.png\",
  \"viewOrder\": 5, \"isActive\": true, \"itemId\":
  \"dc6d060e-b78b-4e05-8739-cd86c43289e0\", \"showInAndroid\": true,
  \"showInIos\": true, \"showInPwa\": true, \"feed_type\": \"MUSIC\",
  \"rich_deeplink\":
  \"https://qa-share.myjosh.in/audio/dc6d060e-b78b-4e05-8739-cd86c43289e0\"
  } \] }, \"MUSIC2\": { \"sectionName\": \"MUSIC2\", \"sectionTitle\":
  \"sec-music2\", \"sectionIsActive\": true, \"sectionId\": 36,
  \"sectionDepth\": 11, \"sectionRecords\": \[ { \"recordId\": 812,
  \"thumbnail\": \"\", \"viewOrder\": 0, \"isActive\": true, \"itemId\":
  \"78299fb4-a957-4051-8a28-079aa63039bd\", \"showInAndroid\": true,
  \"showInIos\": true, \"feed_type\": \"MUSIC\", \"rich_deeplink\":
  \"https://qa-share.myjosh.in/audio/78299fb4-a957-4051-8a28-079aa63039bd\"
  }, { \"recordId\": 768, \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/9270ef7fca7c00c65a1cceafc6a08c31.png\",
  \"viewOrder\": 0, \"isActive\": true, \"itemId\":
  \"fab71fa3-8a35-4c0e-908b-e02d6b0095e8\", \"showInAndroid\": true,
  \"showInIos\": true, \"feed_type\": \"MUSIC\", \"rich_deeplink\":
  \"https://qa-share.myjosh.in/audio/fab71fa3-8a35-4c0e-908b-e02d6b0095e8\"
  }, { \"recordId\": 997, \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/4c1bb1ca34266b6f3e17a6365c67fbd0.png\",
  \"viewOrder\": 5, \"isActive\": true, \"itemId\":
  \"a8c9e69e-1a13-4db5-a203-6a0aec2676da\", \"showInAndroid\": true,
  \"showInIos\": true, \"showInPwa\": true, \"feed_type\": \"MUSIC\",
  \"rich_deeplink\":
  \"https://qa-share.myjosh.in/audio/a8c9e69e-1a13-4db5-a203-6a0aec2676da\"
  } \] } }, \"BANNER\": { \"JS Callback Banners\": { \"sectionName\":
  \"JS Callback Banners\", \"sectionTitle\": \"JS Callback Banners\",
  \"sectionIsActive\": true, \"sectionId\": 57, \"sectionDepth\": 1050,
  \"sectionRecords\": \[ { \"recordId\": 1016, \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/dTlBVkxyeQ==.jpg\",
  \"viewOrder\": 0, \"isActive\": true, \"itemId\":
  \"0cb3f147-c5dc-4026-b3c4-339f7fc7640a\", \"showInAndroid\": true,
  \"showInIos\": true, \"showInPwa\": true, \"feed_type\": \"BANNER\",
  \"rich_deeplink\":
  \"https://qa-share.myjosh.in/challenge/0cb3f147-c5dc-4026-b3c4-339f7fc7640a\"
  }, { \"recordId\": 938, \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/1c7ea3a9f08c0a5eff08fa5cd2ad864e.png\",
  \"viewOrder\": 0, \"isActive\": true, \"itemId\":
  \"5b529cfd-aae0-4867-ab44-949ea0c82ad1\", \"showInAndroid\": true,
  \"showInIos\": true, \"showInPwa\": true, \"feed_type\": \"BANNER\",
  \"rich_deeplink\":
  \"https://qa-share.myjosh.in/challenge/5b529cfd-aae0-4867-ab44-949ea0c82ad1\"
  }, { \"recordId\": 934, \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/3f3a6e4ed54a05d0e88299329858f55a.png\",
  \"viewOrder\": 1, \"isActive\": true, \"itemId\":
  \"c3dc4477-6c5f-4340-b8b9-0d866509a05f\", \"showInAndroid\": true,
  \"showInIos\": true, \"showInPwa\": true, \"feed_type\": \"BANNER\",
  \"rich_deeplink\":
  \"https://qa-share.myjosh.in/challenge/c3dc4477-6c5f-4340-b8b9-0d866509a05f\"
  }, { \"recordId\": 598, \"title\": \"M3challenge\", \"description\":
  \"\", \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/8ec60d134d1a46742e7ef52336e11602.png\",
  \"viewOrder\": 2, \"isActive\": true, \"itemId\":
  \"618a992d-6f2f-4cd3-a041-ccc8fbd5f3d1\", \"showInAndroid\": true,
  \"showInIos\": true, \"showInPwa\": true, \"deeplink_url\":
  \"http://qa-share.myjosh.in/challenge/618a992d-6f2f-4cd3-a041-ccc8fbd5f3d1\",
  \"feed_type\": \"BANNER\" } \] }, \"BANNER1\": { \"sectionName\":
  \"BANNER1\", \"sectionTitle\": \"Challenge Banner1\",
  \"sectionIsActive\": true, \"sectionId\": 1, \"sectionDepth\": 0,
  \"sectionRecords\": \[ { \"recordId\": 1013, \"title\": \"josh
  concert\", \"description\": \"\", \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/969140ec3773b8c42a2c0006648b762b.png\",
  \"viewOrder\": 0, \"subtitle\": \"\", \"isActive\": true,
  \"showInAndroid\": true, \"showInIos\": true, \"showInPwa\": false,
  \"deeplink_url\":
  \"http://www.coolfie.io/webItem?webModel=%7B%22title%22%3A%22josh-cricket-leaderboard%22%2C%22url%22%3A%22https%3A%2F%2Fqa-webitem-share.myjosh.in%2Fwebview%2Fjosh-cricket-leaderboard%22%7D\",
  \"feed_type\": \"BANNER\", \"rich_deeplink\":
  \"http://www.coolfie.io/webItem?webModel=%7B%22title%22%3A%22josh-cricket-leaderboard%22%2C%22url%22%3A%22https%3A%2F%2Fqa-webitem-share.myjosh.in%2Fwebview%2Fjosh-cricket-leaderboard%22%7D\"
  }, { \"recordId\": 874, \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/0c190d4c69e4dbdcd1d15800d61beb3e.png\",
  \"viewOrder\": 1, \"isActive\": true, \"itemId\":
  \"738bc012-6247-4fe8-a32a-5938f9158a3b\", \"showInAndroid\": true,
  \"showInIos\": true, \"showInPwa\": false, \"feed_type\": \"BANNER\",
  \"rich_deeplink\":
  \"http://www.coolfie.io/webItem?webModel=%7B%22title%22%3A%22josh-astro%22%2C%22url%22%3A%22https%3A%2F%2Fqa-webitem-share.myjosh.in%2Fwebview%2Fjosh-astro%22%7D\"
  } \] }, \"BANNER2\": { \"sectionName\": \"BANNER2\", \"sectionTitle\":
  \"Challenge Banner2\", \"sectionIsActive\": true, \"sectionId\": 29,
  \"sectionDepth\": 1, \"sectionRecords\": \[ { \"recordId\": 1004,
  \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/6b23e0433d50f4657d6592df6e481d6b.png\",
  \"viewOrder\": 1, \"isActive\": true, \"itemId\":
  \"547e5cfa-e45a-4372-9f0b-1e43dca9f563\", \"showInAndroid\": true,
  \"showInIos\": true, \"showInPwa\": true, \"feed_type\": \"BANNER\",
  \"rich_deeplink\":
  \"http://qa-share.myjosh.in/challenge/547e5cfa-e45a-4372-9f0b-1e43dca9f563\"
  }, { \"recordId\": 1005, \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/0b25a4c142e0ab1fbf28f496e1577443.png\",
  \"viewOrder\": 2, \"isActive\": true, \"itemId\":
  \"855f4cf6-c961-4c38-afb3-73232929269e\", \"showInAndroid\": true,
  \"showInIos\": true, \"showInPwa\": true, \"feed_type\": \"BANNER\",
  \"rich_deeplink\":
  \"http://qa-share.myjosh.in/challenge/855f4cf6-c961-4c38-afb3-73232929269e\"
  }, { \"recordId\": 751, \"title\": \"Sponsored challenge\",
  \"description\": \"this is sponsored\", \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/14b789bf93ee9f60966d7dd579707b9e.png\",
  \"viewOrder\": 8, \"subtitle\": \"spons\", \"isActive\": true,
  \"itemId\": \"c1b3b10a-cb3f-44f1-b8c6-8e7812dc5101\",
  \"showInAndroid\": true, \"showInIos\": true, \"showInPwa\": true,
  \"deeplink_url\":
  \"https://qa-share.myjosh.in/challenge/c1b3b10a-cb3f-44f1-b8c6-8e7812dc5101\",
  \"feed_type\": \"BANNER\", \"rich_deeplink\":
  \"https://qa-share.myjosh.in/challenge/c1b3b10a-cb3f-44f1-b8c6-8e7812dc5101\"
  }, { \"recordId\": 763, \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/3170403d1761f6e89280201342f736ac.png\",
  \"viewOrder\": 10, \"isActive\": true, \"itemId\":
  \"47f26bfa-5d06-47e8-99dc-2521b2716719\", \"showInAndroid\": true,
  \"showInIos\": true, \"showInPwa\": true, \"feed_type\": \"BANNER\",
  \"rich_deeplink\":
  \"https://qa-share.myjosh.in/challenge/47f26bfa-5d06-47e8-99dc-2521b2716719\"
  }, { \"recordId\": 697, \"title\": \"ban2dep10\", \"description\":
  \"des-ban2-dep10\", \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/bdf3bf1da3405725be763540d6601144.png\",
  \"viewOrder\": 11, \"subtitle\": \"sub-ban2-dep10\", \"isActive\":
  true, \"itemId\": \"51c032ef-1ea9-4395-a66f-17147b1b3a70\",
  \"showInAndroid\": true, \"showInIos\": true, \"showInPwa\": true,
  \"deeplink_url\":
  \"https://qa-share.myjosh.in/challenge/51c032ef-1ea9-4395-a66f-17147b1b3a70\",
  \"feed_type\": \"BANNER\", \"rich_deeplink\":
  \"https://qa-share.myjosh.in/challenge/51c032ef-1ea9-4395-a66f-17147b1b3a70\"
  } \] }, \"Banner4\": { \"sectionName\": \"Banner4\", \"sectionTitle\":
  \"Challenge Banner4\", \"sectionIsActive\": true, \"sectionId\": 39,
  \"sectionDepth\": 15, \"sectionRecords\": \[ { \"recordId\": 735,
  \"title\": \"cheduetr7\", \"description\": \"cheduetr7\",
  \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/16ac169b293c85238c380c8ad6a6f447.png\",
  \"viewOrder\": 2, \"subtitle\": \"cheduetr7\", \"isActive\": true,
  \"itemId\": \"dcd036ab-799f-4788-8da1-59688d387095\",
  \"deeplink_url\":
  \"https://qa-share.myjosh.in/challenge/dcd036ab-799f-4788-8da1-59688d387095\",
  \"feed_type\": \"BANNER\", \"rich_deeplink\":
  \"https://qa-share.myjosh.in/challenge/dcd036ab-799f-4788-8da1-59688d387095\"
  }, { \"recordId\": 738, \"title\": \"cheaudior7\", \"description\":
  \"cheaudior7\", \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/887e6d6e7b82e057ad634d8b41a6da8b.png\",
  \"viewOrder\": 4, \"subtitle\": \"cheaudior7\", \"isActive\": true,
  \"itemId\": \"d7a472b4-8375-4969-8566-63f8b7191458\",
  \"deeplink_url\":
  \"https://qa-share.myjosh.in/challenge/d7a472b4-8375-4969-8566-63f8b7191458\",
  \"feed_type\": \"BANNER\", \"rich_deeplink\":
  \"https://qa-share.myjosh.in/challenge/d7a472b4-8375-4969-8566-63f8b7191458\"
  }, { \"recordId\": 736, \"title\": \"chenonaudior7\", \"description\":
  \"chenonaudior7\", \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/fc882f02eb51461cee0734f45c950d45.png\",
  \"viewOrder\": 5, \"subtitle\": \"chenonaudior7\", \"isActive\": true,
  \"itemId\": \"96db0a84-540b-45e1-a6f7-484c525e39ec\",
  \"deeplink_url\":
  \"https://qa-share.myjosh.in/challenge/96db0a84-540b-45e1-a6f7-484c525e39ec\",
  \"feed_type\": \"BANNER\", \"rich_deeplink\":
  \"https://qa-share.myjosh.in/challenge/96db0a84-540b-45e1-a6f7-484c525e39ec\"
  } \] } }, \"POPULAR CREATORS\": { \"CREATOR2\": { \"sectionName\":
  \"CREATOR2\", \"sectionTitle\": \"sec-creator2\", \"sectionIsActive\":
  true, \"sectionId\": 31, \"sectionDepth\": 2, \"sectionRecords\": \[ {
  \"recordId\": 764, \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/76942322a38b26db5a5a2279305f78ff.png\",
  \"viewOrder\": 0, \"isActive\": true, \"itemId\":
  \"9da6b1be-238e-479c-87b3-be34ef6a639c\", \"showInAndroid\": true,
  \"showInIos\": true, \"showInPwa\": true, \"feed_type\": \"POPULAR
  CREATORS\", \"rich_deeplink\":
  \"https://www.coolfie.io/profile/9da6b1be-238e-479c-87b3-be34ef6a639c\"
  }, { \"recordId\": 999, \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/f3780e91aa800e01fccd179e7cdab98a.png\",
  \"viewOrder\": 3, \"isActive\": true, \"itemId\":
  \"e1ce96a1-4b81-4893-ba4b-e32ec3985050\", \"showInAndroid\": true,
  \"showInIos\": true, \"showInPwa\": true, \"feed_type\": \"POPULAR
  CREATORS\", \"rich_deeplink\":
  \"https://www.coolfie.io/profile/e1ce96a1-4b81-4893-ba4b-e32ec3985050\"
  } \] }, \"CREATOR1\": { \"sectionName\": \"CREATOR1\",
  \"sectionTitle\": \"Creators\", \"sectionIsActive\": true,
  \"sectionId\": 2, \"sectionDepth\": 3, \"sectionRecords\": \[ {
  \"recordId\": 808, \"thumbnail\": \"\", \"viewOrder\": 0,
  \"isActive\": true, \"itemId\":
  \"3c9f3fc1-9233-4e77-986d-2710e26b020e\", \"showInAndroid\": true,
  \"showInIos\": true, \"showInPwa\": true, \"feed_type\": \"POPULAR
  CREATORS\", \"rich_deeplink\":
  \"https://www.coolfie.io/profile/3c9f3fc1-9233-4e77-986d-2710e26b020e\"
  }, { \"recordId\": 652, \"title\": \"Chethan\", \"description\":
  \"des-che\", \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/46f49c7a1eafe5e4f39221c8cf8a0ae6.png\",
  \"viewOrder\": 2, \"isActive\": true, \"itemId\":
  \"4e8e77e4-a882-4f0d-b6d8-f4c1aa91eba4\", \"showInAndroid\": true,
  \"showInIos\": true, \"showInPwa\": true, \"verified\": true,
  \"deeplink_url\":
  \"https://qa-share.myjosh.in/profile/4e8e77e4-a882-4f0d-b6d8-f4c1aa91eba4\",
  \"feed_type\": \"POPULAR CREATORS\", \"is_verified\": true,
  \"rich_deeplink\":
  \"http://www.coolfie.io/profile/4e8e77e4-a882-4f0d-b6d8-f4c1aa91eba4\"
  }, { \"recordId\": 716, \"title\": \"ಚೆಥನ್ ಬಳಕೆದಾರ\", \"description\":
  \"des-chethan\", \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/d972f563d847d39ee8d606635ccdbb61.png\",
  \"viewOrder\": 2, \"subtitle\": \"sub-chethan\", \"isActive\": true,
  \"itemId\": \"b9706983-5936-4cb8-b401-619638eb02b8\",
  \"showInAndroid\": true, \"showInIos\": true, \"showInPwa\": true,
  \"verified\": false, \"deeplink_url\":
  \"https://qa-share.myjosh.in/profile/b9706983-5936-4cb8-b401-619638eb02b8\",
  \"feed_type\": \"POPULAR CREATORS\", \"is_verified\": false,
  \"rich_deeplink\":
  \"https://www.coolfie.io/profile/b9706983-5936-4cb8-b401-619638eb02b8\"
  }, { \"recordId\": 745, \"title\": \"ram pavan\", \"description\":
  \"rampavan\", \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/6567de379482dc7c9c834db33df60996.png\",
  \"viewOrder\": 4, \"subtitle\": \"ramm\", \"isActive\": true,
  \"itemId\": \"34b0976d-b9d5-48eb-b4eb-a83c16799a37\",
  \"showInAndroid\": true, \"showInIos\": true, \"showInPwa\": true,
  \"verified\": false, \"deeplink_url\":
  \"https://qa-share.myjosh.in/profile/34b0976d-b9d5-48eb-b4eb-a83c16799a37\",
  \"feed_type\": \"POPULAR CREATORS\", \"is_verified\": false,
  \"rich_deeplink\":
  \"http://www.coolfie.io/profile/34b0976d-b9d5-48eb-b4eb-a83c16799a37\"
  }, { \"recordId\": 1008, \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/acb638a74b929f0082dcdd643270a152.png\",
  \"viewOrder\": 10, \"isActive\": true, \"itemId\":
  \"23d788e1-e6bf-469f-8087-f20c1a98658a\", \"showInAndroid\": true,
  \"showInIos\": true, \"showInPwa\": true, \"feed_type\": \"POPULAR
  CREATORS\", \"rich_deeplink\":
  \"https://www.coolfie.io/profile/23d788e1-e6bf-469f-8087-f20c1a98658a\"
  } \] }, \"Creator4\": { \"sectionName\": \"Creator4\",
  \"sectionTitle\": \"sec-creator4\", \"sectionIsActive\": true,
  \"sectionId\": 53, \"sectionDepth\": 205, \"sectionRecords\": \[ {
  \"recordId\": 770, \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/cfc59a4737c054e1f0e5fcd04d5d9131.png\",
  \"viewOrder\": 0, \"isActive\": true, \"itemId\":
  \"9da6b1be-238e-479c-87b3-be34ef6a639c\", \"showInAndroid\": true,
  \"showInIos\": true, \"showInPwa\": true, \"feed_type\": \"POPULAR
  CREATORS\", \"rich_deeplink\":
  \"https://www.coolfie.io/profile/9da6b1be-238e-479c-87b3-be34ef6a639c\"
  }, { \"recordId\": 777, \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/01d8fe2c28e3b2edcf5cf3ade1e19443.png\",
  \"viewOrder\": 1, \"isActive\": true, \"itemId\":
  \"9da6b1be-238e-479c-87b3-be34ef6a639c\", \"showInAndroid\": true,
  \"showInIos\": true, \"showInPwa\": true, \"feed_type\": \"POPULAR
  CREATORS\", \"rich_deeplink\":
  \"https://www.coolfie.io/profile/9da6b1be-238e-479c-87b3-be34ef6a639c\"
  } \] }, \"sec-creator 3\": { \"sectionName\": \"sec-creator 3\",
  \"sectionTitle\": \"title-sec-creator3\", \"sectionIsActive\": false,
  \"sectionId\": 51, \"sectionDepth\": 203, \"sectionRecords\": \[ {
  \"recordId\": 761, \"thumbnail\": \"\", \"viewOrder\": 2,
  \"isActive\": true, \"itemId\":
  \"9da6b1be-238e-479c-87b3-be34ef6a639c\", \"verified\": false,
  \"feed_type\": \"POPULAR CREATORS\", \"is_verified\": false } \] } },
  \"TRENDING_DUET\": { \"TRENDING_DUET2\": { \"sectionName\":
  \"TRENDING_DUET2\", \"sectionTitle\": \"sec-trending_duet\",
  \"sectionIsActive\": true, \"sectionId\": 35, \"sectionDepth\": 13,
  \"sectionRecords\": \[ { \"recordId\": 603, \"title\":
  \"Trend-duetpg1\", \"description\": \"des-trend-duetpg1\",
  \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/076e3caed758a1c18c91a0e9cae3368f.png\",
  \"viewOrder\": 1, \"isActive\": true, \"itemId\":
  \"eb04c315-f511-4596-aecf-6bdea4ee6d3d\", \"deeplink_url\":
  \"https://qa-share.myjosh.in/duet/eb04c315-f511-4596-aecf-6bdea4ee6d3d\",
  \"feed_type\": \"TRENDING_DUET\", \"rich_deeplink\":
  \"https://qa-share.myjosh.in/duet/eb04c315-f511-4596-aecf-6bdea4ee6d3d\"
  }, { \"recordId\": 992, \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/f3780e91aa800e01fccd179e7cdab98a.png\",
  \"viewOrder\": 2, \"isActive\": true, \"itemId\":
  \"c624a56f-20c2-444a-9cba-d02b7fa7eba7\", \"showInAndroid\": true,
  \"showInIos\": true, \"showInPwa\": true, \"feed_type\":
  \"TRENDING_DUET\", \"rich_deeplink\":
  \"https://qa-share.myjosh.in/duet/c624a56f-20c2-444a-9cba-d02b7fa7eba7\"
  }, { \"recordId\": 762, \"thumbnail\": \"\", \"viewOrder\": 3,
  \"isActive\": true, \"itemId\":
  \"db55c2ce-3146-499e-8ffb-40da08237569\", \"showInAndroid\": true,
  \"showInIos\": true, \"showInPwa\": true, \"feed_type\":
  \"TRENDING_DUET\", \"rich_deeplink\":
  \"https://qa-share.myjosh.in/duet/db55c2ce-3146-499e-8ffb-40da08237569\"
  } \] }, \"Trending_duet3\": { \"sectionName\": \"Trending_duet3\",
  \"sectionTitle\": \"duet section not video\", \"sectionIsActive\":
  true, \"sectionId\": 55, \"sectionDepth\": 1001, \"sectionRecords\":
  \[ { \"recordId\": 795, \"title\": \"video 1\", \"description\": \"\",
  \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/076e3caed758a1c18c91a0e9cae3368f.png\",
  \"viewOrder\": 0, \"subtitle\": \"\", \"isActive\": true,
  \"deeplink_url\":
  \"https://qa-share.myjosh.in/video/79d74d29-8ea3-4240-828b-f61ce2c70219\",
  \"feed_type\": \"TRENDING_DUET\", \"rich_deeplink\":
  \"https://qa-share.myjosh.in/video/79d74d29-8ea3-4240-828b-f61ce2c70219\"
  }, { \"recordId\": 796, \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/bdf3bf1da3405725be763540d6601144.png\",
  \"viewOrder\": 1, \"isActive\": true, \"itemId\":
  \"79d74d29-8ea3-4240-828b-f61ce2c70219\", \"feed_type\":
  \"TRENDING_DUET\", \"rich_deeplink\":
  \"https://qa-share.myjosh.in/video/79d74d29-8ea3-4240-828b-f61ce2c70219\"
  } \] }, \"TRENDING_DUET1\": { \"sectionName\": \"TRENDING_DUET1\",
  \"sectionTitle\": \"Trending Duet\", \"sectionIsActive\": true,
  \"sectionId\": 6, \"sectionDepth\": 12, \"sectionRecords\": \[ {
  \"recordId\": 682, \"title\": \"duet 2_4_15\", \"description\":
  \"des-duet\", \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/ba45c8f60456a672e003a875e469d0eb.png\",
  \"viewOrder\": 2, \"subtitle\": \"sub-duet\", \"isActive\": true,
  \"itemId\": \"e934d6f0-1792-4a5b-8126-aa83c81b3d6d\",
  \"deeplink_url\":
  \"https://qa-share.myjosh.in/duet/e934d6f0-1792-4a5b-8126-aa83c81b3d6d\",
  \"feed_type\": \"TRENDING_DUET\", \"rich_deeplink\":
  \"https://qa-share.myjosh.in/duet/e934d6f0-1792-4a5b-8126-aa83c81b3d6d\"
  }, { \"recordId\": 661, \"title\": \"duet_pg04\", \"description\":
  \"des-2-dec-2020\", \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/bdf3bf1da3405725be763540d6601144.png\",
  \"viewOrder\": 4, \"isActive\": true, \"itemId\":
  \"fba7a246-ac9e-4449-b843-c396033318e0\", \"showInAndroid\": true,
  \"showInIos\": true, \"deeplink_url\":
  \"https://qa-share.myjosh.in/duet/fba7a246-ac9e-4449-b843-c396033318e0\",
  \"feed_type\": \"TRENDING_DUET\", \"rich_deeplink\":
  \"https://qa-share.myjosh.in/duet/fba7a246-ac9e-4449-b843-c396033318e0\"
  }, { \"recordId\": 1009, \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/acb638a74b929f0082dcdd643270a152.png\",
  \"viewOrder\": 5, \"isActive\": true, \"itemId\":
  \"cdc2bfc3-7268-439d-80f2-482bac7151b1\", \"showInAndroid\": true,
  \"showInIos\": true, \"showInPwa\": true, \"feed_type\":
  \"TRENDING_DUET\", \"rich_deeplink\":
  \"https://qa-share.myjosh.in/duet/cdc2bfc3-7268-439d-80f2-482bac7151b1\"
  } \] } }, \"CATEGORIES\": { \"CATEGORY2\": { \"sectionName\":
  \"CATEGORY2\", \"sectionTitle\": \"sec-Categories2\",
  \"sectionIsActive\": true, \"sectionId\": 34, \"sectionDepth\": 9,
  \"sectionRecords\": \[ { \"recordId\": 773, \"title\": \"r775cat\",
  \"description\": \"des-cat\", \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/be0cc9c49f03ddeedf6cda3bdb35c111.png\",
  \"viewOrder\": 0, \"subtitle\": \"sub-catdan\", \"isActive\": true,
  \"showInAndroid\": true, \"showInIos\": true, \"showInPwa\": true,
  \"deeplink_url\":
  \"https://qa-api.myjosh.in/search/category?q=Dance&lang_code=en\",
  \"feed_type\": \"CATEGORIES\", \"rich_deeplink\":
  \"http://www.coolfie.io/category/Dance\" }, { \"recordId\": 1010,
  \"title\": \"Music\", \"description\": \"just do it\", \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/acb638a74b929f0082dcdd643270a152.png\",
  \"viewOrder\": 4, \"subtitle\": \"music for ever\", \"isActive\":
  true, \"showInAndroid\": true, \"showInIos\": true, \"showInPwa\":
  true, \"deeplink_url\":
  \"https://qa-api.myjosh.in/search/category?q=Music&lang_code=en\",
  \"feed_type\": \"CATEGORIES\", \"rich_deeplink\":
  \"http://www.coolfie.io/category/Music\" } \] }, \"CATEGORY1\": {
  \"sectionName\": \"CATEGORY1\", \"sectionTitle\": \"Categories\",
  \"sectionIsActive\": true, \"sectionId\": 5, \"sectionDepth\": 8,
  \"sectionRecords\": \[ { \"recordId\": 5, \"title\": \"Glamour\",
  \"description\": \"glam-des\", \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/76bb3405f6.png\",
  \"viewOrder\": 0, \"subtitle\": \"Glam-sub\", \"isActive\": true,
  \"showInAndroid\": true, \"showInIos\": true, \"showInPwa\": true,
  \"deeplink_url\":
  \"https://qa-api.coolfie.io/search/category?q=Glamour&lang_code=en\",
  \"feed_type\": \"CATEGORIES\", \"rich_deeplink\":
  \"http://www.coolfie.io/category/Glamour\" }, { \"recordId\": 681,
  \"title\": \"dance-2-4-15\", \"description\": \"des-dance\",
  \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/be0cc9c49f03ddeedf6cda3bdb35c111.png\",
  \"viewOrder\": 0, \"subtitle\": \"sub-dance\", \"isActive\": true,
  \"showInAndroid\": true, \"showInIos\": true, \"showInPwa\": true,
  \"deeplink_url\":
  \"https://qa-api.myjosh.in/search/category?q=Dance&lang_code=en\",
  \"feed_type\": \"CATEGORIES\", \"rich_deeplink\":
  \"http://www.coolfie.io/category/Dance\" }, { \"recordId\": 7,
  \"title\": \"Music\", \"description\": \"\", \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/a234897dc552154950c23ea8ea63f62f.png\",
  \"viewOrder\": 0, \"isActive\": true, \"showInAndroid\": true,
  \"showInIos\": true, \"showInPwa\": true, \"deeplink_url\":
  \"https://qa-api.myjosh.in/search/category?q=Music&lang_code=en\",
  \"feed_type\": \"CATEGORIES\", \"rich_deeplink\":
  \"http://www.coolfie.io/category/Music\" } \] } }, \"FEED\": {
  \"FEED1\": { \"sectionName\": \"FEED1\", \"sectionTitle\": \"Feed\",
  \"sectionIsActive\": true, \"sectionId\": 4, \"sectionDepth\": 6,
  \"sectionRecords\": \[ { \"recordId\": 667, \"title\": \"Latest 2\",
  \"description\": \"des-latest2\", \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/5b3ac2b4d713c14de2b678e30ea9af61.png\",
  \"viewOrder\": 1, \"isActive\": true, \"showInAndroid\": true,
  \"showInIos\": true, \"showInPwa\": true, \"deeplink_url\":
  \"https://qa-api.myjosh.in/feed/latest/\", \"feed_type\": \"FEED\",
  \"rich_deeplink\": \"https://www.coolfie.io/feed/latest/\" }, {
  \"recordId\": 591, \"title\": \"Trending\", \"description\":
  \"des-fresh\", \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/562957eaeb146a38e816413b1d9ca7fb.png\",
  \"viewOrder\": 1, \"isActive\": true, \"showInAndroid\": true,
  \"showInIos\": true, \"showInPwa\": true, \"deeplink_url\":
  \"https://qa-api.myjosh.in/feed/trending/\", \"feed_type\": \"FEED\",
  \"rich_deeplink\": \"https://www.coolfie.io/feed/trending/\" }, {
  \"recordId\": 709, \"title\": \"Latest\", \"description\":
  \"des-latest\", \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/562957eaeb146a38e816413b1d9ca7fb.png\",
  \"viewOrder\": 1, \"subtitle\": \"sub-latest\", \"isActive\": true,
  \"showInAndroid\": true, \"showInIos\": true, \"showInPwa\": true,
  \"deeplink_url\": \"https://qa-api.myjosh.in/feed/latest/\",
  \"feed_type\": \"FEED\", \"rich_deeplink\":
  \"https://www.coolfie.io/feed/latest/\" }, { \"recordId\": 656,
  \"title\": \"Fresh\", \"description\": \"des-trending\",
  \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/562957eaeb146a38e816413b1d9ca7fb.png\",
  \"viewOrder\": 3, \"isActive\": true, \"showInAndroid\": true,
  \"showInIos\": true, \"showInPwa\": true, \"deeplink_url\":
  \"https://qa-api.myjosh.in/feed/latest/\", \"feed_type\": \"FEED\",
  \"rich_deeplink\": \"https://qa-api.myjosh.in/feed/latest/\" }, {
  \"recordId\": 659, \"title\": \"trending 3\", \"description\":
  \"des-trend 3\", \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/562957eaeb146a38e816413b1d9ca7fb.png\",
  \"viewOrder\": 4, \"isActive\": true, \"showInAndroid\": true,
  \"showInIos\": true, \"showInPwa\": true, \"deeplink_url\":
  \"https://qa-api.myjosh.in/feed/trending/\", \"feed_type\": \"FEED\",
  \"rich_deeplink\": \"https://www.coolfie.io/feed/trending/\" } \] },
  \"FEED2\": { \"sectionName\": \"FEED2\", \"sectionTitle\":
  \"sec-feed2\", \"sectionIsActive\": true, \"sectionId\": 33,
  \"sectionDepth\": 7, \"sectionRecords\": \[ { \"recordId\": 811,
  \"title\": \"latest8.5\", \"description\": \"deslatest8.5\",
  \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/562957eaeb146a38e816413b1d9ca7fb.png\",
  \"viewOrder\": 0, \"subtitle\": \"sublatest8.5\", \"isActive\": true,
  \"showInAndroid\": true, \"showInIos\": true, \"showInPwa\": true,
  \"deeplink_url\": \"https://qa-api.myjosh.in/feed/latest/\",
  \"feed_type\": \"FEED\", \"rich_deeplink\":
  \"https://www.coolfie.io/feed/latest/\" }, { \"recordId\": 772,
  \"title\": \"r775 latest\", \"description\": \"des-latest\",
  \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/562957eaeb146a38e816413b1d9ca7fb.png\",
  \"viewOrder\": 0, \"subtitle\": \"sub-latest\", \"isActive\": true,
  \"showInAndroid\": true, \"showInIos\": true, \"showInPwa\": true,
  \"deeplink_url\": \"https://qa-api.myjosh.in/feed/latest/\",
  \"feed_type\": \"FEED\", \"rich_deeplink\":
  \"https://www.coolfie.io/feed/latest/\" }, { \"recordId\": 766,
  \"title\": \"newR8.6 latest\", \"description\": \"des
  -newr8.6-latest\", \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/5b3ac2b4d713c14de2b678e30ea9af61.png\",
  \"viewOrder\": 0, \"subtitle\": \"sub - newr8.6-latest\",
  \"isActive\": true, \"showInAndroid\": true, \"showInIos\": true,
  \"showInPwa\": true, \"deeplink_url\":
  \"https://qa-api.myjosh.in/feed/latest/\", \"feed_type\": \"FEED\",
  \"rich_deeplink\": \"https://www.coolfie.io/feed/latest/\" }, {
  \"recordId\": 1011, \"title\": \"latest\", \"description\": \"go fr
  latest\", \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/acb638a74b929f0082dcdd643270a152.png\",
  \"viewOrder\": 4, \"subtitle\": \"latest one\", \"isActive\": true,
  \"showInAndroid\": true, \"showInIos\": true, \"showInPwa\": true,
  \"deeplink_url\": \"https://qa-api.myjosh.in/feed/latest/\",
  \"feed_type\": \"FEED\", \"rich_deeplink\":
  \"http://www.coolfie.io/category/latest/\" } \] } }, \"POPULAR
  HASHTAG\": { \"HASHTAG1\": { \"sectionName\": \"HASHTAG1\",
  \"sectionTitle\": \"Popular Hashtags\", \"sectionIsActive\": true,
  \"sectionId\": 3, \"sectionDepth\": 4, \"sectionRecords\": \[ {
  \"recordId\": 930, \"title\": \"newhashtagformat\", \"description\":
  \"\", \"thumbnail\": \"\", \"isChallenge\": true, \"viewOrder\": 1,
  \"subtitle\": \"\", \"isActive\": true, \"showInAndroid\": true,
  \"showInIos\": true, \"showInPwa\": true, \"deeplink_url\":
  \"https://qa-api.coolfie.io/search/tags?q=motivationchallenge&lang_code=en\",
  \"feed_type\": \"POPULAR HASHTAG\", \"rich_deeplink\":
  \"https://www.coolfie.io/tags/motivationchallenge\" }, { \"recordId\":
  679, \"title\": \"hash_3_0_14\", \"description\": \"des-hash-3-0-14\",
  \"thumbnail\": \"\", \"isChallenge\": false, \"viewOrder\": 2,
  \"subtitle\": \"sub-hash-3-0-14\", \"isActive\": true,
  \"showInAndroid\": true, \"showInIos\": true, \"showInPwa\": true,
  \"deeplink_url\":
  \"https://qa-api.myjosh.in/search/tags?q=motivationchallenge&lang_code=en\",
  \"feed_type\": \"POPULAR HASHTAG\", \"rich_deeplink\":
  \"https://www.coolfie.io/tags/motivationchallenge\" }, { \"recordId\":
  254, \"title\": \"friendship_challenge\", \"isChallenge\": true,
  \"viewOrder\": 3, \"isActive\": true, \"showInAndroid\": true,
  \"showInIos\": true, \"showInPwa\": true, \"deeplink_url\":
  \"https://qa-api.myjosh.in/search/tags?q=friendship_challenge&lang_code=en\",
  \"feed_type\": \"POPULAR HASHTAG\", \"rich_deeplink\":
  \"https://qa-share.myjosh.in/challenge/e4b1c97e-f2c6-46e2-86b7-9221585b0d78\"
  }, { \"recordId\": 649, \"title\": \"funnydance\", \"description\":
  \"\", \"thumbnail\": \"\", \"isChallenge\": true, \"viewOrder\": 5,
  \"isActive\": true, \"showInAndroid\": true, \"showInIos\": true,
  \"showInPwa\": true, \"deeplink_url\":
  \"https://qa-api.myjosh.in/search/tags?q=funnydance&lang_code=en\",
  \"feed_type\": \"POPULAR HASHTAG\", \"rich_deeplink\":
  \"http://qa-share.myjosh.in/challenge/a32cb3c6-f657-4e1b-a046-c0753d272e4c\"
  }, { \"recordId\": 639, \"title\": \"Josh Viral Star\",
  \"description\": \"test\", \"thumbnail\": \"\", \"isChallenge\": true,
  \"viewOrder\": 10, \"isActive\": true, \"showInAndroid\": true,
  \"showInIos\": true, \"showInPwa\": true, \"deeplink_url\":
  \"https://qa-api.coolfie.io/search/tags?q=JoshStar&lang_code=en\",
  \"feed_type\": \"POPULAR HASHTAG\", \"rich_deeplink\":
  \"http://qa-share.myjosh.in/challenge/c4e53e22-3575-417c-999a-760118d14177\"
  } \] }, \"HASHTAG2\": { \"sectionName\": \"HASHTAG2\",
  \"sectionTitle\": \"sec-hashtag2\", \"sectionIsActive\": true,
  \"sectionId\": 32, \"sectionDepth\": 5, \"sectionRecords\": \[ {
  \"recordId\": 717, \"title\": \"friends_cup\", \"description\": \"\",
  \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/98cc9f342c9cb2f489f70e138f49f734.png\",
  \"isChallenge\": true, \"viewOrder\": 1, \"subtitle\": \"cup\",
  \"isActive\": true, \"showInAndroid\": true, \"showInIos\": true,
  \"showInPwa\": true, \"deeplink_url\":
  \"https://qa-api.myjosh.in/search/tags?q=friendship_challenge&lang_code=en\",
  \"feed_type\": \"POPULAR HASHTAG\", \"rich_deeplink\":
  \"https://qa-share.myjosh.in/challenge/e4b1c97e-f2c6-46e2-86b7-9221585b0d78\"
  }, { \"recordId\": 1012, \"title\": \"career\", \"description\": \"one
  not one\", \"thumbnail\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/acb638a74b929f0082dcdd643270a152.png\",
  \"isChallenge\": false, \"viewOrder\": 3, \"subtitle\": \"career
  one\", \"isActive\": true, \"showInAndroid\": true, \"showInIos\":
  true, \"showInPwa\": true, \"deeplink_url\":
  \"https://qa-api.myjosh.in/search/tags?q=motivationchallenge&lang_code=en\",
  \"feed_type\": \"POPULAR HASHTAG\", \"rich_deeplink\":
  \"https://www.coolfie.io/tags/motivationchallenge\" } \] } } } }

- **Request Method and URL:**

  POST : https://qa-gateway.coolfie.io/api/v1/zerosearch/version/update

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/zerosearch/version/update\' \\

- **Success Response:**

  json{ \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.14.11.40\", \"code\": 200 }, \"data\": \[\] }

- **Request Method and URL:**

  POST : https://qa-gateway.coolfie.io/api/v1/fonts/cms/add?lang_code=en

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/fonts/cms/add?lang_code=en\' \\

  \--form \'font_name=\"Font-test-2\"\' \\

  \--form \'mime_type=\"ttf\"\' \\

  \--form \'width=\"267\"\' \\

  \--form \'height=\"120\"\' \\

  \--form \'is_bold_style_supported=\"true\"\' \\

  \--form \'viewOrder=\"40\"\' \\

  \--form \'thumbNailUrl=@\"/home/varikutitheja/Desktop/test.png\"\' \\

  \--form \'fontUrl=@\"/home/varikutitheja/Desktop/test.ttf\"\'

- **Success Response:**

  json{ \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.14.11.40\", \"code\": 200 }, \"data\": \[\] }

- **Request Method and URL:**

  POST : https://qa-gateway.coolfie.io/api/v1/fonts/cms/update/0

- **Curl Request:**

  curl \--location \--request POST
  \'<https://qa-gateway.coolfie.io/api/v1/fonts/cms/update/0>\' \\

  \--form \'font_name=\"\"\' \\

  \--form \'mime_type=\"ttf\"\' \\

  \--form \'width=\"53\"\' \\

  \--form \'height=\"50\"\' \\

  \--form \'is_bold_style_supported=\"true\"\' \\

  \--form \'viewOrder=\"\"\' \\

  \--form \'thumbNailUrl=@\"/home/varikutitheja/Desktop/default.png\"\'

- **Success Response:**

  json{ \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.14.11.40\", \"code\": 200 }, \"data\": \[\] }

- **Request Method and URL:**

  DELETE : https://qa-gateway.coolfie.io/api/v1/fonts/cms/remove/63

- **Curl Request:**

  curl \--location \--request DELETE
  \'https://qa-gateway.coolfie.io/api/v1/fonts/cms/remove/63\' \\

- **Success Response:**

  json{ \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.14.11.40\", \"code\": 200 }, \"data\": \[\] }

- **Request Method and URL:**

  GET : https://qa-gateway.coolfie.io/api/v1/fonts/list?lang_code=en,te

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/fonts/list?lang_code=en,te\' \\

  \--header \'Content-Type: application/json\' \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { \"count\": 9, \"rows\":
  \[ { \"id\": \"0\", \"font_name\": \"\", \"url\": \"\",
  \"thumbnail_url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/font-thumbnails/default.png\",
  \"mime_type\": \"ttf\", \"width\": 53, \"height\": 50,
  \"is_bold_style_supported\": true, \"auto_download\": false }, {
  \"id\": \"20\", \"font_name\": \"OpenSans\", \"url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/OpenSans_ExtraBold.ttf\",
  \"thumbnail_url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/font-thumbnails/OpenSans.png\",
  \"mime_type\": \"ttf\", \"width\": 267, \"height\": 120,
  \"is_bold_style_supported\": false, \"auto_download\": true }, {
  \"id\": \"21\", \"font_name\": \"OstrichSans\", \"url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/OstrichSans-Heavy.ttf\",
  \"thumbnail_url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/font-thumbnails/OstrichSans.png\",
  \"mime_type\": \"ttf\", \"width\": 192, \"height\": 120,
  \"is_bold_style_supported\": false, \"auto_download\": true }, {
  \"id\": \"22\", \"font_name\": \"YesevaOne\", \"url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/YesevaOne-Regular_v2.ttf\",
  \"thumbnail_url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/font-thumbnails/YesevaOne.png\",
  \"mime_type\": \"ttf\", \"width\": 258, \"height\": 120,
  \"is_bold_style_supported\": false, \"auto_download\": true }, {
  \"id\": \"66\", \"font_name\": \"Font-test-2\", \"url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/c2FtcGxlXzY0MMOXNDI2.png\",
  \"thumbnail_url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/font-thumbnails/dGVzdCptdWx0aXBseQ==.jpg\",
  \"mime_type\": \"ttf\", \"width\": 267, \"height\": 120,
  \"is_bold_style_supported\": true, \"auto_download\": true }, {
  \"id\": \"67\", \"font_name\": \"Font-test-3\", \"url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/c2FtcGxlXzY0MMOXNDI2.png\",
  \"thumbnail_url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/font-thumbnails/dGVzdCptdWx0aXBseQ==.jpg\",
  \"mime_type\": \"ttf\", \"width\": 267, \"height\": 120,
  \"is_bold_style_supported\": true, \"auto_download\": true }, {
  \"id\": \"47\", \"font_name\": \"Ramabhadra\", \"url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/Ramabhadra.ttf\",
  \"thumbnail_url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/font-thumbnails/Ramabhadra.png\",
  \"mime_type\": \"ttf\", \"width\": 207, \"height\": 120,
  \"is_bold_style_supported\": false }, { \"id\": \"48\", \"font_name\":
  \"Ramaraja\", \"url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/Ramaraja-Regular.ttf\",
  \"thumbnail_url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/font-thumbnails/Ramaraja.png\",
  \"mime_type\": \"ttf\", \"width\": 207, \"height\": 120,
  \"is_bold_style_supported\": false }, { \"id\": \"51\", \"font_name\":
  \"Pothana2000\", \"url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/Pothana2000.ttf\",
  \"thumbnail_url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/font-thumbnails/Pothana2000.png\",
  \"mime_type\": \"ttf\", \"width\": 243, \"height\": 120,
  \"is_bold_style_supported\": false } \], \"pageNumber\": 1,
  \"next_page_url\":
  \"https://qa-gateway.coolfie.io/api/v1/fonts/list?pageNumber=1&lang_code=en,te&pageSize=10\"
  } }

- **Request Method and URL:**

  GET :
  https://qa-gateway.coolfie.io/api/v1/fonts/cms/list?lang_code=en,te

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/fonts/cms/list?lang_code=en,te\'
  \\

  \--header \'Content-Type: application/json\' \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { \"count\": 9, \"rows\":
  \[ { \"id\": \"0\", \"font_name\": \"\", \"url\": \"\",
  \"thumbnail_url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/font-thumbnails/default.png\",
  \"mime_type\": \"ttf\", \"width\": 53, \"height\": 50,
  \"is_bold_style_supported\": true, \"auto_download\": false,
  \"isDefault\": true }, { \"id\": \"20\", \"font_name\": \"OpenSans\",
  \"url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/OpenSans_ExtraBold.ttf\",
  \"thumbnail_url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/font-thumbnails/OpenSans.png\",
  \"mime_type\": \"ttf\", \"width\": 267, \"height\": 120,
  \"is_bold_style_supported\": false, \"auto_download\": true,
  \"isDefault\": false }, { \"id\": \"21\", \"font_name\":
  \"OstrichSans\", \"url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/OstrichSans-Heavy.ttf\",
  \"thumbnail_url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/font-thumbnails/OstrichSans.png\",
  \"mime_type\": \"ttf\", \"width\": 192, \"height\": 120,
  \"is_bold_style_supported\": false, \"auto_download\": true,
  \"isDefault\": false }, { \"id\": \"22\", \"font_name\":
  \"YesevaOne\", \"url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/YesevaOne-Regular_v2.ttf\",
  \"thumbnail_url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/font-thumbnails/YesevaOne.png\",
  \"mime_type\": \"ttf\", \"width\": 258, \"height\": 120,
  \"is_bold_style_supported\": false, \"auto_download\": true,
  \"isDefault\": false }, { \"id\": \"66\", \"font_name\":
  \"Font-test-2\", \"url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/c2FtcGxlXzY0MMOXNDI2.png\",
  \"thumbnail_url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/font-thumbnails/dGVzdCptdWx0aXBseQ==.jpg\",
  \"mime_type\": \"ttf\", \"width\": 267, \"height\": 120,
  \"is_bold_style_supported\": true, \"auto_download\": true,
  \"isDefault\": false }, { \"id\": \"67\", \"font_name\":
  \"Font-test-3\", \"url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/c2FtcGxlXzY0MMOXNDI2.png\",
  \"thumbnail_url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/font-thumbnails/dGVzdCptdWx0aXBseQ==.jpg\",
  \"mime_type\": \"ttf\", \"width\": 267, \"height\": 120,
  \"is_bold_style_supported\": true, \"auto_download\": true,
  \"isDefault\": false }, { \"id\": \"47\", \"font_name\":
  \"Ramabhadra\", \"url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/Ramabhadra.ttf\",
  \"thumbnail_url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/font-thumbnails/Ramabhadra.png\",
  \"mime_type\": \"ttf\", \"width\": 207, \"height\": 120,
  \"is_bold_style_supported\": false, \"isDefault\": false }, { \"id\":
  \"48\", \"font_name\": \"Ramaraja\", \"url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/Ramaraja-Regular.ttf\",
  \"thumbnail_url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/font-thumbnails/Ramaraja.png\",
  \"mime_type\": \"ttf\", \"width\": 207, \"height\": 120,
  \"is_bold_style_supported\": false, \"isDefault\": false }, { \"id\":
  \"51\", \"font_name\": \"Pothana2000\", \"url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/Pothana2000.ttf\",
  \"thumbnail_url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/font-thumbnails/Pothana2000.png\",
  \"mime_type\": \"ttf\", \"width\": 243, \"height\": 120,
  \"is_bold_style_supported\": false, \"isDefault\": false } \] } }

- **Request Method and URL:**

  POST : https://qa-gateway.coolfie.io/api/v1/stickers/CAMERA/add

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/stickers/CAMERA/add\' \\

  \--form
  \'stickerUrl=@\"/home/varikutitheja/Desktop/10.d1/gateway_icons/Revised
  Stickers/0A86B840-EF49-4D5F-BF5F-0FBE89FFE75C.animatedsticker\"\' \\

  \--form
  \'thumbnailUrl=@\"/home/varikutitheja/Desktop/10.d1/gateway_icons/Revised
  Stickers/0A86B840-EF49-4D5F-BF5F-0FBE89FFE75C.png\"\' \\

  \--form \'mimeType=\"animatedsticker\"\' \\

  \--form \'isActive=\"true\"\' \\

  \--form \'assetId=\"72660e64-6ee9-11ec-8ed9-6b7f0e6e3196\"\' \\

  \--form \'stickerName=\"Dummy name\"\'

- **Success Response:**

  json{ \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.14.11.40\", \"code\": 200 }, \"data\": \[\] }

- **Request Method and URL:**

  POST : https://qa-gateway.coolfie.io/api/v1/stickers/CAMERA/1096

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/stickers/CAMERA/1096\' \\

  \--form \'isActive=\"false\"\' \\

  \--form
  \'thumbnailUrl=@\"/home/varikutitheja/Desktop/sample-files/sample_640×426.jpeg\"\'

- **Success Response:**

  json{ \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.14.11.40\", \"code\": 200 }, \"data\": \[\] }

- **Request Method and URL:**

  GET : https://qa-gateway.coolfie.io/api/v1/stickers/CAMERA/3319

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/stickers/CAMERA/3319\' \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { \"stickerId\": 3319,
  \"assetId\": \"41C973AE-CC3F-471A-8D7D-DEC59E3F81FC\",
  \"stickerName\": \"Poof\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/41C973AE-CC3F-471A-8D7D-DEC59E3F81FC.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/41C973AE-CC3F-471A-8D7D-DEC59E3F81FC.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true } }

- **Request Method and URL:**

  GET :
  https://qa-gateway.coolfie.io/api/v1/stickers/CAMERA/filters/list?isActive=true&mimeType=png

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/stickers/CAMERA/filters/list?isActive=true&mimeType=png\'
  \\

  \--data-raw \'\'

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { \"total\": 1139,
  \"count\": 25, \"rows\": \[ { \"stickerId\": 2353, \"assetId\":
  \"B4FE7C25-5067-4520-A280-596061660445\", \"stickerName\": \"#Karma\",
  \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/B4FE7C25-5067-4520-A280-596061660445.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/B4FE7C25-5067-4520-A280-596061660445.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 2375, \"assetId\":
  \"F17D8640-05DB-498F-88BA-535B1D2F2081\", \"stickerName\": \"#Karma\",
  \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/F17D8640-05DB-498F-88BA-535B1D2F2081.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/F17D8640-05DB-498F-88BA-535B1D2F2081.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 2258, \"assetId\":
  \"2C1D4153-D9D6-4BC5-B85C-E536BDD7AB5F\", \"stickerName\": \"100%
  Desi\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/2C1D4153-D9D6-4BC5-B85C-E536BDD7AB5F.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/2C1D4153-D9D6-4BC5-B85C-E536BDD7AB5F.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 2337, \"assetId\":
  \"67E1632C-AEB3-4E37-96E4-D751F0F9BED4\", \"stickerName\": \"100%
  Desi/ So% desi\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/67E1632C-AEB3-4E37-96E4-D751F0F9BED4.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/67E1632C-AEB3-4E37-96E4-D751F0F9BED4.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 2479, \"assetId\":
  \"178386B6-CA87-4384-B18C-BE0424A8CE42\", \"stickerName\": \"24
  Pargana\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/178386B6-CA87-4384-B18C-BE0424A8CE42.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/178386B6-CA87-4384-B18C-BE0424A8CE42.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3200, \"assetId\":
  \"08D4F0E9-1B0A-4A93-9C85-37A0FC8B7CDD\", \"stickerName\": \"8 Ball\",
  \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/08D4F0E9-1B0A-4A93-9C85-37A0FC8B7CDD.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/08D4F0E9-1B0A-4A93-9C85-37A0FC8B7CDD.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 2407, \"assetId\":
  \"A9E6EDB6-FD62-421B-8B59-E9150D4BBC7C\", \"stickerName\": \"Aahan\",
  \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/A9E6EDB6-FD62-421B-8B59-E9150D4BBC7C.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/A9E6EDB6-FD62-421B-8B59-E9150D4BBC7C.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 2429, \"assetId\":
  \"52F26CA2-2EFE-465D-8E1B-50D1ADD190BE\", \"stickerName\": \"Aai
  Shappath\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/52F26CA2-2EFE-465D-8E1B-50D1ADD190BE.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/52F26CA2-2EFE-465D-8E1B-50D1ADD190BE.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 2426, \"assetId\":
  \"AD7D8368-EF71-4290-A056-2CE5988068DE\", \"stickerName\": \"Aaichya
  Gavat Jabari \", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/AD7D8368-EF71-4290-A056-2CE5988068DE.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/AD7D8368-EF71-4290-A056-2CE5988068DE.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 2259, \"assetId\":
  \"2C2C665A-BBA8-4C00-8653-D4FFAE0E7A8A\", \"stickerName\": \"Aam
  Aadmi\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/2C2C665A-BBA8-4C00-8653-D4FFAE0E7A8A.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/2C2C665A-BBA8-4C00-8653-D4FFAE0E7A8A.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 2298, \"assetId\":
  \"D6987905-5F1B-4052-B0E5-4B27145662A6\", \"stickerName\": \"Aao Kabhi
  Haveli Pe\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/D6987905-5F1B-4052-B0E5-4B27145662A6.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/D6987905-5F1B-4052-B0E5-4B27145662A6.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 2395, \"assetId\":
  \"DC76BA38-5682-4837-9091-900F0127F0CC\", \"stickerName\": \"Abba
  Champeseru\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/DC76BA38-5682-4837-9091-900F0127F0CC.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/DC76BA38-5682-4837-9091-900F0127F0CC.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 2781, \"assetId\":
  \"CC0CCDEA-37A2-4FCB-9076-4E6C00E61E2F\", \"stickerName\": \"About To
  Puke\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/CC0CCDEA-37A2-4FCB-9076-4E6C00E61E2F.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/CC0CCDEA-37A2-4FCB-9076-4E6C00E61E2F.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 2773, \"assetId\":
  \"66000340-9111-42F1-BAA9-0E7192A11A46\", \"stickerName\": \"About To
  Puke\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/66000340-9111-42F1-BAA9-0E7192A11A46.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/66000340-9111-42F1-BAA9-0E7192A11A46.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 2410, \"assetId\":
  \"BC2A3F36-81F7-471E-AE24-20CD59A51C66\", \"stickerName\":
  \"Adaengappa\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/BC2A3F36-81F7-471E-AE24-20CD59A51C66.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/BC2A3F36-81F7-471E-AE24-20CD59A51C66.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 2468, \"assetId\":
  \"278D52C0-0B54-4A78-A5C4-616AA30EB40C\", \"stickerName\": \"Agra\",
  \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/278D52C0-0B54-4A78-A5C4-616AA30EB40C.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/278D52C0-0B54-4A78-A5C4-616AA30EB40C.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 2477, \"assetId\":
  \"28646B17-CC8E-4402-9DDF-1BBC58E1679B\", \"stickerName\":
  \"Ahmedabad\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/28646B17-CC8E-4402-9DDF-1BBC58E1679B.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/28646B17-CC8E-4402-9DDF-1BBC58E1679B.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 2283, \"assetId\":
  \"A4F2BE14-B315-4175-8279-A8BB9ED360AD\", \"stickerName\":
  \"Ainvayi\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/A4F2BE14-B315-4175-8279-A8BB9ED360AD.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/A4F2BE14-B315-4175-8279-A8BB9ED360AD.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 2941, \"assetId\":
  \"96961D43-5E17-4253-8112-829183DA44BE\", \"stickerName\": \"Air
  Blow\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/96961D43-5E17-4253-8112-829183DA44BE.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/96961D43-5E17-4253-8112-829183DA44BE.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3387, \"assetId\":
  \"21F80E2C-0C66-4158-9C2D-3B027370AB71\", \"stickerName\":
  \"Airplane\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/21F80E2C-0C66-4158-9C2D-3B027370AB71.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/21F80E2C-0C66-4158-9C2D-3B027370AB71.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3207, \"assetId\":
  \"2352EC38-7707-461D-892B-EAC1A64F955C\", \"stickerName\":
  \"Airpods\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/2352EC38-7707-461D-892B-EAC1A64F955C.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/2352EC38-7707-461D-892B-EAC1A64F955C.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 2456, \"assetId\":
  \"7F83DC4F-77D8-4CA0-8000-9EF7EBFB552B\", \"stickerName\": \"Ajmer\",
  \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/7F83DC4F-77D8-4CA0-8000-9EF7EBFB552B.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/7F83DC4F-77D8-4CA0-8000-9EF7EBFB552B.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 2488, \"assetId\":
  \"D9FE7B5A-8445-41C0-AD0D-B5497973D733\", \"stickerName\":
  \"Alapuzha\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/D9FE7B5A-8445-41C0-AD0D-B5497973D733.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/D9FE7B5A-8445-41C0-AD0D-B5497973D733.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3127, \"assetId\":
  \"1B7F0497-ED2D-470F-93BD-BB68A7E0BDD6\", \"stickerName\":
  \"Alcohol\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/1B7F0497-ED2D-470F-93BD-BB68A7E0BDD6.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/1B7F0497-ED2D-470F-93BD-BB68A7E0BDD6.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3125, \"assetId\":
  \"730671E5-2E6F-4A29-9701-0AF9D172A04D\", \"stickerName\": \"Alcohol
  Cheers\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/730671E5-2E6F-4A29-9701-0AF9D172A04D.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/730671E5-2E6F-4A29-9701-0AF9D172A04D.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true } \],
  \"next_page_url\":
  \"https://qa-gateway.coolfie.io/api/v1/stickers/CAMERA/filters/list?pageNumber=1&pageSize=10&mimeType=png&isActive=true\"
  } }

- **Request Method and URL:**

  GET : https://qa-gateway.coolfie.io/api/v1/stickers/CAMERA/12/15/list

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/stickers/CAMERA/12/15/list\' \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { \"total\": 95, \"count\":
  25, \"rows\": \[ { \"stickerId\": 3296, \"assetId\":
  \"304C23C0-DC83-4B79-97B3-3E80CD0C4A04\", \"stickerName\": \"Christmas
  Cookie\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/304C23C0-DC83-4B79-97B3-3E80CD0C4A04.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/304C23C0-DC83-4B79-97B3-3E80CD0C4A04.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3297, \"assetId\":
  \"9F3C279E-DAFD-4369-8C51-BD39961D6F67\", \"stickerName\": \"Christmas
  Bells\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/9F3C279E-DAFD-4369-8C51-BD39961D6F67.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/9F3C279E-DAFD-4369-8C51-BD39961D6F67.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3298, \"assetId\":
  \"ADA49A85-3002-4810-9446-9AFCC7DD3180\", \"stickerName\": \"Christmas
  Flakes\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/ADA49A85-3002-4810-9446-9AFCC7DD3180.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/ADA49A85-3002-4810-9446-9AFCC7DD3180.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3299, \"assetId\":
  \"66C91FC4-C359-45C8-B6A9-DDF270C6A570\", \"stickerName\": \"Christmas
  Tree\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/66C91FC4-C359-45C8-B6A9-DDF270C6A570.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/66C91FC4-C359-45C8-B6A9-DDF270C6A570.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3300, \"assetId\":
  \"B9D98A50-519A-4657-AACC-EBAB0806D48B\", \"stickerName\": \"Zzz\",
  \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/B9D98A50-519A-4657-AACC-EBAB0806D48B.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/B9D98A50-519A-4657-AACC-EBAB0806D48B.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3301, \"assetId\":
  \"2B4B50A0-C11B-4F21-B792-A1ED6947762B\", \"stickerName\":
  \"Exclamation\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/2B4B50A0-C11B-4F21-B792-A1ED6947762B.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/2B4B50A0-C11B-4F21-B792-A1ED6947762B.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3302, \"assetId\":
  \"079A26A0-E8C3-42B4-BECA-A9103896FFC9\", \"stickerName\": \"Yellow
  Flower\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/079A26A0-E8C3-42B4-BECA-A9103896FFC9.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/079A26A0-E8C3-42B4-BECA-A9103896FFC9.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3303, \"assetId\":
  \"8912FD71-311B-4D73-A999-492536597BC4\", \"stickerName\": \"Red
  Ball\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/8912FD71-311B-4D73-A999-492536597BC4.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/8912FD71-311B-4D73-A999-492536597BC4.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3304, \"assetId\":
  \"AFE74A39-5D2C-485A-B686-09DB38B339C8\", \"stickerName\": \"Point
  Left\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/AFE74A39-5D2C-485A-B686-09DB38B339C8.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/AFE74A39-5D2C-485A-B686-09DB38B339C8.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3305, \"assetId\":
  \"C383A7B1-6B82-4657-B829-4503E2D114DC\", \"stickerName\":
  \"Moustache\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/C383A7B1-6B82-4657-B829-4503E2D114DC.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/C383A7B1-6B82-4657-B829-4503E2D114DC.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3306, \"assetId\":
  \"DFDC4E57-B4A8-4C77-848A-47ED28045353\", \"stickerName\": \"Alert\",
  \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/DFDC4E57-B4A8-4C77-848A-47ED28045353.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/DFDC4E57-B4A8-4C77-848A-47ED28045353.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3307, \"assetId\":
  \"D12E2EC3-B246-4B5E-B583-F46CF5311282\", \"stickerName\": \"Iron
  Man\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/D12E2EC3-B246-4B5E-B583-F46CF5311282.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/D12E2EC3-B246-4B5E-B583-F46CF5311282.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3308, \"assetId\":
  \"EB563D2E-C30E-4D12-969B-299C88A107ED\", \"stickerName\": \"Flame\",
  \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/EB563D2E-C30E-4D12-969B-299C88A107ED.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/EB563D2E-C30E-4D12-969B-299C88A107ED.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3309, \"assetId\":
  \"2BD1472E-01D0-478D-927F-65DBC4896AE7\", \"stickerName\": \"Flower
  Bouquet\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/2BD1472E-01D0-478D-927F-65DBC4896AE7.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/2BD1472E-01D0-478D-927F-65DBC4896AE7.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3310, \"assetId\":
  \"2D0598B5-2CD8-419B-99F9-81B167968F8F\", \"stickerName\":
  \"Sunflower\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/2D0598B5-2CD8-419B-99F9-81B167968F8F.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/2D0598B5-2CD8-419B-99F9-81B167968F8F.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3311, \"assetId\":
  \"8748909F-D1B6-4E13-9EB5-3F00B4C5A71A\", \"stickerName\": \"I Love
  You\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/8748909F-D1B6-4E13-9EB5-3F00B4C5A71A.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/8748909F-D1B6-4E13-9EB5-3F00B4C5A71A.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3312, \"assetId\":
  \"D139CD6F-33F2-44D3-8470-5AC05003E221\", \"stickerName\": \"Diamond
  Ring\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/D139CD6F-33F2-44D3-8470-5AC05003E221.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/D139CD6F-33F2-44D3-8470-5AC05003E221.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3313, \"assetId\":
  \"6F136E19-ED95-48B4-A420-6DD789E74609\", \"stickerName\":
  \"Trumpet\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/6F136E19-ED95-48B4-A420-6DD789E74609.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/6F136E19-ED95-48B4-A420-6DD789E74609.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3314, \"assetId\":
  \"AE3CD476-F65E-46AE-B9BE-5ECAFA232E44\", \"stickerName\": \"Race
  Car\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/AE3CD476-F65E-46AE-B9BE-5ECAFA232E44.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/AE3CD476-F65E-46AE-B9BE-5ECAFA232E44.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3315, \"assetId\":
  \"D1892D67-9280-47D7-9FF5-7213A22F8FC4\", \"stickerName\": \"Bug\",
  \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/D1892D67-9280-47D7-9FF5-7213A22F8FC4.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/D1892D67-9280-47D7-9FF5-7213A22F8FC4.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3316, \"assetId\":
  \"33D4811D-9110-4F39-8D2E-682D306C3E75\", \"stickerName\": \"Stabbed
  Knife\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/33D4811D-9110-4F39-8D2E-682D306C3E75.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/33D4811D-9110-4F39-8D2E-682D306C3E75.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3317, \"assetId\":
  \"35A189ED-4337-4DCC-85BD-2D9809419085\", \"stickerName\": \"Smoke\",
  \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/35A189ED-4337-4DCC-85BD-2D9809419085.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/35A189ED-4337-4DCC-85BD-2D9809419085.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3318, \"assetId\":
  \"39A21E74-00C6-48F9-96B0-485114B6F8F5\", \"stickerName\": \"Grundy\",
  \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/39A21E74-00C6-48F9-96B0-485114B6F8F5.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/39A21E74-00C6-48F9-96B0-485114B6F8F5.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3319, \"assetId\":
  \"41C973AE-CC3F-471A-8D7D-DEC59E3F81FC\", \"stickerName\": \"Poof\",
  \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/41C973AE-CC3F-471A-8D7D-DEC59E3F81FC.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/41C973AE-CC3F-471A-8D7D-DEC59E3F81FC.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true }, {
  \"stickerId\": 3320, \"assetId\":
  \"43CFDE02-9332-41AD-B75E-E95F10BB34E6\", \"stickerName\": \"Shooting
  Star\", \"stickerUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/43CFDE02-9332-41AD-B75E-E95F10BB34E6.animatedsticker\",
  \"thumbnailUrl\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_stickers/43CFDE02-9332-41AD-B75E-E95F10BB34E6.png\",
  \"mimeType\": \"animatedsticker\", \"isActive\": true } \],
  \"next_page_url\":
  \"https://qa-gateway.coolfie.io/api/v1/stickers/CAMERA/12/15/list?pageNumber=1&pageSize=10\"
  } }

- **Request Method and URL:**

  DELETE : https://qa-gateway.coolfie.io/api/v1/stickers/CAMERA/1096

- **Curl Request:**

  curl \--location \--request DELETE \'https://qa-gateway.cool

- fie.io/api/v1/stickers/CAMERA/1096\' \\

- **Success Response:**

  json{ \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.14.11.40\", \"code\": 200 }, \"data\": \[\] }

- **Request Method and URL:**

  GET : https://qa-gateway.coolfie.io/api/v1/stickers/CAMERA/9/7/count

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/stickers/CAMERA/9/7/count\' \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": 0 }

- **Request Method and URL:**

  POST : https://qa-gateway.coolfie.io/api/v1/stickers/CAMERA/subtab/add

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/stickers/CAMERA/subtab/add\' \\

  \--header \'Content-Type: application/json\' \\

  \--data-raw \'{

  \"displayName\": \"Filter-2\",

  \"isActive\": true,

  \"langCode\": \"en\"

  }\'

- **Success Response:**

  json{ \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.14.11.40\", \"code\": 200 }, \"data\": \[\] }

- **Request Method and URL:**

  POST : https://qa-gateway.coolfie.io/api/v1/stickers/CAMERA/subtab/53

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/stickers/CAMERA/subtab/53\' \\

  \--header \'Content-Type: application/json\' \\

  \--data-raw \'{

  \"displayName\": \"Filter-2-Updated\",

  \"isActive\": true

  }\'

- **Success Response:**

  json{ \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.14.11.40\", \"code\": 200 }, \"data\": \[\] }

- **Request Method and URL:**

  DELETE :
  https://qa-gateway.coolfie.io/api/v1/stickers/COMMENT/subtab/13

- **Curl Request:**

  curl \--location \--request DELETE
  \'https://qa-gateway.coolfie.io/api/v1/stickers/COMMENT/subtab/13\' \\

- **Success Response:**

  json{ \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.14.11.40\", \"code\": 200 }, \"data\": \[\] }

- **Request Method and URL:**

  GET : https://qa-gateway.coolfie.io/api/v1/stickers/COMMENT/subtab/13

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/stickers/COMMENT/subtab/13\' \\

- **Success Response:**

  json{ \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.14.11.40\", \"code\": 200 }, \"data\": \[\] }

- **Request Method and URL:**

  GET :
  https://qa-gateway.coolfie.io/api/v1/stickers/COMMENT/subtab/list

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/stickers/COMMENT/subtab/list\'
  \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": \[ { \"subTabId\": 1,
  \"displayName\": \"Featured\", \"isActive\": true }, { \"subTabId\":
  2, \"displayName\": \"Stickers\", \"isActive\": true }, {
  \"subTabId\": 3, \"displayName\": \"Hindi\", \"langCode\": \"hi\",
  \"isActive\": true }, { \"subTabId\": 4, \"displayName\": \"Telugu\",
  \"langCode\": \"te\", \"isActive\": true }, { \"subTabId\": 5,
  \"displayName\": \"Malayalam\", \"langCode\": \"ml\", \"isActive\":
  true }, { \"subTabId\": 6, \"displayName\": \"Tamil\", \"langCode\":
  \"ta\", \"isActive\": true }, { \"subTabId\": 7, \"displayName\":
  \"Kannada\", \"langCode\": \"kn\", \"isActive\": true }, {
  \"subTabId\": 8, \"displayName\": \"Marathi\", \"langCode\": \"mr\",
  \"isActive\": true }, { \"subTabId\": 9, \"displayName\":
  \"Gujarati\", \"langCode\": \"gu\", \"isActive\": true }, {
  \"subTabId\": 10, \"displayName\": \"Bangla\", \"langCode\": \"bn\",
  \"isActive\": true }, { \"subTabId\": 12, \"displayName\": \"Food\",
  \"isActive\": true }, { \"subTabId\": 18, \"displayName\": \"r9dcom\",
  \"langCode\": \"en\", \"isActive\": true }, { \"subTabId\": 20,
  \"displayName\": \"r9d - en\", \"langCode\": \"en\", \"isActive\":
  true }, { \"subTabId\": 21, \"displayName\": \"r9 - hi\",
  \"langCode\": \"hi\", \"isActive\": true }, { \"subTabId\": 22,
  \"displayName\": \"r9d - no lang\", \"isActive\": true }, {
  \"subTabId\": 23, \"displayName\": \"r9-nolang\", \"isActive\": true
  }, { \"subTabId\": 24, \"displayName\": \"r12b\", \"langCode\":
  \"en\", \"isActive\": true } \] }

- **Request Method and URL:**

  GET :
  https://qa-gateway.coolfie.io/api/v1/stickers/COMMENT/tabs/9/subtab/list

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/stickers/COMMENT/tabs/9/subtab/list\'
  \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": \[ { \"subTabId\": 1,
  \"displayName\": \"Featured\", \"isActive\": true }, { \"subTabId\":
  3, \"displayName\": \"Hindi\", \"langCode\": \"hi\", \"isActive\":
  true }, { \"subTabId\": 20, \"displayName\": \"r9d - en\",
  \"langCode\": \"en\", \"isActive\": true }, { \"subTabId\": 24,
  \"displayName\": \"r12b\", \"langCode\": \"en\", \"isActive\": true }
  \] }

- **Request Method and URL:**

  POST :
  https://qa-gateway.coolfie.io/api/v1/stickers/COMMENT/tabs/9/mapSubTabs

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/stickers/COMMENT/tabs/9/mapSubTabs\'
  \\

  \--header \'Content-Type: application/json\' \\

  \--data-raw \'\[

  {

  \"subTabId\": 13,

  \"viewOrder\": 10

  },

  {

  \"subTabId\": 15,

  \"viewOrder\": 5

  }

  \]\'

- **Success Response:**

  json{ \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.14.11.40\", \"code\": 200 }, \"data\": \[\] }

- **Request Method and URL:**

  POST :
  https://qa-gateway.coolfie.io/api/v1/stickers/COMMENT/2/1/mapStickers

- **Curl Request:**

  curl \--location \--request POST
  \'<https://qa-gateway.coolfie.io/api/v1/stickers/COMMENT/2/1/mapStickers>\'
  \\

  \--header \'Content-Type: application/json\' \\

  \--data-raw \'\[

  {

  \"stickerId\": 2,

  \"viewOrder\": 10

  },

  {

  \"stickerId\": 3,

  \"viewOrder\": 20

  }

  \]\'

- **Success Response:**

  json{ \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.14.11.40\", \"code\": 200 }, \"data\": \[\] }

- **Request Method and URL:**

  POST :
  https://qa-gateway.coolfie.io/api/v1/stickers/COMMENT/2/version/update

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/stickers/COMMENT/2/version/update\'
  \\

- **Success Response:**

  json{ \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.14.11.40\", \"code\": 200 }, \"data\": \[\] }

- **Request Method and URL:**

  GET : https://qa-gateway.coolfie.io/api/v1/stickers/CAMERA/mimeTypes

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/stickers/CAMERA/mimeTypes\' \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": \[ \"png\",
  \"animatedsticker\", \"jpeg\" \] }

- **Request Method and URL:**

  GET :
  https://qa-gateway.coolfie.io/api/v1/stickers/tabs?lang_code=en&version=8102141&supported_external_tabs=bitmoji

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/stickers/tabs?lang_code=en&version=8102141&supported_external_tabs=bitmoji\'
  \\

  \--header \'Content-Type: application/json\' \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { \"feedFilterMode\":
  \"SINGLE_FILTER\", \"lang_code\": \"en\", \"defaultTabId\": \"49\",
  \"tabs\": \[ { \"contentUrl\":
  \"https://qa-gateway.coolfie.io/api/v1/stickers/list?tabId=49&version=15&filters=62\",
  \"displayName\": \"Gyaandu\", \"tabType\": \"REMOTE\", \"tabId\":
  \"49\", \"defaultFilterId\": \"62\" }, { \"contentUrl\":
  \"https://qa-gateway.coolfie.io/api/v1/stickers/list?tabId=11&version=25&filters=14\",
  \"displayName\": \"Food\", \"tabType\": \"REMOTE\", \"tabId\": \"11\",
  \"defaultFilterId\": \"14\" }, { \"contentUrl\":
  \"https://qa-gateway.coolfie.io/api/v1/stickers/list?tabId=48&version=13&filters=61\",
  \"displayName\": \"Cities\", \"tabType\": \"REMOTE\", \"tabId\":
  \"48\", \"defaultFilterId\": \"61\" }, { \"contentUrl\":
  \"https://qa-gateway.coolfie.io/api/v1/stickers/list?tabId=10&version=4&filters=13\",
  \"displayName\": \"Stickers\", \"tabType\": \"REMOTE\", \"tabId\":
  \"10\", \"defaultFilterId\": \"13\" }, { \"contentUrl\":
  \"https://bitmoji.api.snapchat.com/api/direct/pack/popular?limit=50&page=1\",
  \"displayName\": \"Bitmoji\", \"tabType\": \"EXTERNAL_BITMOJI\",
  \"tabId\": \"45\", \"searchUrl\":
  \"https://bitmoji.api.snapchat.com/api/direct/search?limit=50\",
  \"baseUrl\": \"https://bitmoji.api.snapchat.com/api\" }, {
  \"contentUrl\":
  \"https://qa-gateway.coolfie.io/api/v1/stickers/list?tabId=13&version=2&filters=16\",
  \"displayName\": \"Emojis\", \"tabType\": \"REMOTE\", \"tabId\":
  \"13\", \"defaultFilterId\": \"16\" }, { \"contentUrl\":
  \"https://qa-gateway.coolfie.io/api/v1/stickers/list?tabId=12&version=1&filters=15\",
  \"displayName\": \"GIF\", \"tabType\": \"REMOTE\", \"tabId\": \"12\",
  \"defaultFilterId\": \"15\" }, { \"contentUrl\":
  \"https://qa-gateway.coolfie.io/api/v1/stickers/list?tabId=50&version=1&filters=7\",
  \"displayName\": \"Sab\", \"tabType\": \"REMOTE\", \"tabId\": \"50\",
  \"defaultFilterId\": \"7\" } \], \"version\": \"236\" } }

- **Request Method and URL:**

  GET :
  https://qa-gateway.coolfie.io/api/v1/stickers/list?tabId=9&filters=26,25

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/stickers/list?tabId=9&filters=26,25\'
  \\

  \--header \'Content-Type: application/json\' \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { \"count\": 0 } }

- **Request Method and URL:**

  GET :
  https://qa-gateway.coolfie.io/api/v1/comment/stickers/tabs?lang_code=en&version=8102141&supported_external_tabs=bitmoji

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/comment/stickers/tabs?lang_code=en&version=8102141&supported_external_tabs=bitmoji\'
  \\

  \--header \'Content-Type: application/json\' \\

  \--header \'Host: qa-gateway.myjosh.in\' \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { } }

- **Request Method and URL:**

  GET :
  https://qa-gateway.coolfie.io/api/v1/stickers/list?tabId=9&filters=26,25

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/stickers/list?tabId=9&filters=26,25\'
  \\

  \--header \'Content-Type: application/json\' \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { \"count\": 0 } }

- **Request Method and URL:**

  POST :
  https://qa-gateway.coolfie.io/api/v1/zerosearch/version/update?langCode=en

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/zerosearch/version/update?langCode=en\'
  \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { } }

- **Request Method and URL:**

  POST :
  https://qa-gateway.coolfie.io/api/v1/zerosearch/post?lang_code=en

- **Curl Request:**

  curl \--location \--request POST
  \'<https://qa-gateway.coolfie.io/api/v1/zerosearch/post?lang_code=en>\'
  \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { } }

- **Request Method and URL:**

  POST :
  https://qa-gateway.coolfie.io/api/v1/zerosearch/update?lang_code=en

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/zerosearch/update?lang_code=en\'
  \\

  \--form \'recordId=\"854\"\' \\

  \--form \'title=\"test-oops\"\' \\

  \--form \'subtitle=\"test-subtitle\"\' \\

  \--form \'description=\"test-description\"\' \\

  \--form \'viewOrder=\"2500\"\' \\

  \--form \'isActive=\"true\"\' \\

  \--form \'thumbnail=@\"/home/varikutitheja/Desktop/default.png\"\' \\

  \--form \'feedType=\"POPULAR HASHTAG\"\' \\

  \--form \'deeplink_url=\"test-deeplink_url\"\' \\

  \--form \'rich_deeplink=\"test-rich_deeplink\"\' \\

  \--form \'sectionId=\"3\"\'

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { } }

- **Request Method and URL:**

  DELETE : https://qa-gateway.coolfie.io/api/v1/zerosearch/delete/854

- **Curl Request:**

  curl \--location \--request DELETE
  \'https://qa-gateway.coolfie.io/api/v1/zerosearch/delete/854\' \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { } }

- **Request Method and URL:**

  POST : https://qa-gateway.coolfie.io/api/v1/josh/handshake/

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/josh/handshake/\' \\

  \--header \'Content-Type: application/json; charset=UTF-8\' \\

  \--header \'coolfie-debug-info:
  appVersion=4.9.0&osVersion=10&clientId=bda58994-7e91&androidId=4cb6f567da56f774&installSource=CoolfieHome&user_lang=bn&nav_lang=bn&width=1080&height=2034\'
  \\

  \--header \'content-uuids-seen:
  d02658a7-d9a0-4a71-9d49-1be017e64483,c6c9d78e-00e7-4ca6-908a-a1962fc45cef,ace416ad-6cf5-4134-94d0-8eface2fc965,87292574-0ae4-4670-ac11-98ac41f6f6fa,32b9ab35-97a7-4b88-99d3-3d74e6f34b62\'
  \\

  \--header \'history-policy: 2\' \\

  \--header \'user-uuid;\' \\

  \--header \'auth-token;\' \\

  \--header \'install-referrer;\' \\

  \--header \'User-Agent: Dalvik/2.1.0 (Linux; U; Android 10; ONEPLUS
  A5010 Build/QKQ1.191014.012)\' \\

  \--header \'X-abof-cronet-tracking-data:
  strmU%7C1%7CT%7Cgwoq%7C4036629%7C1%7C1%7C0%7C1\' \\

  \--data-raw \'{

  \"android_id\": \"4cb6f567da56f774\",

  \"appOpenEvent\": false,

  \"client_info\": {

  \"app_language\": \"hi\",

  \"app_version\": \"4.8.0\",

  \"brand\": \"Josh\",

  \"default_notification_lang\": \"hi\",

  \"device\": \"android\",

  \"gaid\": \"\",

  \"gaid_opt_out_status\": false,

  \"height\": 23523,

  \"manufacturer\": \"OnePlus\",

  \"model\": \"ONEPLUS A5010\",

  \"os_version\": \"10\",

  \"width\": 1080,

  \"android_id\": \"4cb6f567da56f774\",

  \"client_id\": \"wer435\",

  \"udid\": \"4cb6f567da56f774\"

  },

  \"connection_info\": {

  \"cellid\": \"&cellid=\-\-\-\-\-\--Gsm\",

  \"connection\": \"w\"

  },

  \"handshake_version\": \"421\",

  \"install_type\": \"NA\",

  \"location_info\": {

  \"is_GPS_location\": false,

  \"lat\": \"\",

  \"lon\": \"\"

  },

  \"packageName\": \"com.eterno.shortvideos\",

  \"referrer\": \"utm_source=CoolfieHome\",

  \"isCronetEnabled\": false

  }\'

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { \"base_url\": {
  \"sso_url\": \"https://qa-api.myjosh.in\", \"analytics_url\":
  \"http://beacon-qa.rtp.myjosh.in/topics/analytics-events-coolfie\",
  \"font_list_url\": \"https://qa-gateway.myjosh.in/api/v1/fonts/list\",
  \"full_sync_url\":
  \"https://qa-josh-notif-inbox.myjosh.in/api/obelix/fallback/sync\",
  \"meme_list_url\": \"http://qa-api.myjosh.in/apij/meme/list\",
  \"adsHandshakeUrl\": \"http://qa-money.myjosh.in/api/v2/handshake\",
  \"application_url\": \"https://qa-api.myjosh.in\",
  \"appsOnDeviceUrl\":
  \"http://qa-money.newshunt.com/api/v1/userProfile/dh-ddc.php\",
  \"faqs_config_url\": \"http://qa-share.myjosh.in/faqs\",
  \"default_feed_url\":
  \"https://qa-feed.myjosh.in/feed/home?lang_code=bn\",
  \"profile_faqs_url\": \"http://qa-share.myjosh.in/faqs\",
  \"userHandShakeUrl\":
  \"https://qa-api.myjosh.in/user/handshake-config\",
  \"app_handshake_url\":
  \"https://qa-gateway.myjosh.in/api/v1/josh/handshake\",
  \"apps_on_device_url\":
  \"https://api.newshuntads.com/api/v1/userProfile/dh-ddc.php\",
  \"upload_service_url\": \"https://qa-api.myjosh.in/content\",
  \"camera_duet_feed_url\":
  \"https://qa-feed.myjosh.in/v1/feed/collections/videos/5572df21-f4ad-400b-8bab-64fc7551f103\",
  \"deeplink_content_api\": \"https://qa-api.myjosh.in/deeplink\",
  \"detailDefaultFeedURL\":
  \"https://qa-api.myjosh.in/feed/home?langCode=bn\",
  \"location_service_url\": \"https://locationservice.myjosh.in/\",
  \"pull_notification_url\":
  \"https://qa-josh-notif-inbox.myjosh.in/api/obelix/fallback/pull\",
  \"content_gifts_list_url\":
  \"https://qa-api.myjosh.in/apij/content/gifters-list\",
  \"fallback_full_sync_url\":
  \"https://qa-josh-notif-inbox.myjosh.in/api/obelix/fallback/sync\",
  \"delete_notification_url\":
  \"https://qa-josh-notif-inbox.myjosh.in/api/obelix/fallback/delete\",
  \"sticky_notification_url\":
  \"https://qa-josh-sticky-notification.myjosh.in/v1\",
  \"notification_trigger_url\":
  \"http://qa-pullnotification.myjosh.in/notification-pull/v2/pull\",
  \"fallback_pull_notification_url\":
  \"https://qa-josh-notif-inbox.myjosh.in/api/obelix/fallback/pull\",
  \"notification_tray_channels_url\":
  \"http://qa-notifications.myjosh.in/notification/channels/config?appId=JOSH_APP&version=5\",
  \"max_version_for_flexible_update\": 5000,
  \"fallback_delete_notification_url\":
  \"https://qa-josh-notif-inbox.myjosh.in/api/obelix/fallback/delete\",
  \"max_version_for_mandatory_update\": 0,
  \"notification_channels_update_url\":
  \"https://qa-gateway.myjosh.in/api/v1/notification/channel/post\",
  \"image_resumable_upload_result_url\":
  \"https://qa-api.myjosh.in/image/create-v2\",
  \"image_resumable_upload_service_url\":
  \"https://qa-api.myjosh.in/image/upload-v2\",
  \"image_processing_status_polling_url\":
  \"https://qa-api.myjosh.in/image/uploaded-item-status\",
  \"min_gap_between_app_update_prompt_secs\": 300,
  \"video_views_in_session_for_update_prompt\": 3,
  \"resumable_upload_service_url\":
  \"https://qa-api.myjosh.in/content/upload-v2\",
  \"resumable_upload_result_url\":
  \"https://qa-api.myjosh.in/content/create-v2\",
  \"profile_insights_url\":
  \"https://qa-share.myjosh.in/analytics/profile-insight/\",
  \"camera_effects_landing_assets_v2_url\":
  \"http://qa-api.myjosh.in/camera/assets?version=4&collection_uuid=ee71f7bd-d1d3-40e6-8c53-d1ca610f440c&page=0&size=10\",
  \"static_config_url\":
  \"https://qa-gateway.myjosh.in/api/v1/upgrade/version/info/JOSH_STATIC_CONFIG/1447\",
  \"widget_order_url\":
  \"https://qa-gateway.myjosh.in/api/v1/upgrade/version/info/WIDGET_ORDER/1\",
  \"discovery_page_url\":
  \"https://qa-feed.myjosh.in/page/discovery/main-discovery-page\",
  \"apply_for_verification_url\":
  \"https://qa-share.myjosh.in/webview/apply-verification\",
  \"ai_processor_config_url_new\":
  \"https://qa-gateway.myjosh.in/api/v1/upgrade/version/info/AI_PROCESSOR_NEW/9\",
  \"watermark_url\":
  \"https://qa-gateway.myjosh.in/api/v1/upgrade/version/info/WATERMARK/25\",
  \"device_list_url\":
  \"https://qa-gateway.myjosh.in/api/v1/upgrade/version/info/DEVICE_LIST/4\",
  \"delete_account_url\": \"https://qa-share.myjosh.in/deleteAccount\",
  \"app_themes_url\":
  \"https://qa-gateway.myjosh.in/api/v1/app/themes/info?version=144\",
  \"interest_list_url\":
  \"https://qa-feed.myjosh.in/feed/interestlist?version=1\",
  \"astro_signs_url\":
  \"https://qa-gateway.myjosh.in/api/v1/upgrade/version/info/ASTRO_SIGNS/3\",
  \"app_multiprocess_url\":
  \"https://qa-gateway.myjosh.in/api/v1/upgrade/version/info/APP_MULTIPROCESS/11\",
  \"hashtags_list_url\":
  \"https://qa-gateway.myjosh.in/api/v1/upgrade/version/info/HASHTAG_ONBOARD/12\",
  \"gifts_list_versioned_url\":
  \"http://qa-api.myjosh.in/gift/list?version=55\",
  \"musicSearchTabsUrl\":
  \"https://qa-gateway.myjosh.in/api/v1/upgrade/version/info/MUSIC_SEARCH_TABS/61?langCode=bn\",
  \"application_url_v2\": \"https://qa-api.myjosh.in/apij\",
  \"quick_comments_url\":
  \"https://qa-gateway.myjosh.in/api/v1/upgrade/version/info/QUICK_COMMENTS/18\",
  \"globalSearchTabsUrl\":
  \"https://qa-gateway.myjosh.in/api/v1/upgrade/version/info/GLOBAL_SEARCH_TABS/47?langCode=bn\",
  \"experiment_url\": \"http://76.223.34.165/api/run\",
  \"discovery_url\":
  \"https://qa-gateway.myjosh.in/api/v1/upgrade/discovery/search?version=12374\",
  \"template_list_url\":
  \"https://qa-api.myjosh.in/apij/template/list?page=0&size=10\",
  \"template_search_url\":
  \"https://qa-feed.myjosh.in/TEMPLATE/search?page=0&size=10\",
  \"profile_view_url\":
  \"https://qa-gateway.myjosh.in/api/v1/upgrade/version/info/PROFILE_VIEW/9\",
  \"content_insights_url\":
  \"https://qa-share.myjosh.in/analytics/content-insight/\",
  \"camera_effects_landing_assets_url\":
  \"https://qa-gateway.myjosh.in/api/v1/camera/effect/assets/40?version=75&pageNumber=0&pageSize=4\",
  \"social_share_url\": \"https://qa-api.myjosh.in/social/\",
  \"ads_brand_list_url\":
  \"http://qa-api.myjosh.in/apij/brand/list/v1?version=89\",
  \"music_search_url\":
  \"https://qa-feed.myjosh.in/soundboard/v2/search/?tab_id=sr&page=0&rows=10\",
  \"cold_start_url\": \"https://qa-feed.myjosh.in/v2/feed/coldstart\",
  \"ai_processor_config_url\":
  \"https://qa-gateway.myjosh.in/api/v1/upgrade/version/info/AI_PROCESSOR/9\",
  \"contact_sync_config_url\":
  \"https://qa-gateway.myjosh.in/api/v1/upgrade/version/info/CONTACT_SYNC/8\",
  \"baseUrlForQuic\": \"https://qa-stream-g.myjosh.in\",
  \"sso_config_url\":
  \"https://qa-gateway.myjosh.in/api/v1/upgrade/version/info/SSO/56\",
  \"camera_effects_tabs_v2_url\":
  \"https://qa-gateway.myjosh.in/api/v1/camera/effect/tabs?version=96&page=0&size=5\",
  \"camera_effects_tabs_v3_url\":
  \"http://qa-api.myjosh.in/camera/tabs?version=65&page=0&size=15\",
  \"comment_sticker_tabs_url\":
  \"https://qa-gateway.myjosh.in/api/v1/comment/stickers/tabs?version=111\",
  \"audioPickerUrl\":
  \"https://qa-gateway.myjosh.in/api/v1/audio/tabs?version=375&langCode=bn\",
  \"page_base_url\": \"https://qa-feed.myjosh.in\", \"player_url\":
  \"https://qa-gateway.myjosh.in/api/v1/upgrade/version/info/PLAYER_INFO/13?isCronetEnabled=true\",
  \"camera_effects_tabs_url\":
  \"https://qa-gateway.myjosh.in/api/v1/camera/effect/tabs?version=675\",
  \"bookmark_base_url\": \"http://qa-api.myjosh.in\",
  \"stickerTabsUrl\":
  \"https://qa-gateway.myjosh.in/api/v1/stickers/tabs?version=236\",
  \"demo_entity_url\":
  \"https://qa-gateway.myjosh.in/api/v1/upgrade/version/info/DEMO_ENTITY/3\",
  \"image_share_url\": \"https://qa-api.myjosh.in/image/\",
  \"collection_base_url\": \"https://qa-feed.myjosh.in/v1/feed\",
  \"audio_discovery_page_url\":
  \"https://qa-feed.myjosh.in/page/audio/main-audio-page\",
  \"dns_config_url\":
  \"https://qa-gateway.myjosh.in/api/v1/upgrade/dns?version=34\",
  \"lang_list_url\":
  \"https://qa-gateway.myjosh.in/api/v1/langlist?version=69\",
  \"live_category_interests\":
  \"https://qa-gateway.myjosh.in/api/v1/upgrade/version/info/LIVE_CATEGORY_INTERESTS/3\",
  \"global_search_v3_url\":
  \"https://qa-gateway.myjosh.in/api/v1/upgrade/version/info/GLOBAL_SEARCH_TABS_V3/48?langCode=bn\"
  }, \"home_tab_list\": \[ { \"url\":
  \"https://qa-feed.myjosh.in/feed/followings?lang_code=bn\", \"name\":
  \"Following\", \"feed_type\": \"HOME\", \"landing_tab\": false,
  \"selected_tab_icon_url\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/handshake/selected_follow.png\",
  \"un_selected_tab_icon_url\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/handshake/follow.png\"
  }, { \"url\": \"https://qa-feed.myjosh.in/feed/foryou?lang_code=bn\",
  \"name\": \"Popular\", \"feed_type\": \"HOME\", \"landing_tab\": true,
  \"selected_tab_icon_url\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/handshake/selected_popular.png\",
  \"un_selected_tab_icon_url\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/handshake/popular.png\"
  } \], \"live_tab_list\": \[ { \"url\":
  \"https://qa-feed.myjosh.in/v1/feed/live\", \"name\": \"Live\",
  \"s_enable\": true, \"feed_type\": \"LIVE\", \"landing_tab\": true }
  \], \"shop_tab_list\": \[ { \"url\":
  \"https://qa-feed.myjosh.in/feed/shoppables\", \"name\": \"Shop\",
  \"s_enable\": true, \"feed_type\": \"SHOP\", \"landing_tab\": true }
  \], \"camera_effects_landing_assets_v2_url\":
  \"http://qa-api.myjosh.in/camera/assets?version=1&collection_uuid=ee71f7bd-d1d3-40e6-8c53-d1ca610f440c&page=0&size=10\",
  \"handshake_version\": \"71\", \"lang_code\": \"bn\", \"user_seg\":
  \"strmU\|14\|T\|gwq\|36783515\|9\|14\|0\|9\~pth\|34\|T\|\|37446827\|114\|34\|0\|114\",
  \"shareToken\": \"0xd99a4030e046e134\",
  \"deeplinkWhitelistedDomains\": \[ \"www.myjosh.in\",
  \"share.myjosh.in\", \"qa-share.myjosh.in\", \"feed.coolfie.io\",
  \"api.coolfie.io\", \"qa-api.coolfie.io\", \"qa-feed.coolfie.io\",
  \"www.coolfie.io\", \"coolfie.io\", \"share.coolfie.io\",
  \"dev-share.coolfie.io\", \"stage-share.coolfie.io\",
  \"stage-share.myjosh.in\", \"qa-feed.myjosh.in\", \"feed.myjosh.in\",
  \"qa-api.myjosh.in\", \"api.myjosh.in\", \"myjosh.in\",
  \"dev-share.myjosh.in\" \], \"max_version_for_flexible_update\": 5000,
  \"max_version_for_mandatory_update\": 0,
  \"rewardSignatureRefreshTime\": 1800, \"encryption\": { \"version\":
  1, \"key\":
  \"LS0tLS1CRUdJTiBQVUJMSUMgS0VZLS0tLS0KTUlHZk1BMEdDU3FHU0liM0RRRUJBUVVBQTRHTkFEQ0JpUUtCZ1FDWkd2L1dncXo1OEhjOURMZUFObHRmNFVJMwp3Vkoyb0xJYzZEemRheFdaTXRSVkYzTGYySlFSZURQMTRsKzNYUGdXaC9lVlFBU1Z3QTZKaUYxemw1WXhJS1ovCmppc2NEaFRDS25idmE1dTdrYjFMb0FUTlFKQlZtZGhSOFVZbWc3dUZWMnJTVUg3UEJ3VytyLzhKcm9sOXA1SGEKckIxVlBPMEtIR0YyZ2JNS2V3SURBUUFCCi0tLS0tRU5EIFBVQkxJQyBLRVktLS0tLQo=\"
  } } }

- **Request Method and URL:**

  GET : https://qa-gateway.coolfie.io/api/v1/josh/handshake?lang_code=ta

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/josh/handshake?lang_code=ta\'
  \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { \"details\": {
  \"base_url\": { \"sso_url\": \"https://accounts.myjosh.in/api/v1\",
  \"analytics_url\":
  \"http://beacon-qa.rtp.myjosh.in/topics/analytics-events-coolfie\",
  \"font_list_url\": \"https://qa-gateway.myjosh.in/api/v1/fonts/list\",
  \"full_sync_url\":
  \"https://josh-notif-inbox-prod-master-n3.myjosh.in/api/obelix/fallback/sync\",
  \"meme_list_url\": \"http://qa-api.myjosh.in/apij/meme/list\",
  \"adsHandshakeUrl\":
  \"http://qa-money.myjosh.in/api/v1/handShake.php\",
  \"application_url\": \"https://qa-api.myjosh.in\",
  \"appsOnDeviceUrl\":
  \"http://qa-money.newshunt.com/api/v1/userProfile/dh-ddc.php\",
  \"faqs_config_url\": \"http://qa-share.myjosh.in/faqs\",
  \"default_feed_url\":
  \"https://qa-feed.myjosh.in/feed/home?lang_code=ta\",
  \"profile_faqs_url\": \"http://qa-share.myjosh.in/faqs\",
  \"userHandShakeUrl\":
  \"https://qa-api.myjosh.in/user/handshake-config\",
  \"app_handshake_url\":
  \"https://qa-gateway.myjosh.in/api/v1/josh/handshake\",
  \"apps_on_device_url\":
  \"https://api.newshuntads.com/api/v1/userProfile/dh-ddc.php\",
  \"upload_service_url\": \"https://qa-api.myjosh.in/content\",
  \"camera_duet_feed_url\":
  \"https://qa-feed.myjosh.in/v1/feed/collections/videos/5572df21-f4ad-400b-8bab-64fc7551f103\",
  \"deeplink_content_api\": \"https://qa-api.myjosh.in/deeplink\",
  \"detailDefaultFeedURL\":
  \"https://qa-api.myjosh.in/feed/home?langCode=ta\",
  \"location_service_url\": \"https://locationservice.myjosh.in/\",
  \"pull_notification_url\":
  \"http://qa-josh-notif-inbox.myjosh.in/api/obelix/fallback/pull\",
  \"content_gifts_list_url\":
  \"https://qa-api.myjosh.in/apij/content/gifters-list\",
  \"fallback_full_sync_url\":
  \"https://qa-josh-notif-inbox.myjosh.in/api/obelix/fallback/sync\",
  \"delete_notification_url\":
  \"https://qa-josh-notif-inbox.myjosh.in/api/obelix/fallback/delete\",
  \"sticky_notification_url\":
  \"https://qa-josh-sticky-notification.myjosh.in/v1\",
  \"notification_trigger_url\":
  \"http://qa-pullnotification.myjosh.in/notification-pull/v2/pull\",
  \"fallback_pull_notification_url\":
  \"https://josh-notif-inbox-prod-master.myjosh.in/api/obelix/fallback/pull\",
  \"notification_tray_channels_url\":
  \"http://qa-notifications.myjosh.in/notification/channels/config?appId=JOSH_APP&version=5\",
  \"max_version_for_flexible_update\": 5000,
  \"fallback_delete_notification_url\":
  \"https://josh-notif-inbox-prod-master.myjosh.in/api/obelix/fallback/delete\",
  \"max_version_for_mandatory_update\": 0,
  \"notification_channels_update_url\":
  \"https://qa-gateway.myjosh.in/api/v1/notification/channel/post\",
  \"image_resumable_upload_result_url\":
  \"https://qa-api.myjosh.in/image/create-v2\",
  \"image_resumable_upload_service_url\":
  \"https://qa-api.myjosh.in/image/upload-v2\",
  \"image_processing_status_polling_url\":
  \"https://qa-api.myjosh.in/image/uploaded-item-status\",
  \"min_gap_between_app_update_prompt_secs\": 300,
  \"video_views_in_session_for_update_prompt\": 3 }, \"home_tab_list\":
  \[ { \"url\":
  \"https://qa-feed.myjosh.in/feed/followings?lang_code=ta\", \"name\":
  \"Following\", \"feed_type\": \"HOME\", \"landing_tab\": false,
  \"selected_tab_icon_url\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/handshake/selected_follow.png\",
  \"un_selected_tab_icon_url\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/handshake/follow.png\"
  }, { \"url\": \"https://qa-feed.myjosh.in/feed/foryou?lang_code=ta\",
  \"name\": \"For You\", \"feed_type\": \"HOME\", \"landing_tab\": true,
  \"selected_tab_icon_url\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/handshake/selected_add_user.png\",
  \"un_selected_tab_icon_url\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/handshake/add_user.png\"
  } \], \"live_tab_list\": \[ { \"url\":
  \"https://qa-feed.myjosh.in/v1/feed/live\", \"name\": \"Live\",
  \"s_enable\": true, \"feed_type\": \"LIVE\", \"landing_tab\": true }
  \], \"meme_list_url\": \"http://qa-api.myjosh.in/apij/meme/list\",
  \"shop_tab_list\": \[ { \"url\":
  \"https://qa-feed.myjosh.in/feed/shoppables\", \"name\": \"Shop\",
  \"s_enable\": true, \"feed_type\": \"SHOP\", \"landing_tab\": true }
  \], \"max_version_for_flexible_update_ios\": \"5000\",
  \"camera_effects_landing_assets_v2_url\":
  \"http://qa-api.myjosh.in/camera/assets?version=1&collection_uuid=ee71f7bd-d1d3-40e6-8c53-d1ca610f440c&page=0&size=10\",
  \"max_version_for_mandatory_update_ios\": \"0\",
  \"max_version_for_flexible_update_android\": \"5000\",
  \"max_version_for_mandatory_update_android\": \"0\" }, \"version\":
  \"476\" } }

- **Request Method and URL:**

  GET : https://qa-gateway.coolfie.io/api/v1/josh/post/11/?lang_code=te

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/josh/post/11/?lang_code=te\' \\

  \--header \'Content-Type: application/json\' \\

  \--data-raw \'{

  \"base_url\": {

  \"sso_url\": \"https://accounts.dailyhunt.in/api/v1\",

  \"analytics_url\":
  \"https://data.dailyhunt.in/topics/analytics-events-coolfie\",

  \"font_list_url\": \"https://gateway.coolfie.io/api/v1/fonts/list\",

  \"full_sync_url\":
  \"https://josh-notif-inbox-prod-master-n3.coolfie.io/api/obelix/fallback/sync\",

  \"adsHandshakeUrl\": \"http://money.coolfie.io/api/v1/handShake.php\",

  \"application_url\": \"https://api.coolfie.io\",

  \"appsOnDeviceUrl\":
  \"http://money.coolfie.io/api/v1/userProfile/dh-ddc.php\",

  \"faqs_config_url\": \"http://support.myjosh.in/support/home\",

  \"profile_faqs_url\": \"https://share.myjosh.in/faqs\",

  \"default_feed_url\":
  \"https://feed.coolfie.io/feed/home?lang_code=te\",

  \"userHandShakeUrl\":
  \"https://api.coolfie.io/user/handshake-config\",

  \"app_handshake_url\":
  \"https://gateway.coolfie.io/api/v1/josh/handshake\",

  \"apps_on_device_url\":
  \"https://api.newshuntads.com/api/v1/userProfile/dh-ddc.php\",

  \"upload_service_url\": \"https://api.coolfie.io/content\",

  \"deeplink_content_api\": \"https://api.coolfie.io/deeplink\",

  \"detailDefaultFeedURL\":
  \"https://api.coolfie.io/feed/home?langCode=te\",

  \"location_service_url\": \"https://locationservice.dailyhunt.in/\",

  \"pull_notification_url\":
  \"https://josh-notif-inbox-prod-master-n3.coolfie.io/api/obelix/fallback/pull\",

  \"fallback_full_sync_url\":
  \"https://josh-notif-inbox-prod-master.coolfie.io/api/obelix/fallback/sync\",

  \"delete_notification_url\":
  \"https://josh-notif-inbox-prod-master-n3.coolfie.io/api/obelix/fallback/delete\",

  \"notification_trigger_url\":
  \"https://prod-pullnotification.dailyhunt.in/notification-pull/v2/pull\",

  \"fallback_pull_notification_url\":
  \"https://josh-notif-inbox-prod-master.coolfie.io/api/obelix/fallback/pull\",

  \"notification_tray_channels_url\":
  \"https://api-notificationchannels.dailyhunt.in/notification-pull/v2/getTrayChannels?appId=JOSH_APP&version=3\",

  \"max_version_for_flexible_update\": 0,

  \"fallback_delete_notification_url\":
  \"https://josh-notif-inbox-prod-master.coolfie.io/api/obelix/fallback/delete\",

  \"max_version_for_mandatory_update\": 0,

  \"notification_channels_update_url\":
  \"https://gateway.coolfie.io/api/v1/notification/channel/post\",

  \"min_gap_between_app_update_prompt_secs\": 172800,

  \"video_views_in_session_for_update_prompt\": 5

  },

  \"home_tab_list\": \[

  {

  \"url\": \"https://feed.coolfie.io/feed/followings?lang_code=te\",

  \"name\": \"Following\",

  \"feed_type\": \"HOME\",

  \"landing_tab\": false

  },

  {

  \"url\": \"https://feed.coolfie.io/feed/foryou?lang_code=te\",

  \"name\": \"For You\",

  \"feed_type\": \"HOME\",

  \"landing_tab\": true

  }

  \],

  \"max_version_for_flexible_update_ios\": \"0\",

  \"max_version_for_mandatory_update_ios\": \"0\",

  \"max_version_for_flexible_update_android\": \"100000\",

  \"max_version_for_mandatory_update_android\": \"0\"

  }\'

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { } }

- **Request Method and URL:**

  GET :
  https://qa-gateway.coolfie.io/api/v1/camera/effect/cms/assetTypes?isTabbable=false

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/camera/effect/cms/assetTypes?isTabbable=false\'
  \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": \[ { \"assetTypeId\": 1,
  \"assetTypeName\": \"FILTER\", \"isActive\": true }, {
  \"assetTypeId\": 2, \"assetTypeName\": \"EFFECT\", \"isActive\": true
  }, { \"assetTypeId\": 3, \"assetTypeName\": \"MASK\", \"isActive\":
  true }, { \"assetTypeId\": 8, \"assetTypeName\": \"FU_STICKER\",
  \"isActive\": true }, { \"assetTypeId\": 9, \"assetTypeName\":
  \"FU_AR_MASK\", \"isActive\": true }, { \"assetTypeId\": 10,
  \"assetTypeName\": \"FU_BIGHEAD\", \"isActive\": true }, {
  \"assetTypeId\": 11, \"assetTypeName\": \"FU_EXPRESSION_RECOGNITION\",
  \"isActive\": true }, { \"assetTypeId\": 12, \"assetTypeName\":
  \"FU_FACE_WARP\", \"isActive\": true }, { \"assetTypeId\": 13,
  \"assetTypeName\": \"FU_GESTURE_RECOGNITION\", \"isActive\": true }, {
  \"assetTypeId\": 14, \"assetTypeName\": \"FU_GAME\", \"isActive\":
  true }, { \"assetTypeId\": 15, \"assetTypeName\": \"FU_MAKEUP\",
  \"isActive\": true }, { \"assetTypeId\": 16, \"assetTypeName\":
  \"FU_ANIMOJI\", \"isActive\": true }, { \"assetTypeId\": 17,
  \"assetTypeName\": \"FU_PORTRAIT_SEGMENTATION\", \"isActive\": true },
  { \"assetTypeId\": 18, \"assetTypeName\": \"FU_HAIR_COLOUR\",
  \"isActive\": true }, { \"assetTypeId\": 19, \"assetTypeName\":
  \"FU_PORTRAIT_SEGMENTATION_HUMAN_OUTLINE\", \"isActive\": true }, {
  \"assetTypeId\": 20, \"assetTypeName\":
  \"FU_PORTRAIT_SEGMENTATION_BG_SEG_CUSTOM\", \"isActive\": true }, {
  \"assetTypeId\": 21, \"assetTypeName\": \"ZOOMCAM\", \"isActive\":
  true } \] }

- **Request Method and URL:**

  POST : https://qa-gateway.coolfie.io/api/v1/camera/effect/cms/tabs/add

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/camera/effect/cms/tabs/add\' \\

  \--header \'Cookie:
  X-abof-cronet-tracking-data=strmU%7C14%7CT%7Cgwq%7C36783515%7C9%7C14%7C0%7C9%7Epth%7C34%7CT%7C%7C37446827%7C114%7C34%7C0%7C114;
  cdn_info=d%2Fandroid%2Fav%2F4.9.0%2Fl%2Fbn%2Fnl%2Fbn%2Fpnu%2Fn1%2F;
  client_info=app_language=hi&app_version=4.8.0&gaid=&activation_date=null&os_version=10&fst_act_TS=null&client_id=wer435&manufacturer=OnePlus&width=1080&model=ONEPLUS+A5010&user_lang=null&android_id=4cb6f567da56f774&udid=4cb6f567da56f774&brand=Josh&device=android&default_notification_lang=hi&gaid_opt_out_status=false&height=23523;
  sign_info=MDwCHAXOZ%2BfVlc8FtjRiQj9xahJcs%2Bf9Tup%2FxGzNTioCHEOrDDB43XV2OSGGWNRl3%2FmfaZcjKb3YXPOp0zU%3D\'
  \\

  \--form \'tabName=\"Icon Test\"\' \\

  \--form \'tabType=\"REMOTE\"\' \\

  \--form \'tabOperation=\"BASIC\"\' \\

  \--form \'assetType=\"3\"\' \\

  \--form
  \'iconUrl=@\"/home/varikutitheja/Desktop/sample-files/sample_640×426.jpeg\"\'

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { } }

- **Request Method and URL:**

  POST : https://qa-gateway.coolfie.io/api/v1/camera/effect/cms/tabs/40

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/camera/effect/cms/tabs/40\' \\

  \--form \'tabName=\"Mixed All\"\' \\

  \--form
  \'iconUrl=@\"/home/varikutitheja/Desktop/sample-files/test3.jpg\"\'

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { } }

- **Request Method and URL:**

  POST : https://qa-gateway.coolfie.io/api/v1/camera/effect/cms/tabs/40

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/camera/effect/cms/tabs/40\' \\

  \--form \'tabName=\"Mixed All\"\' \\

  \--form
  \'iconUrl=@\"/home/varikutitheja/Desktop/sample-files/test3.jpg\"\'

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { } }

- **Request Method and URL:**

  POST :
  https://qa-gateway.coolfie.io/api/v1/camera/effect/cms/tabs/viewOrder

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/camera/effect/cms/tabs/viewOrder\'
  \\

  \--header \'Content-Type: application/json\' \\

  \--data-raw \'\[

  {

  \"tabId\": 11,

  \"viewOrder\": 100

  },

  {

  \"tabId\": 12,

  \"viewOrder\": 101

  },

  {

  \"tabId\": 13,

  \"viewOrder\": 102

  }

  \]\'

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { } }

- **Request Method and URL:**

  DELETE :
  https://qa-gateway.coolfie.io/api/v1/camera/effect/cms/tabs/20

- **Curl Request:**

  curl \--location \--request DELETE
  \'<https://qa-gateway.coolfie.io/api/v1/camera/effect/cms/tabs/20>\'
  \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { } }

- **Request Method and URL:**

  GET : https://qa-gateway.coolfie.io/api/v1/camera/effect/cms/tabs/40

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/camera/effect/cms/tabs/40\' \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { \"tab_name\": \"Mixed
  All\", \"tab_type\": \"REMOTE\", \"tab_operation\": \"MIXED\",
  \"tab_index\": 18, \"tab_id\": 40, \"is_active\": true,
  \"red_dot_enabled\": false, \"icon_url\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/camera_effects/test3.jpg\"
  } }

- **Request Method and URL:**

  GET : https://qa-gateway.coolfie.io/api/v1/camera/effect/cms/tabs/list

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/camera/effect/cms/tabs/list\'
  \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": \[ { \"tab_name\":
  \"Clear\", \"tab_type\": \"LOCAL\", \"tab_operation\": \"LOCAL\",
  \"tab_index\": 0, \"tab_id\": 26, \"is_active\": true,
  \"red_dot_enabled\": true, \"red_dot_updated_time\": 1623929823000 },
  { \"tab_name\": \"Recent\", \"tab_type\": \"LOCAL\",
  \"tab_operation\": \"LOCAL\", \"tab_index\": 1, \"tab_id\": 28,
  \"is_active\": true, \"red_dot_enabled\": true,
  \"red_dot_updated_time\": 1623933300000 }, { \"tab_name\":
  \"mask-test1\", \"tab_type\": \"LOCAL\", \"tab_operation\": \"LOCAL\",
  \"tab_index\": 2, \"tab_id\": 31, \"is_active\": true,
  \"red_dot_enabled\": true, \"red_dot_updated_time\": 1624000388000 },
  { \"tab_name\": \"cms test 2\", \"tab_type\": \"LOCAL\",
  \"tab_operation\": \"LOCAL\", \"tab_index\": 3, \"tab_id\": 78,
  \"is_active\": true, \"red_dot_enabled\": true,
  \"red_dot_updated_time\": 1654700037000, \"icon_url\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/camera_effects/demo_img_5.png\"
  }, { \"tab_name\": \"CMS TEST 4\", \"tab_type\": \"LOCAL\",
  \"tab_operation\": \"LOCAL\", \"tab_index\": 4, \"tab_id\": 79,
  \"is_active\": true, \"red_dot_enabled\": true,
  \"red_dot_updated_time\": 1654700444000, \"icon_url\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/camera_effects/demo_img_1.jpg\"
  }, { \"tab_name\": \"Effects\", \"tab_type\": \"REMOTE\",
  \"tab_operation\": \"MIXED\", \"tab_index\": 5, \"tab_id\": 60,
  \"is_active\": true, \"red_dot_enabled\": true,
  \"red_dot_updated_time\": 1627537953000 }, { \"tab_name\":
  \"Background\", \"tab_type\": \"REMOTE\", \"tab_operation\":
  \"MIXED\", \"tab_index\": 6, \"tab_id\": 65, \"is_active\": true,
  \"red_dot_enabled\": true, \"red_dot_updated_time\": 1627556268000 },
  { \"tab_name\": \"Face Warp\", \"tab_type\": \"REMOTE\",
  \"tab_operation\": \"MIXED\", \"tab_index\": 7, \"tab_id\": 68,
  \"is_active\": true, \"red_dot_enabled\": true,
  \"red_dot_updated_time\": 1627556416000 }, { \"tab_name\":
  \"Expression Recognition\", \"tab_type\": \"REMOTE\",
  \"tab_operation\": \"MIXED\", \"tab_index\": 8, \"tab_id\": 67,
  \"is_active\": true, \"red_dot_enabled\": true,
  \"red_dot_updated_time\": 1627556359000 }, { \"tab_name\": \"Hair
  Colour\", \"tab_type\": \"REMOTE\", \"tab_operation\": \"MIXED\",
  \"tab_index\": 9, \"tab_id\": 72, \"is_active\": true,
  \"red_dot_enabled\": true, \"red_dot_updated_time\": 1633684430000 },
  { \"tab_name\": \"Makeup\", \"tab_type\": \"REMOTE\",
  \"tab_operation\": \"MIXED\", \"tab_index\": 10, \"tab_id\": 64,
  \"is_active\": true, \"red_dot_enabled\": true,
  \"red_dot_updated_time\": 1627556164000 }, { \"tab_name\":
  \"Animojis\", \"tab_type\": \"REMOTE\", \"tab_operation\": \"MIXED\",
  \"tab_index\": 11, \"tab_id\": 63, \"is_active\": true,
  \"red_dot_enabled\": true, \"red_dot_updated_time\": 1627556114000 },
  { \"tab_name\": \"Games\", \"tab_type\": \"REMOTE\",
  \"tab_operation\": \"MIXED\", \"tab_index\": 12, \"tab_id\": 66,
  \"is_active\": true, \"red_dot_enabled\": true,
  \"red_dot_updated_time\": 1627556319000 }, { \"tab_name\": \"Gesture
  Recognition\", \"tab_type\": \"REMOTE\", \"tab_operation\": \"MIXED\",
  \"tab_index\": 13, \"tab_id\": 69, \"is_active\": true,
  \"red_dot_enabled\": true, \"red_dot_updated_time\": 1627556468000 },
  { \"tab_name\": \"Filters\", \"tab_type\": \"REMOTE\",
  \"tab_operation\": \"MIXED\", \"tab_index\": 14, \"tab_id\": 61,
  \"is_active\": true, \"red_dot_enabled\": true,
  \"red_dot_updated_time\": 1627537962000 }, { \"tab_name\": \"Big
  Head\", \"tab_type\": \"REMOTE\", \"tab_operation\": \"MIXED\",
  \"tab_index\": 15, \"tab_id\": 70, \"is_active\": true,
  \"red_dot_enabled\": true, \"red_dot_updated_time\": 1628172643000 },
  { \"tab_name\": \"7016effects\", \"tab_type\": \"REMOTE\",
  \"tab_operation\": \"MIXED\", \"tab_index\": 16, \"tab_id\": 80,
  \"is_active\": true, \"red_dot_enabled\": true,
  \"red_dot_updated_time\": 1654749834000 }, { \"tab_name\":
  \"532xtest\", \"tab_type\": \"REMOTE\", \"tab_operation\": \"MIXED\",
  \"tab_index\": 17, \"tab_id\": 73, \"is_active\": true,
  \"red_dot_enabled\": true, \"red_dot_updated_time\": 1650526510000 },
  { \"tab_name\": \"Mixed All\", \"tab_type\": \"REMOTE\",
  \"tab_operation\": \"MIXED\", \"tab_index\": 18, \"tab_id\": 40,
  \"is_active\": true, \"red_dot_enabled\": false, \"icon_url\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/camera_effects/test3.jpg\"
  }, { \"tab_name\": \"BIGHEAD_BASIC\", \"tab_type\": \"REMOTE\",
  \"tab_operation\": \"BASIC\", \"asset_type\": 10, \"tab_index\": 19,
  \"tab_id\": 49, \"is_active\": true, \"red_dot_enabled\": true,
  \"red_dot_updated_time\": 1651499619000 }, { \"tab_name\":
  \"STICKER_BASIC\", \"tab_type\": \"REMOTE\", \"tab_operation\":
  \"BASIC\", \"asset_type\": 8, \"tab_index\": 20, \"tab_id\": 47,
  \"is_active\": true, \"red_dot_enabled\": true }, { \"tab_name\":
  \"Effects_BASIC\", \"tab_type\": \"REMOTE\", \"tab_operation\":
  \"BASIC\", \"asset_type\": 2, \"tab_index\": 21, \"tab_id\": 36,
  \"is_active\": true, \"red_dot_enabled\": true,
  \"red_dot_updated_time\": 1624014627000 }, { \"tab_name\":
  \"EXPRESSION_BASIC\", \"tab_type\": \"REMOTE\", \"tab_operation\":
  \"BASIC\", \"asset_type\": 11, \"tab_index\": 22, \"tab_id\": 50,
  \"is_active\": true, \"red_dot_enabled\": true }, { \"tab_name\":
  \"Masks_BASIC\", \"tab_type\": \"REMOTE\", \"tab_operation\":
  \"BASIC\", \"asset_type\": 3, \"tab_index\": 23, \"tab_id\": 38,
  \"is_active\": true, \"red_dot_enabled\": true,
  \"red_dot_updated_time\": 1624003012000 }, { \"tab_name\":
  \"Filters_BASIC\", \"tab_type\": \"REMOTE\", \"tab_operation\":
  \"BASIC\", \"asset_type\": 1, \"tab_index\": 24, \"tab_id\": 39,
  \"is_active\": true, \"red_dot_enabled\": true,
  \"red_dot_updated_time\": 1624003066000 }, { \"tab_name\":
  \"FilterTrending_BASIC\", \"tab_type\": \"REMOTE\", \"tab_operation\":
  \"BASIC\", \"asset_type\": 1, \"tab_index\": 25, \"tab_id\": 45,
  \"is_active\": true, \"red_dot_enabled\": true,
  \"red_dot_updated_time\": 1624008290000 }, { \"tab_name\":
  \"AR_MASK_BASIC\", \"tab_type\": \"REMOTE\", \"tab_operation\":
  \"BASIC\", \"asset_type\": 9, \"tab_index\": 26, \"tab_id\": 48,
  \"is_active\": true, \"red_dot_enabled\": true }, { \"tab_name\":
  \"FACE_WARP_BASIC\", \"tab_type\": \"REMOTE\", \"tab_operation\":
  \"BASIC\", \"asset_type\": 12, \"tab_index\": 27, \"tab_id\": 51,
  \"is_active\": true, \"red_dot_enabled\": true }, { \"tab_name\":
  \"GESTURE_BASIC\", \"tab_type\": \"REMOTE\", \"tab_operation\":
  \"BASIC\", \"asset_type\": 13, \"tab_index\": 28, \"tab_id\": 52,
  \"is_active\": true, \"red_dot_enabled\": true }, { \"tab_name\":
  \"GAME_BASIC\", \"tab_type\": \"REMOTE\", \"tab_operation\":
  \"BASIC\", \"asset_type\": 14, \"tab_index\": 29, \"tab_id\": 53,
  \"is_active\": true, \"red_dot_enabled\": true }, { \"tab_name\":
  \"MAKEUP_BASIC\", \"tab_type\": \"REMOTE\", \"tab_operation\":
  \"BASIC\", \"asset_type\": 15, \"tab_index\": 30, \"tab_id\": 54,
  \"is_active\": true, \"red_dot_enabled\": true }, { \"tab_name\":
  \"ANIMOJI_BASIC\", \"tab_type\": \"REMOTE\", \"tab_operation\":
  \"BASIC\", \"asset_type\": 16, \"tab_index\": 31, \"tab_id\": 55,
  \"is_active\": true, \"red_dot_enabled\": true }, { \"tab_name\":
  \"Cms test1\", \"tab_type\": \"REMOTE\", \"tab_operation\": \"MIXED\",
  \"tab_index\": 32, \"tab_id\": 74, \"is_active\": true,
  \"red_dot_enabled\": true, \"red_dot_updated_time\": 1650704624000 },
  { \"tab_name\": \"BACKGROUND_BASIC\", \"tab_type\": \"REMOTE\",
  \"tab_operation\": \"BASIC\", \"asset_type\": 17, \"tab_index\": 33,
  \"tab_id\": 56, \"is_active\": true, \"red_dot_enabled\": true }, {
  \"tab_name\": \"HAIR_COLOUR_BASIC\", \"tab_type\": \"REMOTE\",
  \"tab_operation\": \"BASIC\", \"asset_type\": 18, \"tab_index\": 33,
  \"tab_id\": 57, \"is_active\": true, \"red_dot_enabled\": true }, {
  \"tab_name\": \"Zoomcam_BASIC\", \"tab_type\": \"REMOTE\",
  \"tab_operation\": \"BASIC\", \"asset_type\": 18, \"tab_index\": 33,
  \"tab_id\": 71, \"is_active\": true, \"red_dot_enabled\": true,
  \"red_dot_updated_time\": 1631521469000 }, { \"tab_name\": \"Icon
  Test\", \"tab_type\": \"REMOTE\", \"tab_operation\": \"BASIC\",
  \"asset_type\": 3, \"tab_id\": 77, \"is_active\": true,
  \"red_dot_enabled\": true, \"red_dot_updated_time\": 1654250821000,
  \"icon_url\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/camera_effects/sample_640×426.jpeg\"
  }, { \"tab_name\": \"HUMAN_OUTLINE_BASIC\", \"tab_type\": \"REMOTE\",
  \"tab_operation\": \"BASIC\", \"asset_type\": 19, \"tab_id\": 58,
  \"is_active\": true, \"red_dot_enabled\": true }, { \"tab_name\":
  \"BG_SEG_CUSTOM_BASIC\", \"tab_type\": \"REMOTE\", \"tab_operation\":
  \"BASIC\", \"asset_type\": 20, \"tab_id\": 59, \"is_active\": true,
  \"red_dot_enabled\": true } \] }

- **Request Method and URL:**

  POST :
  https://qa-gateway.coolfie.io/api/v1/camera/effect/cms/tabs/56/updateVersion

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/camera/effect/cms/tabs/56/updateVersion\'
  \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { } }

- **Request Method and URL:**

  GET :
  https://qa-gateway.coolfie.io/api/v1/camera/effect/cms/tabs/3/assets

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/camera/effect/cms/tabs/3/assets\'
  \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { } }

- **Request Method and URL:**

  GET :
  https://qa-gateway.coolfie.io/api/v1/camera/effect/cms/assetType/3/assets

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/camera/effect/cms/assetType/3/assets\'
  \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": \[ { \"pk\": 1023, \"id\":
  \"62D20446-2E3D-4493-91CB-14B6E3160676\", \"category\": 0, \"name\":
  \"Holi\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/62D20446-2E3D-4493-91CB-14B6E3160676.1.arscene\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/62D20446-2E3D-4493-91CB-14B6E3160676.png\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"coverUrl2\": \"\",
  \"viewOrder\": 13, \"filterType\": \"\", \"hasSound\": true,
  \"validTill\": 1643621733298, \"label\": \"Hot\", \"assetType\": 3,
  \"assetTypeName\": \"MASK\" }, { \"pk\": 650, \"id\":
  \"B271F162-3C20-4C83-90ED-EF722EA78DA9\", \"category\": 0, \"name\":
  \"Dusshera\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/B271F162-3C20-4C83-90ED-EF722EA78DA9.1.arscene\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/B271F162-3C20-4C83-90ED-EF722EA78DA9.png\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"coverUrl2\": \"\",
  \"viewOrder\": 14, \"filterType\": \"\", \"isArchived\": false,
  \"hasSound\": true, \"alias\": \"Face\", \"notShowInThumbnail\":
  false, \"validTill\": 1643615226490, \"label\": \"new1\",
  \"assetType\": 3, \"assetTypeName\": \"MASK\" }, { \"pk\": 50, \"id\":
  \"0DA345FA-A13A-44B1-9549-3B79C9DE9EF2\", \"category\": 0, \"name\":
  \"Kitty\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/0DA345FA-A13A-44B1-9549-3B79C9DE9EF2.2.arscene\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/0DA345FA-A13A-44B1-9549-3B79C9DE9EF2.png\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"coverUrl2\": \"\",
  \"viewOrder\": 15, \"filterType\": \"\", \"hasSound\": false,
  \"validTill\": 1643612955115, \"label\": \"New\", \"assetType\": 3,
  \"assetTypeName\": \"MASK\" }, { \"pk\": 527, \"id\":
  \"918F57EB-C65B-4729-AD69-5BEB41426D40\", \"category\": 0, \"name\":
  \"Meow\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/918F57EB-C65B-4729-AD69-5BEB41426D40.2.arscene\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/918F57EB-C65B-4729-AD69-5BEB41426D40.png\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"coverUrl2\": \"\",
  \"viewOrder\": 70, \"filterType\": \"\", \"hasSound\": false,
  \"alias\": \"Mast Image\", \"validTill\": 1646040952490, \"label\":
  \"new\", \"assetType\": 3, \"assetTypeName\": \"MASK\" }, { \"pk\":
  911, \"id\": \"FD135303-4192-44D1-8682-A727105EDE83\", \"category\":
  0, \"name\": \"Crown\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/FD135303-4192-44D1-8682-A727105EDE83.3.arscene\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/FD135303-4192-44D1-8682-A727105EDE83.png\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"coverUrl2\": \"\",
  \"viewOrder\": 90, \"filterType\": \"\", \"hasSound\": false,
  \"validTill\": 1629525378299, \"label\": \"new\", \"assetType\": 3,
  \"assetTypeName\": \"MASK\" }, { \"pk\": 760, \"id\":
  \"D18BD048-4176-4E14-B705-7E2A4DF08274\", \"category\": 0, \"name\":
  \"Iron Man\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/D18BD048-4176-4E14-B705-7E2A4DF08274.2.arscene\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/D18BD048-4176-4E14-B705-7E2A4DF08274.png\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"coverUrl2\": \"\",
  \"viewOrder\": 120, \"filterType\": \"\", \"hasSound\": false,
  \"validTill\": 1635595574872, \"label\": \"new\", \"assetType\": 3,
  \"assetTypeName\": \"MASK\" }, { \"pk\": 915, \"id\":
  \"FE960FE8-4884-4BB0-8F1F-0E61AD7C4004\", \"category\": 0, \"name\":
  \"Giraffe\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/FE960FE8-4884-4BB0-8F1F-0E61AD7C4004.3.arscene\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/FE960FE8-4884-4BB0-8F1F-0E61AD7C4004.png\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"coverUrl2\": \"\",
  \"viewOrder\": 130, \"filterType\": \"\", \"userAction\": \"\",
  \"hasSound\": false, \"validTill\": 1643615241627, \"label\": \"new\",
  \"assetType\": 3, \"assetTypeName\": \"MASK\" }, { \"pk\": 469,
  \"id\": \"827EB8A5-1804-45CE-B054-4BA640E566A9\", \"category\": 0,
  \"name\": \"Chicken dinner\", \"desc\": \"\", \"tags\": \"\",
  \"version\": 0, \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/827EB8A5-1804-45CE-B054-4BA640E566A9.6.arscene\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/827EB8A5-1804-45CE-B054-4BA640E566A9.png\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"coverUrl2\": \"\",
  \"viewOrder\": 150, \"filterType\": \"\", \"userAction\": \"Nod your
  head\", \"hasSound\": false, \"assetType\": 3, \"assetTypeName\":
  \"MASK\" }, { \"pk\": 509, \"id\":
  \"8DF4B0BC-3438-4A1D-8BB6-3D6E11D48D92\", \"category\": 0, \"name\":
  \"Party glass\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/8DF4B0BC-3438-4A1D-8BB6-3D6E11D48D92.2.arscene\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/8DF4B0BC-3438-4A1D-8BB6-3D6E11D48D92.png\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"coverUrl2\": \"\",
  \"viewOrder\": 160, \"filterType\": \"\", \"hasSound\": false,
  \"validTill\": 1635596349417, \"label\": \"new\", \"assetType\": 3,
  \"assetTypeName\": \"MASK\" }, { \"pk\": 369, \"id\":
  \"63833FB8-95F7-4A92-A852-A048BA223F5E\", \"category\": 0, \"name\":
  \"Petal shower\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/63833FB8-95F7-4A92-A852-A048BA223F5E.1.arscene\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/63833FB8-95F7-4A92-A852-A048BA223F5E.png\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"coverUrl2\": \"\",
  \"viewOrder\": 170, \"filterType\": \"\", \"hasSound\": false,
  \"validTill\": 1635682761939, \"label\": \"new\", \"assetType\": 3,
  \"assetTypeName\": \"MASK\" }, { \"pk\": 146, \"id\":
  \"25C78DC6-823C-4103-9E8A-D84350362F16\", \"category\": 0, \"name\":
  \"Pick you\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/25C78DC6-823C-4103-9E8A-D84350362F16.3.arscene\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/25C78DC6-823C-4103-9E8A-D84350362F16.png\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"coverUrl2\": \"\",
  \"viewOrder\": 180, \"filterType\": \"\", \"userAction\": \"\",
  \"hasSound\": false, \"assetType\": 3, \"assetTypeName\": \"MASK\" },
  { \"pk\": 776, \"id\": \"D3F9A1A9-CFD8-46B6-8E9C-DC3E87A9A687\",
  \"category\": 0, \"name\": \"Retro love\", \"desc\": \"\", \"tags\":
  \"\", \"version\": 0, \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/D3F9A1A9-CFD8-46B6-8E9C-DC3E87A9A687.3.arscene\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/D3F9A1A9-CFD8-46B6-8E9C-DC3E87A9A687.png\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"coverUrl2\": \"\",
  \"viewOrder\": 190, \"filterType\": \"\", \"userAction\": \"\",
  \"hasSound\": false, \"assetType\": 3, \"assetTypeName\": \"MASK\" },
  { \"pk\": 418, \"id\": \"73F1C799-B7F0-4F12-9679-F9840F61D557\",
  \"category\": 0, \"name\": \"Glam\", \"desc\": \"\", \"tags\": \"\",
  \"version\": 0, \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/73F1C799-B7F0-4F12-9679-F9840F61D557.5.arscene\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/73F1C799-B7F0-4F12-9679-F9840F61D557.png\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"coverUrl2\": \"\",
  \"viewOrder\": 200, \"filterType\": \"\", \"userAction\": \"\",
  \"hasSound\": false, \"assetType\": 3, \"assetTypeName\": \"MASK\" },
  { \"pk\": 867, \"id\": \"F067A31B-01B7-4384-A8FE-E5A7CE790418\",
  \"category\": 0, \"name\": \"In love\", \"desc\": \"\", \"tags\":
  \"\", \"version\": 0, \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/F067A31B-01B7-4384-A8FE-E5A7CE790418.5.arscene\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/F067A31B-01B7-4384-A8FE-E5A7CE790418.png\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"coverUrl2\": \"\",
  \"viewOrder\": 210, \"filterType\": \"\", \"userAction\": \"\",
  \"hasSound\": false, \"assetType\": 3, \"assetTypeName\": \"MASK\" },
  { \"pk\": 651, \"id\": \"B2AEDB44-FF3B-45A6-A66D-0A2B1E6D48ED\",
  \"category\": 0, \"name\": \"Showtime\", \"desc\": \"\", \"tags\":
  \"\", \"version\": 0, \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/B2AEDB44-FF3B-45A6-A66D-0A2B1E6D48ED.5.arscene\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/B2AEDB44-FF3B-45A6-A66D-0A2B1E6D48ED.png\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"coverUrl2\": \"\",
  \"viewOrder\": 220, \"filterType\": \"\", \"userAction\": \"\",
  \"hasSound\": false, \"assetType\": 3, \"assetTypeName\": \"MASK\" },
  { \"pk\": 852, \"id\": \"EA962143-6CCA-42E4-B7FC-9615B9EEA231\",
  \"category\": 0, \"name\": \"Glitch skull\", \"desc\": \"\", \"tags\":
  \"\", \"version\": 0, \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/EA962143-6CCA-42E4-B7FC-9615B9EEA231.3.arscene\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/EA962143-6CCA-42E4-B7FC-9615B9EEA231.png\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"coverUrl2\": \"\",
  \"viewOrder\": 240, \"filterType\": \"\", \"userAction\": \"\",
  \"hasSound\": false, \"assetType\": 3, \"assetTypeName\": \"MASK\" },
  { \"pk\": 340, \"id\": \"5C5D8FC4-8970-44DC-B85C-DE0A375CB5D6\",
  \"category\": 0, \"name\": \"Kitty berries\", \"desc\": \"\",
  \"tags\": \"\", \"version\": 0, \"minAppVersion\": \"\",
  \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/5C5D8FC4-8970-44DC-B85C-DE0A375CB5D6.2.arscene\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/5C5D8FC4-8970-44DC-B85C-DE0A375CB5D6.png\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"coverUrl2\": \"\",
  \"viewOrder\": 250, \"filterType\": \"\", \"userAction\": \"\",
  \"hasSound\": false, \"assetType\": 3, \"assetTypeName\": \"MASK\" },
  { \"pk\": 754, \"id\": \"D115AFF8-D7E4-4EB5-8ABB-9BAF2D6793F2\",
  \"category\": 0, \"name\": \"Thug life\", \"desc\": \"\", \"tags\":
  \"\", \"version\": 0, \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/D115AFF8-D7E4-4EB5-8ABB-9BAF2D6793F2.4.arscene\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/D115AFF8-D7E4-4EB5-8ABB-9BAF2D6793F2.png\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"coverUrl2\": \"\",
  \"viewOrder\": 260, \"filterType\": \"\", \"userAction\": \"\",
  \"hasSound\": false, \"assetType\": 3, \"assetTypeName\": \"MASK\" },
  { \"pk\": 262, \"id\": \"464EDF75-34AF-40AD-BCEB-5BD8712BF723\",
  \"category\": 0, \"name\": \"Anonymous\", \"desc\": \"\", \"tags\":
  \"\", \"version\": 0, \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/464EDF75-34AF-40AD-BCEB-5BD8712BF723.2.arscene\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/464EDF75-34AF-40AD-BCEB-5BD8712BF723.png\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"coverUrl2\": \"\",
  \"viewOrder\": 270, \"filterType\": \"\", \"userAction\": \"\",
  \"hasSound\": false, \"assetType\": 3, \"assetTypeName\": \"MASK\" },
  { \"pk\": 258, \"id\": \"45B2C68F-D6DB-4567-96A7-82276AA11848\",
  \"category\": 0, \"name\": \"Bride\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/45B2C68F-D6DB-4567-96A7-82276AA11848.4.arscene\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/45B2C68F-D6DB-4567-96A7-82276AA11848.png\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"coverUrl2\": \"\",
  \"viewOrder\": 280, \"hasSound\": false, \"assetType\": 3,
  \"assetTypeName\": \"MASK\" } \] }

- **Request Method and URL:**

  POST :
  https://qa-gateway.coolfie.io/api/v1/camera/effect/cms/tabs/17/assetMapping

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/camera/effect/cms/tabs/17/assetMapping\'
  \\

  \--header \'Content-Type: application/json\' \\

  \--data-raw \'\[

  {

  \"assetId\": 191,

  \"viewOrder\":100

  },

  {

  \"assetId\": 527,

  \"viewOrder\":200

  }

  \]\'

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { } }

- **Request Method and URL:**

  GET :
  https://qa-gateway.coolfie.io/api/v1/camera/effect/tabs?version=272&supported_assets=EFFECT,MASK,FU_AR_MASK,FU_STICKER,FU_GAME,FU_EXPRESSION_RECOGNITION,FU_FACE_WARP,FU_GESTURE_RECOGNITION,FU_BIGHEAD,FU_PORTRAIT_SEGMENTATION,FU_ANIMOJI,FU_PORTRAIT_SEGMENTATION_HUMAN_OUTLINE,FU_MAKEUP,FU_HAIR_COLOUR,FU_PORTRAIT_SEGMENTATION_BG_SEG_CUSTOM

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/camera/effect/tabs?version=272&supported_assets=EFFECT,MASK,FU_AR_MASK,FU_STICKER,FU_GAME,FU_EXPRESSION_RECOGNITION,FU_FACE_WARP,FU_GESTURE_RECOGNITION,FU_BIGHEAD,FU_PORTRAIT_SEGMENTATION,FU_ANIMOJI,FU_PORTRAIT_SEGMENTATION_HUMAN_OUTLINE,FU_MAKEUP,FU_HAIR_COLOUR,FU_PORTRAIT_SEGMENTATION_BG_SEG_CUSTOM\'
  \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { \"tabs\": \[ {
  \"tabType\": \"LOCAL_CLEAR\", \"displayName\": \"Clear\" }, {
  \"tabType\": \"LOCAL_RECENT\", \"displayName\": \"Recent\" }, {
  \"tabType\": \"LOCAL_MASK-TEST1\", \"displayName\": \"mask-test1\" },
  { \"tabType\": \"LOCAL_CMS TEST 2\", \"iconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/camera_effects/demo_img_5.png\",
  \"displayName\": \"cms test 2\" }, { \"tabType\": \"LOCAL_CMS TEST
  4\", \"iconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/camera_effects/demo_img_1.jpg\",
  \"displayName\": \"CMS TEST 4\" }, { \"tabType\": \"REMOTE\",
  \"contentUrl\":
  \"https://qa-gateway.myjosh.in/api/v1/camera/effect/assets/60?version=38&supported_assets=EFFECT,MASK,FU_AR_MASK,FU_STICKER,FU_GAME,FU_EXPRESSION_RECOGNITION,FU_FACE_WARP,FU_GESTURE_RECOGNITION,FU_BIGHEAD,FU_PORTRAIT_SEGMENTATION,FU_ANIMOJI,FU_PORTRAIT_SEGMENTATION_HUMAN_OUTLINE,FU_MAKEUP,FU_HAIR_COLOUR,FU_PORTRAIT_SEGMENTATION_BG_SEG_CUSTOM\",
  \"assetIds\": \[\], \"displayName\": \"Effects\" }, { \"tabType\":
  \"REMOTE\", \"contentUrl\":
  \"https://qa-gateway.myjosh.in/api/v1/camera/effect/assets/65?version=44&supported_assets=EFFECT,MASK,FU_AR_MASK,FU_STICKER,FU_GAME,FU_EXPRESSION_RECOGNITION,FU_FACE_WARP,FU_GESTURE_RECOGNITION,FU_BIGHEAD,FU_PORTRAIT_SEGMENTATION,FU_ANIMOJI,FU_PORTRAIT_SEGMENTATION_HUMAN_OUTLINE,FU_MAKEUP,FU_HAIR_COLOUR,FU_PORTRAIT_SEGMENTATION_BG_SEG_CUSTOM\",
  \"assetIds\": \[\], \"displayName\": \"Background\" }, { \"tabType\":
  \"REMOTE\", \"contentUrl\":
  \"https://qa-gateway.myjosh.in/api/v1/camera/effect/assets/68?version=16&supported_assets=EFFECT,MASK,FU_AR_MASK,FU_STICKER,FU_GAME,FU_EXPRESSION_RECOGNITION,FU_FACE_WARP,FU_GESTURE_RECOGNITION,FU_BIGHEAD,FU_PORTRAIT_SEGMENTATION,FU_ANIMOJI,FU_PORTRAIT_SEGMENTATION_HUMAN_OUTLINE,FU_MAKEUP,FU_HAIR_COLOUR,FU_PORTRAIT_SEGMENTATION_BG_SEG_CUSTOM\",
  \"assetIds\": \[\], \"displayName\": \"Face Warp\" }, { \"tabType\":
  \"REMOTE\", \"contentUrl\":
  \"https://qa-gateway.myjosh.in/api/v1/camera/effect/assets/67?version=22&supported_assets=EFFECT,MASK,FU_AR_MASK,FU_STICKER,FU_GAME,FU_EXPRESSION_RECOGNITION,FU_FACE_WARP,FU_GESTURE_RECOGNITION,FU_BIGHEAD,FU_PORTRAIT_SEGMENTATION,FU_ANIMOJI,FU_PORTRAIT_SEGMENTATION_HUMAN_OUTLINE,FU_MAKEUP,FU_HAIR_COLOUR,FU_PORTRAIT_SEGMENTATION_BG_SEG_CUSTOM\",
  \"assetIds\": \[\], \"displayName\": \"Expression Recognition\" }, {
  \"tabType\": \"REMOTE\", \"contentUrl\":
  \"https://qa-gateway.myjosh.in/api/v1/camera/effect/assets/72?version=29&supported_assets=EFFECT,MASK,FU_AR_MASK,FU_STICKER,FU_GAME,FU_EXPRESSION_RECOGNITION,FU_FACE_WARP,FU_GESTURE_RECOGNITION,FU_BIGHEAD,FU_PORTRAIT_SEGMENTATION,FU_ANIMOJI,FU_PORTRAIT_SEGMENTATION_HUMAN_OUTLINE,FU_MAKEUP,FU_HAIR_COLOUR,FU_PORTRAIT_SEGMENTATION_BG_SEG_CUSTOM\",
  \"assetIds\": \[\], \"displayName\": \"Hair Colour\" }, { \"tabType\":
  \"REMOTE\", \"contentUrl\":
  \"https://qa-gateway.myjosh.in/api/v1/camera/effect/assets/64?version=29&supported_assets=EFFECT,MASK,FU_AR_MASK,FU_STICKER,FU_GAME,FU_EXPRESSION_RECOGNITION,FU_FACE_WARP,FU_GESTURE_RECOGNITION,FU_BIGHEAD,FU_PORTRAIT_SEGMENTATION,FU_ANIMOJI,FU_PORTRAIT_SEGMENTATION_HUMAN_OUTLINE,FU_MAKEUP,FU_HAIR_COLOUR,FU_PORTRAIT_SEGMENTATION_BG_SEG_CUSTOM\",
  \"assetIds\": \[\], \"displayName\": \"Makeup\" }, { \"tabType\":
  \"REMOTE\", \"contentUrl\":
  \"https://qa-gateway.myjosh.in/api/v1/camera/effect/assets/63?version=13&supported_assets=EFFECT,MASK,FU_AR_MASK,FU_STICKER,FU_GAME,FU_EXPRESSION_RECOGNITION,FU_FACE_WARP,FU_GESTURE_RECOGNITION,FU_BIGHEAD,FU_PORTRAIT_SEGMENTATION,FU_ANIMOJI,FU_PORTRAIT_SEGMENTATION_HUMAN_OUTLINE,FU_MAKEUP,FU_HAIR_COLOUR,FU_PORTRAIT_SEGMENTATION_BG_SEG_CUSTOM\",
  \"assetIds\": \[\], \"displayName\": \"Animojis\" }, { \"tabType\":
  \"REMOTE\", \"contentUrl\":
  \"https://qa-gateway.myjosh.in/api/v1/camera/effect/assets/66?version=26&supported_assets=EFFECT,MASK,FU_AR_MASK,FU_STICKER,FU_GAME,FU_EXPRESSION_RECOGNITION,FU_FACE_WARP,FU_GESTURE_RECOGNITION,FU_BIGHEAD,FU_PORTRAIT_SEGMENTATION,FU_ANIMOJI,FU_PORTRAIT_SEGMENTATION_HUMAN_OUTLINE,FU_MAKEUP,FU_HAIR_COLOUR,FU_PORTRAIT_SEGMENTATION_BG_SEG_CUSTOM\",
  \"assetIds\": \[\], \"displayName\": \"Games\" }, { \"tabType\":
  \"REMOTE\", \"contentUrl\":
  \"https://qa-gateway.myjosh.in/api/v1/camera/effect/assets/69?version=18&supported_assets=EFFECT,MASK,FU_AR_MASK,FU_STICKER,FU_GAME,FU_EXPRESSION_RECOGNITION,FU_FACE_WARP,FU_GESTURE_RECOGNITION,FU_BIGHEAD,FU_PORTRAIT_SEGMENTATION,FU_ANIMOJI,FU_PORTRAIT_SEGMENTATION_HUMAN_OUTLINE,FU_MAKEUP,FU_HAIR_COLOUR,FU_PORTRAIT_SEGMENTATION_BG_SEG_CUSTOM\",
  \"assetIds\": \[\], \"displayName\": \"Gesture Recognition\" }, {
  \"tabType\": \"REMOTE\", \"contentUrl\":
  \"https://qa-gateway.myjosh.in/api/v1/camera/effect/assets/70?version=13&supported_assets=EFFECT,MASK,FU_AR_MASK,FU_STICKER,FU_GAME,FU_EXPRESSION_RECOGNITION,FU_FACE_WARP,FU_GESTURE_RECOGNITION,FU_BIGHEAD,FU_PORTRAIT_SEGMENTATION,FU_ANIMOJI,FU_PORTRAIT_SEGMENTATION_HUMAN_OUTLINE,FU_MAKEUP,FU_HAIR_COLOUR,FU_PORTRAIT_SEGMENTATION_BG_SEG_CUSTOM\",
  \"assetIds\": \[\], \"displayName\": \"Big Head\" }, { \"tabType\":
  \"REMOTE\", \"contentUrl\":
  \"https://qa-gateway.myjosh.in/api/v1/camera/effect/assets/80?version=2&supported_assets=EFFECT,MASK,FU_AR_MASK,FU_STICKER,FU_GAME,FU_EXPRESSION_RECOGNITION,FU_FACE_WARP,FU_GESTURE_RECOGNITION,FU_BIGHEAD,FU_PORTRAIT_SEGMENTATION,FU_ANIMOJI,FU_PORTRAIT_SEGMENTATION_HUMAN_OUTLINE,FU_MAKEUP,FU_HAIR_COLOUR,FU_PORTRAIT_SEGMENTATION_BG_SEG_CUSTOM\",
  \"assetIds\": \[\], \"displayName\": \"7016effects\" }, { \"tabType\":
  \"REMOTE\", \"contentUrl\":
  \"https://qa-gateway.myjosh.in/api/v1/camera/effect/assets/73?version=14&supported_assets=EFFECT,MASK,FU_AR_MASK,FU_STICKER,FU_GAME,FU_EXPRESSION_RECOGNITION,FU_FACE_WARP,FU_GESTURE_RECOGNITION,FU_BIGHEAD,FU_PORTRAIT_SEGMENTATION,FU_ANIMOJI,FU_PORTRAIT_SEGMENTATION_HUMAN_OUTLINE,FU_MAKEUP,FU_HAIR_COLOUR,FU_PORTRAIT_SEGMENTATION_BG_SEG_CUSTOM\",
  \"assetIds\": \[\], \"displayName\": \"532xtest\" }, { \"tabType\":
  \"REMOTE\", \"contentUrl\":
  \"https://qa-gateway.myjosh.in/api/v1/camera/effect/assets/40?version=30&supported_assets=EFFECT,MASK,FU_AR_MASK,FU_STICKER,FU_GAME,FU_EXPRESSION_RECOGNITION,FU_FACE_WARP,FU_GESTURE_RECOGNITION,FU_BIGHEAD,FU_PORTRAIT_SEGMENTATION,FU_ANIMOJI,FU_PORTRAIT_SEGMENTATION_HUMAN_OUTLINE,FU_MAKEUP,FU_HAIR_COLOUR,FU_PORTRAIT_SEGMENTATION_BG_SEG_CUSTOM\",
  \"assetIds\": \[\], \"iconUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/camera_effects/test3.jpg\",
  \"displayName\": \"Mixed All\" } \], \"labelTimestamp\":
  1655884507500, \"version\": \"675\" } }

- **Request Method and URL:**

  GET :
  https://qa-gateway.coolfie.io/api/v1/camera/effect/assets/40?supported_assets=FILTER,EFFECT,MASK

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/camera/effect/assets/40?supported_assets=FILTER,EFFECT,MASK\'
  \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": \[ { \"id\":
  \"1AACCE79-7EAB-4B2E-AE9B-E53A02AFC055\", \"category\": 0, \"name\":
  \"Petal Shower\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/1AACCE79-7EAB-4B2E-AE9B-E53A02AFC055.3.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/1AACCE79-7EAB-4B2E-AE9B-E53A02AFC055.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=1AACCE79-7EAB-4B2E-AE9B-E53A02AFC055\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"7625B430-0E06-446C-A558-A18F33FA4FCE\", \"category\": 0, \"name\":
  \"Energy Swirl\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/7625B430-0E06-446C-A558-A18F33FA4FCE.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/7625B430-0E06-446C-A558-A18F33FA4FCE.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"hasSound\": false, \"alias\": \"\",
  \"sdkType\": \"\", \"assetType\": \"EFFECT\", \"categoryName\": \"\",
  \"showAnimation\": false, \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=7625B430-0E06-446C-A558-A18F33FA4FCE\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"62D20446-2E3D-4493-91CB-14B6E3160676\", \"category\": 0, \"name\":
  \"Holi\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/62D20446-2E3D-4493-91CB-14B6E3160676.1.arscene\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/62D20446-2E3D-4493-91CB-14B6E3160676.png\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"\",
  \"hasSound\": true, \"assetType\": \"MASK\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?mask_id=62D20446-2E3D-4493-91CB-14B6E3160676\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"0DA345FA-A13A-44B1-9549-3B79C9DE9EF2\", \"category\": 0, \"name\":
  \"Kitty\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/0DA345FA-A13A-44B1-9549-3B79C9DE9EF2.2.arscene\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/0DA345FA-A13A-44B1-9549-3B79C9DE9EF2.png\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"\",
  \"hasSound\": false, \"assetType\": \"MASK\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?mask_id=0DA345FA-A13A-44B1-9549-3B79C9DE9EF2\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"CA1D1AAD-8408-4204-986F-F28565D9729B\", \"category\": 0, \"name\":
  \"B/W Shake\", \"desc\": \"\", \"tags\": \"\", \"version\": 0,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/CA1D1AAD-8408-4204-986F-F28565D9729B.2.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/CA1D1AAD-8408-4204-986F-F28565D9729B.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"userAction\": \"\", \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=CA1D1AAD-8408-4204-986F-F28565D9729B\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"D18BD048-4176-4E14-B705-7E2A4DF08274\", \"category\": 0, \"name\":
  \"Iron Man\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/D18BD048-4176-4E14-B705-7E2A4DF08274.2.arscene\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/D18BD048-4176-4E14-B705-7E2A4DF08274.png\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"\",
  \"hasSound\": false, \"assetType\": \"MASK\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?mask_id=D18BD048-4176-4E14-B705-7E2A4DF08274\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"177F591D-5F0E-4321-BFFD-F2A79D50D91F\", \"category\": 0, \"name\":
  \"Water Bucket\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/177F591D-5F0E-4321-BFFD-F2A79D50D91F.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/177F591D-5F0E-4321-BFFD-F2A79D50D91F.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"alias\": \"Water Image\", \"assetType\": \"EFFECT\",
  \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=177F591D-5F0E-4321-BFFD-F2A79D50D91F\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"30638A40-F007-42A7-A411-EABF2AFBE5D2\", \"category\": 0, \"name\":
  \"Malik\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/30638A40-F007-42A7-A411-EABF2AFBE5D2.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/30638A40-F007-42A7-A411-EABF2AFBE5D2.1.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=30638A40-F007-42A7-A411-EABF2AFBE5D2\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"60CED887-CF60-4C58-8756-C9B8C5AFFBCC\", \"category\": 0, \"name\":
  \"Dettol Looped\", \"version\": 0, \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/60CED887-CF60-4C58-8756-C9B8C5AFFBCC.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/60CED887-CF60-4C58-8756-C9B8C5AFFBCC.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\": \"EFFECT\",
  \"assetType\": \"EFFECT\", \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?effect_id=60CED887-CF60-4C58-8756-C9B8C5AFFBCC\",
  \"pass_through\": \"EFFECT\" }, { \"id\":
  \"553463AB-6F40-4CAF-B0D8-DB3AD3AA6B24\", \"category\": 1, \"name\":
  \"Swiss\", \"desc\": \"\", \"tags\": \"\", \"version\": 2,
  \"minAppVersion\": \"\", \"packageUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/553463AB-6F40-4CAF-B0D8-DB3AD3AA6B24.1.videofx\",
  \"packageSize\": 0, \"coverUrl\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/553463AB-6F40-4CAF-B0D8-DB3AD3AA6B24.jpg\",
  \"supportedAspectRatio\": 0, \"idx\": 0, \"filterType\":
  \"SIMPLE_FILTER\", \"userAction\": \"\", \"assetType\": \"FILTER\",
  \"deeplinkUrl\":
  \"https://qa-share.myjosh.in/camera/details?filter_id=553463AB-6F40-4CAF-B0D8-DB3AD3AA6B24\",
  \"pass_through\": \"EFFECT\" } \], \"version\": 30, \"hasNext\": true
  }

- **Request Method and URL:**

  GET : https://qa-gateway.coolfie.io/api/v1/app/themes/info?version=34

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/app/themes/info?version=34\' \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { \"version\": \"34\",
  \"bottom_bar\": { \"discovery\": { \"active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/ZGlzY292ZXJ5.jpeg\",
  \"non_active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/ZGlzY292ZXJ5MQ==.jpeg\",
  \"home_non_active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/ZGlzY292ZXJ5LWRvd25sb2Fk.png\"
  }, \"profile\": { \"active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/cHJvZmlsZQ==.jpeg\",
  \"non_active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/cHJvZmlsZTE=.jpeg\",
  \"home_non_active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/ZG93bmxvYWQtbG92ZQ==.jpeg\"
  }, \"create\": { \"active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/Y3JlYXRl.jpeg\",
  \"non_active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/UG9saXRpY2FsLUJhbm5lcjE1.jpg\"
  }, \"home\": { \"active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/cGx1dG8=.jpeg\",
  \"non_active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/Zm9yeW91.jpeg\"
  } } } }

- **Request Method and URL:**

  GET : https://qa-gateway.coolfie.io/api/v1/app/themes/cms/info

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/app/themes/cms/info\'

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": \[ { \"themeId\": 1,
  \"themeName\": \"Bottom bar\", \"tabData\": \[ { \"tabId\": 1,
  \"tabName\": \"home\", \"active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/cGx1dG8=.jpeg\",
  \"non_active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/Zm9yeW91.jpeg\",
  \"max_version\": \"7.2.0\", \"min_version\": \"0.0.0\" }, { \"tabId\":
  2, \"tabName\": \"discovery\", \"active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/ZGlzY292ZXJ5.jpeg\",
  \"non_active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/ZGlzY292ZXJ5MQ==.jpeg\",
  \"home_non_active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/ZGlzY292ZXJ5LWRvd25sb2Fk.png\",
  \"max_version\": \"7.2.0\", \"min_version\": \"0.0.0\" }, { \"tabId\":
  3, \"tabName\": \"create\", \"active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/Y3JlYXRl.jpeg\",
  \"non_active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/UG9saXRpY2FsLUJhbm5lcjE1.jpg\",
  \"max_version\": \"7.2.0\", \"min_version\": \"0.0.0\" }, { \"tabId\":
  4, \"tabName\": \"notification\", \"active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/bm9pdGlm.jpeg\",
  \"non_active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/bm90aWZmZg==.jpeg\",
  \"home_non_active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/ZG93bmxvYWQtbm90aWZmZg==.jpeg\",
  \"start_date\": 1659872864821, \"end_date\": 1660716177871,
  \"max_version\": \"7.2.0\", \"min_version\": \"0.0.0\" }, { \"tabId\":
  5, \"tabName\": \"profile\", \"active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/cHJvZmlsZQ==.jpeg\",
  \"non_active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/cHJvZmlsZTE=.jpeg\",
  \"home_non_active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/ZG93bmxvYWQtbG92ZQ==.jpeg\",
  \"max_version\": \"7.2.0\", \"min_version\": \"0.0.0\" }, { \"tabId\":
  6, \"tabName\": \"game\", \"active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/cHJvZmlsZQ==.jpeg\",
  \"non_active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/Z2FtZTI=.png\",
  \"home_non_active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/Z2FtZTE=.png\",
  \"start_date\": 1650180663349, \"end_date\": 1650353465980,
  \"max_version\": \"7.2.0\", \"min_version\": \"0.0.0\" }, { \"tabId\":
  13, \"tabName\": \"home\", \"max_version\": \"100.0.0\",
  \"min_version\": \"7.2.0\" }, { \"tabId\": 14, \"tabName\":
  \"discovery\", \"active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/search_selected_1.png\",
  \"non_active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/search_1.png\",
  \"start_date\": 1660029975632, \"end_date\": 1660634779703,
  \"max_version\": \"100.0.0\", \"min_version\": \"7.2.0\" }, {
  \"tabId\": 15, \"tabName\": \"shop\", \"max_version\": \"100.0.0\",
  \"min_version\": \"7.2.0\" }, { \"tabId\": 16, \"tabName\": \"live\",
  \"max_version\": \"100.0.0\", \"min_version\": \"7.2.0\" }, {
  \"tabId\": 17, \"tabName\": \"notification\", \"active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/message_selected_32.png\",
  \"non_active_state\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/app_themes/bm90aQ==.png\",
  \"start_date\": 1659425446929, \"end_date\": 1661062991819,
  \"max_version\": \"100.0.0\", \"min_version\": \"7.2.0\" }, {
  \"tabId\": 18, \"tabName\": \"profile\", \"max_version\": \"100.0.0\",
  \"min_version\": \"7.2.0\" } \] }, { \"themeId\": 2, \"themeName\":
  \"App icon\", \"tabData\": \[ { \"tabId\": 27, \"tabName\":
  \"app_icon\", \"max_version\": \"100.0.0\", \"min_version\": \"0.0.0\"
  } \] }, { \"themeId\": 3, \"themeName\": \"Splash\", \"tabData\": \[ {
  \"tabId\": 28, \"tabName\": \"Splash\", \"max_version\": \"100.0.0\",
  \"min_version\": \"0.0.0\" } \] } \] }

- **Request Method and URL:**

  POST : https://qa-gateway.coolfie.io/api/v1/app/themes/3/cms/update

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/app/themes/3/cms/update\' \\

  \--form \'endDate=\"1729785455000\"\'

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { } }

- **Request Method and URL:**

  GET : https://qa-gateway.coolfie.io/api/v1/app/themes/cms/appIconIds

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/app/themes/cms/appIconIds\' \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": \[ \"DEFAULT_APP_ICON\",
  \"APP_ICON_1\", \"APP_ICON_2\" \] }

- **Request Method and URL:**

  GET : https://qa-gateway.coolfie.io/api/v1/analytics/hello

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/analytics/hello\' \\

  \--header \'Content-Type: application/json\' \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 } }

- **Request Method and URL:**

  GET :
  https://qa-gateway.coolfie.io/api/v1/community/details/22039c81-be7e-4de4-bdbc-a6450d147317

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/community/details/22039c81-be7e-4de4-bdbc-a6450d147317\'
  \\

  \--header \'Content-Type: application/json\' \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { } }

- **Request Method and URL:**

  GET : https://qa-gateway.coolfie.io/api/v1/cruise/info

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/cruise/info\' \\

  \--header \'Content-Type: application/json\' \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { \"environment\": \"qa\",
  \"buildVersion\": \"20220907\", \"buildDate\": \"07-09-2022\",
  \"properties\": { \"file\": { \"DNS_INFO.ttl\": \"-1\",
  \"ab.segment.base.url\": \"qa-abof.myjosh.in\",
  \"ab.service.call.enabled.from.app.version.android\": \"4.4.9\",
  \"ab.service.call.enabled.from.app.version.ios\": \"\",
  \"ab.service.call.enabled.till.app.version.android\": \"4.9.0\",
  \"ab.service.call.enabled.till.app.version.ios\": \"\",
  \"ab.service.call.enabled.till.app.version.pwa\": \"\",
  \"ab.testing.enabled.percentage\": \"10\",
  \"abof.home.tab.experiment.short.name\": \"pth\",
  \"abof.home.tab.identifier\": \"For You\",
  \"abof.local.cache.experiment.short.name\": \"cache\",
  \"abof.local.cache.identifier\": \"true\",
  \"activity.nudge.url.folder\": \"activities/\",
  \"ads.brand.list.version.url.template\":
  \"/apij/brand/list/v1?version={0}\", \"ads.handshake.content.url\":
  \"/api/v2/handshake\", \"ads.new.handshake.base.url\":
  \"http://qa-money.coolfie.io\", \"analytics.base.url\":
  \"http://qa-data.dailyhunt.io\", \"analytics.url\":
  \"http://beacon-qa.rtp.dailyhunt.in/topics/analytics-events-coolfie\",
  \"android.clear.session.data\": \"false\",
  \"android.clear.session.data.version\": \"3.0.0\",
  \"android.new.ads.handshake.from.version\": \"3.0.0\",
  \"api.base.url\": \"http://qa-api.coolfie.io\",
  \"api.delete.account.url.template\": \"deleteAccount\",
  \"api.discovery.audio.page.url.template\": \"/page/audio/{0}\",
  \"api.discovery.collection.url.template\": \"/v1/feed\",
  \"api.discovery.page.url.template\": \"/page/discovery/{0}\",
  \"api.material.info.template\":
  \"/api/v1/materialinfo/{0}?version={1}\",
  \"api.music.search.url.template\":
  \"/soundboard/v2/search/?tab_id=sr&page=0&rows=10\",
  \"api.upload.url.template\": \"/content\",
  \"api.user.handshake.url.template\": \"/user/handshake-config\",
  \"api.version.info.template\":
  \"/api/v1/upgrade/version/info/{0}/{1}\", \"app.theme.app.icons.ids\":
  \"{\\\"DEFAULT_APP_ICON\\\":\\\"DEFAULT_APP_ICON.png\\\",\\\"APP_ICON_1\\\":\\\"APP_ICON_1.png\\\",\\\"APP_ICON_2\\\":\\\"APP_ICON_2.png\\\"}\",
  \"app.theme.cron.expression\": \"0 0 2 \* \* \*\",
  \"app.themes.s3.url.folder\": \"app_themes/\",
  \"app.themes.version.url\": \"/api/v1/app/themes/info?version={0}\",
  \"app.tomcat.stuck-thread-detection.interrupt.thread.thresold\":
  \"1\", \"app.tomcat.stuck-thread-detection.thresold\": \"1\",
  \"audio.tab.cms.content.url.path\":
  \"/audio/list?categoryId=##CATEGORY_KEY##&lang=##LANG_CODE##\",
  \"audio.tab.picker.versioned.api.url\":
  \"/api/v1/audio/tabs?version={0}&langCode={1}\",
  \"aws.access.key.id\": \"\", \"aws.default.region\": \"ap-south-1\",
  \"aws.secret.key.id\": \"\", \"banner.meta.content.url\":
  \"/challenge/batch-get\", \"banner.title.deeplink\":
  \"https://qa-share.myjosh.in/challenge/7728e9ee-c1c2-4812-84de-95f97da7b13a\",
  \"base.url\": \"https://qa-api.coolfie.io\", \"base.url.quic\":
  \"https://qa-stream-g.coolfie.io\", \"bitmoji.base.url\":
  \"https://bitmoji.api.snapchat.com/api\", \"bitmoji.content.api\":
  \"/direct/pack/popular?limit={0}&page=1\", \"bitmoji.search.api\":
  \"/direct/search?limit={0}\", \"build.server\": \"\",
  \"cache.block.master.writes\": \"false\",
  \"cache.fallback.master.for.read\": \"false\",
  \"cache.key.replace.regx\": \"\[\\\\\[\\\\\], =\]\",
  \"cache.master.scan.delay\": \"3600000\", \"cache.prefill.enabled\":
  \"true\", \"cache.prefill.regions\":
  \"JOSH_HANDSHAKE,HANDSHAKE,VERSION_INFO,VIDEO_MATERIAL,ZERO_SEARCH,TOPOLOGY,COMMUNITY,LANG_LIST,CATEGORIES,CAMERA_EFFECT_TABS,CAMERA_ASSET_TYPES,JOSH_STICKERS,JOSH_STICKERS_TABS,COMMENT_STICKER_TABS,COMMENT_STICKERS,APP_THEME,ENCRYPTION,ACTIVITY_NUDGE\",
  \"cache.read.disabling.allowed\": \"true\", \"cache.store.on.error\":
  \"true\", \"cache.sync.enabled\": \"false\",
  \"cached.properties.include.file.types\": \"properties\",
  \"cached.properties.refresh.millis\": \"60000\",
  \"camera.carousal.tab.name\": \"Camera Carousal\",
  \"camera.effect.assets.cms.default.page.size\": \"10\",
  \"camera.effect.assets.default.page.size\": \"15\",
  \"camera.effect.assets.url.template\":
  \"/api/v1/camera/effect/assets/{0}?version={1}&supported_assets={2}\",
  \"camera.effect.tab.folder\": \"camera_effects/\",
  \"camera.effect.tabs.url.template\":
  \"/api/v1/camera/effect/tabs?version={0}&supported_assets={1}&page={2}&size={3}\",
  \"camera.effects.tabs.version.url.template\":
  \"/api/v1/camera/effect/tabs?version={0}\",
  \"camera.filters.url.template\":
  \"/api/v1/material/2/list?filterType=SIMPLE_FILTER&version={0}\",
  \"camera.sticker.supported.mime.types\": \"png,animatedsticker,jpeg\",
  \"category.title.deeplink\":
  \"https://qa-share.myjosh.in/challenge/7728e9ee-c1c2-4812-84de-95f97da7b13a\",
  \"cleanup.cron.expression\": \"0 0 2 \* \* SUN\",
  \"cleanup.removal.folders\":
  \"/home/josh_gateway/nhlogs/tomcat,/home/josh_gateway/nhlogs\",
  \"cms.sticker.assets.default.page.size\": \"25\",
  \"comment.sticker.assets.url.template\":
  \"/api/v1/comment/stickers/assets?tabId={0}&version={1}\",
  \"comment.sticker.supported.mime.types\": \"png,webp,jpeg\",
  \"comment.sticker.tabs.version.url.template\":
  \"/api/v1/comment/stickers/tabs?version={0}\",
  \"comment.stickers.thumbnail.folder\": \"comment_stickers/\",
  \"comment.stickers.url.folder\": \"comment_stickers/\",
  \"connection.request.timeout\": \"2000\",
  \"content.report.service.content.url\": \"/content/report\",
  \"cookie.domain\": \"coolfie.io\",
  \"cookies.writing.to.redis.enabled.apis\":
  \"/josh/handshake,/handshake\", \"coolfie.domain\": \"coolfie.io\",
  \"creator.meta.content.url\": \"/user/batch-get\",
  \"creator.title.deeplink\":
  \"https://qa-share.myjosh.in/challenge/7728e9ee-c1c2-4812-84de-95f97da7b13a\",
  \"cron.key.value.cache.refresh.process\": \"60000\",
  \"cronet.app.id\": \"RsgybJFsJ4oFGjejb9yxl\",
  \"cronet.app.short.name\": \"jqa\", \"cronet.experiment.short.name\":
  \"strmU\", \"cronet.project.id\": \"fFx_w0K8gwAfP-k-ogoql\",
  \"cronet.project.short.name\": \"gtwy\",
  \"deeplink.whitelisted.domains\":
  \"\[\\\"www.myjosh.in\\\",\\\"share.myjosh.in\\\",\\\"qa-share.myjosh.in\\\",\\\"feed.coolfie.io\\\",\\\"api.coolfie.io\\\",\\\"qa-api.coolfie.io\\\",\\\"qa-feed.coolfie.io\\\",\\\"www.coolfie.io\\\",\\\"coolfie.io\\\",\\\"share.coolfie.io\\\",\\\"dev-share.coolfie.io\\\",\\\"stage-share.coolfie.io\\\",\\\"stage-share.myjosh.in\\\",\\\"qa-feed.myjosh.in\\\",\\\"feed.myjosh.in\\\",\\\"qa-api.myjosh.in\\\",\\\"api.myjosh.in\\\",\\\"myjosh.in\\\",\\\"dev-share.myjosh.in\\\"\]\",
  \"default.cache.async.refresh.millis\": \"300000\",
  \"default.cookie.expire.seconds\": \"315360000\",
  \"default.lang.key\": \"na\", \"default.lang.set\": \"hi,en\",
  \"default.tab.id.for.josh.stickers\": \"9\",
  \"delete.fallback.notification.path\":
  \"/api/obelix/fallback/delete\", \"delete.notification.path\":
  \"/api/obelix/fallback/delete\", \"deploy.env\": \"qa\",
  \"dh.app.metrics.CASSANDRA.attribution.enabled\": \"true\",
  \"dh.app.metrics.COMPONENT.attribution.enabled\": \"true\",
  \"dh.app.metrics.CONTROLLER.attribution.enabled\": \"true\",
  \"dh.app.metrics.DATA_ACCESS_POINTS.attribution.enabled\": \"true\",
  \"dh.app.metrics.ELASTICSEARCH.attribution.enabled\": \"true\",
  \"dh.app.metrics.EXTERNAL_SERVICES.attribution.enabled\": \"true\",
  \"dh.app.metrics.GROUP.attribution.enabled\": \"true\",
  \"dh.app.metrics.HEADLINES.attribution.enabled\": \"true\",
  \"dh.app.metrics.HYSTRIX.attribution.enabled\": \"true\",
  \"dh.app.metrics.KAFKA.attribution.enabled\": \"true\",
  \"dh.app.metrics.LEVEL0.attribution.enabled\": \"true\",
  \"dh.app.metrics.LEVEL1.attribution.enabled\": \"true\",
  \"dh.app.metrics.LOCATION.attribution.enabled\": \"true\",
  \"dh.app.metrics.MYSQL.attribution.enabled\": \"true\",
  \"dh.app.metrics.NEWSPAPER.attribution.enabled\": \"true\",
  \"dh.app.metrics.PUBLISHERNEWS.attribution.enabled\": \"true\",
  \"dh.app.metrics.REDIS.attribution.enabled\": \"true\",
  \"dh.app.metrics.RELATEDNEWS.attribution.enabled\": \"true\",
  \"dh.app.metrics.RESTTEMPLATE.attribution.enabled\": \"true\",
  \"dh.app.metrics.STORY.attribution.enabled\": \"true\",
  \"dh.app.metrics.SYNDICATION.attribution.enabled\": \"true\",
  \"dh.app.metrics.TICKER.attribution.enabled\": \"true\",
  \"dh.app.metrics.TOPIC.attribution.enabled\": \"true\",
  \"dh.app.metrics.USERPAGE.attribution.enabled\": \"true\",
  \"dh.app.metrics.WEBITEM.attribution.enabled\": \"true\",
  \"disable.dns.caching\": \"false\", \"disable.nlfc\": \"false\",
  \"discovery.search.version.api.template\":
  \"/api/v1/upgrade/discovery/search?version={0}\",
  \"discovery.section.BANNER.collection.title\": \"Challenge Banner\",
  \"discovery.section.CATEGORY.collection.title\": \"Categories\",
  \"discovery.section.CREATOR.collection.title\": \"Popular Creators\",
  \"discovery.section.FEED.collection.title\": \"Feed\",
  \"discovery.section.HASHTAG.challenge.enabled.list\":
  \"funny,dance,cute,life,talent,travel,friendship_challenge\",
  \"discovery.section.HASHTAG.collection.title\": \"Popular Hashtags\",
  \"discovery.section.MUSIC.collection.title\": \"Music\",
  \"discovery.section.TRENDING_DUET.collection.title\": \"Trending
  Duet\", \"discovery.trending.tab.info\":
  \"{\\\"id\\\":\\\"main-trending-page\\\",\\\"name\\\":\\\"Trends\\\",\\\"tab_icon_url\\\":\\\"trending_icon\\\",\\\"url\\\":\\\"https://qa-feed.coolfie.io/page/trending/main-trending-page\\\",\\\"type\\\":\\\"TRENDING\\\"}\",
  \"discovery.trends.tab.index\": \"1\",
  \"discovery.trends.tab.version.android\": \"5.0.1\",
  \"discovery.trends.tab.version.ios\": \"4.0.0\",
  \"dns.config.url.template\": \"/api/v1/upgrade/dns?version={0}\",
  \"dns.entries\":
  \"\[{\\\"hostname\\\":\\\"qa-gateway.coolfie.io\\\",\\\"ip\\\":\[\\\"180.179.92.138\\\"\],\\\"heartbeatUrl\\\":\\\"https://qa-gateway.coolfie.io/api/v1/health\\\"},{\\\"hostname\\\":\\\"qa-api.coolfie.io\\\",\\\"ip\\\":\[\\\"180.179.92.137\\\"\],\\\"heartbeatUrl\\\":\\\"http://qa-api.coolfie.io/admin/healthcheck\\\"},{\\\"hostname\\\":\\\"qa-feed.coolfie.io\\\",\\\"ip\\\":\[\\\"180.179.92.136\\\"\],\\\"heartbeatUrl\\\":\\\"https://qa-feed.coolfie.io/health\\\"},{\\\"hostname\\\":\\\"josh-notif-inbox-qa.coolfie.io\\\",\\\"ip\\\":\[\\\"180.179.92.135\\\"\],\\\"heartbeatUrl\\\":\\\"http://josh-notif-inbox-qa.coolfie.io/api/obelix/oor\\\"},{\\\"hostname\\\":\\\"qa-stream.coolfie.io\\\",\\\"ip\\\":\[\\\"180.179.92.134\\\"\],\\\"heartbeatUrl\\\":\\\"https://qa-stream.coolfie.io/healthcheck\\\"},{\\\"hostname\\\":\\\"qa-share.myjosh.in\\\",\\\"ip\\\":\[\\\"180.179.92.133\\\"\],\\\"heartbeatUrl\\\":\\\"https://qa-share.myjosh.in/hc.html\\\"}\]\",
  \"dns.first.level.cache.ttl\": \"86400000\", \"dns.lookup.timeout\":
  \"5000\", \"dns.schedule.heartbeat.interval\": \"900000\",
  \"dns.second.level.cache.ttl\": \"86400000\",
  \"duet.meta.thumbnail.quality\": \"h\",
  \"duet.meta.thumbnail.resolution\": \"165\",
  \"duet.meta.thumbnail.type\": \"still\",
  \"duetable.flag.enabled.duet.meta\": \"false\",
  \"effects.es.upload.enabled\": \"true\",
  \"element.level.share.url.format\": \"{0}/camera/details?{1}={2}\",
  \"empty.cookie.expire.seconds\": \"60\", \"enable.custom.feed.meta\":
  \"true\", \"enable.custom.feed.meta.android\": \"true\",
  \"enable.custom.feed.meta.ios\": \"true\",
  \"enable.video.assets.not.shown.in.thumbnail.android\": \"true\",
  \"enable.video.assets.not.shown.in.thumbnail.ios\": \"true\",
  \"encryption.key.api\": \"/api/v1/sdk/latestkey/\",
  \"encryption.key.cache.async.refresh.millis\": \"21600000\",
  \"exclude.discovery.in.handshake.from\": \"2.3.0\",
  \"extra.handshake.boolean.configuration\":
  \"enable_video_download_on_share-\>true;;is_firebase_event_enabled-\>true;;hit_firebase_event_once-\>true;;dev_error_for_2xxTo4xx_enabled-\>false;;enableGzip_v2-\>true;;allowEmptyTitleInCreatePost-\>false;;enable_whatsapp_share-\>true\",
  \"extra.handshake.boolean.configuration.for.CoolfieHome\": \"\",
  \"extra.handshake.configuration\": \"followersTabName-\>Top Fans\",
  \"extra.handshake.configuration.for.CoolfieHome\": \"\",
  \"extra.handshake.integer.configuration\":
  \"location_prompt_for_max_time_count-\>2;;location_prompt_after_max_post_count-\>1;;max_recent_interaction_count-\>50;;max_recent_navigable_action_count-\>30;;min_upload_duration-\>5;;max_upload_size-\>50;;handshakeDefaultInterval-\>43200000;;maxApiDelay-\>2000;;timerPeriodInSeconds-\>60;;maxErrorEventPerInterval-\>10;;upload_duration_v2-\>60;;firstTimePullDelay-\>60\",
  \"extra.handshake.integer.configuration.for.CoolfieHome\":
  \"max_version_for_mandatory_update-\>0;;max_version_for_flexible_update-\>100000;;min_gap_between_app_update_prompt_secs-\>172800;;video_views_in_session_for_update_prompt-\>5\",
  \"face.unity.type.ids\": \"25,26,27,28,29,30,31,32,33,34,35,36,37\",
  \"faqs.config.url\": \"http://support.myjosh.in/support/home\",
  \"feed.base.url\": \"https://qa-feed.coolfie.io\",
  \"feed.title.deeplink\":
  \"https://qa-share.myjosh.in/challenge/7728e9ee-c1c2-4812-84de-95f97da7b13a\",
  \"feed.type.meta.core.threadpool.size\": \"40\",
  \"feed.type.meta.fetch.timeout\": \"1000\",
  \"feed.type.meta.max.threadpool.size\": \"400\",
  \"feed.type.meta.service.connection.request.timeout\": \"1000\",
  \"feed.type.meta.service.url.connection.timeout\": \"1000\",
  \"feed.type.meta.service.url.read.timeout\": \"1000\",
  \"feed.types.for.meta.call\": \"BANNER,MUSIC,TRENDING_DUET,POPULAR
  CREATORS\", \"gateway.base.url\": \"https://qa-gateway.coolfie.io\",
  \"global.search.tabs.v2.app.android.version\": \"4.11.0\",
  \"global.search.tabs.v2.app.ios.version\": \"2.1.0\",
  \"global.search.tabs.v2.template\":
  \"/api/v2/upgrade/version/info/{0}/{1}?langCode={2}\",
  \"handshake.base.urls\": \"{\\\"GATEWAY\\\":\\\"gateway.base.url\\\",
  \\\"ONBOARD\\\": \\\"api.base.url\\\"}\",
  \"handshake.base.urls.config\":
  \"{\\\"delete_account_url\\\":\\\"https://qa-share.myjosh.in/deleteAccount\\\",\\\"apply_for_verification_url\\\":\\\"https://qa-share.myjosh.in/webview/apply-verification\\\",\\\"profile_insights_url\\\":\\\"https://qa-share.myjosh.in/analytics/profile-insight/\\\",\\\"content_insights_url\\\":\\\"https://qa-share.myjosh.in/analytics/content-insight/\\\",\\\"sso_url\\\":\\\"https://qa-api.coolfie.io\\\",\\\"interest_list_url\\\":\\\"https://qa-feed.coolfie.io/feed/interestlist?version=1\\\",\\\"experiment_url\\\":\\\"http://76.223.34.165/api/run\\\",\\\"application_url_v2\\\":\\\"https://qa-api.coolfie.io/apij\\\",\\\"image_share_url\\\":\\\"https://qa-api.myjosh.in/image/\\\",\\\"social_share_url\\\":\\\"https://qa-api.myjosh.in/social/\\\",\\\"template_list_url\\\":\\\"https://qa-api.myjosh.in/apij/template/list?page=0&size=5\\\",\\\"template_search_url\\\":\\\"https://qa-feed.myjosh.in/TEMPLATE/search?page=0&size=10\\\"}\",
  \"handshake.home.tab.list.json\": \"\[{\\\"url\\\":
  \\\"http://qa-feed.coolfie.io/feed/followings?lang_code={0}\\\",
  \\\"feed_type\\\": \\\"HOME\\\", \\\"name\\\":
  \\\"home.tab.following.name.en\\\", \\\"landing_tab\\\": false,
  \\\"identifier\\\": \\\"following\\\"}, {\\\"url\\\":
  \\\"http://qa-feed.coolfie.io/feed/foryou?lang_code={0}\\\",
  \\\"feed_type\\\": \\\"HOME\\\", \\\"name\\\":
  \\\"home.tab.forYou.name.en\\\", \\\"landing_tab\\\": true,
  \\\"identifier\\\": \\\"forYou\\\"}\]\", \"hashtag.title.deeplink\":
  \"https://qa-share.myjosh.in/challenge/7728e9ee-c1c2-4812-84de-95f97da7b13a\",
  \"hit.report.service\": \"true\", \"home.tab.following.name.en\":
  \"Following\", \"home.tab.forYou.name.en\": \"For You\",
  \"html.chunk.size\": \"500\", \"https.enabled.pull.notifications\":
  \"true\", \"include.archived.video.resources.version.upto\":
  \"2.3.13\", \"include.community.for.version.upto\": \"1.1\",
  \"include.discovery.search.from.version.onwards\": \"2.0.14\",
  \"include.zero.search.for.version.upto\": \"2.0.16\",
  \"inmemory.ACTIVITY_NUDGE.enable\": \"true\",
  \"inmemory.ACTIVITY_NUDGE.expireAfterWriteSecs\": \"3600\",
  \"inmemory.ACTIVITY_NUDGE.size\": \"50\",
  \"inmemory.APP_THEME.enable\": \"true\",
  \"inmemory.APP_THEME.expireAfterWriteSecs\": \"3600\",
  \"inmemory.APP_THEME.size\": \"50\", \"inmemory.AUDIO_TABS.enable\":
  \"true\", \"inmemory.AUDIO_TABS.expireAfterWriteSecs\": \"3600\",
  \"inmemory.AUDIO_TABS.size\": \"1000\", \"inmemory.AWS_S3.enable\":
  \"true\", \"inmemory.AWS_S3.expireAfterWriteSecs\": \"300\",
  \"inmemory.AWS_S3.size\": \"100\",
  \"inmemory.CAMERA_ASSET_TYPES.enable\": \"true\",
  \"inmemory.CAMERA_ASSET_TYPES.expireAfterWriteSecs\": \"3600\",
  \"inmemory.CAMERA_ASSET_TYPES.size\": \"200\",
  \"inmemory.CAMERA_EFFECT_TABS.enable\": \"true\",
  \"inmemory.CAMERA_EFFECT_TABS.expireAfterWriteSecs\": \"3600\",
  \"inmemory.CAMERA_EFFECT_TABS.size\": \"100\",
  \"inmemory.CATEGORIES.enable\": \"true\",
  \"inmemory.CATEGORIES.expireAfterWriteSecs\": \"3600\",
  \"inmemory.CATEGORIES.size\": \"1000\",
  \"inmemory.COMMENT_STICKERS.enable\": \"true\",
  \"inmemory.COMMENT_STICKERS.expireAfterWriteSecs\": \"3600\",
  \"inmemory.COMMENT_STICKERS.size\": \"1000\",
  \"inmemory.COMMENT_STICKER_TABS.enable\": \"true\",
  \"inmemory.COMMENT_STICKER_TABS.expireAfterWriteSecs\": \"3600\",
  \"inmemory.COMMENT_STICKER_TABS.size\": \"1000\",
  \"inmemory.COMMUNITY.enable\": \"true\",
  \"inmemory.COMMUNITY.expireAfterWriteSecs\": \"3600\",
  \"inmemory.COMMUNITY.size\": \"1000\",
  \"inmemory.DB_KEY_VALUE_CONF.enable\": \"true\",
  \"inmemory.DB_KEY_VALUE_CONF.expireAfterWriteSecs\": \"60\",
  \"inmemory.DB_KEY_VALUE_CONF.size\": \"10\",
  \"inmemory.DH_HANDSHAKE.enable\": \"true\",
  \"inmemory.DH_HANDSHAKE.expireAfterWriteSecs\": \"300\",
  \"inmemory.DH_HANDSHAKE.size\": \"20\",
  \"inmemory.DH_ZERO_SEARCH.enable\": \"true\",
  \"inmemory.DH_ZERO_SEARCH.expireAfterWriteSecs\": \"300\",
  \"inmemory.DH_ZERO_SEARCH.size\": \"1000\",
  \"inmemory.DNS_INFO.enable\": \"true\",
  \"inmemory.DNS_INFO.expireAfterWriteSecs\": \"172800\",
  \"inmemory.DNS_INFO.size\": \"50\",
  \"inmemory.FEED_TYPE_META.enable\": \"true\",
  \"inmemory.FEED_TYPE_META.expireAfterWriteSecs\": \"28800\",
  \"inmemory.FEED_TYPE_META.size\": \"2000\",
  \"inmemory.HANDSHAKE.enable\": \"true\",
  \"inmemory.HANDSHAKE.expireAfterWriteSecs\": \"3600\",
  \"inmemory.HANDSHAKE.size\": \"20\", \"inmemory.JOSH_FONTS.enable\":
  \"true\", \"inmemory.JOSH_FONTS.expireAfterWriteSecs\": \"3600\",
  \"inmemory.JOSH_FONTS.size\": \"1000\",
  \"inmemory.JOSH_HANDSHAKE.enable\": \"true\",
  \"inmemory.JOSH_HANDSHAKE.expireAfterWriteSecs\": \"3600\",
  \"inmemory.JOSH_HANDSHAKE.size\": \"50\",
  \"inmemory.JOSH_STICKERS.enable\": \"true\",
  \"inmemory.JOSH_STICKERS.expireAfterWriteSecs\": \"3600\",
  \"inmemory.JOSH_STICKERS.size\": \"1000\",
  \"inmemory.JOSH_STICKERS_TABS.enable\": \"true\",
  \"inmemory.JOSH_STICKERS_TABS.expireAfterWriteSecs\": \"3600\",
  \"inmemory.JOSH_STICKERS_TABS.size\": \"1000\",
  \"inmemory.LANG_LIST.enable\": \"true\",
  \"inmemory.LANG_LIST.expireAfterWriteSecs\": \"3600\",
  \"inmemory.LANG_LIST.size\": \"50\", \"inmemory.REPORT.enable\":
  \"true\", \"inmemory.REPORT.expireAfterWriteSecs\": \"300\",
  \"inmemory.REPORT.size\": \"1000\", \"inmemory.TOPOLOGY.enable\":
  \"true\", \"inmemory.TOPOLOGY.expireAfterWriteSecs\": \"43200\",
  \"inmemory.TOPOLOGY.size\": \"5\", \"inmemory.USERS.enable\":
  \"true\", \"inmemory.USERS.expireAfterWriteSecs\": \"300\",
  \"inmemory.USERS.size\": \"1000\", \"inmemory.VERSIONED_API.enable\":
  \"true\", \"inmemory.VERSIONED_API.expireAfterWriteSecs\": \"28800\",
  \"inmemory.VERSIONED_API.size\": \"1000\",
  \"inmemory.VERSION_CMS_INFO.enable\": \"true\",
  \"inmemory.VERSION_CMS_INFO.expireAfterWriteSecs\": \"3600\",
  \"inmemory.VERSION_CMS_INFO.size\": \"500\",
  \"inmemory.VERSION_INFO.enable\": \"true\",
  \"inmemory.VERSION_INFO.expireAfterWriteSecs\": \"3600\",
  \"inmemory.VERSION_INFO.size\": \"200\",
  \"inmemory.VIDEO_MATERIAL.enable\": \"true\",
  \"inmemory.VIDEO_MATERIAL.expireAfterWriteSecs\": \"3600\",
  \"inmemory.VIDEO_MATERIAL.size\": \"50\",
  \"inmemory.ZERO_SEARCH.enable\": \"true\",
  \"inmemory.ZERO_SEARCH.expireAfterWriteSecs\": \"3600\",
  \"inmemory.ZERO_SEARCH.size\": \"1000\",
  \"ios.exclude.discovery.in.handshake.from\": \"1.2.0\",
  \"ios.include.discovery.search.from.version.onwards\": \"1.0.0\",
  \"ios.new.ads.handshake.from.version\": \"1.4.0\",
  \"josh.feedback.mail.subject.content\": \"Josh - Content Reported\",
  \"josh.feedback.mail.subject.profile\": \"Josh - Profile Reported\",
  \"josh.feedback.mail.subject.review.moderation\": \"Josh - Content
  Request for Review\", \"josh.feedback.mail.subject.user\": \"Josh -
  Profile Reported\", \"josh.feedback.mail.topic\":
  \"arn:aws:sns:ap-south-1:514352861371:Josh-Gateway-QA\",
  \"josh.fonts.thumbnail.folder\": \"josh_fonts/font-thumbnails/\",
  \"josh.fonts.url.folder\": \"josh_fonts/\",
  \"josh.fresh.ticket.name\": \"Josh Issue\",
  \"josh.freshdesk.secret.key\": \"BspI81X7LWE7Wyou99Of\",
  \"josh.freshdesk.ticket.cc.emails\": \"\",
  \"josh.freshdesk.ticket.create.url\": \"\",
  \"josh.freshdesk.ticket.disable\": \"false;\",
  \"josh.report.feedback.sns.disable\": \"false\",
  \"josh.report.feedback.subject\": \"Josh - Feedback Report\",
  \"josh.report.feedback.subject.enable\": \"false\",
  \"josh.report.feedback.topic\":
  \"arn:aws:sns:ap-south-1:514352861371:Josh-Report-Feedback-QA\",
  \"josh.stickers.thumbnail.folder\": \"josh_stickers/\",
  \"josh.stickers.url.folder\": \"josh_stickers/\",
  \"josh.support.email.disable\": \"false\", \"josh.target.group.arn\":
  \"arn:aws:elasticloadbalancing:ap-south-1:514352861371:targetgroup/internal-gw/f7a6df7795dcf7f5\",
  \"lang.codes\": \"All,bh,bn,en,gu,hi,kn,ml,mr,or,pa,ta,te\",
  \"lang.list.categories.tags.limit\": \"1\",
  \"lang.list.categories.tags.limit.enabled\": \"true\",
  \"lang.list.image.template\": \"%s/stream/%s/%s%s\",
  \"lang.list.remove.categories.enabled\": \"true\",
  \"lang.list.subtitle\": \"See videos made in this language\",
  \"lang.list.title\": \"Select your languages\",
  \"langlist.version.url.template\": \"/api/v1/langlist?version={0}\",
  \"latch.build.handshake.response.timeout\": \"1800\",
  \"latch.populate.discovery.section.timeout\": \"1200\",
  \"local.cache.ab.android.min.version\": \"2.5.0\",
  \"local.cache.ab.ios.min.version\": \"2.5.0\",
  \"local.cache.ab.testing.enabled\": \"true\", \"location.tab.index\":
  \"0\", \"location.tab.info\":
  \"{\\\"url\\\":\\\"https://qa-feed.coolfie.io/v1/feed/nearby\\\",\\\"name\\\":\\\"Nearby\\\",\\\"feed_type\\\":\\\"HOME\\\",\\\"landing_tab\\\":false,\\\"tab_type\\\":\\\"LOCATION\\\"}\",
  \"location.tab.version.android\": \"8.0.0\",
  \"location.tab.version.ios\": \"6.0.0\",
  \"log.client.payload.enabled\": \"true\",
  \"log.client.payload.response.time.thresold\": \"3000\",
  \"logs.retention.period\": \"7\", \"machine.out.of.rotation\":
  \"false\", \"metrics.profiling.API.CMS.enabled\": \"false\",
  \"metrics.profiling.AWS_S3.CMS.enabled\": \"false\",
  \"metrics.profiling.MySQL.CMS.enabled\": \"false\",
  \"metrics.profiling.RestClient.CMS.enabled\": \"false\",
  \"metrics.profiling.enabled.percentiles\": \"0.95,0.99\",
  \"metrics.profiling.from.servlet.filter.enabled\": \"true\",
  \"metrics.profiling.histogram.max.expected.value\": \"10\",
  \"min.offset.to.append\\\"\": \"0\", \"min.percentage.completion\":
  \"60\", \"min.time.spent.to.trigger\": \"6000\",
  \"min.time.spent.to.trigger.with.social\": \"6000\",
  \"moderation.duplicate.report.url\": \"report/ownership-content/1\",
  \"moderation.nsfw.report.url\": \"report/machine-moderation/1\",
  \"music.meta.content.url\": \"/audio/batch-get\",
  \"music.title.deeplink\":
  \"https://qa-share.myjosh.in/challenge/7728e9ee-c1c2-4812-84de-95f97da7b13a\",
  \"myjosh.ads.new.handshake.base.url\": \"http://qa-money.myjosh.in\",
  \"myjosh.analytics.base.url\": \"http://qa-data.dailyhunt.io\",
  \"myjosh.analytics.url\":
  \"http://beacon-qa.rtp.myjosh.in/topics/analytics-events-coolfie\",
  \"myjosh.api.base.url\": \"http://qa-api.myjosh.in\",
  \"myjosh.banner.title.deeplink\":
  \"https://qa-share.myjosh.in/challenge/7728e9ee-c1c2-4812-84de-95f97da7b13a\",
  \"myjosh.base.url\": \"https://qa-api.myjosh.in\",
  \"myjosh.base.url.quic\": \"https://qa-stream-g.myjosh.in\",
  \"myjosh.base.url.swap.map\": \"{\\\"locationservice.dailyhunt.in\\\":
  \\\"locationservice.myjosh.in\\\", \\\"beacon-qa.rtp.dailyhunt.in\\\":
  \\\"beacon-qa.rtp.myjosh.in\\\", \\\"accounts.dailyhunt.in\\\":
  \\\"accounts.myjosh.in\\\", \\\"qa-pullnotification.dailyhunt.in\\\":
  \\\"qa-pullnotification.myjosh.in\\\",
  \\\"qa-notifications.dailyhunt.in\\\":
  \\\"qa-notifications.myjosh.in\\\"}\", \"myjosh.bitmoji.base.url\":
  \"https://bitmoji.api.snapchat.com/api\",
  \"myjosh.category.title.deeplink\":
  \"https://qa-share.myjosh.in/challenge/7728e9ee-c1c2-4812-84de-95f97da7b13a\",
  \"myjosh.cookie.domain\": \"myjosh.in\",
  \"myjosh.creator.title.deeplink\":
  \"https://qa-share.myjosh.in/challenge/7728e9ee-c1c2-4812-84de-95f97da7b13a\",
  \"myjosh.deeplink.whitelisted.domains\":
  \"\[\\\"www.myjosh.in\\\",\\\"share.myjosh.in\\\",\\\"qa-share.myjosh.in\\\",\\\"feed.coolfie.io\\\",\\\"api.coolfie.io\\\",\\\"qa-api.coolfie.io\\\",\\\"qa-feed.coolfie.io\\\",\\\"www.coolfie.io\\\",\\\"coolfie.io\\\",\\\"share.coolfie.io\\\",\\\"dev-share.coolfie.io\\\",\\\"stage-share.coolfie.io\\\",\\\"stage-share.myjosh.in\\\",\\\"qa-feed.myjosh.in\\\",\\\"feed.myjosh.in\\\",\\\"qa-api.myjosh.in\\\",\\\"api.myjosh.in\\\",\\\"myjosh.in\\\",\\\"dev-share.myjosh.in\\\"\]\",
  \"myjosh.discovery.trending.tab.info\":
  \"{\\\"id\\\":\\\"main-trending-page\\\",\\\"name\\\":\\\"Trends\\\",\\\"tab_icon_url\\\":\\\"trending_icon\\\",\\\"url\\\":\\\"https://qa-feed.myjosh.in/page/trending/main-trending-page\\\",\\\"type\\\":\\\"TRENDING\\\"}\",
  \"myjosh.dns.entries\":
  \"\[{\\\"hostname\\\":\\\"qa-gateway.myjosh.in\\\",\\\"ip\\\":\[\\\"180.179.92.138\\\"\],\\\"heartbeatUrl\\\":\\\"https://qa-gateway.myjosh.in/api/v1/health\\\"},{\\\"hostname\\\":\\\"qa-api.myjosh.in\\\",\\\"ip\\\":\[\\\"180.179.92.137\\\"\],\\\"heartbeatUrl\\\":\\\"http://qa-api.myjosh.in/admin/healthcheck\\\"},{\\\"hostname\\\":\\\"qa-feed.myjosh.in\\\",\\\"ip\\\":\[\\\"180.179.92.136\\\"\],\\\"heartbeatUrl\\\":\\\"https://qa-feed.myjosh.in/health\\\"},{\\\"hostname\\\":\\\"josh-notif-inbox-qa.myjosh.in\\\",\\\"ip\\\":\[\\\"180.179.92.135\\\"\],\\\"heartbeatUrl\\\":\\\"http://josh-notif-inbox-qa.myjosh.in/api/obelix/oor\\\"},{\\\"hostname\\\":\\\"qa-stream.myjosh.in\\\",\\\"ip\\\":\[\\\"180.179.92.134\\\"\],\\\"heartbeatUrl\\\":\\\"https://qa-stream.myjosh.in/healthcheck\\\"},{\\\"hostname\\\":\\\"qa-share.myjosh.in\\\",\\\"ip\\\":\[\\\"180.179.92.133\\\"\],\\\"heartbeatUrl\\\":\\\"https://qa-share.myjosh.in/hc.html\\\"}\]\",
  \"myjosh.domain\": \"myjosh.in\",
  \"myjosh.domain.enabled.from.app.version.android\": \"4.5.0\",
  \"myjosh.domain.enabled.from.app.version.ios\": \"1.6.0\",
  \"myjosh.fallback.enabled\": \"false\", \"myjosh.faqs.config.url\":
  \"http://support.myjosh.in/support/home\", \"myjosh.feed.base.url\":
  \"https://qa-feed.myjosh.in\", \"myjosh.feed.title.deeplink\":
  \"https://qa-share.myjosh.in/challenge/7728e9ee-c1c2-4812-84de-95f97da7b13a\",
  \"myjosh.gateway.base.url\": \"https://qa-gateway.myjosh.in\",
  \"myjosh.handshake.base.urls.config\":
  \"{\\\"delete_account_url\\\":\\\"https://qa-share.myjosh.in/deleteAccount\\\",\\\"apply_for_verification_url\\\":\\\"https://qa-share.myjosh.in/webview/apply-verification\\\",\\\"profile_insights_url\\\":\\\"https://qa-share.myjosh.in/analytics/profile-insight/\\\",\\\"content_insights_url\\\":\\\"https://qa-share.myjosh.in/analytics/content-insight/\\\",\\\"sso_url\\\":\\\"https://qa-api.myjosh.in\\\",\\\"interest_list_url\\\":\\\"https://qa-feed.myjosh.in/feed/interestlist?version=1\\\",\\\"experiment_url\\\":\\\"http://76.223.34.165/api/run\\\",\\\"application_url_v2\\\":\\\"https://qa-api.myjosh.in/apij\\\",\\\"image_share_url\\\":\\\"https://qa-api.myjosh.in/image/\\\",\\\"social_share_url\\\":\\\"https://qa-api.myjosh.in/social/\\\",\\\"template_list_url\\\":\\\"https://qa-api.myjosh.in/apij/template/list?page=0&size=10\\\",\\\"template_search_url\\\":\\\"https://qa-feed.myjosh.in/TEMPLATE/search?page=0&size=10\\\"}\",
  \"myjosh.handshake.home.tab.list.json\": \"\[{\\\"url\\\":
  \\\"http://qa-feed.myjosh.in/feed/followings?lang_code={0}\\\",
  \\\"feed_type\\\": \\\"HOME\\\", \\\"name\\\":
  \\\"home.tab.following.name.en\\\", \\\"landing_tab\\\": false,
  \\\"identifier\\\": \\\"following\\\"}, {\\\"url\\\":
  \\\"http://qa-feed.myjosh.in/feed/foryou?lang_code={0}\\\",
  \\\"feed_type\\\": \\\"HOME\\\", \\\"name\\\":
  \\\"home.tab.forYou.name.en\\\", \\\"landing_tab\\\": true,
  \\\"identifier\\\": \\\"forYou\\\"}\]\",
  \"myjosh.hashtag.title.deeplink\":
  \"https://qa-share.myjosh.in/challenge/7728e9ee-c1c2-4812-84de-95f97da7b13a\",
  \"myjosh.location.tab.info\":
  \"{\\\"url\\\":\\\"https://qa-feed.myjosh.in/v1/feed/nearby\\\",\\\"name\\\":\\\"Nearby\\\",\\\"feed_type\\\":\\\"HOME\\\",\\\"landing_tab\\\":false,\\\"tab_type\\\":\\\"LOCATION\\\"}\",
  \"myjosh.music.title.deeplink\":
  \"https://qa-share.myjosh.in/challenge/7728e9ee-c1c2-4812-84de-95f97da7b13a\",
  \"myjosh.obelix.fallback.notification.hostname\":
  \"qa-josh-notif-inbox.myjosh.in\",
  \"myjosh.obelix.notification.topology.refresh.api\":
  \"http://qa-josh-notif-inbox.myjosh.in/api/obelix/topology_v2\",
  \"myjosh.onboard.base.url\": \"https://qa-api.myjosh.in\",
  \"myjosh.onboard.java.base.url\": \"qa-api.myjosh.in\",
  \"myjosh.page.base.url\": \"https://qa-feed.myjosh.in\",
  \"myjosh.popular.selected.tab.icon.url\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/handshake/selected_popular.png\",
  \"myjosh.popular.tab.icon.url\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/handshake/popular.png\",
  \"myjosh.pull.notification.hosts.mapping\":
  \"qa-josh-notif-inbox.myjosh.in:n1\", \"myjosh.pwa.page.base.url\":
  \"https://qa-share.myjosh.in/\",
  \"myjosh.rich.deeplink.template.for.profile\":
  \"http://www.myjosh.in/profile/{0}\", \"myjosh.security.base.url\":
  \"http://qa-josh-security.myjosh.in\", \"myjosh.share.base.url\":
  \"https://qa-share.myjosh.in\", \"myjosh.strem.base.url\":
  \"https://qa-stream.myjosh.in\",
  \"myjosh.trending.duet.title.deeplink\":
  \"https://qa-share.myjosh.in/challenge/7728e9ee-c1c2-4812-84de-95f97da7b13a\",
  \"myjosh.upload.base.url\": \"https://qa-api.myjosh.in\",
  \"myjosh.video.host.full.url\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/zerosearch/thumbnails/\",
  \"myjosh.video.host.url\": \"https://qa-stream.myjosh.in\",
  \"mysql.jdbc.maxActive\": \"100\", \"mysql.jdbc.maxIdle\": \"10\",
  \"mysql.jdbc.password\": \"Adm!nj0\$#46\", \"mysql.jdbc.url\":
  \"jdbc:mysql://qa-josh-db.cmdiltkwgiys.ap-south-1.rds.amazonaws.com:3306/qa_josh_content_db?useUnicode=true&connectionCollation=utf8_general_ci&characterSetResults=utf8&characterEncoding=utf8\",
  \"mysql.jdbc.username\": \"qa_josh_content_db\",
  \"mysql.jdc.maxWait\": \"10000\",
  \"mysql.jdc.minEvictableIdleTimeMillis\": \"500000\",
  \"mysql.jdc.timeBetweenEvictionRunsMillis\": \"60000\",
  \"new.ads.handshake.from.version\": \"3.0.0\",
  \"obelix.connection.request.timeout\": \"100\",
  \"obelix.fallback.notification.hostname\":
  \"qa-josh-notif-inbox.coolfie.io\",
  \"obelix.notification.topology.refresh.api\":
  \"http://qa-josh-notif-inbox.coolfie.io/api/obelix/topology_v2\",
  \"obelix.topology.cache.async.refresh.millis\": \"21600000\",
  \"obelix.url.connection.timeout\": \"500\",
  \"obelix.url.read.timeout\": \"1000\", \"onboard.base.url\":
  \"https://qa-api.coolfie.io\", \"onboard.es.api.url\":
  \"/apij/entity/gateway/{entityType}/{id}\", \"onboard.java.base.url\":
  \"qa-api.coolfie.io\", \"onboard.service.connection.request.timeout\":
  \"1000\", \"onboard.service.url.connection.timeout\": \"2500\",
  \"onboard.service.url.read.timeout\": \"1500\", \"page.base.url\":
  \"https://qa-feed.coolfie.io\", \"page.size.for.josh.stickers.api\":
  \"50\", \"popular.ab.testing.enabled\": \"true\",
  \"popular.creator.section.depth\": \"200\",
  \"popular.selected.tab.icon.url\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/handshake/selected_popular.png\",
  \"popular.tab.ab.android.min.version\": \"4.4.9\",
  \"popular.tab.ab.ios.min.version\": \"2.5.0\",
  \"popular.tab.icon.url\":
  \"https://qa-stream.myjosh.in/stream/qa-josh-content/handshake/popular.png\",
  \"pull.fallback.notification.path\": \"/api/obelix/fallback/pull\",
  \"pull.notification.hosts.mapping\":
  \"qa-josh-notif-inbox.coolfie.io:n1\", \"pull.notification.path\":
  \"/api/obelix/fallback/pull\", \"pwa.device.request.header.key\":
  \"josh_pwa\", \"pwa.include.discovery.search.from.version.onwards\":
  \"0.0\", \"pwa.page.base.url\": \"https://qa-share.myjosh.in/\",
  \"rateconfig.enabled\": \"true\",
  \"rateconfig.max.number.of.times.to.show.rate.screen\": \"3\",
  \"rateconfig.max.wait.days.for.new.users.to.show.rate.screen\": \"7\",
  \"rateconfig.min.launches.for.new.users.to.show.rate.screen\": \"3\",
  \"rateconfig.min.number.of.app.launches.to.wait.after.last.seen\":
  \"10\", \"rateconfig.min.number.of.books.read\": \"4\",
  \"rateconfig.min.number.of.days.to.wait.showing.rate.screen\": \"30\",
  \"rateconfig.min.number.of.days.user.to.wait.after.last.seen\":
  \"10\", \"rateconfig.min.number.of.stories.viewed.per.session\":
  \"10\", \"rateconfig.pre.activity.session.wait.time.in.seconds\":
  \"600\", \"redis.cluster.clusterView.refresh.enable\": \"false\",
  \"redis.cluster.clusterView.refresh.periodInSeconds\": \"120\",
  \"redis.cluster.enable\": \"true\",
  \"report.connection.request.timeout\": \"100\",
  \"report.feedback.threadpool.size\": \"20\",
  \"report.url.connection.timeout\": \"500\",
  \"report.url.read.timeout\": \"1000\",
  \"request.headers.logging.enabled.apis\": \"/josh/handshake\",
  \"resumable.upload.result.url\": \"/content/create-v2\",
  \"resumable.upload.service.url\": \"/content/upload-v2\",
  \"reward.signature.refresh.time\": \"1800\",
  \"rich.deeplink.template.for.profile\":
  \"http://www.coolfie.io/profile/{0}\", \"s3.bucket\":
  \"qa-josh-content\", \"s3.bucket.gateway\": \"josh-gateway\",
  \"scheduler.cache.stats.reader.enable\": \"true\",
  \"scheduler.tomcat.access.log.reader.enable\": \"true\",
  \"security.base.url\": \"http://qa-josh-security.myjosh.in\",
  \"server.port\": \"8080\", \"share.base.url\":
  \"https://qa-share.myjosh.in\", \"skip.nlfc.for.session.on.failure\":
  \"3\", \"speed.quality.config.android\":
  \"{\\\"200\\\":\\\"slow\\\",\\\"2000\\\":\\\"average\\\",\\\"6000\\\":\\\"good\\\",\\\"8000\\\":\\\"fast\\\",\\\"16000\\\":\\\"veryfast\\\"}\",
  \"sticker.es.upload.enabled\": \"true\", \"sticker.tab.filters\":
  \"SINGLE_FILTER\", \"sticker.tab.list.endpoint\":
  \"/api/v1/stickers/list?tabId={0}&version={1}\",
  \"sticker.tabs.config.url.template\":
  \"/api/v1/stickers/tabs?version={0}\", \"stream.api.endpoint\":
  \"stream\", \"stream.host.coolfie\": \"stream.coolfie.io\",
  \"stream.host.myjosh\": \"stream.myjosh.in\", \"strem.base.url\":
  \"https://qa-stream.coolfie.io\", \"sync.fallback.notification.path\":
  \"/api/obelix/fallback/sync\", \"sync.notification.path\":
  \"/api/obelix/fallback/sync\",
  \"tomcat.access.log.max.entries.inmemory\": \"10000\",
  \"tomcat.access.log.reader.util.allowed.status.codes\": \"200\",
  \"trending.duet.meta.content.url\": \"/content/batch-get\",
  \"trending.duet.title.deeplink\":
  \"https://qa-share.myjosh.in/challenge/7728e9ee-c1c2-4812-84de-95f97da7b13a\",
  \"upload.base.url\": \"https://qa-api.coolfie.io\",
  \"upload.format.list\": \"3gp,mp4\",
  \"upload.threshold.for.s3.bucket.in.bytes\": \"5248000\",
  \"url.connection.timeout\": \"2000\", \"url.read.timeout\": \"2000\",
  \"user.cookie.redis.config.hosts\":
  \"redis-10001.josh-aws-qa-redislabs-cluster.myjosh.in:10001\",
  \"user.cookie.redis.config.password\": \"gkyPX9AssET2EDzd\",
  \"user.cookie.redis.key.template\": \"cookie\_%s\",
  \"user.cookie.redis.key.ttl\": \"86400000\",
  \"user.headlines.expire.seconds\": \"900\",
  \"user.report.service.content.url\": \"/user/report\",
  \"user.segments.enabled\": \"true\",
  \"user.segments.included.characters\": \"a,b,c,d\",
  \"version-info.cache.async.refresh.millis\": \"300000\",
  \"version.check.handshake.disabled\": \"true\",
  \"version.info.db.enabled\": \"true\",
  \"version.info.file.upload.folder\": \"josh_version_content/\",
  \"version.info.s3.file.location\": \"version_info/\",
  \"video.host.full.url\":
  \"https://qa-stream.coolfie.io/stream/qa-josh-content/zerosearch/thumbnails/\",
  \"video.host.url\": \"https://qa-stream.coolfie.io\",
  \"video.material.cover.url.format\":
  \"{0}/{1}/{2}/{3}/cover/{4}/{5}\",
  \"video.material.cover.url2.format\":
  \"{0}/{1}/{2}/{3}/cover2/{4}/{5}\",
  \"video.material.default.sdk.type\": \"JOSH_CAM1\",
  \"video.material.license.format\":
  \"{0}/{1}/{2}/{3}/license/{4}/{5}\",
  \"video.material.mask.name.not.supported.till.app.version\":
  \"4.7.0\", \"video.material.package.url.format\":
  \"{0}/{1}/{2}/{3}/{4}/{5}\", \"video.material.s3.bucket\":
  \"qa-josh-content\", \"video.material.s3.common.location\":
  \"material\", \"video.material.sdk.android.license.file.location\":
  \"{0}/{1}/{2}/joshCam1Config/license/android/7913-269-e6000bb2f7f211a6b8f36cf3c3b83f17.lic\",
  \"video.material.sdk.ios.license.file.location\":
  \"{0}/{1}/{2}/joshCam1Config/license/ios/7913-269-8b75008cd2aeca3f426fceed537c5e78.lic\",
  \"video.material.sdk.license.file.location\":
  \"{0}/{1}/{2}/joshCam1Config/license/meisheLicense_20201103.lic\",
  \"whitelisted.client.ids\": \"9dad880a-7a75\",
  \"write.cookie.to.redis.for.domain\": \"coolfie.io\",
  \"zero.search.separate.version.update\": \"true\",
  \"zerosearch.thumbnail.folder\": \"zerosearch/thumbnails/\" }, \"db\":
  { \"aws.sns.subscription.request\": \"{\\n \\\"Type\\\" :
  \\\"SubscriptionConfirmation\\\",\\n \\\"MessageId\\\" :
  \\\"e17cc09d-4228-4fe0-8a0f-4971430b03c5\\\",\\n \\\"Token\\\" :
  \\\"2336412f37fb687f5d51e6e2425e90ccf7a37c8a51dea832e0a72af7494085696616ff8316b7b87fe09915c022f01b6e4b33e0e80ff4d7cd781de3650cb62e4dd874eddcea4c9e9473c376a955455419426757be3084f295b6384563a9e3ce520599fe8d45aeb1a5b959d2fc7068ef9e73fee1d883b6763ff9eef0b69389998b\\\",\\n
  \\\"TopicArn\\\" :
  \\\"arn:aws:sns:ap-south-1:514352861371:Gateway-For-Cache-Sync\\\",\\n
  \\\"Message\\\" : \\\"You have chosen to subscribe to the topic
  arn:aws:sns:ap-south-1:514352861371:Gateway-For-Cache-Sync.\\nTo
  confirm the subscription, visit the SubscribeURL included in this
  message.\\\",\\n \\\"SubscribeURL\\\" :
  \\\"https://sns.ap-south-1.amazonaws.com/?Action=ConfirmSubscription&TopicArn=arn:aws:sns:ap-south-1:514352861371:Gateway-For-Cache-Sync&Token=2336412f37fb687f5d51e6e2425e90ccf7a37c8a51dea832e0a72af7494085696616ff8316b7b87fe09915c022f01b6e4b33e0e80ff4d7cd781de3650cb62e4dd874eddcea4c9e9473c376a955455419426757be3084f295b6384563a9e3ce520599fe8d45aeb1a5b959d2fc7068ef9e73fee1d883b6763ff9eef0b69389998b\\\",\\n
  \\\"Timestamp\\\" : \\\"2021-06-18T10:42:58.850Z\\\",\\n
  \\\"SignatureVersion\\\" : \\\"1\\\",\\n \\\"Signature\\\" :
  \\\"TCNcOCOxanHq8BwZTTzkQ/N4kBWHS0oyi2U7ZVZf7ZM73qhgn/ActvN96ygowqMJ4VFknb7q89O1VHgzsGF5TeQgxnNZ0T2IwpJiIriZ56pykxbWTZRP9DUhTPBc3hMn0+gAHuUvM4Bz1SUMZMgx+3k3+XqcMm8mdMYDcVVMVtLhutvQk1CpybTpLwuKD/wYMNdCHGi2SBWl2O3Vi8oXLPdyilA2PibVQHFqI0rSTNkJOGT3DjBSeSU4+BHW0BbqJpwxj01mD0sBJ0rETs3aFyk9wbDAo1Gl+RC6nxtLvlroNj6p8dXQBBEtHALp2Row6wJICw1HkeiCtUFVwk+kfQ==\\\",\\n
  \\\"SigningCertURL\\\" :
  \\\"https://sns.ap-south-1.amazonaws.com/SimpleNotificationService-010a507c1833636cd94bdb98bd93083a.pem\\\"\\n}\",
  \"aws.sns.subscription.response\":
  \"{\\\"ConfirmSubscriptionResponse\\\":{\\\"ConfirmSubscriptionResult\\\":{\\\"SubscriptionArn\\\":\\\"arn:aws:sns:ap-south-1:514352861371:Gateway-For-Cache-Sync:790a35c4-ed6f-4dd6-9f0f-59ed414e97db\\\"},\\\"ResponseMetadata\\\":{\\\"RequestId\\\":\\\"2a35b662-1c21-5071-8193-ef2466d33983\\\"}}}\",
  \"default.font\":
  \"{\\\"id\\\":\\\"0\\\",\\\"font_name\\\":\\\"\\\",\\\"url\\\":\\\"\\\",\\\"thumbnail_url\\\":\\\"https://qa-stream.coolfie.io/stream/qa-josh-content/josh_fonts/font-thumbnails/default.png\\\",\\\"mime_type\\\":\\\"ttf\\\",\\\"width\\\":53,\\\"height\\\":50,\\\"is_bold_style_supported\\\":true,\\\"auto_download\\\":false}\",
  \"default.tab.id.for.josh.stickers\": \"25\",
  \"discovery.trends.tab.version.ios\": \"4.0.0\", \"ec2.instances\":
  \"{\\\"i-01772c63718d89726\\\":\\\"10.12.1.83\\\"}\",
  \"handshake.base.urls.config\":
  \"{\\\"delete_account_url\\\":\\\"https://qa-share.myjosh.in/deleteAccount\\\",\\\"apply_for_verification_url\\\":\\\"https://qa-share.myjosh.in/webview/apply-verification\\\",\\\"profile_insights_url\\\":\\\"https://qa-share.myjosh.in/analytics/profile-insight/\\\",\\\"content_insights_url\\\":\\\"https://qa-share.myjosh.in/analytics/content-insight/\\\",\\\"sso_url\\\":\\\"https://qa-api.coolfie.io\\\",\\\"interest_list_url\\\":\\\"https://qa-feed.coolfie.io/feed/interestlist?version=1\\\",\\\"experiment_url\\\":\\\"http://76.223.34.165/api/run\\\",\\\"application_url_v2\\\":\\\"https://qa-api.coolfie.io/apij\\\",\\\"image_share_url\\\":\\\"https://qa-api.myjosh.in/image/\\\",\\\"social_share_url\\\":\\\"https://qa-api.myjosh.in/social/\\\",\\\"template_list_url\\\":\\\"https://qa-api.myjosh.in/apij/template/list?page=0&size=5\\\",\\\"template_search_url\\\":\\\"https://qa-feed.myjosh.in/TEMPLATE/search?page=0&size=10\\\",\\\"cold_start_url\\\":\\\"https://qa-feed.myjosh.in/v2/feed/coldstart\\\"}\",
  \"local.cache.ab.testing.enabled\": \"false\", \"mrinal\": \"dutta\",
  \"myjosh.default.font\":
  \"{\\\"id\\\":\\\"0\\\",\\\"font_name\\\":\\\"\\\",\\\"url\\\":\\\"\\\",\\\"thumbnail_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/josh_fonts/font-thumbnails/default.png\\\",\\\"mime_type\\\":\\\"ttf\\\",\\\"width\\\":53,\\\"height\\\":50,\\\"is_bold_style_supported\\\":true,\\\"auto_download\\\":false}\",
  \"myjosh.handshake.base.urls.config\":
  \"{\\\"delete_account_url\\\":\\\"https://qa-share.myjosh.in/deleteAccount\\\",\\\"apply_for_verification_url\\\":\\\"https://qa-share.myjosh.in/webview/apply-verification\\\",\\\"profile_insights_url\\\":\\\"https://qa-share.myjosh.in/analytics/profile-insight/\\\",\\\"content_insights_url\\\":\\\"https://qa-share.myjosh.in/analytics/content-insight/\\\",\\\"sso_url\\\":\\\"https://qa-api.myjosh.in\\\",\\\"interest_list_url\\\":\\\"https://qa-feed.myjosh.in/feed/interestlist?version=1\\\",\\\"experiment_url\\\":\\\"http://76.223.34.165/api/run\\\",\\\"application_url_v2\\\":\\\"https://qa-api.myjosh.in/apij\\\",\\\"image_share_url\\\":\\\"https://qa-api.myjosh.in/image/\\\",\\\"social_share_url\\\":\\\"https://qa-api.myjosh.in/social/\\\",\\\"template_list_url\\\":\\\"https://qa-api.myjosh.in/apij/template/list?page=0&size=10\\\",\\\"template_search_url\\\":\\\"https://qa-feed.myjosh.in/TEMPLATE/search?page=0&size=10\\\",\\\"cold_start_url\\\":\\\"https://qa-feed.myjosh.in/v2/feed/coldstart\\\"}\",
  \"page.audio.default\": \"main-audio-page\",
  \"page.discovery.default\": \"main-discovery-page\",
  \"speed.quality.config.android\":
  \"{\\\"200\\\":\\\"slow\\\",\\\"2000\\\":\\\"average\\\",\\\"6000\\\":\\\"good\\\",\\\"8000\\\":\\\"fast\\\",\\\"16000\\\":\\\"veryfast\\\"}\",
  \"tesing utf16\": \"കേരളപ്പിറവി\",
  \"user.segments.included.characters\": \"a,b,c,d\", \"utkarsh\":
  \"seth\", \"whitelisted.client.ids\": \"9dad880a-7a75,6b25a0a6-e213\",
  \"കേരളപ്പിറവി\": \"testing utf8\" } }, \"jenkinsBuildNumber\": \"1\",
  \"rotation\": \"IN\" } }

- **Request Method and URL:**

  GET : https://qa-gateway.coolfie.io/api/v1/health

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/health\' \\

  \--header \'Content-Type: application/json\' \\

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 } }

- **Request Method and URL:**

  POST :
  https://qa-gateway.coolfie.io/api/v1/report/content/some-action?abusedId=1&clientId=10000&contentUuid=dvubsk

- **Curl Request:**

  curl \--location \--request POST
  \'https://qa-gateway.coolfie.io/api/v1/report/content/some-action?abusedId=1&clientId=10000&contentUuid=dvubsk\'
  \\

  \--header \'Content-Type: application/json\' \\

  \--data-raw \'{

  \"name\": \"name\",

  \"itemId\": \"itemId\",

  \"reportId\": \"reportId\",

  \"comment\": \"Nothing is there to do. hello noobs. adding \@ailab to
  add sns\",

  \"createdAt\": 1615814533,

  \"reportType\": \"reportType\",

  \"email\": \"email@gmail.com\",

  \"mobile\": \"911\",

  \"option\": \"option\"

  }\'

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.12.1.83\", \"code\": 200 }, \"data\": { } }

- **Request Method and URL:**

  GET : https://qa-gateway.coolfie.io/api/v1/es/effects

- **Curl Request:**

  curl \--location \--request GET
  \'https://qa-gateway.coolfie.io/api/v1/es/effects\' \\

- **Success Response:**

  { \"code\": 200, \"data\":
  \"\\n{\\\"index\\\":{\\\"\_id\\\":\\\"163DE520-95FC-4CF3-B847-C43F1D474587\\\"}}\\n{\\\"id\\\":\\\"163DE520-95FC-4CF3-B847-C43F1D474587\\\",\\\"category\\\":0,\\\"name\\\":\\\"Vintage\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/163DE520-95FC-4CF3-B847-C43F1D474587.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/163DE520-95FC-4CF3-B847-C43F1D474587.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":160,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"18C6DAA7-0776-4D72-AB6D-8C195FA17617\\\"}}\\n{\\\"id\\\":\\\"18C6DAA7-0776-4D72-AB6D-8C195FA17617\\\",\\\"category\\\":0,\\\"name\\\":\\\"Moody\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/18C6DAA7-0776-4D72-AB6D-8C195FA17617.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/18C6DAA7-0776-4D72-AB6D-8C195FA17617.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":210,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"2215EC1E-A9EE-4B5C-89CB-BF488178C910\\\"}}\\n{\\\"id\\\":\\\"2215EC1E-A9EE-4B5C-89CB-BF488178C910\\\",\\\"category\\\":0,\\\"name\\\":\\\"Aesth\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/2215EC1E-A9EE-4B5C-89CB-BF488178C910.2.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/2215EC1E-A9EE-4B5C-89CB-BF488178C910.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":20,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"3C1C1944-117F-4D4C-8432-22D165CB27BC\\\"}}\\n{\\\"id\\\":\\\"3C1C1944-117F-4D4C-8432-22D165CB27BC\\\",\\\"category\\\":0,\\\"name\\\":\\\"Classic\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/3C1C1944-117F-4D4C-8432-22D165CB27BC.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/3C1C1944-117F-4D4C-8432-22D165CB27BC.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":230,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"4EFE3455-C58D-499C-B311-D445F752D567\\\"}}\\n{\\\"id\\\":\\\"4EFE3455-C58D-499C-B311-D445F752D567\\\",\\\"category\\\":0,\\\"name\\\":\\\"Caffeine\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/4EFE3455-C58D-499C-B311-D445F752D567.3.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/4EFE3455-C58D-499C-B311-D445F752D567.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":130,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"553463AB-6F40-4CAF-B0D8-DB3AD3AA6B24\\\"}}\\n{\\\"id\\\":\\\"553463AB-6F40-4CAF-B0D8-DB3AD3AA6B24\\\",\\\"category\\\":1,\\\"name\\\":\\\"Swiss\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":2,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/553463AB-6F40-4CAF-B0D8-DB3AD3AA6B24.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/553463AB-6F40-4CAF-B0D8-DB3AD3AA6B24.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":60,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"61B3A8B9-C843-450D-AB93-56FF082FF120\\\"}}\\n{\\\"id\\\":\\\"61B3A8B9-C843-450D-AB93-56FF082FF120\\\",\\\"category\\\":0,\\\"name\\\":\\\"Warm\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/61B3A8B9-C843-450D-AB93-56FF082FF120.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/61B3A8B9-C843-450D-AB93-56FF082FF120.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":30,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"6BDB176F-D105-49A7-98D2-3A0D98103F2C\\\"}}\\n{\\\"id\\\":\\\"6BDB176F-D105-49A7-98D2-3A0D98103F2C\\\",\\\"category\\\":0,\\\"name\\\":\\\"Mocktail\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/6BDB176F-D105-49A7-98D2-3A0D98103F2C.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/6BDB176F-D105-49A7-98D2-3A0D98103F2C.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":120,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"is_archived\\\":false,\\\"has_sound\\\":false,\\\"not_show_in_thumbnail\\\":false,\\\"valid_till\\\":1626251114365,\\\"label\\\":\\\"New\\\",\\\"category_name\\\":\\\"\\\",\\\"show_animation\\\":false,\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"73844D15-405B-4B3F-AC71-403B7E069166\\\"}}\\n{\\\"id\\\":\\\"73844D15-405B-4B3F-AC71-403B7E069166\\\",\\\"category\\\":1,\\\"name\\\":\\\"Retro\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":2,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/73844D15-405B-4B3F-AC71-403B7E069166.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/73844D15-405B-4B3F-AC71-403B7E069166.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":180,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"7D8A1839-B7D3-4C91-AD7A-8FB920322818\\\"}}\\n{\\\"id\\\":\\\"7D8A1839-B7D3-4C91-AD7A-8FB920322818\\\",\\\"category\\\":0,\\\"name\\\":\\\"Vanilla\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/7D8A1839-B7D3-4C91-AD7A-8FB920322818.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/7D8A1839-B7D3-4C91-AD7A-8FB920322818.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":150,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"C8C90F0B-2120-4D1A-A538-F59BA39D8F52\\\"}}\\n{\\\"id\\\":\\\"C8C90F0B-2120-4D1A-A538-F59BA39D8F52\\\",\\\"category\\\":0,\\\"name\\\":\\\"Smile\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/C8C90F0B-2120-4D1A-A538-F59BA39D8F52.2.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/C8C90F0B-2120-4D1A-A538-F59BA39D8F52.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":50,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"valid_till\\\":1626337464086,\\\"label\\\":\\\"New\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"D1AC10BD-39F9-407D-8277-895E52066392\\\"}}\\n{\\\"id\\\":\\\"D1AC10BD-39F9-407D-8277-895E52066392\\\",\\\"category\\\":0,\\\"name\\\":\\\"Bahamas\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/D1AC10BD-39F9-407D-8277-895E52066392.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/D1AC10BD-39F9-407D-8277-895E52066392.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":90,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"label\\\":\\\"New\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"D4C889D0-423A-4A3D-A141-7BA74063AE35\\\"}}\\n{\\\"id\\\":\\\"D4C889D0-423A-4A3D-A141-7BA74063AE35\\\",\\\"category\\\":0,\\\"name\\\":\\\"Poser\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/D4C889D0-423A-4A3D-A141-7BA74063AE35.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/D4C889D0-423A-4A3D-A141-7BA74063AE35.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":240,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"D50DC3F9-1995-4B08-8D75-88DEBDC33E28\\\"}}\\n{\\\"id\\\":\\\"D50DC3F9-1995-4B08-8D75-88DEBDC33E28\\\",\\\"category\\\":0,\\\"name\\\":\\\"Bleak\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/D50DC3F9-1995-4B08-8D75-88DEBDC33E28.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/D50DC3F9-1995-4B08-8D75-88DEBDC33E28.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":190,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"D9226363-B1E4-4144-880A-EDAB6ED2E654\\\"}}\\n{\\\"id\\\":\\\"D9226363-B1E4-4144-880A-EDAB6ED2E654\\\",\\\"category\\\":2,\\\"name\\\":\\\"Alpine\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":2,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/D9226363-B1E4-4144-880A-EDAB6ED2E654.2.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/D9226363-B1E4-4144-880A-EDAB6ED2E654.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":100,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"DA06CB37-BD38-454A-B868-34B8ABC4BECC\\\"}}\\n{\\\"id\\\":\\\"DA06CB37-BD38-454A-B868-34B8ABC4BECC\\\",\\\"category\\\":0,\\\"name\\\":\\\"Punch\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/DA06CB37-BD38-454A-B868-34B8ABC4BECC.2.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/DA06CB37-BD38-454A-B868-34B8ABC4BECC.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":250,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"DE535DD7-91A3-4AC2-89DE-2BA94C32BFB2\\\"}}\\n{\\\"id\\\":\\\"DE535DD7-91A3-4AC2-89DE-2BA94C32BFB2\\\",\\\"category\\\":0,\\\"name\\\":\\\"Moscow\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/DE535DD7-91A3-4AC2-89DE-2BA94C32BFB2.8.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/DE535DD7-91A3-4AC2-89DE-2BA94C32BFB2.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":80,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"E25437B0-80F8-4515-91E0-1AB7D087D438\\\"}}\\n{\\\"id\\\":\\\"E25437B0-80F8-4515-91E0-1AB7D087D438\\\",\\\"category\\\":0,\\\"name\\\":\\\"Rio\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/E25437B0-80F8-4515-91E0-1AB7D087D438.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/E25437B0-80F8-4515-91E0-1AB7D087D438.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":110,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"F4071666-225C-4ACE-B0E5-60C9F7E940F1\\\"}}\\n{\\\"id\\\":\\\"F4071666-225C-4ACE-B0E5-60C9F7E940F1\\\",\\\"category\\\":0,\\\"name\\\":\\\"Sepia\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/F4071666-225C-4ACE-B0E5-60C9F7E940F1.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/F4071666-225C-4ACE-B0E5-60C9F7E940F1.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":170,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"FAE50247-F14C-40CE-AD43-29CA3E604838\\\"}}\\n{\\\"id\\\":\\\"FAE50247-F14C-40CE-AD43-29CA3E604838\\\",\\\"category\\\":0,\\\"name\\\":\\\"Citrus\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/FAE50247-F14C-40CE-AD43-29CA3E604838.3.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/FAE50247-F14C-40CE-AD43-29CA3E604838.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":140,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"amritsar\\\"}}\\n{\\\"id\\\":\\\"amritsar\\\",\\\"category\\\":0,\\\"name\\\":\\\"amritsar\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/amritsar.videofx\\\",\\\"package_size\\\":0,\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":350,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"mathura\\\"}}\\n{\\\"id\\\":\\\"mathura\\\",\\\"category\\\":0,\\\"name\\\":\\\"mathura\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/mathura.videofx\\\",\\\"package_size\\\":0,\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":351,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"vrindavan\\\"}}\\n{\\\"id\\\":\\\"vrindavan\\\",\\\"category\\\":0,\\\"name\\\":\\\"vrindavan\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/vrindavan.videofx\\\",\\\"package_size\\\":0,\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":352,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"varanasi\\\"}}\\n{\\\"id\\\":\\\"varanasi\\\",\\\"category\\\":0,\\\"name\\\":\\\"varanasi\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/varanasi.videofx\\\",\\\"package_size\\\":0,\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":353,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"barsana\\\"}}\\n{\\\"id\\\":\\\"barsana\\\",\\\"category\\\":0,\\\"name\\\":\\\"barsana\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/barsana.videofx\\\",\\\"package_size\\\":0,\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":354,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"baldeo\\\"}}\\n{\\\"id\\\":\\\"baldeo\\\",\\\"category\\\":0,\\\"name\\\":\\\"baldeo\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/baldeo.videofx\\\",\\\"package_size\\\":0,\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":355,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"jaipur\\\"}}\\n{\\\"id\\\":\\\"jaipur\\\",\\\"category\\\":0,\\\"name\\\":\\\"jaipur\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/jaipur.videofx\\\",\\\"package_size\\\":0,\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":356,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"udaipur\\\"}}\\n{\\\"id\\\":\\\"udaipur\\\",\\\"category\\\":0,\\\"name\\\":\\\"udaipur\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/udaipur.videofx\\\",\\\"package_size\\\":0,\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":357,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"pushkar\\\"}}\\n{\\\"id\\\":\\\"pushkar\\\",\\\"category\\\":0,\\\"name\\\":\\\"pushkar\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/pushkar.videofx\\\",\\\"package_size\\\":0,\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":358,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"anandapur_sahib\\\"}}\\n{\\\"id\\\":\\\"anandapur_sahib\\\",\\\"category\\\":0,\\\"name\\\":\\\"anandapur_sahib\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/anandapur_sahib.videofx\\\",\\\"package_size\\\":0,\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":359,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"shahpura_bagh\\\"}}\\n{\\\"id\\\":\\\"shahpura_bagh\\\",\\\"category\\\":0,\\\"name\\\":\\\"shahpura_bagh\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/shahpura_bagh.videofx\\\",\\\"package_size\\\":0,\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":360,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"ramathra_fort\\\"}}\\n{\\\"id\\\":\\\"ramathra_fort\\\",\\\"category\\\":0,\\\"name\\\":\\\"ramathra_fort\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/ramathra_fort.videofx\\\",\\\"package_size\\\":0,\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":361,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"ce551302-7216-11ec-873b-4b6e5aaa9440\\\"}}\\n{\\\"id\\\":\\\"ce551302-7216-11ec-873b-4b6e5aaa9440\\\",\\\"category\\\":0,\\\"name\\\":\\\"Dummy\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/ce551302-7216-11ec-873b-4b6e5aaa9440.2.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/ce551302-7216-11ec-873b-4b6e5aaa9440.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":324,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"label\\\":\\\"Dummy\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"ce551302-7216-11ec-873b-4b6e5aaa9440\\\"}}\\n{\\\"id\\\":\\\"ce551302-7216-11ec-873b-4b6e5aaa9440\\\",\\\"category\\\":0,\\\"name\\\":\\\"Dummy
  Filter\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/ce551302-7216-11ec-873b-4b6e5aaa9440.2.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/ce551302-7216-11ec-873b-4b6e5aaa9440.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":2445,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"label\\\":\\\"dummy\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"4562EDA7-26D9-4179-8E5B-D24B041FC789\\\"}}\\n{\\\"id\\\":\\\"4562EDA7-26D9-4179-8E5B-D24B041FC789\\\",\\\"category\\\":0,\\\"name\\\":\\\"Pongal\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/4562EDA7-26D9-4179-8E5B-D24B041FC789.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/Pongal.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":21421,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"label\\\":\\\"pongal\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"A8ABB71-3ED4-4339-9052-25B9D35E4ADA\\\"}}\\n{\\\"id\\\":\\\"A8ABB71-3ED4-4339-9052-25B9D35E4ADA\\\",\\\"category\\\":0,\\\"name\\\":\\\"TestQA1\\\",\\\"desc\\\":\\\"TestQA1\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/A8ABB71-3ED4-4339-9052-25B9D35E4ADA.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/F4071666-225C-4ACE-B0E5-60C9F7E940F1.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":10001,\\\"filter_type\\\":\\\"SIMPLE_FILTER\\\",\\\"asset_type\\\":\\\"FILTER\\\",\\\"label\\\":\\\"TestQA1\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"11DD8ED9-880F-4017-B973-6A6B708129F7\\\"}}\\n{\\\"id\\\":\\\"11DD8ED9-880F-4017-B973-6A6B708129F7\\\",\\\"category\\\":0,\\\"name\\\":\\\"Daylight\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/11DD8ED9-880F-4017-B973-6A6B708129F7.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/11DD8ED9-880F-4017-B973-6A6B708129F7.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":270,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"1AACCE79-7EAB-4B2E-AE9B-E53A02AFC055\\\"}}\\n{\\\"id\\\":\\\"1AACCE79-7EAB-4B2E-AE9B-E53A02AFC055\\\",\\\"category\\\":0,\\\"name\\\":\\\"Petal
  Shower\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/1AACCE79-7EAB-4B2E-AE9B-E53A02AFC055.3.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/1AACCE79-7EAB-4B2E-AE9B-E53A02AFC055.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":130,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"259D1CBF-2A20-4A2C-AFDD-185B05B0B07D\\\"}}\\n{\\\"id\\\":\\\"259D1CBF-2A20-4A2C-AFDD-185B05B0B07D\\\",\\\"category\\\":0,\\\"name\\\":\\\"Retro
  TV\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/259D1CBF-2A20-4A2C-AFDD-185B05B0B07D.2.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/259D1CBF-2A20-4A2C-AFDD-185B05B0B07D.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":170,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"35716E29-D415-442E-9837-B4202EA6A465\\\"}}\\n{\\\"id\\\":\\\"35716E29-D415-442E-9837-B4202EA6A465\\\",\\\"category\\\":1,\\\"name\\\":\\\"Glitterfall\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":2,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/35716E29-D415-442E-9837-B4202EA6A465.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/35716E29-D415-442E-9837-B4202EA6A465.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":210,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"35B954E1-8D38-40BC-A567-F6DA1D557950\\\"}}\\n{\\\"id\\\":\\\"35B954E1-8D38-40BC-A567-F6DA1D557950\\\",\\\"category\\\":0,\\\"name\\\":\\\"RGB
  Glitch\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/35B954E1-8D38-40BC-A567-F6DA1D557950.2.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/35B954E1-8D38-40BC-A567-F6DA1D557950.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":180,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"381869EE-F40D-4F4D-A641-ED2B59DD18AE\\\"}}\\n{\\\"id\\\":\\\"381869EE-F40D-4F4D-A641-ED2B59DD18AE\\\",\\\"category\\\":0,\\\"name\\\":\\\"Dreamy\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/381869EE-F40D-4F4D-A641-ED2B59DD18AE.3.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/381869EE-F40D-4F4D-A641-ED2B59DD18AE.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":190,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"3B145FE8-E780-403F-A7B2-A061CB56243F\\\"}}\\n{\\\"id\\\":\\\"3B145FE8-E780-403F-A7B2-A061CB56243F\\\",\\\"category\\\":0,\\\"name\\\":\\\"Bubbles\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/3B145FE8-E780-403F-A7B2-A061CB56243F.3.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/3B145FE8-E780-403F-A7B2-A061CB56243F.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":140,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"548F5513-648C-4FDD-8025-BDB006C86803\\\"}}\\n{\\\"id\\\":\\\"548F5513-648C-4FDD-8025-BDB006C86803\\\",\\\"category\\\":0,\\\"name\\\":\\\"3
  Grid\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/548F5513-648C-4FDD-8025-BDB006C86803.2.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/548F5513-648C-4FDD-8025-BDB006C86803.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":330,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"617B0867-099D-417A-985C-59C6EE7B75ED\\\"}}\\n{\\\"id\\\":\\\"617B0867-099D-417A-985C-59C6EE7B75ED\\\",\\\"category\\\":2,\\\"name\\\":\\\"6
  Grid\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":2,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/617B0867-099D-417A-985C-59C6EE7B75ED.2.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/617B0867-099D-417A-985C-59C6EE7B75ED.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":300,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"7625B430-0E06-446C-A558-A18F33FA4FCE\\\"}}\\n{\\\"id\\\":\\\"7625B430-0E06-446C-A558-A18F33FA4FCE\\\",\\\"category\\\":0,\\\"name\\\":\\\"Energy
  Swirl\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/7625B430-0E06-446C-A558-A18F33FA4FCE.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/7625B430-0E06-446C-A558-A18F33FA4FCE.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":110,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"is_archived\\\":false,\\\"has_sound\\\":false,\\\"alias\\\":\\\"\\\",\\\"not_show_in_thumbnail\\\":false,\\\"sdk_type\\\":\\\"\\\",\\\"valid_till\\\":0,\\\"label\\\":\\\"\\\",\\\"category_name\\\":\\\"\\\",\\\"show_animation\\\":false,\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"7FFCF99A-5336-4464-BACD-9D32D5D2DC5E\\\"}}\\n{\\\"id\\\":\\\"7FFCF99A-5336-4464-BACD-9D32D5D2DC5E\\\",\\\"category\\\":0,\\\"name\\\":\\\"Star
  Fall\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/7FFCF99A-5336-4464-BACD-9D32D5D2DC5E.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/7FFCF99A-5336-4464-BACD-9D32D5D2DC5E.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":120,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"895EFE2F-C116-4DBE-A244-67C6C26DC864\\\"}}\\n{\\\"id\\\":\\\"895EFE2F-C116-4DBE-A244-67C6C26DC864\\\",\\\"category\\\":0,\\\"name\\\":\\\"4
  Grid\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/895EFE2F-C116-4DBE-A244-67C6C26DC864.3.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/895EFE2F-C116-4DBE-A244-67C6C26DC864.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":320,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"8B952A30-CD2F-4E77-ABED-EC1DDF4AA67E\\\"}}\\n{\\\"id\\\":\\\"8B952A30-CD2F-4E77-ABED-EC1DDF4AA67E\\\",\\\"category\\\":2,\\\"name\\\":\\\"Film
  Reel\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":2,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/8B952A30-CD2F-4E77-ABED-EC1DDF4AA67E.2.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/8B952A30-CD2F-4E77-ABED-EC1DDF4AA67E.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":240,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"914AECF6-D404-4EC9-8C80-4B463BA4E33C\\\"}}\\n{\\\"id\\\":\\\"914AECF6-D404-4EC9-8C80-4B463BA4E33C\\\",\\\"category\\\":0,\\\"name\\\":\\\"Golden
  Shower\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/914AECF6-D404-4EC9-8C80-4B463BA4E33C.2.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/914AECF6-D404-4EC9-8C80-4B463BA4E33C.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":220,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"A298F02A-1E80-96BE-20F0-6ED3831D9CFE\\\"}}\\n{\\\"id\\\":\\\"A298F02A-1E80-96BE-20F0-6ED3831D9CFE\\\",\\\"category\\\":0,\\\"name\\\":\\\"VHS\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/A298F02A-1E80-96BE-20F0-6ED3831D9CFE.2.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/A298F02A-1E80-96BE-20F0-6ED3831D9CFE.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":260,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"A8A4344D-45DA-460F-A18F-C0E2355FE864\\\"}}\\n{\\\"id\\\":\\\"A8A4344D-45DA-460F-A18F-C0E2355FE864\\\",\\\"category\\\":0,\\\"name\\\":\\\"Glitch
  Zoom\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/A8A4344D-45DA-460F-A18F-C0E2355FE864.5.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/A8A4344D-45DA-460F-A18F-C0E2355FE864.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":70,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"valid_till\\\":1626251216784,\\\"label\\\":\\\"Hot\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"ABAAD551-6E94-4F1C-B8D1-12209BEBBB6D\\\"}}\\n{\\\"id\\\":\\\"ABAAD551-6E94-4F1C-B8D1-12209BEBBB6D\\\",\\\"category\\\":0,\\\"name\\\":\\\"Disco
  Lights\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/ABAAD551-6E94-4F1C-B8D1-12209BEBBB6D.2.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/ABAAD551-6E94-4F1C-B8D1-12209BEBBB6D.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":150,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"valid_till\\\":1630389339807,\\\"label\\\":\\\"new\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"B3B3FDE1-727F-4C41-A506-3F095FF9C5D3\\\"}}\\n{\\\"id\\\":\\\"B3B3FDE1-727F-4C41-A506-3F095FF9C5D3\\\",\\\"category\\\":0,\\\"name\\\":\\\"Dizzy\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/B3B3FDE1-727F-4C41-A506-3F095FF9C5D3.2.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/B3B3FDE1-727F-4C41-A506-3F095FF9C5D3.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":20,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"label\\\":\\\"new\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"B69DAD3B-8113-4E92-8BFD-12EF0D8AED20\\\"}}\\n{\\\"id\\\":\\\"B69DAD3B-8113-4E92-8BFD-12EF0D8AED20\\\",\\\"category\\\":2,\\\"name\\\":\\\"Camera
  Focus\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":2,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/B69DAD3B-8113-4E92-8BFD-12EF0D8AED20.2.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/B69DAD3B-8113-4E92-8BFD-12EF0D8AED20.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":340,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"B8D91810-03C7-4100-BEC6-3B832C0A3D01\\\"}}\\n{\\\"id\\\":\\\"B8D91810-03C7-4100-BEC6-3B832C0A3D01\\\",\\\"category\\\":0,\\\"name\\\":\\\"2
  Grid\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/B8D91810-03C7-4100-BEC6-3B832C0A3D01.2.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/B8D91810-03C7-4100-BEC6-3B832C0A3D01.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":310,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"BCD1FAAD-D5C5-468F-A4F2-1C2138F485C0\\\"}}\\n{\\\"id\\\":\\\"BCD1FAAD-D5C5-468F-A4F2-1C2138F485C0\\\",\\\"category\\\":0,\\\"name\\\":\\\"Color
  Seperation\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/BCD1FAAD-D5C5-468F-A4F2-1C2138F485C0.3.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/BCD1FAAD-D5C5-468F-A4F2-1C2138F485C0.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":160,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"C6EDD0D4-845A-4D5F-9022-349343B5DEAE\\\"}}\\n{\\\"id\\\":\\\"C6EDD0D4-845A-4D5F-9022-349343B5DEAE\\\",\\\"category\\\":0,\\\"name\\\":\\\"Cosmos\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/C6EDD0D4-845A-4D5F-9022-349343B5DEAE.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/C6EDD0D4-845A-4D5F-9022-349343B5DEAE.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":200,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"CA1D1AAD-8408-4204-986F-F28565D9729B\\\"}}\\n{\\\"id\\\":\\\"CA1D1AAD-8408-4204-986F-F28565D9729B\\\",\\\"category\\\":0,\\\"name\\\":\\\"B/W
  Shake\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/CA1D1AAD-8408-4204-986F-F28565D9729B.2.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/CA1D1AAD-8408-4204-986F-F28565D9729B.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":50,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"label\\\":\\\"new\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"CD50AE6B-0BD0-4AFD-B122-7D1E33A2C76A\\\"}}\\n{\\\"id\\\":\\\"CD50AE6B-0BD0-4AFD-B122-7D1E33A2C76A\\\",\\\"category\\\":0,\\\"name\\\":\\\"9
  Grid
  Marque\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/CD50AE6B-0BD0-4AFD-B122-7D1E33A2C76A.2.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/CD50AE6B-0BD0-4AFD-B122-7D1E33A2C76A.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":290,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"D3953EDC-CC71-4C63-B1A9-D905180F562D\\\"}}\\n{\\\"id\\\":\\\"D3953EDC-CC71-4C63-B1A9-D905180F562D\\\",\\\"category\\\":0,\\\"name\\\":\\\"Disco
  Leaks\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/D3953EDC-CC71-4C63-B1A9-D905180F562D.2.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/D3953EDC-CC71-4C63-B1A9-D905180F562D.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":280,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"DDBA78BB-9B83-4E29-B39B-4152AF1AFD00\\\"}}\\n{\\\"id\\\":\\\"DDBA78BB-9B83-4E29-B39B-4152AF1AFD00\\\",\\\"category\\\":0,\\\"name\\\":\\\"Polaroid\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/DDBA78BB-9B83-4E29-B39B-4152AF1AFD00.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/DDBA78BB-9B83-4E29-B39B-4152AF1AFD00.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":250,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"E0CD6EBA-7D95-4F83-B9F8-79FE55C2979E\\\"}}\\n{\\\"id\\\":\\\"E0CD6EBA-7D95-4F83-B9F8-79FE55C2979E\\\",\\\"category\\\":0,\\\"name\\\":\\\"Energy
  Lines\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/E0CD6EBA-7D95-4F83-B9F8-79FE55C2979E.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/E0CD6EBA-7D95-4F83-B9F8-79FE55C2979E.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":100,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"E1877C68-4610-41F6-B0F3-432CA468FE3E\\\"}}\\n{\\\"id\\\":\\\"E1877C68-4610-41F6-B0F3-432CA468FE3E\\\",\\\"category\\\":0,\\\"name\\\":\\\"Earth
  Shatter\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/E1877C68-4610-41F6-B0F3-432CA468FE3E.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/E1877C68-4610-41F6-B0F3-432CA468FE3E.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":90,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"FCBB591F-7502-48AF-93BC-4B4A094A660E\\\"}}\\n{\\\"id\\\":\\\"FCBB591F-7502-48AF-93BC-4B4A094A660E\\\",\\\"category\\\":0,\\\"name\\\":\\\"Golden
  Burst\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/FCBB591F-7502-48AF-93BC-4B4A094A660E.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/FCBB591F-7502-48AF-93BC-4B4A094A660E.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":230,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"B199E719-D58B-4AB3-8ED6-8DEB9832612C\\\"}}\\n{\\\"id\\\":\\\"B199E719-D58B-4AB3-8ED6-8DEB9832612C\\\",\\\"category\\\":0,\\\"name\\\":\\\"F2\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/B199E719-D58B-4AB3-8ED6-8DEB9832612C.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/B199E719-D58B-4AB3-8ED6-8DEB9832612C.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":80,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"9F06B9A5-EC3A-4282-B597-4A6810137C85\\\"}}\\n{\\\"id\\\":\\\"9F06B9A5-EC3A-4282-B597-4A6810137C85\\\",\\\"category\\\":0,\\\"name\\\":\\\"Dettol\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/9F06B9A5-EC3A-4282-B597-4A6810137C85.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/9F06B9A5-EC3A-4282-B597-4A6810137C85.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":9,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"94FE2DD3-1794-4DDD-9887-291FA0536B6A\\\"}}\\n{\\\"id\\\":\\\"94FE2DD3-1794-4DDD-9887-291FA0536B6A\\\",\\\"category\\\":0,\\\"name\\\":\\\"Dettol
  V1\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/94FE2DD3-1794-4DDD-9887-291FA0536B6A.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/94FE2DD3-1794-4DDD-9887-291FA0536B6A.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":7,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"valid_till\\\":1643353716921,\\\"label\\\":\\\"New1\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"50CED887-CF60-4C58-8756-C9B8C5AFFBCC\\\"}}\\n{\\\"id\\\":\\\"50CED887-CF60-4C58-8756-C9B8C5AFFBCC\\\",\\\"category\\\":0,\\\"name\\\":\\\"Dettol
  V2\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/50CED887-CF60-4C58-8756-C9B8C5AFFBCC.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/50CED887-CF60-4C58-8756-C9B8C5AFFBCC.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":8,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"user_action\\\":\\\"\\\",\\\"label\\\":\\\"test\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"60CED887-CF60-4C58-8756-C9B8C5AFFBCC\\\"}}\\n{\\\"id\\\":\\\"60CED887-CF60-4C58-8756-C9B8C5AFFBCC\\\",\\\"category\\\":0,\\\"name\\\":\\\"Dettol
  Looped\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/60CED887-CF60-4C58-8756-C9B8C5AFFBCC.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/60CED887-CF60-4C58-8756-C9B8C5AFFBCC.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":5,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"valid_till\\\":1643612899048,\\\"label\\\":\\\"new\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"619DFD51-DE42-4F39-BF4A-24EC9F01C99E\\\"}}\\n{\\\"id\\\":\\\"619DFD51-DE42-4F39-BF4A-24EC9F01C99E\\\",\\\"category\\\":0,\\\"name\\\":\\\"2X\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/619DFD51-DE42-4F39-BF4A-24EC9F01C99E.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/619DFD51-DE42-4F39-BF4A-24EC9F01C99E.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":1,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"valid_till\\\":1650802483480,\\\"label\\\":\\\"latest\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"177F591D-5F0E-4321-BFFD-F2A79D50D91F\\\"}}\\n{\\\"id\\\":\\\"177F591D-5F0E-4321-BFFD-F2A79D50D91F\\\",\\\"category\\\":0,\\\"name\\\":\\\"Water
  Bucket\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/177F591D-5F0E-4321-BFFD-F2A79D50D91F.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/177F591D-5F0E-4321-BFFD-F2A79D50D91F.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":4,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"alias\\\":\\\"Water
  Image\\\",\\\"valid_till\\\":1650738606399,\\\"label\\\":\\\"latest\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"2257D45D-D909-458B-8004-04CB20CDAA12\\\"}}\\n{\\\"id\\\":\\\"2257D45D-D909-458B-8004-04CB20CDAA12\\\",\\\"category\\\":0,\\\"name\\\":\\\"Lucknow
  a large city in northern India and capital of
  UP\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/2257D45D-D909-458B-8004-04CB20CDAA12.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/blank.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":1340,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"30638A40-F007-42A7-A411-EABF2AFBE5D2\\\"}}\\n{\\\"id\\\":\\\"30638A40-F007-42A7-A411-EABF2AFBE5D2\\\",\\\"category\\\":0,\\\"name\\\":\\\"Malik\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/30638A40-F007-42A7-A411-EABF2AFBE5D2.1.videofx\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/30638A40-F007-42A7-A411-EABF2AFBE5D2.1.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":1,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"valid_till\\\":1650797843152,\\\"label\\\":\\\"latest\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"9585FCC7-C5E3-41CE-A341-D121DFE87744\\\"}}\\n{\\\"id\\\":\\\"9585FCC7-C5E3-41CE-A341-D121DFE87744\\\",\\\"category\\\":0,\\\"name\\\":\\\"2x
  Menthol\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/videofx_2/2xmenthol.jpg\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/videofx_2/2xmenthol.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":2,\\\"type_name\\\":\\\"videofx\\\",\\\"view_order\\\":0,\\\"filter_type\\\":\\\"EFFECT\\\",\\\"asset_type\\\":\\\"EFFECT\\\",\\\"has_sound\\\":true,\\\"valid_till\\\":1646226643963,\\\"label\\\":\\\"New3
  updated\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"0DA345FA-A13A-44B1-9549-3B79C9DE9EF2\\\"}}\\n{\\\"id\\\":\\\"0DA345FA-A13A-44B1-9549-3B79C9DE9EF2\\\",\\\"category\\\":0,\\\"name\\\":\\\"Kitty\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/0DA345FA-A13A-44B1-9549-3B79C9DE9EF2.2.arscene\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/0DA345FA-A13A-44B1-9549-3B79C9DE9EF2.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":14,\\\"type_name\\\":\\\"arscene\\\",\\\"view_order\\\":15,\\\"filter_type\\\":\\\"\\\",\\\"asset_type\\\":\\\"MASK\\\",\\\"has_sound\\\":false,\\\"valid_till\\\":1643612955115,\\\"label\\\":\\\"New\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"25C78DC6-823C-4103-9E8A-D84350362F16\\\"}}\\n{\\\"id\\\":\\\"25C78DC6-823C-4103-9E8A-D84350362F16\\\",\\\"category\\\":0,\\\"name\\\":\\\"Pick
  you\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/25C78DC6-823C-4103-9E8A-D84350362F16.3.arscene\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/25C78DC6-823C-4103-9E8A-D84350362F16.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":14,\\\"type_name\\\":\\\"arscene\\\",\\\"view_order\\\":180,\\\"filter_type\\\":\\\"\\\",\\\"asset_type\\\":\\\"MASK\\\",\\\"user_action\\\":\\\"\\\",\\\"has_sound\\\":false,\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"45B2C68F-D6DB-4567-96A7-82276AA11848\\\"}}\\n{\\\"id\\\":\\\"45B2C68F-D6DB-4567-96A7-82276AA11848\\\",\\\"category\\\":0,\\\"name\\\":\\\"Bride\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/45B2C68F-D6DB-4567-96A7-82276AA11848.4.arscene\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/45B2C68F-D6DB-4567-96A7-82276AA11848.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":14,\\\"type_name\\\":\\\"arscene\\\",\\\"view_order\\\":280,\\\"asset_type\\\":\\\"MASK\\\",\\\"has_sound\\\":false,\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"464EDF75-34AF-40AD-BCEB-5BD8712BF723\\\"}}\\n{\\\"id\\\":\\\"464EDF75-34AF-40AD-BCEB-5BD8712BF723\\\",\\\"category\\\":0,\\\"name\\\":\\\"Anonymous\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/464EDF75-34AF-40AD-BCEB-5BD8712BF723.2.arscene\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/464EDF75-34AF-40AD-BCEB-5BD8712BF723.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":14,\\\"type_name\\\":\\\"arscene\\\",\\\"view_order\\\":270,\\\"filter_type\\\":\\\"\\\",\\\"asset_type\\\":\\\"MASK\\\",\\\"user_action\\\":\\\"\\\",\\\"has_sound\\\":false,\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"5C5D8FC4-8970-44DC-B85C-DE0A375CB5D6\\\"}}\\n{\\\"id\\\":\\\"5C5D8FC4-8970-44DC-B85C-DE0A375CB5D6\\\",\\\"category\\\":0,\\\"name\\\":\\\"Kitty
  berries\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/5C5D8FC4-8970-44DC-B85C-DE0A375CB5D6.2.arscene\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/5C5D8FC4-8970-44DC-B85C-DE0A375CB5D6.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":14,\\\"type_name\\\":\\\"arscene\\\",\\\"view_order\\\":250,\\\"filter_type\\\":\\\"\\\",\\\"asset_type\\\":\\\"MASK\\\",\\\"user_action\\\":\\\"\\\",\\\"has_sound\\\":false,\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"63833FB8-95F7-4A92-A852-A048BA223F5E\\\"}}\\n{\\\"id\\\":\\\"63833FB8-95F7-4A92-A852-A048BA223F5E\\\",\\\"category\\\":0,\\\"name\\\":\\\"Petal
  shower\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/63833FB8-95F7-4A92-A852-A048BA223F5E.1.arscene\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/63833FB8-95F7-4A92-A852-A048BA223F5E.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":14,\\\"type_name\\\":\\\"arscene\\\",\\\"view_order\\\":170,\\\"filter_type\\\":\\\"\\\",\\\"asset_type\\\":\\\"MASK\\\",\\\"has_sound\\\":false,\\\"valid_till\\\":1635682761939,\\\"label\\\":\\\"new\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"73F1C799-B7F0-4F12-9679-F9840F61D557\\\"}}\\n{\\\"id\\\":\\\"73F1C799-B7F0-4F12-9679-F9840F61D557\\\",\\\"category\\\":0,\\\"name\\\":\\\"Glam\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/73F1C799-B7F0-4F12-9679-F9840F61D557.5.arscene\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/73F1C799-B7F0-4F12-9679-F9840F61D557.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":14,\\\"type_name\\\":\\\"arscene\\\",\\\"view_order\\\":200,\\\"filter_type\\\":\\\"\\\",\\\"asset_type\\\":\\\"MASK\\\",\\\"user_action\\\":\\\"\\\",\\\"has_sound\\\":false,\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"827EB8A5-1804-45CE-B054-4BA640E566A9\\\"}}\\n{\\\"id\\\":\\\"827EB8A5-1804-45CE-B054-4BA640E566A9\\\",\\\"category\\\":0,\\\"name\\\":\\\"Chicken
  dinner\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/827EB8A5-1804-45CE-B054-4BA640E566A9.6.arscene\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/827EB8A5-1804-45CE-B054-4BA640E566A9.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":14,\\\"type_name\\\":\\\"arscene\\\",\\\"view_order\\\":150,\\\"filter_type\\\":\\\"\\\",\\\"asset_type\\\":\\\"MASK\\\",\\\"user_action\\\":\\\"Nod
  your
  head\\\",\\\"has_sound\\\":false,\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"8DF4B0BC-3438-4A1D-8BB6-3D6E11D48D92\\\"}}\\n{\\\"id\\\":\\\"8DF4B0BC-3438-4A1D-8BB6-3D6E11D48D92\\\",\\\"category\\\":0,\\\"name\\\":\\\"Party
  glass\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/8DF4B0BC-3438-4A1D-8BB6-3D6E11D48D92.2.arscene\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/8DF4B0BC-3438-4A1D-8BB6-3D6E11D48D92.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":14,\\\"type_name\\\":\\\"arscene\\\",\\\"view_order\\\":160,\\\"filter_type\\\":\\\"\\\",\\\"asset_type\\\":\\\"MASK\\\",\\\"has_sound\\\":false,\\\"valid_till\\\":1635596349417,\\\"label\\\":\\\"new\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"918F57EB-C65B-4729-AD69-5BEB41426D40\\\"}}\\n{\\\"id\\\":\\\"918F57EB-C65B-4729-AD69-5BEB41426D40\\\",\\\"category\\\":0,\\\"name\\\":\\\"Meow\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/918F57EB-C65B-4729-AD69-5BEB41426D40.2.arscene\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/918F57EB-C65B-4729-AD69-5BEB41426D40.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":14,\\\"type_name\\\":\\\"arscene\\\",\\\"view_order\\\":70,\\\"filter_type\\\":\\\"\\\",\\\"asset_type\\\":\\\"MASK\\\",\\\"has_sound\\\":false,\\\"alias\\\":\\\"Mast
  Image\\\",\\\"valid_till\\\":1646040952490,\\\"label\\\":\\\"new\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"B271F162-3C20-4C83-90ED-EF722EA78DA9\\\"}}\\n{\\\"id\\\":\\\"B271F162-3C20-4C83-90ED-EF722EA78DA9\\\",\\\"category\\\":0,\\\"name\\\":\\\"Dusshera\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/B271F162-3C20-4C83-90ED-EF722EA78DA9.1.arscene\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/B271F162-3C20-4C83-90ED-EF722EA78DA9.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":14,\\\"type_name\\\":\\\"arscene\\\",\\\"view_order\\\":14,\\\"filter_type\\\":\\\"\\\",\\\"asset_type\\\":\\\"MASK\\\",\\\"is_archived\\\":false,\\\"has_sound\\\":true,\\\"alias\\\":\\\"Face\\\",\\\"not_show_in_thumbnail\\\":false,\\\"valid_till\\\":1643615226490,\\\"label\\\":\\\"new1\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"B2AEDB44-FF3B-45A6-A66D-0A2B1E6D48ED\\\"}}\\n{\\\"id\\\":\\\"B2AEDB44-FF3B-45A6-A66D-0A2B1E6D48ED\\\",\\\"category\\\":0,\\\"name\\\":\\\"Showtime\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/B2AEDB44-FF3B-45A6-A66D-0A2B1E6D48ED.5.arscene\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/B2AEDB44-FF3B-45A6-A66D-0A2B1E6D48ED.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":14,\\\"type_name\\\":\\\"arscene\\\",\\\"view_order\\\":220,\\\"filter_type\\\":\\\"\\\",\\\"asset_type\\\":\\\"MASK\\\",\\\"user_action\\\":\\\"\\\",\\\"has_sound\\\":false,\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"D115AFF8-D7E4-4EB5-8ABB-9BAF2D6793F2\\\"}}\\n{\\\"id\\\":\\\"D115AFF8-D7E4-4EB5-8ABB-9BAF2D6793F2\\\",\\\"category\\\":0,\\\"name\\\":\\\"Thug
  life\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/D115AFF8-D7E4-4EB5-8ABB-9BAF2D6793F2.4.arscene\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/D115AFF8-D7E4-4EB5-8ABB-9BAF2D6793F2.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":14,\\\"type_name\\\":\\\"arscene\\\",\\\"view_order\\\":260,\\\"filter_type\\\":\\\"\\\",\\\"asset_type\\\":\\\"MASK\\\",\\\"user_action\\\":\\\"\\\",\\\"has_sound\\\":false,\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"D18BD048-4176-4E14-B705-7E2A4DF08274\\\"}}\\n{\\\"id\\\":\\\"D18BD048-4176-4E14-B705-7E2A4DF08274\\\",\\\"category\\\":0,\\\"name\\\":\\\"Iron
  Man\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/D18BD048-4176-4E14-B705-7E2A4DF08274.2.arscene\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/D18BD048-4176-4E14-B705-7E2A4DF08274.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":14,\\\"type_name\\\":\\\"arscene\\\",\\\"view_order\\\":120,\\\"filter_type\\\":\\\"\\\",\\\"asset_type\\\":\\\"MASK\\\",\\\"has_sound\\\":false,\\\"valid_till\\\":1635595574872,\\\"label\\\":\\\"new\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"D3F9A1A9-CFD8-46B6-8E9C-DC3E87A9A687\\\"}}\\n{\\\"id\\\":\\\"D3F9A1A9-CFD8-46B6-8E9C-DC3E87A9A687\\\",\\\"category\\\":0,\\\"name\\\":\\\"Retro
  love\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/D3F9A1A9-CFD8-46B6-8E9C-DC3E87A9A687.3.arscene\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/D3F9A1A9-CFD8-46B6-8E9C-DC3E87A9A687.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":14,\\\"type_name\\\":\\\"arscene\\\",\\\"view_order\\\":190,\\\"filter_type\\\":\\\"\\\",\\\"asset_type\\\":\\\"MASK\\\",\\\"user_action\\\":\\\"\\\",\\\"has_sound\\\":false,\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"EA962143-6CCA-42E4-B7FC-9615B9EEA231\\\"}}\\n{\\\"id\\\":\\\"EA962143-6CCA-42E4-B7FC-9615B9EEA231\\\",\\\"category\\\":0,\\\"name\\\":\\\"Glitch
  skull\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/EA962143-6CCA-42E4-B7FC-9615B9EEA231.3.arscene\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/EA962143-6CCA-42E4-B7FC-9615B9EEA231.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":14,\\\"type_name\\\":\\\"arscene\\\",\\\"view_order\\\":240,\\\"filter_type\\\":\\\"\\\",\\\"asset_type\\\":\\\"MASK\\\",\\\"user_action\\\":\\\"\\\",\\\"has_sound\\\":false,\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"F067A31B-01B7-4384-A8FE-E5A7CE790418\\\"}}\\n{\\\"id\\\":\\\"F067A31B-01B7-4384-A8FE-E5A7CE790418\\\",\\\"category\\\":0,\\\"name\\\":\\\"In
  love\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/F067A31B-01B7-4384-A8FE-E5A7CE790418.5.arscene\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/F067A31B-01B7-4384-A8FE-E5A7CE790418.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":14,\\\"type_name\\\":\\\"arscene\\\",\\\"view_order\\\":210,\\\"filter_type\\\":\\\"\\\",\\\"asset_type\\\":\\\"MASK\\\",\\\"user_action\\\":\\\"\\\",\\\"has_sound\\\":false,\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"FD135303-4192-44D1-8682-A727105EDE83\\\"}}\\n{\\\"id\\\":\\\"FD135303-4192-44D1-8682-A727105EDE83\\\",\\\"category\\\":0,\\\"name\\\":\\\"Crown\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/FD135303-4192-44D1-8682-A727105EDE83.3.arscene\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/FD135303-4192-44D1-8682-A727105EDE83.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":14,\\\"type_name\\\":\\\"arscene\\\",\\\"view_order\\\":90,\\\"filter_type\\\":\\\"\\\",\\\"asset_type\\\":\\\"MASK\\\",\\\"has_sound\\\":false,\\\"valid_till\\\":1629525378299,\\\"label\\\":\\\"new\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"FE960FE8-4884-4BB0-8F1F-0E61AD7C4004\\\"}}\\n{\\\"id\\\":\\\"FE960FE8-4884-4BB0-8F1F-0E61AD7C4004\\\",\\\"category\\\":0,\\\"name\\\":\\\"Giraffe\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/FE960FE8-4884-4BB0-8F1F-0E61AD7C4004.3.arscene\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/FE960FE8-4884-4BB0-8F1F-0E61AD7C4004.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":14,\\\"type_name\\\":\\\"arscene\\\",\\\"view_order\\\":130,\\\"filter_type\\\":\\\"\\\",\\\"asset_type\\\":\\\"MASK\\\",\\\"user_action\\\":\\\"\\\",\\\"has_sound\\\":false,\\\"valid_till\\\":1643615241627,\\\"label\\\":\\\"new\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"62D20446-2E3D-4493-91CB-14B6E3160676\\\"}}\\n{\\\"id\\\":\\\"62D20446-2E3D-4493-91CB-14B6E3160676\\\",\\\"category\\\":0,\\\"name\\\":\\\"Holi\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/arscene_14/62D20446-2E3D-4493-91CB-14B6E3160676.1.arscene\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/arscene_14/62D20446-2E3D-4493-91CB-14B6E3160676.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":14,\\\"type_name\\\":\\\"arscene\\\",\\\"view_order\\\":13,\\\"filter_type\\\":\\\"\\\",\\\"asset_type\\\":\\\"MASK\\\",\\\"has_sound\\\":true,\\\"valid_till\\\":1643621733298,\\\"label\\\":\\\"Hot\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"2d1\\\"}}\\n{\\\"id\\\":\\\"2d1\\\",\\\"category\\\":0,\\\"name\\\":\\\"Crown\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_sticker_25/2d1.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_sticker_25/2d1.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":25,\\\"type_name\\\":\\\"fu_sticker\\\",\\\"view_order\\\":10,\\\"asset_type\\\":\\\"FU_STICKER\\\",\\\"alias\\\":\\\"Crown\\\",\\\"valid_till\\\":1629462370947,\\\"label\\\":\\\"New\\\",\\\"category_name\\\":\\\"Crown\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"2d6\\\"}}\\n{\\\"id\\\":\\\"2d6\\\",\\\"category\\\":0,\\\"name\\\":\\\"Cloche
  Hat\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_sticker_25/2d6.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_sticker_25/2d6.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":25,\\\"type_name\\\":\\\"fu_sticker\\\",\\\"view_order\\\":40,\\\"asset_type\\\":\\\"FU_STICKER\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Cloche
  hat\\\",\\\"category_name\\\":\\\"Cloche
  hat\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"2d9\\\"}}\\n{\\\"id\\\":\\\"2d9\\\",\\\"category\\\":0,\\\"name\\\":\\\"Hair
  Band\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_sticker_25/2d9.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_sticker_25/2d9.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":25,\\\"type_name\\\":\\\"fu_sticker\\\",\\\"view_order\\\":70,\\\"asset_type\\\":\\\"FU_STICKER\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Hair
  band\\\",\\\"category_name\\\":\\\"Hair
  band\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"2d10\\\"}}\\n{\\\"id\\\":\\\"2d10\\\",\\\"category\\\":0,\\\"name\\\":\\\"Flower
  Crown\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_sticker_25/2d10.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_sticker_25/2d10.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":25,\\\"type_name\\\":\\\"fu_sticker\\\",\\\"view_order\\\":80,\\\"asset_type\\\":\\\"FU_STICKER\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Flower
  crown\\\",\\\"category_name\\\":\\\"Flower
  crown\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"3d1\\\"}}\\n{\\\"id\\\":\\\"3d1\\\",\\\"category\\\":0,\\\"name\\\":\\\"Bucket
  Hat\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_sticker_25/3d1.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_sticker_25/3d1.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":25,\\\"type_name\\\":\\\"fu_sticker\\\",\\\"view_order\\\":10,\\\"asset_type\\\":\\\"FU_STICKER\\\",\\\"alias\\\":\\\"Bucket
  Hat\\\",\\\"valid_till\\\":1629548783656,\\\"label\\\":\\\"New\\\",\\\"category_name\\\":\\\"Bucket
  Hat\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"3d2\\\"}}\\n{\\\"id\\\":\\\"3d2\\\",\\\"category\\\":0,\\\"name\\\":\\\"Clown
  Hat\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_sticker_25/3d2.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_sticker_25/3d2.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":25,\\\"type_name\\\":\\\"fu_sticker\\\",\\\"view_order\\\":20,\\\"asset_type\\\":\\\"FU_STICKER\\\",\\\"alias\\\":\\\"Clown
  hat\\\",\\\"valid_till\\\":1635682046168,\\\"label\\\":\\\"new\\\",\\\"category_name\\\":\\\"Clown
  hat\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"3d3\\\"}}\\n{\\\"id\\\":\\\"3d3\\\",\\\"category\\\":0,\\\"name\\\":\\\"Warrior\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_sticker_25/3d3.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_sticker_25/3d3.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":25,\\\"type_name\\\":\\\"fu_sticker\\\",\\\"view_order\\\":30,\\\"asset_type\\\":\\\"FU_STICKER\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Warrior\\\",\\\"category_name\\\":\\\"Warrior\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"3d4\\\"}}\\n{\\\"id\\\":\\\"3d4\\\",\\\"category\\\":0,\\\"name\\\":\\\"Duck\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_sticker_25/3d4.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_sticker_25/3d4.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":25,\\\"type_name\\\":\\\"fu_sticker\\\",\\\"view_order\\\":40,\\\"asset_type\\\":\\\"FU_STICKER\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Duck\\\",\\\"category_name\\\":\\\"Duck\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"3d5\\\"}}\\n{\\\"id\\\":\\\"3d5\\\",\\\"category\\\":0,\\\"name\\\":\\\"Roses
  &
  Lilies\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_sticker_25/3d5.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_sticker_25/3d5.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":25,\\\"type_name\\\":\\\"fu_sticker\\\",\\\"view_order\\\":50,\\\"asset_type\\\":\\\"FU_STICKER\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Roses
  & lilies\\\",\\\"category_name\\\":\\\"Roses &
  lilies\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"3d6\\\"}}\\n{\\\"id\\\":\\\"3d6\\\",\\\"category\\\":0,\\\"name\\\":\\\"Floral
  Band\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_sticker_25/3d6.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_sticker_25/3d6.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":25,\\\"type_name\\\":\\\"fu_sticker\\\",\\\"view_order\\\":60,\\\"asset_type\\\":\\\"FU_STICKER\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Floral
  band\\\",\\\"category_name\\\":\\\"Floral
  band\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"3d8\\\"}}\\n{\\\"id\\\":\\\"3d8\\\",\\\"category\\\":0,\\\"name\\\":\\\"Mask
  Hat\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_sticker_25/3d8.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_sticker_25/3d8.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":25,\\\"type_name\\\":\\\"fu_sticker\\\",\\\"view_order\\\":80,\\\"asset_type\\\":\\\"FU_STICKER\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Mask
  Hat\\\",\\\"category_name\\\":\\\"Mask
  Hat\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"3d9\\\"}}\\n{\\\"id\\\":\\\"3d9\\\",\\\"category\\\":0,\\\"name\\\":\\\"Tribal\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_sticker_25/3d9.2.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_sticker_25/3d9.2.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":25,\\\"type_name\\\":\\\"fu_sticker\\\",\\\"view_order\\\":5,\\\"asset_type\\\":\\\"FU_STICKER\\\",\\\"valid_till\\\":1650802036104,\\\"label\\\":\\\"Asset
  testing\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"ar1\\\"}}\\n{\\\"id\\\":\\\"ar1\\\",\\\"category\\\":0,\\\"name\\\":\\\"Blue
  Wings\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_armask_26/ar1.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_armask_26/ar1.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":26,\\\"type_name\\\":\\\"fu_armask\\\",\\\"view_order\\\":10,\\\"asset_type\\\":\\\"FU_AR_MASK\\\",\\\"alias\\\":\\\"Blue
  Wings\\\",\\\"valid_till\\\":1635595687955,\\\"label\\\":\\\"New\\\",\\\"category_name\\\":\\\"Blue
  Wings\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"ar2\\\"}}\\n{\\\"id\\\":\\\"ar2\\\",\\\"category\\\":0,\\\"name\\\":\\\"Blue
  Bird\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_armask_26/ar2.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_armask_26/ar2.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":26,\\\"type_name\\\":\\\"fu_armask\\\",\\\"view_order\\\":20,\\\"asset_type\\\":\\\"FU_AR_MASK\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Blue
  Bird\\\",\\\"category_name\\\":\\\"Blue
  Bird\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"ar3\\\"}}\\n{\\\"id\\\":\\\"ar3\\\",\\\"category\\\":0,\\\"name\\\":\\\"Clown\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_armask_26/ar3.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_armask_26/ar3.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":26,\\\"type_name\\\":\\\"fu_armask\\\",\\\"view_order\\\":30,\\\"asset_type\\\":\\\"FU_AR_MASK\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Clown\\\",\\\"category_name\\\":\\\"Clown\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"ar4\\\"}}\\n{\\\"id\\\":\\\"ar4\\\",\\\"category\\\":0,\\\"name\\\":\\\"Leopard\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_armask_26/ar4.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_armask_26/ar4.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":26,\\\"type_name\\\":\\\"fu_armask\\\",\\\"view_order\\\":40,\\\"asset_type\\\":\\\"FU_AR_MASK\\\",\\\"alias\\\":\\\"Leopard\\\",\\\"valid_till\\\":1635595701895,\\\"label\\\":\\\"new\\\",\\\"category_name\\\":\\\"Leopard\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"ar5\\\"}}\\n{\\\"id\\\":\\\"ar5\\\",\\\"category\\\":0,\\\"name\\\":\\\"Orange
  Wings\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_armask_26/ar5.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_armask_26/ar5.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":26,\\\"type_name\\\":\\\"fu_armask\\\",\\\"view_order\\\":50,\\\"asset_type\\\":\\\"FU_AR_MASK\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Orange
  wings\\\",\\\"category_name\\\":\\\"Orange
  wings\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"ar6\\\"}}\\n{\\\"id\\\":\\\"ar6\\\",\\\"category\\\":0,\\\"name\\\":\\\"Panda\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_armask_26/ar6.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_armask_26/ar6.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":26,\\\"type_name\\\":\\\"fu_armask\\\",\\\"view_order\\\":60,\\\"asset_type\\\":\\\"FU_AR_MASK\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Panda\\\",\\\"category_name\\\":\\\"Panda\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"ar7\\\"}}\\n{\\\"id\\\":\\\"ar7\\\",\\\"category\\\":0,\\\"name\\\":\\\"Red
  Wings\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_armask_26/ar7.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_armask_26/ar7.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":26,\\\"type_name\\\":\\\"fu_armask\\\",\\\"view_order\\\":70,\\\"asset_type\\\":\\\"FU_AR_MASK\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Red
  wings\\\",\\\"category_name\\\":\\\"Red
  wings\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"ar8\\\"}}\\n{\\\"id\\\":\\\"ar8\\\",\\\"category\\\":0,\\\"name\\\":\\\"Tiger\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_armask_26/ar8.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_armask_26/ar8.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":26,\\\"type_name\\\":\\\"fu_armask\\\",\\\"view_order\\\":80,\\\"asset_type\\\":\\\"FU_AR_MASK\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Tiger\\\",\\\"category_name\\\":\\\"Tiger\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"ar9\\\"}}\\n{\\\"id\\\":\\\"ar9\\\",\\\"category\\\":0,\\\"name\\\":\\\"Tiger
  Mask\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_armask_26/ar9.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_armask_26/ar9.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":26,\\\"type_name\\\":\\\"fu_armask\\\",\\\"view_order\\\":90,\\\"asset_type\\\":\\\"FU_AR_MASK\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Tiger
  mask\\\",\\\"category_name\\\":\\\"Tiger
  mask\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"ar10\\\"}}\\n{\\\"id\\\":\\\"ar10\\\",\\\"category\\\":0,\\\"name\\\":\\\"White
  Tiger
  Mask\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_armask_26/ar10.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_armask_26/ar10.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":26,\\\"type_name\\\":\\\"fu_armask\\\",\\\"view_order\\\":100,\\\"asset_type\\\":\\\"FU_AR_MASK\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"White
  tiger mask\\\",\\\"category_name\\\":\\\"White tiger
  mask\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"er2\\\"}}\\n{\\\"id\\\":\\\"er2\\\",\\\"category\\\":0,\\\"name\\\":\\\"Gas
  Mask\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_expression_28/er2.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_expression_28/er2.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":28,\\\"type_name\\\":\\\"fu_expression\\\",\\\"view_order\\\":20,\\\"asset_type\\\":\\\"FU_EXPRESSION_RECOGNITION\\\",\\\"user_action\\\":\\\"Puff
  your cheeck\\\",\\\"alias\\\":\\\"Gas
  mask\\\",\\\"valid_till\\\":1653990412850,\\\"label\\\":\\\"new2\\\",\\\"category_name\\\":\\\"Gas
  mask\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"er3\\\"}}\\n{\\\"id\\\":\\\"er3\\\",\\\"category\\\":0,\\\"name\\\":\\\"Hat
  &
  Mask\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_expression_28/er3.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_expression_28/er3.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":28,\\\"type_name\\\":\\\"fu_expression\\\",\\\"view_order\\\":30,\\\"asset_type\\\":\\\"FU_EXPRESSION_RECOGNITION\\\",\\\"user_action\\\":\\\"Blink\\\",\\\"alias\\\":\\\"Hat
  &
  mask\\\",\\\"valid_till\\\":1653991053918,\\\"label\\\":\\\"new2\\\",\\\"category_name\\\":\\\"Hat
  &
  mask\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"er4\\\"}}\\n{\\\"id\\\":\\\"er4\\\",\\\"category\\\":0,\\\"name\\\":\\\"Kiss\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_expression_28/er4.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_expression_28/er4.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":28,\\\"type_name\\\":\\\"fu_expression\\\",\\\"view_order\\\":40,\\\"asset_type\\\":\\\"FU_EXPRESSION_RECOGNITION\\\",\\\"user_action\\\":\\\"Give
  me a
  kiss\\\",\\\"alias\\\":\\\"Kiss\\\",\\\"valid_till\\\":1643363346822,\\\"label\\\":\\\"new1\\\",\\\"category_name\\\":\\\"Kiss\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"er5\\\"}}\\n{\\\"id\\\":\\\"er5\\\",\\\"category\\\":0,\\\"name\\\":\\\"Flash\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_expression_28/er5.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_expression_28/er5.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":28,\\\"type_name\\\":\\\"fu_expression\\\",\\\"view_order\\\":50,\\\"asset_type\\\":\\\"FU_EXPRESSION_RECOGNITION\\\",\\\"user_action\\\":\\\"Frown\\\",\\\"alias\\\":\\\"Flash\\\",\\\"category_name\\\":\\\"Flash\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"er6\\\"}}\\n{\\\"id\\\":\\\"er6\\\",\\\"category\\\":0,\\\"name\\\":\\\"Double
  Braid\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_expression_28/er6.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_expression_28/er6.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":28,\\\"type_name\\\":\\\"fu_expression\\\",\\\"view_order\\\":60,\\\"asset_type\\\":\\\"FU_EXPRESSION_RECOGNITION\\\",\\\"user_action\\\":\\\"Smile\\\",\\\"alias\\\":\\\"Double
  braid\\\",\\\"category_name\\\":\\\"Double
  braid\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"er7\\\"}}\\n{\\\"id\\\":\\\"er7\\\",\\\"category\\\":0,\\\"name\\\":\\\"Frog
  Hat\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_expression_28/er7.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_expression_28/er7.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":28,\\\"type_name\\\":\\\"fu_expression\\\",\\\"view_order\\\":70,\\\"asset_type\\\":\\\"FU_EXPRESSION_RECOGNITION\\\",\\\"user_action\\\":\\\"Whistle\\\",\\\"alias\\\":\\\"Frog
  hat\\\",\\\"category_name\\\":\\\"Frog
  hat\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"er1\\\"}}\\n{\\\"id\\\":\\\"er1\\\",\\\"category\\\":0,\\\"name\\\":\\\"Cyberpunk\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_expression_28/er1.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_expression_28/er1.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":28,\\\"type_name\\\":\\\"fu_expression\\\",\\\"view_order\\\":1,\\\"asset_type\\\":\\\"FU_EXPRESSION_RECOGNITION\\\",\\\"user_action\\\":\\\"Open
  your mouth
  fully\\\",\\\"alias\\\":\\\"Cyberpunk\\\",\\\"valid_till\\\":1653935421791,\\\"label\\\":\\\"new2\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"fw2\\\"}}\\n{\\\"id\\\":\\\"fw2\\\",\\\"category\\\":0,\\\"name\\\":\\\"Bubbly
  Cheeks\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_facewarp_29/fw2.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_facewarp_29/fw2.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":29,\\\"type_name\\\":\\\"fu_facewarp\\\",\\\"view_order\\\":20,\\\"asset_type\\\":\\\"FU_FACE_WARP\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"\\\",\\\"valid_till\\\":1654849810247,\\\"label\\\":\\\"new\\\",\\\"category_name\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"fw3\\\"}}\\n{\\\"id\\\":\\\"fw3\\\",\\\"category\\\":0,\\\"name\\\":\\\"Annoyed\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_facewarp_29/fw3.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_facewarp_29/fw3.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":29,\\\"type_name\\\":\\\"fu_facewarp\\\",\\\"view_order\\\":30,\\\"asset_type\\\":\\\"FU_FACE_WARP\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"\\\",\\\"category_name\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"fw4\\\"}}\\n{\\\"id\\\":\\\"fw4\\\",\\\"category\\\":0,\\\"name\\\":\\\"Pear
  Face\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_facewarp_29/fw4.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_facewarp_29/fw4.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":29,\\\"type_name\\\":\\\"fu_facewarp\\\",\\\"view_order\\\":40,\\\"asset_type\\\":\\\"FU_FACE_WARP\\\",\\\"valid_till\\\":1629980906495,\\\"label\\\":\\\"New\\\",\\\"category_name\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"fw5\\\"}}\\n{\\\"id\\\":\\\"fw5\\\",\\\"category\\\":0,\\\"name\\\":\\\"Chubby
  Baby\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_facewarp_29/fw5.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_facewarp_29/fw5.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":29,\\\"type_name\\\":\\\"fu_facewarp\\\",\\\"view_order\\\":50,\\\"asset_type\\\":\\\"FU_FACE_WARP\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"\\\",\\\"category_name\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"fw6\\\"}}\\n{\\\"id\\\":\\\"fw6\\\",\\\"category\\\":0,\\\"name\\\":\\\"Straight
  Face
  Boomer\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_facewarp_29/fw6.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_facewarp_29/fw6.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":29,\\\"type_name\\\":\\\"fu_facewarp\\\",\\\"view_order\\\":60,\\\"asset_type\\\":\\\"FU_FACE_WARP\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"\\\",\\\"category_name\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"fw7\\\"}}\\n{\\\"id\\\":\\\"fw7\\\",\\\"category\\\":0,\\\"name\\\":\\\"Feeling
  Sorry\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_facewarp_29/fw7.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_facewarp_29/fw7.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":29,\\\"type_name\\\":\\\"fu_facewarp\\\",\\\"view_order\\\":70,\\\"asset_type\\\":\\\"FU_FACE_WARP\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"\\\",\\\"category_name\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"fw8\\\"}}\\n{\\\"id\\\":\\\"fw8\\\",\\\"category\\\":0,\\\"name\\\":\\\"Stuffed
  Mouth\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_facewarp_29/fw8.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_facewarp_29/fw8.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":29,\\\"type_name\\\":\\\"fu_facewarp\\\",\\\"view_order\\\":80,\\\"asset_type\\\":\\\"FU_FACE_WARP\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"\\\",\\\"category_name\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"fw10\\\"}}\\n{\\\"id\\\":\\\"fw10\\\",\\\"category\\\":0,\\\"name\\\":\\\"Bully\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_facewarp_29/fw10.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_facewarp_29/fw10.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":29,\\\"type_name\\\":\\\"fu_facewarp\\\",\\\"view_order\\\":100,\\\"asset_type\\\":\\\"FU_FACE_WARP\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"\\\",\\\"category_name\\\":\\\"\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"fw9\\\"}}\\n{\\\"id\\\":\\\"fw9\\\",\\\"category\\\":0,\\\"name\\\":\\\"Gentleman\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_facewarp_29/fw9.2.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_facewarp_29/fw9.2.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":29,\\\"type_name\\\":\\\"fu_facewarp\\\",\\\"view_order\\\":90,\\\"asset_type\\\":\\\"FU_FACE_WARP\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"fw1\\\"}}\\n{\\\"id\\\":\\\"fw1\\\",\\\"category\\\":0,\\\"name\\\":\\\"Grumpy\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_facewarp_29/fw1.2.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_facewarp_29/fw1.2.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":29,\\\"type_name\\\":\\\"fu_facewarp\\\",\\\"view_order\\\":25,\\\"asset_type\\\":\\\"FU_FACE_WARP\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"gr1\\\"}}\\n{\\\"id\\\":\\\"gr1\\\",\\\"category\\\":0,\\\"name\\\":\\\"Petals\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_gesture_30/gr1.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_gesture_30/gr1.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":30,\\\"type_name\\\":\\\"fu_gesture\\\",\\\"view_order\\\":10,\\\"asset_type\\\":\\\"FU_GESTURE_RECOGNITION\\\",\\\"user_action\\\":\\\"High
  five\\\",\\\"alias\\\":\\\"Petals\\\",\\\"valid_till\\\":1655884507500,\\\"label\\\":\\\"new3\\\",\\\"category_name\\\":\\\"Petals\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"gr2\\\"}}\\n{\\\"id\\\":\\\"gr2\\\",\\\"category\\\":0,\\\"name\\\":\\\"Aqua\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_gesture_30/gr2.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_gesture_30/gr2.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":30,\\\"type_name\\\":\\\"fu_gesture\\\",\\\"view_order\\\":20,\\\"asset_type\\\":\\\"FU_GESTURE_RECOGNITION\\\",\\\"user_action\\\":\\\"High
  five\\\",\\\"alias\\\":\\\"Aqua\\\",\\\"valid_till\\\":1655877621158,\\\"label\\\":\\\"new3\\\",\\\"category_name\\\":\\\"Aqua\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"gr3\\\"}}\\n{\\\"id\\\":\\\"gr3\\\",\\\"category\\\":0,\\\"name\\\":\\\"Snow\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_gesture_30/gr3.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_gesture_30/gr3.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":30,\\\"type_name\\\":\\\"fu_gesture\\\",\\\"view_order\\\":30,\\\"asset_type\\\":\\\"FU_GESTURE_RECOGNITION\\\",\\\"user_action\\\":\\\"High
  five\\\",\\\"alias\\\":\\\"Snow\\\",\\\"category_name\\\":\\\"Snow\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"gr4\\\"}}\\n{\\\"id\\\":\\\"gr4\\\",\\\"category\\\":0,\\\"name\\\":\\\"Kitty\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_gesture_30/gr4.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_gesture_30/gr4.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":30,\\\"type_name\\\":\\\"fu_gesture\\\",\\\"view_order\\\":40,\\\"asset_type\\\":\\\"FU_GESTURE_RECOGNITION\\\",\\\"user_action\\\":\\\"Holding
  fist\\\",\\\"alias\\\":\\\"Kitty\\\",\\\"valid_till\\\":1643104606575,\\\"label\\\":\\\"new2\\\",\\\"category_name\\\":\\\"Kitty\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"gr5\\\"}}\\n{\\\"id\\\":\\\"gr5\\\",\\\"category\\\":0,\\\"name\\\":\\\"Little
  Heart\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_gesture_30/gr5.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_gesture_30/gr5.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":30,\\\"type_name\\\":\\\"fu_gesture\\\",\\\"view_order\\\":50,\\\"asset_type\\\":\\\"FU_GESTURE_RECOGNITION\\\",\\\"user_action\\\":\\\"Finger
  heart\\\",\\\"alias\\\":\\\"Little
  heart\\\",\\\"valid_till\\\":1650952832489,\\\"label\\\":\\\"new\\\",\\\"category_name\\\":\\\"Little
  heart\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"halfhighlighter\\\"}}\\n{\\\"id\\\":\\\"halfhighlighter\\\",\\\"category\\\":0,\\\"name\\\":\\\"Sugar
  Cosmetics\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_gesture_30/halfhighlighter.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_gesture_30/halfhighlighter.jpg\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":30,\\\"type_name\\\":\\\"fu_gesture\\\",\\\"view_order\\\":0,\\\"asset_type\\\":\\\"FU_GESTURE_RECOGNITION\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"g1\\\"}}\\n{\\\"id\\\":\\\"g1\\\",\\\"category\\\":0,\\\"name\\\":\\\"Space
  Shooter\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_game_31/g1.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_game_31/g1.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":31,\\\"type_name\\\":\\\"fu_game\\\",\\\"view_order\\\":10,\\\"asset_type\\\":\\\"FU_GAME\\\",\\\"alias\\\":\\\"Space
  shooter\\\",\\\"valid_till\\\":1651125403015,\\\"label\\\":\\\"new1\\\",\\\"category_name\\\":\\\"Space
  shooter\\\",\\\"pass_through\\\":\\\"GAME\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"g2\\\"}}\\n{\\\"id\\\":\\\"g2\\\",\\\"category\\\":0,\\\"name\\\":\\\"Burst
  the
  Balloons\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_game_31/g2.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_game_31/g2.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":31,\\\"type_name\\\":\\\"fu_game\\\",\\\"view_order\\\":20,\\\"asset_type\\\":\\\"FU_GAME\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Burst
  the
  balloons\\\",\\\"valid_till\\\":1650970157268,\\\"label\\\":\\\"new\\\",\\\"category_name\\\":\\\"Burst
  the
  balloons\\\",\\\"pass_through\\\":\\\"GAME\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"g3\\\"}}\\n{\\\"id\\\":\\\"g3\\\",\\\"category\\\":0,\\\"name\\\":\\\"Pick
  the
  Fruits\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_game_31/g3.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_game_31/g3.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":31,\\\"type_name\\\":\\\"fu_game\\\",\\\"view_order\\\":30,\\\"asset_type\\\":\\\"FU_GAME\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Pick
  the
  fruits\\\",\\\"valid_till\\\":1654854517157,\\\"label\\\":\\\"new2\\\",\\\"category_name\\\":\\\"Pick
  the
  fruits\\\",\\\"pass_through\\\":\\\"GAME\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"g4\\\"}}\\n{\\\"id\\\":\\\"g4\\\",\\\"category\\\":0,\\\"name\\\":\\\"Pose\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_game_31/g4.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_game_31/g4.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":31,\\\"type_name\\\":\\\"fu_game\\\",\\\"view_order\\\":40,\\\"asset_type\\\":\\\"FU_GAME\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Pose\\\",\\\"valid_till\\\":1650966943819,\\\"label\\\":\\\"new\\\",\\\"category_name\\\":\\\"Pose\\\",\\\"pass_through\\\":\\\"GAME\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"supermodel\\\"}}\\n{\\\"id\\\":\\\"supermodel\\\",\\\"category\\\":0,\\\"name\\\":\\\"Supermodel\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_makeup_32/supermodel.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_makeup_32/supermodel.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":32,\\\"type_name\\\":\\\"fu_makeup\\\",\\\"view_order\\\":10,\\\"filter_type\\\":\\\"zhiganhui7\\\",\\\"asset_type\\\":\\\"FU_MAKEUP\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"supermodel\\\",\\\"valid_till\\\":1655904638062,\\\"label\\\":\\\"new3\\\",\\\"category_name\\\":\\\"supermodel\\\",\\\"asset_params\\\":\\\"{\\\\\\\"blend_type_tex_blusher\\\\\\\":0,\\\\\\\"blend_type_tex_blusher2\\\\\\\":0,\\\\\\\"makeup_blusher_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_blusher\\\\\\\":\\\\\\\"zhuangrong_sh.png\\\\\\\",\\\\\\\"makeup_intensity_blusher\\\\\\\":0.800000011920929,\\\\\\\"makeup_eyeBrow_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_brow\\\\\\\":\\\\\\\"brow.png\\\\\\\",\\\\\\\"brow_warp\\\\\\\":1.0,\\\\\\\"brow_warp_type\\\\\\\":3,\\\\\\\"makeup_intensity_eyeBrow\\\\\\\":0.699999988079071,\\\\\\\"makeup_eyelash_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_eyeLash\\\\\\\":\\\\\\\"eyeLash.png\\\\\\\",\\\\\\\"makeup_intensity_eyelash\\\\\\\":1.0,\\\\\\\"makeup_eyeLiner_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_eyeLiner\\\\\\\":\\\\\\\"eyeLiner.png\\\\\\\",\\\\\\\"makeup_intensity_eyeLiner\\\\\\\":1.0,\\\\\\\"blend_type_tex_eye\\\\\\\":0,\\\\\\\"blend_type_tex_eye2\\\\\\\":0,\\\\\\\"blend_type_tex_eye3\\\\\\\":1,\\\\\\\"blend_type_tex_eye4\\\\\\\":0,\\\\\\\"makeup_eye_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"makeup_eye_color2\\\\\\\":\[0.5882353186607361,0.3607843220233917,0.30588236451148989,1.0\],\\\\\\\"makeup_eye_color3\\\\\\\":\[0.9882352948188782,0.95686274766922,0.9372549057006836,1.0\],\\\\\\\"tex_eye\\\\\\\":\\\\\\\"eye.png\\\\\\\",\\\\\\\"tex_eye2\\\\\\\":\\\\\\\"eye2.png\\\\\\\",\\\\\\\"tex_eye3\\\\\\\":\\\\\\\"eye3.png\\\\\\\",\\\\\\\"makeup_intensity_eye\\\\\\\":1.0,\\\\\\\"makeup_highlight_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_highlight\\\\\\\":\\\\\\\"zhuangrong_gg.png\\\\\\\",\\\\\\\"makeup_intensity_highlight\\\\\\\":1.0,\\\\\\\"makeup_shadow_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_shadow\\\\\\\":\\\\\\\"zhuangrong_yy.png\\\\\\\",\\\\\\\"makeup_intensity_shadow\\\\\\\":1.0,\\\\\\\"makeup_lip_color\\\\\\\":\[0.501960813999176,0.10196078568696976,0.10196078568696976,1.0\],\\\\\\\"lip_type\\\\\\\":0,\\\\\\\"is_two_color\\\\\\\":0,\\\\\\\"makeup_intensity_lip\\\\\\\":1.0}\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"daisy\\\"}}\\n{\\\"id\\\":\\\"daisy\\\",\\\"category\\\":0,\\\"name\\\":\\\"Daisy\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_makeup_32/daisy.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_makeup_32/daisy.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":32,\\\"type_name\\\":\\\"fu_makeup\\\",\\\"view_order\\\":20,\\\"filter_type\\\":\\\"zhiganhui8\\\",\\\"asset_type\\\":\\\"FU_MAKEUP\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"daisy\\\",\\\"valid_till\\\":1655896006130,\\\"label\\\":\\\"new3\\\",\\\"category_name\\\":\\\"daisy\\\",\\\"asset_params\\\":\\\"{\\\\\\\"blend_type_tex_blusher\\\\\\\":0,\\\\\\\"blend_type_tex_blusher2\\\\\\\":0,\\\\\\\"makeup_blusher_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_blusher\\\\\\\":\\\\\\\"zhuangrong_sh.png\\\\\\\",\\\\\\\"makeup_intensity_blusher\\\\\\\":0.800000011920929,\\\\\\\"makeup_eyeBrow_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_brow\\\\\\\":\\\\\\\"brow.png\\\\\\\",\\\\\\\"brow_warp\\\\\\\":1.0,\\\\\\\"brow_warp_type\\\\\\\":3,\\\\\\\"makeup_intensity_eyeBrow\\\\\\\":0.699999988079071,\\\\\\\"makeup_eyelash_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_eyeLash\\\\\\\":\\\\\\\"eyeLash.png\\\\\\\",\\\\\\\"makeup_intensity_eyelash\\\\\\\":0.800000011920929,\\\\\\\"makeup_eyeLiner_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_eyeLiner\\\\\\\":\\\\\\\"eyeLiner.png\\\\\\\",\\\\\\\"makeup_intensity_eyeLiner\\\\\\\":0.699999988079071,\\\\\\\"blend_type_tex_eye\\\\\\\":0,\\\\\\\"blend_type_tex_eye2\\\\\\\":0,\\\\\\\"blend_type_tex_eye3\\\\\\\":1,\\\\\\\"blend_type_tex_eye4\\\\\\\":0,\\\\\\\"makeup_eye_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"makeup_eye_color2\\\\\\\":\[0.5882353186607361,0.3607843220233917,0.30588236451148989,1.0\],\\\\\\\"makeup_eye_color3\\\\\\\":\[1.0,1.0,1.0,1.0\],\\\\\\\"tex_eye\\\\\\\":\\\\\\\"eye.png\\\\\\\",\\\\\\\"tex_eye2\\\\\\\":\\\\\\\"eye2.png\\\\\\\",\\\\\\\"tex_eye3\\\\\\\":\\\\\\\"eye3.png\\\\\\\",\\\\\\\"makeup_intensity_eye\\\\\\\":1.0,\\\\\\\"makeup_highlight_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_highlight\\\\\\\":\\\\\\\"zhuangrong_gg.png\\\\\\\",\\\\\\\"makeup_intensity_highlight\\\\\\\":1.0,\\\\\\\"makeup_shadow_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_shadow\\\\\\\":\\\\\\\"zhuangrong_yy.png\\\\\\\",\\\\\\\"makeup_intensity_shadow\\\\\\\":0.6000000238418579,\\\\\\\"makeup_lip_color\\\\\\\":\[0.6509804129600525,0.3019607961177826,0.250980406999588,1.0\],\\\\\\\"lip_type\\\\\\\":0,\\\\\\\"is_two_color\\\\\\\":0,\\\\\\\"makeup_intensity_lip\\\\\\\":0.8999999761581421}\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"early_autumn\\\"}}\\n{\\\"id\\\":\\\"early_autumn\\\",\\\"category\\\":0,\\\"name\\\":\\\"Early
  Autumn\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_makeup_32/early_autumn.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_makeup_32/early_autumn.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":32,\\\"type_name\\\":\\\"fu_makeup\\\",\\\"view_order\\\":30,\\\"filter_type\\\":\\\"zhiganhui6\\\",\\\"asset_type\\\":\\\"FU_MAKEUP\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"early_autumn\\\",\\\"valid_till\\\":1651743369774,\\\"label\\\":\\\"latest\\\",\\\"category_name\\\":\\\"early_autumn\\\",\\\"asset_params\\\":\\\"{\\\\\\\"blend_type_tex_blusher\\\\\\\":0,\\\\\\\"blend_type_tex_blusher2\\\\\\\":0,\\\\\\\"makeup_blusher_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_blusher\\\\\\\":\\\\\\\"zhuangrong_sh.png\\\\\\\",\\\\\\\"makeup_intensity_blusher\\\\\\\":1.0,\\\\\\\"makeup_eyeBrow_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_brow\\\\\\\":\\\\\\\"brow.png\\\\\\\",\\\\\\\"brow_warp\\\\\\\":1.0,\\\\\\\"brow_warp_type\\\\\\\":3,\\\\\\\"makeup_intensity_eyeBrow\\\\\\\":0.699999988079071,\\\\\\\"makeup_eyelash_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_eyeLash\\\\\\\":\\\\\\\"eyeLash.png\\\\\\\",\\\\\\\"makeup_intensity_eyelash\\\\\\\":1.0,\\\\\\\"makeup_eyeLiner_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_eyeLiner\\\\\\\":\\\\\\\"eyeLiner.png\\\\\\\",\\\\\\\"makeup_intensity_eyeLiner\\\\\\\":1.0,\\\\\\\"blend_type_tex_eye\\\\\\\":0,\\\\\\\"blend_type_tex_eye2\\\\\\\":0,\\\\\\\"blend_type_tex_eye3\\\\\\\":1,\\\\\\\"blend_type_tex_eye4\\\\\\\":0,\\\\\\\"makeup_eye_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"makeup_eye_color2\\\\\\\":\[0.5882353186607361,0.3607843220233917,0.30588236451148989,1.0\],\\\\\\\"makeup_eye_color3\\\\\\\":\[0.9882352948188782,0.9647058844566345,0.9490196108818054,1.0\],\\\\\\\"tex_eye\\\\\\\":\\\\\\\"eye.png\\\\\\\",\\\\\\\"tex_eye2\\\\\\\":\\\\\\\"eye2.png\\\\\\\",\\\\\\\"tex_eye3\\\\\\\":\\\\\\\"eye3.png\\\\\\\",\\\\\\\"makeup_intensity_eye\\\\\\\":1.0,\\\\\\\"makeup_highlight_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_highlight\\\\\\\":\\\\\\\"zhuangrong_gg.png\\\\\\\",\\\\\\\"makeup_intensity_highlight\\\\\\\":0.800000011920929,\\\\\\\"makeup_shadow_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_shadow\\\\\\\":\\\\\\\"zhuangrong_yy.png\\\\\\\",\\\\\\\"makeup_intensity_shadow\\\\\\\":0.6000000238418579,\\\\\\\"makeup_lip_color\\\\\\\":\[0.7215686440467835,0.2705882489681244,0.18039216101169587,1.0\],\\\\\\\"lip_type\\\\\\\":0,\\\\\\\"is_two_color\\\\\\\":0,\\\\\\\"makeup_intensity_lip\\\\\\\":0.8999999761581421}\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"harbour_wind\\\"}}\\n{\\\"id\\\":\\\"harbour_wind\\\",\\\"category\\\":0,\\\"name\\\":\\\"Harbour
  Wind\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_makeup_32/harbour_wind.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_makeup_32/harbour_wind.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":32,\\\"type_name\\\":\\\"fu_makeup\\\",\\\"view_order\\\":40,\\\"filter_type\\\":\\\"ziran8\\\",\\\"asset_type\\\":\\\"FU_MAKEUP\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"harbour_wind\\\",\\\"valid_till\\\":1643615270301,\\\"label\\\":\\\"new\\\",\\\"category_name\\\":\\\"harbour_wind\\\",\\\"asset_params\\\":\\\"{\\\\\\\"blend_type_tex_blusher\\\\\\\":0,\\\\\\\"blend_type_tex_blusher2\\\\\\\":0,\\\\\\\"makeup_blusher_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_blusher\\\\\\\":\\\\\\\"zhuangrong_sh.png\\\\\\\",\\\\\\\"makeup_intensity_blusher\\\\\\\":1.0,\\\\\\\"makeup_eyeBrow_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_brow\\\\\\\":\\\\\\\"brow.png\\\\\\\",\\\\\\\"brow_warp\\\\\\\":1.0,\\\\\\\"brow_warp_type\\\\\\\":3,\\\\\\\"makeup_intensity_eyeBrow\\\\\\\":0.699999988079071,\\\\\\\"makeup_eyelash_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_eyeLash\\\\\\\":\\\\\\\"eyeLash.png\\\\\\\",\\\\\\\"makeup_intensity_eyelash\\\\\\\":0.800000011920929,\\\\\\\"makeup_eyeLiner_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_eyeLiner\\\\\\\":\\\\\\\"eyeLiner.png\\\\\\\",\\\\\\\"makeup_intensity_eyeLiner\\\\\\\":0.800000011920929,\\\\\\\"blend_type_tex_eye\\\\\\\":0,\\\\\\\"blend_type_tex_eye2\\\\\\\":0,\\\\\\\"blend_type_tex_eye3\\\\\\\":1,\\\\\\\"blend_type_tex_eye4\\\\\\\":0,\\\\\\\"makeup_eye_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"makeup_eye_color2\\\\\\\":\[0.5882353186607361,0.3607843220233917,0.30588236451148989,1.0\],\\\\\\\"makeup_eye_color3\\\\\\\":\[1.0,1.0,1.0,1.0\],\\\\\\\"tex_eye\\\\\\\":\\\\\\\"eye.png\\\\\\\",\\\\\\\"tex_eye2\\\\\\\":\\\\\\\"eye2.png\\\\\\\",\\\\\\\"tex_eye3\\\\\\\":\\\\\\\"eye3.png\\\\\\\",\\\\\\\"makeup_intensity_eye\\\\\\\":0.8999999761581421,\\\\\\\"makeup_highlight_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_highlight\\\\\\\":\\\\\\\"zhuangrong_gg.png\\\\\\\",\\\\\\\"makeup_intensity_highlight\\\\\\\":1.0,\\\\\\\"makeup_shadow_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_shadow\\\\\\\":\\\\\\\"zhuangrong_yy.png\\\\\\\",\\\\\\\"makeup_intensity_shadow\\\\\\\":0.800000011920929,\\\\\\\"makeup_lip_color\\\\\\\":\[0.5803921818733215,0.25882354378700259,0.20000000298023225,1.0\],\\\\\\\"lip_type\\\\\\\":0,\\\\\\\"is_two_color\\\\\\\":0,\\\\\\\"makeup_intensity_lip\\\\\\\":0.800000011920929}\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"red_maple\\\"}}\\n{\\\"id\\\":\\\"red_maple\\\",\\\"category\\\":0,\\\"name\\\":\\\"Red
  Maple\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_makeup_32/red_maple.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_makeup_32/red_maple.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":32,\\\"type_name\\\":\\\"fu_makeup\\\",\\\"view_order\\\":50,\\\"filter_type\\\":\\\"zhiganhui3\\\",\\\"asset_type\\\":\\\"FU_MAKEUP\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"red_maple\\\",\\\"valid_till\\\":1643615574052,\\\"label\\\":\\\"New\\\",\\\"category_name\\\":\\\"red_maple\\\",\\\"asset_params\\\":\\\"{\\\\\\\"blend_type_tex_blusher\\\\\\\":0,\\\\\\\"blend_type_tex_blusher2\\\\\\\":0,\\\\\\\"makeup_blusher_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_blusher\\\\\\\":\\\\\\\"zhuangrong_sh.png\\\\\\\",\\\\\\\"makeup_intensity_blusher\\\\\\\":1.0,\\\\\\\"makeup_eyeBrow_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_brow\\\\\\\":\\\\\\\"brow.png\\\\\\\",\\\\\\\"brow_warp\\\\\\\":1.0,\\\\\\\"brow_warp_type\\\\\\\":3,\\\\\\\"makeup_intensity_eyeBrow\\\\\\\":0.699999988079071,\\\\\\\"makeup_eyelash_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_eyeLash\\\\\\\":\\\\\\\"eyeLash.png\\\\\\\",\\\\\\\"makeup_intensity_eyelash\\\\\\\":0.699999988079071,\\\\\\\"makeup_eyeLiner_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_eyeLiner\\\\\\\":\\\\\\\"eyeLiner.png\\\\\\\",\\\\\\\"makeup_intensity_eyeLiner\\\\\\\":0.800000011920929,\\\\\\\"blend_type_tex_eye\\\\\\\":0,\\\\\\\"blend_type_tex_eye2\\\\\\\":0,\\\\\\\"blend_type_tex_eye3\\\\\\\":1,\\\\\\\"blend_type_tex_eye4\\\\\\\":0,\\\\\\\"makeup_eye_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"makeup_eye_color2\\\\\\\":\[0.5882353186607361,0.3607843220233917,0.30588236451148989,1.0\],\\\\\\\"makeup_eye_color3\\\\\\\":\[1.0,1.0,1.0,1.0\],\\\\\\\"tex_eye\\\\\\\":\\\\\\\"eye.png\\\\\\\",\\\\\\\"tex_eye2\\\\\\\":\\\\\\\"eye2.png\\\\\\\",\\\\\\\"tex_eye3\\\\\\\":\\\\\\\"eye3.png\\\\\\\",\\\\\\\"makeup_intensity_eye\\\\\\\":1.0,\\\\\\\"makeup_highlight_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_highlight\\\\\\\":\\\\\\\"zhuangrong_gg.png\\\\\\\",\\\\\\\"makeup_intensity_highlight\\\\\\\":1.0,\\\\\\\"makeup_shadow_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_shadow\\\\\\\":\\\\\\\"zhuangrong_yy.png\\\\\\\",\\\\\\\"makeup_intensity_shadow\\\\\\\":1.0,\\\\\\\"makeup_lip_color\\\\\\\":\[0.5803921818733215,0.250980406999588,0.21960784494876862,1.0\],\\\\\\\"lip_type\\\\\\\":1,\\\\\\\"is_two_color\\\\\\\":0,\\\\\\\"makeup_intensity_lip\\\\\\\":1.0}\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"age\\\"}}\\n{\\\"id\\\":\\\"age\\\",\\\"category\\\":0,\\\"name\\\":\\\"Age\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_makeup_32/age.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_makeup_32/age.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":32,\\\"type_name\\\":\\\"fu_makeup\\\",\\\"view_order\\\":60,\\\"filter_type\\\":\\\"zhiganhui1\\\",\\\"asset_type\\\":\\\"FU_MAKEUP\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"age\\\",\\\"valid_till\\\":1643615485352,\\\"label\\\":\\\"new\\\",\\\"category_name\\\":\\\"age\\\",\\\"asset_params\\\":\\\"{\\\\\\\"blend_type_tex_blusher\\\\\\\":0,\\\\\\\"blend_type_tex_blusher2\\\\\\\":0,\\\\\\\"makeup_blusher_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_blusher\\\\\\\":\\\\\\\"zhuangrong_sh.png\\\\\\\",\\\\\\\"makeup_intensity_blusher\\\\\\\":0.8999999761581421,\\\\\\\"makeup_eyeLiner_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_eyeLiner\\\\\\\":\\\\\\\"eyeLiner.png\\\\\\\",\\\\\\\"makeup_intensity_eyeLiner\\\\\\\":1.0,\\\\\\\"makeup_eyelash_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_eyeLash\\\\\\\":\\\\\\\"eyeLash.png\\\\\\\",\\\\\\\"makeup_intensity_eyelash\\\\\\\":0.699999988079071,\\\\\\\"makeup_eyeBrow_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_brow\\\\\\\":\\\\\\\"brow.png\\\\\\\",\\\\\\\"brow_warp\\\\\\\":1.0,\\\\\\\"brow_warp_type\\\\\\\":3,\\\\\\\"makeup_intensity_eyeBrow\\\\\\\":0.699999988079071,\\\\\\\"blend_type_tex_eye\\\\\\\":0,\\\\\\\"blend_type_tex_eye2\\\\\\\":0,\\\\\\\"blend_type_tex_eye3\\\\\\\":1,\\\\\\\"blend_type_tex_eye4\\\\\\\":0,\\\\\\\"makeup_eye_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"makeup_eye_color2\\\\\\\":\[0.5882353186607361,0.3607843220233917,0.30588236451148989,1.0\],\\\\\\\"makeup_eye_color3\\\\\\\":\[1.0,1.0,1.0,1.0\],\\\\\\\"tex_eye\\\\\\\":\\\\\\\"eye.png\\\\\\\",\\\\\\\"tex_eye2\\\\\\\":\\\\\\\"eye2.png\\\\\\\",\\\\\\\"tex_eye3\\\\\\\":\\\\\\\"eye3.png\\\\\\\",\\\\\\\"makeup_intensity_eye\\\\\\\":1.0,\\\\\\\"makeup_highlight_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_highlight\\\\\\\":\\\\\\\"zhuangrong_gg.png\\\\\\\",\\\\\\\"makeup_intensity_highlight\\\\\\\":1.0,\\\\\\\"makeup_shadow_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_shadow\\\\\\\":\\\\\\\"zhuangrong_yy.png\\\\\\\",\\\\\\\"makeup_intensity_shadow\\\\\\\":0.699999988079071,\\\\\\\"makeup_lip_color\\\\\\\":\[0.6509804129600525,0.21176470816135407,0.29019609093666079,1.0\],\\\\\\\"lip_type\\\\\\\":0,\\\\\\\"is_two_color\\\\\\\":0,\\\\\\\"makeup_intensity_lip\\\\\\\":0.800000011920929}\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"neighbor_girl\\\"}}\\n{\\\"id\\\":\\\"neighbor_girl\\\",\\\"category\\\":0,\\\"name\\\":\\\"Neighbour
  Girl\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_makeup_32/neighbor_girl.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_makeup_32/neighbor_girl.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":32,\\\"type_name\\\":\\\"fu_makeup\\\",\\\"view_order\\\":70,\\\"filter_type\\\":\\\"ziran2\\\",\\\"asset_type\\\":\\\"FU_MAKEUP\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"neighbor_girl\\\",\\\"valid_till\\\":1643615500300,\\\"label\\\":\\\"new\\\",\\\"category_name\\\":\\\"neighbor_girl\\\",\\\"asset_params\\\":\\\"{\\\\\\\"blend_type_tex_blusher\\\\\\\":0,\\\\\\\"blend_type_tex_blusher2\\\\\\\":0,\\\\\\\"makeup_blusher_color\\\\\\\":\[0.89,0.26,0.28,1.0\],\\\\\\\"tex_blusher\\\\\\\":\\\\\\\"mu_style_blush_01.bundle\\\\\\\",\\\\\\\"makeup_intensity_blusher\\\\\\\":1.0,\\\\\\\"makeup_eyeBrow_color\\\\\\\":\[0.28,0.16,0.08,1.0\],\\\\\\\"tex_brow\\\\\\\":\\\\\\\"mu_style_eyebrow_01.bundle\\\\\\\",\\\\\\\"brow_warp\\\\\\\":1.0,\\\\\\\"brow_warp_type\\\\\\\":1,\\\\\\\"makeup_intensity_eyeBrow\\\\\\\":0.20000000298023225,\\\\\\\"makeup_eyelash_color\\\\\\\":\[0.28,0.16,0.08,1.0\],\\\\\\\"tex_eyeLash\\\\\\\":\\\\\\\"mu_style_eyelash_01.bundle\\\\\\\",\\\\\\\"makeup_intensity_eyelash\\\\\\\":0.699999988079071,\\\\\\\"makeup_eyeLiner_color\\\\\\\":\[0.28,0.16,0.08,1.0\],\\\\\\\"tex_eyeLiner\\\\\\\":\\\\\\\"mu_style_eyeliner_06.bundle\\\\\\\",\\\\\\\"makeup_intensity_eyeLiner\\\\\\\":0.699999988079071,\\\\\\\"blend_type_tex_eye\\\\\\\":0,\\\\\\\"blend_type_tex_eye2\\\\\\\":0,\\\\\\\"blend_type_tex_eye3\\\\\\\":0,\\\\\\\"blend_type_tex_eye4\\\\\\\":0,\\\\\\\"makeup_eye_color\\\\\\\":\[1.0,0.72,0.36,1.0\],\\\\\\\"makeup_eye_color2\\\\\\\":\[0.93,0.45,0.25,1.0\],\\\\\\\"tex_eye\\\\\\\":\\\\\\\"mu_style_eyeshadow_02.bundle\\\\\\\",\\\\\\\"makeup_intensity_eye\\\\\\\":0.8999999761581421,\\\\\\\"makeup_foundation_color\\\\\\\":\[0.91,0.81,0.74,1.0\],\\\\\\\"tex_foundation\\\\\\\":\\\\\\\"mu_style_foundation_01.bundle\\\\\\\",\\\\\\\"makeup_intensity_foundation\\\\\\\":1.0,\\\\\\\"makeup_lip_color\\\\\\\":\[0.84,0.26,0.16,1.0\],\\\\\\\"lip_type\\\\\\\":0,\\\\\\\"is_two_color\\\\\\\":0,\\\\\\\"makeup_intensity_lip\\\\\\\":0.6000000238418579}\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"warm_winter\\\"}}\\n{\\\"id\\\":\\\"warm_winter\\\",\\\"category\\\":0,\\\"name\\\":\\\"Warm
  Winter\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_makeup_32/warm_winter.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_makeup_32/warm_winter.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":32,\\\"type_name\\\":\\\"fu_makeup\\\",\\\"view_order\\\":80,\\\"filter_type\\\":\\\"zhiganhui2\\\",\\\"asset_type\\\":\\\"FU_MAKEUP\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"warm_winter\\\",\\\"category_name\\\":\\\"warm_winter\\\",\\\"asset_params\\\":\\\"{\\\\\\\"blend_type_tex_blusher\\\\\\\":0,\\\\\\\"blend_type_tex_blusher2\\\\\\\":1,\\\\\\\"makeup_blusher_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"makeup_blusher_color2\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_blusher\\\\\\\":\\\\\\\"zhuangrong_sh.png\\\\\\\",\\\\\\\"tex_blusher2\\\\\\\":\\\\\\\"zhuangrong_sh2.png\\\\\\\",\\\\\\\"makeup_intensity_blusher\\\\\\\":0.699999988079071,\\\\\\\"makeup_eyeBrow_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_brow\\\\\\\":\\\\\\\"brow.png\\\\\\\",\\\\\\\"brow_warp\\\\\\\":1.0,\\\\\\\"brow_warp_type\\\\\\\":3,\\\\\\\"makeup_intensity_eyeBrow\\\\\\\":0.699999988079071,\\\\\\\"makeup_eyelash_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_eyeLash\\\\\\\":\\\\\\\"eyeLash.png\\\\\\\",\\\\\\\"makeup_intensity_eyelash\\\\\\\":0.8999999761581421,\\\\\\\"makeup_eyeLiner_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_eyeLiner\\\\\\\":\\\\\\\"eyeLiner.png\\\\\\\",\\\\\\\"makeup_intensity_eyeLiner\\\\\\\":0.800000011920929,\\\\\\\"blend_type_tex_eye\\\\\\\":0,\\\\\\\"blend_type_tex_eye2\\\\\\\":0,\\\\\\\"blend_type_tex_eye3\\\\\\\":1,\\\\\\\"blend_type_tex_eye4\\\\\\\":0,\\\\\\\"makeup_eye_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"makeup_eye_color2\\\\\\\":\[0.5882353186607361,0.3607843220233917,0.30588236451148989,1.0\],\\\\\\\"makeup_eye_color3\\\\\\\":\[1.0,1.0,1.0,1.0\],\\\\\\\"tex_eye\\\\\\\":\\\\\\\"eye.png\\\\\\\",\\\\\\\"tex_eye2\\\\\\\":\\\\\\\"eye2.png\\\\\\\",\\\\\\\"tex_eye3\\\\\\\":\\\\\\\"eye3.png\\\\\\\",\\\\\\\"makeup_intensity_eye\\\\\\\":1.0,\\\\\\\"makeup_highlight_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_highlight\\\\\\\":\\\\\\\"zhuangrong_gg.png\\\\\\\",\\\\\\\"makeup_intensity_highlight\\\\\\\":1.0,\\\\\\\"makeup_shadow_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_shadow\\\\\\\":\\\\\\\"zhuangrong_yy.png\\\\\\\",\\\\\\\"makeup_intensity_shadow\\\\\\\":1.0,\\\\\\\"makeup_lip_color\\\\\\\":\[0.5803921818733215,0.20000000298023225,0.10196078568696976,1.0\],\\\\\\\"lip_type\\\\\\\":0,\\\\\\\"is_two_color\\\\\\\":0,\\\\\\\"makeup_intensity_lip\\\\\\\":0.800000011920929}\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"accident\\\"}}\\n{\\\"id\\\":\\\"accident\\\",\\\"category\\\":0,\\\"name\\\":\\\"Accident\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_makeup_32/accident.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_makeup_32/accident.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":32,\\\"type_name\\\":\\\"fu_makeup\\\",\\\"view_order\\\":90,\\\"filter_type\\\":\\\"ziran2\\\",\\\"asset_type\\\":\\\"FU_MAKEUP\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"accident\\\",\\\"valid_till\\\":1650951595104,\\\"label\\\":\\\"new\\\",\\\"category_name\\\":\\\"accident\\\",\\\"asset_params\\\":\\\"{\\\\\\\"blend_type_tex_blusher\\\\\\\":0,\\\\\\\"blend_type_tex_blusher2\\\\\\\":0,\\\\\\\"makeup_blusher_color\\\\\\\":\[0.89,0.26,0.40,1.0\],\\\\\\\"tex_blusher\\\\\\\":\\\\\\\"mu_style_blush_02.bundle\\\\\\\",\\\\\\\"makeup_intensity_blusher\\\\\\\":1.0,\\\\\\\"makeup_eyeBrow_color\\\\\\\":\[0.21,0.05,0.02,1.0\],\\\\\\\"tex_brow\\\\\\\":\\\\\\\"mu_style_eyebrow_01.bundle\\\\\\\",\\\\\\\"brow_warp\\\\\\\":1.0,\\\\\\\"brow_warp_type\\\\\\\":0,\\\\\\\"makeup_intensity_eyeBrow\\\\\\\":0.5,\\\\\\\"makeup_eyelash_color\\\\\\\":\[0.21,0.05,0.02,1.0\],\\\\\\\"tex_eyeLash\\\\\\\":\\\\\\\"mu_style_eyelash_06.bundle\\\\\\\",\\\\\\\"makeup_intensity_eyelash\\\\\\\":0.6000000238418579,\\\\\\\"makeup_eyeLiner_color\\\\\\\":\[0.21,0.05,0.02,1.0\],\\\\\\\"tex_eyeLiner\\\\\\\":\\\\\\\"mu_style_eyeliner_05.bundle\\\\\\\",\\\\\\\"makeup_intensity_eyeLiner\\\\\\\":0.4000000059604645,\\\\\\\"blend_type_tex_eye\\\\\\\":0,\\\\\\\"blend_type_tex_eye2\\\\\\\":1,\\\\\\\"blend_type_tex_eye3\\\\\\\":0,\\\\\\\"blend_type_tex_eye4\\\\\\\":0,\\\\\\\"makeup_eye_color\\\\\\\":\[0.82,0.15,0.24,1.0\],\\\\\\\"makeup_eye_color2\\\\\\\":\[1.0,0.92,0.74,1.0\],\\\\\\\"tex_eye\\\\\\\":\\\\\\\"mu_style_eyeshadow_04.bundle\\\\\\\",\\\\\\\"makeup_intensity_eye\\\\\\\":0.800000011920929,\\\\\\\"makeup_foundation_color\\\\\\\":\[0.87,0.74,0.69,1.0\],\\\\\\\"tex_foundation\\\\\\\":\\\\\\\"mu_style_foundation_01.bundle\\\\\\\",\\\\\\\"makeup_intensity_foundation\\\\\\\":1.0,\\\\\\\"makeup_highlight_color\\\\\\\":\[0.97,0.95,0.95,1.0\],\\\\\\\"tex_highlight\\\\\\\":\\\\\\\"mu_style_highlight_02.bundle\\\\\\\",\\\\\\\"makeup_intensity_highlight\\\\\\\":1.0,\\\\\\\"makeup_shadow_color\\\\\\\":\[0.40,0.12,0.18,1.0\],\\\\\\\"tex_shadow\\\\\\\":\\\\\\\"mu_style_contour_01.bundle\\\\\\\",\\\\\\\"makeup_intensity_shadow\\\\\\\":1.0,\\\\\\\"makeup_lip_color\\\\\\\":\[0.6,0.11,0.23,1.0\],\\\\\\\"lip_type\\\\\\\":0,\\\\\\\"is_two_color\\\\\\\":0,\\\\\\\"makeup_intensity_lip\\\\\\\":0.8600000143051148}\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"paper_cranes\\\"}}\\n{\\\"id\\\":\\\"paper_cranes\\\",\\\"category\\\":0,\\\"name\\\":\\\"Paper
  Cranes\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_makeup_32/paper_cranes.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_makeup_32/paper_cranes.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":32,\\\"type_name\\\":\\\"fu_makeup\\\",\\\"view_order\\\":100,\\\"filter_type\\\":\\\"zhiganhui2\\\",\\\"asset_type\\\":\\\"FU_MAKEUP\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"paper_cranes\\\",\\\"valid_till\\\":1650959511916,\\\"label\\\":\\\"new\\\",\\\"category_name\\\":\\\"paper_cranes\\\",\\\"asset_params\\\":\\\"{\\\\\\\"blend_type_tex_blusher\\\\\\\":0,\\\\\\\"blend_type_tex_blusher2\\\\\\\":0,\\\\\\\"makeup_blusher_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_blusher\\\\\\\":\\\\\\\"zhuangrong_sh.png\\\\\\\",\\\\\\\"makeup_intensity_blusher\\\\\\\":1.0,\\\\\\\"makeup_eyeBrow_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_brow\\\\\\\":\\\\\\\"brow.png\\\\\\\",\\\\\\\"brow_warp\\\\\\\":1.0,\\\\\\\"brow_warp_type\\\\\\\":5,\\\\\\\"makeup_intensity_eyeBrow\\\\\\\":0.699999988079071,\\\\\\\"makeup_eyelash_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_eyeLash\\\\\\\":\\\\\\\"eyeLash.png\\\\\\\",\\\\\\\"makeup_intensity_eyelash\\\\\\\":0.8999999761581421,\\\\\\\"makeup_eyeLiner_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_eyeLiner\\\\\\\":\\\\\\\"eyeLiner.png\\\\\\\",\\\\\\\"makeup_intensity_eyeLiner\\\\\\\":0.8999999761581421,\\\\\\\"blend_type_tex_eye\\\\\\\":0,\\\\\\\"blend_type_tex_eye2\\\\\\\":0,\\\\\\\"blend_type_tex_eye3\\\\\\\":1,\\\\\\\"blend_type_tex_eye4\\\\\\\":0,\\\\\\\"makeup_eye_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"makeup_eye_color2\\\\\\\":\[0.5882353186607361,0.3607843220233917,0.30588236451148989,1.0\],\\\\\\\"makeup_eye_color3\\\\\\\":\[1.0,1.0,1.0,1.0\],\\\\\\\"tex_eye\\\\\\\":\\\\\\\"eye.png\\\\\\\",\\\\\\\"tex_eye2\\\\\\\":\\\\\\\"eye2.png\\\\\\\",\\\\\\\"tex_eye3\\\\\\\":\\\\\\\"eye3.png\\\\\\\",\\\\\\\"makeup_intensity_eye\\\\\\\":0.8999999761581421,\\\\\\\"makeup_highlight_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_highlight\\\\\\\":\\\\\\\"zhuangrong_gg.png\\\\\\\",\\\\\\\"makeup_intensity_highlight\\\\\\\":1.0,\\\\\\\"makeup_shadow_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_shadow\\\\\\\":\\\\\\\"zhuangrong_yy.png\\\\\\\",\\\\\\\"makeup_intensity_shadow\\\\\\\":1.0,\\\\\\\"makeup_lip_color\\\\\\\":\[0.5490196347236633,0.12156862765550614,0.10196078568696976,1.0\],\\\\\\\"lip_type\\\\\\\":0,\\\\\\\"is_two_color\\\\\\\":0,\\\\\\\"makeup_intensity_lip\\\\\\\":0.8999999761581421}\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"mermaid\\\"}}\\n{\\\"id\\\":\\\"mermaid\\\",\\\"category\\\":0,\\\"name\\\":\\\"Mermaid\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_makeup_32/mermaid.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_makeup_32/mermaid.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":32,\\\"type_name\\\":\\\"fu_makeup\\\",\\\"view_order\\\":110,\\\"filter_type\\\":\\\"zhiganhui1\\\",\\\"asset_type\\\":\\\"FU_MAKEUP\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"mermaid\\\",\\\"category_name\\\":\\\"mermaid\\\",\\\"asset_params\\\":\\\"{\\\\\\\"blend_type_tex_blusher\\\\\\\":0,\\\\\\\"blend_type_tex_blusher2\\\\\\\":1,\\\\\\\"makeup_blusher_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"makeup_blusher_color2\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_blusher\\\\\\\":\\\\\\\"zhuangrong_sh.png\\\\\\\",\\\\\\\"tex_blusher2\\\\\\\":\\\\\\\"zhuangrong_sh2.png\\\\\\\",\\\\\\\"makeup_intensity_blusher\\\\\\\":1.0,\\\\\\\"makeup_eyeBrow_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_brow\\\\\\\":\\\\\\\"brow.png\\\\\\\",\\\\\\\"brow_warp\\\\\\\":1.0,\\\\\\\"brow_warp_type\\\\\\\":5,\\\\\\\"makeup_intensity_eyeBrow\\\\\\\":0.699999988079071,\\\\\\\"makeup_eyelash_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_eyeLash\\\\\\\":\\\\\\\"eyeLash.png\\\\\\\",\\\\\\\"makeup_intensity_eyelash\\\\\\\":1.0,\\\\\\\"makeup_eyeLiner_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_eyeLiner\\\\\\\":\\\\\\\"eyeLiner.png\\\\\\\",\\\\\\\"makeup_intensity_eyeLiner\\\\\\\":1.0,\\\\\\\"blend_type_tex_eye\\\\\\\":0,\\\\\\\"blend_type_tex_eye2\\\\\\\":0,\\\\\\\"blend_type_tex_eye3\\\\\\\":1,\\\\\\\"blend_type_tex_eye4\\\\\\\":0,\\\\\\\"makeup_eye_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"makeup_eye_color2\\\\\\\":\[0.5882353186607361,0.3607843220233917,0.30588236451148989,1.0\],\\\\\\\"makeup_eye_color3\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_eye\\\\\\\":\\\\\\\"eye.png\\\\\\\",\\\\\\\"tex_eye2\\\\\\\":\\\\\\\"eye2.png\\\\\\\",\\\\\\\"tex_eye3\\\\\\\":\\\\\\\"eye3.png\\\\\\\",\\\\\\\"makeup_intensity_eye\\\\\\\":1.0,\\\\\\\"makeup_highlight_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_highlight\\\\\\\":\\\\\\\"zhuangrong_gg.png\\\\\\\",\\\\\\\"makeup_intensity_highlight\\\\\\\":1.0,\\\\\\\"makeup_shadow_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_shadow\\\\\\\":\\\\\\\"zhuangrong_yy.png\\\\\\\",\\\\\\\"makeup_intensity_shadow\\\\\\\":0.800000011920929,\\\\\\\"makeup_lip_color\\\\\\\":\[0.6000000238418579,0.239215686917305,0.27843138575553896,1.0\],\\\\\\\"lip_type\\\\\\\":1,\\\\\\\"is_two_color\\\\\\\":0,\\\\\\\"makeup_intensity_lip\\\\\\\":0.8999999761581421}\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"rose\\\"}}\\n{\\\"id\\\":\\\"rose\\\",\\\"category\\\":0,\\\"name\\\":\\\"Rose\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_makeup_32/rose.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_makeup_32/rose.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":32,\\\"type_name\\\":\\\"fu_makeup\\\",\\\"view_order\\\":120,\\\"filter_type\\\":\\\"zhiganhui2\\\",\\\"asset_type\\\":\\\"FU_MAKEUP\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"rose\\\",\\\"category_name\\\":\\\"rose\\\",\\\"asset_params\\\":\\\"{\\\\\\\"blend_type_tex_blusher\\\\\\\":1,\\\\\\\"blend_type_tex_blusher2\\\\\\\":0,\\\\\\\"makeup_blusher_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_blusher\\\\\\\":\\\\\\\"zhuangrong_sh.png\\\\\\\",\\\\\\\"makeup_intensity_blusher\\\\\\\":1.0,\\\\\\\"makeup_eyeBrow_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_brow\\\\\\\":\\\\\\\"brow.png\\\\\\\",\\\\\\\"brow_warp\\\\\\\":1.0,\\\\\\\"brow_warp_type\\\\\\\":3,\\\\\\\"makeup_intensity_eyeBrow\\\\\\\":0.699999988079071,\\\\\\\"makeup_eyelash_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_eyeLash\\\\\\\":\\\\\\\"eyeLash.png\\\\\\\",\\\\\\\"makeup_intensity_eyelash\\\\\\\":1.0,\\\\\\\"makeup_eyeLiner_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_eyeLiner\\\\\\\":\\\\\\\"eyeLiner.png\\\\\\\",\\\\\\\"makeup_intensity_eyeLiner\\\\\\\":1.0,\\\\\\\"blend_type_tex_eye\\\\\\\":0,\\\\\\\"blend_type_tex_eye2\\\\\\\":0,\\\\\\\"blend_type_tex_eye3\\\\\\\":1,\\\\\\\"blend_type_tex_eye4\\\\\\\":0,\\\\\\\"makeup_eye_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"makeup_eye_color2\\\\\\\":\[0.5882353186607361,0.3607843220233917,0.30588236451148989,1.0\],\\\\\\\"makeup_eye_color3\\\\\\\":\[1.0,1.0,1.0,1.0\],\\\\\\\"tex_eye\\\\\\\":\\\\\\\"eye.png\\\\\\\",\\\\\\\"tex_eye2\\\\\\\":\\\\\\\"eye2.png\\\\\\\",\\\\\\\"tex_eye3\\\\\\\":\\\\\\\"eye3.png\\\\\\\",\\\\\\\"makeup_intensity_eye\\\\\\\":1.0,\\\\\\\"makeup_highlight_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_highlight\\\\\\\":\\\\\\\"zhuangrong_gg.png\\\\\\\",\\\\\\\"makeup_intensity_highlight\\\\\\\":1.0,\\\\\\\"makeup_shadow_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_shadow\\\\\\\":\\\\\\\"zhuangrong_yy.png\\\\\\\",\\\\\\\"makeup_intensity_shadow\\\\\\\":1.0,\\\\\\\"makeup_lip_color\\\\\\\":\[0.38823530077934267,0.18039216101169587,0.12941177189350129,1.0\],\\\\\\\"lip_type\\\\\\\":0,\\\\\\\"is_two_color\\\\\\\":0,\\\\\\\"makeup_intensity_lip\\\\\\\":1.0}\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"girl\\\"}}\\n{\\\"id\\\":\\\"girl\\\",\\\"category\\\":0,\\\"name\\\":\\\"Southern
  GIrl\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_makeup_32/girl.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_makeup_32/girl.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":32,\\\"type_name\\\":\\\"fu_makeup\\\",\\\"view_order\\\":130,\\\"filter_type\\\":\\\"zhiganhui4\\\",\\\"asset_type\\\":\\\"FU_MAKEUP\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"girl\\\",\\\"category_name\\\":\\\"girl\\\",\\\"asset_params\\\":\\\"{\\\\\\\"blend_type_tex_blusher\\\\\\\":0,\\\\\\\"blend_type_tex_blusher2\\\\\\\":0,\\\\\\\"makeup_blusher_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_blusher\\\\\\\":\\\\\\\"zhuangrong_sh.png\\\\\\\",\\\\\\\"makeup_intensity_blusher\\\\\\\":0.800000011920929,\\\\\\\"makeup_eyeBrow_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_brow\\\\\\\":\\\\\\\"brow.png\\\\\\\",\\\\\\\"brow_warp\\\\\\\":1.0,\\\\\\\"brow_warp_type\\\\\\\":3,\\\\\\\"makeup_intensity_eyeBrow\\\\\\\":0.5,\\\\\\\"makeup_eyelash_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_eyeLash\\\\\\\":\\\\\\\"eyeLash.png\\\\\\\",\\\\\\\"makeup_intensity_eyelash\\\\\\\":1.0,\\\\\\\"makeup_eyeLiner_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_eyeLiner\\\\\\\":\\\\\\\"eyeLiner.png\\\\\\\",\\\\\\\"makeup_intensity_eyeLiner\\\\\\\":0.949999988079071,\\\\\\\"blend_type_tex_eye\\\\\\\":0,\\\\\\\"blend_type_tex_eye2\\\\\\\":0,\\\\\\\"blend_type_tex_eye3\\\\\\\":1,\\\\\\\"blend_type_tex_eye4\\\\\\\":0,\\\\\\\"makeup_eye_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"makeup_eye_color2\\\\\\\":\[0.5882353186607361,0.3607843220233917,0.30588236451148989,1.0\],\\\\\\\"makeup_eye_color3\\\\\\\":\[1.0,1.0,1.0,1.0\],\\\\\\\"tex_eye\\\\\\\":\\\\\\\"eye.png\\\\\\\",\\\\\\\"tex_eye2\\\\\\\":\\\\\\\"eye2.png\\\\\\\",\\\\\\\"tex_eye3\\\\\\\":\\\\\\\"eye3.png\\\\\\\",\\\\\\\"makeup_intensity_eye\\\\\\\":0.699999988079071,\\\\\\\"makeup_highlight_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_highlight\\\\\\\":\\\\\\\"zhuangrong_gg.png\\\\\\\",\\\\\\\"makeup_intensity_highlight\\\\\\\":1.0,\\\\\\\"makeup_shadow_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_shadow\\\\\\\":\\\\\\\"zhuangrong_yy.png\\\\\\\",\\\\\\\"makeup_intensity_shadow\\\\\\\":0.699999988079071,\\\\\\\"makeup_lip_color\\\\\\\":\[0.5411764979362488,0.20000000298023225,0.20000000298023225,1.0\],\\\\\\\"lip_type\\\\\\\":1,\\\\\\\"is_two_color\\\\\\\":0,\\\\\\\"makeup_intensity_lip\\\\\\\":1.0}\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"sweet\\\"}}\\n{\\\"id\\\":\\\"sweet\\\",\\\"category\\\":0,\\\"name\\\":\\\"Sweet
  Bun\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_makeup_32/sweet.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_makeup_32/sweet.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":32,\\\"type_name\\\":\\\"fu_makeup\\\",\\\"view_order\\\":140,\\\"filter_type\\\":\\\"ziran2\\\",\\\"asset_type\\\":\\\"FU_MAKEUP\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"sweet\\\",\\\"category_name\\\":\\\"sweet\\\",\\\"asset_params\\\":\\\"{\\\\\\\"blend_type_tex_blusher\\\\\\\":0,\\\\\\\"blend_type_tex_blusher2\\\\\\\":0,\\\\\\\"makeup_blusher_color\\\\\\\":\[0.93,0.35,0.43,1.0\],\\\\\\\"tex_blusher\\\\\\\":\\\\\\\"mu_style_blush_04.bundle\\\\\\\",\\\\\\\"makeup_intensity_blusher\\\\\\\":1.0,\\\\\\\"makeup_eyeBrow_color\\\\\\\":\[0.33,0.09,0.18,1.0\],\\\\\\\"tex_brow\\\\\\\":\\\\\\\"mu_style_eyebrow_01.bundle\\\\\\\",\\\\\\\"brow_warp\\\\\\\":1.0,\\\\\\\"brow_warp_type\\\\\\\":6,\\\\\\\"makeup_intensity_eyeBrow\\\\\\\":0.5,\\\\\\\"makeup_eyeLiner_color\\\\\\\":\[0.33,0.09,0.18,1.0\],\\\\\\\"tex_eyeLiner\\\\\\\":\\\\\\\"mu_style_eyeliner_02.bundle\\\\\\\",\\\\\\\"makeup_intensity_eyeLiner\\\\\\\":0.5,\\\\\\\"makeup_eyelash_color\\\\\\\":\[0.33,0.09,0.18,1.0\],\\\\\\\"tex_eyeLash\\\\\\\":\\\\\\\"mu_style_eyelash_02.bundle\\\\\\\",\\\\\\\"makeup_intensity_eyelash\\\\\\\":0.5,\\\\\\\"blend_type_tex_eye\\\\\\\":0,\\\\\\\"blend_type_tex_eye2\\\\\\\":0,\\\\\\\"blend_type_tex_eye3\\\\\\\":0,\\\\\\\"blend_type_tex_eye4\\\\\\\":0,\\\\\\\"makeup_eye_color\\\\\\\":\[1.0,0.43,0.44,1.0\],\\\\\\\"tex_eye\\\\\\\":\\\\\\\"mu_style_eyeshadow_01.bundle\\\\\\\",\\\\\\\"makeup_intensity_eye\\\\\\\":0.699999988079071,\\\\\\\"makeup_foundation_color\\\\\\\":\[0.87,0.74,0.69,1.0\],\\\\\\\"tex_foundation\\\\\\\":\\\\\\\"mu_style_foundation_01.bundle\\\\\\\",\\\\\\\"makeup_intensity_foundation\\\\\\\":1.0,\\\\\\\"makeup_highlight_color\\\\\\\":\[1.0,0.96,0.93,1.0\],\\\\\\\"tex_highlight\\\\\\\":\\\\\\\"mu_style_highlight_01.bundle\\\\\\\",\\\\\\\"makeup_intensity_highlight\\\\\\\":1.0,\\\\\\\"makeup_shadow_color\\\\\\\":\[0.41,0.22,0.15,1.0\],\\\\\\\"tex_shadow\\\\\\\":\\\\\\\"mu_style_contour_01.bundle\\\\\\\",\\\\\\\"makeup_intensity_shadow\\\\\\\":1.0,\\\\\\\"makeup_lip_color\\\\\\\":\[0.84,0.16,0.27,1.0\],\\\\\\\"lip_type\\\\\\\":0,\\\\\\\"is_two_color\\\\\\\":0,\\\\\\\"makeup_intensity_lip\\\\\\\":0.5}\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"charming\\\"}}\\n{\\\"id\\\":\\\"charming\\\",\\\"category\\\":0,\\\"name\\\":\\\"Charming\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_makeup_32/charming.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_makeup_32/charming.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":32,\\\"type_name\\\":\\\"fu_makeup\\\",\\\"view_order\\\":150,\\\"filter_type\\\":\\\"ziran2\\\",\\\"asset_type\\\":\\\"FU_MAKEUP\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"charming\\\",\\\"category_name\\\":\\\"charming\\\",\\\"asset_params\\\":\\\"{\\\\\\\"blend_type_tex_blusher\\\\\\\":0,\\\\\\\"blend_type_tex_blusher2\\\\\\\":0,\\\\\\\"makeup_blusher_color\\\\\\\":\[1.0,0.39,0.32,1.0\],\\\\\\\"tex_blusher\\\\\\\":\\\\\\\"mu_style_blush_03.bundle\\\\\\\",\\\\\\\"makeup_intensity_blusher\\\\\\\":1.0,\\\\\\\"makeup_eyeBrow_color\\\\\\\":\[0.28,0.16,0.08,1.0\],\\\\\\\"tex_brow\\\\\\\":\\\\\\\"mu_style_eyebrow_01.bundle\\\\\\\",\\\\\\\"brow_warp\\\\\\\":1.0,\\\\\\\"brow_warp_type\\\\\\\":3,\\\\\\\"makeup_intensity_eyeBrow\\\\\\\":0.6000000238418579,\\\\\\\"makeup_eyelash_color\\\\\\\":\[0.28,0.16,0.08,1.0\],\\\\\\\"tex_eyeLash\\\\\\\":\\\\\\\"mu_style_eyelash_03.bundle\\\\\\\",\\\\\\\"makeup_intensity_eyelash\\\\\\\":0.6000000238418579,\\\\\\\"makeup_eyeLiner_color\\\\\\\":\[0.28,0.16,0.08,1.0\],\\\\\\\"tex_eyeLiner\\\\\\\":\\\\\\\"mu_style_eyeliner_03.bundle\\\\\\\",\\\\\\\"makeup_intensity_eyeLiner\\\\\\\":0.6000000238418579,\\\\\\\"blend_type_tex_eye\\\\\\\":0,\\\\\\\"blend_type_tex_eye2\\\\\\\":0,\\\\\\\"blend_type_tex_eye3\\\\\\\":0,\\\\\\\"blend_type_tex_eye4\\\\\\\":0,\\\\\\\"makeup_eye_color\\\\\\\":\[0.89,0.61,0.41,1.0\],\\\\\\\"makeup_eye_color2\\\\\\\":\[0.86,0.26,0.07,1.0\],\\\\\\\"tex_eye\\\\\\\":\\\\\\\"mu_style_eyeshadow_03.bundle\\\\\\\",\\\\\\\"makeup_intensity_eye\\\\\\\":0.699999988079071,\\\\\\\"makeup_foundation_color\\\\\\\":\[0.80,0.74,0.65,1.0\],\\\\\\\"tex_foundation\\\\\\\":\\\\\\\"mu_style_foundation_01.bundle\\\\\\\",\\\\\\\"makeup_intensity_foundation\\\\\\\":1.0,\\\\\\\"makeup_highlight_color\\\\\\\":\[0.99,0.98,0.95,1.0\],\\\\\\\"tex_highlight\\\\\\\":\\\\\\\"mu_style_highlight_01.bundle\\\\\\\",\\\\\\\"makeup_intensity_highlight\\\\\\\":1.0,\\\\\\\"makeup_lip_color\\\\\\\":\[0.81,0.31,0.22,1.0\],\\\\\\\"lip_type\\\\\\\":0,\\\\\\\"is_two_color\\\\\\\":0,\\\\\\\"makeup_intensity_lip\\\\\\\":0.699999988079071}\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"sexy\\\"}}\\n{\\\"id\\\":\\\"sexy\\\",\\\"category\\\":0,\\\"name\\\":\\\"Smoking
  Hot\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_makeup_32/sexy.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_makeup_32/sexy.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":32,\\\"type_name\\\":\\\"fu_makeup\\\",\\\"view_order\\\":160,\\\"filter_type\\\":\\\"ziran2\\\",\\\"asset_type\\\":\\\"FU_MAKEUP\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"sexy\\\",\\\"category_name\\\":\\\"sexy\\\",\\\"asset_params\\\":\\\"{\\\\\\\"blend_type_tex_blusher\\\\\\\":0,\\\\\\\"blend_type_tex_blusher2\\\\\\\":0,\\\\\\\"makeup_blusher_color\\\\\\\":\[0.96,0.44,0.42,1.0\],\\\\\\\"tex_blusher\\\\\\\":\\\\\\\"mu_style_blush_02.bundle\\\\\\\",\\\\\\\"makeup_intensity_blusher\\\\\\\":1.0,\\\\\\\"makeup_eyeBrow_color\\\\\\\":\[0.28,0.16,0.08,1.0\],\\\\\\\"tex_brow\\\\\\\":\\\\\\\"mu_style_eyebrow_01.bundle\\\\\\\",\\\\\\\"brow_warp\\\\\\\":1.0,\\\\\\\"brow_warp_type\\\\\\\":2,\\\\\\\"makeup_intensity_eyeBrow\\\\\\\":0.4000000059604645,\\\\\\\"makeup_eyelash_color\\\\\\\":\[0.28,0.16,0.08,1.0\],\\\\\\\"tex_eyeLash\\\\\\\":\\\\\\\"mu_style_eyelash_04.bundle\\\\\\\",\\\\\\\"makeup_intensity_eyelash\\\\\\\":0.699999988079071,\\\\\\\"makeup_eyeLiner_color\\\\\\\":\[0.28,0.16,0.08,1.0\],\\\\\\\"tex_eyeLiner\\\\\\\":\\\\\\\"mu_style_eyeliner_01.bundle\\\\\\\",\\\\\\\"makeup_intensity_eyeLiner\\\\\\\":0.6000000238418579,\\\\\\\"blend_type_tex_eye\\\\\\\":0,\\\\\\\"blend_type_tex_eye2\\\\\\\":0,\\\\\\\"blend_type_tex_eye3\\\\\\\":1,\\\\\\\"blend_type_tex_eye4\\\\\\\":0,\\\\\\\"makeup_eye_color\\\\\\\":\[0.88,0.32,0.32,1.0\],\\\\\\\"makeup_eye_color2\\\\\\\":\[0.69,0.25,0.25,1.0\],\\\\\\\"makeup_eye_color3\\\\\\\":\[0.98,0.80,0.760,1.0\],\\\\\\\"tex_eye\\\\\\\":\\\\\\\"mu_style_eyeshadow_06.bundle\\\\\\\",\\\\\\\"makeup_intensity_eye\\\\\\\":0.8999999761581421,\\\\\\\"makeup_foundation_color\\\\\\\":\[0.82,0.71,0.62,1.0\],\\\\\\\"tex_foundation\\\\\\\":\\\\\\\"mu_style_foundation_01.bundle\\\\\\\",\\\\\\\"makeup_intensity_foundation\\\\\\\":1.0,\\\\\\\"makeup_highlight_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_highlight\\\\\\\":\\\\\\\"mu_style_highlight_02.bundle\\\\\\\",\\\\\\\"makeup_intensity_highlight\\\\\\\":0.0,\\\\\\\"makeup_shadow_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_shadow\\\\\\\":\\\\\\\"mu_style_contour_01.bundle\\\\\\\",\\\\\\\"makeup_intensity_shadow\\\\\\\":1.0,\\\\\\\"makeup_lip_color\\\\\\\":\[0.60,0.16,0.16,1.0\],\\\\\\\"lip_type\\\\\\\":0,\\\\\\\"is_two_color\\\\\\\":0,\\\\\\\"makeup_intensity_lip\\\\\\\":0.800000011920929}\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"bored_cat\\\"}}\\n{\\\"id\\\":\\\"bored_cat\\\",\\\"category\\\":0,\\\"name\\\":\\\"Bored
  Cat\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_makeup_32/bored_cat.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_makeup_32/bored_cat.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":32,\\\"type_name\\\":\\\"fu_makeup\\\",\\\"view_order\\\":170,\\\"filter_type\\\":\\\"zhiganhui5\\\",\\\"asset_type\\\":\\\"FU_MAKEUP\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"bored_cat\\\",\\\"category_name\\\":\\\"bored_cat\\\",\\\"asset_params\\\":\\\"{\\\\\\\"blend_type_tex_blusher\\\\\\\":0,\\\\\\\"blend_type_tex_blusher2\\\\\\\":1,\\\\\\\"makeup_blusher_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"makeup_blusher_color2\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_blusher\\\\\\\":\\\\\\\"zhuangrong_sh.png\\\\\\\",\\\\\\\"tex_blusher2\\\\\\\":\\\\\\\"zhuangrong_sh2.png\\\\\\\",\\\\\\\"makeup_intensity_blusher\\\\\\\":1.0,\\\\\\\"makeup_eyeBrow_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_brow\\\\\\\":\\\\\\\"brow.png\\\\\\\",\\\\\\\"brow_warp\\\\\\\":1.0,\\\\\\\"brow_warp_type\\\\\\\":3,\\\\\\\"makeup_intensity_eyeBrow\\\\\\\":0.699999988079071,\\\\\\\"makeup_eyelash_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_eyeLash\\\\\\\":\\\\\\\"eyeLash.png\\\\\\\",\\\\\\\"makeup_intensity_eyelash\\\\\\\":0.699999988079071,\\\\\\\"makeup_eyeLiner_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_eyeLiner\\\\\\\":\\\\\\\"eyeLiner.png\\\\\\\",\\\\\\\"makeup_intensity_eyeLiner\\\\\\\":0.699999988079071,\\\\\\\"blend_type_tex_eye\\\\\\\":0,\\\\\\\"blend_type_tex_eye2\\\\\\\":0,\\\\\\\"blend_type_tex_eye3\\\\\\\":1,\\\\\\\"blend_type_tex_eye4\\\\\\\":0,\\\\\\\"makeup_eye_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"makeup_eye_color2\\\\\\\":\[0.5882353186607361,0.3607843220233917,0.30588236451148989,1.0\],\\\\\\\"makeup_eye_color3\\\\\\\":\[1.0,1.0,1.0,1.0\],\\\\\\\"tex_eye\\\\\\\":\\\\\\\"eye.png\\\\\\\",\\\\\\\"tex_eye2\\\\\\\":\\\\\\\"eye2.png\\\\\\\",\\\\\\\"tex_eye3\\\\\\\":\\\\\\\"eye3.png\\\\\\\",\\\\\\\"makeup_intensity_eye\\\\\\\":0.8999999761581421,\\\\\\\"makeup_highlight_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_highlight\\\\\\\":\\\\\\\"zhuangrong_gg.png\\\\\\\",\\\\\\\"makeup_intensity_highlight\\\\\\\":1.0,\\\\\\\"makeup_shadow_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_shadow\\\\\\\":\\\\\\\"zhuangrong_yy.png\\\\\\\",\\\\\\\"makeup_intensity_shadow\\\\\\\":0.800000011920929,\\\\\\\"makeup_lip_color\\\\\\\":\[0.501960813999176,0.10980392247438431,0.12941177189350129,1.0\],\\\\\\\"lip_type\\\\\\\":0,\\\\\\\"is_two_color\\\\\\\":0,\\\\\\\"makeup_intensity_lip\\\\\\\":0.800000011920929}\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"purple_rhyme\\\"}}\\n{\\\"id\\\":\\\"purple_rhyme\\\",\\\"category\\\":0,\\\"name\\\":\\\"Purple
  Rhythm\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_makeup_32/purple_rhyme.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_makeup_32/purple_rhyme.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":32,\\\"type_name\\\":\\\"fu_makeup\\\",\\\"view_order\\\":180,\\\"filter_type\\\":\\\"zhiganhui1\\\",\\\"asset_type\\\":\\\"FU_MAKEUP\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"purple_rhyme\\\",\\\"category_name\\\":\\\"purple_rhyme\\\",\\\"asset_params\\\":\\\"{\\\\\\\"blend_type_tex_blusher\\\\\\\":0,\\\\\\\"blend_type_tex_blusher2\\\\\\\":0,\\\\\\\"makeup_blusher_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"makeup_blusher_color2\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_blusher\\\\\\\":\\\\\\\"zhuangrong_sh.png\\\\\\\",\\\\\\\"makeup_intensity_blusher\\\\\\\":1.0,\\\\\\\"makeup_eyeBrow_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_brow\\\\\\\":\\\\\\\"brow.png\\\\\\\",\\\\\\\"brow_warp\\\\\\\":1.0,\\\\\\\"brow_warp_type\\\\\\\":3,\\\\\\\"makeup_intensity_eyeBrow\\\\\\\":0.699999988079071,\\\\\\\"makeup_eyelash_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_eyeLash\\\\\\\":\\\\\\\"eyeLash.png\\\\\\\",\\\\\\\"makeup_intensity_eyelash\\\\\\\":1.0,\\\\\\\"makeup_eyeLiner_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_eyeLiner\\\\\\\":\\\\\\\"eyeLiner.png\\\\\\\",\\\\\\\"makeup_intensity_eyeLiner\\\\\\\":1.0,\\\\\\\"makeup_highlight_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_highlight\\\\\\\":\\\\\\\"zhuangrong_gg.png\\\\\\\",\\\\\\\"makeup_intensity_highlight\\\\\\\":0.800000011920929,\\\\\\\"makeup_shadow_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"tex_shadow\\\\\\\":\\\\\\\"zhuangrong_yy.png\\\\\\\",\\\\\\\"makeup_intensity_shadow\\\\\\\":0.699999988079071,\\\\\\\"makeup_lip_color\\\\\\\":\[0.5490196347236633,0.20000000298023225,0.250980406999588,1.0\],\\\\\\\"lip_type\\\\\\\":1,\\\\\\\"is_two_color\\\\\\\":0,\\\\\\\"makeup_intensity_lip\\\\\\\":0.8999999761581421,\\\\\\\"blend_type_tex_eye\\\\\\\":0,\\\\\\\"blend_type_tex_eye2\\\\\\\":0,\\\\\\\"blend_type_tex_eye3\\\\\\\":1,\\\\\\\"blend_type_tex_eye4\\\\\\\":0,\\\\\\\"makeup_eye_color\\\\\\\":\[0.0,0.0,0.0,0.0\],\\\\\\\"makeup_eye_color2\\\\\\\":\[0.5882353186607361,0.3607843220233917,0.30588236451148989,1.0\],\\\\\\\"makeup_eye_color3\\\\\\\":\[1.0,1.0,1.0,1.0\],\\\\\\\"tex_eye\\\\\\\":\\\\\\\"eye.png\\\\\\\",\\\\\\\"tex_eye2\\\\\\\":\\\\\\\"eye2.png\\\\\\\",\\\\\\\"tex_eye3\\\\\\\":\\\\\\\"eye3.png\\\\\\\",\\\\\\\"makeup_intensity_eye\\\\\\\":1.0}\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"an02\\\"}}\\n{\\\"id\\\":\\\"an02\\\",\\\"category\\\":0,\\\"name\\\":\\\"Baby
  Deer\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_animoji_33/an2.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_animoji_33/an2.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":33,\\\"type_name\\\":\\\"fu_animoji\\\",\\\"view_order\\\":20,\\\"asset_type\\\":\\\"FU_ANIMOJI\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Baby
  Deer\\\",\\\"category_name\\\":\\\"Baby
  Deer\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"an03\\\"}}\\n{\\\"id\\\":\\\"an03\\\",\\\"category\\\":0,\\\"name\\\":\\\"Baby
  Girl\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_animoji_33/an3.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_animoji_33/an3.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":33,\\\"type_name\\\":\\\"fu_animoji\\\",\\\"view_order\\\":30,\\\"asset_type\\\":\\\"FU_ANIMOJI\\\",\\\"alias\\\":\\\"Baby
  Girl\\\",\\\"valid_till\\\":1630067327504,\\\"label\\\":\\\"New\\\",\\\"category_name\\\":\\\"Baby
  Girl\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"an04\\\"}}\\n{\\\"id\\\":\\\"an04\\\",\\\"category\\\":0,\\\"name\\\":\\\"Bunny\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_animoji_33/an4.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_animoji_33/an4.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":33,\\\"type_name\\\":\\\"fu_animoji\\\",\\\"view_order\\\":40,\\\"asset_type\\\":\\\"FU_ANIMOJI\\\",\\\"alias\\\":\\\"Bunny\\\",\\\"valid_till\\\":1629525434631,\\\"label\\\":\\\"new\\\",\\\"category_name\\\":\\\"Bunny\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"an05\\\"}}\\n{\\\"id\\\":\\\"an05\\\",\\\"category\\\":0,\\\"name\\\":\\\"Deer\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_animoji_33/an5.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_animoji_33/an5.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":33,\\\"type_name\\\":\\\"fu_animoji\\\",\\\"view_order\\\":50,\\\"asset_type\\\":\\\"FU_ANIMOJI\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Deer\\\",\\\"category_name\\\":\\\"Deer\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"an06\\\"}}\\n{\\\"id\\\":\\\"an06\\\",\\\"category\\\":0,\\\"name\\\":\\\"Girl\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_animoji_33/an6.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_animoji_33/an6.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":33,\\\"type_name\\\":\\\"fu_animoji\\\",\\\"view_order\\\":60,\\\"asset_type\\\":\\\"FU_ANIMOJI\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Girl\\\",\\\"category_name\\\":\\\"Girl\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"an07\\\"}}\\n{\\\"id\\\":\\\"an07\\\",\\\"category\\\":0,\\\"name\\\":\\\"Lion\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_animoji_33/an7.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_animoji_33/an7.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":33,\\\"type_name\\\":\\\"fu_animoji\\\",\\\"view_order\\\":70,\\\"asset_type\\\":\\\"FU_ANIMOJI\\\",\\\"alias\\\":\\\"Lion\\\",\\\"valid_till\\\":1629289743808,\\\"label\\\":\\\"New\\\",\\\"category_name\\\":\\\"Lion\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"an08\\\"}}\\n{\\\"id\\\":\\\"an08\\\",\\\"category\\\":0,\\\"name\\\":\\\"Pig\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_animoji_33/an8.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_animoji_33/an8.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":33,\\\"type_name\\\":\\\"fu_animoji\\\",\\\"view_order\\\":80,\\\"asset_type\\\":\\\"FU_ANIMOJI\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Pig\\\",\\\"category_name\\\":\\\"Pig\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"an09\\\"}}\\n{\\\"id\\\":\\\"an09\\\",\\\"category\\\":0,\\\"name\\\":\\\"Seal\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_animoji_33/an9.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_animoji_33/an9.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":33,\\\"type_name\\\":\\\"fu_animoji\\\",\\\"view_order\\\":90,\\\"asset_type\\\":\\\"FU_ANIMOJI\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Seal\\\",\\\"category_name\\\":\\\"Seal\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"an10\\\"}}\\n{\\\"id\\\":\\\"an10\\\",\\\"category\\\":0,\\\"name\\\":\\\"Skull\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_animoji_33/an10.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_animoji_33/an10.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":33,\\\"type_name\\\":\\\"fu_animoji\\\",\\\"view_order\\\":100,\\\"asset_type\\\":\\\"FU_ANIMOJI\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Skull\\\",\\\"category_name\\\":\\\"Skull\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"an01\\\"}}\\n{\\\"id\\\":\\\"an01\\\",\\\"category\\\":0,\\\"name\\\":\\\"Alien\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_animoji_33/an1.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_animoji_33/an1.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":33,\\\"type_name\\\":\\\"fu_animoji\\\",\\\"view_order\\\":1,\\\"asset_type\\\":\\\"FU_ANIMOJI\\\",\\\"has_sound\\\":true,\\\"alias\\\":\\\"Alien\\\",\\\"label\\\":\\\"New\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"bgseg1\\\"}}\\n{\\\"id\\\":\\\"bgseg1\\\",\\\"category\\\":0,\\\"name\\\":\\\"Casual
  Teen\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_background_34/bgseg1.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_background_34/bgseg1.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":34,\\\"type_name\\\":\\\"fu_background\\\",\\\"view_order\\\":10,\\\"asset_type\\\":\\\"FU_PORTRAIT_SEGMENTATION\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Casual
  teen\\\",\\\"valid_till\\\":1650798341148,\\\"label\\\":\\\"new\\\",\\\"category_name\\\":\\\"Casual
  teen\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"bgseg4\\\"}}\\n{\\\"id\\\":\\\"bgseg4\\\",\\\"category\\\":0,\\\"name\\\":\\\"Hair
  Knots\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_background_34/bgseg4.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_background_34/bgseg4.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":34,\\\"type_name\\\":\\\"fu_background\\\",\\\"view_order\\\":40,\\\"asset_type\\\":\\\"FU_PORTRAIT_SEGMENTATION\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Hair
  knots\\\",\\\"valid_till\\\":1643615614837,\\\"label\\\":\\\"New\\\",\\\"category_name\\\":\\\"Hair
  knots\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"bgseg5\\\"}}\\n{\\\"id\\\":\\\"bgseg5\\\",\\\"category\\\":0,\\\"name\\\":\\\"Gamer\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_background_34/bgseg5.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_background_34/bgseg5.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":34,\\\"type_name\\\":\\\"fu_background\\\",\\\"view_order\\\":50,\\\"asset_type\\\":\\\"FU_PORTRAIT_SEGMENTATION\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Gamer\\\",\\\"category_name\\\":\\\"Gamer\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"bgseg7\\\"}}\\n{\\\"id\\\":\\\"bgseg7\\\",\\\"category\\\":0,\\\"name\\\":\\\"Popsicle\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_background_34/bgseg7.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_background_34/bgseg7.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":34,\\\"type_name\\\":\\\"fu_background\\\",\\\"view_order\\\":70,\\\"asset_type\\\":\\\"FU_PORTRAIT_SEGMENTATION\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Popsicle\\\",\\\"category_name\\\":\\\"Popsicle\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"bgseg8\\\"}}\\n{\\\"id\\\":\\\"bgseg8\\\",\\\"category\\\":0,\\\"name\\\":\\\"Sea
  view\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_background_34/bgseg8.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_background_34/bgseg8.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":34,\\\"type_name\\\":\\\"fu_background\\\",\\\"view_order\\\":80,\\\"asset_type\\\":\\\"FU_PORTRAIT_SEGMENTATION\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Sea
  view\\\",\\\"category_name\\\":\\\"Sea
  view\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"bgseg9\\\"}}\\n{\\\"id\\\":\\\"bgseg9\\\",\\\"category\\\":0,\\\"name\\\":\\\"Sunglass\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_background_34/bgseg9.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_background_34/bgseg9.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":34,\\\"type_name\\\":\\\"fu_background\\\",\\\"view_order\\\":90,\\\"asset_type\\\":\\\"FU_PORTRAIT_SEGMENTATION\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Sunglass\\\",\\\"valid_till\\\":1643615625878,\\\"label\\\":\\\"New\\\",\\\"category_name\\\":\\\"Sunglass\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"bgseg2\\\"}}\\n{\\\"id\\\":\\\"bgseg2\\\",\\\"category\\\":0,\\\"name\\\":\\\"Formals\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_background_34/bgseg2.2.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_background_34/bgseg2.2.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":34,\\\"type_name\\\":\\\"fu_background\\\",\\\"view_order\\\":20,\\\"asset_type\\\":\\\"FU_PORTRAIT_SEGMENTATION\\\",\\\"valid_till\\\":1646219151588,\\\"label\\\":\\\"new3\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"bgseg3.0\\\"}}\\n{\\\"id\\\":\\\"bgseg3.0\\\",\\\"category\\\":0,\\\"name\\\":\\\"Senpai\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_background_34/bgseg3.0.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_background_34/bgseg3.0.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":34,\\\"type_name\\\":\\\"fu_background\\\",\\\"view_order\\\":30,\\\"asset_type\\\":\\\"FU_PORTRAIT_SEGMENTATION\\\",\\\"valid_till\\\":1650798361473,\\\"label\\\":\\\"new\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"haircolor1\\\"}}\\n{\\\"id\\\":\\\"haircolor1\\\",\\\"category\\\":0,\\\"name\\\":\\\"Hair
  1\\\",\\\"version\\\":0,\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_haircolour_35/icon_hair_gradualchange_01.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":35,\\\"type_name\\\":\\\"fu_haircolour\\\",\\\"view_order\\\":0,\\\"asset_type\\\":\\\"FU_HAIR_COLOUR\\\",\\\"valid_till\\\":1654854149776,\\\"label\\\":\\\"new\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"haircolor2\\\"}}\\n{\\\"id\\\":\\\"haircolor2\\\",\\\"category\\\":0,\\\"name\\\":\\\"Hair
  2\\\",\\\"version\\\":0,\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_haircolour_35/icon_hair_gradualchange_02.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":1,\\\"type_id\\\":35,\\\"type_name\\\":\\\"fu_haircolour\\\",\\\"view_order\\\":1,\\\"asset_type\\\":\\\"FU_HAIR_COLOUR\\\",\\\"valid_till\\\":1654847685034,\\\"label\\\":\\\"new\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"haircolor3\\\"}}\\n{\\\"id\\\":\\\"haircolor3\\\",\\\"category\\\":0,\\\"name\\\":\\\"Hair
  3\\\",\\\"version\\\":0,\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_haircolour_35/icon_hair_gradualchange_03.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":2,\\\"type_id\\\":35,\\\"type_name\\\":\\\"fu_haircolour\\\",\\\"view_order\\\":2,\\\"asset_type\\\":\\\"FU_HAIR_COLOUR\\\",\\\"valid_till\\\":1653983732688,\\\"label\\\":\\\"New2\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"haircolor4\\\"}}\\n{\\\"id\\\":\\\"haircolor4\\\",\\\"category\\\":0,\\\"name\\\":\\\"Hair
  4\\\",\\\"version\\\":0,\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_haircolour_35/icon_hair_gradualchange_04.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":3,\\\"type_id\\\":35,\\\"type_name\\\":\\\"fu_haircolour\\\",\\\"view_order\\\":3,\\\"asset_type\\\":\\\"FU_HAIR_COLOUR\\\",\\\"valid_till\\\":1643613008104,\\\"label\\\":\\\"new\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"haircolor5\\\"}}\\n{\\\"id\\\":\\\"haircolor5\\\",\\\"category\\\":0,\\\"name\\\":\\\"Hair
  5\\\",\\\"version\\\":0,\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_haircolour_35/icon_hair_gradualchange_05.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":4,\\\"type_id\\\":35,\\\"type_name\\\":\\\"fu_haircolour\\\",\\\"view_order\\\":4,\\\"asset_type\\\":\\\"FU_HAIR_COLOUR\\\",\\\"valid_till\\\":1651669859299,\\\"label\\\":\\\"new1\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"haircolor6\\\"}}\\n{\\\"id\\\":\\\"haircolor6\\\",\\\"category\\\":1,\\\"name\\\":\\\"Hair
  6\\\",\\\"version\\\":0,\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_haircolour_35/icon_hair_hairsalon_01.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":35,\\\"type_name\\\":\\\"fu_haircolour\\\",\\\"view_order\\\":5,\\\"asset_type\\\":\\\"FU_HAIR_COLOUR\\\",\\\"valid_till\\\":1653981072516,\\\"label\\\":\\\"new2\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"haircolor7\\\"}}\\n{\\\"id\\\":\\\"haircolor7\\\",\\\"category\\\":1,\\\"name\\\":\\\"Hair
  7\\\",\\\"version\\\":0,\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_haircolour_35/icon_hair_hairsalon_02.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":1,\\\"type_id\\\":35,\\\"type_name\\\":\\\"fu_haircolour\\\",\\\"view_order\\\":6,\\\"asset_type\\\":\\\"FU_HAIR_COLOUR\\\",\\\"valid_till\\\":1653976054974,\\\"label\\\":\\\"new2\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"haircolor8\\\"}}\\n{\\\"id\\\":\\\"haircolor8\\\",\\\"category\\\":1,\\\"name\\\":\\\"Hair
  8\\\",\\\"version\\\":0,\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_haircolour_35/icon_hair_hairsalon_03.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":2,\\\"type_id\\\":35,\\\"type_name\\\":\\\"fu_haircolour\\\",\\\"view_order\\\":7,\\\"asset_type\\\":\\\"FU_HAIR_COLOUR\\\",\\\"valid_till\\\":1653976134560,\\\"label\\\":\\\"new2\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"haircolor9\\\"}}\\n{\\\"id\\\":\\\"haircolor9\\\",\\\"category\\\":1,\\\"name\\\":\\\"Hair
  9\\\",\\\"version\\\":0,\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_haircolour_35/icon_hair_hairsalon_04.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":3,\\\"type_id\\\":35,\\\"type_name\\\":\\\"fu_haircolour\\\",\\\"view_order\\\":8,\\\"asset_type\\\":\\\"FU_HAIR_COLOUR\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"haircolor10\\\"}}\\n{\\\"id\\\":\\\"haircolor10\\\",\\\"category\\\":1,\\\"name\\\":\\\"Hair
  10\\\",\\\"version\\\":0,\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_haircolour_35/icon_hair_hairsalon_05.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":4,\\\"type_id\\\":35,\\\"type_name\\\":\\\"fu_haircolour\\\",\\\"view_order\\\":9,\\\"asset_type\\\":\\\"FU_HAIR_COLOUR\\\",\\\"valid_till\\\":1650951543922,\\\"label\\\":\\\"new\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"haircolor11\\\"}}\\n{\\\"id\\\":\\\"haircolor11\\\",\\\"category\\\":1,\\\"name\\\":\\\"Hair
  11\\\",\\\"version\\\":0,\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_haircolour_35/icon_hair_hairsalon_06.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":5,\\\"type_id\\\":35,\\\"type_name\\\":\\\"fu_haircolour\\\",\\\"view_order\\\":10,\\\"asset_type\\\":\\\"FU_HAIR_COLOUR\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"haircolor12\\\"}}\\n{\\\"id\\\":\\\"haircolor12\\\",\\\"category\\\":1,\\\"name\\\":\\\"Hair
  12\\\",\\\"version\\\":0,\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_haircolour_35/icon_hair_hairsalon_07.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":6,\\\"type_id\\\":35,\\\"type_name\\\":\\\"fu_haircolour\\\",\\\"view_order\\\":11,\\\"asset_type\\\":\\\"FU_HAIR_COLOUR\\\",\\\"valid_till\\\":1654848236058,\\\"label\\\":\\\"new\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"haircolor13\\\"}}\\n{\\\"id\\\":\\\"haircolor13\\\",\\\"category\\\":1,\\\"name\\\":\\\"Hair
  13\\\",\\\"version\\\":0,\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_haircolour_35/icon_hair_hairsalon_08.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":7,\\\"type_id\\\":35,\\\"type_name\\\":\\\"fu_haircolour\\\",\\\"view_order\\\":12,\\\"asset_type\\\":\\\"FU_HAIR_COLOUR\\\",\\\"valid_till\\\":1654848211057,\\\"label\\\":\\\"new\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"bgseg6\\\"}}\\n{\\\"id\\\":\\\"bgseg6\\\",\\\"category\\\":0,\\\"name\\\":\\\"Outline\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_humanoutline_36/bgseg6.1.bundle\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_humanoutline_36/bgseg6.1.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":36,\\\"type_name\\\":\\\"fu_humanoutline\\\",\\\"view_order\\\":60,\\\"asset_type\\\":\\\"FU_PORTRAIT_SEGMENTATION_HUMAN_OUTLINE\\\",\\\"user_action\\\":\\\"\\\",\\\"alias\\\":\\\"Outline\\\",\\\"category_name\\\":\\\"Outline\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"Custom_Bg_Seg\\\"}}\\n{\\\"id\\\":\\\"Custom_Bg_Seg\\\",\\\"category\\\":0,\\\"name\\\":\\\"Custom
  Bg Seg\\\",\\\"desc\\\":\\\"Add From
  Gallery\\\",\\\"version\\\":0,\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/fu_bgsegcustom_37/bg_custom.png\\\",\\\"package_size\\\":0,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/fu_bgsegcustom_37/bg_custom.png\\\",\\\"supported_aspect_ratio\\\":0,\\\"idx\\\":0,\\\"type_id\\\":37,\\\"type_name\\\":\\\"fu_bgsegcustom\\\",\\\"view_order\\\":-500,\\\"asset_type\\\":\\\"FU_PORTRAIT_SEGMENTATION_BG_SEG_CUSTOM\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"cartoon\\\"}}\\n{\\\"id\\\":\\\"cartoon\\\",\\\"category\\\":1,\\\"name\\\":\\\"Cartoon\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":1,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/zoomeffect_13/cartoon.zip\\\",\\\"package_size\\\":747000,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/zoomeffect_13/nv_noselected_cartoon.png\\\",\\\"supported_aspect_ratio\\\":127,\\\"cover_url2\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover2/zoomeffect_13/nv_selected_cartoon.png\\\",\\\"idx\\\":13,\\\"type_id\\\":13,\\\"type_name\\\":\\\"zoomeffect\\\",\\\"view_order\\\":110,\\\"asset_type\\\":\\\"ZOOMCAM\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"daily\\\"}}\\n{\\\"id\\\":\\\"daily\\\",\\\"category\\\":1,\\\"name\\\":\\\"Daily\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":1,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/zoomeffect_13/daily.zip\\\",\\\"package_size\\\":1800000,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/zoomeffect_13/nv_noselected_daily.png\\\",\\\"supported_aspect_ratio\\\":127,\\\"cover_url2\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover2/zoomeffect_13/nv_selected_daily.png\\\",\\\"idx\\\":14,\\\"type_id\\\":13,\\\"type_name\\\":\\\"zoomeffect\\\",\\\"view_order\\\":50,\\\"asset_type\\\":\\\"ZOOMCAM\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"dogpacks\\\"}}\\n{\\\"id\\\":\\\"dogpacks\\\",\\\"category\\\":1,\\\"name\\\":\\\"Dog\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":1,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/zoomeffect_13/dogpacks.zip\\\",\\\"package_size\\\":33000,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/zoomeffect_13/nv_noselected_dogpacks.png\\\",\\\"supported_aspect_ratio\\\":127,\\\"cover_url2\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover2/zoomeffect_13/nv_selected_dogpacks.png\\\",\\\"idx\\\":9,\\\"type_id\\\":13,\\\"type_name\\\":\\\"zoomeffect\\\",\\\"view_order\\\":130,\\\"asset_type\\\":\\\"ZOOMCAM\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"dramatization\\\"}}\\n{\\\"id\\\":\\\"dramatization\\\",\\\"category\\\":1,\\\"name\\\":\\\"Dramatization\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":1,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/zoomeffect_13/dramatization.zip\\\",\\\"package_size\\\":36000,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/zoomeffect_13/nv_noselected_dramatization.png\\\",\\\"supported_aspect_ratio\\\":127,\\\"cover_url2\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover2/zoomeffect_13/nv_selected_dramatization.png\\\",\\\"idx\\\":1,\\\"type_id\\\":13,\\\"type_name\\\":\\\"zoomeffect\\\",\\\"view_order\\\":140,\\\"asset_type\\\":\\\"ZOOMCAM\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"fire\\\"}}\\n{\\\"id\\\":\\\"fire\\\",\\\"category\\\":1,\\\"name\\\":\\\"Fire\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":1,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/zoomeffect_13/fire.zip\\\",\\\"package_size\\\":2100000,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/zoomeffect_13/nv_noselected_fire.png\\\",\\\"supported_aspect_ratio\\\":127,\\\"cover_url2\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover2/zoomeffect_13/nv_selected_fire.png\\\",\\\"idx\\\":7,\\\"type_id\\\":13,\\\"type_name\\\":\\\"zoomeffect\\\",\\\"view_order\\\":30,\\\"asset_type\\\":\\\"ZOOMCAM\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"horror\\\"}}\\n{\\\"id\\\":\\\"horror\\\",\\\"category\\\":1,\\\"name\\\":\\\"Horror\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":1,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/zoomeffect_13/horror.zip\\\",\\\"package_size\\\":100000,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/zoomeffect_13/nv_noselected_horror.png\\\",\\\"supported_aspect_ratio\\\":127,\\\"cover_url2\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover2/zoomeffect_13/nv_selected_horror.png\\\",\\\"idx\\\":5,\\\"type_id\\\":13,\\\"type_name\\\":\\\"zoomeffect\\\",\\\"view_order\\\":70,\\\"asset_type\\\":\\\"ZOOMCAM\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"love\\\"}}\\n{\\\"id\\\":\\\"love\\\",\\\"category\\\":1,\\\"name\\\":\\\"Love\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":1,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/zoomeffect_13/love.zip\\\",\\\"package_size\\\":428000,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/zoomeffect_13/nv_noselected_love.png\\\",\\\"supported_aspect_ratio\\\":127,\\\"cover_url2\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover2/zoomeffect_13/nv_selected_love.png\\\",\\\"idx\\\":8,\\\"type_id\\\":13,\\\"type_name\\\":\\\"zoomeffect\\\",\\\"view_order\\\":40,\\\"asset_type\\\":\\\"ZOOMCAM\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"no\\\"}}\\n{\\\"id\\\":\\\"no\\\",\\\"category\\\":1,\\\"name\\\":\\\"No\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":1,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/zoomeffect_13/no.zip\\\",\\\"package_size\\\":117000,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/zoomeffect_13/nv_noselected_no.png\\\",\\\"supported_aspect_ratio\\\":127,\\\"cover_url2\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover2/zoomeffect_13/nv_selected_no.png\\\",\\\"idx\\\":4,\\\"type_id\\\":13,\\\"type_name\\\":\\\"zoomeffect\\\",\\\"view_order\\\":10,\\\"asset_type\\\":\\\"ZOOMCAM\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"rhythm\\\"}}\\n{\\\"id\\\":\\\"rhythm\\\",\\\"category\\\":1,\\\"name\\\":\\\"Rhythm\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":1,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/zoomeffect_13/rhythm.zip\\\",\\\"package_size\\\":90000,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/zoomeffect_13/nv_noselected_rhythm.png\\\",\\\"supported_aspect_ratio\\\":127,\\\"cover_url2\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover2/zoomeffect_13/nv_selected_rhythm.png\\\",\\\"idx\\\":10,\\\"type_id\\\":13,\\\"type_name\\\":\\\"zoomeffect\\\",\\\"view_order\\\":80,\\\"asset_type\\\":\\\"ZOOMCAM\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"shake\\\"}}\\n{\\\"id\\\":\\\"shake\\\",\\\"category\\\":1,\\\"name\\\":\\\"Shake\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":1,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/zoomeffect_13/shake.zip\\\",\\\"package_size\\\":42000,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/zoomeffect_13/nv_noselected_shake.png\\\",\\\"supported_aspect_ratio\\\":127,\\\"cover_url2\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover2/zoomeffect_13/nv_selected_shake.png\\\",\\\"idx\\\":12,\\\"type_id\\\":13,\\\"type_name\\\":\\\"zoomeffect\\\",\\\"view_order\\\":60,\\\"asset_type\\\":\\\"ZOOMCAM\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"spring\\\"}}\\n{\\\"id\\\":\\\"spring\\\",\\\"category\\\":1,\\\"name\\\":\\\"spring\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":1,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/zoomeffect_13/spring.zip\\\",\\\"package_size\\\":22000,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/zoomeffect_13/nv_noselected_spring.png\\\",\\\"supported_aspect_ratio\\\":127,\\\"cover_url2\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover2/zoomeffect_13/nv_selected_spring.png\\\",\\\"idx\\\":2,\\\"type_id\\\":13,\\\"type_name\\\":\\\"zoomeffect\\\",\\\"view_order\\\":90,\\\"asset_type\\\":\\\"ZOOMCAM\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"tragedy\\\"}}\\n{\\\"id\\\":\\\"tragedy\\\",\\\"category\\\":1,\\\"name\\\":\\\"Tragedy\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":1,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/zoomeffect_13/tragedy.zip\\\",\\\"package_size\\\":2200000,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/zoomeffect_13/nv_noselected_tragedy.png\\\",\\\"supported_aspect_ratio\\\":127,\\\"cover_url2\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover2/zoomeffect_13/nv_selected_tragedy.png\\\",\\\"idx\\\":6,\\\"type_id\\\":13,\\\"type_name\\\":\\\"zoomeffect\\\",\\\"view_order\\\":120,\\\"asset_type\\\":\\\"ZOOMCAM\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"tv\\\"}}\\n{\\\"id\\\":\\\"tv\\\",\\\"category\\\":1,\\\"name\\\":\\\"TV\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":1,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/zoomeffect_13/tv.zip\\\",\\\"package_size\\\":2100000,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/zoomeffect_13/nv_noselected_tv.png\\\",\\\"supported_aspect_ratio\\\":127,\\\"cover_url2\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover2/zoomeffect_13/nv_selected_tv.png\\\",\\\"idx\\\":3,\\\"type_id\\\":13,\\\"type_name\\\":\\\"zoomeffect\\\",\\\"view_order\\\":20,\\\"asset_type\\\":\\\"ZOOMCAM\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\\n{\\\"index\\\":{\\\"\_id\\\":\\\"wasted\\\"}}\\n{\\\"id\\\":\\\"wasted\\\",\\\"category\\\":1,\\\"name\\\":\\\"Wasted\\\",\\\"desc\\\":\\\"\\\",\\\"tags\\\":\\\"\\\",\\\"version\\\":1,\\\"min_app_version\\\":\\\"\\\",\\\"package_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/zoomeffect_13/wasted.zip\\\",\\\"package_size\\\":138000,\\\"cover_url\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover/zoomeffect_13/nv_noselected_wasted.png\\\",\\\"supported_aspect_ratio\\\":127,\\\"cover_url2\\\":\\\"https://qa-stream.myjosh.in/stream/qa-josh-content/material/cover2/zoomeffect_13/nv_selected_wasted.png\\\",\\\"idx\\\":15,\\\"type_id\\\":13,\\\"type_name\\\":\\\"zoomeffect\\\",\\\"view_order\\\":100,\\\"asset_type\\\":\\\"ZOOMCAM\\\",\\\"pass_through\\\":\\\"EFFECT\\\"}\"
  }

<!-- -->

- **Request Method and URL:**

  GET :
  https://gateway.myjosh.in/api/v1/upgrade/version/info/JOSH_STATIC_CONFIG/478

- **Curl Request:**

  curl \--location \--request GET
  \'https://gateway.myjosh.in/api/v1/upgrade/version/info/JOSH_STATIC_CONFIG/478\'

- **Success Response:**

  { \"code\": 200, \"status\": { \"message\": \"OK\", \"server\":
  \"10.10.35.85\", \"code\": 200 }, \"data\": { \"version\": 1057,
  \"data\": { \"jems_wallet_page_url\":
  \"https://share.myjosh.in/webview/jems-wallet?user_uuid={0}&client_id={1}\",
  \"profile_rejected_show_count\": 2, \"gifters_list_api\":
  \"http://api.myjosh.in/apij/gift/gifters-list\",
  \"bookmark_webview_url\":
  \"https://share.myjosh.in/webview/bookmarks\",
  \"search_default_popular_feed_url\":
  \"https://feed.myjosh.in/search/?q=viral\", \"tipping_icon_url\":
  \"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/Z2lmdF9pY29u.png\",
  \"gifting_icon_url\":
  \"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/Z2lmdF9pY29u.png\",
  \"recent_search_item_count\": 25, \"bottom_bar_tab_sequence\": \[
  \"HOME\", \"EXPLORE\", \"LIVE\", \"SHOP\", \"NOTIFICATIONINBOX\",
  \"PROFILE\" \], \"disable_custom_tab_social_auth\": false,
  \"is_seekbar_enabled\": true, \"educational_nudge_count_per_session\":
  3, \"educational_nudge_duration_in_ms\": 3000,
  \"is_tabbar_swiping_enabled\": true, \"like_comment_tab_list\": \[
  \"LIKE\", \"COMMENT\", \"GIFT\" \], \"contact_sync_message_config\": {
  \"zero_state_message\": \"Contact sync successful, no friends were
  found but you can always invite them later.\",
  \"after_follow_message\": \"You\'ve followed %d people from your
  contact book\", \"sync_in_bg\": \"Enjoy videos while we sync your
  contacts.\", \"with_contacts_state\": \"Contacts synced successfully.
  Tap to find your friends.\", \"action_text\": \"Find Friends\" },
  \"camera_tab_sequence\": \[ \"CAMERA\", \"PHOTOS\", \"MEMES\",
  \"TEMPLATES\", \"DUETS\" \],
  \"sticky_notif_refresh_interval_in_mins\": 15,
  \"cs_ttl_duration_in_minutes\": \"30\",
  \"wait_on_cs_page_in_seconds\": \"3\", \"max_photo_upload_limit\": 10,
  \"supportedMimetypes\": \[ \"video/mp4\", \"video/quicktime\",
  \"video/x-ms-wmv\", \"video/mov\", \"video/mpg\" \],
  \"reaction_sync_interval_in_seconds\": 86400, \"maxCommentCharLimit\":
  150, \"max_recent_cache_action_count\": 30, \"showDataSaverMode\":
  true, \"splash_ad_request_launch\": 2,
  \"repeated_launch_api_request_delay\": 10000,
  \"show_share_nudge_loop_count\": 2, \"max_share_nudge_show_count\": 3,
  \"max_lifetime_show_share_nudge_count\": 7, \"max_edit_nudge_count\":
  3, \"grid_item_count\": 3, \"enable_youtube_connect\": true,
  \"enable_instagram_connect\": true, \"softRelaunchDelay\": 600000,
  \"hardRelaunchDelay\": 1800000, \"animated_icon_duration_in_ms\": 500,
  \"create_post_max_char\": 120, \"precache_interest_icons\": true,
  \"video_edit_resolution\": 720,
  \"max_sticker_comment_nudge_show_count\": 1,
  \"is_apply_for_verification_enabled\": true,
  \"create_video_nudge_dismissal\": 3000, \"vote_nudge_dismissal\":
  3000, \"share_voted_video_nudge_dismissal\": 3000,
  \"effectsExpiryMaxDays\": 30, \"items_toshow_in_inbox\": 7,
  \"max_tpv_profile_suggestions\": 5, \"reduced_percent_volume_dub\":
  20, \"vote_interval_in_seconds\": 86400,
  \"experiment_incorrect_otp_max_attempts\": 2,
  \"experiment_resend_otp_max_attempts\": 2, \"snapchatLogoutIconUrl\":
  \"https://sdk.bitmoji.com/me/sticker/#AVATAR_ID#/204d8f0d-50e5-4db5-a810-f6525a68dc39\",
  \"enable_lite_sync_once\": false, \"disable_experiment_api\": false,
  \"enableAutoSaveVideos\": true, \"max_selected_videos_gallery\": 15,
  \"max_event_videos_to_download\": 2, \"max_event_videos_to_show\": 2,
  \"game_center_url\":
  \"https://feed.myjosh.in/page_collection/game/main-game-page\",
  \"allow_splash_ad\": false, \"allow_masthead_ad\": false,
  \"disable_josh_live\": false, \"jl_enable_room_options\": false,
  \"jl_is_default_video_enabled\": true,
  \"noti_display_on_tray_event_enable\": true, \"device_wake_up_flag\":
  false, \"refresh_wait_time_ms\": 1500, \"hide_block_user_option\":
  false, \"image_share_url\": \"https://api.myjosh.in/image/\",
  \"social_share_url\": \"https://api.myjosh.in/social/\",
  \"images_auto_scroll_duration_in_ms\": 5000, \"send_tip_page_url\":
  \"https://share.myjosh.in/webview/pay-tips?tip_to={0}&tip_by={1}&tip_to_image_url={2}&tip_to_user_name={3}&tip_by_user_name={4}\",
  \"tip_transactions_page_url\":
  \"https://share.myjosh.in/webview/tip-transactions?user_id={0}\",
  \"buy_jems_page_url\":
  \"https://share.myjosh.in/webview/pay-tips-v1?tip_to={0}&tip_by={1}&tip_to_image_url={2}&tip_to_user_name={3}&tip_by_user_name={4}&package_id={5}&package_collection_id={6}\",
  \"disable_buffer_settings_for_ads\": false, \"mute_ab_test_variant\":
  \"SESSION_MUTE\", \"zone_info_dialog_data\": { \"title\":
  \"\<h1\>Content on this page is community managed.\</h1\>\",
  \"message\": \"\<p\>Josh does not make any warranties about the
  completeness, reliability and accuracy of this information. \<a
  href=\'https://share.myjosh.in/terms-conditions\'\>Read
  TnC\</a\>\</p\>\", \"ctaText\": \"\<strong\>Okay\</strong\>\" },
  \"template_search_hints\": \[ \"Good Morning\", \"Love\" \],
  \"image_card_config\": { \"min_time_threshold_in_ms\": 5000,
  \"max_count_per_session\": 3, \"animation_list\": \[ 0, 1, 5, 6, 8 \]
  }, \"appsflyer_events\": { \"C2\": 180, \"C3\": 180, \"C4\": 180,
  \"C5\": 180, \"C6\": 180, \"C7\": 180, \"C8\": 180, \"C9\": 180,
  \"C10\": 180, \"C11\": 180, \"C12\": 540, \"C13\": 540, \"C14\": 540,
  \"C15\": 540, \"C16\": 1000, \"C17\": 1, \"C18\": 1, \"C19\": 180,
  \"C20\": 180, \"C22\": 540, \"C23\": 540, \"C24\": 540, \"C25\": 540,
  \"C26\": 540, \"C27\": 180, \"C28\": 180, \"C29\": 180, \"C30\": 180,
  \"C31\": 180, \"C32\": 180, \"C33\": 180, \"C34\": 180, \"C35\": 180,
  \"C36\": 180, \"C37\": 180, \"C38\": 180, \"C39\": 180, \"C40\": 180,
  \"C41\": 180, \"C42\": 180, \"C43\": 180, \"C44\": 180, \"C45\": 180,
  \"C46\": 180, \"C47\": 180, \"C48\": 180, \"C49\": 180, \"C50\": 180
  }, \"zero_page\": { \"like_comment_fpv\": { \"COMMENT\": { \"title\":
  \"No Comments\" }, \"GIFT\": { \"description\": \"Explore gift section
  and be the first one to send gift\", \"title\": \"No Gift Received\"
  }, \"LIKE\": { \"title\": \"No Likes\" } }, \"like_comment_tpv\": {
  \"COMMENT\": { \"title\": \"No Comments\" }, \"GIFT\": { \"cta_text\":
  \"Send Gifts\", \"description\": \"Explore gift section and be the
  first one to send gift\", \"title\": \"No Gift Received\" }, \"LIKE\":
  { \"title\": \"No Likes\" } }, \"user_fpv\": { \"2\": {
  \"description\": \"Try posting more content and invite your friends\",
  \"title\": \"No Fans\" }, \"3\": { \"cta_deeplink\":
  \"http://share.myjosh.in/page/discovery/main-discovery-page\",
  \"cta_text\": \"Discovery\", \"description\": \"Explore discover
  section and follow creators and other users\", \"title\": \"Not
  Following Anyone\" }, \"4\": { \"cta_deeplink\":
  \"http://share.myjosh.in/page/discovery/main-discovery-page\",
  \"cta_text\": \"Discovery\", \"description\": \"Explore discover
  section and follow pages\", \"title\": \"Not Following Any Pages\" },
  \"5\": { \"title\": \"No Suggestion\" } }, \"user_tpv\": { \"1\": {
  \"title\": \"No Mutual Followers\" }, \"2\": { \"title\": \"No Fans\"
  }, \"3\": { \"title\": \"No Followers\" }, \"4\": { \"title\": \"No
  Pages\" }, \"5\": { \"title\": \"No Suggestions\" } }, \"zone\": {
  \"1\": { \"title\": \"No Followers\" }, \"2\": { \"title\": \"No
  Suggestions\" } } }, \"nlfc_embed_config\": { \"disable_nlfc\": false,
  \"min_time_spent_to_trigger\": 3000, \"social_interactions_trigger\":
  \[ \"like\", \"share\", \"comment\", \"click\" \],
  \"skip_nlfc_for_session_on_failure\": 3, \"min_offset_to_append\": 1
  }, \"nlfc_image_config\": { \"disable_nlfc\": false,
  \"min_time_spent_to_trigger\": 3000, \"social_interactions_trigger\":
  \[ \"like\", \"share\", \"comment\" \],
  \"skip_nlfc_for_session_on_failure\": 3, \"min_offset_to_append\": 1
  }, \"pullNotificationConfig\": { \"pull_notifications_enabled\": true,
  \"firstTimePullDelay\": 300 }, \"api_sequencing_config\": {
  \"api_sequencing_max_delay_ms\": 180000, \"api_hit_interval_time_ms\":
  4000, \"fl_api_hit_interval_time_ms\": 2000,
  \"delay_max_video_count\": 10, \"cache_api_delay_time_ms\": 10000,
  \"delay_after_handshake\": 3000 }, \"myelin_config\": { \"enable\":
  false, \"disable_for_verified\": \[ \"k\", \"m\", \"l\" \],
  \"sync_time\": 86400000, \"quality\": { \"fast\": \"average\",
  \"good\": \"average\", \"average\": \"average\" } },
  \"wakeUpPartnerInformation\": { \"minimumBatteryRequired\": 15,
  \"partnerPackages\": \[ { \"packageName\": \"com.eterno\", \"action\":
  \"com.eterno.intent.woken_up_service_start\",
  \"foregroundServiceSupport\": true, \"wakeupsections\": \[
  \"Notification\", \"Deeplink\", \"Splash\", \"App Controller\" \],
  \"dndStartTime\": 82800, \"dndEndTime\": 21300, \"wakeDelay\":
  86400000, \"disabledManufacturer\": \[\] }, { \"packageName\":
  \"com.newsdistill.mobile\", \"action\":
  \"com.newsdistill.mobile.intent.ACTION_WAKEUP\",
  \"foregroundServiceSupport\": true, \"wakeupsections\": \[
  \"Notification\", \"Deeplink\", \"Splash\", \"App Controller\" \],
  \"dndStartTime\": 82800, \"dndEndTime\": 21300, \"wakeDelay\":
  86400000, \"disabledManufacturer\": \[\] } \] },
  \"discovery_tab_list\": \[ { \"id\": \"main-discovery-page\",
  \"name\": \"Discovery\", \"tab_icon_url\": \"discovery_icon\",
  \"url\":
  \"https://feed.myjosh.in/page/discovery/main-discovery-page\",
  \"type\": \"DISCOVERY\" }, { \"id\": \"main-audio-page\", \"name\":
  \"Music\", \"tab_icon_url\": \"audio_icon\", \"url\":
  \"https://feed.myjosh.in/page/audio/main-audio-page\", \"type\":
  \"AUDIO\" } \], \"duet_video_volume_config\": {
  \"dueted_video_volume\": 20, \"recorded_video_volume\": 100 },
  \"wa_status_sent_config\": \[ { \"min_version\": 30, \"max_version\":
  2147483647, \"enable\": true, \"path_wa_status\":
  \"/Android/media/com.whatsapp/WhatsApp/Media/.Statuses\",
  \"path_wa_sent_video\":
  \"/Android/media/com.whatsapp/WhatsApp/Media/WhatsApp Video/Sent\",
  \"path_wa_sent_image\":
  \"/Android/media/com.whatsapp/WhatsApp/Media/WhatsApp Images/Sent\" },
  { \"min_version\": 0, \"max_version\": 29, \"enable\": true,
  \"path_wa_status\": \"WhatsApp/Media/.Statuses\",
  \"path_wa_sent_video\": \"WhatsApp/Media/WhatsApp Video/Sent\",
  \"path_wa_sent_image\": \"WhatsApp/Media/WhatsApp Images/Sent\" } \],
  \"compilation_rules\": { \"default\": 720, \"resolutions\": \[ {
  \"max\": 2147483647, \"min\": 2160, \"result\": 2160 }, { \"max\":
  2059, \"min\": 1080, \"result\": 1080 }, { \"max\": 1079, \"min\":
  641, \"result\": 720 }, { \"max\": 640, \"min\": 481, \"result\": 640
  }, { \"max\": 480, \"min\": 361, \"result\": 480 }, { \"max\": 360,
  \"min\": 1, \"result\": 360 } \] }, \"createPostConfig\": {
  \"noOfHashTagAllowed\": 5, \"noOfUserHandleAllowed\": 3,
  \"maxNumKeywords\": 5 }, \"uploadConfig\": {
  \"resumableUploadsEnabled\": true, \"failureAutoRetryThreshold\": 5,
  \"connectTimeout\": 60000, \"readTimeout\": 60000, \"writeTimeout\":
  60000, \"tusChunkSize\": 1048576, \"tusRequestPayloadSize\": -1,
  \"tusExtendedRetryDelays\": \[ 10000, 10000, 10000, 10000, 20000 \],
  \"tusNormalRetryDelays\": \[ 500, 1000, 2000, 3000 \] },
  \"lp_gotosetting_dialog_config\": { \"lp_gotosetting_dialog_title\":
  \"Allow Josh to access this device's location?\",
  \"lp_gotosetting_dialog_desc\": \"This will help you reach a more
  relevant audience &amp; gain followers, Please go to settings and
  allow location permission\", \"lp_gotosetting_dialog_pos_action\":
  \"Go To Settings\", \"lp_gotosetting_dialog_neg_action\": \"Later\",
  \"lp_gotosetting_dialog_show_after_x_post\": 4 }, \"postLangMapping\":
  \[ { \"languageGroup\": \[ \"na\" \], \"values\": \[ \"hi\", \"en\",
  \"te\", \"ta\", \"ml\", \"kn\", \"mr\", \"gu\", \"bn\", \"or\",
  \"pa\", \"bh\" \] }, { \"languageGroup\": \[ \"hi\", \"mr\", \"pa\",
  \"gu\", \"bh\", \"or\", \"bn\" \], \"values\": \[ \"hi\", \"mr\",
  \"pa\", \"gu\", \"bh\", \"or\", \"bn\", \"en\", \"te\", \"ta\",
  \"ml\", \"kn\" \] }, { \"languageGroup\": \[ \"te\", \"ta\", \"ml\",
  \"kn\" \], \"values\": \[ \"te\", \"ta\", \"ml\", \"kn\", \"hi\",
  \"en\", \"mr\", \"pa\", \"gu\", \"bh\", \"or\", \"bn\" \] } \],
  \"uploadShareConfig\": { \"shareChannels\": \[ { \"pkgName\":
  \"com.twitter.android\", \"iconUrl\": \"twitter\", \"name\":
  \"TWITTER\" }, { \"pkgName\": \"com.instagram.android\", \"iconUrl\":
  \"instagram\", \"name\": \"INSTAGRAM\" }, { \"pkgName\":
  \"com.facebook.katana\", \"iconUrl\": \"facebook\", \"name\":
  \"FACEBOOK\" }, { \"pkgName\": \"com.whatsapp\", \"iconUrl\":
  \"whatsapp\", \"name\": \"WHATSAPP\" } \], \"initialPollingDelayMs\":
  10000, \"pollingDelayMs\": 7000, \"maxPollingAttempts\": 15,
  \"shareNudgeCount\": 7, \"delaySharePromptHideMs\": 3000,
  \"delayPIPSuccessHideMs\": 5000 }, \"profileBlockedConfig\": {
  \"pb_config_title\": \"Profile Blocked!\", \"pb_config_subtitle\":
  \"This profile has been blocked due to violation of community
  guidelines.\", \"pb_config_cta\": \"Learn more\",
  \"pb_config_cta_link\":
  \"https://share.myjosh.in/help/community-violation-guidelines\",
  \"pb_config_subtitle_dialog\": \"You cannot post a video\",
  \"pb_config_cta_neg_dialog\": \"Dismiss\" },
  \"fpv_profile_quality_config\": \[ { \"network_quality\":
  \"veryfast\", \"profile_quality\": \"veryfast\" }, {
  \"network_quality\": \"fast\", \"profile_quality\": \"veryfast\" }, {
  \"network_quality\": \"good\", \"profile_quality\": \"veryfast\" }, {
  \"network_quality\": \"average\", \"profile_quality\": \"good\" }, {
  \"network_quality\": \"slow\", \"profile_quality\": \"average\" } \],
  \"fpv_quality_nudge_config\": { \"network_quality\": \"average\",
  \"message\": \"Slow Internet! Playing Video in Low Quality\",
  \"duration\": 3000, \"per_session_count\": 1 },
  \"deviceWakeUpConfiguration\": { \"minimumBatteryRequired\": 15,
  \"dndStartTime\": 82800, \"dndEndTime\": 21300, \"wakeDelay\":
  86400000 }, \"quality_mapping\": \[ { \"network_quality\":
  \"veryfast\", \"profile_quality\": \"fast\" }, { \"network_quality\":
  \"fast\", \"profile_quality\": \"fast\" }, { \"network_quality\":
  \"good\", \"profile_quality\": \"good\" }, { \"network_quality\":
  \"average\", \"profile_quality\": \"average\" }, {
  \"network_quality\": \"slow\", \"profile_quality\": \"slow\" } \],
  \"cache_config\": { \"cache_offline_directory_max_size_in_mb\": 200,
  \"cache_prefetch_directory_max_size_in_mb\": 250,
  \"cache_directory_max_size_in_mb\": 100, \"clear_session_data\":
  false, \"min_cache_item_to_fetch_api\": 5, \"hard_start_config\": {
  \"disableHardStart\": true, \"file_download_percentage\": 100,
  \"download_high_bitrate_variant\": true,
  \"min_stream_download_on_average_network\": 2,
  \"min_stream_download_on_fast_network\": 2,
  \"min_stream_download_on_good_network\": 2,
  \"min_stream_download_on_slow_network\": 2 },
  \"session_start_config\": { \"average\": {
  \"from_offline_back_to_back\": 10 }, \"fast\": {
  \"from_offline_back_to_back\": 10 }, \"good\": {
  \"from_offline_back_to_back\": 10 }, \"slow\": {
  \"from_offline_back_to_back\": 10 }, \"veryfast\": {
  \"from_offline_back_to_back\": 10 } }, \"prefetch_download_config\": {
  \"disable_cache\": false, \"prefetch_download_count_config\": {
  \"slow\": { \"no_of_videos\": 8, \"min_cache_percentage_ofl_to_onl\":
  100 }, \"average\": { \"no_of_videos\": 8,
  \"min_cache_percentage_ofl_to_onl\": 85 }, \"good\": {
  \"no_of_videos\": 8, \"min_cache_percentage_ofl_to_onl\": 70 },
  \"fast\": { \"no_of_videos\": 8, \"min_cache_percentage_ofl_to_onl\":
  50 }, \"veryfast\": { \"no_of_videos\": 8,
  \"min_cache_percentage_ofl_to_onl\": 50 } } },
  \"offline_download_config\": { \"sort_type\": \"recency\",
  \"disable_cache\": false, \"global_cache_ttl_days\": 180,
  \"max_cache_item\": 40, \"recommended_video_quality\": \"good\",
  \"ucq_download_config\": { \"average\": { \"exit\": 2, \"minimise\":
  1, \"notification\": 2 }, \"fast\": { \"exit\": 3, \"minimise\": 2,
  \"notification\": 2 }, \"slow\": { \"exit\": 2, \"minimise\": 1,
  \"notification\": 2 }, \"good\": { \"exit\": 3, \"minimise\": 2,
  \"notification\": 2 }, \"veryfast\": { \"exit\": 3, \"minimise\": 2,
  \"notification\": 2 } }, \"cache_api_sync_time_secs\": 259200,
  \"app_inactivity_duration_days\": 30 }, \"buffer_threshold_config\": {
  \"average\": { \"organic\": {
  \"buffer_threshold_initial_videos_secs\": 4,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 4 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 4,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 4 } },
  \"fast\": { \"organic\": { \"buffer_threshold_initial_videos_secs\":
  4, \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 4 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 4,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 4 } },
  \"slow\": { \"organic\": { \"buffer_threshold_initial_videos_secs\":
  4, \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 4 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 4,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 4 } },
  \"good\": { \"organic\": { \"buffer_threshold_initial_videos_secs\":
  4, \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 4 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 4,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 4 } },
  \"veryfast\": { \"organic\": {
  \"buffer_threshold_initial_videos_secs\": 4,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 4 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 4,
  \"initial_videos_max_index\": 5, \"buffer_threshold_secs\": 4 } } } },
  \"data_saver_cache_config\": {
  \"cache_offline_directory_max_size_in_mb\": 100,
  \"cache_prefetch_directory_max_size_in_mb\": 200,
  \"cache_directory_max_size_in_mb\": 100, \"clear_session_data\":
  false, \"recommended_profile\": \"average\",
  \"enable_notification_prefetch\": true,
  \"min_cache_item_to_fetch_api\": 5, \"session_start_config\": {
  \"slow\": { \"from_offline_back_to_back\": 1 }, \"average\": {
  \"from_offline_back_to_back\": 1 }, \"good\": {
  \"from_offline_back_to_back\": 1 }, \"fast\": {
  \"from_offline_back_to_back\": 1 }, \"veryfast\": {
  \"from_offline_back_to_back\": 1 } }, \"prefetch_download_config\": {
  \"disable_cache\": true, \"prefetch_download_count_config\": {
  \"slow\": { \"no_of_videos\": 0, \"min_cache_percentage_ofl_to_onl\":
  100 }, \"average\": { \"no_of_videos\": 0,
  \"min_cache_percentage_ofl_to_onl\": 80 }, \"good\": {
  \"no_of_videos\": 0, \"min_cache_percentage_ofl_to_onl\": 60 },
  \"fast\": { \"no_of_videos\": 0, \"min_cache_percentage_ofl_to_onl\":
  40 }, \"veryfast\": { \"no_of_videos\": 0,
  \"min_cache_percentage_ofl_to_onl\": 25 } } },
  \"offline_download_config\": { \"sort_type\": \"recency\",
  \"disable_cache\": true, \"global_cache_ttl_days\": 15,
  \"max_cache_item\": 40, \"recommended_video_quality\": \"good\",
  \"ucq_download_config\": { \"average\": { \"exit\": 0, \"minimise\":
  0, \"notification\": 0 }, \"fast\": { \"exit\": 0, \"minimise\": 0,
  \"notification\": 0 }, \"slow\": { \"exit\": 0, \"minimise\": 0,
  \"notification\": 0 }, \"good\": { \"exit\": 0, \"minimise\": 0,
  \"notification\": 0 }, \"veryfast\": { \"exit\": 0, \"minimise\": 0,
  \"notification\": 0 } }, \"cache_api_sync_time_secs\": 86400,
  \"app_inactivity_duration_days\": 10 }, \"buffer_threshold_config\": {
  \"average\": { \"organic\": {
  \"buffer_threshold_initial_videos_secs\": 6,
  \"initial_videos_max_index\": 7, \"buffer_threshold_secs\": 6 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 6,
  \"initial_videos_max_index\": 7, \"buffer_threshold_secs\": 6 } },
  \"fast\": { \"organic\": { \"buffer_threshold_initial_videos_secs\":
  6, \"initial_videos_max_index\": 7, \"buffer_threshold_secs\": 6 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 6,
  \"initial_videos_max_index\": 7, \"buffer_threshold_secs\": 6 } },
  \"slow\": { \"organic\": { \"buffer_threshold_initial_videos_secs\":
  6, \"initial_videos_max_index\": 7, \"buffer_threshold_secs\": 6 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 6,
  \"initial_videos_max_index\": 7, \"buffer_threshold_secs\": 6 } },
  \"good\": { \"organic\": { \"buffer_threshold_initial_videos_secs\":
  6, \"initial_videos_max_index\": 7, \"buffer_threshold_secs\": 6 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 6,
  \"initial_videos_max_index\": 7, \"buffer_threshold_secs\": 6 } },
  \"veryfast\": { \"organic\": {
  \"buffer_threshold_initial_videos_secs\": 6,
  \"initial_videos_max_index\": 7, \"buffer_threshold_secs\": 6 },
  \"inorganic\": { \"buffer_threshold_initial_videos_secs\": 6,
  \"initial_videos_max_index\": 7, \"buffer_threshold_secs\": 6 } } } },
  \"duet_config\": { \"camera_portrait_min_height_to_width\": { \"h\":
  16, \"w\": 9 }, \"camera_portrait_max_height_to_width\": { \"h\": 21,
  \"w\": 9 }, \"camera_landscape_min_width_to_height\": { \"h\": 8,
  \"w\": 9 }, \"camera_landscape_max_width_to_height\": { \"h\": 9,
  \"w\": 21 }, \"video_download_url\": \"\",
  \"create_and_edit_configs\": { \"duetable_config_for_verified\": {
  \"default_value\": \"OFF\", \"aspect_ratio\": {
  \"allow_for_portrait\": true, \"allow_for_square\": true,
  \"allow_for_landscape\": false }, \"video_source\": {
  \"camera_with_josh_library\": true, \"camera_without_josh_library\":
  true, \"gallery_with_josh_library\": true,
  \"gallery_without_josh_library\": true, \"duet\": false },
  \"video_source_v2\": \[ { \"srcType\": \"camera\", \"josh_library\":
  true, \"non_josh_library\": true }, { \"srcType\": \"gallery\",
  \"josh_library\": true, \"non_josh_library\": true }, { \"srcType\":
  \"multi_segment_camera\", \"josh_library\": true,
  \"non_josh_library\": true }, { \"srcType\":
  \"multi_segment_gallery\", \"josh_library\": true,
  \"non_josh_library\": true }, { \"srcType\":
  \"multi_segment_camera_gallery\", \"josh_library\": true,
  \"non_josh_library\": true }, { \"srcType\": \"external_d-id\",
  \"josh_library\": true, \"non_josh_library\": true }, { \"srcType\":
  \"external\", \"josh_library\": true, \"non_josh_library\": true }, {
  \"srcType\": \"duet\", \"josh_library\": false, \"non_josh_library\":
  false } \] }, \"duetable_config_for_nonverified\": {
  \"default_value\": \"OFF\", \"aspect_ratio\": {
  \"allow_for_portrait\": true, \"allow_for_square\": true,
  \"allow_for_landscape\": false }, \"video_source\": {
  \"camera_with_josh_library\": true, \"camera_without_josh_library\":
  true, \"gallery_with_josh_library\": true,
  \"gallery_without_josh_library\": true, \"duet\": false },
  \"video_source_v2\": \[ { \"srcType\": \"camera\", \"josh_library\":
  true, \"non_josh_library\": true }, { \"srcType\": \"gallery\",
  \"josh_library\": true, \"non_josh_library\": true }, { \"srcType\":
  \"multi_segment_camera\", \"josh_library\": true,
  \"non_josh_library\": true }, { \"srcType\":
  \"multi_segment_gallery\", \"josh_library\": true,
  \"non_josh_library\": true }, { \"srcType\":
  \"multi_segment_camera_gallery\", \"josh_library\": true,
  \"non_josh_library\": true }, { \"srcType\": \"external_d-id\",
  \"josh_library\": true, \"non_josh_library\": true }, { \"srcType\":
  \"external\", \"josh_library\": true, \"non_josh_library\": true }, {
  \"srcType\": \"duet\", \"josh_library\": false, \"non_josh_library\":
  false } \] } } }, \"splash_time\": 2000, \"splashTime\": 1000,
  \"fire_track_from_cache\": true, \"handshake_version\": \"470\",
  \"performance_analytics_enabled\": false, \"upload_duration\": 120,
  \"disable_error_event\": false, \"disable_slow_network_prompts\":
  false, \"speed_quality_map\": { \"100\": \"slow\", \"500\":
  \"average\", \"1000\": \"good\", \"10000\": \"fast\", \"50000\":
  \"veryfast\" }, \"record_duration\": 15, \"first_time_pull_delay\":
  300, \"first_chunk_request_params\": { \"cdn\": \"Y\", \"src\":
  \"app\" }, \"max_upload_size\": 200, \"upgrade\": \"LATEST\",
  \"rateConfig\": { \"enable\": true,
  \"preActivitySessionWaitTimeInSeconds\": 600,
  \"minNumberOfStoriesViewedPerSession\": 10, \"minNumberOfBooksRead\":
  4, \"maxNumberOfTimesToShowRateScreen\": 3,
  \"minNumberOfDaysToWaitShowingRateScreen\": 30,
  \"maxWaitDaysForNewUsersToShowRateScreen\": 7,
  \"minLaunchesForNewUsersToShowRateScreen\": 3,
  \"minNumberOfDaysUserToWaitAfterLastSeen\": 10,
  \"minNumberOfAppLaunchesToWaitAfterLastSeen\": 10 },
  \"maxHistoryCount\": 50, \"enable_reactions_api_hit\": true,
  \"max_recent_interaction_count\": 50,
  \"location_fetch_interval_in_seconds\": 86400,
  \"min_gap_between_app_update_prompt_secs\": 172800,
  \"video_views_in_session_for_update_prompt\": 5, \"permission\": {
  \"id\": 24, \"event\": \"appLaunch\", \"activity\": { \"type\":
  \"permission\", \"attributes\": { \"gapCount\": \"4\", \"permDesc\":
  \"Josh needs access to the following\", \"permTitle\": \"Permissions
  required\", \"openSettings\": \"Josh needs storage access to perform
  this action. To enable it, please visit your app settings.\",
  \"settingsAction\": \"Settings\", \"storagePermDesc\": \"We need this
  for critical features like downloading a video.\",
  \"locationPermDesc\": \"We need this to show you videos being posted
  by users around you.\", \"storagePermSubtitle\": \"Storage Access\",
  \"locationPermSubtitle\": \"Location Access\",
  \"permissionNegativeBtn\": \"LATER\", \"permissionPositiveBtn\":
  \"Allow\" } }, \"resource\": \"coolfie\", \"precondition\": {
  \"minItemsViewed\": 7, \"minTimeEngaged\": 0, \"maxNumberOfDisplay\":
  0, \"minNumberOfOccurences\": 5 } }, \"fire_comscore_from_cache\":
  true, \"max_notifications_in_tray\": 6, \"thumbnail_qualities\": {
  \"fast\": { \"quality\": \"h\", \"resolution\": 480 }, \"good\": {
  \"quality\": \"h\", \"resolution\": 480 }, \"slow\": { \"quality\":
  \"h\", \"resolution\": 480 }, \"average\": { \"quality\": \"h\",
  \"resolution\": 480 } }, \"default_notification_duration\": 120,
  \"max_upload_bitrate\": 1500, \"pull_notifications_enabled\": true,
  \"video_qualities\": { \"fast\": { \"quality\": \"h\", \"resolution\":
  480 }, \"good\": { \"quality\": \"h\", \"resolution\": 480 },
  \"slow\": { \"quality\": \"h\", \"resolution\": 480 }, \"average\": {
  \"quality\": \"h\", \"resolution\": 480 } },
  \"disable_firebase_perf\": false, \"google_play_url\": {
  \"share_video_text\": \"Download Josh for more videos like this!\",
  \"download_video_text\": \"Download Josh for more videos like this!\",
  \"share_google_play_url\": \"https://m.myjosh.in/6OaT/32e07bf\",
  \"setting_google_play_url\": \"https://m.myjosh.in/6OaT/568901e6\",
  \"download_google_play_url\": \"https://m.myjosh.in/6OaT/6d76ce25\",
  \"download_live_stream_text\": \"Download Josh for more livestreams
  like this!\", \"duet_share_text\": \"Create and watch amazing duets
  with %1\$s! \\n%2\$s \\nDownload Josh now to watch & even create more
  great videos like this!
  \\nhttps://play.google.com/store/apps/details?id=com.eterno.shortvideos\"
  }, \"default_notification_text\": \"Welcome to Josh! Check out the
  latest news in your preferred language.\",
  \"story_detail_error_page_url\":
  \"https://m.dailyhunt.in/webItem/errorPage.html\",
  \"share_floating_icon_type\": \"floatingIconBentArrow\",
  \"upload_format_list\": \[ \"3gp\", \"mp4\" \], \"nlfc_config\": {
  \"disable_nlfc\": false, \"min_time_spent_to_trigger\": 9000,
  \"min_time_spent_to_trigger_with_social\": 9000,
  \"min_percentage_completion\": 85,
  \"skip_nlfc_for_session_on_failure\": 3, \"min_offset_to_append\": 1
  }, \"moderationNsfwReportUrl\":
  \"https://share.myjosh.in/report/machine-moderation/1\",
  \"moderationDuplicateReportUrl\":
  \"https://share.myjosh.in/report/ownership-content/1\",
  \"joshCam1Config\": { \"licenseUrl\":
  \"https://stream.myjosh.in/stream/prod-ugc-contents/joshCam1Config/license/android/20986-269-0d067db8c6410857b82bc96e5405a5e9.lic\",
  \"licenseUrliOS\":
  \"https://stream.myjosh.in/stream/prod-ugc-contents/joshCam1Config/license/ios/20986-316-98dbba5e3c21614641960fd652004345.lic\"
  }, \"sdkType\": \"JOSH_CAM1\", \"followersTabName\": \"Top Fans\",
  \"handshakeDefaultInterval\": 86400000, \"maxApiDelay\": 2000,
  \"maxErrorEventPerInterval\": 10, \"upload_duration_v2\": 60,
  \"min_upload_duration\": 5, \"max_recent_navigable_action_count\": 30,
  \"timerPeriodInSeconds\": 60, \"firstTimePullDelay\": 60,
  \"enable_whatsapp_share\": true, \"enable_video_download_on_share\":
  true, \"hit_firebase_event_once\": true, \"enableGzip_v2\": true,
  \"allowEmptyTitleInCreatePost\": false, \"is_firebase_event_enabled\":
  true, \"dev_error_for_2xxTo4xx_enabled\": false,
  \"location_prompt_for_max_time_count\": 3,
  \"location_prompt_after_max_post_count\": 0, \"video_resources\": {
  \"1\": \"https://gateway.myjosh.in/api/v1/materialinfo/1?version=1\",
  \"2\":
  \"https://gateway.myjosh.in/api/v1/materialinfo/2?version=888\",
  \"3\": \"https://gateway.myjosh.in/api/v1/materialinfo/3?version=1\",
  \"4\": \"https://gateway.myjosh.in/api/v1/materialinfo/4?version=1\",
  \"5\": \"https://gateway.myjosh.in/api/v1/materialinfo/5?version=1\",
  \"6\": \"https://gateway.myjosh.in/api/v1/materialinfo/6?version=1\",
  \"7\": \"https://gateway.myjosh.in/api/v1/materialinfo/7?version=1\",
  \"8\": \"https://gateway.myjosh.in/api/v1/materialinfo/8?version=1\",
  \"9\": \"https://gateway.myjosh.in/api/v1/materialinfo/9?version=1\",
  \"10\":
  \"https://gateway.myjosh.in/api/v1/materialinfo/10?version=1\",
  \"11\":
  \"https://gateway.myjosh.in/api/v1/materialinfo/11?version=1\",
  \"12\":
  \"https://gateway.myjosh.in/api/v1/materialinfo/12?version=1\",
  \"13\":
  \"https://gateway.myjosh.in/api/v1/materialinfo/13?version=1\",
  \"14\":
  \"https://gateway.myjosh.in/api/v1/materialinfo/14?version=139\",
  \"15\":
  \"https://gateway.myjosh.in/api/v1/materialinfo/15?version=1\",
  \"16\":
  \"https://gateway.myjosh.in/api/v1/materialinfo/16?version=1\",
  \"17\":
  \"https://gateway.myjosh.in/api/v1/materialinfo/17?version=1\",
  \"24\":
  \"https://gateway.myjosh.in/api/v1/materialinfo/24?version=1\",
  \"25\":
  \"https://gateway.myjosh.in/api/v1/materialinfo/25?version=7\",
  \"26\":
  \"https://gateway.myjosh.in/api/v1/materialinfo/26?version=259\",
  \"27\":
  \"https://gateway.myjosh.in/api/v1/materialinfo/27?version=2\",
  \"28\":
  \"https://gateway.myjosh.in/api/v1/materialinfo/28?version=1\",
  \"29\":
  \"https://gateway.myjosh.in/api/v1/materialinfo/29?version=1\",
  \"30\":
  \"https://gateway.myjosh.in/api/v1/materialinfo/30?version=140\",
  \"31\":
  \"https://gateway.myjosh.in/api/v1/materialinfo/31?version=10\",
  \"32\":
  \"https://gateway.myjosh.in/api/v1/materialinfo/32?version=7\",
  \"33\":
  \"https://gateway.myjosh.in/api/v1/materialinfo/33?version=1\",
  \"34\":
  \"https://gateway.myjosh.in/api/v1/materialinfo/34?version=42\",
  \"35\":
  \"https://gateway.myjosh.in/api/v1/materialinfo/35?version=2\",
  \"36\":
  \"https://gateway.myjosh.in/api/v1/materialinfo/36?version=1\",
  \"37\": \"https://gateway.myjosh.in/api/v1/materialinfo/37?version=2\"
  }, \"following_sync_interval_in_seconds\": 86400,
  \"appsOnDeviceEnabled\": false, \"appsOnDeviceEnabledV2\": true,
  \"cleanupConfig\": { \"maxMusicDownloads\": 20,
  \"maxStickerDownloads\": 100, \"maxCommentStickerDownloads\": 100,
  \"maEffectsDownloads\": 50 }, \"network_config\": {
  \"exo_weightage_double\": 0.8, \"network_weightage_double\": 2,
  \"sliding_percentile_percentile\": 0.5, \"bitrate_expression\": {
  \"id\": \"1\", \"formula\": \"(e\*0.8)+(n\*2)\" },
  \"bitrate_expression_exception\": { \"id\": \"2\", \"formula\":
  \"(e\*0.8)+(n\*0.7)\" }, \"bitrate_expression_v2\": { \"id\": \"3\",
  \"formula\": \"function f42(e,n){ \\n if(e\<n) return e\*0.8+n\*0.7;
  \\n else { var wa=e\*e/(e+n)+n\*n/(e+n); return
  Math.min(wa,e);};\\n};\" }, \"lifetime_bitrate_capture_window_sec\":
  604800, \"coldstart_transition_threshold_sec\": 10,
  \"coldstart_network_provider_mapping\": \[ { \"network\": \"4G\",
  \"provider\": \"Jio 4G\", \"quality\": \"good\" }, { \"network\":
  \"4G\", \"provider\": \"airtel\", \"quality\": \"good\" }, {
  \"network\": \"4G\", \"provider\": \"Vi India\", \"quality\": \"good\"
  }, { \"network\": \"4G\", \"provider\": \"IND airtel\", \"quality\":
  \"good\" }, { \"network\": \"4G\", \"provider\": \"Vodafone IN\",
  \"quality\": \"good\" }, { \"network\": \"4G\", \"provider\":
  \"Airtel\", \"quality\": \"good\" }, { \"network\": \"4G\",
  \"provider\": \"Idea\", \"quality\": \"good\" }, { \"network\":
  \"4G\", \"provider\": \"JIO 4G\", \"quality\": \"good\" }, {
  \"network\": \"w\", \"provider\": \"Jio 4G\", \"quality\": \"fast\" },
  { \"network\": \"w\", \"provider\": \"airtel\", \"quality\": \"fast\"
  }, { \"network\": \"4G\", \"provider\": \"JIO\", \"quality\": \"good\"
  }, { \"network\": \"4G\", \"provider\": \"AIRTEL\", \"quality\":
  \"good\" }, { \"network\": \"3G\", \"provider\": \"Vi India\",
  \"quality\": \"avg\", \"maxQuality\": \"good\" }, { \"network\":
  \"w\", \"provider\": \"Vi India\", \"quality\": \"fast\" }, {
  \"network\": \"4G\", \"provider\": \"VIL\", \"quality\": \"good\" }, {
  \"network\": \"4G\", \"provider\": \"Vodafone\", \"quality\": \"good\"
  }, { \"network\": \"w\", \"provider\": \"Vodafone IN\", \"quality\":
  \"fast\" }, { \"network\": \"w\", \"provider\": \"IND airtel\",
  \"quality\": \"fast\" }, { \"network\": \"2G\", \"provider\":
  \"airtel\", \"quality\": \"slow\", \"maxQuality\": \"avg\" }, {
  \"network\": \"4G\", \"provider\": \"Airtel \| airtel\", \"quality\":
  \"good\" }, { \"network\": \"4G\", \"provider\": \"IND AirTel\",
  \"quality\": \"good\" }, { \"network\": \"3G\", \"provider\":
  \"Vodafone IN\", \"quality\": \"avg\", \"maxQuality\": \"good\" }, {
  \"network\": \"w\", \"provider\": \"Idea\", \"quality\": \"fast\" }, {
  \"network\": \"4G\", \"provider\": \"JIO 4G \| Jio 4G\", \"quality\":
  \"good\" }, { \"network\": \"4G\", \"provider\": \"AirTel\",
  \"quality\": \"good\" }, { \"network\": \"3G\", \"provider\":
  \"Idea\", \"quality\": \"avg\", \"maxQuality\": \"good\" }, {
  \"network\": \"4G\", \"provider\": \"Vi India \| Vodafone IN\",
  \"quality\": \"good\" }, { \"network\": \"2G\", \"provider\": \"Vi
  India\", \"quality\": \"slow\", \"maxQuality\": \"avg\" }, {
  \"network\": \"w\", \"provider\": \"Airtel\", \"quality\": \"fast\" },
  { \"network\": \"3G\", \"provider\": \"BSNL MOBILE\", \"quality\":
  \"avg\", \"maxQuality\": \"good\" }, { \"network\": \"4G\",
  \"provider\": \"BSNL MOBILE\", \"quality\": \"good\" }, { \"network\":
  \"4G\", \"provider\": \"Vi India \| Idea\", \"quality\": \"good\" }, {
  \"network\": \"3G\", \"provider\": \"BSNL Mobile\", \"quality\":
  \"avg\", \"maxQuality\": \"good\" }, { \"network\": \"4G\",
  \"provider\": \"BSNL Mobile\", \"quality\": \"good\" }, { \"network\":
  \"4G\", \"provider\": \"IDEA\", \"quality\": \"good\" }, {
  \"network\": \"w\", \"provider\": \"JIO 4G\", \"quality\": \"fast\" },
  { \"network\": \"w\", \"provider\": \"BSNL MOBILE\", \"quality\":
  \"fast\" }, { \"network\": \"4G\", \"provider\": \"Jio\", \"quality\":
  \"good\" }, { \"network\": \"4G\", \"provider\": \"Airtel_BH\",
  \"quality\": \"good\" }, { \"network\": \"w\", \"provider\": \"BSNL
  Mobile\", \"quality\": \"fast\" }, { \"network\": \"2G\",
  \"provider\": \"Idea\", \"quality\": \"slow\", \"maxQuality\": \"avg\"
  }, { \"network\": \"2G\", \"provider\": \"Vodafone IN\", \"quality\":
  \"slow\", \"maxQuality\": \"avg\" }, { \"network\": \"4G\",
  \"provider\": \"!dea\", \"quality\": \"good\" }, { \"network\":
  \"3G\", \"provider\": \"CellOne\", \"quality\": \"avg\",
  \"maxQuality\": \"good\" }, { \"network\": \"4G\", \"provider\":
  \"JIO4G\", \"quality\": \"good\" }, { \"network\": \"4G\",
  \"provider\": \"Airtel Stay Home\", \"quality\": \"good\" }, {
  \"network\": \"2G\", \"provider\": \"Airtel\", \"quality\": \"slow\",
  \"maxQuality\": \"avg\" }, { \"network\": \"w\", \"provider\":
  \"JIO\", \"quality\": \"fast\" }, { \"network\": \"2G\", \"provider\":
  \"IND airtel\", \"quality\": \"slow\", \"maxQuality\": \"avg\" }, {
  \"network\": \"0\", \"provider\": \"Jio 4G\", \"quality\": \"fast\" },
  { \"network\": \"3G\", \"provider\": \"airtel\", \"quality\": \"avg\",
  \"maxQuality\": \"good\" }, { \"network\": \"WiFi\", \"provider\":
  \"AirTel\", \"quality\": \"fast\" }, { \"network\": \"4G\",
  \"provider\": \"unknown\", \"quality\": \"good\" }, { \"network\":
  \"WiFi\", \"provider\": \"unknown\", \"quality\": \"fast\" }, {
  \"network\": \"WiFi\", \"provider\": \"Jio\", \"quality\": \"fast\" },
  { \"network\": \"4G\", \"provider\": \"CellOne\", \"quality\":
  \"good\" }, { \"network\": \"3G\", \"provider\": \"!dea\",
  \"quality\": \"avg\", \"maxQuality\": \"good\" }, { \"network\":
  \"w\", \"provider\": \"VIL\", \"quality\": \"fast\" }, { \"network\":
  \"4G\", \"provider\": \"Ind-Jio\", \"quality\": \"good\" }, {
  \"network\": \"w\", \"provider\": \"Vi India \| Vodafone IN\",
  \"quality\": \"fast\" }, { \"network\": \"3G\", \"provider\": \"VIL\",
  \"quality\": \"avg\", \"maxQuality\": \"good\" }, { \"network\":
  \"4G\", \"provider\": \"Emergency calls only\", \"quality\": \"good\"
  }, { \"network\": \"2G\", \"provider\": \"Jio 4G\", \"quality\":
  \"slow\", \"maxQuality\": \"avg\" }, { \"network\": \"3G\",
  \"provider\": \"Vodafone\", \"quality\": \"avg\", \"maxQuality\":
  \"good\" }, { \"network\": \"3G\", \"provider\": \"Jio 4G\",
  \"quality\": \"avg\", \"maxQuality\": \"good\" }, { \"network\":
  \"w\", \"provider\": \"AIRTEL\", \"quality\": \"fast\" }, {
  \"network\": \"4G\", \"provider\": \"No service\", \"quality\":
  \"good\" }, { \"network\": \"w\", \"provider\": \"Vi India \| Idea\",
  \"quality\": \"fast\" }, { \"network\": \"0\", \"provider\":
  \"airtel\", \"quality\": \"fast\" }, { \"network\": \"w\",
  \"provider\": \"Vodafone\", \"quality\": \"fast\" }, { \"network\":
  \"4G\", \"provider\": \"Any\", \"quality\": \"good\" }, { \"network\":
  \"3G\", \"provider\": \"Any\", \"quality\": \"avg\", \"maxQuality\":
  \"good\" }, { \"network\": \"2G\", \"provider\": \"Any\", \"quality\":
  \"slow\", \"maxQuality\": \"avg\" }, { \"network\": \"Any\",
  \"provider\": \"Any\", \"quality\": \"good\" } \],
  \"exo_sliding_percentile_max_weight\": 1000 },
  \"speed_quality_map_v2\": { \"200\": \"slow\", \"2000\": \"average\",
  \"6000\": \"good\", \"8000\": \"fast\", \"16000\": \"veryfast\" },
  \"cameraProperties\": { \"videoCaptureResolution\":
  \"EXTREMELY_HIGH\", \"recordBitrate\": \"3000000\", \"fps\": \"30\",
  \"audioSampleRate\": \"44100\", \"autoFocus\": \"Y\",
  \"autoExposure\": \"Y\", \"sharpness\": \"Y\", \"beautify\": \"Y\",
  \"Intensity\": \"0.2\", \"videoStabilization\": \"Y\",
  \"continuousFocus\": \"Y\", \"zoom\": \"Y\", \"maxZoom\": \"99\",
  \"bitDepth\": \"8\", \"compileBitrate\": \"3000000\",
  \"audioBitrate\": \"160000\", \"losslessAudio\": \"true\",
  \"encoderPreset\": \"MEDIUM\", \"encoderCRF\": \"17\",
  \"encoderName\": \"H.265\", \"encoderProfile\": \"high\", \"HDR\":
  \"none\" }, \"cameraPropertiesiOS\": { \"videoCaptureResolution\":
  \"SUPER_HIGH\", \"recordBitrate\": \"3000000\", \"fps\": \"30\",
  \"audioSampleRate\": \"44100\", \"autoFocus\": \"Y\",
  \"autoExposure\": \"Y\", \"sharpness\": \"Y\", \"beautify\": \"Y\",
  \"Intensity\": \"0.2\", \"videoStabilization\": \"Y\",
  \"continuousFocus\": \"Y\", \"zoom\": \"Y\", \"maxZoom\": \"99\",
  \"bitDepth\": \"8\", \"compileBitrate\": \"3000000\",
  \"audioBitrate\": \"160000\", \"losslessAudio\": \"true\",
  \"encoderPreset\": \"MEDIUM\", \"encoderCRF\": \"17\",
  \"encoderName\": \"H.265\", \"encoderProfile\": \"high\", \"HDR\":
  \"none\" }, \"max_consumed_cache_items_count\": 30, \"attRules\": {
  \"enableATTPrompt\": true, \"attPromptConfig\": {
  \"minInstallLaunchCount\": 2, \"minUpgradeLaunchCount\": 3,
  \"coolOffLaunchCount\": 2, \"maxAttemptCount\": 30, \"title\":
  \"Personalized Ads\", \"message\": \"Josh would like permission to
  serve personalized ads to you\" } }, \"quicHints\": \[ { \"host\":
  \"stream-g.myjosh.in\", \"port\": 443, \"alternatePort\": 443 } \],
  \"bookmarkConfig\": { \"musicTrimNudgeCount\": 5,
  \"bookMarkNudgeCount\": 5, \"bookmarkSyncMinimumGap\": 86400000 },
  \"reactivate_account_config\": { \"temporarily_deactivated_title\":
  \"We missed you\...\", \"temporarily_deactivated_sub_title\": \"Tap
  the button below to reactivate\\nyour account\",
  \"temporarily_deactivated_cta_text\": \"Reactivate Account\",
  \"permanently_deactivated_title\": \"This account has been permanently
  deleted\", \"permanently_deactivated_sub_title\": \"To use Josh,
  create a new account.\", \"permanently_deactivated_cta_text\":
  \"Create New Account\" }, \"csConfig\": { \"enabled\": true,
  \"frequencyTimeMS\": 86400000, \"bucketSizeNew\": 2000 },
  \"profile_wizard_config\": { \"completeMsgDismissTimeInMills\": 3000,
  \"setUpProfileMsgShowTimeInDays\": 360 }, \"fileUploads\": {
  \"twitter\":
  \"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/Twitter-Logo.webp\",
  \"instagram\":
  \"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/Instagram-Logo.webp\",
  \"facebook\":
  \"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/Facebook-Logo.webp\",
  \"whatsapp\":
  \"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/Whatsapp-Logo.webp\",
  \"uploads\":
  \"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/VmlkZW8=.png\",
  \"trending\":
  \"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/VHJlbmRpbmdfMQ==.png\",
  \"likes\":
  \"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/TGlrZV8x.png\",
  \"drafts\":
  \"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/ZHJhZnRz.png\",
  \"tagged\":
  \"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/TWVudGlvbl8x.png\",
  \"audio_icon\":
  \"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/bXVzaWM=.png\",
  \"discovery_icon\":
  \"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/ZGlzY292ZXJ5.png\",
  \"trending_icon\":
  \"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/TmV3X1RyZW5kaW5nX0ljb25fMQ==.png\",
  \"photos\":
  \"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/UGhvdG9fTmV3XzE=.png\",
  \"tipping_icon_url\":
  \"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/Z2lmdF9pY29u.png\",
  \"gifting_icon_url\":
  \"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/Z2lmdF9pY29u.png\",
  \"uploads_selected\":
  \"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/dXBsb2Fkc19zZWxlY3RlZA==.png\",
  \"trending_selected\":
  \"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/dHJlbmRpbmdfc2VsZWN0ZWQ=.png\",
  \"tagged_selected\":
  \"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/dGFnZ2VkX3NlbGVjdGVk.png\",
  \"social_selected\":
  \"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/c29jaWFsX3NlbGVjdGVk.png\",
  \"photos_selected\":
  \"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/cGhvdG9zX3NlbGVjdGVk.png\",
  \"likes_selected\":
  \"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/bGlrZXNfc2VsZWN0ZWQ=.png\",
  \"drafts_selected\":
  \"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/ZHJhZnRzX3NlbGVjdGVk.png\",
  \"social\":
  \"https://stream.myjosh.in/stream/prod-ugc-contents/josh_version_content/JOSH_STATIC_CONFIG/c29jaWFs.png\"
  } } } }
