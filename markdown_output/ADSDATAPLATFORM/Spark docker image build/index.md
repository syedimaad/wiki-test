## For GKE batch jobs

1.  Download and extract spark distribution

2.  Download gcs connector shaded jar into jars directory

3.  Download alluxio client jar into jars directory

4.  bin/docker-image-tool.sh -r
    asia-docker.pkg.dev/dh-gcp-ads-prod/asia.gcr.io/spark -t v3.5.0
    build

5.  cd /mnt/vol1/dh-ads/gke-common/gcp-spark-runtime-docker-image

6.  Edit docker/Dockerfile, change FROM image name to above.

7.  docker build -t
    asia-docker.pkg.dev/dh-gcp-ads-prod/asia.gcr.io/spark/spark:cached-ivy-3.5.0
    -f docker/Dockerfile .

8.  `docker push asia-docker.pkg.dev/dh-gcp-ads-prod/asia.gcr.io/spark/spark:cached-ivy-3.5.0`

## Spark Standalone

1.  Download and extract spark distribution

2.  Download gcs connector shaded jar into jars directory

3.  Download alluxio client jar into jars directory

4.  bin/docker-image-tool.sh -r
    asia-docker.pkg.dev/dh-gcp-ads-prod/asia.gcr.io/spark -b
    java_image_tag=8-jdk -t v3.5.0 build

5.  cd
    /mnt/vol1/dh-ads/gke-common/gcp-spark-runtime-docker-image-standalone

6.  Edit docker/Dockerfile, change FROM image name to above.

7.  docker build -t
    asia-docker.pkg.dev/dh-gcp-ads-prod/asia.gcr.io/spark/spark:3.5.0-standalone
    -f docker/Dockerfile .

8.  `docker push asia-docker.pkg.dev/dh-gcp-ads-prod/asia.gcr.io/spark/spark:3.5.0-standalone`

9.  `cd /mnt/vol1/dh-ads/gke-spark-standalone`

10. Edit `deployment-spark-3.5.yaml` and `apply-spark-3.5.sh` - Change
    namespace and docker image.

11. Create namespace if required.
    `kubectl --context=gke_dh-gcp-ads-prod_asia-south1_dh-gcp-ads-k8s-prod-auto-standard create namespace spark-standalone-3-5`

12. `bash apply-spark-3.5.sh`

13. For the webui, wait for External-IP of the spark standalone master
    service.
    `kubectl --context=gke_dh-gcp-ads-prod_asia-south1_dh-gcp-ads-k8s-prod-auto-standard --namespace=spark-standalone-3-5 get svc`

### Run applications

1.  Create a new sheet
    in[https://docs.google.com/spreadsheets/d/1jJ_TpjSdtwRgIKq6daQCHWGv196c643d1dp7tM0gvyQ/edit#gid=1509970502](https://docs.google.com/spreadsheets/d/1jJ_TpjSdtwRgIKq6daQCHWGv196c643d1dp7tM0gvyQ/edit#gid=1509970502){card-appearance="inline"}to
    list application configs to run.

2.  `sudo su`

3.  `cd /etc/systemd/system`

4.  `cp spark3-3-k8-processes-monitor-timer.timer spark3-5-k8-processes-monitor-timer.timer`

5.  `cp spark3-3-k8-processes-monitor.service spark3-5-k8-processes-monitor.service`

6.  Edit path to deployment.yaml file, namespace, master IP etc.

7.  `systemctl enable spark3-5-k8-processes-monitor-timer.timer`

8.  `systemctl enable spark3-5-k8-processes-monitor.service`

9.  `systemctl start spark3-5-k8-processes-monitor-timer.timer`

10. `journalctl -u spark3-5-k8-processes-monitor.service -f` to check
    logs
