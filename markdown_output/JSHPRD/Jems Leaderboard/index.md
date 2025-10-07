  ----------------------- ------------
  **Document Status**     READYGreen
  **Android Sprint**      R11.A
  **Product Owners**      
  **Product Designers**   
  **Josh Lite**           YEsGreen
  ----------------------- ------------

##  Executive Summary

With the introduction of Jems, leaderboards for key actions inside the
app like top likers, top commenters, top gamers etc provides an exciting
gamification opportunity for users to earn free jems and exchange it for
money or exciting deals from partner brands.

##  Objective

To increase engagement, time spent and overall retention inside the app
through leaderboards.

##  Functional Specifications 

#### **CTA Pages**

There are two ways to land into the leaderboard page:

- Notifications \> Leaderboard chip

- Profile FPV \> Leaderboard icon\

#### **Leaderboard Landing Page**

- Leaderboard categories to be added (decking configurable):

  - Top Gamers

  - Top Likers

  - Top Commenters

  - Top Streamers

  - Top Sharers

  - Top Gifters

  - Top Posters (Camera + Duets)

  - Top Followers

- If the user has participated, their position should always show on the
  top in a separate section

- On tap of name, profile photo or user handle, redirect to user's
  profile

- ~~Ranking colour and profile photo ring colour to be red for #1, #2
  and #3~~

- On tap of the thumbnail icon, redirect to a detailed view of that
  video

- Leaderboard starts at 6:00 AM and ends at 11:59 PM post which it
  resets (configurable)

- If the user has participated in any of the categories, on coming
  inside the leaderboard page after those day's results are announced,
  show congratulatory popup

- Total number of Jems assigned to the winners are (configurable):

  - 1st: 50 Jems

  - 2nd: 10 Jems

  - 3rd: 5 Jems

- Congratulatory popup should show total number of Jems collected across
  categories and description should capture total number of categories
  won

- Share achievement to be leveraged from contest flow

- Once the leaderboard resets and no results are populated yet, show
  empty state

- If number of entries within a category \< 3, hide the category

- Share description: 

  - [Non-participant:]{.underline} Checkout the Josh leaderboard: {URL}

  - [Participant:]{.underline} Checkout my rank in the Josh leaderboard:
    {URL}\

#### **Hero Banner**

- Banner will have two states:

  - Participation Period - 6:00 AM to 11:59 PM (configurable)

  - Winners Period - 12:00 AM to 5:59 AM (configurable)

- Both states will have their respective countdown timers

- Background image banner to be configurable

- Banner will also have an informational ticker with multiple
  configurable text boxes that will horizontally scroll for both states

## Notification Requirements

\
**Results Notification**

- Once the results are out, send a push notification to the participants
  with the text 'Leaderboard results for DD Month are out. Tap to view
  your rank.'

- On tap of the notification go to the notification results landing page

- If results page has expired, then land to the active participation
  page

- There should be no constraint of social notifications only sending 1 /
  hour
