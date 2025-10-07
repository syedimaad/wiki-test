VM address: [Location
Learning](https://console.cloud.google.com/compute/instancesDetail/zones/asia-south1-a/instances/dh-gcp-ads-global-location-learning?project=dh-gcp-ads-prod)

Currently, this VM is running a supervisor process with the current
config.

bash\[dh-ads@dh-gcp-ads-global-location-learning \~\]\$ cat
supervisord/supervisord.d/locationCron.ini
\[program:dh_global_location_cron\] environment=ENV=prod,MODE=learning
directory = /mnt/vol1/dh-ads/dh_global_location_api command =
/mnt/vol1/dh-ads/dh_global_location_api/dh_global_location_api user =
dh-ads autostart = true autorestart = true stopasgroup = true \#
stopsignal = QUIT redirect_stderr = true stdout_logfile =
/mnt/vol1/dh-ads/logs/access.log stderr_logfile =
/mnt/vol1/dh-ads/logs/error.log logfile_maxbytes = 10MB

This runs the location service API in learning mode which runs the
`scheduler()` function in `main.go`

We start the learning to train IP model here.

- Start a Kafka Processor which creates a Kafka Queue and fetches
  locations to be trained and pushes them to Redis

  - Data is pushed into Kafka by AdEngine Team

- Start consuming data from Kafka having request topics
  `"reqmessages", "josh_req_messages"` which is then processed and read

- Data is selected on the following conditions

  - if request timestamp is not older than 3 \* time interval set (1800
    in current prod config file)

  - IP should be a valid ipv4

- Currently IP based training happen on DH and JOSH is used for accuracy
  check if accuracy check is on in config

- if location source is IP, we start the training

  - Fetch a valid IP and divide the last part of IP by 4.
