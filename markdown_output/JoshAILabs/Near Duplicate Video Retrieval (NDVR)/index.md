### [[Inspiration]{style="color: rgb(17,85,204);"}](https://www.microsoft.com/en-us/research/uploads/prod/2021/01/ICPR.pdf)

### Key challenges faced by the current model

1.  Capturing temporal context - The current approach (traditional NDVR
    techniques) is just to get Mobilenet embeddings for n equidistant
    frames and aggregating them. In this way of trying to get a video
    embedding from frames , we loose out on the temporal information.
    This is what the paper proposes to solve the shortcomings of
    traditional NDVR techniques. Two stream architecture that combines
    RGB with optical flow features followed by a multi-head attention
    mechanism.

2.  Duplicate videos often contain frames that are

    1.  Noisy - frames heavily edited from the original content

    2.  Irrelevant -- unrelated frames deliberately inserted to
        circumvent copy detection

### Approach

We plan on training a Siamese network with [[[triplet
loss]{.underline}]{style="color: rgb(17,85,204);"}](https://towardsdatascience.com/triplet-loss-advanced-intro-49a07b7d8905)
where -

- Anchor - Original video

- Positive - Duplicate video with random augmentation (basic Filters and
  text for now)

- Negative - Different video.

### Architecture

#### Steps to Generate Embeddings for each video

1.  Extract M equidistant frames from video.

2.  Extract:

    1.  RGB_features (from Inception_v3) - (2048, M)

    2.  Flow_features (from Flownet 2.0) - (1024, M)

3.  Apply the multi-head (N=4) attention and shifting operation to get -

    1.  RGB_attention_features - (2048, 4)

    2.  Flow_attention_features - (1024, 4)

4.  Flatten (Concatenation operation in the architecture figure) these
    attention_features:

    1.  RGB_attention_vector - 2048 \* 4 = 8192

    2.  Flow_attention_vector - 1024 \* 4 = 4096

5.  Split these flattened vectors into K splits.

    1.  Basically, Step 4. And 5. has converted the attention vectors
        from (2048, N=4), (1024,N=4) to (2048, K), (1024, K)
        respectively.

6.  Concatenate the split feature vectors individually to get K vectors
    and pass them through a fully connected layer to get Enriched
    Features i.e. Embeddings.

**[Distance Metric]{.underline}**

Cosine distance to measure the similarity between a query video Q and a
reference video R -

### Training Triplet-Data Preparation - (Anchor, Positive, Negative)

#### [General Guidelines to data-preparation for NDVR model training using Siamese Network.]{.underline}

1.  Negative sampling is challenging for NVDR due to the imbalanced
    nature of the problem. The total number of negative samples
    (dissimilar video pairs) is far higher than that of positive samples
    (near duplicate videos). Moreover, most of the negative samples are
    easy examples and thus do not contribute much to learning.

2.  Real-world duplicate videos often contain frames that are noisy --
    i.e., frames heavily edited from the original content -- and
    irrelevant -- i.e., unrelated frames deliberately inserted to
    circumvent copy detection.

#### **[Our Strategy]{.underline} -**

1.  Leverage current DeDup model in production - For an Anchor video,

    1.  Positive example would be any video that matched with score
        greater than 0.98 (Current threshold is 0.95 in production)

    2.  Negative example can be picked from the same blip cluster basis
        the distance from the anchor video.

2.  Take Videos of some famous creators (these should be creator
    profiles where in a lot of the videos are ones in which the same
    creator is present).

    1.  Positive pairs can be created by doing random Augmentation
        (described in the next section) to the same video.

    2.  Negative pairs can be different videos of the same creator.

3.  Leverage the error cases identified by the operations team.

    1.  Positive pairs - False Negatives identified by the operations
        team

    2.  Negative Pairs - Same as described in 1b - i.e, video can be
        picked from the same blip cluster as the anchor video.

**[Inference / Production]{.underline} -**

The model inference has been designed as an API. The dockerized version
of this has been pushed to the josh-prod-acr in AZURE. Load testing was
done in the dev environment. It was found that one pod (NC8asT4_v3) can
handle 3-4 RPS comfortably.

**[Current State]{.underline}** - Discussions are being done to use the
NDVR model as an additional filter as it has really low False Positive
Rates.

Further some iterations need to be done to refine the model. This
iteration has shown some promising results.
