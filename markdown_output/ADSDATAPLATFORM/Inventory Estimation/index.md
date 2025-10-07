16truelistfalse

## Running Monthly Job

1.  Extract 30 days of data.

2.  Sanitise and sort individual files

    daily_aggregations/scripts/sanitise.sh or related path

3.  Merge sort the sorted files into dailyaggregation.csv

    daily_aggregations/scripts/merge_sort.sh or related path

4.  Segregate dailyaggregation.csv into two parts( ensure memory does
    not spike)

5.  Remove last_seen from redis_setter.py

6.  Create a new ES index. Point `config.impressionData.yml` to new
    index.

7.  Repeat the following steps for files created in step 4

    1.  Split it into multiple files.

    2.  Run redis_setter.py in parallel for each file.

    3.  ~~Run tmpScripts/check_redis_ie.py for a sanity check of Redis
        data and also to get unique client_ids in a file.~~

    4.  Run the monthly back-population job.
