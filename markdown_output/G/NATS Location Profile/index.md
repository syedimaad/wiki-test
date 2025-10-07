Referring to
[https://nats.io/](https://nats.io/){card-appearance="inline"}

Currently we are pushing the Location Profile ,which is created through
[Location Profile
Processing](https://gitlab.dailyhunt.in/nh-ads-platform/locationprofileprocessing),
into Redis, we plan to eventually shift to NATs Data which is a faster
key value pair store.

## Uses of NATS

- Key Value Store similar to Redis

- Have a Queue known as History which works like Kafka to process and
  consume data/message stored in NATS

## Flow Change

- Addition of NATS VM in config file.

  - bash nats://dh-gcp-ads-kafka-nats-n1.dailyhunt.in:4222
    nats://dh-gcp-ads-kafka-nats-n2.dailyhunt.in:4222
    nats://dh-gcp-ads-kafka-nats-n3.dailyhunt.in:4222

- Currently, we are setting keys in NATS along with Redis in the
  following format

  - `ads_user_profile user.dh.<client_id>.location`

  - ads_user_profile is a bucket containing a key called user.\
    user has a subkey of `dh`,`j`, or `pv` refers to DailyHunt, JOSH and
    Public Vibe respectively where we store the location for that
    client.

**NOTE:** location contains a JSON Format which is similar to how we
store data in Redis currently, reason for doing this is to reduce the
number of keys present in NATS

## Sample CLI Commands to Fetch Data

`nats kv watch ads_user_profile user.dh.*.location`

Fetch location for dh users which are pushed in NATS. \* is used to
fetch for all users present, can specify a user there as well and get
data for that user only.

\[2023-08-07 12:49:14\] PUT ads_user_profile \>
user.dh.LzVsdzc3VnZCOGNZa2NUV3liTVdSQT09A.location: {\"city\":
\"bengaluru\", \"state\": \"karnataka\", \"country\": \"india\",
\"cityId\": \"c17_407\", \"stateId\": \"s17\", \"countryId\":
\"85632469\", \"countryCode\": \"IN\", \"constituency\":
\"shivajinagar\", \"constituencyId\": \"CN2060_S17\", \"confidence\":
0.4, \"latitude\": 12.9593, \"longitude\": 77.5862, \"ip\":
\"157.45.223.25\", \"source\": \"IP\", \"last_updated\": \"2023-08-07
12:49:14\", \"isp\": \"jio\", \"ISOCountryCode\": \"IND\"} \[2023-08-07
12:49:14\] PUT ads_user_profile \> user.dh.1319154382.location:
{\"city\": \"bengaluru\", \"state\": \"karnataka\", \"country\":
\"india\", \"cityId\": \"c17_407\", \"stateId\": \"s17\", \"countryId\":
\"85632469\", \"countryCode\": \"IN\", \"pincode\": \"\",
\"constituency\": \"shivajinagar\", \"constituencyId\": \"CN2060_S17\",
\"latitude\": \"12.9572883\", \"longitude\": \"77.5858797\", \"ip\":
\"42.105.126.207\", \"isp\": \"vodafone\", \"source\": \"GPS\",
\"ISOCountryCode\": \"IND\"} \[2023-08-07 12:49:14\] PUT
ads_user_profile \> user.dh.NU0vNlVZQXJkRFdzdGpQNHlJYm16QT09A.location:
{\"city\": \"ahmedabad\", \"state\": \"gujarat\", \"country\":
\"india\", \"cityId\": \"c12_229\", \"stateId\": \"s12\", \"countryId\":
\"85632469\", \"countryCode\": \"IN\", \"pincode\": \"380004\",
\"constituency\": \"gandevi\", \"constituencyId\": \"CN1116_S12\",
\"latitude\": \"NA\", \"longitude\": \"NA\", \"ip\": \"49.34.115.205\",
\"isp\": \"jio\", \"source\": \"IP\", \"ISOCountryCode\": \"IND\"}
\[2023-08-07 12:49:14\] PUT ads_user_profile \>
user.dh.YVBzSFZvVXUwaHdneDA5R010Tyt5Zz09A.location: {\"city\":
\"bilaspur\", \"state\": \"chhattisgarh\", \"country\": \"india\",
\"pincode\": \"495006\", \"cityId\": \"c7_192\", \"stateId\": \"s7\",
\"countryId\": \"85632469\", \"countryCode\": \"IN\", \"constituency\":
\"ramgarh\", \"constituencyId\": \"CN3439_S16\", \"confidence\": 0.4,
\"latitude\": 22.0885, \"longitude\": 82.1693, \"ip\":
\"106.194.177.235\", \"source\": \"IP\", \"last_updated\": \"2023-08-07
12:49:14\", \"isp\": \"airtel\", \"ISOCountryCode\": \"IND\"}
\[2023-08-07 12:49:14\] PUT ads_user_profile \>
user.dh.c1_d1_a1_1912902326.location: {\"city\": \"\", \"state\": \"\",
\"country\": \"\", \"cityId\": \"\", \"stateId\": \"\", \"countryId\":
\"\", \"countryCode\": \"\", \"pincode\": \"\", \"constituency\": \"\",
\"constituencyId\": \"\", \"latitude\": \"NA\", \"longitude\": \"NA\",
\"ip\": \"103.240.204.5\", \"isp\": \"\", \"source\": \"\"} \[2023-08-07
12:49:14\] PUT ads_user_profile \> user.dh.1570335984.location:
{\"city\": \"ahmedabad\", \"state\": \"gujarat\", \"country\":
\"india\", \"cityId\": \"c12_229\", \"stateId\": \"s12\", \"countryId\":
\"85632469\", \"countryCode\": \"IN\", \"pincode\": \"380004\",
\"constituency\": \"gandevi\", \"constituencyId\": \"CN1116_S12\",
\"latitude\": \"NA\", \"longitude\": \"NA\", \"ip\":
\"106.205.212.111\", \"isp\": \"airtel\", \"source\": \"IP\",
\"ISOCountryCode\": \"IND\"} \[2023-08-07 12:49:14\] PUT
ads_user_profile \> user.dh.TWxMcEZueXdJOUdtU3BvSzZBRGVhdz09A.location:
{\"city\": \"hyderabad\", \"state\": \"telangana\", \"country\":
\"india\", \"pincode\": \"500082\", \"cityId\": \"c32_800\",
\"stateId\": \"s32\", \"countryId\": \"85632469\", \"

`nats kv history ads_user_profile user.dh.VDgxV1I1ZkUyTHNzdVdZd1hRR0xHZz09A.location`

Get History of a key with the changes, currently 100 latest changes are
recorded

\[dh-ads@dh-gcp-ads-kafka-nats-n1 \~\]\$ nats kv history
ads_user_profile user.dh.VDgxV1I1ZkUyTHNzdVdZd1hRR0xHZz09A.location
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
\_ History for ads_user_profile \>
user.dh.VDgxV1I1ZkUyTHNzdVdZd1hRR0xHZz09A.location \_
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
\_ Key \_ Revision \_ Op \_ Created \_ Length \_ Value \_
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
\_ user.dh.VDgxV1I1ZkUyTHNzdVdZd1hRR0xHZz09A.location \_ 21677 \_ PUT \_
07 Aug 23 12:49 IST \_ 309 \_ {\"city\": \"\", \"s\...ryCode\": \"IND\"}
\_
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
