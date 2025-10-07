#### Source Code:

[<http://devops.dailyhunt.in/gitlist/index.php/dh-sysadmin.git/blob/master/Scripts/python/lbstats.py>]{style="color: rgb(39,78,19);"}

###### Requirements:

1.  Python 2.7.x
2.  Python Modules\
    -  urllib2\
    -  urllib\
    - elasticsearch\
    - dateutil  \
    \

[**Usage: **]{.underline}

    usage: lbstats.py [-h] -LBH LBHOST [-LBN LBNAME [LBNAME ...]]

The Python Script running every minute at 192.168.2.224 machine through
cron(root). It is connecting the nitro api and collecting current lb
data to send to ES cluster.

#### Crontab Entry at 192.168.2.224:

    * * * * * /home/selvam.mariappan/lbstats.py -LBH 192.168.168.253 &>> /home/selvam.mariappan/lbstats_logs/lbstats_`date +\%F`.log
    * * * * * /home/selvam.mariappan/lbstats.py -LBH 192.168.168.254 &>> /home/selvam.mariappan/lbstats_logs/lbstats_`date +\%F`.log
    * * * * * /home/selvam.mariappan/lbstats.py -LBH 192.168.1.251 &>> /home/selvam.mariappan/lbstats_logs/lbstats_`date +\%F`.log
    * * * * * /home/selvam.mariappan/lbstats.py -LBH 192.168.1.247 &>> /home/selvam.mariappan/lbstats_logs/lbstats_`date +\%F`.log

### Grafana Dashboard:

<http://admin-stats.dailyhunt.in/dashboard/db/lbstats-filter-dashboard?orgId=2>

Please get lbrule name for the respective domain requests from Network
team and search and select it in the ***lbrule*** option.

 

#### Reference:

<https://developer-docs.citrix.com/projects/netscaler-nitro-api/en/11.0/statistics/load-balancing/lbvserver/lbvserver/>

\

\~ SELVAM
