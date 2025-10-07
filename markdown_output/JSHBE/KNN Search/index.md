#### Capacity Assumption/Planning

Each node is to handle 1M documents. Using this as a baseline, below is
the number of shards to bucket mapping.

  ----------------- ------------------------------ --------------------------------------------------------- ---------------------- --------------
  **Bucket Name**   **Parameters**                 **S3 Location**                                           **Number of Shards**   **Priority**
  V100              views \> 100                   /bucket/\<lang_code\>/shard_id/\*.sst \|\| \*.scanmodel   15                     2
  V1000             views \> 1000                  /bucket/\<lang_code\>/shard_id/\*.sst \|\| \*.scanmodel   5                      1
  DAILY             created_date \> Now - 3 Days   /bucket/\<date\>/shard_id/\*.sst \|\| \*.scanmodel        3                      3
  ----------------- ------------------------------ --------------------------------------------------------- ---------------------- --------------

#### Shard Strategy

Murmur 128 bit hash to be used against the content uuid. Further take
modulus based on the number of shards based on the bucket type.

  ------------ ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ ------------------------------
  **Module**   **Library**                                                                                                                                                                                                                                      **Function/Parameters**
  Java         [https://commons.apache.org/proper/commons-codec/apidocs/org/apache/commons/codec/digest/MurmurHash3.html](https://commons.apache.org/proper/commons-codec/apidocs/org/apache/commons/codec/digest/MurmurHash3.html){card-appearance="inline"}   hash128, seed=0, signed=True
  Python       [https://pypi.org/project/murmurhash3/](https://pypi.org/project/murmurhash3/){card-appearance="inline"} , [https://pypi.org/project/mmh3/](https://pypi.org/project/mmh3/){card-appearance="inline"}                                            hash128, seed=0, signed=True
  ------------ ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ ------------------------------

#### APIs

+----------------+----------------+-----------------------------+------------------+
| **Task**       | **Comments**   | **Endpoint**                | **Availability** |
+----------------+----------------+-----------------------------+------------------+
| Content uuid   | Given a        | Method: GET\                | Node, Cluster    |
| to Embedding   | content uuid.  | Path:                       |                  |
|                | Fetch the      | /embedding/\<content_uuid\> |                  |
|                | embedding from |                             |                  |
|                | the rocks db   |                             |                  |
+----------------+----------------+-----------------------------+------------------+
| Similar        | Get K similar  | Method: POST\               | Node             |
| Content        | items based on | Path: /similar\             |                  |
| Search, KNN    | the embedding  | Body: { embedding : byte    |                  |
| Search         |                | array, k : no of similar    |                  |
|                |                | items}                      |                  |
+----------------+----------------+-----------------------------+------------------+
| KNN Search →   | 1.  Fetch K    | Method: POST\               | Cluster          |
| Generate       |     similar    | Path: /generate-candidate\  |                  |
| Candidate      |     items from | Body: { history : byte      |                  |
|                |     all nodes  | array, bucket_name:         |                  |
|                |                | knn_search_gt_100 , k : no  |                  |
|                | 2.  Search API | of similar items , data: \[ |                  |
|                |     on node to | { content_uuid: ,           |                  |
|                |     exclude    | lang_code: } ...\]          |                  |
|                |     the        |                             |                  |
|                |     Historical |                             |                  |
|                |     items      |                             |                  |
|                |     based on   |                             |                  |
|                |     input      |                             |                  |
|                |     bloom      |                             |                  |
|                |     filter     |                             |                  |
|                |                |                             |                  |
|                | 3.  Merge the  |                             |                  |
|                |     results    |                             |                  |
|                |     from each  |                             |                  |
|                |     node and   |                             |                  |
|                |     send back  |                             |                  |
|                |     the        |                             |                  |
|                |     response   |                             |                  |
+----------------+----------------+-----------------------------+------------------+
| Topology       | 1.  Node Id to |                             | Cluster          |
|                |     Shard Id   |                             |                  |
|                |     Mapping    |                             |                  |
+----------------+----------------+-----------------------------+------------------+

#### SST/Scan Files

1.  Base path: s3://aiml-lab-datalakes/content_embeddings_knn/BLIP

2.  scann_model_path :
    {base_path}/{bucket_name}/scann_models/{lang}/{shard_num}

3.  sst_files_path -\> {base_path}/{bucket_name}/sst_files/{shard_num}

4.  languages - \'hi\', \'te\', \'ta\', \'en\', \'pa\', \'gu\', \'or\',
    \'ml\', \'mr\', \'bh\', \'bn\', \'kn\'

5.  bucket_name - \'knn_search_gt_1000\', \'knn_search_gt_100\',
    \'knn_search_daily\'

6.  shard_num

    1.  \'gt_1000\':\[0,1,2,\...4\]

    2.  \'gt_100\':\[0,1,2,\...14\]

    3.  \'daily\':\[0\]

  ---------- -- --
  **Path**      
                
                
  ---------- -- --

`base_path = scann_model_path -> sst_files_path -> {base_path}/{bucket_name}/sst_files/{shard_num} languages - 'hi', 'te', 'ta', 'en', 'pa', 'gu', 'or', 'ml', 'mr', 'bh', 'bn', 'kn' bucket_name - 'gt_1000', 'gt_100', 'daily' shard_num - {'gt_1000':[0,1,2,...4], 'gt_100':[0,1,2,...14], 'daily':[0] }`

#### Architecture

Cluster Name → knn-\<bucket-name\>-blip-\<version\>-internal.myjosh.in
