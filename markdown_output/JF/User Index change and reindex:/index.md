jsonPUT ugc-users-v2 { \"mappings\": { \"properties\": {
\"USER_PROFILE_ICON_file_size\": { \"type\": \"long\" },
\"USER_PROFILE_ICON_pixel_size\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"USER_PROFILE_ICON_processed_server\": { \"type\": \"text\",
\"fields\": { \"keyword\": { \"type\": \"keyword\", \"ignore_above\":
256 } } }, \"USER_PROFILE_ICON_profile_icon_url\": { \"type\": \"text\",
\"fields\": { \"keyword\": { \"type\": \"keyword\", \"ignore_above\":
256 } } }, \"USER_PROFILE_ICON_profile_thumbnail_url\": { \"type\":
\"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"USER_PROFILE_ICON_transcoding_status\": {
\"type\": \"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"USER_PROFILE_ICON_transcoding_time\": {
\"type\": \"date\" }, \"USER_PROFILE_ICON_url\": { \"type\": \"text\",
\"fields\": { \"keyword\": { \"type\": \"keyword\", \"ignore_above\":
256 } } }, \"access_level\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"active\": { \"type\": \"text\", \"fields\": { \"keyword\": { \"type\":
\"keyword\", \"ignore_above\": 256 } } }, \"agg_modified_at\": {
\"type\": \"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"algo_persona\": { \"properties\": {
\"a\": { \"type\": \"text\", \"fields\": { \"keyword\": { \"type\":
\"keyword\", \"ignore_above\": 256 } } } } }, \"allow_download\": {
\"type\": \"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"allow_follow\": { \"type\": \"text\",
\"fields\": { \"keyword\": { \"type\": \"keyword\", \"ignore_above\":
256 } } }, \"allow_josh_live\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"allow_local_share\": { \"type\": \"text\", \"fields\": { \"keyword\":
{ \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"allow_profile_tagging\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"allow_share\": { \"type\": \"text\", \"fields\": { \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 } } },
\"auto_nsfw_comments\": { \"type\": \"long\" }, \"auto_nsfw_posts\": {
\"type\": \"long\" }, \"badge\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"bio_data\": { \"type\": \"text\", \"fields\": { \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 } } },
\"camera_posts_count\": { \"type\": \"long\" }, \"categories\": {
\"type\": \"text\", \"fields\": { \"beider_morse\": { \"type\":
\"text\", \"analyzer\": \"beider_morse\" }, \"keyword\": { \"type\":
\"keyword\", \"ignore_above\": 256 }, \"keyword_lowercase\": { \"type\":
\"text\", \"analyzer\": \"keyword_analyzer\" }, \"metaphone\": {
\"type\": \"text\", \"analyzer\": \"metaphone\" }, \"ngram\": {
\"type\": \"text\", \"analyzer\": \"edge_analyzer\" },
\"refined_soundex\": { \"type\": \"text\", \"analyzer\":
\"refined_soundex\" } } }, \"community_lead_id\": { \"type\": \"text\",
\"fields\": { \"keyword\": { \"type\": \"keyword\", \"ignore_above\":
256 } } }, \"community_manager_id\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"content_create_langs\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"content_creation_langs\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"content_location_cities\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"content_location_states\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"content_target_categories\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"content_uuid\": { \"type\": \"text\", \"fields\": { \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 } } }, \"contest_meta\": {
\"properties\": { \"curated_age\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"curated_aspect_ratio\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"curated_gender\": { \"type\": \"text\", \"fields\": { \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 } } }, \"curated_genre\": {
\"type\": \"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"curated_org_content\": { \"type\":
\"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"curated_quality_ratio\": { \"type\":
\"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"curated_type\": { \"type\": \"text\",
\"fields\": { \"keyword\": { \"type\": \"keyword\", \"ignore_above\":
256 } } }, \"curated_watermark\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"curated_x_factor\": { \"type\": \"text\", \"fields\": { \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 } } } } },
\"created_date\": { \"type\": \"text\", \"fields\": { \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 } } }, \"created_time\": {
\"type\": \"long\" }, \"curated_age\": { \"type\": \"text\", \"fields\":
{ \"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"curated_aspect_ratio\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"curated_data\": { \"properties\": { \"curated_age\": { \"type\":
\"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"curated_aspect_ratio\": { \"type\":
\"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"curated_gender\": { \"type\": \"text\",
\"fields\": { \"keyword\": { \"type\": \"keyword\", \"ignore_above\":
256 } } }, \"curated_genre\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"curated_org_content\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"curated_quality_ratio\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"curated_type\": { \"type\": \"text\", \"fields\": { \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 } } },
\"curated_watermark\": { \"type\": \"text\", \"fields\": { \"keyword\":
{ \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"curated_x_factor\": { \"type\": \"text\", \"fields\": { \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 } } } } },
\"curated_entities\": { \"properties\": { \"curated_age\": {
\"properties\": { \"S\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } } } },
\"curated_aspect_ratio\": { \"properties\": { \"S\": { \"type\":
\"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } } } }, \"curated_gender\": { \"properties\": {
\"S\": { \"type\": \"text\", \"fields\": { \"keyword\": { \"type\":
\"keyword\", \"ignore_above\": 256 } } } } }, \"curated_genre\": {
\"properties\": { \"L\": { \"properties\": { \"S\": { \"type\":
\"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } } } } } }, \"curated_org_content\": {
\"properties\": { \"S\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } } } },
\"curated_quality_ratio\": { \"properties\": { \"S\": { \"type\":
\"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } } } }, \"curated_tg\": { \"properties\": {
\"S\": { \"type\": \"text\", \"fields\": { \"keyword\": { \"type\":
\"keyword\", \"ignore_above\": 256 } } } } }, \"curated_type\": {
\"properties\": { \"S\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } } } },
\"curated_watermark\": { \"properties\": { \"S\": { \"type\": \"text\",
\"fields\": { \"keyword\": { \"type\": \"keyword\", \"ignore_above\":
256 } } } } }, \"curated_x_factor\": { \"properties\": { \"S\": {
\"type\": \"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } } } } } }, \"curated_gender\": { \"type\":
\"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"curated_genre\": { \"type\": \"text\",
\"fields\": { \"keyword\": { \"type\": \"keyword\", \"ignore_above\":
256 } } }, \"curated_lang\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"curated_org_content\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"curated_quality_ratio\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"curated_tg\": { \"type\": \"text\", \"fields\": { \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 } } }, \"curated_type\": {
\"type\": \"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"curated_watermark\": { \"type\":
\"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"curated_x_factor\": { \"type\": \"text\",
\"fields\": { \"keyword\": { \"type\": \"keyword\", \"ignore_above\":
256 } } }, \"date_created\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"date_modified\": { \"type\": \"text\", \"fields\": { \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 } } }, \"display_persona\":
{ \"type\": \"text\", \"fields\": { \"keyword\": { \"type\":
\"keyword\", \"ignore_above\": 256 } } }, \"display_persona_ack_time\":
{ \"type\": \"long\" }, \"display_persona_update_time\": { \"type\":
\"long\" }, \"doc\": { \"properties\": { \"categories\": { \"type\":
\"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"tags\": { \"type\": \"text\", \"fields\":
{ \"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } } } },
\"doc_as_upsert\": { \"type\": \"boolean\" }, \"download_count\": {
\"type\": \"long\" }, \"download_uu\": { \"type\": \"long\" },
\"duet_posts_count\": { \"type\": \"long\" }, \"email\": { \"type\":
\"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"engaged_users_count\": { \"type\":
\"long\" }, \"engagement_uu\": { \"type\": \"long\" },
\"external_did_posts_count\": { \"type\": \"long\" },
\"first_content_date\": { \"type\": \"date\" }, \"first_creation_date\":
{ \"type\": \"long\" }, \"fk_downloads\": { \"type\": \"long\" },
\"fk_followers_uu\": { \"type\": \"long\" }, \"fk_likes\": { \"type\":
\"long\" }, \"fk_shares\": { \"type\": \"long\" }, \"fk_views\": {
\"type\": \"long\" }, \"followers_uu\": { \"type\": \"long\" },
\"gallery_posts_count\": { \"type\": \"long\" }, \"gender\": { \"type\":
\"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"handle\": { \"type\": \"text\",
\"fields\": { \"beider_morse\": { \"type\": \"text\", \"analyzer\":
\"beider_morse\" }, \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 }, \"keyword_lowercase\": { \"type\": \"text\",
\"analyzer\": \"keyword_analyzer\" }, \"metaphone\": { \"type\":
\"text\", \"analyzer\": \"metaphone\" }, \"ngram\": { \"type\":
\"text\", \"analyzer\": \"edge_analyzer\" }, \"refined_soundex\": {
\"type\": \"text\", \"analyzer\": \"refined_soundex\" } }, \"copy_to\":
\[ \"search_fields\" \] }, \"hide_stats\": { \"type\": \"text\",
\"fields\": { \"keyword\": { \"type\": \"keyword\", \"ignore_above\":
256 } } }, \"image_posts_count\": { \"type\": \"long\" }, \"is_active\":
{ \"type\": \"boolean\" }, \"lang_code\": { \"type\": \"text\",
\"fields\": { \"keyword\": { \"type\": \"keyword\", \"ignore_above\":
256 } } }, \"lastModifiedDate\": { \"type\": \"long\" },
\"last_content_date\": { \"type\": \"date\" }, \"last_creation_date\": {
\"type\": \"long\" }, \"last_deactivation_time\": { \"type\": \"date\"
}, \"last_modified_date\": { \"type\": \"date\" }, \"like_count\": {
\"type\": \"long\" }, \"like_uu\": { \"type\": \"long\" },
\"live_category_interests\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"manual_nsfw_post_count\": { \"type\": \"long\" },
\"manual_nsfw_posts\": { \"type\": \"long\" }, \"max_cap_followings\": {
\"type\": \"long\" }, \"moderation_level\": { \"type\": \"long\" },
\"modified_date\": { \"type\": \"text\", \"fields\": { \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 } } },
\"multi_segment_camera_gallery_posts_count\": { \"type\": \"long\" },
\"multi_segment_camera_posts_count\": { \"type\": \"long\" },
\"multi_segment_gallery_posts_count\": { \"type\": \"long\" },
\"music_count\": { \"type\": \"text\", \"fields\": { \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 } } }, \"name\": {
\"type\": \"text\", \"fields\": { \"beider_morse\": { \"type\":
\"text\", \"analyzer\": \"beider_morse\" }, \"keyword\": { \"type\":
\"keyword\", \"ignore_above\": 256 }, \"keyword_lowercase\": { \"type\":
\"text\", \"analyzer\": \"keyword_analyzer\" }, \"metaphone\": {
\"type\": \"text\", \"analyzer\": \"metaphone\" }, \"ngram\": {
\"type\": \"text\", \"analyzer\": \"edge_analyzer\" },
\"refined_soundex\": { \"type\": \"text\", \"analyzer\":
\"refined_soundex\" } }, \"copy_to\": \[ \"search_fields\" \] },
\"name_trans\": { \"type\": \"text\", \"fields\": { \"beider_morse\": {
\"type\": \"text\", \"analyzer\": \"beider_morse\" }, \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 }, \"keyword_lowercase\": {
\"type\": \"text\", \"analyzer\": \"keyword_analyzer\" }, \"metaphone\":
{ \"type\": \"text\", \"analyzer\": \"metaphone\" }, \"ngram\": {
\"type\": \"text\", \"analyzer\": \"edge_analyzer\" },
\"refined_soundex\": { \"type\": \"text\", \"analyzer\":
\"refined_soundex\" } } }, \"othersource_posts_count\": { \"type\":
\"long\" }, \"phone\": { \"type\": \"text\", \"fields\": { \"keyword\":
{ \"type\": \"keyword\", \"ignore_above\": 256 } } }, \"phone_no\": {
\"type\": \"long\" }, \"pixel_size\": { \"type\": \"text\", \"fields\":
{ \"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"play_count\": { \"type\": \"long\" }, \"play_uu\": { \"type\":
\"long\" }, \"posts_count\": { \"type\": \"long\" },
\"posts_count_via_camera\": { \"type\": \"long\" },
\"posts_count_via_upload\": { \"type\": \"long\" },
\"posts_in_last_7_days\": { \"type\": \"long\" }, \"profile_icon_url\":
{ \"type\": \"text\", \"fields\": { \"keyword\": { \"type\":
\"keyword\", \"ignore_above\": 256 } } }, \"profile_overlay_name_url\":
{ \"type\": \"text\", \"fields\": { \"keyword\": { \"type\":
\"keyword\", \"ignore_above\": 256 } } }, \"profile_pic\": { \"type\":
\"keyword\", \"index\": false }, \"profile_thumbnail_url\": { \"type\":
\"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"rc_total_download_count\": { \"type\":
\"long\" }, \"rc_total_like_count\": { \"type\": \"long\" },
\"rc_total_play_count\": { \"type\": \"long\" },
\"rc_total_share_count\": { \"type\": \"long\" },
\"rc_total_view_count\": { \"type\": \"long\" }, \"real_fans_count\": {
\"type\": \"long\" }, \"real_fans_uu\": { \"type\": \"long\" },
\"remunerate\": { \"type\": \"text\", \"fields\": { \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 } } }, \"report_count\": {
\"type\": \"long\" }, \"search_fields\": { \"type\": \"completion\",
\"analyzer\": \"standard\", \"preserve_separators\": true,
\"preserve_position_increments\": true, \"max_input_length\": 50,
\"fields\": { \"autocomplete\": { \"type\": \"completion\",
\"analyzer\": \"stopword_analyzer\", \"preserve_separators\": true,
\"preserve_position_increments\": false, \"max_input_length\": 10 } } },
\"share_count\": { \"type\": \"long\" }, \"share_uu\": { \"type\":
\"long\" }, \"shoppable\": { \"type\": \"boolean\" }, \"skip_masking\":
{ \"type\": \"text\", \"fields\": { \"keyword\": { \"type\":
\"keyword\", \"ignore_above\": 256 } } }, \"skip_moderation\": {
\"type\": \"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"source\": { \"type\": \"text\",
\"fields\": { \"keyword\": { \"type\": \"keyword\", \"ignore_above\":
256 } } }, \"sponsored_text\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"tags\": { \"type\": \"text\", \"fields\": { \"beider_morse\": {
\"type\": \"text\", \"analyzer\": \"beider_morse\" }, \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 }, \"keyword_lowercase\": {
\"type\": \"text\", \"analyzer\": \"keyword_analyzer\" }, \"metaphone\":
{ \"type\": \"text\", \"analyzer\": \"metaphone\" }, \"ngram\": {
\"type\": \"text\", \"analyzer\": \"edge_analyzer\" },
\"refined_soundex\": { \"type\": \"text\", \"analyzer\":
\"refined_soundex\" } }, \"copy_to\": \[ \"search_fields\" \] },
\"target_categories\": { \"type\": \"text\", \"fields\": { \"keyword\":
{ \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"total_downloads\": { \"type\": \"long\" }, \"total_fans_count\": {
\"type\": \"long\" }, \"total_likes\": { \"type\": \"long\" },
\"total_review_request\": { \"type\": \"long\" }, \"total_shares\": {
\"type\": \"long\" }, \"total_views\": { \"type\": \"long\" },
\"unlike_count\": { \"type\": \"long\" }, \"unlike_uu\": { \"type\":
\"long\" }, \"updated_time\": { \"type\": \"long\" },
\"user_blocked_from_tagging\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"user_lang_primary\": { \"type\": \"text\", \"fields\": { \"keyword\":
{ \"type\": \"keyword\", \"ignore_above\": 256 } } }, \"user_name\": {
\"type\": \"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 }, \"keyword_lowercase\": { \"type\": \"text\",
\"analyzer\": \"keyword_analyzer\" } } },
\"user_profile_icon_file_size\": { \"type\": \"long\" },
\"user_profile_icon_pixel_size\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"user_profile_transcoding_status\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"user_profile_transcoding_time\": { \"type\": \"date\" },
\"user_type\": { \"type\": \"text\", \"fields\": { \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 } } }, \"user_uuid\": {
\"type\": \"keyword\" }, \"verified\": { \"type\": \"boolean\" },
\"view_count\": { \"type\": \"long\" }, \"view_uu\": { \"type\":
\"long\" } } }, \"settings\": { \"index\": { \"analysis\": { \"filter\":
{ \"beider_morse_filter\": { \"replace\": \"false\", \"type\":
\"phonetic\", \"encoder\": \"beider_morse\" }, \"ngram\": {
\"token_chars\": \[ \"letter\", \"digit\", \"punctuation\", \"symbol\"
\], \"min_gram\": \"2\", \"type\": \"edge_ngram\", \"max_gram\": \"30\"
}, \"metaphone_filter\": { \"replace\": \"false\", \"type\":
\"phonetic\", \"encoder\": \"doublemetaphone\" },
\"refined_soundex_filter\": { \"replace\": \"false\", \"type\":
\"phonetic\", \"encoder\": \"refinedsoundex\" } }, \"analyzer\": {
\"edge_analyzer\": { \"filter\": \[ \"lowercase\", \"ngram\",
\"asciifolding\" \], \"type\": \"custom\", \"tokenizer\": \"whitespace\"
}, \"refined_soundex\": { \"filter\": \[ \"lowercase\",
\"refined_soundex_filter\" \], \"type\": \"custom\", \"tokenizer\":
\"standard\" }, \"beider_morse\": { \"filter\": \[ \"lowercase\",
\"beider_morse_filter\" \], \"type\": \"custom\", \"tokenizer\":
\"standard\" }, \"keyword_analyzer\": { \"filter\": \[ \"lowercase\" \],
\"type\": \"custom\", \"tokenizer\": \"keyword\" }, \"metaphone\": {
\"filter\": \[ \"lowercase\", \"metaphone_filter\" \], \"type\":
\"custom\", \"tokenizer\": \"standard\" }, \"stopword_analyzer\": {
\"type\": \"standard\", \"stopwords\": \[ \"and\", \"the\" \] } } } } }
}

**[Reindex Data:]{.underline}**

jsonPOST \_reindex { \"source\": { \"index\": \"ugc-users-v1\" },
\"dest\": { \"index\": \"ugc-users-v2\" } }

**[Sample Get Query:]{.underline}**

jsonGET ugc-users-v2/\_search { \"suggest\": { \"suggestestions\": {
\"prefix\": \"sou\", \"completion\": { \"field\": \"search_fields\",
\"size\" : 7, \"skip_duplicates\" : true, \"fuzzy\":{ \"fuzziness\" : 1
} } } } }
