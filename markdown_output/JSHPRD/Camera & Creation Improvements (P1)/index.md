  ----------------------- -------------------
  **Document Status**     READYGreen
  **Theme**               Camera & Creation
  **Product Owners**      
  **Product Designers**   
  **Josh Lite**           NORed
  ----------------------- -------------------

##  Executive Summary

Josh camera is enriched with several tools and functionalities that are
optimized for creators. Our goal is to improve and simplify several
flows to also make the overall experience seamless for regular users.

##  Objective

To simplify the camera experience and improve organic creation on the
platform.

##  Success metrics

List project goals and the metrics you\'ll use to judge its success.

  ----------------------------------- ----------------------------------------
  **Goal**                            **Metric**
  Improved creation                   Video post improvement
  Improved use of templates & duets   Video post improvement
  More usage of our camera tools      Usage of effects, filters etc improves
  ----------------------------------- ----------------------------------------

##  Functional Specifications 

Effects Label on Feed

- Music and effects label to be improved with a translucent background
  and background blur = 20

- If text \> label width, enable ticker scroll

- On tap of 'Try Now', open camera with the asset auto-loaded (camera
  should slide up from bottom to top)

- On tap of anywhere else in the label, open asset detailed page

Figma node
[here](https://www.figma.com/file/pNvUojuSBj9Rt2q6GuAmz7/Camera?node-id=14914%3A63054)

Effects Promo Card (R13)

A new promo card that encourages users to create a video on a popular
effect:

- \[BE\] The 3 eligible cards from the effect to be algo-powered with an
  option to manually deck specific videos

- All three videos will play on mute and on loop

- Thumbnail of the center video to be used as a blur background (blur
  radius = 100)

- Background should have a translucent black overlay with 60% or 0.6
  transparency

- Title with effect name should be max one line and ellipsize if text \>
  label width

- On tap of 'Use Effect', open the camera and automatically load the
  effect

- If the props / beans have not downloaded for the effect, open the
  camera and trigger the downloading popup

- On tap of save, change the icon state and show the respective toast
  message based on success or failure

Figma node
[here](https://www.figma.com/file/pNvUojuSBj9Rt2q6GuAmz7/Camera?node-id=14894%3A52905)

Camera, Templates & Duets Tabs (R13)

Goal is to build a single destination for all creation funnels:

- 'Pick a Song\' CTA to be removed from the center top and be replaced
  with three tabs called 'Camera', 'Templates' and \'Duets'

- Users can navigate between tabs either on swipe or tap of the tab

- Active tab font weight should be semi-bold

- Navigation between Camera to other tabs should be seamless where the
  black background should fade in and out as the user swipes

- Swiping of the tabs should be disabled if the user horizontally swipes
  anywhere below the record button

- Swipe should only be enabled 15 (dp / pt) above the effect shortcuts
  so as to not cause an intended swipe into any tab

- Horizontal & vertical swipe UX to be seamless with the right threshold
  and focus

- Order of tabs should be configurable

- If a user shuts the camera and reopens, always start with the camera
  irrespective of which last tab the user was on\

[Templates Tab]{.underline}

- On swipe, fade the black background in (same for swipe out)

- Templates are shown inside respective sections (ordering, visibility &
  text configurable)

- Section title should support emoji unicodes

- On tap of bookmarks, directly show bookmarked templates page

- \[BE\] Videos in each of the sections are algo powered with an option
  to manually deck select items to the top

- Template thumbnails should support both .jpg and .animated webp

- Templates title should be a max of 1 line after which it would be
  ellipsized

- The thumbnails will show as a collection and will display all items
  before the next section starts

- In the preview page, enable users to vertically swipe to the next /
  previous preview video

- If a user swipes down and swipes back up in template preview, restart
  the video from the beginning

- On tap of search, open the keyboard with the cursor active

- \[BE\] Configurability to add a suggested search string, ex: "Holi",
  "Diwali" etc (if no suggested string then show just Search text)

- If suggested strings \> 1, auto-rotate the text every 4 seconds with a
  slide in and out animation

- Search will work on every character and filter the results

- If search is open and the user swipes to another screen and comes
  back, reset the UI back to the default state and close search

- On tap of \'X\' in search, close search and the keyboard

- On tap of the thumbnail, open preview and the rest of the downstream
  funnel remains the same as discovery trends

- Loader state should have a shimmer effect

- If a user taps the bookmark icon, go to the templates bookmark page
  directly with a black background

- If a user opens the template preview and removes the bookmark, on
  coming back to the bookmarks page, remove that item\

[Duets Tab (Out of Scope for R12)]{.underline}

- On swipe, fade the black background in (same for swipe out)

- Page title should be configurable

- Duetable videos should be manually controlled via ops

- Eligible duetable videos are shown in a card view

- The ratio of the card is 2:3 and not 9:16 hence video should fit
  vertically in the center and the rest of the video will bleed out

- The cards will scroll and play one at a time (other videos stop)

- If a user swipes into the next video mid-way from the current video,
  on scrolling back up the video will restart from the beginning

- This card extends the global mute / unmute state of the user's feed
  i.e. if the user is in muted state then this video will also play on
  mute and vice-versa

- On tap of the 'Create Duet' button, open the duet camera

- On tap of the video, user should be able to mute / unmute

- At the end of the page show a bounce animation

Figma node
[here](https://www.figma.com/file/pNvUojuSBj9Rt2q6GuAmz7/Camera?node-id=14865%3A51711)

Camera Tray & Order

- Tray to be moved lower on the right for better accessibility

- Tray icons to be enriched and replaced with the new ones as shown in
  Figma

- New order and visibility of icons are (configurable):

  - Music / Pick a Song

  - Beautify

  - Timer

  - Green Screen

  - Flash

  - Speed (collapsed)

  - ZoomCam (collapsed)

  - Align (collapsed)

- Tray should animate when expanding / minimizing and not jump open /
  close

- When a song is selected, display the song cover photo instead of the
  default icon

- User can discard the song from the Selected Song bottomsheet on tap

- Music icon will show tooltip next to music up to 2 times
  (configurable) with text 'Tap to add music'

- Tooltip will autohide after the configured time as set in other
  tooltips currently

Figma node
[here](https://www.figma.com/file/pNvUojuSBj9Rt2q6GuAmz7/Camera?node-id=14865%3A54927)

Camera Effects Tray & Shortcuts (R13)

- Effect shortcuts will show to the left and right of the capture button

- Filter bundles to also be supported in the shortcuts

- Horizontal effects carousel will work both on swipe as well as tap

- Items will be configurable from the CMS

- Thumbs should support .jpeg and animated .webp

- On moving from one effect to another enable haptic and change the
  effect name on the label

- Label enables bookmarking and unbookmarking

- On tap of \'X\' on the label, remove the effect and scroll the
  carousel back to its default state (no haptic to be added here)

- If text width \> label width, ellipsize text

- \[BE / CMS\] Camera effects should support packaged deeplink URL

- On swiping or tapping, the active effect will show inside the capture
  circle and on recording the active effect will apply

- If the bundle of the active effect or the FU beans / props has not
  downloaded, show a loader inside the circle (popup to be removed)

- Effects tray should open with a parallax animation

- When tray opens, fade out camera icons not needed and fade in the ones
  needed with quick animation speed (like 100-150ms)

- Tray will first open at 50% and the camera viewport will pro-rata
  shrink

- On swiping up on the tray the viewport will continue to shrink and
  eventually hide and the tray will become full screen

- In the full-view state, if the user taps on any effect, animate the
  tray back to 50% and preview the effect on the camera

- If the tray is at 50% height and the user taps search, open the tray
  entirely and display the keyboard

- Search results should show on every character

- On tap of \'X\' in the search bar, remove the text input and on scroll
  hide the keyboard and remove text box from active / focus state

- Max number of lines for effect title will be 1 and will ellipsize if
  label width \> card width

- Tabs will now display icons instead of text and divide by screen width
  rather than overflow

- Tabs list and order:

  - Bookmarks

  - Recent

  - Trending (default)

  - Beauty

  - Games

- If there are no bookmarks or recent items, show default state

- Remove \'X\' option from the recent tray (rest of the logic remains
  the same as currently is)

- Tabs cab be accessed by swiping as well as tapping

- Tapping on save icon near the camera will instantly bookmark /
  unbookmark the previewed effect

- Tapping on the square icon will dismiss the effects tray and expand
  the camera into full-screen

- On tap of reset, remove the selected effect card and remove effect
  preview from camera

- Max tabs = 8 (including recent and bookmarks)

[Camera Deeplink]{.underline}

- If asset is marked fixed via deeplink, hide effects shortcut and
  effect label will show the name of the deeplink with bookmark and
  cross hidden (if asset is marked as fixed)

Figma node
[here](https://www.figma.com/file/pNvUojuSBj9Rt2q6GuAmz7/Camera?node-id=14865%3A52071)

Camera Speed UX

- UI improvement of tray

- Normal, fast and other text to be replaced with actual speed values

Figma node
[here](https://www.figma.com/file/pNvUojuSBj9Rt2q6GuAmz7/Camera?node-id=15363%3A65117)

Camera Green Screen (R13)

- On tap of green screen icon, open tray with a parallax effect (UX
  behaviour same as effects tray)

- If the props / beans are not downloaded, on tap of the icon show
  download state inside the tray and then show the assets

- While in download state, disable swiping of tabs

- There will be two tabs 'Green Screen\' & 'Gallery' (in iOS it will be
  called \'Camera Roll')

- On tapping any effect, it will preview on the camera

- In the full-view state, if the user taps on any effect, animate the
  tray back to 50% and preview the effect on the camera

- On swipe or tap of gallery tab, it will show the user's native gallery

- If gallery access permission is not given, show permission state
  asking for gallery access

- User can tap tap the reset button to remove any applied green screen
  effect

Figma node
[here](https://www.figma.com/file/pNvUojuSBj9Rt2q6GuAmz7/Camera?node-id=15186%3A67143)

Preview Asset Chips

The goal of asset chips is to reduce the complexity and number of steps
in applying any asset in the preview flow.

- Following assets will show as preview chips:

  - Effects (circle)

  - Stickers (as is)

  - Music (square w/ radius)

  - Captions (as is)

- Which ever direction (left or right) has scroll area available, show
  fade to transparency for better UX

- Scroll should only be enabled if chips width \> label width

- Assets added from the camera page will automatically show as chips in
  the preview page

- Any new asset added in the preview page will append in the front of
  the chips and will horizontally scroll

- On tap of the chip, it will open the timeline to enable users to
  adjust the duration of the asset

- During the time of adjusting the timeline, the asset cannot be moved
  around and all controls will be hidden

- Chip width will remain fixed and text will ellipsize if it overflows

- Tap to adjust timeline should show up to 2 unique sessions
  (configurable)

Figma node
[here](https://www.figma.com/file/pNvUojuSBj9Rt2q6GuAmz7/Camera?node-id=15210%3A63912)

Preview Stickers UX (R13)

- Stickers tray will show as an inline BottomSheet with a blur
  background (blur radius = 100)

- Tabs to be replaced with section headers (headers need not be sticky)

- On tap of the sticker, directly apply it to the entire duration of the
  timeline instead of opening the timeline view

- User should be able to adjust the sticker with controls directly on
  the preview page

- On tapping or trying to adjust stickers show controls, on tapping
  anywhere outside, hide the controls

- On tapping search, display the keyboard and search on every character

- Sticker search behaviour to be the same as effects search

Figma node
[here](https://www.figma.com/file/pNvUojuSBj9Rt2q6GuAmz7/Camera?node-id=14939%3A59028)

Preview Filters UX

- On the preview page, filters will be shown on swipe and not as a tab

- \[BE\] Order and name of the filter will be BE controlled

- Filter will apply as the user is swiping and not on release

- For first time users, show educational lottie animation

- Lottie asset:
  [https://edit.lottiefiles.com/?src=https%3A%2F%2Fassets1.lottiefiles.com%2Fpackages%2Flf20_anwxjkdj.json](https://edit.lottiefiles.com/?src=https%3A%2F%2Fassets1.lottiefiles.com%2Fpackages%2Flf20_anwxjkdj.json){card-appearance="inline"}

Figma node
[here](https://www.figma.com/file/pNvUojuSBj9Rt2q6GuAmz7/Camera?node-id=14880%3A52905)

Duets Promo Card

- A new promo card that encourages users to create a video on a popular
  duet:

  - The duetable video should play as a regular video from start to end
    with audio (not a thumb or GIF)

  - This card extends the global mute / unmute state of the user's feed
    i.e. if the user is in muted state then this video will also play on
    mute and vice-versa

  - On tap of the video, user should be able to mute / unmute

  - The same video to be used as a blur background (blur radius = 100)
    and will play alongside the overlay video

  - Title with effect name should be max one line and ellipsize if text
    \> label width

  - On tap of 'Create Duet, open duetcam with the respective video

Camera Music Suggestions (R13)

- CMS configurable audio suggestions that will be shown in as a nudge

- There will be no preview of the audio either by default or on tap

- Tapping on the tooltip will automatically apply the song with its
  default values

- Suggested nudge will only show until the user takes any action i.e. if
  the user starts recording or taps an effect and the suggested audio
  hasn't been clicked, hide it for that session

- If song title \> label width enable ticker scroll

- Suggested audio for the same Audio ID will show be configurable
  (default = 2)

- If the nudge count \< max configured count, on tap of the nudge \'X\'
  hide it for that session (it will still show the next time the user
  shuts and opens the camera)

- Ops controlled suggestions that enables one-tap to add

- On tap of X remove the suggestion and do not show it again ever

- \[BE\] Config to control how many times the suggestion is shown for
  the same user if ignored and X not tapped

- If 'Suggested Audio' variant exists, show that instead of the new user
  variant

- If 'Suggested Audio' variant is shown instead of new user variant, it
  does not impact the configurable count value

Preview Text UX

- Text tab will directly open the 'Add text' text box rather than the
  timeline view

- Bottom carousel will have the following elements:

  - Bold

  - Italics

  - Shadow

  - Font list (current logic remains same)

- Top options:

  - Background:

    - On tap, open the list of colour options vertically on the right

    - None / reset icon should remain fixed when vertically scrolling

    - Colour options to remain the same

    - Radius to add a curve to the border

    - Radius to have haptics as the value changes

  - Text align:

    - Default radius is left radius

    - On tap, change to center align and on tap again change to right
      align

    - When on right align, tapping comes back to left align

  - Stroke:

    - On tap, open the list of colour options vertically on the right

    - None / reset icon should remain fixed when vertically scrolling

    - Colour options to remain the same

    - Thickness to add a stroke to the border

    - Radius to have haptics as the value changes

Preview Dub UX

Only UI improvements with all other elements remaining the same.

Preview Time UX

Only UI improvements with all other elements remaining the same.

Camera Timer UX

Only UI improvements with all other elements remaining the same.

Camera ZoomCam UX

Only UI improvements with all other elements remaining the same.

Camera Beautify UX

- Skin and Face tab to be removed and all beauty tools to be shown in
  one single horizontal carousel

- Order of beauty tools:

  - Auto

  - Face

  - Eye

  - Chin

  - Head Size

  - Head Width

  - Forehead

  - Nose

  - Mouth

  - Nose Length

  - Eyelid

  - Smile

  - Smoothen

  - Whiten

  - Blush

Preview Edit UX

Only UI improvements with all other elements remaining the same.

Preview Animations UX

Only UI improvements with all other elements remaining the same.

Preview Transitions UX

Only UI improvements with all other elements remaining the same.

Preview Music, Trim & Multi-Audio UX

No change for now.

## Error Handling

- If templates are not returned when swiping owing to failure or
  internet, show empty state

## BE & CMS Requirements 

#### [1. Effects & Duet Promo Card]{.underline}

Ability for ops to create a promo card for an effect. Elements include:

- Effect ID (for effects)

- Video ID decking (for effects)

- Duetable Video ID (for duets)

- TTL

- Scheduling

#### [2. Audio Suggestions Tooltip]{.underline}

Ability for ops team to configurable a single promoted song as
suggestions on the camera. Elements include:

- Audio ID

- TTL

- Scheduling

- Times shown per user per Audio ID

#### [3. Effects Shortcut]{.underline}

Ability for ops to configure effect shortcuts on the camera. Elements
include:

- Effect ID / Camera deeplink

- Left & right index

- TTL

- Scheduling

#### [4. Templates Tab]{.underline}

Ability for ops to create categories and add templates. Elements
include:

- Template ID

- Thumb

- Title

- Index

#### [5. Templates & Sticker Search]{.underline}

- Templates and sticker search should be based on template / sticker
  title and keywords

- Suggested search string elements:

  - String

  - Max string = 5

  - Index

  - TTL

  - Scheduling

#### [6. Duets Tab]{.underline}

Ability for ops to ad duetable videos. Elements include:

- Video ID

- Index

##  Open Questions

  -------------------------------------------------------------------------------------------- ----------------------------------------------------------------------- -----------------------
  **Question**                                                                                 **Answer**                                                              **Date Answered**
  In feed promo cards for effects and duets, should the inspired creation count be gamified?   e.g., We\'ll announce the feature with a blog post and a presentation   Type // to add a date
  -------------------------------------------------------------------------------------------- ----------------------------------------------------------------------- -----------------------

## Additional Notes

- Camera should open and close with a slide up / slide down effect

- Relevant zero-state screens as shown in Figma should have the shimmer
  effect

##  Figma

https://www.figma.com/file/pNvUojuSBj9Rt2q6GuAmz7/Camera?node-id=14535%3A38017

## Instrumentation

Camera Effects Promo Card (R14):
[https://docs.google.com/spreadsheets/d/1f3mHeHN2ivXaYZncxBoVI3Y619bfwlX2O_omn_8EB_Y/edit#gid=1595704841&range=A52](https://docs.google.com/spreadsheets/d/1f3mHeHN2ivXaYZncxBoVI3Y619bfwlX2O_omn_8EB_Y/edit#gid=1595704841&range=A52){card-appearance="inline"}

[https://docs.google.com/spreadsheets/d/1f3mHeHN2ivXaYZncxBoVI3Y619bfwlX2O_omn_8EB_Y/edit#gid=372605624&range=A2](https://docs.google.com/spreadsheets/d/1f3mHeHN2ivXaYZncxBoVI3Y619bfwlX2O_omn_8EB_Y/edit#gid=372605624&range=A2){card-appearance="inline"}
