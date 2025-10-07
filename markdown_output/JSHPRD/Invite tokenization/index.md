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

If user A invites user B, and B signs up, they should automatically
start following A

##  Objective

If user A invites user B, and B signs up, they should automatically
start following A

##  Functional Specifications

**Invite tokenization and passing it in the onboarding events w/
implicit follow for the inviter-invitee**

1.  If user A invites user B, and B signs up, they should automatically
    start following A. 

    1.  The actual follow relationship should be formed as soon as the
        user identification building process is complete (ie. the system
        can uniquely identify the user).

2.  ~~Upon successful follow, a snackbar indicates the same.~~

    1.  ~~Action on the snackbar directs the user to the profile link of
        who they followed.~~

3.  Upon successful follow, send a notification to the user's
    notification inbox in existing templates for follow relationships

4.  **Note:** for the initial release, we will only have invite
    tokenization for logged in users.

    1.  This may be upgraded in a later release for non logged in
        inviters too.

##  Figma

N/A
