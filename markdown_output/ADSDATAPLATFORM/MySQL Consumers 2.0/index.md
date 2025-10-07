saluber:
<https://saluber.dailyhunt.in/d/jwPKfbfksnizsa/kafka-overview?orgId=3&from=now-2d&to=now&viewPanel=12>

1.  Read from Kafka topics and write to 3 mysql tables -

    1.  `oads.ox_data_intermediate_ad_zone`

    2.  `daedalus_reports.dhx_performance_data`

    3.  `daedalus_reports.ox_affiliate_deliveries`

2.  To add new columns to the above tables, take downtime (at
    midnight) - Pause MPE, Mysql consumers, and restart.

3.  Kafka topics, consumers, tables are common for DH, Josh, PV.

------------------------------------------------------------------------

#### GIT REPO:

<https://gitlab.dailyhunt.in/nh-ads-platform/adsdataprocessing>

------------------------------------------------------------------------

#### VM:

PROD:

[dh-gcp-ads-analyticsnrt-kafka-consumer-n1.dailyhunt.in](http://dh-gcp-ads-analyticsnrt-kafka-consumer-n1.dailyhunt.in),

[dh-gcp-ads-analyticsnrt-kafka-consumer-n2.dailyhunt.in](http://dh-gcp-ads-analyticsnrt-kafka-consumer-n1.dailyhunt.in)

STAGE:

[dh-gcp-ads-pacing-engine-stage-n1.dailyhunt.in](http://dh-gcp-ads-pacing-engine-stage-n1.dailyhunt.in)

------------------------------------------------------------------------

#### PATH:

PROD: /mnt/vol1/dh-ads/adsdataprocessing

PROD_TEST: /mnt/vol1/dh-ads/dishant/adsdataprocessing

STAGE: /mnt/vol1/dh-ads/dishant/adsdataprocessing

**LOGS**:

PROD: /mnt/vol1/dh-ads/adsdataprocessing/logs

PROD_TEST: /mnt/vol1/dh-ads/dishant/adsdataprocessing/logs

STAGE: /mnt/vol1/dh-ads/dishant/adsdataprocessing/logs

------------------------------------------------------------------------

#### TESTING:

for Testing on prod we have created tables

`oads_test.ox_data_intermediate_ad_zone`

`daedalus_reports_test.dhx_performance_data`

`daedalus_reports_test.ox_affiliate_deliveries`

- change databases in all queries

- change kafka consumer group name as well

------------------------------------------------------------------------

CRONS:

n1:

\*/2 \* \* \* \* docker run \--rm -i \--name=\"clicks\" -v
/mnt/vol1/dh-ads/adsdataprocessing:/app mysqlconsumers:latest python3
src/consumers/ClicksConsumer.py\>\> /tmp/cronlogClick 2\>&1 \*/4 \* \*
\* \* sh
/mnt/vol1/dh-ads/adsdataprocessing/src/scripts/kill-if-not-enough-processes-running.sh
\"src/consumers/ClicksConsumer.py\" 1 \"oxClicksQueue\"
\"kafka-clk-events-consumer\" 50000 \"clicks\"\>\> /tmp/cronlogClickStop
2\>&1 \*/2 \* \* \* \* docker run \--rm -i \--name=\"postbacks\" -v
/mnt/vol1/dh-ads/adsdataprocessing:/app mysqlconsumers:latest python3
src/consumers/PostBacksConsumer.py\>\> /tmp/cronlogPostback 2\>&1 \*/5
\* \* \* \* sh
/mnt/vol1/dh-ads/adsdataprocessing/src/scripts/kill-if-not-enough-processes-running.sh
\"src/consumers/PostBacksConsumer.py\" 1 \"oxPostBackQueue\"
\"kafka-pb-events-consumer\" 10000 \"postbacks\"\>\>
/tmp/cronlogPostbackStop 2\>&1 \*/2 \* \* \* \* docker run \--rm -i
\--name=\"adinteraction\" -v /mnt/vol1/dh-ads/adsdataprocessing:/app
mysqlconsumers:latest python3 src/consumers/AdInteractionConsumer.py\>\>
/tmp/cronlogAdInt 2\>&1 \*/6 \* \* \* \* sh
/mnt/vol1/dh-ads/adsdataprocessing/src/scripts/kill-if-not-enough-processes-running.sh
\"src/consumers/AdInteractionConsumer.py\" 1 \"oxAdInteractionQueue\"
\"kafka-ad-interaction-events-consumer\" 10000 \"adinteraction\"\>\>
/tmp/cronlogAdIntStop 2\>&1 \*/1 \* \* \* \* docker run \--rm -i
\--name=\"vast\" -v /mnt/vol1/dh-ads/adsdataprocessing:/app
mysqlconsumers:latest python3 src/consumers/VastConsumer.py\>\>
/tmp/cronlogVast 2\>&1 \*/3 \* \* \* \* sh
/mnt/vol1/dh-ads/adsdataprocessing/src/scripts/kill-if-not-enough-processes-running.sh
\"src/consumers/VastConsumer.py\" 1 \"vastEventQueue\"
\"kafka-vast-events-consumer-prod\" 10000 \"vast\"\>\>
/tmp/cronlogVastStop 2\>&1 \*/1 \* \* \* \* docker run \--rm -i
\--name=\"request\" -v /mnt/vol1/dh-ads/adsdataprocessing:/app
mysqlconsumers:latest python3 src/consumers/RequestsConsumer.py\>\>
/tmp/cronlogReq 2\>&1 \*/2 \* \* \* \* sh
/mnt/vol1/dh-ads/adsdataprocessing/src/scripts/kill-if-not-enough-processes-running.sh
\"src/consumers/RequestsConsumer.py\" 25 \"oxReqQueue\"
\"kafka-req-events-consumer\" 3000000 \"request\"\>\>
/tmp/cronlogReqStop 2\>&1 \*/2 \* \* \* \* docker run \--rm -i
\--name=\"appevent\" -v /mnt/vol1/dh-ads/adsdataprocessing:/app
mysqlconsumers:latest python3 src/consumers/AppEventsConsumer.py\>\>
/tmp/cronlogAppevents 2\>&1 \*/11 \* \* \* \* sh
/mnt/vol1/dh-ads/adsdataprocessing/src/scripts/kill-if-not-enough-processes-running.sh
\"src/consumers/AppEventsConsumer.py\" 1 \"oxAppEventPostBackQueue\"
\"kafka-appev-events-consumer-new\" 10000 \"appevent\"\>\>
/tmp/cronlogAppeventsStop 2\>&1 \*/2 \* \* \* \* docker run \--rm -i
\--name=\"attributions\" -v /mnt/vol1/dh-ads/adsdataprocessing:/app
mysqlconsumers:latest python3 src/consumers/AttributionsConsumer.py\>\>
/tmp/cronlogAttribtions 2\>&1 \*/7 \* \* \* \* sh
/mnt/vol1/dh-ads/adsdataprocessing/src/scripts/kill-if-not-enough-processes-running.sh
\"src/consumers/AttributionsConsumer.py\" 1 \"oxAttributionsQueue\"
\"kafka-attrev-events-consumer\" 10000 \"attributions\"\>\>
/tmp/cronlogAttribtionsStop 2\>&1 \*/2 \* \* \* \* docker run \--rm -i
\--name=\"pollsv2\" -v /mnt/vol1/dh-ads/adsdataprocessing:/app
mysqlconsumers:latest python3 src/consumers/PollsConsumerV2.py\>\>
/tmp/cronlogpollsv2 2\>&1 \*/8 \* \* \* \* sh
/mnt/vol1/dh-ads/adsdataprocessing/src/scripts/kill-if-not-enough-processes-running.sh
\"src/consumers/PollsConsumerV2.py\" 2 \"pollsV2\"
\"kafka-pollV2-events-consumer-prod\" 10000 \"pollsv2\"\>\>
/tmp/cronlogpollsv2Stop 2\>&1 \*/2 \* \* \* \* docker run \--rm -i
\--name=\"polls\" -v /mnt/vol1/dh-ads/adsdataprocessing:/app
mysqlconsumers:latest python3 src/consumers/PollsConsumer.py\>\>
/tmp/cronlogPolls 2\>&1 \*/9 \* \* \* \* sh
/mnt/vol1/dh-ads/adsdataprocessing/src/scripts/kill-if-not-enough-processes-running.sh
\"src/consumers/PollsConsumer.py\" 13 \"pollStoreNew\"
\"kafka-poll-events-consumer-prod\" 1000000 \"polls\"\>\>
/tmp/cronlogPollsStop 2\>&1 \*/5 \* \* \* \* docker run \--rm -i
\--name=\"dfp\" -v /mnt/vol1/dh-ads/adsdataprocessing:/app
mysqlconsumers:latest python3 src/dfp/dfpDataPopulate.py \>\>
/tmp/cronlogDfp 2\>&1 \*/10 \* \* \* \* sh
/mnt/vol1/dh-ads/adsdataprocessing/src/scripts/kill-container.sh \"dfp\"
840 \>\> /tmp/cronlogDfpStop 2\>&1 \*/4 \* \* \* \* docker run \--rm -i
\--name=\"faultTolerance\" -v /mnt/vol1/dh-ads/adsdataprocessing:/app -v
/mnt/vol1/dh-ads/.ssh:/mnt/vol1/dh-ads/.ssh:ro mysqlconsumers:latest
python3 /app/src/scripts/falutToleranceCheker.py \>\> /tmp/cronlogFault
2\>&1 \*/11 \* \* \* \* sh
/mnt/vol1/dh-ads/adsdataprocessing/src/scripts/kill-container.sh
\"faultTolerance\" 840\>\> /tmp/cronlogFaultStop 2\>&1

n2:

\*/1 \* \* \* \* docker run \--rm -i \--name=\"impression\" -v
/mnt/vol1/dh-ads/adsdataprocessing:/app mysqlconsumers:latest python3
src/consumers/ImpressionsConsumer.py\>\> /tmp/cronlogImp 2\>&1 \*/2 \*
\* \* \* sh
/mnt/vol1/dh-ads/adsdataprocessing/src/scripts/kill-if-not-enough-processes-running.sh
\"src/consumers/ImpressionsConsumer.py\" 4 \"oxImpQueue\"
\"kafka-imp-events-consumer\" 1000000 \"impression\"\>\>
/tmp/cronlogImpStop 2\>&1 \*/2 \* \* \* \* docker run \--rm -i
\--name=\"replacement\" -v /mnt/vol1/dh-ads/adsdataprocessing:/app
mysqlconsumers:latest python3
src/consumers/ReplacementEventsConsumer.py\>\> /tmp/cronlogReplacement
2\>&1 \*/3 \* \* \* \* sh
/mnt/vol1/dh-ads/adsdataprocessing/src/scripts/kill-if-not-enough-processes-running.sh
\"src/consumers/ReplacementEventsConsumer.py\" 5 \"oxReplacedQueue\"
\"kafka-replacement-events-consumer\" 50000 \"replacement\"\>\>
/tmp/cronlogReplacementStop 2\>&1 \*/1 \* \* \* \* docker run \--rm -i
\--name=\"inflated\" -v /mnt/vol1/dh-ads/adsdataprocessing:/app
mysqlconsumers:latest python3
src/consumers/InflatedRespondedConsumer.py\>\> /tmp/cronlogInflated
2\>&1 \*/4 \* \* \* \* sh
/mnt/vol1/dh-ads/adsdataprocessing/src/scripts/kill-if-not-enough-processes-running.sh
\"src/consumers/InflatedRespondedConsumer.py\" 13
\"oxInflatedRespondedQueue\" \"kafka-inf-res-events-consumer\" 3000000
\"inflated\"\>\> /tmp/cronlogInflatedStop 2\>&1 \*/2 \* \* \* \* docker
run \--rm -i \--name=\"feedback\" -v
/mnt/vol1/dh-ads/adsdataprocessing:/app mysqlconsumers:latest python3
src/consumers/FeedbackConsumer.py\>\> /tmp/cronlogFeedback 2\>&1 \*/5 \*
\* \* \* sh
/mnt/vol1/dh-ads/adsdataprocessing/src/scripts/kill-if-not-enough-processes-running.sh
\"src/consumers/FeedbackConsumer.py\" 1 \"adFeedback\"
\"kafka-feedback-consumer\" 10000 \"feedback\"\>\>
/tmp/cronlogFeedbackStop 2\>&1

------------------------------------------------------------------------

[https://developers.google.com/ad-manager/api/deprecation](https://developers.google.com/ad-manager/api/deprecation){card-appearance="inline"}

DFP Fetch data processing is running from this repo every 5 min and
updating to `daedalus_reports.dhx_direct_campaign_revenue_source_dfp`
table\
Cron:

\*/5 \* \* \* \* docker run \--rm -i \--name=\"dfp\" -v
/mnt/vol1/dh-ads/adsdataprocessing:/app mysqlconsumers:latest python3
src/dfp/dfpDataPopulate.py \>\> /tmp/cronlogDfp 2\>&1 \*/10 \* \* \* \*
sh /mnt/vol1/dh-ads/adsdataprocessing/src/scripts/kill-container.sh
\"dfp\" 840 \>\> /tmp/cronlogDfpStop 2\>&1

------------------------------------------------------------------------

Consumer Groups Lag Monitoring Script:

\*/4 \* \* \* \* docker run \--rm -i \--name=\"faultTolerance\" -v
/mnt/vol1/dh-ads/adsdataprocessing:/app -v
/mnt/vol1/dh-ads/.ssh:/mnt/vol1/dh-ads/.ssh:ro mysqlconsumers:latest
python3 /app/src/scripts/falutToleranceCheker.py \>\> /tmp/cronlogFault
2\>&1 \*/11 \* \* \* \* sh
/mnt/vol1/dh-ads/adsdataprocessing/src/scripts/kill-container.sh
\"faultTolerance\" 840\>\> /tmp/cronlogFaultStop 2\>&1

------------------------------------------------------------------------

Np-wise report:

select b.source_group, a.campaign_id,a.campaign_name,a.order_id,
a.order_name, sum(requests) as requests, sum(impressions) as
impressions, sum(clicks) as clicks from
**hive.ads.newspaper_wise_report** as a join
ads.np_to_source_group_mapping as b on a.np_source_id=b.np_source_id
where a.report_year=2023 and a.report_month=8 group by 1,2,3,4,5
