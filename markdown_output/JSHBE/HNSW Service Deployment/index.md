Build Server: **10.10.161.127**

## Pre Deployment

1.  Comment the Linux crontabs if any are configured in the Build server

2.  Update the script from the git repo in the Build server in path
    */home/ec2-user/git/hnswlib*

3.  Build and Compile the module.???

## V100

1.  In Build Server, modify this script
    *[/home/ec2-user/deployment/init.sh]{.underline}* to load the v100
    related init_params.txt from S3

2.  Stop the EC2 Build Instance

3.  Create a new AMI from the Build Instance

4.  AMI Naming convention followed:
    *[josh-aiml-knn-search-Hnswlib-v100-V2]{.underline}*, change V2 to
    V3..Vn

5.  Update the Launch Template:
    *[v100-knn-search-service-lt]{.underline}* with the new AMI

6.  Start Instance Refresh in the ASG:
    *[v100-knn-search-service_asg]{.underline}*

7.  Service Status Check
    <http://v100-knn-search-internal.myjosh.in/status>

## Fresh

1.  In Build Server, modify this script
    *[/home/ec2-user/deployment/init.sh]{.underline}* to load the fresh
    related init_params.txt from S3

2.  Stop the EC2 Build Instance

3.  Create a new AMI from the Build Instance

4.  AMI Naming convention followed:
    *[josh-aiml-knn-search-Hnswlib-fresh-V2]{.underline}*, change V2 to
    V3..Vn

5.  Update the Launch Template:
    *[fresh-knn-search-service-lt]{.underline}* with the new AMI

6.  Start Instance Refresh in the ASG:
    *[fresh-knn-search-service-asg]{.underline}*

7.  Service Status Check
    <http://fresh-knn-search-internal.myjosh.in/status>

## Post Deployment

1.  Start the EC2 Build Instance.

2.  Enable the crontabs which were running.

## AMI Reference for Service Initiation

AMI for Fresh: ami-0aa432fcc7d62195f :
josh-aiml-knn-search-Hnswlib-fresh-V4

AMI for View \> 100: ami-0374874ddfb4515f9 :
josh-aiml-knn-search-Hnswlib-v100-V4
