**Pre-request:-**

** **

- Kubernetes cluster : 1.20+

- Helm: 3.0+

- EFS CSI driver: It is required for persistence storage for DAG. Take
  the below   aws reference.

[https://docs.aws.amazon.com/eks/latest/userguide/efs-csi.html](https://docs.aws.amazon.com/eks/latest/userguide/efs-csi.html){card-appearance="inline"}

- EBS CSI driver: It is required for redis and worker persistence
  storage

**Configuration**:-

- Create EKS cluster having version greater than 1.20+. we have used the
  1.23.

- Create 2 node group:-

- One for non-worker nodes:- pgbouncer, redis, scheduler, statsd,
  triggerer, 

          webserver is launched in non-worker nodegroup.

- One for worker nodes:- worker nodes are launched in worker node group.

[Create an IAM OIDC provider for your
cluster](https://docs.aws.amazon.com/eks/latest/userguide/enable-iam-roles-for-service-accounts.html).
[https://docs.aws.amazon.com/eks/latest/userguide/enable-iam-roles-for-service-accounts.html](https://docs.aws.amazon.com/eks/latest/userguide/enable-iam-roles-for-service-accounts.html){card-appearance="inline"}

- Create IAM policy and role for EFS and EBS CSI driver.

[https://docs.aws.amazon.com/eks/latest/userguide/csi-iam-role.html](https://docs.aws.amazon.com/eks/latest/userguide/csi-iam-role.html){card-appearance="inline"}

[https://docs.aws.amazon.com/eks/latest/userguide/efs-csi.html](https://docs.aws.amazon.com/eks/latest/userguide/efs-csi.html){card-appearance="inline"}

- Install the EBS and EFS CSI drive in your cluster if not present.
  Above link will take you there.

<!-- -->

- Create postgres for airflow databases. We have use the RDS postgres
  for this setup

[https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_GettingStarted.CreatingConnecting.PostgreSQL.html](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_GettingStarted.CreatingConnecting.PostgreSQL.html){card-appearance="inline"}

- Create Secret for the web server secret key and RDS credentials.

   Sample example: 

- *kubectl create secret generic airflow -n airflow
  \--from-literal=connection=postgresql://userxxx:Passwordxxx@host:5432/db*

- *kubectl create secret generic my-webserver-secret -n airflow
  \--from-literal=\"webserver-secret-key=\$(python3 -c \'import secrets;
  print(secrets.token_hex(16))\')\"*

**Architecture:**

We have used the metadata as a postgres. DAG is managed by EFS. Workers
use the stateful set . Scheduler and web server are stateless.

For user communication we have use the internal load balancer that
connect to web-ui at backed 

Cluster setup commands and files are below:-

=====

Installing the EFS Driver:-

→ [Create the IAM policy]{.underline}

*curl -o iam-policy-example.json*
[*https://raw.githubusercontent.com/kubernetes-sigs/aws-efs-csi-driver/master/docs/iam-policy-example.json*](https://raw.githubusercontent.com/kubernetes-sigs/aws-efs-csi-driver/master/docs/iam-policy-example.json)

*aws iam create-policy*\
*\--policy-name AmazonEKS_EFS_CSI_Driver_Policy*\
*\--policy-document file://iam-policy-example.json*

→ [Create the trusted role for oidc identity]{.underline}

*aws eks describe-cluster \--name josh-recsys-eks-cluster \--query
\"cluster.identity.oidc.issuer\" \--output text*

*aws iam create-role*\
*\--role-name AmazonEKS_EFS_CSI_DriverRole_recsys-eks-cluster*\
*\--assume-role-policy-document file://\"trust-policy.json\"*

→ [Attach the role policy]{.underline}

*aws iam attach-role-policy*\
*\--policy-arn
arn:aws:iam::514352861371:policy/AmazonEKS_EFS_CSI_Driver_Policy*\
*\--role-name AmazonEKS_EFS_CSI_DriverRole_recsys-eks-cluster*

→ [Installing the driver via helm]{.underline}

*helm repo add aws-efs-csi-driver*
[*https://kubernetes-sigs.github.io/aws-efs-csi-driver/*](https://kubernetes-sigs.github.io/aws-efs-csi-driver/)

*helm repo update*

*helm upgrade -i aws-efs-csi-driver
aws-efs-csi-driver/aws-efs-csi-driver*\
*\--namespace kube-system*\
*\--set*
[*image.repository=602401143452.dkr.ecr.ap-south-1.amazonaws.com/eks/aws-efs-csi-driver*](http://image.repository=602401143452.dkr.ecr.ap-south-1.amazonaws.com/eks/aws-efs-csi-driver)
\
*\--set controller.serviceAccount.create=false*\
*\--set controller.serviceAccount.name=efs-csi-controller-sa*

→ [create the EFS filesystem]{.underline}

*vpc_id=\$(aws eks describe-cluster*\
*\--name josh-recsys-eks-cluster*\
*\--query \"cluster.resourcesVpcConfig.vpcId\"*\
*\--output text)*

*cidr_range=\$(aws ec2 describe-vpcs*\
*\--vpc-ids \$vpc_id*\
*\--query \"Vpcs\[\].CidrBlock\"*\
*\--output text*\
*\--region ap-south-1)*

*security_group_id=\$(aws ec2 create-security-group*\
*\--group-name josh-recsys-eks-cluster-sg*\
*\--description \"josh-recsys-eks-cluster efs sg\"*\
*\--vpc-id \$vpc_id*\
*\--output text)*

*aws ec2 authorize-security-group-ingress*\
*\--group-id \$security_group_id*\
*\--protocol tcp*\
*\--port 2049 \## i have allowed all traffic to internal vpc*\
*\--cidr \$cidr_range*

*file_system_id=\$(aws efs create-file-system*\
*\--region ap-south-1*\
*\--performance-mode generalPurpose*\
*\--query \'FileSystemId\'*\
*\--output text)*

*aws ec2 describe-subnets*\
*\--filters \"Name=vpc-id,Values=\$vpc_id\"*\
*\--query \'Subnets\[\*\].{SubnetId: SubnetId,AvailabilityZone:
AvailabilityZone,CidrBlock: CidrBlock}\'*\
*\--output table*

*aws efs create-mount-target*\
*\--file-system-id \$file_system_id*\
*\--subnet-id subnet-0d69fd2153a38bfa4 \## Create mount for all the
subnet associated with eks cluster*\
*\--security-groups \$security_group_id*

→ [Create storage class]{.underline}

*kubectl apply -f storageclass.yaml*

→ [Create DB secter]{.underline}

*kubectl create secret generic airflowdb-password -n
control-apps-airflow
\--from-literal=connection=mysql+mysqldb://airflow:AirFl0w12@moco-common-mysql.control-apps:3306/ai*rflow

→ [Create webserver secret]{.underline}

*kubectl create secret generic airflow-webserver-secret -n
control-apps-airflow \--from-literal=\"webserver-secret-key=\$(python3
-c \'import secrets; print(secrets.token_hex(16))\')\"*

→ [install airflow]{.underline}

*helm repo add apache-airflow*
[*https://airflow.apache.org*](https://airflow.apache.org)

*helm upgrade \--install airflow apache-airflow/airflow \--namespace
control-apps-airflow \--create-namespace -f overwrite.yaml*

Reference:-
[https://airflow.apache.org/docs/apache-airflow/stable/index.html](https://airflow.apache.org/docs/apache-airflow/stable/index.html){card-appearance="inline"}
