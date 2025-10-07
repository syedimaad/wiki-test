## 

1.  Environment Setup

2.  Getting relevant Client IDs and its data

    1.  If client id list already passed, return it.

    2.  else merge client IDs from postback and leadpostback and return
        only unique values.

3.  Extract Features for the client IDs from the data

    1.  Establish a redis and mongo connection

    2.  Divide the data into batches

    3.  Iterating through each row of the data , Divide in batches and
        retrieve the entries from mongo

    4.  Update the redis

    5.  write the file to a parquet file on an output file.
