# Paper

<https://dl.acm.org/doi/abs/10.1145/3394486.3403370>

or

<https://sci-hub.se/10.1145/3394486.3403370>

# Overview

The SimClusters system consists of two stages

## Stage 1: Community Discovery or User Interest Representations Generation

- In this, bipartite communities from user-user graph will be discovered
  at scale, resulting in learning sparse, non-negative representations
  for users. This output is referred as "**User Interest
  Representations**"

- Firstly the whole user-user-follow directed graph is reconstructed
  into a bipartite graph which contains two sets of users named L set
  and R set, with edges show follow relationships from L to R set

- R set contain users who are the most followed or infuencers or usually
  the top most users of the platform

- L set contains all the remaining users

- Then the following three step process is performed

### Similarity Graph of Right Nodes

- "right projection" of the bipartite graph is calculated which is done
  by calculating the similarity between the nodes in the right partition
  of the bipartite graph based on their incoming edges, and then form a
  weighted, undirected graph consisting only of the nodes in the right
  partition

### Communities of Right Nodes

- communities from the above similarity graph is formed, using a novel
  neighborhood-based

  sampling algorithm named "**Neighborhood-aware Metropolis Hastings**".
  From this step, an r\*k matrix is formed which is the representation
  of communities for R set of users, where k is a hyperparameter of
  communities required to form and r is the number of users in R set

### Communities of Left Nodes

- assigning of nodes from the L set to the communities discovered in the
  previous step by multiplying adjacency matrix of size l\*r with above
  r\*k matrix to form l\*k matrix which is the target representation of
  L set of users, where k is a hyperparameter of communities required to
  form and r is the number of users in R set and l is the number of
  users in L set

Finally, we have **(l+r)\*k matrix** which is the representation for
both L & R set of users w.r.t top communities. This is further referred
as U

## Stage 2: Item Representations

- This stage computes representations for different items, such as
  Tweets, Hashtags, or users (videos incase of Josh) - which can be the
  targets for different recommendation problems

- Along with the user interest representations U from Stage 1, this
  stage also relies on a user--item bipartite graph that is formed from
  historical or on-going user engagements with those items on the
  platform

- general framework is to compute an item's representation by
  aggregating the representations of all the users who engaged with it,
  i.e., the representation for item 𝑗 is\
  W(𝑗) = 𝑎𝑔𝑔𝑟𝑒𝑔𝑎𝑡𝑒 ({U(𝑢), ∀𝑢 ∈ N (𝑗)}),\
  where N (𝑗) denotes all the users who engaged with item 𝑗 in the
  corresponding user--item bipartite graph, and W(𝑗) and U(𝑢) are both
  vectors

- The 𝑎𝑔𝑔𝑟𝑒𝑔𝑎𝑡𝑒 function can be chosen based on different applications,
  and can also be learned from a specific supervised task. Incase of
  twitter, they used a relatively simple, interpretable 𝑎𝑔𝑔𝑟𝑒𝑔𝑎𝑡𝑒
  function with the goal that W(𝑗, 𝑐) can be interpreted as the level of
  interest an average user of the community 𝑐 currently has in this item
  j which is a "exponentially time-decayed average" based algorithm

- Further, two views or key-value objects are generated in both cases of
  User and Item representations named R and C. The first view is R, and
  R (𝑗) tracks the top communities for the item 𝑗 or a user j. The
  second view is C, and C (𝑐) tracks the top items/users for the
  community c

## Candidate Generation and Candidate Ranking

- For a random user u, the following are fetched

  - U(u) which is the user interest representation of the user u which
    is a subset of U from stage 1

  - Top communities from C of user u

  - Top items from R of items from the previously fetched top
    communities. Let is be Items

  - W(Items) which is the item representation of the items which is a
    subset of W from stage 2

- The items are basically possible candidates for the user u

- Compute dot product or cosine similarity between U(u) vector and
  W(items) matrix to get scaler values which can be sorted to get
  ranking of Items

# Analysis

## Josh Item-User watch history intersection

- Brief: Intersection of users who have watched two random items for a
  period of certain days

- Reason: To find any impact on items by active users or most common
  users on the platform

- Samples

  - 8k random items served on 20230410 with views ranging between
    20230408-10

  - 15k random hindi items served on 20230405 with views ranging between
    20230401-05

- **Observation**: Very less or in fact negligible common users among
  items

# Task Tracker

+------------------+------------------+------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Task**         | **Brief**        | **Status** | **Result**                                                                                                                                                                                                                                   |
+------------------+------------------+------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Setting up of    | cloning          | Done       | jar files                                                                                                                                                                                                                                    |
| twitter sbf      | twitter's sbf    |            |                                                                                                                                                                                                                                              |
| codebase         | repo and         |            |                                                                                                                                                                                                                                              |
|                  | building package |            |                                                                                                                                                                                                                                              |
|                  | with maven       |            |                                                                                                                                                                                                                                              |
+------------------+------------------+------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Josh             | poc of josh      | Done       | majority of the users fall under single community and num-communities fall to single digits with few users fall under the remaining communities                                                                                              |
| user-user-follow | users follow     |            |                                                                                                                                                                                                                                              |
| graph to         | relationship     |            |                                                                                                                                                                                                                                              |
| communities      | logged for a     |            |                                                                                                                                                                                                                                              |
|                  | sample period    |            |                                                                                                                                                                                                                                              |
|                  | (20230401-19)    |            |                                                                                                                                                                                                                                              |
+------------------+------------------+------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Josh user-user   | analysis of      | Done       | 99.8 percentile of users/ creators are having below 100 followers & 99.6 percentile of users follow atleast 100 users/creators\                                                                                                              |
| follow stats     | users follow     |            |                                                                                                                                                                                                                                              |
|                  | graph for the    |            |                                                                                                                                                                                                                                              |
|                  | follow events    |            |                                                                                                                                                                                                                                              |
|                  | logged for a     |            |                                                                                                                                                                                                                                              |
|                  | sample period    |            |                                                                                                                                                                                                                                              |
|                  | (20230401-19)    |            |                                                                                                                                                                                                                                              |
+------------------+------------------+------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| User-Creator     | analysis of      | Done       | all the creators came under single community                                                                                                                                                                                                 |
| like             | users creators   |            |                                                                                                                                                                                                                                              |
| interactions     | like graph for   |            |                                                                                                                                                                                                                                              |
|                  | the interactions |            |                                                                                                                                                                                                                                              |
|                  | logged for a     |            |                                                                                                                                                                                                                                              |
|                  | sample period    |            |                                                                                                                                                                                                                                              |
|                  | (20230401-15)    |            |                                                                                                                                                                                                                                              |
+------------------+------------------+------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| EDA:             | Understanding    | Done       | Basic EDA Completed. Link:                                                                                                                                                                                                                   |
|                  | users - blip     |            | [https://docs.google.com/spreadsheets/d/1a0LwSGAji2LtnshtQf6dMqlVQ0v36EYjMl0uxdg_AnE/edit#gid=1533888972](https://docs.google.com/spreadsheets/d/1a0LwSGAji2LtnshtQf6dMqlVQ0v36EYjMl0uxdg_AnE/edit#gid=1533888972){card-appearance="inline"} |
|                  | cluster affinity |            |                                                                                                                                                                                                                                              |
|                  |                  |            | At high level, it looks like users tend to follow creators across multiple topics( Blip clusters) and "like" content from different clusters. There's no cluster which dominates users share across follow & likes.                          |
|                  | - Use blip       |            |                                                                                                                                                                                                                                              |
|                  |   subcluster     |            |                                                                                                                                                                                                                                              |
|                  |                  |            |                                                                                                                                                                                                                                              |
|                  | - Check the      |            |                                                                                                                                                                                                                                              |
|                  |   coverage of    |            |                                                                                                                                                                                                                                              |
|                  |   followers (    |            |                                                                                                                                                                                                                                              |
|                  |   after          |            |                                                                                                                                                                                                                                              |
|                  |   filtering      |            |                                                                                                                                                                                                                                              |
|                  |   creators)      |            |                                                                                                                                                                                                                                              |
|                  |                  |            |                                                                                                                                                                                                                                              |
|                  | - Threshold for  |            |                                                                                                                                                                                                                                              |
|                  |   creators       |            |                                                                                                                                                                                                                                              |
|                  |   within each    |            |                                                                                                                                                                                                                                              |
|                  |   clusters       |            |                                                                                                                                                                                                                                              |
|                  |                  |            |                                                                                                                                                                                                                                              |
|                  | - Use Likes as   |            |                                                                                                                                                                                                                                              |
|                  |   affinity       |            |                                                                                                                                                                                                                                              |
|                  |   metric         |            |                                                                                                                                                                                                                                              |
+------------------+------------------+------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
