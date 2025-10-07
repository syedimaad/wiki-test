  ----------------------- ----------------------------------------------
  **\@Document Status**   NOT STARTED / IN-PROGRESSYellow / READYGreen
  **Product Managers**    
  **Product Designers**   
  ----------------------- ----------------------------------------------

## Context & Summary

Implementation of Clickable Exit Splash Ads on user doing the double
back to exit the App.

## First principles note

1.  Placing the exit splash ad on doing the double back to exit the app
    will create ads inventory and also a new ad format

2.  Revenue impact

##  Objective

Placing the Exit Splash Ad on user doing the double back to exit the App

##  Success metrics

  ---------------- --------------------------- ------------------- ------------------
  **Goal**         **Metric**                  **Current Value**   **Target Value**
  Revenue Impact   Ad Impressions, Ad Clicks   0                   
  ---------------- --------------------------- ------------------- ------------------

## Competitive Analysis

ShareChat does an Exit Splash Ad

##  Functional Specifications

1.  Creating a Ad Slot named as exit splash for users who do double back
    to exit from the app.

2.  This Ad slot supports Image/HTML (to support Video)/GIF and should
    be clickable

3.  This Exit Splash Ad is of two types:\
    a) Full Screen Exit Splash\
    b) Mini Screen Exit Splash

4.  This ad should support both direct and network ads. Network ads to
    be disabled in phase 1

5.  This Ad slot should have a cross button on top right for the user to
    dismiss the Ad. When user clicks on cross button the user should
    exit the app as his natural flow

6.  The splash should have configuration to auto dismiss after X secs.
    On auto dismiss the user should exit the app as his natural flow

7.  This X secs has to be configurable at BE

8.  When the user clicks on CTA or the ad, open the LP on internal
    chrome browser

9.  If an user clicks on the ad/cta and lands to a LP and then does
    double back he shouldn't be shown the exit splash now - configurable
    (back to splash or exit the app)

10. New Zone to be added in DD called "Exit Splash"

11. This zone should have all targeting features

12. Tracking to be enabled for capturing the impressions and click. 3rd
    party trackers to be enabled

13. Ability to switch the ad slot on or off should be provided

14. New User exclusion should have a different configuration for this ad
    slot

15. Thin/regular user targeting to be built

### **Additional Information:**

1.  This Ad should be End to End bleed on the user screen. The status
    bar of the user device should be immersive of the **Full Screen Exit
    Splash**

## BE & CMS Requirements

New Ad format and inventory Bed to be created on Daedalus

##  Open Questions

## Reference Materials

[https://drive.google.com/file/d/1MzmbRYESnXPOh9cJEC0I7m9NkrluOpjz/view?usp=drivesdk](https://drive.google.com/file/d/1MzmbRYESnXPOh9cJEC0I7m9NkrluOpjz/view?usp=drivesdk){card-appearance="inline"} -
ShareChat reference

[https://docs.google.com/spreadsheets/d/1WajuhhIqlcpvOO3kTYU3Xa1emjFBw513tQLMd7Kr1ag/edit#gid=1342203425](https://docs.google.com/spreadsheets/d/1WajuhhIqlcpvOO3kTYU3Xa1emjFBw513tQLMd7Kr1ag/edit#gid=1342203425){card-appearance="inline"} -
Data for Normal Exit and Force Exit - UUs

##  Figma

https://www.figma.com/file/hdwp9MwoN1Nvb4ipYzR2tA/Ads-Master-File?node-id=2036%3A42039https://www.figma.com/file/hdwp9MwoN1Nvb4ipYzR2tA/Ads-Master-File?node-id=2049%3A48747
https://www.figma.com/proto/hdwp9MwoN1Nvb4ipYzR2tA/Ads-Master-File?node-id=2143%3A49005&scaling=min-zoom&page-id=2049%3A48747&starting-point-node-id=2143%3A48535

https://www.figma.com/proto/hdwp9MwoN1Nvb4ipYzR2tA/Ads-Master-File?node-id=2037%3A43305&scaling=min-zoom&page-id=2036%3A42039&starting-point-node-id=2044%3A43870&show-proto-sidebar=1

### **Meeting Notes:**

[https://docs.google.com/document/d/1pbinybhOHc-qXDpSnjyzRqbLIGKsQAQ2KRoUAeT75TY/edit](https://docs.google.com/document/d/1pbinybhOHc-qXDpSnjyzRqbLIGKsQAQ2KRoUAeT75TY/edit){card-appearance="inline"}

## Instrumentation

We need to capture the below three events and all the events which our
regular ads have.

1.  Auto Dismiss of the Ad event

2.  User clicking on Dismiss button to close the Ad

3.  User clicking on Ad to go to LP
