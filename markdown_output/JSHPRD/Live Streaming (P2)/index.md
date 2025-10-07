  ----------------------- --------------------
  **Document Status**     READYGreen
  **Android Sprint**      R11
  **iOS Sprint**          add release sprint
  **Product Owners**      
  **Product Designers**   
  **Android Leads**       @ android leads
  **Android Devs**        @ android devs
  **iOS Leads**           @ ios leads
  **iOS Devs**            @ ios devs
  **QA Devs**             @ qa devs
  **Josh Lite**           YEsGreen
  ----------------------- --------------------

##  Executive Summary

In R10, we launched live-streaming with video and audio rooms. As part
of our efforts in continuously improving the experience, we are looking
to add some important and functional features that make it easier for
people to create and share livestreams, including room scheduling,
waiting areas, room invitations and others.

##  Objective

Goal is to improve two key areas: creation and consumption. For
creation, we are launching scheduling of rooms that enables users to
create a room before time and enable interested people to RSVP. For
consumption, we are optimizing the share path by enabling users to
invite others to the live stream.

##  Technical Requirements

####  **Schedule Room**

- Scheduling comprises of two elements: date and time

- Default date to be set to current date

- Default time to be set to the nearest upcoming hour where minimum time
  between current and set time \> 30 minutes (ex: if current time is
  3:15pm, then set time should be 4:00pm but if current time is 3:45pm,
  then set time should be 5:00pm)

- By default, date and time will open with default options and on tap of
  either, the calendar or timepicker will open

- Minutes in timepicker will be every 5 minutes (ex: 30, 35, 40 etc)

- On tap of date or time, component should appear and BottomSheet should
  expand with a slide up animation

- UX of component and BottomSheet animation is an important factor and
  should be managed elegantly

- User can toggle between months using the left and right arrow

- If the calendar month is the current month then disable back arrow,
  else enable

- On tap of \'Schedule Now\', dismiss the entire BottomSheet including
  the create room one, come to homepage and show the scheduled flash
  message

- On tap of \'Go Back\', discard the selections / changes made and
  dismiss the BottomSheet (create room BottomSheet will show below it)

####  **Invite to Room**

- Shows a list of friends (mutually followed users)

- If no friends exist, show empty state and hide the search bar

- List will be displayed in an alphabetical order

- Search will enable users to search for specific people

- As soon as the user hits the invite button, show a flash message if
  they are inside the app or a push notification if the app is in the
  background

- Tapping on \'Go to Room\' will open the room and add the user as a
  viewer or front row

- Tapping on cross will dismiss the flash message

- If a user joins the room via a deeplink but the room has already ended
  and does not have replay on, take to homepage and show \'Room Ended\'
  flash message\

#### **Edit Room Details**

- Opens Edit Room Details from 3 dots inside room \> Edit Room Details
  popup

- Same funnel as edit inside Create Room\

#### **Local Notifications**

- Extend all event triggers that currently power flash messages into
  push notifications sent locally\

#### **Raise Hands Nudge**

- For first time users, show raise hands educational popup so that users
  become aware of what the feature is about

##  Figma

Type /image to add mockups, diagrams, and screenshots related to the
requirements.

## Instrumentation
