POC/ Owner - Nitesh Sawadia , email - <nitesh.sawadia@verse.in>

Repo link
-<https://gitlab.dailyhunt.in/ai-lab/dh-reco/candidate-generator/collaborative-filtering/-/tree/starfish_prod?ref_type=heads>

**Objective-**

Candidate generation through Collaborative filtering methods.

**Theory-**

*Implicit data (the type of data we're using here)* is data we gather
from the users behaviour, with no ratings or specific actions needed. It
could be what items a user purchased, how many times they played a song
or watched a movie, how long they've spent reading a specific article
etc. The upside is that we have a lot more of this data, the downside is
that it's more noisy and not always apparent what it means.

Under the hood, Alternating Least Squres (henceforth ALS) is a \'fancy\'
two step gradient descent technique to find matrices 𝑃P, the user
factors matrix and 𝑄Q, the item factor matrix such that 𝑈≈𝑃𝑄𝑇U≈PQT. The
gradient descent works to minimise the square of the L2 norm of the
matrix \|𝑈−𝑃𝑄𝑇\|\|U−PQT\|

This is very similar to Ordinary Least Squares (henceforth OLS), which
also involves gradient descent to find the coefficient matrix 𝑤w of a
linear regression model 𝑦=𝑋𝑤+𝜖y=Xw+ϵ. The gradient descent works to
minimize the square of the L2 norm of the vector \|𝑦−𝑋𝑤\|\|y−Xw\|

This establishes the fact that ALS in recommender systems is an analogue
of OLS in linear regression.

**Approach taken -**

1.  (***Previous Approach***) Trained a two-tower model with *user_id
    vs. item_id* as UI-matrix on MIND news dataset.

2.  ***(Current Approach)*** Train 3-ALS models with the following
    UI-matrices on DH-data :

    1.  user_id vs article_NER_community(s)

    2.  user_id vs article_topic

    3.  user_id vs article_story_id ;

with ***ratings*** inferred by calculating **PMI (Point-wise Mutual
Information)** based on no. of articles under each entity as score.

**WorkFlow DAG**

**Filtering Rules applied-**

1.  Valid Article for Collaborative signal if number of users interacted
    \> 20.

2.  Valid Users for Collaborative signal if -

    1.  number of PV-interactions per day \<= 200 (bot filter)and,

    2.  number of active days \>= 2 with a minimum of 2 events per
        active day

in a period of 5 days and user was active for a minimum of 2 days.

3\. Valid entity (ner_community, topic, story) for Collaborative signal
if minimum 5 users have interacted with that entity.

**STARFISH INTEGRATION**

**[Training ]{.underline}**

- SPV events data (past 7 days)

Columns - 

1.  Client_id

2.  Properties_epoch_time_millis

3.  Properties_item_language

4.  Properties_item_id

5.  Properties_pv_activity

6.  Properties_user_app_ver

7.  Properties_timespent

Top-level Filters -

1.  Best client-item event by time spent

2.  Properties_pv_activity == story_detail

3.  Properties_timespent \>= 5 seconds

4.  User app version \>= 16.0

CF related Filters -

1.  Article filter - must be interacted by minimum 20 clients

2.  Bot filter - number of events in a day \> 200 is considered as bot

3.  Active day filter - Minimum of 2 events in a day is an active day,
    and users must have at least 2 active days.

- Enriched articles data

Columns - 

1.  Article_id

2.  Lang_code

3.  Sub_format

4.  Published_at

5.  Created_at

6.  Bibo_filter

7.  Nsfw_level

8.  Category - only name

9.  Story_dynamic_info - only cluster_id

10. Topic - for the version latest CF model has subscribed to

11. Ne_communities - only list of communities for the version latest CF
    model has subscribed to

- Training Schedule - Every hour

- Output - User vectors and Attribute vectors ***(To be stored in kafka
  for inference)***

  - DataType - Array\[Float\]

  - Dimension - 32

**[Inference]{.underline}**

Given an user-vector and corresponding model version (preferably
latest), perform KNN search on corresponding attribute vector store to
get the CF-attribute distribution.

Components :

1.  Version management Service

    1.  Fetch the latest active CF model version using
        /get_latest_service api

    2.  Get its subscribees' data using /get-subscribers-and-subscribee
        api

2.  Items Pool

Filters - 

1.  Latest article Version by published_at

2.  Language Specific

3.  Article id like r\"n\\d{8,10}\"

4.  Sub_format should be one of \"STORY\",\"S_W_IMAGES\",\"S_W_VIDEO\",
    \"S_W_PHOTOGALLERY\"

5.  Bibo_filter is True or Null

6.  Article not older than 72 hours from the time of inference

Preprocessing-

1.  For attributes with multiple versions like, topic and
    ne_communities, get the value corresponding to the version in
    subscribees data

2.  Define Item Age (in hours) bucket according to item age calculated
    on published at

item_age = (datetime now timestamp - (published_at/ 1000)) /3600

Age Buckets - 

1.  Item_age \<= 6 Hours

2.  6 hours \< item_age \<= 12 hours

3.  12 hours \< item_age \<= 18 hours

4.  18 hours \< item_age \<= 24 hours

5.  Otherwise

6.  Get the latest item_score (api developed by Lakshay chauhan) for all
    the articles to get the item_score column

7.  For each variant of CF- Define Rank of articles under each
    categorical value of the attribute (like topic) considering
    age_bucket and item_score.

*(Done in offline inference)*

*entity_window = Window.partitionBy(entity_col_name).orderBy(*

*        F.col(\"age_bucket\").asc(), F.col(\"item_score\").desc())*

**[Sampling Strategy]{.underline}** (Needs to be discussed)**\*\*\***

1.  Requires items pool, no. of max_candidates required and CF-attribute
    distribution of the User

2.  Boosting weights function - To get the sample count distribution
    from CF-attribute distribution

3.  Sample the articles belonging to each attribute value according to
    sample count distribution

4.  Return list of article_ids and corresponding item scores

    Flow-Diagram for Online Inference

**References-**

[https://medium.com/radon-dev/als-implicit-collaborative-filtering-5ed653ba39fe](https://medium.com/radon-dev/als-implicit-collaborative-filtering-5ed653ba39fe){card-appearance="inline"}
