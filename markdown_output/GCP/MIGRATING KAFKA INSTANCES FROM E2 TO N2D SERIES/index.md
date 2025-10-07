1.   Open google console and navigate to project where you want the
    migration to be done\

2.  Then go to instance group section and search for the group under
    which kafka instance are part of Example:

 **ads-prod → Compute Engine → Instance groups
→dh-gcp-ads-kafka-nrt-asia-south1-a-mig**\

3\. Then select any one of the instance from the group and remove that
instance (**dh-gcp-ads-analyticsnrt-kafka-n2**)  from the umig\
\
*This is done to prevent the health of the group ---\> This is done to
take the KafkaREST running on the VM gracefully out from the LB to avoid
errors in service interacting with KafkaREST.*\

4. Open a new tab and navigate to **ads-prod → Compute Engine → VM
instances**

5.Then select the instance (**dh-gcp-ads-analyticsnrt-kafka-n2**)  that
you removed from group , then do the following steps\
\
Verify the KafaREST log before stopping the VM. Once no request is
coming to the VM. Proceed further.\
cmd: **cd /mnt/vol1/dh-ads/ confluent-5.5.0/logs         **\
**tail -100f kafka-rest.logs**\
\
*Stop the instance → click on edit → under machine configuration →
select N2D →under machine type select required configuration (given by
developers) → check for the service account to be same as earlier
service account → save changes → start the instance *

6\. Then login into the instance and check for all the service (i.e
Kafka, kafka-rest, zookeeper) in the following path\
Cmd: **cd /mnt/vol1/dh-ads/supervisord/supervisord.d/         **\
**ls**

7\. You need to check if kafka is stable in logs (optional)\
Cmd: **cd /mnt/vol1/dh-ads/ confluent-5.5.0/logs         **\
**tail -100f server.logs**\

8\. Once its stable (get confirmation from developer) add back the
instance to group\
\
Cmd:**  gcloud compute instance-groups unmanaged add-instances 
dh-gcp-ads-kafka-nrt-asia-south1-a-mig \\**

**    \--zone=asia-south1-a \\**

**    \--instances=dh-gcp-ads-analyticsnrt-kafka-n2**

**9. Follow same steps to all the instances**

 
