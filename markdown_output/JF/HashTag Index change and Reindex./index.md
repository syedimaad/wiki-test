[Index Definition:]{.underline}

jsonPUT ugc-hashtag-v2 { \"mappings\" : { \"properties\" : {
\"agg_modified_at\" : { \"type\" : \"text\", \"fields\" : { \"keyword\"
: { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"ancilliary_tags\" : { \"type\" : \"text\", \"fields\" : { \"keyword\"
: { \"type\" : \"keyword\", \"ignore_above\" : 256 } } },
\"download_count\" : { \"type\" : \"long\" }, \"fk_download_count\" : {
\"type\" : \"long\" }, \"fk_downloads\" : { \"type\" : \"long\" },
\"fk_like_count\" : { \"type\" : \"long\" }, \"fk_likes\" : { \"type\" :
\"long\" }, \"fk_share_count\" : { \"type\" : \"long\" }, \"fk_shares\"
: { \"type\" : \"long\" }, \"fk_view_count\" : { \"type\" : \"long\" },
\"fk_views\" : { \"type\" : \"long\" }, \"id\" : { \"type\" : \"text\",
\"fields\" : { \"keyword\" : { \"type\" : \"keyword\", \"ignore_above\"
: 256 } } }, \"like_count\" : { \"type\" : \"long\" }, \"modified_date\"
: { \"type\" : \"date\" }, \"name\" : { \"type\" : \"text\", \"fields\"
: { \"keyword\" : { \"type\" : \"keyword\", \"ignore_above\" : 256 } },
\"copy_to\": \"search_fields\" }, \"name_trans\" : { \"type\" :
\"text\", \"fields\" : { \"keyword\" : { \"type\" : \"keyword\",
\"ignore_above\" : 256 } } }, \"search_fields\": { \"type\":
\"completion\", \"analyzer\": \"standard\", \"preserve_separators\":
true, \"preserve_position_increments\": true, \"max_input_length\": 50,
\"fields\": { \"autocomplete\": { \"type\": \"completion\",
\"analyzer\": \"stopword_analyzer\", \"preserve_separators\": true,
\"preserve_position_increments\": false, \"max_input_length\": 10 } } },
\"play_count\" : { \"type\" : \"long\" }, \"share_count\" : { \"type\" :
\"long\" }, \"unlike_count\" : { \"type\" : \"long\" }, \"view_count\" :
{ \"type\" : \"long\" } } }, \"settings\": { \"index\": {
\"number_of_shards\" : \"5\", \"number_of_replicas\" : \"1\",
\"analysis\": { \"analyzer\": { \"stopword_analyzer\": { \"type\":
\"standard\", \"stopwords\": \[ \"and\", \"the\" \] } } } } } }

**[Reindex the data:]{.underline}**

jsonPOST \_reindex { \"source\": { \"index\": \"ugc-hashtag-v1\" },
\"dest\": { \"index\": \"ugc-hashtag-v2\" } }

**[Sample Get Query:]{.underline}**

jsonGET ugc-hashtag-v2/\_search { \"suggest\": { \"suggestestions\": {
\"prefix\": \"sou\", \"completion\": { \"field\": \"search_fields\",
\"size\" : 7, \"skip_duplicates\" : true, \"fuzzy\":{ \"fuzziness\" : 1
} } } } }
