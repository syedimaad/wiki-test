17

+----------------------------------------------------------------------------------------------------------------+----------------------+----------------------+
| **Version Type**                                                                                               | **Meta Features**    | **Objectives**       |
+----------------------------------------------------------------------------------------------------------------+----------------------+----------------------+
| **Current Production**                                                                                                                                       |
+----------------------------------------------------------------------------------------------------------------+----------------------+----------------------+
| User Mean History with Blip Embeds (Hindi language)                                                            | UserTower +          | P90                  |
|                                                                                                                | Short-Term history\  |                      |
|                                                                                                                | ItemTower + Blip     |                      |
|                                                                                                                | (PCA 128)            |                      |
+----------------------------------------------------------------------------------------------------------------+----------------------+----------------------+
| **Future Roadmap**                                                                                                                                           |
+----------------------------------------------------------------------------------------------------------------+----------------------+----------------------+
| Language                                                                                                       | UserTower+           | P90 / Like / Share / |
|                                                                                                                | Short-term history   | Loop                 |
| (Regional languages: Kannada, Telugu, Tamil, Malayalam)                                                        | (100)\               |                      |
|                                                                                                                | ItemTower + Blip     |                      |
|                                                                                                                | (PCA 128)            |                      |
+----------------------------------------------------------------------------------------------------------------+----------------------+----------------------+
| Video + Audio Embeddings                                                                                       | UserTower+           | P90 / Like / Share / |
|                                                                                                                | Short-term history   | Loop                 |
|                                                                                                                | (100)\               |                      |
|                                                                                                                | ItemTower + Audio    |                      |
|                                                                                                                | (PCA 128) + Blip     |                      |
|                                                                                                                | (PCA 128)            |                      |
+----------------------------------------------------------------------------------------------------------------+----------------------+----------------------+
| Language                                                                                                       | UserTower+           | Like / Share / Loop  |
|                                                                                                                | Short-term history   | / P90                |
| (Regional languages: Kannada, Telugu, Tamil, Malayalam)                                                        | (100)\               |                      |
|                                                                                                                | ItemTower + Blip     |                      |
|                                                                                                                | (PCA 128) + Audio    |                      |
|                                                                                                                | (PCA 128)            |                      |
+----------------------------------------------------------------------------------------------------------------+----------------------+----------------------+
| Watch Time : Item                                                                                              | UserTower +          | Dynamic Watch Time   |
|                                                                                                                | Short-term history   |                      |
| (Video embeddings)                                                                                             | (100)\               |                      |
|                                                                                                                | ItemTower + Blip     |                      |
|                                                                                                                | (PCA 128)            |                      |
+----------------------------------------------------------------------------------------------------------------+----------------------+----------------------+
| Watch Time : User                                                                                              | UserTower +          | Dynamic Watch Time   |
|                                                                                                                | Short-term history   |                      |
| (Video embeddings)                                                                                             | (100)\               |                      |
|                                                                                                                | ItemTower + Blip     |                      |
|                                                                                                                | (PCA 128)            |                      |
+----------------------------------------------------------------------------------------------------------------+----------------------+----------------------+
| Blended embeddings                                                                                             | UserTower +          | Like / Share / Loop  |
|                                                                                                                | Short-term history   | / P90                |
|                                                                                                                | (100)\               |                      |
|                                                                                                                | ItemTower + Combined |                      |
|                                                                                                                | embeddings           |                      |
+----------------------------------------------------------------------------------------------------------------+----------------------+----------------------+
| Session based history                                                                                          | UserTower+ Session   | Like / Share / Loop  |
|                                                                                                                | history + Long-term  | / P90                |
|                                                                                                                | history\             |                      |
|                                                                                                                | ItemTower + Blip     |                      |
|                                                                                                                | (PCA 128) + Audio    |                      |
|                                                                                                                | (PCA 128)            |                      |
+----------------------------------------------------------------------------------------------------------------+----------------------+----------------------+
| **Past Experiments**                                                                                                                                         |
+----------------------------------------------------------------------------------------------------------------+----------------------+----------------------+
| [Base                                                                                                          | UserTower\           | all_events(p80) w/o  |
| Features](https://evp.atlassian.net/wiki/spaces/JoshAILabs/pages/200146945/Two+Tower+Meta+Based#Base-features) | ItemTower +          | sample_wt/\          |
| with pretrained Dedup Embeddings                                                                               | MobileNet (PCA 128)  | all events(p80) with |
|                                                                                                                |                      | sample_wt            |
+----------------------------------------------------------------------------------------------------------------+----------------------+----------------------+
| User Mean History with Dedup                                                                                   | UserTower +          | P90                  |
|                                                                                                                | Short-Term history\  |                      |
|                                                                                                                | ItemTower +          |                      |
|                                                                                                                | MobileNet (PCA 128)  |                      |
+----------------------------------------------------------------------------------------------------------------+----------------------+----------------------+
| User Mean History with SimClr                                                                                  | UserTower +          | P90                  |
|                                                                                                                | Short-Term history\  |                      |
|                                                                                                                | ItemTower + SimClr   |                      |
|                                                                                                                | (PCA 128)            |                      |
+----------------------------------------------------------------------------------------------------------------+----------------------+----------------------+
| Concat User History with SimClr                                                                                | UserTower +          | P99                  |
|                                                                                                                | Very-Short-Term      |                      |
|                                                                                                                | history\             |                      |
|                                                                                                                | ItemTower + SimClr   |                      |
|                                                                                                                | (PCA 128)            |                      |
+----------------------------------------------------------------------------------------------------------------+----------------------+----------------------+
| User History Distribution with SimClr                                                                          | UserTower +          | P99                  |
|                                                                                                                | Short-Term history\  |                      |
|                                                                                                                | ItemTower + SimClr   |                      |
|                                                                                                                | (PCA 128)            |                      |
+----------------------------------------------------------------------------------------------------------------+----------------------+----------------------+
| Normalization Expts in User History Distribution with SimClr                                                   | UserTower +          | P99 with and w/o     |
|                                                                                                                | Short-Term history\  | sample_wt            |
|                                                                                                                | ItemTower + SimClr   |                      |
|                                                                                                                | (PCA 128)            |                      |
+----------------------------------------------------------------------------------------------------------------+----------------------+----------------------+

#### Base features

- UserTower

  - day_of_week \[categorical\]

  - hour_of_day \[categorical\]

  - user_handset_maker \[categorical\]

  - user_time_performance_features \[dense_vector\] (ctr, depth,
    watch_time, num_items, pos_events)

  - user_depth_performance_features \[dense_vector\] (ctr, watch_time,
    num_items, pos_events)

- ItemTower

  - creator_id \[categorical\]

  - item_id \[categorical\]

  - item_age \[continuous\]

  - item_performance_features \[dense_vector\] (daywise (ctr, likes,
    shares, downloads)),

  - creator_performance_features \[dense_vector\] (daywise (ctr, likes,
    shares, downloads))

#### Label

- "1" : Positive Interaction

- "0" : Negative Interaction

*\*positive and Negative Interaction defined based on different data.*

#### Model loss function

[[[BinaryCrossentropy]{.underline}]{style="color: rgb(17,85,204);"}](https://www.tensorflow.org/api_docs/python/tf/keras/losses/BinaryCrossentropy)
with logits=True

#### Metrics

- AUC

- NDCG@5

- NDCG@10

- MRR

- MAP

- CUST-MAP@10

- Recall@5, Recall@10

### Two Tower with Blip Embed, User History

1.  Client Filter Criteria

    - min 4 interactions

    - max 2000 interactions (for 7 days) (99.9 percentile)

    - min 1 positive interaction

    - min 1 neg interaction

2.  Item Filter Criteria

    - min 3 interactions

3.  Positive Label Criteria

    - fraction_watch \> 0.9

4.  Sample Weight

    - None

5.  Features added

    - User tower

      - pos-mean-hist-emb (blip)

      - neg-mean-hist-emb (blip)

    - Item tower

      - blip_embeddings (pca 128 components)

6.  Features removed

    - User tower

      - None

    - Item tower

      - item_idx

7.  Positive-Negative Ratio \~ 5 : 5

+-------------------------------------+--------------+
| **Train DATA**                      | **VAL DATA** |
+-------------------------------------+--------------+
| 7 days                              | 27th June    |
|                                     |              |
| (20th June \~ 26th June)            |              |
|                                     |              |
| (40% sampled of 1.5b filtered data) |              |
+-------------------------------------+--------------+

Metrics and Comments

  ------------------------------------------------------------------------------------------------------------------------------------------------- ---------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------- --------------------------------------------------------------------------------------------------------------------------------
  [**[[AUC]{.underline}]{style="color: rgb(17,85,204);"}**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_auc_score.html)   [**[[NDCG@5]{.underline}]{style="color: rgb(17,85,204);"}**](https://github.com/msnews/MIND/blob/master/evaluate.py)   [**[[NDCG@10]{.underline}]{style="color: rgb(17,85,204);"}**](https://github.com/msnews/MIND/blob/master/evaluate.py)   [**[[MRR]{.underline}]{style="color: rgb(17,85,204);"}**](https://github.com/msnews/MIND/blob/master/evaluate.py)   [**[[MAP]{.underline}]{style="color: rgb(17,85,204);"}**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.average_precision_score.html)   **CUST-MAP@10**   **Comments**
  0.677                                                                                                                                             0.712                                                                                                                  0.738                                                                                                                   0.228                                                                                                               0.681                                                                                                                                                       0.649             User getting some variety of items in top 100 with cardinality of 10000 for 1000 random users, with good item-item similarity.
  ------------------------------------------------------------------------------------------------------------------------------------------------- ---------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------- --------------------------------------------------------------------------------------------------------------------------------

Recall Scores:

  ------------------ -------------- --------------- --------------- ----------------
  **Item-Filters**   **Recall@5**   **Recall@10**   **Recall@50**   **Recall@100**
  Unfiltered         72.55          75.28           81.52           85.37
  \< 3000 views      71.89          75.01           81.88           87.18
  \< 1000 views      72.17          75.03           82.95           87.99
  ------------------ -------------- --------------- --------------- ----------------
