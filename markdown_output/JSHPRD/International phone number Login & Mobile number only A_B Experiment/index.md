  ----------------------- --------------------
  **Document Status**     READYGreen
  **Android Sprint**      add release sprint
  **iOS Sprint**          add release sprint
  **Product Owners**      
  **Product Designers**   
  **Android Leads**       
  **Android Devs**        @ android devs
  **iOS Leads**           @ ios leads
  **iOS Devs**            @ ios devs
  **QA Devs**             @ qa devs
  **Josh Lite**           YEsGreen / NORed
  ----------------------- --------------------

##  Executive Summary

International users commonly opt for Facebook and Google as we do not
currently offer mobile number support. With that said, one way to
address the needs of international users is: To extend login through
mobile to accommodate the needs of international users.

##  Objective

International login support through mobile numbers for users outside
India.

##  Success metrics

  ---------------------------------------------- ------------
  **Goal**                                       **Metric**
  Allow international users to login via phone   TBA
                                                 
  ---------------------------------------------- ------------

##  Functional Specifications

- Mobile number login to be extended for international users as well

- Country code will be auto-populated from the phonelib library

- Users will also have an option to select a country from the drop-down

- Selection of country will fill the country code field.

## PWA Requirements

#### LoginLandingPage- Support for international Number

International users commonly opt for Facebook and Google as we do not
currently offer mobile number support, one way to address the needs of
international users is: To extend login through mobile to accommodate
the needs of international users. A mobile phone text field will have a
country code displayed by default which can be modified by tapping and
selecting another country from the country list dropdown.

True caller Users - A bottom sheet appears which will have CTA to "Use
Number" or "User another login method".

Non-True caller Users - For these users, verification needs to be done
using our OTP validation. For this country code will be detected and the
user will be asked to enter the number in the text field.

Detection of country code will happen from sim detection.

If sim detection fails fallback to BE Location Api and the returned
value is used.

If location permission is not granted then detection will be done on ip.

This needs to be done before landing on login landing page incase
detection is not done and user lands on Login Landing page, the code
will be picked from the system pop up.

If even detection from the system pop-up fails, we will fall back to
India country code i.e +91.

**Scenario 1.**

An international user changes country code and sets code for a country
that is not supported i.e Pakistan.

**Behaviour** - The textbox is disabled and when the user clicks on it
he gets an error message "Mobile login is not supported in your country,
Please try other login methods". User can see Facebook and Google login.

**Scenario 2.**

User has selected non supported country code, now wants to change it.

**Behaviour -** Country code selection field is active, user can change
to any other country code. the text box is enabled to enter mobile
number if user has selected a supported country for mobile login

##  Open Questions

  ---------------------------------------------------------------------------- ---------------------------------------------------- -------------------
  **Question**                                                                 **Answer**                                           **Date Answered**
  Will it be country name search only or country/country code basis search ?   Will be searched by both country name and its code   27th Jan
  What happens in case of some wrong search query ?                            Error message to be shown                            27th Jan
  ---------------------------------------------------------------------------- ---------------------------------------------------- -------------------

## Additional Notes

[https://github.com/google/libphonenumber](https://github.com/google/libphonenumber){card-appearance="inline"}

##  Figma

https://www.figma.com/file/7B6DdMIYSatTikLPsbW6FV/Onboarding?node-id=1263%3A803

## Instrumentation

[https://evp.atlassian.net/wiki/spaces/JSHPRD/pages/97910877/International+phone+number+Login+Mobile+number+only+A+B+Experiment#%F0%9F%93%B2-Instrumentation](https://evp.atlassian.net/wiki/spaces/JSHPRD/pages/97910877/International+phone+number+Login+Mobile+number+only+A+B+Experiment#%F0%9F%93%B2-Instrumentation){card-appearance="inline"}
