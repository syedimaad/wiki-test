**Feature Store Requirements:**

1.  It has to be fast - 1ms per request.

2.  Store MAU scale user features. \-- 90M users

3.  Could it replace our parquet files + redis as a single source of
    truth?

4.  Consistent across any replications

5.  Ease of update on new features + scale of new features

**Problems with redis**

1.  Memory requirements in redis - already at \~80% of the cluster.

    1.  How do we scale to new features getting added?

    2.  How do we scale to users increasing?

2.  Ease of updates

    1.  It is very difficult currently to update the features and use
        them in both training and runtime simultaneously.

3.  Two sources of truth

4.  The network call. - out of the 1ms - more than 50% time is spent on
    network.

**Current Pipeline**

Feature_extraction

- Creates and keeps updated a parquet file with MAU users all features

- Updates the redis key for each users in MAU with latest features.

AdLearning

- consumes the MAU features from the parquet to train models

RustRealTimePredictAPI

- consumes the redis key for each user and predicts from different
  models.

**Explored till now**

- LMDB \-- memory mapped file key value store.\
  - sub ms query time

- Feast --

  - pros

    - [https://docs.feast.dev/how-to-guides/running-feast-in-production#4.3.-java-based-feature-server-deployed-on-kubernetes](https://docs.feast.dev/how-to-guides/running-feast-in-production#4.3.-java-based-feature-server-deployed-on-kubernetes){card-appearance="inline"}

    - can be linked with local, aws and gcp easily

    - uses redis+SQL(DB)

    - works in python

  - cons

    - does not support ETL/ELT

    - Data Warehousing

    - doesn't support features related tasks like engineering or
      validation

  - Good Tutorial to understand:
    [https://colab.research.google.com/github/feast-dev/feast-fraud-tutorial/blob/master/notebooks/Fraud_Detection_Tutorial.ipynb#scrollTo=Sk0fdKESD3j](https://colab.research.google.com/github/feast-dev/feast-fraud-tutorial/blob/master/notebooks/Fraud_Detection_Tutorial.ipynb#scrollTo=Sk0fdKESD3j-)

- Hopswork --
  [https://www.hopsworks.ai/feature-store](https://www.hopsworks.ai/feature-store){card-appearance="inline"}

  - pros

    - Supports Feature Engineering and Validation

    - Offline feature store uses HopsFS

    - Available on GCP, AWS, Kubernetes

    - works on python,scala and java

  - cons

    - not sure if this provides better latency than the current existing
      model

- Tecton -
  [https://docs.tecton.ai/v2/](https://docs.tecton.ai/v2/){card-appearance="inline"}

  - pros

    - Supports AWS

    - Uses Python,SQL and Spark mostly

  - cons

    - average response time is 30ms

    - not available on GCP

    - only available on python

**POC**

- setup a similar working pipeline for one project

- benchmark test with the currently existing feature store on P99
  response time

- test new feature addition and updates ease on this new pipeline

**Steps to take for POC**

- ~~Understand current feature preprocessing and data flow process into
  Redis and Parquets~~

- Creation of a Gitlab repository and a test server to work on

- ~~Setup FEAST on a GCP server (?access requirement)~~

  - Using CentOS and hosting FEAST over docker (issues remain)

- ~~Get access to the raw data and create a similar pipeline using FEAST
  (?getting familiar with how to query data)~~

- ~~Create a FEAST Server HTTP which will serve data to the RUST
  inference engine~~

- Create a FEAST Server that is non python dependent

- Use P99 response time as a metric to benchmark the existing and new
  pipeline for the RUST Engine

- Try out adding new features to the feature store
