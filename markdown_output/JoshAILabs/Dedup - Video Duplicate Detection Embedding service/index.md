**Git link** :
<https://gitlab.dailyhunt.in/josh-ai-labs/dedup-azure-service>\
\
**Algorithm for generation of Dedup Embeddings:**

1.  Takes video of **75 frames** each of size: (**224,224,3**)
    \[**equidistant frames are selected**\]

2.  Imports **pre-trained Mobile-Net** model to calculate embeddings for
    each of the frames

3.  After getting embeddings for 75 frames, **aggregation** is done by
    **summing up to get a single embedding** for the video

4.  Embeddings are then saved in the following location:\
    \
    f"<https://joshprodaimlsa.blob.core.windows.net/dedup/dedup-embeddings-v2/0000025d-de56-41af-94b4-665e7e9d4c8a.npz>\
    \
    **Storage account**: joshprodaimlsa\
    **Container**: dedup\
    **Blob_path** :
    dedup-embeddings-v2/0000016f-e827-4da8-ba45-dc5691f8b2c6.npz\
    \
    \
    **Deployment details**:\
    It is currently running on 10 pods. Configuration of the pods :
    **Standard nc8as t4 v3 (8 cpu cores and 1 gpu)**

**For checking the service:**

1.  ssh into the azure instance : ssh -i
    \<path\>/josh-dev-transcoding-key.pem <azureuser@10.70.32.4>

2.  display the pods name running under dedup namespace : kubectl get
    pods -n dedup

3.  Use any one pod_name and get inside the container: kubectl exec -it
    \<pod_name\> -n dedup  bash

4.  display the logs and use tail command to view recent logs.

5.  sudo docker build -t
    [joshprodregistry.azurecr.io/dedup_api:latest](http://joshprodregistry.azurecr.io/dedup_api:latest)
    .

    sudo docker push
    [joshprodregistry.azurecr.io/dedup_api:latest](http://joshprodregistry.azurecr.io/dedup_api:latest)\
