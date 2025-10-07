implemented kNN evaluation and noticed that recall numbers were very
low.

\-\-\-\-\--KNN Metrics\-\-\-\-\-- ┌─────┬─────────────┐ │ k │ Recall@k │
├─────┼─────────────┤ │ 1 │ 0.000314308 │ ├─────┼─────────────┤ │ 5 │
0.00141824 │ ├─────┼─────────────┤ │ 10 │ 0.00259898 │
├─────┼─────────────┤ │ 20 │ 0.00457565 │ ├─────┼─────────────┤ │ 100 │
0.0157888 │ ├─────┼─────────────┤ │ 200 │ 0.026093 │
└─────┴─────────────┘

Contrast this with in-batch metrics (batch size = 8192)

+\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--+\-\-\-\-\-\-\-\-\-\-\--+ \|
metric \| value \|
\|\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--+\-\-\-\-\-\-\-\-\-\-\--\| \|
val_hit_rate_at_1 \| 0.00668433 \| \| val_hit_rate_at_5 \| 0.0251992 \|
\| val_hit_rate_at_20 \| 0.0753406 \| \| val_hit_rate_at_100 \| 0.231435
\| \| val_hit_rate_at_200 \| 0.337464 \|
+\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--+\-\-\-\-\-\-\-\-\-\-\--+

We want to try out the following to root cause and fix this issue

- \[Done\] Use **high dimensional embeddings** (48d → 96d?)

  - Converges faster but no significant improvement in in-batch metrics

- \[Done\] Train a **separate model for each language**

  - Based on the TSNE analysis model has capacity to differentiate
    languages (for example in the image below even a small language like
    Japanese, marked red, can be differentiated from the rest of the
    languages)

<!-- -->

- \[Done\] Increase the size of common embedding table & separate out a
  separate table each for query and item towers \[[merge
  request](https://gitlab.dailyhunt.in/josh-recsys/mtl-training-pipeline/merge_requests/198)\]

  - Improves in-batch hit rate metrics

  - Does not improve kNN metrics

- \[Done\] Use **hard negative mining** and **mini-batching of users**
  to construct large virtual batches \[[merge
  request](https://gitlab.dailyhunt.in/josh-recsys/mtl-training-pipeline/merge_requests/198)\]

  - Speeds up training significantly

  - Does not improve kNN metrics (so batch size does not help)

- **Sort data** by req_city_id &/ user_lang (query features) and train
  model without shuffling to give model better negatives

- Add select item performance features as passthrough features in
  evaluation and join with item embedding data frame for **filtering the
  index**. Example feature:

  - `item_engagement_15d`

- Change the nature of the model so that it outputs **unnormalized
  embeddings**

  - Hypothesis is tail content will automatically be pushed towards the
    origin

  - Change the nature of the loss function so that **negative pairwise
    distances** are used as opposed to dot-products
