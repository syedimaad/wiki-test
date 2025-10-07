## 

## Server Details:

+:-------:+:--------------------------------------------------------:+:---------------------------------------------------------------------------------------------------------------:+
| Service | IP Address                                               | Domain                                                                                                          |
+---------+----------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------+
| Nginx   | 192.168.1.20                                             | es-devops.dailyhunt.in:9200                                                                                     |
+---------+----------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------+
| ES      |     http://es-devops.dailyhunt.in:9200/_cat/nodes?v&h=ip | \                                                                                                               |
+---------+----------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------+
| Kibana  | 192.168.1.20                                             | [http://stats.dailyhunt.in](http://stats.dailyhunt.in/app/kibana#/discover?_g=()&_a=(columns:!(_source),index:) |
+---------+----------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------+
| Grafana | 192.168.1.20                                             | <http://admin-stats.dailyhunt.in>                                                                               |
+---------+----------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------+

## ES Monitoring: {#es-monitoring .auto-cursor-target}

###### source:

<http://devops.dailyhunt.in/gitlist/index.php/dh-sysadmin.git/blob/master/ElasticSearch/Monitoring/es_indexing_alert.py>

We are monitoring the document indexing count for each index at specific
interval. When there will be indexing count zero at specific interval we
will get alerts.

This script is running on 192.168.1.20 machine at root user crontab. We
passing the index name and timeframe to check as arguments to the
script.

#### 192.168.1.20 Crontab Entry:

    ### Elasticsearch indices monitoring alert
    ES_ALERT_LOG='/mnt/vol2/dh-devops-data/es_indexing_alert'
    */2 * * * * /usr/local/bin/python ${REPO_DIR}/ElasticSearch/Monitoring/es_indexing_alert.py -i lbstats -t 2 >> ${ES_ALERT_LOG}/alert_output_`date +\%F`.log 2>&1
    */2 * * * * /usr/local/bin/python ${REPO_DIR}/ElasticSearch/Monitoring/es_indexing_alert.py -i elasticsearch_metrics -t 2 >> ${ES_ALERT_LOG}/alert_output_`date +\%F`.log 2>&1
    */2 * * * * /usr/local/bin/python ${REPO_DIR}/ElasticSearch/Monitoring/es_indexing_alert.py -i redisinfo -t 2 >> ${ES_ALERT_LOG}/alert_output_`date +\%F`.log 2>&1
    15,45 * * * * /usr/local/bin/python ${REPO_DIR}/ElasticSearch/Monitoring/es_indexing_alert.py -i cloudmetrics -t 20 >> ${ES_ALERT_LOG}/alert_output_`date +\%F`.log 2>&1

\

## ES Cleanup:

We are removing old data in ElasticSearch through curator on
192.168.1.20.

###### source:

<http://devops.dailyhunt.in/gitlist/index.php/dh-sysadmin.git/tree/master/ElasticSearch/Curator/>

#### 192.168.1.20 Crontab Entry:

30 01 \* \* \* /usr/bin/curator
/home/selvam.mariappan/es_index_clean.yml \>\>
/mnt/vol2/dh-devops-data/curator/es_index_clean.log 2\>&1

\

\

\~ SELVAM
