[Contents]{.underline}

1.  Explore the new table 

2.  New Datagen job

3.  Two-tower training (might require changes based on generated
    data/results)

4.  Create scann model for item vectors

5.  generating user vectors from the model itself

6.  (or) generating user vectors by handling the api service

**Explore the new table **

s3://josh-reco-ml-dataset/snapshot/daily_with_recent_k/prod_v4/

- All Prod-p90 Existing columns are present

- Pcc98,likes,shares,skips,loops are extra columns

- Pcc98 as positive history and skips as negative history

- Pcc98 : {mean : 187,median : 9} of around 10k events

- Skips : {mean : 165,median : 64} of around 10k events

**New Datagen job**

- Need latest 100 items of pcc98 and skips by slicing, if not available
  set the rest to 0

- Need to check if any other changes are required \[change the code acc
  to user model strategy\].

**generating user vectors from the model itself**

- Datagen should generate simple direct raw features for user features

  - hod (Hour of the Day)

  - dow (Day of the Week)

  - handset_maker (maker of the mobile,without cleaning)

  - Pos history( just past 100 pcc_98 items)

  - Neg history( just past 100 skip items)

  - User_overall_short_like_ctr

  - User_overall_short_share_ctr

  - User_overall_short_download_ctr

  - User_overall_mid_ctr

  - User_overall_mid_like_ctr

  - User_overall_mid_share_ctr

  - User_overall_mid_download_ctr

  - User_overall_life_ctr

  - User_overall_life_like_ctr

  - User_overall_life_share_ctr

  - User_overall_life_download_ctr

- Need to add preprocessing layers and  mean layers in user tower code
  itself 

Handset maker cleaning and mapping

concatenating user-meta-features as list

Mean of item-ids after mapping to their embeddings

- And save user tower model as separate model \[inputs : raw features,
  output : user vector\]

**Create scann model for item vectors**

- After training save item vectors scann model

**Training**

**Inference**
