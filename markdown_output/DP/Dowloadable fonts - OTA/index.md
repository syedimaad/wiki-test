  ----------------------- ----------------------------------------------
  **Document Status**     NOT STARTED / IN-PROGRESSYellow / READYGreen
  **Product Managers**    
  **Product Designers**   @ product designers
  ----------------------- ----------------------------------------------

## Context & Summary

With the 20.x release, we are planning to revamp our design. One of the
items include the ability to update the fonts w/o a client release. So
basically going forwards we can update the fonts on the client directly
from the backend. This helps us experiment and update the fonts quickly
and with less efforts.

## Objective

- Ability to update fonts on the client directly from the backend (w/o a
  client release)

- Selective update to a user cohort so that experiments can be carried
  out if needed

## Current Scope

- Ability to have a different font per language. eg. English = Font X,
  Hindi = Font Y

- For release 20.0.x

  - Android

    - English: Libre Franklin

    - All other languages: Noto sans

  - iOS

    - English: Libre Franklin

    - All other languages: San Fransisco

## Current Blockers

1.  Not everything is available: bold, semi bold, medium (was not
    working) currently we have normal and bold\
    font file pertaining to font weight

2.  1st time experience: use font which was not available, gap in
    between 1st experience and the time it was downloaded

### R2 Scope and Feasibility

- Dev team come back on what is a better method: Api vs Google framework

- We need to define edge cases and fallbacks

- Need to define default font (in case it fails to load in first
  experience)

## Assumptions

List any assumptions you have about your users, technical constraints,
or business goals.

## ❗ Call-outs

List all the call-outs that we want to highlight to our stakeholders

##  Functional Specifications

Android reference doc:
[https://developer.android.com/guide/topics/ui/look-and-feel/downloadable-fonts#downloadable-fonts-process](https://developer.android.com/guide/topics/ui/look-and-feel/downloadable-fonts#downloadable-fonts-process){card-appearance="inline"}

## Error Handling

List all product and feature errors and edge cases here.

## PWA Requirements

List all requirements for web & PWA pages needed in this feature.

## BE & CMS Requirements

What configurations and CMS provisions are needed to power this feature?
List here.

##  Open Questions

+----------------------+----------------------+-----------------------+
| **Question**         | **Answer**           | **Date Answered**     |
+----------------------+----------------------+-----------------------+
| Can we make the      | e.g., We\'ll         | Type // to add a date |
| update to the fonts  | announce the feature |                       |
| only to a selective  | with a blog post and |                       |
| set of users for     | a presentation       |                       |
| experimentation      |                      |                       |
| purposes?            |                      |                       |
+----------------------+----------------------+-----------------------+
| Limited to Google    |                      |                       |
| fonts?               |                      |                       |
+----------------------+----------------------+-----------------------+
| Backend              |                      |                       |
| implementation:      |                      |                       |
| Versioned API        |                      |                       |
+----------------------+----------------------+-----------------------+
| Language /           |                      |                       |
| Percentage /\        |                      |                       |
| Parameters for       |                      |                       |
| configurability?     |                      |                       |
+----------------------+----------------------+-----------------------+
| Font provider?       |                      |                       |
+----------------------+----------------------+-----------------------+
| Same size →          |                      |                       |
| Different font might |                      |                       |
| have different       |                      |                       |
| sizes. Size          |                      |                       |
| management needed?   |                      |                       |
| Very high effort!    |                      |                       |
+----------------------+----------------------+-----------------------+
|                      |                      |                       |
+----------------------+----------------------+-----------------------+

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
