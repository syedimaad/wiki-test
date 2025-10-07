The following team members are currently part of this oncall rotation

- 

- 

- 

- 

- 

- 

- \

700falseSpreadsheet-2023-05-25T00:22:26.tfss0.7859990109444408

Weekly oncall rotations with the following responsibilities -

- Run feature monitoring and report any issues to the feature store team

- Train and refresh ranker and retrieval models either through airflow
  or manually

  - Send message on slack updating team members about deployment

- Fix all intermittent airflow errors and make sure that they're running
  smoothly

- Train and refresh PPR source

- Content pipelines

[This](https://docs.google.com/spreadsheets/d/1AWBEQhLXhhixkiJXs4Fgippmc5C_-EsURVkOU4Tgilc/edit#gid=681403525)
sheet reflects the state of various prod models. The oncall should make
sure that this sheet is updated.

# Feature Monitoring

Note that these notebook would need to updated as and when we move to
new versions of training data or add any new feature transformations.

- Notebook to compare offline vs online feature skew -
  <https://apoorv-ml-gpu-test.notebook.ap-south-1.sagemaker.aws/lab/tree/oncall_monitoring/feature_monitoring.ipynb>

- Notebook to compute ranking metrics on online logged data -
  <https://apoorv-ml-gpu-test.notebook.ap-south-1.sagemaker.aws/lab/tree/oncall_monitoring/online_auc_logged.ipynb>

# Deploy models on Triton

- copy the artifacts from vocab, training and blip module/index gen
  scripts to the correct directories. Update timestamps or dt references
  in upload_to_build_s3.sh and upload_to_prod_s3.sh. Check in the
  changes

<!-- -->

- checkout your py and plugin branches

- go to py folder

- run sbuild

- make sure no errors when it loads the image

- test postman and ensure no errors for a few hashcodes

- ctrl + c

- sh register_build.sh

- dlog

- look at the logs on prod traffic and ensure no errors

- ctrl + c

- sh deregister_build.sh

- merge your branches to master and checkout latest master

- run sprod

- make sure no errors when it loads the image

- test postman and ensure no errors for a few hashcodes

- ctrl + c

- sh register_build.sh

- dlog

- look at the logs on prod traffic and ensure no errors

- ctrl + c

- sh deregister_build.sh

- sh \~/scripts/prod_force_deployment.sh

# Refreshing PPR

POC -

# Airflow

- [Pipeline](https://airflow-josh-recsys-eks-cluster.myjosh.in/dags/prod_gen_training_metadata/grid)
  to generate training metadata which includes

  - [Vocab](https://s3.console.aws.amazon.com/s3/buckets/josh-reco-ml-model-artifacts?region=ap-south-1&prefix=aux_vocab_ranker/prod/&showversions=false)

  - [Blip
    model](https://s3.console.aws.amazon.com/s3/buckets/josh-reco-ml-model-artifacts?region=ap-south-1&prefix=aux_blip_ranker/prod/&showversions=false)

  - [Blip LTHM
    Model](https://s3.console.aws.amazon.com/s3/buckets/josh-reco-ml-model-artifacts?region=ap-south-1&prefix=aux_blip_lthm_ranker/prod/&showversions=false)

  - [Blip cold start
    index](https://s3.console.aws.amazon.com/s3/buckets/josh-reco-ml-model-artifacts?region=ap-south-1&prefix=coldstart_blip_index/prod/&showversions=false)

- [Pipeline](https://airflow-josh-recsys-eks-cluster.myjosh.in/dags/prod_ranker_v2_full_train/grid?dag_run_id=scheduled__2023-05-24T00%3A00%3A00%2B00%3A00&task_id=parse_arguments.get_train_end_date)
  to run ranker_v2 training and run inference

  - Outputs ranker model

  - Outputs query tower (currently not used in prod)

  - Outputs retrieval index

# Content Pipelines

POC -
