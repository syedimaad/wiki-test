[You can download the redis monitoring script(check_redis.pl) from the
url
\"<http://devops.dailyhunt.in/repo/scripts/nagios_plugins/check_port.pl>\"]{style="color: rgb(85,85,85);"}

[The script has the below perquisite to run on machine. It will be
installed by ansible playbook
[redis_install.yml](http://devops.dailyhunt.in/gitlist/index.php/dh-sysadmin.git/blob/master/Ansible/playbooks/roles/redis_install/tasks/main.yml).]{style="color: rgb(85,85,85);"}

\

1. [[epel-release-6-8.noarch.rpm](http://devops.dailyhunt.in/repo/rpms/centos-6.8/epel-release-6-8.noarch.rpm)]{.wikiexternallink}

2\. perl-Redis

3\. perl-Nagios-Plugin.noarch

\

The check_redis.pl script will support all kind of monitoring for redis
cluster.

You can find the script usage below. 

#### **Redis Cluster and Node Check:**

bash\$ /etc/check_mk/check_redis.pl -H \<redis_node\> -p \<port\> ex. \$
/etc/check_mk/check_redis.pl -H 192.168.3.64 -p 7001

**Redis Replication Status:**

[It should be run for all redis slave nodes if the redis cluster has
slave.]{style="color: rgb(85,85,85);"}

bash\$ /etc/check_mk/check_redis.pl -H \<slave-node\> -p \<port\> -r
\<replication_warn_in_seconds,replication_crit_in_seconds\> ex. \$
/etc/check_mk/check_redis.pl -H 192.168.3.63 -p 7001 -r 12,20

#### **Redis Memory Usage:**

bash\$ /etc/check_mk/check_redis.pl -H \<redis-node\> -p \<port\> -m
\<WARN:Memory in \[K, M, G\],CRIT: Memory\[K, M, G\]\> -M \<total redis
memory in \[K, M, G\]\> ex. \$ /etc/check_mk/check_redis.pl -H
192.168.3.64 -p 7001 -m WARN:20G,CRIT:30G -M 40G

#### **Redis Connected Clients:**

bash\$ /etc/check_mk/check_redis.pl -H \<redis-node\> -p \<port\>
\--connected_clients=\<WARN:threshold,CRIT:threshold\> ex. \$
/etc/check_mk/check_redis.pl -H 192.168.3.64 -p 7001
\--connected_clients=WARN:700,CRIT:4100

**Redis Keys Count:**

bash\$ /etc/check_mk/check_redis.pl -H \<redis-node\> -p \<port\>
\--total_keys=WARN:\<WARN_keys_threshold\>,CRIT:\<CRIT_keys_threshold\>
ex. \$ /etc/check_mk/check_redis.pl -H 192.168.3.64 -p 7001
\--total_keys=WARN:1750000,CRIT:1850000

\

Redis offset check is not needed instead that we are monitoring
replication in seconds.

\
