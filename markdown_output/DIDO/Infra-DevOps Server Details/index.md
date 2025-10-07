## DailyHunt DevOps Common Server Details:

+:-----:+:-------------------------------------------------:+:--------------:+:----------------------:+
| SL.No | HostName                                          | IP Address     | Application Details    |
+-------+---------------------------------------------------+----------------+------------------------+
| 1     | [build1.newshunt.com](http://build1.newshunt.com) | 192.168.10.70  | Jenkins\               |
|       |                                                   |                | Artifactory\           |
|       |                                                   |                | redis(26615, 26616,    |
|       |                                                   |                | 26715 and 26716)\      |
|       |                                                   |                | redis-sentinel(20000)\ |
|       |                                                   |                | Httpd                  |
+-------+---------------------------------------------------+----------------+------------------------+
| 2     | [neo4.newshunt.com](http://neo4.newshunt.com)     | 192.168.10.103 | GitLab                 |
+-------+---------------------------------------------------+----------------+------------------------+
| 3     | [neo2.newshunt.com](http://neo2.newshunt.com)     | 192.168.10.101 | DNS (named)\           |
|       |                                                   |                | Httpd\                 |
|       |                                                   |                | Public url Monitoring  |
|       |                                                   |                | (mrpe)                 |
+-------+---------------------------------------------------+----------------+------------------------+
| 4     | [neo3.newshunt.com](http://neo3.newshunt.com)     | 192.168.10.102 | DNS (named)\           |
|       |                                                   |                | Httpd (apache2)\       |
|       |                                                   |                | Httpd (apache2-i2)\    |
|       |                                                   |                | MySQL                  |
+-------+---------------------------------------------------+----------------+------------------------+

\

\

## DH-Infra Admin Server Details:

+:-----:+:-------------------------------------------------------------------------:+:------------:+:---------------------:+
| SL.NO | HostName                                                                  | IP Address   | Application Details   |
+-------+---------------------------------------------------------------------------+--------------+-----------------------+
| 1     | [admin-analytics.dailyhunt.in](http://admin-analytics.dailyhunt.in)       | 192.168.2.36 | vSphere Metric        |
|       |                                                                           |              | Collector (Cron)\     |
|       |                                                                           |              | Monthly Report        |
|       |                                                                           |              | Generator (Cron)\     |
|       |                                                                           |              | MySQL\                |
|       |                                                                           |              | Logstash              |
|       |                                                                           |              | (Supervisord)\        |
|       |                                                                           |              | Jupyter Notebook\     |
|       |                                                                           |              | Influxdb              |
+-------+---------------------------------------------------------------------------+--------------+-----------------------+
| 2     | [dh-sysadmin-kibana.dailyhunt.in](http://dh-sysadmin-kibana.dailyhunt.in) | 192.168.1.20 | ElasticSearch         |
|       |                                                                           |              | Monitoring            |
|       |                                                                           |              | (Supervisord)\        |
|       |                                                                           |              | Grafana               |
|       |                                                                           |              | (Supervisord)\        |
|       |                                                                           |              | Kibana (Supervisord)\ |
|       |                                                                           |              | Nginx (Supervisord)\  |
|       |                                                                           |              | Redis Stats Collector |
|       |                                                                           |              | (Cron)\               |
|       |                                                                           |              | ElasticSearch         |
|       |                                                                           |              | Indexing Alert        |
|       |                                                                           |              | (Cron)\               |
|       |                                                                           |              | ES Curator Cleanup    |
|       |                                                                           |              | (Cron)                |
+-------+---------------------------------------------------------------------------+--------------+-----------------------+
| 3     | [dh-sysadmin-es-n5.dailyhunt.in](http://dh-sysadmin-es-n5.dailyhunt.in)   | 192.168.1.21 | ElasticSearch         |
+-------+---------------------------------------------------------------------------+--------------+-----------------------+
| 4     | [dh-sysadmin-es-n4.dailyhunt.in](http://dh-sysadmin-es-n4.dailyhunt.in)   | 192.168.1.22 | ElasticSearch         |
+-------+---------------------------------------------------------------------------+--------------+-----------------------+
| 5     | [dh-sysadmin-es-n3.dailyhunt.in](http://dh-sysadmin-es-n3.dailyhunt.in)   | 192.168.1.28 | ElasticSearch         |
+-------+---------------------------------------------------------------------------+--------------+-----------------------+
| 6     | [dhxen-admin-es-n1.dailyhunt.in](http://dhxen-admin-es-n1.dailyhunt.in)   | 192.168.5.21 | ElasticSearch         |
+-------+---------------------------------------------------------------------------+--------------+-----------------------+
| 7     | [admin-grafana.dailyhunt.in](http://admin-grafana.dailyhunt.in)           | 192.168.7.56 | Jenkins\              |
|       |                                                                           |              | Nginx\                |
|       |                                                                           |              | Httpd (bugsquash)     |
+-------+---------------------------------------------------------------------------+--------------+-----------------------+
| 8     | [admin-gerrit.dailyhunt.in](http://admin-gerrit.dailyhunt.in)             | 192.168.7.18 | Gerrit\               |
|       |                                                                           |              | MySQL\                |
|       |                                                                           |              | Httpd (gitlist)       |
+-------+---------------------------------------------------------------------------+--------------+-----------------------+

\
