\# start yanagashima cd /home/nexverse/yanagishima-23.0
./bin/yanagishima-start.sh
http://10.170.9.41:8181/#datasource=nexverse&engine=presto&tab=qlist&queryid=20250902_071612_00000_ew5qc
nvuser/nv2025

Trino UI

http://10.170.9.41:8009/ui/ login anything

To VM start Trino service

\# master su nexverse cd \~ cd /home/nexverse/trino-server-443
./bin/launcher restart #Wroker : pwd: /home/nexverse/trino-server-443
./bin/launcher start

Start Hive metastore

cd /home/nexverse/hive export HADOOP_HEAPSIZE=16384 /bin/hive \--service
metastore &
