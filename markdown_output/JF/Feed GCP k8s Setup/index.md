## Deployment

  --------------------------- -----------------------------------------------------
  **GitLab Repo**             <https://gitlab.dailyhunt.in/josh-p13n/feed-engine>
  **Current Master Branch**   **master-w5**
  --------------------------- -----------------------------------------------------

**Deployment Steps:**

1.  First commit your changes to above current master branch for prod or
    "custom" branch for canary

2.  Upload jar

    1.  **Prod** -
        `gs://josh-deploy-artifacts/feed-engine/jars/feed-engine-0.0.1-SNAPSHOT.jar`

    2.  **Canary** -
        `gs://josh-deploy-artifacts/feed-engine/canary_jars/feed-engine-0.0.1-SNAPSHOT.jar`

3.  Upload config

    1.  **Prod** -
        `gs://josh-deploy-artifacts/feed-engine/config/config.tar.xz`

    2.  **Canary** -
        `gs://josh-deploy-artifacts/feed-engine/canary_config/config.tar.xz`

4.  open [this
    link](https://gitlab.dailyhunt.in/josh-p13n/feed-engine/-/pipelines)
    to start deployment

5.  Recent deployments page should appear where you would see which
    branch/commit id was deployed

6.  Click on `Run Pipeline` button appearing at the top right of the
    deployment history table

7.  It opens a form page, select the branch you want to deploy (by
    default current master branch appears) \[**Note: For PROD do not
    change branch**\]

8.  **Note:** The form should have multiple variable rows like
    `DEPLOY_ENVIRONMENT`, `DEPLOYMENT_NAME`, `ROLLING_UPDATE`,
    `IMAGE_TAG`

9.  If form described in above 2 steps does not load properly, please
    refresh the page

10. Do not change `DEPLOY_ENVIRONMENT`

11. For `DEPLOYMENT_NAME` choose `feed-api for PROD` /
    `canary for CANARY`

12. `ROLLING_UPDATE` → This value determines how many % new servers will
    be spawned to replace old servers

13. Old servers will not be drained/terminated until new servers are
    healthy and running

14. Run this command and copy the short commit id -
    `git rev-parse --short HEAD`

15. `IMAGE_TAG` →

    1.  **PROD** - Format `dd-mmm-yy-<commit id>` (Examples:
        `10-Mar-23-fd87dd0a`, `06-Jun-23-8823ee6e`
        `18-Sep-23-42157f0eb`)

    2.  **CANARY** - `<dev name>-<branch-name>`

16. Click on `Run Pipeline` and on the next page click on play button to
    start deployment

## POD Commands

- Configure AWS EKS pod\
  `gcloud container clusters get-credentials josh-serv-internal-prod-zone-b --zone asia-south1-b --project josh-prod-392409 && kubectl config use-context gke_josh-prod-392409_asia-south1-b_josh-serv-internal-prod-zone-b`

- To see currently running pods\
  `kubectl get pods -n feed-api -o wide`

- Tail pod logs\
  `kubectl logs -n feed-api <pod name> --tail=10 --follow`

- SSH onto pods\
  `kubectl exec -it <pod name> -n feed-api bash`

- To see number of pods running and current docker image running on
  pods - **Note:** The `IMAGE_TAG` given by you during deployment should
  reflect here\
  `kubectl get deployments -n feed-api -o wide`

## DSL Config Path

- DSL Common Config -
  `gs://josh-deploy-artifacts/feed-engine/dsl/dsl_common_config.json`

- DSL Execution Config -
  `gs://josh-deploy-artifacts/feed-engine/dsl/dsl_execution_config.json`

## Service Dashboards

All service dashboards can be found
[here](https://operation.myjosh.in/dashboards/f/a7122c7c-03cb-4dd4-8547-f9b24f091129/feed-api-java)

- [Cluster and POD Stats
  Dashboard](https://operation.myjosh.in/d/85a562078cdf77779eaa1add43ccec1exyzdd/cluster-system-stats-feed-api?orgId=1) -
  Node CPU Utilisation, Node to Pod Mapping, Pod CPU Utilisation, Pod
  Disk Utilisation, Pod Memory Usage, Pod Level Network Stats

- [Ingress / Egress
  Stats](https://operation.myjosh.in/d/k8s-nginx-ingress-prometheus-ng/ingress-controller?orgId=1&refresh=1m&var-controller_class=All&var-namespace=feed-api&var-ingress=All&var-pod=All&var-datasource=Thanos) -
  LB Level Stats, Request Count, Connection Count, 2xx count, Non 2xx
  Count

- [Feed Engine
  Stats](https://operation.myjosh.in/d/DCpyg517z/feed-engine-stats?orgId=1&refresh=10s)

- [Feed Engine Cassandra
  Stats](https://operation.myjosh.in/d/uDnDF754zoi/feed-engine-cassandra-stats?orgId=1)

- [Feed Engine JVM
  Stats](https://operation.myjosh.in/d/cc5f603a-15a9-40d8-acdf-694aa431ee3f/feed-engine-jvm-stats?orgId=1)

- [Feed Engine ML
  Stats](https://operation.myjosh.in/d/VILxnvJ7ytza/feed-engine-ml-stats?orgId=1)

- [Feed Engine Redis
  Stats](https://operation.myjosh.in/d/VILxnvJ7z30/feed-engine-redis-stats?orgId=1)

- [Miscellaneous
  Data](https://operation.myjosh.in/d/VILxnvJ7zrgyt/feed-engine-stats-exception-counters-and-timers?orgId=1) -
  Pricing Hit Ratio, Location Cookie Stats, ES Query Timers, etc

## Logs

- For LB level logs please use below query

  (((((\_sourceCategory=\"josh/prod/gke/logs/stdout\" and
  \_collector=\"HTTP\"))))) \| json field=\_raw
  \"kubernetes.namespace_name\" \| where %\"kubernetes.namespace_name\"
  matches \"\*ingress-nginx-ext\*\" \| json \"content\" as cnt \| parse
  regex field=cnt
  \"\^(?\<src_ip\>\\d{1,3}\\.\\d{1,3}\\.\\d{1,3}\\.\\d{1,3})\" \| parse
  regex field=cnt
  \"(?\<method\>\[A-Z\]+)\\s(?\<url\>\\S+)\\sHTTP/\[\\d\\.\]+\\\"\\s(?\<status_code\>\\d+)\\s(?\<size\>\[\\d-\]+)\\s\\\"(?\<referrer\>.\*?)\\\"\\s\\\"(?\<user_agent\>.+?)\\\"\\s(?\<request_length\>\\d{1,3})\\s(?\<request_time\>\\d+\\.\\d+)\\s(?\<proxy_upstream_name\>\\\[.\*\\\])\\s\\\[(?\<weighted_svc\>.\*)\\\]\\s(?\<upstream_addr\>.\*)\\s(?\<upstream_response_length\>.\*)\\s(?\<upstream_response_time\>\\d+\\.\\d+)\\s(?\<upstream_status\>.\*)\\s(?\<req_id\>.\*).\*\"
  \| where proxy_upstream_name =
  \"\[feed-api-feed-api-java-service-5000\]\"

- For application logs\

  \_dataTier=Infrequent \_sourceCategory=\"josh/prod/gke/logs/stdout\"
  and \_collector=\"HTTP\" \| json field=\_raw
  \"kubernetes.namespace_name\" as ns \| where ns matches \"feed-api\"
  \| where content matches \"\*\<your seach query\>\*\"
