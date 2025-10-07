## **NOTE:** This document is only for archival and is not to be used. Please refer to Live Virtual Gifting 1.0 for updated and actual specs of this feature.

  ----------------------- -------------
  **Document Status**     OUTDATEDRed
  **Product Owners**      /
  **Product Designers**   
  **Josh Lite**           YEsGreen
  ----------------------- -------------

##  Executive Summary

Gifts are thoughtful virtual items that can be bought using *Jems*
(inspired by the word Gems) and given to support their favourite
creators in livestreams. Jems are in-app virtual currency that can be
bought against real money and are bundled at different prices. 

##  Objective

Goal is to explore live monetization through virtual gifting and in-app
purchases.

##  Success metrics

  ----------------------------------------------------- ----------------------------------
  **Goal**                                              **Metric**
  Users purchasing Jems to send virtual gifts           Transaction & revenue increases
  Users sending virtual gifts with the purchased Jems   Transaction & revenue increases
  Increased time spent in the live feature              Engagement & retention increases
  ----------------------------------------------------- ----------------------------------

## Competitive Analysis

Other platforms that support virtual gifting and live tipping:

- Instagram

- TikTok

- Tango

##  Functional Specifications

####  **Feed & Live Landing Page**

- Live coachmark nudge to have new text that indicates X jems added to
  wallet for users who tap the live button (default X = 50)

- For first time users visiting the landing page, show congratulations
  popup and add jems to the user's wallet (this is only a first time
  behavior)

####  **Room**

- Gifts can only be shared by viewers and not the host and speakers

- Gifts only go to the host and not speakers present in the room

- If the original host leaves, gifts go to the latest host

- Viewers will now see a gift option available that enables them to send
  virtual gifts to creators

- For first time users, show coachmark nudge

- On tap, open BottomSheet with gift options (BottomSheet should have a
  SlideUp / SlideDown animation)

- On tap of a gift, if there is balance of jems in the wallet, send the
  gift and if not, open the Google Play payments popup to enable users
  to buy the same number of jems as the value of the gift

- Once the jems are added to the wallet, the user should tap again to
  send the gift (since it would be unfair to automatically send it
  assuming user may change their mind)

- If the user dismisses the Google Payments / iTunes Payments
  BottomSheet, show the Buy Jems BottomSheet behind it and throw a snack
  message saying 'Insufficient funds. Buy jems to send a gift.'

- Once a gift is shared, it is shown in the comments for everyone to see

- If the gift is the kohinoor, animate the asset in full screen first
  and then shrink inside the comment

- Animation should be broadcasted to all users via Tencent

####  **Buying Jems**

- Jems can be bought in bundles or packages

- When a user taps a package, trigger the Google Play payments
  BottomSheet to facilitate payment

- On success callback, add the jems to the user's wallet and show
  success popup

- If payment fails, show appropriate snack message

- Ops can also configure flash sale which displays discount %, countdown
  timer, jems package and discount

- If a user reaches the max number of package purchases that they can
  make during a flash sale, show the appropriate snack message

- On tap of Jems balance, go to Jems wallet page

####  **Jems Wallet**

- Jems wallet to be added in profile settings

- On tap of the wallet, user has the option to recharge, which will
  trigger the Buy Jems flow above

- Jems redemption, transaction history and FAQs to be taken from the
  user rewards flow

## Error Handling

List all product and feature errors and edge cases here.

## BE & CMS Requirements 

- **Jems Configurability**

  - INR to Jem base price (buy)

  - INR to Jem base price (sell)

  - INR to Jem base price (earn)

  - Package types

    - Number of jems in package

    - Price automatically calculated basis base price

    - Discount

    - Package labels & colour (Hot, New)

  - Flash sale

    - Flash sale start / end date

    - Number of jems

    - Discount

    - Repurchase rules (max X times)\

- **Gifts Management**

  - Adding / removing / managing a gift

  - Editing gift name, image and meta

  - Gift value

  - Gift discount\

- **Josh Live Ops Portal**

  - Ability to add / manage / remove creators / agencies

  - Control % pay between creators / agencies

  - Add / edit bank account details of creators / agencies

  - View transaction history of creators / agencies

  - \[?\] View live stats of creators / agencies\

- **Agency Portal**

  - \[?\] Ability to add / manage / remove creators in their portfolio

  - \[?\] View transaction history of creators

  - \[?\] View live stats of creators / agencies

##  Open Questions

  ------------------------------------------------ ----------------------------------------------------------------------- -----------------------
  **Question**                                     **Answer**                                                              **Date Answered**
  Payment gateway will be native or third-party?   e.g., We\'ll announce the feature with a blog post and a presentation   Type // to add a date
  ------------------------------------------------ ----------------------------------------------------------------------- -----------------------

##  Out of Scope

List the features discussed which are out of scope or might be revisited
in a later release.

## Reference materials

Add links to research and other key documents here.

## Additional Notes

Add additional notes or comments, if any.

##  Figma

Type /image to add mockups, diagrams, and screenshots related to the
requirements.

## Instrumentation
