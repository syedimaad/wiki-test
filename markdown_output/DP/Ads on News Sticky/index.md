  ----------------------- ----------------------------------------------
  **Document Status**     NOT STARTED / IN-PROGRESSYellow / READYGreen
  **Product Managers**    
  **Product Designers**   
  ----------------------- ----------------------------------------------

## Context & Summary

Use news sticky to show ads to user in order to bridge the content and
ad DAU gap

## First principles note

1.  Place content/banner ads in news sticky to show ads to user who only
    interact with notification

2.  High value content promotion with \$ backing to be placed here

##  Objective

1.  Users who only interact with notifications ie click on next/previous
    in a news sticky, refresh a news sticky, remove notification from
    tray\--\> show ads to such users

2.  Since they are a part of content DAU, make them a part of Ad DAU too

##  Success metrics

List project goals and the metrics you\'ll use to judge its success.

  ------------------------------------------------------------ ----------------------------------------------- ------------------- ------------------
  **Goal**                                                     **Metric**                                      **Current Value**   **Target Value**
  Increase content dau to ad dau conversion in notifications   Notification refresh,swipe= impression          0                   
  Increase inventory Bed                                       impressions generated from ads on news sticky   0                   
  ------------------------------------------------------------ ----------------------------------------------- ------------------- ------------------

##  Functional Specifications

1.  News sticky to have a card reserved for an ad slot. This ad slot can
    either support an image banner or a branded article

2.  ~~News sticky to have a masthead ad below the news article.~~

3.  Click to land to the URL configured on the ad opened within the
    internal browser of the app/chrome/chrome tab.(similar to config of
    ads today)

4.  Ad slot enablement to be controlled by Ad BE and to be targetable
    basis thin/regular user cookie

5.  Ads should not be the 1st card in sticky. Below behavior is
    expected:

    - User can click on 1st card n hence sees the ad because the 1st
      card in sticky goes away(ticker will auto swipe when user is on
      the tray hence ad can be 1st card)

    - User moves to next card in sticky n hence sees the ad

    - If ad becomes the 1st card due to some action done by user in
      previous content cards or auto transition then move ad to 2nd card

6.  Click tracking to be available

7.  ~~Place an ad only on the next arrow click by user~~

8.  Request in API=View/posted on tray with non trackability\-\--\> Ad
    requested/ ad inflated event to be fired

9.  Soft impression: User who clicked on item/next/previous/cross; ie if
    user has seen any card after ad position we are assuming user has
    seen the ad

10. Full Impression: User who clicked on item/next/previous/cross on the
    ad item itself then fire a full impression

11. Extra pixel is needed , for delivered only, 3rd party. Still not
    feasible to get view confirmation.

## BE & CMS Requirements

- DD to have a new slot called news sticky

##  Open Questions

  -------------------------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------
  **Question**                                                                                                               **Answer**                                                                                                                                                                 **Date Answered**
  Do we want to do banners on news sticky?                                                                                   Yes                                                                                                                                                                        Type // to add a date
  Behavior confirmation\--\> User has swiped and then locked screen. Comes back to mobile, 1st news loads for news sticky.   observation was it stays on the item it had last scrolled to till it was auto-refreshed. In case it was auto-refreshed it would start from first item (Verified by Atul)   02/05/2022
  Can we add HTML pixel tracking on sticky cards?                                                                                                                                                                                                                                                       
  -------------------------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------

##  Out of Scope

1.  Check feasibility of callback during sticky news card view→ Not
    possible

List the features discussed which are out of scope or might be revisited
in a later release.

## Reference Materials

Add links to research and other key documents here.

## Additional Notes

1.  Sent= Available impressions

2.  Delivered= Delivered Impressions

3.  Soft impressions= Guarantee Impressions

4.  Hard Impressions=Engaged Users

5.  Soft Impressions\--\> Remove ad if fired/remove on sticky
    refresh/remove on expiry/no impression/full impression

Add additional notes or comments, if any.

##  Figma

https://www.figma.com/file/hdwp9MwoN1Nvb4ipYzR2tA/Ads-Master-File?node-id=1712%3A24522

## Instrumentation
