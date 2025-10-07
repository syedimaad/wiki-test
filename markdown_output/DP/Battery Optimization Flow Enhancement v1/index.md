  ----------------------- -------------------
  **Document Status**     IN-PROGRESSYellow
  **Product Owners**      
  **Product Designers**   Venkatesh K B
  **DH Lite**             YEsGreen
  ----------------------- -------------------

## Context & Summary

Android 12 has introduced some [[restrictions to foreground
services]{.underline}](https://developer.android.com/about/versions/12/behavior-changes-12#foreground-service-launch-restrictions)
which impacts our ability to display cricket, election and sticky ticker
notifications. By having the battery optimization disabled, we can
bypass these restrictions. To increase our conversions, idea here is t

1.  Revisit current flow for disabling battery optimization and
    understand what changes need to be made

2.  Figure out new events where we can trigger the prompt to disable
    battery optimization

##  Objective

To increase our notification delivery success, our aim is to target more
conversions in the disable battery optimization flow

##  Success metrics

List project goals and the metrics you\'ll use to judge its success.

  ---------------------------------------- ----------------------------------------------------- ------------------- ------------------
  **Goal**                                 **Metric**                                            **Current Value**   **Target Value**
  Increase notification delivery success   \% of users who disable battery optimization for DH   0.5                 1
  ---------------------------------------- ----------------------------------------------------- ------------------- ------------------

## Competitive Analysis

NA

## Assumptions

NA

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
