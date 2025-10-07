**Pre-request:-**

** **

- Kubernetes cluster : 1.20+

- Helm: 3.0+

- EFS CSI driver: It is required for persistence storage for user data.
  Take the below  aws reference.

[https://docs.aws.amazon.com/eks/latest/userguide/efs-csi.html](https://docs.aws.amazon.com/eks/latest/userguide/efs-csi.html){card-appearance="inline"}

- AutoScaler to scale user node

**Configuration**:-

- Create EKS clusters having versions greater than 1.20+. We have used
  the 1.23.

<!-- -->

- Create IAM policy and role for EFS CSI driver.

[https://docs.aws.amazon.com/eks/latest/userguide/csi-iam-role.html](https://docs.aws.amazon.com/eks/latest/userguide/csi-iam-role.html){card-appearance="inline"}

[https://docs.aws.amazon.com/eks/latest/userguide/efs-csi.html](https://docs.aws.amazon.com/eks/latest/userguide/efs-csi.html){card-appearance="inline"}

- Install the  EFS CSI drive in your cluster if not present. Above link
  will take you there.

commands and installation steps are at Apache Airflow Kubernetes Cluster
AWS

- Create mysql for the hub database.

mysql+pymysql://jupyterhub:Jupyt3rhub123@moco-common-mysql.control-apps:3306/jupyterhub

**Architecture:**

- Hub:- Manages user accounts, authentication, and coordinates single
  User Notebook Servers using a Spawner.

- Proxy:- The public facing part of JupyterHub that uses a dynamic proxy
  to route HTTP requests to the Hub and Single User Notebook Servers.

- Single-User Notebook Server:- A dedicated, single-user, Jupyter
  Notebook server is started for each user on the system when the user
  logs in. The object that starts the single-user notebook servers is
  called a Spawner.

- User Database:- Create the mysql database for hub metadata.

 

Use the below sample helm command to install the cluster:-

*helm upgrade \--install jupyterhub jupyterhub/jupyterhub \--namespace
control-apps-jupyterhub \--create-namespace \--values
jupyter-overwrite.yaml*

Configure the alb ingress:-

*kubectl apply -f jupyterhub-ingress.yaml*

All other configuration are in the deployed files(see the attachment)
