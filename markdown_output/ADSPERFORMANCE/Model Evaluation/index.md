**[Performance Metrics for display
advertisements]{style="color: rgb(67,67,67);"}**

[CTR (Click-through rate) -\> #Clicks / #Impressions (View an
ad)]{style="color: rgb(67,67,67);"}

[CVR (Conversion rate) -\> #Conversion / #Clicks
]{style="color: rgb(67,67,67);"}

[where action of conversion can like app install, filled lead form,
product purchase etc]{style="color: rgb(67,67,67);"}

[So CTR / CVR Prediction can be modeled as a binary classification
problem and we can use predicted probabilities as is of our use case,
For example: CTR Prediction -\> Clicks are used as positive set and rest
impressions as negative set, predicted_ctr = p(click/impression)
]{style="color: rgb(67,67,67);"}

**[Metrics to evaluate ctr/cvr prediction model
]{style="color: rgb(67,67,67);"}**

1.  [AUC - ROC Curve]{style="color: rgb(67,67,67);"}

2.  [Decile Rank]{style="color: rgb(67,67,67);"}

3.  [RIG (Relative Information Gain)]{style="color: rgb(67,67,67);"}

**[Confusion Matrix]{style="color: rgb(67,67,67);"}**

[TPR (Recall) -\> Predicted Positive / all actually positive
]{style="color: rgb(67,67,67);"}

[FPR - \> Predicted Positive / all actually negative
]{style="color: rgb(67,67,67);"}

**[AUC ]{style="color: rgb(67,67,67);"}**

[An aggregate measure of performance across all possible classification
thresholds. One way of interpreting AUC is as the probability that the
model ranks a random positive example more highly than a random negative
example.]{style="color: rgb(67,67,67);"}

- *[Scale-invariant]{style="color: rgb(67,67,67);"}*[ -\> Measures how
  well predictions are ranked, rather than their absolute values, Not
  desirable when we need well calibrated probability
  outputs.]{style="color: rgb(67,67,67);"}

- *[Classification-threshold-invariant]{style="color: rgb(67,67,67);"}*[
  -\> Measures the quality of the model\'s predictions irrespective of
  what classification threshold is chosen.
  ]{style="color: rgb(67,67,67);"}

- [A poorly fitted model has even higher AUC in the presence of a large
  number of negative samples concentrated on the low end of the p_click
  score range, thus lower CTR. This has an effect of lowering the FPR in
  the relatively higher range of p_click scores, thus raising the AUC
  score.]{style="color: rgb(67,67,67);"}

**[Rank ]{style="color: rgb(67,67,67);"}**

[Steps ]{style="color: rgb(67,67,67);"}

1.  [Sort predictions in descending order of
    probabilities.]{style="color: rgb(67,67,67);"}

2.  [Divide Eval set into 10 deciles and count no of clicks in each
    decile.]{style="color: rgb(67,67,67);"}

3.  [Multiply decile_no and no of clicks for each decile and then take
    avg (weighted average).]{style="color: rgb(67,67,67);"}

[So ideally we want all clicks in top so decile rank would be lower , If
clicks are ranked in lower deciles, we have used decile_no as penalty So
rank becomes higher and model is worse in that
case.]{style="color: rgb(67,67,67);"}

- [It depends on number and position of positive samples in the sorted
  evaluation set, it ignores negative
  samples.]{style="color: rgb(67,67,67);"}

- [Rank can be used in comparison of two models on same positive set
  count.]{style="color: rgb(67,67,67);"}

- [Rank as a number is difficult to
  interpret.]{style="color: rgb(67,67,67);"}

[ Example ]{style="color: rgb(67,67,67);"}

  -------- -------------- ------------------------
  Decile   No of clicks   Decile \* No of clicks
  1        1658           1658
  2        413            826
  3        226            678
  4        122            488
  5        83             415
  6        41             246
  7        36             252
  8        16             128
  9        8              72
  10       3              30
  -------- -------------- ------------------------

[Rank = sum_of\_(decile\*no_of_clicks) /
no_of_deciles_with_atleast_one_click = 4793 / 10 =
479.3]{style="color: rgb(67,67,67);"}

**[RIG ]{style="color: rgb(67,67,67);"}**[(Relative Information
Gain)]{style="color: rgb(67,67,67);"}

- Easy to interpret unlike rank

- More Reliable, follows higher the better trend, unlike auc which might
  be misleading in some cases

- [Not Scale-invariant unlike auc, it takes calibration into
  account]{style="color: rgb(67,67,67);"}

- [Both positive and negative class are used in computation, unlike
  rank]{style="color: rgb(67,67,67);"}

- Ranges from 0 to 100% and negative score mean model is performing
  worse than predicting ctr for each user

[RIG = 1 - NCE ( normalized cross entropy) → How much logloss is reduced
w.r.t if we predicted ctr ?]{style="color: rgb(67,67,67);"}

[NCE = log_loss using calibrated model predictions / log_loss if we
predict ctr of dataset]{style="color: rgb(67,67,67);"}

LogLoss =\>

[https://www.google.com/search?q=log+x+graph&rlz=1C1CHBD_enIN816IN816&oq=log+x+g&aqs=chrome.0.0i512j69i57j0i512l2j46i10i199i465j69i60l3.2407j0j7&sourceid=chrome&ie=UTF-8](https://www.google.com/search?q=log+x+graph&rlz=1C1CHBD_enIN816IN816&oq=log+x+g&aqs=chrome.0.0i512j69i57j0i512l2j46i10i199i465j69i60l3.2407j0j7&sourceid=chrome&ie=UTF-8){card-appearance="inline"}

Calibration = mean_prediction / mean_ctr

Calibrated_prediction = model_prediction / calibration

[Area-Under-ROC (AUC) is also a pretty good metric for measuring ranking
quality without considering calibration. In a realistic environment, we
expect the prediction to be accurate instead of merely getting the
optimal ranking order to avoid potential under-delivery or
over-delivery. NCE measures the goodness of predictions and implicitly
reflects calibration. For example, if a model overpredicts by 2x and we
apply a global multiplier 0.5 to fix the calibration, the corresponding
NCE will be also improved even though AUC remains the
same]{style="color: rgb(67,67,67);"}

Model Evaluation Examples:

**Example1 → Rig metric is easy to interpret unlike rank**

  ------------- ------------ ------- -------- ------- ------------- ------ ------ --------- --------- --------------------
  campaign_id   model_type   auc     rank     rig     calibration   mean   std    num_pos   num_neg   CTR/CVR (eval-set)
  100004        CAMP         0.860   70.90    18.77   1.11          0.17   0.74   342       222.5k    0.15%
  100004        ORDER        0.842   77.40    15.65   1.22          0.19   0.34   342       222.5k    0.15%
  100004        CAMP_OLD     0.824   82.90    15.59   1.10          0.17   0.48   342       222.5k    0.15%
  100004        SUBCAT       0.766   100.30   8.79    1.16          0.18   0.20   342       222.5k    0.15%
  100004        CAT          0.607   151.90   0.68    3.70          0.57   0.43   342       222.5k    0.15%
  ------------- ------------ ------- -------- ------- ------------- ------ ------ --------- --------- --------------------

**Example2 → Very high auc model does not have very high rig score**

  ------------- ------------- ----------- --------- ----------- ------------- ------ ------ --------- --------- --------------------
  campaign_id   model_type    auc         rank      rig         calibration   mean   std    num_pos   num_neg   CTR/CVR (eval-set)
  204           APP_BRAND     **0.994**   428.14    **67.39**   1.55          1.49   7.48   2408      247.2k    0.96%
  204           APP           0.993       430.19    67.10       1.52          1.46   7.46   2408      247.2k    0.96%
  204           APP_CAT       0.794       1131.86   8.05        0.54          0.52   0.74   2408      247.2k    0.96%
  204           APP_GENERIC   0.789       1150.09   13.96       2.96          2.86   6.39   2408      247.2k    0.96%
  ------------- ------------- ----------- --------- ----------- ------------- ------ ------ --------- --------- --------------------

**Example3 → Model XGB_LR despite having high auc does poor on rig and
rank metric**

  ------------- ------------- ------- --------- ------- ------------- ------ ------ --------- --------- --------------------
  campaign_id   model_type    auc     rank      rig     calibration   mean   std    num_pos   num_neg   CTR/CVR (eval-set)
  226           APP_BRAND     0.863   474.20    17.40   1.50          0.68   1.88   2363      519.7k    0.45%
  226           **APP**       0.851   500.30    15.95   1.49          0.67   1.91   2363      519.7k    0.45%
  226           APP_CAT       0.697   841.60    -2.50   4.27          1.93   5.69   2363      519.7k    0.45%
  226           **XGB_LR**    0.851   976.50    -2.70   0.37          0.17   0.06   2363      519.7k    0.45%
  226           APP_GENERIC   0.605   1053.50   -6.89   7.61          3.44   6.41   2363      519.7k    0.45%
  ------------- ------------- ------- --------- ------- ------------- ------ ------ --------- --------- --------------------

[ ]{style="color: rgb(67,67,67);"}
