17

# Aim

The document aims at capturing the proposal of adding a client Id based
Load Balancer for AdEngine and its advantages vs disadvantages. This
also captures how can we go ahead with this with no risk.

# What is the proposal?

Currently, Load Balancer for AdEngine distributes traffic equally to all
active AdEngine serving VM. The routing is done at the request level.
This means all VMs get an almost equal number of requests to handle. One
disadvantage with this approach for routing is a user\'s request can end
up in different VMs, resulting in no way to track users\' recently
handled requests but to go to Redis (Central Cache) and valid if
required.

Currently, every request engine has an extremely high dependency on
Redis to get Client Profile, Audience Segment, deduplication of
requests, impressions, clicks, etc... This requires a network call to be
made to Redis, and each network call translates to multiple Redis
commands being executed on Redis cluster, the more the number of
commands executed more the compute requirement. High compute requirement
contributes to high cost as well. This also makes us extremely highly
dependent on Redis. Redis can be a single source of failure. We have not
restarted Redis VM ever, and if done it would have a business impact.

# Questions that are addressed below

1.  Why Redis?

2.  Is our usage pattern tightly coupled to only Redis? Is it a Red
    flag? Are there better solutions available in the market?

3.  Can we reduce dependency on Redis and if done, is it worth it?

4.  What are the cost implications of having such a big Redis Cluster?
    The current Cluster size is 1.4 TB of memory and 192 CPUs.

5.  Do we need to make a network call to Redis for every request?

6.  Can we have a disk-based replacement of Redis, without impacting the
    performance of the serving Engine? Assuming disk-based solutions
    would be cost-effective.

# Quick Snapshot of below

If we can route the request for a client Id to a specific VM then that
VM can cache data locally with a TTL (say 5 mins) and treat Redis as a
universal Caching layer. This will result in the low command being
executed on Redis (Low compute requirements). We can downscale our Redis
cluster.

This allows us to have visibility into past ads being served to the user
without going to the external system and opens up a new dimension of
thoughts in serving Ads. Like, a user was served A1 and A2 ad in the
last 10 seconds, given we know that can we serve better. Currently, this
is achievable with client change but it is just an example.\
**Note**: Later on (If required), we can move to disk-based low latency
stores that can act as a fallback of local cache.

# What Data is saying?

## Is traffic equally distributed if hashing is done based on client Id?

**Yes**, can be checked
[here](https://docs.google.com/spreadsheets/d/1sX1L6TQSdhoJ2cpnsZpR1sl9l5w12c-mc9A30aL1a94/edit#gid=1032201448).
Pulled data is consistent and has been taken for 5 days worth of
traffic.

## What would be the additional memory requirement for AdEngine VM if it manages local cache as well?

Memory requirement is captured
[here](https://docs.google.com/spreadsheets/d/1sX1L6TQSdhoJ2cpnsZpR1sl9l5w12c-mc9A30aL1a94/edit#gid=1989132547).
Below are the memor requirement keeping a TTL of 5 mins:

  ------------------- -----------------------------
  **Number of VMs**   **Memory Requirement (MB)**
  50                  420
  100                 208
  150                 138
  200                 104
  ------------------- -----------------------------

## How many network calls can be reduced?

Details are captured
[here](https://docs.google.com/spreadsheets/d/1sX1L6TQSdhoJ2cpnsZpR1sl9l5w12c-mc9A30aL1a94/edit#gid=1192583019).
If we keep a TTL of 5 mins then we can reduce around 3 network calls per
user. If seen at a macro level, we can reduce around 700 mn to 800 mn
network calls per day. This will, incur less network bandwidth as well.

## How much response time improvement can we expect?

Currently, Redis calls by AdEngine take \~3-4 ms (including network
time). Since we will be reducing this, VM can crunch more requests
thereby resulting in less VM being needed in the Serving Cluster. We can
quantify the improvement only after going to production for this.

# How can this be solved?

GCP provides Consistent Hashing based network Load Balancers called
[**Maglevs**](https://research.google/pubs/pub44824/). Since it is
consistent Hashing based so scenarios downscale and upscales are handled
out of the bound by Maglevs and we need not worry. When a node goes out
of rotation, requests are directed to a new VM and rebalancing happens.
Given we know this we can start having client Profiles or other cached
information that we pull from Redis, in the VM application itself,
resulting in fewer Redis network calls.

**What happens when a node goes out of rotation OR gets added to
rotation during autoscaling?**

During downscale, Maglevs redirect the requests for client Ids that were
mapped to the VM going out of the serving cluster to another VM. Would
this result in more traffic/burden to another VM? Since it is consistent
hashing-based routing, traffic will quickly adjust as per new cluster
configs.

**Note**: This is already running smoothly in S2S for quite some time
now.

**Would there be a cache miss when upscale/downscale happens?**

Yes, and in such a scenario, Redis will act as a fallback main cache.
This is effectively the current state of AdEngine. currently, all
requests come to Redis

Once this is done, we can better estimate usage of Redis Cluster and
downscale accordingly if required. Depending on the numbers only we can
gauge if a fast disk-based layer can replace Redis at this time.

# How to move to production with No RISK?

**Steps**:

1.  Have a separate MIG of VMs with Maglev-based routing and transfer 1%
    of the overall traffic to this cluster.

2.  Monitor and validate that each VM is serving an almost equal number
    of requests

3.  Monitor memory and VM system metrics like CPU, RPS, failures, load
    average, etc

4.  Validate that Redis is working as expected and no anomaly is found.

5.  Let it run for 2,3 days.

6.  Slowly increase the traffic in exponential manner (1%,2%,5%,10%,20%,
    50%,100%) and during each transition follow steps 1 to 5.

7.  At this stage, all the traffic will be moving via the new MIG
    cluster with Maglevs. Update LB logic to avoid minor computation
    that we added for transition.

# Summary

The above activity will have the below-mentioned advantages:

1.  Improved Ad response time as we will be reducing network calls to
    Redis

2.  We will have visibility across ad-Request for a user. This will open
    up new opportunities for implementation or product requirements.

3.  We expect Redis commands per second to reduce by more than 10 times.
    10 times because AdEngine makes multi-get requests for a client Id.
    Each network call translates to multiple commands in Redis. Each
    command consumes some resource

4.  Since the data says post this we can expect to reduce RPS on Redis
    significantly, thereby opening an opportunity to move to a
    persistent key-value store database like Rocks-DB, which will be
    much cheaper as compared to an in-memory database.

5.  Increasing the local TTL from 5 mins to 10 mins will have a
    proportional gain on the above-mentioned points.

**Note**: We would still need Redis for usages like hard stop times
between OIs, but that can be managed with just one instance itself. Once
we reach that stage new options would surface.

# **References**:

[https://research.google/pubs/pub44824/](https://research.google/pubs/pub44824/){card-appearance="inline"}

[https://docs.google.com/spreadsheets/d/1sX1L6TQSdhoJ2cpnsZpR1sl9l5w12c-mc9A30aL1a94/edit#gid=1032201448](https://docs.google.com/spreadsheets/d/1sX1L6TQSdhoJ2cpnsZpR1sl9l5w12c-mc9A30aL1a94/edit#gid=1032201448){card-appearance="inline"}
