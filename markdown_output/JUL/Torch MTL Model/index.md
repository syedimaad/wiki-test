## Location of model

`s3://josh-reco-ml-dataset/us-ml-team/models/mtl/torch/prod/1670070913/model_scripted.pt`

## Tasks (output columns)

- p_lte2 =\> bounce / skip / watch_duration_in_seconds \<= 2

- p_lte5 =\> watch_duration_in_seconds \<= 5

<!-- -->

- p_pcc85 =\> watch_fraction \>= 85%

- p_pcc90 =\> watch_fraction \>= 90%

- p_pcc98 =\> watch_fraction \>= 98%

- p_pcc100 =\> watch_fraction \>= 100%

- p_gte7 =\> watch_duration_in_seconds \>= 7

- p_gte10 =\> watch_duration_in_seconds \>= 10

<!-- -->

- e_watch_duration =\> predict **mean** of
  min(watch_duration_in_seconds, 60)

- median_watch_duration =\> predict **p50** of
  min(watch_duration_in_seconds, 60)

- std_dev_watch_duration =\> predict **std-dev** of
  min(watch_duration_in_seconds, 60)

## Training

- 14 days

<!-- -->

- 5B rows

<!-- -->

- 2 epochs

- 24 hours to train

## Performance

  ------------------------------- --------
  metric                          value
  val_p_lte2_AUC                  0.7727
  val_p_lte2_AP                   0.5943
  val_p_lte5_AUC                  0.7752
  val_p_lte5_AP                   0.7308
  val_p_pcc85_AUC                 0.8042
  val_p_pcc85_AP                  0.6875
  val_p_pcc90_AUC                 0.8061
  val_p_pcc90_AP                  0.6675
  val_p_pcc98_AUC                 0.8217
  val_p_pcc98_AP                  0.6377
  val_p_pcc100_AUC                0.8255
  val_p_pcc100_AP                 0.6298
  val_p_gte7_AUC                  0.7766
  val_p_gte7_AP                   0.7837
  val_p_gte10_AUC                 0.7800
  val_p_gte10_AP                  0.7481
  val_e_watch_duration_MAE        9.3323
  val_e_watch_duration_log1p_R2   0.3021
  ------------------------------- --------

## Verification

Please use

`s3://josh-reco-ml-dataset/us-ml-team/models/mtl/torch/prod/1670070913/io_dict.pt`

for verifying preprocessing and model:

- For preprocessing logic verification please use `io_dict['batch']` and
  look at the following columns: `client_id_str` (raw) and compare it
  with `client_id` (preprocessed). Similarly for `item_id_str` and
  `item_id`.

- For model I/O do `outputs = model(io_dict['batch'])`

  - Compare `outputs[0]` with `io_dict['output']['p_lte2']`

  - Compare `outputs[1]` with `io_dict['output']['p_lte5']`

  - Compare `outputs[2]` with `io_dict['output']['p_pcc85']`

  - Compare `outputs[3]` with `io_dict['output']['p_pcc90']`

  - Compare `outputs[4]` with `io_dict['output']['p_pcc98']`

  - Compare `outputs[5]` with `io_dict['output']['p_pcc100']`

  - Compare `outputs[6]` with `io_dict['output']['p_gte7']`

  - Compare `outputs[7]` with `io_dict['output']['p_gte10']`

  - Compare `outputs[8]` with `io_dict['output']['e_watch_duration']`

  - Compare `outputs[9]` with
    `io_dict['output']['q_watch_duration_p50']`

  - Compare `outputs[10]` with `torch.stack(`\
    `[io_dict['output']['q_watch_duration_p10'].squeeze(1), `\
    `io_dict['output']['q_watch_duration_p30'].squeeze(1), `\
    `io_dict['output']['q_watch_duration_p50'].squeeze(1), `\
    `io_dict['output']['q_watch_duration_p70'].squeeze(1), `\
    `io_dict['output']['q_watch_duration_p90'].squeeze(1),], dim=1).std(dim=1, unbiased=False, keepdim=True)`

## Serving Contract

model = torch.jit.load(path_to_pt_file) model.eval() model.forward(self,
inp: Dict\[str, torch.Tensor\]) -\> Tuple\[torch.Tensor, torch.Tensor,
torch.Tensor, torch.Tensor, torch.Tensor, torch.Tensor, torch.Tensor,
torch.Tensor, torch.Tensor, torch.Tensor, torch.Tensor\]

*Output order:*

- p_lte2, p_lte5, p_pcc85, p_pcc90, p_pcc98, p_pcc100, p_gte7, p_gte10,
  mean_watch_duration, median_watch_duration, std_dev_watch_duration

## String features (torch.long)

*Convert feature names to lower case. Null imputed by NA and then
preprocess like so:*

seed = xxhash.xxh32(to_lower_case(column_name), 0).intdigest()
batch\[column_name\] = \\ np.array( \[ \# xxh64 ranges from 0 to
2\*\*64-1 \# torch.int64 ranges from -2\*\*63 to 2\*\*63-1
xxhash.xxh64(str(value), seed).intdigest() - 2\*\*63 for value in
batch\[column_name\].values \], dtype=np.int64, )

Features are:

\[ \'client_id\', \'creator_id\', \'user_app_ver\', \'item_id\',
\'item_lang\', \'user_lang\', \'handset_maker\', \'handset_model\',
\'network_quality\', \'user_connection\', \'user_feed_source\',
\'clustered_audio_id\', \'req_city_id\', \'req_state_id\', \'clv\',
\'creator_level\', \'creator_user_type\', \'user_os_platform\',
\'user_os_ver\', \'zone_ids\', \'history_size\', \]

## Timestamp features (torch.long)

*Convert feature names to lower case. Null imputed by -1*

\[ \'play_timestamp\', \'item_publish_date_in_epoch\',
\'last_time_stamp\', \'last_play_timestamp\', \]

## Boolean features (torch.long)

*Convert feature names to lower case. Null imputed by -1*

\[ \'dislike\', \'has_follow\', \]

## Location features (torch.float)

*Convert feature names to lower case. Null imputed by -1*

\[ \'latitude\', \'longitude\', \]

## Numerical features (torch.float)

*Convert feature names to lower case. Null imputed by -1*

\[ \'video_length\', \'item_like_uu\', \'item_share_uu\',
\'item_download_uu\', \'item_view_uu\', \'item_comment_uu\',
\'item_engagement_uu\', \'item_timespent_0To3\',
\'item_timespent_3To6\', \'item_timespent_6To9\',
\'item_timespent_9To12\', \'item_timespent_12To15\',
\'item_timespent_15To18\', \'item_timespent_18To21\',
\'item_timespent_21To24\', \'item_timespent_24To30\',
\'item_timespent_30To40\', \'item_timespent_40To60\',
\'item_timespent_Gt60\', \'item_view_24h\', \'item_engagement_24h\',
\'item_view_3d\', \'item_engagement_3d\', \'item_view_7d\',
\'item_engagement_7d\', \'item_view_15d\', \'item_engagement_15d\',
\'item_download_ctr\', \'item_share_ctr\', \'item_like_ctr\',
\'item_ctr\', \'item_ctr_24hr\', \'item_ctr_3d\', \'item_ctr_7d\',
\'item_ctr_15d\', \'item_like_24h\', \'item_share_24h\',
\'item_like_3d\', \'item_share_3d\', \'item_like_7d\',
\'item_share_7d\', \'item_like_15d\', \'item_share_15d\',
\'item_like_ctr_24hr\', \'item_like_ctr_3d\', \'item_like_ctr_7d\',
\'item_like_ctr_15d\', \'item_share_ctr_24hr\', \'item_share_ctr_3d\',
\'item_share_ctr_7d\', \'item_share_ctr_15d\', \'creator_cv\',
\'creator_pv\', \'creator_lp\', \'creator_lc\', \'creator_sc\',
\'creator_cc\', \'creator_dl\', \'creator_ctr_12d\',
\'creator_ctr_24h\', \'creator_ctr_3d\', \'creator_ctr_7d\',
\'creator_cv_12d\', \'creator_cv_24h\', \'creator_cv_3d\',
\'creator_cv_7d\', \'creator_dl_12d\', \'creator_dl_24h\',
\'creator_dl_3d\', \'creator_dl_7d\', \'creator_lc_12d\',
\'creator_lc_24h\', \'creator_lc_3d\', \'creator_lc_7d\',
\'creator_pv_12d\', \'creator_pv_24h\', \'creator_pv_3d\',
\'creator_pv_7d\', \'creator_sc_12d\', \'creator_sc_24h\',
\'creator_sc_3d\', \'creator_sc_7d\', \'creator_videoposted\',
\'creator_nsfwposted\', \'creator_pcc05\', \'creator_pcc520\',
\'creator_pcc2040\', \'creator_pcc4060\', \'creator_pcc6070\',
\'creator_pcc7080\', \'creator_pcc8090\', \'creator_pcc90100\',
\'creator_viewle20\', \'creator_viewle50\', \'creator_viewle100\',
\'creator_viewle500\', \'creator_viewle1000\', \'creator_viewle10000\',
\'creator_viewle50000\', \'creator_viewle100000\',
\'creator_viewle500000\', \'creator_viewle1000000\',
\'creator_viewle5000000\', \'creator_viewle100000000\',
\'creator_viewgt100000000\', \'creator_daysvideoposted\',
\'creator_timespent_le_5sec\', \'creator_timespent_gt_5sec\',
\'creator_timespent_gt_10sec\', \'creator_timespent_gt_20sec\',
\'creator_timespent_gt_30sec\', \'creator_timespent_gt_60sec\',
\'creator_timespent_gt_120sec\', \'creator_ctr\',
\'creator_download_ctr\', \'creator_share_ctr\', \'creator_like_ctr\',
\'user_overall_short_loop\', \'user_overall_short_like\',
\'user_overall_short_share\', \'user_overall_short_comment\',
\'user_overall_short_download\',
\'user_overall_short_timespent_le_5sec\',
\'user_overall_short_timespent_gt_5sec\',
\'user_overall_short_timespent_gt_10sec\',
\'user_overall_short_timespent_gt_20sec\',
\'user_overall_short_timespent_gt_30sec\',
\'user_overall_short_timespent_gt_60sec\',
\'user_overall_short_timespent_gt_120sec\',
\'user_overall_short_pcc_0_5\', \'user_overall_short_pcc_5_20\',
\'user_overall_short_pcc_20_40\', \'user_overall_short_pcc_40_60\',
\'user_overall_short_pcc_60_70\', \'user_overall_short_pcc_70_80\',
\'user_overall_short_pcc_80_90\', \'user_overall_short_pcc_90_100\',
\'user_overall_short_dislike\', \'user_overall_short_lp_ctr\',
\'user_overall_short_total_engaged\',
\'user_overall_short_total_plays\', \'user_overall_short_ctr\',
\'user_overall_short_like_ctr\', \'user_overall_short_download_ctr\',
\'user_overall_mid_loop\', \'user_overall_mid_like\',
\'user_overall_mid_share\', \'user_overall_mid_comment\',
\'user_overall_mid_download\', \'user_overall_mid_timespent_le_5sec\',
\'user_overall_mid_timespent_gt_5sec\',
\'user_overall_mid_timespent_gt_10sec\',
\'user_overall_mid_timespent_gt_20sec\',
\'user_overall_mid_timespent_gt_30sec\',
\'user_overall_mid_timespent_gt_60sec\',
\'user_overall_mid_timespent_gt_120sec\', \'user_overall_mid_pcc_0_5\',
\'user_overall_mid_pcc_5_20\', \'user_overall_mid_pcc_20_40\',
\'user_overall_mid_pcc_40_60\', \'user_overall_mid_pcc_60_70\',
\'user_overall_mid_pcc_70_80\', \'user_overall_mid_pcc_80_90\',
\'user_overall_mid_pcc_90_100\', \'user_overall_mid_dislike\',
\'user_overall_mid_lp_ctr\', \'user_overall_mid_total_engaged\',
\'user_overall_mid_total_plays\', \'user_overall_mid_ctr\',
\'user_overall_mid_like_ctr\', \'user_overall_mid_download_ctr\',
\'user_overall_life_like\', \'user_overall_life_share\',
\'user_overall_life_comment\', \'user_overall_life_download\',
\'user_overall_life_timespent_le_5sec\',
\'user_overall_life_timespent_gt_5sec\',
\'user_overall_life_timespent_gt_10sec\',
\'user_overall_life_timespent_gt_20sec\',
\'user_overall_life_timespent_gt_30sec\',
\'user_overall_life_timespent_gt_60sec\',
\'user_overall_life_timespent_gt_120sec\',
\'user_overall_life_pcc_0_5\', \'user_overall_life_pcc_5_20\',
\'user_overall_life_pcc_20_40\', \'user_overall_life_pcc_40_60\',
\'user_overall_life_pcc_60_70\', \'user_overall_life_pcc_70_80\',
\'user_overall_life_pcc_80_90\', \'user_overall_life_pcc_90_100\',
\'user_overall_life_dislike\', \'user_overall_life_lp_ctr\',
\'user_overall_life_total_engaged\', \'user_overall_life_total_plays\',
\'user_overall_life_ctr\', \'user_overall_life_like_ctr\',
\'user_overall_life_download_ctr\', \'user_creator_life_like\',
\'user_creator_life_share\', \'user_creator_life_comment\',
\'user_creator_life_download\', \'user_creator_life_timespent_le_5sec\',
\'user_creator_life_timespent_gt_5sec\',
\'user_creator_life_timespent_gt_10sec\',
\'user_creator_life_timespent_gt_20sec\',
\'user_creator_life_timespent_gt_30sec\',
\'user_creator_life_timespent_gt_60sec\',
\'user_creator_life_timespent_gt_120sec\',
\'user_creator_life_pcc_0_5\', \'user_creator_life_pcc_5_20\',
\'user_creator_life_pcc_20_40\', \'user_creator_life_pcc_40_60\',
\'user_creator_life_pcc_60_70\', \'user_creator_life_pcc_70_80\',
\'user_creator_life_pcc_80_90\', \'user_creator_life_pcc_90_100\',
\'user_creator_life_dislike\', \'user_creator_life_lp_ctr\',
\'user_creator_life_total_engaged\', \'user_creator_life_total_plays\',
\'user_creator_life_ctr\', \'user_creator_life_like_ctr\',
\'user_creator_life_download_ctr\', \'user_tpv_life_like\',
\'user_tpv_life_share\', \'user_tpv_life_comment\',
\'user_tpv_life_download\', \'user_tpv_life_timespent_le_5sec\',
\'user_tpv_life_timespent_gt_5sec\',
\'user_tpv_life_timespent_gt_10sec\',
\'user_tpv_life_timespent_gt_20sec\',
\'user_tpv_life_timespent_gt_30sec\',
\'user_tpv_life_timespent_gt_60sec\',
\'user_tpv_life_timespent_gt_120sec\', \'user_tpv_life_pcc_0_5\',
\'user_tpv_life_pcc_5_20\', \'user_tpv_life_pcc_20_40\',
\'user_tpv_life_pcc_40_60\', \'user_tpv_life_pcc_60_70\',
\'user_tpv_life_pcc_70_80\', \'user_tpv_life_pcc_80_90\',
\'user_tpv_life_pcc_90_100\', \'user_tpv_life_dislike\',
\'user_tpv_life_lp_ctr\', \'user_tpv_life_total_engaged\',
\'user_tpv_life_total_plays\', \'user_tpv_life_ctr\',
\'user_tpv_life_like_ctr\', \'user_tpv_life_download_ctr\', \]

## Blending analysis

Please use the evaluation data from:\
s3://josh-reco-ml-dataset/us-ml-team/models/mtl/torch/prod/1670070913/eval_predictions.parquet\
and join it with signals from dt=20221202 partition

## Model sensitivity analysis

Random perturbations within 1 +/- 1e-6 of the feature value result in
large changes in model output (ignore the timestamp features in red). So
please be careful with dtype

  ------------------------------------------------------------------ ------------------------------------------------------
  **feature**                                                        **sensitivity_at_1e6**
  **[item_publish_date_in_epoch]{style="color: rgb(255,86,48);"}**   [24.31221124716100]{style="color: rgb(255,86,48);"}
  **[last_play_timestamp]{style="color: rgb(255,86,48);"}**          [20.255377981811800]{style="color: rgb(255,86,48);"}
  **[play_timestamp]{style="color: rgb(255,86,48);"}**               [11.299660219810900]{style="color: rgb(255,86,48);"}
  **user_overall_short_timespent_gt_60sec**                          7.664664043113590
  **user_tpv_life_comment**                                          7.491764891892670
  **user_overall_life_dislike**                                      7.255055848509070
  **user_creator_life_ctr**                                          5.766187212429940
  **user_overall_life_ctr**                                          5.66642505582422
  **user_overall_life_comment**                                      4.853602638468150
  **user_overall_short_ctr**                                         4.755246685817840
  **user_overall_short_timespent_gt_120sec**                         4.616964911110700
  **user_overall_short_pcc_0_5**                                     4.466579691506920
  **user_overall_short_lp_ctr**                                      3.1868408201262400
  **user_tpv_life_dislike**                                          3.0732726212590900
  **user_overall_short_timespent_gt_30sec**                          2.814315096475180
  **user_overall_short_pcc_80_90**                                   2.8036070754751600
  **user_overall_life_lp_ctr**                                       2.7207733830437100
  **user_creator_life_lp_ctr**                                       2.585592260584240
  **user_overall_short_pcc_5_20**                                    2.5397829711437200
  **user_overall_short_pcc_90_100**                                  2.5260157650336600
  **user_overall_short_like_ctr**                                    2.298593265004460
  **user_creator_life_pcc_0_5**                                      2.2224035812541800
  **user_overall_short_timespent_le_5sec**                           2.1973600145429400
  **user_overall_short_dislike**                                     2.1962503669783500
  **user_overall_short_timespent_gt_20sec**                          2.192362048663200
  **user_overall_short_pcc_40_60**                                   2.0387782249599700
  **user_overall_short_pcc_20_40**                                   1.9798589404672400
  **user_overall_short_pcc_70_80**                                   1.7700186930596800
  **user_overall_short_timespent_gt_10sec**                          1.7527439398691100
  **user_overall_short_pcc_60_70**                                   1.676430250518020
  **user_overall_life_like_ctr**                                     1.4376179315149800
  **user_overall_short_timespent_gt_5sec**                           1.4033443992957500
  **user_creator_life_timespent_gt_30sec**                           1.4009775593876800
  **user_tpv_life_timespent_gt_120sec**                              1.3912775088101600
  **user_creator_life_pcc_80_90**                                    1.309735607355830
  **user_creator_life_timespent_gt_120sec**                          1.2872113613411800
  **user_creator_life_timespent_le_5sec**                            1.2715351302176700
  **user_creator_life_download_ctr**                                 1.2403124244883700
  **user_overall_short_loop**                                        1.2052553705871100
  **user_overall_short_download_ctr**                                1.1924159014597500
  **user_overall_life_download_ctr**                                 1.1830332921817900
  **user_creator_life_pcc_20_40**                                    1.1391628067940500
  **video_length**                                                   1.041692541912200
  **user_creator_life_comment**                                      0.9571684524416920
  **user_overall_mid_timespent_gt_120sec**                           0.9439897956326600
  **user_creator_life_pcc_60_70**                                    0.9346137754619120
  **user_creator_life_timespent_gt_60sec**                           0.9286375250667330
  **user_creator_life_pcc_40_60**                                    0.9111026301980020
  **user_creator_life_timespent_gt_5sec**                            0.8746910374611620
  **user_tpv_life_timespent_gt_60sec**                               0.8510485757142310
  **user_overall_life_timespent_gt_30sec**                           0.8314715698361400
  **user_overall_mid_ctr**                                           0.8225164376199250
  **user_overall_life_timespent_gt_120sec**                          0.8221359923481940
  **user_tpv_life_pcc_0_5**                                          0.7830499205738310
  **user_overall_short_comment**                                     0.772230327129364
  **user_tpv_life_timespent_gt_30sec**                               0.7250215159729120
  **user_overall_mid_comment**                                       0.7069952553138140
  **user_creator_life_dislike**                                      0.7008740678429600
  **user_tpv_life_download**                                         0.6715161493048070
  **user_creator_life_pcc_5_20**                                     0.6708059227094050
  **user_overall_short_share**                                       0.6682859268039470
  **user_overall_mid_download_ctr**                                  0.6577915977686640
  **user_tpv_life_pcc_70_80**                                        0.6420124787837270
  **user_tpv_life_timespent_gt_5sec**                                0.6107048131525520
  **user_overall_mid_pcc_80_90**                                     0.5924329627305270
  **user_tpv_life_download_ctr**                                     0.5906711099669340
  **user_tpv_life_timespent_le_5sec**                                0.5830041831359270
  **user_creator_life_timespent_gt_20sec**                           0.5601872457191350
  **user_tpv_life_pcc_80_90**                                        0.5532864015549420
  **user_overall_mid_dislike**                                       0.5427206866443160
  **user_overall_mid_timespent_gt_60sec**                            0.5362488562241200
  **user_creator_life_like_ctr**                                     0.5220098188146950
  **user_overall_life_pcc_0_5**                                      0.5149557022377850
  **user_overall_life_timespent_gt_60sec**                           0.49536165315657900
  **user_tpv_life_share**                                            0.4913886543363330
  **user_overall_life_pcc_80_90**                                    0.48502516001462900
  **user_overall_short_total_engaged**                               0.4773685475811360
  **user_overall_mid_lp_ctr**                                        0.4606117494404320
  **user_creator_life_timespent_gt_10sec**                           0.45211315155029300
  **user_tpv_life_total_engaged**                                    0.45112299267202600
  **user_overall_life_timespent_gt_5sec**                            0.4372593481093650
  **user_creator_life_like**                                         0.4367050714790820
  **user_creator_life_pcc_70_80**                                    0.4307946655899290
  **user_tpv_life_like**                                             0.4155965056270360
  **user_tpv_life_pcc_90_100**                                       0.4080924205482010
  **user_tpv_life_timespent_gt_10sec**                               0.37987721152603600
  **user_tpv_life_pcc_60_70**                                        0.3707064548507330
  **user_creator_life_share**                                        0.3613451961427930
  **user_overall_mid_pcc_90_100**                                    0.35104413982480800
  **user_overall_mid_pcc_0_5**                                       0.33264646772295200
  **user_overall_mid_like**                                          0.32964914571493900
  **user_overall_short_download**                                    0.3198356367647650
  **creator_viewgt100000000**                                        0.31950543634593500
  **user_overall_life_pcc_70_80**                                    0.3178682876750830
  **user_tpv_life_pcc_40_60**                                        0.31055703293532100
  **creator_viewle100000000**                                        0.30720268841832900
  **user_overall_mid_share**                                         0.3069754457101230
  **user_overall_mid_pcc_70_80**                                     0.30275906901806600
  **user_tpv_life_pcc_20_40**                                        0.29841321520507300
  **user_tpv_life_timespent_gt_20sec**                               0.2983805490657690
  **user_overall_mid_timespent_gt_5sec**                             0.29718768782913700
  **user_overall_life_pcc_90_100**                                   0.29474503826350000
  **user_creator_life_pcc_90_100**                                   0.2889891155064110
  **user_creator_life_total_engaged**                                0.267044804058969
  **user_overall_life_pcc_60_70**                                    0.2664456842467190
  **user_overall_mid_pcc_60_70**                                     0.2618168480694290
  **user_overall_short_total_plays**                                 0.2542350674048070
  **user_creator_life_download**                                     0.25199197698384500
  **user_overall_mid_timespent_gt_30sec**                            0.24449166376143700
  **user_overall_mid_pcc_20_40**                                     0.23987996391952000
  **user_tpv_life_pcc_5_20**                                         0.227410183288157
  **user_tpv_life_ctr**                                              0.2199641428887840
  **user_overall_mid_like_ctr**                                      0.21923724561929700
  **user_overall_life_timespent_gt_20sec**                           0.21019657142460300
  **user_overall_mid_timespent_gt_20sec**                            0.2083497354760770
  **user_overall_life_pcc_5_20**                                     0.20822470542043400
  **user_overall_life_like**                                         0.20809511188417700
  **user_overall_mid_pcc_40_60**                                     0.20557967945933300
  **user_overall_life_download**                                     0.19715121015906300
  **user_overall_mid_timespent_le_5sec**                             0.19603667315095700
  **user_overall_mid_download**                                      0.1951923593878750
  **user_overall_mid_pcc_5_20**                                      0.18914826214313500
  **creator_viewle5000000**                                          0.1807864522561430
  **user_overall_life_pcc_40_60**                                    0.18071692902594800
  **user_tpv_life_like_ctr**                                         0.16521182842552700
  **user_overall_mid_timespent_gt_10sec**                            0.1633716281503440
  **user_overall_short_like**                                        0.16019768081605400
  **user_tpv_life_total_plays**                                      0.15028042253106800
  **user_overall_life_pcc_20_40**                                    0.14843358658254100
  **user_tpv_life_lp_ctr**                                           0.14247533399611700
  **user_overall_life_timespent_gt_10sec**                           0.12772143818438100
  **user_overall_life_share**                                        0.12363116256892700
  **user_overall_mid_loop**                                          0.11366910766810200
  **user_creator_life_total_plays**                                  0.11035313364118300
  **user_overall_life_timespent_le_5sec**                            0.108702527359128
  **creator_nsfwposted**                                             0.1040672417730090
  **creator_viewle500000**                                           0.10051820427179300
  **user_overall_mid_total_engaged**                                 0.09997470770031210
  **creator_viewle1000000**                                          0.08711488917469980
  **user_overall_life_total_plays**                                  0.053503247909247900
  **creator_viewle100000**                                           0.04941239021718500
  **creator_viewle50**                                               0.04713817033916710
  **creator_viewle50000**                                            0.04600232932716610
  **user_overall_mid_total_plays**                                   0.04393488634377720
  **creator_viewle1000**                                             0.034124287776649
  **user_overall_life_total_engaged**                                0.032931333407759700
  **creator_viewle10000**                                            0.032207369804382300
  **creator_viewle20**                                               0.030665472149848900
  **creator_videoposted**                                            0.02897626254707580
  **creator_viewle100**                                              0.02633261028677230
  **creator_viewle500**                                              0.023487117141485200
  **creator_daysvideoposted**                                        0.01880638301372530
  **creator_timespent_gt_60sec**                                     0.009034969843924050
  **item_ctr_24hr**                                                  0.004978245124220850
  **creator_timespent_gt_120sec**                                    0.00446811318397522
  **creator_pcc05**                                                  0.0022332649677991900
  **creator_pcc8090**                                                0.0019593164324760400
  **item_ctr**                                                       0.0019187107682228100
  **item_ctr_3d**                                                    0.0016946345567703200
  **creator_dl**                                                     0.0009313225746154790
  **creator_pcc6070**                                                0.000835140235722065
  **item_share_ctr_24hr**                                            0.0007256632670760160
  **item_like_ctr_24hr**                                             0.000635860487818718
  **item_like_ctr**                                                  0.0006141141057014470
  **item_ctr_7d**                                                    0.0004686182364821430
  **item_like_ctr_15d**                                              0.0003698980435729030
  **item_like_ctr_7d**                                               0.00034319236874580400
  **creator_ctr_24h**                                                0.0002573942765593530
  **creator_timespent_gt_30sec**                                     0.0002387678250670430
  **creator_timespent_gt_10sec**                                     0.0002387678250670430
  **creator_timespent_gt_20sec**                                     0.0002387678250670430
  **creator_pcc7080**                                                0.0002387678250670430
  **item_ctr_15d**                                                   0.0002387678250670430
  **creator_timespent_gt_5sec**                                      0.0002387678250670430
  **creator_download_ctr**                                           0.0002387678250670430
  **creator_share_ctr**                                              0.0002387678250670430
  **creator_like_ctr**                                               0.0002387678250670430
  **item_share_ctr**                                                 0.0002387678250670430
  **latitude**                                                       0.0002387678250670430
  **creator_ctr**                                                    0.0002387678250670430
  **item_share_ctr_15d**                                             0.0002387678250670430
  **item_like_ctr_3d**                                               0.0002387678250670430
  **creator_timespent_le_5sec**                                      0.0002387678250670430
  **creator_pcc90100**                                               0.0002387678250670430
  **creator_pcc4060**                                                0.0002387678250670430
  **creator_pcc2040**                                                0.0002387678250670430
  **creator_pcc520**                                                 0.0002387678250670430
  **creator_ctr_7d**                                                 0.0002387678250670430
  **creator_ctr_3d**                                                 0.0002387678250670430
  **creator_ctr_12d**                                                0.0002387678250670430
  **creator_cc**                                                     0.0002387678250670430
  **creator_sc**                                                     0.0002387678250670430
  **creator_lc**                                                     0.0002387678250670430
  **creator_lp**                                                     0.0002387678250670430
  **creator_cv**                                                     0.0002387678250670430
  **item_download_ctr**                                              0.0002387678250670430
  **item_share_ctr_7d**                                              0.0002387678250670430
  **item_share_ctr_3d**                                              0.0002387678250670430
  **longitude**                                                      0.0002387678250670430
  ------------------------------------------------------------------ ------------------------------------------------------
