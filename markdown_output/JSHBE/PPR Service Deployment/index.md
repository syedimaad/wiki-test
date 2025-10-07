Build Server: **10.17.194.36, ssh -i  ugc-prod.pem **
[**ec2-user@10.17.194.36**](mailto:ec2-user@10.17.194.36)

## Pre Deployment

1.  Take the latest pull from git in the folder
    /*[home/ec2-user/git/retrieval]{.underline}* in Build Server

2.  Execute the script
    *[/home/ec2-user/deployment/build.sh]{.underline}* to build the
    module and copy the jar to the required place.

3.  Modify the
    script *[/home/ec2-user/deployment/init_deployment.sh]{.underline}*
    if there is any change in the S3 Path of the graph data.

4.  Execute [sudo supervisorctl restart ppr]{.underline} to restart the
    service and verify once.

## Deployment Steps

1.  Stop the EC2 Build Instance -
    <https://ap-south-1.console.aws.amazon.com/ec2/home?region=ap-south-1#Instances:instanceState=running>

2.  Create a new AMI from the Build Instance

3.  AMI Naming convention followed:
    *[josh-aiml-us-ppr-search-v3]{.underline}*, change V3 to V4..Vn -
    [https://ap-south-1.console.aws.amazon.com/ec2/home?region=ap-south-1#Images:visibility=owned-by-me;search=:ppr;v=3;\$case=tags:false\\,client:false;\$regex=tags:false\\,client:false](https://ap-south-1.console.aws.amazon.com/ec2/home?region=ap-south-1#Images:visibility=owned-by-me;search=:ppr;v=3;$case=tags:false%5C,client:false;$regex=tags:false%5C,client:false)

4.  Update the Launch Template: *[ppr-search-lt]{.underline}* with the
    new AMI

5.  Start Instance Refresh in the ASG: *[ppr-search-asg]{.underline}*

6.  Service Status Check
    <https://ppr-search-internal.myjosh.in/ppr/healthcheck>

## Post Deployment

1.  Start the EC2 Build Instance
