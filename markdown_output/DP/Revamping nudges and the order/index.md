  ----------------------- ----------------------------------------------
  **Document Status**     NOT STARTED / IN-PROGRESSYellow / READYGreen
  **Product Managers**    
  **Product Designers**   @ product designers
  ----------------------- ----------------------------------------------

17

## Context & Summary

Nudges serve as a guide to a user, explaining them how they can
experience the app without even the user feeling intrusive. They are
coach marks which guide users to do the actions we want them to do. When
combined with data-driven intelligence, these nudges become biggest
growth hacks, as they can persuade users to do exactly what you want
them to.

### Nudges Today: [Link](https://docs.google.com/spreadsheets/d/1oWekxLVt5pHrteSJ4E4kiE1XWcdG5sjEnXTXgLYStJM/edit?usp=sharing)

### Nudges new design: [Link](https://www.figma.com/file/3Zt2tJPNPB1fZmoqhVUuwi/Nudges?node-id=0%3A1)

### Nudges text changes: [Link](https://docs.google.com/spreadsheets/d/1oWekxLVt5pHrteSJ4E4kiE1XWcdG5sjEnXTXgLYStJM/edit?usp=sharing)

### Changed screens

#### Zero States

  ------------------------- ----------------------------- ---------
  **Zero states**           **New**                       **Old**
  Notifications                                           
  FPV:Followers                                           
  FPV: Following sources                                  
  FPV: Following hashtag    Same screen design as above   
  FPV: Following location   Same screen design as above   
  ------------------------- ----------------------------- ---------

  --------------------------------------------- ---------------------- ------------------------------------------
  **Element**                                   **Display Behavior**   **Action Behavior**
  Notifications zero state\> Home                                      On click, redirects user to For you page
  Followers zero state\> Follow                                        On click, redirects user to Follow page
  Following sources zero state\> Follow                                On click, redirects user to Follow page
  FPV: Following hashtag zero state\>Follow                            On click, redirects user to Follow page
  FPV: Following location zero state\> Follow                          On click, redirects user to Follow page
  --------------------------------------------- ---------------------- ------------------------------------------

#### Article Detail page Swipe Coachmark

  -- --------- ---------
     **New**   **Old**
               
  -- --------- ---------

  ----------------- --------------------------------------------------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------
  **Element**       **Display behavior**                                                                                                                                **Action behavior**
  Swipe Coachmark   When triggered, a black transparent screen covers the the current article and a peek of next article comes over this. The peek occurs for 2 times   Once user clicks anywhere on the screen (or swipes) the nudge goes away
  ----------------- --------------------------------------------------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------

##### Trigger logic

+-------------+-------------+--------------+-------------+----------------+
| **Pre       | **When to   | **When to    | **where to  | **Frequency of |
| condition** | trigger     | trigger      | display**   | the to be      |
|             | (old)**     | (new)**      |             | displayed(only |
|             |             |              |             | when all       |
|             |             |              |             | conditions are |
|             |             |              |             | met)**         |
+-------------+-------------+--------------+-------------+----------------+
| Min app     | When user   | When user    | Article     | All conditions |
| launch = 1  | lands on    | lands on     | detail page | are to be met: |
|             | article     | article      |             |                |
|             | detail page | detail page  |             | 1.  If left    |
|             | after app   | after app    |             |     swipe      |
|             | install and | install and  |             |     action on  |
|             | clicks back | user has not |             |     article    |
|             | to go to    | scrolled     |             |     detail     |
|             | feed list   | down in 'n\' |             |     page is    |
|             |             | seconds,     |             |     not        |
|             |             | \'n' is to   |             |     recorded   |
|             |             | be made      |             |     even once  |
|             |             | configurable |             |     in last    |
|             |             | n=24secs     |             |     24s SPV    |
|             |             |              |             |                |
|             |             |              |             | 2.  Minimum    |
|             |             |              |             |     time gap   |
|             |             |              |             |     of 15 days |
|             |             |              |             |     to exist   |
|             |             |              |             |                |
|             |             |              |             | 3.  Maximum of |
|             |             |              |             |     3 time to  |
|             |             |              |             |     be shown   |
|             |             |              |             |     in a       |
|             |             |              |             |     user's     |
|             |             |              |             |     lifetime   |
+-------------+-------------+--------------+-------------+----------------+

# Phase 2

## First principles note

**User perspective:**

- New user: To have a basic understanding of the product

- Existing user: Nudge to use un-used features/un-explored sections of
  the app so they can be more engaged

- Churned users:

  - App didn't appeal- Show them how we have improved since they last
    installed

  - Difficult to understand

**Business perspective:**

- Want to help user understand the product by simple guide- the value we
  provide them

- Want them to be more engaged on the app

  - Spend more time

  - Open app more frequently

**Issues:**

1.  Nudges frequency irregular

2.  Flow of nudges

3.  Nudges are not unified

##  Objective

1.  Unifying current nudges- UI

2.  When to nudge - what is the right moment to nudge users

3.  Whom to nudge - which users to nudge depending on the different
    stages of their app journey, which is the Person

4.  How to nudge - finding the best suiting type of nudge for the
    scenario, which is the nudge Mechanism

5.  Add missing nudges in required screens

##  Success metrics

List project goals and the metrics you\'ll use to judge its success.

  ------------------------------------ --------------------------------------------- ------------------- ------------------
  **Goal**                             **Metric**                                    **Current Value**   **Target Value**
  e.g., Simplify the user experience   e.g., Customer satisfaction score increases                       
                                                                                                         
  ------------------------------------ --------------------------------------------- ------------------- ------------------

## Competitive Analysis

Provide information on your top competitors here.

## Assumptions

List any assumptions you have about your users, technical constraints,
or business goals.

## ❗ Call-outs

List all the call-outs that we want to highlight to our stakeholders

##  Functional Specifications

List all product and feature requirements here.

## Error Handling

List all product and feature errors and edge cases here.

## Notification Requirements

List all requirements for push, local & inbox notifications as well as
flash messages.

## PWA Requirements

List all requirements for web & PWA pages needed in this feature.

## BE & CMS Requirements

What configurations and CMS provisions are needed to power this feature?
List here.

##  Open Questions

  ----------------------------------------------------------- ----------------------------------------------------------------------- -----------------------
  **Question**                                                **Answer**                                                              **Date Answered**
  e.g., How might we make users more aware of this feature?   e.g., We\'ll announce the feature with a blog post and a presentation   Type // to add a date
  ----------------------------------------------------------- ----------------------------------------------------------------------- -----------------------

##  Out of Scope

List the features discussed which are out of scope or might be revisited
in a later release.

## Reference Materials

Add links to research and other key documents here.

## Additional Notes

**Ideas:**

1.  Nudge to login (Get personalized news\>maintain a profile\>engage in
    comments\> join a group)

2.  Nudges to make pages visible (Automobile/Cricket)

3.  Nudge to follow a topic (Eg. Ukraine related news: click here to get
    news of this topic)

4.  App issues (Crash/slowness etc.): Facing issue, report this to us\>
    Redirect them to support

##  Figma

Type /image to add mockups, diagrams, and screenshots related to the
requirements.

## Instrumentation
