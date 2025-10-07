\- to describe the problem and detailed implementation here.\

Tasks:

How to?

1.  Deduplicate across days. - is there an identifier from S2S?

2.  Determine the clustering strategy

    1.  best clustering Algo

    2.  Number of clusters

    3.  the compute and time required for the clustering to run

    4.  data size / variance required for good performant clustering.

    5.  Metrics we can use:

        1.  Silhouette scores might not work as there would not have a
            lot of differential.

        2.  Pseudo labels to advertisers - construct a metric.

3.  Store the created clusters and map to new images.

4.  Use the stored clusters

    1.  Enrich user profile

        1.  AdLearning models

        2.  Demographics

    2.  Analytics

        1.  which cluster has higher CTR.

        2.  which clusters have higher volume of images

            1.  Response volume

            2.  Impression volume

        3.  is it possible to tag clusters using the text / landing
            pages

5.  Accommodate/ Redo the above changes when we add the textual data?

Todo:

1.  Clustering Strategy Determination.

    1.  Determine the deduplication key

        1.  What happens if we do have duplicates?

        2.  Banner meta store contains hash based bannerIds for network
            banners which can be used for deduplication across days.

            Stats -

            Avg. DAU Banner Ids - 1.5M

            MAU Banner Ids - 18.4M

            Deduped MAU Banner Ids - 11.4M

            Current embedding data is available for 11 days -

            Total Banner embeddings - 16.5M

            Deduped Banner embeddings - 8.4M

            This unique embedding dataset can be used as a starting
            point for cluster testing.

    2.  Finalize (one or more) metric(s) to be used for evaluating
        clustering algos.

        1.  Clustering (10 banners example) -

            1.  Get cluster sizes and values

            2.  Predicted (Assuming we get banner ids within clusters
                and have external advertiser labelling) -\
                CID1 - \[BID1: ajio, BID2: ajio, BID3: nykaa, BID4:
                nykaa\],\
                CID2 - \[BID5: nykaa, BID6: nykaa, BID7: nykaa, BID8:
                1mg\],\
                CID3 - \[BID9: ajio, BID10: 1mg\]

            3.  Actual -\
                nykaa - 5, ajio - 3, 1mg - 2

            4.  Table (Adv. x clusters) -\
                Advertiser \| CID \| Count \| Center nykaa \| 1 \| 2 \|
                (1,8) nykaa \| 2 \| 3 \| (4,4) nykaa \| 3 \| 0 \|
                (-2,12) ajio \| 1 \| 2 \| (1,8) ajio \| 2 \| 0 \| (4,4)
                ajio \| 3 \| 1 \| (-2,12) 1mg \| 1 \| 0 \| (1,8) 1mg \|
                2 \| 1 \| (4,4) 1mg \| 3 \| 1 \| (-2,12)

            5.  Idea 1 -\
                Recall(nykaa) = Max(nykaa.count)/nykaa.actuals\
                = 3/5, if CID3 also has 1 nykaa - 3/6\
                Best case (5,0,0) - 5/5, Worst case (2,2,1) - 2/5\
                aggr - Sum(Max(adv.count)) / total_values = (3 + 2 + 1)
                = 6/10,\
                if CID3 also has 1 nykaa, aggr = 6/11\

                Idea 2 -\
                Heuristic1(nykaa) = Max(nykaa.count) /
                (Sum(nykaa.cluster_count)+1 (Except max) \*
                1/nykaa.actuals\
                =\> 3/((2 + 0) + 1) \* 1/5 = 3/15 , if CID3 also has 1
                nykaa - 3/((2 + 1) + 1) \* 1/6 = 3/24\
                Best case - 5/5, Worst case - 2/20\
                aggr - Sum(Max(adv.count) / (Sum(adv.cluster_count)+1
                (Except max)) / total_values\
                = (3/3 + 2/2 + 1/2) / 10 = 5/20,\
                if CID3 also has 1 nykaa, aggr = (3/4 + 2/2 + 1/2) / 11
                = 9/44\

                Idea 3 -\
                Heuristic2(nykaa) = Max(nykaa.count) /
                (Product(nykaa.cluster_count+1) (Except max) \*
                1/nykaa.actuals\
                =\> 3/((2+1) \* (0+1)) \* 1/5 = 3/20 , if CID3 also has
                1 nykaa - 3/((2+1) \* (1+1)) \* 1/6 = 3/30\
                Best case - 5/5, Worst case - 2/30\
                aggr = Sum(Max(nykaa.count) /
                (Product(nykaa.cluster_count+1) (Except max)) /
                total_values\
                = (3/3 + 2/2 + 1/2) / 10 = 5/20,\
                if CID3 also has 1 nykaa, aggr = (3/6 + 2/2 + 1/2) / 11
                = 4/22\
                \
                \
                (Aggregate is weighted mean of the adv.. Since their
                total actuals cancel each other out in the formula, we
                finally get sum of respective adv. values / total)\
                \
                Idea 4 -\
                nykaa.center = (4,6)\
                Heuristic3(nykaa) =
                WeightedAvg(nykaa.peak_cluster_center -
                nykaa.rest_cluster_centers)\
                =\> ((Dist(CID2, CID1) \*
                ((nykaa.this_cluster_count+1)/nykaa.total_cluster_count) +
                (Dist(CID2, CID3) \*
                ((nykaa.this_cluster_count+1)/nykaa.total_cluster_count))
                / 2 = (5\**3/5 + 10\**1/5) / 2 = 5/2\
                aggr = Sum(WeightedAvg(adv.peak_cluster_center -
                adv.rest_cluster_centers)) / total_values\
                = (5/2 + 15/3 + 15/2) / 10 = 1.5\
                \
                Detailed example -\
                Recall:\
                Clustering 1 -\
                adv1 10,2,2,2,2,2 = 10/20 = 0.5\
                adv2 5,1,1,1,0,0 = 5/8 = 0.625\
                adv3 12,3,3,3,3,0 = 12/24 = 0.5\
                aggr = (10/20 + 5/8 + 12/24) / 52 = **0.0312**

                Clustering 2 -\
                adv1 8,4,4,4,0,0 = 8/20 = 0.4\
                adv2 3,3,2,0,0,0 = 3/8 = 0.375\
                adv3 9,6,6,3,0,0 = 9/24 = 0.375\
                aggr = (8/20 + 3/8 + 9/24) / 52 = **0.0221**\
                \
                Heuristic1:\
                Clustering 1 -\
                adv1 10,2,2,2,2,2 = 10/11 \* 1/20 = 0.0455\
                adv2 5,1,1,1,0,0 = 5/4 \* 1/8 = 0.1562\
                adv3 12,3,3,3,3,0 = 12/13 \* 1/24 = 0.0385\
                aggr = (10/11 + 5/4 \* 12/13) / 52 = **0.0397**

                Clustering 2 -\
                adv1 8,4,4,4,0,0 = 8/13 \* 1/20 = 0.0308\
                adv2 3,3,2,0,0,0 = 3/6 \* 1/8 = 0.0625\
                adv3 9,6,6,3,0,0 = 9/16 \* 1/24 = 0.0234\
                aggr = (8/13 + 3/6 + 9/16) / 52 = **0.0323**\
                \
                Heuristic2:\
                Clustering 1 -\
                adv1 10,2,2,2,2,2 = 10/243 \* 1/20 = 0.0021\
                adv2 5,1,1,1,0,0 = 5/8 \* 1/8 = 0.0781\
                adv3 12,3,3,3,3,0 = 12/256 \* 1/24 = 0.002\
                aggr = (10/243 + 5/8 \* 12/256) / 52 = **0.0014**

                Clustering 2 -\
                adv1 8,4,4,4,0,0 = 8/125 \* 1/20 = 0.0032\
                adv2 3,3,2,0,0,0 = 3/12 \* 1/8 = 0.0312\
                adv3 9,6,6,3,0,0 = 9/196 \* 1/24 = 0.0019\
                aggr = (8/125 + 3/12 + 9/196) / 52 = **0.0069**\

    3.  Research clustering algos. (1 day)

    4.  Define strategies of clustering (1.5 days)

2.  Train and evaluate clustering strategies

    1.  Generate train/test split on the available data (sampled) (1.5
        days)

    2.  Train the model and eval all the strategies. Hopefully, we will
        have a clear winner. (2 days)

    3.  Final Train the model and save it. (As much data as possible) -
        only memory and compute bound. (1 day)

3.  Inference

    1.  A batch prediction service - for determining cluster of new
        incoming images.

        1.  Storage at the per banner level.

        2.  Should we use a GCS bucket or something like that?

4.  Utilising stored cluster per banner

    1.  User Aggregation

    2.  Kudu Data aggregation

Brainstorm:

You have identified 1 clusterid as central to the advertiser → by
max(nykaa_count)

for each advertiser :

- identify the best cluster for this advertiser. i.e peak cluster

- find mis-clustered ads.

- how far away are the mis-clustered ads from the best cluster?

  - distance between cluster center and misclassified point.

- Sum or average this column - average distance of mis-clustering

Meeting 18/05

1.  Choose the dataset.

2.  k = \[5, 10 ,15\]

3.  for a given k

    1.  Train a clustering model

    2.  Predict on the entire data.

    3.  ~~Evaluate~~

    4.  EDA on the predictions

    5.  Process the predicted data - and map the cluster_ids to user
        data

        1.  Should support

            1.  Req level mapping

            2.  Imp level mapping

            3.  Click Level Mapping

        2.  Simplest formulation is counts of clusters.

    6.  EDA on this user data.

    7.  Experiment.scala with this user data.

Iter 1: k == 5 , only req level mapping → added 5 features. → even if no
good results. we should implement at least till Iter 3.

Iter 2: k == 5 , req,imp, click level mapping → added 15 features.

Iter 3: k == 10, req,imp, click level mapping → added 30 features.

### Final Conclusions -

- Steps taken to create cluster user features from banner images and get
  experimental metrics -

  1.  [Download network banner
      images](https://gitlab.dailyhunt.in/nh-ads-platform/networkintelligence/blob/image_embeddings/src/image/image_downloader.py)

  2.  [Generate image embeddings from banner
      images](https://gitlab.dailyhunt.in/nh-ads-platform/networkintelligence/blob/image_embeddings/src/image/embedding_generator.py)
      (1792 features per image for efficientnet)

  3.  (Optional) [Compress embedding features via
      PCA](http://perf.ads.jupyter2-n3.dailyhunt.in/groot/edit/prakhar/image_emb_pca.py)
      (tested with features compressed from 1792 to 16)

  4.  Use
      [K-means](https://spark.apache.org/docs/latest/ml-clustering.html)
      on N days of embedding features ([tested with 15 and 20 days
      data](http://perf.ads.jupyter2-n3.dailyhunt.in/groot/edit/prakhar/image_emb_kmeans_final.py),
      K=10) to create trained cluster model

  5.  [Generate cluster
      predictions](http://perf.ads.jupyter2-n3.dailyhunt.in/groot/edit/prakhar/image_emb_kmeans_pred.py)
      for N days - each banner now belongs to a cluster.

  6.  [Aggregate banner cluster data on the basis of
      users](http://perf.ads.jupyter2-n3.dailyhunt.in/groot/notebooks/prakhar/user_cluster_aggr.ipynb)
      to create user cluster feature parquet

  7.  [Run experiments on apps/campaigns to check offline
      metrics](https://gitlab.dailyhunt.in/nh-ads-platform/AdLearning/blob/master/scripts/runFeatureExperiment.sh)

- Results -

  - Clustering techniques explored ([see
    here](https://spark.apache.org/docs/latest/ml-clustering.html)) -

    - K-means (K-means++) - gave the best standard output (based on
      silhouette score (SS))

    - LDA - intended for word document clustering

    - Bisecting K-means - irregular SS, often going in the negative

    - GMM/PIC - did not have a predict call available in the library

  - Heuristics explored (see the document above for details) - Most
    custom heuristics failed to capture both the difference in K values
    and the information from intrinsic data. SS proved to be most
    reliable method of comparison

    - Recall based

    - Sum based

    - Product based

    - Cluster center weighted average based

    - Silhouette score (SS)

  - [Experiment
    metrics](https://docs.google.com/spreadsheets/d/1MthiRAb3KMkq7Fs5CPKvbpnQiwxICnv9qa0okiYCb-o/edit?usp=sharing)
    and conclusions -

    - Experiments conducted with

      - Efficientnet embeddings

      - 15 days of clustering data

      - K-means

      - K = 10

        - Resulted in a very minute bump in RIG and rank scores. Further
          analysis on campaign store data revealed that the density of
          the data was good enough to be impactful, but the features did
          not give a good yield.

      - PCA compression prior to clustering the data (after efficientnet
        embeddings) also resulted in a similar output

  - Future possibilities -

    - A few networks are able to target high value clients for enhanced
      CTR/CVRs. Extracting features from banners might work better with
      contextual processing along with the banner descriptions. Though
      given that different banners could have the same descriptions,
      this might be challenging.

    - A pre-bucketing/clustering of banners before doing the actual
      clustering for better initialization of ML models could also be
      explored.
