#### **Repos/Links:** [**Github**](https://gitlab.dailyhunt.in/josh-ai-labs/josh-dnn-two-tower-recsys/-/blob/gcp_changes/dataproc_scripts/mtl_datagen_dag.py) **\|** [**Airflow**](https://9291f5f1902943c2af4748fe9fc5cde1-dot-asia-south1.composer.googleusercontent.com/dags/mtl-datagen/grid)

**Monitoring Stats:**

py{ \"datagen_start_time\": \"2023-09-14::10:08:51\",
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
(0.0%)\", \"(0.0, 1.0\]\": \"7,539 (1.03%)\", \"(1.0, 2.0\]\": \"8,817
(1.21%)\", \"(2.0, 4.0\]\": \"34,625 (4.75%)\", \"(4.0, 7.0\]\":
\"85,162 (11.69%)\", \"(7.0, 14.0\]\": \"72,460 (9.94%)\", \"(14.0,
30.0\]\": \"173,006 (23.74%)\", \"(30.0, 60.0\]\": \"228,166 (31.31%)\",
\"(60.0, 90.0\]\": \"118,931 (16.32%)\", \"(90.0, inf\]\": \"0 (0.0%)\"
}, \"item_age_buckets_delta_7d\": { \"(-inf, 0.0\]\": \"0 (+0.0%)\",
\"(0.0, 1.0\]\": \"477 (+6.75%)\", \"(1.0, 2.0\]\": \"2,819 (+47.0%)\",
\"(2.0, 4.0\]\": \"5,199 (+17.67%)\", \"(4.0, 7.0\]\": \"-5,856
(-6.43%)\", \"(7.0, 14.0\]\": \"-24,594 (-25.34%)\", \"(14.0, 30.0\]\":
\"11,537 (+7.15%)\", \"(30.0, 60.0\]\": \"30,830 (+15.62%)\", \"(60.0,
90.0\]\": \"-3,899 (-3.17%)\", \"(90.0, inf\]\": \"0 (+0.0%)\" },
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
