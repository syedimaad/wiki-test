  ----------------------- --------------------------
  **Document Status**     IN-PROGRESSYellow
  **Product Owners**      ,
  **Product Designers**   UI has been shared below
  ----------------------- --------------------------

##  Executive Summary

Magzter to introduce a feature to improve conversion rates for users
arriving from Google. This initiative leverages a time-limited
promotional offer on Gold subscriptions, targeting users who come to the
website through Google searches. The offer activates for 24 hours after
the user arrives on the site, providing an incentive to subscribe.

## Feature Summary

This feature detects when a user is referred to www.magzter.com via
Google and provides them with the **Gold Subscription** at an offer
price for **24 hours**. If no current Gold offer is active, the special
offer will activate, displaying a timer to the user to indicate the
limited-time nature of the discount. The timer starts when the user
first lands on any page within the site after coming from Google.

##  Objective

- **Increase conversion rate** for users visiting the Magzter website
  from Google searches.

- Provide the **Gold Subscription** at an **offer price** for 24 hours,
  only for users referred from Google.

## Target Audience

- **Users referred by Google**: The system will identify users arriving
  from [www.google.com](http://www.google.com/) by checking the referrer
  header.

## Feature Details

### 1. **Google User Detection**

- The feature will detect if a user is coming from Google by checking
  the **referrer header** for "[www.google.com](http://www.google.com)"

- If the referer matches Google and no existing Gold offer is running,
  the system activates the Gold subscription offer for 24 hours.

### 2. **24-Hour Cookie for Offer Persistence**

- Once a user is identified as coming from Google and the offer is
  activated, a **cookie** will be set on their browser.

- This cookie stores the information that the user is eligible for the
  Gold offer for the next 24 hours, ensuring the offer is available
  across all Magzter pages during that time.

### 3. **Offer Timer**

- The user will be presented with a **countdown timer** on the home
  page, displaying the remaining time for the offer. (Similar to the
  current offer UI)

- The user will also be displayed with a timer on the Magazine Details
  page as per the following UI -
  [https://www.figma.com/design/qeQWT6BBp6O0kk2njdr0XG/organic-search-offer?node-id=0-1&node-type=canvas&t=oevwZAqZcv9HJf1C-0](https://www.figma.com/design/qeQWT6BBp6O0kk2njdr0XG/organic-search-offer?node-id=0-1&node-type=canvas&t=oevwZAqZcv9HJf1C-0){card-appearance="inline"}
  . This can be displayed at regular Gold offer time also if the expiry
  is within 72 hours.

- The timer starts from the moment the user first lands on any page
  after arriving from Google.

### 5. **No Offer if Already Active**

- If there is an existing Gold offer running on the site, the system
  does **not activate this special offer** for Google-referred users.

- This ensures no conflicts with other promotional strategies or offers.

## Edge Cases

1.  **User Visits After 24 Hours**:

    - If the user returns to the website after the 24-hour period, the
      offer will no longer be available unless another Google-referred
      visit occurs.

2.  **Users visits again reference from Google**:

    - If user visits again from Google with referrer during the special
      24 hour offer time, no need to extend the offer duration.

3.  **User Already Has Active Subscription**:

    - If the user already has a Gold subscription, this offer will not
      apply.

##  Success metrics

  -------------------------- -----------------------------
  **Goal**                   **Metric**
  Increase Conversion Rate   New User to Conversion Rate
                             
  -------------------------- -----------------------------

## Error Handling

List all product and feature errors and edge cases here.

##  Open Questions

  ----------------------------------------------------------- ----------------------------------------------------------------------- -----------------------
  **Question**                                                **Answer**                                                              **Date Answered**
  e.g., How might we make users more aware of this feature?   e.g., We\'ll announce the feature with a blog post and a presentation   Type // to add a date
  ----------------------------------------------------------- ----------------------------------------------------------------------- -----------------------

## Instrumentation

- GA Event Tracking to be enabled for tracking activations of this offer

- Conversions are already available in GA, we can match the above event
  and track conversions
