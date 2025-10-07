  ----------------------- --------------------------------
  **Document Status**     IN-PROGRESSYellow / READYGreen
  **Android Sprint**      add release sprint
  **iOS Sprint**          add release sprint
  **Product Owners**      \@Karandeep
  **Product Designers**   \@Mimansa
  **Android Leads**       @ android leads
  **Android Devs**        @ android devs
  **iOS Leads**           @ ios leads
  **iOS Devs**            @ ios devs
  **QA Devs**             @ qa devs
  **Josh Lite**           YEsGreen / NORed
  ----------------------- --------------------------------

##  Executive Summary

Currently users cannot do the string search for Videos. Video content
type should be a part of a Search results as Video content is our main
value proposition for the users as a player in Short Video space.

Along with the String search for videos, few additional changes have
been identified which will enhance the user experience:

- Currently the search in Discovery is not Inline & it is a 2 step flow

- Recent search history - Not Available

- Contextual search (Showing keywords to choose from that have an
  affinity with the characters typed by the user), showing search
  results on enter/selection of the keyword Vs current functionality of
  Search per character.

- Search Video by string - Not available

- Showing zone/Fan clubs as a result of Search - Under All Tab

##  Objective

Showing video content type as Search result, it will reduce the steps
for the user to consume the desired video content. Videos have high CTR
& are more engaging too.

##  Success metrics

List project goals and the metrics you\'ll use to judge its success.

  ----------------------------------------------------------- -------------------------------------------------------------------------------
  **Goal**                                                    **Metric**
  User can find the desired video content via search easily   More consumption of Videos via Discovery Search
  As search will be inline & single step                      More people utilising search functionality to find the desired content/users.
  ----------------------------------------------------------- -------------------------------------------------------------------------------

## Competitive Analysis

Both MX TakaTak & Moj show videos as a result for the string search.

##  Assumptions

List any assumptions you have about your users, technical constraints,
or business goals.

##  Functional Specifications

### **Making the search in discovery Inline, single step flow: To be done in R13**

Adding a search text box at the top of the Discovery page, above the
Discovery, Trending & Music Tabs.

**Clicking on the Search text box** - Opens a keyboard inline overlaying
the default screen with "Recent Search History" chips on the top
followed by the "Popular Videos for you" section. (if Recent Search
History available otherwise only "Popular Videos for You section will
come).

"Back arrow" comes on the left of the Search Text box - clicking on the
same will take user to the default Discovery page state.

When user starts searching for keyword, a cross icon appears on the
right corner within a text box, clicking on the same will bring user to
the no keyword search state (With recent history items & popular videos
for you).

## **Search Behavior:**

### **Multiple Placeholder text on the Search bar: To be done in R13**

User can search normal String, with Hash(#) as prefix & with @ as
prefix. Education for the same will be done using placeholder texts
inside the search bar (Via API) E.g. Search "Funny content", Search
"@Kapil Sharma" for users & Search "#Holi" for hashtags. **(Multiple
default placeholders to be shown in the Search bar on the Discovery page
to showcase the type of search possible (UI would be similar to
Instagram, one placeholder text transitioning to other))**.

### **Type ahead Keywords with suggestive entities for Search - To be done in R13**

Two ways it will be helpful:

- Users don't have to type the full text to search, suggestions are
  available for the user to choose. (Less typing time)

- No display of Search result for intermediate characters, loading of
  the search result at client side once user selects the keyword to
  search from suggestions or press enter) 

When a user starts typing in the search bar, we suggest typeahead
keywords (related to the text entered by the user) & entities such as
users & hashtags which have a match with the typed string. (Maximum 10
suggestions followed by **"See All Result"** CTA).

Click on the "See All Result" CTA will search for the typed CTA & take
user to the result page, similar to pressing the "Enter" CTA from
keyboard.

Suggestion list: Maximum 5 Type ahead keyword suggestion & rest 5 can be
the entity suggestions (Mixture of User/accounts & hashtags).

But if user use @ as prefix for the search then we can suggest all 5
users/accounts entities along with 5 typeahead keywords (That too with @
as prefix)

If user use \# as prefix for the search then we can suggest all 5
Hashtag entities along with type ahead keywords (That too with \# as
prefix)

If Entity suggestions are less than 5 then Type ahead suggestion should
fill in to complete the list to 10 & vice versa.

In case of no suggestion list available, "See All Result" CTA will be
shown & clicking on the same will work similar to pressing "Enter" CTA
i.e. show results for the string typed.

**Normal String Search: Partially done in R12**

If a user search for the normal string, user to be landed on the "All"
tab with multiple content type search results displayed. In default
state Videos section will be decked at the top, followed by Users than
Hashtags & Music section.

In case there is an exact text match with the verified profile, managed
profile & Ghost profiles, then the user section will be decked at the
top followed by Videos, Hashtags & Music.

If there is an exact match with the Zone, then the Zone section will be
decked at the top followed by other sections.

**With Hashtag(#) as prefix search:** **Done in R12**

If user search with hashtag as prefix, user to be landed on the
"Hashtag" tab with list of hashtag search results. (Intent to search for
Hashtag shown by the user)

**With @ as prefix search: Done in R12**

If user search with @ as prefix, user to be landed on the "Users" tab
with list of user profile search results. (Intent to search for profiles
shown by the user)

**Select Entity from the suggestion List: To be done in R13**

If user selects the entity (User or hashtag) from the suggestion list
than he will directly lands on the entity page.

Once user is on the search results screen & started exploring results
using multiple tabs (All, Video, User, Hashtag, Music) from any tab if
user start searching for other keyword using search bar, he will get
suggestive keywords related to the text entered. Once he press enter or
select a type ahead keyword from the suggestion list, search results
will get updated as per the new keyword or if he selects the entity then
lands on the entity page as described above.

If Keyboard in on the screen & user starts scrolling the screen to
explore the content, keyboard should close, should be implemented
wherever applicable.

**Recent Search History section - To be done in R13**

#### Six (Controlled by Config) recently search items (Including String/keyword, keyword with @ prefix, keyword with \# prefix or the entities like User profile or the Hashtag visited by the user) in the form of Chips UI, with option to remove them from history one by one (using a cross icon).

When user selects to remove the search history item (one by one), no
feedback toast only the list item will be removed. For the removal of
the last/single item from history the entire section (including heading)
will disappear & the page will have "Popular Video for you" section
only.

**Keyword Searched Chips** - Search Icon with the string user searched
for.

**Entity Searched Chips** - For Users, account's display picture along
with the account name & for Hashtags it would be hash icon along with
the hashtag name. (Depicted in the Figma file)

**Recent Search History Page:** "See All" CTA at the top right next to
the Recent history heading, clicking on the same will redirect user to
the detailed recent history page with the complete (Limited to "X"
count) list of keywords & entities searched or visited by the user via
Search funnel. Right aligned cross icon for each line item to remove the
recent search items individually, also a "Clear All" CTA on the top
right as a part of a Header to clear the entire recent history at once,
clicking on the same will trigger a pop-up for confirming the action,
once confirmed the entire history of the user will be removed & users
lands on the Default screen with "Popular Videos for You" section (No
recent search history).

On the Recent Search history page, list will also have two type of items
one is the Keyword Searched & the 2nd is Entity Searched. UI for the
list item would be as per their type. For Keywords, search icon will be
shown on the left followed by the String text & for the entities like
users/accounts, display picture will be on the left followed by user
name &below it the account id as depicted in the figma file. For Hashtag
entity, hash icon on the left followed by Hashtag name & View count as
per figma.

**Clicking on the Chip from the Default screen or list item from the
Recent search History page:**

Clicking on the recent "keyword searched" directly showcase the Search
results for the Keyword string & if user clicks on the "entity searched"
then directly the entity page will open. (Hashtag page or User/Account
profile page)

**What will come in Recent Search History: To be done in R13**

Recent Search history will include keywords & entities:

1.  Typed keyword in case of Enter click by user to search

2.  Keyword selected by the user from the suggestion list for Search

3.  Entity selected by the user from the suggestion list

### **Different Tabs in Search result page:**

Tabs sequence would be "All", then "Videos", then "Users", then
"Hashtags" & last "Music" & it will get repeated. Count of the result
for each content type to be shown next to the tab heading.

**All Tab: Done in R12**

Content Type Sections:

- **Video Section:** Section heading & "See All" CTA followed by grid of
  6 -

- **Zone section:** Section heading with horizontal cards in the form of
  carousal, showing results of Zones for the search keyword. Card will
  have Display picture, Name, Category, N.o of super-fans & N.o of
  posts. Also a group of 8 images (Thumbnails) from the fan-club page to
  showcase the collection. Clicking on the card will redirect user to
  the Fan-club page. "Plus" CTA is available on the Fan-club card,
  clicking the same will make user follow the fan-club with followed
  feedback to the user as shown in the Figma. If a user is swiping
  horizontally within the zone section then carousel will work otherwise
  the horizontal swipe will shift the tab. (As in current
  implementation)

- **Users section:** Section heading & "See All" CTA followed by a
  horizontal carousel of 3 rows of user profile list. If user is swiping
  horizontally within the user profile section then carousel will work
  otherwise the horizontal swipe will shift the tab (As in current
  implementation)

- **Hashtag section:** Section heading with "See All" CTA followed by
  horizontally scrollable Hashtag chips (Maximum 20 count)

- **Music section:** Section heading & "See All" CTA followed by a
  horizontal carousel of 2 rows of music tracks list. If user is swiping
  horizontally within the music track list section then carousel will
  work otherwise the horizontal swipe will shift the tab (As in current
  implementation)

"See All" CTA: Clicking on the same will navigate user to the specific
content type Tab with all the search results listed for the keyword
searched, also maintain the position of the content on the screen. For
e.g if user navigates to the Video tab via "See All" CTA from 3rd video
grid on All tab, then those videos of 3rd grid should be upfront on the
screen with up & down scroll enabled. Similar behaviour for other tabs
also.

**Zone: String Search on data points - Done in R12**

Zone name, Hashtags attached, Category name, Description (Can be picked
from the most Active Social media platform for the celebrity) etc.

**Video: String Search on data point**- **Done in R12**

Author name of a video, Title/Heading, Hashtags, other data available
like Mood, Genre etc. around Audio track used in a video (recently added
to Content ES)) (Text match & Fuzzy match Algorithm)

**New Video Tab: Done in R12**

Addition of a new Video Tab in the Discovery Search screen (Along with
All, Users, Hashtags & Music), showing video results in the grid design
format for the searched keyword.

Users can click on the Video thumbnail (GIF) to open the full video play
screen.

**To be Done in R13:**

Some Videos with bigger thumbnails - On the basis of resolution &
engagement rate of the videos.

**Hashtag tab: Done in R12**

Hashtag name, Post count on the left, with what hashtag is attached to
on the right e.g: Contest or Zone category such as Celebrity, Mood,
Festival etc as text along with the Zone display pic as icon. Clicking
on the same will redirect user to the specific page of the zone, contest
etc.

For the hashtags which are not attached to any contest or zones, the
behavior will be redirecting to the hashtag page.

**To be done in R13:** \*In current implementation we show post views
instead of post count but post count would be a better metrics to show.

**User Tab: - To be done in R13**

Zone will also come as a part of a search result list under User Tab,
they will be decked on the top of the User page as cards in the carousal
format (Horizontally placing all the cards which comes as a result of
search). Below the card there would be normal list of users as decked in
the current implementation.

Clicking on the card (anywhere) will redirect user to the Zone page.
Clicking on the plus icon will make user follow the zone (Follow
feedback will be there)

**Loading screen: - To be done in R13**

Loading screens to be updated to shimmer screens - Figma have loading
screens for each type.

**Ranking Logic for Search results: - Already parked with BE team**

**Problem Definition:**

For User search results, after Verified profiles as result, some blank
profiles (Low quality profiles) get decked. Similarly for Hashtag search
results too, some hashtags with less video count get decked at the top.

**Proposed Solution:**

**Enhancements around decking Logic for Search Results: (Including some
additional parameters for content ranking logic along with the fuzzy
match results)**

**Videos -** Including Views/Engagement metrics for the videos to decide
the decking (Highest views ranked at the top) along with Text match &
Fuzzy match algorithms.

**Users** - N.o of posts created by the user + N.o of fans & hearts
(User Quality Metrics) to be used to decide decking with verified
accounts at the top (present In Current logic) - To prevent empty
profiles from coming on the top.

(User Profiles with zero content should be excluded from the result
list - In \"ALL tab\") Maybe later **-** User to User Affinity
(Location, Phone book contact, interests can also be factored) & user
interests can also be incorporated.

**Hashtags** - N.o of Videos & Views associated with a Hashtag, with
highest ranked at the top. (To prevent Hashtags with Less videos to come
on top)

We can enhance the current logic for the ranking with the help of the
Analytics team. (Including parameters & deciding their weightage)

(Ranking should be within the results groups - Like for Exact text match
results should be decked on the top, we can implement ranking among them
using new fields listed above. Followed by highest ranked fuzzy match
group (Ranking among them) (Can decide the cutoff values for match
results to make multiple groups)

## Error Handling

List all product and feature errors and edge cases here.

## Notification Requirements

Not required

## BE & CMS Requirements

Search API to include Video content.

Popular Videos for you list - Trending Video API can be used here to
showcase the list of videos.

##  Figma

https://www.figma.com/file/iSoeHrXUzvPAYHE8pFoY9V/Search-flows?node-id=1065%3A1086

## Instrumentation

[https://docs.google.com/spreadsheets/d/1f3mHeHN2ivXaYZncxBoVI3Y619bfwlX2O_omn_8EB_Y/edit#gid=1595704841&range=A121](https://docs.google.com/spreadsheets/d/1f3mHeHN2ivXaYZncxBoVI3Y619bfwlX2O_omn_8EB_Y/edit#gid=1595704841&range=A121){card-appearance="inline"}
