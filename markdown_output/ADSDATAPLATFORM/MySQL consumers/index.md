1.  Read from Kafka topics and write to 2 mysql tables -
    oads.ox_data_intermediate_ad_zone and
    daedalus_reports.ox_partner_deliveries.

2.  To add new columns to the above tables, take downtime (at
    midnight) - Pause MPE, Mysql consumers, and restart.

3.  Git repo -
    <https://gitlab.dailyhunt.in/nh-ads-platform/ad-analytics-data>

4.  VMs -
    [dh-gcp-ads-analyticsnrt-kafka-consumer-n1.dailyhunt.in](http://dh-gcp-ads-analyticsnrt-kafka-consumer-n2.dailyhunt.in)
    and
    [dh-gcp-ads-analyticsnrt-kafka-consumer-n2.dailyhunt.in](http://dh-gcp-ads-analyticsnrt-kafka-consumer-n2.dailyhunt.in)

5.  Kafka topics, consumers, tables are common for DH, Josh, PV.

6.  Assign left partitions (in case of unequal division of partitions)
    to workers to the last worker. #TODO

7.  #TODO - Why are 8004, 8005 zone_id entries not processed after 2
    hours?

8.  Testing should be done on stage mpe VM
    (dh-gcp-ads-pacing-engine-stage-n1).

    1.  Pre prod testing can be done on table in prod mysql server -
        DB - **testing**, can create new table or use
        (ox_data_intermediate_ad_zone).

9.  Crons on n1 -

\# Check if all consumers are running, if not kill all of them and
restart. \*/6 \* \* \* \*
/mnt/vol1/dh-ads/kafka-ad-analytics-data/ad-analytics-data/kill-if-not-enough-processes-running.sh
\"/bin/python
/mnt/vol1/dh-ads/kafka-ad-analytics-data/ad-analytics-data/RequestsConsumer.py\"
25 \"oxReqQueue\" \"kafka-req-events-consumer\" 3000000 \>\>
/tmp/cronlog 2\>&1 \*/4 \* \* \* \*
/mnt/vol1/dh-ads/kafka-ad-analytics-data/ad-analytics-data/kill-if-not-enough-processes-running.sh
\"/bin/python
/mnt/vol1/dh-ads/kafka-ad-analytics-data/ad-analytics-data/PostBacksConsumer.py\"
1 \"oxPostBackQueue\" \"kafka-pb-events-consumer\" 10000 \>\>
/tmp/cronlog 2\>&1 \*/3 \* \* \* \*
/mnt/vol1/dh-ads/kafka-ad-analytics-data/ad-analytics-data/kill-if-not-enough-processes-running.sh
\"/bin/python
/mnt/vol1/dh-ads/kafka-ad-analytics-data/ad-analytics-data/ClicksConsumer.py\"
1 \"oxClicksQueue\" \"kafka-clk-events-consumer\" 50000 \>\>
/tmp/cronlog 2\>&1 \*/5 \* \* \* \*
/mnt/vol1/dh-ads/kafka-ad-analytics-data/ad-analytics-data/kill-if-not-enough-processes-running.sh
\"/bin/python
/mnt/vol1/dh-ads/kafka-ad-analytics-data/ad-analytics-data/VastConsumer.py\"
1 \"vastEventQueue\" \"kafka-vast-events-consumer-prod\" 10000 \>\>
/tmp/cronlog 2\>&1 \*/5 \* \* \* \*
/mnt/vol1/dh-ads/kafka-ad-analytics-data/ad-analytics-data/kill-if-not-enough-processes-running.sh
\"/bin/python
/mnt/vol1/dh-ads/kafka-ad-analytics-data/ad-analytics-data/AppEventsConsumer.py\"
1 \"oxAppEventPostBackQueue\" \"kafka-appev-events-consumer-new\" 10000
\>\> /tmp/cronlog 2\>&1 \*/5 \* \* \* \*
/mnt/vol1/dh-ads/kafka-ad-analytics-data/ad-analytics-data/kill-if-not-enough-processes-running.sh
\"/bin/python
/mnt/vol1/dh-ads/kafka-ad-analytics-data/ad-analytics-data/AttributionsConsumer.py\"
1 \"oxAttributionsQueue\" \"kafka-attrev-events-consumer\" 10000 \>\>
/tmp/cronlog 2\>&1 \*/3 \* \* \* \*
/mnt/vol1/dh-ads/kafka-ad-analytics-data/ad-analytics-data/kill-if-not-enough-processes-running.sh
\"/bin/python
/mnt/vol1/dh-ads/kafka-ad-analytics-data/ad-analytics-data/PollsConsumer.py\"
13 \"pollStoreNew\" \"kafka-poll-events-consumer-prod\" 1000000 \>\>
/tmp/cronlog 2\>&1 \*/5 \* \* \* \*
/mnt/vol1/dh-ads/kafka-ad-analytics-data/ad-analytics-data/kill-if-not-enough-processes-running.sh
\"/bin/python
/mnt/vol1/dh-ads/kafka-ad-analytics-data/ad-analytics-data/PollsConsumerV2.py\"
1 \"pollsV2\" \"kafka-pollV2-events-consumer-prod\" 10000 \>\>
/tmp/cronlog 2\>&1 \*/5 \* \* \* \*
/mnt/vol1/dh-ads/kafka-ad-analytics-data/ad-analytics-data/kill-if-not-enough-processes-running.sh
\"/bin/python
/mnt/vol1/dh-ads/kafka-ad-analytics-data/ad-analytics-data/AdInteractionConsumer.py\"
1 \"oxAdInteractionQueue\" \"kafka-ad-interaction-events-consumer\"
10000 \>\> /tmp/cronlogAdInt 2\>&1

10. Crons on n2 -

    1.  \# Check if all consumers are running, if not kill all of them
        and restart. \*/2 \* \* \* \*
        /mnt/vol1/dh-ads/kafka-ad-analytics-data/ad-analytics-data/kill-if-not-enough-processes-running.sh
        \"/bin/python
        /mnt/vol1/dh-ads/kafka-ad-analytics-data/ad-analytics-data/InflatedRespondedConsumer.py\"
        13 \"oxInflatedRespondedQueue\"
        \"kafka-inf-res-events-consumer\" 3000000 \>\> /tmp/cronlogV2
        2\>&1 \*/3 \* \* \* \*
        /mnt/vol1/dh-ads/kafka-ad-analytics-data/ad-analytics-data/kill-if-not-enough-processes-running.sh
        \"/bin/python
        /mnt/vol1/dh-ads/kafka-ad-analytics-data/ad-analytics-data/ImpressionsConsumer.py\"
        4 \"oxImpQueue\" \"kafka-imp-events-consumer\" 1000000 \>\>
        /tmp/cronlogV2 2\>&1 \*/5 \* \* \* \*
        /mnt/vol1/dh-ads/kafka-ad-analytics-data/ad-analytics-data/kill-if-not-enough-processes-running.sh
        \"/bin/python
        /mnt/vol1/dh-ads/kafka-ad-analytics-data/ad-analytics-data/FeedbackConsumer.py\"
        1 \"adFeedback\" \"kafka-feedback-consumer\" 10000 \>\>
        /tmp/cronlogV2 2\>&1 \* \* \* \* \*
        /mnt/vol1/dh-ads/kafka-ad-analytics-data/ad-analytics-data/kill-if-not-enough-processes-running.sh
        \"/bin/python
        /mnt/vol1/dh-ads/kafka-ad-analytics-data/ad-analytics-data/ReplacementEventsConsumer.py\"
        9 \"oxReplacedQueue\" \"kafka-replacement-events-consumer\"
        1000000 \>\> /tmp/cronlogReplacement 2\>&1

11. Grafana link to monitor - Dashboard - Kafka Stats -
    <http://saluber.dailyhunt.in/d/kafkastats/kafka-stats?viewPanel=12&orgId=22&from=now-1h&to=now>

12. Components getting impacted by lag in mysql consumers - MPE,
    Daedalus dashboard

13. DAN MySQL consumers path -
    /mnt/vol1/dh-ads/dan-ad-analytics-data/ad-analytics-data
