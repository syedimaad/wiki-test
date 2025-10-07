**Purpose:**

Serve campaigns by RPS (instead of total number of required requests)

**New tech used:**

- ETCD

- Prometheus

- GCS

**Functioning:**

1.  Changed computation of required requests to RPS

2.  Keys to be set to ETCD:

    1.  active_campaigns - Comma separated list of delivering campaigns

    2.  rps\_\<campaign_id\> - Float type value of RPS

Following processes set the above ETCD keys:

- MPE 5-minutely process - Function which previously updated campaigns\'
  required requests to Redis has been changed to write RPS to ETCD.

- Poll Prometheus to compute the current delivery of campaigns, compare
  to the latest required requests number (computed by MPE) and update
  ETCD's active_campaigns and respective campaign rps\_ keys
  accordingly. \### To be checked - In case of computing new rps based
  on the delivery, should the hard stop time be 300 seconds or should be
  (current time - mpe finish time)?

- Alert rules pushed to GCS, create trigger function in GCS to send POST
  request to Flask server, Flask server will update campaign's rps keys
  to ETCD.

**Misc:**

- Aggressive cacher stopped, instead we trigger cache primer update.

- For test campaigns, RPS is set to default value (1.0) (Test campaigns
  definition is in the function - is_valid_for_aggresive_cacher )
