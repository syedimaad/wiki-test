Staging VM Location:
<https://console.cloud.google.com/compute/instancesDetail/zones/asia-south1-a/instances/dh-gcp-ads-locationservice-pelias-stage-n1?project=dh-gcp-ads-stage>

## Updating entire pelias

1.  Export all the environment variables listed in
    `~/docker/projects/planet/.env`

2.  Check if pelias docker is running by using `docker ps`

3.  Run `~/docker/projects/pelias compose down` to stop the running
    pelias services

4.  Read all the commands listed in `region_wish.sh` file located inside
    `~/docker` folder (referenced from:
    [https://github.com/pelias/docker?tab=readme-ov-file#quickstart-build-script](https://github.com/pelias/docker?tab=readme-ov-file#quickstart-build-script){card-appearance="inline"}

5.  Make sure to run them in order and run `pelias download wof` to
    redownload WOF db ***only***

6.  Once Pelias is up again, test the API with a curl command

## Updating and running only Pelias with Whosonfirst configured

1.  After linking `DATA_DIR` to relevant path run the following script
    to update Pelias only for WOF\

    bashpelias compose pull pelias elastic start pelias elastic wait
    pelias elastic create pelias download wof pelias prepare placeholder
    pelias import wof pelias compose up

SAMPLE API command

bashcurl \--location
\'http://dh-location-pelias.dailyhunt.in/v1/reverse?size=20&point.lon=77.3185554&point.lat=28.5673456&sources=osm\'

Running `pelias prepare all` command can take upto 24 hours

# List of Errors which can occur

## Resource Already Exists

> \[resource_already_exists_exception\] index
> \[pelias/IfF1EXITRYuRu9M9uifmTA\] already exists, with {
> index_uuid=\"IfF1EXITRYuRu9M9uifmTA\" & index=\"pelias\" }

## Fix:

- Delete `nodes/0` in `elasticsearch` folder

- Rerun `pelias elastic start`

## Access Denied Exception

> ElasticsearchException\[failed to bind service\]; nested:
> AccessDeniedException\[/usr/share/elasticsearch/data/nodes\];

## Fix:

- check `SUDO_USER` & `SUDO_UID` by running `pelias system env`

- if user is not `dh-ads` run `UNSET SUDO_USER` and `SUDO_UID` and
  verify if it's correct or not

# References:

- <https://medium.com/@mohammedayub44/yet-another-awesome-geo-coder-open-sourced-spatial-search-c295970a8226>

- 
