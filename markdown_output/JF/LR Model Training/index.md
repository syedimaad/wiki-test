## Introduction to Model Training:

**FLOW**: Data from event gen → model training job → model (a file of
number arrays)

We are using LR Model : it is a predictive model which is used to
predict if a user X is shown with video Y will the user X like it or not
(1/0) but LR gives a probability score (which is in between 0 -1) and
based on a threshold we define if the value crosses threshold it will be
1 else 0.

### Training:

step 1: take the event stream which we have created
s3://josh-lr/\<path_toevents_folder\>/\<language_code\> - this is the
input for the job

step 2: we need create some config files for model training job to pick
up and start executing

step 3: we need to copy these config files to s3 and also the new code
jars to s3

step 4: run the spark streaming job

### How LR works

**user feature vector** → constructed out of user profile (historical
activity of a user - what kind of videos he watched, videos he liked..
etc)

**item feature vector** → constructed the metadata of a particular item,
what kind of video it is.

**event feature vector** → a video played event characteristics → what
was the time of the day, day of the week, festival, the event currently,
happening. (cross of user and item) → input data to our model

**event feature vector**: \[\....0, 1, 0.8, \...\...\...\...\] =\>
100000 length of array\
**user feature vector**: \[\...\...., 0.1, 1, 23, 0.9, \...\...\] =\>
100000 length of array\
**item feature vector**: \[...., 0, 1, 23, 0.9, \...\...\] -\> 100000
length of array\
per event, we process all these feature vectors

for all events loop { result = result \* LR(user_feature_vector,
event_feature_vector, item_feature_vector) }

what is result? result is a model : \[...., 0, 12, 6, 0.9, \...\...\]
=\> 100000 length of array\
At every 1 hr, we dump the current variable data of result, that will be
our model

### Deployment

changes to spark-submit command are

- jar version change

- model version change

- \--inputPath change to whatever we need

LR training cluster master IP 10.10.44.47

ssh -i ugc-prod.pem hadoop@10.10.44.47

download all the jars from S3 to /home/hadoop/ctr_predict/lib/\
aws s3 cp s3://josh-lr/ctr_predict/jars/JPLR11/ . ----recursive\
Path of JARs in S3 s3://josh-lr/ctr_predict/jars/\<version\>/\
Path of config files in S3
s3://josh-lr/ctr_predict/metadata/SPARK/HI/\<version\>/\
\
Projects:

ctr_metadata → config for the LR Model

ctr_prediction → even gen spark, processor

### Feature Vectors 1234567829

1, 2, 3, 4, 5

\[0.6, 0.4, ..\]

0 - hashtag #comedy

1 - hashtag #funny

2 - location = delhi

3 - hashtag #dance

user_fv

-\> previous he has seen #comedy videos, we will populate at \@th
position (some non zero value is populated)\
60% of videos he has seen are comedy

at 1st position we may put 0.6

40% of videos he has seen are funny

at 2nd position, we may put 0.4

overall we are encoding user behavior in the past into a numerical array
because our LR algorithm only understands numerical\
arrays, these arrays are more specifically called feature vectors

this framework can be applied to all of the feature vectors

user, event, item

each feature vector can have a different config of positions to feature
mapping

feature type -\> feature

feature1, feature2, ..

0, 1, 2, 3, 4, 5, 6, 7 ... (the feature1 can be at position 0 and
feature2 can be at position 7, the feature1 can be defined by 6 values
giving the model a deeper understanding of the feature)

feature 1 → hashtag #comedy → overall 30 videos have been seen until now
in the past

0 → how many videos he has seen over 10s

1 → how many videos he has seen less than 10s

2 → how many videos has seen over 90% of the video

3 → how many videos has seen over 50% of the video

4 → how many videos he has liked (pressed like button)

5 → how many videos he has shared\

**What will be the value at position 0 ? how do we get that ?**\
position 0 data stores → how many videos he has seen over 10s\
Let's say, out of 30 videos in hashtag #comedy he has seen 15 videos
over 10s in the past in his lifetime of activity\
So, Position - 0 -\> value - 15\
Instead of putting 15, we run this value against a function before
putting it here zscore(15) which is in b/w 0 to 1\
So, for all users in our universe of the app ecosystem\
we are going to get the value of their activity at position 0

arr = \[\] for all users loop { arr.append(value at position 0 - for
hashtag #comedy number of videos they have seen over 10s) }

\[5 , 4, ...., 8 ,12\]\
mean of this array -\> M\
standard deviation of this array -\> D

zscore(15) { value = (15 - M) / D }

whatever the value is as the output of ***zscore***, we are going to
populate that into our position 0\
.. same thing we are going to do for all features\
? what is the use of zscore → it makes the value for all users between 0
to 1, making all the values on the same scale\
*for eg, one user may have 1234 as the count for a position 0, one user
might have just 10,*

there is a huge difference in the scale of the values, value 2 is 100X
more, we need to bring down the scale, ***zscore*** is a good value to
compress everything to a uniform scale between 0 to 1.\
In any machine learning model the scale of input numbers should be
finite so we do this exercise.

Looking forward for all documentation on lr training including the link
of KT videos

**Sub-Section Links:**

1
