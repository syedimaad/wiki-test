  ----------------------- ----------------------------------------------
  **Document Status**     NOT STARTED / IN-PROGRESSYellow / READYGreen
  **Product Managers**    
  **Product Designers**   @ product designers
  ----------------------- ----------------------------------------------

17

## Context & Summary

Today \~65% of the user's location detected is through IP. (\~13%
through GPS, \~22% through Cell Tower/Coords). As accuracy of location
detected through IP is only \~48%, users are served news feed of
incorrect location

##  Objective

To serve feed in FY/News basis the Primary location, followed locations
& recent location

To inform user about the new Primary location being added.

Stable Location Tab that which doesn't change based on the location
detected on one specific day

##  Success metrics

+---+---------------+---------------+---------------+---------------+
|   | **Goal**      | **Metric**    | **Current     | **Target      |
|   |               |               | Value**       | Value**       |
+---+---------------+---------------+---------------+---------------+
| 1 | #Users who    | CTR on News   |               |               |
|   | consume       | cards\        |               |               |
|   | location      | Time Spent in |               |               |
|   | invoked news  | Story_detail\ |               |               |
|   | cards should  |               |               |               |
|   | increase      |               |               |               |
+---+---------------+---------------+---------------+---------------+
| 2 | Reduction in  | CTR, TS on    |               |               |
|   | complaints    | Location Tab  |               |               |
|   | about         |               |               |               |
|   | incorrect     |               |               |               |
|   | Location Tab  |               |               |               |
|   | display       |               |               |               |
+---+---------------+---------------+---------------+---------------+
| 3 | Lesser        |               |               |               |
|   | variation in  |               |               |               |
|   | Location      |               |               |               |
|   | detected by   |               |               |               |
|   | Ads service & |               |               |               |
|   | Content       |               |               |               |
+---+---------------+---------------+---------------+---------------+

##  Functional Specifications

## **PROBLEM STATEMENT 1:**

Location changes real time leading to change in Feed (basis location)
frequently

## **Approach:**

Feed to get powered from 3 categories of locations:

I. Primary(Base) location A

II\. Followed locations B (b1,b2,b3..)

III\. Recent location C

### I. PRIMARY LOCATION A:

#### **Deciding Primary Location A:**

Two approaches:

1.  **Primary Location selected by User Explicitly in Settings** ([New
    Design
    Link](https://www.figma.com/file/CJkfPPbKAS4TQKpF3p9lTL/Settings?node-id=749%3A2450)):
    Settings \> When user selects a set of locations, the 1st location
    selected will be tagged with "You'll see news about \<loc\> on a
    separate Tab" (This tag can be dragged across to other locations.) -
    This new feature of Locations is part of 20.0.x Settings Revamp

    1.  Informing User about the Primary location: Taken care in
        Settings when user selects a location explicitly.

2.  **System assigned Primary location**:

    1.  The top ranked location in the last 15days or 30 sessions which
        ever is LATER, will be set as Primary Location.

        1.  **For New users until 30sessions or 15 days is met**: No
            change in location detection/assignment logic from the
            existing logic. But we'll educate user about the location
            detected.

        2.  **Frequency of showing Stickybanner:** every 3 sessions once
            until 30 sessions is met.

    2.  When user opens app, ranking is to be calculated for last 30
        sessions and if there is a change in Primary location, assign
        new Primary location from the next session onwards.

    3.  **Informing user about change in System assigned Primary
        location**:

        1.  Sticky Banner at top for 1 entire session: "Continue seeing
            news about \<Loc_A\>, your detected location ? You will see
            this location as a tab also

            1.  will:

                1.  make this location as **USER SELECTED PRIMARY
                    LOCATION**

                2.  add this Location as Primary Location under
                    Settings. Prompt for Primary Location to not appear
                    anymore;

                3.  Tab Location will be changed to this location

            2.  will:

                1.  BLACKLIST this Location as Primary Location. Do not
                    propose same location next time.

                2.  Navigate users to Location Settings page

                3.  Store a repo of **BLACKLISTED Primary locations**.
                    Later If user goes to settings & selects the same
                    location, WHITELIST it.

        2.  Duration of Stickybanner: If user doesn't act, display for
            the entire session. The last assigned Primary location will
            continue to be Primary location unless a new Primary
            location is assigned based on the Ranking Logic defined
            above.

        3.  Stickybanner to be displayed on FY, News and Location Tabs
            only.

**NOTE:**

If user Ticks Primary location that's assigned based on Ranking Logic ,
consider it as USER SELECTED PRIMARY LOCATION and override detected loc.

**[Order of Preference for Locations to power Reco linked
modules:]{.underline}**

1.USER SELECTED PRIMARY Location \> 2. PRIMARY LOCATION ASSIGNED BY
SYSTEM based on Ranking Logic \> 3. Recent Detected Location

### III. RECENT LOCATION C:

Whenever user opens app, If the same location C is detected in the next
3 sessions or for next 24hours whichever is EARLIER, then Reco to start
ingesting news about Location C also.

Note: If Location C is already part of Primary location or Followed locs
then no need to educate user.

**Informing User about the feed basis Recent location C detected :**

1.  Over the REFERRAL STRING card: "Because we detected Location_C" with
    .

    1.  Click :

        1.  Take user to settings page with stickybanner on Top: Do you
            want to follow Location_C ?

        2.  If user clicks , do not show referral news card for the same
            location going ahead.

        3.  No need to blacklist/whitelist Location C.

~~Note: If user follows the same blacklisted loc in settings, whitelist
the loc~~

## **PROBLEM STATEMENT 2:**

Today For users who have no location followed explicitly, Every Sunday
the Location Tab (3rd Tab) changes based on the last detected location
by Gateway. 

**Approach:**

1.  For users following a location: 1st Followed location is assigned as
    the Location Tab.

2.  For users not following any location:

    1.  3rd tab to not update basis the location detected on Sunday.

    2.  PRIMARY LOCATION ASSIGNED by system for first time (based on
        Ranking logic) will be the Location.

    3.  **NOTE**: If there is any change in Primary location detected by
        system in subsequent sessions, DO NOT change the tab
        automatically. Tab to always have the initial Primary location
        assigned. Only when user visits the tab display a StickyBanner
        on top "Do you want to change the location from A_old to A_new,
        your detected location? " ( will add this Location under
        Settings \> Selected Locations \> 1st Location, will set older
        location as Primary location & In Settings older location gets
        added as 1st Location. )

**Distribution of News Items:**

Will be decided by Reco.

**[Open points:]{.underline}**

Where to store Primary location info ?: To be discussed between User
service & Gateway. It'll mostly go to User service.

If user selects & overrides detection location, selected location

##  Figma

Type /image to add mockups, diagrams, and screenshots related to the
requirements.

## Instrumentation
