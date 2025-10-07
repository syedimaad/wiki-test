## 1. Motivation

At a high level, Josh has a lot of newly created videos, each of them
ranging from to-be-popular videos to a long tail of random and weird
ones. Can we predict their future potential or quality and use such
predictions to improve our stack?

Specifically, these predictions can be used in at least the follow
places:

1.  Update blending function by making it aware of the predicted quality

2.  Make the flywheel (cold start content) candidate retrieval more
    effective by sampling based on these "quality" predictions

3.  Consume these predictions as features in ranker and candidate
    generation models

Note that the notion of quality that we want to predict here
encapsulates popularity, skip rates of videos and not their visual
quality.

## 2. Formulation

Look at created videos in a day and try to predict their performance 7
days later, but based on information available at creation time. This
means that 1 training example corresponds to 1 newly created video.

Details (features, architecture, performance) of different versions of
the quality model are available below.

## 3. Feature ablation

For experiments in this section, I train on 11 days, 15 epochs (approx
700k videos per day), with dcn-dlrm MTL architecture having 4 task: (1)
avg watch time, (2) num full watches, (3) num skips, (4) skip rate for
each created video. Batch size=2e9. Skips are defined as time spent is 0
to 3 sec. Full watch is defined as time spent \>= 100% of video length.

[Spearman
correlation](https://en.wikipedia.org/wiki/Spearman%27s_rank_correlation_coefficient)
is used to measure how well the model can rank test data for the
corresponding task. This metric varies from \[-1, 1\] and 0 means the
model isn't able to predict ordering better than random. +1 means
perfect ordering.

**Key takeaways**

- BLIP features alone bring more predictive power than creator features
  alone, however the creator features are also fairly useful and bring
  +8-20% improvement when used with BLIP.

TODO: add bias analysis when language and length are also used

## 4. \[V1\] BLIP based quality model

**Features**

- BLIP embedding of a video

**Architecture**

- DCN-DLRM based model trained on 4 tasks:

  - item_timespent_0to3

  - avg_watch_time

  - num_full_watch

  - item_skip_ctr_7d

- For just the BLIP embedding as feature, this architecture basically
  calculates dot products across different dimensions of blip embedding
  (and its projections), in addition to more projects and norms

**Training data**

- Model trained on 26 days, ending on 20230102. Approx 18M videos

- Training data obtained by joining created videos metadata with item
  level performance 7 days later

**Misc**

- MLFlow experiment id - TODO

**Performance**

This and the below sections need updating

  -------- -------
  metric   value
  -------- -------

  ---------------------------------------- ---------------------
  val_e_item_timespent_0to3_MAE            257.76897888183595
  val_e_item_timespent_0to3_log1p_R2       0.3853572070598602
  val_e_item_timespent_0to3_SpearmanCorr   0.7552288472652435
  val_e_item_timespent_0to3_count          38188.0
  val_e_item_timespent_0to3_loss           1.1957720518112183
  val_e_avg_watch_time_MAE                 2.2924069573488906
  val_e_avg_watch_time_log1p_R2            0.2285300492703568
  val_e_avg_watch_time_SpearmanCorr        0.4354913294315338
  val_e_avg_watch_time_count               38188.0
  val_e_avg_watch_time_loss                0.9233237981796265
  val_e_num_full_watch_MAE                 116.85801138237744
  val_e_num_full_watch_log1p_R2            0.38362570671895174
  val_e_num_full_watch_SpearmanCorr        0.573390680551529
  val_e_num_full_watch_count               38188.0
  val_e_num_full_watch_loss                1.1600802898406983
  val_p_item_skip_ctr_7d_calibration       0.9955864786605932
  val_p_item_skip_ctr_7d_SpearmanCorr      0.28189843595027925
  val_p_item_skip_ctr_7d_loss              0.9761700391769409
  val_loss                                 4.255346250534058
  ---------------------------------------- ---------------------

**Model location**

- `s3://josh-reco-ml-dataset/us-ml-team/models/quality/v1`

**Demo videos**

In a test set of 224 videos -

**Below are the videos predicted most skippable. (1 = most skippable)**

1.  [https://share.myjosh.in/content/87078e55-dd16-401e-ba62-d3663913cbfc](https://share.myjosh.in/content/87078e55-dd16-401e-ba62-d3663913cbfc){card-appearance="inline"}
    (random guy talking)

2.  [https://share.myjosh.in/content/96a2c3bb-b969-4bdc-8c62-aa26ecf1f3cd](https://share.myjosh.in/content/96a2c3bb-b969-4bdc-8c62-aa26ecf1f3cd){card-appearance="inline"}
      (random guy talking)

3.  [https://share.myjosh.in/content/e953f3a1-7353-406d-8877-42de0411580f](https://share.myjosh.in/content/e953f3a1-7353-406d-8877-42de0411580f){card-appearance="inline"}
      (random guy talking)

4.  [https://share.myjosh.in/content/c88965e4-7c34-462f-872f-21f0d7949bf3](https://share.myjosh.in/content/c88965e4-7c34-462f-872f-21f0d7949bf3){card-appearance="inline"}
      (random guy talking)

5.  [https://share.myjosh.in/content/c22b734d-6add-4474-81cc-672a6f9ef7e7](https://share.myjosh.in/content/c22b734d-6add-4474-81cc-672a6f9ef7e7){card-appearance="inline"}
    (first person shooting game)

6.  [https://share.myjosh.in/content/d56b7f0e-40be-4e61-bd99-74c4178cb055](https://share.myjosh.in/content/d56b7f0e-40be-4e61-bd99-74c4178cb055){card-appearance="inline"}
      (random guy talking)

7.  <https://share.myjosh.in/content/52f594e5-de2c-47a2-b1aa-8ce3b56ae170>
      (random guy talking)

8.  [https://share.myjosh.in/content/09d95298-8949-4652-82f9-0293c49f3f62](https://share.myjosh.in/content/09d95298-8949-4652-82f9-0293c49f3f62){card-appearance="inline"}
      (random guy talking)

9.  [https://share.myjosh.in/content/19ab894d-9adb-4f0a-9ea5-04f9e7ce4312](https://share.myjosh.in/content/19ab894d-9adb-4f0a-9ea5-04f9e7ce4312){card-appearance="inline"}
      (random guy talking)

10. [https://share.myjosh.in/content/89c7bfc7-d767-4798-b3a5-c10516493e9a](https://share.myjosh.in/content/89c7bfc7-d767-4798-b3a5-c10516493e9a){card-appearance="inline"}
    (ambedkar\'s photo)

**And below are the videos predicted least skippable. (1 = least
skippable)**

1.  [https://share.myjosh.in/content/85fbafa6-251a-4d64-80d4-b1a24e430a43](https://share.myjosh.in/content/85fbafa6-251a-4d64-80d4-b1a24e430a43){card-appearance="inline"}
    (stage performance, woman, not nsfw)

2.  [https://share.myjosh.in/content/3ceaec2d-7edb-4d5e-bbcc-261f337ac923](https://share.myjosh.in/content/3ceaec2d-7edb-4d5e-bbcc-261f337ac923){card-appearance="inline"}
    (big crane, engineering)

3.  [https://share.myjosh.in/content/8ce4aaca-19c5-4137-8a7b-0207ec5c28da](https://share.myjosh.in/content/8ce4aaca-19c5-4137-8a7b-0207ec5c28da){card-appearance="inline"}
    (has a story line)

4.  [https://share.myjosh.in/content/8e34b321-4ab8-484f-b116-1c0e7230b80f](https://share.myjosh.in/content/8e34b321-4ab8-484f-b116-1c0e7230b80f){card-appearance="inline"}
    (newborn kid and mom)

5.  [https://share.myjosh.in/content/2e22db9a-da80-4656-99b1-8f14a674d4a8](https://share.myjosh.in/content/2e22db9a-da80-4656-99b1-8f14a674d4a8){card-appearance="inline"}
    (funny, joke)

6.  [https://share.myjosh.in/content/636967e0-4ea7-4d62-9f94-a41c895e3b32](https://share.myjosh.in/content/636967e0-4ea7-4d62-9f94-a41c895e3b32){card-appearance="inline"}
    (dance, cat, joke)

7.  [https://share.myjosh.in/content/b13a847c-bd6a-4b72-b56a-04b8d1328437](https://share.myjosh.in/content/b13a847c-bd6a-4b72-b56a-04b8d1328437){card-appearance="inline"}
    (traffic, engineering)

8.  [https://share.myjosh.in/content/10491d3e-101c-4589-8886-a2e6baa430ee](https://share.myjosh.in/content/10491d3e-101c-4589-8886-a2e6baa430ee){card-appearance="inline"}
    (woman dancing, not nsfw)

9.  [https://share.myjosh.in/content/6afa29a2-ee95-489a-b0ac-079e9183625e](https://share.myjosh.in/content/6afa29a2-ee95-489a-b0ac-079e9183625e){card-appearance="inline"}
    (woman, slightly nsfw)

10. [https://share.myjosh.in/content/5a905205-882f-4942-93d8-c8e28eefb148](https://share.myjosh.in/content/5a905205-882f-4942-93d8-c8e28eefb148){card-appearance="inline"}
    (animals)
