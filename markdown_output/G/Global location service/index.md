  --------------------- -------------------
  **Document Status**   IN-PROGRESSYellow
  **Product Owners**    
  --------------------- -------------------

##  Executive Summary

Global Location service is purely to get a location(city/state/country)
based on set of input params like lat/long, cell_id, ip. Along with this
it supports getting top cities of an user or getting details of a
location based on his locationID

##  Objective

We planned this service to be single source of truth for user location
detection across teams & apps.

##  Assumptions

We have made certain assumptions while designing the architecture and
finalising the data source.

1.  [whosonfirst](https://geocode.earth/data/whosonfirst/combined/) is
    the best data set for us to use for GPS(lat/long) conversion to a
    location entity.

2.  [maxmind](https://www.maxmind.com/en/geoip-demo) DB is one of our
    data source to check location for an IP.

3.  We have our own ip learning module which seems to be better than
    mmdb.

## Monitoring

We are using graffana for monitoring of our system.

1.  [Global location
    service](http://saluber.dailyhunt.in/d/CgCw8jKbx4/global-location-service-application?orgId=22)

2.  [Location
    learning](http://saluber.dailyhunt.in/d/CgCw8jKbx6/location_learning?orgId=22)

## GCP VM details and monitoring

1.  [Global location
    service](https://console.cloud.google.com/compute/instanceGroups/details/asia-south1/dh-gcp-ads-global-location-service-mig?project=dh-gcp-ads-prod)

2.  [Pelias1](https://console.cloud.google.com/compute/instanceGroups/details/asia-south1-a/dh-gcp-ads-pelias-asia-south1-a-umig?project=dh-gcp-ads-prod).
    [Pelias2](https://console.cloud.google.com/compute/instanceGroups/details/asia-south1-b/dh-gcp-ads-pelias-asia-south1-b-umig?project=dh-gcp-ads-prod)

3.  [Location
    learning](https://console.cloud.google.com/compute/instancesDetail/zones/asia-south1-a/instances/dh-gcp-ads-global-location-learning?project=dh-gcp-ads-prod)

4.  [Location
    DB](https://console.cloud.google.com/compute/instancesDetail/zones/asia-south1-c/instances/dh-gcp-ads-locationdb-mysql-slave-n1?project=dh-gcp-ads-prod)

Environments and resource details

  ----- --------------------------------------------------------------------------------- ---------------------------------------------------------------------------------------------------------------------------------------------------- ---------------------------------------------------------------------------
        **stage**                                                                         **qa**                                                                                                                                               **prod**
  url   [stage-locationservice.dailyhunt.in](http://stage-locationservice.dailyhunt.in)   [qa-locationservice.dailyhunt.in](http://qa-locationservice.dailyhunt.in)                                                                            [locationservice.dailyhunt.in](http://stage-locationservice.dailyhunt.in)
  gcp                                                                                     <https://console.cloud.google.com/compute/instanceGroups/details/asia-south1-a/dh-gcp-ads-locationservice-asia-south1-a-mig?project=dh-gcp-ads-qa>   
  ----- --------------------------------------------------------------------------------- ---------------------------------------------------------------------------------------------------------------------------------------------------- ---------------------------------------------------------------------------
