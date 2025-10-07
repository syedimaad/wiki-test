# Aim

The document aims to address the over-delivery issue and quantify the
severity of the problem and come up with a solution to reduce it to as
low as possible

# What is the problem

We at Ad-Tech support different types of Campaigns delivery like
Contract, paced-contract exclusive, contract exclusive, etc. Contract
exclusive and paced contracts have high priority over contracts and they
don't get stopped as soon as the campaign reaches its delivery
requirements. The problem is that the amount of money hit we take due to
this is significant. It can be seen in the CR2 reports as well. **Based
on EDA done over Feb and March month data we are over-delivering in the
order of INR 25 Lakh per month this comes to around INR 3+ crore per
year.**
[https://docs.google.com/spreadsheets/d/1NTbCHGeR5VLAWeJTy6bjjcP5N4tfKEbCVsxY9W9FwhI/edit#gid=1319379811](https://docs.google.com/spreadsheets/d/1NTbCHGeR5VLAWeJTy6bjjcP5N4tfKEbCVsxY9W9FwhI/edit#gid=1319379811){card-appearance="inline"}

**Note**: Contract Exclusive campaigns are time-bound and there is no
clear boundary for the system to stop the campaigns. Contract-Exclusive
contribution if major here can be said around 80%

# Why is it happening

Below are the reasons causing this over-delivery in respective priority:

- Currently, Contract exclusive campaigns are stopped by the system when
  the campaign\'s end date is reached. Over-delivery happens if a
  campaign reaches its delivery before the end date is reached. Ops
  usually stop such campaigns manually and we should talk to them as to
  what rationale Ad-Ops take to stop the campaign.

- Kafka Consumer delay (1) →

- Over-delivery due to concurrent requests (2)

- Over-delivery due to high incoming traffic towards the end of the
  campaign (3)

- Over-delivery due to delayed events ()

- Over-delivery due to MPE operation interval of 5 mins

# Concerns

- There are zones where the Ad is not currently configured. If a new
  campaign comes in for that zone, Ad-Ops don't have visibility into
  inventory, which can lead to misconfigured contract exclusive
  campaign. Ex: Ad-Ops don't have visibility into the auto zone.
  **Ad-Tech should provide this visibility**

# Solution

1.  Check if we are bumping up impressions towards the end of the
    campaign

2.  Paced Exclusive Campaigns we bump impressions by 20% towards the end
    of the campaign

TBA
