**Model S3 Path:**
s3://josh-reco-ml-dataset/models/mtl/tf/prod/1667082425/model/

**EC2 Instance Type:** g4dn.4xlarge

# **Benchmark Results** {#benchmark-results style="text-align: center;"}

## Ranker: Running against GPU {#ranker-running-against-gpu style="text-align: center;"}

### **[Jmeter Stats]{.underline}** {#jmeter-stats style="text-align: center;"}

  -------------- ---------------- ------------- ------------ -------------- -------------- -------------- --------- --------- ------------- ---------------- --------------------- -----------------
  **Label**      **\# Samples**   **Average**   **Median**   **90% Line**   **95% Line**   **99% Line**   **Min**   **Max**   **Error %**   **Throughput**   **Received KB/sec**   **Sent KB/sec**
  HTTP Request   26288            92            93           97             99             112            44        141       0.000%        53.73045         28.92                 113.89
                                                                                                                                                                                   
  -------------- ---------------- ------------- ------------ -------------- -------------- -------------- --------- --------- ------------- ---------------- --------------------- -----------------

### **Time Budget Report** {#time-budget-report style="text-align: center;"}

  ----------------------------------- --------- ----- ------- -------
  pre_reco:                           17.94ms   for   7022    calls
  get_candidates:                     7.03ms    for   7022    calls
  get_entities:                       0.87ms    for   42132   calls
  get_external_candidates:            4.85ms    for   7022    calls
  get_user_profile_wrapper:           3.55ms    for   7022    calls
  limit_candidates:                   1.23ms    for   7022    calls
  get_user_online_history:            0.82ms    for   7022    calls
  get_user_profile:                   8.78ms    for   594     calls
  transform:                          0.65ms    for   7022    calls
  select_candidates:                  0.41ms    for   7022    calls
  get_entities_key:                   0.08ms    for   14044   calls
  get_item_meta:                      0.09ms    for   7022    calls
  construct_user_vector:              1.06ms    for   594     calls
  multi_get:                          0.02ms    for   22269   calls
  handle_raw_user_profile_success:    0.37ms    for   592     calls
  get_hashcode:                       0.01ms    for   14044   calls
  handle_user_feed_profile_success:   0.14ms    for   592     calls
  top_zone:                           0.00ms    for   7022    calls
  top_price_range:                    0.00ms    for   7022    calls
  get_creator_entities_key:           0.00ms    for   7022    calls
  top_location:                       0.00ms    for   7022    calls
  get_affinity_genres:                0.02ms    for   581     call
  ----------------------------------- --------- ----- ------- -------

### **Inference Stage wise Metrics** {#inference-stage-wise-metrics style="text-align: center;"}

  --- ----------------------------------------------------------------------------- ----------- ---------------------
      **Stage**                                                                     **count**   **Time Taken (ms)**
  1   nv_inference_request_success{model=\"**mtl_ensemble_feed**\",version=\"1\"}   27417       104.43743
  2   nv_inference_request_success{model=\"**mtl**\",version=\"1\"}                 27417       36.63329215
  3   nv_inference_request_success{model=\"**mtl_pre_process**\",version=\"1\"}     27417       56.83507134
  4   nv_inference_request_success{model=\"**mtl_post_process**\",version=\"1\"}    27417       11.24947941
  --- ----------------------------------------------------------------------------- ----------- ---------------------

## Ranker: Running against CPU {#ranker-running-against-cpu style="text-align: center;"}

while Testing on the CPU we are getting the following error

[{\"error\":\"in ensemble \'mtl_ensemble_feed\', indices\[6,0\] =
-2147483648 is not in \[0, 3)\\n\\t \[\[{{node
model/bool_embedding_dislike/embedding_9/embedding_lookup}}\]\]\"}]{style="color: rgb(255,86,48);"}
