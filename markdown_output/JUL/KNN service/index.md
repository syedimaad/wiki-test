Main repo <https://gitlab.dailyhunt.in/dmitry.yashunin/knn>

## HNSW web server

Code
<https://gitlab.dailyhunt.in/dmitry.yashunin/knn/blob/develop/Simple-Web-Server/hnswlib_server.cpp>

### How to start

wide./hnswlib_server \<data dim\> \<search space\> \<s3 path to
serialised hnsw index\> \<s3 path to hnsw dict\>

Example

wide./hnswlib_server 128 l2 \\
s3://josh-reco-ml-dataset/us-ml-team/dmitryy/knn/hnsw_server_tests/hnsw_index.bin
\\
s3://josh-reco-ml-dataset/us-ml-team/dmitryy/knn/hnsw_server_tests/hnsw_index_dict.txt

Server status can be checked by GET request
`http://{server IP}:8000/status`\
Server outputs json `{"status": <status>}` . If server is ready the
status will be `"INDEX_INITIALIZED"`

### Types of supported requests

Code with examples how to prepare data, send requests, receive and parse
responses :\
<https://gitlab.dailyhunt.in/dmitry.yashunin/knn/blob/master/utils/sanity_check_hnsw_server.py>\
<https://gitlab.dailyhunt.in/dmitry.yashunin/knn/blob/master/utils/load_tester.py>

#### Check status

Used to check if server is ready

GET request to `http://{server IP}:8000/status`

Server outputs json `{"status": <status>}` . If server is ready the
status will be `"INDEX_INITIALIZED"`

#### Health check

Used to check if server is ready

GET request to `http://{server IP}:8000/healthcheck`

If server is ready the server will return `"HTTP/1.1 200 OK"`, if server
is not ready it will return `"HTTP/1.1 400 Bad Request"`

#### Set ef

Sets `ef` parameter for search requests

POST request to `http://{IP}:8000/request`\
json format of the request:

json{\"request_type\": \"SET_EF\", \"params\": {\"ef\": \<integer ef
value\>}}

#### Get items

Returns vectors for specified item_ids

POST request to `http://{IP}:8000/request`\
json format of the request:

json{\"request_type\": \"GET_ITEMS\", \"params\": {\"ids\": \<string
with ids\>}}

string contains ids delimited by spaces

Server will send json:

json{\"found\": \<string with 0 and 1\>, \"items\": \<base64 encoded bin
numpay array\> }

"found": 0 - item id is not found in the index, 1 - item id is found\
base 64 encoded string contains flatten binary numpy array\

#### Search knn

Returns nearest neighbours for query with item ids or vectors

POST request to `http://{IP}:8000/request`\
json format of the request:

json{\"request_type\": \"SEARCH_KNN\", \"params\": {\"k\": k,
\"query_size\": \<integer query size\>, \"query_ids\": \<string with
ids\>, \# optional \"query\": \<base64 encoded bin numpay array\>, \#
optional \"send_items_back\": \<True/False\>, \# optional
\"send_ids_back\": \<True/False\>, \# optional \"send_distances_back\":
\<True/False\> \# optional }}

`query_ids` is string with ids delimited by spaces\
`query` is base 64 encoded string containing binary numpy array of shape
\[query_size, dim\]\
flags `send_items_back` `send_ids_back` `send_distances_back` are
optional, keep only those that are `True`

Server will send json:

json{\"num_neighbors\": \<base64 encoded bin numpay array\>, \"items\":
\<base64 encoded bin numpay array\>, \# optional \"ids\": \<string with
ids\>, \# optional \"distances\": \<base64 encoded bin numpay array\> \#
optional }

all base64 strings contain flatten binary numpy arrays

## Build hnsw index

code
<https://gitlab.dailyhunt.in/dmitry.yashunin/knn/blob/develop/utils/build_hnsw_index.py>

`build_hnsw_index.py` builds hnsw index, checks recall, save serialised
index to s3, can apply PCA model to data. PCA model can be trained from
scratch or loaded from s3.

Script works in 2 modes:

- full

- incremental

In `full` mode hnsw index is built from scratch. Use `--save_pca_data`
parameter to save PCA data. PCA model is saved automatically.

In `incremental` mode existing hnsw index is periodically updated with
new items and serialised. Existing index is loaded, s3 folder with
incremental items is checked for new items, new items are added to the
index.

Index is serialised in 2 files: `hnsw_index.bin` and
`hnsw_index_dict.txt`

`--src_list` specifies list of s3 paths to parquet files with items.
Columns must have names \"item_id\" and \"item_embedding\".

### Examples

#### Full mode

Load 768 BLIP embeddings from parquet files in s3 from `src_list`, train
PCA model to compress data to 128, save results to s3 in `work_dir`
folder

python3 build_hnsw_index.py \--full \--apply_trained_pca \--pca_dim 128
\\ \--src_list
s3://aiml-lab-datalakes/content_embeddings/BLIP/view_bucket/gt_100/ \\
\--work_dir \<your s3 work dir folder\>

Load 768 BLIP embeddings from parquet files in s3, apply pretrained PCA
model to compress data to 128, save results to s3 in `work_dir` folder

python3 build_hnsw_index.py \--full \--apply_pretrained_pca \\
\--pca_pretrained
s3://josh-reco-ml-dataset/us-ml-team/dmitryy/knn/hnsw_server_tests_full/pca_model.pckl
\\ \--src_list
s3://aiml-lab-datalakes/content_embeddings/BLIP/view_bucket/gt_100/ \\
\--work_dir \<your s3 work dir folder\>

`pca_pretrained` points to the s3 path of the pretrained PCA model

Build index from provided data without applying PCA (`--src_list` points
to s3 folder with data) save results to s3 in `work_dir` folder

python3 build_hnsw_index.py \--full \\ \--src_list
s3://josh-reco-ml-dataset/us-ml-team/dmitryy/knn/hnsw_server_tests_full/PCA_data_128/
\\ \--work_dir \<your s3 work dir folder\>

#### Incremental mode

Every `period` minutes checks `src` folder in s3 for new items and adds
the to the index. Results are saved in `work_dir`. Index is preloaded
from `index_bin_in` and `index_dict_in` paths. `dim` dimension of the
data. `max_elements` specifies maximal expected number of items in the
index.

python3 build_hnsw_index.py \--incremental \\ \--src_list
s3://josh-reco-ml-dataset/us-ml-team/dmitryy/knn/hnsw_server_tests/PCA_data_128/
\\ \--dim 128 \\ \--work_dir
s3://josh-reco-ml-dataset/us-ml-team/dmitryy/knn/hnsw_server_tests_incremental_mac
\\ \--index_bin_in
s3://josh-reco-ml-dataset/us-ml-team/dmitryy/knn/hnsw_server_tests_mac/hnsw_index.bin
\\ \--index_dict_in
s3://josh-reco-ml-dataset/us-ml-team/dmitryy/knn/hnsw_server_tests_mac/hnsw_index_dict.txt
\\ \--period 60 \\ \--max_elements 100000000

Notes on `max_elements` parameter. It should be relatively high so that
we fit into RAM. If the actual number of items (items in preloaded
index + new items) exceeds the `max_elements` script will stop working.
