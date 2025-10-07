------------------------------------------------------------------------

Saluber:
<https://saluber.dailyhunt.in/d/hb7fSEsqa0Zzasdasd/ads-host-overview?orgId=3&var-hostname=dh-gcp-ads-scylladb-prod-n1.dailyhunt.in&var-hostname=dh-gcp-ads-scylladb-prod-n2.dailyhunt.in&var-hostname=dh-gcp-ads-scylladb-prod-n3.dailyhunt.in&var-hostname=dh-gcp-ads-scylladb-prod-n4.dailyhunt.in&var-hostip=All&var-ipforhostdown=All>

schema :
<https://docs.google.com/spreadsheets/d/1zux-SZLyMs4hFfqWj_BjO6PPHHKoLwQZ97arNyPM4S4/edit#gid=423041631>

create Table Cmd:

str=\"\"\"CREATE TABLE ads_data.userprofile (aduid text PRIMARY KEY,
dh_client_id text, josh_client_id text, pv_client_id text,
dh_first_install_date timestamp, josh_first_install_date timestamp,
dh_acquisition_campaign text, josh_acquisition_campaign text,
dh_master_source text, josh_master_source text, dh_app_version text,
josh_app_version text, pv_app_version text, dh_user_languages
set\<text\>, josh_user_languages set\<text\>, pv_user_languages
set\<text\>, dh_user_id text, conn_affinity
list\<frozen\<week_affinity\>\>, dh_user_type text, sunsign text,
age_range text, age_range_source text, age_range_v2 text, age int,
age_last_updated_time timestamp, age_info blob, dob date, gender text,
gender_info blob, gender_last_updated_time timestamp, gender_source
text, dh_topic_affinity list\<frozen\<week_affinity\>\>,
dh_lang_affinity list\<frozen\<week_affinity\>\>, josh_lang_affinity
list\<frozen\<week_affinity\>\>, pv_lang_affinity
list\<frozen\<week_affinity\>\>, dh_social_login_data social_login_data,
dfp_location dfp_location, battery_capacity battery_capacity, data_usage
data_usage, os_info os_info, device_memory_info device_memory, udid
text, android_id text, device device, app_affinity
list\<frozen\<affinity\>\>, media_info media_info,
dh_num_days_active_in_month int, josh_num_days_active_in_month int ,
pv_num_days_active_in_month int , location location,
temp_audience_segments map\<text, int\>, dynamic_audience_segments
map\<text, timestamp\>, app_categories set\<text\>, app_ids set\<int\>,
dh_genres set\<text\>, audience_segment set\<int\>, top_cities
frozen\<top_cities\>, last_updated_aduid timestamp, gaid text, idfa
text, isp text, analytics_location analytics_location,
location_event_captured_on timestamp, last_updated timestamp,
dh_last_seen timestamp, josh_last_seen timestamp, pv_last_seen
timestamp, imas_t map\<text, text\>, dh_astro_data text,
location_created_by text) WITH compression = { \'sstable_compression\':
\'org.apache.cassandra.io.compress.ZstdCompressor\' };\"\"\"
session.execute(str)

**Fields That are yet to be updated:**

`josh_lang_affinity`, `pv_lang_affinity`,
`josh_num_days_active_in_month, pv_num_days_active_in_month`, `isp`

**Commented**

updateUserProfile - Running

adClickersAudienceSegments - Running

audienceSegments(dynamic_as, as) - Running

dynamicAudienceSegments(tas) - Running

appsConsumer - Running

locationConsumer(Shivam) - Running

conn_affinity udt example \[ { \"week\": 1, \"affinity\": { \"4g\": 10,
\"w\": 4 } }, { \"week\": 2, \"affinity\": {} } \]weekaffinity = {
\"week_num\": int, \"affinity\": map\<text, int\> }
list\<week_affinity\> topic_affinity \[ { \"week\": 20, \"affinity\": {
\"world\": 10, \"sports\": 5 } } \]

------------------------------------------------------------------------

DATA TYPES:

1\. analytics_location:

str=\"\"\"CREATE TYPE IF NOT EXISTS analytics_location ( city text,
state text, country text, last_updated timestamp );\"\"\"
session.execute(str)

2.  top_cities:

str=\"\"\"CREATE TYPE IF NOT EXISTS top_cities_location ( country text,
state text, city text, country_id text, state_id text, city_id text,
score double, source map\<text, double\> );\"\"\" session.execute(str)
str=\"\"\"CREATE TYPE IF NOT EXISTS top_cities ( top_cities_list
list\<frozen\<top_cities_location\>\>, last_updated timestamp );\"\"\"
session.execute(str)

3.  location:

str=\"\"\"CREATE TYPE IF NOT EXISTS location ( city text, state text,
country text, constituency text, source text, cityid text, stateid text,
countryid text, countrycode text, isocountrycode text, constituencyid
text, latitude double, longitude double, pincode int, confidence float,
ip text, extended_city extended_city, last_updated_location timestamp
);\"\"\" session.execute(str)

4.  extended_city:

str=\"\"\"CREATE TYPE IF NOT EXISTS extended_city ( countrycode text,
countryid text, stateid text, state text, cityid text, city text,
centroid_distance float, boundary_distance float );\"\"\"
session.execute(str)

5.  media_info:

str=\"\"\"CREATE TYPE IF NOT EXISTS media_info ( audio_files_count
bigint, camera_images_count bigint, total_images_count bigint,
video_files_count bigint );\"\"\" session.execute(str)

5.  affinity:

str=\"\"\"CREATE TYPE IF NOT EXISTS affinity ( name text, val int
);\"\"\" session.execute(str)

6.  device:

str=\"\"\"CREATE TYPE IF NOT EXISTS device ( model text, brand text,
platform text, resolution text, os_version text, app_data_model text,
app_data_brand text, gaid_opt_out_status boolean, pricerange text
);\"\"\" session.execute(str)

7.  device_memory:

str=\"\"\"CREATE TYPE IF NOT EXISTS device_memory (
total_external_memory_size bigint, total_internal_memory_size bigint,
available_external_memory_size bigint, total_ram_size bigint,
available_internal_memory_size bigint );\"\"\" session.execute(str)

8.  os_info:

str=\"\"\"CREATE TYPE IF NOT EXISTS os_info ( last_os_build_time bigint,
last_boot_time bigint );\"\"\" session.execute(str)

9.  data_usage:

str=\"\"\"CREATE TYPE IF NOT EXISTS data_usage ( total_wifi_usage
bigint, total_mobile_usage bigint, dh_data_usage bigint, josh_data_usage
bigint, pv_data_usage bigint );\"\"\" session.execute(str)

10. battery_capacity:

str=\"\"\"CREATE TYPE IF NOT EXISTS battery_capacity ( battery_health
bigint, battery_temp bigint, battery_tech text, battery_capacity bigint
);\"\"\" session.execute(str)

11. dfp_location:

str=\"\"\"CREATE TYPE IF NOT EXISTS dfp_location ( city text, state
text, country text, pincode bigint );\"\"\" session.execute(str)

12. social_login_data:

str=\"\"\"CREATE TYPE IF NOT EXISTS social_login_data ( user_name text,
user_action text, last_updated timestamp, gender text, user_auth_type
text, user_id text, client_id text, date_of_birth timestamp );\"\"\"
session.execute(str)

13. week_affinity:

str=\"\"\"CREATE TYPE IF NOT EXISTS week_affinity ( week int,
affinity_score map\<text, int\> );\"\"\"
session.execute(str)str=\"\"\"ALTER TYPE location ADD extended_city
extended_city;\"\"\" session.execute(str)

#### VMs:

STAGE: `dh-gcp-ads-scylladb-stage-n1.dailyhunt.in`

QA: `dh-gcp-ads-scylladb-qa-n1.dailyhunt.in`

PROD:

`dh-gcp-ads-scylladb-prod-n1.dailyhunt.in,`\
`dh-gcp-ads-scylladb-prod-n2.dailyhunt.in,`\
`dh-gcp-ads-scylladb-prod-n3.dailyhunt.in,`\
`dh-gcp-ads-scylladb-prod-n4.dailyhunt.in`

------------------------------------------------------------------------

- Keyspace: `ads_data`

- Table: `userprofile`

- prod_test_table: `userprofiletest`

- user1: `data_userprofile_updater`

- password1: `xelAvrtXHOlUfhi`

- user2: `adengine_user`

- password2: `hWfmHHRmsYHIPb4`

- [create perf user]{style="color: rgb(255,153,31);"}

- cqlsh -u data_userprofile_updater 10.50.27.212

------------------------------------------------------------------------

ADUID UPDATE FLOW CHART:\
[https://drive.google.com/file/d/1GBEyBmI4SRXA20u-W1DR2gVP0ZhbKN8W/view?usp=sharing](https://drive.google.com/file/d/1GBEyBmI4SRXA20u-W1DR2gVP0ZhbKN8W/view?usp=sharing){card-appearance="inline"}

~~DATA Jobs To Move:~~

1.  ~~aduidUpdateProcess(universal-Profile)~~

    1.  ~~Effort - 5~~

2.  ~~insert_num_times.py (DHUserProfile)~~

    1.  ~~Move to UnifiedUserProfile codebase~~

    2.  ~~Effort - 1~~

3.  ~~insertInstallSource.py (unifiedProfile)~~

    1.  ~~Effort - 1~~

4.  ~~updateUserProfile.py (unifiedProfile)~~

    1.  ~~Effort - 1~~

5.  ~~astroProcessor.py (DHUserProfile)~~

    1.  ~~Move to UnifiedUserProfile codebase~~

    2.  ~~Effort - 1~~

6.  ~~updateTopicReadership.py (DHUserProfile)~~

    1.  ~~Move to UnifiedUserProfile codebase~~

    2.  ~~Effort - 1~~

7.  ~~social_login_processor_kafka.py (DHUserProfile)~~

    1.  ~~Move to UnifiedUserProfile codebase~~

    2.  ~~Effort - 1~~

8.  ~~HourlyBidsRequestProcessor.py (S2S-analytics)~~

    1.  ~~Move to UnifiedUserProfile codebase~~

    2.  ~~Effort - 1~~

9.  ~~adClickersAudienceSegments.py (unifiedProfile)~~

    1.  ~~Effort - 1~~

10. ~~audienceSegmentProcessor.py(DHUserProfile)~~

    1.  ~~Move to UnifiedUserProfile codebase~~

    2.  ~~Effort - 1~~

11. ~~appsQueueConsumer (unifiedProfile)~~

    1.  ~~Club with Iceberg Migration for appsprofile changes.~~

    2.  ~~Effort - 5~~

12. ~~Josh & PV specific processes~~

13. ~~Location consumer changes to push to scylla~~

14. ~~Top cities process changes to push to scylla~~

15. ~~Perf team changes to push to scylla~~

16. ~~Confirm if josh onboarding process is needed~~

17. ~~Migrate MAU data from Mongo & Redis to Scylla~~

18. ~~Validate and ensure data correctness~~

19. ~~Phase 2 - Move all batch jobs to GKE~~

------------------------------------------------------------------------

# ALL UPDATE JOBS:

------------------------------------------------------------------------

- Repo: location-profile

- File: **AdUidsMappingStreamingKudu**.**scala**

- fields:

  - ALl Fields

- VM: <http://10.50.0.27:8080/>

- Currently it is running separately need to merge

- [change temp_audience_segment logic for
  merge]{style="color: rgb(191,38,0);"}

------------------------------------------------------------------------

- Repo: unifiedProfile

- File: **insert_num_times**.**py** (currently running for **DH** Only)

- fields:

  - aduid dh_client_id/josh_client_id/pv_client_id
    dh_num_days_active_in_month/josh_num_days_active_in_month/pv_num_days_active_in_month
    last_updated

- VM: dh-gcp-ads-dataproc-n1.dailyhunt.in

- DAG:
  <http://ads-data-airflow.dailyhunt.in/code?dag_id=active-num-days-processor>

------------------------------------------------------------------------

- Repo: unifiedProfile

- File: **insertInstallSource**.**py** (currently running for **DH** and
  **JOSH**)

- fields:

  - aduid dh_client_id/josh_client_id/pv_client_id
    dh_first_install_date/josh_first_install_date
    dh_acquisition_campaign/josh_acquisition_campaign
    dh_master_source/josh_master_source last_updated

- VM: dh-gcp-ads-dataproc-n5.dailyhunt.in

- DAG:
  <http://ads-data-airflow.dailyhunt.in/code?dag_id=insert-install-source>

------------------------------------------------------------------------

- Repo: unifiedProfile

- File: **updateUserProfile**.**py** (currently running for **DH**,
  **JOSH and PV**)

- fields:

  - aduid dh_client_id/josh_client_id/pv_client_id device conn_affinity
    dh_app_version/josh_app_version/pv_app_version
    dh_user_languages/josh_user_languages/pv_user_languages dh_user_id
    (for DH Only) dh_user_type (for DH Only) last_updated

- VM: dh-gcp-ads-dataproc-n5.dailyhunt.in

- DAG:
  <http://ads-data-airflow.dailyhunt.in/tree?dag_id=user-profile-update>

------------------------------------------------------------------------

- Repo: unifiedProfile

- File: **astroProcessor.py** (currently running for **DH**)

- fields:

  - aduid dh_client_id/josh_client_id/pv_client_id gender gender_source
    age age_range age_range_v2 age_range_source sunsign
    age_last_updated_time gender_last_updated_time last_updated

- VM: dh-gcp-ads-dataproc-n1.dailyhunt.in

- CRONS:

  - \*/2 \* \* \* \* docker run \--rm \--name=\"astro\"  -v
    /mnt/vol2/unifiedprofile:/app unifiedprofile:latest python3
    /app/userProfileProcessing/astroProcessor.py DH\>\>
    logs/cronlogAstro 2\>&1

  - \*/5 \* \* \* \* sh
    /mnt/vol2/unifiedprofile/scripts/kill-if-not-enough-processes-running.sh
    \"userProfileProcessing/astroProcessor.py\" 2
    \"news_userinfo_events\" \"ads-profile-events-consumer\" 10000
    \"astro\"\>\> logs/cronlogAstroStop 2\>&1

------------------------------------------------------------------------

- Repo: unifiedProfile

- File: **updateTopicReadership**.**py** (currently running for **DH**)

- fields:

  - aduid dh_client_id/josh_client_id/pv_client_id dh_topic_affinity
    dh_lang_affinity dh_genres last_updated

- VM: dh-gcp-ads-dataproc-n1.dailyhunt.in

- DAGS:

  - <http://ads-data-airflow.dailyhunt.in/tree?dag_id=topic-readership-storypage-view>

  - <http://ads-data-airflow.dailyhunt.in/tree?dag_id=topic-readership>

------------------------------------------------------------------------

- Repo: unifiedProfile

- File: **socialLoginProcessor**.**py** (currently running for **DH**)

- fields:

  - aduid dh_client_id/josh_client_id/pv_client_id gender gender_source
    dob age age_range age_range_v2 age_range_source dh_social_login_data
    last_updated

- VM: dh-gcp-ads-dataproc-n1.dailyhunt.in

- CRONS:

  - \* \* \* \* docker run \--rm \--name=\"social_login\"  -v
    /mnt/vol2/unifiedprofile:/app unifiedprofile:latest python3
    /app/userProfileProcessing/socialLoginProcessor.py DH\>\>
    logs/cronlogSocialLogin 2\>&1

  - \* \* \* \* sh
    /mnt/vol2/unifiedprofile/scripts/kill-if-not-enough-processes-running.sh
    \"userProfileProcessing/socialLoginProcessor.py\" 4
    \"user_profile_update_event_prod\"
    \"user-profile-login-events-consumer\" 10000 \"social_login\"\>\>
    logs/cronlogSocialLoginStop 2\>&1

- `gender_last_updated_time`**[ can be updated
  (TODO)]{style="color: rgb(191,38,0);"}**

------------------------------------------------------------------------

- Repo: s2s-analytics

- File: **hourlyBidsRequestsProcessor**.**py**

- fields:

  - aduid dh_client_id/josh_client_id/pv_client_id dfp_location
    last_updated

- VM: dh-gcp-ads-dataproc-n4.dailyhunt.in

- CRON:

  - 50 \* \* \* \* cd /mnt/vol1/dh-ads/s2s-analytics/dfp/; sh
    latestLogProcessExecutor.sh \>\>
    /mnt/vol1/dh-ads/s2s-analytics/dfp/logs/logslatestProcessExecutionHourly\_\`date
    +\\%Y\\%m\\%d\\%H\`.log 2\>&1

------------------------------------------------------------------------

- Repo: unifiedProfile

- File: **adClickersAudienceSegments**.**py**

- fields:

  - aduid dh_client_id/josh_client_id/pv_client_id
    dynamic_audience_segments last_updated

- VM: dh-gcp-ads-dataproc-n5.dailyhunt.in

- DAG:
  <http://ads-data-airflow.dailyhunt.in/tree?dag_id=clicker-audience-segment-processor>

------------------------------------------------------------------------

- Repo: unifiedProfile

- File: **audienceSegmentProcessor**.**py** (currently running for
  **DH**, **JOSH and PV**)

- fields:

  - aduid dh_client_id/josh_client_id/pv_client_id audience_segment
    dynamic_audience_segments last_updated

- VM: dh-gcp-ads-dataproc-n5.dailyhunt.in

- DAG:

  - DH:
    <http://ads-data-airflow.dailyhunt.in/home?search=dh-audience-segment-processor>

  - JOSH:
    <http://ads-data-airflow.dailyhunt.in/tree?dag_id=josh-audience-segment-processor-new>

  - PV:
    <http://ads-data-airflow.dailyhunt.in/tree?dag_id=pv-audience-segment-processor>

Please, debug Audience Segment Process and fix

------------------------------------------------------------------------

- Repo: location-profile

- File: **universal_profile**.**py**

- fields:

  - aduid top_cities last_updated

- VM: dh-gcp-ads-data-edge-n1.dailyhunt.in

- DAG:
  <http://ads-data-airflow.dailyhunt.in/tree?dag_id=universal-profile-location>

------------------------------------------------------------------------

- Repo: audience_segments_processing

- Files: **as_file_deletion.py, as_file_processing.py,
  dynamic_as_deletion.py, dynamic_as_updation.py**

- fields:

  - aduid temp_audience_segments last_updated

- VM: dh-gcp-ads-dataproc-n3.dailyhunt.in

- Running from Supervisor

------------------------------------------------------------------------

- Repo: unifiedProfile

- File: **appsQueueConsumer.py**

- fields:

  - aduid app_ids app_categories device app_affinity udid android_id
    battery_capacity data_usage os_info media_info device_memory_info
    last_updated

- VM: dh-gcp-ads-dataproc-n5.dailyhunt.in

- DAG:

  - \* \* \* \* docker run \--rm \--name=\"unified_apps\"  -v
    /mnt/vol1/dh-ads/unifiedprofile:/app unifiedprofile:latest
    bin/run.sh appsProcessing/appsQueueConsumer.py \>\>
    logs/unifiedapps_stdout 2\>&1

------------------------------------------------------------------------

- Repo: InMarketAudienceSegments

- File: **imas_update_processor.py**

- fields:

  - aduid audience_segment imas_t last_updated

- VM: dh-gcp-ads-dataproc-n4.dailyhunt.in

- DAG:

  - 00 7 \* \* \* cd /mnt/vol1/dh-ads/inmarketaudiencesegment &&
    bin/run_py.sh IMAS/imas_update_processor.py \>\>
    /mnt/vol1/dh-ads/inmarketaudiencesegment/logs/cron_imas_daily.log
    2\>&1

------------------------------------------------------------------------

[https://drive.google.com/file/d/1WK6xtXvx8qn6Kf9UqAhEGrKFx4RupeTg/view?usp=sharing](https://drive.google.com/file/d/1WK6xtXvx8qn6Kf9UqAhEGrKFx4RupeTg/view?usp=sharing){card-appearance="inline"}

[https://drive.google.com/file/d/1cV55o_tPz7gdZxCYllnELmwlwM56zQsF/view?usp=sharing](https://drive.google.com/file/d/1cV55o_tPz7gdZxCYllnELmwlwM56zQsF/view?usp=sharing){card-appearance="inline"}

[https://drive.google.com/file/d/1GBEyBmI4SRXA20u-W1DR2gVP0ZhbKN8W/view?usp=sharing](https://drive.google.com/file/d/1GBEyBmI4SRXA20u-W1DR2gVP0ZhbKN8W/view?usp=sharing){card-appearance="inline"}

[https://drive.google.com/file/d/1cV55o_tPz7gdZxCYllnELmwlwM56zQsF/view?usp=sharing](https://drive.google.com/file/d/1cV55o_tPz7gdZxCYllnELmwlwM56zQsF/view?usp=sharing){card-appearance="inline"}

------------------------------------------------------------------------

Backfill and data check path

VM: dataproc-n1

path: /mnt/vol2/dishant/unifiedprofile

command:\
docker run \--rm \--name=\"DH_backfill\" -v
/mnt/vol2/dishant/unifiedprofile:/app unifiedprofile:latest bin/run.sh
backfill/scylla_backfill.py DH &

DataCheck\
docker run \--rm \--name=\"DH_data_check\" -v
/mnt/vol2/dishant/unifiedprofile:/app unifiedprofile:latest bin/run.sh
backfill/redis_data_check.py DH &\
