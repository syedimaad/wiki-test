First we need to disabled the cron from the infra-automation
**(10.10.35.108)** server which will automatically starting the docker
on all the EMR nodes.

**Stop Docker service with adhoc**\
ansible Josh-User-Follow-QA-Stream -m shell -a \'systemctl stop docker
\|\| service docker stop\' -b -u ec2-user

**copy script with adhoc**\
ansible Josh-User-Follow-QA-Stream \--module-name copy \--args
\"src=/home/ubuntu/node_exporter.sh
dest=/home/ec2-user/node_exporter.sh\" -b -u ec2-user

**change Permission with adhoc**\
ansible Josh-User-Follow-QA-Stream -m file -a
\"dest=/home/ec2-user/node_exporter.sh mode=755 owner=ec2-user
group=ec2-user\" -b -u ec2-user

**run Script with adhoc**\
ansible Josh-User-Follow-QA-Stream -m shell -a \"sh
/home/ec2-user/node_exporter.sh\" -b -u ec2-user
