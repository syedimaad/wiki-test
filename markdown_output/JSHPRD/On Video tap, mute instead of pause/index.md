  ----------------------- --------------------------------
  **Document Status**     IN-PROGRESSYellow / READYGreen
  **Android Sprint**      add release sprint
  **iOS Sprint**          add release sprint
  **Product Owners**      \@karandeep
  **Product Designers**   \@varsha
  **Android Leads**       @ android leads
  **Android Devs**        @ android devs
  **iOS Leads**           @ ios leads
  **iOS Devs**            @ ios devs
  **QA Devs**             @ qa devs
  **Josh Lite**           YEsGreen / NORed
  ----------------------- --------------------------------

##  Executive Summary

Currently on tapping the video on Home Video feed & from FPV & TPV we
pause the video. When the user swipes to the next video the state is not
maintained. (For all the full screen Video format)

##  Objective

Changing the behaviour on Tap from pause to mute, as we are in a short
video environment where mute makes much more sense than pause.

##  Success metrics

List project goals and the metrics you\'ll use to judge its success.

  --------------------------------------------- -----------------------------
  **Goal**                                      **Metric**
  Videos can be consumed in passive state too   Users consuming more videos
  --------------------------------------------- -----------------------------

## Competitive Analysis

Instagram - Mute on Tap, for Moj & Takatak pause on Tap.

##  Assumptions

Short videos are consumable even in mute state, content like dance,
cooking, Hook steps etc.

##  Functional Specifications

1.  When the user taps on the video, the video should get muted instead
    of a pause.

2.  The state should be maintained when a user swipes the videos or
    access video via other funnels (E.g if a user mutes the Video on
    Home Video feed, the same state needs to be maintained when the user
    watches a video via profile page.

3.  The state should be maintained across the sessions for a user.

4.  On another tap the video will get unmuted.

5.  Across the sessions for a user maintaining mute/play state of the
    video - AB Testing

6.  "Tap to Unmute" - come for 1st video (1-2 second nudge) when new
    session is started (with Mute state maintained across the sessions)

## Error Handling/Edge cases

The state of Mute or Play to be maintained across the sessions & for
Video play via different funnels (Via Home feed, Via TPV or FPV & Via
Discovery page)

For Ads - We should extend the Mute behaviour on tap, Video Ads coming
in the feed should be in a same state as other videos. (Mute or Play
state)

When receiving a call while watching a video, video should get mute &
then comes back to play state (if that was the default state of the
Video) after the call ends.

##  Figma

https://www.figma.com/file/QhCVcztHB559r2DCcBIU8o/Home?node-id=10836%3A24914

## Instrumentation
