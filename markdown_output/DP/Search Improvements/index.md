  ----------------------- ----------------------------------------------
  **Document Status**     NOT STARTED / IN-PROGRESSYellow / READYGreen
  **Product Managers**    
  **Product Designers**   @ product designers
  ----------------------- ----------------------------------------------

## Context & Summary

The PRD will focus on improving the existing search functionality that
will help our users to get access to the more effective topics in a more
effective manner.

+----------------------+-------------------------------+-------------------------------------------------------------------------------+
| **User Journey**     | - **Specs**                   | **Figma**                                                                     |
+----------------------+-------------------------------+-------------------------------------------------------------------------------+
| Click on Search icon | [Recommended                  | https://www.figma.com/file/DfkOqlsRO6uTKnOfEMp5hk/Search?node-id=1285%3A14160 |
| →                    | Searches]{.underline}         |                                                                               |
| Pre-Search/Discover  |                               |                                                                               |
| page will be         | - **Case 1: When user has not |                                                                               |
| displayed            |   searched anything in        |                                                                               |
|                      |   lifetime**                  |                                                                               |
|                      |                               |                                                                               |
|                      |   - *Most searched            |                                                                               |
|                      |     entities(OGC, NER,        |                                                                               |
|                      |     Location) in a month of   |                                                                               |
|                      |     time at the user's        |                                                                               |
|                      |     language level*           |                                                                               |
|                      |                               |                                                                               |
|                      | - **Case 2: If the user has   |                                                                               |
|                      |   searched for something in   |                                                                               |
|                      |   the previous session and    |                                                                               |
|                      |   visits next again**         |                                                                               |
|                      |                               |                                                                               |
|                      |   - *Show recommended         |                                                                               |
|                      |     entities that are based   |                                                                               |
|                      |     on user's last searched   |                                                                               |
|                      |     items*                    |                                                                               |
|                      |                               |                                                                               |
|                      |     - *eg: User searched for  |                                                                               |
|                      |       **"Kohli"***            |                                                                               |
|                      |                               |                                                                               |
|                      |       - *Recommended can be   |                                                                               |
|                      |         "Rohit Sharma" since  |                                                                               |
|                      |         Rohit Sharma is a     |                                                                               |
|                      |         Cricker Player, and   |                                                                               |
|                      |         "Anushka Sharma"*     |                                                                               |
|                      |                               |                                                                               |
|                      |     - *eg: User Searched for  |                                                                               |
|                      |       **"Bangalore"***        |                                                                               |
|                      |                               |                                                                               |
|                      |       - *Recommended can be   |                                                                               |
|                      |         "Bangalore traffic",  |                                                                               |
|                      |         "Mysore" etc*         |                                                                               |
+----------------------+-------------------------------+-------------------------------------------------------------------------------+
| Click on Search bar  | - **Case 1: Zero State**      | https://www.figma.com/file/DfkOqlsRO6uTKnOfEMp5hk/Search?node-id=1262%3A11882 |
| -\>                  |                               |                                                                               |
|                      |   - [Recommended              |                                                                               |
| Suggestions dropdown |     Searches]{.underline}     |                                                                               |
| page will be served  |                               |                                                                               |
|                      |     - *Most searched          |                                                                               |
|                      |       entities(OGC, NER,      |                                                                               |
|                      |       Location) in a month of |                                                                               |
|                      |       time at the user's      |                                                                               |
|                      |       language level*         |                                                                               |
|                      |                               |                                                                               |
|                      | - **Case 2: If the user has   |                                                                               |
|                      |   recent search history**     |                                                                               |
|                      |                               |                                                                               |
|                      |   - [Recent                   |                                                                               |
|                      |     Searches]{.underline}     |                                                                               |
|                      |                               |                                                                               |
|                      |     - *Show the recent 3      |                                                                               |
|                      |       searches from the       |                                                                               |
|                      |       user's search history.  |                                                                               |
|                      |       Show*                   |                                                                               |
|                      |                               |                                                                               |
|                      |   - [Recommended]{.underline} |                                                                               |
|                      |                               |                                                                               |
|                      |     - *Show recommended       |                                                                               |
|                      |       entities that are based |                                                                               |
|                      |       on user's last searched |                                                                               |
|                      |       items*                  |                                                                               |
|                      |                               |                                                                               |
|                      |     - *eg: User searched for  |                                                                               |
|                      |       **"Kohli"***            |                                                                               |
|                      |                               |                                                                               |
|                      |       - *Recommended can be   |                                                                               |
|                      |         "Rohit Sharma" since  |                                                                               |
|                      |         Rohit Sharma is a     |                                                                               |
|                      |         Cricker Player, and   |                                                                               |
|                      |         "Anushka Sharma"*     |                                                                               |
|                      |                               |                                                                               |
|                      |     - *eg: User Searched for  |                                                                               |
|                      |       **"Bangalore"***        |                                                                               |
|                      |                               |                                                                               |
|                      |       - *Recommended can be   |                                                                               |
|                      |         "Bangalore traffic",  |                                                                               |
|                      |         "Mysore" etc*         |                                                                               |
+----------------------+-------------------------------+-------------------------------------------------------------------------------+
| While typing -       | Recommended entities &        | https://www.figma.com/file/DfkOqlsRO6uTKnOfEMp5hk/Search?node-id=1377%3A18505 |
| Recommended entities | Recommended auto completion   |                                                                               |
| dropdown             | keywords distribution % to be |                                                                               |
|                      | 80:20                         |                                                                               |
|                      |                               |                                                                               |
|                      | - Recommended Entities -      |                                                                               |
|                      |                               |                                                                               |
|                      |   - Max recommendations to be |                                                                               |
|                      |     displayed from each       |                                                                               |
|                      |     entity is 2.              |                                                                               |
|                      |                               |                                                                               |
|                      |   - Trending topics           |                                                                               |
|                      |                               |                                                                               |
|                      |   - NERs                      |                                                                               |
|                      |                               |                                                                               |
|                      |   - Sources                   |                                                                               |
|                      |                               |                                                                               |
|                      |   - Locations                 |                                                                               |
|                      |                               |                                                                               |
|                      | Note: % distribution is       |                                                                               |
|                      | configurable, also in case    |                                                                               |
|                      | the entity recommendation is  |                                                                               |
|                      | less than 8, relaxed          |                                                                               |
|                      | suggestion can be more than   |                                                                               |
|                      | \>2                           |                                                                               |
|                      |                               |                                                                               |
|                      | - recommendation should start |                                                                               |
|                      |   from left                   |                                                                               |
|                      |                               |                                                                               |
|                      | - total suggestion should be  |                                                                               |
|                      |   10+1, 1 suggestion from the |                                                                               |
|                      |   word                        |                                                                               |
|                      |                               |                                                                               |
|                      | - recommended searched should |                                                                               |
|                      |   not include UGC profiles n  |                                                                               |
|                      |   sources                     |                                                                               |
+----------------------+-------------------------------+-------------------------------------------------------------------------------+
| When a user lands on | case 1: when a user has       |                                                                               |
| the search result    | clicked on the suggestion     |                                                                               |
| page                 | proposed by the system        |                                                                               |
|                      |                               |                                                                               |
|                      | 1.  Profile: Goes to the NER  |                                                                               |
|                      |     page                      |                                                                               |
|                      |                               |                                                                               |
|                      | 2.  Sources: Goes to the UGC  |                                                                               |
|                      |     page                      |                                                                               |
|                      |                               |                                                                               |
|                      | 3.  Location: Goes to the     |                                                                               |
|                      |                               |                                                                               |
|                      | Search result page            |                                                                               |
|                      |                               |                                                                               |
|                      | 1.  Sections                  |                                                                               |
+----------------------+-------------------------------+-------------------------------------------------------------------------------+

  --------------------------------- ------------------------------------
  **Scenarios**                     **What happens in recommendation**
  User enters more than 3 letters   
  User enters a complete word       
  User enters the complete topic    
  --------------------------------- ------------------------------------

Note

1.  We need to remove the UGC profile/sources from the search result

2.  The suggestion should be done in this order in case of

### Non-exact matches/Incomplete

- Trending hashtags related to the keywords entered

- Profiles

- Sources

- Location

### Exact matches/complete

- Trending hashtags related to the keywords entered

- Profiles

- Sources

- Location

### Post Search

Different sections for :

1.  News

2.  Profile

3.  Sources

4.  Location

i
