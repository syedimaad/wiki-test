17

# Aim

The document aims at capturing the dev spec to implement IP training to
improve the accuracy of Location Service via IP resolution

# Architecture Diagram

\<TO BE ADDED\>

# Components

## Kafka request consumer

<http://saluber.dailyhunt.in/d/kafkastats/kafka-stats?orgId=22>

We will be creating a new consumer group to read from the topic
**reqmessages** topic and transform the events into the below structure

{ \"ip\": \"101.102.103.104\", \"latitude\": 33.45667456, \"longitude\":
78.345657546, \"city\": \"bengaluru\", \"client_id\":
\"dh.asdfgdfg456gh78\", \"epochtime\": 1655098405000 }

**Application parameters**:

**time_range** → 10mins or 600 seconds or 60000 ms

**bit_range** → 4 bit

**Transformation logic**

**Key template** → \<timerange_quotient\>-\<ip1.ip2.1p3\>-\<ip_range\>

**timerange_quotient** → **epochtime** / **time_range (**1655098405000 /
60000**) = 27584973**

**ip1.ip2.1p3 →** 101.102.103

**ip_range** → last 8 bits of above ip i.e **104** divided by bit_range
→ 104 / 4 = 26

Final Key → **27584973-101.102.103-26**

{ \"27584973-101.102.103-26\" : { \"bengaluru\": 100, \"bengaluru_lat\":
33.46457567 \* 100, \"bengaluru_long\": 78.4545678 \* 100, \"pune\": 10,
\"pune_lat\": 33.456678789, \"pune_long\": 78.1233452345,
\"created_at\": 1655098405000 } }

## Redis

We will be utilizing the **HSET data structure** provided by Redis for
this use case. All the fields except in the above response will be
incremented. We will be using **HINCRBYFLOAT**, **HINCRBY,**
**HGETALL,** and **HSETNX** to make updating the response an atomic
operation.

More details about each command
[https://redis.io/commands/hset/](https://redis.io/commands/hset/){card-appearance="inline"}

- We are expecting to update around 1,50,000 in a span of 10 mins.

- We would be keeping a TTL of 30 mins for each key.

- We should be using pipelines functionality provided by Redis to bulk
  update the Keys

- We are expecting to execute \~**6000** commands per second on Redis
  with this. We will tune more based on feedback

## Global Location Service

The global location service will read from Redis using **HGETALL** and
apply basic Heuristics to come up with a city-based on response.

**Some heuristics to apply are as below**

1.  If only one city exists in the response with more than **10 counts**
    return the city against the input IP

2.  If more than 1 cities are present in the response, check for the gap
    in the absolute count between the top 2 cities. If the gap in counts
    between the top two cities is more than **20** chose the max one
    with high confidence score if not then chose the max one with a low
    confidence score.

To handle edge cases around the start of the interval. Global location
service to pull two keys against an IP. One based on the current time
range and one with the previous time range for the same IP. For Example:
While pulling for **27584973**-101.102.103-26 also pull for
**27584972**-101.102.103-26. This will help improve the coverage

# Monitoring

Since the window for training and predicting the location is low, it
would become hard to debug production issues if any. We can get started
with basic monitoring and enhance it with time.
