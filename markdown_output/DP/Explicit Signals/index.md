  ----------------------- ----------------------------------------------
  **Document Status**     NOT STARTED / IN-PROGRESSYellow / READYGreen
  **Product Managers**    
  **Product Designers**   
  ----------------------- ----------------------------------------------

## Context & Summary

To extract explicit signals from users which can be shared with the
backend to help in personalizing the feed 

Identify interactive behavior of users:

Understand user motive to determine the direction to be followed further
**USP - personalization**

## First principles note

*Existing :*

- follow/block features currently active only for newspaper - not
  existing for individual topics/genre

- Show more is currently not present 

- Show less is active for genre - more articles from same genre will be
  removed from the feed - less effective  Understand the existing flaw:

The action of clicking on show less indicates dislike in the back end
but the exact reason why is not implied 

The IGs for articles or videos might be very broad and enabling actions
based on the assumption of reason for like/dislike might not be
effective 

#### ***New ideas for explicit signals :***

- Add Show more:

  - Publisher/Genre/Location

- Improvements to Show Less:

- Add a second layer to explicitly ask the user for the reason for Show
  less (similar to 3 dots facebook does on Notifications). Is it because
  of:

  - Publisher ? - block option. DD & Vimal Inputs: Pull L3 Genre and
    other options under 3 dots upfront in feed list/spv. 

  - Genre ?

  - location is irrelevant ?

  - NER(celebs/locations/landmarks)

  - There can be an option of none of the above/ skip 

  - Add an option to "update your interests"

- Add to favorites / Save articles / save to collection - If user is
  saving articles, weightage can be added to the specific genre \
  *\*There should be a threshold *

- Share with friends - in app or copy link  *- Requires introducing
  Share inside Social layer. Can be picked after the Social layer is
  flawless.Prompt to follow can be shown in the immediate next session *

- *Report :*\
  *Existing - Fake/ Misleading*\
  *Biased*\
  *New - Fake*\
  *Biased*

- *Block - Undo Nudge - ⅔ sec *

- *Follow - NLF card recommendations *

- *Detail page's follow nudge is existing: on the Ad (reduces
  discoverability) Rethink design*\

- *Point system to add weightage for : Hashtag(Genre)NER
  Source/Publisher Recommendations based on points *

- Articles shared or received via share need to be mapped with existing
  user behavior - genres/publishers/IGs etc. Weightage to the genre of
  the item shared or received can continuously increase/decrease based
  on the user's consumption of those items (after the consumption
  exceeds some threshold). 

- Eg: If the user doesn't open items shared to him, weightage shouldn't
  increase. 

- Prompt to choose interests during on boarding (provide an option to
  skip/do this later) 

'Choose Topics that interest you'

Find out related genres and suggest, when a genre is clicked. \
Instead of texts, let the design have Tiles (image+ overlapped text) so
that it appears bigger and gets traction

- ME cards - nudging users to discover a tab. When user clicks on
  individual topic tab \> show other relevant topics as recommendations

ex: User licks on Share market tab \> recommend business and finance
through Inapp/ ME carousel in Depth 0 - Slot 2 ?

\

- Location Card Enhancement: 

Suggest locations based on the user's detected loc 

Capture signals from articles viewed by user from different cities and
give suggestions

Creative: ME carousel/ In-app nf

Top 2nd location ranked in user's recent location bucket.

- Analyze watch time of video articles  - Pass the data to Reco. 

##  Objective

- To get more explicit signals from users 

- To improve feed personalization based on user inputs 

- To have a point tracking system for content categorization

Provide context on this project and explain how it fits into your
organization\'s strategic goals.

##  Success metrics

List project goals and the metrics you\'ll use to judge its success.

  ------------------------------------ --------------------------------------------- ------------------- ------------------
  **Goal**                             **Metric**                                    **Current Value**   **Target Value**
  e.g., Simplify the user experience   e.g., Customer satisfaction score increases                       
                                                                                                         
  ------------------------------------ --------------------------------------------- ------------------- ------------------

## Competitive Analysis

Provide information on your top competitors here.

## Assumptions

List any assumptions you have about your users, technical constraints,
or business goals.

## ❗ Call-outs

List all the call-outs that we want to highlight to our stakeholders

##  Functional Specifications

List all product and feature requirements here.

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

## Reference Materials

Add links to research and other key documents here.

## Additional Notes

Add additional notes or comments, if any.

##  Figma

Type /image to add mockups, diagrams, and screenshots related to the
requirements.

## Instrumentation
