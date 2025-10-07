Pre-request:-

-- Python3+ version is required

-- S3 bucket and credentials:- S3 bucket for artifact storage

-- Mysql Database:- for backend entity storage

Architecture:-

→ Create the docker base image by installing the below package:-

*docker run -it ubuntu:20.04 bash*

*apt update && apt install python3 python3-pip*

*pip install mlflow*

→ Create the docker image for mlflow:-

*docker build -t mlflow -f Dockerfile_mysql .*

*docker tag mlflow:latest*
[*514352861371.dkr.ecr.ap-south-1.amazonaws.com/mlflow:mysql*](http://514352861371.dkr.ecr.ap-south-1.amazonaws.com/mlflow:mysql)

*docker push*
[*514352861371.dkr.ecr.ap-south-1.amazonaws.com/mlflow:mysql*](http://514352861371.dkr.ecr.ap-south-1.amazonaws.com/mlflow:mysql)

→ create deployment and ingess file (deployment_mysql.yaml,
mlflow-ingress.yaml)

*kubectl apply -f deployment_mysql.yaml*

*kubectl apply -f mlflow-ingress.yaml*
