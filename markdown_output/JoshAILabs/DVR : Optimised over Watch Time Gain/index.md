**paper :**
[**https://arxiv.org/pdf/2208.05190v1.pdf**](https://arxiv.org/pdf/2208.05190v1.pdf)

**Duration Bias**

- If we consider watch time as metric, longer videos tends to have
  larger watch time compared to shorter videos which favours long
  video\`s in recommendation

- if we consider watch percentage (P90) as metric, shorter videos tends
  to have more watch percentage than long videos which favours short
  video\`s in recommendation

- EX : a video of 10 sec has more watch percentage than video of 60 sec

**3 methods to avoid duration bias**

1.  Remove micro-video duration from input features, which eliminates
    duration bias fundamentally

2.  Introducing an unbiased evaluation label Watch Time Gain (WTG),
    which measures a user's relative engagement on a video against the
    average engagement of all users on videos with the same
    duration-level.

3.  DVR based model architecture which completely eliminates implicit
    duration signals

**Watch Time Gain (WTG)**

- We first divide the given items video duration into buckets with equal
  width bins

- And we calculate the mean watch time/time spent within each similar
  video duration bucket

- For each event we find the delta between time spent by the user and
  the avg time spent of all users of that duration bucket( mean watch
  time)

- And we divide the delta by standard deviation to standardise the watch
  time within the bucket which makes it independent of video duration

**Debiased Video Recommendation(DVR)**

In order to make the predicted WTG independent with video duration, we
add an extra regression layer and train the framework in a adversarial
way using Gradient Reversal Layer (GRL)

- Here Φ represents any backbone Recommendation model and Ψ represents
  Duration Regressor model

- Φ tries to predict WTG from given input features

- Ψ tries to predict the duration of the video using predicted WTG from
  Φ

- Now, GRL tries to force Ψ to discover possible correlations between
  the predicted WTG from Φ and video duration as much as possible in the
  forward pass.

- And In the Backward pass we take the negative gradients and use them
  to eliminate video duration influence on Backbone model ( so that it
  predicts WTG without disturbance of video duration)

In short we will be optimising Ψ using 𝐿 𝐷 and optimising Φ with 𝐿 𝑊 𝑇𝐺
− 𝐿 𝐷

**Proposed Metric**

WTG@K is the average of top k recommended videos WTG\`s , the more WTG@K
the user is willing to spend time on top recommended videos

------------------------------------------------------------------------

**Questionnaires**

How to categorize the buckets ?

- Based on quantile distribution ( select the range btw quantiles where
  most of the data i.e \> 98 or 99% data lies and also width of bucket
  will be decided based on subsequent quantity of videos in it)

What is the criteria for positive and negative label ?

- The criteria is Watch Time Gain (WTG) and threshold is where ratio of
  positive to negative items count is 50:50 (or) 60:40

How to evaluate ?

- Hit ratio and other metrics

------------------------------------------------------------------------
