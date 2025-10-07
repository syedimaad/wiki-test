**CoNet: Co-occurrence neural networks for recommendation**

Paper link : <http://zhouxiuze.com/pub/conet.pdf>

**Dataset Creation:**

1.  For user U , create separate lists of items_liked and items_skipped
    (\< 2 seconds) , over a specific training window.

2.  For example :\
    User U's liked item list : \[i1 , i2, i3, i4\]

    User U's skipped item list : \[i5,i6,i7,i8\]

3.  I/p will be in the following format

  ---------- ----------- ----------- ------------
  **User**   **Item1**   **Item2**   **Target**
  U          i1          i2          1
  U          i1          i5          0
  U          i2          i6          0
  U          i3          i1          1
  ---------- ----------- ----------- ------------

3\. We can create a specific proportion of positive and negative data
for each user (1:4 , 3:5 etc).

**Architecture of Co-Net:**

- **Embedding Layer :** Embeddings of user and the two items are
  represented as Pu , Qi and Qj respectively. (using embedding layer)

- **Attention Layer** **:** This layer calculates preference of user (u)
  with respect to items i and j.

  1\. We calculate dot product scores of (u,i) and (u,j) and assign it
  to Si and Sj respectively\
  2. Now weight is calculated :\
  ai = sigmoid(Si - Sj) , aj = sigmoid(Sj - Si)\

- **Co-occurrence Layer :** Finally, the weighted sum is calculated :
  Vij = ai\*Qi + (1-ai)\*Qj\

- **Interaction Layer :** The output of this layer is some aggregation
  of Pu and Vij (concatenation , sum etc)\
  \

- **Hidden Layers :** The resultant of Interaction Layer is passed to
  hidden layers

- **Predictive Layer** : In this layer, sigmoid function is used to
  calculate the final value \[0,1\] . Binary cross-entropy loss is used

**Comparison with current ALS:**

1.  Here we are also incorporating negative sampling in the form of
    video-skips for all the users.

2.  Attention layer calculates user's preference of one item over
    another, which is a significant user-level information , not getting
    captured in ALS

3.  It can be used for both User-Item and Item-Item retrieval.

**DeepFM: A Factorization-Machine based Neural Network for CTR
Prediction**

paper link : <https://arxiv.org/pdf/1703.04247.pdf>\
\
**Dataset Creation :**

1.  User - Item pairs. Other meta features can also be added

2.  For example :\
    user's features → id , hod , dow, user_ctr etc\
    item's features → id , item_age , item_ctr etc\

**Architecture :**

- **Deep component :**\
  \
  1. For each feature , embedding layer is present\
  2. The embeddings are passed to hidden layers, followed by final
  output (y_DNN)\

- **FM component :**\
  \
  1. For each feature, embedding layer is present\
  2. Pairwise inner product is calculated with all the features\
  3. Final output is given by (y_FM)\

- final output → y = sigmoid(y_DNN + y_FM)

**Comparison with current ALS:**

1.  Meta features getting used

2.  Feature level interaction is done and is getting contributed in the
    output prediction value

Evaluation is done on real world industrial dataset and ctr improvement
is achieved. So this can be tried for our case too.
