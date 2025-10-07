**[Index Definition:]{.underline}**

jsonPUT ugc-contests-v2 { \"mappings\" : { \"properties\" : {
\"agg_modified_at\" : { \"type\" : \"text\", \"fields\" : { \"keyword\"
: { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"animated_icon_transcoding_status\" : { \"type\" : \"text\", \"fields\"
: { \"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } }
}, \"animated_icon_transcoding_time\" : { \"type\" : \"date\" },
\"animated_icon_url\" : { \"type\" : \"text\", \"fields\" : {
\"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"audio_id\" : { \"type\" : \"text\", \"fields\" : { \"keyword\" : {
\"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"auto_moderation_label\" : { \"type\" : \"text\", \"fields\" : {
\"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"auto_moderation_reason\" : { \"type\" : \"text\", \"fields\" : {
\"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"background_color_code\" : { \"type\" : \"text\", \"fields\" : {
\"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"background_image_file_name\" : { \"type\" : \"text\", \"fields\" : {
\"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"background_image_file_path\" : { \"type\" : \"text\", \"fields\" : {
\"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"background_image_url_file_name\" : { \"type\" : \"text\", \"fields\" :
{ \"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"background_image_url_file_path\" : { \"type\" : \"text\", \"fields\" :
{ \"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"banner_data\" : { \"properties\" : { \"c1_b1\" : { \"properties\" : {
\"element_cta\" : { \"type\" : \"text\", \"fields\" : { \"keyword\" : {
\"type\" : \"keyword\", \"ignore_above\" : 256 } } }, \"id\" : {
\"type\" : \"text\", \"fields\" : { \"keyword\" : { \"type\" :
\"keyword\", \"ignore_above\" : 256 } } }, \"view_order\" : { \"type\" :
\"long\" } } } } }, \"banner_height\" : { \"type\" : \"long\" },
\"banner_width\" : { \"type\" : \"long\" }, \"batch_seq\" : { \"type\" :
\"long\" }, \"bit_rate\" : { \"type\" : \"text\", \"fields\" : {
\"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"bit_rate_int\" : { \"type\" : \"long\" }, \"bn_like_count\" : {
\"type\" : \"long\" }, \"bn_p_score_v2\" : { \"type\" : \"float\" },
\"bn_rewards\" : { \"properties\" : { \"12hr\" : { \"properties\" : {
\"a\" : { \"type\" : \"long\" }, \"b\" : { \"type\" : \"long\" } } },
\"16hr\" : { \"properties\" : { \"a\" : { \"type\" : \"long\" }, \"b\" :
{ \"type\" : \"long\" } } }, \"1hr\" : { \"properties\" : { \"a\" : {
\"type\" : \"long\" }, \"b\" : { \"type\" : \"long\" } } }, \"4hr\" : {
\"properties\" : { \"a\" : { \"type\" : \"long\" }, \"b\" : { \"type\" :
\"long\" } } }, \"8hr\" : { \"properties\" : { \"a\" : { \"type\" :
\"long\" }, \"b\" : { \"type\" : \"long\" } } }, \"life\" : {
\"properties\" : { \"a\" : { \"type\" : \"long\" }, \"b\" : { \"type\" :
\"long\" } } } } }, \"bn_t_score_v2\" : { \"type\" : \"float\" },
\"bn_view_count\" : { \"type\" : \"long\" }, \"category_dialog_title\" :
{ \"type\" : \"text\", \"fields\" : { \"keyword\" : { \"type\" :
\"keyword\", \"ignore_above\" : 256 } } }, \"category_search\" : {
\"type\" : \"text\", \"fields\" : { \"keyword\" : { \"type\" :
\"keyword\", \"ignore_above\" : 256 } } }, \"content_category\" : {
\"type\" : \"text\", \"fields\" : { \"keyword\" : { \"type\" :
\"keyword\", \"ignore_above\" : 256 } } }, \"content_category_id\" : {
\"type\" : \"text\", \"fields\" : { \"keyword\" : { \"type\" :
\"keyword\", \"ignore_above\" : 256 } } }, \"content_title\" : {
\"type\" : \"text\", \"fields\" : { \"keyword\" : { \"type\" :
\"keyword\", \"ignore_above\" : 256 } } }, \"content_uuid\" : { \"type\"
: \"text\", \"fields\" : { \"keyword\" : { \"type\" : \"keyword\",
\"ignore_above\" : 256 } } }, \"contest_category_id\" : { \"type\" :
\"text\", \"fields\" : { \"keyword\" : { \"type\" : \"keyword\",
\"ignore_above\" : 256 } } }, \"contest_id\" : { \"type\" : \"text\",
\"fields\" : { \"keyword\" : { \"type\" : \"keyword\", \"ignore_above\"
: 256 } } }, \"contest_type\" : { \"type\" : \"text\", \"fields\" : {
\"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"control_config\" : { \"properties\" : { \"allow_commenting\" : {
\"type\" : \"text\", \"fields\" : { \"keyword\" : { \"type\" :
\"keyword\", \"ignore_above\" : 256 } } }, \"allow_download\" : {
\"type\" : \"text\", \"fields\" : { \"keyword\" : { \"type\" :
\"keyword\", \"ignore_above\" : 256 } } }, \"hashtag_clickable\" : {
\"type\" : \"text\", \"fields\" : { \"keyword\" : { \"type\" :
\"keyword\", \"ignore_above\" : 256 } } } } }, \"created_date\" : {
\"type\" : \"date\" }, \"created_day\" : { \"type\" : \"date\" },
\"custom_search_fields\" : { \"type\" : \"text\", \"fields\" : {
\"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"description\" : { \"type\" : \"text\", \"fields\" : { \"keyword\" : {
\"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"disable_in_feed\" : { \"type\" : \"boolean\" }, \"download_count\" : {
\"type\" : \"long\" }, \"download_url\" : { \"type\" : \"text\",
\"fields\" : { \"keyword\" : { \"type\" : \"keyword\", \"ignore_above\"
: 256 } } }, \"download_uu\" : { \"type\" : \"long\" },
\"duet_file_available\" : { \"type\" : \"boolean\" }, \"duet_meta\" : {
\"properties\" : { \"creator_id\" : { \"type\" : \"text\", \"fields\" :
{ \"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"creator_user_name\" : { \"type\" : \"text\", \"fields\" : {
\"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"creator_verified\" : { \"type\" : \"boolean\" }, \"duetable\" : {
\"type\" : \"text\", \"fields\" : { \"keyword\" : { \"type\" :
\"keyword\", \"ignore_above\" : 256 } } }, \"video_id\" : { \"type\" :
\"text\", \"fields\" : { \"keyword\" : { \"type\" : \"keyword\",
\"ignore_above\" : 256 } } } } }, \"duet_transcoding_status\" : {
\"type\" : \"text\", \"fields\" : { \"keyword\" : { \"type\" :
\"keyword\", \"ignore_above\" : 256 } } }, \"duet_transcoding_time\" : {
\"type\" : \"date\" }, \"duet_url\" : { \"type\" : \"text\", \"fields\"
: { \"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } }
}, \"duetable\" : { \"type\" : \"text\", \"fields\" : { \"keyword\" : {
\"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"en_download_count\" : { \"type\" : \"long\" }, \"en_like_count\" : {
\"type\" : \"long\" }, \"en_p_score_v2\" : { \"type\" : \"float\" },
\"en_p_score_v3\" : { \"type\" : \"float\" }, \"en_play_count\" : {
\"type\" : \"long\" }, \"en_rewards\" : { \"properties\" : { \"12hr\" :
{ \"properties\" : { \"a\" : { \"type\" : \"long\" }, \"b\" : { \"type\"
: \"long\" } } }, \"16hr\" : { \"properties\" : { \"a\" : { \"type\" :
\"long\" }, \"b\" : { \"type\" : \"long\" } } }, \"1hr\" : {
\"properties\" : { \"a\" : { \"type\" : \"long\" }, \"b\" : { \"type\" :
\"long\" } } }, \"4hr\" : { \"properties\" : { \"a\" : { \"type\" :
\"long\" }, \"b\" : { \"type\" : \"long\" } } }, \"8hr\" : {
\"properties\" : { \"a\" : { \"type\" : \"long\" }, \"b\" : { \"type\" :
\"long\" } } }, \"life\" : { \"properties\" : { \"a\" : { \"type\" :
\"long\" }, \"b\" : { \"type\" : \"long\" } } } } }, \"en_share_count\"
: { \"type\" : \"long\" }, \"en_t_score_v2\" : { \"type\" : \"float\" },
\"en_t_score_v3\" : { \"type\" : \"float\" }, \"en_view_count\" : {
\"type\" : \"long\" }, \"end_date\" : { \"type\" : \"date\" },
\"engagement_uu\" : { \"type\" : \"long\" }, \"enhancement_selected\" :
{ \"type\" : \"text\", \"fields\" : { \"keyword\" : { \"type\" :
\"keyword\", \"ignore_above\" : 256 } } }, \"file_size\" : { \"type\" :
\"long\" }, \"fk_downloads\" : { \"type\" : \"long\" }, \"fk_likes\" : {
\"type\" : \"long\" }, \"fk_shares\" : { \"type\" : \"long\" },
\"fk_views\" : { \"type\" : \"long\" }, \"hashtag\" : { \"type\" :
\"text\", \"fields\" : { \"keyword\" : { \"type\" : \"keyword\",
\"ignore_above\" : 256 } }, \"copy_to\": \"search_fields\" },
\"hi_view_count\" : { \"type\" : \"long\" }, \"hide_banner\" : {
\"type\" : \"text\", \"fields\" : { \"keyword\" : { \"type\" :
\"keyword\", \"ignore_above\" : 256 } } }, \"hide_stats\" : { \"type\" :
\"text\", \"fields\" : { \"keyword\" : { \"type\" : \"keyword\",
\"ignore_above\" : 256 } } }, \"icon_file_name\" : { \"type\" :
\"text\", \"fields\" : { \"keyword\" : { \"type\" : \"keyword\",
\"ignore_above\" : 256 } } }, \"icon_file_path\" : { \"type\" :
\"text\", \"fields\" : { \"keyword\" : { \"type\" : \"keyword\",
\"ignore_above\" : 256 } } }, \"icon_transcoding_status\" : { \"type\" :
\"text\", \"fields\" : { \"keyword\" : { \"type\" : \"keyword\",
\"ignore_above\" : 256 } } }, \"icon_transcoding_time\" : { \"type\" :
\"date\" }, \"icon_url\" : { \"type\" : \"text\", \"fields\" : {
\"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"is_active\" : { \"type\" : \"boolean\" }, \"is_audio_allowed\" : {
\"type\" : \"boolean\" }, \"is_audio_fixed\" : { \"type\" : \"boolean\"
}, \"is_votable\" : { \"type\" : \"boolean\" }, \"kn_like_count\" : {
\"type\" : \"long\" }, \"kn_p_score_v2\" : { \"type\" : \"float\" },
\"kn_rewards\" : { \"properties\" : { \"12hr\" : { \"properties\" : {
\"a\" : { \"type\" : \"long\" }, \"b\" : { \"type\" : \"long\" } } },
\"16hr\" : { \"properties\" : { \"a\" : { \"type\" : \"long\" }, \"b\" :
{ \"type\" : \"long\" } } }, \"1hr\" : { \"properties\" : { \"a\" : {
\"type\" : \"long\" }, \"b\" : { \"type\" : \"long\" } } }, \"4hr\" : {
\"properties\" : { \"a\" : { \"type\" : \"long\" }, \"b\" : { \"type\" :
\"long\" } } }, \"8hr\" : { \"properties\" : { \"a\" : { \"type\" :
\"long\" }, \"b\" : { \"type\" : \"long\" } } }, \"life\" : {
\"properties\" : { \"a\" : { \"type\" : \"long\" }, \"b\" : { \"type\" :
\"long\" } } } } }, \"kn_share_count\" : { \"type\" : \"long\" },
\"kn_t_score_v2\" : { \"type\" : \"float\" }, \"kn_view_count\" : {
\"type\" : \"long\" }, \"lang_code\" : { \"type\" : \"text\", \"fields\"
: { \"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } }
}, \"like_count\" : { \"type\" : \"long\" }, \"like_uu\" : { \"type\" :
\"long\" }, \"lp_0_uu\" : { \"type\" : \"long\" }, \"m3u8_profiles\" : {
\"type\" : \"text\", \"fields\" : { \"keyword\" : { \"type\" :
\"keyword\", \"ignore_above\" : 256 } } }, \"m3u8_transcoding_status\" :
{ \"type\" : \"text\", \"fields\" : { \"keyword\" : { \"type\" :
\"keyword\", \"ignore_above\" : 256 } } }, \"m3u8_transcoding_time\" : {
\"type\" : \"date\" }, \"m3u8_url\" : { \"type\" : \"text\", \"fields\"
: { \"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } }
}, \"mask_status\" : { \"type\" : \"text\", \"fields\" : { \"keyword\" :
{ \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"mask_status_update_time\" : { \"type\" : \"date\" }, \"masked\" : {
\"type\" : \"boolean\" }, \"max_participation_allowed\" : { \"type\" :
\"long\" }, \"max_video_duration_ms\" : { \"type\" : \"long\" },
\"max_vote_allowed\" : { \"type\" : \"long\" },
\"min_video_duration_ms\" : { \"type\" : \"long\" },
\"moderation_level\" : { \"type\" : \"long\" }, \"modified_date\" : {
\"type\" : \"date\" }, \"mp4_transcoding_status\" : { \"type\" :
\"text\", \"fields\" : { \"keyword\" : { \"type\" : \"keyword\",
\"ignore_above\" : 256 } } }, \"mp4_transcoding_time\" : { \"type\" :
\"date\" }, \"mp4_url\" : { \"type\" : \"text\", \"fields\" : {
\"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"not_processed\" : { \"type\" : \"boolean\" }, \"orientation\" : {
\"type\" : \"text\", \"fields\" : { \"keyword\" : { \"type\" :
\"keyword\", \"ignore_above\" : 256 } } }, \"p_score_v2\" : { \"type\" :
\"float\" }, \"p_score_v3\" : { \"type\" : \"float\" }, \"pcc_0_5_uu\" :
{ \"type\" : \"long\" }, \"pixel_size\" : { \"type\" : \"text\",
\"fields\" : { \"keyword\" : { \"type\" : \"keyword\", \"ignore_above\"
: 256 } } }, \"play_count\" : { \"type\" : \"long\" }, \"play_uu\" : {
\"type\" : \"long\" }, \"prepared_content_title\" : { \"type\" :
\"text\", \"fields\" : { \"keyword\" : { \"type\" : \"keyword\",
\"ignore_above\" : 256 } } }, \"primary_banner_file_name\" : { \"type\"
: \"text\", \"fields\" : { \"keyword\" : { \"type\" : \"keyword\",
\"ignore_above\" : 256 } } }, \"primary_banner_file_path\" : { \"type\"
: \"text\", \"fields\" : { \"keyword\" : { \"type\" : \"keyword\",
\"ignore_above\" : 256 } } }, \"processed\" : { \"type\" : \"long\" },
\"promo_video_id\" : { \"type\" : \"text\", \"fields\" : { \"keyword\" :
{ \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"recent_tab_icon_filepath\" : { \"type\" : \"text\", \"fields\" : {
\"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"report_count\" : { \"type\" : \"long\" }, \"report_url\" : { \"type\"
: \"text\", \"fields\" : { \"keyword\" : { \"type\" : \"keyword\",
\"ignore_above\" : 256 } } }, \"request_id\" : { \"type\" : \"text\",
\"fields\" : { \"keyword\" : { \"type\" : \"keyword\", \"ignore_above\"
: 256 } } }, \"review_bucket\" : { \"type\" : \"long\" }, \"rewards\" :
{ \"properties\" : { \"12hr\" : { \"properties\" : { \"a\" : { \"type\"
: \"long\" }, \"b\" : { \"type\" : \"long\" } } }, \"16hr\" : {
\"properties\" : { \"a\" : { \"type\" : \"long\" }, \"b\" : { \"type\" :
\"long\" } } }, \"1hr\" : { \"properties\" : { \"a\" : { \"type\" :
\"long\" }, \"b\" : { \"type\" : \"long\" } } }, \"4hr\" : {
\"properties\" : { \"a\" : { \"type\" : \"long\" }, \"b\" : { \"type\" :
\"long\" } } }, \"8hr\" : { \"properties\" : { \"a\" : { \"type\" :
\"long\" }, \"b\" : { \"type\" : \"long\" } } }, \"life\" : {
\"properties\" : { \"a\" : { \"type\" : \"long\" }, \"b\" : { \"type\" :
\"long\" } } } } }, \"rules_data\" : { \"type\" : \"text\", \"fields\" :
{ \"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"search_tags\" : { \"type\" : \"text\", \"fields\" : { \"keyword\" : {
\"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"secondary_banner_file_name\" : { \"type\" : \"text\", \"fields\" : {
\"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"secondary_banner_file_path\" : { \"type\" : \"text\", \"fields\" : {
\"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"seq_counter\" : { \"type\" : \"long\" }, \"share_count\" : { \"type\"
: \"long\" }, \"share_url\" : { \"type\" : \"text\", \"fields\" : {
\"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"share_url_v2\" : { \"type\" : \"text\", \"fields\" : { \"keyword\" : {
\"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"share_url_v2_expanded\" : { \"type\" : \"text\", \"fields\" : {
\"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"share_uu\" : { \"type\" : \"long\" }, \"short_url\" : { \"type\" :
\"text\", \"fields\" : { \"keyword\" : { \"type\" : \"keyword\",
\"ignore_above\" : 256 } } }, \"short_url_key\" : { \"type\" : \"text\",
\"fields\" : { \"keyword\" : { \"type\" : \"keyword\", \"ignore_above\"
: 256 } } }, \"sponsored\" : { \"type\" : \"text\", \"fields\" : {
\"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"sponsored_text\" : { \"type\" : \"text\", \"fields\" : { \"keyword\" :
{ \"type\" : \"keyword\", \"ignore_above\" : 256 } } }, \"start_date\" :
{ \"type\" : \"date\" }, \"status\" : { \"type\" : \"text\", \"fields\"
: { \"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } }
}, \"submission_info\" : { \"properties\" : { \"end_date\" : { \"type\"
: \"date\" }, \"start_date\" : { \"type\" : \"date\" } } }, \"svig\" : {
\"type\" : \"text\", \"fields\" : { \"keyword\" : { \"type\" :
\"keyword\", \"ignore_above\" : 256 } } }, \"t_score_v2\" : { \"type\" :
\"float\" }, \"t_score_v3\" : { \"type\" : \"float\" },
\"ta_p_score_v2\" : { \"type\" : \"float\" }, \"ta_rewards\" : {
\"properties\" : { \"12hr\" : { \"properties\" : { \"a\" : { \"type\" :
\"long\" }, \"b\" : { \"type\" : \"long\" } } }, \"16hr\" : {
\"properties\" : { \"a\" : { \"type\" : \"long\" }, \"b\" : { \"type\" :
\"long\" } } }, \"1hr\" : { \"properties\" : { \"a\" : { \"type\" :
\"long\" }, \"b\" : { \"type\" : \"long\" } } }, \"4hr\" : {
\"properties\" : { \"a\" : { \"type\" : \"long\" }, \"b\" : { \"type\" :
\"long\" } } }, \"8hr\" : { \"properties\" : { \"a\" : { \"type\" :
\"long\" }, \"b\" : { \"type\" : \"long\" } } }, \"life\" : {
\"properties\" : { \"a\" : { \"type\" : \"long\" }, \"b\" : { \"type\" :
\"long\" } } } } }, \"ta_t_score_v2\" : { \"type\" : \"float\" },
\"ta_view_count\" : { \"type\" : \"long\" }, \"tags\" : { \"type\" :
\"text\", \"fields\" : { \"keyword\" : { \"type\" : \"keyword\",
\"ignore_above\" : 256 } } }, \"tags_array\" : { \"type\" : \"text\",
\"fields\" : { \"keyword\" : { \"type\" : \"keyword\", \"ignore_above\"
: 256 } } }, \"target_languages\" : { \"type\" : \"text\", \"fields\" :
{ \"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"targeted_locations\" : { \"properties\" : { \"granularity\" : {
\"type\" : \"text\", \"fields\" : { \"keyword\" : { \"type\" :
\"keyword\", \"ignore_above\" : 256 } } }, \"lat\" : { \"type\" :
\"text\", \"fields\" : { \"keyword\" : { \"type\" : \"keyword\",
\"ignore_above\" : 256 } } }, \"long\" : { \"type\" : \"text\",
\"fields\" : { \"keyword\" : { \"type\" : \"keyword\", \"ignore_above\"
: 256 } } } } }, \"te_view_count\" : { \"type\" : \"long\" }, \"theme\"
: { \"properties\" : { \"background\" : { \"properties\" : {
\"color_code\" : { \"type\" : \"text\", \"fields\" : { \"keyword\" : {
\"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"image_url_file_name\" : { \"type\" : \"text\", \"fields\" : {
\"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"image_url_file_path\" : { \"type\" : \"text\", \"fields\" : {
\"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } } }
}, \"end_date_ms\" : { \"type\" : \"text\", \"fields\" : { \"keyword\" :
{ \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"overlay_image_file_name\" : { \"type\" : \"text\", \"fields\" : {
\"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"overlay_image_file_path\" : { \"type\" : \"text\", \"fields\" : {
\"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"start_date_ms\" : { \"type\" : \"text\", \"fields\" : { \"keyword\" :
{ \"type\" : \"keyword\", \"ignore_above\" : 256 } } } } },
\"thumbnail\" : { \"type\" : \"text\", \"fields\" : { \"keyword\" : {
\"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"thumbnail_transcoding_status\" : { \"type\" : \"text\", \"fields\" : {
\"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"thumbnail_transcoding_time\" : { \"type\" : \"date\" },
\"thumbnail_url\" : { \"type\" : \"text\", \"fields\" : { \"keyword\" :
{ \"type\" : \"keyword\", \"ignore_above\" : 256 } } }, \"title\" : {
\"type\" : \"text\", \"fields\" : { \"keyword\" : { \"type\" :
\"keyword\", \"ignore_above\" : 256 } } }, \"top_tab_icon_filepath\" : {
\"type\" : \"text\", \"fields\" : { \"keyword\" : { \"type\" :
\"keyword\", \"ignore_above\" : 256 } } }, \"ts_0_3_uu\" : { \"type\" :
\"long\" }, \"type\" : { \"type\" : \"text\", \"fields\" : { \"keyword\"
: { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"unlike_count\" : { \"type\" : \"long\" }, \"url\" : { \"type\" :
\"text\", \"fields\" : { \"keyword\" : { \"type\" : \"keyword\",
\"ignore_above\" : 256 } } }, \"user_profile\" : { \"properties\" : {
\"auto_nsfw_posts\" : { \"type\" : \"long\" }, \"curated_age\" : {
\"type\" : \"text\", \"fields\" : { \"keyword\" : { \"type\" :
\"keyword\", \"ignore_above\" : 256 } } }, \"curated_gender\" : {
\"type\" : \"text\", \"fields\" : { \"keyword\" : { \"type\" :
\"keyword\", \"ignore_above\" : 256 } } }, \"curated_genre\" : {
\"type\" : \"text\", \"fields\" : { \"keyword\" : { \"type\" :
\"keyword\", \"ignore_above\" : 256 } } }, \"curated_org_content\" : {
\"type\" : \"text\", \"fields\" : { \"keyword\" : { \"type\" :
\"keyword\", \"ignore_above\" : 256 } } }, \"curated_quality_ratio\" : {
\"type\" : \"text\", \"fields\" : { \"keyword\" : { \"type\" :
\"keyword\", \"ignore_above\" : 256 } } }, \"curated_tg\" : { \"type\" :
\"text\", \"fields\" : { \"keyword\" : { \"type\" : \"keyword\",
\"ignore_above\" : 256 } } }, \"curated_type\" : { \"type\" : \"text\",
\"fields\" : { \"keyword\" : { \"type\" : \"keyword\", \"ignore_above\"
: 256 } } }, \"curated_x_factor\" : { \"type\" : \"text\", \"fields\" :
{ \"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"engagement_uu\" : { \"type\" : \"long\" }, \"gender\" : { \"type\" :
\"text\", \"fields\" : { \"keyword\" : { \"type\" : \"keyword\",
\"ignore_above\" : 256 } } }, \"manual_nsfw_posts\" : { \"type\" :
\"long\" }, \"moderation_level\" : { \"type\" : \"long\" }, \"name\" : {
\"type\" : \"text\", \"fields\" : { \"keyword\" : { \"type\" :
\"keyword\", \"ignore_above\" : 256 } } }, \"nsfw_posts_count\" : {
\"type\" : \"long\" }, \"profile_pic\" : { \"type\" : \"text\",
\"fields\" : { \"keyword\" : { \"type\" : \"keyword\", \"ignore_above\"
: 256 } } }, \"real_followers_count\" : { \"type\" : \"long\" },
\"real_hearts_count\" : { \"type\" : \"long\" }, \"real_shares_count\" :
{ \"type\" : \"long\" }, \"remunerate\" : { \"type\" : \"text\",
\"fields\" : { \"keyword\" : { \"type\" : \"keyword\", \"ignore_above\"
: 256 } } }, \"user_name\" : { \"type\" : \"text\", \"fields\" : {
\"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"user_type\" : { \"type\" : \"text\", \"fields\" : { \"keyword\" : {
\"type\" : \"keyword\", \"ignore_above\" : 256 } } }, \"user_uuid\" : {
\"type\" : \"text\", \"fields\" : { \"keyword\" : { \"type\" :
\"keyword\", \"ignore_above\" : 256 } } }, \"verified\" : { \"type\" :
\"boolean\" }, \"view_uu\" : { \"type\" : \"long\" } } },
\"video_count\" : { \"type\" : \"long\" }, \"video_duration\" : {
\"type\" : \"float\" }, \"video_source\" : { \"type\" : \"text\",
\"fields\" : { \"keyword\" : { \"type\" : \"keyword\", \"ignore_above\"
: 256 } } }, \"view_count\" : { \"type\" : \"long\" }, \"view_uu\" : {
\"type\" : \"long\" }, \"votes\" : { \"type\" : \"long\" },
\"voting_info\" : { \"properties\" : { \"end_date\" : { \"type\" :
\"date\" }, \"start_date\" : { \"type\" : \"date\" } } },
\"wmj_transcoding_status\" : { \"type\" : \"text\", \"fields\" : {
\"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"wmj_transcoding_time\" : { \"type\" : \"date\" }, \"wmj_url\" : {
\"type\" : \"text\", \"fields\" : { \"keyword\" : { \"type\" :
\"keyword\", \"ignore_above\" : 256 } } }, \"search_fields\": {
\"type\": \"completion\", \"analyzer\": \"standard\",
\"preserve_separators\": true, \"preserve_position_increments\": true,
\"max_input_length\": 50, \"fields\": { \"autocomplete\": { \"type\":
\"completion\", \"analyzer\": \"stopword_analyzer\",
\"preserve_separators\": true, \"preserve_position_increments\": false,
\"max_input_length\": 10 } } } } }, \"settings\": { \"analysis\": {
\"analyzer\": { \"stopword_analyzer\": { \"stopwords\": \[ \"and\",
\"the\" \], \"type\": \"standard\" } } } } }

**[Reindex the data:]{.underline}**

jsonPOST \_reindex { \"source\": { \"index\": \"ugc-contests-v1\" },
\"dest\": { \"index\": \"ugc-contests-v2\" } }

**[Sample Get Query:]{.underline}**

jsonGET ugc-contests-v2/\_search { \"query\": { \"bool\": { \"must\": \[
{ \"prefix\": { \"hashtag.keyword\": { \"value\": \"test\" } } } \] } },
\"suggest\": { \"suggestions\": { \"prefix\": \"test\", \"completion\":
{ \"field\": \"search_fields\", \"size\": 7, \"fuzzy\": { \"fuzziness\":
1, \"transpositions\": true, \"min_length\": 3, \"prefix_length\": 1,
\"unicode_aware\": false, \"max_determinized_states\": 10000 },
\"skip_duplicates\": true } } } }
