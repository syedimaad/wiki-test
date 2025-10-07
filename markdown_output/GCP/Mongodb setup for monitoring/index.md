1.  All vm stats are collected from 172.20.10.98 (prometheus server) so
    update vm entries in pf file \

    vi /etc/prometheus/prometheus.yml

2.  Since these vm contain mongo database we need to update the port
    used by mongo in the vm\
    cmd: **vi /etc/blackbox/Database-Targets/Mongo-Targets.yml** \--\>
    here update ip address along with port (u can get port number from
    db team)

3.  Then run following commands\
    -**promtool check config /etc/prometheus/prometheus.yml**\
    -**curl \--location \--request POST**
    [**http://172.20.10.98:9090/-/reload**](http://172.20.10.98:9090/-/reload)

4.  To get application level monitoring u need to add data in
    prometheus-application server(172.20.10.99)

5.  Application server is used for all the application level monitoring
    like (mysql,redis,mongo\...etc) but all the service will run on
    unique ports 

6.  To create a specific port for your server u need to create a
    supervisord file\
     cmd: **cd /mnt/vol1/phoenix.admin/supervisord/supervisord.d/**
    \--\> here u need to create a new .ini file

**example**: 

\[program: mongo_content2_enrichment\]

command=/mnt/vol1/phoenix.admin/Exporters_Prometheus/mongodb_exporter/mongodb_exporter
\--mongodb.uri=mongodb://collectionreader:secretpass@172.20.15.137:50000
\--web.listen-address=:9322

user=phoenix.admin

autostart=true

autorestart=true

startsecs=10

startretries=36

redirect_stderr=true

stdout_logfile=/mnt/vol2/phoenix.admin-data/supervisord/logs/mongo_exporter_content2_enrichment.log

stderr_logfile=/mnt/vol2/phoenix.admin-data/supervisord/logs/mongo_exporter_content2_enrichment.error.log

stopsignal=KILL

**here**: collectionreader:secretpass@172.20.15.137:50000 \-\-\--\>
update with username:password@\_ip\_:port     

web.listen-address=:9322\-\--\> update with web.listen-address=:unique
port-number

also change the name of logfiles \--\> (.log and .error.log) and program
name

**note**:- username,password,port will be provided by db-team

7\. to know which all ports are alredy in use 

 cmd: **netstat -anlp \|grep LISTEN** \-\--\> U can see all the ports
being used 

8\. after creating .ini file run the following commands

 cmd: - **supervisorctl**

\>**reread**

\>**update**

\>**status** \-\--\> if u are able to see all the files u have created
and status is running then u have successfully created the port

9\. then update the vm details along with the port u have created (i.e
port declared in .ini file)  \--\> **pf** file

**example:**

- job_name: \'ads_mongodb_metrics_aiml_mongo_n2\'

    static_configs:

- targets: \[\'172.20.10.99:9324\'\]

      labels:

        cluster: \'AIML-GCP\'

        node: \'aiml-mongo\'

        env: \'PROD\'

        host: \"10.90.131.4\"

    scrape_interval: 20s

10\. then run following commands:

\-**promtoolcheck**

\-**rp → reload prometheus**
