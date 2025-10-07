if you can fill in this with the approach and results.\
\
Basically take all of the non-leaky features - pass through some
dimensionality reduction - (PCA, Autoencoder) and then use that vector
as a feature in scala Xgboost model.

\

additional to all the features or only that vector.

\

2 things to test for : 

1.  Learning co-dependence of vectors may be.

2.  Reduction in training time? 

Train 2 models for a campaign with very basic pca model

Save these models as well\
\
<http://perf.ads.jupyter2-n3.dailyhunt.in/groot/notebooks/notebooks/nitin/tasks/userProfileDim/PCA.ipynb>

------------------------------------------------------------------------

Plan:

- Start with small batch of data and try to see if Autoencoder/PCA
  works.

- For Evaluation run test on columns before and after dimensionality
  reduction and measure difference in RIG/RANK

- Try using the reduced dimension embedding as additional features or
  maybe replacement of old features whichever works the best.

- Other algos to try : LDA/UMAP/TSNE/PCA

- Initially to start try using ig columns.. there are more than 270 ig
  columns.

- Avoid using leaky features
