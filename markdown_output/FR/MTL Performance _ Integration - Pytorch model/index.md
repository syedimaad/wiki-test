**Model S3 Path:**
`s3://josh-reco-ml-dataset/models/mtl/torch/prod/1669847083/model_scripted.pt`

**Ref link**Torch MTL Model

**EC2 Instance Type:** g4dn.4xlarge

# **Benchmark Results** {#benchmark-results style="text-align: center;"}

## Ranker: Running against GPU {#ranker-running-against-gpu style="text-align: center;"}

### **[Jmeter Stats]{.underline}** {#jmeter-stats style="text-align: center;"}

  -------------- ---------------- ------------- --------- --------- --------------- ------------- ---------------- --------------------- ----------------- ----------------
  **Label**      **\# Samples**   **Average**   **Min**   **Max**   **Std. Dev.**   **Error %**   **Throughput**   **Received KB/sec**   **Sent KB/sec**   **Avg. Bytes**
  HTTP Request   11823            185           109       731       28.25           0.000%        53.85229         1052.29               265.29            20009.4
  TOTAL          11823            185           109       731       28.25           0.000%        53.85229         1052.29               265.29            20009.4
  -------------- ---------------- ------------- --------- --------- --------------- ------------- ---------------- --------------------- ----------------- ----------------

### **Time Budget Report** {#time-budget-report style="text-align: center;"}

  ----------------------------------- --------- ----- ---------
  get_pre_process_output:             87.90ms   for   4082
  pre_reco:                           51.12ms   for   4082
  transform:                          36.40ms   for   4082
  construct_col_tensor:               0.12ms    for   1134796
  get_candidates:                     15.67ms   for   4082
  get_user_profile_wrapper:           13.25ms   for   4082
  get_recommendations_tensor:         10.51ms   for   4082
  get_entities:                       1.75ms    for   20410
  blend:                              8.12ms    for   4082
  get_user_profile:                   6.48ms    for   4082
  get_external_candidates:            5.95ms    for   4082
  select_candidates:                  5.55ms    for   4082
  limit_candidates:                   3.13ms    for   4082
  construct_feature_vector:           2.92ms    for   4082
  populate_creator_fv_cache:          1.29ms    for   4082
  construct_user_vector:              1.24ms    for   4082
  populate_item_fv_cache:             1.01ms    for   4082
  get_user_online_history:            0.80ms    for   4082
  get_user_creator_history:           0.72ms    for   4082
  get_score_dict:                     0.68ms    for   4082
  get_elapsed_days:                   0.00ms    for   1405437
  get_entities_key:                   0.26ms    for   8164
  handle_raw_user_profile_success:    0.46ms    for   4068
  multi_get:                          0.32ms    for   4135
  get_creator_entities_key:           0.21ms    for   4082
  handle_user_feed_profile_success:   0.14ms    for   4074
  get_item_meta:                      0.06ms    for   4082
  get_trimmed_profile:                0.03ms    for   4082
  get_affinity_genres:                0.02ms    for   4022
  get_affinity_genres_map:            0.02ms    for   4082
  get_hashcode:                       0.01ms    for   4082
  top_zone:                           0.00ms    for   8164
  top_location:                       0.00ms    for   4082
  top_price_range:                    0.00ms    for   4082
  get_model_output:                   0.00ms    for   4082
  ----------------------------------- --------- ----- ---------

### **Inference Stage wise Metrics** {#inference-stage-wise-metrics style="text-align: center;"}

  --- ----------------------------------------- ----------- --------------------------- ------------------- -------------------
      **Stage**                                 **count**   **Total Time Taken (us)**   **Avg TIme (us)**   **Avg Time (ms)**
  1   {model=\"pytorch\",version=\"1\"}         51166       175484363                   3429.706504         3.429706504
  2   {model=\"ensemble_feed\",version=\"1\"}   51166       2509307                     49.04246961         0.04904246961
  --- ----------------------------------------- ----------- --------------------------- ------------------- -------------------
