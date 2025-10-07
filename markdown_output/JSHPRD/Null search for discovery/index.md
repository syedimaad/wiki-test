  ----------------------- ----------------------------------------------
  **Document Status**     NOT STARTED / IN-PROGRESSYellow / READYGreen
  **Android Sprint**      add release sprint
  **iOS Sprint**          add release sprint
  **Product Owners**      \@karandeep
  **Product Designers**   \@mimansa
  **Android Leads**       @ android leads
  **Android Devs**        @ android devs
  **iOS Leads**           @ ios leads
  **iOS Devs**            @ ios devs
  **QA Devs**             @ qa devs
  **Josh Lite**           YEsGreen / NORed
  ----------------------- ----------------------------------------------

##  Executive Summary

Null Search Case for Discover: All, User, Hashtags & Music section.
Currently if zero result is found for the searched keyword, "No result"
text is shown to the user. (Funnel ends here, No CTA for the user)

3 possible scenarios identified for the NULL Result:

1\. Spelling mistakes

2\. Searched content not present with Josh &

3\. Random group of alphabet searched.

**Current Search Algorithm:** Exact Text match & Fuzzy match - Cosine
Similarity. (
[https://nanonets.com/blog/fuzzy-matching-fuzzy-logic/](https://nanonets.com/blog/fuzzy-matching-fuzzy-logic/){card-appearance="inline"}
)

**Understanding 3 scenarios:**

1.  **Spelling Mistake:** Fuzzy search takes care of this scenario as
    suggestions are on the basis of similarity rather than exact match,
    so in most of the cases the user is shown the desired results.

2.  **Search content not present with Josh:** Not able to reproduce such
    case, as in most of the cases results are available (Exact or
    Similar)

3.  **Random group of Alphabets:** Abusing Search functionality by user,
    but this is the case where Null results came mostly & even if the
    result list is available that is less in count (4-5) with mostly
    blank profiles or hashtags with 2-3 content attached.

##  Objective

Ideal flow would be that, for any kind of keyword search funnel should
not end with Zero result text. 

We should guide our users with Similar searches/Trending topics option &
also show the best content available in Josh which might be of user's
interest & the funnel continues as he consumes content, follows other
users & explores music etc.

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

When the results for the searched keyword by user is less than or equal
to 10 in count we will show the below mentioned results: 

**On Client side - 3 Sections of the Search result page:**  Figma:
[[Link]{.underline}](https://www.figma.com/file/iSoeHrXUzvPAYHE8pFoY9V/Search-flows?node-id=1065%3A1086)

1.  **Result Section:** Showing results for the Searched keyword:

    1.  Show search result list if any (Less than or equal to 10) 

    2.  Null result: Text & Graphic stating - "Zero result for your
        search"

**2. Keyword Suggestion section:** 

**A. Similar Searches:** On the basis of the keyword searched by the
user - suggestion of new keywords using Anagram Solver (
[https://www.thewordfinder.com/anagram-solver/](https://www.thewordfinder.com/anagram-solver/){card-appearance="inline"}
) 

(Anagram Solver: It is a tool used to rearrange letters to generate all
the possible words from them)

a\. Upto X keywords - clicking on the same directly searches the
keyword.

b\. Decking of keywords - Longest keyword & starting with the same
alphabet as original searched keyword will be on top. (Ignoring 2 letter
words)

c\. Should remove this section if Anagram solver is not giving any
result.

\
B. **Trending Topics Suggestion:** List of Trending Keywords, defined
via CRM. 

       

**3. Popular Content:** Showing what we show currently when a user
clicks on the Search button. (Most appropriate as per business goals &
user experience) - Different for different sections of the discovery
page. (E.g: For User section - Popular users, For Music section -
Popular music list)

(Real Time update for Result list (Currently present) & Similar
Keywords - Via Anagram Solver)

**Search Result List Ending:**

No demarcation for the user to know that the search result list ends,
text to be shown "Showing 20 Search Results".

## Error Handling

List of all the edge cases:

- When Anagram solver gives no result for the searched keyword. (Or only
  2 letter words)

## Notification Requirements

No

## PWA Requirements

No

## BE & CMS Requirements

API level changes required for conditional search results - For Zero &
Limited results.

Anagram Solver to be integrated in the search funnel to provide Similar
keywords. Ranking logic to be applied for decking of these Keywords.

##  Figma

https://www.figma.com/file/iSoeHrXUzvPAYHE8pFoY9V/Search-flows?node-id=1065%3A1086

## Instrumentation
