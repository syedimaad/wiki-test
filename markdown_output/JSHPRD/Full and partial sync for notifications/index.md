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

## Executive Summary

This track aims to improve notifications handling to reduce overhead and
speed things up for the user.

##  Objective

Deliver a cleaner and leaner notifications functionality to users.

##  Functional Specifications

**Overview**

1.  Right now notifications are locally powered and heavily handled by
    the client. This presents several challenges/limitations and it is
    also not an optimal way to approach this.

2.  We want increased reliability in delivery, reduction in data usage,
    optimisations in performance and better user experience.

3.  The way we're considering doing this is by:

    1.  Sharing ownership between client and backend.

    2.  Tracking the status of each notification that goes out.

    3.  Grouping notifications by category, type, time and the nature of
        the update.

    4.  Refreshing existing notifications based on validity,
        obsolescence and other superseding notifications.\

**Needs**

1.  Deliver only relevant amount of data/notifications on each cycle
    (only the delta for returning users)

2.  Track and manage notifications from the backend at an API level. 

    1.  Understand which notifications failed to deliver and retry them
        until delivery (if still relevant/and within a valid duration).

    2.  Clear/update/edit notifications based on rules and newer
        notifications. Notifications inbox

    3.  Reposting notifications to the notifications tray/shade

        1.  Ability to control this from the BE or all channels vs.
            specific channels

        2.  This notification type gets reposted on the tray at defined
            intervals until a BE controlled max time.

        3.  Reposting to happen until the user acts on the notification
            item

            1.  Click, ib_click, delete by swipe, delete by tray clear

3.  Inbox refresh upon delivery of new/updated notifications **\<ALREADY
    HANDLED\>**

    1.  When the app is in the background (automatic)

    2.  When the user is in any section other than the notification
        inbox (automatic)

        1.  ~~Snackbar with 'n new notifications' with a 'View' CTA~~

    3.  Message pill suggesting pull-to-refresh if the user is in the
        notifications inbox

4.  Notification hierarchy and update mechanism will be specified for a
    future release.\

**Others**

1.  Red dot

    1.  Animation on the red dot

    2.  Red-dot will show up as it does right now. An additional
        animation will be added to the dot that repeats till the
        notifications inbox is accessed.

2.  Red-dot logic: Maintain a red dot for a session if a user logs into
    the Josh app.

    1.  Clear the red dot if the user accesses the notification inbox.

3.  Smart grouping

    1.  Depending on the new entity 'notification_subtype',
        notifications will get grouped together:

        1.  If 1+ notifications of the same type are delivered in
            succession.

        2.  If time \>t has passed since the delivery of the
            notification

        3.  If the notification has been read
