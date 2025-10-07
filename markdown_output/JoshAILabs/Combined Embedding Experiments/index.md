### Data Extraction

From every video file

- Decord is used to extract **5** **equidistant frames**

- MoviePy(python ffmpeg wrapper) is used to extract audio at sample rate
  16000, (if multiple channels are present they are averaged) and saved
  as WAV

### Preprocessing

Video

- Resized to (224,224)

- Normalization : torchvision.transforms.Normalize(\
  mean=\[-0.48145466/0.26862954, -0.4578275/ 0.26130258,
  -0.40821073/0.27577711\],\
  std=\[1/0.26862954, 1/0.26130258, 1/0.27577711\]\
  )\
  (This normalization function is used consistently across almost all
  VIT variants and subvariants )

Audio

- ASTFeatureExtractor class from HuggingFace is used to convert the WAV
  file. This class extracts mel-filter bank features (128 mel filters),
  pads/truncates them to a fixed length and normalizes them using a mean
  and standard deviation.

### Process

The Video and Audio Features are passed through the relevant pretrained
models. They both output 768 dimensional embeddings.

We L2 normalize the embeddings individually and

- Concatenate them after that. With this we get a 1536 dimensional
  vector.

- Sum the vectors, With this we get a 768 dimensional vector.

On the Resultant (Concatenated/Summed) vector, we apply UMAP. The
following parameters have been set on UMAP:

- n_neighbors=400,

- n_components=128,

- metric=\"cosine\"

### Experiments

  --- ------------------------------------- ------------------- ------------------------------ ------------------
      **Visual Encoder**                    **Audio Encoder**   **Dimensionality Reduction**   **Type**
  1   VIT (base_patch32_224_clip_laion2b)   AST                 UMAP                           Concatenated
  2   VIT (base_patch32_224_clip_laion2b)   AST                 PCA                            Concatenated/Sum
  3   VIT (base_patch32_224_clip_laion2b)   AST                 Various UMAP variants          Concatenated/Sum
  4   VIT (base_patch32_224_clip_laion2b)   HTSAT               UMAP/PCA                       Concatenated/Sum
  5   VIT (base_patch32_224_clip_laion2b)   WHISPER             UMAP/PCA                       Concatenated/Sum
  6   BLIP                                  AST                 UMAP/PCA                       Concatenated/Sum
  7   BLIP                                  HTSAT               UMAP/PCA                       Concatenated/Sum
  8   BLIP                                  WHISPER             UMAP/PCA                       Concatenated/Sum
  --- ------------------------------------- ------------------- ------------------------------ ------------------

### Metrics

Two Tower offline metrics averaged over ( - ) using the first
experimental embeddings ({VIT (base_patch32_224_clip_laion2b) + AST}
\[Concatenated\] =\> UMAP )

  --- ---------------- --------- ----------------- --------------- --------- ------------ ------------- -------------- --------------- --------------- ---------------- ----------------- ------------------ --------------------
      **Experiment**   **auc**   **avg_prec@10**   **map_score**   **mrr**   **ndcg@5**   **ndcg@10**   **recall@5**   **recall@10**   **recall@50**   **recall@100**   **recall@gt_5**   **recall@gt_10**   **recall@all_pos**
  1   Base Line        0.647     0.655             0.696           0.217     0.699        0.732         0.715          0.75            0.81            0.86             0.624             0.631              0.624
  2   1                0.655     0.664             0.703           0.222     0.71         0.742         0.725          0.759           0.818           0.867            0.629             0.636              0.629
  3                                                                                                                                                                                                          
  --- ---------------- --------- ----------------- --------------- --------- ------------ ------------- -------------- --------------- --------------- ---------------- ----------------- ------------------ --------------------

### Architecture

 
