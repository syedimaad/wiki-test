  ----------------------- ----------------------------------------------
  **Document Status**     NOT STARTED / IN-PROGRESSYellow / READYGreen
  **Product Managers**    
  **Product Designers**   
  ----------------------- ----------------------------------------------

## Context & Summary

To create more awareness about Dailyhunt as a brand, we are planning to
start an initiative to delight the users with a doodle on the app splash
screen. This doodle will be around calendar events.

##  Objective

- Increase brand recall

- Drive engagement within the app around the doodle

##  Success metrics

List project goals and the metrics you\'ll use to judge its success.

  ------------------------------------ --------------------------------------------- ------------------- ------------------
  **Goal**                             **Metric**                                    **Current Value**   **Target Value**
  e.g., Simplify the user experience   e.g., Customer satisfaction score increases                       
                                                                                                         
  ------------------------------------ --------------------------------------------- ------------------- ------------------

##  Functional Specifications

### Doodle play

- The doodle will be about calendar events like World Environment day,
  Independence day, etc

- The splash doodle can be delivered to a language specific user set

- To be delivered by ads module on the splash screen

- Will be scheduled atleast a month in advance

- Temporal deep topic to be already created against every doodle

## Phase 1

1.  Splash screen with the doodle

2.  ME card with the doodle → Click on ME card leads to deep topic
    page - **Single card?**

    1.  Ticker is possible with static image

    2.  HTML ticker with GIF to be tested?

    3.  Operationally ME card is better to execute day in - day out.

    4.  Options as single card

        1.  Standalone ticker with no other tickers runnning

        2.  ME carousel with only one topic

        3.  Following tab, News tab, ticker → Single card?, FY → other 3
            tickers

        4.  Running via Ads in PPC1

3.  Cover image of the deep topic can be modified to have the doodle as
    an animated entity → use ME for the same

    1.  Can be a static image

    2.  For animated, we'll need a client release

4.  Creative can be added in the Disovery page to take the user to the
    today's doodle topic page

5.  Share

    1.  Default share from 3 dots on the topic page

    2.  Deep topic is configuration driven, then floating share icon can
        be added. via fetch

    3.  Native web item i - frame page, PWA whatsapp share can be added
        in HTML \> invoke share prompt

  ----------------- ------------ ------------------------------------------------------------------------------------------------------------------------------------------------------------------
                    **Ticker**   **PPC1**
  GIF Support       ?            Yes
  Discoverability   D0           D1
  Dimensions        420x184      [http://adspecs.dailyhunt.in/static_ads/dailyhunt_ad_spec/ros.html](http://adspecs.dailyhunt.in/static_ads/dailyhunt_ad_spec/ros.html){card-appearance="inline"}
                                 
  ----------------- ------------ ------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Phase 2

### Driving traffic to the doodle topic page

+----------------------+----------------------+----------------------+
| **Options**          | **Pros**             | **Cons**             |
+----------------------+----------------------+----------------------+
| Replace the search   | - Clean UX           | - This would require |
| bar with this doodle |                      |   a release and the  |
| and click lands the  | - Makes discovery    |   logo change on     |
| user to the deep     |   easier             |   masthead can only  |
| topic page           |                      |   be visible on new  |
|                      |                      |   version            |
|                      |                      |                      |
|                      |                      | - Creative to be     |
|                      |                      |   placed on the      |
|                      |                      |   current search     |
|                      |                      |   will be limited by |
|                      |                      |   the current small  |
|                      |                      |   real estate        |
+----------------------+----------------------+----------------------+
| ~~An article can be  | - ~~Easier           | - ~~Article will     |
| created for every    |   implementation?~~  |   fight for          |
| doodle we do with    |                      |   visibility with    |
| description as to    | - ~~Can plugin the   |   other content      |
| what\'s the thought  |   article within any |   cards~~            |
| process behind it &  |   section → related  |                      |
| other variants that  |   stories, etc~~     | - ~~UI perception by |
| are made can be part |                      |   the user might be  |
| of that article &    |                      |   taken as any other |
| this article can     |                      |   content card /     |
| come in the feed in  |                      |   ad~~               |
| some depth & card#   |                      |                      |
| on days where we     |                      |                      |
| have the doodle~~    |                      |                      |
+----------------------+----------------------+----------------------+
| Serve the doodle     | - Easier             | - Same as option 2   |
| card through ME.     |   implementation?    |                      |
| Click leads to topic |                      |                      |
| page                 |                      |                      |
|                      |                      |                      |
| Possible to keep it  |                      |                      |
| daily at a specific  |                      |                      |
| spot?                |                      |                      |
+----------------------+----------------------+----------------------+

- Cover image of the deep topic can be modified to have the doodle as an
  animated entity

  - Click on the cover image opens up the full screen doodle

  - Share button to be added on the cover image for the user to share
    the doodle

- ~~Notification to be delivered to the user wishing them about the
  event~~ Not doing as notifications are already being served around
  important days separately

  - ~~Click on notification lands the user directly on the topic page~~

  - ~~On landing,~~

    - ~~Option 1: User sees the splash doodle and then goes to the topic
      page~~

    - ~~Option 2: User gets a watch today's doodle button on the page \>
      Highlighted/blinking which shows the splash doodle~~

  - ~~If splash doodle has been already seen, then land the user
    directly to the topic page~~

- ~~Article detailed page related to the splash doodle can have a CTA to
  the to watch the doodle or visit the topic page to watch the doodle~~
  Not doing

- Ad inventory PGI \> Tanvi

- Same festival \> different topics \> we have different topics

  - Should we have different image for different languages \> same
    topic?

## Error Handling

List all product and feature errors and edge cases here.

## Notification Requirements

NA

## PWA Requirements

- Option 1: Currently 1 month for MENA MVP and cleanup. In case this
  needs to be prioritized

- Option 2

  - Replacing current logo with the splash doodle

## BE & CMS Requirements

NA

##  Open Questions

  ---------------------------------------------------------- ----------------------------------------------------------------------- -----------------------
  **Question**                                               **Answer**                                                              **Date Answered**
  Content density across languages for all calendar events   e.g., We\'ll announce the feature with a blog post and a presentation   Type // to add a date
  ---------------------------------------------------------- ----------------------------------------------------------------------- -----------------------

##  Out of Scope

List the features discussed which are out of scope or might be revisited
in a later release.

##  Figma

Type /image to add mockups, diagrams, and screenshots related to the
requirements.

## Instrumentation
