  ----------------------- ---------------------
  **Document Status**     IN-PROGRESSYellow
  **Android Sprint**      add release sprint
  **iOS Sprint**          add release sprint
  **Product Owners**      
  **Product Designers**   @ product designers
  **Android Leads**       @ android leads
  **Android Devs**        @ android devs
  **iOS Leads**           @ ios leads
  **iOS Devs**            @ ios devs
  **QA Devs**             @ qa devs
  **Josh Lite**           YEsGreen / NORed
  ----------------------- ---------------------

##  Executive Summary

User views a shoppable video on their feed and is presented with
products tagged to the video while the playback continues in the
background. Tapping on the presented product will deep link the user to
the purchase funnel of a 3P merchant property

##  Objective

Enable users to discover and shop for physical products contextual to
the video being served to them on their respective feeds

##  Success metrics

List project goals and the metrics you\'ll use to judge its success.

  ------------------------------------ ---------------------------------------------
  **Goal**                             **Metric**
  e.g., Simplify the user experience   e.g., Customer satisfaction score increases
                                       
  ------------------------------------ ---------------------------------------------

## Competitive Analysis

Provide information on your top competitors here.

##  Assumptions

List any assumptions you have about your users, technical constraints,
or business goals.

##  Functional Specifications

# **Qualifying Videos**

- Whitelisted users\' id will qualify to be marked as shoppable (list
  [[here]{.underline}](https://docs.google.com/document/d/1e0ufcop4Q8888Wb3WZKM0WbrMLiq7mh1CZiXtEoBYJQ/edit#bookmark=id.7j1246o1ec12))

- CMS: Content ops will have a tool to pick videos from these
  whitelisted users\' id and mark them as shoppable + tag products /
  SKUs to them

  - When marked so, content ops can also tag the item(s) from a partner
    product catalog to the video 

  - Tagging controls on CMS

    - Single/multiple items (capped at 5)

    - Decking order 

    - Displayed in the vertical masthead carousel

  - CMS / Ads: Fetch (latest) metadata of card + Ability to modify

    - Product Brand

    - Product Price

    - Featured Image (from a set of merchant images) 

    - Merchant name

    - Discount %

# **Shoppable Content Experience**

Multiple experiences will be modeled for when the shopping experience
kicks in on defined configurable triggers. 

- Shoppable items will be displayed in the masthead tray on the left
  side of the Home feed

- Replacement widget

  - Used in the case of multiple products tagged to a shoppable video

  - Basis defined triggers, auto-transition / animate the bottom section
    down and sidebar towards the right

  - Animate in (from the bottom) a widget, to display an API ordered
    carousal of tagged products

  - Widget is vertically scrollable with a max. of 5 items (capped at
    CMS)

  - On tap of the \>\> button, transition out the masthead tray (to the
    left)

  - A configurable trigger can be Default type only.

- In-place widget

  - Used when only a single product is tagged to a shoppable video

  - Basis configurable triggers, transition / animate ~~the Shop Now
    button to present a single~~ card as depicted in the UI

  - The configurable trigger can be Default or Custom types

- Configurable triggers

  - Default 

    - Display Widget: User watches videos for \>x seconds (default = 3s)

    - Kill Widget: Once visible on screen, the user doesn't interact
      with a widget for \>y seconds (default y = 7s)

  - Custom 

    - Display Widget: CMS defined start time marker

    - Kill Widget: CMS defined end time marker

    - Each video may have multiple marker sets (forward-looking) #To be
      decided

- Once user/session/brand thresholds (defined in the next section) kick
  in, and further shoppable ads are served in the feed, 

  - Do not present the widget to the user via auto-transition

- Users can view the masthead tray on the left side of the Home feed
  with single or multiple cards

- Tapping on any shoppable card will 

  - Open the appropriate deep link in the 3P app if present or in a
    **Chrome Tab** (not the browser in order to borrow the login from
    Chrome app if the user is already logged in to the merchant site
    there + to avoid 3P deep link redirection complications)

  - (Legality) Dwell the user on the feed/chrome tab for n seconds
    (default 2s) to display appropriate redirection messaging on a
    blocking popup with the message "You are now leaving Josh and are
    being redirected to [Amazon. in](http://Amazon.in)"

- Sidebar configurability similar to branded content/ads \[CHECK\] 

  - Ops can choose which ones to show/hide among Profile, Like, Comment.

  - 3-dots is fixed and will need to be modeled to point to a PWA report
    page where  the context of shoppable ads is captured downstream

  - \[CHECK\] If ad/content is not linked to any user/brand profile,
    then hide the profile icon in the sidebar, and on swipe, treat as
    CTA and react accordingly

# **Feed Experience**

- CMS / Static Config + Feed: Model for F-capping at video level,
  creator level, user level, session-level in that order

  - Video

    - Repeated views of the same video drive the denominator higher

    - Feed UX / fatigue

    - To manage merchant commitments/expectations

  - Creator

    - Limit per creator/type to level the playing field 

    - For eg., cap for Faisu = 3 vs. non-platinum creator = 5

  - User

    - Frequency control to remove the fatigue of seeing shoppable
      content repeatedly, especially for non-engaged users

    - To maintain the exclusivity when user attention is actually
      required (rather than letting it be amortized + decayed over time)

- Session: Similar as user + balance feed UX vs. ads

- Manipulate video on feed basis type of shoppable video and above
  thresholds

  - Shop Now button reacts to the default display widget trigger and
    color transitions from translucent to opaque/white

  - The shopping experience becomes user-triggered only ie., the user
    will need to tap on the Shop Now button in order to invoke the
    widget

# **Brand Profiles**

- Enhancements, if any, are being discussed

- Shoppable content marked as a different type of video (ref: duets)
  within promo TTL?

- FPV: Insights to include shoppable content information
  (forward-looking)

# **Attribution & Measurement**

Each item will need to be instrumented and attributed at a creator +
item level

- Appropriate instrumentation on the client-side will enable measurement
  of #views of widgets and CTA engagement on Shop Now & on items

- (?) 3P merchants/partners will provide deep link URLs attributable to
  Josh and to the individual creator within Josh (Optimise Media?) 

- (?) On tap/click of any shoppable product in the widget, for internal
  reconciliation, fire an internal campaign beacon on tap of the item
  deep link  including but not limited to below attributes/params

  - Merchant ID

  - Product / SKU ID

  - Product Price

  - Video ID

  - Creator ID / Sub-affiliate ID

  - Affiliate ID

  - Other Standard Ad Params as required

- Reporting will need to be recorded at creator level, drilling down to
  videoId, merchantId, productId, product meta 

- Reconciliation with 3P data will need to be carried out (Optimise
  Media?)

# **Whitelisted UserID**

To be provided by Content Strategy Team ([[Sahil
Bhagat]{.underline}](mailto:sahil.bhagat@verse.in) to follow up)

1.  Select some managed/identified users and only some of their selected
    items to prompt shopping flow as overlays on them

2.  Lambda for
    [http://accio.ai](http://accio.ai){card-appearance="inline"} , for
    items from #1 with userId and itemId details

3 a) extraction and catalog matching done in
[http://accio.ai](http://accio.ai){card-appearance="inline"} offline
pipeline, meta in the desired format composed

3 b) allow ops to override for final selection, the timing of overlay
(frame/seconds start to end), and ordering of products from the enriched
output from #3a)

4\. Postback of enriched meta with proposed attribution parameters,
userId, and itemId to ads endpoint from
[http://accio.ai](http://accio.ai){card-appearance="inline"} pipeline

5\. Ads to enable campaign management flow, campaign delivery goals,
delivery constraints, tracking and exposing meta API for shopping widget

6\. App to send details on shopping widget exposure/occurrences to feed
request and receive distancing constraints in feed response

7\. App to invoke ads API for shopping widget meta and tracker URLs to
fire.

# Home Feed

With the introduction of the Shop and Games tab on the home feed, there
will be a new position introduced for the Profile and Notification icon.

Shop - Placed on the 4th position on the bottom menu bar. Clicking on
the Shop tab will take the user to the feed where all shoppable content
could be accessed by scrolling.

Games - Placed on the 5th or the last position on the bottom menu bar.

Profile - Placed on the right top corner of the home feed.

Notification - Placed on the right top corner before the Profile icon.

For You - For You tab to be accommodated inside the drop-down with other
tabs on the left top corner.

Following - Placed inside the drop down of Josh Icon on the left top
corner.

## Error Handling

List all product and feature errors and edge cases here.

## Notification Requirements

List all requirements for push, local & inbox notifications as well as
flash messages.

## PWA Requirements

List all requirements for web & PWA pages needed in this feature.

## BE & CMS Requirements

[https://evp.atlassian.net/wiki/spaces/JSHPRD/pages/102793299/Shoppable+Content#%E2%9B%93-BE-%26-CMS-Requirements](https://evp.atlassian.net/wiki/spaces/JSHPRD/pages/102793299/Shoppable+Content#%E2%9B%93-BE-%26-CMS-Requirements){card-appearance="inline"}

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

https://www.figma.com/proto/2gaMkq0wJiJJzTofrF5So6/E-commerce?node-id=931%3A7970&viewport=243%2C48%2C0.51&scaling=min-zoom&starting-point-node-id=931%3A7970&show-proto-sidebar=1

##  Figma

https://www.figma.com/file/2gaMkq0wJiJJzTofrF5So6/E-commerce

## Instrumentation
