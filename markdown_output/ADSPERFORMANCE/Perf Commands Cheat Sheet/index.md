### YARN

- Yarn Link:
  [[YARN]{.underline}](http://dh-hw-ads-learning-n2.dailyhunt.in:8088/ui2/index.html#/yarn-apps/apps)

- Ambari Link:
  [[AMBARI]{.underline}](http://dh-hw-ads-learning-n1.dailyhunt.in:8080/#/main/services/HDFS/summary)

- Yarn Application kill:

  bashyarn application -kill \<app_id\>

- Yarn Application Move:

- yarn application -movetoqueue \<app_id\> -queue \<queue_name\>

### Hostnames / IP of the Learning Cluster

  ------------------------------------------------------------------------------------- -------------------
  **Hostname**                                                                          **New IP**
  [**dh-hw-ads-learning-n1.dailyhunt.in**](http://dh-hw-ads-learning-n1.dailyhunt.in)   **172.20.48.151**
  [**dh-hw-ads-learning-n2.dailyhunt.in**](http://dh-hw-ads-learning-n2.dailyhunt.in)   **172.20.48.152**
  [**dh-hw-ads-learning-n3.dailyhunt.in**](http://dh-hw-ads-learning-n3.dailyhunt.in)   **172.20.48.153**
  [**dh-hw-ads-learning-n4.dailyhunt.in**](http://dh-hw-ads-learning-n4.dailyhunt.in)   **172.20.48.154**
  [**dh-hw-ads-learning-n5.dailyhunt.in**](http://dh-hw-ads-learning-n5.dailyhunt.in)   **172.20.48.155**
  [**dh-hw-ads-learning-n6.dailyhunt.in**](http://dh-hw-ads-learning-n6.dailyhunt.in)   **172.20.48.156**
  ------------------------------------------------------------------------------------- -------------------

### Important Paths

- **UserProfile:** /user/dh-ads/data/processed/userProfileV2.parquet

- **Campaigns**: /user/dh-ads/data/processed/campaign_store

- **Leads**: /user/dh-ads/data/processed/lead_store

- **Apps**: /user/dh-ads/data/processed/app_store

- **Models**: /user/dh-ads/modelsV2/

- **Meta**: /user/dh-ads/metaV2/

\

### DB access

- [MySQL Master: \*\*\*Caution\*\*\*]{.underline} 

mysql daedalus -uoads_user -peterno123 -h db.internal.ads.dailyhunt.in
-P38036

- [MySQL slave:]{.underline}

mysql daedalus -uoads_user -peterno123
-hdb-slave1.internal.ads.dailyhunt.in -P3306

- [MySQL Stage DB]{.underline}: 

mysql daedalus -uroot -peterno123\$ -hdb-stage.internal.ads.dailyhunt.in
-P3306

### Redis Connection 

ssh to 192.168.24.139 or dh6-ads-learning-n1 redis-cli -p 8003 -h
cache-n1.internal.ads.dailyhunt.in -c HGET \"U:{\<client_id\>}\" ua
#redis-5.0.8/bin/redis-cli -p 8003 -h cache-n1.internal.ads.dailyhunt.in
-c #redis-5.0.8/bin/redis-cli -h 192.168.7.76 -p 8001 -c #To connect to
redis on learning cluster n3  cd /mnt/vol1/dh-ads/redis ./redis-cli -h
10.50.16.62 -p 8001 -c

### Mongo

mongo \--host usrmongo-n2.internal.ads.dailyhunt.in \--port 10001 -u
dhuadmin -p dyt@dmin123 \--authenticationDatabase admin

### Redis Kafka Consumer offset

**Note**: One can reset the offset to latest, earliest etc.. below is an
example to move it to latest

bin/kafka-consumer-groups \--bootstrap-server localhost:9092 \--group
\<group_id\> \--topic \<topic_id\> \--reset-offsets \--to-latest
\--execute

### Airflow DB fetch table size command

SELECT table_name, Sum(data_length+index_length)/1024/1024 tablesize
FROM information_schema.tables WHERE table_schema=\'airflow_perf_edge\'
group by table_name;

 
