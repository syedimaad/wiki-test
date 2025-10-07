**References :**

Distillation based Multi-task Learning: A Candidate Generation Model for
Improving Reading Duration <https://arxiv.org/pdf/2102.07142.pdf>

Modelling Task Relationships in Multi-task Learning with Multi-gate
Mixture-of-Experts\
<https://dl.acm.org/doi/pdf/10.1145/3219819.3220007>

### Probable Tasks (output columns)

- p_pcc85 =\> watch_fraction \>= 85%

- pcc90 =\> watch_fraction \>= 90%

- wtg =\> watch time \> avg watch time of item across all user in past 7
  days.

- p_like =\> liked or not

- p_shared =\> shared or not

- gt_10sec =\> video watch time\>10sec

 

## **Proposed Architecture**

**Approach 1:**

 

Setup:

1.  Input -- User and item features, like dow, hod, content_embedding,
    item_meta, creator_meta, etc.

2.  Expert -- \[ANN architecture with dense layers having size 512, 248,
    128\] X 2

3.  Gate -- \[ANN architecture with softmax activation\] X 4

4.  ANN -- \[ANN having same dense layers as Expert but having item
    feature and user feature as input explicitly\] X 2

5.  Tower -- \[It is another set of dense layers having size 512, 248,
    128, 32, 8, 1\] X 2

6.  Output -- The task on top of which we will be training our model on
    \[gt_10sec,pcc90\]

7.  Loss functions : Binary cross entropy

8.  input to towers : concat(Gij\*Ej) \[ where j = range(0,2) and i =
    range(0,4)\]

 

Description:

The architecture is the same as MMOE, but having two additional elements
of ANN+Gate, which explicitly takes either user or item feature and
eventually generates softmax scores which is later multiplied by experts
of each task. Basically each item and user ANN+Gate is multiplied with
each task.

 

 

 

**Approach** **2** :

**Teacher-Student Model**

**Teacher:**

Input : \[user features, item_features \] → take concatenated user and
item features

experts : \[ANN architecture with hidden layers (1024,512,256)\] X 2

gates : \[ANN architecture with softmax activation\] X 2

Towers : \[ANN architecture with hidden layers (256,128,64,32,1)

Main tasks : \[gt10_sec,pcc90\] ( other tasks → \[mean watch time, loop,
etc (play around it)\])

Here assume \[ Pctr : gt_10_sec and Pcvr : pcc90 \]

- loss function for Pctr : binary cross entropy

- Pctcvr = Pctr\*Pcvr

- loss function for Pctcvr : binary cross entropy

final loss function for teacher model : w1\*Pctcvr + w2\*Pctr \[ w1,w2
are tunable weights\]

**Student**

Input : User and Item features passed through user tower and item tower

Towers : \[ANN architecture with hidden layers (512,256,64,32)\] X 2

Main Task : \[ pcc90 \]

student loss function is directly included in kl divergence loss

**final loss : teacher loss+student loss.**
