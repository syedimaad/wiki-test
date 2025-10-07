json \"handle\": { \"type\": \"text\", \"fields\": { \"beider_morse\": {
\"type\": \"text\", \"analyzer\": \"beider_morse\" }, \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 }, \"keyword_lowercase\": {
\"type\": \"text\", \"analyzer\": \"keyword_analyzer\" }, \"metaphone\":
{ \"type\": \"text\", \"analyzer\": \"metaphone\" }, \"ngram\": {
\"type\": \"text\", \"analyzer\": \"edge_analyzer\" },
\"refined_soundex\": { \"type\": \"text\", \"analyzer\":
\"refined_soundex\" } }, \"copy_to\": \[ \"search_fields\" \] },
\"name\": { \"type\": \"text\", \"fields\": { \"beider_morse\": {
\"type\": \"text\", \"analyzer\": \"beider_morse\" }, \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 }, \"keyword_lowercase\": {
\"type\": \"text\", \"analyzer\": \"keyword_analyzer\" }, \"metaphone\":
{ \"type\": \"text\", \"analyzer\": \"metaphone\" }, \"ngram\": {
\"type\": \"text\", \"analyzer\": \"edge_analyzer\" },
\"refined_soundex\": { \"type\": \"text\", \"analyzer\":
\"refined_soundex\" } }, \"copy_to\": \[ \"search_fields\" \] },
\"tags\": { \"type\": \"text\", \"fields\": { \"beider_morse\": {
\"type\": \"text\", \"analyzer\": \"beider_morse\" }, \"keyword\": {
\"type\": \"keyword\", \"ignore_above\": 256 }, \"keyword_lowercase\": {
\"type\": \"text\", \"analyzer\": \"keyword_analyzer\" }, \"metaphone\":
{ \"type\": \"text\", \"analyzer\": \"metaphone\" }, \"ngram\": {
\"type\": \"text\", \"analyzer\": \"edge_analyzer\" },
\"refined_soundex\": { \"type\": \"text\", \"analyzer\":
\"refined_soundex\" } }, \"copy_to\": \[ \"search_fields\" \] },
\"search_fields\": { \"type\": \"completion\", \"analyzer\":
\"standard\", \"preserve_separators\": true,
\"preserve_position_increments\": true, \"max_input_length\": 50,
\"fields\": { \"autocomplete\": { \"type\": \"completion\",
\"analyzer\": \"stopword_analyzer\", \"preserve_separators\": true,
\"preserve_position_increments\": false, \"max_input_length\": 10 } } }
