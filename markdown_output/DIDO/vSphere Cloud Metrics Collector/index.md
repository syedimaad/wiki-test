Using MOB or Managed Object Browser, we are collecting the ESXi  and 
VMs metrics details with run time information.

[**More details about MOB:**]{.underline}

[v](https://pubs.vmware.com/vsphere-50/index.jsp?topic=%2Fcom.vmware.wssdk.pg.doc_50%2FPG_ChB_Using_MOB.20.1.html)[Sphere 
MOB](https://pubs.vmware.com/vsphere-50/index.jsp?topic=%2Fcom.vmware.wssdk.pg.doc_50%2FPG_ChB_Using_MOB.20.1.html)

###### source:

<http://devops.dailyhunt.in/gitlist/index.php/dh-sysadmin.git/tree/master/vSphereAPI/>

###### perquisites:

1.  MOB should be enabled at vcenter
2.  Python 3.6 or greater
3.  Python modules i.e pyVmomi, pyVim

## Cloud Metrics Analytics Setup Architecture:

## Update Cloud Meta Data

Update vpshere cloud and authentication details in cloud_meta.yml file
in the source folder.

For example.

dh1: host: \'192.168.2.224\' port: \'5443\' user: \'vs-user\' passwd:
\'t3ch@b@ng123\' data_path: \'/mnt/vol2/CloudData/\' esxi_metrics: cpu:
\[\'cpu.ready.summation\', \'cpu.usagemhz.average\',
\'cpu.usage.average\'\] memory: \[\'mem.active.average\',
\'mem.consumed.average\', \'mem.granted.average\',
\'mem.shared.average\', \'mem.sharedcommon.average\',
\'mem.usage.average\'\] disk: \[\'disk.maxTotalLatency.latest\',
\'disk.usage.average\', \'disk.read.average\', \'disk.write.average\'\]
vm_metrics: cpu: \[\'cpu.usage.average\'\] memory:
\[\'mem.usage.average\', \'mem.consumed.average\',
\'mem.entitlement.average\', \'mem.granted.average\'\] disk:
\[\'disk.maxTotalLatency.latest\', \'disk.usage.average\',
\'disk.read.average\', \'disk.write.average\'\]

***data_path***      -  Directory where we are storing our final json
files. 

***esxi_metrics***  - Please mention what are the metrics you want to
monitor in ESXi and its sub metrics values.

***vm_metrics***    - Please mention what are the metrics you want to
monitor in VMs and its sub metrics values.

## Collecting ESXi metrics:

We are collecting ESXi metrics
using [esxihosts_metrics_usage.py](http://devops.dailyhunt.in/gitlist/index.php/dh-sysadmin.git/blob/master/vSphereAPI/esxihosts_metrics_usage.py)
and passing the cloud name i.e dh1 or dh2 as argument. 

[**Usage:**]{.underline}

/usr/local/bin/python3.6 vSphereAPI/esxihosts_metrics_usage.py dh2

## Collecting VMs Metrics:

Like ESXi, we are collecting the vm metrics details in the cloud
using [vmhosts_metrics_usage.py](http://devops.dailyhunt.in/gitlist/index.php/dh-sysadmin.git/blob/master/vSphereAPI/vmhosts_metrics_usage.py)
script. Here also we have to pass the cloud name as argument.

[**Usage:**]{.underline}

/usr/local/bin/python3.6
\${REPO_PATH}/vSphereAPI/vmhosts_metrics_usage.py dh1

## Execution Details:

We are running the ESXi and VMs metrics collector script every hour 1st
and 31st minute through crontab along with cloud name and It is
collecting last 30 minutes data from 00:00 to 29:59 and 30:00 to 59:59
respectively when run at half hour interval.

 It is writing the data into /mnt/vol2/CloudData/\<YYYY-MM-DD\>
directory in json format.

We are running the script at 192.168.2.36 machine\'s crontab.

#### Crontab Entry:

    REPO_PATH=/mnt/vol1/dh-devops/dh-sysadmin
    01,31 * * * * /usr/local/bin/python3.6 ${REPO_PATH}/vSphereAPI/vmhosts_metrics_usage.py dh1 >> /mnt/vol2/logs/dh1_vm_metrics.log
    01,31 * * * * /usr/local/bin/python3.6 ${REPO_PATH}/vSphereAPI/vmhosts_metrics_usage.py dh2 >> /mnt/vol2/logs/dh2_vm_metrics.log
    01,31 * * * * /usr/local/bin/python3.6 ${REPO_PATH}/vSphereAPI/esxihosts_metrics_usage.py dh1 >> /mnt/vol2/logs/dh1_esxi_metrics.log
    01,31 * * * * /usr/local/bin/python3.6 ${REPO_PATH}/vSphereAPI/esxihosts_metrics_usage.py dh2 >> /mnt/vol2/logs/dh2_esxi_metrics.log

## Push The json Data to ES using Logstash:

Once the data updated in the json file
in /mnt/vol2/CloudData/\<YYYY-MM-DD\> directory, the logstash will
automatically push the updated json data to our ES cluster.

[**Logstash conf in our repo:**]{.underline}

<http://devops.dailyhunt.in/gitlist/index.php/dh-sysadmin.git/blob/master/ElasticSearch/Logstash/logstash.conf_2.36>

[**Logstash path on server 192.168.2.36:**]{.underline}

/mnt/vol1/dh-devops/logstash/config/logstash.conf

## Grafana Dashboards For Cloud Metrics Data:

All Cloud ESXi Metrics Details
- [http://admin-stats.dailyhunt.in/dashboard/db/vsphere-esxi-metrics](http://admin-stats.dailyhunt.in/dashboard/db/vsphere-esxi-metrics){style="letter-spacing: 0.0px;"}

DH1 Cloud Metrics
- <http://admin-stats.dailyhunt.in/dashboard/db/dh1-cloud?orgId=1>

DH2 Grid 1 Metrics
- <http://admin-stats.dailyhunt.in/dashboard/db/dh2-grid-01-cluster?orgId=1>

DH2 Grid 2 Metrics
- <http://admin-stats.dailyhunt.in/dashboard/db/dh2-grid-02-cluster?orgId=1>

DH2 Grid 3 Metrics
- <http://admin-stats.dailyhunt.in/dashboard/db/dh2-grid-03-cluster?orgId=1>

\

\

\~ SELVAM
