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
  **Josh Lite**           NORed
  ----------------------- ---------------------

##  Executive Summary

Interactive stickers are a growing trend in short-video apps like TikTok
and Instagram where users can not only see videos but also interact with
them through polls, quizzes and Q&As among other features.

##  Objective

Increase engagement of Josh videos through new interactive stickers.

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

###  **Polls**

- Interactive stickers will be accessible inside the stickers tab

- On tap of Poll sticker, add poll to sticker preview page page with
  question box active and keyboard open

- User can add a question upto a maximum of 3 lines

- Options can fit a maximum of 30 characters

- If a person tries to press the keyboard enter or dismiss the keyboard
  before the question or options are added, disallow it and keep
  keyboard open as is

- Default font size of the options is 14 inside the sticker preview area

- As the user keeps typing, the font size should pro-rata decrease to 10
  characters and a maximum of 2 lines inside the sticker preview area

- Once the user finishes filling the poll information and taps 'Done',
  add the sticker to the sticker preview page page along with the
  controls to angle, scale and remove

- User can move, scale and rotate the sticker within the bounds of the
  safe area which shows as the user is trying to move the sticker around

- Interactive elements to capture:

  - Width

  - Height

  - X axis

  - Y axis

  - Scale

  - Rotation

- User can tap on the X icon to delete the sticker

- On the video player page, poll will show as an interactive sticker
  over the video

- Once the user taps an option, it shows the percentage of users who
  also selected the same option

- On downloading the video, the poll with the options (not results) will
  get downloaded statically

- In the sticker preview timeline, left and right controls to be hidden
  as the sticker will be added through the entire duration of the video
  (colour will still be seen)

### **Quiz**

- On tap of Quiz sticker, add quiz to edit page with question box active
  and keyboard open

- User can add a question upto a maximum of 2 lines

- Answers option can also be a maximum of 2 lines

- User can add a maximum of 4 answers with a minimum of 2

- Until the minimum threshold is reached, Done button should be disabled

- If a person tries to press the keyboard enter or dismiss the keyboard
  before the question or options are added, disallow it and keep
  keyboard open as is

- Once the user starts typing the second option, automatically mark it
  as the correct option (shown with blue background and a tick) and a
  nudge saying tap to select your answer

- If the user has already marked the first option as the correct one,
  then do not auto-select the second option as correct

- If the user backspaces the second option which was selected as
  correct, change the correct option to the first one

- On tap of the radio button on the left (A, B, C, D), change the
  correct answer to the tapped one

- If options \< 4, show add below and once 4 is reached do not show add

- Once the user finishes filling the quiz information and taps 'Done',
  add the sticker to the camera edit page

- User can move, scale and rotate the sticker within the bounds of the
  safe area which shows as the user is trying to move the sticker around

- Interactive elements to capture:

  - Width

  - Height

  - X axis

  - Y axis

  - Scale

  - Rotation

- User can tap on the X icon to delete the sticker

- On the video player page, quiz will show as an interactive sticker
  over the video

- Once the user taps an option, it shows the correct answer as selected
  by the creator

- If the answer is wrong, a red colour will show over the user's
  selection and a blue colour over the correct answer along with a
  haptic vibration

- If the answer is correct, it will show a blue colour over the correct
  answer along with a haptic vibration and a confetti animation

- Lottie for confetti:
  [https://lottiefiles.com/74694-confetti](https://lottiefiles.com/74694-confetti){card-appearance="inline"}

- On downloading the video, the poll with the options (not results) will
  get downloaded statically

- In the sticker preview timeline, left and right controls to be hidden
  as the sticker will be added through the entire duration of the video
  (colour will still be seen)

## Edge Cases 

- **Stickers over stickers**

  - Users can add add multiple stickers over one another and there is a
    possibility that they may add a sticker over an interactive element 

  - In such a case, in the sticker preview the regular sticker can show
    over the interactive sticker, but once posted, the interactive
    sticker will always be on the top and regular sticker behind it so
    as to ensure that tapability will never be compromised

  - If one interactive sticker is added over another, ex: quiz is added
    over poll, the latest one will show on top (unless poll sticker is
    tapped inside the sticker preview page in which case poll sticker
    will jump to the top)

  - From an interactivity standpoint, whatever sticker is tapped will
    work and from the areas that overlap, whatever is on top will be
    'interactable'\

- **Stickers over buttons**

  - Users may flout the safe areas and place the sticker in a way that
    overlays key actions in the video player page such as like, comment,
    share etc. 

  - In this case, the action buttons will always win over the sticker\

- **Sticker resize too small**

  - Users may try to resize the sticker in a way that makes
    interactivity very difficult

  - In such cases, if the sticker dimensions become lesser than 30% of
    the base dimensions (as per the sticker preview page), animate the
    sticker back to at least 30% (refer Insta from a UX standpoint)

## Error Handling

List all product and feature errors and edge cases here.

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
