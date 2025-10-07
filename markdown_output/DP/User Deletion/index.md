  --------------------- -------------------
  **Document Status**   IN-PROGRESSYellow
  **Product Owners**    
  **Reviewer**          
  **Developer**         
  **Approver**          
  --------------------- -------------------

## Context & Summary

All the users in the DH app should have a control on their profile to
delete the account as it is a mandate form the government and the social
media sites like FB, Google and others.

We are creating a flow for the user to delete their DH account and
adhere to the laws.

## First principles note

- Allow the user to delete the DH account.\
  - How the user is able to delete the DH account?\
  - What all information is needed to delete the users DH account?\
  - What will happen if the user account is deleted?\
  - How the user will be able to restore the deleted account?

## What are we changing?

As a user, if I have created an account on the DH app I am not able to
delete my account as I don\'t see any option to delete my account.

We will be providing the user with the an option of getting their
account deactivated/deleted.

## Key User Persona

- **Logged in user:** The users who wants to delete their DH account.\
  logged in users are the user who attached/logged in the app through\
  - Phone Number\
  - Facebook\
  - Google\
  - Truecaller\
  - Apple

<!-- -->

- **Guest User:** User who want to delete the DH account but using the
  app as a guest user.\
  Guest users are the user who has not attached/logged in the DH app
  through\
  - Phone Number\
  - Facebook\
  - Google\
  - Truecaller\
  - Apple

## User Stories

+--------+----------------+--------------------+--------------+----------------------+----------------+
| **\#** | **Use Case**   | **Acceptance       | **Priority** | **Wireframe/Design** | **Comments**   |
|        |                | Criteria**         |              |                      |                |
+--------+----------------+--------------------+--------------+----------------------+----------------+
| 1\.    | As a user I    | 1.  The user       | P1           |                      | - The deletion |
|        | should be able |     should see an  |              |                      |   of the user  |
|        | to delete my   |     option of      |              |                      |   profile is   |
|        | DH account     |     deleting the   |              |                      |   very         |
|        | created        |     account in the |              |                      |   important    |
|        | through        |     settings tab   |              |                      |   and this     |
|        | Google,        |     of the app.    |              |                      |   should be    |
|        | Facebook,      |                    |              |                      |   done through |
|        | truecaller or  | 2.  The user       |              |                      |   the app.     |
|        | Apple ID, by   |     should be able |              |                      |                |
|        | clicking on    |     to click in    |              |                      |                |
|        | the delete     |     the delete     |              |                      |                |
|        | account        |     profile button |              |                      |                |
|        | button/Take    |                    |              |                      |                |
|        | action button  |                    |              |                      |                |
|        | in the DH app. |                    |              |                      |                |
+--------+----------------+--------------------+--------------+----------------------+----------------+
| 2\.    | As a user, on  | 1.  Once the user  | P1           |                      | This will a    |
|        | clicking on    |     click on       |              |                      | PWA page so    |
|        | the delete     |     submit the     |              |                      | that if we     |
|        | account button |     following      |              |                      | have to change |
|        | I should be    |     details will   |              |                      | the questions  |
|        | taken to:\     |     be sent in the |              |                      | we don\'t have |
|        | 1. I can see a |     backend:\      |              |                      | to give an app |
|        | series of      |     - Name of the  |              |                      | update.        |
|        | question to    |     User\          |              |                      |                |
|        | understand why |     - client ID\   |              |                      | The page has   |
|        | I want to      |     - Username\    |              |                      | to open in a   |
|        | delete my      |     - email ID     |              |                      | language       |
|        | account. All   |     (Communication |              |                      | selected by    |
|        | the questions  |     email ID)\     |              |                      | the user.      |
|        | should be      |     - Phone        |              |                      |                |
|        | mandatory.     |     Number\        |              |                      |                |
|        |                |     - Number of    |              |                      |                |
|        | 2\. All the    |     Posts\         |              |                      |                |
|        | questions will |     - Activity of  |              |                      |                |
|        | have a option  |     the user\      |              |                      |                |
|        | to select      |     - History of   |              |                      |                |
|        | answer (Radio  |     the user\      |              |                      |                |
|        | Button).       |     - Question     |              |                      |                |
|        |                |     response       |              |                      |                |
|        | 3\. Once I     |     filled by the  |              |                      |                |
|        | filled the     |     user           |              |                      |                |
|        | questioner I   |                    |              |                      |                |
|        | should be able |                    |              |                      |                |
|        | to submit my   |                    |              |                      |                |
|        | response.      |                    |              |                      |                |
+--------+----------------+--------------------+--------------+----------------------+----------------+
| 3\.    | As a user I    | The user should be | P1           |                      | If the user    |
|        | should be able | shown a list of    |              |                      | has more than  |
|        | to see how     | linked accounts.   |              |                      | 1 account      |
|        | many account I |                    |              |                      | linked then    |
|        | have linked    | "You have          |              |                      | the user has   |
|        | with the DH    | following linked   |              |                      | to shown all   |
|        | app.\          | accounts please    |              |                      | the account    |
|        | I should be    | re-authenticate    |              |                      | linked.        |
|        | able to        | the account to     |              |                      |                |
|        | reauthenticate | delete your        |              |                      | The user has   |
|        | my linked      | Dailyhunt          |              |                      | to unlink one  |
|        | account in     | account".          |              |                      | account at a   |
|        | terms to       |                    |              |                      | time by        |
|        | delete my DH   |                    |              |                      | clicking on    |
|        | account.       |                    |              |                      | the account    |
|        |                |                    |              |                      | that they want |
|        |                |                    |              |                      | to unlink.     |
|        |                |                    |              |                      |                |
|        |                |                    |              |                      | After the      |
|        |                |                    |              |                      | authentication |
|        |                |                    |              |                      | is done for    |
|        |                |                    |              |                      | that account   |
|        |                |                    |              |                      | the user       |
|        |                |                    |              |                      | should again   |
|        |                |                    |              |                      | land on the    |
|        |                |                    |              |                      | same page till |
|        |                |                    |              |                      | all the        |
|        |                |                    |              |                      | accounts are   |
|        |                |                    |              |                      | unlinked.      |
|        |                |                    |              |                      |                |
|        |                |                    |              |                      | If the user    |
|        |                |                    |              |                      | has unlinked 1 |
|        |                |                    |              |                      | account the    |
|        |                |                    |              |                      | refresh list   |
|        |                |                    |              |                      | should exclude |
|        |                |                    |              |                      | that social    |
|        |                |                    |              |                      | login and show |
|        |                |                    |              |                      | rest social    |
|        |                |                    |              |                      | login.         |
+--------+----------------+--------------------+--------------+----------------------+----------------+
| 4\.    | As a user I    | The warning        | P1           |                      | need your      |
|        | should get a   | message is as      |              |                      | input in this. |
|        | warning        | follows "Are you   |              |                      |                |
|        | message that   | sure you want to   |              |                      | This popup     |
|        | all data will  | delete the         |              |                      | will be native |
|        | be lost and    | account?           |              |                      | popup. can     |
|        | the account    |                    |              |                      | this be a on   |
|        | cannot be      | All the data will  |              |                      | the user's     |
|        | restored once  | be lost and you    |              |                      | language.      |
|        | deleted.       | cannot restore the |              |                      |                |
|        |                | data once deleted" |              |                      | Web need to    |
|        | Once I click   |                    |              |                      | pass the       |
|        | on delete      |                    |              |                      | callbacks to   |
|        | request my     |                    |              |                      | the client for |
|        | personal       |                    |              |                      | this popup.    |
|        | information    |                    |              |                      |                |
|        | and my         |                    |              |                      |                |
|        | question       |                    |              |                      |                |
|        | response       |                    |              |                      |                |
|        | should be      |                    |              |                      |                |
|        | submitted to   |                    |              |                      |                |
|        | the DH team.   |                    |              |                      |                |
|        |                |                    |              |                      |                |
|        | If I click on  |                    |              |                      |                |
|        | 'cancle' I     |                    |              |                      |                |
|        | should be take |                    |              |                      |                |
|        | back to the    |                    |              |                      |                |
|        | setting page.  |                    |              |                      |                |
+--------+----------------+--------------------+--------------+----------------------+----------------+
| 5\.    | As a user once | The CS team should | P1           |                      | The popup      |
|        | I clicks on    | work in getting    |              |                      | should be      |
|        | 'Delete' the   | the account delete |              |                      | configurable   |
|        | request should | through the tool   |              |                      | strings so     |
|        | be submitted   | provided to the    |              |                      | that we can    |
|        | to the backend | team.              |              |                      | change the     |
|        | team and I     |                    |              |                      | wording in the |
|        | should get a   | After the account  |              |                      | toast.         |
|        | screen which   | is deleted the     |              |                      |                |
|        | says 'We have  | user should be     |              |                      |                |
|        | taken your     | logged out of the  |              |                      |                |
|        | request your   | app and the        |              |                      |                |
|        | account will   | credentials the    |              |                      |                |
|        | be deleted     | user has used to   |              |                      |                |
|        | soon\'.        | signup in the      |              |                      |                |
|        |                | should be locked.  |              |                      |                |
+--------+----------------+--------------------+--------------+----------------------+----------------+
| 6\.    | As a non       | For a non logged   |              |                      |                |
|        | logged         | in user/Guest user |              |                      |                |
|        | in/guest user  | #1,2,4 and 5 will  |              |                      |                |
|        | I should be    | be followed.\      |              |                      |                |
|        | able to delete | #3 will not be     |              |                      |                |
|        | my account.    | applicable as we   |              |                      |                |
|        |                | don\'t need it as  |              |                      |                |
|        |                | the user is not a  |              |                      |                |
|        |                | logged in user.    |              |                      |                |
+--------+----------------+--------------------+--------------+----------------------+----------------+

## Wireframe

## Design Link.

https://www.figma.com/file/6O2yUpLS12hQi4hE4JGWq3/Profile?node-id=1105%3A1367

## Important Links

Apple id login document-

For Apple, <https://developer.apple.com/news/?id=12m75xbj>

## Roadmap Ahead

## Questions and Clarifications

1.  Sign out to be discussed with Prashant and Bapu.

2.  GD to give clarification on point 3.
