`parquet_updater.sh   runs following `

1.  embeddings_joiner.py \--\> -\> Creates a joined embeddings from
    latest embeddings files available 

2.  user_profile_extraction.py \--\> Fetches data from mongo and updates
    in redis and stores in parquet for 2-days active users (feature set
    is non-embedding features)            

3.  dau_embeddings_joiner.py -\> Generates parquet file with all
    features including (embedding features) for (2-day active users +
    MAU users with embeddings in old user parquet)

4.  ProfileUpdateEntry.Scala -\>  Updates MAU file with new data
    extracted in step3 

5.  `embedding_updater.py ->  reads userProfileV2.parquet file and updates embeddings features`

6.  `Here MAU ->  35 days`

7.  format for fields with encoding_type = \"embeddings\"\
    id -\> { d:\"0.2,0.1,\...\...\...\", i:1} , where d is data and i =
    1 if imputed
