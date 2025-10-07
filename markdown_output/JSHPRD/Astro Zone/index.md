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
  **Josh Lite**           YEsGreen
  ----------------------- ---------------------

##  Executive Summary

A majority of Indians consume astrology content on a daily basis,
whether it is through snippets in a newspaper, astrology apps, WhatsApp
messages or other means. Given that astrology is a powerful content
vertical, we are looking to build an 'AstroZone' to enable users to view
their daily horoscope for important categories like education,
relationships, marriage and wealth among others.

##  Objective

To increase app open and time spent through astrology content.

##  Success metrics

List project goals and the metrics you\'ll use to judge its success.

  ------------------------------------ ---------------------------------------------
  **Goal**                             **Metric**
  e.g., Simplify the user experience   e.g., Customer satisfaction score increases
                                       
  ------------------------------------ ---------------------------------------------

## Competitive Analysis

Provide information on your top competitors here.

##  Assumptions

List any assumptions you have about your users, technical constraints,
or business goals.

##  Functional Specifications

####  **Home Feed**

- Configurable, circular masthead to show at defined time periods for
  astro zone, ex: from 7:00 AM - 900 AM

- On tap of masthead, it will directly open the interactive video
  defined inside the detailed page

- If the video is inside detailed page, tapping back will come back to
  home feed and if the video is inside the home feed, swiping to the
  next video and coming back will cause the video to restart\

**Video Player**

- Astro video will play like any other Josh video

- CMS will provide the interactive positions, duration of display and
  associated video for the astro video

- Client to enable interaction and load the subsequent video/s

- Duet and share icons to be hidden from this video

- Once a specific astro category is over, change its colour to indicate
  that its been viewed and show all the options again so that the user
  can select

- Once a user swipes to the next screen and comes back to the astro
  content, start from the beginning \

**Video Flow**

1.  Intro video

2.  Zodiac sign options

3.  Category options (CTA to go back to Zodiac sign)

4.  Category-specific video

5.  Category options (CTA to go back to Zodiac sign)\

## Error Handling

List all product and feature errors and edge cases here.

## Push Notification Requirements

- Once a user has added their information from the BottomSheet, they
  have shown high intent to consume that content and would hence receive
  push notifications for the same (needs discussion with notification
  team)

## BE & CMS Requirements 

- **Circular Masthead Configurability**

  - Duration: start & end time

  - Repeat rules

  - Thumb media: image or webp

  - Video to show & from which handle based on meta provided by user
    (ex: if a user selects capricorn, show today's video from handle
    \@astrozone_capricorn)

  - Nudge text

  - CTA\

- **Astro Video**

  - Video per category per sign per day

  - Respective Josh handle/s powering the video/s

  - Interactivity touchpoints, including:

    - X Axis

    - Y Axis

    - Width

    - Height

    - Scale

    - Rotation

##  Open Questions

  ----------------------------------------------------------- ----------------------------------------------------------------------- -----------------------
  **Question**                                                **Answer**                                                              **Date Answered**
  e.g., How might we make users more aware of this feature?   e.g., We\'ll announce the feature with a blog post and a presentation   Type // to add a date
  ----------------------------------------------------------- ----------------------------------------------------------------------- -----------------------

##  Out of Scope

List the features discussed which are out of scope or might be revisited
in a later release.

## Reference materials

Add links to research and other key documents here.

## Additional Notes

Add additional notes or comments, if any.

##  Figma

Type /image to add mockups, diagrams, and screenshots related to the
requirements.

## Instrumentation
