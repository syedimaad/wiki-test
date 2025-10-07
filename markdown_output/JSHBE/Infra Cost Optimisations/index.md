1.  Use new file structure for new content → Azure (Done)

2.  Original needs to be removed → 21st Feb → Susanta

    1.  views \< 1000 && created_date \>= Now - 30d → delete

    2.  views \< 1000 && created_date \>= Now - 7d → keep in glacier

    3.  Move Original Videos to S3 new path → Wednesday (23rd Feb)

    4.  Ongoing strategy to keep the original videos → Wednesday 1st
        March

3.  Create new schema for cold store combining ES + Dynamo (Only Meta) →
    Wednesday → Ashish

    1.  Schema for parquet

4.  Identify the warm content → Abhilash

5.  API to add the content from Cold store to warm

    1.  Populate from Parquet to ES for a content uuid/user uuid →
        Friday

6.  Follow ( Susanta Team )

    1.  Dynamo → Move the data from dynamo to parquet/ Start writing to
        Parquet → Swamy

    2.  Redis → Maintain following and follwed_by only for warm users →
        Ashish/Monika (28th Feb)

7.  Follow → Reduce gratification follows for old data (Sohanvir)

    1.  Reduce the number for new users

    2.  Increase count for old users and remove bots

8.  Remove redis for contact sync

    1.  Go with basic recommendations

9.  Dynamo Tables

    1.  josh_hive_moderation_data → Move the data from dynamo to
        parquet/ Start writing to Parquet

    2.  hive_content_logo_scores → Move the data from dynamo to parquet/
        Start writing to Parquet

10. Audio Meta table

    1.  Avoid Profile pic and handle updates cascading to content / meta
        table

    2.  Read from creator cache and put to share path, audio response
        and Feed Asset Response

11. Reactions Like Follow in Redis

    1.  Post Reactions in obelix POC
