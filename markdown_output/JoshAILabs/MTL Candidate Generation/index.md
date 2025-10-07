**References :**

Distillation based Multi-task Learning: A Candidate Generation Model for
Improving Reading Duration <https://arxiv.org/pdf/2102.07142.pdf>

Modelling Task Relationships in Multi-task Learning with Multi-gate
Mixture-of-Experts\
<https://dl.acm.org/doi/pdf/10.1145/3219819.3220007>

**Github link :**
[**https://gitlab.dailyhunt.in/josh-ai-labs/mtl_candidate_generation/-/tree/training_update?ref_type=heads**](https://gitlab.dailyhunt.in/josh-ai-labs/mtl_candidate_generation/-/tree/training_update?ref_type=heads)

**Prod Server: 10.70.32.94** (key: ugc-prod)

### Probable Tasks (output columns)

- gt_5sec =\> video watch time \>5sec

- pcc90 =\> watch fraction \>= 90%

**PROD** **APPROACH** :

**Whats new compared to Baseline approach?**

- Added Extra loss in teacher model along with **ctr** and **ctcvr**
  losses i.e, **cvr loss**

- Replaced **KL divergence loss** with **MSE loss** for distillation

**Data Source** : `Flatten_ds_v5`

+--------------------------+---------------------+----------------------+
| **User Columns**                                                      |
+--------------------------+---------------------+----------------------+
| Column Name              | Embedding Dimension | Embedding layer Type |
+--------------------------+---------------------+----------------------+
| dow                      | (4,)                | Embedding            |
+--------------------------+---------------------+----------------------+
| hod                      | (4,)                | QR-Embedding         |
+--------------------------+---------------------+----------------------+
| gender                   | (3,)                | one-hot Encoding     |
+--------------------------+---------------------+----------------------+
| state_id                 | (8 ,)               | QR-Embedding         |
+--------------------------+---------------------+----------------------+
| city_id                  | (16,)               | QR-Embedding         |
+--------------------------+---------------------+----------------------+
| age                      | (1,)                |                      |
+--------------------------+---------------------+----------------------+
| clv                      | (4,)                | QR-Embedding         |
+--------------------------+---------------------+----------------------+
| price_range              | (6,)                | QR-Embedding         |
+--------------------------+---------------------+----------------------+
| handset_makerItem        | (8,)                | QR-Embedding         |
| Columns                  |                     |                      |
+--------------------------+---------------------+----------------------+
| recent_k_like_item_ids   | (20,)               | Mean Embedding       |
+--------------------------+---------------------+----------------------+
| recent_k_pcc_98_item_ids | (50,)               | Mean Embedding       |
+--------------------------+---------------------+----------------------+
| recent_k_skip_item_ids   | (50,)               | Mean Embedding       |
+--------------------------+---------------------+----------------------+
| user_stats_cols          | (45,)               |                      |
+--------------------------+---------------------+----------------------+

+--------------------+---------------------+----------------------+
| **Item Columns**                                                |
+--------------------+---------------------+----------------------+
| Column Name        | Embedding Dimension | Embedding layer Type |
+--------------------+---------------------+----------------------+
| genre              | (8,)                | QR-Embedding         |
+--------------------+---------------------+----------------------+
| creator_id         | (31,)               | QR-Embedding         |
+--------------------+---------------------+----------------------+
| item_id            | (64,)               | QR-Embedding         |
+--------------------+---------------------+----------------------+
| item_idx           | (128,)              | Blip-Embedding       |
+--------------------+---------------------+----------------------+
| item_age_norm      | (1,)                |                      |
+--------------------+---------------------+----------------------+
| content_stats_cols | (70,)               |                      |
+--------------------+---------------------+----------------------+
| creator_stats_cols | (70,)               |                      |
+--------------------+---------------------+----------------------+
| content_perf_cols  | (224,)              |                      |
+--------------------+---------------------+----------------------+

**Teacher Model Specifics**

Input : \[user features, item_features \] → take concatenated user and
item features

experts : ANN architecture with hidden layers \[888,512,256,128\] X 2

gates : ANN architecture with softmax activation
\[888,512,256,128,64,3\] X 2

Towers : ANN architecture with hidden layers \[192,128,64,32,16,8,1\] X
2

Main tasks : \[gt5_sec,pcc90\]

Here assume \[ Pctr : gt5_sec and Pcvr : pcc90 \]

- loss function for Pctr : binary cross entropy

- loss function for Pcvr: binary cross entropy

- Pctcvr = Pctr\*Pcvr

- loss function for Pctcvr : binary cross entropy

final loss function for teacher model : Pctr + Pcvr + Pctcvr

**Student Model Specifics**

Input : User and Item features passed through user tower and item tower

User Tower : ANN architecture with hidden layers \[291,256,128,64,32\]

Item Tower : ANN architecture with hidden layers \[597,256,128,64,32\]

Main Task : \[ pcc90 \]

**Distillation Loss** btw teacher and student : Mean Squared Error

\
**final loss :** teacher loss+student loss.

**Optimizer :** AdamW(lr=1e-4, weight_decay=1e-2) =\> weight_decay adds
as a regularizing term

**Scheduler :** StepLR(step_size=5, gamma=0.1)

**Epochs :** 4
