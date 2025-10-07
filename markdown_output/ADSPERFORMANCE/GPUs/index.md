**Steps to power on/off GCP gpu machine, use GPUs judicially**

#dh-gcp-ads-gpu-learning-n1-vm 10.50.16.53
#dh-gcp-ads-gpu-learning-n2-vm 10.50.16.57 #dh-gcp-ads-gpu-learning-n3
curl
https://cicd.dailyhunt.in/view/GCP/job/GPU1-GCP-PROD-START/build?token=RCRqPbH86t
&& sleep 90 curl
https://cicd.dailyhunt.in/view/GCP/job/GPU1-GCP-PROD-STOP/build?token=RCRqPbH86t
&& sleep 150 curl
https://cicd.dailyhunt.in/view/GCP/job/GPU2-GCP-PROD-START/build?token=RCRqPbH86t
&& sleep 90 curl
https://cicd.dailyhunt.in/view/GCP/job/GPU2-GCP-PROD-STOP/build?token=RCRqPbH86t
&& sleep 150 curl
https://cicd.dailyhunt.in/view/GCP/job/GPU3-GCP-PROD-START/build?token=RCRqPbH86t
&& sleep 90 curl
https://cicd.dailyhunt.in/view/GCP/job/GPU3-GCP-PROD-STOP/build?token=RCRqPbH86t
&& sleep 150

\- please add the new GPU info here.
