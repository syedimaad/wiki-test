### Metadata Process flow

1.  Read Metadata (Batch of messages of around \~100 to \~6000) from
    Kinesis Stream using the Pyspark streaming module.

    1.  Create / Update Events of an Entity are pushed to Kinesis from
        the API or other modules

2.  Append the metadata to the Temporary Delta table stored in the AWS
    S3 location. Here we will not verify for existence of the entity in
    the delta table. Just appending whatever is consumed from Kinesis

3.  The delta table data in the temporary S3 location is flushed/merged
    with the Master Delta table frequently among anyone below

    1.  When the record size reaches a value of **N** in the temporary
        S3 Location**.**

    2.  In the frequency of every **T** (3) Hours.

4.  Before merging to the Master table, the data is processed to merge
    the multiple update events for an entity.

5.  Repeats from the Step 1

### Data Compaction and Manifest Generation

At the end of each data merge to the Master Delta table,

Compaction - Merging multiple delta files in S3

Manifest Generation - Manifest generation for Athena to read the current
version of Parquet files

Vacuum - Deleting the older Parquet files

### Need of Temporary Delta Table

1.  Each data merge to the Master Delta table for a batch of messages by
    PySpark does

    1.  Downloading the entire data (parquet files) of a partition from
        S3.

    2.  Merge the updated data locally and upload it back to S3.

2.  If the above process is done for each batch message consumed from
    Kinesis, the data read & write to S3 will increase which increases
    the data transfer cost as well.

### Athena Tables

1.  At Athena External tables were created with the location pointing to
    the S3 location of the delta table.

2.  Frequent run of `MSCK REPAIR TABLE {meta_data_table}` needed at
    Athena to get the new Partitions added to Delta table.

### Info

1.  AWS S3 Location of metadata is s3://josh-meta/{**entity**}/

Entities with metadata available in S3 and corresponding Athena as below

  ------------ --------------------------- ---------------------
  **entity**   **S3 Location**             **Athena Table**
  video        s3://josh-meta/video/       josh_video_meta
  audio        s3://josh-meta/audio/       josh_audio_meta
  creator      s3://josh-meta/creator/     josh_creator_meta
  zone         s3://josh-meta/zone/        josh_zone_meta
  challenge    s3://josh-meta/challenge/   josh_challenge_meta
  ------------ --------------------------- ---------------------
