# **Problem**

Within an OI, there are contract campaigns that meet its OI requirement
even before the OI ends. This leads to a loss of ad impressions for good
users that might come in the remaining part of the OI. Can we leverage
that somehow and still how Ad to the good users even if the requirement
for the OI is met.

**Note**: We should make sure that over-delivery should not be
significant with the proposed solution.

# Solution

## **Approach 1**

current_priority_factor → .5

new_priority_factor after delivery is met within OI → .01

## **Approach 2**

new_priority_factor after delivery is met within OI →
**current_priority_factor \* .5** (**Tunable parameter**, should be part
of the central config so that it needs can be changed in the database
and AdEngine release is not needed)

**Note**: Even if over-delivery happens, it would be happening with the
good users

# **Impact**

It will have a positive impact on performance for those campaigns which
get delivered within OI. We have a lot of such campaigns.

# **Changes required**

**AdEngine:**

TBA

**Ranking:**

TBA
