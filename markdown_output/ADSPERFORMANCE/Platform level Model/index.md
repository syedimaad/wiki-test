- Requirements:\
  The platform level model framework should

  1.  Be a replacement to the campaign level model

  2.  Be able to consume and learn from delivery across the platform

      1.  Allow for opportunities of cross campaign learning

  3.  Solve for cold start gap between campaign live and model training.

  4.  Allow for addition campaigns / entities

  5.  Be easy to retrain

  6.  Be easy to incorporate new user level / dynamic features.

  7.  Be extendible to different entities (apps, leads etc)

  8.  Allow for A/B testing

  9.  Allow for multiple model variants and selection between them

  10. Not be biased by the inventory of a big campaign

  11. [Allow for hierarchical
      aggregations]{style="color: rgb(151,160,175);"}

<!-- -->

- Metrics to track

  - Performance (CTR, AUC, Rank..)

  - Data Preprocessing time/space

  - Effort to retrain the model

  - Coverage of platform data (train, test size)

<!-- -->

- Challenges:

  - Finalizing Formulation

  - How to measure perf?

    - offline

    - online

  - 

<!-- -->

- Formulations:

  - M(user, dynamics, campaign) \--\> Score.\
    Or

  - M(user, dynamics, campaign_list) \--\> Sorted campaign list
