**[Index Definition:]{.underline}**

jsonPUT josh-zones-v4 { \"mappings\": { \"properties\": { \"alias\": {
\"type\": \"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"allow_follow\": { \"type\": \"boolean\"
}, \"auto_scroll_ms\": { \"type\": \"long\" }, \"cover_banner\": {
\"properties\": { \"cta_data\": { \"properties\": { \"inline_cta_text\":
{ \"type\": \"text\", \"fields\": { \"keyword\": { \"type\":
\"keyword\", \"ignore_above\": 256 } } } } }, \"cta_text\": { \"type\":
\"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"duration_ms\": { \"type\": \"long\" },
\"height\": { \"type\": \"long\" }, \"id\": { \"type\": \"text\",
\"fields\": { \"keyword\": { \"type\": \"keyword\", \"ignore_above\":
256 } } }, \"player_url\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"thumbnail\": { \"type\": \"text\", \"fields\": { \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 } } }, \"type\": {
\"type\": \"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"url\": { \"type\": \"text\", \"fields\":
{ \"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"view_order\": { \"type\": \"text\", \"fields\": { \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 } } }, \"width\": {
\"type\": \"long\" } } }, \"created_date\": { \"type\": \"long\" },
\"description\": { \"type\": \"text\", \"fields\": { \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 } } }, \"enabled_tabs\": {
\"type\": \"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"fan_labels\": { \"properties\": {
\"type\": { \"type\": \"text\", \"fields\": { \"keyword\": { \"type\":
\"keyword\", \"ignore_above\": 256 } } }, \"value\": { \"type\":
\"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } } } }, \"follow_count\": { \"type\": \"long\"
}, \"hashtag\": { \"type\": \"text\", \"fields\": { \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 }, \"keyword_lowercase\": {
\"type\": \"text\", \"analyzer\": \"keyword_analyzer\" }, \"ngram\": {
\"type\": \"text\", \"analyzer\": \"edge_analyzer\" },
\"refined_soundex\": { \"type\": \"text\", \"analyzer\":
\"refined_soundex\" } }, \"copy_to\": \"search_fields\" }, \"id\": {
\"type\": \"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"image_post_count\": { \"type\": \"long\"
}, \"lang_code\": { \"type\": \"text\", \"fields\": { \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 } } }, \"level\": {
\"type\": \"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"modified_date\": { \"type\": \"long\" },
\"prev_image\": { \"type\": \"text\", \"fields\": { \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 } } }, \"prev_images\": {
\"properties\": { \"id\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"url\": { \"type\": \"text\", \"fields\": { \"keyword\": { \"type\":
\"keyword\", \"ignore_above\": 256 } } } } }, \"share_url\": { \"type\":
\"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"social_post_count\": { \"type\": \"long\"
}, \"status\": { \"type\": \"text\", \"fields\": { \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 } } }, \"strip_image\": {
\"type\": \"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"sub_title\": { \"type\": \"text\",
\"fields\": { \"keyword\": { \"type\": \"keyword\", \"ignore_above\":
256 }, \"keyword_lowercase\": { \"type\": \"text\", \"analyzer\":
\"keyword_analyzer\" }, \"ngram\": { \"type\": \"text\", \"analyzer\":
\"edge_analyzer\" }, \"refined_soundex\": { \"type\": \"text\",
\"analyzer\": \"refined_soundex\" } }, \"copy_to\": \"search_fields\" },
\"sub_type\": { \"type\": \"text\", \"fields\": { \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 }, \"keyword_lowercase\": {
\"type\": \"text\", \"analyzer\": \"keyword_analyzer\" }, \"ngram\": {
\"type\": \"text\", \"analyzer\": \"edge_analyzer\" },
\"refined_soundex\": { \"type\": \"text\", \"analyzer\":
\"refined_soundex\" } } }, \"target_languages\": { \"type\": \"text\",
\"fields\": { \"keyword\": { \"type\": \"keyword\", \"ignore_above\":
256 } } }, \"title\": { \"type\": \"text\", \"fields\": { \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 }, \"keyword_lowercase\": {
\"type\": \"text\", \"analyzer\": \"keyword_analyzer\" }, \"ngram\": {
\"type\": \"text\", \"analyzer\": \"edge_analyzer\" },
\"refined_soundex\": { \"type\": \"text\", \"analyzer\":
\"refined_soundex\" } }, \"copy_to\": \"search_fields\" },
\"total_post_count\": { \"type\": \"long\" }, \"type\": { \"type\":
\"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 }, \"keyword_lowercase\": { \"type\": \"text\",
\"analyzer\": \"keyword_analyzer\" }, \"ngram\": { \"type\": \"text\",
\"analyzer\": \"edge_analyzer\" }, \"refined_soundex\": { \"type\":
\"text\", \"analyzer\": \"refined_soundex\" } } }, \"video_post_count\":
{ \"type\": \"long\" }, \"view_count\": { \"type\": \"long\" },
\"zone_icon\": { \"type\": \"text\", \"fields\": { \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 } } }, \"zone_image\": {
\"type\": \"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"zone_strip_transcoding_status\": {
\"type\": \"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"zone_target\": { \"properties\": {
\"cover_banner\": { \"properties\": { \"cta_data\": { \"properties\": {
\"inline_cta_text\": { \"type\": \"text\", \"fields\": { \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 } } } } }, \"cta_text\": {
\"type\": \"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"duration_ms\": { \"type\": \"float\" },
\"id\": { \"type\": \"text\", \"fields\": { \"keyword\": { \"type\":
\"keyword\", \"ignore_above\": 256 } } }, \"pixel_size\": { \"type\":
\"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"player_url\": { \"type\": \"text\",
\"fields\": { \"keyword\": { \"type\": \"keyword\", \"ignore_above\":
256 } } }, \"thumbnail\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"type\": { \"type\": \"text\", \"fields\": { \"keyword\": { \"type\":
\"keyword\", \"ignore_above\": 256 } } }, \"url\": { \"type\": \"text\",
\"fields\": { \"keyword\": { \"type\": \"keyword\", \"ignore_above\":
256 } } }, \"view_order\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } } } },
\"description\": { \"type\": \"text\", \"fields\": { \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 } } }, \"fan_labels\": {
\"properties\": { \"type\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"value\": { \"type\": \"text\", \"fields\": { \"keyword\": { \"type\":
\"keyword\", \"ignore_above\": 256 } } } } }, \"lang_code\": { \"type\":
\"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"sub_title\": { \"type\": \"text\",
\"fields\": { \"keyword\": { \"type\": \"keyword\", \"ignore_above\":
256 } } }, \"title\": { \"type\": \"text\", \"fields\": { \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 } } } } },
\"zone_thumbnail_transcoding_status\": { \"type\": \"text\", \"fields\":
{ \"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"zone_thumbnail_transcoding_time\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"zone_type\": { \"type\": \"text\", \"fields\": { \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 } } }, \"zone_uuid\": {
\"type\": \"text\", \"fields\": { \"keyword\": { \"type\": \"keyword\",
\"ignore_above\": 256 } } }, \"search_fields\": { \"type\":
\"completion\", \"analyzer\": \"standard\", \"preserve_separators\":
true, \"preserve_position_increments\": true, \"max_input_length\": 50,
\"fields\": { \"autocomplete\": { \"type\": \"completion\",
\"analyzer\": \"stopword_analyzer\", \"preserve_separators\": true,
\"preserve_position_increments\": false, \"max_input_length\": 10 } },
\"contexts\": \[ { \"name\": \"zone_type\", \"type\": \"category\",
\"path\": \"zone_type\" } \] } } }, \"settings\": { \"index\": {
\"routing\": { \"allocation\": { \"include\": { \"\_tier_preference\":
\"data_content\" } } }, \"number_of_shards\": \"5\", \"analysis\": {
\"filter\": { \"ngram_long\": { \"token_chars\": \[ \"letter\",
\"digit\", \"punctuation\", \"symbol\" \], \"min_gram\": \"2\",
\"type\": \"edge_ngram\", \"max_gram\": \"80\" }, \"ngram_trans\": {
\"token_chars\": \[ \"letter\", \"digit\", \"punctuation\", \"symbol\"
\], \"min_gram\": \"5\", \"type\": \"edge_ngram\", \"max_gram\": \"33\"
}, \"ngram_trans_long\": { \"token_chars\": \[ \"letter\", \"digit\",
\"punctuation\", \"symbol\" \], \"min_gram\": \"5\", \"type\":
\"edge_ngram\", \"max_gram\": \"83\" }, \"refined_soundex_filter\": {
\"replace\": \"false\", \"type\": \"phonetic\", \"encoder\":
\"refinedsoundex\" }, \"beider_morse_filter\": { \"replace\": \"false\",
\"type\": \"phonetic\", \"encoder\": \"beider_morse\" }, \"ngram\": {
\"token_chars\": \[ \"letter\", \"digit\", \"punctuation\", \"symbol\"
\], \"min_gram\": \"2\", \"type\": \"edge_ngram\", \"max_gram\": \"30\"
}, \"metaphone_filter\": { \"replace\": \"false\", \"type\":
\"phonetic\", \"encoder\": \"doublemetaphone\" } }, \"analyzer\": {
\"edge_analyzer\": { \"filter\": \[ \"lowercase\", \"ngram\",
\"asciifolding\" \], \"type\": \"custom\", \"tokenizer\": \"whitespace\"
}, \"stopword_analyzer\": { \"type\": \"standard\", \"stopwords\": \[
\"and\", \"the\" \] }, \"refined_soundex\": { \"filter\": \[
\"lowercase\", \"refined_soundex_filter\" \], \"type\": \"custom\",
\"tokenizer\": \"standard\" }, \"keyword_analyzer\": { \"filter\": \[
\"lowercase\" \], \"type\": \"custom\", \"tokenizer\": \"keyword\" },
\"metaphone\": { \"filter\": \[ \"lowercase\", \"metaphone_filter\" \],
\"type\": \"custom\", \"tokenizer\": \"standard\" }, \"beider_morse\": {
\"filter\": \[ \"lowercase\", \"beider_morse_filter\" \], \"type\":
\"custom\", \"tokenizer\": \"standard\" }, \"edge_analyzer_long\": {
\"filter\": \[ \"lowercase\", \"ngram_long\", \"asciifolding\" \],
\"type\": \"custom\", \"tokenizer\": \"whitespace\" },
\"edge_analyzer_trans\": { \"filter\": \[ \"lowercase\",
\"ngram_trans\", \"asciifolding\" \], \"type\": \"custom\",
\"tokenizer\": \"whitespace\" }, \"edge_analyzer_trans_long\": {
\"filter\": \[ \"lowercase\", \"ngram_trans_long\", \"asciifolding\" \],
\"type\": \"custom\", \"tokenizer\": \"whitespace\" } } },
\"number_of_replicas\": \"1\" } } }

**[Reindex :]{.underline}**

jsonPOST \_reindex { \"source\": { \"index\": \"josh-zones-v3\" },
\"dest\": { \"index\": \"josh-zones-v4\" } }

**[Query:]{.underline}**

jsonGET josh-zones-v4/\_search { \"suggest\": { \"suggestestions\": {
\"prefix\": \"Dancing\", \"completion\": { \"field\": \"search_fields\",
\"size\": 7, \"skip_duplicates\": true, \"fuzzy\": { \"fuzziness\": 1 },
\"contexts\": { \"zone_type\": \[\"COLLECTION\", \"PERSON\"\] } } } } }
