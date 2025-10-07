# List of Models Active - Live

- SPARK_HI_JTLR11 - CTR \< 2 sec - with Categorical Feature Encoding and
  with undersampling 3

- SPARK_HI_JTLR12 - CTR \>= 10 sec - with Categorical Feature Encoding
  and with undersampling 1

- SPARK_HI_JTLR13 - CTR \>= 7 sec - with Categorical Feature Encoding
  and with undersampling 1

- SPARK_HI_JTLR14 - CTR \< 5 sec - with Categorical Feature Encoding and
  with undersampling 1

- SPARK_HI_JPLR23 - PCC 85 % - with Categorical Feature Encoding and
  with undersampling 1

- SPARK_HI_JSHLR24 - Only Share with undersampling 1 and with
  Categorical Feature Encoding

- SPARK_HI_JLKLR23 - Only Like with undersampling 1 and with Categorical
  Feature Encoding

- ~~SPARK_HI_JPLR21~~

- SPARK_HI_JPLR12

- SPARK_HI_JSHLR1

- ~~SPARK_HI_JLKLR1~~

- SPARK_EN_JPLR9

- SPARK_TE_JPLR9

- SPARK_TA_JPLR9

- SPARK_MR_JPLR9

- SPARK_ML_JPLR9

- SPARK_GU_JPLR9

- SPARK_KN_JPLR9

- SPARK_BN_JPLR9

- SPARK_BH_JPLR9

- SPARK_PA_JPLR9

- SPARK_OR_JPLR9

## Input Paths for each model

- **SPARK_HI_JPLR12 - s3://josh-lr/history-filter-events-50/hi**

- **SPARK_HI_JPLR21 - s3://josh-lr/josh-label-filter-events/hi**

- **SPARK_HI_JSHLR1 - s3://josh-lr/sh-events/hi**

- SPARK_HI_JLKLR1 - s3://josh-lr/lk-events/en

- SPARK_EN_JPLR9 - s3://josh-lr/josh-cold-start-events/en

- SPARK_TE_JPLR9 - s3://josh-lr/josh-cold-start-events/te

- **SPARK_TA_JPLR9 - s3://josh-lr/josh-cold-start-events/ta**

- **SPARK_MR_JPLR9 - s3://josh-lr/josh-cold-start-events/mr**

- **SPARK_ML_JPLR9 - s3://josh-lr/josh-cold-start-events/ml**

- SPARK_GU_JPLR9 - s3://josh-lr/josh-cold-start-events/gu

- **SPARK_KN_JPLR9 - s3://josh-lr/josh-cold-start-events/kn**

- **SPARK_BN_JPLR9 - s3://josh-lr/josh-cold-start-events/bn**

- SPARK_BH_JPLR9 - s3://josh-lr/josh-cold-start-events/bh

- **SPARK_PA_JPLR9 - s3://josh-lr/josh-cold-start-events/pa**

- **SPARK_OR_JPLR9 - s3://josh-lr/josh-cold-start-events/or**

## List of DAGs with Output Directory

s3://josh-lr/[josh-label-filter-events](https://s3.console.aws.amazon.com/s3/buckets/josh-lr?region=ap-south-1&prefix=josh-label-filter-events/&showversions=false) -
JPLR23

s3://josh-lr/[[josh-label-lk-events/]{.underline}](https://s3.console.aws.amazon.com/s3/buckets/josh-lr?region=ap-south-1&prefix=josh-label-lk-events/&showversions=false) -
JLKLR21, JLKLR22, JLKR23

s3://josh-lr/[josh-label-sh-events/](https://s3.console.aws.amazon.com/s3/buckets/josh-lr?region=ap-south-1&prefix=josh-label-sh-events/&showversions=false) -
JSHLR21, JSHLR23, JSHLR24

s3://josh-lr/[josh-label-time-lt2s-events/](https://s3.console.aws.amazon.com/s3/buckets/josh-lr?region=ap-south-1&prefix=josh-label-time-lt2s-events/&showversions=false) -
JTLR1, JTLR11\
s3://josh-lr/[josh-label-time-gteq-10s-events/](https://s3.console.aws.amazon.com/s3/buckets/josh-lr?region=ap-south-1&prefix=josh-label-time-gteq-10s-events/&showversions=false) -
JTLR2, JTLR12\
s3://josh-lr/[josh-label-time-gteq-7s-events/](https://s3.console.aws.amazon.com/s3/buckets/josh-lr?region=ap-south-1&prefix=josh-label-time-gteq-7s-events/&showversions=false) -
JTLR3, JTLR13

s3://josh-lr/[josh-label-time-lt5s-events/](https://s3.console.aws.amazon.com/s3/buckets/josh-lr?region=ap-south-1&prefix=josh-label-time-lt5s-events/&showversions=false) -
JTLR4, JTLR14

**~~lr-event-gen-cold-start-dag~~**\
~~s3://josh-lr/josh-cold-start-events~~

**lr-event-gen-dag**\
s3://josh-lr/josh-events\
s3://josh-lr/josh-cold-start-events\
~~s3://josh-lr/josh-cold-start-user-prim-lang-events~~

**lr-event-gen-history-filter-dag**\
~~s3://josh-lr/history-filter-events-40~~\
s3://josh-lr/history-filter-events-50

**lr-event-gen-labeled-filter**\
s3://josh-lr/josh-label-filter-events

**lr-event-gen-lk-sh-dw-dag**\
~~s3://josh-lr/lk-events~~\
s3://josh-lr/sh-events\
~~s3://josh-lr/lk-events-history-50~~\
~~s3://josh-lr/sh-events-history-50~~

**~~lr-event-lk-sh-dw-threshold-filter-runner-dag~~**\
~~s3://josh-lr/events/lk-2-lk-events~~\
~~s3://josh-lr/events/lk-3-lk-events~~\
~~s3://josh-lr/events/sh-2-sh-events~~\
~~s3://josh-lr/events/sh-3-sh-events~~

\
\
\
