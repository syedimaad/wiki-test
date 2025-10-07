## **Automated Node Labeling for Free GPU Memory in GKE**

### **Objective**

To dynamically label GKE nodes with their current **free GPU memory**
value by fetching metrics from Prometheus and updating node labels
automatically every 5 minutes.

------------------------------------------------------------------------

### **Background**

Kuberntes cluster aware of numbe rof GPUs and not free memory of GPU,
hence we are facing issues duirng deployment or restart of pods getting
stuck.

To achieve this updating labels every 5min on free memory and then in
deployment file configure affinity to pod will be placed on nodes which
has enough memory .

- GPU utilization data is exposed via the metric:\
  `DCGM_FI_DEV_FB_FREE`

- Requirement:\
  Extract hostname & free GPU memory from Prometheus, then update
  Kubernetes node labels in the format:

free-gpu-memory=\<value\>\
Use these labels for scheduling, monitoring, or workload placement.

Implementation Steps

1.  Prometheus Query\
    We used the query:

promql\
max by (Hostname) (DCGM_FI_DEV_FB_FREE)\
This returns the latest free GPU memory (in MB) per node.

2.  Test Command\
    Tested locally using:

\
PROM_URL=\"\<http://\<prometheus-url\>\>/api/v1/query\"\
QUERY=\'max by (Hostname) (DCGM_FI_DEV_FB_FREE)\'

curl -s -G \"\$PROM_URL\" \\\
\--data-urlencode \"query=\$QUERY\" \\\
\| jq -r \'.data.result\[\] \| \"\\(.metric.Hostname)
\\(.value\[1\])\"\' \\\
\| grep gke \\\
\| while read -r node mem; do\
echo \"Labeling node \$node with free-gpu-memory=\$mem\"\
kubectl label node \"\$node\" free-gpu-memory=\"\$mem\" \--overwrite\
done\
3. RBAC Configuration\
Created a ClusterRole + ClusterRoleBinding + ServiceAccount to allow the
script to label nodes:

apiVersion:
[rbac.authorization.k8s.io/v1](http://rbac.authorization.k8s.io/v1)\
kind: ClusterRole\
metadata:\
name: gpu-labeler-role\
rules:

- apiGroups: \[\"\"\]\
  resources: \[\"nodes\"\]\
  verbs: \[\"get\", \"list\", \"label\", \"patch\", \"update\"\]

------------------------------------------------------------------------

apiVersion:
[rbac.authorization.k8s.io/v1](http://rbac.authorization.k8s.io/v1)\
kind: ClusterRoleBinding\
metadata:\
name: gpu-labeler-binding\
roleRef:\
apiGroup: [rbac.authorization.k8s.io](http://rbac.authorization.k8s.io)\
kind: ClusterRole\
name: gpu-labeler-role\
subjects:

- kind: ServiceAccount\
  name: gpu-labeler\
  namespace: default

4.  CronJob Configuration\

Store Prometheus URL in a ConfigMap/Secret for flexibility.

Add retries and error handling for Prometheus downtime.

data flow from Prometheus → CronJob → Node Labels for

apiVersion: v1 kind: ServiceAccount metadata: name: gpu-labeler
namespace: default apiVersion: rbac.authorization.k8s.io/v1 kind:
ClusterRole metadata: name: node-labeler rules: - apiGroups: \[\"\"\]
resources: \[\"nodes\"\] verbs: \[\"get\", \"list\", \"watch\",
\"label\", \"patch\", \"update\"\] apiVersion:
rbac.authorization.k8s.io/v1 kind: ClusterRoleBinding metadata: name:
node-labeler-binding roleRef: apiGroup: rbac.authorization.k8s.io kind:
ClusterRole name: node-labeler subjects: - kind: ServiceAccount name:
gpu-labeler namespace: default apiVersion: batch/v1 kind: CronJob
metadata: name: gpu-memory-labeler namespace: default spec: schedule:
\"\*/5 \* \* \* \*\" \# Every 5 minutes jobTemplate: spec: template:
spec: serviceAccountName: gpu-labeler restartPolicy: Never containers: -
name: gpu-memory-labeler image: dtzar/helm-kubectl:latest command: -
/bin/sh - -c - \| PROM_URL=\"http://10.90.150.222:8040/api/v1/query\"
QUERY=\'max by (Hostname) (DCGM_FI_DEV_FB_FREE)\' curl -s -G
\"\$PROM_URL\" \\ \--data-urlencode \"query=\$QUERY\" \\ \| jq -r
\'.data.result\[\] \| \"\\(.metric.Hostname) \\(.value\[1\])\"\' \\ \|
grep gke \\ \| while read -r node mem; do echo \"Labeling node \$node
with free-gpu-memory=\$mem\" kubectl label node \"\$node\"
free-gpu-memory=\"\$mem\" \--overwrite done

Sample deployment to select nodes with enough gpu memory

apiVersion: apps/v1 kind: Deployment metadata: name: xlm-roberta-ner-v3
namespace: xlm-roberta-ner labels: app: xlm-roberta-ner-v3
argocd.argoproj.io/instance: xlm-roberta-ner-prod
k8slens-edit-resource-version: v1 spec: replicas: 1 selector:
matchLabels: app: xlm-roberta-ner-v3 template: metadata: labels: app:
xlm-roberta-ner-v3 annotations: prometheus.io/path: /metrics
prometheus.io/port: \'8096\' prometheus.io/scrape: \'true\' spec:
containers: - name: xlm-roberta-ner-v3 image: \>-
asia-south1-docker.pkg.dev/et-gcp-aiml-prod-v2/aiml-k8s/xlm-roberta-ner:20250810_01
ports: - containerPort: 8094 protocol: TCP - containerPort: 8095
protocol: TCP - containerPort: 8096 protocol: TCP - containerPort: 8089
protocol: TCP env: - name: NVIDIA_DISABLE_REQUIRE value: \'1\'
resources: limits: nvidia.com/gpu: \'1\' livenessProbe: httpGet: path:
/health port: 8089 scheme: HTTP initialDelaySeconds: 620 timeoutSeconds:
50 periodSeconds: 50 successThreshold: 1 failureThreshold: 3
readinessProbe: httpGet: path: /health port: 8089 scheme: HTTP
initialDelaySeconds: 620 timeoutSeconds: 50 periodSeconds: 50
successThreshold: 2 failureThreshold: 3 lifecycle: preStop: exec:
command: - /bin/sh - \'-c\' - sleep 120 terminationMessagePath:
/dev/termination-log terminationMessagePolicy: File imagePullPolicy:
IfNotPresent restartPolicy: Always terminationGracePeriodSeconds: 30
dnsPolicy: ClusterFirst affinity: nodeAffinity:
requiredDuringSchedulingIgnoredDuringExecution: nodeSelectorTerms: -
matchExpressions: - key: gpu-memory-free-mb operator: Gt values: -
\"5000\" securityContext: {} tolerations: - key: nvidia.com/gpu
operator: Equal value: present effect: NoSchedule strategy: type:
Recreate

Varaprasad N

Aug 10 2025
