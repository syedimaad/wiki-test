1.  Git repo -
    <https://gitlab.dailyhunt.in/nh-ads-platform/adsweeklyprofileprocessing>

2.  VM - edge n1. /mnt/vol1/dh-ads/kuduhive/kubernetes

3.  Mongo collections - AdProfile_Week\_\<week_number\> under respective
    dbs - dhads, joshads, pvads

4.  Scripts to create Mongo collections - in Git repos - DHUserprofile,
    JoshUserProfile, PvUserProfile. #TODO - move to airflow

    1.  Run on dataproc-n1, josh-compute, dataproc-n1 respectively.

    2.  00 19 \* \* 6 bin/run.sh
        adsProfileProcessing/performWeeklyTasks.py 00 19 31 12 \*
        bin/run.sh adsProfileProcessing/performWeeklyTasksYearlyJob.py
        00 19 \* \* 6 bin/run.sh
        adsProfileProcessing/PublicVibePerformWeeklyTasks.py 00 19 31 12
        \* bin/run.sh
        adsProfileProcessing/PublicVibePerformWeeklyTasksYearlyJob.py 00
        19 \* \* 6 bin/run.sh
        adsProfileProcessing/JoshPerformWeeklyTasks.py 00 19 31 12 \*
        bin/run.sh
        adsProfileProcessing/JoshPerformWeeklyTasksYearlyJob.py

5.  Airflow dags links -

    1.  <http://ads-data-airflow.dailyhunt.in/tree?dag_id=dh-kudu-mongo-sinker>

    2.  <http://ads-data-airflow.dailyhunt.in/tree?dag_id=josh-kudu-mongo-sinker>

    3.  <http://ads-data-airflow.dailyhunt.in/tree?dag_id=publicvibe-kudu-mongo-sinker>

6.  #TODO- Increase time between retries in airflow

7.  Add new placements to the config if new placement is added/created.

8.  #TODO - Migrate to new schema

9.  In case mongo collection creation script fails, the hourly process
    will create non-sharded collection. Steps to be followed to handle
    this scenario:

    1.  Stop currently running job in spark

    2.  Disable airflow dag

    3.  Delete the weekly collection.

    4.  Rerun mongo collection creation script.
