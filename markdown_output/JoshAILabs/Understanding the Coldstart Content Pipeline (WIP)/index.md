### Problem Statement

Tracking the VP and their performance across user feeds is one of the
biggest and most impactful KRAs of the BU. Frequently, we keep
encountering problems with the VP going down in the users\' feed.

In the context of cold-start arms, this implies that the number of
events served to the users from these specific arms is on the lower
side.

To get into the depth of this problem, we took the approach of first
understanding the current flow of cold-start arms in-depth and all the
possible factors that contribute to change in VP from this flow. Since
there are too many moving parts, it is tough to directly correlate a
change to the direct impact on the VP.

However, it is possible to bring more checks and balances in place to
have better control of the experiments/production flow.

## Flow (current understanding) 

- Candidate Sampler → config → Candidate arms/generators → Item Sampler
  to create Query

- Query → HNSW Index Class → Generator specific function → Nearest
  Neighbours

Notes

1.  for each arm, there is a predefined limit and properties.

2.  Using these properties the ItemSamplingRetrieval class is called and
    items are sampled from the user history using the properties of that
    particular arm. The items sampled can be over various types, such as
    "recent_watch", "like", "recent_history", etc.

3.  The sampled items are basically the query items that are then used
    to call the respective index for the given arm.

4.  In the case of cold-start content, HNSW index class is called, this
    contains multiple functions which define the type of query to use
    for the HNSW, such as "items_to_items",
    "items_to_items_recent_watch", etc. Each of these functions contains
    its own logic which used the query items in various ways.

5.  In these functions, RocksDB/HNSW is called to obtain the embeddings
    corresponding to each query item, and then function-specific logic
    is applied to form a final query embedding to query HNSW and get the
    nearest neighbors.

6.  After this, any distance threshold and popularity bias mentioned in
    the properties for the specific arm is implemented on the result
    nearest neighbors.\
    Currently the following thresholds are being used:

    1.  `v2v_recent_watch_coldstart_content`

        1.  distance_threshold: `1.0`

        2.  popularity bias:`1000`

    2.  `v2v_blip_hist_coldstart_content`

        1.  distance_threshold: `1.0`

        2.  popularity bias:` N/A`

    3.  `v2v_blip_most_recent_like_coldstart_content`

        1.  distance_threshold: `1.0`

7.  The results are then sent through Ranker and Blending.

**Current API Refresh Frequency**: Every 4 hours

**Current HNSW Index creation Frequency**: Every 2 hours

New content in every Refresh:

Coldstart Content Arms and their distribution:

- \'u2v_blip_coldstart_content\', 0.005 or 10 items whichever higher

- \'v2v_recent_watch_coldstart_content\', 0.06 or 70 items, whichever is
  higher

- \'v2v_blip_hist_coldstart_content\', 0.05 or 50 items, whichever is
  higher

- \'v2v_blip_most_recent_like_coldstart_content\' 0.035 or 50 items,
  whichever is higher.

- \'item_cand\~coldstart_content_graphdb\' (Not Using HNSW cold-start
  index)

Frequently Occurring Issues:

- The number of events served to the user has been going down. The
  reason needs to be figured out.

### Action Items

1 complete [Check if indices are being formed
correctly.]{.placeholder-inline-tasks}

2 complete [Check if the queries are being formed
correctly.]{.placeholder-inline-tasks}

3 complete [Check the output from Generator specific functions' arms
which might have affected distribution (Config logs for every date
provided below.)]{.placeholder-inline-tasks}

Config logs (DateWise):22_06_2023 lru_cache_max_size changed from 50000
to 25000 (unsure how this may effect serving) Day of drop 23_06_2023 : 4
gem candidate sources of gem added above blip coldstart_content arms
27_06_2023: max_limit(distribution) changes for newuser sources (should
have no effect) v2v_coldstart(user) moved up (may have effect) ann_als
hashcodes reduced (should have no effect) 28_06_2023: v2v_recent_longw
removed (it was below coldstart_content, thus should have no effect)
29_06_2023: v2v_coldstart(user) properties changed (should have no
effect) 30_06_2023: top_creator_content\~popular_meta added above blip
coldstart_content arms, but not enabled (should have no effect)
01_07_2023 v2v_coldstart(user) properties changed (should have no
effect) 03_07_2023: top_creator_content\~popular_meta enabled above blip
coldstart_content arms (may have effect) 05_07_2023:
top_creator_content\~popular_meta disabled (should have no effect)
content_based_ppr properties changed (should have no effect) ann_als
disabled (should have no effect) dnn_mtl_model for all hashcodes (may
have effect) v2v_theme added above above blip coldstart_content arms
(may have effect) 06_07_2023 some bloom_filter fix was pushed (unsure
how this may effect serving) changes made regarding v2v_m_queries, below
blip coldstart_content arms (should not have any effect) 07_07_2023
serving starts rising for coldstart_content arms, no changes in config

5 complete [Check if any noticeable timeout issues have taken place vs
the change in VP. ]{.placeholder-inline-tasks}

6 incomplete [Check correlation between VP and everytime index is
refreshed]{.placeholder-inline-tasks}

7 incomplete [Check VPs in the entire platform vs VP on
coldstart_content arms]{.placeholder-inline-tasks}

8 complete [Check for the uniqueness (freshness) of the items being
served. Perform and item id level check.]{.placeholder-inline-tasks}

This chart shows the Counts of Unique items served on each date and the
new items served on that day.

This chart shows the Counts of all the events on the dates.

This chart is combination of the charts above but the counts are all
normalized so that they are all between the same range.

**Observation:**

The new unique items served each day seem to be a bit less, but the days
before the drop also show the around similar number of new unique items.

9 complete [Implement a logger for the change in config (versioning) for
tracking the changes\
\
]{.placeholder-inline-tasks}

## Steps taken to tackle Coldstart Content problems: 

1.  **Processes set:**

- **Data Sources (Athena table) not updating** : Alerts in place on API
  end to notify when delta for new items in null, Also mentioned to team
  responsible for Athena Table to set alerts on their end if new items
  are not being populated.

- **Index not created** : Alerts in place on API end to notify whenever
  there is a problem/error to create the index. Also a debug log exists
  to keep track of all items being indexed every 2 hours, along with a
  muted notification every time the index is pushed to s3.

- **Config changes manually** : Logging config every time a commit is
  pushed to master so that changes can be revisited in a programmatic
  manner.  Also, hold any person accountable for changes made to the
  config for coldstart_content arms.

- **Manual index refresh** : Automate any processes that are manual for
  refresh of HNSW index

**2. One time debugging exercise:**

- **Serving decreased** : Reduced any popularity bias (num of views
  threshold)  present so that all content can get surfaced

- **Query Formation** : Manually checked if the queries made to the BLIP
  index inside the Triton server are correct (preformed for multiple
  users)

- **Index outputs** : Manually loaded index to check if outputs are
  inline with BLIP similarity visually.
