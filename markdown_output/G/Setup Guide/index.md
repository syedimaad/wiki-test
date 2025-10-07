Gitlab Repository:
<https://gitlab.dailyhunt.in/nh-ads-platform/dh_global_location_api>

**Needed stack:**

1.  golang

2.  mysql (for pincode & constituencies)

    1.  DB name: nhloc

3.  redis

4.  kafka (for location learning)

**Installation needed:**

brew install rocksdb export
CGO_CFLAGS=\"-I/usr/local/Cellar/rocksdb/8.9.1/include\" \\ export
CGO_LDFLAGS=\"-L/usr/local/Cellar/rocksdb/8.9.1 -lrocksdb -lstdc++ -lm
-lz -lsnappy -llz4 -lzstd\"

**Data to download:**

sqlite:
<https://data.geocode.earth/wof/dist/sqlite/whosonfirst-data-admin-latest.db.bz2>

mmdb:

note put the files at desired place as per the config
(/dev/config/apiConfig.json)

cmd to copy mmdb file:

mkdir backup/mmdb cp mmdb/\* backup/mmdb

**Connection needed:**

If you don't have the redis &kafka in local connect it to **qa env &**
if needed whitelist your machine to connect to these. (kafka is not
required for location serving node, it is for location learning)

\"redis\": { \"hostAddresses\": \[ \"10.52.0.24:7000\" \], }, \"kafka\":
{ \"bootstrapServers\":
\"dh-gcp-ads-kafka-qa-n1.dailyhunt.in:9092,dh-gcp-ads-kafka-qa-n2.dailyhunt.in:9092,dh-gcp-ads-kafka-qa-n3.dailyhunt.in:9092\",
\"autoOffsetReset\": \"earliest\", }

**Steps:**

1.  Download / clone the repository from

    git clone
    git@gitlab.dailyhunt.in:nh-ads-platform/dh_global_location_api.git

2.  go to dh_global_location_api directory

    cd dh_global_location_api

3.  build the code

    go build .

4.  run the code

    ./dh_global_location_api
