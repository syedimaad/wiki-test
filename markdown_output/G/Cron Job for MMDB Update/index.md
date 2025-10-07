Code Link : [MMDB Update
Go](https://gitlab.dailyhunt.in/nh-ads-platform/dh_global_location_api/-/blob/master/schedulers/jobs/mmdbUpdate.go)

## Objective

We have a cron task to refresh our MaxMind DB daily (also known as
MMDB), which is used for fetching Location based on IP.

## Steps

- download the unzip files of MMDB for City and ISP in the MMDB
  directory in a mounted location which is accessible to all VMs.

- fetch all the IPs of Location Service MIG

- hit an API in location service called `refresh/mmdb`

  - close the file being read of old MMDB file

  - replace the file of MMDB with new one

  - read the new file for MMDB

## Error Checks Currently Present

1.  Downloading of MMDB file

2.  Unzipping Error of MMDB FIle

3.  Regarding reading or closing of any file

If all of this happens successfully we send a 200 response from the API

Any error which occurs is sent via Mailer.
