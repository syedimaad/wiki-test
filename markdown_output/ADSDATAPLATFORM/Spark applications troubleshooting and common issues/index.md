# **Streaming applications**

## List of applications

with their resource configurations and schedule are listed in this
google sheet.

[https://docs.google.com/spreadsheets/d/1jJ_TpjSdtwRgIKq6daQCHWGv196c643d1dp7tM0gvyQ/edit?gid=1509970502#gid=1509970502](https://docs.google.com/spreadsheets/d/1jJ_TpjSdtwRgIKq6daQCHWGv196c643d1dp7tM0gvyQ/edit?gid=1509970502#gid=1509970502){card-appearance="inline"}

## 2 minute monitoring application

### Code repository:

<https://gitlab.dailyhunt.in/nh-ads-platform/spark-k8-autoscale-process-monitor>

This runs as a systemd one-shot service, on a timer of 2 minutes.

VM:

[dh-gcp-ads-data-edge-n1.dailyhunt.in](http://dh-gcp-ads-data-edge-n1.dailyhunt.in)

### Systemd Configuration files:

/etc/systemd/system/spark3-5-k8-processes-monitor.service
/etc/systemd/system/spark3-5-k8-processes-monitor-timer.timer

### Logs

sudo journalctl -u spark3-5-k8-processes-monitor -f

### Discover IP Address of spark standalone master-

bashset -ex if \[\[ -z \"\${SPARK_MASTER_URI}\" \]\]; then
SPARK_STANDALONE_MASTER_IP=\$(kubectl
\--context=gke_dh-gcp-ads-prod_asia-south1_dh-gcp-ads-k8s-prod-auto-standard
\--namespace=spark-standalone-3-5 -ojson get svc
spark-standalone-master-service \| jq \--raw-output \"
.status.loadBalancer.ingress \| .\[\].ip\") export
SPARK_MASTER_URI=spark://\${SPARK_STANDALONE_MASTER_IP}:7077 fi set +ex

Open \`http://\${`SPARK_STANDALONE_MASTER_IP`}:8080\` to see the spark
standalone web UI.

<http://dh-gcp-ads-data-admin-n4.dailyhunt.in:3000/d/a10d47b5-2d18-4bc4-91e3-332d013bd0a2/dh-ads-events?orgId=1&refresh=30s&from=now-6h&to=now>

## Common issues

Spark standalone master ui does not open. This likely means that the
spark

`kubectl --context=gke_dh-gcp-ads-prod_asia-south1_dh-gcp-ads-k8s-prod-auto-standard --namespace=spark-standalone delete pod spark-standalone-master-6b59df7b77-8rqrz`

Application keeps failing

If application keeps failing, and being resubmitted every 2 minutes, we
need to look at the stacktrace of the driver application.

Discover worker number, Exec into container. check stderr.
