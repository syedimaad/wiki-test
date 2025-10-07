Following are the various approaches we are working on for clustering
user level interests:

- [v2v-ppc](#v2v-pcc) deployedGreen

- [v2v-timespent](#v2v-timespent) deployedGreen

- [Long term history clusters using timespent](#lthm_timespent)
  DEPLOYEDYellow

- [Clustering using Neural Networks](#nn_clustering) PAUSEDYellow

### v2v-pcc : v2v-pcc

- Here we take positive and negative engagements, using hard definitions
  in the following manner-

  - Full watched (positive) → if pcc \>= 98%

  - Likes (positive) → if video is liked

  - Skips (negative) → if pcc \< 20%

- Following parameters are required

  - `num_full_watch , num_likes , num_skips` \-\-- for events

  - `watch_weight, like_weight, skip_weight`

  - `num_queries , window_size`

- Intializing `num_queries` to 15, i.e we form queries among most recent
  15 full watched item_ids and take a `window_size` of 30

- Weights are initialized in the following manner:

  - `watch_weight = 1.0, like_weight = 2.0 , skip_weight = -1.0`

- Watch2Watch -- matrix which stores pairwise similarity scores based on
  blip index, having dimension
  `[num_queries X (num_queries+window_size)]`

- Watch2Like - similarity score matrix of dimension
  `(num_queries X num_likes)`

- Watch2Skips - similarity score matrix of dimension
  `(num_queries X num_skips)`

- For each item in num_queries , we sum the scores from above matrices
  and multiply weights (like,share - 2.0 , full_watched - 1.5, skip -
  (-1.5)):

  - score\[i\] = np.sum(watch2watch\[i\],axis=1)\*watch_weight +
    np.sum(watch2like\[i\],axis=1)\*like_weight +
    np.sum(watch2skip\[i\],axis=1)\*skip_weight

Idea is to boost the queries which have similarity to user's liked,
shared and full watched items, and penalize if it is similar to skipped
items.

The queries are then sorted according to the scores and similar queries
are then clustered together based on blip similarity.

**Findings :** If a full_watched_video (considered as query) was similar
to user's skipped items, it's score was getting downvoted and the
algorithm would rank it lower in the final queries formed.

**Prod** : `v2v_recent_watch` used as candidate source arm based on
above logic

### v2v-timespent : v2v-timespent

The drawback of the above approach is that we are just taking queries
for items which were full-watched. But there are many clients, who
generally do not full watch the content, and have very less positive
engagement (soft actions).

So in this method, we use raw events as input with time_spent by the
client on respective item_ids.

- Following parameters are required

  - `num_raw_events, time_spent_list`

  - `min_similarity_threshold, min_clustering_threshold , p and q`

  - `num_queries` (initalized to 15)

- We supply 100-500 raw events as input to the function and get all
  their time_spents. Let it be N

- N X N matrix is created with pairwise similarity scores based on blip
  embedding

  - `Sim_score[i,j] = cosine_similarity(Ei,Ej)`

    where Ei and Ej are 32 dimensional blip embedding

  - To incorporate only similar items, we include only those scores
    which are \> 0.5 (`min_similarity_threshold`), otherwise we make the
    score as 0

- N X N matrix is created with aggregated time_spent scores based on
  following formula:

  - `Ts_Score[i,j] = (Ti)^p * (Tj)^q`

  - where i and j are any two item_ids , p and q are parameters (usually
    taken as 0.5)

- `Cluster_Score[i,j] = Ts_Score[i,j] * Sim_score[i,j]`

- Next we take the row wise sum to get the aggregated scores for each
  item.

  `np.sum(Cluster_score, axis=1)`

- We sort the scores, and take the first 15 or whatever was sent as
  num_queries parameter.

- Similar queries are then clustered together using following steps:

  - Create 15 X 15 matrix (`Sim_score_final`) involving cosine
    similarity scores of blip embeddings of those videos

    `IF Sim_score_final[i,j] > min_clustering_threshold THEN Cluster item j to item i`

The final clusters formed are the queries for the user.

**Findings :** Even a low pcc % on a relatively longer video with a
like/share event was getting good boost and was appearing among
prominent clusters.

### Long term history clusters using timespent: lthm_timespent

**Findings from dbscan algorithm :** The LTHM clusters which were
generated for client basis, were not distinct .. multiple clusters were
formed with same thematic content.

**Approach using timespent data:**

The objective is to replace the current LTHM logic (using DBSCAN) which
is failing to categorize items into n proper clusters.

The approach is same as v2v-timespent, but the input is all the positive
interactions (watch, like, share) in past 30/14 days for each client.

The important parameters required for the clustering logic are:

- `min_clustering_threshold`: the similarity threshold which groups the
  items into one clusters

- `min_cluster_size`: the minimum cluster size required for a cluster to
  be valid as a histpry cluster for a user.

- `min_centroid_clustering_threshold`: clustering threshold for grouping
  the centroids of the history clusters.

We consider all the videos as queries , i.e
`num_queries = total_item_ids`

**Observations** : Distinct clusters were formed, each having a
different theme

**Drawback :** For highly active clients .. (which have \~ 1000 positive
events within 30 days) , high no. of clusters were getting formed with
similar theme

**Resolution :** Another step was introduced, where we take the
centroids of the formed clusters, and cluster it using following steps:

- If C clusters were formed, we take C centroids and form a C X C matrix
  (`Centroids_sim_score`) with blip similarity score

- `IF Centroids_sim_score[i,j] > min_centroid_threshold THEN Cluster item j to item i`

### Clustering using Neural Networks: nn_clustering

The objective is to cluster items using neural networks. The approach is
to train a neural network based on the labels from lthm clusters (using
time spent), where we try to project d dimensional blip embeddings to c
dimensions, which will try to categorise the items into c clusters which
are uniform across all the clients.

\

- The dataset consists of at most 1000 positive interactions for each
  client along with the cluster ids predicted by lthm timespent.

- The input to the model are blip 32 dimension with targets as cluster
  ids, which are then modified to c dimesions (to capture c features) ,
  which is then passed through MLP and softmax.

- The loss function is as below

  (yiyj - pipj)\^2

Where yi, yj refers to the truth labels (cluster ids returned by lthm
timespent), and pi,pj refers to what the model predicts.

**Observations** : Distinct clusters are formed and some clusters were
better than clusters formed using lthm timespent.

**Drawback :** The network is failing to categorize categories which are
not popular (eg: anime).
