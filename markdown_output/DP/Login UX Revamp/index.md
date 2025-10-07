  ----------------------- ----------------------------------------------
  **Document Status**     NOT STARTED / IN-PROGRESSYellow / READYGreen
  **Product Owners**      
  **Product Designers**   @ product designers
  ----------------------- ----------------------------------------------

## Context & Summary

**Purpose of a Login page:**

Login page allows a user to gain partial/ full access to an application
by entering their credentials(e-mail/ mobile) or through a social media
login. Login helps the business to get personal information of the user,
communicate and track their behaviors in the application. 

There are many applications where sign-ups are mandatory in order to
save the user's data and sync it across devices, Ex: Facebook, WhatsApp
etc. Whereas, there are applications where sign in isn't needed or
requested. Delaying the login process allows users to try out the app
and determine what value they'll receive, before having to give away
personal information.

In the context of DH, personalized news is our core value proposition
for the users. We are also a social platform where users can comment,
reply or react to articles, videos etc. and hence, authentication is
vital to avoid trolls and to moderate user interactions.

Why are we revamping the login UX of DH?

- DH's logged in user base is less than 10% of our overall users
  currently

- Login UI/ UX doesn't convey the value proposition of DH or its login
  worthy features

- Facebook and Gmail login - partners don't share login information of
  users to DH. Will affect communication when we have subscription users

## First principles note

- **Login Pitch**

  - Delight the user to login - what value does logging in give to the
    user?

  - 'Settings-\>Sign in' has poor visibility. Can we accommodate the
    'Sign in' icon within the Profile screen?

  - UX/ UI - can we update content on the login screen?

    - **Generic pitch**

      - Get personalized News and Video for you, anytime & anywhere 
        \_\_\_\_

      - Engage with the DH community, share your opinion on diverse
        topics and genres

      - Follow your favorite news publishers, save articles and much
        more..

    - \'Why join Dailyhunt community?' (when Social elements are
      upgraded)'

      - 10+ have commented on Article \'X\'. Why not express your views?

      - 100+ have reacted to this post by Publisher \'Y'. Save article &
        read later

      - Profile 'X' is rated the 'Top commenter' by 2+ Publishers. Earn
        your badge to fame today! 

      - 316K+ have joined the DH community. Why not put a face and name
        to your profile?

<!-- -->

- **Methods of login**

  - Can we figure out the preferred login journey for the user? - FB/
    Google/ TC/ Email

  - Can we use login as a module which can be invoked based on user
    actions?

  - UX/ UI - How do we reduce decision fatigue at the login screen? 

    - Once we figure out the preferred method of login by users, can we
      re-prioritize the screens?

    - Can we experiment with only Mobile number authentication?

    - 'Enter your email' can be a skippable screen as a follow up to
      mobile number

  - Can we improve the efficiency of Mobile login?

  - Are there advanced login methods we can experiment on? Single tap
    etc.

<!-- -->

- **Login as a module**

  - Can we restrict certain features which were previous accessible to
    non-logged in users?

    - Example: In the profile section, can we show only headers like
      'Saved/Activity/History' with a \'Sign in to access these
      features\' prompt?

    - Need to check current usage of such features by non-logged in
      users

  - Can we invoke different content on the Login page based on these use
    cases?

    - Fill details in profile section - generic pitch

    - Create post - show finished post with a lot of engagement

    - Save articles/ videos - show more instances where save feature is
      useful/ generic pitch

    - After typing a reply, comment - show finished comment with a lot
      of engagement

    - Charcha corner - show finished comment with a lot of engagement

    - Win predictor - generic pitch

    - ..

##  Objective

Provide context on this project and explain how it fits into your
organization\'s strategic goals.

##  Success metrics

List project goals and the metrics you\'ll use to judge its success.

  ------------------------------------ --------------------------------------------- ------------------- ------------------
  **Goal**                             **Metric**                                    **Current Value**   **Target Value**
  e.g., Simplify the user experience   e.g., Customer satisfaction score increases                       
                                                                                                         
  ------------------------------------ --------------------------------------------- ------------------- ------------------

## Competitive Analysis

+--------------+------------------+--------------+--------------+------------+--------------+-----------+-------------+
| **Features** | **Sub-Features** | **LinkedIn** | **Inshorts** | **Quora**  | **DH**       | **The     | **TOI**     |
|              |                  |              |              |            |              | Hindu**   |             |
+--------------+------------------+--------------+--------------+------------+--------------+-----------+-------------+
| **Account**  | First time       | ✅           |              | ✅         |              | ✅        | ✅          |
|              | sign-up          |              |              |            |              |           |             |
|              +------------------+--------------+--------------+------------+--------------+-----------+-------------+
|              | Mandatory        | ✅           |              | ✅         |              |           |             |
|              | sign-in          |              |              |            |              |           |             |
+--------------+------------------+--------------+--------------+------------+--------------+-----------+-------------+
| \            | Login Pitch      | "Make the    | "Sign in to  | "Place to  | "Get         | Member    | "Sign up or |
|              |                  | most of your | save your    | share      | personalized | Benefits  | log in to   |
| **Login      |                  | professional | likes and    | knowledge  | news and     | include - | save        |
| screen**     |                  | life"        | Bookmarks"   | and better | video for    | Ad free,  | stories,    |
|              |                  |              |              | understand | you, anytime | Trending, | leave       |
| \            |                  |              |              | the world" | & anywhere"  | Faster    | comments,   |
|              |                  |              |              |            |              | page      | earn        |
|              |                  |              |              |            |              | loads     | Timespoints |
|              |                  |              |              |            |              | etc."     | & a lot     |
|              |                  |              |              |            |              |           | more"       |
|              +------------------+--------------+--------------+------------+--------------+-----------+-------------+
|              | Email            | ✅           |              | ✅         |              | ✅        | ✅          |
|              +------------------+--------------+--------------+------------+--------------+-----------+-------------+
|              | Phone            | ✅           | ✅           |            | ✅           |           | ✅          |
|              +------------------+--------------+--------------+------------+--------------+-----------+-------------+
|              | Sign in with     | ✅           | ✅           | ✅         | ✅           | ✅        | ✅          |
|              | Gmail            |              |              |            |              |           |             |
|              +------------------+--------------+--------------+------------+--------------+-----------+-------------+
|              | Sign in with FB  |              | ✅           | ✅         | ✅           | ✅        | ✅          |
|              +------------------+--------------+--------------+------------+--------------+-----------+-------------+
|              | Sign in with     |              | ✅           |            |              | ✅        |             |
|              | Twitter          |              |              |            |              |           |             |
+--------------+------------------+--------------+--------------+------------+--------------+-----------+-------------+

Quora

Uber

Times of India

Inshorts login pitch

Airbnb

Inshorts login page

Mint login

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

  ------------------------------------------------------------------------------------------------------------------------ ----------------------------------------------------------------------------------------------------------------------------- -----------------------
  **Question**                                                                                                             **Answer**                                                                                                                    **Date Answered**
  Once the user logs in, how are we using that data (e-mail/ phone) to personalize and serve better content to the user?   e.g., We\'ll announce the feature with a blog post and a presentation                                                         Type // to add a date
  Will mobile number and e-mail id be only used for communication in future? or can we get more insights about the user?                                                                                                                                 
  Can we use data to show social, personalized ads?                                                                        Example: LinkedIn Ad (with forms) is auto-filled for the user using the data we collect through login. Improves conversion.   
  ------------------------------------------------------------------------------------------------------------------------ ----------------------------------------------------------------------------------------------------------------------------- -----------------------

##  Out of Scope

List the features discussed which are out of scope or might be revisited
in a later release.

## Reference Materials

+------------+------------------+------------------+------------------+
| Login method used by users                                          |
+------------+------------------+------------------+------------------+
| Method     | First time login | Overall login    | \% change (wrt   |
|            | (%)              | (%)              | first time       |
|            |                  |                  | login)           |
+------------+------------------+------------------+------------------+
| APPLE      | 0.1%             | 0.0%             | 5%               |
+------------+------------------+------------------+------------------+
| FACEBOOK   | **29.1%**        | 29.8%            | 36%              |
+------------+------------------+------------------+------------------+
| GOOGLE     | **27.3%**        | 28.7%            | 39%              |
+------------+------------------+------------------+------------------+
| TRUECALLER | **43.5%**        | 41.5%            | 26%              |
+------------+------------------+------------------+------------------+
|            | 37,928,977       | 50,141,024       |                  |
+------------+------------------+------------------+------------------+

  ------------------- -----------------------------------------------
  Google**(27.3%)**   \% Users who gave permission for sharing data
  E-mail              99.97%
  ------------------- -----------------------------------------------

  --------------------- -----------------------------------------------
  Facebook**(29.1%)**   \% Users who gave permission for sharing data
  E-mail                50.4%
  DOB                   27.4%
  Gender                15.1%
  --------------------- -----------------------------------------------

  ------------------------ -----------------------------------------------
  True caller**(43.5%)**   \% Users who gave permission for sharing data
  E-mail                   21.50%
  ------------------------ -----------------------------------------------

Add links to research and other key documents here.

## Additional Notes

Add additional notes or comments, if any.

##  Figma

Type /image to add mockups, diagrams, and screenshots related to the
requirements.

## Instrumentation
