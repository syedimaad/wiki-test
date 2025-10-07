# System Design

Above is the flow of real time system which is deployed for blip service

# API Details:

- Original Video URL (No Transcoding) is read from the request.

- Last 150 frames are excluded.

- Out of the remaining frames, 5 equidistant frames are chosen.

- Above frames are passed through BLIP model to get embedding of 768
  dims.

- BLIP 128 embedding will be generated with PCA model using above 768
  dims

- L0, L1 & L2 clusters will be identified using various KMeans models
  with the input of BLIP 768 embedding

- One frame per second in the first 2 seconds of the video is send to
  celebrity zone pipeline to get identified zones along with cosine
  similarity values

- Using Hive vector and BLIP 128 embedding, the overall glamour score
  and glamour level will be computed using a RandomForest model

- Some raw features and embeddings will be computed using the super
  model with the input of 10 equidistant frames along with total video
  length

The API & Poller script is being run on 20 Standard_NC8as_T4_v3
instances having one 16 GB GPU and 8 CPU Cores with 2 workers per pod
and 1 pod per node/instance which intotal turns to 40 workers of API and
Poller.

# More Information on Individual Components:

- Celebrity Zones : Celebrity Zones

- SUPER MODEL : SUPER MODEL

- Glamour Rf Model : Glamour Random Forest Model

# Import Links:

- request topic -
  [http://prod-kafkaui-az.myjosh.in/topics/josh_video_embed_generation_request](http://prod-kafkaui-az.myjosh.in/topics/josh_video_embed_generation_request?o=-3&p=-1&q&s=10#messages)

- response topic -
  [http://prod-kafkaui-az.myjosh.in/topics/josh_video_embed_generation_response](http://prod-kafkaui-az.myjosh.in/topics/josh_video_embed_generation_response?o=-1&p=-1&q&s=20#messages)

- embedding response topic (Azure) -
  [http://prod-kafkaui-az.myjosh.in/topics/josh_video_embeddings](http://prod-kafkaui-az.myjosh.in/topics/josh_video_embeddings?o=-3&p=-1&q&s=10#messages)

- embedding response topic (GCP) -
  [http://josh-kafkaui-gke.myjosh.in/topics/josh_video_embeddings](http://josh-kafkaui-gke.myjosh.in/topics/josh_video_embeddings?p=-1&s=50&o=-1#messages)

- grafana -
  [http://monitoring-prod.myjosh.in/d/jwPKIsniz/strimzi-kafka-exporter?orgId=1&var-kubernetes_namespace=kafka&var-strimzi_cluster_name=kafka-cluster&var-consumergroup=prod_blip_request_cg-1&var-topic=josh_video_embed_generation_request](http://monitoring-prod.myjosh.in/d/jwPKIsniz/strimzi-kafka-exporter?orgId=1&var-kubernetes_namespace=kafka&var-strimzi_cluster_name=kafka-cluster&var-consumergroup=prod_blip_request_cg-1&var-topic=josh_video_embed_generation_request&from=now-6h&to=now&refresh=5s)
