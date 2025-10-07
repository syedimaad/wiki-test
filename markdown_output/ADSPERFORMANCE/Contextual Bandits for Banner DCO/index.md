## **UCB (upper confidence bound):**

- The Upper Confidence Bound (UCB) algorithm is often phrased as
  \"optimism in the face of uncertainty\"

- UCB algorithm is only concerned with Upper confidence bound

- Reward of UCB is represented as following equation and overall we need
  to maximize this equation

**If we have more information about the particular user id it will more
accurately predict the corresponding banner id. So there is were
contextual bandit comes in.**

## **LINUCB DISJOINT:**

- Here we need to calculate theta

  This Equation represents normal equation which is use in place of
  gradient dataset when we have smaller no of features in the dataset

- Above equation can be represented as

  here theta is the parameter that is to be learned

- At the crux of the algorithm, we wish to find the arm with the highest
  UCB at time `t`

- The mean reward estimate of each arm (red box) and

- The corresponding upper confidence bound (blue box), where `α` is a
  hyper parameter

- The higher `α` is, the wider the confidence bounds become. Thus it
  results in a higher emphasis placed on exploration instead of
  exploitation.

**PLOTS WITH VARYING ALPHA VALUE:**

- FOR ALPHA = 1.5

  here we get the ctr value close to 15 percent as here between 200 to
  450 steps model was exploring different arms and eventually it
  increased after 450 steps.

- FOR ALPHA = 1

  here we get the ctr value close to 20 percent as here between 200 to
  500 steps model was exploring different arms and eventually it
  increased after 500 steps.

- FOR ALPHA = 0.5

  here we get the ctr value close to 42 percent as here between 200 to
  650 steps model was exploring different arms and eventually it
  increased after 650 steps.

**Here as we decreasing the value of alpha we are getting better ctr% as
decreasing the value alpha seems to give less chances for exploration
comparatively.**

**RESULTS:**

some of the predictions corresponding to user_id

## **LINUCB HYBRID:**

**How this LINUCB Hybrid is different from LINUCB DISJOINT?**

- `x_{t,a}` represents the contextual information of the new observation
  data

- `z_{t,a}` represents the combination of arm features and contextual
  attributes.

- If we removed this, the algorithm reverts back to LinUCB Disjoint.

here Z term is added and now need to maximize this equation p(t, a)

In similar form, this is once again represented by picking the arm based
on the sum of :

- The mean reward estimate of each arm using both shared and non-shared
  components (blue box). As mentioned previously, `β*` represents the
  shared components. Unlike `θ*_a`, `β*` was trained based on all time
  steps such that arms with similar attributes will tend to capture
  similar reward structure.

- The corresponding confidence bound (red box), where `α` is a hyper
  parameter.

LINUCB Implementation:

**PLOTS for LINUCB**:

- Here red line indicates the average rewards in the dataset

- So this can be also used as the evaluation metrics such that the
  cumulative rewards obtained should be above this red line which
  behaves as the threshold.

- Here we have made the plots for the varying alpha values.

**Current Issues** :

Z value in the p(t, a) function.

# Offline Evaluation of Multi-Armed Bandit Algorithms

- Replay Evaluator is the technique used for offline evaluation of
  Multi-Armed Bandit Algorithms

- Requires the larger dataset for evaluation using replay evaluator.

# Evaluation Metrics for a Bandit

- In bandit problems the metrics used is Regret which is the difference
  between the reward of the arm chosen by the algorithm and the actually
  reward

- But to measure this regret we also need to know the rewards which the
  bandit didn't choose but in real world this is not possible . So
  regret can't be considered as the good metrics.

- We can take cumulative reward as the best suitable metrics for bandit
  problems to evaluate offline.

- This is simply the cumulative sum of all the bandit's replay scores
  from the cases where a non-null score exists.

**LINK FOR THE CODE:**

[https://colab.research.google.com/drive/1qiuvXRJvxVpfen35liAIWjh23tmcEzLK?usp=sharing](https://colab.research.google.com/drive/1qiuvXRJvxVpfen35liAIWjh23tmcEzLK?usp=sharing){card-appearance="inline"}
