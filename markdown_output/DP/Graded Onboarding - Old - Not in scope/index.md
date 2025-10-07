  ----------------------- ---------------------
  **llDocument Status**   IN-PROGRESSYellow
  **Product Managers**    
  **Product Designers**   @ product designers
  ----------------------- ---------------------

## Context & Summary

Users might be overwhelmed by seeing a lot of features for the first
time, which might lead to things such as dropping off due to confusion
or sensing real value.

**First Principle:**

- With expresso coming in, there will be too many things for the users
  to consume in the first go

- The progressive introduction of the other core items

- start from minimal UI and then take the user to the full-blown app in
  a gradual manner.

## **[New Users]{style="color: rgb(54,179,126);"}**

+------------------------------------------------+---------------------------------------------+
| **[Scenario]{style="color: rgb(255,86,48);"}** | **[Specs]{style="color: rgb(255,86,48);"}** |
+------------------------------------------------+---------------------------------------------+
| A                                              | 1.  Expresso default                        |
|                                                |                                             |
|                                                | 2.  Less element in the 1st release         |
|                                                |                                             |
|                                                | 3.  Education about other core elements     |
|                                                |                                             |
|                                                | 4.  Cross sell of long reads                |
+------------------------------------------------+---------------------------------------------+
| B                                              | 1.  Long reads default                      |
|                                                |                                             |
|                                                | 2.  Less element in the 1st release         |
|                                                |                                             |
|                                                | 3.  Education about other core elements     |
|                                                |                                             |
|                                                | 4.  Cross sell of expresso                  |
+------------------------------------------------+---------------------------------------------+
| C                                              | 1.  Option lies with the user to choose     |
|                                                |     their default home during onboarding    |
|                                                |                                             |
|                                                | 2.  Less element in the 1st release         |
|                                                |                                             |
|                                                | 3.  Education about other core elements     |
|                                                |                                             |
|                                                | 4.  Cross sell of non-selected items        |
+------------------------------------------------+---------------------------------------------+

**[A/B texting Config:]{style="color: rgb(0,184,217);"}**

  ---------------------- ------- ------- -------
  **User-type**          **A**   **B**   **C**
  **Deferred known**     Known   Known   0%
  **Deferred Unknown**   45%     45%     10%
  **Non-Deferred**       45%     45%     10%
  **Pre-burn**           48%     48%     4%
  ---------------------- ------- ------- -------

Due to any reasons, if the configs are not sent to the client- the
default will be long reads home and follow **[Deferred- Known
(A)]{style="color: rgb(54,179,126);"}** from the below table

**Pre-burn+ Non-deferred= approx. 80% of new users**

[Note: The scenario percentage is configurable and can vary based on the
below metrics]{style="color: rgb(255,86,48);"}

**Metrics : ts_expresso, ts_long_reads, pv_expresso, pv_long_reads**

### [General configs for all types of users:]{style="color: rgb(76,154,255);"}

+-----------+----------------------------+----------------------------+
| **Stage** | **Launch**                 | **Configs**                |
+-----------+----------------------------+----------------------------+
| Stage 1   | 1st                        | 1.  top tab will be "For   |
|           |                            |     you", "News",          |
|           |                            |     "Cricket", +           |
|           |                            |                            |
|           |                            | 2.  Bottom bar will have 4 |
|           |                            |     elements- Home, long   |
|           |                            |     reads, Search, profile |
|           +----------------------------+----------------------------+
|           | 2nd                        | 1.  video is added,        |
|           |                            |     animation of the icon  |
+-----------+----------------------------+----------------------------+
|           | 2nd view of long reads     | 1.  Nudge on "+" for       |
|           |                            |     manage tabs            |
+-----------+----------------------------+----------------------------+
| Stage 2   | 3rd                        | 1.  Bottom bar becomes 5+1 |
+-----------+----------------------------+----------------------------+

### [Specific Configs for user type]{style="color: rgb(76,154,255);"}

+--------------+------------+-----------------------------------------+-----------------------------------------+---------------------------------------------------------------+--------------------------------------------------------------+-----------------------------------------------------+
| **Stage**    | **Launch** | **[Deferred- Known                      | **[Deferred- Known                      | **[Deferred- unknown /                                        | **[Deferred- unknown /                                       | **[Deferred- unknown /                              |
|              |            | (A)]{style="color: rgb(54,179,126);"}** | (B)]{style="color: rgb(54,179,126);"}** | Non-deferred/(A)/Pre-Burn]{style="color: rgb(54,179,126);"}** | Non-deferred(B)/pre-burn]{style="color: rgb(54,179,126);"}** | Non-deferred(C)]{style="color: rgb(54,179,126);"}** |
+--------------+------------+-----------------------------------------+-----------------------------------------+---------------------------------------------------------------+--------------------------------------------------------------+-----------------------------------------------------+
| Stage 1      | 1st        | 1.  Default to Expresso                 | 1.  Default to Long-reads               | Follow **[Deferred- Known                                     | Follow **[Deferred- Known                                    | 1.  User lands on long reads default                |
|              |            |                                         |                                         | (A)]{style="color: rgb(54,179,126);"}**                       | (B)]{style="color: rgb(54,179,126);"}**                      |                                                     |
| 1.  Default  |            | 2.  Long reads will be a separate       | 2.  Expresso will be separate bottom    |                                                               |                                                              | 2.  Expresso will be animated                       |
|     home     |            |     bottom tab                          |     tab                                 |                                                               |                                                              |                                                     |
|              |            |                                         |                                         |                                                               |                                                              | 3.  Nudge to make exoresso default home tab if      |
| 2.  Less     |            |                                         |                                         |                                                               |                                                              |                                                     |
|     items in |            |                                         |                                         |                                                               |                                                              | a\. the user spent "x " seconds on expresso         |
|     top tabs |            |                                         |                                         |                                                               |                                                              |                                                     |
|              |            |                                         |                                         |                                                               |                                                              | b\. on the 2nd exploration of expresso in the same  |
| 3.  3 items  |            |                                         |                                         |                                                               |                                                              | launch                                              |
|     in       |            |                                         |                                         |                                                               |                                                              |                                                     |
|     bottom   |            |                                         |                                         |                                                               |                                                              |                                                     |
|     bar      |            |                                         |                                         |                                                               |                                                              |                                                     |
|              |            |                                         |                                         |                                                               |                                                              |                                                     |
| 4.  Video    |            |                                         |                                         |                                                               |                                                              |                                                     |
|     addition |            |                                         |                                         |                                                               |                                                              |                                                     |
+--------------+------------+-----------------------------------------+-----------------------------------------+---------------------------------------------------------------+--------------------------------------------------------------+-----------------------------------------------------+
| Stage 2      | 3rd        | NA                                      | NA                                      |                                                               |                                                              | 1.  User not interacted with expresso on the bottom |
|              |            |                                         |                                         |                                                               |                                                              |     bar: Default user to expresso tab- education    |
|              |            |                                         |                                         |                                                               |                                                              |     about the shorts format                         |
|              |            |                                         |                                         |                                                               |                                                              |                                                     |
|              |            |                                         |                                         |                                                               |                                                              | 2.  Interacted: DO Nothing                          |
+--------------+------------+-----------------------------------------+-----------------------------------------+---------------------------------------------------------------+--------------------------------------------------------------+-----------------------------------------------------+
| Stage 3      | 5th        | Story/Feed card talking about other     | Expresso card with explore more cta     |                                                               |                                                              | NA                                                  |
|              |            | format with "know more CTA-takes user   |                                         |                                                               |                                                              |                                                     |
| Cross sell   |            | directly to long reads(botom-bar)       |                                         |                                                               |                                                              |                                                     |
| of long      |            |                                         |                                         |                                                               |                                                              |                                                     |
| reads/       |            |                                         |                                         |                                                               |                                                              |                                                     |
| expresso     |            |                                         |                                         |                                                               |                                                              |                                                     |
|              +------------+-----------------------------------------+-----------------------------------------+---------------------------------------------------------------+--------------------------------------------------------------+-----------------------------------------------------+
|              | 8th        | Interacted with show more - No action   | Interacted with show more - No action   |                                                               |                                                              | Expresso interacted : Do nothing                    |
|              |            | needed                                  | needed                                  |                                                               |                                                              |                                                     |
|              |            |                                         |                                         |                                                               |                                                              | Expresso not intercated : Nudge on the bottom bar   |
|              |            | Not-Interacted with show more- In-app   | Not-Interacted with show more- In-app   |                                                               |                                                              | for expresso                                        |
|              |            | notification for the other format       | notification for the other format       |                                                               |                                                              |                                                     |
|              +------------+-----------------------------------------+-----------------------------------------+---------------------------------------------------------------+--------------------------------------------------------------+-----------------------------------------------------+
|              | 10th       | Interacted with show more - No action   | Interacted with show more - No action   |                                                               |                                                              | NA                                                  |
|              |            | needed                                  | needed                                  |                                                               |                                                              |                                                     |
+--------------+------------+-----------------------------------------+-----------------------------------------+---------------------------------------------------------------+--------------------------------------------------------------+-----------------------------------------------------+

### Flow Chart for above

# [Existing Users]{style="color: rgb(54,179,126);"}

Config table

+-----------+------------+---------------------------+-----------------+
| **Stage** | **Launch** | **Thin users**            | **Heavy Users** |
+-----------+------------+---------------------------+-----------------+
| 1         | 1st        | 1.  User lands on long    |                 |
|           |            |     reads default         |                 |
|           |            |                           |                 |
|           |            | 2.  Expresso will be      |                 |
|           |            |     animated              |                 |
|           |            |                           |                 |
|           |            | 3.  Top bar will be 3     |                 |
|           |            |     tabs                  |                 |
|           |            |                           |                 |
|           |            | 4.  Bottom bar will be    |                 |
|           |            |     5+1                   |                 |
|           |            |                           |                 |
|           |            | 5.  Nudge to make         |                 |
|           |            |     exoresso default home |                 |
|           |            |     tab if                |                 |
|           |            |                           |                 |
|           |            | a\. the user spent "x "   |                 |
|           |            | seconds on expresso       |                 |
|           |            |                           |                 |
|           |            | b\. on the 2nd            |                 |
|           |            | exploration of expresso   |                 |
|           |            | in the same launch        |                 |
+-----------+------------+---------------------------+-----------------+
|           | 3rd        | 1.  User not interacted   |                 |
|           |            |     with expresso on the  |                 |
|           |            |     bottom bar: Default   |                 |
|           |            |     user to expresso tab- |                 |
|           |            |     education about the   |                 |
|           |            |     shorts format         |                 |
|           |            |                           |                 |
|           |            | 2.  Interacted- DO        |                 |
|           |            |     nothing               |                 |
+-----------+------------+---------------------------+-----------------+
|           | 8th        | Expresso interacted : Do  |                 |
|           |            | nothing                   |                 |
|           |            |                           |                 |
|           |            | Expresso not intercated : |                 |
|           |            | Nudge on the bottom bar   |                 |
|           |            | for expresso              |                 |
+-----------+------------+---------------------------+-----------------+
|           | 10th       |                           |                 |
+-----------+------------+---------------------------+-----------------+

A/B Testing configs:

Time period: 2 weeks

Threshold page view: N

### Mapping of page views (Long reads/expresso)

  ------------------------------------------------- ---------------------- --------------------
                                                    **PV of long_reads**   **PV of expresso**
  List view                                         Yes                    
  Story detail page( except expresso detail page)   Yes                    
  Any top tabs view                                 Yes                    
  Story view inside expresso                                               Yes
  Details page of search result/discovery page      Yes                    
  Story detail page of expresso                                            Yes
  ------------------------------------------------- ---------------------- --------------------

  ------------------- -------------------------------------- -------------------------------------------------
  **User_type**       **ratio(pv_expresso/pv_long_reads)**   **correction- method**
  Heavy Expresso      4                                      in-app\-\-\--\>notification
  Medium Expresso     2                                      in-app\-\-\--\>notification\-\--tooltip\--nudge
  Average             aprox 1                                NA
  Medium Long reads   0.5                                    in-app\-\-\--\>notification\-\--tooltip\--nudge
  Heavy Long reads    0.25                                   in-app\-\-\--\>notification
  ------------------- -------------------------------------- -------------------------------------------------

Design Inputs: The user flow, choice screen, cross-sell mechanism

Cross-sell mechanism:

1.  Story card one for all or do you want to keep it dynamic?

2.  Know more lands to list view or story detail\-\--list view?

3.  Notification- to differentiate between expresso n list view?

4.  immersive inclusion

  ------------------- -------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------
                      **Expresso Default**                                                                                           **Long reads Default**
  Heavy Expresso      NA                                                                                                             Lands to expresso home when the user opens the app next organically not through notification or deep links
  Medium Expresso     NA                                                                                                             Lands to expresso home when the user opens the app next organically not through notification or deep links
  Average             NA                                                                                                             NA
  Medium Long reads   Lands to long reads home when the user opens the app next organically not through notification or deep links   NA
  Heavy Long reads    Lands to long reads home when the user opens the app next organically not through notification or deep links   NA
  ------------------- -------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------

Wireframe link:
[https://miro.com/app/board/uXjVOjsEZrI=/?share_link_id=988202477719](https://miro.com/app/board/uXjVOjsEZrI=/?share_link_id=988202477719){card-appearance="inline"}

**[Existing user ]{style="color: rgb(255,86,48);"}**

**[Thin n unknown]{style="color: rgb(255,86,48);"}**

**Who :**

- For age 18-24 users non-plat users-

- For low engagement users: Users with \<5 days of activity in the
  preceding month-

Have to be uploaded to BE

**When:**

1st view of the home zone after update

**Why?**

Thin user/unknown users cannot find stickiness to the app, so to engage
with users, show them the fresh look with expresso and see if they find
stickiness this time.

Specs Sheet:
[https://docs.google.com/spreadsheets/d/1faiekJOTQlmkwHKH4Jn1bRP1JiEdlw1z6bFTqvd9xP8/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1faiekJOTQlmkwHKH4Jn1bRP1JiEdlw1z6bFTqvd9xP8/edit?usp=sharing){card-appearance="inline"}

## **[Heavy User]{style="color: rgb(255,86,48);"}**

**Who :**

- Platinum users

- For engagement users: Users with \>5 days of activity in the preceding
  month

Have to be uploaded to BE

**When:**

1st view of the home zone after update

**Why?**

Heavy users already are aware of most of the app features so no major
interruptions are needed for such kinds of users

Specs Sheet:
[https://docs.google.com/spreadsheets/d/1faiekJOTQlmkwHKH4Jn1bRP1JiEdlw1z6bFTqvd9xP8/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1faiekJOTQlmkwHKH4Jn1bRP1JiEdlw1z6bFTqvd9xP8/edit?usp=sharing){card-appearance="inline"}

## **[New Users]{style="color: rgb(255,86,48);"}**

**Who :**

- New users: Identifier: **Deferred Deep Link Approach**  - We can have
  separate landing url for Expresso zone and use the same as deferred
  deep link in Google and Facebook campaigns. Users coming from these
  campaigns to land in Expresso zone by default post language selection.

- Users from specific genre campaigns. Again based on ad groups. {Ad
  group to have agreed nomenclature format of \_Exp}

Have to be uploaded to BE

**When:**

- Preferable at first launch

- In case identification takes time, definitely from the second launch

- No transition within a session in case information of home zone comes
  during the session when the user is browsing

**Why?**

News users are getting exposed to the app for the first time, which
downloading the app, the value prop they know is a **short format** for
consumption of content.

Default Launch: Expresso tab

## Setting:

- Setting for the user to change the default home at any given point in
  time

- Setting get updated based on the user action on the nudges

- The default home setting will be "long reads"

- Default home setting for all readers except the new readers( intent:
  expresso)

## Instrumentation
