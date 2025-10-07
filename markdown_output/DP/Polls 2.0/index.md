  ----------------------- ----------------------------------------------
  **Document Status**     NOT STARTED / IN-PROGRESSYellow / READYGreen
  **Product Managers**    
  **Product Designers**   @ product designers
  ----------------------- ----------------------------------------------

## Context & Summary

Polls provide a way to get an opinion on a specific topic instantly
across a set no. of options.

## First principles note

### Use cases

- User engagement

- Market research

- Political research

- Feedback

- RSVP for events

### Research

**Current poll conversions for UP elections: \~3.5% (Views →
responses)**

[https://docs.google.com/spreadsheets/d/1Tz-h1AfGEq-9Eh0GwTeaGo8og8wqwAOypwGOWzYpzEQ/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1Tz-h1AfGEq-9Eh0GwTeaGo8og8wqwAOypwGOWzYpzEQ/edit?usp=sharing){card-appearance="inline"}

**Current poll creation process:**
[https://docs.google.com/document/d/1PCy4PJMccI9ZtxjMOWw7gQfdvQLQ5REbGexGtSGXal0/edit?usp=sharing](https://docs.google.com/document/d/1PCy4PJMccI9ZtxjMOWw7gQfdvQLQ5REbGexGtSGXal0/edit?usp=sharing){card-appearance="inline"}

**Poll scenarios**

+--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Buckets**        | **Scenarios**                                                                                                                                                    |
+--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| User engagement    | - Sports win predictors                                                                                                                                          |
|                    |                                                                                                                                                                  |
|                    | - Score predictors                                                                                                                                               |
|                    |                                                                                                                                                                  |
|                    | - Entertainment show win predictors                                                                                                                              |
|                    |                                                                                                                                                                  |
|                    | - Today's trivia around calendar events                                                                                                                          |
|                    |                                                                                                                                                                  |
|                    |   - Did you know                                                                                                                                                 |
|                    |                                                                                                                                                                  |
|                    |   - Small quiz / questions                                                                                                                                       |
+--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Market research    | - [Youtube survey like                                                                                                                                           |
|                    |   ads](https://www.cordcuttersnews.com/youtube-is-adding-survey-ads-to-your-tv-screen/#:~:text=Published%202%20years%20ago%20on,that%20pop%20up%20on%20devices.) |
|                    |                                                                                                                                                                  |
|                    | - Best X of the year - host public polls                                                                                                                         |
|                    |                                                                                                                                                                  |
|                    | - SMBs to get pulse on the ground for launches                                                                                                                   |
+--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Political research | - Election pre poll                                                                                                                                              |
|                    |                                                                                                                                                                  |
|                    | - Get pulse on burning issues                                                                                                                                    |
|                    |                                                                                                                                                                  |
|                    | - Exit Poll                                                                                                                                                      |
+--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Feedback           | - NPS                                                                                                                                                            |
|                    |                                                                                                                                                                  |
|                    | - Get explicit input from customers to personalize their feed (Not as an actual poll but using the same underlying framework)                                    |
+--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| RSVP for events    | - Audio chat rooms                                                                                                                                               |
|                    |                                                                                                                                                                  |
|                    | - Live podcasts / tv                                                                                                                                             |
+--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+

## Types of polls

1.  Multiple Choices (One or more than one options to choose)

2.  Quiz Mode (Shows right or wrong answers after the vote)

3.  Open-Ended Questions (Respondents can submit any text as an answer)

4.  Visible Votes (Reveal the percentage of votes after the user chooses
    an option)

5.  Invisible & Anonymous Votes (Not reveal the vote percentage & name
    of voters)

6.  Slider Ratings (To get an average number within a range)

7.  Up-vote or Down-vote responses (Suitable for yes/no questions)

8.  Nested Questions (Questions change based on responses like Typeform)

##  Objective

1.  Increase poll consumption across various sections

2.  Modularize polls to be plug-n-play across Dailyhunt

3.  Make poll creation easier for the content ops team

4.  Increase TS post poll engagement

##  Success metrics

List project goals and the metrics you\'ll use to judge its success.

  ---------------------------------- ------------------------- ------------------- ------------------
  **Goal**                           **Metric**                **Current Value**   **Target Value**
  Increase poll engagement           Poll Impressions                              
  Increase poll engagement           Poll funnel conversions                       
  Increase TS post poll egnagement   TS post poll action                           
  Simplify poll creation             Time to create polls                          
  ---------------------------------- ------------------------- ------------------- ------------------

## Competitive Analysis

Koo

Reddit

Twitter

Facebook

##  Functional Specifications

### Scenarios

#### Win predictors / Score predictors / Entertainment shows o/p predictors / Share market predictors

- Communication to the user if the prediction turns out to be correct

- Streak of continuous correct predictions

  - Share this on WhatsApp

- Streak of continuous predictions

- Ranking & leaderboard: IPL, Series, Cricket

- Notify me with the result \> merge this communication with the first
  article detail that they see?

- Monetization & rewards?

- Change prediction?

#### Design Handshake

- Elements

  - Question

  - Image (optional)

  - Discrete: Options 2-10

    - Images (optoinal) \> Layouts

    - Quiz

  - Continous: 0-100, 5 increment, 1 increment

  - Time to end / View results

  - Results out by time → notify as soon as results are out → in-app
    notifs?

  - No. of voters

  - Share successful prediction

  - Place on leaderboard

  - share

    - Win Predictor → share with a group and ask them to vote

    - Share the result

    - Share achievement

      - Leaderboard

      - Streak

  - Comment (count) \| Share \| 3 Dots

    - Profile posted by \> Who posted this?

  - [Who creates this? Use cases \> poll within charcha \>
    ]{style="color: rgb(255,86,48);"}

  - <https://www.figma.com/file/z6QpyT9gslNpgZP0ERIDhR/Discovery-%2F-Challenges?node-id=3935%3A148>

  - Meetup like string to denote users who are voting

  - Experience for multi questions polls

#### Leaderboard \| Design handshake

- Latest predictions \> CTA to activities

- Add in profile section \> activity

#### Today's trivia

- Anchor around today's topic of the day \> Follow DH doodle

- eg. Independence day \> where did we hoist the first flag?, etc

#### Market research

- Before we go full screen into videos, can we pop up this question to
  the users with an option to skip?

  - Sponsored?

  - Skip

  - Interations \> Load video post that? (P1)

- Communicate value: Your input helped us in some way??

#### Best X of the year - host public polls

- Autozone: Best hatchback / sedan / SUV of the year

- Which car are you most excited about launching next month \> Once
  answer is submitted, show articles on launch of the car \> map against
  hashtag

- Best 2-wheeler

- What features do you care in a 4 wheeler

  - Show matching vehicles

#### Design \| Engage user post poll response

- CTA to take user somewhere post poll response

- Carousel of articles?

- 

#### Political research

- What change would you want in your constituency / city / state

- Pre-poll

- Approval ratings for your politician \> continous activity like
  feedback page \> Need logged in / verified users

#### Explicit inputs to personalize feed

- Use poll framework to capture signals and improve personalization

- What decade were you born in?

  - Boomer

  - Gen Z

  - Use this for persona mapping

- Mood of the day capture \> associate this with a sentimental article
  about crime, etc

  - Hopeful

  - Anxious

  - Angry

  - Bored

Quiz?

#### RSVP for events

- Capture RSVP for events when they go live on DH \> podcasts \>
  specific TV shows

- Audio chat rooms

### Poll creation \> Ways to improve

### Improve Discoverability

- To improve discoverability \> associate hastags with Polls \> Polls to
  appear wherever hashtag is relevant

  - eg. Ukr Rus war \> Should Putin stop the war now? \> This poll can
    come in the topic page \> Post a story against this hashtag \>

- Enable poll sharing

  - Possibility to share the poll

  - Users can react with app / w/o app \> maintain cookies /

- Enable poll embedding

- Poll arena

  - List all polls \> Filter by category

  - Trigger charcha aspect here and bring that upfront

- Show Charcha stats like 10K people are discussing about this \> to
  view share your opinion

### Polls + Charcha Corner \> Engagement

### Recommended articles based on poll response

- Show recommended articles right below polls which match the user's
  prediction

- Suggest expert opinions post prediction is made \> Cricket experts
  discussing pre match

- Suggest expert reviews post event is over \> Cricket experts
  discussing post match

### Places where polls can exist

Feed \> appears as ad

Tickers

Post detail page?

Polls competing against other cards on the feed \> frequency caps \>
language / location / etc

Polls in feed \> meta params to be captured against polls so that reco
can utilize and serve this

Experience for multi questions polls

### Data requirements

1.  How many users visit the cricket tab when the game is live? \> If
    this is significant, live polls can be based on the game

### Polls as a platform

The polls platform at Dailyhunt enables you to create, manage and run
your polls on Dailyhunt as well as your website and app.

- Leverage the Dailyhunt userbase to expand the reach of your poll

- Customize your poll from our vast library of poll formats

- Garner responses for the same polls on your platforms (website & app)

#### Poll creation

The poll creation self serve utility enables a user to create polls from
a variety of different poll formats.

The user can customize the below points around a poll

1.  Type

    1.  MCQ

    2.  Quiz

    3.  etc

2.  Layout

    1.  Image on the left

    2.  Text only

    3.  ...

3.  Image

    1.  ...

4.  Question

5.  Options

6.  Running time

7.  Target audience

    1.  Location

    2.  Language

#### Poll Management

1.  Ability to create & schedule polls

2.  Ability to edit any polls before it goes live

3.  Ability to deactivate a scheduled or live poll

4.  Ability to see the list of all polls by status

    1.  Live

    2.  Scheduled

    3.  Closed

5.  Ability to view poll stats

    1.  Impressions

    2.  No. of votes

    3.  No. of votes against each option

#### Embedding polls

1.  Embed a poll onto any website using the poll embed url

2.  Show poll & poll reaction page

### Notes \<Ignore\>

- Polls \> Opinions \> Question / Topic

- Plug n Play

\-- Cricket \> Predict & Win? \>

\-- Creating polls \> Placing them within a section \>

Types

- MCQ

\-- Including iamges within polls

- Binary

- Ratings scale: Bookmyshow / IMDB / etc

Problem statement

- Currently its only for web-item. Need to look at a native way to do
  this as well. Can be served to FY, but need to be done through Ads
  Backend, process is complex

\--

- Today its ads backend led, wanted to bring in the content angle as
  well \>

\-- limitations: multiple teams involved in ads backend led, process is
complex

\-- powered by BE \> deep zone like behavior

\--

- Textual answers \> Charcha

- Results of poll \> communication

- Discovery of polls

\--Other than top stories, trending,

- Process

- Text \> Straightforward

- Image \> complex

Arun Kohlapur \> Shubham sharma

- Design: Basic

- Segmenting is super deep

Nikhil content ops, Sagar, Ads ops

Time?

\-- 2+days, 1+day

\-- Hours

Deeplink for polls

run polls based on keywords

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

Future scope:

- Consider poll responses as signals to personlize the content for the
  user

##  Figma

Type /image to add mockups, diagrams, and screenshots related to the
requirements.

## Instrumentation
