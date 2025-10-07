Redis Cluster provides a way to run a Redis installation where data is
automatically shared across multiple Redis nodes.

Redis Cluster also provides some degree of availability during
partitions, that is in practical terms the ability to continue the
operations when some nodes fail or are not able to communicate. 

1.  Login into any one of redis instance  (10.50.24.96)

2.  Do the following steps as any common user (i.e dh-ads,dh-aiml...etc)

3.  To know the location of supervisord config file use the following\
    **Cmd**:**  ps -ef \|grep supervisord**

4.  Then open the config file to know the location of .ini files\
    **Cmd: cat  /mnt/vol1/dh-ads/supervisord/supervisord.conf**

5.  Go to location of .ini files\
    **Cmd: cd /mnt/vol1/dh-ads/supervisord/supervisord.d**\
    **ls**

6.  The create .ini file \
    **Cmd: vim name_file.ini**

**Example:**

\[program:redis-server_8001\]

***command=/mnt/vol1/dh-ads/redis-5.0.3/bin/redis-server
/mnt/vol1/dh-ads/redis-5.0.3/redis_config/8001/redis_8001.conf***

autostart=true

autorestart=true

user=dh-ads

redirect_stderr=true

stdout_logfile=/mnt/vol2/dh-ads-data/logs/worker-std-out.log

stderr_logfile=/mnt/vol2/dh-ads-data/logs/worker-std-err.log

Add the above content in .ini file 

**Command** = start command for the redis will be provided by the DB
teamNote: you must create a log directory under 
"/mnt/vol2/dh-ads-data/" this location if its not present

7\. Similarly create .ini files for all specified commands and ports by
db team 

8\. Then run the following commands 

**Cmd** **: supervisorctl**

-reread 

-update

-status 

if u are able to see all the files u have created and status is running
then u have  successfully enabled the supervisor 

9\. Now follow same steps for all the specified redis instances
