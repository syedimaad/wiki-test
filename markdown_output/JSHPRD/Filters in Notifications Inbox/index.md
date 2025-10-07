**Document Status**

  ----------------------- ---------------------
  **Document Status**     READYGreen
  **Android Sprint**      add release sprint
  **iOS Sprint**          add release sprint
  **Product Owners**      
  **Product Designers**   @ product designers
  **Android Leads**       @ android leads
  **Android Devs**        @ android devs
  **iOS Leads**           @ ios leads
  **iOS Devs**            @ ios devs
  **QA Devs**             @ qa devs
  **Josh Lite**           YEsGreen / NORed
  ----------------------- ---------------------

##  Executive Summary

The notifications inbox will have filters to select different
notification types. The aim of this feature is to allow the user to cut
through the clutter when there are a large number of notifications in
their inbox. 

##  Objective

The aim of this feature is to allow the user to cut through the clutter
when there are a large number of notifications in their inbox. 

##  Functional Specifications

**FILTERS FOR NOTIFICATIONS INBOX**

**Overview**

1.  The notifications inbox will have filters to select different
    notification types. The aim of this feature is to allow the user to
    cut through the clutter when there are a large number of
    notifications in their inbox. 

2.  The filters will be based on a few notification types:

    1.  Content

    2.  Social

        1.  Mentions

        2.  Followers

            1.  Follower activity/interactions

        3.  Likes (on own videos)

        4.  Comments/replies

    3.  Josh Notices

    4.  Promotions

3.  UI is
    [[here]{.underline}](https://www.figma.com/file/SWfkbuRYnkTQ8GcNtyBBrU/Notification?node-id=1883%3A1804).

**Suggestion**

1.  To address these types, we will need to introduce a new entity
    'notification_subtype' that is included in the payload for every
    notification. The slugs for these would be:

    1.  content

    2.  social_mentions

    3.  social_followers

    4.  social_likes

    5.  social_replies

    6.  josh_notices

    7.  promos

**Behaviour and user flow**

1.  Upon landing on the notification tab, a filter button is available
    on top of the inbox. 

    1.  Each of its options will correspond to a particular
        notification_subtype and one for 'All'.

    2.  Tapping on each option will enable/disable it and filter the
        list of notifications based on selected filters once the user
        hits 'Apply'.

    3.  If the user clears the filters, the notification inbox will
        display all notifications (same as now)

##  Figma

https://www.figma.com/file/SWfkbuRYnkTQ8GcNtyBBrU/Notification?node-id=1883%3A1804
