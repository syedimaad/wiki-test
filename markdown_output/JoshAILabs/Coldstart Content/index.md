**repo :**
<https://gitlab.dailyhunt.in/josh-ai-labs/cold_start_hnsw/-/tree/dev_gcs?ref_type=heads>

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

- Start VM ([10.180.191](http://10.180.191.221:8080/home).210)

- Run script on VM

- Stop VM

- Generate monitoring reports.

**Chat :**

<https://mail.google.com/chat/u/0/#chat/space/AAAA-XCe4UA>

<https://mail.google.com/chat/u/0/#chat/space/AAAAg5dh3zs>
