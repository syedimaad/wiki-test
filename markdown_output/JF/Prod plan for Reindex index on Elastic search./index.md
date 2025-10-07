To release /typeAhead search in josh. We need to reindex 5 Es index. The
index and there size information is present in attached xls file. During
the reindex process, Write will be stopped and reindex process will be
start.

Existing index informationas in mentioned format

index name → alias. : elastic search cluster

ugc-users-v3 -\> ugc-users :
[josh-users-es.myjosh.in:9200](http://josh-users-es.myjosh.in:9200)\
ugc-hashtag-v2 -\> ugc-hashtags :
[josh-hashtags-es.myjosh.in:9200](http://josh-hashtags-es.myjosh.in:9200)\
josh-zones-v1 -\> josh-zones :
[josh-discovery-es.myjosh.in:9200](http://josh-discovery-es.myjosh.in:9200)\
ugc-challenge-v1 -\> ugc-challenge :
[josh-challenges-es.myjosh.in:9200](http://josh-challenges-es.myjosh.in:9200)\
ugc-contests-v1 -\> ugc-contests :josh-challenges-es.myjosh.in:9200

**Final changed Index alias will be as given below. The Elastic host
will be same**

ugc-users-v4 -\> ugc-users

ugc-hashtag-v3 -\> ugc-hashtags

josh-zones-v2 -\> josh-zones

ugc-challenge-v2 -\> ugc-challenge

ugc-contests-v2 -\> ugc-contests

[https://docs.google.com/spreadsheets/d/1SVTUzhpKGBsE_jebs64cKLtbd8-AS51UOznZjg_uBWE/edit#gid=0](https://docs.google.com/spreadsheets/d/1SVTUzhpKGBsE_jebs64cKLtbd8-AS51UOznZjg_uBWE/edit#gid=0){card-appearance="inline"}

[**Reindexing process Steps :**]{.underline}

1.  Stop Write on Existing index. Read will be served as it is. The
    below Write jobs will be stopped.

    1.  Reaction Job By Feed : Ikjot

    2.  Another job from api :

2.  Checking Disk/CPU/Memory on elastic cluster as Reindex process will
    take additional resources. The details of rough estimation are
    attached in above google sheet.

3.  Start Reindex using Reindex Api with

    bashvar src_index = \"ugc-users-v2\" var dest_index =
    \"ugc-users-v2\" curl -HContent-Type:application/json -XPOST
    localhost:9200/\_reindex?wait_for_completion=false&pretty -d\'{
    \"source\": { \"index\": \"\'\$src_index\'\" }, \"dest\": {
    \"index\": \"\'\$dest_index\'\" } }\' done

4.  Check the status of Reindex task using tasks elastic api:

    1.  `GET _tasks/oTUltX4IQMOUUVeiohTt8A:12345?wait_for_completion=true&timeout=10s`

    2.  `GET _tasks?actions=*reindex&wait_for_completion=true&timeout=10s`

5.  Once the Reindex finished. The alias will be switched to new Es and
    removed from old index. We use alias in code to access index. Hence
    no change required in feed-engine. The api code to change the alias
    for josh-zones

POST https://host:port/\_aliases { \"actions\": \[ { \"remove\": {
\"index\": \"josh-zones-v1\", \"alias\": \"josh-zones\" } }, { \"add\":
{ \"index\": \"josh-zones-v2\", \"alias\": \"josh-zones\" } } \] }

Few elastic reference docs are mentioned below.

[https://www.elastic.co/guide/en/elasticsearch/reference/7.10/reindex-upgrade-inplace.html](https://www.elastic.co/guide/en/elasticsearch/reference/7.10/reindex-upgrade-inplace.html){card-appearance="inline"}

Document shared by [Elastic.co](http://Elastic.co) team for same.

[https://www.elastic.co/blog/changing-mapping-with-zero-downtime](https://www.elastic.co/blog/changing-mapping-with-zero-downtime){card-appearance="inline"}\
[https://www.elastic.co/blog/reindex-is-coming](https://www.elastic.co/blog/reindex-is-coming){card-appearance="inline"}
