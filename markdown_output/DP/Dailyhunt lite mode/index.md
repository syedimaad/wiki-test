  ----------------------- ----------------------------------------------
  **Document Status**     NOT STARTED / IN-PROGRESSYellow / READYGreen
  **Product Managers**    
  **Product Designers**   @ product designers
  ----------------------- ----------------------------------------------

17

## Context & Summary

Many of our users have limited/no access to high-speed internet.
Currently, the experience becomes slow for them. Idea is to curate a
great experience for them based on their data speed.

## First principles note

Curating the parameters in the case of slow data connections helps us
provides a better experience for the user.

- Mobile data is a scarce resource for this user. We need to plan out an
  experience that utilizes the user's mobile data efficiently and
  continues giving them a better experience

- Any content format that consumes a large amount of data can be ignored
  from the feed, viz. Video, Viral, CoC

- Content caching to be done based on **F** pattern

  - Load the first X feed cards

  - For these cards, start caching chunk 1 from top to bottom

  - Once chunk 1 is loaded, move to chunk 2

- \
  \
  Definition of Low Speed / Connectivity

  ----------------------------------------------------------
  Connectivity Type
  [2G \| 3 G ]{style="color: rgb(191,38,0);"}\| 4G \| Wifi
  ----------------------------------------------------------

  ------------------------------------------------------------------------------
  Connection Quality
  Excellent \| Goog \| Average \| [Poor \| Bad]{style="color: rgb(191,38,0);"}
  ------------------------------------------------------------------------------

Any of the red criteria should trigger ***Lite*** mode on our app

##  Success metrics

List project goals and the metrics you\'ll use to judge its success.

  ------------------------------------ --------------------------------------------- ------------------- ------------------
  **Goal**                             **Metric**                                    **Current Value**   **Target Value**
  e.g., Simplify the user experience   e.g., Customer satisfaction score increases                       
                                                                                                         
  ------------------------------------ --------------------------------------------- ------------------- ------------------

##  Functional Specifications

### Triggering Lite mode

- Connectivity Type = 2G / 3G [OR]{style="color: rgb(191,38,0);"}
  Connection Quality = Poor / Bad

- User has been in this state for 5 secs (configurable)

Prompt the user - *We've switched to a lite mode experience.
[Undo]{.underline}*

### Lite mode config

#### List View

+----------------------------------------+-------------------------------------------+-----------------+--------------+
| **Config**                             | **Value**                                 | **Effort**      | **Priority** |
+----------------------------------------+-------------------------------------------+-----------------+--------------+
| Card Type                              | Small                                     |                 | P0           |
+----------------------------------------+-------------------------------------------+-----------------+--------------+
| Video Auto play                        | Off                                       |                 | P0           |
+----------------------------------------+-------------------------------------------+-----------------+--------------+
| Video - Auto Caching (play ready)      | Off                                       |                 | P0           |
+----------------------------------------+-------------------------------------------+-----------------+--------------+
| Reduce prefetch of Chunk 1             | 5 items only                              |                 | P0           |
+----------------------------------------+-------------------------------------------+-----------------+--------------+
| AD Caching?                            | Off, similar to prefetch size             |                 | P1           |
+----------------------------------------+-------------------------------------------+-----------------+--------------+
| Live TV                                | Off (Don't insert card)                   |                 | P0           |
+----------------------------------------+-------------------------------------------+-----------------+--------------+
| Collections                            | Off (Don't show)                          |                 | P1           |
+----------------------------------------+-------------------------------------------+-----------------+--------------+
| Video prefetch                         | Off (TBC with Santosh)                    |                 | P1           |
+----------------------------------------+-------------------------------------------+-----------------+--------------+
| [Memes]{style="color: rgb(191,38,0);"} | [Remove (Carousel or single cards         |                 | P0           |
|                                        | too?)]{style="color: rgb(191,38,0);"}     |                 |              |
+----------------------------------------+-------------------------------------------+-----------------+--------------+
| Cricket ticker                         | \< 30kb, refersh cycle: 5secs\            | Not to be done  | P2           |
|                                        | configure refresh cycle: 20 secs          | right now       |              |
|                                        | (configurable) easily, beyond, to be      |                 |              |
|                                        | validated\                                |                 |              |
|                                        | \                                         |                 |              |
|                                        | (Ad coming between ticker carousel -      |                 |              |
|                                        | TBC)\                                     |                 |              |
|                                        | (Lite version of ticker?)                 |                 |              |
+----------------------------------------+-------------------------------------------+-----------------+--------------+
| ME cards (other than tickers)          | Off                                       |                 | P1           |
+----------------------------------------+-------------------------------------------+-----------------+--------------+
| Live update tickers                    | \< 30kb, refersh cycle: 5secs\            | Not to be done  | P2           |
|                                        | configure refresh cycle: 20 secs easily,  | right now       |              |
|                                        | beyond, to be validated                   |                 |              |
+----------------------------------------+-------------------------------------------+-----------------+--------------+
| [~~Web content on the                  | - [~~Cricket page lite mode?~~            |                 |              |
| app~~]{style="color: rgb(191,38,0);"}  |   ]{style="color: rgb(191,38,0);"}        |                 |              |
|                                        |                                           |                 |              |
|                                        | - [~~Other webviews (with most            |                 |              |
|                                        |   DAUs)~~]{style="color: rgb(191,38,0);"} |                 |              |
+----------------------------------------+-------------------------------------------+-----------------+--------------+

#### Detail View

+-------------------------------------------+----------------------------------------------------+----+
| Image Quality                             | Low only                                           | P0 |
+-------------------------------------------+----------------------------------------------------+----+
| SP Supplement Ad Slots                    | On                                                 | P1 |
+-------------------------------------------+----------------------------------------------------+----+
| Story page ad slots                       | Remains                                            | P0 |
+-------------------------------------------+----------------------------------------------------+----+
| Related articles                          | Lazy load\                                         | P1 |
|                                           | Not wait for scroll \> only delay loading?         |    |
+-------------------------------------------+----------------------------------------------------+----+
| [Video]{style="color: rgb(191,38,0);"}    | [Switch quality to                                 | P0 |
|                                           | low]{style="color: rgb(191,38,0);"}                |    |
+-------------------------------------------+----------------------------------------------------+----+
| [Embeds]{style="color: rgb(191,38,0);"}   | [Retain]{style="color: rgb(191,38,0);"}            | P1 |
+-------------------------------------------+----------------------------------------------------+----+
| Image                                     | Don't load by default. Blur and tap to download    | P1 |
+-------------------------------------------+----------------------------------------------------+----+
| [~~Story                                  | [~~No HTML \> Text                                 |    |
| content~~]{style="color: rgb(191,38,0);"} | only?~~]{style="color: rgb(191,38,0);"}\           |    |
|                                           | [~~Constraints:~~]{style="color: rgb(191,38,0);"}\ |    |
|                                           | [~~- Embeds don't work~~                           |    |
|                                           | ]{style="color: rgb(191,38,0);"}\                  |    |
|                                           | [~~- RICH text                                     |    |
|                                           | preserved~~]{style="color: rgb(191,38,0);"}\       |    |
|                                           | [~~- Choice to load html                           |    |
|                                           | version~~]{style="color: rgb(191,38,0);"}\         |    |
|                                           | \                                                  |    |
|                                           | ~~Not possible~~                                   |    |
+-------------------------------------------+----------------------------------------------------+----+

#### Notifications

[~~Avoid big image?~~]{style="color: rgb(191,38,0);"}

#### Misc

  ------------------- ------------
  App update prompt   Don't show
                      
  ------------------- ------------

#### Background activities (Consuming data)

  ---------------------- ----------------------------------------- ----
  Splash                 Not fetched within X secs, app can open   P1
  Font sync                                                        
  Doodle                 Off                                       
  Future ad caching                                                
  Instrumentaion sync?                                             P1
  ---------------------- ----------------------------------------- ----

### Rules

- Lite mode is introduced as a parameter in settings with options: On \|
  Off \| Auto. Default set to Auto

- Lite mode to be made active when

  - User has explicitly selected this from settings

  - Lite mode is set to AUTO **AND** ((Data connection is 2G/3G **OR**
    Connection quality is poor) for \>= 5 secs)

- Lite mode should be made inactive when

  - User has explicitly selected this from the settings

  - Lite mode is set to AUTO **AND** ((Data connection is not 2G/3G
    **OR** Connection quality is not poor) for \>= 30 secs)

### Design Handshake

- Slow network snackbar UI & content

- Slow network detected popup

- Loading for a long time / Feed stuck loading - UI & content

- Hold the interest of the customer until the feed is ready for the
  first time

**Ads caching meeting notes**

- Ads does caching based on network quality, poor good average. Today
  its set to 1

- Dailyhunt Go config already available, can just use that

- Can customize content based on lite mode. eg. Don't serve video ads

- Can resize content. eg. 30 MB image can be made to 2 MB

<!-- -->

- stop video card on the feed, 

- connectivity stamping is happening incorrectly

- are we downloading the smaller image on the client and then we are
  making them smaller

- video, CoC, viral not be served on the feed

- F type loading pattern for cards on the feed \> 

- Expresso caching \> AMPs cannot be cached \> types of cards that can
  be inserted can be tweaked

- communications to the user to be optimized

Josh caching learnings

- Prefetch logic

  - one after the other \> every video 20 % \> sequential

  - For entertainment like items we can prefetch this for carousels

- Downloaded content to use where

  - Start with offline videos and then go on to fresh

  - atleast 20 videos to be downloaded at any point of time

  - Notification on the tray and then disappears

- Event day videos

  - Cache and store the curated content

- User profile based \< news focused or entertainment focused

  - First video load can be inserted like an NLFC based on when its
    ready

- Embeds caching

  - preload and render the embed

##  Figma

Type /image to add mockups, diagrams, and screenshots related to the
requirements.

## Instrumentation
