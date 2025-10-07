  ----------------------- ---------------------
  **Document Status**     IN-PROGRESSYellow
  **Product Managers**    
  **Product Designers**   @ product designers
  ----------------------- ---------------------

## Context & Summary

Why have sound notifications? Purpose/Value?

Accessibility features are an important part of the mobile experience.
Sounds are a way to provide a more unique, branded experience for the
app.

It can be helpful for people to get alerted every time there are some
categories they want to be notified about, people wearing earplugs or
headphones might not check the screen too frequently but with sound
notification, they get alerted. It also helps to prioritize app
notification, for example, if a person wants to get to be alerted every
time there is some breaking news or interactions on their post.

## First-principles note

- What is the purpose of the sound feature?

- What are the problems we are trying to solve? What are the key person

- What are our top competitors doing about the problem? If sound,
  explore more

- How do we measure the success of this feature? How to test it in a
  controlled environment?

- What is the functional requirement? ( Design, acceptance criteria)

##  Objective

1.  Alerting the users with the right set of information(breaking new,
    trending new, etc.) makes users interact with the app, once the
    interaction starts the user might spend time checking similar
    stories, thus it improves the overall user engagement and average
    session time.

2.  Improve user experience- we have got a considerable amount of req
    for this feature requirement, addition of the feature will enable
    users to track the news, events, etc. more effectively

3.  More the time user spends on the app, the more can be chances of the
    user interaction with the ads in that given time thus increasing
    views and clicks on the ads, thus boosting ad revenues.

+----------------------------------------+---------------------------------------------+----------------------------------------------+
| **User personas**                      | **[Pains]{style="color: rgb(255,86,48);"}** | **[Gains]{style="color: rgb(54,179,126);"}** |
+----------------------------------------+---------------------------------------------+----------------------------------------------+
| User                                   | - Not very alert to check screens for       | Functional                                   |
| "[A]{style="color: rgb(54,179,126);"}" |   notifications                             |                                              |
| doesn't check his phone quite          |                                             | - Sound alerts about notification helps to   |
| frequently- maybe a housewife/elder    | - Misses important news, cricket scores,    |   keeps a better track                       |
| people                                 |   etc                                       |                                              |
|                                        |                                             | - Does not miss upon any important news      |
|                                        | - Too many notification which one to        |                                              |
|                                        |   prioritse                                 | - Distinguish dailyhunt notifications from   |
|                                        |                                             |   others                                     |
|                                        |                                             |                                              |
|                                        |                                             | - Do the configurational changes directly    |
|                                        |                                             |   from the app rather than going to android  |
|                                        |                                             |   settings                                   |
+----------------------------------------+---------------------------------------------+----------------------------------------------+
| User                                   | - Not very alert to check screens for       | Functional                                   |
| "[B]{style="color: rgb(76,154,255);"}" |   notifications                             |                                              |
| likes to wear earphones/headphones     |                                             | - Sound alerts about notification helps to   |
| most of the time while using mobile    | - Misses important news, cricket scores.    |   keeps a better track                       |
| phones                                 |                                             |                                              |
|                                        |                                             | - Does not miss upon any important news      |
|                                        |                                             |                                              |
|                                        |                                             | - Do the configurational changes directly    |
|                                        |                                             |   from the app rather than going to android  |
|                                        |                                             |   settings                                   |
+----------------------------------------+---------------------------------------------+----------------------------------------------+
| User                                   | - Too many notification which one to        | Functional                                   |
| "[C]{style="color: rgb(255,86,48);"}"  |   prioritse                                 |                                              |
| wants to priortise daily news          |                                             | - Sound alerts about notification helps to   |
| notification in compared to other      | - Misses important news, cricket scores,    |   keeps a better track                       |
| notifications he is getting.           |   etc                                       |                                              |
|                                        |                                             | - Does not miss upon any important news      |
|                                        |                                             |                                              |
|                                        |                                             | - Distinguish dailyhunt notifications from   |
|                                        |                                             |   others                                     |
|                                        |                                             |                                              |
|                                        |                                             | - Do the configurational changes directly    |
|                                        |                                             |   from the app rather than going to android  |
|                                        |                                             |   settings                                   |
+----------------------------------------+---------------------------------------------+----------------------------------------------+

##  Success metrics

List project goals and the metrics you\'ll use to judge its success.

  ------------------------- ---------------------------------------------------------------------------------- ------------------- ------------------
  **Goal**                  **Metric**                                                                         **Current Value**   **Target Value**
  Improve user engagement   Increase average session timing, DAU, number of notification activated post live                       Market rate
  Improve user experience   Improve csat                                                                                           Market rate
  ------------------------- ---------------------------------------------------------------------------------- ------------------- ------------------

## Competitive Analysis

There are already several apps that have this in-app sound notification
feature. Some of them are listed below:

- Facebook

- Google messenger

- Whatsapp

- Gmail

### [Feature comparison]{style="color: rgb(76,154,255);"}

  ----------------------------------------------- -------------- -------------- -------------- ---------- --------------- ------------
  **Feature**                                     **Facebook**   **WhatsApp**   **Inshorts**   **Mint**   **Sharechat**   **Public**
  Sound Notification(general)                                                                                             
  Customizable alert tones                                                                                                
  Sound notification (Group notification)                                                                                 
  Customizable alert tones (Group notification)                                                                           
  In-app notification (Sound)                                                                                             
  In-app notification (Vibrate)                                                                                           
  ----------------------------------------------- -------------- -------------- -------------- ---------- --------------- ------------

## Assumptions

- Users are more reactive to sound alerts.

- Users who once start interacting with one of the sections will consume
  other similar stories too.

- Users want to prioritize Dailyhunt sub-categories and sound
  notifications will help them in doing this.

#### [Experimentation]{style="color: rgb(191,38,0);"}

- Using polls to understand what **% of users**- actually feel sound
  notifications will be a good addition

- A/B testing, launching the feature for the defined user personal, for
  example- **5-10% of female users**, and analyzing data points as
  notifications turned off per day( pre/post-launch), average session
  time

## ❗ Call-outs

- Too-many sound notifications might become annoying for the users, and
  might also impact app consumption or uninstalling of the app.

- Users might disable notifications altogether as a repercussion of
  building this feature.

- The notifications channels are not segmented that well now, which
  means if a user opts for breaking news, he might get sound
  notifications for other irrelevant stories also

##  Functional Specifications

Sound notifications are a way to alert users to track the ongoing
stories more effectively at the same time we do not want to
annoy/irritate users with too many alerts.

## Phase-1

  ----------------------------- ------------------------------------------------------------------------------------------------- --------------------- ---------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------------------------------------------------------
  **Categories**                **Cases**                                                                                         **Sound & Vibrate**   **Frequency**                                                                            **Backend Logic**
  Breaking news (Breaking L1)   NA                                                                                                Yes                   Only for the first time the notification is posted- no sound for any kind of reposting   One notification id should only alert once through sound, from the next time if the same notification id is posted again, there should be no sound.
  Trending (Breaking L1)        NA                                                                                                Yes                   Only for the first time the notification is posted- no sound for any kind of reposting   One notification id should only alert once through sound, from the next time if the same notification id is posted again, there should be no sound.
  Social                        Mentions                                                                                          Yes                   Everytime                                                                                Whenever a client id is used anywhere as mention
  Support                       User has received a response from DH on their ticket                                              Yes                   Everytime                                                                                
                                When status of ticket is being changed to closed by DH                                            Yes                                                                                                            
                                Reminder: Awaiting user's input on a ticket                                                       Yes                   For 1st time only                                                                        
                                Couldn't submit feedback due to some issue (tech/internet/app not updated)(CTA to resubmit it?)   Yes                   For 1st time only                                                                        
  ----------------------------- ------------------------------------------------------------------------------------------------- --------------------- ---------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------------------------------------------------------

- The volume of conversation tones is controlled by the user's
  **phone\'s notifications volume**.

- The Sound of the notification will be the **default notification
  sound** of the device.

- Type of vibration: long/short will be based on andriod setting

[Sample code]{style="color: rgb(64,50,148);"}

Uri
soundUri=RingtoneManager.getDefaultUri(RingtoneManager.TYPENOTIFICATION);
builder.setSound(soundUri);

- The sound alert will be by **default on for the A/B testing phase**,
  the user will have the option to switch it off/on using the toggle
  button

- On switching off the sound option from the android setting, the
  in-app-sound notification should be in its current state. Ex: If it\'s
  on, then it should remain on irrespective of the sound option for the
  app is disabled from the android setting and vice versa.

**Image references:**

## Phase-2

Phase-2 will be an addition/improvement to the phase-1 launch and we
will only be rolling out phase-2 once we will success metric defined in
phase-1 is realized.

  --------------------------------------------------- ----------------------------------------------------------------------------- ------------------- ---------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------------------------------------------------------
  **Categories**                                      **Cases**                                                                     **Sound feature**   **Frequency**                                                                            **Backend Logic**
  Breaking news (Breaking L1) (Includes all genres)   NA                                                                            Yes                 Only for the first time the notification is posted- no sound for any kind of reposting   One notification id should only alert once through sound, from the next time if the same notification id is posted again, there should be no sound.
  Top Article (Includes all genres)                   Based on personalised notification basis                                      Yes                 Only for the first time the notification is posted- no sound for any kind of reposting   One notification id should only alert once through sound, from the next time if the same notification id is posted again, there should be no sound.
  Individual genres                                   Option to select sound for specific country, specific league, Ongoing match                                                                                                                
                                                      Option to select specific teams for Ipl                                                                                                                                                    
  --------------------------------------------------- ----------------------------------------------------------------------------- ------------------- ---------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------------------------------------------------------

- The volume of conversation tones is controlled by the user's
  **phone\'s notifications volume**.

- The Sound of the notification will be the **default notification
  sound** of the device.

[Sample code]{style="color: rgb(64,50,148);"}

Uri
soundUri=RingtoneManager.getDefaultUri(RingtoneManager.TYPENOTIFICATION);
builder.setSound(soundUri);

- The sound alert will be by **default off**, the user will have the
  option to switch it off/on using the toggle button

- On switching off the sound option from the android setting, the
  in-app-sound notification should be in its current state. Ex: If it\'s
  on, then it should remain on irrespective of the sound option for the
  app is disabled from the android setting and vice versa.

### Experimentation:

**[Experiment 1]{style="color: rgb(76,154,255);"}**

Type of user: 5% of the total user who have notifications turned on

Timespan: 2 months

Data for success: change in no. of people clicking on notification and
coming to the platform, change in number of people turning on/off the
notifications

Time restrictions: 10am - 7pm

Reason: Sound shouldn't become bothering in early morning or late night,
mostly it can useful during the day timings

**Other specification**

- Platinum users won\'t be having this feature in the a/b texting phase

- Time-restricted sound offering.

a\. Not for night heavy users- might be disturbing and irritating

b\. Not for morning timing- again can be disturbing

c\. afternoon timing are the best for our use case when older people,
housewife usually have time to check their phones.

- Based on the impact of the A/B testing we will be adding the vibration
  also to the feature. Users have to option to choose from one of the
  below

a\. Sound with vibration

b\. Sound only

c\. Vibration only

**[Experiment 2]{style="color: rgb(76,154,255);"}**

Type of user: 15% of the female user who have notifications turned on

Timespan: 2 months

Data for success: change in no. of people clicking on notification and
coming to the platform, change in number of people turning on/off the
notifications

Time restrictions: 10am - 9pm

Reason: Extended night hours might be useful for the key personas we
defined above like housewifes who usually mostly use their phones during
afternoons n nights

**Other specification**

- Platinum users won\'t be having this feature in the a/b texting phase

- Time-restricted sound offering.

a\. Not for night heavy users- might be disturbing and irritating

b\. Not for morning timing- again can be disturbing

c\. afternoon timing are the best for our use case when older people,
housewife usually have time to check their phones.

- Based on the impact of the A/B testing we will be adding the vibration
  also to the feature. Users have to option to choose from one of the
  below

a\. Sound with vibration

b\. Sound only

c\. Vibration only

**[Experiment 3]{style="color: rgb(76,154,255);"}**

Type of user: 5% of the total user who have notifications turned off

Timespan: 2 months

Data for success: change in no. of people clicking on notification and
coming to the platform, change in number of people turning on/off the
notifications

Time restrictions: 10am - 6pm

**Other specification**

- Platinum users won\'t be having this feature in the a/b texting phase

- Time-restricted sound offering.

a\. Not for night heavy users- might be disturbing and irritating

b\. Not for morning timing- again can be disturbing

c\. afternoon timing are the best for our use case when older people,
housewife usually have time to check their phones.

- Based on the impact of the A/B testing we will be adding the vibration
  also to the feature. Users have to option to choose from one of the
  below

a\. Sound with vibration

b\. Sound only

c\. Vibration only

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

The design is just for reference, we will come up with the final design

https://www.figma.com/file/T9IAsA6NlknKKL10uZ3QBM/Sound-notification?node-id=0%3A1

After much discussion, we decided to move with design 1

1.  Simpler and easy to understand

2.  Restrict too many notifications

  ---------------- ------------ ---------
  **Issue type**   **Client**   **MIS**
  PO               2            2
  P1               11           2
  P2               9            0
  ---------------- ------------ ---------

## Instrumentation
