POC B:

Insert data from requests, impressions and other kafka topics into the
same Hudi logical location - test for time, CPU and RAM taken to insert.

Time, CPU and RAM taken and to join requests and impressions over
varying time frames. (5 min, 1 hour, 1 day) - first time and subsequent.

Store all events in their separate parquets, have a table definition of
a merge table (merge on read) table, and measure all the above
parameters for querying that table.

- Read Hudi table data from sparkSQL tried to sync with hive.

- Functionality testing of schema evolution(add columns) in hudi table.

- Functionality testing of pushing requests,impressions and clicks data
  to one hudi location and create one bigtable and query the data in
  sparkSQL.
