+----------------+------------+------------+---------------------+--------------------+-------------+-----------------+
| **Experiment** | **celebs** | **training | **Backbone**        | **loss**           | **Misc**    | **output**      |
|                |            | data**     |                     |                    |             |                 |
+----------------+------------+------------+---------------------+--------------------+-------------+-----------------+
| custom CNN     | 135        | 33 k       | none                | triplet loss (0.9) |             |                 |
| Architecture   |            | images     |                     |                    |             |                 |
|                | (50 data   |            |                     |                    |             |                 |
|                | samples    |            |                     |                    |             |                 |
|                | each)      |            |                     |                    |             |                 |
+----------------+------------+------------+---------------------+--------------------+-------------+-----------------+
| Pretrained     | 135        | 33 k       | Resnet              | triplet loss       |             |                 |
| model as       |            | images     |                     | (0.65)             |             |                 |
| backbone       | (50 data   |            |                     |                    |             |                 |
|                | samples    |            |                     |                    |             |                 |
|                | each)      |            |                     |                    |             |                 |
+----------------+------------+------------+---------------------+--------------------+-------------+-----------------+
| Semi Hard      | 135        | 33 k       | Resnet              | triplet loss       | Miners : {\ | shows           |
| Mining & Hard  |            | images     |                     | (0.65)             | margin :    | improvement     |
| Mining         | (50 data   |            |                     |                    | 0.2,\       |                 |
|                | samples    |            |                     |                    | distance :  |                 |
|                | each)      |            |                     |                    | cosine      |                 |
|                |            |            |                     |                    | distance\   |                 |
|                |            |            |                     |                    | }           |                 |
+----------------+------------+------------+---------------------+--------------------+-------------+-----------------+
| Simclr         | \~1200\    | 13k images | Simclr (which uses  | {\                 | down-stream | 99.2% training  |
| Approach       | (around 10 |            | Resnet18 as         | contrastive *loss  | task :      | accuracy and 5% |
|                | data       |            | pretrained model)   | :* \["NT-Xent      | linear head | testing         |
|                | samples    |            |                     | *loss*"            |             | accuracy\       |
|                | each)      |            |                     | (Normalized        |             | \               |
|                |            |            |                     | Temperature-Scaled |             |                 |
|                |            |            |                     | Cross-Entropy      |             |                 |
|                |            |            |                     | *Loss*)\],         |             |                 |
|                |            |            |                     | downstream task    |             |                 |
|                |            |            |                     | loss : cross       |             |                 |
|                |            |            |                     | -entropy loss\     |             |                 |
|                |            |            |                     | }                  |             |                 |
+----------------+------------+------------+---------------------+--------------------+-------------+-----------------+
| Simclr         | \~1200\    | 13k images | Simclr (which uses  | {contrastive *loss | down-stream | Implemen-tation |
| Approach-2     | (around 10 |            | Resnet18 as         | :* \["NT-Xent      | task :      | Failed          |
|                | data       |            | pretrained model)   | *loss*"            | linear head |                 |
|                | samples    |            |                     | (Normalized        |             |                 |
|                | each)      |            |                     | Temperature-Scaled |             |                 |
|                |            |            |                     | Cross-Entropy      |             |                 |
|                |            |            |                     | *Loss*)\],         |             |                 |
|                |            |            |                     | downstream task    |             |                 |
|                |            |            |                     | loss : triplet     |             |                 |
|                |            |            |                     | loss}              |             |                 |
+----------------+------------+------------+---------------------+--------------------+-------------+-----------------+
| Fine Tuning on | \~1200\    | 13k images | Inception-Resnetv1\ | CrossEntropyLoss   |             | 99.2% training  |
| existing prod  | (around 10 |            | (vgggface2          | (0.3)              |             | accuracy and    |
| model          | data       |            | pretrained weights) |                    |             | 96.7% testing   |
|                | samples    |            |                     |                    |             | accuracy        |
|                | each)      |            |                     |                    |             |                 |
+----------------+------------+------------+---------------------+--------------------+-------------+-----------------+
| Fine Tuning    | \~1200\    | 13k images | Inception-Resnetv1\ | CrossEntropyLoss   | pre-whitten | 99.8% training  |
| with Filters   | (around 10 |            | (vgggface2          | (0.3)              | filter      | accuracy and    |
| on existing    | data       |            | pretrained weights) |                    | applied     | 97.8% testing   |
| prod model     | samples    |            |                     |                    |             | accuracy        |
|                | each)      |            |                     |                    |             |                 |
+----------------+------------+------------+---------------------+--------------------+-------------+-----------------+
