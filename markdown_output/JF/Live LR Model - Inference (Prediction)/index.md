**Jars location in s3:**

- s3://josh-lr/artifacts/lr-scorer-v2/jars/cassandra_jar_v3/

**Branches:**

- for 6.0.10 versioned jars :
  *master-6.0.10-cassandra-changes-v2-astra-db-changes*

- for 7.2.0 versioned jars : *master-7.1.0-merge-lr-pred-exp5-changes*

### DAG : josh-lr-pred-daily-hi-fp-redis-exp (lr_pred_hi_redis_fp_v3.py)

jelr5_hi - models: JPLR23 JTLR11 JTLR12 JTLR13 JTLR14 JLKLR23 JSHLR24
(jar versioned 7.2.0)

### DAG : josh-lr-pred-daily-other-lang-fp-redis-exp (lr_pred_other_lang_redis_fp_jelr5.py)

jelr5_en - models: JPLR23 JTLR11 JTLR12 JTLR13 JTLR14 JLKLR23 JSHLR24
(jar versioned 7.2.0)\
jelr5_ta - models: JPLR23 JTLR11 JTLR12 JTLR13 JTLR14 JLKLR23 JSHLR24
(jar versioned 7.2.0)\
jelr5_te - models: JPLR23 JTLR11 JTLR12 JTLR13 JTLR14 JLKLR23 JSHLR24
(jar versioned 7.2.0)\
jelr5_bh - models: JPLR23 JTLR11 JTLR12 JTLR13 JTLR14 JLKLR23 JSHLR24
(jar versioned 7.2.0)

### DAG : josh-lr-pred-daily-hi-like-share-ctr-redis (lr_pred_hi_like_share_ctr_test_redis_v2)

jplr12_hi - jar versioned 6.0.10\
jshlr1_hi - jar versioned 6.0.10\
jelr1_hi - jar versioned 6.0.10

### DAG : josh-lr-pred-other-lang-ctr-redis (lr_pred_daily_other_lang_ctr_test_redis_v2.py)

jplr9_en - jar versioned 6.0.10\
jplr9_te - jar versioned 6.0.10\
jplr9_ta - jar versioned 6.0.10\
jplr9_kn - jar versioned 6.0.10\
jplr9_bn - jar versioned 6.0.10\
jplr9_gu - jar versioned 6.0.10\
jplr9_mr - jar versioned 6.0.10\
jplr9_ml - jar versioned 6.0.10\
jplr9_bh - jar versioned 6.0.10\
jplr9_pa - jar versioned 6.0.10\
jplr9_or - jar versioned 6.0.10

### DAG : josh-lr-pred-other-lang-share-redis (lr_pred_daily_other_lang_share_redis_v2.py)

jplr9_en - jar versioned 6.0.10\
jplr9_ta\
jplr9_te\
jplr9_ml\
jplr9_mr\
jplr9_kn\
jplr9_gu\
jplr9_bn\
jplr9_bh\
jplr9_pa

### DAG : josh-lr-pred-daily-ctr-redis-fp (lr_pred_daily_redis_fp_v2_redis_v2.py)

jplr12_fp_hi - jar versioned 6.0.10\
jplr9_fp_en - jar versioned 6.0.10\
jplr9_fp_ta\
jplr9_fp_te\
jplr9_fp_ml\
jplr9_fp_mr\
jplr9_fp_kn\
jplr9_fp_bh\
jplr9_fp_bn\
jplr9_fp_gu\
jplr9_fp_pa
