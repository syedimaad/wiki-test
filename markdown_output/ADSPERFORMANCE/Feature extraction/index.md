## Feature Extraction

1.  Responsible for extracting features from the data store mongo - and
    make them available for training models (AdLearning) and runtime
    predictions (Ranking Service)

2.  Repo :

    1.  DH :
        <https://gitlab.dailyhunt.in/nh-ads-platform/feature-extraction>

    2.  Josh :
        <https://gitlab.dailyhunt.in/nh-ads-platform/josh-feature-extraction>

3.  Tech: Python, PySpark, Redis

4.  Rough Responsibility:

    1.  Batched query from mongo

    2.  Transformations on features

    3.  Save to parquet

    4.  Write and update to redis

5.  Dependencies: Embedding Pipeline
