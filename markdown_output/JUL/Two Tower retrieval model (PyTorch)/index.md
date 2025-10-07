*Following an example of MTL model, this page describes a two tower
models for user and items trained using ray.*

## Model versions

1.  V1 \<\-\-- we have this ready and want to experiment with it.

    1.  *At a high level, this is a simple two tower model using
        video/user-ID and non-ID features to project each entity into a
        K dimensional embedding.*

2.  V2

    1.  At a high level, this will be a bag of items based model

## V1 Trained user tower model is exported in:

`s3://josh-reco-ml-dataset/us-ml-team/models/retrieval/torch/prod/02122022/model_scripted.pt`

This is trained on 100% of 7 days data until 11/30; took 7.5 hrs on 8
gpus.

## V1 \[Sample\] Input to the exported user model's forward:

- Below is an example of an input batch with features of 2 users, passed
  to forward method:

{\'client_id\': tensor(\[\[-4051809575896614810\], \[
312847671560370627\]\]), \'creator_id\': tensor(\[\[
4254087672289006204\], \[-8240087861918539225\]\]), \'item_id\':
tensor(\[\[5202139100420288909\], \[8306332682418550710\]\]),
\'item_lang\': tensor(\[\[ 923421901795282152\],
\[4326204459932127792\]\]), \'user_lang\':
tensor(\[\[-4581073419408352527\], \[-5502504947823469636\]\]),
\'user_connection\': tensor(\[\[5006279549153002971\],
\[5006279549153002971\]\]), \'user_feed_source\':
tensor(\[\[-2014649680745157998\], \[-3806893605711019523\]\]),
\'creator_level\': tensor(\[\[ 436174504413106933\],
\[5324351509709555386\]\]), \'creator_user_type\':
tensor(\[\[-2550248491701579066\], \[-2550248491701579066\]\]),
\'user_os_platform\': tensor(\[\[-2189599060188726840\],
\[-2189599060188726840\]\]), \'user_os_ver\':
tensor(\[\[-7025373144296308602\], \[-7025373144296308602\]\]),
\'video_length\': tensor(\[\[23.2667\], \[15.0667\]\]),
\'item_like_uu\': tensor(\[\[ 131\], \[34513\]\]), \'item_share_uu\':
tensor(\[\[ 1\], \[1415\]\]), \'item_download_uu\': tensor(\[\[ 3\],
\[1436\]\]), \'item_view_uu\': tensor(\[\[ 11714\], \[1283876\]\]),
\'item_comment_uu\': tensor(\[\[ 0\], \[31\]\]), \'item_engagement_uu\':
tensor(\[\[ 8395\], \[840394\]\]), \'item_timespent_0to3\': tensor(\[\[
2401\], \[414164\]\]), \'item_timespent_3to6\': tensor(\[\[ 814\],
\[76668\]\]), \'item_timespent_6to9\': tensor(\[\[ 612\], \[39912\]\]),
\'item_timespent_9to12\': tensor(\[\[ 1237\], \[34676\]\]),
\'item_timespent_12to15\': tensor(\[\[ 661\], \[189901\]\]),
\'item_timespent_15to18\': tensor(\[\[ 368\], \[339426\]\]),
\'item_timespent_18to21\': tensor(\[\[ 490\], \[39107\]\]),
\'item_timespent_21to24\': tensor(\[\[ 2335\], \[13730\]\]),
\'item_timespent_24to30\': tensor(\[\[ 2382\], \[146749\]\]),
\'item_timespent_30to40\': tensor(\[\[ 743\], \[82583\]\]),
\'item_timespent_40to60\': tensor(\[\[ 345\], \[17247\]\]),
\'item_timespent_gt60\': tensor(\[\[ 113\], \[5996\]\]),
\'item_view_24h\': tensor(\[\[1436\], \[2282\]\]),
\'item_engagement_24h\': tensor(\[\[1024\], \[1676\]\]),
\'item_view_3d\': tensor(\[\[5309\], \[3101\]\]),
\'item_engagement_3d\': tensor(\[\[3774\], \[2258\]\]),
\'item_view_7d\': tensor(\[\[9541\], \[3559\]\]),
\'item_engagement_7d\': tensor(\[\[6976\], \[2461\]\]),
\'item_view_15d\': tensor(\[\[11634\], \[ 5860\]\]),
\'item_engagement_15d\': tensor(\[\[8325\], \[3883\]\]),
\'item_download_ctr\': tensor(\[\[0.0003\], \[0.0011\]\]),
\'item_share_ctr\': tensor(\[\[8.5368e-05\], \[1.1021e-03\]\]),
\'item_like_ctr\': tensor(\[\[0.0112\], \[0.0269\]\]), \'item_ctr\':
tensor(\[\[0.7139\], \[0.6485\]\]), \'item_ctr_24hr\':
tensor(\[\[0.7110\], \[0.7287\]\]), \'item_ctr_3d\':
tensor(\[\[0.7079\], \[0.7220\]\]), \'item_ctr_7d\':
tensor(\[\[0.7282\], \[0.6861\]\]), \'item_ctr_15d\':
tensor(\[\[0.7128\], \[0.6582\]\]), \'item_like_24h\': tensor(\[\[15\],
\[55\]\]), \'item_share_24h\': tensor(\[\[0\], \[3\]\]),
\'item_like_3d\': tensor(\[\[56\], \[78\]\]), \'item_share_3d\':
tensor(\[\[1\], \[3\]\]), \'item_like_7d\': tensor(\[\[105\], \[
82\]\]), \'item_share_7d\': tensor(\[\[1\], \[4\]\]), \'item_like_15d\':
tensor(\[\[130\], \[115\]\]), \'item_share_15d\': tensor(\[\[1\],
\[5\]\]), \'item_like_ctr_24hr\': tensor(\[\[0.0104\], \[0.0241\]\]),
\'item_like_ctr_3d\': tensor(\[\[0.0105\], \[0.0252\]\]),
\'item_like_ctr_7d\': tensor(\[\[0.0110\], \[0.0230\]\]),
\'item_like_ctr_15d\': tensor(\[\[0.0112\], \[0.0196\]\]),
\'item_share_ctr_24hr\': tensor(\[\[0.0000\], \[0.0013\]\]),
\'item_share_ctr_3d\': tensor(\[\[0.0002\], \[0.0010\]\]),
\'item_share_ctr_7d\': tensor(\[\[0.0001\], \[0.0011\]\]),
\'item_share_ctr_15d\': tensor(\[\[8.5955e-05\], \[8.5324e-04\]\]),
\'item_publish_date_in_epoch\': tensor(\[\[1.6681e+12\],
\[1.5999e+12\]\], dtype=torch.float64), \'creator_cv\': tensor(\[\[
23107\], \[1814858\]\], dtype=torch.int32), \'creator_pv\': tensor(\[\[
12806\], \[1064758\]\]), \'creator_lp\': tensor(\[\[ 8550\],
\[1025485\]\], dtype=torch.int32), \'creator_lc\': tensor(\[\[ 298\],
\[32411\]\], dtype=torch.int32), \'creator_sc\': tensor(\[\[0\],
\[0\]\], dtype=torch.int32), \'creator_cc\': tensor(\[\[0\], \[0\]\],
dtype=torch.int32), \'creator_dl\': tensor(\[\[ 32\], \[1335\]\],
dtype=torch.int32), \'creator_ctr_12d\': tensor(\[\[0.6066\],
\[0.6106\]\]), \'creator_ctr_24h\': tensor(\[\[0.6374\], \[0.6689\]\]),
\'creator_ctr_3d\': tensor(\[\[0.5842\], \[0.6710\]\]),
\'creator_ctr_7d\': tensor(\[\[0.6099\], \[0.6359\]\]),
\'creator_cv_12d\': tensor(\[\[15671\], \[ 4659\]\]),
\'creator_cv_24h\': tensor(\[\[1743\], \[2419\]\]), \'creator_cv_3d\':
tensor(\[\[8497\], \[3289\]\]), \'creator_cv_7d\': tensor(\[\[14474\],
\[ 3801\]\]), \'creator_dl_12d\': tensor(\[\[16\], \[ 4\]\]),
\'creator_dl_24h\': tensor(\[\[1\], \[3\]\]), \'creator_dl_3d\':
tensor(\[\[11\], \[ 3\]\]), \'creator_dl_7d\': tensor(\[\[15\], \[
4\]\]), \'creator_lc_12d\': tensor(\[\[192\], \[ 93\]\]),
\'creator_lc_24h\': tensor(\[\[18\], \[54\]\]), \'creator_lc_3d\':
tensor(\[\[98\], \[77\]\]), \'creator_lc_7d\': tensor(\[\[177\], \[
81\]\]), \'creator_pv_12d\': tensor(\[\[9506\], \[2845\]\]),
\'creator_pv_24h\': tensor(\[\[1111\], \[1618\]\]), \'creator_pv_3d\':
tensor(\[\[4964\], \[2207\]\]), \'creator_pv_7d\': tensor(\[\[8827\],
\[2417\]\]), \'creator_sc_12d\': tensor(\[\[8\], \[4\]\]),
\'creator_sc_24h\': tensor(\[\[0\], \[3\]\]), \'creator_sc_3d\':
tensor(\[\[2\], \[3\]\]), \'creator_sc_7d\': tensor(\[\[7\], \[4\]\]),
\'creator_videoposted\': tensor(\[\[15\], \[ 9\]\], dtype=torch.int32),
\'creator_nsfwposted\': tensor(\[\[4\], \[1\]\], dtype=torch.int32),
\'creator_pcc05\': tensor(\[\[ 4049\], \[111955\]\], dtype=torch.int32),
\'creator_pcc520\': tensor(\[\[ 4562\], \[446852\]\],
dtype=torch.int32), \'creator_pcc2040\': tensor(\[\[ 2081\],
\[122975\]\], dtype=torch.int32), \'creator_pcc4060\': tensor(\[\[
2384\], \[59751\]\], dtype=torch.int32), \'creator_pcc6070\':
tensor(\[\[ 559\], \[18224\]\], dtype=torch.int32), \'creator_pcc7080\':
tensor(\[\[ 663\], \[27460\]\], dtype=torch.int32), \'creator_pcc8090\':
tensor(\[\[ 839\], \[43468\]\], dtype=torch.int32),
\'creator_pcc90100\': tensor(\[\[ 7970\], \[984173\]\],
dtype=torch.int32), \'creator_viewle20\': tensor(\[\[2\], \[0\]\],
dtype=torch.int32), \'creator_viewle50\': tensor(\[\[1\], \[0\]\],
dtype=torch.int32), \'creator_viewle100\': tensor(\[\[2\], \[0\]\],
dtype=torch.int32), \'creator_viewle500\': tensor(\[\[1\], \[1\]\],
dtype=torch.int32), \'creator_viewle1000\': tensor(\[\[8\], \[3\]\],
dtype=torch.int32), \'creator_viewle10000\': tensor(\[\[0\], \[2\]\],
dtype=torch.int32), \'creator_viewle50000\': tensor(\[\[1\], \[2\]\],
dtype=torch.int32), \'creator_viewle100000\': tensor(\[\[0\], \[0\]\],
dtype=torch.int32), \'creator_viewle500000\': tensor(\[\[0\], \[0\]\],
dtype=torch.int32), \'creator_viewle1000000\': tensor(\[\[0\], \[0\]\],
dtype=torch.int32), \'creator_viewle5000000\': tensor(\[\[0\], \[1\]\],
dtype=torch.int32), \'creator_viewle100000000\': tensor(\[\[0\],
\[0\]\], dtype=torch.int32), \'creator_viewgt100000000\':
tensor(\[\[0\], \[0\]\], dtype=torch.int32),
\'creator_daysvideoposted\': tensor(\[\[13\], \[ 4\]\],
dtype=torch.int32), \'creator_timespent_le_5sec\': tensor(\[\[ 8020\],
\[647525\]\], dtype=torch.int32), \'creator_timespent_gt_5sec\':
tensor(\[\[ 2281\], \[102575\]\], dtype=torch.int32),
\'creator_timespent_gt_10sec\': tensor(\[\[ 3663\], \[738390\]\],
dtype=torch.int32), \'creator_timespent_gt_20sec\': tensor(\[\[ 5452\],
\[188431\]\], dtype=torch.int32), \'creator_timespent_gt_30sec\':
tensor(\[\[ 2887\], \[130641\]\], dtype=torch.int32),
\'creator_timespent_gt_60sec\': tensor(\[\[ 748\], \[5827\]\],
dtype=torch.int32), \'creator_timespent_gt_120sec\': tensor(\[\[ 56\],
\[1469\]\], dtype=torch.int32), \'creator_ctr\': tensor(\[\[0.5542\],
\[0.5867\]\]), \'creator_download_ctr\': tensor(\[\[0.0014\],
\[0.0007\]\]), \'creator_share_ctr\': tensor(\[\[0.\], \[0.\]\]),
\'creator_like_ctr\': tensor(\[\[0.0129\], \[0.0179\]\]),
\'user_overall_short_loop\': tensor(\[\[320.\], \[ 74.\]\],
dtype=torch.float64), \'user_overall_short_like\': tensor(\[\[6.\],
\[0.\]\], dtype=torch.float64), \'user_overall_short_share\':
tensor(\[\[14.\], \[ 0.\]\], dtype=torch.float64),
\'user_overall_short_comment\': tensor(\[\[0.\], \[0.\]\],
dtype=torch.float64), \'user_overall_short_download\': tensor(\[\[14.\],
\[ 0.\]\], dtype=torch.float64),
\'user_overall_short_timespent_le_5sec\': tensor(\[\[111.\], \[217.\]\],
dtype=torch.float64), \'user_overall_short_timespent_gt_5sec\':
tensor(\[\[80.\], \[48.\]\], dtype=torch.float64),
\'user_overall_short_timespent_gt_10sec\': tensor(\[\[305.\], \[
75.\]\], dtype=torch.float64),
\'user_overall_short_timespent_gt_20sec\': tensor(\[\[81.\], \[27.\]\],
dtype=torch.float64), \'user_overall_short_timespent_gt_30sec\':
tensor(\[\[56.\], \[15.\]\], dtype=torch.float64),
\'user_overall_short_timespent_gt_60sec\': tensor(\[\[13.\], \[ 2.\]\],
dtype=torch.float64), \'user_overall_short_timespent_gt_120sec\':
tensor(\[\[2.\], \[0.\]\], dtype=torch.float64),
\'user_overall_short_pcc_0_5\': tensor(\[\[17.\], \[48.\]\],
dtype=torch.float64), \'user_overall_short_pcc_5_20\': tensor(\[\[
70.\], \[145.\]\], dtype=torch.float64),
\'user_overall_short_pcc_20_40\': tensor(\[\[66.\], \[63.\]\],
dtype=torch.float64), \'user_overall_short_pcc_40_60\':
tensor(\[\[63.\], \[28.\]\], dtype=torch.float64),
\'user_overall_short_pcc_60_70\': tensor(\[\[26.\], \[ 8.\]\],
dtype=torch.float64), \'user_overall_short_pcc_70_80\':
tensor(\[\[34.\], \[ 9.\]\], dtype=torch.float64),
\'user_overall_short_pcc_80_90\': tensor(\[\[69.\], \[ 6.\]\],
dtype=torch.float64), \'user_overall_short_pcc_90_100\':
tensor(\[\[303.\], \[ 77.\]\], dtype=torch.float64),
\'user_overall_short_dislike\': tensor(\[\[0.\], \[0.\]\],
dtype=torch.float64), \'user_overall_short_lp_ctr\':
tensor(\[\[0.5000\], \[0.2000\]\]),
\'user_overall_short_total_engaged\': tensor(\[\[457.\], \[119.\]\],
dtype=torch.float64), \'user_overall_short_total_plays\':
tensor(\[\[648.\], \[384.\]\], dtype=torch.float64),
\'user_overall_short_ctr\': tensor(\[\[0.7100\], \[0.3100\]\]),
\'user_overall_short_like_ctr\': tensor(\[\[0.0100\], \[0.0000\]\]),
\'user_overall_short_download_ctr\': tensor(\[\[0.0300\], \[0.0000\]\]),
\'user_overall_mid_loop\': tensor(\[\[464.\], \[144.\]\],
dtype=torch.float64), \'user_overall_mid_like\': tensor(\[\[9.\],
\[0.\]\], dtype=torch.float64), \'user_overall_mid_share\':
tensor(\[\[18.\], \[ 0.\]\], dtype=torch.float64),
\'user_overall_mid_comment\': tensor(\[\[0.\], \[0.\]\],
dtype=torch.float64), \'user_overall_mid_download\': tensor(\[\[18.\],
\[ 0.\]\], dtype=torch.float64), \'user_overall_mid_timespent_le_5sec\':
tensor(\[\[215.\], \[365.\]\], dtype=torch.float64),
\'user_overall_mid_timespent_gt_5sec\': tensor(\[\[131.\], \[ 91.\]\],
dtype=torch.float64), \'user_overall_mid_timespent_gt_10sec\':
tensor(\[\[524.\], \[146.\]\], dtype=torch.float64),
\'user_overall_mid_timespent_gt_20sec\': tensor(\[\[135.\], \[ 47.\]\],
dtype=torch.float64), \'user_overall_mid_timespent_gt_30sec\':
tensor(\[\[78.\], \[31.\]\], dtype=torch.float64),
\'user_overall_mid_timespent_gt_60sec\': tensor(\[\[15.\], \[ 4.\]\],
dtype=torch.float64), \'user_overall_mid_timespent_gt_120sec\':
tensor(\[\[2.\], \[1.\]\], dtype=torch.float64),
\'user_overall_mid_pcc_0_5\': tensor(\[\[28.\], \[78.\]\],
dtype=torch.float64), \'user_overall_mid_pcc_5_20\': tensor(\[\[131.\],
\[257.\]\], dtype=torch.float64), \'user_overall_mid_pcc_20_40\':
tensor(\[\[117.\], \[112.\]\], dtype=torch.float64),
\'user_overall_mid_pcc_40_60\': tensor(\[\[109.\], \[ 50.\]\],
dtype=torch.float64), \'user_overall_mid_pcc_60_70\': tensor(\[\[50.\],
\[14.\]\], dtype=torch.float64), \'user_overall_mid_pcc_70_80\':
tensor(\[\[63.\], \[17.\]\], dtype=torch.float64),
\'user_overall_mid_pcc_80_90\': tensor(\[\[120.\], \[ 13.\]\],
dtype=torch.float64), \'user_overall_mid_pcc_90_100\':
tensor(\[\[482.\], \[144.\]\], dtype=torch.float64),
\'user_overall_mid_dislike\': tensor(\[\[0.\], \[0.\]\],
dtype=torch.float64), \'user_overall_mid_lp_ctr\': tensor(\[\[0.4300\],
\[0.2200\]\]), \'user_overall_mid_total_engaged\': tensor(\[\[754.\],
\[229.\]\], dtype=torch.float64), \'user_overall_mid_total_plays\':
tensor(\[\[1100.\], \[ 685.\]\], dtype=torch.float64),
\'user_overall_mid_ctr\': tensor(\[\[0.6900\], \[0.3400\]\]),
\'user_overall_mid_like_ctr\': tensor(\[\[0.0100\], \[0.0000\]\]),
\'user_overall_mid_download_ctr\': tensor(\[\[0.0200\], \[0.0000\]\]),
\'user_overall_life_like\': tensor(\[\[40.\], \[ 0.\]\],
dtype=torch.float64), \'user_overall_life_share\': tensor(\[\[40.\], \[
0.\]\], dtype=torch.float64), \'user_overall_life_comment\':
tensor(\[\[0.\], \[0.\]\], dtype=torch.float64),
\'user_overall_life_download\': tensor(\[\[61.\], \[ 0.\]\],
dtype=torch.float64), \'user_overall_life_timespent_le_5sec\':
tensor(\[\[2277.\], \[ 443.\]\], dtype=torch.float64),
\'user_overall_life_timespent_gt_5sec\': tensor(\[\[1188.\], \[
106.\]\], dtype=torch.float64),
\'user_overall_life_timespent_gt_10sec\': tensor(\[\[3543.\], \[
168.\]\], dtype=torch.float64),
\'user_overall_life_timespent_gt_20sec\': tensor(\[\[915.\], \[ 51.\]\],
dtype=torch.float64), \'user_overall_life_timespent_gt_30sec\':
tensor(\[\[620.\], \[ 38.\]\], dtype=torch.float64),
\'user_overall_life_timespent_gt_60sec\': tensor(\[\[93.\], \[ 5.\]\],
dtype=torch.float64), \'user_overall_life_timespent_gt_120sec\':
tensor(\[\[17.\], \[ 1.\]\], dtype=torch.float64),
\'user_overall_life_pcc_0_5\': tensor(\[\[297.\], \[ 98.\]\],
dtype=torch.float64), \'user_overall_life_pcc_5_20\':
tensor(\[\[1651.\], \[ 312.\]\], dtype=torch.float64),
\'user_overall_life_pcc_20_40\': tensor(\[\[1175.\], \[ 132.\]\],
dtype=torch.float64), \'user_overall_life_pcc_40_60\':
tensor(\[\[894.\], \[ 58.\]\], dtype=torch.float64),
\'user_overall_life_pcc_60_70\': tensor(\[\[460.\], \[ 15.\]\],
dtype=torch.float64), \'user_overall_life_pcc_70_80\':
tensor(\[\[515.\], \[ 20.\]\], dtype=torch.float64),
\'user_overall_life_pcc_80_90\': tensor(\[\[990.\], \[ 14.\]\],
dtype=torch.float64), \'user_overall_life_pcc_90_100\':
tensor(\[\[2671.\], \[ 163.\]\], dtype=torch.float64),
\'user_overall_life_dislike\': tensor(\[\[0.\], \[0.\]\],
dtype=torch.float64), \'user_overall_life_lp_ctr\': tensor(\[\[0.3800\],
\[0.2100\]\]), \'user_overall_life_total_engaged\': tensor(\[\[5188.\],
\[ 263.\]\], dtype=torch.float64), \'user_overall_life_total_plays\':
tensor(\[\[8653.\], \[ 812.\]\], dtype=torch.float64),
\'user_overall_life_ctr\': tensor(\[\[0.6000\], \[0.3300\]\]),
\'user_overall_life_like_ctr\': tensor(\[\[0.0100\], \[0.0000\]\]),
\'user_overall_life_download_ctr\': tensor(\[\[0.0100\], \[0.0000\]\]),
\'user_creator_life_like\': tensor(\[\[31.\], \[ 0.\]\],
dtype=torch.float64), \'user_creator_life_share\': tensor(\[\[36.\], \[
0.\]\], dtype=torch.float64), \'user_creator_life_comment\':
tensor(\[\[0.\], \[0.\]\], dtype=torch.float64),
\'user_creator_life_download\': tensor(\[\[39.\], \[ 0.\]\],
dtype=torch.float64), \'user_creator_life_timespent_le_5sec\':
tensor(\[\[635.\], \[224.\]\], dtype=torch.float64),
\'user_creator_life_timespent_gt_5sec\': tensor(\[\[392.\], \[ 42.\]\],
dtype=torch.float64), \'user_creator_life_timespent_gt_10sec\':
tensor(\[\[1641.\], \[ 130.\]\], dtype=torch.float64),
\'user_creator_life_timespent_gt_20sec\': tensor(\[\[441.\], \[ 47.\]\],
dtype=torch.float64), \'user_creator_life_timespent_gt_30sec\':
tensor(\[\[297.\], \[ 37.\]\], dtype=torch.float64),
\'user_creator_life_timespent_gt_60sec\': tensor(\[\[48.\], \[ 5.\]\],
dtype=torch.float64), \'user_creator_life_timespent_gt_120sec\':
tensor(\[\[8.\], \[1.\]\], dtype=torch.float64),
\'user_creator_life_pcc_0_5\': tensor(\[\[78.\], \[56.\]\],
dtype=torch.float64), \'user_creator_life_pcc_5_20\': tensor(\[\[453.\],
\[154.\]\], dtype=torch.float64), \'user_creator_life_pcc_20_40\':
tensor(\[\[373.\], \[ 56.\]\], dtype=torch.float64),
\'user_creator_life_pcc_40_60\': tensor(\[\[359.\], \[ 33.\]\],
dtype=torch.float64), \'user_creator_life_pcc_60_70\':
tensor(\[\[209.\], \[ 6.\]\], dtype=torch.float64),
\'user_creator_life_pcc_70_80\': tensor(\[\[257.\], \[ 10.\]\],
dtype=torch.float64), \'user_creator_life_pcc_80_90\':
tensor(\[\[427.\], \[ 8.\]\], dtype=torch.float64),
\'user_creator_life_pcc_90_100\': tensor(\[\[1306.\], \[ 163.\]\],
dtype=torch.float64), \'user_creator_life_dislike\': tensor(\[\[0.\],
\[0.\]\], dtype=torch.float64), \'user_creator_life_lp_ctr\':
tensor(\[\[0.4400\], \[0.3400\]\]), \'user_creator_life_total_engaged\':
tensor(\[\[2435.\], \[ 220.\]\], dtype=torch.float64),
\'user_creator_life_total_plays\': tensor(\[\[3462.\], \[ 486.\]\],
dtype=torch.float64), \'user_creator_life_ctr\': tensor(\[\[0.7100\],
\[0.4600\]\]), \'user_creator_life_like_ctr\': tensor(\[\[0.0100\],
\[0.0000\]\]), \'user_creator_life_download_ctr\': tensor(\[\[0.0200\],
\[0.0000\]\]), \'user_tpv_life_like\': tensor(\[\[ 0.\], \[-1.\]\],
dtype=torch.float64), \'user_tpv_life_share\': tensor(\[\[ 0.\],
\[-1.\]\], dtype=torch.float64), \'user_tpv_life_comment\': tensor(\[\[
0.\], \[-1.\]\], dtype=torch.float64), \'user_tpv_life_download\':
tensor(\[\[ 0.\], \[-1.\]\], dtype=torch.float64),
\'user_tpv_life_timespent_le_5sec\': tensor(\[\[ 0.\], \[-1.\]\],
dtype=torch.float64), \'user_tpv_life_timespent_gt_5sec\': tensor(\[\[
0.\], \[-1.\]\], dtype=torch.float64),
\'user_tpv_life_timespent_gt_10sec\': tensor(\[\[ 0.\], \[-1.\]\],
dtype=torch.float64), \'user_tpv_life_timespent_gt_20sec\': tensor(\[\[
0.\], \[-1.\]\], dtype=torch.float64),
\'user_tpv_life_timespent_gt_30sec\': tensor(\[\[ 0.\], \[-1.\]\],
dtype=torch.float64), \'user_tpv_life_timespent_gt_60sec\': tensor(\[\[
0.\], \[-1.\]\], dtype=torch.float64),
\'user_tpv_life_timespent_gt_120sec\': tensor(\[\[ 1.\], \[-1.\]\],
dtype=torch.float64), \'user_tpv_life_pcc_0_5\': tensor(\[\[ 0.\],
\[-1.\]\], dtype=torch.float64), \'user_tpv_life_pcc_5_20\': tensor(\[\[
0.\], \[-1.\]\], dtype=torch.float64), \'user_tpv_life_pcc_20_40\':
tensor(\[\[ 0.\], \[-1.\]\], dtype=torch.float64),
\'user_tpv_life_pcc_40_60\': tensor(\[\[ 0.\], \[-1.\]\],
dtype=torch.float64), \'user_tpv_life_pcc_60_70\': tensor(\[\[ 0.\],
\[-1.\]\], dtype=torch.float64), \'user_tpv_life_pcc_70_80\':
tensor(\[\[ 0.\], \[-1.\]\], dtype=torch.float64),
\'user_tpv_life_pcc_80_90\': tensor(\[\[ 0.\], \[-1.\]\],
dtype=torch.float64), \'user_tpv_life_pcc_90_100\': tensor(\[\[ 1.\],
\[-1.\]\], dtype=torch.float64), \'user_tpv_life_dislike\': tensor(\[\[
0.\], \[-1.\]\], dtype=torch.float64), \'user_tpv_life_lp_ctr\':
tensor(\[\[ 0.\], \[-1.\]\]), \'user_tpv_life_total_engaged\':
tensor(\[\[ 1.\], \[-1.\]\], dtype=torch.float64),
\'user_tpv_life_total_plays\': tensor(\[\[ 1.\], \[-1.\]\],
dtype=torch.float64), \'user_tpv_life_ctr\': tensor(\[\[ 1.\],
\[-1.\]\]), \'user_tpv_life_like_ctr\': tensor(\[\[ 0.\], \[-1.\]\]),
\'user_tpv_life_download_ctr\': tensor(\[\[ 0.\], \[-1.\]\]),
\'play_timestamp\': tensor(\[\[1669299905\], \[1669377932\]\]),
\'latitude\': tensor(\[\[-1.\], \[-1.\]\], dtype=torch.float64),
\'longitude\': tensor(\[\[-1.\], \[-1.\]\], dtype=torch.float64),
\'e_watch_duration\': tensor(\[24.2750, 16.7060\], dtype=torch.float64),
\'p_watch\': tensor(\[1., 1.\])} \## end input

## V1 \[Sample\] Output of the exported user model's forward:

- Below is an output embedding example from the forward method.

tensor(\[\[ 8.6332e-02, -1.6138e-01, 2.4185e-01, -8.8508e-02,
2.6923e-02, 1.2509e-01, 5.7762e-02, -8.6006e-02, -9.5532e-02,
1.5369e-01, -1.3635e-01, 8.8171e-02, 7.4676e-02, 2.0063e-01, 2.1606e-01,
2.9447e-01, -1.7519e-01, -5.4806e-02, -1.1762e-01, 1.8505e-01,
8.0222e-02, 1.3808e-01, 1.7482e-02, -2.9529e-01, -2.1031e-01,
-2.1111e-01, 2.7559e-01, -1.3607e-01, 9.3914e-02, -1.5093e-01,
-1.3073e-01, -2.8112e-04, -1.4873e-01, 4.3810e-02, 2.4332e-01,
6.2773e-02, 6.1483e-02, -3.0013e-02, 1.6408e-01, -1.2083e-01,
1.5780e-01, -6.2816e-02, 9.5877e-02, 1.4135e-01, 1.1604e-01, 4.1560e-02,
-3.4482e-02, -1.5206e-02\], \[ 4.2702e-02, 1.7685e-01, 9.9337e-02,
2.2983e-01, 4.5765e-02, -3.0888e-02, 1.1864e-01, 3.0058e-03,
-2.8382e-02, 8.0594e-02, 2.0381e-01, 3.6420e-04, 2.2213e-01, 3.3977e-01,
9.1263e-02, 1.1904e-01, -3.4495e-01, -2.2206e-01, -2.4112e-02,
1.1451e-01, 4.4632e-02, -1.0048e-01, -3.8445e-02, -3.4419e-01,
1.0249e-01, 3.9756e-02, 4.3962e-02, 7.0105e-02, -9.7255e-03,
-3.9112e-01, -9.5129e-02, 1.4135e-01, 4.2617e-02, 1.9792e-01,
5.2666e-02, -4.7386e-02, -4.5596e-02, -1.4239e-01, -1.2832e-02,
3.7982e-02, -8.9948e-02, 2.5115e-02, 1.0650e-01, 8.7699e-02, 1.0580e-01,
1.4797e-01, 4.6620e-02, 5.3992e-02\]\])

## Training data:

- label: watch percentage \> 0.85 or watch time \> 60s

- 7 days of data

- x.x B rows

- 3 epochs\

## V1 Model accuracy numbers (In batch)

\## During eval - \'val_loss\': 19.223135528564455,
\'val_hit_rate_at_1\': 0.05109374999999999, \'val_hit_rate_at_5\':
0.13405029296874993, \'val_hit_rate_at_20\': 0.2518774414062501,
\'val_hit_rate_at_100\': 0.47223388671875, \'val_hit_rate_at_200\':
0.5823254394531249 \## During training val_loss: 19.18995913752803
val_hit_rate_at_1: 0.05095757378472222482919 val_hit_rate_at_5:
0.134223090277777882923 val_hit_rate_at_20: 0.2526403356481481482921
val_hit_rate_at_100: 0.472299081307870358292 val_hit_rate_at_200:
0.58207194010416668292 train_loss: 17.3535530925723182916
train_hit_rate_at_1: 0.07750067291648806 train_hit_rate_at_5:
0.194328763725672982915 train_hit_rate_at_20: 0.351632772130763182913
train_hit_rate_at_100: 0.599152142005596482912 train_hit_rate_at_200:
0.70849001486180528291

## Serving the model:

There are user and item side embeddings.

User side embeddings are produced by using the model in the following
way:

model = torch.jit.load(path_to_pt_file) \# model.forward(self, batch:
Dict\[str, torch.Tensor\]) -\> torch.Tensor batch: Dict\[str,
torch.Tensor\] = { \"feature0_name\": torch.Tensor(\[feature0_value\]),
\"feature1_name\": torch.Tensor(\[feature1_value\]), \... } user_emb =
model.forward(batch)

Output is a batch of user embeddings, 48 dim each.

Item side embeddings are output by running the item tower on all unique
item ids:

`s3://josh-reco-ml-dataset/us-ml-team/models/retrieval/torch/prod/02122022/item_emb.parquet`

Those are indexed using ScaNN and output into:

`s3://josh-reco-ml-dataset/us-ml-team/models/retrieval/torch/prod/02122022/scann_index`

Please refer to the notebook for the steps to load the index, initialize
and query it (for now, keeping it in Chetan's instance since it's
running, probably should push it into the repo):

<https://cverma-5.notebook.ap-south-1.sagemaker.aws/notebooks/scann_for_recurrent_training.ipynb#Indexing-all-of-the-item-embeddings>

### *Below are all of the user features that needs to be present in order to run the forward of the exported model.*

## V1 Numerical features for user tower (torch.float):

Convert feature names to lower case. Null imputed by -1

\[ \'user_overall_short_loop\', \'user_overall_short_like\',
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

## V1 Categorical (string) features for user tower (torch.long):

*Convert feature names to lower case. Null imputed by NA and then hashed
the following way:*

seed = xxhash.xxh32(to_lower_case(column_name), 0).intdigest()
batch\[column_name\] = np.array( \[ \# xxh64 ranges from 0 to 2\*\*64-1
\# torch.int64 ranges from -2\*\*63 to 2\*\*63-1
xxhash.xxh64(str(value), seed).intdigest() - 2\*\*63 for value in
batch\[column_name\].values \], dtype=np.int64, )

Features are:

\[ \'client_id\', \'user_lang\', \'user_connection\',
\'user_feed_source\', \'user_os_platform\', \'user_os_ver\', \]

## V1 Location features for user tower (torch.float):

*Convert feature names to lower case. Null imputed by -1.0*

\[ \'latitude\', \'longitude\', \]

## V1 All numerical features used in training (torch.float):

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
\'item_share_ctr_7d\', \'item_share_ctr_15d\',
\'item_publish_date_in_epoch\', \'creator_cv\', \'creator_pv\',
\'creator_lp\', \'creator_lc\', \'creator_sc\', \'creator_cc\',
\'creator_dl\', \'creator_ctr_12d\', \'creator_ctr_24h\',
\'creator_ctr_3d\', \'creator_ctr_7d\', \'creator_cv_12d\',
\'creator_cv_24h\', \'creator_cv_3d\', \'creator_cv_7d\',
\'creator_dl_12d\', \'creator_dl_24h\', \'creator_dl_3d\',
\'creator_dl_7d\', \'creator_lc_12d\', \'creator_lc_24h\',
\'creator_lc_3d\', \'creator_lc_7d\', \'creator_pv_12d\',
\'creator_pv_24h\', \'creator_pv_3d\', \'creator_pv_7d\',
\'creator_sc_12d\', \'creator_sc_24h\', \'creator_sc_3d\',
\'creator_sc_7d\', \'creator_videoposted\', \'creator_nsfwposted\',
\'creator_pcc05\', \'creator_pcc520\', \'creator_pcc2040\',
\'creator_pcc4060\', \'creator_pcc6070\', \'creator_pcc7080\',
\'creator_pcc8090\', \'creator_pcc90100\', \'creator_viewle20\',
\'creator_viewle50\', \'creator_viewle100\', \'creator_viewle500\',
\'creator_viewle1000\', \'creator_viewle10000\',
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

## V1 All categorical (string) features used in training (torch.long):

*Same processing applied as for user features - convert feature names to
lower case.*

*Null imputed by NA and then hashed.*

\[ \'client_id\', \'creator_id\', \'item_id\', \'item_lang\',
\'user_lang\', \'user_connection\', \'user_feed_source\',
\'creator_level\', \'creator_user_type\', \'user_os_platform\',
\'user_os_ver\', \]

## V1 Location features used in training of a full model (torch.float):

*Convert feature names to lower case. Null imputed by -1.0*

\[ \'latitude\', \'longitude\', \]
