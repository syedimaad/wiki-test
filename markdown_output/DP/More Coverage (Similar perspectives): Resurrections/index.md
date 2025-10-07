  ----------------------- ----------------------------------------------
  **Document Status**     NOT STARTED / IN-PROGRESSYellow / READYGreen
  **Product Managers**    
  **Product Designers**   @ product designers
  ----------------------- ----------------------------------------------

17

## Context & Summary

We had implemented similar perspectives earlier. This worked well but
had a tech limitation due to high load. Idea is to bring back similar
perspectives bar banking on the tech optimizations that are now
available.

## First principles note

- It enables users to go deeper into the a particular story and know all
  the relevant details

- Similar perspectives showcases Dailyhunt as a non-biased aggregator
  featuring all different opinions from different media houses

##  Objective

- Bring back similar perspectives with tech optimizations to manage load

- Align the implementation with new reco

- Tweak it to merge with the new designs

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

##  Functional Specifications

Older spec doc:
[https://docs.google.com/document/d/17-H1VVX5yc8Ic0ymfEk6n07-uE6ca6kgtFED4ei7yLQ/edit](https://docs.google.com/document/d/17-H1VVX5yc8Ic0ymfEk6n07-uE6ca6kgtFED4ei7yLQ/edit){card-appearance="inline"}

[https://docs.google.com/spreadsheets/d/118GFO6jPu7ZHl-ilsntjj826Q2WjrFfz4Ohpi0n61MA/edit#gid=1777803125](https://docs.google.com/spreadsheets/d/118GFO6jPu7ZHl-ilsntjj826Q2WjrFfz4Ohpi0n61MA/edit#gid=1777803125){card-appearance="inline"}

  ------------------------------------------------------------------------------------------ ---------------------------------------------------------------------------------------
  **Feed**                                                                                   **Detail page**
  [Link](https://www.figma.com/file/HVSGkagDKr9FmmRnv9QGs1/Feed-Cards?node-id=380%3A19865)   [Link](https://www.figma.com/file/9gdvlxIwxbYX5SIKn8x7HO/Articles?node-id=224%3A5197)
  ------------------------------------------------------------------------------------------ ---------------------------------------------------------------------------------------

  ----- --------------------------------- --------------------------------------- --------------------------------------------------------------------------------------
        **Elements**                      **Display behavior** (Element Status)   **Action behavior**
  1\.   Headline                                                                  Click will lead to article detail page for
  2\.   Publisher name                                                            Click will lead to article detail page of this article
  3\.   Verification tick                                                         Click will lead to article detail page of this article
  4\.   Timestamp (only in detail page)                                           Click will lead to article detail page of this article
  5\.   More coverage card bar                                                    Scrolling will show other cards that are present under more coverage of this article
  ----- --------------------------------- --------------------------------------- --------------------------------------------------------------------------------------

**New config**

+----------------------------------+----------------------------------+
| **Item**                         | **Details**                      |
+----------------------------------+----------------------------------+
| No. of cards in one MC           | 1+4\                             |
| collection                       | 1+5\                             |
|                                  | Min: 4, Max: 5\                  |
|                                  | (BE constraint: Max of 20 story  |
|                                  | cards per page)                  |
+----------------------------------+----------------------------------+
| No. of MC collections in one     | Min: 0\                          |
| page                             | Max: 2                           |
+----------------------------------+----------------------------------+
| User affinity params to be       | - Follow/Block                   |
| considered : Runtime compute     |                                  |
+----------------------------------+----------------------------------+
|                                  |                                  |
+----------------------------------+----------------------------------+

+----------------------+----------------------+----------------------+
|                      | **Approach**         | **Constraint**       |
+----------------------+----------------------+----------------------+
| How does a card      | - Density of MC      | - Exception- **P0    |
| qualify for more     |                      |   not to have MC**   |
| coverage in feed?    |   - min threshold on |                      |
|                      |     no. of similar   | - No distancing      |
| How do we shortlist  |     items            |   needed, back to    |
| 1-2 cards per page   |                      |   back card can have |
| for more coverage?   | - Flag on content    |   MC                 |
|                      |   (Top Story\>       |                      |
|                      |   inform worthy      |                      |
|                      |   global             |                      |
|                      |   only\>trending or  |                      |
|                      |   LR/GLOBAL) till D2 |                      |
|                      |                      |                      |
|                      | - D3+ based on LR    |                      |
|                      |   score and fallback |                      |
|                      |   as GLOBAL score    |                      |
+----------------------+----------------------+----------------------+
| Mapping a story to   | - Collection         | - One collection can |
| its More coverage    |   Creation &         |   have only one item |
| (similar             |   sequence of        |   per publisher      |
| perspectives )       |   stories to be      |                      |
|                      |   decided at the     | -                    |
|                      |   time of enrichment |                      |
|                      |                      |                      |
|                      | - **Filter**         |                      |
|                      |                      |                      |
|                      |   - Similarity (A \< |                      |
|                      |     S \< B ), B \> A |                      |
|                      |                      |                      |
|                      |   - Publish time of  |                      |
|                      |     key elect items  |                      |
|                      |     (t-x, t+y), y\>x |                      |
|                      |                      |                      |
|                      |   - Content Quality  |                      |
|                      |     score \> CQ      |                      |
|                      |     (90?)            |                      |
|                      |                      |                      |
|                      |   - Not from same    |                      |
|                      |     source as Key    |                      |
|                      |     elect            |                      |
|                      |                      |                      |
|                      |   - Not ICC content  |                      |
|                      |                      |                      |
|                      |   - BIBO partners    |                      |
|                      |     only             |                      |
|                      |                      |                      |
|                      | - **Feed Ranking**   |                      |
|                      |                      |                      |
|                      |   - Explicit follow- |                      |
|                      |     Recent to be     |                      |
|                      |     ranked first,    |                      |
|                      |     rest follow CE   |                      |
|                      |     sequence         |                      |
|                      |                      |                      |
|                      |   - Remove blocked   |                      |
|                      |     sources          |                      |
+----------------------+----------------------+----------------------+

In case of MC only on details page (notification , share and non feed MC
scenarios) we will not be doing re-ranking, but following the original
ranking provided at ingestion after client has removed the blocked
source (define the minimum number of items we want to show on detail or
do you want to show all which qualifies after filtering blocks)

**Element:**

**Feed**

1.  Interactions:

    1.  Scroll: Directs to next MC card

    2.  Click on whole MC card zone: Opens article detail page for this
        MC card

    3.  Swipe will lead to next story, and parent item will be added in
        swipe as first story.

    4.  Parent story spv will have card position as -1 so that more
        coverage items have same card positions in SCV & SPV

**Detail View of Key elect**

1.  Same MC carousel at bottom as Feed

2.  Swipe left will take to detail page of next feed story

3.  Click on whole MC card zone: Opens article detail page for this MC
    card

    1.  There will be no nesting

    2.  There will be no MC cards for this article

    3.  Swipe from this story will take user to detail page of next feed
        story. Parent item will be added as first story in swipe stream
        (same logic for card position as feed)

Decisions:

1.  ~~If feed card didn't qualify for MC in feed, in detail view also
    there will be no MC cards~~ If MC exist for the hero article, show
    MC in detail view (min: , max: )

**Specs:**

1.  More coverage will be a carousel of cards (min-max)

2.  Each card to contain

    1.  Headline as per publisher

    2.  Publisher Name

    3.  Verification tick (if any)

3.  Click on anywhere on the card will lead to article detail page for
    that article

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

**Open points:**

1\. Defining Similarity range (s1, s2) - ***As per abhirup, even items
which have similarity of 98-99 might not be duplicate and probably will
be talking about different topic but same NERs***

2\. More Coverage items to have published date within x hours of the
main item\'s published date: Defining X hrs - ***Extracting data of
similar items with threshold and publish date to decide the values we
should configure for creating the more coverage collection***

**Tech discussion:**
[https://docs.google.com/document/d/1HouxPsYmuOFrTMUxhNNYFaRfJMNBVValAUtuLJ0Ka2M/edit?usp=sharing](https://docs.google.com/document/d/1HouxPsYmuOFrTMUxhNNYFaRfJMNBVValAUtuLJ0Ka2M/edit?usp=sharing){card-appearance="inline"}

##  Out of Scope

List the features discussed which are out of scope or might be revisited
in a later release.

##  Figma

Feed:
<https://www.figma.com/file/HVSGkagDKr9FmmRnv9QGs1/Feed-Cards?node-id=380%3A19865>

Detail:
<https://www.figma.com/file/9gdvlxIwxbYX5SIKn8x7HO/Articles?node-id=224%3A5197>

## Phase 2:

1.  Adding a floating CTA in deatil page/ +3 more on image in detail
    page

2.  Adding nudge for MC in feed:
    <https://www.figma.com/file/3Zt2tJPNPB1fZmoqhVUuwi/Nudges?node-id=346%3A15946>

## Instrumentation
