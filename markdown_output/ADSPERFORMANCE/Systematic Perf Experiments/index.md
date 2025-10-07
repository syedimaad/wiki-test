## Requirements:

#### Experiments Platform should

1.  Be online as well as offline.

2.  Be sandboxed from production

3.  support easy logging newer information at event level

4.  Have clean and trackable evaluation data sets for each entity
    (offline)

5.  support non-binary model selection

6.  Dynamic weight distribution among the models (experiment comparison
    , statistical significance, confidence intervals, chi square test)

7.  Have a strong offline evaluation - ( like 7 day running window
    evaluation, )

8.  Have specific clear guidelines of how do we make a decision of
    whether this experiment is doing well. (thresholds on when to choose
    a model, when to stop a model, when to increase and decrease
    weights).

9.  Have great dashboards and reports and alerts!

#### Training platform should

1.  support entity level lists of available models (maintain when was
    the model last trained)

2.  maintain training frequency of each model type at entity level

    1.  Also optimize the transformation vs training time - if similar
        dataset train together.

------------------------------------------------------------------------

## Plan

#### Phase 1 : Improve

1.  Improve the reporting on experiments

    1.  Time dimension

    2.  Statistical significance

        1.  NULL Hypothesis -- both A and B paths are equal

        2.  Hypothesis to test → A is better than B or B is better than
            A.

        3.  CVR_A == 0.5% and CVR_B == 5% → Apply Statistical
            Significance Test →

2.  Improve the Evaluation Dataset - and metric being tracked. (can it
    be uuid)

3.  Improve (if we can) offline evaluations on online experiments - and
    add them to reporting.

4.  Improve application level metric tracking in Prometheus

5.  Improve experimental features addition

    1.  Design Experimental Feature Extraction

        1.  how experimental features can be added - without breaking
            the production flow.

        2.  Ease of making experimental features available in A/B
            without touching the prod models

        3.  Another redis key? another parquet?

#### Phase 2: Build

1.  New Training scheduler

    1.  consider which model to retrain

    2.  Log all available types of models for an entity

2.  System Experimentation Flow

    1.  Enabling all / selected models in production

        1.  Ranking should be unaware of these choices. These should be
            in the experimentation platform and shared with the
            AdLearning/build-so module.

    2.  Static computation of distribution weights

    3.  Dynamic update on weights of experiments.

        1.  When do we update?

        2.  Where do we get the data?

        3.  Will it be (near) real time?

        4.  Can this be rolled out slowly

        5.  Logging needs to be airtight.

#### Phase 3: Observe and Update

1.  How to display overall performance of an entity as distributed by
    the experiments at certain point in time?

2.  Very fast paced dashboards

    1.  can it be done via Prometheus?
