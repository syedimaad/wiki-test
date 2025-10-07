Analysis of Missing Embeds from start point of the pipeline i.e daily
new items from josh video meta to end of the pipeline where these embeds
are being used in prod.

**Architecture of pipeline**

Steps to retrieve items at each end:

1.  The pipeline starts with 100% of new items which are uploaded the
    day before the analysis. We can get this data from
    `(“josh_meta”.”josh_video_meta”)` table

2.  Subsequently, a portion of these items are sent to GCP(old version
    users data), resulting in a loss of x% of the data, as indicated
    within the same table

3.  These items are pushed to the Kafka request topic(
    `josh_video_embed_generation_request`) by the API team. Logs are
    maintained by them. By querying the request topic, we can determine
    the percentage of data loss between step 2 and step 3.

4.  Next, the ML pipeline processes the payloads from the Request Topic
    and transfers them to the respective Response Topics(
    `josh_video_embed_generation_response & josh_video_embeddings`). The
    logs for this stage are maintained by `josh-ai-labs`. It is
    important to note that there can be scope of three types of losses
    within this stage, including bugs, pre-filters applied at the code
    level, and failures of fully loaded worker

5.  The Response Topic contains both meta`(ES: "ugc-prod-contents")` and
    embeddings `("josh_meta"."josh_video_blip_128_embedding"`)
    information, which is then directed to multiple data storage
    sources. In the case of meta Topic, three possible losses may occur
    BigQuery, ES, and Oblix. Similarly, for embeddings Topic, there are
    two possible loss scenarios: BigQuery and Oblix. API team is
    responsible for this step.

6.  Now From BigQuery, data is consumed by prod RocksDB. Anurag handles
    this part. Loss of data is being tracked by Sumo logic monitoring by
    Harish.\
    <https://verse.in.sumologic.com/ui/#/search/c38d65be_d096_2023_0902_e07f51c52051>\
    Query:

`_sourceCategory="josh/prod/gke/logs/stdout" "item embedding missing list"`

Ans also those missing items are being logged by Harish and missing
RocksDB items are stored in a temp table
`josh-prod-392409.josh_in_ailab.elt_rocksdb_miss`

**Daily Report Format**

Embedding Tracker Summary Date: 2023-09-21 Blip embedding generation
pipeline1. New items in josh-video-meta table: 141850 2. Items lost
before input Kafka topic: 74 3. Items lost in pipeline processing: 1
RocksDB Summary with frequency threshold of items called \>= 1 times 1.
Total item missed: 4083 2. Invalid item ids (no valid content meta): 119
3. Valid item ids embedding missing in serving (considering expected
delay 3): 3626 3a. Item\'s embedding present in the athena table: 2449
3a1. Warm table: 2358 3a1a. Missing in both hot and cold SST pipeline: 0
3a2. Non-warm table: 91 3a3. Not present in
table(josh_content_uuid_misc_ids_mapper): 0 3b. Item\'s embedding not
present: 1177 3b1. less than 5 sec: 332 3b2. older item: 845 3b3. failed
in pipeline: 0 4. Valid item ids embedding missing in serving: 2630 5.
Valid item ids not present in content meta: 157 RocksDB Summary with
frequency threshold of items called \>= 5 times 1. Total item missed:
192 2. Invalid item ids (no valid content meta): 7 3. Valid item ids
embedding missing in serving (considering expected delay 3): 56 3a.
Item\'s embedding present in the athena table: 18 3a1. Warm table: 15
3a1a. Missing in both hot and cold SST pipeline: 0 3a2. Non-warm table:
3 3a3. Not present in table(josh_content_uuid_misc_ids_mapper): 0 3b.
Item\'s embedding not present: 38 3b1. less than 5 sec: 24 3b2. older
item: 14 3b3. failed in pipeline: 0 4. Valid item ids embedding missing
in serving: 141 5. Valid item ids not present in content meta: 6

Description:

`New items in josh-video-meta table`: newly created items on \<Date\>
and these items are present in josh-video-meta table.

`Items lost before input Kafka topic`: items those were created on
\<Date\> and not present in
kafka-topic(josh_video_embed_generation_request).

`Items lost in pipeline processing`: Items failed in blip-azure-service
pipeline.

`RocksDB Summary`

Here we are taking the logs from sumologics for last 24 hours

`Total item missed`: number of items missed during fallback in rocksdb

`Items missed in RocksDB query and item occurance more than t`: number
of items missed during fallback in rocksdb and having occurrence of item
is more than t

`Invalid item ids`: Invalid item ids here are some eg. 1688743016075,
i_81dc32a2-c654-48b1-90d1-ceef3135f42e

`Valid item ids`: valid item ids missed during fallback in rocksdb out
of total item missed.

`- Item's embedding present`: number of Items embedding present in
blip-128 embedding table out of valid item ids.

`Warm`: warm items embedding present in blip-128 embedding table out of
Item's embedding present.

`Missing in both hot and cold`: warm item's embedding present in
embedding table but missed in hot and cold store

`Not present in content meta`: warm item's embedding present in blip-128
embedding table but not present in content meta

`Non-warm`: non-warm items embedding present in blip-128 embedding table
out of Item's embedding present.

`Not present in table(josh_content_uuid_misc_ids_mapper)`: Item's
embedding present in blip-128 embedding table but not present in
josh_content_uuid_misc_ids_mapper table.

`- Item's embedding not present`: valid item id's embedding not present
in blip-128 embedding table.

`Items present in josh_video_meta`: valid item id's embedding not
present in blip-128 but item present in content meta table.

`Items not present in josh_video_meta`: Items not even present in
blip-128 embedding table and content meta table.

Alerting Space:
<https://mail.google.com/chat/u/0/#chat/space/AAAA8Yq_teY>

Repo:
<https://gitlab.dailyhunt.in/josh-ai-labs/embedding-tracker/-/tree/gcp?ref_type=heads>
