  ----------------------- --------------------
  **Document Status**     READYGreen
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
  ----------------------- --------------------

##  Executive Summary

We\'ve noticed a questionable drop-off in sign-up flow. We collated data
for the last 60 days (10th Oct 2021-8th Dec 2021) and discovered that
there is a significant drop in the percentage of users between the
language selection page and signup completion. Very few users complete
the sign-up flow.

##  Objective

Optimize steps in order to save users from having to put any effort into
completing the flow.

##  Success metrics

List project goals and the metrics you\'ll use to judge its success.

  ----------------------------------------------------- ------------
  **Goal**                                              **Metric**
  Increase % of users completing the sign up process.   TBA
                                                        
  ----------------------------------------------------- ------------

## Analysis

## [Login Landing Page]{.underline}

### Observations 

- Users landing on Login Landing Page \~ 300K

- Users have 3 options to log in - Mobile, Facebook & Google.

- Users clicking on any of the three options \~ 168K

- There is a drop of 44% from Login Landing to the mode of Login
  selection.

- Users opting with mobile signup is highest constituting 45% followed
  by Facebook \~ 31% then Google.

##  Assumptions

### Possible reasons to drop

- Users are not sure what to do next.

- Multiple login options might confuse users

- Users are too lazy to enter their phone number

- Users not comfortable sharing their number

- Users escaping from multiple steps

- The screen is not appealing enough for users to proceed

##  Functional Specifications

#### Login Landing Page

- Users should be shown a catchy login title that interests them to log
  in and explore.

- Users should be provided with three options to log in - Mobile, FB,
  Google.

- Mobile login option to be prompted on Landing login page.

- For dual sim devices, users get an option to select the number.

- The selection of phone numbers can be done from the pop-up menu.

- For experimentation, there will be one variant without social login
  option

- Mobile number login to be extended for international users as well

- Country code will be auto-populated from the geo library

- Users will also have an option to select a country from the drop-down

- Selection of country will fill the country code field

- For Inline login, when Tc is installed the user will see the TC bottom
  sheet to log in with a single tap.

- If the user selects another login method on the inline login page, the
  user will see a full-screen login landing page.

- If TC is not installed, we use the same current screen with a mobile
  number login on top.

#### Enter OTP Page

- On the OTP page, users will see verified OTP titles.

- The mobile number on which OTP has been sent will be shown

- Resend link will be positioned to the right for better access

## PWA Requirements

#### LoginLandingPage- Title Change

Showing a title to the users which tells the reason behind and benefits
they would get. Here specifying login to create a profile which will
allow them to follow profiles, make their own videos and from them.  If
they know what all they can do after logging in, they'll be more likely
to log in and complete steps. Keep this page clean so that users are not
distracted.

#### LoginLandingPage- Auto-detection of mobile number via TrueCaller

Optimizing this page that auto-fills the mobile number field with
users\' phone numbers to reduce the step in the funnel associated with
typing in a large string of numbers. This will reduce users\' efforts,
minimize error submissions from incorrect typing in the mobile number
field with the user's number. This will also reduce a step in the signup
funnel. With TrueCaller integration the entire OTP verification page can
be skipped. With TrueCaller integration, a bottom sheet will appear
where the user has two option

1.  User Number - The user can tap on this and proceed to the next step,
    OTP verification page will be skipped in this flow.

2.  Log in with another type - If the user has TrueCaller and still
    wants to login via Google or Facebook or any other number, the user
    can tap on the link and go back to Login Landing Page

3.  On the Login Landing page, users can proceed with FB and follow the
    FB funnel.

4.  Users can also select Google and proceed with Google Login

5.  Users can tap on the phone number field and enter another phone
    number.

#### EnterOTPPage- No OTP flow (TrueCaller users)

With the integration of TrueCaller, as soon as users tap on the number
which is populated in the bottom sheet, the user will be directly taken
to the "Allow contact" page. The entire OTP verification step can be
skipped for users who have TrueCaller installed on their phones.

#### EnterOTPPage- Auto-detection of OTP from SMS(without TrueCaller)

After the user clicks on "Send OTP", an OTP is sent. Instead of asking
users to manually enter the OTP and auto-detected OTP from SMS can
optimize the flow of traffic.

#### EnterOTPPage- Auto-submission from OTP text-box

After OTP is detected, an auto submission mechanism can make this flow
effortless for users.

In this flow reading OTP from SMS, populating it in the OTP text box and
its submission can be automated and sent to the system that is not
directly linked with external action by the user.

#### EnterOTPPage- OTP text change

For scenarios where auto-detection is not done due to a technical
glitch, manually entering the OTP will be a fallback case. While asking
users to enter their one-time password, we can educate them slightly
here as well to utilize the application for sharing OTPs that were
shared on their number earlier. This way the user feels more at ease and
conversational.

#### EnterOTPPage - Reposition Resend

Changing the position of the "Resend" button to the right side makes it
easily accessible to users.

**Summary for TrueCaller flow**

  ---------------------------- ----------------------------------- -------------------
  **Scenario**                 **Flow**                            **Config**
  TrueCaller Present           One Tap Login                       
  TrueCaller not present       Enter Number with Country code      
  Non TrueCaller (India)       Existing JOSH OTP flow              BE enabled config
  Non TrueCaller (non-India)   TrueCaller SDK - OTP verification   BE enabled config
  ---------------------------- ----------------------------------- -------------------

 Open Questions

  ----------------------------------------------------------------- ----------------------------------------------------------- -------------------
  **Question**                                                      **Answer**                                                  **Date Answered**
  Decision on skippable login screen.                               This page is dropped for TC login flow                      27th Jan
  Will TC be integrated to other login screens like inline login.   TC login flow to be integrated with Inline login as well.   27th Jan
  ----------------------------------------------------------------- ----------------------------------------------------------- -------------------

##  Out of Scope

There is the scope of optimization in the transition from the Language
select page to the Login Landing page as well. We have seen a drop of
100K however, due to error instrumentation not in place improvisation
for this step is not included. 

Details of errors in the signup flow will give us more opportunities to
optimize this funnel. We plan to enhance the following flow with more
access to data

- Drop off from Language selection to Login Landing Page

- Drop off from Sign up completion to view Allow contact Page

- Errors occur in the signup process and contact sync process.

## Reference Materials

True caller documentation -
[https://docs.truecaller.com/truecaller-sdk/android/user-flows-for-verification-truecaller-+-non-truecaller-users](https://docs.truecaller.com/truecaller-sdk/android/user-flows-for-verification-truecaller-+-non-truecaller-users){card-appearance="inline"}

## Additional Notes

[https://docs.google.com/spreadsheets/d/140PnhXKBxt9lwrgQaeLqHnsivIw9ROaCFdl9v6t43DA/edit#gid=41144892](https://docs.google.com/spreadsheets/d/140PnhXKBxt9lwrgQaeLqHnsivIw9ROaCFdl9v6t43DA/edit#gid=41144892){card-appearance="inline"}

##  Figma

https://www.figma.com/file/7B6DdMIYSatTikLPsbW6FV/Onboarding?node-id=1263%3A803

## Instrumentation
