### Objective

Send personalized notifications to users basis their interests in the
past

### Approach

- Fetch interests of users (Medoids → Medoids are item ids that
  represent users\' interests)

  - Across a day (or more), fetch each user's list of medoids

  - **Source :**
    s3://josh-reco-ml-dataset/us-ml-team/long_term_history_modeling/blip_16/{yyyymmdd}/

  - Medoids are pre-computed using the following algorithm:

    - Take past X days events (Currently X is 14 days)

    - For every user-item interaction, based on the interaction type
      (like video_liked, video_shared, full_watch etc), compute weight
      for every unique user-item interaction

    - Get blip embeddings (PCA 128, Trimmed to first 16 values) for each
      item of every user-item interaction

    - At user level, Run DBSCAN clustering on the trimmed blip
      embeddings of their interacted items

    - Assign cluster numbers to each interacted item of that user

    - Sample (Weighted Sampling based on computed weight) items from
      each cluster to get a max of 12 items in total, such that the
      ratio of actual items across clusters will be same as ratio of
      sampled items across clusters\
      (For Example:\
      A user has interacted with 120 items, after running DBSCAN, 30
      items fell under cluster-1, 40 under cluster-2, 50 under
      cluster-3\
      Now to get a max of 12 items for that user, we sample cluster-1 to
      get 3 items, cluster-2 for 4 items, cluster-3 for 5 items as the
      ratio remains the same as 3:4:5 )

    - Assign these sampled items as medoids for the user and store
      accordingly

    - Repeat the above for all users

- Global Medoids Generation

  - Find all unique medoids from the above dataset

  - Get blip embeddings (PCA 128) of all the unique medoids (Trimmed to
    first 16 values) and run KMeans (current k set to 500)

  - Store one medoid for each cluster (using KMedoids Algorithm, setting
    k to 1, which inturn gives the item which is closest to the rest in
    the same cluster)

- Captions/notification templates for each global medoid/cluster

  - \<Process\>

- Candidates for a user

  - For a user, fetch their interest medoids (Same used in step 1)

  - Using the above medoids, query the global medoids computed from the
    previous step

- Filtering

  - If the user has already watched specific candidates, replace them or
    increase the candidate pool by querying a more extensive item index

  - A more extensive index could be created in the following ways:

    - Popular items blip index

    - Global Medoids Index

    - Cold start index

- Ranking

  - The candidates generated after the filtering process in the previous
    step needs to be ranked in order to get the one item that will be
    served to the user in the notification.

  - The template being used for this particular item will remain the
    same as the template used for its global medoid. Alternatively, we
    can use a similar template from the variations of templates used for
    the global medoids.

- Template Generation

  - TODO

Open ended questions:

1.  Users\' medoids are items ids that represent a user's interest.
    These item ids can change on a daily level given the algorithm used
    for calculating medoids.

2.  Refreshing the template on a daily level might be a challenge, if it
    is a manual process

3.  Fix the frequency of global medoids generation

4.  Target frame from the video for Generating Notification Big Image

5.  Filtering out items which have been sent to users but haven't got
    any engagement

    1.  Storing Delivered items/notifications for a user

    2.  Click but not played?

6.  Select Global Medoid(item) based on user language

7.  Include Celebrity affinity to identify Global Medoid for cases where
    user has a celebrity based Local Medoid(LTHM)

8.  Allow Replacement of Global Medoid by Ops??

9.  Blip vs GEM for Global Medoids?

10. Including Popular video as Global Medoid based on Ranking(to enble
    alternate video selection in case user has already viewed)
