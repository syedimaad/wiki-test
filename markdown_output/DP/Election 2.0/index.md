  ----------------------- ----------------------------------------------
  **Document Status**     NOT STARTED / IN-PROGRESSYellow / READYGreen
  **Product Managers**    
  **Product Designers**   
  ----------------------- ----------------------------------------------

17true

## Context & Summary

Election 2.0 is a revamped version of the current election property to
provide users access to information at a constituency, state level and
general elections.

Focusing more on users to participate in the election process by adding
features such as Grievance tab, rate the MLA and Government, Predict and
win, Vote and Snap will help users to spend more time by pointing the
issues, and bragging right.

##  Objective

- To provide end to end information about election starting from Pre
  election to Post election,

- Place for an user to talk about their issues in their constituency

- Convert these users to DAU 

## ❗ Call-outs (Tech Blocks)

+----------------+-----------------+------------------+-----------+------------------+------------------+
| **Location     | **Polls**       | **Grievance**    | **Build   | **Selfie(Photos) | **Leaderboard ** |
| Mapping**      |                 |                  | on        | on polling day** |                  |
|                |                 |                  | Previous  |                  |                  |
|                |                 |                  | setup **  |                  |                  |
+----------------+-----------------+------------------+-----------+------------------+------------------+
| IP based       | Polls on FY and | Prepopulating    | MLA /     | On polling       | Politician       |
| mapping to     | inside topic    | the hashtags,    | candidate | days - take a    | leaderboard      |
| locate the     | will be powered |                  | profile   | selfie of yours  | (State level     |
| constituency   | via ads         | Issue tags       | Page      | and post.        | based on ratings |
| of the user on | mechanism       | (Infrastructure, |           |                  | received)        |
| FY and inside  |                 | traffic,         |           |                  |                  |
| election zone  |                 | sanitation)      |           |                  |                  |
+----------------+-----------------+------------------+-----------+------------------+------------------+
| Show closest   | 2 types of      | Prepopulating    | Party     | Will need        | Happiness Index  |
| constituencies | polls\          | the              | Page      | -Prepopulated    | (Ranking of MLAs |
| based on       |                 | locations(IP +   |           | hashtags         | based on users   |
| current IP     | 1.  Time        | Followed         |           | -Prepopulating   | ratings)         |
| location for   |     Bound -     | location)        |           | the locations    |                  |
| tagging        |     Based on    |                  |           |                  |                  |
| grievances     |     relevancy   | Pre Populated    |           |                  |                  |
|                |     in the      | constituency     |           |                  |                  |
|                |     phase of    | based on Highest |           |                  |                  |
|                |     elections,  | DH users present |           |                  |                  |
|                |     will run    | in the region    |           |                  |                  |
|                |     for a       |                  |           |                  |                  |
|                |     specified   |                  |           |                  |                  |
|                |     time2.      |                  |           |                  |                  |
|                |     Evergreen - |                  |           |                  |                  |
|                |     From the    |                  |           |                  |                  |
|                |     start of    |                  |           |                  |                  |
|                |     run to      |                  |           |                  |                  |
|                |     elections   |                  |           |                  |                  |
|                |     till exit   |                  |           |                  |                  |
|                |     polls       |                  |           |                  |                  |
+----------------+-----------------+------------------+-----------+------------------+------------------+
| Target polls   | Location        | Prepopulating    |           | Moderation of    | Star Citizen     |
| based on       | specific (T+E)  | leader name,     |           | Posts/Selfies    | Leaderboard (All |
| location       |                 | Political        |           |                  | users ranking    |
|                |                 | Parties          |           |                  | based on inbuilt |
|                |                 |                  |           |                  | logic)           |
+----------------+-----------------+------------------+-----------+------------------+------------------+
|                |                 | Moderations of   |           |                  |                  |
|                |                 | Posts            |           |                  |                  |
|                |                 |                  |           |                  |                  |
|                |                 | Post a snapshot  |           |                  |                  |
|                |                 | of top issues of |           |                  |                  |
|                |                 | constituency for |           |                  |                  |
|                |                 | the day at the   |           |                  |                  |
|                |                 | EOD - Automated  |           |                  |                  |
|                |                 | process          |           |                  |                  |
+----------------+-----------------+------------------+-----------+------------------+------------------+
|                |                 | Issues           |           |                  |                  |
|                |                 | Resolved         |           |                  |                  |
+----------------+-----------------+------------------+-----------+------------------+------------------+
|                |                 | Notifying the    |           |                  |                  |
|                |                 | approved/        |           |                  |                  |
|                |                 | disapproved      |           |                  |                  |
|                |                 | posts to the     |           |                  |                  |
|                |                 | users            |           |                  |                  |
+----------------+-----------------+------------------+-----------+------------------+------------------+

##  Functional Specifications

## 1 Pre- Election

#### 1.1 Discoverability

Through Dynamic Tickers and Notification ( tickers→ information about
the subtopics of election, ex: Know your candidate, Apka neta apka soch
)

#### **1.2 Average user : Home Page (Election Bound state)**

  ---------------------------------------------- ------------------------------------- --------------------------------------------
  **Elements**                                   **Display**                           **CTA**
  Edit Location (Default location based on IP)   Icon on the Top Right of the screen   Drop down to select State and Constituency
  Grievance                                      Most interacted Post                  Will land on Grievance Tab
  Videos                                         Video Carousel                        Immersive view
  Political Leaderboard                          Top 3 Politician with their rating    Land on the main Political leaderboard
  Happiness Index                                User constituency index, Ranking      Land to Happiness Index board
  Poll                                           Banner                                Land on to Poll tab
  ---------------------------------------------- ------------------------------------- --------------------------------------------

#### **1.3 Peeping Tom and Chanakya : Home Page (Election Bound state)**

  ---------------------------------------------- ------------------------------------------------------------------------- --------------------------------------------
  **Elements**                                   **Display**                                                               **CTA**
  Edit Location (Default location based on IP)   Icon on the Top Right of the screen                                       Drop down to select State and Constituency
  Constituency                                   Key leader card with their rating, badge (rating trend )                  Will land on the Constituency zone
  Polls                                          Poll of the day                                                           Will land on the Poll Tab
  Grievance                                      Most interacted post of the constituency                                  Land on the Constituency tab
  Profiles                                       Charch or poll or summary of the candidates related to the constituency   Profile Page
  Videos                                         PV Video                                                                  Campaign Page
  ---------------------------------------------- ------------------------------------------------------------------------- --------------------------------------------

#### **1.4 Constituency Tab**

+----------------------+----------------------+----------------------+
| **Elements**         | **Display**          | **CTA**              |
+----------------------+----------------------+----------------------+
| MLA Details          | MLA Name,            | 1.  Click on         |
|                      | designation, image,  |     MLA\--\> Profile |
|                      | party logo, rating,  |     Page 2. Click on |
|                      | Badge, rate now      |     Rate now \--\>   |
|                      | button, nearest      |     Question Related |
|                      | polling booth        |     to the Candidate |
|                      | number, polling      |                      |
|                      | date, Total voters   |                      |
+----------------------+----------------------+----------------------+
| Political            | Leaderboard button   | Ranking of key       |
| Leaderboard          |                      | leaders based on the |
|                      |                      | rating received      |
+----------------------+----------------------+----------------------+
| Issues Tagged        | Constituency name    | Post\--\> Land on    |
|                      | (IP or Edited),      | the Grievance tab    |
|                      | Total issues tagged  |                      |
|                      | with the trend       |                      |
|                      | relative to previous |                      |
|                      | day, Post now        |                      |
+----------------------+----------------------+----------------------+
| Happiness Index      | Index chart with     | NA                   |
|                      | info (happy,         |                      |
|                      | satisfactory,        |                      |
|                      | Unhappy )            |                      |
+----------------------+----------------------+----------------------+
| Happiness Index      | Know More            | Drop down with Poll  |
|                      |                      | regarding the        |
|                      |                      | constituency         |
+----------------------+----------------------+----------------------+
| Happiness Index      | List of Polls        | Users can click on   |
|                      |                      | the options for each |
|                      |                      | poll question        |
+----------------------+----------------------+----------------------+
| Key Leaders          | Carousel of Key      | Click on each        |
|                      | leaders in the       | leader\--\> Profile  |
|                      | constituency (Name,  | page                 |
|                      | Image, party logo)   |                      |
+----------------------+----------------------+----------------------+
| Voters Data          | Male and Female      | NA                   |
|                      | Voters (percentage   |                      |
|                      | and Absolute         |                      |
|                      | numbers)             |                      |
+----------------------+----------------------+----------------------+
| Previous Voters      | Male and Female      | NA                   |
| share                | participated in      |                      |
|                      | voting (percentage   |                      |
|                      | and Absolute         |                      |
|                      | numbers)             |                      |
+----------------------+----------------------+----------------------+
| Previous Election    | Top 3 Candidates     | NA                   |
| Result               | name, image, party   |                      |
|                      | logo, position,      |                      |
|                      | votes                |                      |
|                      | received(absolute    |                      |
|                      | numbers) percentage  |                      |
+----------------------+----------------------+----------------------+
| Past Election Result | List of Winners,     | NA                   |
|                      | year, votes          |                      |
|                      | received, Party      |                      |
+----------------------+----------------------+----------------------+
| Videos               | PV Video Carousel    | Full screen video    |
+----------------------+----------------------+----------------------+
| News                 | News cards list      | Detail article from  |
|                      |                      | each news card       |
+----------------------+----------------------+----------------------+

**  1.5 Poll Tab**

1.  Party cards→ Possible candidates from each party 

2.   Brief information about each candidate→ Previous win/loss,
    accomplishment, positions, strength/weakness, (hashtags to their
    articles)

3.  Vote button on each candidate to select →submit 

4.  Graph it displays how many votes for each candidate(After user
    clicks submit button) 

5.  After candidate are finalized and approved by EC only the list of
    candidates and option to vote by the user

6.  Pin the manifesto by each party 

7.  Opinion polls result (news partner/ publishers) 

  **1.6 Leaders Profile  **

  ------------------------ --------------------------------------------------------------- ----------------------------------------------------
  **Elements**             **Display**                                                     **CTA**
  Cover Image              Party related, Leader related Cover image                       NA
  Leader image             Political leader image with party icon , Name and Designation   NA
  Brief Info               3-4 Lines Brief Information of the leader                       NA
  Know more                Detail Page of the leader                                       More information about the leader 
  Charcha Corner           Button                                                          Opens Repository of Charcha related to that leader
  Poll                     Button                                                          Opens Repository of Polls related to that leader
  Posts                    Button                                                          Opens Repository of Posts related to that leader
  Grievance post           Button                                                          List of Grievance post tagged against the leader
  Charcha of the day       Charcha question of that leader                                 Comments
  Political timeline       Leaders Political data in the form of carousel                  NA
  Poll of the day          Poll about the leader                                           options to record users opinion
  Accomplishment           Political Accomplishments of the leader                         NA
  Background information   Assets, Liabilities, Criminal records information               NA
  ------------------------ --------------------------------------------------------------- ----------------------------------------------------

#### **1.7 Grievance Tab**

  --------------------------------------- ---------------------------------------------------------- ----------------------------------------------------------------------------
  **Elements**                            **Display**                                                **CTA**
  Post Now                                Button                                                     Post screen
  create account                          User has to create account if no account exists (Button)   Google, Fb, icon to create an account 
  Create Post                             Camera icon, Gallery icon                                  Camera icon→ Open camera to snap it, Galley icon→opens users Photo gallery
  Tag and comment option                  Hashtag and @ icon                                         #, @ \--\> Will be added on the Create Post
  Post as Anonymous                       Option to Choose as Anonymous                              Name on the post will be displayed as Anonymous
  Post with Name                          Option to Choose as post with user name                    Name on the Post will be displayed as User login Name
  Photos posted by users                  List of the photos(issues) posted by users                 
  Comment, whatsapp,  3dots               Icons                                                      
  #voice your opinion #raise your voice   pre populate on create post screen                         
  --------------------------------------- ---------------------------------------------------------- ----------------------------------------------------------------------------

#### 1.7 **Campaign (Live Tv and Videos)**

  ------------------- ------------------- ---------
  **Elements**        **Display**         **CTA**
  Live Rally videos   Video Carousel      
  Live Tv             Live Tv Carousel    
  ------------------- ------------------- ---------

## 2 Non- Election bound States

#### 2.1 **Average User: Know Your Constituency(Home Page)**

  ----------------------- ------------------------------------------------------------- --------------------------------------------
  **Elements**            **Display**                                                   **CTA**
  Edit Location           Icon on the Top Right of the screen                           Drop down to select State and Constituency
  Grievance               Most interacted Post                                          Will land on Grievance Tab
  Videos                  Video Carousel                                                Immersive view
  Political Leaderboard   Top 3 Politician with their rating                            Land on the main Political leaderboard
  Happiness Index         Top 3 Constituency from the state + User constituency index   Land to Happiness Index board
  Poll                    Banner                                                        Land on to Poll tab
  ----------------------- ------------------------------------------------------------- --------------------------------------------

#### 2.2 **Average User : Gujarat and HP Elections (Home Page)**

  ---------------------------- -------------------------- --------------------------
  **Elements**                 **Display**                **CTA**
  Key leaders from the state   Name, Image, party logo    Land to the Profile page
  Key Constituency Card        Constituency name          Constituency tab
  Grievance                    Post Carousel              Grievance tab
  Poll                         Banner                     Poll tab
  Videos                       Carousel                   PV Full view video
  News                         News card                  Detail page 
  ---------------------------- -------------------------- --------------------------

#### 2.3 **Peeping Tom and Chanakya  : Know Your Constituency (Home Page)**

** **

  --------------- ------------------------------------------------------------------------- --------------------------------------------
  **Elements**    **Display**                                                               **CTA**
  Edit Location   Icon on the Top Right of the screen                                       Drop down to select State and Constituency
  Constituency    Key leader card with their rating, badge (rating trend )                  Will land on the Constituency zone
  Polls           Poll of the day                                                           Will land on the Poll Tab
  Grievance       Most interacted post of the constituency                                  Land on the Constituency tab
  Profiles        Charch or poll or summary of the candidates related to the constituency   Profile Page
  Campaign        Video clips                                                               Campaign Page
  --------------- ------------------------------------------------------------------------- --------------------------------------------

#### 2.4 **Peeping Tom and Chanakya : Gujarat and HP Election  (Home Page)**

  ---------------------------- -------------------------- --------------------------
  **Elements**                 **Display**                **CTA**
  Key leaders from the state   Name, Image, party logo    Land to the Profile page
  Key Constituency Card        Constituency name          Constituency tab
  Grievance                    Post Carousel              Grievance tab
  Poll                         Banner                     Poll tab
  Videos                       Carousel                   PV Full view video
  News                         News card                  Detail page 
  ---------------------------- -------------------------- --------------------------

## 3 Voting Day

#### **3.1 Discoverability **

Through Dynamic Tickers and Notification → Nudge users to vote

#### **3.2 Election Home Page (Election Bound States)**

  ---------------------------------- -------------------------------------
  Elements                           Display 
  Edit                               State and Constituency
  List of Polling Booths             Click will open Google Maps
  Voter id search                    I frame to search the polling booth
  Hourly voting trend constituency   Graph
  Hourly voting trend State          Graph
  News                               Lists
  Videos                             PV
  ---------------------------------- -------------------------------------

#### **3.3 Election Home Page (Non- Election Bound States GUJ and HP)**

  ----------------------------------------- ------------------------
  Elements                                  Display 
  Edit                                      State and Constituency
  Hourly voting trend top 5 constituency    Infographics
  Hourly voting trend State                 Infographic 
  News                                      Lists
  Videos                                    PV
  ----------------------------------------- ------------------------

#### **3.4 Poll Tab**

1.  Have you voted? How's your experience  

2.  Details from the pre election- ( final day of voting graph about the
    candidates)

3.  Exit polls 

  ------------------------ -------------------------------------------
  Elements                 Display
  Edit                     State and Constituency
  Poll                     Carousel
  Post now                 Open the Post page
  Pre-populated hashtags   #Voted2022 #firsttimevoter #voteforchange
  List of Posts            Photo, like
  ------------------------ -------------------------------------------

 **3.4 Grievance**

1.  Display of Photos/Videos posted by the users of that constituency

2.  Option for user to upload the photos/videos

3.  Option to write description to the Photo/Video user is uploading 

#### **3.5 Leaders Profile**

1.  Sitting MLA/MP information→ Any positions they are holding in
    government, their activities in assembly/parliament 

2.  Number of development works undertaken by that MLA/MP and option to
    rate those work and submit 

3.  Graph of ratings by the user 

4.  Charcha/Comment for each line item 

5.  List of the members of Government (Cm and council of minister)
    Option to rate them (0-5) 

#### **3.6 Campaign**

1.  Live rally videos (constituency and state level)

## BE & CMS Requirements

What configurations and CMS provisions are needed to power this feature?
List here.
