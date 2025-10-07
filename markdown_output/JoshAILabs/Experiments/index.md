+----------------+-----------------+--------------+----------+-----------+-----------+---------------+
| **Experiment** | **Description** | **Labels**   | **Data   | **Teacher | **Student | **AUC**\      |
|                |                 |              | Schema** | loss**    | loss**    | **&**\        |
|                |                 |              |          |           |           | **HITRATIO**\ |
+----------------+-----------------+--------------+----------+-----------+-----------+---------------+
| approach 1     |                 |  gt_5sec &   | snapshot | ctr +     | kl div    | -17%          |
|                |                 | pcc90        |          | ctcvr     | loss +    |               |
|                |                 |              |          |           | teacher   |               |
|                |                 |              |          |           | loss      |               |
+----------------+-----------------+--------------+----------+-----------+-----------+---------------+
| approach 1     |                 | p90 & plike  | snapshot | ctr +\    | kl div    | -11%          |
|                |                 |              |          | ctcvr     | loss +    |               |
|                |                 |              |          |           | teacher   |               |
|                |                 |              |          |           | loss      |               |
+----------------+-----------------+--------------+----------+-----------+-----------+---------------+
| approach 2     |                 | skip & p90   | snapshot | ctr+\     | kl div    | -18%          |
|                |                 | label        |          | ctcvr     | loss +    |               |
|                |                 |              |          |           | teacher   |               |
|                |                 |              |          |           | loss      |               |
+----------------+-----------------+--------------+----------+-----------+-----------+---------------+
| approach 2     |                 | p90 label &  | snapshot | ctr+\     | kl div    | -10.8%\       |
|                |                 | plike        |          | ctcvr     | loss +    | &\            |
|                |                 |              |          |           | teacher   | Hit-rate:\    |
|                |                 |              |          |           | loss      | 1.8%          |
+----------------+-----------------+--------------+----------+-----------+-----------+---------------+
| approach 2     |                 | p90 label or | snapshot | ctr +\    | kl div    | -17%\         |
|                |                 | plike        |          | ctcvr     | loss +    | &\            |
|                |                 |              |          |           | teacher   | Hit-rate:\    |
|                |                 |              |          |           | loss      | 0.6%          |
+----------------+-----------------+--------------+----------+-----------+-----------+---------------+
| approach 2     |                 | p90 label    | snapshot | ctr +\    | kl div    | -11.7%        |
|                |                 |              |          | ctcvr     | loss      |               |
|                |                 | & loop label |          |           |           |               |
+----------------+-----------------+--------------+----------+-----------+-----------+---------------+
| approach 2     | train teacher   | gt_5sec &\   | snapshot | ctr +\    | kl div    | -9.8%         |
|                | and student one | p90 label    |          | ctcvr     | loss\     |               |
|                | after the other |              |          |           |           |               |
+----------------+-----------------+--------------+----------+-----------+-----------+---------------+
| approach 2     | train teacher   | gt_5sec &\   | snapshot | ctr +\    | kl div    | -17.5%        |
|                | and student one | p90 label    |          | ctcvr     | loss\     |               |
|                | after the other |              |          |           | &\        |               |
|                |                 |              |          |           | along     |               |
|                |                 |              |          |           | with      |               |
|                |                 |              |          |           | cosine    |               |
|                |                 |              |          |           | layer     |               |
|                |                 |              |          |           | before    |               |
|                |                 |              |          |           | dot layer |               |
+----------------+-----------------+--------------+----------+-----------+-----------+---------------+
| approach 2     |                 | gt_5sec &\   | snapshot | ctr+\     | MSE loss  | -10.6%        |
|                |                 | p90 label    |          | ctcvr     |           |               |
+----------------+-----------------+--------------+----------+-----------+-----------+---------------+
| approach 2     |                 | gt_5sec &\   | snapshot | ctr +\    | MSE       | -9.8%         |
|                |                 | p90 label    |          | ctcvr     | loss +    |               |
|                |                 |              |          |           | teacher   |               |
|                |                 |              |          |           | loss      |               |
+----------------+-----------------+--------------+----------+-----------+-----------+---------------+
| approach 2     | increased 1     | gt_5sec &\   | snapshot | ctr +\    | MSE loss  | -6.7%         |
|                | more expert     | plike        |          | ctcvr     |           |               |
+----------------+-----------------+--------------+----------+-----------+-----------+---------------+
| approach 2     | increased 1     | gt_5sec &\   | snapshot | ctr +\    | MSE loss\ | -5.9%         |
|                | more expert     | plike        |          | ctcvr     | + teacher |               |
|                |                 |              |          |           | loss      |               |
+----------------+-----------------+--------------+----------+-----------+-----------+---------------+
| approach 2     | stacked MMOE\   | gt_5sec &\   | snapshot | ctr +\    | kl div    | -15%          |
|                | \[added one     | p90 label    |          | ctcvr     | loss      |               |
|                | more layer of   |              |          |           |           |               |
|                | experts\]       |              |          |           |           |               |
+----------------+-----------------+--------------+----------+-----------+-----------+---------------+
| approach 2     | original        | gt_5sec &\   | Flattend | ctr +\    | kl div    | kl loss error |
|                |                 | p90 label    |          | ctcvr     | loss      |               |
|                |                 |              |          |           |           |               |
|                |                 |              |          | epoch-1   | epoch-1\  |               |
|                |                 |              |          | loss:     | loss: 0.9 |               |
|                |                 |              |          | 1.52      |           |               |
+----------------+-----------------+--------------+----------+-----------+-----------+---------------+
| approach 2     | stacked MMOE\   | gt_5sec &\   | Flattend | ctr +\    | kl div    | kl loss error |
|                | \[added one     | p90 label    |          | ctcvr     | loss\     |               |
|                | more layer of   |              |          |           | \         |               |
|                | experts(3) \]   |              |          | epoch-1   | epoch-1\  |               |
|                |                 |              |          | loss:     | loss:     |               |
|                |                 |              |          | 1.66      | 1.14      |               |
+----------------+-----------------+--------------+----------+-----------+-----------+---------------+
| approach 2     | replaced relu   | gt_5sec &\   | Flattend | ctr +\    | kl div    | kl loss error |
|                | with leaky relu | p90 label    |          | ctcvr     | loss\     |               |
|                |                 |              |          |           | \         |               |
|                |                 |              |          | epoch-1   | epoch-1\  |               |
|                |                 |              |          | loss:     | loss:     |               |
|                |                 |              |          | 1.62      | 1.12      |               |
+----------------+-----------------+--------------+----------+-----------+-----------+---------------+
| approach 2     | added dropout   | gt_5sec &\   | Flattend | ctr +\    | kl div    | kl loss error |
|                | layer(0.2)      | p90 label    |          | ctcvr\    | loss\     |               |
|                |                 |              |          | epoch-1   | \         |               |
|                |                 |              |          | loss:     | epoch-1\  |               |
|                |                 |              |          | 1.32      | loss:     |               |
|                |                 |              |          |           | 1.03      |               |
+----------------+-----------------+--------------+----------+-----------+-----------+---------------+
| prod-approach  | added extra cvr | gt_5sec &\   | Flattend | ctr +     | MSE loss  | auc : 0.74    |
|                | loss to teacher | p90 label    |          | cvr\      |           |               |
|                | model and MSE   |              |          | + ctcvr   |           | hit-rate: 14% |
|                | loss to student |              |          |           |           |               |
|                | model           |              |          |           |           |               |
+----------------+-----------------+--------------+----------+-----------+-----------+---------------+
| prod-approach  | Balancing/\     | w1\*gt_5sec\ | Flattend | ctr +     | MSE loss  | auc : 0.76\   |
|                | normalizing the | &\           |          | cvr\      |           |               |
|                | target labels   | w2\*p90      |          | + ctcvr   |           |               |
|                |                 | label        |          |           |           |               |
+----------------+-----------------+--------------+----------+-----------+-----------+---------------+

And other experiments Based on Hyper Parameter Tunings ( very little
improvements) like\

- Dense Layer changes in Experts, Gates and Tower networks \[different
  hidden layer shapes\]

- Optimizers and Scheduler changes \[Adam,AdamW,SGD\] & \[stepLR =\> (15
  steps, 3steps) , cyclicLR =\> (10 steps)\]

- Feature level changes \[ added and removed some features based on
  importance\]

- Qr-Embedding changes \[combined q & r, added q & r\]\
  \
  \
