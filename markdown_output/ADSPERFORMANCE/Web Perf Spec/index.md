Objective : Improve web user\'s advertising campaigns performance
metrics (CTR) 

Web User Types:

1.  Dailyhunt Website Users

2.  Dailyhunt Audience Network (DAN)

    1.  Generic Publisher

    2.  OneIndia

Data Available for each type of web user

1.  IP based location resolution

2.  Ad Placement ID

3.  Ad slot size

4.  User Agent (Browser and OS Info), Might also have phone brand
    information

5.  Publisher ID / IAB category

- Potential features for each type of web user:

1.  Location Based (City Tier and State)

2.  Placement Ids given publisher

3.  Ad slot size

4.  Publisher ID  / IAB category for generic / Cat model

5.  Time based features

\

DAN Publisher - OneIndia:

- Additional Information available 

1.  All oneindia articles data which are published on dailyhunt app

2.  We might also get user_session_id (which is valid for a year)

- Additional Potential features:

1.  Article language

2.  Article text / title embedding

3.  Article text / title word count 

4.  Article and campaign similarity score

5.  User profile based on user_session_id

    1.  Click History based features

    2.  nth_impression per session

DH WEB:

- Additional Potential features:

1.  user_connection  -\> 2g,3g,4g,w

2.  connection_speed -\> fast,good,average,slow

3.  User profile based on user_session_id (similar to one india)

4.  Device brand

Performance Analysis of web vs app traffic

[https://docs.google.com/spreadsheets/d/1FrPV0wQ-dNnYXC19CnshKDgq3xy8hM6ssGrotr_7fkg/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1FrPV0wQ-dNnYXC19CnshKDgq3xy8hM6ssGrotr_7fkg/edit?usp=sharing){card-appearance="inline"}

TODO:

1.  OneIndia PV traffic EDA.

2.  Getting clarity on User Session. (Who will we ask?)

3.  Event Data store - where are impressions/ clicks stored?

    1.  Schema

    2.  extraction scripts that we will need

4.  POCs for perf models

    1.  Article campaign match scoring.

5.  Design the perf interface with DAN

    1.  How do the req params get transferred?

        1.  Location

        2.  Refer above

6.  Perf scoring mechanism

    1.  Computation

    2.  Filtering? Some sort of MPE here?

    3.  How will the bid looklike? how will the score translate to CPM?
        and then how will delivery be impacted with this CPM?

7.  Design on Prod pipeline

    1.  How we extract features from ingested articles?

    2.  How we extract features from campaigns

    3.  Where do we store the features?
