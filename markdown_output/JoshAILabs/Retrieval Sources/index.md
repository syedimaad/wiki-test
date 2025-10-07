This page will have all the monitoring and alert details about all the
candidate retrieval sources and offline indexes/processes that support
the feed.

List of candidate arms and respective indexes to be monitored:

+------------------------------------------------------------------------------------------------+----------+---------------------------------------+-----------+
| **Index Name**                                                                                 | **% VP** | **Candidate source supported**        | **Owner** |
+------------------------------------------------------------------------------------------------+----------+---------------------------------------+-----------+
| [PPR                                                                                           | 29-32%   | content_based_ppr                     |           |
| Index](https://evp.atlassian.net/wiki/spaces/JoshAILabs/pages/372965454/Retrieval+Sources#PPR) |          |                                       |           |
|                                                                                                |          | content_based_ppr_non_hindi           |           |
|                                                                                                |          |                                       |           |
|                                                                                                |          | content_based_ppr_non_hindi_coldstart |           |
|                                                                                                |          |                                       |           |
|                                                                                                |          | content_based_ppr_coldstart           |           |
+------------------------------------------------------------------------------------------------+----------+---------------------------------------+-----------+
| Coldstart Content                                                                              | 12%      | v2v_recent_watch_coldstart_content\   |           |
|                                                                                                |          | v2v_blip_most_recent_like\            |           |
|                                                                                                |          | v2v_blip_hist_coldstart_content\      |           |
|                                                                                                |          | u2v_blip_coldstart_content            |           |
+------------------------------------------------------------------------------------------------+----------+---------------------------------------+-----------+
| MTL - Candidate Generation                                                                     | 3%       | dnn_mtl_model_gt5_p90_v1_hi           |           |
+------------------------------------------------------------------------------------------------+----------+---------------------------------------+-----------+
| V2V                                                                                            | 50%      | v2v_recent_watch                      |           |
|                                                                                                |          |                                       |           |
|                                                                                                |          | v2v_blip_hist                         |           |
+------------------------------------------------------------------------------------------------+----------+---------------------------------------+-----------+
| Popular Source                                                                                 |          |                                       |           |
+------------------------------------------------------------------------------------------------+----------+---------------------------------------+-----------+

## Index-wised Tracked Metrics:

### MTL - Candidate Generation:

#### **Datagen (**[**Github**](https://gitlab.dailyhunt.in/josh-ai-labs/josh-dnn-two-tower-recsys/-/blob/gcp_changes/dataproc_scripts/mtl_datagen_dag.py) **\|** [**Airflow**](https://9291f5f1902943c2af4748fe9fc5cde1-dot-asia-south1.composer.googleusercontent.com/dags/mtl-datagen/grid)**)** 

1.  py{ \"datagen_start_time\": \"2023-09-14::10:08:51\",
    \"num_raw_events\": 798019767, \"num_raw_items\": 2551996,
    \"num_events_post_filter_item_moderation\": 762270080,
    \"num_items_post_filter_item_moderation\": 2028824,
    \"item_loss_percentage_item_moderation\": 20.5005,
    \"num_events_post_filter_feed_source\": 444220921,
    \"num_items_post_filter_feed_source\": 921680,
    \"item_loss_percentage_feed_source\": 43.3835,
    \"num_events_post_filter_client_events\": 400229791,
    \"num_items_post_filter_client_events\": 886727,
    \"item_loss_percentage_client_events\": 1.3696,
    \"num_events_post_filter_video_length\": 400226999,
    \"num_items_post_filter_video_length\": 886485,
    \"item_loss_percentage_video_length\": 0.0095,
    \"num_events_post_filter_play_duration\": 379864163,
    \"num_items_post_filter_play_duration\": 871385,
    \"item_loss_percentage_play_duration\": 0.5917,
    \"num_events_post_filter_item_age\": 378861449,
    \"num_items_post_filter_item_age\": 844078,
    \"item_loss_percentage_item_age\": 1.07,
    \"num_events_post_filter_item_events\": 376982210,
    \"num_items_post_filter_item_events\": 728868,
    \"item_loss_percentage_item_events\": 4.5145,
    \"num_events_post_filters\": 376982210,
    \"num_unique_items_post_filters\": 728868,
    \"num_items_post_embed_join\": 728706,
    \"item_loss_post_embedding_join\": 0.0222,
    \"num_events_post_embedding_join\": 376975889, \"num_final_rows\":
    376975889, \"item_age_bucket_formated\": { \"(-inf, 0.0\]\": \"0
    (0.0%)\", \"(0.0, 1.0\]\": \"7,539 (1.03%)\", \"(1.0, 2.0\]\":
    \"8,817 (1.21%)\", \"(2.0, 4.0\]\": \"34,625 (4.75%)\", \"(4.0,
    7.0\]\": \"85,162 (11.69%)\", \"(7.0, 14.0\]\": \"72,460 (9.94%)\",
    \"(14.0, 30.0\]\": \"173,006 (23.74%)\", \"(30.0, 60.0\]\":
    \"228,166 (31.31%)\", \"(60.0, 90.0\]\": \"118,931 (16.32%)\",
    \"(90.0, inf\]\": \"0 (0.0%)\" }, \"item_age_buckets_delta_7d\": {
    \"(-inf, 0.0\]\": \"0 (+0.0%)\", \"(0.0, 1.0\]\": \"477 (+6.75%)\",
    \"(1.0, 2.0\]\": \"2,819 (+47.0%)\", \"(2.0, 4.0\]\": \"5,199
    (+17.67%)\", \"(4.0, 7.0\]\": \"-5,856 (-6.43%)\", \"(7.0, 14.0\]\":
    \"-24,594 (-25.34%)\", \"(14.0, 30.0\]\": \"11,537 (+7.15%)\",
    \"(30.0, 60.0\]\": \"30,830 (+15.62%)\", \"(60.0, 90.0\]\": \"-3,899
    (-3.17%)\", \"(90.0, inf\]\": \"0 (+0.0%)\" },
    \"new_items_in_index_1d_delta\": \"26,612 (3.65%)\",
    \"common_items_in_index_1d_delta\": \"702,094 (96.35%)\",
    \"item_diff_1d_delta\": \"3,848 (+0.53%)\", \"item_diff_7d_delta\":
    \"16,513 (+2.32%)\", \"datagen_run_time\": \"3.0h:21mins\",
    \"datagen_end_time\": \"2023-09-14::13:30:12\", \"SUCCESS\": true }

**Error Alerts added:**

- delta_1d, delta_7d events/items less than 10%.

- delta_1d, delta_7d item_age buckets less than 10%.

- raw data not found for more than 3hrs.

- delta_1d new items less than 3%.

- any error occurred while running datagen.

**Schedule:**

- Runs daily 8:30am IST:

  - ~Starts\ with\ generating\ date\ for\ which\ it\ has\ to\ process,~

  - ~Checks\ and\ waits\ for\ V4\ Success\ file,\ present\ in~
    `snapshot/train-dataset-v4/daily_success_files`

  - ~Starts\ Dataproc\ cluster\ and\ submits\ the\ datagen\ job.~

  - ~Datagen\ starts\ with\ filtering\ the\ data\ based\ on\ item_lang\ and\ then\ samples\ 70%\ random\ data~

  - ~Datagen\ applies\ filters\ defined\ in\ config\ file\ in\ the\ same\ order,\ and\ also\ checks\ for\ reduce\ in\ events\ as\ well\ as\ items\ per\ filter\ and\ alerts\ the\ user\ if\ anything\ goes\ +-\ the\ defined\ thresholds.~

  - ~Some\ preprocessing\ is\ applied\ to\ normalize\ the\ float\ columns\ and\ nulls\ are\ replaced\ with\ some\ constant\ values.~

  - ~Blip\ embeds\ are\ read\ from\ 128\ dim\ data\ and\ items\ are\ filtered\ out\ if\ the\ blip\ embed\ is\ not\ found.~

  - ~Meta\ data\ is\ saved\ along\ with\ latest\ item\ and\ user\ features\ available,\ then\ the\ processed\ Data\ is\ written\ to\ Cloud.~

  - ~Monitoring\ dict\ is\ saved\ and\ processed\ for\ any\ alerts\ to\ be\ sent.~

  - ~On\ datagen\ completion\ cluster\ gets\ terminated\ and\ data_copy\ success\ file\ is\ generated\ in\ Azure~

  - ~Using\ Azure~
    [~data\ factory\ pipeline~](https://adf.azure.com/en/authoring/pipeline/copy_mtl_datagen_from_gcs?factory=%2Fsubscriptions%2Ff6b7aa7e-08ed-4347-ac30-c9efab8702b2%2FresourceGroups%2FJosh-Prod-aiml-RG%2Fproviders%2FMicrosoft.DataFactory%2Ffactories%2FCopy-data-from-AWS)~,\ the\ data\ is\ being\ copied\ from\ gcp\ to\ azure.~

**Deployment Details:**

- Setup:

  - Job running on
    [Airflow](https://9291f5f1902943c2af4748fe9fc5cde1-dot-asia-south1.composer.googleusercontent.com/dags/mtl-datagen/grid).

  - Using Dataproc Cluster to create data.

- Cluster Details:

  - master-node: 1 \* `n2d-standard-8`

  - core-nodes: 15 \* `n2d-highmem-16`

**Files:**

- [josh_recsys_datagen_gcp.py](https://gitlab.dailyhunt.in/josh-ai-labs/josh-dnn-two-tower-recsys/-/blob/gcp_changes/dataproc_scripts/josh_recsys_datagen_gcp.py):
  main_datagen file

- [main-config.yaml](https://gitlab.dailyhunt.in/josh-ai-labs/josh-dnn-two-tower-recsys/-/blob/gcp_changes/core/cfgs/main-config.yaml)
  main_config file

**Alerts Groups**:
[Info](https://chat.google.com/room/AAAAecldEGQ?cls=7) \|
[Error](https://chat.google.com/room/AAAAtqHMPkg?cls=7)

#### **MODEL TRAINING (**[**Git**](https://gitlab.dailyhunt.in/josh-ai-labs/mtl_candidate_generation/-/tree/azure-training?ref_type=heads)**)**

**Deployment Details:**

- Node Type: [Standard NC48ads A100 v4 (48 vcpus, 440 GiB
  memory)]{style="color: rgb(76,154,255);"}

- IP: [10.70.8.4]{style="color: rgb(76,154,255);"}

**Metrics:**

1.  Scann model size

2.  Loss of the model

3.  Training time taken

**Model Training error alerts:**

1.  Notify if SUCCESS file doesn't exist after 3 hr

2.  Error in item vectors generation

3.  Error in scann model creation

4.  Error in TSNE dataframe creation

5.  Error in assets update on Azure

6.  Error in assets copy to GCP

7.  Error in assets copy to AWS

**Scripts:**

1.  datasets/torch_dataset.py - Helps in reading data from azure

2.  item_vectors_extraction.py - Helps to generate item vector from
    student model

3.  save_scann_model.py - Created and saves the scann model once the
    vectors are generated

4.  train.py - Executes the mtl training

5.  upload_to_az.py - Uploads the model assets to azure

6.  cfgs/mtl_config.yaml - Cofig to take layers, inputs, etc dimension

7.  generate_clusters.py - Generate TSNE df with item vectors

8.  models/custom_layers.py - Custom layers like QR embedding, Embedding
    Aggregator, etc

9.  models/mmoe.py - This is the teacher model of mtl

10. models/two_tower.py - This is the student part of mtl

11. save_user2item_scann_model.py - Creates and saves scann model of u2i

12. upload_from_az_to_aws.py - Uploads data from azure to aws

13. user_vectors_extraction.py - Helps in extraction of user vectors
    from model

14. config_parser.py - Used to parse config

15. item_streamlit_viewer.py - Helps in visualizing the TSNE df

16. python_utils.py - Support functions for python

17. scripts/notify_chat.py - Sends notification in chat groups

18. scripts/notify_helper.py - Helper class for notify_chat.py

19. scripts/script_helper.py - Additional helper functions

20. scripts/upload_files.sh - Was used to copy code from local to aws

21. upload_from_az_to_gcp.py - It is used to upload assets from azure to
    gcp

**Schedule:**

It starts looking for SUCCESS file on azure "mtl-recommendation"
container at 11am, whenever that file is there, it starts training with
"ray". Once all the epochs are completed and model weights are there,
the item_vector generation starts. After having the vectors, we create
TSNE and Scann Model. It is then pushed to azure and also copied to GCP.

**Alerts Groups**:
[Info](https://chat.google.com/room/AAAAecldEGQ?cls=7) \|
[Error](https://chat.google.com/room/AAAAtqHMPkg?cls=7)

## Coldstart content HNSW 

Metrics Logged:

{ \"7d index pushed\": true, \"48h index pushed\": true, \"start_time\":
\"YYYY-MM-DD HH:mm:ss\", \"item_count\": \<count of items from query\>,
\"embedding_count\": \<count of embeddings found\>,
\"percent_of_embeddings_missing\": \<%age of embeddings missing\> ,
\"Delta (new items) between previous and new index\": \<\>, \"Count for
7d index\": \<\>, \"Count for 48h index\": \<\>, \"Day-Wise Count
distribution for 7d\": { }, \"Time taken (seconds) to create 7d index\":
279.854627, \"Time taken (seconds) to create 48h index\": 0.321115,
\"Current Index Size in MB (7d)\": 289.21605682373047, \"Previous Index
Size in MB (7d)\": 287.00686264038086, \"Difference in Size (Current -
Prev) (7d)\": 2.2091941833496094, \"end_time\": \"2023-08-08 10:10:02\"
\"Diff between current run and previous avg\": { \"No. of previous runs
available(out of 7) for Diff in Avg\": 7, \"Run time checked\": \<run
time\>, \"Diff in Count for 7d index\": \" %\", \"Diff in Avg. Video
Duration 7d\": \" %\", \"Diff in Avg. Video Duration 48h\": \" %\",
\"Diff in Current Index Size in MB (7d)\": \" %\", \"Diff in
Language-Wise Count distribution for 7 day index\": { \"All\": \" %\",
\"NA\": \" %\", \"bh\": \" %\", \"bn\": \" %\", \"en\": \" %\", \"gu\":
\" %\", \"hi\": \" %\", \"kn\": \" %\", \"ml\": \" %\", \"mr\": \" %\",
\"na\": \" %\", \"or\": \" %\", \"pa\": \" %\", \"ta\": \" %\", \"te\":
\" %\" } }, \"version\": \"YYYYMMDDHH\" }

**Alerts**:

- \"Count for 7d index\", \"Avg. Video Duration 7d\", \"Avg. Video
  Duration 48h\", \"Current Index Size in MB (7d)\",

  if delta between value of current run and avg value of last 7 runs is
  \>50% or \<-50%

- `percent_of_embeddings_missing` \> 0.15%

- `Delta (new items) between previous and new index` = 0

**Scripts:**

<https://gitlab.dailyhunt.in/josh-ai-labs/cold_start_hnsw/-/tree/dev_gcs?ref_type=heads>

- [cold_start_hnsw_script.py](https://gitlab.dailyhunt.in/josh-ai-labs/cold_start_hnsw/-/blob/dev_gcs/cold_start_hnsw_script.py) -
  contains all the code to generate coldstart indices.

- [config.json](https://gitlab.dailyhunt.in/josh-ai-labs/cold_start_hnsw/-/blob/dev_gcs/config.json) -
  related config used by the above script.

**Schedule:**

Currently the script is run on an GCP instance every 2 hours. It is
controlled by an airflow (<http://10.180.191.221:8080/home>)from where 4
commands are executed:

- Start VM

- Run script on VM

- Stop VM

- Generate monitoring reports.

## PPR

PPR is a graph based retrieval source, which has N nodes (item-id's) and
E weighted edges (weighted number of common zones between two item-ids)

### Touch Points:

- Detailed Doc : Personalised Page Rank (PPR)

- Code Repository :
  <https://gitlab.dailyhunt.in/josh-ai-labs/ppr-graph-generation/-/tree/prod>

- Airflow Dag :
  <https://31f876a73e4f40ef8fef41318fbb66cc-dot-asia-south1.composer.googleusercontent.com/dags/ppr_graph_gen>

- Notification channels:

  - \[INFO\] PPR Daily Runner →
    <https://chat.google.com/room/AAAAQnw1-5A?cls=4>

  - \[ERROR\] PPR Daily Runner→
    <https://chat.google.com/room/AAAAGnAE5vc?cls=4>

- Metrics Dashboard →
  <http://10.180.128.17:8010/public/dashboard/5b4daad1-fda5-47a3-bfd6-7f3a7b09d8e4>

### Metrics logged:

The following metrics are logged on each run

- Target Date : The target date of graph gen from which events prior to
  X (45) days will be considered during graph generation

- Size of graph (GB): The edge list dataset file size in gb, of the
  graph created

- Total number of nodes in graph: Here node represents the item id, so
  total number of unique item ids

- Total number of edges in graph: Here edge represented by item_id_1 and
  item_id_2 having positive interaction in the same session, so total
  number of such type of pairs or edges.

- Average video length: The average video length of all the nodes
  (items/videos) in the graph

- Item Age Distribution : Distribution of item ages over certain fixed
  buckets

- Language Distribution : Distribution of item languages over all
  distinct languages

### Metrics Dashboard:

- An Internal Dashboard is available to compare the above metrics

- Dashboard link →
  <http://10.180.128.17:8010/public/dashboard/5b4daad1-fda5-47a3-bfd6-7f3a7b09d8e4>

### Notifications - Alerts/Reports:

- Any alerts due to exceptions occured in pipeline will be sent to
  respective ERROR Gchat space

- A detailed summary report will be sent to respective INFO Gchat space
  with the above metrics and their comparison (percentage delta) with
  the previous day run as well as the average of prior 7 days runs

- Following is an example report\

  PPR Graph Gen Monitoring Report Target Date : 2023-09-14 Delta between
  current and previous day run Basic Metrics num_items(delta%) num_nodes
  848977(+0.16%) num_edges 353639179(-0.64%) size_gb 25.97(-0.66%)
  avg_vlen 17.33(+0.11%) Item Age Distribution num_items(delta%) 91-120
  50333(-1.48%) 8-14 60618(-2.66%) 61-90 195029(+0.82%) 31-60
  282132(+0.37%) 2-7 51345(+0.34%) 15-30 205316(+0.35%) 120+ 0(0.0%) 1
  3151(+3.55%) 0 1052(+7.19%) Language Distribution num_items(delta%) te
  27353(-0.41%) ta 32589(+0.09%) pa 10461(+0.86%) or 593(-2.0%) na
  13729(+1.37%) mr 13210(+1.49%) ml 2940(+0.07%) kn 16837(+0.06%) hi
  447897(-0.01%) gu 2501(-1.82%) en 234287(+0.32%) bn 26646(+0.64%) bh
  19740(+0.47%) all 112(-8.55%)
  \-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--
  Delta between current and average of previous 7 days runs Basic
  Metrics num_items(delta%) num_nodes 848977(-0.34%) num_edges
  353639179(-3.17%) size_gb 25.97(-3.29%) avg_vlen 17.33(+0.2%) Item Age
  Distribution num_items(delta%) 91-120 50333(-4.59%) 8-14 60618(-19.0%)
  61-90 195029(+2.56%) 31-60 282132(+0.01%) 2-7 51345(+10.74%) 15-30
  205316(+1.44%) 120+ 0(0.0%) 1 3151(-22.57%) 0 1052(-14.71%) Language
  Distribution num_items(delta%) te 27353(-3.14%) ta 32589(-2.17%) pa
  10461(+1.95%) or 593(-9.96%) na 13729(+3.59%) mr 13210(+1.79%) ml
  2940(-2.93%) kn 16837(-2.14%) hi 447897(-0.76%) gu 2501(-8.47%) en
  234287(+0.67%) bn 26646(+0.79%) bh 19740(+0.51%) all 112(-23.27%)
  Click to view Dashboard

## **LTHM (Long term history modelling)**

#### **High level summary of the Algos :**

1.  **v2v_mt_cluster** : Generates Clusters for active clients on 30
    days positive events (pcc98, likes, shares) using DBSCAN algorithm

2.  **v2v_mt_cluster_ts** : Generates Clusters for active clients on 30
    days positive events (pcc98, likes, shares) using timespent based
    algorithm

3.  **lthm_plus_minus** : Generates positive and negative sub_clusters
    for active clients on 14 days raw events using timespent based
    algorithm for storing affinity and anti-affinity of client

**Metrics logged :**

1.  **Coverage :** % of active clients for whom lthm clusters were
    formed \[will be used for all the above 3 algos\]

2.  **Num_clusters :** Distribution of clusters formed for each of the
    client \[will be used for v2v_mt_cluster and v2v_mt_cluster_ts\]

3.  **Num_positive_subclusters and Num_negative_subclusters :**
    Distribution of positive and negative subclusters formed for each of
    the client \[will be used for lthm_plus_minus\]

For LTHM (timespent) clusters

py{ \"mean\": 11.38, \"std\": 1.79, \"percentile_values\": { \"0.1\":
10, \"0.2\": 12, \"0.3\": 12, \"0.4\": 12, \"0.5\": 12, \"0.6\": 12,
\"0.7\": 12, \"0.8\": 12, \"0.9\": 12 },
\"active_clients_count_as_on_2023-08-14\": 5310856,
\"num_clients_with_lthm_calculated\": 3656724, \"clients_coverage\":
0.69 }

For LTHM (plus_minus) clusters

py{ \"positive_sub_clusters\": { \"mean\": 3.73, \"std\": 1.6,
\"percentile_values\": { \"0.1\": 1, \"0.2\": 2, \"0.3\": 3, \"0.4\": 4,
\"0.5\": 5, \"0.6\": 5, \"0.7\": 5, \"0.8\": 5, \"0.9\": 5 } },
\"negative_sub_clusters\": { \"mean\": 3.24, \"std\": 1.65,
\"percentile_values\": { \"0.1\": 1, \"0.2\": 1, \"0.3\": 2, \"0.4\": 3,
\"0.5\": 3, \"0.6\": 4, \"0.7\": 5, \"0.8\": 5, \"0.9\": 5 } },
\"active_clients_count_as_on_2023-08-14\": 5310856,
\"num_clients_with_lthm_calculated\": 3770832, \"clients_coverage\":
0.71 }

**Scripts:**

[https://console.cloud.google.com/storage/browser/aiml-lab-datalakes/lthm/scripts?project=josh-prod-392409](https://console.cloud.google.com/storage/browser/aiml-lab-datalakes/lthm/scripts?project=josh-prod-392409&pageState=(%22StorageObjectListTable%22:(%22f%22:%22%255B%255D%22))&prefix=&forceOnObjectsSortingFiltering=false)

- [pyspark_cluster_ts.py](https://console.cloud.google.com/storage/browser/_details/aiml-lab-datalakes/lthm/scripts/pyspark_cluster_ts.py;tab=live_object) -
  pyspark script to generate 14/30 days lthm ts clusters.

- [pyspark_cluster_plus_minus.py](https://console.cloud.google.com/storage/browser/_details/aiml-lab-datalakes/lthm/scripts/pyspark_cluster_plus_minus.py?project=josh-prod-392409) -
  pyspark script to generate +/- clusters

- [generate_ser_from_parquet.py](https://console.cloud.google.com/storage/browser/_details/aiml-lab-datalakes/lthm/scripts/generate_ser_from_parquet.py;tab=live_object) -
  script to convert parquet data to proto file that is sent as input to
  updating redis.

- [redis_cache_update.py](https://console.cloud.google.com/storage/browser/_details/aiml-lab-datalakes/lthm/scripts/redis_cache_update.py;tab=live_object) -
  script to update lthm clusters on redis

- [utils](https://console.cloud.google.com/storage/browser/aiml-lab-datalakes/lthm/scripts/utils?pageState=(%22StorageObjectListTable%22:(%22f%22:%22%255B%255D%22))&prefix=&forceOnObjectsSortingFiltering=false) -
  location of helper files used in the above scripts

**Schedule:**

The jobs are scheduled via airflow which runs daily on the following
dag:\
[prod_ranker_metadata_dag_v4](https://9291f5f1902943c2af4748fe9fc5cde1-dot-asia-south1.composer.googleusercontent.com/dags/prod_ranker_metadata_dag_v4/grid)

## **V2V Index**

The index creation is part of preranker job dag.

**Scripts**

The index creation implementation is at

\[AWS\]
[main_blip_module_gen.py](https://gitlab.dailyhunt.in/josh-recsys/mtl-training-pipeline/-/blob/main/main_blip_module_gen.py)

\[GCP\][gcp_main_blip_module_gen.py](https://gitlab.dailyhunt.in/josh-ai-labs/ranker-jobs-gcp/-/blob/main/gcp_main_blip_module_gen.py)

query filters:

- Item_age: 60 days

- event_range: last 30 days

- minimum_engagement: 5

- blip_embedding dimension: 32

**Various distribution of data is measured**

[Alert Space](https://mail.google.com/mail/u/0/#chat/space/AAAAG6zu4S0)
, [Error
Space](https://mail.google.com/mail/u/0/#chat/space/AAAAefUb_uA)

py{ \"item_count\": 1311480.0, \"language_counts\": { \"\": 1194,
\"All\": 622, \"NA\": 23113, \"bh\": 34092, \"bn\": 49784, \"en\":
330223, \"gu\": 6815, \"hi\": 708750, \"kn\": 22778, \"ml\": 9392,
\"mr\": 23650, \"na\": 4, \"or\": 3560, \"pa\": 17732, \"ta\": 44657,
\"te\": 35114 }, \"avg_watch_durations\": 17.56,
\"item_count_7d_delta%\": 0.74, \"language_counts_7d_delta%\": { \"\":
-4.41, \"All\": -36.96, \"NA\": 8.15, \"bh\": 0.47, \"bn\": 8.18,
\"en\": 3.25, \"gu\": 0.87, \"hi\": -1.2, \"kn\": 2.59, \"ml\": -0.59,
\"mr\": 7.86, \"na\": 76.55, \"or\": 0.68, \"pa\": 5.26, \"ta\": -0.06,
\"te\": -1.84 }, \"avg_watch_durations_7d_delta%\": 0.22 }

**Schedule:**

The jobs are scheduled via airflow which runs daily on the following
dag:\
[prod_ranker_metadata_dag_v4](https://9291f5f1902943c2af4748fe9fc5cde1-dot-asia-south1.composer.googleusercontent.com/dags/prod_ranker_metadata_dag_v4/grid)

### POPULAR Sources -

Qualitative Analysis Dashboard (<http://10.180.191.221:8085/>) contains
metric logging for 5 buckets -

1.  Items that have been identified popular today. (Today's data)

2.  Items that were identified popular yesterday. (Yesterday's data)

3.  Items that were popular yesterday but were not a part of today's
    popular set. (Exited Items)

4.  Items that are common in yesterday's set and today's set. (Persisted
    Items)

5.  Items that were not a part of yesterday's popular set but are
    identified as popular today. (New Items)

For all these buckets, the following metrics are logged -

1.  Language Distribution

2.  Views

3.  Like Rate

4.  Share Rate

5.  Loop Rate

6.  PCC98 Rate

7.  Skip Rate

**Drift** has also been calculated for items for all metrics (like rate,
share rate, loop rate, pcc98 rate, skip rate) -

1.  New Items (% drift from exited items)

2.  Persisted Items Drift

**SCRIPTS** -

A cronjob has been setup in GCP instance (10.180.191.221) that is
scheduled to run a bash script

(/home/ubuntu/user-files/shreyas.rao/popular/dailyrunner.sh) everyday at
3.30 AM. The time has been chosen as the source get updated daily at
3.00 and take around 10-15 minutes to update the sources.
