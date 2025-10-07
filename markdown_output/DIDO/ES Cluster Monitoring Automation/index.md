This automation used to monitor ES cluster and Send the metrics to our
infra ES cluster. We are adding monitoring ES cluster nodes behind our
nginx server proxy, so that if any one of ES node down, still we can
continue the cluster monitoring through connecting other vms.

##### Add Nginx proxy for monitoring ES cluster.

Login into 192.168.1.20 machine and open nginx conf file.

Nginx Conf - */mnt/vol1/dh-devops/nginx/conf.d/nginx.conf*

Choose one new unused port in 920x series and assign it to new reverse
proxy with \"es-devops.dailyhunt.in\"

Please find the same config below.

\

\$ vi */mnt/vol1/dh-devops/nginx/conf.d/nginx.conf*

upstream es_search { server 192.168.132.14:9201; server
192.168.132.27:9201; server 192.168.132.29:9201; server
192.168.132.31:9201; server 192.168.132.33:9201; } server { listen 9204;
server_name es-devops.dailyhunt.in; location / { proxy_pass
http://es_search; proxy_set_header X-Forwarded-For \$remote_addr;
proxy_set_header Host \$host; } }

Now reload the nginx service,

\$ /mnt/vol1/dh-devops/nginx/sbin/nginx -s reload

Please make sure the nginx reverse proxy is working fine. In the above
example, I used port 9204. So the url check will be,

<http://es-devops.dailyhunt.in:9204/_cat/nodes?v>

##### Adding and Starting service to Monitor ES cluster:

Now we have to start the service through supervisord to monitor the ES
cluster.

In the same 192.168.1.20 machine, move into supervisord ini directory.

\$ cd /mnt/vol1/dh-devops/supervisord/supervisord.d

Now you can create new ini file like below to configure ES cluster
monitoring. In the below example, you have to modify three lines.

1.  command =
    /mnt/vol1/dh-devops/grafana-4.6.3/scripts/es_metrics_collector.py
    ***http://es-devops.dailyhunt.in:9204***

    In this command, the url will be your nginx proxy url.

2.  stdout_logfile =
    /mnt/vol2/dh-devops-data/elasticsearch/logs/es_dh_search_metrics.log

3.  stderr_logfile =
    /mnt/vol2/dh-devops-data/elasticsearch/logs/es_dh_search_metrics_err.log

\$ vi es_dh_search_metrics.ini

\[program:es_dh_search\] directory =
/mnt/vol1/dh-devops/grafana-4.6.3/scripts command =
/mnt/vol1/dh-devops/grafana-4.6.3/scripts/es_metrics_collector.py
http://es-devops.dailyhunt.in:9204 user = phoenix.admin autostart = true
autorestart = true stopsignal = QUIT redirect_stderr = true
stdout_logfile =
/mnt/vol2/dh-devops-data/elasticsearch/logs/es_dh_search_metrics.log
stderr_logfile =
/mnt/vol2/dh-devops-data/elasticsearch/logs/es_dh_search_metrics_err.log
logfile_maxbytes = 10MB

Once the supervisord ini file is created, please reread and update
supervisorctl to start newly added service.

\$ supervisorctl reread

\$ supervisorctl update

\$ supervisorctl status \<service name\>

Now The service started to monitor the ES cluster metrics and pushing
the data to our ES cluster. Next we are going to create dashboard in
grafana to visualize the ES Cluster metrics.

###  Creating Dashboard for ES Cluster Metrics: 

1.  Login into Grafana.

    Url - <http://admin-stats.dailyhunt.in/login>

    User - dh-devops

2.  Switch into DevOps organization and Save the \"ES DevOps Cluster
    Dashboard\" json in your local computer using Export and \"Save to
    file\" option.

    \

3.  Now Switch into respective organization where you want to create
    dashboard.

4.  Add DataSource of ES Metrics Index Name If it is not exist already,
    Please refer  to add DataSource. For ES metrcis, the index name
    always be**elasticsearch_metrics-\***.\
    \
    \

5.  Once the DataSource Creation is done, Click Grafana Icon on the top
    left size and Move the cursor to Dashboard and Click \"Import\".\
    \
    \
    \

6.  Click \"Upload .json File\" and Open Previously Exported Json file
    from your local computer.\
    \
    \
    \

7.  Now Edit Your Dashboard Name and Select respective DataSource in the
    drop down.\
    \
    \
    \

8.  Change the ES cluster name to view recently monitoring added ES
    cluster metrics. You can find cluster_name on nginx proxy url, In my
    case <http://es-devops.dailyhunt.in:9204/>\
    \
    \
    \
    \
    \

9.  Click the close \"**x**\" and Save the dashboard by clicking the
    Save icon in the top of the dashboard.\
    \

10. Final Dashboard,\
    \
    \
    \
    \

That is it. Now We have enabled Monitoring for ES cluster and Created
Dashboard for The ES cluster metrics. 

\

**-Sanal K**
