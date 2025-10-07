The following are findings of long term user history analysis on basis
of BLIP cluster consumption.

### The Data:

User history was collected for all unique users for **31.10.2022**

History length: 91 days-100 days (13-14 weeks)

Filters applied:

- Minimum of 10 interactions by user.

- User history length should be less than 99%ile of the data.

### Analysis:

Ratio of unique clusters watched to total clusters present.

##### Fully watched (play_duration\>=video_length)

Over a period of 100 days users have consumed about 40% of all\
secondary clusters.

Over a period of 100 days users have consumed about 11.5% of all\
primary clusters.

Shared:

Over a period of 100 days users have shared about 9% of all\
secondary clusters.

Over a period of 100 days users have shared about 6% of all\
primary clusters.

Liked:

Over a period of 100 days users have liked about 14% of all secondary
clusters.

Over a period of 100 days users have shared about 7.75% of all primary
clusters.

### Cluster Counts:

------------------------------------------------------------------------

**[[Cluster-wise counts for distinct items served, played, liked and
shared]{.underline}]{style="color: rgb(191,38,0);"}**[[:]{.underline}
]{style="color: rgb(191,38,0);"}[https://docs.google.com/spreadsheets/d/1_aIGvmwha0V4HU67useCGEJUAmrQrJrrCLJWvz6HSAQ/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1_aIGvmwha0V4HU67useCGEJUAmrQrJrrCLJWvz6HSAQ/edit?usp=sharing){card-appearance="inline"}[
]{style="color: rgb(191,38,0);"}

------------------------------------------------------------------------

**Distribution of number of clusters served to users**

### **Longest Continuous Cluster watch analysis:**

Aim of this analysis was to understand how long a user has interest in
on one topic.

The following was done to understand this for **each user**:

- Divide 91 days of user history on the basis of weeks. 1 to 13.

- Get the oldest week the user was active from, that is, how many weeks
  the user has been on the platform.

- Loop through the User history, item wise, and get the count for the
  number of ***consecutive*** weeks that the user has fully watched a
  cluster. (Drawback: If user consumed only one full video from the
  cluster in one week, it will still be counted.)

- For the user, find the longest number of consecutive weeks they
  watched **any** cluster for. Lets call this *longest_interest_period*

- For the user, find the median of the number of consecutive weeks they
  watched **any** cluster for. Lets call this *median_interest_period*

Longest_interest_period

Median_interest_period

Average value for *longest_interest_period (Excluding values for \>=13
weeks):* `4.230`

Mean values for *longest_interest_period (Excluding values for \>=13
weeks):* `3.0`

Average value for *median_interest_period (Excluding values for \>=13
weeks):* `3.055`

Mean values for *median_interest_period (Excluding values for \>=13
weeks):* `2.0`
