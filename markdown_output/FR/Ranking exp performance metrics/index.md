**Model S3 Path:**
s3://josh-reco-ml-dataset/models/inference/prod/feed-deploy-artifacts/model_repo/model_v15/

**EC2 Instance Type:** g4dn.4xlarge

### **Time Budget Report:**

  --------------------------------------- --------- ----- ----- ------- -------
  timebudget report\...                                                 
  pre_reco                                90.57ms   for         91      calls
  get_candidates                          18.77ms   for         91      calls
  get_entities                            2.16ms    for   546   calls   
  construct_differential_feature_vector   2.11ms    for   546   calls   
  populate_creator_fv_cache               1.63ms    for   637   calls   
  populate_item_fv_cache                  1.57ms    for   637   calls   
  select_candidates                       8.66ms    for         91      calls
  get_user_profile_wrapper                8.02ms    for         91      calls
  get_external_candidates                 5.91ms    for         91      calls
  construct_feature_vector                5.04ms    for         91      calls
  get_user_profile                        90.43ms   for   3     calls   
  limit_candidates                        2.80ms    for         91      calls
  get_user_online_history                 2.20ms    for         91      calls
  multi_get                               0.69ms    for   275   calls   
  get_user_creator_history                1.02ms    for         91      calls
  handle_user_feed_profile_success        26.52ms   for   3     calls   
  get_entities_key                        0.20ms    for   182   calls   
  get_creator_entities_key                0.14ms    for         91      calls
  get_item_meta                           0.08ms    for         91      calls
  get_trimmed_profile                     0.02ms    for         91      calls
  get_hashcode                            0.01ms    for         91      calls
  top_zone                                0.00ms    for         91      calls
  top_location                            0.00ms    for         91      calls
                                                                        
  --------------------------------------- --------- ----- ----- ------- -------

Vs Prod

  --------------------------------------- --------- ----- ------- ------- -------
  timebudget report\...                                                   
  pre_reco                                83.10ms   for           1489    calls
  get_candidates                          27.54ms   for           1459    calls
  get_entities                            3.82ms    for           6860    calls
  select_candidates                       16.09ms   for           1459    calls
  multi_get                               2.85ms    for           6050    calls
  populate_creator_fv_cache               1.55ms    for   10213   calls   
  construct_differential_feature_vector   1.72ms    for           8754    calls
  populate_item_fv_cache                  1.43ms    for   10213   calls   
  get_user_profile_wrapper                6.58ms    for           1459    calls
  get_external_candidates                 5.88ms    for           1024    calls
  construct_feature_vector                4.11ms    for           1459    calls
  transform                               3.62ms    for           1489    calls
  limit_candidates                        3.31ms    for           1459    calls
  get_user_profile                        6.93ms    for   479     calls   
  get_user_online_history                 1.07ms    for           1459    calls
  get_user_creator_history                0.70ms    for           1459    calls
  get_item_meta                           0.57ms    for           1459    calls
  get_entities_key                        0.17ms    for           2918    calls
  construct_user_vector                   0.72ms    for   479     calls   
  get_creator_entities_key                0.14ms    for           1459    calls
  handle_raw_user_profile_success         0.26ms    for   474     calls   
  handle_user_feed_profile_success        0.10ms    for   476     calls   
  get_trimmed_profile                     0.02ms    for           1459    calls
  --------------------------------------- --------- ----- ------- ------- -------

### **Inference Stage wise Metrics**

  ------------------------------------------------------------------------------------ ------------ ------------------- ------------------
  stage                                                                                time taken   time taken in sec   time taken in ms
  nv_inference_request_duration_us{model=\"lightgbm_le_2sec\",version=\"20221109\"}    191393065    8988.121771         8.988121771
  nv_inference_request_duration_us{model=\"lightgbm_liked\",version=\"20221109\"}      173451501    8145.557481         8.145557481
  nv_inference_request_duration_us{model=\"lightgbm_gt_10sec\",version=\"20221109\"}   126357510    5933.949            5.933949
  nv_inference_request_duration_us{model=\"lightgbm_gt_7sec\",version=\"20221109\"}    161344453    7576.991312         7.576991312
  nv_inference_request_duration_us{model=\"lightgbm_le_5sec\",version=\"20221109\"}    192045828    9018.776557         9.018776557
  nv_inference_request_duration_us{model=\"lightgbm_pcc85\",version=\"20221109\"}      99768482     4685.28609          4.68528609
  nv_inference_request_duration_us{model=\"lightgbm_shared\",version=\"20221109\"}     190753129    8958.069362         8.958069362
  nv_inference_request_duration_us{model=\"pre_process\",version=\"1\"}                2095332925   98400.15615         98.40015615
  nv_inference_request_duration_us{model=\"common_process\",version=\"1\"}             0            0                   0
                                                                                                                        
  ------------------------------------------------------------------------------------ ------------ ------------------- ------------------

prod

  ------------------------------------------------------------------------------------ ----------- ------------- ------------------
  stage                                                                                                          time taken in ms
  nv_inference_request_duration_us{model=\"lightgbm_le_2sec\",version=\"20221109\"}    20925321    9408.867356   9.408867356
  nv_inference_request_duration_us{model=\"lightgbm_liked\",version=\"20221109\"}      20977362    9432.267086   9.432267086
  nv_inference_request_duration_us{model=\"lightgbm_gt_7sec\",version=\"20221109\"}    20990103    9437.995953   9.437995953
  nv_inference_request_duration_us{model=\"ensemble_feed\",version=\"1\"}              363586382   163483.0854   163.4830854
  nv_inference_request_duration_us{model=\"lightgbm_gt_10sec\",version=\"20221109\"}   20970673    9429.259442   9.429259442
  nv_inference_request_duration_us{model=\"lightgbm_le_5sec\",version=\"20221109\"}    21063037    9470.790018   9.470790018
  nv_inference_request_duration_us{model=\"lightgbm_pcc85\",version=\"20221109\"}      20748079    9329.172212   9.329172212
  nv_inference_request_duration_us{model=\"post_process\",version=\"1\"}               34212087    15383.13264   15.38313264
  nv_inference_request_duration_us{model=\"lightgbm_shared\",version=\"20221109\"}     21222109    9542.315198   9.542315198
  nv_inference_request_duration_us{model=\"pre_process\",version=\"1\"}                307199973   138129.4843   138.1294843
  nv_inference_request_duration_us{model=\"common_process\",version=\"1\"}             0                         
  ------------------------------------------------------------------------------------ ----------- ------------- ------------------

# **Benchmark Results**

## Ranker : Running against GPU

### **[Jmeter Stats:]{.underline}**

  -------------- ------------ --------- -------- ---------- ---------- ---------- ----- ----- --------- ------------ ----------------- -------------
  Label          \# Samples   Average   Median   90% Line   95% Line   99% Line   Min   Max   Error %   Throughput   Received KB/sec   Sent KB/sec
  HTTP Request   20027        90        87       109        117        135        56    667   0.00%     55.41751     521.97            167.63
  TOTAL          20027        90        87       109        117        135        56    667   0.00%     55.41751     521.97            167.63
  -------------- ------------ --------- -------- ---------- ---------- ---------- ----- ----- --------- ------------ ----------------- -------------

summary = 171252 in 00:23:24 =  122.0/s Avg:    81 Min:    42 Max:  2028
Err:    36 (0.02%) summary +   3773 in 00:00:30 =  125.8/s Avg:    79
Min:    45 Max:   216 Err:     0 (0.00%) Active: 10 Started: 10
Finished: 0 summary = 175025 in 00:23:54 =  122.1/s Avg:    81 Min:   
42 Max:  2028 Err:    36 (0.02%) summary +   3778 in 00:00:30 =  125.8/s
Avg:    79 Min:    49 Max:   223 Err:     0 (0.00%) Active: 10 Started:
10 Finished: 0 summary = 178803 in 00:24:24 =  122.2/s Avg:    81 Min: 
  42 Max:  2028 Err:    36 (0.02%) summary +   3731 in 00:00:30 = 
124.4/s Avg:    80 Min:    54 Max:   245 Err:     0 (0.00%) Active: 10
Started: 10 Finished: 0 summary = 182534 in 00:24:54 =  122.2/s Avg:   
81 Min:    42 Max:  2028 Err:    36 (0.02%)

prod

summary +   2029 in 00:00:30 =   67.6/s Avg:   147 Min:    68 Max:  2003
Err:     1 (0.05%) Active: 10 Started: 10 Finished: 0

summary =   5796 in 00:01:26 =   67.6/s Avg:   146 Min:    68 Max:  2003
Err:     1 (0.02%)

summary +   2035 in 00:00:30 =   67.8/s Avg:   147 Min:    70 Max:   271
Err:     0 (0.00%) Active: 10 Started: 10 Finished: 0

summary =   7831 in 00:01:56 =   67.6/s Avg:   146 Min:    68 Max:  2003
Err:     1 (0.01%)

summary +   1985 in 00:00:30 =   66.2/s Avg:   151 Min:    68 Max:  2003
Err:     3 (0.15%) Active: 10 Started: 10 Finished: 0

summary =   9816 in 00:02:26 =   67.3/s Avg:   147 Min:    68 Max:  2003
Err:     4 (0.04%)

summary +   2046 in 00:00:30 =   68.2/s Avg:   146 Min:    72 Max:   260
Err:     0 (0.00%) Active: 10 Started: 10 Finished: 0

summary =  11862 in 00:02:56 =   67.5/s Avg:   147 Min:    68 Max:  2003
Err:     4 (0.03%)

  -------------- ------------ --------- -------- ---------- ---------- ---------- ----- ------ --------- ------------ ----------------- -------------
  Label          \# Samples   Average   Median   90% Line   95% Line   99% Line   Min   Max    Error %   Throughput   Received KB/sec   Sent KB/sec
  HTTP Request   12446        146       144      187        200        226        61    2003   0.03%     52.46938     500.19            158.82
  TOTAL          12446        146       144      187        200        226        61    2003   0.03%     52.46938     500.19            158.82
  -------------- ------------ --------- -------- ---------- ---------- ---------- ----- ------ --------- ------------ ----------------- -------------
