**Status**

1 complete [Articles in Mongodb]{.placeholder-inline-tasks}

2 incomplete [Story clustering algo]{.placeholder-inline-tasks}

3 complete [Story clustering node in
pipeline]{.placeholder-inline-tasks}

4 complete [Entity graphs]{.placeholder-inline-tasks}

5 complete [NERs extraction]{.placeholder-inline-tasks}

6 complete [TF-IDF based keyword extraction]{.placeholder-inline-tasks}

7 complete [Primary NERs]{.placeholder-inline-tasks}

8 complete [Secondary NERs]{.placeholder-inline-tasks}

9 complete [Web app integration \[In
Progress\]]{.placeholder-inline-tasks}

# Data Enriching Pipeline

- It's going to be batch process run periodically for new added articles

- NER graphs - Entities connected by semantic relationships

- NERs extraction node - NERs pipelines for English and Indic languages

1.  **Primary Relations**Extract entities from Header Keywords. If there
    is a direct relationship between two entities, then that
    relationship is added to the set of primary relations. 

2.  **Secondary Relations**If two entities are connected by a path of
    two edges then that relationship is added to the set of secondary
    relationships.If an entity does not have any relationship with any
    other entity found in keywords then we use secondary keywords to
    filter relationships and add it to the set of secondary relations.

3.  **TF-IDF based keyword extraction on story level**Document is
    defined as a combined story of perspective articles. And TDF-IDF is
    applied to find top N keywords filtered at article level

    1.  Heading keyword

    2.  Chunk 1 keyword

4.  **Primary NERs**NERs found in Headers

5.  **Secondary NERs**NERs found in Chunk1

# API

\
10.55.0.199:8017/docs\

# [Demo Web App](http://10.55.0.199:8021)
