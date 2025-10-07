  ----------------------------
  **line_item_product_code**
  AWSLambda
  AWSDatabaseMigrationSvc
  AWSCodeCommit
  AmazonS3
  AmazonEC2
  AWSCloudShell
  AmazonQuickSight
  datapipeline
  AmazonGuardDuty
  AmazonCognito
  2ot70g95967pa820dml8qauogh
  ElasticMapReduce
  AmazonCloudFront
  AmazonDAX
  AmazonMCS
  AWSSecretsManager
  AmazonDynamoDB
  AmazonSageMaker
  AmazonVPC
  AmazonStates
  AmazonSES
  AmazonECR
  AWSCodeArtifact
  AmazonDocDB
  6g1ummt7ko6h3r9lsgku5f5326
  AWSBackup
  AmazonElastiCache
  AWSSupportBusiness
  AmazonMWAA
  AWSDirectConnect
  AmazonGlacier
  AmazonRoute53
  AmazonRedshift
  9ita2vl7bhtee4wbst8z5h1w0
  AWSGlue
  AmazonCloudWatch
  AmazonEFS
  AmazonAthena
  AWSIoT
  AWSGlobalAccelerator
  AmazonInspector
  AmazonECS
  AWSCostExplorer
  AWSQueueService
  AmazonKinesis
  AWSELB
  AmazonApiGateway
  AmazonKinesisFirehose
  ComputeSavingsPlans
  AWSCloudTrail
  AmazonSNS
  AWSXRay
  AWSTransfer
  AmazonEKS
  AWSBudgets
  AmazonRekognition
  AmazonMSK
  AmazonES
  AWSSystemsManager
  awskms
  AmazonKinesisAnalytics
  AmazonRDS
  AWSConfig
  AWSDeveloperSupport
  AWSDataTransfer
  AWSElementalMediaStore
  AmazonNeptune
  ----------------------------

Example Query ::

\##### S3 \###

select DATE_FORMAT((line_item_usage_start_date),\'%Y-%m-%d\') AS
day_line_item_usage_start_date

,
"line_item_resource_id\",\"line_item_usage_type\",\"line_item_line_item_type\"
,sum(\"line_item_unblended_cost\" ) from cost_analysis where
year=\'2022\' and month='6' and date='6' and
\"line_item_product_code\"=\'AmazonS3\' group by
line_item_resource_id,\"line_item_usage_type\",\"line_item_line_item_type",DATE_FORMAT((line_item_usage_start_date),'%Y-%m-%d');

DATE_FORMAT((line_item_usage_start_date),\'%Y-%m-%d\') AS
day_line_item_usage_start_date

select
\"line_item_resource_id\",\"line_item_usage_type\",\"line_item_line_item_type\"
,sum(\"line_item_unblended_cost\" ),
DATE_FORMAT((line_item_usage_start_date),\'%Y-%m-%d\') AS
day_line_item_usage_start_date from cost_analysis where
line_item_usage_start_date BETWEEN
FROM_ISO8601_TIMESTAMP(\'2022-06-26T00:00:00\') AND
FROM_ISO8601_TIMESTAMP(\'2022-06-26T01:23:45\') and
\"line_item_product_code\"=\'AmazonKinesis\' group by
line_item_resource_id,\"line_item_usage_type\",\"line_item_line_item_type\",DATE_FORMAT((line_item_usage_start_date),\'%Y-%m-%d\');

select
\"line_item_resource_id\",\"line_item_usage_type\",\"line_item_line_item_type\"
,sum(\"line_item_unblended_cost\" ) from cost_analysis where
line_item_usage_start_date BETWEEN
FROM_ISO8601_TIMESTAMP(\'2022-07-04T00:00:00\') AND
FROM_ISO8601_TIMESTAMP(\'2022-07-04T23:59:45\') and
\"line_item_product_code\"=\'AmazonElastiCache\' group by
line_item_resource_id,\"line_item_usage_type\",\"line_item_line_item_type\";

select
\"line_item_resource_id\",\"line_item_usage_type\",\"line_item_line_item_type\"
,sum(\"line_item_unblended_cost\" ),
DATE_FORMAT((line_item_usage_start_date),\'%Y-%m-%d\') AS
day_line_item_usage_start_date from cost_analysis where
line_item_usage_start_date BETWEEN
FROM_ISO8601_TIMESTAMP(\'2022-06-26T00:00:00\') AND
FROM_ISO8601_TIMESTAMP(\'2022-06-28T23:59:45\') and
\"line_item_product_code\"=\'AmazonS3\' group by
line_item_resource_id,\"line_item_usage_type\",\"line_item_line_item_type\",DATE_FORMAT((line_item_usage_start_date),\'%Y-%m-%d\');

DYNAMODB

select
\"line_item_resource_id\",\"line_item_usage_type\",\"line_item_line_item_type\"
,sum(\"line_item_unblended_cost\" ),
DATE_FORMAT((line_item_usage_start_date),\'%Y-%m-%d\') AS
day_line_item_usage_start_date from cost_analysis where
line_item_usage_start_date BETWEEN
FROM_ISO8601_TIMESTAMP(\'2022-07-03T00:00:00\') AND
FROM_ISO8601_TIMESTAMP(\'2022-07-03T23:59:45\') and
\"line_item_product_code\"=\'AmazonDynamoDB\' group by
line_item_resource_id,\"line_item_usage_type\",\"line_item_line_item_type\",DATE_FORMAT((line_item_usage_start_date),\'%Y-%m-%d\');

AWSELB

select
\"line_item_resource_id\",\"line_item_usage_type\",\"line_item_line_item_type\"
,sum(\"line_item_unblended_cost\" ),
DATE_FORMAT((line_item_usage_start_date),\'%Y-%m-%d\') AS
day_line_item_usage_start_date from cost_analysis where
line_item_usage_start_date BETWEEN
FROM_ISO8601_TIMESTAMP(\'2022-07-25T00:00:00\') AND
FROM_ISO8601_TIMESTAMP(\'2022-07-25T23:59:45\') and
\"line_item_product_code\"=\'AWSELB\' group by
line_item_resource_id,\"line_item_usage_type\",\"line_item_line_item_type\",DATE_FORMAT((line_item_usage_start_date),\'%Y-%m-%d\');

\#### Ec2 query \###

select
\"resource_tags_user_name\",\"line_item_resource_id\",\"line_item_usage_type\",\"line_item_line_item_type\"
,sum(\"line_item_unblended_cost\" ) from cost_analysis where
line_item_usage_start_date BETWEEN
FROM_ISO8601_TIMESTAMP(\'2022-07-05T00:00:00\') AND
FROM_ISO8601_TIMESTAMP(\'2022-07-05T23:59:45\') and
\"line_item_product_code\"=\'AmazonEC2\' group by
resource_tags_user_name,
line_item_resource_id,\"line_item_usage_type\",\"line_item_line_item_type\";

### Athena ::

select
\"line_item_resource_id\",\"line_item_usage_type\",\"line_item_line_item_type\"
,sum(\"line_item_unblended_cost\" ),
DATE_FORMAT((line_item_usage_start_date),\'%Y-%m-%d\') AS
day_line_item_usage_start_date from cost_analysis where
line_item_usage_start_date BETWEEN
FROM_ISO8601_TIMESTAMP(\'2022-07-18T00:00:00\') AND
FROM_ISO8601_TIMESTAMP(\'2022-07-22T23:59:45\') and
\"line_item_product_code\"=\'AmazonAthena\' group by
line_item_resource_id,\"line_item_usage_type\",\"line_item_line_item_type\",DATE_FORMAT((line_item_usage_start_date),\'%Y-%m-%d\');

\##### EC2 Tag with EMR ID####

select \"resource_tags_aws_elasticmapreduce_job_flow_id\",
\"resource_tags_user_name\",\"line_item_resource_id\",\"line_item_usage_type\",\"line_item_line_item_type\"
,sum(\"line_item_unblended_cost\" ) from cost_analysis where
line_item_usage_start_date BETWEEN
FROM_ISO8601_TIMESTAMP(\'2022-07-05T00:00:00\') AND
FROM_ISO8601_TIMESTAMP(\'2022-07-05T23:59:45\') and
\"line_item_product_code\"=\'AmazonEC2\' group by
resource_tags_user_name,
line_item_resource_id,\"line_item_usage_type\",\"line_item_line_item_type\",\"resource_tags_aws_elasticmapreduce_job_flow_id\"

\~

Srini
