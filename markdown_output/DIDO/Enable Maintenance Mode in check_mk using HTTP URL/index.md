This documentation will use to add specific service or host in
Maintenance mode in check_mk using curl script. So it could be automated
whenever we have planned activity.

### [Add downtime for specific service:]{.underline}

\$ [curl
\"]{style="color: rgb(85,85,85);"}[[http://infra-overseer.dailyhunt.in/dailyhunt/check_mk/view.py?output_format=json&\_transid=-1&\_do_confirm=yes&\_do_actions=yes&&\_username=infra-overseer&\_secret=AHLFBWHYIXHNMVXIHAAX&view_name=service&host=]{.nolink}]{.wikiexternallink
style="color: rgb(85,85,85);"}***\<hostname\>***[&service=]{style="color: rgb(85,85,85);"}***\<servicename\>***[&\_down_comment=]{style="color: rgb(85,85,85);"}***\<downtime
comments\>***[&\_down_from_now=yes&\_down_minutes=]{style="color: rgb(85,85,85);"}***\<downtime
in minutes\>***[\"]{style="color: rgb(85,85,85);"}

Ex:-

bashcurl
\"http://infra-overseer.dailyhunt.in/dailyhunt/check_mk/view.py?output_format=json&\_transid=-1&\_do_confirm=yes&\_do_actions=yes&&\_username=infra-overseer&\_secret=AHLFBWHYIXHNMVXIHAAX&view_name=service&host=admin-grafana.dailyhunt.in&service=Filesystem%20/&\_down_comment=test&\_down_from_now=yes&\_down_minutes=15\"

Sample Output:-

MESSAGE: Successfully sent 1
commands.\[\[\"sitealias\",\"host\",\"service_description\",\"service_icons\",\"service_state\",\"svc_group_memberlist\",\"svc_servicelevel\",\"svc_contact_groups\",\"svc_contacts\",\"svc_plugin_output\",\"svc_long_plugin_output\",\"svc_perf_data\",\"perfometer\",\"svc_check_command\",\"svc_check_interval\",\"svc_attempt\",\"svc_notification_number\",\"svc_check_type\",\"svc_state_age\",\"svc_last_time_ok\",\"svc_check_age\",\"svc_next_check\",\"svc_next_notification\",\"svc_last_notification\",\"svc_check_latency\",\"svc_check_duration\",\"svc_in_downtime\",\"svc_in_notifper\",\"svc_notifper\",\"service_display_name\",\"svc_custom_vars\",\"check_manpage\",\"svc_custom_notes\",\"svc_pnpgraph\"\],\[\"dailyhunt1\",\"admin-grafana.dailyhunt.in\",\"Filesystem
/\",\"rulesets pnp\",\"WARN\",\"\",\"\",\"check-mk-notify,
Eben-Notification, Newshunt-Admins\",\"anurag.saxena1, busupalli.raghu,
check-mk-notify, deepak.athreya.cs, mohamed.ibrahim, nagarajan.sg,
phoenix-support, ravi.kushwaha1, selvam.mariappan, shaji.narayanan1,
sreeraj.va1, srinivas.kanneboyina, sysadmin-alerts,
verse-support-eben\",\"WARN - 85.5% used (6.62 of 7.75 GB), (levels at
80.00/90.00%), trend: -84.90 kB / 24 hours, inodes available
438k/83.55%\",\"\",\"/=6781.3671875MB;6347.54375;7140.986719;0;7934.429688
growth=0;;;; trend=-0.082909;;;0;330.601237\",\"85.47
%\",\"check_mk-df\",\"60s/120s\",\"1/1\",\"18981\",\"PASSIVE\",\"2017-07-22
16:21:23\",\"2017-07-22 13:16:49\",\"3 sec\",\"2017-07-22
16:22:23\",\"in 57 sec\",\"2 min\",\"0.000 sec\",\"0.000
sec\",\"no\",\"yes\",\"24X7\",\"Filesystem /\",\"\",\" This check
measures the usage of filesystems. The usage is checked against a
warning and a critical level, which can be specified in numerous ways.
Beware: on Linux and UNIX systems the filesystem might reserve a certain
amount for root (typical is 5%). This checks considers that reserved
space as used. This is consistent with the percentage-column in the
output of df on most distributions. So your filesystem might be at 100%
in a situation where root still has 5% free space available. On some
distributions, df seems to use the user allocatable space instead of the
total filesystem size as base for the percentage calculation, this might
result in differences between the percentage values shown by that df
version and the value shown in Check_MK. From our point of view, the
calculation of Check_MK is more accurate. Trends: This checks supports
filesystem trends. This means that the df check is able to compute the
change of the used space over the time and can make a forecast into the
future. It can estimate the time when the filesystem will be full. In
the default configuration the check will compute the trend based on the
data of the last 24 hours using a logarithmic average that gives more
recent data a higher weight. Also data beyond the 24 hours will to some
small degree be reflected in the computation. The advantage of this
algorithm is a more precise prediction and a simpler implementation,
which does not need any access to any RRDs or similar storage. Please
note that when a filesystem is started to be monitored, the trend of the
past is unknown and is assumed to be zero. It will take at least one
trend range of time until the trend approximately reflects the reality.
Grouping: In some situations you do not want to monitor a single
filesystem but a group of filesystems forming a pool. Only the total
usage of the pool is of interest. The df check supports pools by
defining groups. For each group you specify a name and a list of
globbing patterns (path patterns containing \* and ?). The name is being
used as the check item. All filesystems that match one of the patterns
are part of the pool. When using inventory you specify the groups with
the ruleset filesystem_groups. When configuring manual checks, you
specify the list of patterns in the check parameter
\\\"patterns\\\".\",\"\",\"render_pnp_graphs(\'dailyhunt1_admin-grafana.dailyhunt.in_Filesystem
/\_graph\', \'dailyhunt1\', \'admin-grafana.dailyhunt.in\', \'Filesystem
/\', \'1\', \'/dailyhunt/check_mk/\',
\'http://192.168.7.65/dailyhunt1/pnp4nagios/\', false, \'Add this graph
to\...\', null, null)\"\]

\

    If there is a space in the service name, we have to replace it with %20 in http url. 

### [Remove downtime on specific service:]{.underline}

\$ [curl
\"]{style="color: rgb(85,85,85);"}[[http://infra-overseer.dailyhunt.in/dailyhunt/check_mk/view.py?output_format=json&\_transid=-1&\_do_confirm=yes&\_do_actions=yes&\_username=infra-overseer&\_secret=AHLFBWHYIXHNMVXIHAAX&view_name=service&service=]{.nolink}]{.wikiexternallink
style="color: rgb(85,85,85);"}***\<servicename\>***[&host=]{style="color: rgb(85,85,85);"}***\<hostname\>***[&\_down_remove=Remove%20all\"]{style="color: rgb(85,85,85);"}

[Ex:-]{style="color: rgb(85,85,85);"}

bashcurl
\"http://infra-overseer.dailyhunt.in/dailyhunt/check_mk/view.py?output_format=json&\_transid=-1&\_do_confirm=yes&\_do_actions=yes&\_username=infra-overseer&\_secret=AHLFBWHYIXHNMVXIHAAX&view_name=service&service=Filesystem%20/&host=admin-grafana.dailyhunt.in&\_down_remove=Remove%20all\"

[Sample Output:-]{style="color: rgb(85,85,85);"}

MESSAGE: Successfully sent 1
commands.\[\[\"sitealias\",\"host\",\"service_description\",\"service_icons\",\"service_state\",\"svc_group_memberlist\",\"svc_servicelevel\",\"svc_contact_groups\",\"svc_contacts\",\"svc_plugin_output\",\"svc_long_plugin_output\",\"svc_perf_data\",\"perfometer\",\"svc_check_command\",\"svc_check_interval\",\"svc_attempt\",\"svc_notification_number\",\"svc_check_type\",\"svc_state_age\",\"svc_last_time_ok\",\"svc_check_age\",\"svc_next_check\",\"svc_next_notification\",\"svc_last_notification\",\"svc_check_latency\",\"svc_check_duration\",\"svc_in_downtime\",\"svc_in_notifper\",\"svc_notifper\",\"service_display_name\",\"svc_custom_vars\",\"check_manpage\",\"svc_custom_notes\",\"svc_pnpgraph\"\],\[\"dailyhunt1\",\"admin-grafana.dailyhunt.in\",\"Filesystem
/\",\"rulesets pnp downtime
comment\",\"WARN\",\"\",\"\",\"check-mk-notify, Eben-Notification,
Newshunt-Admins\",\"anurag.saxena1, busupalli.raghu, check-mk-notify,
deepak.athreya.cs, mohamed.ibrahim, nagarajan.sg, phoenix-support,
ravi.kushwaha1, selvam.mariappan, shaji.narayanan1, sreeraj.va1,
srinivas.kanneboyina, sysadmin-alerts, verse-support-eben\",\"WARN -
85.5% used (6.62 of 7.75 GB), (levels at 80.00/90.00%), trend: +12.20 kB
/ 24 hours, inodes available
438k/83.55%\",\"\",\"/=6781.49609375MB;6347.54375;7140.986719;0;7934.429688
growth=0;;;; trend=0.011919;;;0;330.601237\",\"85.47
%\",\"check_mk-df\",\"60s/120s\",\"1/1\",\"19076\",\"PASSIVE\",\"2017-07-22
16:21:23\",\"2017-07-22 13:16:49\",\"47 sec\",\"2017-07-22
16:22:23\",\"46 sec in the past!\",\"3 min\",\"0.000 sec\",\"0.000
sec\",\"yes\",\"yes\",\"24X7\",\"Filesystem /\",\"\",\" This check
measures the usage of filesystems. The usage is checked against a
warning and a critical level, which can be specified in numerous ways.
Beware: on Linux and UNIX systems the filesystem might reserve a certain
amount for root (typical is 5%). This checks considers that reserved
space as used. This is consistent with the percentage-column in the
output of df on most distributions. So your filesystem might be at 100%
in a situation where root still has 5% free space available. On some
distributions, df seems to use the user allocatable space instead of the
total filesystem size as base for the percentage calculation, this might
result in differences between the percentage values shown by that df
version and the value shown in Check_MK. From our point of view, the
calculation of Check_MK is more accurate. Trends: This checks supports
filesystem trends. This means that the df check is able to compute the
change of the used space over the time and can make a forecast into the
future. It can estimate the time when the filesystem will be full. In
the default configuration the check will compute the trend based on the
data of the last 24 hours using a logarithmic average that gives more
recent data a higher weight. Also data beyond the 24 hours will to some
small degree be reflected in the computation. The advantage of this
algorithm is a more precise prediction and a simpler implementation,
which does not need any access to any RRDs or similar storage. Please
note that when a filesystem is started to be monitored, the trend of the
past is unknown and is assumed to be zero. It will take at least one
trend range of time until the trend approximately reflects the reality.
Grouping: In some situations you do not want to monitor a single
filesystem but a group of filesystems forming a pool. Only the total
usage of the pool is of interest. The df check supports pools by
defining groups. For each group you specify a name and a list of
globbing patterns (path patterns containing \* and ?). The name is being
used as the check item. All filesystems that match one of the patterns
are part of the pool. When using inventory you specify the groups with
the ruleset filesystem_groups. When configuring manual checks, you
specify the list of patterns in the check parameter
\\\"patterns\\\".\",\"\",\"render_pnp_graphs(\'dailyhunt1_admin-grafana.dailyhunt.in_Filesystem
/\_graph\', \'dailyhunt1\', \'admin-grafana.dailyhunt.in\', \'Filesystem
/\', \'1\', \'/dailyhunt/check_mk/\',
\'http://192.168.7.65/dailyhunt1/pnp4nagios/\', false, \'Add this graph
to\...\', null, null)\"\]

### [Add downtime for a host:]{.underline}

\$ [curl
\"]{style="color: rgb(85,85,85);"}[[http://infra-overseer.dailyhunt.in/dailyhunt/check_mk/view.py?output_format=json&\_transid=-1&\_do_confirm=yes&\_do_actions=yes&&\_username=infra-overseer&\_secret=AHLFBWHYIXHNMVXIHAAX&view_name=hoststatus&host=]{.nolink}]{.wikiexternallink
style="color: rgb(85,85,85);"}***\<hostname\>***[&\_down_comment=]{style="color: rgb(85,85,85);"}***\<downtime
comments\>***[&\_down_from_now=yes&\_down_minutes=]{style="color: rgb(85,85,85);"}***\<downtime
in mins\>***[\"]{style="color: rgb(85,85,85);"}

Ex:-

bashcurl
\"http://infra-overseer.dailyhunt.in/dailyhunt/check_mk/view.py?output_format=json&\_transid=-1&\_do_confirm=yes&\_do_actions=yes&&\_username=infra-overseer&\_secret=AHLFBWHYIXHNMVXIHAAX&view_name=hoststatus&host=admin-grafana.dailyhunt.in&\_down_comment=test&\_down_from_now=yes&\_down_minutes=15\"

Sample Output:-

MESSAGE: Successfully sent 1
commands.\[\[\"sitealias\",\"host\",\"alias\",\"host_icons\",\"host_state\",\"host_address\",\"host_group_memberlist\",\"host_parents\",\"host_childs\",\"host_servicelevel\",\"host_contact_groups\",\"host_contacts\",\"host_plugin_output\",\"host_perf_data\",\"host_attempt\",\"host_notification_number\",\"host_check_interval\",\"host_check_type\",\"host_state_age\",\"host_check_age\",\"host_next_check\",\"host_next_notification\",\"host_last_notification\",\"host_check_latency\",\"host_check_duration\",\"host_in_downtime\",\"host_in_notifper\",\"host_notifper\",\"host_custom_vars\",\"num_services\",\"num_services_ok\",\"num_services_warn\",\"num_services_crit\",\"num_services_unknown\",\"num_services_pending\",\"host_custom_notes\",\"host_pnpgraph\"\],\[\"dailyhunt1\",\"admin-grafana.dailyhunt.in\",\"admin-grafana.dailyhunt.in\",\"rulesets
pnp
aggr\",\"UP\",\"192.168.7.56\",\"Newshunt-Admin-Servers\",\"\",\"\",\"\",\"check-mk-notify,
Eben-Notification, Newshunt-Admins\",\"anurag.saxena1, busupalli.raghu,
check-mk-notify, deepak.athreya.cs, mohamed.ibrahim, nagarajan.sg,
phoenix-support, ravi.kushwaha1, selvam.mariappan, shaji.narayanan1,
sreeraj.va1, srinivas.kanneboyina, sysadmin-alerts,
verse-support-eben\",\"OK - 192.168.7.56: rta 0.329ms, lost
0%\",\"rta=0.329ms;200.000;500.000;0; pl=0%;40;80;; rtmax=0.801ms;;;;
rtmin=0.177ms;;;;\",\"1/1\",\"0\",\"180s/60s\",\"ACTIVE\",\"2017-06-16
08:40:30\",\"2 min\",\"in 48 sec\",\"-\",\"-\",\"0.087 sec\",\"0.008
sec\",\"no\",\"yes\",\"24X7\",\"\",\"21\",\"20\",\"1\",\"0\",\"0\",\"0\",\"\",\"render_pnp_graphs(\'dailyhunt1_admin-grafana.dailyhunt.in\_\_HOST\_\_graph\',
\'dailyhunt1\', \'admin-grafana.dailyhunt.in\', \'\_HOST\_\', \'1\',
\'/dailyhunt/check_mk/\',
\'http://192.168.7.65/dailyhunt1/pnp4nagios/\', false, \'Add this graph
to\...\', null, null)\"\]\]

### [Remove downtime on a host:]{.underline}

\$ [curl
\"]{style="color: rgb(85,85,85);"}[[http://infra-overseer.dailyhunt.in/dailyhunt/check_mk/view.py?output_format=json&\_transid=-1&\_do_confirm=yes&\_do_actions=yes&\_username=infra-overseer&\_secret=AHLFBWHYIXHNMVXIHAAX&view_name=hoststatus&host=]{.nolink}]{.wikiexternallink
style="color: rgb(85,85,85);"}***\<hostname\>***[&\_down_remove=Remove%20all\"]{style="color: rgb(85,85,85);"}

Ex:-

bashcurl
\"http://infra-overseer.dailyhunt.in/dailyhunt/check_mk/view.py?output_format=json&\_transid=-1&\_do_confirm=yes&\_do_actions=yes&\_username=infra-overseer&\_secret=AHLFBWHYIXHNMVXIHAAX&view_name=hoststatus&host=admin-grafana.dailyhunt.in&\_down_remove=Remove%20all\"

Sample Output:-

MESSAGE: Successfully sent 1
commands.\[\[\"sitealias\",\"host\",\"alias\",\"host_icons\",\"host_state\",\"host_address\",\"host_group_memberlist\",\"host_parents\",\"host_childs\",\"host_servicelevel\",\"host_contact_groups\",\"host_contacts\",\"host_plugin_output\",\"host_perf_data\",\"host_attempt\",\"host_notification_number\",\"host_check_interval\",\"host_check_type\",\"host_state_age\",\"host_check_age\",\"host_next_check\",\"host_next_notification\",\"host_last_notification\",\"host_check_latency\",\"host_check_duration\",\"host_in_downtime\",\"host_in_notifper\",\"host_notifper\",\"host_custom_vars\",\"num_services\",\"num_services_ok\",\"num_services_warn\",\"num_services_crit\",\"num_services_unknown\",\"num_services_pending\",\"host_custom_notes\",\"host_pnpgraph\"\],\[\"dailyhunt1\",\"admin-grafana.dailyhunt.in\",\"admin-grafana.dailyhunt.in\",\"rulesets
pnp hostdowntime comment
aggr\",\"UP\",\"192.168.7.56\",\"Newshunt-Admin-Servers\",\"\",\"\",\"\",\"check-mk-notify,
Eben-Notification, Newshunt-Admins\",\"anurag.saxena1, busupalli.raghu,
check-mk-notify, deepak.athreya.cs, mohamed.ibrahim, nagarajan.sg,
phoenix-support, ravi.kushwaha1, selvam.mariappan, shaji.narayanan1,
sreeraj.va1, srinivas.kanneboyina, sysadmin-alerts,
verse-support-eben\",\"OK - 192.168.7.56: rta 0.369ms, lost
0%\",\"rta=0.369ms;200.000;500.000;0; pl=0%;40;80;; rtmax=0.848ms;;;;
rtmin=0.200ms;;;;\",\"1/1\",\"0\",\"180s/60s\",\"ACTIVE\",\"2017-06-16
08:40:30\",\"19 sec\",\"in 2 min\",\"-\",\"-\",\"17.539 sec\",\"0.008
sec\",\"yes\",\"yes\",\"24X7\",\"\",\"21\",\"20\",\"1\",\"0\",\"0\",\"0\",\"\",\"render_pnp_graphs(\'dailyhunt1_admin-grafana.dailyhunt.in\_\_HOST\_\_graph\',
\'dailyhunt1\', \'admin-grafana.dailyhunt.in\', \'\_HOST\_\', \'1\',
\'/dailyhunt/check_mk/\',
\'http://192.168.7.65/dailyhunt1/pnp4nagios/\', false, \'Add this graph
to\...\', null, null)\"\]\]

\

### Automation Script

[http://devops.dailyhunt.in/gitlist/index.php/dh-sysadmin.git/blob/master/Check_mk/check_mk_maintenance.py](http://devops.dailyhunt.in/gitlist/index.php/dh-sysadmin.git/blob/master/Check_mk/dailyhunt.sh)

\

usage: check_mk_maintenance.py \[-h\] -H HOST \[-s SERVICES \[SERVICES
\...\]\]\
\[-d DURATION\] \[-r\]

This script is used to add/remove maintenance of host or services in
check_mk

optional arguments:\
-h, \--help show this help message and exit\
-H HOST, \--host HOST Enter hostname which is configured in check-mk\
-s SERVICES \[SERVICES \...\], \--services SERVICES \[SERVICES \...\]\
Enter the service name\
-d DURATION, \--duration DURATION\
Enter the maintenance time period in minutes\
-r, \--remove

\

[Examples:]{.underline}

- Add host in maintenance    => /usr/bin/python check_mk_maintenance.py -H sysadmin-test-n1.dailyhunt.in -d 1440

- Add Service in maintenance                =\>   /usr/bin/python
  check_mk_maintenance.py -H sysadmin-test-n1.dailyhunt.in -s \'Memory
  used\' \'CPU load\' -d 60

- Remove Service from maintenance  =\>   /usr/bin/python
  check_mk_maintenance.py -H sysadmin-test-n1.dailyhunt.in -s \'Memory
  used\' -r

- Remove host from maintenance        =\>  /usr/bin/python
  check_mk_maintenance.py -H sysadmin-test-n1.dailyhunt.in -r
