1.  Build JAR

    1.  Go to <https://cicd.dailyhunt.in/>

    2.  Click on Project - `ADS-adseventsprocessing-NRT`

    3.  Click on `Build with Parameters` (left side)

    4.  Select the required branch and click `Build`

    5.  Build history can be seen on the left-hand side. Click on your
        `build #` once it is complete.

    6.  Click on `Console Output`(left side)

    7.  Copy the `Uploaded` jar path

2.  Deploy JAR and script

    1.  Go to
        `dh-gcp-ads-data-edge-n1.dailyhunt.in:/mnt/vol1/dh-ads/ads_events/jar`

    2.  Download the jar - `wget Paste_jar_path`

    3.  Create a symlink to the latest downloaded jar(ignore in case
        testing the jar)\
        `unlink AdsEventsProcessing-assembly-0.1.jar`\
        `ln -s new.jar AdsEventsProcessing-assembly-0.1.jar`

    4.  Sync the folder with gcs jar folder -
        `gsutil -m rsync /mnt/vol1/dh-ads/ads_events/jar/ gs://dh-gcp-ads-data/spark-gke/mount/ads_events/jar/`

    5.  Add configs - `/mnt/vol1/dh-ads/nrt-prod-configs/`

    6.  Copy the execution script to
        `/mnt/vol1/dh-ads/ads_events/runtime-scripts/<tenant>/`

    7.  If testing the jar, modify `APPLICATION_JAR` in the script to
        point to the required jar.

    8.  Give execution permission to the script
        `chmod +x script_name.sh`

    9.  Create a new entry for the process in the sheet -
        `spark streaming applications`
        [https://docs.google.com/spreadsheets/d/1jJ_TpjSdtwRgIKq6daQCHWGv196c643d1dp7tM0gvyQ/edit#gid=0](https://docs.google.com/spreadsheets/d/1jJ_TpjSdtwRgIKq6daQCHWGv196c643d1dp7tM0gvyQ/edit#gid=0){card-appearance="inline"}

        - App - Application Name(can be anything)

        - Duration - default means ever running, different durations can
          be given to handle different resources.

        - Script Path - Execution script for this process, refer to
          point `e`

        - Resources - Resources required by the processes.

    10. Check job logs on edge-n1 using
        `sudo journalctl -u spark-k8-processes-monitor -f`

3.  Monitoring

    1.  Use
        `bash /mnt/vol1/dh-ads/mayankdev/gke-spark-standalone/source_3_3.sh`
        to get the URL link and use port 8080. URL -
        <http://10.50.0.27:8080/>

    2.  Under `Running Applications` click on your process.\
        It will open a new tab(which doesn\'t open). Note the URL. it
        will start with something like `worker-set-1` Note this number.

    3.  Under `Running Drivers`, note the driver_id of the process.

    4.  Use the worker-set number and run the following command on
        edge-n1 to enter the pod\
        `kubectl --context=gke_dh-gcp-ads-prod_asia-south1_dh-gcp-ads-k8s-prod-auto-standard --namespace=spark-standalone-3-5 exec --stdin --tty worker-set-1 -- /bin/bash`

    5.  To open the web-ui

        kubectl
        \--context=gke_dh-gcp-ads-prod_asia-south1_dh-gcp-ads-k8s-prod-auto-standard
        \--namespace=spark-standalone port-forward \--address 0.0.0.0 
        pod/worker-set-0 4021:4041

        for spark3.3.2 use this command

        kubectl
        \--context=gke_dh-gcp-ads-prod_asia-south1_dh-gcp-ads-k8s-prod-auto-standard
        \--namespace=spark-standalone-3-3 exec \--stdin \--tty
        worker-set-1 \-- /bin/bash

    6.  Inside the kubernetes pod, `cd ../work/driver_id`

    7.  Here you can check `stdout` and `stderr` logs.

### Useful commands

#### List all pods

kubectl
\--context=gke_dh-gcp-ads-prod_asia-south1_dh-gcp-ads-k8s-prod-auto-standard
\--namespace=spark-standalone get pods

#### To get the web ui ip and port

kubectl
\--context=gke_dh-gcp-ads-prod_asia-south1_dh-gcp-ads-k8s-prod-auto-standard
\--namespace=spark-standalone get svc

#### Restart a pod

kubectl
\--context=gke_dh-gcp-ads-prod_asia-south1_dh-gcp-ads-k8s-prod-auto-standard
\--namespace=spark-standalone delete pod
spark-standalone-master-6b59df7b77-8rqrz

#### Check logs

kubectl
\--context=gke_dh-gcp-ads-prod_asia-south1_dh-gcp-ads-k8s-prod-auto-standard
\--namespace=spark-standalone logs
spark-standalone-master-6b59df7b77-xcwfc

Check logs of 2 minute check script for spark 3.3.2

cd /etc/systemd/system

`sudo journalctl -u spark3-3-k8-processes-monitor.service -f`

#### Check logs of 2 minute check script for spark

sudo journalctl -u spark-k8-processes-monitor.service -f

spark cluster urls

spark 3.1.3 - <http://dh-gcp-ads-data-admin-n2.dailyhunt.in:9080/>

spark 2.4.8 - <http://ads-data-standalone-master.dailyhunt.in/>

spark 3.1.3 - <http://10.50.0.7:8080/>

spark 3.3.2 - <http://10.50.0.136:8080/>
