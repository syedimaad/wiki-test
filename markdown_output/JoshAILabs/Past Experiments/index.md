These are trained on 60% of 7 days data  of Hindi Language 

**Filter Condition**

1.  Client Filter Criteria

    - min 4 interactions

    - max 2000 interactions (for 7 days) (99.9 percentile)

    - min 1 positive interaction

    - min 1 neg interaction

2.  Item Filter Criteria

    - min 100 views

**Features Used**

**1.User Features**

- `hod (Hour of the Day)`

- `dow (Day of the Week)`

- `handset_maker (maker of the mobile)`

- `pos_mean_embedding (mean of past 100 positive  events Blip embeddings)`

- `neg_mean_embedding (mean of past 100 negative  events Blip embeddings)`

- `user_meta_features `

  - `User_overall_short_like_ctr`

  - `User_overall_short_share_ctr`

  - `User_overall_short_download_ctr`

  - `User_overall_mid_ctr`

  - `User_overall_mid_like_ctr`

  - `User_overall_mid_share_ctr`

  - `User_overall_mid_download_ctr`

  - `User_overall_life_ctr`

  - `User_overall_life_like_ctr`

  - `User_overall_life_share_ctr`

  - `User_overall_life_download_ctr`

**2. Item Features**

- `Creator_id`

- `` Target_item_embedding (Item`s Blip Embedding) ``

- `Item_age`

- `Item_meta_features`

  - `Item_ctr`

  - `Item_like_ctr`

  - `Item_share_ctr`

  - `Item_download_ctr`

  - `Item_ctr_24hr`

  - `Item_ctr_3d`

  - `Item_ctr_7d`

  - `Item_ctr_15d`

  - `Item_like_ctr_24hr`

  - `Item_like_ctr_3d`

  - `Item_like_ctr_7d`

  - `Item_like_ctr_15d`

  - `Item_share_ctr_24hr`

  - `Item_share_ctr_3d`

  - `Item_share_ctr_7d`

  - `Item_share_ctr_15d`

  - `Creator_ctr`

  - `Creator_like_ctr`

  - `Creator_share_ctr`

  - `Creator_download_ctr`

**Model Tuners**

- Loss Functions : BinaryCrossEntropy( binary classifier ) and
  MeanSquaredError (regression)

- Metrics : \[\]( binary classifier) and \[MeanAbsoluteError ,
  RootMeanSquaredError\](regression)

- Optimizer : Adam ( binary classifier & regression)

**Experiment**

**Buckets**

**Task**

**Archi-tecture**

**Metric**

**Group by**

**Level**

**Aggrega-tion (AVG)/ Gain**

video length

1-sec video-length distrubuted quantiles

timespent

binary classifier on wtg label

Two-Tower Base

video length

5-sec video-length distru-buted quantiles

timespent

binary classifier on wtg label

Two-Tower Base

video length

equi distru-buted quantiles

timespent

binary classifier on wtg label

Two-Tower Base

equi distrubution gave better hit-ratio

video length

equi distru-buted quantiles

timespent

binary classifier on wtg label\
+\
regression task on videolength

Two-Tower Base + gradient reversal layer

hit-ratio is higher than prod-dnn .

prod-wtg-1

video length

equi distru-buted quantiles

timespent

regression task on wtg label

Two-Tower Base

same hit-ratio as above but, faster training

Went to prod but later came back

hit-ratio is not correct method

video length

equi distru-buted quantiles

timespent

regression task on wtg label

Two-Tower base - \[MOD\] ( only item_age column has non-expansion layer)

recall@5 and recall@10 are almost equal to prod-p90

video length

equi distru-buted quantiles

pcc (percentage completion)

binary classifier on wtg label\

modified two tower

recall@5 , recall@10 , map are on par with prod-p90

but auc,mrr recall@50,\
recall@100 are low

Inconsistent results across days

prod-wtg-2

Item-id

each item-id level

timespent

binary classifier on wtg label

modified two tower

recall@5 , recall@10 , recall@50,\
map are higher than prod-p90 with more marginal gap

but auc,mrr, recall@100 are low

consistent results across days

**Prod-wtg-2**\
\
remote server :
[http://10.10.48.35:1234/data/saikrishna/prod/Iwtg/josh-dnn-two-tower-recsys-generic-datagen](http://10.10.48.35:1234/tree/saikrishna/prod/Iwtg/josh-dnn-two-tower-recsys-generic-datagen)

  ---------- ----------- ----------- ------------ -------
  Recall@5   Recall@10   Recall@50   Recall@100   MAP
  0.755      0.783       0.825       0.863        0.737
  ---------- ----------- ----------- ------------ -------

\
It has satisfied its requirement of increasing users watch time but was
bot able to perform well on pcc 98 and also serving was very less (may
be because of build server)
