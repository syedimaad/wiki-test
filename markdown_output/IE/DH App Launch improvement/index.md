iOSAppLaunchImprovemets

  ------------ -------------
  **Status**   NOT STARTED
  **Owners**   
  ------------ -------------

## Objective

To reduce the Cold start launch time of the DH app. The aim is to reduce
the launch time (time to first frame) to under 500ms for the 90th and
350ms for the 50th percentile of users.

## Areas of improvement

- App Delegate

  - Reduction in the number of operations in appDidFinishLaunching

  - Identification of heavy workflows in the function and finding ways
    to defer these

  - If deferring a heavy task is not possible, find ways to optimize the
    task

- The below sheet has functions that can be moved from the AppDelegate
  further to improve App Launch

[https://docs.google.com/spreadsheets/d/1imxm-31NeIkM_QWTWz9RB1yIK5h0Ro9BUsBTo8VVZEY/edit?gid=0#gid=0](https://docs.google.com/spreadsheets/d/1imxm-31NeIkM_QWTWz9RB1yIK5h0Ro9BUsBTo8VVZEY/edit?gid=0#gid=0){card-appearance="inline"}

note

Please Note: This document is developing currently...

:::: {.panel .conf-macro .output-block style="background-color: rgb(234,230,255);border-color: rgb(153,141,217);border-width: 1.0px;"}
::: {.panelContent style="background-color: rgb(234,230,255);"}
Please Note: This document is developing currently...
:::
::::
