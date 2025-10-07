**Problem Statement:**\
1. To understand whether users are forming long term clusters of glam
content by lthm, such that glam can be re-introduced for them

2\. If the above is yes, then are we able to retrieve lower glam level
(3, 4) from higher glam level (5, 7) from clusters, because now we have
stopped 5th and 7th glam level serving

**Approach:**

*"End date taken for lthm is 20th April, and for KNN is 10th June 2023"*

1.  Take lthm clusters (items) and filter those clients who have minimum
    1 event and glam/total_videos ratio more than 0.1.

2.  Take 1000 videos from each glam level from lthm_clusters and do knn
    search on blip embedding to get top 100 candidates. See the
    distribution corresponding to each glam level.

**Results:**

1.  Out of 1 lakh clients, `46288` clients satisfied the above
    condition, so if scaled to all clients (1.3 m) the ratio will come
    out to be approx 0.46.

2.  Retrieved candidates having 3rd or 4th glam level:

    1.  3rd glam level → 0.64

    2.  4th glam level → 0.61

    3.  5th glam_level → 0.31

    4.  7th glam_level → 0.68

**Conclusion:**

There are a good amount of clients having glam in lthm clusters, and
also for those glam we are able to retrieve lower glam level from
current index. Hence, this can be integrated in the pipeline to serve
glamour to those clients again.

**Analysis Notebook Link:**\
<http://10.10.38.252:8890/notebooks/work-with-dinesh/theme_analysis_glamour.ipynb>
