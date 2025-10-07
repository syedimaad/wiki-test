  ----------------------- --------------------------------
  **Document Status**     IN-PROGRESSYellow / READYGreen
  **Android Sprint**      add release sprint
  **iOS Sprint**          add release sprint
  **Product Owners**      
  **Product Designers**   \@mimansa
  **Android Leads**       @ android leads
  **Android Devs**        @ android devs
  **iOS Leads**           @ ios leads
  **iOS Devs**            @ ios devs
  **QA Devs**             @ qa devs
  **Josh Lite**           YEsGreen
  ----------------------- --------------------------------

##  Executive Summary

Currently, no suggestion of keywords for the users to directly search
the results when user start the typing, recent search history is also
unavailable.

##  Objective

By providing the suggestive keywords as a type ahead & storing the
recent search history, search feature becomes more useful for the users.

##  Success metrics

List project goals and the metrics you\'ll use to judge its success.

  ------------------------------------------------- -----------------------------------------------------------------------
  **Goal**                                          **Metric**
  Increase the usage of Discovery Search by users   More consumption/exploration of content via Discovery Search section.
  ------------------------------------------------- -----------------------------------------------------------------------

## Competitive Analysis

Recent Search history feature is available in Instagram & Mx Taka Tak
both. Suggestive type ahead keywords & entities is present in Instagram.

##  Assumptions

Users have a tendency to do the repeat search & also type ahead &
suggestive entities will help user reach the desired result fast.

##  Functional Specifications

**UI:** When the user clicks on the Search bar to open an on-screen
keyboard inline - In the default screen the recent search history will
be shown at the top limited to 6 items followed by the Popular Videos
for you section.

**Recent Search Keywords** -

Six recently search items (Including String/keyword, keyword with @
prefix, keyword with \# prefix or the entities like User profile or the
Hashtag visited by the user) in the form of Chips UI, with option to
remove them from history one by one (using a cross icon).

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

**Type Ahead & Entity suggestion:**

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

## Error Handling

List of all the edge cases:

- No Recent Search keywords available - (User have not searched any
  keyword yet or cleared the recent History) - This section should be
  removed from UI (Designed in Figma)

## Notification Requirements

No Notification required for the same.

## PWA Requirements

No Requirements of PWA pages.

##  Figma

https://www.figma.com/file/iSoeHrXUzvPAYHE8pFoY9V/Search-flows?node-id=1065%3A1086

## Instrumentation
