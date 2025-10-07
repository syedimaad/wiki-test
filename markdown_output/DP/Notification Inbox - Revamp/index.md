  ----------------------- ----------------------------------------------
  **Document Status**     NOT STARTED / IN-PROGRESSYellow / READYGreen
  **Product Owners**      
  **Product Designers**   @ product designers
  ----------------------- ----------------------------------------------

## Context & Summary

**Purpose of Notification Inbox:**

Whether for work, news, banking or just to chat with friends, mobile
notifications tell an user what they need to attend to and when. While
some users like getting notifications, others turn off most
notifications for their peace of mind. A notification inbox acts as a
repository, where the user can view all their notifications in one
place. 

Since notifications are an integral part of the way users consume news
on DH, notification inbox helps reduce notification overload/ fatigue.

Why are we revamping the Notification Inbox of DH?

- Current notification inbox is a combination of news and social
  notifications

- With the introduction of Sticky, average daily notification count has
  increased to 50-60

- Current 3 dot features and icons under each notification - need to
  check usage and revamp

- Notification Inbox icon on average gets 1 million+ unique user clicks
  per day

- There is scope for monetization

## First principles note 

- **Declutter notifications**

  - Can we give separate categories of notifications - News, Social,
    Subscription(transactions)?

  - Can we group the notifications wrt date, especially for news?

  - Are the read/unread notifications in Notification inbox currently
    intuitive?

  - How can we accommodate transactions of subscription users in the
    current inbox?

  - Can we use 'List user interface' to read stories from inbox?

  - Grouped notification landing on notification inbox needs to be
    re-looked

<!-- -->

- **Features and icons**

  - Can we give more power to individual notifications?

    - Display publisher name along with news notification

    - 3 dots setting (delete/ see less of these
      notifications(publisher)/ report)

  - Can we revisit the features in 3 dots? - Improve or get rid of it

  - How useful is the delete notification feature? Need to check current
    usage and use cases

  - Can we introduce search?

<!-- -->

- **Monetize**

  - Can we monetize this section considering so many users visit the
    section?

  - Can we create Ad zones here?

    - Banner ads between notifications in the list

##  Objective

With the revamped notification inbox, users should be able to:

- Revisit skipped notifications from tray

- View categories of notifications - Today, Earlier/ Home, News, Social,
  Transaction etc.

- Filter out notifications based on time and content

- Search for an article/ video viewed through notification tray

- View individual items from grouped notifications received on tray

- Edit individual notifications - delete, mark unread, mute etc.

##  Success metrics

List project goals and the metrics you\'ll use to judge its success.

  ------------------------------------ --------------------------------------------- ------------------- ------------------
  **Goal**                             **Metric**                                    **Current Value**   **Target Value**
  e.g., Simplify the user experience   e.g., Customer satisfaction score increases                       
                                                                                                         
  ------------------------------------ --------------------------------------------- ------------------- ------------------

## Competitive Analysis

+----------------+------------------+--------------+--------------+--------------+-----------+--------+---------+---------------------------------------------------------+
| **Features**   | **Sub-features** | **Facebook** | **LinkedIn** | **Inshorts** | **Quora** | **DH** | **The   | **Mint**                                                |
|                |                  |              |              |              |           |        | Hindu** |                                                         |
+----------------+------------------+--------------+--------------+--------------+-----------+--------+---------+---------------------------------------------------------+
| **Notification | Defined          | ✅           |              |              |           |        |         |                                                         |
| Inbox layout** | Categories       |              |              |              |           |        |         |                                                         |
|                |                  |              |              |              |           |        |         |                                                         |
|                | (Ex: New/        |              |              |              |           |        |         |                                                         |
|                | Earlier)         |              |              |              |           |        |         |                                                         |
|                +------------------+--------------+--------------+--------------+-----------+--------+---------+---------------------------------------------------------+
|                | Filter (Topics/  |              |              |              | ✅        | ✅     |         |                                                         |
|                | Profile/         |              |              |              |           |        |         |                                                         |
|                | Mentions etc.)   |              |              |              |           |        |         |                                                         |
+----------------+------------------+--------------+--------------+--------------+-----------+--------+---------+---------------------------------------------------------+
| **Individual   | 3 dot setting    | ✅           | ✅           |              | ✅        |        |         |                                                         |
| Notification** | (Ex: delete/ see |              |              |              |           |        |         |                                                         |
|                | less of this/    |              |              |              |           |        |         |                                                         |
| \              | report)          |              |              |              |           |        |         |                                                         |
|                +------------------+--------------+--------------+--------------+-----------+--------+---------+---------------------------------------------------------+
|                | Read/ Unread     | ✅           | ✅           |              | ✅        | ✅     |         | ✅                                                      |
|                |                  |              |              |              |           |        |         |                                                         |
|                | (Ex: white/      |              |              |              |           |        |         |                                                         |
|                | blue)            |              |              |              |           |        |         |                                                         |
|                +------------------+--------------+--------------+--------------+-----------+--------+---------+---------------------------------------------------------+
|                | Date/ Day        | ✅           |              |              | ✅        |        |         | ✅                                                      |
|                +------------------+--------------+--------------+--------------+-----------+--------+---------+---------------------------------------------------------+
|                | Time             | ✅           | ✅           |              |           | ✅     | ✅      | ✅                                                      |
|                |                  |              |              |              |           |        |         |                                                         |
|                |                  |              |              |              |           |        |         | ###### (5 min read)                                     |
|                +------------------+--------------+--------------+--------------+-----------+--------+---------+---------------------------------------------------------+
|                | Publisher/       | ✅           | ✅           |              | ✅        |        |         | ✅                                                      |
|                | Author/ Group/   |              |              |              |           |        |         |                                                         |
|                | Profile name     |              |              |              |           |        |         | ###### (Premium) {#premium style="text-align: center;"} |
|                | mentioned        |              |              |              |           |        |         |                                                         |
|                +------------------+--------------+--------------+--------------+-----------+--------+---------+---------------------------------------------------------+
|                | No. of comments  | ✅           | ✅           |              |           | ✅     |         |                                                         |
|                +------------------+--------------+--------------+--------------+-----------+--------+---------+---------------------------------------------------------+
|                | No. of           | ✅           | ✅           |              |           |        |         |                                                         |
|                | reactions/ likes |              |              |              |           |        |         |                                                         |
+----------------+------------------+--------------+--------------+--------------+-----------+--------+---------+---------------------------------------------------------+

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
