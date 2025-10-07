# \_u7f5jhcsy1tkScope for MVP:

\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--

User Facing features on a high level:

Phase 0:

1.  1-on-1 Chat

2.  Group Chat

3.  1-on-1 Audio Calling

4.  1-on-1 Video Calling

Phase 1

1.  Group Audio Calling

2.  Group Video Calling

3.  Clubs and Communities

Platforms

Frontend:

Android and iOS (MVP)

Backend:

Basic CMS/ Admin portal for User and content management [(Sendbird
Dashboard)]{style="color: rgb(0,0,255);"}

\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--

### \_v457vq4erkv2User Account Management

[User Chat Account linked to Josh Account]{style="color: rgb(0,0,255);"}

1.  Users should be able to use the same account as their Josh account

2.  Non signed-in user will be asked to sign in/ sign up before they can
    use this feature

3.  User data taken from Josh would include profile picture and display
    name

### \_ixhmd452gtjOnboarding

Non logged in users (who have josh installed on their device) will be
asked to sign up as soon as they click on the Chat tab. Logged in users
will see the zero state UI of Chat.

## \_g3b0qsxwbrioChat (1-on-1 + Group)

[(Sendbird backend support available via Modular APIs;
]{style="color: rgb(0,0,255);"}

[ Fronted, API integration to be taken
up)]{style="color: rgb(0,0,255);"}

### \_icnhu3wcqhaoUI - Landing Page

Chat Card Cases

- Other than, Sent, Received and Unread messages we also show if the
  last message received was a photo, video, sticker

- Typing Indicator takes precedence over any last message
  (Read/Unread/Received/Sent). Typing Indicator is shown when the user
  is typing something.

- Call updates will be shown marked in a different font colour. There
  are two cases:

  - If an audio/video was the last interaction (timestamp shown here is
    of the call)

  - If the user has missed an audio/video call from this user - in this
    case a call CTA appears on the right. Upon clicking it will trigger
    the same type i.e. Audio/Video

### \_ql94o61dk6k1Zero State

In the beginning the user lands on the chat for the first time they see
their first chat message thread with the Josh Chatbot.

Josh Chatbot would be sending two different kinds of messages -

1.  Preconfigured messages at times that are pre-decided. For e.g. first
    message when user opens the app, a feature list message after the
    first 36 hours etc.

2.  Messages manually pushed by the Sendbird CMS - by operators.

Suggestions widget

Along with this there will be a suggestions widget which randomly show
any 5 mutual connections (mutual connections are two users mutually
following each other in the Josh ecosystem)

For a new user (not/barely having any connections - less than 5) the
suggestions widget does not show up.

([Backend API to be created by Josh team - which will be shared with the
clients to consume)]{style="color: rgb(0,0,255);"}

### \_99t12xb2y9pmCreate New Flow

\-- Users can create new chat message threads as well as groups through
this

\-- Landing page would have all the users the logged in user is
following right below the create new group option sorted alphabetically

\-- For 1-on-1 DM's :

As soon as a user is selected, there is an API call to be made that
checks if this user is also following back the logged in user.

- If two users mutually follow each other then the chat request **does
  not** go to the Requests section of the invited user. They can
  directly start chatting

- However, if only one of them follows the other - they invite would
  first land into the requests tab of the user rather than

([Backend API to be created by Josh team - which gives info to the
clients)]{style="color: rgb(0,0,255);"}

### \_4vzv3yh84thoCarousel View in Chat UI

- This would consist of thumbnails of recently uploaded Josh videos of
  creators (users) who the logged in user is following.

- Any of the users' contacts (users who the who have uploaded a new
  video will appear in a carousel view at the top of the Chat UI)

- These would be video thumbnails and the user's display name and
  profile pic would be right below it

- A video that the user has not consumed would be highlighted through a
  border

- Once the user consumes this video it moves to the end of the queue

([Backend API to be created by Josh team - which send required data to
the clients)]{style="color: rgb(0,0,255);"}

### \_vupek9mmxela

### \_e6pp59rdm9f2

### \_yb1ui0s35fej

### \_rwn6g8q4i6lh

### \_lhfvumqob8ud

### \_yqvh72n3i48f

### \_2bbkw2hm3nf1Requests/ Invites from other Users

### \_yd32n3k664yq

### \_azv4cao92xzs

### \_fptot5jzaso5

### \_rmaw563jv6va

Request Receiver can make an action with or without viewing the requests
that he/she receives

One way is to edit and select 1 or more requests for a common action -
Accept, Decline, Block

Another way is to click on an individual request and view the message in
order to get some context.

### \_319dxxsqon3kChat UI

### \_kuwn11q0rp8g

### \_hrl8t26j0h74

### \_e0zq9kaosn5w

### \_3m2nrajxrlnb

### \_873klxs59g1r

### \_x3fs86gdrai

### \_8j6u51b980ew

### \_ctbf5zuxv2s4

### \_utf7l8l24uwj

**Offline messages**: The status space would show a loader if the
message has not gone from the sender's end, due to bandwidth or any
other issues

### \_7p2ps1rvrdykLong press on a message

Long pressing on a message would show a popup to the user and depending
on whether the message was sent by him/her it would display various
options:

- If message is sent by a user: Reactions, Copy, Edit, Reply Delete

- If message is not sent by a user: Reactions, Copy, Reply

### \_gpejizp0exp5Group Chat and Basic Moderation (For MVP)

### \_tdoatjcmsgqd

For the MVP moderation will be structured in the following way

- The host will be the admin/ creator of the group and will have the
  option to edit name and profile pic of he group

- Initially the "Add group name" - any user can add a group name,
  however only the host will be able to edit it.

- Profile picture can only be edited by the host (default profile
  picture is already set based on predefined rules by sendbird)

- The host cannot make other users as admins

- Only the host can remove users from the channel

### \_dhcl4m3sizh2Default landing page for calls tab

As soon as the the user goes to the calls tab, they should see 2 widgets

\--Call logs with a history of the last 7 calls. There will be a see
more pulldown that the users can use to see more call history
(paginated, 1st tap will show next 7 and another tap will show the
entire week)

\--Call Friends where all users whose chat request the user has accepted
are listed. Sorting order will be order on the chat module (not
alphabetical and not last active)

### \_g2vrmw1vludeProfile Intervention/ Entry Points in Josh

Profiles will have a CTA to start chats with a user

By default, sending a message to any user should be possible if they
mutually follow each other. Otherwise the first message will be sent and
only that will be visible to the receiver. Based on that sending the
next message would require the receiver to accept the chat request of
the sender.

### \_3ew0ybd4r5ai

### \_if44yyo12ie1Sharing:

- Users should be able to share the following media (for the MVP)

  - Images

  - Videos

  - Stickers, Emojis

  - Rich Links

  - Josh Videos

Senders and Receivers will be able to download and save the images and
videos shared.

## \_77ewrrc6soitGroup Chat

### \_hxr95p6da16Create New Flow

### \_t6dakxlcgm4r

### \_ilagp9j8vssw

### \_9upwi6zcffdc

### \_wepko5arbjki

### \_rri8ieqnh37d

### \_axeztq79lvhf

### \_1z7twogwx4d6

### \_lywjo54xqsxy

Within the Create New Flow user would need to access "Create new Group".
This will show them users that they follow:

- Users can be searched and checked to add the groups

- This will form a bubble of the group member at the top

- There will be a status at the bottom to indicate the total capacity of
  the group

### \_fk7x5ruubm02Chat UI

- Adding a group name will not be mandatory and can be added at any
  point in time by any user

- By default, Group name would be a combination of the first 2-3 members
  of the group

- Replies in a group would show who has replied to whom (unlike 1-on-1
  chat)

- For MVP, we will just show how many users have seen the messages at
  the end of the chat. (and not how many it was delivered). This will
  NOT be on an individual message basis, but only show who has read all
  messages.

### \_7h13ohltjaa4Group Page

This would show the

- Profile pic (if creator is viewing this is editable)

- Name (if creator is viewing this is editable)

- Option to add more members

- Toggle notification on/off

- Leave Group

- Delete Chat history

- Other participants

## \_dg86ap9dhohjSendbird SDK Support for Private Chats and Group Chats

- [Typing indicators]{style="color: rgb(66,66,66);"}

- [Read receipts]{style="color: rgb(66,66,66);"}

- [Delivery receipts]{style="color: rgb(66,66,66);"}

- [User presence indicators]{style="color: rgb(66,66,66);"}

- [Push notifications]{style="color: rgb(66,66,66);"}

- [Reactions]{style="color: rgb(66,66,66);"}

- [User mentions]{style="color: rgb(66,66,66);"}

- [Channel mentions]{style="color: rgb(66,66,66);"}

- [Unread message count]{style="color: rgb(66,66,66);"}

- [Mention count]{style="color: rgb(66,66,66);"}

- [User invitation]{style="color: rgb(66,66,66);"}

- [Channel list]{style="color: rgb(66,66,66);"}

- [Admin Messages]{style="color: rgb(66,66,66);"}

- [Announcements]{style="color: rgb(66,66,66);"}

- [Offline Messages]{style="color: rgb(66,66,66);"}

- [Send Images, Videos, Stickers]{style="color: rgb(66,66,66);"}

- **[Moderation: Profanity, Blurred
  image]{style="color: rgb(66,66,66);"}**

### \_7ziyfsr3477y

## \_81okx2wupwymAudio and Video Calling

### \_ka7skjc3vkf0Default landing page for calls tab

As soon as the the user goes to the calls tab, they should see 2 widgets

\--Call logs with a history of the last 7 calls. There will be a see
more pulldown that the users can use to see more call history
(paginated, 1st tap will show next 7 and another tap will show the
entire week)

\--Call Friends where all users whose chat request the user has accepted
are listed. Sorting order will be order on the chat module (not
alphabetical and not last active)

### \_rbots1w2njz0Receiving Calls

Users should be able to receive calls via notifications as depicted
above. The notification itself would have the Accept/Decline option.

Call UI

- Users can toggle Audio and Video both during calls

- For Video calls, users can switch from cameras - front and back

- Quick toggle shortcuts for speaker and bluetooth audio would also be
  present

\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--

### \_dt4ylsg1y7ccPrivacy and Security (MVP)

1.  All messages to be end-to-end encrypted

2.  Ability to report someone - A small operations team would be
    required to moderate and look into any such complaints.

### \_5w1dt7z7uftlBackend Portal - for Ops team to manage and moderate

Check on users and content that has been reported - manually remove/
resolve such issues

[Sendbird support available]{style="color: rgb(0,0,255);"}

### \_2vm9po6t71h4Notifications

1.  Users receive notification for

    1.  New messages from 1-on-1 chats

    2.  New messages from group chats

    3.  Chat requests - "Xyz wants to connect with you"

    4.  Missed Calls - Both Audio and Video

## \_es2t4yhga0hlPhase 2 (Post MVP)

These features will be taken up after the MVP and constitute some
Advanced integrations and features which are highly customizable by the
user

### \_z4u6eu1wgbosUser Account Management

1.  Sync Account (Chats, communities and Call history) to different
    device

2.  Option to backup data (and preferences, if any) to Josh Cloud

This can be automated as well as manual

Configuration settings to be added for managing auto backup over wifi /
mobile data

[Sendbird support available]{style="color: rgb(0,0,255);"}

### \_10uhnq65zfieOnboarding

1.  Sign in through Apple ID

2.  Also users can sign up with an invite link from a friend.

    1.  This link would be the Playstore Deeplink to the Josh app
        listing

    2.  if users do not have the app installed on their device.

**Deferred Deeplinking:** Users would be led to the sign in page after
they have installed the app

### \_yr9pb31639lmNotifications

Control over notifications on a user level i.e. whose message would
entail a notification and whose would not

### \_30i0kxhgpf7bPrivacy and Security

All properties - viewing profile pic, adding to group chats, adding to
last seen etc. can be controlled over an individual basis

## \_26810hof0ub21-on-1 Chant/ DM

1.  Pin Messages to the Top - This way users can bookmark some chats/
    groups that they feel they are frequently accessing

2.  Star a message

## \_wq3j9u9849p2Group Audio and Video Calling

### \_tavxx2by7eniUI and Features

- In and audio call thumbnails would be static profile picture instead
  of live video (in the grid)

- Any user not having a profile picture will have a default placeholder

- Users can toggle audio and video (microphone and camera) at any point
  in the call

- Users can switch from front to rear camera if their video is on

Expanded modal view gives the user info about the call - participant
display name and profile pic

New participants can be invited by simply selecting add people (the user
needs to exist in the inviters' contact list)

[Additional Features to be built over
sendbird]{style="color: rgb(0,0,255);"}

- Status can be divided into 3 parts:

  - Users who have already joined will not have anything against their
    name

  - Users whose device is ringing will have a "Ringing" label against
    their name

  - **Optional:** Users who did not join will have cross against their
    name or would be under the sub-heading "Not in this call"

Any user who has been invited can join the call at any point in time. If
the active - the same would be indicated in the call logs and user can
just click on it and join
