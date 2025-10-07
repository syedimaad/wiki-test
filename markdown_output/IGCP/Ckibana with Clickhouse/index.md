## Introduction

This document outlines the advantages and considerations of
transitioning from the traditional ELK (Elasticsearch, Logstash, Kibana)
stack to **Ckibana**, utilizing **ClickHouse** as the data backend.

## Key Benefits

### 1. Cost Savings

- **Primary Motivation**: The primary driver for this transition is the
  potential for substantial cost reduction, particularly in terms of
  storage and compute resources.

### 2. Performance Improvements

- **Enhanced Query Performance**: ClickHouse is renowned for its
  high-speed query execution, often outperforming Elasticsearch,
  especially in complex analytical queries.

- **Reduced Storage Requirements**: ClickHouse's columnar storage format
  and efficient compression techniques can significantly lower storage
  consumption.

- **Scalability**: ClickHouse handles large-scale data more effectively,
  with better support for distributed architectures.

- **Simplified Maintenance**: The system's architecture and tooling
  contribute to easier maintenance and lower operational complexity.

## Potential Challenges

### 1. Compatibility Issues

- **Migration Concerns**: Moving existing data and queries to ClickHouse
  may require considerable effort in data transformation and reindexing.
  Some features and query capabilities in Elasticsearch might not have
  direct equivalents in ClickHouse.

### 2. Community Support

- **Support Limitations**: The ClickHouse community, while growing, is
  still smaller compared to Elasticsearch. This can pose challenges in
  terms of finding resources, troubleshooting, and community-driven
  tools.

## Ideal Use Cases

### 1. Real-Time Analytics

- **High-Frequency Data Ingestion**: ClickHouse is well-suited for
  environments where real-time analytics and immediate data availability
  are crucial.

### 2. Large-Scale Data Processing

- **Scalability**: It can efficiently process and analyze vast amounts
  of data, making it ideal for big data scenarios.

### 3. Cost-Sensitive Environments

- **Budget Constraints**: Organizations looking to optimize their
  expenditure without compromising on performance will find ClickHouse
  to be a compelling alternative.

## Performance Comparison

### Query Speed and Resource Usage

- **ClickHouse Advantages**: Compared to Elasticsearch, ClickHouse
  typically requires fewer resources to deliver faster query responses,
  particularly for analytical workloads.

## Cost Implications

### Cost-Effectiveness

- **Overall Savings**: The combination of lower storage requirements and
  faster query performance translates into reduced infrastructure costs
  and operational overhead.

## Conclusion

Migrating from the ELK stack to Ckibana with ClickHouse can offer
significant benefits, including reduced costs, enhanced performance, and
better scalability. However, careful consideration of migration
challenges and potential limitations in community support is essential
to ensure a smooth transition.\
\
\
**Implementations Steps**

we are using below github project to integrate with clickhouse for
Kibana\
[https://github.com/TongchengOpenSource/ckibana](https://github.com/TongchengOpenSource/ckibana){card-appearance="inline"}

Start elasticsearch with single node with docker as below.

docker run -d -p 9200:9200 -p 9300:9300 -e
\"discovery.type=single-node\" -e ES_JAVA_OPTS=\"-Xms12g -Xmx20g\"
\--name elasticsearch -m 28GB -v
/root/jvm.options:/usr/share/elasticsearch/config/jvm.options
[docker.elastic.co/elasticsearch/elasticsearch:6.8.22](http://docker.elastic.co/elasticsearch/elasticsearch:6.8.22)

Start Ckibana and Kibana using below steps.

git clone
[https://github.com/TongchengOpenSource/ckibana.git](https://github.com/TongchengOpenSource/ckibana.git){card-appearance="inline"}

cd ckibana-1.0.5/docker-compose

modify docker compose file with below. docker-compose.yaml

change ES ip in file\
**/mnt/ckibana-1.0.5/docker-compose/config/ckibana-application.yaml**

version: \"2\" services: kibana: image: docker.io/kibana:6.8.22
hostname: kibana container_name: kibana environment:
ELASTICSEARCH_HOSTS: http://ckibana:8080 NODE_OPTIONS:
\--max-old-space-size=1800 ports: - \"0.0.0.0:8090:5601\" ckibana:
image: docker.io/ting001/ckibana:1.0.5 hostname: ckibana container_name:
ckibana restart: always ports: - \"0.0.0.0:8091:8080\" volumes: -
./config/ckibana-application.yaml:/wd/application.yaml -
\"/etc/timezone:/etc/timezone:ro\" -
\"/etc/localtime:/etc/localtime:ro\" entrypoint: \[ \"java\",
\"-jar\",\"-Dspring.config.location=/wd/application.yaml\",\"app.jar\"
\]

start ckibana and kibana

docker-compose up -d

**Add clickhouse config like below**

**Add clickhouse config to ckibana**

curl \--location \--request POST
\'localhost:8091/config/updateCk?url=10.90.0.141:8123&user=user2&pass=user2&defaultCkDatabase=default\'

**Add table to visible in kibana index.**

curl \--location \--request POST
\'localhost:8091/config/updateWhiteIndexList?list=events,notifications,reco_ts_aggr\'

Increase time interval and cache liek below

curl \--location \--request POST
\'localhost:8091/config/updateSampleCountMaxThreshold?sampleCountMaxThreshold=1500000000\'
curl \--location \--request POST
\'localhost:8091/config/updateUseCache?useCache=true\'

to check the settings:

Create user in clickhouse and grant permisison

CREATE USER ckibana IDENTIFIED WITH plaintext_password BY \'ckibana\'
grant all on rtp_logs.\* to ckibana

**curl \--location \'localhost:8091/config/all\'**

\
{\"proxy\":{\"ck\":{\"url\":\"10.90.0.141:8123\",\"user\":\"user2\",\"pass\":\"user2\",\"defaultCkDatabase\":\"default\"},\"es\":{\"host\":\"10.90.2.195:9200\",\"headers\":{\"mock\":\"mock\"}},\"roundAbleMinPeriod\":120000,\"round\":0,\"maxTimeRange\":9999999999999,\"blackIndexList\":\[\],\"whiteIndexList\":\[\"events\",\"notifications\",\"reco_ts_aggr\"\],\"enableMonitoring\":false},\"query\":{\"sampleIndexPatterns\":null,\"sampleCountMaxThreshold\":1500000000,\"useCache\":true,\"maxResultRow\":30000},\"threadPool\":{\"msearchProperty\":{\"coreSize\":4,\"queueSize\":10000},\"commonProperty\":{\"coreSize\":4,\"queueSize\":10000}},\"defaultShard\":2}

Configure in Kibana index and use.

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Created by:

Varaprasad N

26th Sep 2024
