  ----------------------- ----------------------------------------------
  **Document Status**     NOT STARTED / IN-PROGRESSYellow / READYGreen
  **Android Sprint**      add release sprint
  **iOS Sprint**          add release sprint
  **Product Owners**      
  **Product Designers**   
  **Android Leads**       @ android leads
  **Android Devs**        @ android devs
  **iOS Leads**           @ ios leads
  **iOS Devs**            @ ios devs
  **QA Devs**             @ qa devs
  **Josh Lite**           YEsGreen / NORed
  ----------------------- ----------------------------------------------

##  Executive Summary

Reduce drop off in contact sync flow & make users follow the other users
from the contact list with Josh account in order to create network
inside Josh App.

##  Objective

Make the contact synch flow smooth for users and help them to create
their JOSH network

##  Success metrics

List project goals and the metrics you\'ll use to judge its success.

  ------------------------------------ ---------------------------------------------
  **Goal**                             **Metric**
  e.g., Simplify the user experience   e.g., Customer satisfaction score increases
                                       
  ------------------------------------ ---------------------------------------------

## Analysis

Once the user has successfully completed the sign-up flow, he is landed
on allow contact. As per our data approx, 79K users view the "Allow
Contact" page however only for 58K users successful contact sync is
done.

##  Observations

- Default state -  Unselected contact list.

- No Follow CTA, only arrow at the bottom (Less visibility)

- No \"Select All\" option - for users to do bulk follow for all the
  contacts with Josh account.

- No feedback for users for the Follow activity

- When a user clicks on the arrow button (at the bottom of the screen)
  without selecting any users from the contact list, it takes the user
  to the Home feed page directly. (Without any blockage)

##  Functional Specifications

List all product and feature requirements here.

## Error Handling

List all product and feature errors and edge cases here.

## Notification Requirements

List all requirements for push, local & inbox notifications as well as
flash messages.

## PWA Requirements

Allow Contact Page - Redirection

In some cases when the number of contacts is high it takes little time
for synch. In such a scenario instead of making users wait for the
completion, redirecting them can improve the user experience.
Redirection can be rule-based depending upon the time taken to complete
contact sync.

This can keep the end-user on track by taking them to where they need to
be while they patiently wait for their data to sync with our system.
Redirection can be done and contact sync can be continues in batches

Rules for redirection

  ------------------------------ -------------------- --------------------------------------------- -----------------------------------------------------
  Scenarios                      Redirection Page     Message                                       Notification
  Friends found in Batch 1       Follow your friend   NA                                            NA
  Friends not found in Batch 1   Home Page            Enjoy the video while we synch your contact   User notified about sync with "Find a friend" link 
  ------------------------------ -------------------- --------------------------------------------- -----------------------------------------------------

**Follow your Friend Page - Enhancements**

We can add some enhancements for the Follow your Friend screen (which is
a part of an onboarding flow & comes when contact sync is done), below
are some **observations on UI/UX.**

- Default state -  Unselected contact list.

- No Follow CTA, only arrow at the bottom (Less visibility)

- No \"Select All\" option - for users to do bulk follow for all the
  contacts with Josh account.

- No feedback to users for the Follow activity

- When a user clicks on the arrow button (at the bottom of the screen)
  without selecting any users from the contact list, it takes the user
  to the Home feed page directly. (Without any blockage)

**Requirements:**

- **Default state** should be the selected one (With all the contacts
  with Josh account already selected to \"Follow\") with an option to
  deselect the complete list & vice versa. **Big sticky Follow button**
  at the bottom of the screen (With the state mentioned as text just
  above it) - Shown in the 1st screen below.

- For the bulk selection & deselection activity:

  - **Unselect All CTA in UI** - When complete contact list is already
    selected

  - **Select All CTA in UI** - When no user from contact list is
    selected & also when list is partially selected.

- If no user from contact list is selected then the **Follow CTA should
  be in deactivated state** (with the text above it saying \"Select
  contacts\")

- Users can also select the contacts individually (Similar to current
  behavior), with text showing n.o of contacts selected by the user,
  above the Follow CTA.

- **Follow activity feedback** for users on the Home feed page as a
  toast (After Follow CTA clicked) showing n.o of users from the contact
  list followed - Shown in the last screen (More Friends CTA present in
  the toast - redirecting user to the Suggestion page)

## BE & CMS Requirements

What configurations and CMS provisions are needed to power this feature?
List here.

##  Open Questions

  ---------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------- -----------------------
  **Question**                                                                                                     **Answer**                                                              **Date Answered**
  Managing bulk follow activity for complete list, as list response is paginated(default) needs to be addressed.   e.g., We\'ll announce the feature with a blog post and a presentation   Type // to add a date
  ---------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------- -----------------------

##  Out of Scope

List the features discussed which are out of scope or might be revisited
in a later release.

## Reference Materials

Add links to research and other key documents here.

## Additional Notes

Add additional notes or comments, if any.

##  Figma

https://www.figma.com/file/7B6DdMIYSatTikLPsbW6FV/Onboarding?node-id=1881%3A9942

## Instrumentation
