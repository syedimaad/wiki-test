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

Experiments

  ------------------- ---------------- ----------------------------- -------------- ------------
  **Experiment No**   **event type**   **Train DATA**                **VAL DATA**   **Status**
  1                   played (p90)     1 Nov - 7 Nov 2022 (7 days)   8 Nov 2022     Completed
  2                   played (p90)     3 Nov - 9 Nov 2022 (7 days)   10 Nov 2022    Completed
  ------------------- ---------------- ----------------------------- -------------- ------------

Results

  ------------------- --------- ----------------- --------- --------- ------------ ------------- -------------- --------------- --------------- ---------------- ----------------- ------------------- --------------------
  **Experiment No**   **auc**   **avg_prec@10**   **map**   **mrr**   **ndcg@5**   **ndcg@10**   **recall@5**   **recall@10**   **recall@50**   **recall@100**   **recall@gt_5**   **recall@gt_100**   **recall@all_pos**
  1                   0.71      0.68              0.69      0.21      0.73         0.75          0.74           0.76            0.81            0.85             0.624             0.627               0.624
  2                   0.70      0.67              0.68      0.21      0.72         0.74          0.73           0.75            0.81            0.86             0.612             0.614               0.612
  ------------------- --------- ----------------- --------- --------- ------------ ------------- -------------- --------------- --------------- ---------------- ----------------- ------------------- --------------------
