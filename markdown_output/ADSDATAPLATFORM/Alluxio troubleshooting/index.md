## Alluxio Master

runs on **dh-gcp-ads-data-presto-query-coordinator-n1.dailyhunt.in** VM.

Web UI:
<http://dh-gcp-ads-data-presto-query-coordinator-n1.dailyhunt.in:9002/overview>

## Workers

dh-gcp-ads-data-presto-query-n6.dailyhunt.in

dh-gcp-ads-data-presto-query-n7.dailyhunt.in

dh-gcp-ads-data-presto-query-n8.dailyhunt.in

dh-gcp-ads-data-presto-query-n9.dailyhunt.in

dh-gcp-ads-data-presto-query-n10.dailyhunt.in

# Common issues

## Alluxio Master is down

Trino queries are failing and streaming applications have stopped
running. Also, the alluxio master web ui does not open.

In this case, need to restart alluxio master.

ssh USER@dh-gcp-ads-data-presto-query-coordinator-n1.dailyhunt.in sudo
-u dh-ads -i cd docker-alluxio-master/ \# To check the failure logs
docker compose logs -f \# Restart docker compose down && docker compose
up -d

After waiting for the alluxio master to come up, which can take a long
time, need to re-register the workers.

Need to do this for each worker individually.

ssh USER@dh-gcp-ads-data-presto-query-n6.dailyhunt.in sudo -u dh-ads -i
cd docker-alluxio-worker/ source .env docker-compose down &&
docker-compose up -d

Check web ui
<http://dh-gcp-ads-data-presto-query-coordinator-n1.dailyhunt.in:9002/overview>
to see if all workers are `In Service`.

## Alluxio is slow

Queries are timing out. This can be due to the alluxio master being low
on resources. Open web ui
<http://dh-gcp-ads-data-presto-query-coordinator-n1.dailyhunt.in:9002/overview>
and look at the System Status.

- `IDLE`

- `ACTIVE`

- `STRESSED`

- `OVERLOADED`
