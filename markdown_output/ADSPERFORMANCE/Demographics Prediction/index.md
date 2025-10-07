## Demographics

1.  Responsible for training models for prediction Age and gender for
    the users.

2.  As the data is limited by the amount of ground truth values we get -
    we use different models and do a combined prediction.

3.  Repo:

    1.  DH

        1.  Xgboost:
            <https://gitlab.dailyhunt.in/nh-ads-platform/ctrPrediction>

        2.  Neural Networks:
            <https://gitlab.dailyhunt.in/nh-ads-platform/nndemographics>

    2.  Josh

        1.  NN:
            <https://gitlab.dailyhunt.in/nh-ads-platform/josh-demographics>

4.  Rough Responsibility:

    1.  Extract data from Mongo which is not in UserProfile.

    2.  Train model(s)

    3.  Predict for all users (! scale!! )

    4.  Combine predictions

    5.  Update in mongo.
