  ----------------------- ---------------------
  **Document Status**     READYGreen
  **Product Managers**    
  **Product Designers**   @ product designers
  ----------------------- ---------------------

## Context & Summary

Enabling support for instream ads in 3rd party content videos in native
and web . Eg. Supporting instream video ads on video feed given by
advertisers

## First principles note

1.  Today ad vmaps can only be attached for content hosted on DH

2.  The positions of this vmaps cannot be customised as per the
    advertiser requirement

##  Objective

1.  Provide a tool to ad ops and ad tech with the ability to attach and
    call vmaps in 3rd party videos

##  Success metrics

List project goals and the metrics you\'ll use to judge its success.

  ------------------------------------ --------------------------------------- ------------------- ------------------
  **Goal**                             **Metric**                              **Current Value**   **Target Value**
  Customised Vmap addition on videos   Impressions, quartile tracking,clicks   0                   Market Rate
                                                                                                   
  ------------------------------------ --------------------------------------- ------------------- ------------------

## Competitive Analysis

Voot/Zee 5 provide this capability

## Assumptions

List any assumptions you have about your users, technical constraints,
or business goals.

## ❗ Call-outs

List all the call-outs that we want to highlight to our stakeholders

##  Functional Specifications

1.  A tool eg spreadsheet which can capture the ad placements in the
    video for both native and web player

2.  Ads BE to consume the ad markers from this tool and attach vmaps.
    Each vmap should have a numerical valuse

3.  These vmaps to be used to render instream video ads

4.  DD to should allow ads configurations against each vmap. Eg VMAP 1
    of X mins to have X campaigns

5.  Duration of these ads can be customised. Eg 1st vmap can have ads
    for 5 mins and 2nd vmap can have ads for 10 mins

6.  Number of campaigns configured for the vmaps should match the ad
    duration set on vmap

7.  Ad cant cross the vmap duration.

8.  If a vmap doesnt have enough ads to meet its duration then the
    campaigns should play in loop

9.  Content should pause when a vmap is played and it should begin from
    the same paused stage when vmap ends

10. All ads tracking functionalities to be supported

## Error Handling

1.  In case the vmap duration and campaign duration dont match DD should
    throw an error and state that campaigns will play in loop

## Notification Requirements

NA

## PWA Requirements

NA

## BE & CMS Requirements

NA

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

Add additional notes or comments, if any.

##  Figma

Type /image to add mockups, diagrams, and screenshots related to the
requirements.

## Instrumentation
