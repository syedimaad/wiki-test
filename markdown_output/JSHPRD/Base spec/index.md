##  Executive Summary

A gamified rewards experience to support user/network growth and
engagement by incentivising users to take certain actions.

##  Objective

**About the project**

1.  Actions we want to incentivize

    1.  Sign-in

    2.  Check-in

    3.  Comment

    4.  Like

    5.  Watch

    6.  Share

2.  UI is
    [[here]{.underline}](https://www.figma.com/file/fM0YQI7w0e6rV3NzYZTBIj/Reward-Program?node-id=452%3A2699).

**The overall scope of the project includes**

1.  New designs/enhancements

    1.  Screens

    2.  Entry points across the app

        1.  Floating elements in the feed (snack bar etc.)

        2.  Profile page

        3.  Cards in feed

        4.  Settings

        5.  Discover

    3.  Josh settings

    4.  Nudges

        1.  Snack bars

        2.  Default Josh nudges

        3.  Nudges via push and inbox notifications

    5.  Rewards overlay notifications

    6.  Pages for FAQs, rules, T&C, Privacy Policy etc.

2.  New functionality (FE + BE + CMS)

    1.  Entry points to rewards dashboard

    2.  Relevant notifications

    3.  Rewards overlay notifications

    4.  Integration with 3rd party providers

    5.  Tracking and logging user actions + stats

    6.  Ability to map rewards to user actions

    7.  Tracking, logging and cataloguing redeemed rewards

    8.  Events and rewards configuration incl. daily challenges

    9.  Nudges based on configuration, events and refresh cycle

    10. Gamification

3.  Partner integrations

    1.  Wallet

    2.  Rewards

    3.  KYC

    4.  Fraud, safety and integrity

4.  **Out of scope for now**

    1.  Referrals

    2.  Escrow for rewards

5.  Spread between PWA and native components will be heavily leaning
    towards PWA with native components making up only the entry points
    and base level functionality that cannot be done in PWA.

##  Functional Specifications

**WHAT ARE REWARDS AND HOW DO THEY WORK?**

**Definition of rewarding actions**

1.  **Actions:**

    1.  These will form the base of each challenge/milestone and the
        reward it connects to. 

    2.  (?) There can be multiple configurations/milestones on top of
        the same kind of action.

        1.  (?) Example: 100 likes for 10 Jems can be active at the same
            time as 50 likes for 5 Jems. 

2.  **Action attributes:**

    1.  Event for which the reward will be given

        1.  Sign-in

        2.  Check-in

        3.  Comment on videos

        4.  Like other users' videos (unique, non-repeating likes)

            1.  Comments by other users

        5.  Watch

            1.  Unique full-video views 

        6.  Create

        7.  **Future releases** can potentially include

            1.  Automated/background actions like:

                1.  Age of the account ("It's your 1 year on Josh. Here
                    are xyz Jems!")

                2.  Session length ("You get 5 Jems for spending 120
                    minutes on Josh today!")

            2.  Number of friends ("Here are 1000 Jems for following
                your 100th creator")

            3.  Dynamic attributes on user's profile, content etc.

                1.  "You have 1.5k likes on this video. The reward for
                    this is abc."

                2.  "You got 100 new followers in 24 hours. You get 50
                    Jems!"

3.  **Milestones/challenges and rewards configuration:**

    1.  Action: the action on which the milestone is based.

    2.  Unique action count: the number of times the action needs to be
        performed to earn this reward.

        1.  This count becomes the milestone for each of these actions
            for the user to perform.

    3.  Daily challenge (TRUE/FALSE)

        1.  Whether this milestone is shown as the daily challenge on
            the user's side.

    4.  Jems rewarded for hitting this milestone

        1.  In the future, a non-Jems reward might be included too.

    5.  Reward/Jems disbursal

        1.  Immediately upon hitting the milestone

        2.  After n seconds of hitting the milestone

    6.  Upper limit per user (ULPU): the number of times a user can earn
        this reward.

    7.  Type

        1.  One-time (in a lifetime)

        2.  Cyclic (the duration in which the user can earn a max of
            ULPU rewards)

            1.  For example: if the duration is 1.5 hours, a user can
                earn a maximum of ULPU rewards in that duration.
                However, after 1.5 hours, the cycle resets and the user
                can again earn ULPU rewards for the next block of 1.5
                hours.

                1.  To clarify: Does the next block start immediately
                    upon completion of the previous one or once the user
                    takes the relevant action again? Depending on the
                    decision, this might or might not be tracked at a
                    user level.

            2.  Reset cyclic events count per:

                1.  Hour

                2.  Day

                3.  Week

                4.  Month

                5.  Year

    8.  Include previously taken actions? (TRUE/FALSE)

        1.  Does the system consider previous relevant actions that the
            user took before the milestone was created? Depending on the
            setting, adjust user progress.

    9.  Targeting: the user segment this reward is applicable to. 

        1.  Based on user attributes available to us.

    10. Milestones

        1.  Milestones will be tied to rewards

        2.  Custom levels/counts can be defined as milestones

            1.  Example: 500 likes, 1000 likes, 5000 likes etc.

                1.  Each of these will have associated rewards.

        3.  Encouragement nudges (multiple can be added to a milestone):

            1.  Type (snack-bar, overlay, push-notification,
                notification-inbox etc. multi-select)

            2.  Checkpoint (custom level/counts)

            3.  Show nudge at

                1.  Completion % for notification (show this nudge at
                    50% of the 1000 likes checkpoint)

                2.  TTL remaining

            4.  Text for the nudge (string with variables)

                1.  Variables:

                    1.  Current count

                    2.  Checkpoint

                    3.  Count till checkpoint

                    4.  Completion % OR TTL remaining

                    5.  Reward

            5.  Example nudges:

                1.  "You are at 900 likes (90%), just 100 likes away
                    from the Super Thousand milestone. Reach 1000 likes
                    to get the pqr reward."

                2.  "You are just 100 likes away from the Super Thousand
                    milestone. Reach 1000 likes within 24 hours to get
                    the pqr reward."

        4.  Milestones will follow targeting rules set at the reward
            level.

\

**PRIMARY SCREENS + FLOWS**

\

**FEED AND REWARDS HOME**

\

1.  **Today**

    1.  Structure and data points

        1.  Data points

        2.  Sections

            1.  Daily check-in

            2.  Today's challenge

            3.  90%+ complete challenges/almost there

            4.  Promoted offers (Daily offers)

                1.  Cases addressed

                    1.  When no offers are promoted

                    2.  When offers are redeemed

                    3.  Section shown

                    4.  Section hidden

        3.  Segues

            1.  T&C

            2.  FAQs

            3.  About User Rewards and rules

    2.  Functionality

        1.  Daily check-in

            1.  Today's check-in

                1.  'Done' state

            2.  Previous check-ins

            3.  Missed check-in

                1.  Educate users about missing check-ins and its
                    implications

            4.  Actions on tapping on individual days

        2.  Today's challenge

            1.  Show relevant challenge as configured

            2.  Hide this section if BE doesn't send any daily challenge

            3.  States

                1.  Active challenge: live challenge for today that has
                    not been completed

                2.  Completed challenge: live challenge for the day that
                    was completed

                3.  No challenge: zero-state

        3.  'Almost there' challenges

        4.  Daily offers

            1.  If the backend does not send any offers to the client,
                hide the Daily Offers section from 'Today'

            2.  Promoted offers

                1.  When no offers are promoted

                    1.  If the section is set to show, show the newest
                        available offers

                2.  Targeting

    3.   Targeting based on user attributes will be possible

2.  **My Rewards**

    1.  Available rewards

        1.  Expiring soon (72 hours or less to go)

    2.  Expired rewards

        1.  Used rewards that are no longer valid (?)

    3.  Rewards for purchase/to claim

    4.  Future releases might allow usage of rewards (integrate with
        partners)

    5.  Track at a user level in user history so it can be used for more

3.  **Milestones/challenges**

4.  **Custom action cards**

    1.  Feed cards + nudges

        1.  Push the user to rewards home

        2.  Push the user to log in to earn rewards

\

**DAILY CHECK-IN/STREAK**

\

1.  **Daily check-in 101 basics:** 

    1.  This feature allows the user to open the app daily to earn
        rewards. This aims to incentivize them to repeat this
        behaviour. 

    2.  Consecutive logins without missing any days maintain the
        streak. 

    3.  Every day is capable of having its own unique reward in the form
        of Jems or rewards via rewards partners.

    4.  If the user misses checking in/opening the app on any day, the
        streak is broken and the user returns to the beginning of the
        sequence to Day 1.

2.  **Configuration/master-data**

    1.  Daily check-in length (no. of days)

        1.  This will define the number of days the daily
            check-in/streak will run for. 

            1.  For example: for 1-week lengths, the streak will reset
                after 7 consecutive days of login by the user.

        2.  Pre-defined options for weeks, months, year (max 1)

    2.  Ability to assign a reward for checking-in for each day

        1.  A reward of either Jems or reward from coupon/code/voucher
            fetched from the 3rd-party partner can be assigned to the
            day.

    3.  Ability to mark specific days as 'special'

        1.  A different animation is associated with these days.

    4.  Refresh of this data + reflection on the user's side happens on

        1.  Missing a check-in

        2.  Hitting a checkpoint

        3.  Therefore the user will see a new set of rewards/Jems for
            each upcoming check-in.

        4.  This will need to be maintained at a user level. Therefore
            different users can have a different set of rewards for the
            same day/sequence.

    5.  Ability to define check-points based on the number of days.

        1.  This defines the cycle when the system fetches an updated 

3.  **User-facing functionality**

    1.  Streak is maintained at a user level. First open after the app
        is installed is counted as Day 1. 

    2.  Every consecutive login is counted as +1 day.

    3.  What happens in case the user isn't signed-in?

        1.  Encourage users to sign in and earn the sign-in + day 1
            check-in reward

        2.  If the user is being tracked on various milestones, reward
            the user with all milestones that they have hit upon login.

            1.  Overlay notifications need to be queued in this case.
                They will show one after another based on when a
                milestone was hit.

        3.  There will be a separate screen/view for logged-out users
            who are progressing on various milestones.

    4.  Hide vs. reveal rewards for check-in

        1.  Show preview up till the next checkpoint. 

        2.  All rewards after that will be hidden behind a ? and the
            preview cannot be seen until the user passes the leading
            checkpoint.

4.  **Daily check-in widget**

<!-- -->

1.  Tracks consecutive days the user opened the app

2.  Indicates missed days (max 1)

3.  Preview of reward

4.  Scrollable horizontally

    1.  Shows a max of +2 weeks

5.  Contains information about what daily check-in is etc.

\

**JEMS WALLET**

\

1.  **Structure and data points**

    1.  Data points

        1.  Current balance

        2.  Lifetime Jems earned (total number of Jems ever collected
            via rewards)

        3.  Today's Jems (+/- Jems today, overall change)

        4.  Lifetime Jems acquired (earned + bought)

        5.  Lifetime Jems spent

2.  **Specific segues**

    1.  Rewards Store

    2.  My Rewards

    3.  Passbook/transaction history

    4.  FAQs

3.  **Functionality**

    1.  Wallet recharge flow that takes the user through integrated
        payment flow.

4.  **Sub-section: Passbook/transaction history**

    1.  List of all transactions done with Jems (both credit and debit)

    2.  Associated visual, colours, indicators for debit/credit

    3.  Timestamp of transactions

    4.  Infinite loader for looking at past transactions

        1.  End with 'No more transactions' label in grey in the middle

\

**REWARDS STORE**

\

1.  **Structure and data points**

    1.  List of all available rewards

        1.  These follow targeting rules and reward configurations.

        2.  Cost, title, description, visual, tags are attached.

        3.  In the case of a time-limited reward, an associated timer is
            available indicating the time left to redeem the reward.

    2.  Sections

        1.  Affordable rewards

        2.  Insufficient balance for these rewards

            1.  Indicates the number of additional Jems needed to redeem
                this reward

    3.  Current Jems balance

    4.  Filters on top of rewards listing

    5.  Specific segues

        1.  FAQs

        2.  T&C (via redemption confirmation bottom sheet)

2.  **Functionality**

    1.  **Filters** on rewards.

        1.  Apply and clear filters

        2.  Categorized filter options

        3.  Count of items under each combination

    2.  **Rewards redemption** by tapping 'Redeem' and going through a
        confirmation process (bottom sheet).

        1.  The reward is added to the user's rewards catalogue (My
            Rewards) immediately.

    3.  Segregation of rewards based on what is affordable and what is
        beyond the current balance.

        1.  A slight visual difference between these categories.

    4.  If the user tries to buy a reward the cost of which exceeds the
        current balance, the user is taken through a **wallet top-up
        flow** which ends with the reward being redeemed.

        1.  By default, the top-up value is prefilled as the additional
            number of Jems needed to redeem that reward with options to
            select standard values.

        2.  If the user selects or edits the value, check if the
            prospective balance would be able to redeem the reward or
            not.

            1.  If yes, allow the user to proceed as normal.

            2.  If no, throw an error message and encourage the user to
                increase the top-up value.

    5.  Integration with **wallet, KYC, redemption and safety
        partners**.

        1.  **KYC flow** for those redeeming cash/INR who have not done
            KYC

        2.  **Withdrawal flow** sending money to the user's chosen
            destination (**bank account, UPI, Paytm wallet** etc.)

\

**INNER WORKINGS**

\

1.  **Background functionality**

    1.  Milestones per user are tracked implicitly in the background and
        tallied.

        1.  If a milestone is configured 

    2.  Upon hitting a milestone, the user sees a visual overlay of the
        milestone met on whichever screen they might be in.

    3.  Milestones notifications CMS configuration

        1.  Title

        2.  String text body

        3.  Visual

            1.  +n Jems

            2.  Icon

            3.  Assign hex values for colours, text etc.

    4.  Every action leads to +1 for that action and every take-back
        (like unliking) counts as -1

2.  **User-level tracking**

    1.  Track maximum events, actions, progress, history and more at a
        user level

3.  **Economy implications**

    1.  The exchange rate for buying and selling Jems will be
        configurable and go into effect for all users immediately upon
        setting

        1.  Configurable via CMS

    2.  When buying or selling, freeze the price for 15 minutes and
        restart with the new exchange rate in case the frozen price
        expires.

4.  **Internal team features**

    1.  Deep instrumentation

    2.  CMS support for

        1.  Josh economy

        2.  Defining rewards and their configuration

        3.  Power-ups configuration

5.  **Backend logging**

    1.  User-level

        1.  Life-time

            1.  Jems bought with INR

            2.  Jems earned

            3.  Jems burned

            4.  Rewards claimed

        2.  Jems earned with timestamp

        3.  Jems burned with timestamp

        4.  Total balance at redemption or recharge with timestamp

    2.  Progress tracking

        1.  User-achievement level

            1.  **Notifications**

6.  **Fraud and manipulation detection**

    1.  Frequency check

    2.  DDoS/brute-force/overload protection

    3.  Spam countering features

    4.  SHIELD SDK to be integrated

7.  **Milestones notifier configuration**

##  Figma

https://www.figma.com/file/fM0YQI7w0e6rV3NzYZTBIj/Reward-Program?node-id=452%3A2699
