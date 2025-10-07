# AWS Autoscale based on any custom metrics

\
\
We want to autoscale EC2 instances based on any custom metrics like SQS
Queue size or LB requests, etc.\
Below  is the setup to perform.\
\
\
Step 1 :\
Create a custom namespace in AWS cloud watch and metrics add sample data
to check.\
*aws cloudwatch put-metric-data \--metric-name
**TestBacklogPerInstance** \--namespace **TestNamespace** \--unit None
\--value 4 \--dimensions
MyOptionalMetricDimensionName=MyOptionalMetricDimensionValue*\
\
Create Target Tracking custom policy,  which value Auto scaling group
has to maintain. Ex : if you put value as 5, if the cloud metric for the
last 5 min is above 5 then it will auto scale, if the value is below 5
then it will downscale.\
{ \"TargetValue\":**5**, \"CustomizedMetricSpecification\":{
\"MetricName\":\"TestBacklogPerInstance\",
\"Namespace\":\"TestNamespace\", \"Dimensions\":\[ {
\"Name\":\"MyOptionalMetricDimensionName\",
\"Value\":\"MyOptionalMetricDimensionValue\" } \],
\"Statistic\":\"Average\", \"Unit\":\"None\" } }\
*aws autoscaling put-scaling-policy \--policy-name
Test-sqs50-target-tracking-scaling-policy \--auto-scaling-group-name
Test-SQS-scale \--policy-type TargetTrackingScaling
\--target-tracking-configuration*
[{\_}{+}file://config.json+\_]{style="color: rgb(0,0,238);"}
(file://config.json)\
\
Here i created based on SQS Queue size and number of ec2 instances,
third monitoring instances has to continuously put metrics in AWS cloud
watch.\
**[Command to check number of messages in
Queue]{style="text-decoration: underline;"}**\
*aws sqs get-queue-attributes \--queue-url*
[[{\_}{+}]{style="color: rgb(0,0,238);"}](https://sqs.ap-south-1.amazonaws.com/514352861371/v2-prod-josh-hls-transcoder)[https://sqs.ap-south-1.amazonaws.com/514352861371/v2-prod-josh-hls-transcoder+\_](https://sqs.ap-south-1.amazonaws.com/514352861371/v2-prod-josh-hls-transcoder+_){.external-link
rel="nofollow"}*  \--attribute-names ApproximateNumberOfMessages
\--region ap-south-1 \| grep -E -o 
\"ApproximateNumberOfMessages.{0,9}\" \|  sed \'s/\[\^0-9\]\*//g\'*\
1233\
**Command to check number of autoscaling instances at present active **\
*aws autoscaling describe-auto-scaling-groups
\--auto-scaling-group-names Test-SQS-scale \--region=ap-south-1 \| grep
\'\"LifecycleState\": \"InService\"\' \| wc -l*\
20\
Ex: Here each EC2 instance can process 100 videos per minute and minimum
we are keeping 4 instances so  they can process 400. 400/100 =4
instances needed,  800/100 =8 instances needed, this needs autoscale. so
our monitoring software will update the calculated value to cloud watch
metrics.\
 \
Create a script and cron to update cloudwatch metrics every hour.\
\[root@dh-aws-infra-prometheus vara\]# cat autoscale_sqs_queue.sh
#!/bin/bash\
Messages_in_sqs_queue=\$(aws sqs get-queue-attributes \--queue-url
[[{+}]{style="color: rgb(0,0,238);"}](https://sqs.ap-south-1.amazonaws.com/514352861371/qa_future_fk_follows_scheduled)[https://sqs.ap-south-1.amazonaws.com/514352861371/qa_future_fk_follows_scheduled+](https://sqs.ap-south-1.amazonaws.com/514352861371/qa_future_fk_follows_scheduled+){.external-link
rel="nofollow"} \--attribute-names ApproximateNumberOfMessages \--region
ap-south-1 \| grep -E -o \"ApproximateNumberOfMessages.{0,9}\" \| sed
\'s/\[\^0-9\]\*//g\')\
NO_OF_INSTANCES=\$(aws autoscaling describe-auto-scaling-groups
\--auto-scaling-group-names Test-SQS-scale \--region=ap-south-1 \| grep
\'\"LifecycleState\": \"InService\"\' \| wc -l)\
Cloud_Watch_Metrics=\$((Messages_in_sqs_queue/NO_OF_INSTANCES))\
aws cloudwatch put-metric-data -[metric-name TestBacklogPerInstance
\--namespace TestNamespace \--unit None \--value \$Cloud_Watch_Metrics
\--dimensions
MyOptionalMetricDimensionName=MyOptionalMetricDimensionValue  ]{style="text-decoration: line-through;"}-region=ap-south-1
\[root@dh-aws-infra-prometheus vara\]#

- \* \* \* \* sh /root/vara/autoscale_sqs_queue.sh\
  **Scale UP: takes 5min to scale up**\
  \
  \
  **[Scale down  : took 15min to scale
  down]{style="text-decoration: underline;"}**\
  \
  \
  \
  \
  ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++[Varaprasad.N
  Oct 5th -2020]{style="text-decoration: underline;"}++++++
