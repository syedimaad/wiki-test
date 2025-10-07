## How to create EC2 instances

1.  Open
    <https://ap-south-1.console.aws.amazon.com/ec2/home?region=ap-south-1#Instances:>

2.  Set tags. See table below.

3.  Choose AMI (OS image)

    1.  To have a connection to gitlab repositories
        (<https://gitlab.dailyhunt.in/>) choose\
        AMI ID: ami-04ab4f817b4f761ff\
        AMI Name: amazon-linux-ec2-init-image\
        If you need access to gitlab from other images please ask for
        help. He will create a custom image for you with access to
        giltlab.

    2.  Otherwise choose any appropriate AMI.

4.  Choose Key pair (login)\
    josh-aiml-us\
    Note: you will need RSA private key to access the instance, ask if
    you don\'t have the key

5.  Choose VPC and subnet\
    VPC: vpc-0c818a736ca01afd1 \| ml_test-vpc\
    Subnet: subnet-0eef14b6432750c9d

6.  Firewall (security groups)

    1.  To have connection between instances need to use security group:
        `josh-aiml-us-sg sg-0db2b6333ca555f4c`

    2.  Otherwise skip this section (choose "Create security group" with
        default settings)

7.  In advanced details open "IAM instance profile"\
    VPCLockDown

8.  To connect via ssh

    1.  We can specify rsa key each time we want to connect

        ssh -i \<path to rsa private key\> \<user\>@\<AWS private IP
        address\>

    2.  Or we can add rsa key to the ssh-agent to not specify it every
        time
        ([link](https://blog.zmole.ro/how-to-use-your-ssh-key-to-connect-remotely-from-mc-midnight-commander/))

        ssh-add \<path to rsa private key\> ssh \<user\>@\<AWS private
        IP address\>

    3.  Users\
        ec2-user - for Amazon images\
        ubuntu - for Ubuntu images

+-------------+-----------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+---------------+---------------+----------------------------+----------------------+------------+
| tag:        | tag: service                                                                            | tag: owner                                                                              | tag: role     | tag: env      | tag: createdby             | tag: bu              | tag: cloud |
| resource    |                                                                                         |                                                                                         |               |               |                            |                      |            |
+-------------+-----------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+---------------+---------------+----------------------------+----------------------+------------+
| compute,emr | api,feed,gateway,share,analytics,aiml,transcode,cms,notification,joshcam,joshlive,infra | api,feed,gateway,share,analytics,aiml,transcode,cms,notification,joshcam,joshlive,infra | No hard       | prod,qa,stage | No hard values. To be set  | josh,ads,dh,pv,infra | aws        |
|             |                                                                                         |                                                                                         | values. To be |               | by the user. General       |                      |            |
|             |                                                                                         |                                                                                         | set by the    |               | Guidelines:                |                      |            |
|             |                                                                                         |                                                                                         | user. General |               |                            |                      |            |
|             |                                                                                         |                                                                                         | Guidelines:   |               | - team name/IAM username   |                      |            |
|             |                                                                                         |                                                                                         |               |               |   during manual creation   |                      |            |
|             |                                                                                         |                                                                                         | - all         |               |                            |                      |            |
|             |                                                                                         |                                                                                         |   lowercase   |               | - terraform/cloudformation |                      |            |
|             |                                                                                         |                                                                                         |               |               |   when automatic           |                      |            |
|             |                                                                                         |                                                                                         | - upto 15     |               |   deployment               |                      |            |
|             |                                                                                         |                                                                                         |   characters  |               |                            |                      |            |
|             |                                                                                         |                                                                                         |               |               |                            |                      |            |
|             |                                                                                         |                                                                                         | - use         |               |                            |                      |            |
|             |                                                                                         |                                                                                         |   underscores |               |                            |                      |            |
|             |                                                                                         |                                                                                         |   over other  |               |                            |                      |            |
|             |                                                                                         |                                                                                         |   special     |               |                            |                      |            |
|             |                                                                                         |                                                                                         |   characters  |               |                            |                      |            |
|             |                                                                                         |                                                                                         |   like space, |               |                            |                      |            |
|             |                                                                                         |                                                                                         |   hyphen      |               |                            |                      |            |
+-------------+-----------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+---------------+---------------+----------------------------+----------------------+------------+
