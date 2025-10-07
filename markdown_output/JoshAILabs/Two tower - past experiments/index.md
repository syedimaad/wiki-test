Experiments tracker:
[https://docs.google.com/spreadsheets/d/1ocGmEoYzV7OD0U6R3AQ_UXWKb91FejyNG947ZIyrn8U/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1ocGmEoYzV7OD0U6R3AQ_UXWKb91FejyNG947ZIyrn8U/edit?usp=sharing){card-appearance="inline"}

### Base Two Tower with Dedup Embeds

1.  Client Filter Criteria

    - min 4 interactions

    - max 2000 interactions (for 7 days, 2x for 14 days) (99.9
      percentile)

    - min 1 positive interaction

    - min 1 neg interaction

2.  Item Filter Criteria

    - min 3 interactions

3.  Positive Label Criteria

    - Like or Share or fraction_watch \> 0.8

4.  Sample Weight

    - None

5.  Features added

    - User tower

      - None

6.  Item tower:

    - dedup_embeddings (pca 128 components)

7.  Features removed

    - User tower

      - user_handset_maker

    - Item tower

      - None

8.  Positive : Negative Ratio **\~ 7 : 3**

9.  Model Architecture:
    [here](http://10.12.4.73:8888/view/dnn-recommendation/two_tower_model/model_analysis/like_share_view_all/dedup_item_without_sample_wt/tt_model.png)

+----------------------------------+--------------+
| **Train DATA**                   | **VAL DATA** |
+----------------------------------+--------------+
| 15 days                          | 5th July     |
|                                  |              |
| (20th June \~ 4th July)          |              |
|                                  |              |
| (30% sample of 3b filtered data) |              |
+----------------------------------+--------------+

Metrics and Comments

  --------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------ ------------------------------------------------------------------------------------- --------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------- ----------------- ---------------------------------------------------
  [**[AUC]{.underline}**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_auc_score.html)   [**[NDCG@5]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py)   [**[NDCG@10]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py)   [**[MRR]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py)   [**[MAP]{.underline}**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.average_precision_score.html)   **CUST-MAP@10**   **Comments**
  0.668                                                                                                           0.762                                                                                0.781                                                                                 0.268                                                                             0.736                                                                                                                     0.685             No clusters based on Context. Visually Very Heavy
  --------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------ ------------------------------------------------------------------------------------- --------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------- ----------------- ---------------------------------------------------

### Base Two Tower with Dedup Embeds with Sample weight

1.  Client Filter Criteria

    - min 4 interactions

    - max 2000 interactions (for 7 days, 2x for 14 days) (99.9
      percentile)

    - min 1 positive interaction

    - min 1 neg interaction

2.  Item Filter Criteria

    - min 3 interactions

3.  Positive Label Criteria

    - Like or Share or fraction_watch \> 0.8

4.  Sample Weight

    - fraction_watched \> 0.8: 1.2

    - Liked: 1.5

    - Shared: 2.0

    - Any of above 2: 2.5

    - All of above: 3

    - Neg interaction: 1.0

5.  Features added

    - User tower

      - None

6.  Item tower

    - dedup_embeddings (pca 128 components)

7.  Features removed

    - User tower

      - user_handset_maker

    - Item tower

      - None

8.  Positive : Negative Ratio

    1.  7 : 3

9.  Model Architecture:
    [here](http://10.12.4.73:8888/view/dnn-recommendation/two_tower_model/model_analysis/like_share_view_all/dedup_item_without_sample_wt/tt_model.png)

+----------------------------------+--------------+
| **Train DATA**                   | **VAL DATA** |
+----------------------------------+--------------+
| 15 days                          | 5th July     |
|                                  |              |
| (20th June \~ 4th July)          |              |
|                                  |              |
| (30% sample of 3b filtered data) |              |
+----------------------------------+--------------+

Metrics and Comments

+---------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------+--------------+
| [**[AUC]{.underline}**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_auc_score.html) | [**[NDCG@5]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py) | [**[NDCG@10]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py) | [**[MRR]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py) | [**[MAP]{.underline}**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.average_precision_score.html) | **CUST-MAP@10** | **Comments** |
+---------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------+--------------+
| 0.667                                                                                                         | 0.762                                                                              | 0.78                                                                                | 0.268                                                                           | 0.736                                                                                                                   | 0.685           | No clusters  |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | based on     |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | Context,     |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 |              |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | Visually     |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | Very Heavy   |
+---------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------+--------------+

### Two Tower with Simclr Embed and User History

History Collection

- Pos History Criteria

  - last 100 items watched by user with label 1

- Neg Hist Criteria

  - last 100 items watched by the user with label 0 and time_spent \<
    avg_timespent by all users for the same item

Data Preparation

1.  Client Filter Criteria

    - min 4 interactions

    - max 2000 interactions (for 7 days, 2x for 14 days) (99.9
      percentile)

    - min 1 positive interaction

    - min 1 neg interaction

2.  Item Filter Criteria

    - min 3 interactions

3.  Positive Label Criteria

    - fraction_watch \> 0.9

4.  Sample Weight

    - Positive Interaction: sqrt(time_spent), capped at 8.0

5.  Features added

    - User tower

      - pos-mean-hist-emb (simclr)

      - neg-mean-hist-emb (simclr)

    - Item tower

      - simclr_embeddings (pca 128 components)

6.  Features removed

    - User tower

      - None

    - Item tower

      - Item_id

      - creator_id

7.  Positive : Negative Ratio

    - 5 : 5

8.  Model Architecture:
    [here](http://10.12.4.73:8888/view/dnn-recommendation/two_tower_model/model_analysis/like_share_view_all/with_simclr_hist_emb_without_creator/tt_model.png)

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

+---------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------+--------------+
| [**[AUC]{.underline}**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_auc_score.html) | [**[NDCG@5]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py) | [**[NDCG@10]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py) | [**[MRR]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py) | [**[MAP]{.underline}**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.average_precision_score.html) | **CUST-MAP@10** | **Comments** |
+---------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------+--------------+
| 0.661                                                                                                         | 0.69                                                                               | 0.721                                                                               | 0.221                                                                           | 0.667                                                                                                                   | 0.631           | Rare         |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | clusters     |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | based on     |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | common       |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | context with |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | visually     |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | similar      |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | content      |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 |              |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | User getting |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | fix set of   |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | items        |
+---------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------+--------------+

### Two Tower with Dedup Embed and User History

1.  Client Filter Criteria

    - min 4 interactions

    - max 2000 interactions (for 7 days, 2x for 14 days) (99.9
      percentile)

    - min 1 positive interaction

    - min 1 neg interaction

2.  Item Filter Criteria

    - min 3 interactions

3.  Positive Label Criteria

    - fraction_watch \> 0.9

4.  Sample Weight

    - Positive Interaction: sqrt(time_spent), capped at 8.0

5.  Features added

    - User tower

      - pos-mean-hist-emb (dedup)

      - neg-mean-hist-emb (dedup)

    - Item tower

      - dedup_embeddings (pca 128 components)

6.  Features removed

    - User tower

      - None

    - Item tower

      - Item_id

      - creator_id

7.  Positive : Negative Ratio \~ 5 : 5

8.  Model Architecture:
    [here](http://10.12.4.73:8888/view/dnn-recommendation/two_tower_model/model_analysis/like_share_view_all/with_dedup_hist_embd_without_creator/tt_model.png)

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

+---------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------+--------------+
| [**[AUC]{.underline}**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_auc_score.html) | [**[NDCG@5]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py) | [**[NDCG@10]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py) | [**[MRR]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py) | [**[MAP]{.underline}**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.average_precision_score.html) | **CUST-MAP@10** | **Comments** |
+---------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------+--------------+
| 0.659                                                                                                         | 0.687                                                                              | 0.718                                                                               | 0.221                                                                           | 0.665                                                                                                                   | 0.628           | Rare         |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | clusters     |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | based on     |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | common       |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | context but  |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | still        |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | visually     |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | similar      |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | content      |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 |              |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | User getting |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | fix set of   |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | items        |
+---------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------+--------------+

### Two Tower with Simclr Embed, User History and Id features

1.  Client Filter Criteria

    1.  min 4 interactions

    2.  max 2000 interactions (for 7 days, 2x for 14 days) (99.9
        percentile)

    3.  min 1 positive interaction

    4.  min 1 neg interaction

2.  Item Filter Criteria

    1.  min 3 interactions

3.  Positive Label Criteria

    1.  fraction_watch \> 0.9

4.  Sample Weight

    1.  Positive Interaction: sqrt(time_spent), capped at 8.0

5.  Features added

    - User tower:

      - pos-mean-hist-emb (simclr)

      - neg-mean-hist-emb (simclr)

    - Item tower:

      - simclr_embeddings (pca 128 components)

6.  Features removed

    - User tower:

      - None

    - Item tower:

      - None

7.  Positive : Negative Ratio

    - 5 : 5

8.  Model Architecture:
    [here](http://10.12.4.73:8888/view/dnn-recommendation/two_tower_model/model_analysis/like_share_view_all/with_simclr_hist_emb_with_creator/tt_model.png)

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

+---------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------+--------------+
| [**[AUC]{.underline}**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_auc_score.html) | [**[NDCG@5]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py) | [**[NDCG@10]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py) | [**[MRR]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py) | [**[MAP]{.underline}**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.average_precision_score.html) | **CUST-MAP@10** | **Comments** |
+---------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------+--------------+
| 0.665                                                                                                         | 0.696                                                                              | 0.725                                                                               | 0.223                                                                           | 0.67                                                                                                                    | 0.637           | Some         |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | clusters     |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | based on     |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | common       |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | context and  |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | creators     |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | with         |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | visually     |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | similar      |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | content      |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 |              |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | User getting |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | fix set of   |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | items        |
+---------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------+--------------+

### Two Tower with Dedup Embed, User History and Id features

1.  Client Filter Criteria

    - min 4 interactions

    - max 2000 interactions (for 7 days, 2x for 14 days) (99.9
      percentile)

    - min 1 positive interaction

    - min 1 neg interaction

2.  Item Filter Criteria

    - min 3 interactions

3.  Positive Label Criteria

    - fraction_watch \> 0.9

4.  Sample Weight

    - Positive Interaction: sqrt(time_spent), capped at 8.0

5.  Features added

    - User tower

      - pos-mean-hist-emb (dedup)

      - neg-mean-hist-emb (dedup)

    - Item tower

      - dedup_embeddings (pca 128 components)

6.  Features removed

    - User tower

      - None

    - Item tower

      - None

7.  Positive : Negative Ratio

    - 5 : 5

8.  Model Architecture:
    [here](http://10.12.4.73:8888/view/dnn-recommendation/two_tower_model/model_analysis/like_share_view_all/with_dedup_hist_embd_with_creator/tt_model.png)

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

+---------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------+--------------+
| [**[AUC]{.underline}**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_auc_score.html) | [**[NDCG@5]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py) | [**[NDCG@10]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py) | [**[MRR]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py) | [**[MAP]{.underline}**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.average_precision_score.html) | **CUST-MAP@10** | **Comments** |
+---------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------+--------------+
| 0.665                                                                                                         | 0.697                                                                              | 0.726                                                                               | 0.222                                                                           | 0.67                                                                                                                    | 0.637           | Some         |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | clusters     |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | based on     |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | common       |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | context and  |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | creators     |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | with         |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | visually     |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | similar      |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | content      |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 |              |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | User getting |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | fix set of   |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | items        |
+---------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------+--------------+

### Two Tower with Simclr Embed, concatenated user history and creator_id

History Collection

- Pos Hist Criteria:

  - last **5** items watched by user with label 1

- Neg Hist Criteria:

  - last **5** items watched by the user with label 0 and time_spent \<
    avg_timespent by all users for the same item.

Data Preparation

1.  Client Filter Criteria

    - min 4 interactions

    - max 2000 interactions (for 7 days, 2x for 14 days) (99.9
      percentile)

    - min 1 positive interaction

    - min 1 neg interaction

2.  Item Filter Criteria

    - min 3 interactions

3.  Positive Label Criteria

    - fraction_watch \> 0.99 or user liked or user shared

4.  Sample Weight

    - None

5.  Features added

    - User tower

      - pos-hist-emb-concat (simclr) \[64 \* 5\]

      - neg-hist-emb-concat (simclr) \[64 \* 5\]

      - normaized_user_ctr_features (from recsys database)

      - normalized_user_timespent_features (from recsys database)

    - Item tower

      - simclr_embeddings (pca 64 components)

      - normalized_item_and_creator_ctr_features (from recsys database)

6.  Features removed

    - User tower

      - user_activity_profile_vector

    - Item tower:

    - Item_id

      - item_performance_features

      - creator_performance_features

7.  Positive : Negative Ratio \~ 4 : 6

8.  Model Architecture:
    [here](http://10.12.4.73:8888/view/dnn-recommendation/two_tower_model/model_analysis/like_share_view_all/perc_watch%3D99/with_simclr_item_5/tt_model.png)

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

  --------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------ ------------------------------------------------------------------------------------- --------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------- ----------------- --------------
  [**[AUC]{.underline}**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_auc_score.html)   [**[NDCG@5]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py)   [**[NDCG@10]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py)   [**[MRR]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py)   [**[MAP]{.underline}**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.average_precision_score.html)   **CUST-MAP@10**   **Comments**
  0.467                                                                                                           0.41                                                                                 0.471                                                                                 0.178                                                                             0.462                                                                                                                     0.363              
  --------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------ ------------------------------------------------------------------------------------- --------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------- ----------------- --------------

### Two Tower with Simclr Embed, user history distribution and creator_id

History Collection

- Pos Hist Criteria:

  - last **100** items watched by user with label 1

- Neg Hist Criteria:

  - last **100** items watched by the user with label 0 and time_spent
    \< avg_timespent by all users for the same item.

Data Preparation

1.  Client Filter Criteria

    - min 4 interactions

    - max 2000 interactions (for 7 days, 2x for 14 days) (99.9
      percentile)

    - min 1 positive interaction

    - min 1 neg interaction

2.  Item Filter Criteria

    - min 3 interactions

3.  Positive Label Criteria

    - fraction_watch \> 0.99 or user liked or user shared

4.  Sample Weight

    - None

5.  Features added

    - User tower

      - pos-hist-cluster-distribution (18 simclr clusters based on
        Kmeans)

      - neg-hist-cluster-distribution (18 simclr clusters based on
        Kmeans)

      - normaized_user_ctr_features (from recsys database)

      - normalized_user_timespent_features (from recsys database)

    - Item tower

      - simclr_embeddings (pca 64 components)

      - normalized_item_and_creator_ctr_features (from recsys database)

6.  Features removed

    - User tower

      - user_activity_profile_vector

    - Item tower

      - Item_id

      - item_performance_features

      - creator_performance_features

7.  Positive : Negative Ratio \~ 4 : 6

8.  Model Architecture:
    [here](http://10.12.4.73:8888/view/dnn-recommendation/two_tower_model/model_analysis/like_share_view_all/perc_watch%3D99/with_simclr_cluster_18/tt_model.png)

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

+---------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------+--------------+
| [**[AUC]{.underline}**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_auc_score.html) | [**[NDCG@5]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py) | [**[NDCG@10]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py) | [**[MRR]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py) | [**[MAP]{.underline}**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.average_precision_score.html) | **CUST-MAP@10** | **Comments** |
+---------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------+--------------+
| 0.741                                                                                                         | 0.725                                                                              | 0.746                                                                               | 0.263                                                                           | 0.684                                                                                                                   | 0.641           | Some         |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | clusters     |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | based on     |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | common       |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | context and  |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | creators     |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | with         |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | visually     |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | similar      |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | content      |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 |              |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | User getting |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | fix set of   |
|                                                                                                               |                                                                                    |                                                                                     |                                                                                 |                                                                                                                         |                 | items        |
+---------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------+--------------+

### Two Tower with Simclr Embed, user history distribution and creator_id, with Normalized two tower output embeddings

History Collection

- Pos Hist Criteria:

  - last 100 items watched by user with label 1

- Neg Hist Criteria:

  - last 100 items watched by the user with label 0 and time_spent \<
    avg_timespent by all users for the same item.

Data Preparation

1.  Client Filter Criteria

    - min 4 interactions

    - max 2000 interactions (for 7 days, 2x for 14 days) (99.9
      percentile)

    - min 1 positive interaction

    - min 1 neg interaction

2.  Item Filter Criteria

    - min 3 interactions

3.  Positive Label Criteria

    - fraction_watch \> 0.99 or user liked or user shared

4.  Sample Weight

    - None

5.  Features added

    - User tower

      - pos-hist-cluster-distribution (18 simclr clusters based on
        Kmeans)

      - neg-hist-cluster-distribution (18 simclr clusters based on
        Kmeans)

      - normaized_user_ctr_features (from recsys database)

      - normalized_user_timespent_features (from recsys database)

    - Item tower

      - simclr_embeddings (pca 64 components)

      - normalized_item_and_creator_ctr_features (from recsys database)

6.  Features removed

    - User tower

      - user_activity_profile_vector

    - Item tower

      - Item_id

      - item_performance_features

      - creator_performance_features

7.  Positive : Negative Ratio \~ 4 : 6

8.  Model Architecture:
    [here](http://10.12.4.73:8888/view/dnn-recommendation/two_tower_model/model_analysis/like_share_view_all/perc_watch%3D99/with_simclr_cluster_18_normalized/tt_model.png)
    \[Dot Product with L2-Normalization\]

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

  --------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------ ------------------------------------------------------------------------------------- --------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------- ----------------- --------------------------------------------------------------
  [**[AUC]{.underline}**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_auc_score.html)   [**[NDCG@5]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py)   [**[NDCG@10]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py)   [**[MRR]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py)   [**[MAP]{.underline}**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.average_precision_score.html)   **CUST-MAP@10**   **Comments**
  0.723                                                                                                           0.712                                                                                0.735                                                                                 0.26                                                                              0.674                                                                                                                     0.63              User getting some variety of items, but less item similarity
  --------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------ ------------------------------------------------------------------------------------- --------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------- ----------------- --------------------------------------------------------------

### Two Tower with Simclr Embed, user history distribution and creator_id, with Batch Normalized two tower output embeddings

History Collection

- Pos Hist Criteria

  - last 100 items watched by user with label 1

- Neg Hist Criteria

  - last 100 items watched by the user with label 0 and time_spent \<
    avg_timespent by all users for the same item.

Data Preparation

1.  Client Filter Criteria

    - min 4 interactions

    - max 2000 interactions (for 7 days, 2x for 14 days) (99.9
      percentile)

    - min 1 positive interaction

    - min 1 neg interaction

2.  Item Filter Criteria

    - min 3 interactions

3.  Positive Label Criteria

    - fraction_watch \> 0.99 or user liked or user shared

4.  Sample Weight

    1.  None

5.  Features added

    - User tower

      - pos-hist-cluster-distribution (18 simclr clusters based on
        Kmeans)

      - neg-hist-cluster-distribution (18 simclr clusters based on
        Kmeans)

      - normaized_user_ctr_features (from recsys database)

      - normalized_user_timespent_features (from recsys database)

    - Item tower

      - simclr_embeddings (pca 64 components)

      - normalized_item_and_creator_ctr_features (from recsys database)

6.  Features removed

    - User tower

      - user_activity_profile_vector

    - Item tower

      - Item_id

      - item_performance_features

      - creator_performance_features

7.  Positive : Negative Ratio \~ 4 : 6

8.  Model Architecture:
    [here](http://10.12.4.73:8888/view/dnn-recommendation/two_tower_model/model_analysis/like_share_view_all/perc_watch%3D99/with_simclr_cluster_18_norm_vec/tt_model.png)
    \[Batch Feature Normalization\]

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

  --------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------ ------------------------------------------------------------------------------------- --------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------- ----------------- --------------------------------------------------------------------------
  [**[AUC]{.underline}**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_auc_score.html)   [**[NDCG@5]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py)   [**[NDCG@10]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py)   [**[MRR]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py)   [**[MAP]{.underline}**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.average_precision_score.html)   **CUST-MAP@10**   **Comments**
  0.738                                                                                                           0.722                                                                                0.744                                                                                 0.262                                                                             0.682                                                                                                                     0.638             Neither Item Similarity found nor high item coverage for user embeddings
  --------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------ ------------------------------------------------------------------------------------- --------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------- ----------------- --------------------------------------------------------------------------

### Two Tower with Simclr Embed, User History with Normalized Dot Product

1.  Client Filter Criteria

    - min 4 interactions

    - max 2000 interactions (for 7 days, 2x for 14 days) (99.9
      percentile)

    - min 1 positive interaction

    - min 1 neg interaction

2.  Item Filter Criteria

    - min 3 interactions

3.  Positive Label Criteria

    - fraction_watch \> 0.9

4.  Sample Weight

    - Positive Interaction: sqrt(time_spent), capped at 8.0

5.  Features added

    - User tower

      - pos-mean-hist-emb (simclr)

      - neg-mean-hist-emb (simclr)

    - Item tower

      - simclr_embeddings (pca 128 components)

6.  Features removed

    - User tower

      - None

    - Item tower

      - item_idx

7.  Positive : Negative Ratio \~ 5 : 5

8.  Model Architecture:
    [here](http://10.12.4.73:8888/view/dnn-recommendation/two_tower_model/model_analysis/like_share_view_all/with_simclr_hist_emb_with_creator/tt_model.png)

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

  --------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------ ------------------------------------------------------------------------------------- --------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------- ----------------- ------------------------------------------------------------------------
  [**[AUC]{.underline}**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_auc_score.html)   [**[NDCG@5]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py)   [**[NDCG@10]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py)   [**[MRR]{.underline}**](https://github.com/msnews/MIND/blob/master/evaluate.py)   [**[MAP]{.underline}**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.average_precision_score.html)   **CUST-MAP@10**   **Comments**
  0.615                                                                                                           0.598                                                                                0.645                                                                                 0.2                                                                               0.617                                                                                                                     0.551             User getting some variety of items in top 20, but less item similarity
  --------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------ ------------------------------------------------------------------------------------- --------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------- ----------------- ------------------------------------------------------------------------
