Index Definition:

jsonPUT type-ahead-v3 { \"mappings\": { \"properties\": { \"count\": {
\"type\": \"long\" }, \"id\": { \"type\": \"text\", \"fields\": {
\"keyword\": { \"type\": \"keyword\", \"ignore_above\": 256 } } },
\"search_term\": { \"type\": \"completion\", \"analyzer\": \"standard\",
\"preserve_separators\": true, \"preserve_position_increments\": true,
\"max_input_length\": 50, \"contexts\": \[ { \"name\": \"searchable\",
\"type\": \"category\" } \], \"fields\": { \"autocomplete\": { \"type\":
\"completion\", \"analyzer\": \"stopword_analyzer\",
\"preserve_separators\": true, \"preserve_position_increments\": false,
\"max_input_length\": 10 } } } } }, \"settings\": { \"analysis\": {
\"analyzer\": { \"stopword_analyzer\": { \"stopwords\": \[ \"and\",
\"the\" \], \"type\": \"standard\" } } } } }

\
[**Search Query :**]{.underline}

json POST type-ahead-v2/\_search?pretty { \"suggest\": {
\"suggestestions\": { \"prefix\": \"sety\", \"completion\": { \"field\":
\"search_term\", \"size\" : 7, \"skip_duplicates\" : true, \"contexts\"
: { \"searchable\" : \[true\] }, \"fuzzy\":{ \"fuzziness\" : 1 } } } } }
