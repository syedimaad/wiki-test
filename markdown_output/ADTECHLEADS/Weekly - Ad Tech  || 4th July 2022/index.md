# **AdEngine**

#### [Video Ads & Field asks]{style="color: rgb(191,38,0);"}

Dailyhunt X Sportrecs - Ready to launch

Video Ads on Web Item - Ready

HTML Polls banner on Josh - Live

Disabled Amazon SDK for IOS and MENA

### [Network Integration ]{style="color: rgb(191,38,0);"}

Vuukle web/S2S integration - Live

Dailyhunt and AdPushup - WAP Integration - Live

Ad Networks for MENA - AdUnit ID creation and siteID creation -
Nimisha/Satyajit

Ad Network integration for Adgebra - S2S Integration with new API end
points - In Progress

### [App Release ]{style="color: rgb(191,38,0);"}

**[DH 19.0.x Milestone2]{style="color: rgb(76,154,255);"}**[
]{style="color: rgb(76,154,255);"} - Depriorized as we prioritise UI/UX
revamp 20.x

- ~~Dedup~~

- ~~Image Splash~~

- Stick Notification Ad

- ~~Enhance consistancy of Impression becon firing~~

- Traffic Header Addition for all internal API calls - SysAdmin request

- EG support for Web topic

- ~~Headline CTA overlay for All ads~~

- ~~Prefetch logic for OSV Ads~~

- ~~RoadBlock campaign - Prefetch and cache Ads - P2~~

**[DH 19.0.x Milestone1]{style="color: rgb(76,154,255);"}** - Ready to
be pushed \|\| BC cleared

- chunk1 storypage Ad

- Error beacon for VDO instream/outstream skip button inconsistency

- Video revamp - video-storypage Ad

- VMAP Flow Change to support sequential instream Ads

**[Josh R12B]{style="color: rgb(76,154,255);"}** - Pushed live

### [Misc]{style="color: rgb(191,38,0);"}

[https://evp.atlassian.net/wiki/spaces/NHADSPLTL/pages/109609309/Evergreen+Ads+-+Protocol+V1#Points-to-remember](https://evp.atlassian.net/wiki/spaces/NHADSPLTL/pages/109609309/Evergreen+Ads+-+Protocol+V1#Points-to-remember){card-appearance="inline"} -
Added FAQ

[widget.dailyhunt.in](http://widget.dailyhunt.in) migrating from NM to
GCS Bucket/Akamai CDN

# Perf

- The Shoppable ML models pipeline is ready. We plan to close the API
  side of things and make things accio compatible as decided by mid-next
  week. We are blocked the catalog ingestion pipeline on the Amazon side

- Location IP training is complete, we have tuned Accuracy and Coverage.
  We plan to go Live with limited traffic (1%) by next week Monday
  11-July-2022. We will be exposing confidence scores as well for the
  detected location

- Multi-arm bandit for Banner Selection is live for 25% of the requests.

# Daedalus

- Operations -

  - Dashboard to view all campaign/banner fields

  - Enable order unlock capability for AdOps

  - Bulk upload of client IDs in sub-targeting

  - New banner for video HTML

- Integrate new Insta-mojo account to enable self-serve payments

- Product -

  - New Poll template

  - Change minimum version targeting for amazon SDK creatives -

    - Android - 18.7

    - iOS - Disabled

  - Josh delivery changes

    - Remove all hardcoded FC for Josh

    - Allow contract-X for Shoppable ads

- Creator Commerce -

  - Offline sync with DJB, Amazon, Optimise is active

  - Ads-attached call integrated from Daedalus

- Reporting -

  - "Send Mail" Option added on revenue monitor - as sometimes failed
    due to network fluctuations

  - Introduce Billing From field for Billing groups & integrate with
    revenue monitor

  - CR6 & CR6b - Add lead ID, lead creation date

  - CR report for Josh and DH combined - ETA: today

  - Reporting - MENA CR

    - CR1 (direct sales only) ETA: today

    - CR 3,4,6 - In testing

    - CR2 - In Dev

- Release:

  - DH 19.0.x Milestone1 - Ready to be pushed \|\| BC cleared

    - Release \| Companion banner - enable 600x600 and add Item Title

    - Introduce new zone video-storypage (zoneId: 12027)

  - DH 19.0.x Milestone2 - QA testing awaited

    - Introduce a new ad slot sticky-notification for sticky
      notifications in dailyhunt app.

    - New subtype under image creative for splash image ad.

- CI/CD automation for Google cloud functions/run

**Data:**

- Removed flywheel restrictions for max delivery in an OI.

- Exposed LTV data in User monetisability superset.

  - One-time monthly dump prepared and charts enabled to unblock
    analysis.

  - Pipeline is in progress. ETA: Friday July 8th

- Publicvibe analysis pipeline extended.

  - Daily dump to GCS to be made available from today, July 4th onwards.

- MENA web zones capability extended to IE.

  - One-time dump in progress. ETA: Tuesday July 5th

- MENA CR5

  - MENA App CR5 ready for consumption - being shared internally right
    now.

  - MENA Web CR5 ETA: Tuesday July 5th

- Josh ads data sharing pipeline

  - Josh ads data now getting dumped to their S3 bucket daily - Bigquery
    not used.

- Newspaper-wise campaign-wise daily delivery dump sharing is in
  progress.

  - ETA: Thursday July 7th

- HWCluster GCP Migration

  - Secondary dump tables moved to MIS team's GCS bucket.
