  ----------------------- ----------------------------------------------
  **Document Status**     NOT STARTED / IN-PROGRESSYellow / READYGreen
  **Android Sprint**      add release sprint
  **iOS Sprint**          add release sprint
  **Product Owners**      @ product owners
  **Product Designers**   @ product designers
  **Android Leads**       @ android leads
  **Android Devs**        @ android devs
  **iOS Leads**           @ ios leads
  **iOS Devs**            @ ios devs
  **QA Devs**             @ qa devs
  **Josh Lite**           YEsGreen / NORed
  ----------------------- ----------------------------------------------

##  Executive Summary

Describe what the product or feature is about, what's its context and
background is. Describe why it's being carried out.

##  Objective

Provide context on this project and explain how it fits into your
organization\'s strategic goals.cess metrics

##  Functional Specifications

**CMS Requirements:**

1.  Brand Campaign Creation:

    1.  Name

    2.  Live duration of campaign (Start & end date)

    3.  Content id (bulk upload)

    4.  Frequency (To be discussed) - of the brand campaign content

Layout & Elements: (Independent Entities) - for Home feed, feed via
Notification & share path. Also for video detail page via TPV & FPV,
Challenge/contest feed.

1.  Horizontal: Next to engagements Icons (Always at the end position)

    1.  Logo - Redirection icon has to be a part of design

    2.  Text (Character Limit & Ellipses state) - Mandatory for
        horizontal placement

    3.  Animation (to be finalised) - ON/OFF

    4.  Animation Type: Tye 1, 2, 3.

2.  Vertical: Top on the right Grid.

    1.  Logo - Redirection icon has to be a part of design

    2.  Animation

    3.  Animation Type: Tye 1, 2, 3.

Data Points - (Both vertical & horizontal icons can co-exist) - Max 2
sets will come in the response.

Set 1:

1.  Flag to show Brand icon

2.  Layout -(Horizontal/Vertical)

3.  Logo Url (32\*32)

4.  Animations - Type 1, 2, 3

5.  Text

6.  LP - URL (Can be deeplink or external)

7.  Campaign Id

8.  Brand Id

Set 2:

1.  Flag to show Brand icon

2.  Layout -(Horizontal/Vertical)

3.  Logo Url

4.  Animations - Type 1, 2, 3

5.  Text

6.  LP - URL (Can be deeplink or external)

7.  Campaign Id

8.  Brand Id

(Sponsored/promoted Tag & Case with already 5 icons, Redirect icon with
Brand Logo)

When Campaign_id is present in a response don't send Zone or Ads Like
CTA.

Phase 1 (Callouts)

1.  No counter for branded logos

2.  Single animation enabled for logos

**Response would be an array with 2 different elements.**

Instrumentation:
[https://docs.google.com/spreadsheets/d/1f3mHeHN2ivXaYZncxBoVI3Y619bfwlX2O_omn_8EB_Y/edit#gid=785720233](https://docs.google.com/spreadsheets/d/1f3mHeHN2ivXaYZncxBoVI3Y619bfwlX2O_omn_8EB_Y/edit#gid=785720233){card-appearance="inline"}

Idea:
[https://docs.google.com/presentation/d/1K_ISTvTmSsMqEUN5O-BL17r0_30IKcH6Fn87VO9Lk5U/edit#slide=id.g153492f0c8e_0_45](https://docs.google.com/presentation/d/1K_ISTvTmSsMqEUN5O-BL17r0_30IKcH6Fn87VO9Lk5U/edit#slide=id.g153492f0c8e_0_45){card-appearance="inline"}

Figma:

https://www.figma.com/file/lZGqTG7GWnziqkxtM2qDvR/Josh-ads?node-id=7630%3A32735

Protocol:

graphqlwide{   \"campaign_info\": {     \"show\": true,    
\"campaign_id\": \"campaign_id here\",     \"brand_id\": \"brand id
here\",     \"horizontal\": {       \"logo_url\": \"logo url here\",    
  \"text\": \"description about compaign like ThmbsUp Coca-cola\",      
\"deep_link\": \"deeplink url here\",       \"show_animation\": true,  
    \"animation_type\": \"1 or 2 or 3 or 4\"     },     \"vertical\": {
      \"logo_url\": \"logo url here\",       \"text\": \"description
about compaign like ThmbsUp Coca-cola\",       \"deep_link\": \"deeplink
url here\",       \"show_animation\": true,       \"animation_type\":
\"1 or 2 or 3 or 4\"     }   } }

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

List the features discussed which are out of scope or might be revisited
in a later release.

## Reference Materials

Add links to research and other key documents here.

## Additional Notes

Add additional notes or comments, if any.

##  Figma

Type /image to add mockups, diagrams, and screenshots related to the
requirements.

## Instrumentation
