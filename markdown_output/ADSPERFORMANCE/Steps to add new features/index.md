In **feature-extraction** - 

1.  Create parquet file with new features + client_id from data in
    MongoDB - 

    1.  Use only new features + client_id in schema and long_cols in
        schema.py

    2.  Add a method in extraction_helper to fetch relevant columns from
        Mongo

    3.  Add corresponding method name in configs.py under correct
        collection name

    4.  Verify a single client_id's data by running etl/extract.py

    5.  Run user_profile_extraction.py in a different branch with above
        changes to get the new features parquet

2.  Add new features to userProfile parquet - 

    1.  Change new_features list in configs.py to add only the new
        features

    2.  Run new_features_joiner.py, provide the new_features parquet
        path and the output path

    3.  Verify the joinedUserProfile parquet including its size, schema
        and count.

    4.  Backup userProfileV2.parquet

    5.  Replace the userProfileV2.parquet with the
        joinedUserProfile.parquet

3.  Merge changes - 

    1.  Verify for at least a 1M set of users that the
        user_profile_extraction.py works as intended along with old
        columns

    2.  Merge additional column changes from (1) along with older
        columns into master branch

4.  Redis update - 

    1.  Run new_features_updater.py with the new_features parquet

In **AdLearning** - 

1.  Make changes to the postback profile - 

    1.  Add columns to postback_add_columns.sh as directed in script

    2.  Run backpopulation via postback_add_columns.sh to update
        postback profile

2.  Add new features to application_properties for experimentation /
    production

\

In case of **experimentation** - 

In **AdLearning** - 

1.  Run models for relevant campaign/app/lead ids and save to a custom
    path

In **ExperimentationPlatform** - 

1.  Run copy_expt_models.py specifying the new model path, entity ids
    and the experiment suffix, check here -
    <https://jira.newshunt.com/browse/NHADSPLTL-3187>

2.  Create corresponding experiments in [[the
    platform]{.underline}](http://ads-experimentation-platform.dailyhunt.in/)
    and observe results.

- Steps 2-5 need to be finished within a day otherwise it could lead to
  production issues/stale data.
