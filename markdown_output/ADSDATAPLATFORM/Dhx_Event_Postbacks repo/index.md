- All dhx_events_postback repo consumers are running from spark
  standalone 3.1.3

- There are 6 consumers - 3 internal, 3 external (Difference lies in
  client id value)

- Consumers write to the Kudu tables - dhx_event_postbacks and
  dhx_event_postbacks_external

- Scripts path to start consumers -
  /mnt/vol1/dh-ads/kuduhive/scripts/processors_check.sh on edge-n1

- Script to compare Kudu and MySQL counts run once a day

  - <http://ads-data-airflow.dailyhunt.in/tree?dag_id=dh-josh-postbacks-monitoring>

  - Email subject - `[Alert] dhx_event_postbacks - Mismatch in counts`

  - Path to the script -
    `/mnt/vol1/dh-ads/kuduhive/scripts/postbacks_report.sh`

- Script to add partitions -
  `/mnt/vol1/dh-ads/kuduhive/scripts/add_postbacks_partitions.sh`

- Airflow dags -
  <http://ads-data-airflow.dailyhunt.in/tree?dag_id=dh-josh-postbacks-monitoring>

  - <http://ads-data-airflow.dailyhunt.in/tree?dag_id=dh-josh-add-postbacks-partitions>

Please check for events with event_name = 'dh_install' (Getting
populated from a consumer in Nrt repo)
