  ----------------------- ---------------------
  **Document Status**     READYGreen
  **Android Sprint**      R11
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

Given that Josh supports a max of 60 second videos, the idea was to
explore integration of long-term content through trusted platforms like
YouTube. 

##  Objective

Goal is to increase time spent and engagement through longer-form
videos.

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

####  **Camera Edit Page**

- New option to link YouTube video

- Option will be the last option in the expanded tray and will not show
  inline

- For first time users, show educational nudge

####  **Link BottomSheet**

- Tapping on the YouTube icon opens a BottomSheet that enables the user
  to type / paste a YouTube URL

- If video URL does not contain the domain
  [https://youtube.com](https://youtube.com){card-appearance="inline"} ,
  do not paste the link and show a snackbar 'Invalid URL' instead

- On tapping of the paste shortcut icon, directly paste the last item
  from the clipboard

- If a link is already present and the user taps the paste icon,
  override the link and the preview

- Once the URL is added, generate a preview of the URL similar to
  WhatsApp and Facebook

- Run a loader until the preview is generated

- Preview should be playable with the native YouTube controls

- If any params are missing you the link pasted is unlisted or private,
  show link broken state and disable the next button

- On every change / keyup event, update the preview area

- For keyup, have a delay of 300ms

- If the video was originally previewing, but on change of some
  characters it breaks, update state to broken link and vice-versa

- If the user starts pressing backspace, hide the preview area until a
  new URL is entered\

#### **Video Player**

- Once the video is over, add a translucent overlay along with a 'View
  Full Video' button

- There will also be a countdown timer of X seconds where if the button
  is not tapped within that period it will restart the same  video (X =
  5 seconds)

- If the user swipes down or is moved to the next screen owing to the
  timer and swipes back up, video will start from the beginning

- When the YouTube player plays, hide all controls in order to keep it
  'look & feel' as native as possible

- When YouTube player plays, hide all other actions / meta

- YouTube player will have its own report icon, on tap of which users
  will be asked for purpose of reporting

- On selecting, show appropriate snack message

## Error Handling

List all product and feature errors and edge cases here.

## Notification Requirements

List all requirements for push, local & inbox notifications as well as
flash messages.

## PWA Requirements

List all requirements for web & PWA pages needed in this feature.

## BE & CMS Requirements

What configurations and CMS provisions are needed to power this feature?
List here.

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
