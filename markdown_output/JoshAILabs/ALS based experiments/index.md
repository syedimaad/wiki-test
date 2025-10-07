**Approaches for events based on watched (90%) \[p90\] :**

Taking motivation from the performance of ALS based on liked events and
two-tower on watch-time-gain, we can move forward with following
approaches for training ALS on watched (90%) events.

**Baseline experiment**

1.  Create user-item interaction matrix with "video_played" as filter
    condition.

2.  If watch_time % \>= 90 then target = 1 , else target = 0.

**Assigning Target based on video length**

1.  Create user-item interaction matrix with Assigning Target based on
    video length. "video_played" as filter condition.

2.  Based on following percentiles (after discarding outliers), specific
    target value can be given with respect to the item. This will be for
    user-item interaction fulfilling the "p90" criteria.

    1.  vl_p0 to vl_p20 → 1

    2.  vl_p20 to vl_p40 → 2

    3.  vl_p40 to vl_p60 → 3

    4.  vl_p60 to vl_p80 → 4

    5.  vl_p80 to vl_p99 → 5

3.  at percentile 99.9 the video_length is coming to be 253 seconds i.e
    , 4 minutes. So items with video_length with percentile \> 99.5
    \[video_length = 70.65 seconds\] can be discarded as outliers

**Assigning Target based on watch_time**

1.  Create user-item interaction matrix with Assigning Target based on
    video length. "video_played" as filter condition.

2.  Discard outliers as discussed in the previous approach.

3.  Calculate mean and standard deviation of watch_time with respect to
    each item

4.  For each user-item interaction, based on the user watch_time, we can
    calculate the watch-time gain value: (USER_WATCH_TIME -
    MEAN_WATCH_TIME) / (STD_DEV).

5.  The above watch time gain value can be used as target for all the
    user-item interactions.

6.  The advantage of this approach is that we are also feeding
    user-level information to the model in the form of *watch_time*

After scaling the values in range \[1,5\], following is the distribution

**Evaluation :**

For creating evaluation data, after taking next day's data , we can
create positive and negative interactions data in the following way:

1.  if watch_time % \>= 90% → label = 1

2.  else, label = 0

Metrics to be used:

1.  Hit ratio @ k →

2.  Coverage @ k → get topK recommendation for all users, check unique
    count of items

3.  Precision @ k →

**ALS experiments by capping** ***item_age*** **:**

+----------+-----------------+--------------+----------------+-------------+----------------+-------------+
| Training | Evaluation_Date | ALS with Item_Age capping                   | Performance of prod-ALS      |
| Dates    |                 |                                             |                              |
+----------+-----------------+--------------+----------------+-------------+----------------+-------------+
|          |                 | Max_Item_Age | Item_Pool_Size | Hit_Rate@50 | Item_Pool_Size | Hit_Rate@50 |
+----------+-----------------+--------------+----------------+-------------+----------------+-------------+
| 15th     | 14th feb        | 45           | 616K           | 37.90%      | 842K           | 33.40%      |
| jan -    |                 |              |                |             |                |             |
| 13th feb |                 |              |                |             |                |             |
|          |                 +--------------+----------------+-------------+                |             |
|          |                 | 15           | 525K           | 37.20%      |                |             |
|          |                 +--------------+----------------+-------------+                |             |
|          |                 | 60           | 636K           | 36.76%      |                |             |
+----------+-----------------+--------------+----------------+-------------+----------------+-------------+
| 11th     | 10th feb        | 45           | 596K           | 32.29%      | 818K           | 28.54%      |
| jan -    |                 |              |                |             |                |             |
| 9th feb  |                 |              |                |             |                |             |
|          |                 +--------------+----------------+-------------+                |             |
|          |                 | 15           | 509K           | 16.50%      |                |             |
|          |                 +--------------+----------------+-------------+                |             |
|          |                 | 60           | 613K           | 31.10%      |                |             |
+----------+-----------------+--------------+----------------+-------------+----------------+-------------+
| 27th     | 26th feb        | 45           | 700K           | 23.07%      | 920K           | 23.13%      |
| jan -    |                 |              |                |             |                |             |
| 25th feb |                 |              |                |             |                |             |
|          |                 +--------------+----------------+-------------+                |             |
|          |                 | 15           | 594K           | 18.50%      |                |             |
|          |                 +--------------+----------------+-------------+                |             |
|          |                 | 60           | 717K           | 23.00%      |                |             |
+----------+-----------------+--------------+----------------+-------------+----------------+-------------+
| 30th     | 1st march       | 60           | 750K           | 33.16%      | 956K           | 34.75%      |
| jan -    |                 |              |                |             |                |             |
| 28th feb |                 |              |                |             |                |             |
+----------+-----------------+--------------+----------------+-------------+----------------+-------------+
