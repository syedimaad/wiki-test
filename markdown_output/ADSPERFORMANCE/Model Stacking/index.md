### Aim:

To try and formulate a stacking implementation of models already trained
and see if there is a lift in AUC.

### Formulation:

[https://drive.google.com/file/d/1zSdjeYn89EGC6v6ioAfzgXMC_XqyFyVz/view?usp=sharing](https://drive.google.com/file/d/1zSdjeYn89EGC6v6ioAfzgXMC_XqyFyVz/view?usp=sharing){layout="center"
data-width="100.00" card-appearance="embed"}

Here Model1, Model 2, ... Model n are different models.

The predictions from the models are fed in to the MetaLearner alongwith
the Y variable. And the meta learner is trained to predict Y on the
basis of the predictions as X.

### Training:

1.  On any given day, treat yesterday's data as process set - X
    features, Y label.

2.  Pick N models starting from (today-1)

3.  Run the X features of process data through N models and generate N
    predictions per data point.

4.  split process set data into 80 - 20 train eval.

5.  On the train split:

    1.  Train a Meta Learner (Logistic Regression) on the N inputs and
        Y.

6.  On the eval split :

    1.  Predict from the Meta Learner.

    2.  Evaluate metrics on each of the N features, and meta learner
        prediction.

Document :
[https://docs.google.com/document/d/1fFfUNHW4F6A-0HZv8gsCetXQ-7D1FNXAg2D6Uucr0cg/edit?usp=sharing](https://docs.google.com/document/d/1fFfUNHW4F6A-0HZv8gsCetXQ-7D1FNXAg2D6Uucr0cg/edit?usp=sharing){card-appearance="inline"}

Averaging outcomes Old result

+-----+--------+-------------+-------+--------+-------------+-------+--------+-------------+------+
|     |        |             |       |        |             |       |        |             |      |
+-----+--------+-------------+-------+--------+-------------+-------+--------+-------------+------+
|     | Testing : 2022_05_23         | Testing : 2022_05_24         | Testing : 2022_05_25        |
+-----+--------+-------------+-------+--------+-------------+-------+--------+-------------+------+
|     | 1st    | Avg Decile  | RANK  | 1st    | Avg Decile  | RANK  | 1st    | Avg Decile  | RANK |
|     | Decile |             |       | Decile |             |       | Decile |             |      |
|     | Labels |             |       | Labels |             |       | Labels |             |      |
+-----+--------+-------------+-------+--------+-------------+-------+--------+-------------+------+
| M1  | 103    | 2.566539924 | 67.5  | 171    | 2.25739645  | 76.3  | 90     | 2.598039216 | 53   |
+-----+--------+-------------+-------+--------+-------------+-------+--------+-------------+------+
| M2  | 82     | 3           | 78.9  | 173    | 2.266272189 | 76.6  | 97     | 2.578431373 | 52.6 |
+-----+--------+-------------+-------+--------+-------------+-------+--------+-------------+------+
| M3  | 140    | 2.239543726 | 58.9  | 144    | 2.668639053 | 90.2  | 107    | 2.455882353 | 50.1 |
+-----+--------+-------------+-------+--------+-------------+-------+--------+-------------+------+
| M4  | 146    | 2.239543726 | 58.9  | 203    | 2.118343195 | 71.6  | 83     | 2.799019608 | 57.1 |
+-----+--------+-------------+-------+--------+-------------+-------+--------+-------------+------+
| M5  | 132    | 2.300380228 | 60.5  | 194    | 2.065088757 | 69.8  | 129    | 1.995098039 | 40.7 |
+-----+--------+-------------+-------+--------+-------------+-------+--------+-------------+------+
| LR  | 96     | 2.600760456 | 68.4  | 181    | 2.25443787  | 76.2  | 110    | 2.446078431 | 49.9 |
+-----+--------+-------------+-------+--------+-------------+-------+--------+-------------+------+
| AVG | 132    | 2.296577947 | 60.4  | 194    | 2.068047337 | 69.9  | 129    | 2.004901961 | 40.9 |
+-----+--------+-------------+-------+--------+-------------+-------+--------+-------------+------+
|     | RIG : \[8.39877, 4.42869,    | RIG : \[10.71927, 11.03016,  | RIG : \[8.6736, 8.78521,    |
|     | 11.27587, 11.19888,          | 7.68008, 11.81435, 12.56145, | 9.59282, 6.7516, 14.52996,  |
|     | 10.43622, 5.93475\]          | 7.68441\]                    | 8.13806\]                   |
+-----+                              |                              |                             |
|     |                              |                              |                             |
+-----+--------+-------------+-------+--------+-------------+-------+--------+-------------+------+
|     |        |             |       |        |             |       |        |             |      |
+-----+--------+-------------+-------+--------+-------------+-------+--------+-------------+------+
|     | Testing : 2022_05_26         | Testing : 2022_05_27         | Testing : 2022_05_28        |
+-----+--------+-------------+-------+--------+-------------+-------+--------+-------------+------+
|     | 1st    | Avg Decile  | RANK  | 1st    | Avg Decile  | RANK  | 1st    | Avg Decile  | RANK |
|     | Decile |             |       | Decile |             |       | Decile |             |      |
|     | Labels |             |       | Labels |             |       | Labels |             |      |
+-----+--------+-------------+-------+--------+-------------+-------+--------+-------------+------+
| M1  | 34     | 3.369230769 | 43.8  | 127    | 2.997142857 | 104.9 | 29     | 3.161290323 | 29.4 |
+-----+--------+-------------+-------+--------+-------------+-------+--------+-------------+------+
| M2  | 37     | 3.538461538 | 46    | 160    | 2.72        | 95.2  | 25     | 3.602150538 | 33.5 |
+-----+--------+-------------+-------+--------+-------------+-------+--------+-------------+------+
| M3  | 37     | 3.369230769 | 43.8  | 145    | 2.791428571 | 97.7  | 22     | 3.204301075 | 29.8 |
+-----+--------+-------------+-------+--------+-------------+-------+--------+-------------+------+
| M4  | 38     | 3.461538462 | 45    | 156    | 2.825714286 | 98.9  | 28     | 3.376344086 | 31.4 |
+-----+--------+-------------+-------+--------+-------------+-------+--------+-------------+------+
| M5  | 30     | 4.107692308 | 53.4  | 154    | 2.734285714 | 95.7  | 22     | 3.333333333 | 31   |
+-----+--------+-------------+-------+--------+-------------+-------+--------+-------------+------+
| LR  | 39     | 3.330769231 | 43.3  | 157    | 2.72        | 95.2  | 28     | 3.150537634 | 29.3 |
+-----+--------+-------------+-------+--------+-------------+-------+--------+-------------+------+
| AVG | 7      | 6.423076923 | 83.5  | 153    | 2.725714286 | 95.4  | 22     | 3.290322581 | 30.6 |
+-----+--------+-------------+-------+--------+-------------+-------+--------+-------------+------+
|     | **RIG : \[2.92014, 1.89791,  | RIG : \[4.92958, 7.48369,    | RIG : \[3.68412, 0.65355,   |
|     | 2.57333, 2.59622, -1.22979,  | 6.97755, 6.63847, 7.62957,   | 3.61738, 2.76003, 2.19741,  |
|     | 2.71494\]**                  | 5.31303\]                    | 2.49037\]                   |
+-----+                              |                              |                             |
|     |                              |                              |                             |
+-----+------------------------------+------------------------------+-----------------------------+

------------------------------------------------------------------------

##  Approaches

Logistic Regression Meta Learner

**Idea** : Use previous 5 days model and train a meta learn over that.

**Outcomes** :

- Predictions were almost similar for all the previous Models which was
  causing High Multi collinearity between the features with VIF over 10
  for some columns. So training LR only over past model predictions was
  useless.

- LR as a meta learner generally works better when we have weak learns
  that are overfitted/underfitted to a particular information of the
  data so that it can make predictions robust by aggregating knowledge
  from other models. But using similar kind of models as weak learners
  will result in same issues that weak learners were facing earlier.

Using Decision Trees to aggregate weak models

**Idea** : Take previous 5 days models and use their prediction to train
Decision Trees.

**Outcomes** :

- As stated in above approach since we don\'t have any additional
  information about the data it will not perform well and it changes the
  outcome prediction by making most of the predictions close to 0 since
  it is the majority class and hence leads to lower loss but that does
  not necessarily means it leads to better results.

- Eg : 0.2 prediction from 1000's of individual response from weak
  models but only 2 of them will be under 'is_postback' and for some
  prediction some model will be better than other So without any more
  information for meta learner it will not perform better than the weak
  learners at least in the long term.

Averaging

**Idea** : Since most of our model outputs are some what similar why not
average out the results

**Outcome** :

- Average was similar to original model predictions and we were unable
  to conclude if there was any significant difference between the
  averaging predictions and original model.

- It might make our model robust but since positive classes are so
  sparse any significant change in prediction was very difficult to
  differentiate whether its actually better or just some little variance
  in the predictions.

Weighted Average

**Idea** : Instead of taking average why not take weighted average wrt
different matrices.

**Outcome** :

- Selecting any metrics single will be difficult but it\'s discussed in
  detailed later.

Where to get these metrics to use?

1.  Use Metrics that are found in meta.csv. **Problem?** Since model is
    using Sample pool of all the past data to retrain, all metrics are
    very similar to each other.

2.  Taking 1 day buffer and using it as test set to get metrics.
    **Problem?** Variation on metrics for test dataset is so much that
    RIG value will be sometimes twice or even thrice as compared to some
    other models or sometimes negative also. Should have tried some
    additional things like random under sampling so that metrics are
    somewhat similar but again averaging will only make our model
    robust, we cannot expect it to boost the overall performance of the
    model so it was not worth pursing this scenario anymore.

Decision Trees as Meta Learner with Random undersampling

**Idea** : Use predictions from previous models along with some
additional top features to help the model predict better scores.

**Outcome** :

- Initially scores were better when data on which meta learner is
  trained is good enough

- We already have prediction results from models so we don\'t need to
  train model on whole data so we use random under sampling to retrain
  the model everyday.

------------------------------------------------------------------------

##  Metrics Selection

AUC/AUCROC/Precision/Recall/RIG/Rank

There are lot of metrics which can be used to compare results. But we
have 2 major problems which which causes issues when choose a single
metric.

1.  Ratio of Minority/Majority class is \< 0.01 so any loss
    function/metric which is used to train the model can easily be
    manipulated by the model by favouring majority class.

2.  We also need to account for probability of the outcome for eg: Model
    1 predicting 0.5 for a positive class with mean of 0.1 is far better
    than another model predicting same class with 0.8 but with mean of
    0.5

**Outcome :**

- For famous metrics like precision recall or f scores it might be a
  good idea to use those but it is not the correct method to compare
  results. For eg: Consider 2 Users, User 1 has following outputs from 2
  valid ad models ( 0.4, 0.2) here 0.4 will be shown, User 2 is having
  output as (0.6, 0.8), despite of having higher probability than User 1
  for Ad 1 it is shown to user 1 not 2 since AD 2 prob is higher for
  user 2. So cannot really rely on metrics as there are so many moving
  parts but tried to narrow down the conclusions as close as possible.

- Compare all the metrics such as RIG/RANK/AUCS/Quantile/etc while
  ensuring same distribution. If all of them shows positive result gain
  then there is high probability that our new model is predicting better
  but again it depends on various other factors also as set by MPE but
  that\'s not the scope of our problem as of now.

------------------------------------------------------------------------

##  Feature Selection

Obviously cannot reuse whole 630 data for retraining again. How to find
best features that affects the label the most. There are multiple ways
for the same with each one having its pros and cons

Correlation Matrix

Cannot Use Correlation matrix for the same reasons single metrics cannot
be selected for any conclusion. all the correlation we see will be due
to changes in majority class while features that affect minority class
will contribute very minute to general correlation.

Production Model Feature Importance

Its a good way to uniquely identify features that are helping the model
the most but it has 2 general problems

1.  Every model have different best feature so cannot guarantee a
    feature set most valid today will be great tomorrow also.

2.  Also a bad model can also produce bad feature importance scores. Due
    to reasons which we discussed earlier we cannot trust any single
    metric to compare if model is predicting poorly/badly or randomly.

WOE/IV

1.  Weight of Evidence and IV : It tells you predictive power of
    independent variable in relation to the dependent variable. Its most
    commonly used for Credit scoring/fraud detection and separates good
    from bad customers.

2.  Value of weight of evidence is considered better than one hot
    encoding

    Cons : It is mostly preferred for linear models and does not
    guarantees best features for non linear models.

Final Selection

- Check output of Correlation matrix and feature importance from old XG
  models. If most of the features are available when features are sorted
  wrt IV then we can simply choose top 50/100 features from the WOE. Its
  not guaranteed that all the features will be important to meta learner
  but due to the complexity we cannot just hard pick top 10/20 features
  and need to make sure after 10 days still most of the top features are
  used by meta learner. For eg: we can see state names in feature
  importance of old models so we cant just pick that particular state as
  it may vary daily/weekly, also we cannot select all states as not all
  of them contribute equally so its better to select top generic
  features and let the meta learner choose which one to prefer based on
  data.

- Later on we can simply change the number of features and what all
  features to select easily but we need to make sure this learner works
  in production. We can tweak it later.

------------------------------------------------------------------------

##  Results

Data

  ------------ -------- ----------
  Date         RIG XG   RIG PROD
  2022_05_27   10.37    9.54
  2022_05_28   10.48    6.01
  2022_05_29   8.78     6.16
  2022_05_30   13.53    2.33
  2022_05_31   13.53    2.33
  2022_06_01   5.44     9.20
  2022_06_02   5.11     1.11
  2022_06_03   -0.05    0.39
  2022_06_04   6.92     -0.27
  2022_06_05   5.58     0.57
  2022_06_06   7.98     4.44
  2022_06_07   10.16    8.33
  ------------ -------- ----------

  --------------- ------------ ------- ---------------- ------------------ ---------------- ------ -------
                               Model   1st Decile Sum   1st Decile Total   Average decile   RANK   RIG
  Train/Test XG   25/26        XG      203              18858              2.17             79.1   10.37
  Predictions     2022_05_27   PROD    166              18858              2.53             92.1   9.54
  Train/Test XG   26/27        XG      51               8334               1.94             18.6   10.48
  Predictions     2022_05_28   PROD    30               8334               2.76             26.5   6.01
  Train/Test XG   27/28        XG      153              19571              2.48             81     8.78
  Predictions     2022_05_29   PROD    126              19571              2.87             93.8   6.16
  Train/Test XG   28/29        XG      54               4873               1.64             12     13.53
  Predictions     2022_05_30   PROD    26               4873               3.22             23.5   2.33
  Train/Test XG   29/30        XG      44               6137               2.18             15.7   13.53
  Predictions     2022_05_31   PROD    32               6137               2.67             19.2   2.33
  Train/Test XG   30/31        XG      44               6952               2.98             27.7   5.44
  Predictions     2022_06_01   PROD    41               6952               2.48             23.1   9.20
  Train/Test XG   31/01        XG      51               10968              2.88             31.7   5.11
  Predictions     2022_06_02   PROD    26               10968              3.55             39.1   1.11
  Train/Test XG   01/02        XG      8                2956               3.83             16.1   -0.05
  Predictions     2022_06_03   PROD    9                2956               3.69             15.5   0.39
  Train/Test XG   02/03        XG      29               7901               2.81             25     6.92
  Predictions     2022_06_04   PROD    14               7901               3.87             34.4   -0.27
  Train/Test XG   03/04        XG      58               11098              2.79             37.9   5.58
  Predictions     2022_06_05   PROD    41               11098              3.67             49.9   0.57
  Train/Test XG   04/05        XG      77               13401              2.47             39.1   7.98
  Predictions     2022_06_06   PROD    53               13401              3.18             50.3   4.44
  Train/Test XG   05/06        XG      152              18924              2.16             60.8   10.16
  Predictions     2022_06_07   PROD    123              18924              2.60             73.1   8.33
  --------------- ------------ ------- ---------------- ------------------ ---------------- ------ -------

com.atlassian.chartchart:defaultLINE012false350#0055CC#23A971falsefalseverticalRIG
ComparisonRIGDATEtrueautoChartdefaultb16d79eb-c976-4d49-9c9a-f172560751dab7e1c163-fc91-4805-97b7-edcb81e2d15dcom.atlassian.chartchart:defaultLINE012false350#0055CC#23A971falsefalseverticalRIG
ComparisonRIGDATEtrueautoChartdefaultb16d79eb-c976-4d49-9c9a-f172560751dab7e1c163-fc91-4805-97b7-edcb81e2d15d

------------------------------------------------------------------------

##  Inference

1.  We can see a significant improvement in the graph but that alone is
    not enough to conclude anything.

2.  There is significant difference in the distribution of the model
    outcomes. Meta learner's distribution is slightly shifted towards 1
    this may be due to 2 reasons.

    1.  **Best Case** : Users which are more likely to click on ads are
        given better scores.

    2.  **Worst Case** : Model tries to decrease loss by slightly
        increasing prediction probability randomly.

3.  Sometimes RIG scores are really low and meta learner performs poorly
    this seems to directly relate to the lower data for that particular
    day.

4.  There were tons of assumptions since we cannot control all the
    variable outside the scope of model like those of MPE, So although
    here we can see significant improvement there is good chance that
    this might not be the case in the production.
