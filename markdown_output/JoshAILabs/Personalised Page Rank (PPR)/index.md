# Overview

**PPR** is a graph based algorithm, where a graph **comprising** of
**nodes** (items/videos) and their intermediate **edges** (**weighted**
connection between the nodes/items/videos), is **traversed** from a
**target** node in a **random** fashion to produce **relavent** list of
nodes balancing out exploration and exploitation required in a
recommender systems

## Phase 1 : Graph Generation

### High level overview

1.  Consider events data for defined target period, comprising of
    features/columns like session_id, client_id, item_id and other event
    level information like played_duration, is_liked etc

2.  We then filter out these events based on some quality levers(will be
    mentioned further)

3.  Futher, the items at a session level will be paired to form all
    possible combinations of items pairs (so called co-occuring pairs of
    items).\
    This is done seperately for both filtered played and liked events\
    These pairs define an edge in our graph

4.  We then assign a default weight of 1 to each of the edge

5.  Further, the assigned weight is boosted based on zones similarity
    (common number of zones between items of a pair

6.  Lastly, all the pairs are aggregated across all sessions to end up
    with distinct pairs while edge weights are summed up during this
    process

7.  Finally we are left with a list of item pairs along with there
    corresponding edge weight which is a culmination of common
    occurances across multitude of users, boosted by similarity between
    them

### Involved Levers or Parameters

- **required days** : the period for which the events are to be
  considered

- **minimum good session time** (in mins) : the minumum value of session
  time (in mins) for which the events to be considered

- **maximum good session time** (in mins) : the maximum value of session
  time (in mins) for which the events to be considered

- **max item age in days** : the maximum age of an item for which the
  events to be considered\
  basically, the max age of an item that can potentially exist in the
  final graph

- **candidate algos** : the set of candidate algorithms for which the
  events to be considered

- **clvs** : the set of clvs for which the events to be considered

- **nav tab** : the set of navigation tabs for which the events to be
  considered

- **minimum video length** *(newly introduced)* : the minimum video
  length (in secs) of an item for which the events to be considered

- For **liked** **events**:

  - **minimum qualifying play duration** : the minimum play duration in
    secs to directly qualify an event

  - **minimum pcc** : the minimum pcc (play duration / video length) to
    qualify an event

  - **pairs boosting formula** :\
    **2.75** \* (1 if **no** common zones exist else {**1.5** + 0.2 \*
    \[**number** of common zones of the pair\]}) \* (**count** of
    co-occurance of the pairs across all sessions)

  - **minimum edge weight** : the minimum value of the final edge weight
    of which the co-occurance pairs to be considered

- For **played** **events**:

  - **minimum qualifying play duration** : the minimum play duration in
    secs to directly qualify an event

  - **minimum acceptable pcc** : the minimum pcc (play duration / video
    length) to qualify an event, along with minimum acceptable play
    duration

  - **minimum acceptable play duration** : the minimum play duration in
    secs to qualify an event, along with minimum acceptable pcc

  - **pairs boosting formula** :\
    (1 if **no** common zones exist else {**1.0** + 0.2 \* \[**number**
    of common zones of the pair\]}) \* (**count** of co-occurance of the
    pairs across all sessions)

  - **minimum edge weight** : the minimum value of the final edge weight
    of which the co-occurance pairs to be considered

- **maximum pairs** : the maximum number of pairs to be finally saved
  (in regards to inference memory and latency concerns)

  --------------------------------------------------- ----------------------------------------------------------------------------------------------
  **Parameter**                                       **Value**
  required days                                       45 days of like events, 30 days of play events
  minimum good session time (in mins)                 2.5
  maximum good session time (in mins)                 60.0
  max item age in days                                100
  candidate algos                                     v2v \| coldstart \| mtl \| ppr \| blip \| graphdb \| als
  clvs                                                platinum+- \| gold +- \| silver+- \| iron+
  nav tab                                             FORYOU \| ENTITY_SEARCH_VIDEO \| SEARCH \| ZONE_FEED \| COLLECTION_VIDEOS \| USER_LATEST_TPV
  minimum video length (in secs)                      7.0
  minimum median pcc                                  0.3
  LIKE - minimum qualifying play duration (in secs)   3
  LIKE - minimum pcc                                  0.2
  LIKE - minimum edge weight                          3.2
  LIKE - extra boost factor                           2.75
  PLAY - minimum qualifying play duration (in secs)   15
  PLAY - minimum acceptable pcc                       0.9
  PLAY - minimum acceptable play duration (in secs)   5
  PLAY - minimum edge weight                          2
  maximum pairs                                       380,000,000
  --------------------------------------------------- ----------------------------------------------------------------------------------------------

#### Building Graph (Edge List Dataset Generation) - Code

1.  Checks for previous day's final success file of
    training_dataset_flattened_v4/v5

2.  Run the main.py script in latest image with required node
    configuration on GKE

    1.  Generate query based on date & other parameters ([Base
        Query](https://gitlab.dailyhunt.in/josh-ai-labs/ppr-graph-generation/-/blob/prod/queries.py))

    2.  Run query on GCP BigQuery and load the edge list dataset as
        pandas dataframe

    3.  Prune edge list dataset (99th percentile)

    4.  Generate Node degree dataset

    5.  Save both datasets to local folder named based on latest epoch
        time in seconds

    6.  Compute various metrics

    7.  Insert metrics to database (MongoDB) as well as store as json in
        the above mentioned local folder

    8.  Upload the folder to required cloud locations

## Phase 2 : Graph Inference

**(The Graph Random Walk Algorithm)**

### High level overview

Select the given target node/item/video in the graph as the **current**
node\
If given item is not present in graph, there's no possible
recommendation

For every walk (**surfer**), till certain count(**steps**):

1.  Get all the neighboring nodes of the current node\
    (if no neighboring node exists, exit the loop)

2.  Compute the visiting probablities of each of the neighboring nodes,
    based on their edge weights\
    Basically, the higher is the edge weight, higher the chances of
    visiting that node

3.  Chose a random node from the list of neighboring nodes based on the
    calculated probabilities

4.  Further, either chose the above random node or randomly chose a
    different node in the overall graph (based on **alpha**, the damping
    factor) as the current node

5.  Now store the current node in a high level node list and continue
    the process

Once done, Again\
For all the walks done,\
Aggregate all the node lists to arrive at distinct nodes along with
their occurance value across all walks, Further sort these nodes in
decending order of their occurance values\
Chose the top required number of nodes (**k**)

### Involved Levers or Parameters

- **surfers** : the number of random walks to be done concurrently
  (basically in parallel)

- **steps** : the number of times a surfer has to take a next move (this
  is the max number of nodes a surfer can traverse to)

- **alpha** or damping factor : the number or decimal value which
  defines the probability of either continuing the walk from the list of
  neighbours or chose some random node from the overall graph\
  This lesser the value, the more the walk proceeds in the path of
  neighbouring nodes and vice-versa\
  This parameter controls the explore-exploit nature of recommendation

- **k** : the top final required number of nodes, selected from the
  sorted list of nodes based on their occurance value across all the
  surfers

  --------------- -------------------------------------------------
  **Parameter**   **Value**
  surfers         4
  steps           12000
  alpha           35 (will be normalised by 100 during inference)
  k               120
  --------------- -------------------------------------------------

# System Design

[](https://viewer.diagrams.net/index.html?tags=%7B%7D&highlight=0000ff&edit=_blank&layers=1&nav=1#G1s3WKoj4qjPGV4foIo9iDbTJKjnxj4zYp)

Click to view [System
Design](https://viewer.diagrams.net/index.html?tags=%7B%7D&highlight=0000ff&edit=_blank&layers=1&nav=1#G1s3WKoj4qjPGV4foIo9iDbTJKjnxj4zYp)
in detail

# Components

- Graph Gen Code Repository :
  <https://gitlab.dailyhunt.in/josh-ai-labs/ppr-graph-generation/-/tree/prod>

- Graph Inference Code Repository :
  <https://gitlab.dailyhunt.in/josh-recsys/retrieval/-/tree/master>

- Image Registry :
  <https://console.cloud.google.com/artifacts/docker/josh-prod-392409/asia-south1/josh-prod-repository/ppr-graph-gen>

- Graph files location :
  <https://console.cloud.google.com/storage/browser/josh-ppr/input_files?project=josh-prod-392409>
  (`gs://josh-ppr/input_files/`)

- Airflow UI :
  <https://31f876a73e4f40ef8fef41318fbb66cc-dot-asia-south1.composer.googleusercontent.com/dags/ppr_graph_gen>

- Airflow Script :
  <https://gitlab.dailyhunt.in/josh-ai-labs/ppr-graph-generation/-/blob/prod/airflow-scripts/ppr_graph_gen.py>

- Metrics Dashboard UI :
  <http://10.180.128.17:8010/public/dashboard/5b4daad1-fda5-47a3-bfd6-7f3a7b09d8e4>

- CRON : `0 3 * * *` \[UTC\] (8:30 AM IST)

### Pipeline Process (Airflow Script) \[TECHNICAL\]

#### Stage 1 - Building Graph (Edge List Dataset Generation)

1.  Checks for previous day's final success file of
    training_dataset_flattened_v4/v5

2.  Run the main.py script in latest image with required node
    configuration on GKE

    1.  Generate query based on date & other parameters ([Base
        Query](https://gitlab.dailyhunt.in/josh-ai-labs/ppr-graph-generation/-/blob/prod/queries.py))

    2.  Run query on GCP BigQuery and load the edge list dataset as
        pandas dataframe

    3.  Prune edge list dataset (99th percentile)

    4.  Generate Node degree dataset

    5.  Save both datasets to local folder named based on latest epoch
        time in seconds

    6.  Compute various metrics

    7.  Insert metrics to database (MongoDB) as well as store as json in
        the above mentioned local folder

    8.  Upload the folder to required cloud locations

#### Stage 2 - Metrics Generation

1.  Query the database (MongoDB) for required metrics of latest graph

2.  Compare it with previously built graph as well as with graphs built
    previously for the last 7 days

3.  Send the report to required GChat Space (`[INFO] PPR Daily Runner`)

#### Stage 3 - Refresh PPR API Service

Send API request to provided webhooks of corresponding Gitlab PPR CI CD
Pipelines which inturn redeploy PPR API pods on AWS & GCP and wait till
new graph is loaded by parsing graph version from debug endpoint

# Experiment Tracker

+----------------------------+------------------------------------------+------------+
| **Experiment name**        | **Experiment in brief**                  | **Status** |
+----------------------------+------------------------------------------+------------+
| Use V5 Dataset             | to use `training_dataset_flattened_v5`   | Done       |
|                            | dataset for graph gen                    |            |
+----------------------------+------------------------------------------+------------+
| Update Candidate Algo      | - Currently, roughly around 25% of       | Done       |
| filters                    |   events (`v2v_recent|ppr|blip|graphdb`) |            |
|                            |   are being used for candidate gen       |            |
|                            |                                          |            |
|                            | - Possibility to pump it to 50%          |            |
|                            |   (`v2v|coldstart|mtl|ppr|blip|graphdb`) |            |
+----------------------------+------------------------------------------+------------+
| Update events quality      | - relax a multitiude of quality related  | Done       |
| thresholds                 |   thresholds to further avoid graph      |            |
|                            |   shrinkage                              |            |
+----------------------------+------------------------------------------+------------+
