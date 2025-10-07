- Whenever we will get the request for the Athena access from the any
  team we need to make a list of the Required filed and need to request
  to the reporter if unknown to you. There is an baseline policy which
  is providing the read only access to the josh_events db is
  **athena-josh_events-analytics-read .** you can always refer this
  policy for the readonly access just need to change the database,
  workgroup and S3 bucket based on the requirement.

- For the full access you need to Grant the full Glue Permission instead
  of get\* and list\* and change the SID name as per the access to make
  the policy user friendly for our team.

- Policy Name should be something like
  **athena-\<database_name\>-\<workgroup_name\>-accesstype .**

- Policy must have the below tags

  - name - **athena-josh_events-analytics-read**

  - database - josh_events

  - workgroup - analytics

  - accesstype - read

- **Required field for the Athena access.**

  1.  Access type - (Read/Write/Full)

  2.  DB name - (Database Name for which access required)

  3.  WorkGroup - (Workgroup name should be same as user team)

  4.  S3 Bucket - (Also need to provide the s3 bucket read access with
      get and put object)

  5.  Datasource - (By default it should be all)

Athena - Cross - Service Interaction
