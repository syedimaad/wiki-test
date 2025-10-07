**Content \<\> Collaborative Generic Embeddings**

**Approach(Currently Training)**

Zero shot learning of video embedding using ALS

Similar to CLIP approach the content embedding is obtained from both VIT
encoder and whisper audio encoder and combined together with the
objective of getting embedding similar to collaborative approach

Architecture

Currently the training of the model is going on with the ALS item
embedding generated for hindi language.

The Training data

Train size - 5 lakh items

Val size - 1.5 lakh items

Final Update

**After Inputs from Yuri**

**Data Formation**

- Take user session(user should not have watched/liked all the videos
  served) take all the videos he has fully watched/liked

- Form the pairs from all the full watched/liked videos and filter based
  on the number of times they have been full watched/liked together by
  different user across sessions

- Calculate the distances from the blip model for these positive pairs
  and use these scores as buckets during training

- Similarly create negative items to the positive pairs using the items
  which have not got interaction from the same user and score them using
  blip

Example data

Item1 Item2 Positive Blip Similarity

Item1 Item3 Negative Blip Similarity

Item3 Item10 Positive Blip Similarity

## Dataset Preparation

### Phase 1: Filtered Client-Item Interactions Preparation

1.  Load `Daily-Snapshot` Data of `Josh-Recsys` for the required date
    range ( Considered 1 week from 20230201 to 20230107 for initial
    training)

2.  Classify every user-item interaction as either `Positve` or
    `Negative` or `Neutal` based on following conditions:

    1.  Consider Positive, if PCC \> 90% or has user liked it

    2.  Consider Negative, if timespent is below 5 secs (Bounce/Skip
        \@5secs) or PCC \< 30%

    3.  Else, Consider as Neutral

3.  Filter out all Neutral events

4.  Filter out all clients who have Positive-CTR above 90%\
    \[ Positive-CTR = Positive-items-count / (Positive-items-count +
    Negative-items-count) \]

5.  Save to S3

### Phase 2: Item Meta Data Preparation

1.  Load Phase 1 final dataset

2.  Get all unique item-id's

3.  Join with `josh-meta/video` delta dataset, and extract required
    features like download_url

4.  Save to S3

### Phase 3: Pairs Preparation

1.  Load Phase 1 final dataset

2.  Positive Pair Preparation:

    1.  Select all positve interactions

    2.  Self join with key as `client-id` to form pairs

    3.  filter out same item-id & duplicate item-id pairs

    4.  Save to S3

3.  Negative Pair Preparation:

    1.  Select all negative interactions

    2.  Self join with key as `client-id, session-id` to form pairs

    3.  Save to S3

4.  Combine both Positive & Negative Pairs to form single Dataset

5.  Group on `item-id-1, item-id-2, pair-type`, to get
    num-clients-interacted aggregated metric

6.  Get meta features like download-url for each item-id by joining with
    Phase-2 Meta dataset

7.  Save to S3
