  ----------------------- --------------------------------
  **Document Status**     IN-PROGRESSYellow / READYGreen
  **Android Sprint**      add release sprint
  **iOS Sprint**          add release sprint
  **Product Owners**      \@Karandeep
  **Product Designers**   \@Sumedh
  **Android Leads**       @ android leads
  **Android Devs**        @ android devs
  **iOS Leads**           @ ios leads
  **iOS Devs**            @ ios devs
  **QA Devs**             @ qa devs
  **Josh Lite**           YEsGreen / NORed
  ----------------------- --------------------------------

##  Executive Summary

Currently, no functionality is available to filter the audio list
available with respect to genre/moods or other high intent keywords. It
will be useful for the users to explore the audios available.

##  Objective

Adding tags in the form of chips on the Discovery section of the "Pick a
Song" page, clicking on the same will Search the keyword & provide the
list of audio results.

##  Success metrics

List project goals and the metrics you\'ll use to judge its success.

  ------------------------------------------------------------------ --------------------------------------------------------
  **Goal**                                                           **Metric**
  Better exploration of Audios files available in the Josh library   More percentage of Video created with background music
  ------------------------------------------------------------------ --------------------------------------------------------

## Competitive Analysis

Mx TakaTak, Instagram don\'t have this functionality

##  Assumptions

Providing theme based keywords to the users to search Audio will help
them explore the Josh Library in a better manner

##  Functional Specifications (Entire section would be a bottom sheet)

1.  Genre collection section on the Library page.

2.  Placeholder text for audio search bar to be powered by backend API -
    multiple text showing kind of search user can execute.

3.  Search text box to be placed as a part of the header next to the
    Bookmark icon.

4.  Clicking on the Search bar from the "Pick a Song page" should invoke
    the keyboard with suggestion list displayed.

5.  Clicking on the genre chips will open a bottom sheet with list of
    audios from the selected genre, no search bar on this page.

6.  Clicking genre chip from the will be placed at the 1st position in
    the highlighted state on the Search screen, followed by the complete
    chip list with Horizontal scroll enabled. Screen scrolled state -
    when scrolled, horizontal chips will get stick at the top of the
    screen. User can select other genre chips to update the audio list.

## Error Handling

When no chips available to show.

## PWA Requirements

No

## BE & CMS Requirements

**Audio genre/mood chips entity**

Provision for the creation of Audio chips entity.

- Adding & removing Audio chip list (Decking of the chips/keywords, as
  listed in the CMS)

Availability of this list for the Client side.

##  Figma

https://www.figma.com/file/kYeklMA5ke0f7O1zLhSujG/Audio-%26-Music-Discovery?node-id=3415%3A19206

## Instrumentation
