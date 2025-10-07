- Trained regressor on top of glam labels, with mapped target values as
  follows

  - 0:0,

  - 1:0.1,

  - 2:0.2,

  - 3:0.35,

  - 4:0.5,

  - 5:0.7,

  - 7:0.85

  -  8: 1

- Input Blip 128 dimension + hive data

- Hive columns

  - max

    - \'general_nsfw\',

    -  \'yes_female_underwear\',

    -  \'yes_sex_toy\',

    -  \'yes_female_nudity\',

    -  \'yes_male_nudity\',

    -  \'yes_female_swimwear\',

    -  \'yes_sexual_activity\',

    -  \'yes_child_present\'

  - min

    - \'General_suggestive\',

- Hive aggregation -\> max of sliding mean (every 3 frames)

- Training Data : 50k(max) from each glam level in qc verified data with
  a 80:20 split and 3,4,5,7 labels filtered on binary classifier.

 

  ------------------------- -------- -------- ----------
  MODEL                     mse      rmse     r2_score
  Random Forest Regressor   0.0197   0.1406   0.8034
  ------------------------- -------- -------- ----------

## DEPLOYMENT

The model is currently run on blip real time service, where it takes
blip_128 pca embeddings and hive data and returns glamour score and
glamour level as output.

Glamour Level is calculated on the following business logic.\

  ----------- ----
  0-0.05      0
  0.05-0.1    0
  0.1-0.15    0
  0.15-0.20   1
  0.20-0.25   1
  0.25-0.30   2
  0.30-0.35   2
  0.35-0.40   3
  0.40-0.45   3
  0.45-0.50   3
  0.5-0.55    3
  0.55-0.6    3
  0.6-0.65    4
  0.65-0.70   5
  0.7-0.75    5
  0.75-0.80   6
  0.80-0.85   7
  0.85-0.9    8
  0.9-0.95    9
  0.95-1      10
  ----------- ----

### GIT REPO LINK

<https://gitlab.dailyhunt.in/josh-ai-labs/blip-azure-service/-/tree/prod/api/glamour>
