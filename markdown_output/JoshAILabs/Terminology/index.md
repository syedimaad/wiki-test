**Gates**:

- Gates control the influence of each expert in the final prediction by
  assigning weights.

- They determine the attention or importance given to each expert based
  on the input data.

**Experts**:

- Experts are specialized sub-models or neural networks.

- They focus on specific tasks or subsets of input features and capture
  different patterns or relationships within the data.

**Towers**:

- Towers consist of groups of experts working together.

- Each tower consists of a set of experts that share the same input
  features but specialize in different aspects or subtasks.

**Pctr**

- According to paper, Pctr is probability of article being clicked

- But, In our case Pctr is the probability of video not being skipped (
  \> 5 sec)

**Pcvr**

- According to paper, Pcvr is probability of article being read

- But, In our case Pcvr is the probability of watching more than 90%
  fraction of video

**Pctcvr**

- It is probability of video being not skipped and also watching more
  than 90% fraction of video

- Basically Pctr \* Pcvr

**QR-Embedding**

- The QR embedding trick involves taking a hash value and creating two
  embeddings from it. The first embedding is the quotient embedding,
  obtained by dividing the original hash embedding by the square root of
  the largest hash value. The second embedding is the remainder
  embedding, obtained by taking the remainder of the division.

- To create the final embedding, the quotient embedding (q) is added to
  the remainder embedding (r)

**One-hot encoding**

- One-hot encoding is a technique that converts a single categorical
  value into a sparse embedding representation where the original value
  is represented by a vector of zeros with a single element set to one

**Mean Embedding Layer**

- Mean Aggregation Embedding Layer is a layer that takes multiple
  embeddings associated with a particular feature and computes their
  average. It aggregates the embeddings by calculating the mean value,
  resulting in a single representation that captures the collective
  information from all the embeddings for that feature.

**Item Tower**

- part of student model (Two Tower Architecture) where input features
  are only item features.

**User Tower**

- part of student model (Two Tower Architecture) where input features
  are only user features.
