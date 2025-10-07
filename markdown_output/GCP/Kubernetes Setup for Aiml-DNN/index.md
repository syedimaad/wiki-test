Requirements: 1. To create a Kubernetes cluster in dh4(kodiac) 2.
Calling jenkins Api with
parameters(lang_code,mode_name,latest_version,version_path) 3. To write
a jenkins pipeline to : - create a docker image - push the image to
repository - deploy on multiple pods (rolling deployment) - to send a
api after deployment to give the status of deployment and parameters
used

4\. There are 3 models(item_tower,user_tower,ranking) each model to have
2 pods and each pod should be deployed in different working nodes

1.  **Creating a Kubernetes Cluster**

    - `Since cluster is already present in dh4 we will be creating worker nodes and adding them to cluster`

    - `Use this template to create a worker node "k1-k8s-cnd-setup-templet" `

    - `Run "User Add and upgrade job" to add the host name to dns and install node exporter`

    - <http://devops3.dailyhunt.in:8080/job/UserAdd_And_Upgrade_VMs/>

    - "172.30.11.236
      [dh4-k1-cnd-k8scluster.dailyhunt.in](http://dh4-k1-cnd-k8cluster.dailyhunt.in)"
      add this entry in "/etc/hosts" in all worker nodes

    - 172.30.11.236 in this server api services is configured → doing
      this host entry helps workers to connect to api

    - Run the following commands : ***systemctl start ntpd*** and
      ***systemctl enable ntpd*** to maintains the system time in
      synchronization with time servers using the Network Time Protocol
      (NTP).

    - Run the below commands to add the worker to the cluster

      - **kubeadm token create \--print-join-command** → execute this
        command in master to get token for worker

      - **kubeadm join \<token copied from master\> →** execute this
        command in worker node

    - Once the worker node is added to the cluster master will start
      assigning pods to this worker to avoid other pods being assigned
      to our workers we will using taints and toleration concept

    -  Run this command to taint worker nodes

      - **kubectl taint nodes \<worker node name\> \<taint
        name\>=true:Noschedule →** execute this in master node

2.  **Steps to create docker image and pusing them to private
    repository**

    - Clone the repo →
      `git clone git@gitlab.dailyhunt.in:ai-lab/dh-reco/libraries/dnn-models-subscriber.git`
      → cd `dnn-models-subscriber` → git checkout starfish-prod → cd
      `dnn-models-server`

    - Dockerfile will be present now we need to run the command to build
      image

      - docker build \\ \--build-arg LANG_CODE=\$lang_code \\
        \--build-arg MODEL_NAME_ARG=\$model_name_arg \\ \--build-arg
        VERSIONS_W_PATHS=\$versions_w_paths \\ \--build-arg
        GCP_CREDS_FILE=\$gcp_creds_file \\ -t
        \${lang_code}-\${model_name_arg}-tfs:latest \\ -t
        \${lang_code}-\${model_name_arg}-tfs:\$latest_version .

      - **NOTE**: Also, assign `gcp_creds_file` to the absolute path of
        GCP application credentials file for the relevant service
        account.

      - The docker image will be named as
        `${lang_code}-${model_name_arg}-tfs:latest` and
        `${lang_code}-${model_name_arg}-tfs:${latest_version}`

        - `docker tag ${lang_code}-${model_name_arg}-tfs:$latest_version docker.dailyhunt.in/aiml/octopus/${lang_code}-${model_name_arg}-tfs:${latest_version}`
          → need to tag the image with the path of repo i.e
          `docker.dailyhunt.in/aiml/octopus/${lang_code}-${model_name_arg}-tfs:${latest_version}`
          since we are pushing image to private repo

        - `docker push docker.dailyhunt.in/aiml/octopus/${lang_code}-${model_name_arg}-tfs:${latest_version}`
          → pushing the image to repo

<!-- -->

3.  **Creating a Deployment file**

    - apiVersion: apps/v1 kind: Deployment metadata: name:
      en-dnn-item-tower namespace: aiml-prod labels: model:
      en-item-tower spec: replicas: 2 selector: matchLabels: model:
      en-item-tower template: metadata: labels: model: en-item-tower
      spec: containers: - name: item-tower image:
      docker.dailyhunt.in/aiml/octopus/en-item_tower-tfs:20230501
      imagePullPolicy: Always ports: - containerPort: 8501 name: http -
      containerPort: 8500 name: grpc

------------------------------------------------------------------------

apiVersion: v1 kind: Service metadata: name: en-item-tower-svc
namespace: aiml-prod spec: ports: - name: http port: 8501 targetPort:
8501 - name: grpc port: 8500 targetPort: 8500 selector: model:
en-item-tower type: NodePort

1.  `apiVersion`: This specifies the API version of the Kubernetes
    object being created. In this case, it\'s the `apps/v1` version of
    the Deployment object.

2.  `kind`: This specifies the type of Kubernetes object being created.
    In this case, it\'s a Deployment.

3.  `replicas`: This specifies the number of replicas that should be
    created for this Deployment object. In this case, it\'s set to 2.

4.  `strategy`: This specifies the update strategy for the Deployment
    object. In this case, it\'s set to RollingUpdate, which means that
    updates will be applied one at a time, with a specified maximum
    number of unavailable pods and no more than a certain number of new
    pods created at once.

    - `rollingUpdate`: This specifies the details of the rolling update
      strategy.

      - `maxSurge`: This specifies the maximum number of new pods that
        can be created at once during an update. In this case, it\'s set
        to 0, which means no new pods can be created during an update.

      - `maxUnavailable`: This specifies the maximum number or
        percentage of pods that can be unavailable during an update. In
        this case, it\'s set to 50%, which means that up to half of the
        pods can be unavailable at once during an update.

5.  The container section specifies the Docker image to be used and some
    additional configuration, such as resource requests and limits, as
    well as liveness and readiness probes to monitor the health of the
    container. The imagePullSecrets section specifies the name of the
    secret used to pull the Docker image from the registry. The
    tolerations and affinity sections specify the pod scheduling rules
    based on node selectors and affinity/anti-affinity rules.

6.  In the service section, the metadata section provides some basic
    information about the service, such as its name and namespace. The
    spec section defines the ports to expose and the selector field
    specifies how to select the pods to manage, in this case by matching
    the \"model\" label to the \"en-item-tower\" value. Finally, the
    type field specifies the type of service to create, in this case a
    NodePort service.

7.  Link for deployment files:
    <https://gitlab.dailyhunt.in/devops/gcp-k8/k8_manifest_files_gcp/-/tree/master/aim-dnn/prod>

8.  **Creating jenkins pipeline**

    - Build

      - Logging into jenkins slave present in gcp using
        `agent {label 'gcp'}` in pipeline

      - <https://cicd.dailyhunt.in/>

      - Defining the parameters that will be used for script

      - Cloning the git repo

        git clone
        git@gitlab.dailyhunt.in:ai-lab/dh-reco/libraries/dnn-models-subscriber.git\'

        used for building docker image

      - Creating docker image

      - Tagging the image and pushing that to nexus repository

    - Deploy

      - Mention the argocd credentials since we are using argocd for
        deploying pods in kube cluster

      - Cloning the git repo where you have all the deployment files

        git clone
        git@gitlab.dailyhunt.in:devops/gcp-k8/k8_manifest_files_gcp.git

      - Edit the deployment with latest image image:
        [docker.dailyhunt.in/aiml/octopus/en-item_tower-tfs:20230501](http://docker.dailyhunt.in/aiml/octopus/en-item_tower-tfs:20230501)

      - Run this commands to sync changes made in deployment file to be
        deployed\
        `ARGOCD_SERVER=172.20.15.97:32292 argocd --grpc-web app sync aiml-dnn-prod --force `

      - `--grpc-web` flag indicates the use of gRPC-Web protocol for
        communication, and `--force` flag forces the synchronization.\
        `ARGOCD_SERVER=172.20.15.97:32292 argocd --grpc-web app wait aiml-dnn-prod --timeout 600`

      - Wait for the synchronization of an application, `--timeout` flag
        specifies a timeout period of 600 seconds.

      - 172.20.15.97 is one of the kubernetes cluster workers we can use
        any worker ip with port `32292` (this is the node port through
        which we can access argocd service)

    - Post build

      - Remove all cloned repos

      - Success: send a curl post with all build data in form of json
        payload to this endpoint `http://10.90.128.158:8110`

      - Failure: send same curl post with jenkins build output link to
        know why the job is failing

    - link :
      <https://gitlab.dailyhunt.in/devops/gcp-k8/k8_manifest_files_gcp/-/blob/master/aim-dnn/prod/Jenkins-aiml-dnn>

9.  **Calling Jenkins Api with
    parameters(lang_code,mode_name,latest_version,version_path)**

    - Create a job
      <https://cicd.dailyhunt.in/view/DH-K8S/job/DH-K8S-aiml-dnn-prod/configure>

    - Go to config enable **Trigger builds remotely**

    - Api:

      - curl -X POST -u gcp-jenkins:11128c286b03a3e3cb69f15622159b1d52
        \"https://cicd.dailyhunt.in/view/DH-K8S/job/DH-K8S-aiml-dnn-prod/buildWithParameters?token=dnn&model_name_arg=user_tower&lang_code=en&latest_version=20230319&versions_w_paths=20230318,gs://ailab-data-platform/ailab-members-files/ayush.jain/DH/DNN/TEMP-DEV/datewise/year=2023/month=03/day=18/models_backup/en/two_tower/user_tower-tf-model-ext;20230319,gs://ailab-data-platform/ailab-members-files/ayush.jain/DH/DNN/TEMP-DEV/datewise/year=2023/month=03/day=19/models_backup/en/two_tower/user_tower-tf-model-ext\"

    - Above url can be used to trigger jenkins job

*\--Arpitha.N*
