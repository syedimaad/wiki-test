  ----------------------- --------------------------------
  **Document Status**     IN-PROGRESSYellow / READYGreen
  **Android Sprint**      add release sprint
  **iOS Sprint**          add release sprint
  **Product Owners**      \@karandeep
  **Product Designers**   \@Sumedh
  **Android Leads**       @ android leads
  **Android Devs**        @ android devs
  **iOS Leads**           @ ios leads
  **iOS Devs**            @ ios devs
  **QA Devs**             @ qa devs
  **Josh Lite**           YEsGreen / NORed
  ----------------------- --------------------------------

##  Executive Summary

Currently, no provision to add local audios to the videos
created/uploaded by the users. It's an important functionality as users
might want to use the saved audios(Local Audios) as background music.

##  Objective

Local Audio list available for the users to choose from & use it as a
background music for the Video created/uploaded.

##  Success metrics

List project goals and the metrics you\'ll use to judge its success.

  ---------------------------------------------------------- -------------------------------------------------------
  **Goal**                                                   **Metric**
  Users can use local audios to add as a background music.   Percentage of Videos with background music increases.
  ---------------------------------------------------------- -------------------------------------------------------

## Competitive Analysis

Mx TakaTak have a provision of adding local audios as background music
to the created videos.

##  Assumptions

List any assumptions you have about your users, technical constraints,
or business goals.

##  Functional Specifications

Clicking on Music icon from the camera screen the bottom sheet will get
triggered as per Figma. Search bar will be at the top of the sheet with
the provision of API powered multiple placeholder text (Transitioning
from one to another)

**Three tabs** - Library, Bookmark & My Music in the "Pick a Song" page
on top of the page

1.  **"Library" section:** Current page showcasing the Audios list &
    Audio collection from the Josh Library

2.  **"Bookmark" section:** Showcasing the bookmarked audio list.

3.  **"My Music" section:** Showcasing the list of Audios saved in the
    local device (user's phone). User can select them as a background
    music for the Video (Similar to current flow). If Storage permission
    is not given then the page will show the message to provide required
    permission to have an access to the local audios saved on the mobile
    device.

(Ordering list for local audios would be Reverse Chrono (Added recently
coming on the top) - time the audio is added in a device)

4\. Horizontal swipe & click on the Tab text will change the tab from
"Library" to "Bookmark" to "My Music".

**Click on the Search bar:**

Click on the search bar will open a keyboard inline with back arrow icon
on the left of the search bar. In the default state "Suggestion Audio"
list will be on the screen. If user starts searching for the Keyword,
results from My Music & Library both will appear on the screen.

Result screen will have 2 sections, On the top we will have "My Music"
section with Section heading & "X" list items ( "X" Count is backend
controlled) shown upfront. If results from My Music collection is
greater than X then "See All" CTA with total result count from My Music
will be present just below the list. Clicking on the CTA will bring the
entire list of Audios from My Music followed by the "See Less" CTA
clicking on which will collapse the list to the limited state.

The section below will be a Library section - Header followed by the
result list from Library for the searched keywords. It will be a long
list showcasing all the results.

**Cases:**

1.  **When results from My Music are Zero** - On the result screen My
    Music section will not be present.

2.  **When results from My Music are less or equal to the X values (Line
    items to be shown upfront)** - "See All" CTA will be missing.

3.  **When results from Library are zero** - No need to show the
    collapse state of My Music result section, all the result items will
    be shown upfront on the screen. (See All CTA not required)

4.  **My Music section is in Expanded state & user started searching a
    new keyword or update the keyword** - New/updated results from My
    Music should be in collapse state only as per the defined rules.

If keyboard is on the screen & user starts scrolling to explore the
suggestion or the result list the keyboard should close.

If user clicks on the back arrow icon next to the Search bar, user will
navigate back to the state from where he started the search funnel.

**Use of My Music:**

Meta data for the Local audio files under My Music tab would be 1. Name
of the file, 2. Author name if available, 3. Audio length

For Music label on the Video Screen for third party view we have to show
the Original content by User name, similar to what we do for videos
without selected audio till the time if we can map the user's audio to
the Audio present in Josh's Library.

For first party view, we can show the name of the audio file (Local
Audio) - as the name of an audio have a context for the creator but not
for the other consumers.

If Audio length for the local file is less than the minimum video length
we are allowing the user to upload then the Audio file will not be shown
under the Local Audio tab.

## Error Handling

Handling the Null state when use don't have any local audios, showing
graphic with text. (Designed in Figma)

Handling the "No Storage permission" given state.

## PWA Requirements

No

## BE & CMS Requirements

When user creates a video using local audio from the mobile phone, the
audio requires to be checked for any copyright issue.

Audio identification process: It can be manual process or existing
finger printing model. Till this process happens video can be shown in
TPV & FPV but will not qualify for the feed.

There can be 3 outcomes for the audio identification process:

1.  Audio matches with the Josh Library: The name of the audio in the
    Video detail UI/Feed UI will be replaced by the track name from Josh
    Library.

2.  Audio does not match with the Josh library & have no copyright
    content: In this case no change required & video can now qualify for
    the Feed content. Audio title remain as "Original "Author-name"".

3.  Audio identified as copyright content: Audio will be removed from
    the Video & "Audio Unavailable" will be shown at the place where
    audio title is shown. When user taps on the video or click on the
    Volume icon at the top right, toast message comes as a overlay with
    text "Audio has been removed due to copyright issues".

For the audios from the local which have copy right issue, UI on the "My
Local" tab & Bookmark tab will be as shown in the Figma. Audios cannot
be used for Video creation & clicking on the line item will trigger a
toast message "Audio has been removed due to copyright issues".

On the bookmark section via Discovery page the same UI will be used to
depict the audios with copy right issue. (Shown in the Figma file)

##  Figma

https://www.figma.com/file/kYeklMA5ke0f7O1zLhSujG/Audio-%26-Music-Discovery?node-id=3415%3A19206

## Instrumentation
