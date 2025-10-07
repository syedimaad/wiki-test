Dockerfile:

FROM python:3.11-slim-buster RUN apt update && apt install -y
build-essential && groupadd \--gid 10555 dh-tech-prod \|\| true \\ &&
useradd \--uid 28758 -g dh-tech-prod dh-ads \|\| true \\ && mkdir -p
/home/dh-ads/ \\ && chown -R dh-ads:dh-tech-prod /home/dh-ads/ USER
28758 WORKDIR /app COPY requirements.txt requirements.txt ENV
TZ=Asia/Kolkata RUN pip3 install -r requirements.txt

If you are making any changes to docker file build the new docker image
and use that.

- docker build \--tag \<image_name\> .

  - E.g. docker build \--tag maintenance:latest .

<!-- -->

- docker images

- docker image rm -f \<image_id\>

<!-- -->

- docker container ls

- docker rm -f \<container_id\> 

# MASTER:

\# maintenance process \*/10 \* \* \* \* docker run \--rm -i
\--name=\"maintenance\" -e HOSTNAME=\'dh-gcp-ads-mpe-n1\'  -v
/mnt/vol1/dh-ads/.ssh:/mnt/vol1/dh-ads/.ssh:ro -v
/mnt/vol1/dh-ads/maintenanceEngine:/app maintenance:d795064e bin/run.sh
src/maintenance.py \>\> logs/maintenance_stdout 2\>&1 #pacing process
\*/5 \* \* \* \* docker run \--rm -i \--name=\"pacing\" -e
HOSTNAME=\'dh-gcp-ads-mpe-n1\'  -v
/mnt/vol1/dh-ads/.ssh:/mnt/vol1/dh-ads/.ssh:ro -v
/mnt/vol1/dh-ads/maintenanceEngine:/app maintenance:d795064e bin/run.sh
src/pacing.py \>\> logs/pacing_stdout 2\>&1 #populate billing process
\*/30 \* \* \* \* docker run \--rm -i \--name=\"populate_billing\" -e
HOSTNAME=\'dh-gcp-ads-mpe-n1\' -v
/mnt/vol1/dh-ads/.ssh:/mnt/vol1/dh-ads/.ssh:ro -v
/mnt/vol1/dh-ads/maintenanceEngine:/app maintenance:d795064e bin/run.sh
src/populateBilling.py \>\> logs/populate_billing_stdout 2\>&1 #banners
delivery process \*/2 \* \* \* \* docker run \--rm -i
\--name=\"banners_delivery\" -e HOSTNAME=\'dh-gcp-ads-mpe-n1\' -v
/mnt/vol1/dh-ads/.ssh:/mnt/vol1/dh-ads/.ssh:ro -v
/mnt/vol1/dh-ads/maintenanceEngine:/app maintenance:d795064e bin/run.sh
src/bannersDelivery.py \>\> logs/banners_delivery_stdout 2\>&1 #alerts
process 0 0,7-23 \* \* \* docker run \--rm -i \--name=\"alerts\" -e
HOSTNAME=\'dh-gcp-ads-mpe-n1\' -v
/mnt/vol1/dh-ads/.ssh:/mnt/vol1/dh-ads/.ssh:ro -v
/mnt/vol1/dh-ads/maintenanceEngine:/app maintenance:d795064e bin/run.sh
src/alerts.py \>\> logs/alerts_stdout 2\>&1 #flywheel alert process \*
\* \* \* \* docker run \--rm -i \--name=\"flywheel_alert\" -e
HOSTNAME=\'dh-gcp-ads-mpe-n1\' -v
/mnt/vol1/dh-ads/.ssh:/mnt/vol1/dh-ads/.ssh:ro -v
/mnt/vol1/dh-ads/maintenanceEngine:/app maintenance:d795064e bin/run.sh
src/tasks/flywheelAlertMailer.py \>\> logs/flywheel_alert_stdout 2\>&1
#log cleanup process 05 00 \* \* \*
/mnt/vol1/dh-ads/maintenanceEngine/src/scripts/log_cleanup.sh \>\>
/tmp/log_cleanup.log 2\>&1

# SLAVE

\# maintenance process \*/10 \* \* \* \* docker run \--rm -i
\--name=\"maintenance\" -e HOSTNAME=\'dh-gcp-ads-mpe-n2\'  -v
/mnt/vol1/dh-ads/.ssh:/mnt/vol1/dh-ads/.ssh:ro -v
/mnt/vol1/dh-ads/maintenanceEngine:/app maintenance:d795064e bin/run.sh
src/maintenance.py \>\> logs/maintenance_stdout 2\>&1 #pacing process
\*/5 \* \* \* \* docker run \--rm -i \--name=\"pacing\" -e
HOSTNAME=\'dh-gcp-ads-mpe-n2\'  -v
/mnt/vol1/dh-ads/.ssh:/mnt/vol1/dh-ads/.ssh:ro -v
/mnt/vol1/dh-ads/maintenanceEngine:/app maintenance:d795064e bin/run.sh
src/pacing.py \>\> logs/pacing_stdout 2\>&1 #populate billing process
#\*/30 \* \* \* \* docker run \--rm -i \--name=\"populate_billing\" -e
HOSTNAME=\'dh-gcp-ads-mpe-n2\' -v
/mnt/vol1/dh-ads/.ssh:/mnt/vol1/dh-ads/.ssh:ro -v
/mnt/vol1/dh-ads/maintenanceEngine:/app maintenance:d795064e bin/run.sh
src/populateBilling.py \>\> logs/populate_billing_stdout 2\>&1 #banners
delivery process \*/2 \* \* \* \* docker run \--rm -i
\--name=\"banners_delivery\" -e HOSTNAME=\'dh-gcp-ads-mpe-n2\' -v
/mnt/vol1/dh-ads/.ssh:/mnt/vol1/dh-ads/.ssh:ro -v
/mnt/vol1/dh-ads/maintenanceEngine:/app maintenance:d795064e bin/run.sh
src/bannersDelivery.py \>\> logs/banners_delivery_stdout 2\>&1 #alerts
process #0 0,7-23 \* \* \* docker run \--rm -i \--name=\"alerts\" -e
HOSTNAME=\'dh-gcp-ads-mpe-n2\' -v
/mnt/vol1/dh-ads/.ssh:/mnt/vol1/dh-ads/.ssh:ro -v
/mnt/vol1/dh-ads/maintenanceEngine:/app maintenance:d795064e bin/run.sh
src/alerts.py \>\> logs/alerts_stdout 2\>&1 #log cleanup process 05 00
\* \* \* /mnt/vol1/dh-ads/maintenanceEngine/src/scripts/log_cleanup.sh
\>\> /tmp/log_cleanup.log 2\>&1

# TEST

docker run \--rm -it \--name=\"maintenance_test\" -e
HOSTNAME=\'dh-gcp-ads-mpe-n1\'  -v
/mnt/vol1/dh-ads/.ssh:/mnt/vol1/dh-ads/.ssh:ro -v
/mnt/vol1/dh-ads/maintenanceEngineTest/maintenanceEngine:/app
maintenance:test bin/run.sh src/maintenance.py \>\>
logs/maintenance_stdout 2\>&1

------------------------------------------------------------------------

# VM:

##### PROD:

- Master:
  [dh-gcp-ads-mpe-n1.dailyhunt.in](http://dh-gcp-ads-mpe-n1.dailyhunt.in)

- Slave:
  [dh-gcp-ads-mpe-n2.dailyhunt.in](http://dh-gcp-ads-mpe-n2.dailyhunt.in)

##### STAGE:

- [dh-gcp-ads-pacing-engine-stage-n1.dailyhunt.in](http://dh-gcp-ads-pacing-engine-stage-n1.dailyhunt.in)

------------------------------------------------------------------------

# PATH:

##### PROD:

Repo: /mnt/vol1/dh-ads/maintenanceEngine

Logs: /mnt/vol1/dh-ads/maintenanceEngine/logs

##### TEST ON PROD:

Repo: /mnt/vol1/dh-ads/maintenanceEngineTest/maintenanceEngine

Logs: /mnt/vol1/dh-ads/maintenanceEngineTest/maintenanceEngine/logs

##### STAGE:

Repo: /mnt/vol1/dh-ads/maintenanceEngineTest/maintenanceEngine

Logs: /mnt/vol1/dh-ads/maintenanceEngineTest/maintenanceEngine/logs

------------------------------------------------------------------------

# DEPLOY STEPS:

##### MASTER :

- after pulling new changes, make sure to change `ENV: 'PROD'` in
  conf/application.yml

##### SLAVE:

- after pulling new changes, make sure to change `ENV: 'PROD'` and
  `SERVER_DESIGNATION: 'SLAVE'` in conf/application.yml

------------------------------------------------------------------------

# CHANGE FROM SLAVE TO MASTER:

- open MySQL Shell

  - mysql -h
    [db.internal.ads.dailyhunt.in](http://db.internal.ads.dailyhunt.in)
    \--database=oads -u oads_user -peterno123 -P 38036

  - use daedalus;

- Query:

  - select \* from mpe_statistics order by id desc  limit 10;

    - Sample Result:

    - +\-\-\-\-\-\-\-\--+\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--+\-\-\-\-\-\-\-\-\-\-\--+\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--+
      \| id \| mpe_finish_time \| process_id \| server_designation \|
      +\-\-\-\-\-\-\-\--+\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--+\-\-\-\-\-\-\-\-\-\-\--+\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--+
      \| 1199120 \| 2024-06-05 12:12:21 \| 3 \| MASTER \| \| 1199119 \|
      2024-06-05 12:10:56 \| 2 \| MASTER \| \| 1199118 \| 2024-06-05
      12:10:28 \| 1 \| MASTER \| \| 1199117 \| 2024-06-05 12:10:24 \| 3
      \| MASTER \| \| 1199116 \| 2024-06-05 12:08:20 \| 3 \| MASTER \|
      \| 1199115 \| 2024-06-05 12:06:21 \| 3 \| MASTER \| \| 1199114 \|
      2024-06-05 12:05:24 \| 1 \| MASTER \| \| 1199113 \| 2024-06-05
      12:04:24 \| 3 \| MASTER \| \| 1199112 \| 2024-06-05 12:02:22 \| 3
      \| MASTER \| \| 1199111 \| 2024-06-05 12:01:12 \| 2 \| MASTER \|
      +\-\-\-\-\-\-\-\--+\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--+\-\-\-\-\-\-\-\-\-\-\--+\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--+

- update server_designation from `SLAVE` to `MASTER` for the latest id
  of that process (**pacing**: process_id=1, **maintenance**:
  process_id=2, **banners_delivery**: process_id=3 ).

  - update mpe_statistics set server_designation = \"MASTER\" where id =
    1199118;

------------------------------------------------------------------------

# Grafana Telegraf/Saluber Monitoring:

<https://saluber.dailyhunt.in/d/Ef02z687z/telegraf-applications?orgId=3&refresh=10s>

------------------------------------------------------------------------

Potantial Issue:

**Daily Aggregation Insertion Failed**\
Insertion Failed Either because of duplicate key or database failure

select \* from ox_data_intermediate_ad_zone where partner_id like
\"DH_APP\'nvOpzp%\";update ox_data_intermediate_ad_zone set partner_id =
\"DH_APP\" where partner_id like \"DH_APP\'nvOpzp%\"; Query OK, 24 rows
affected (49.65 sec)
