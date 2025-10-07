## Subscription Groups

- A Subscription group is the parent entity for all subscriptions

- A subscription group is made up of subscriptions with different access
  levels, prices, and durations so people can select the option that
  best fits their needs. Since people can only buy one subscription
  within a group at a time, creating a single group is the best practice
  for most apps as it prevents people from accidentally purchasing
  multiple subscriptions.

- Every subscription plan must be assigned to a Subscription group

- Users can upgrade, downgrade, or crossgrade between plans in the same
  group using a ranking system

  - **Upgrade:** Someone purchases a subscription that offers a higher
    level of service than their current subscription. They're
    immediately upgraded and receive a refund of the prorated amount of
    their original subscription. If you'd like people to immediately
    access more content or features, rank the subscription higher to
    make it an upgrade.

  - **Downgrade:** Someone selects a subscription that offers a lower
    level of service than their current subscription. The subscription
    continues until the next renewal date, then is renewed at the lower
    level and price.

  - **Crossgrade:** Someone switches to a new subscription of the
    equivalent level. If the subscriptions are the same duration, the
    new subscription begins immediately. If the durations are different,
    the new subscription goes into effect at the next renewal date.

> **Note from Apple:** *Multiple subscription groups aren't recommended
> for apps in which people would expect to have a single active
> subscription. Keep your offerings simple and easy to understand. For
> each subscription, create a user-friendly, self-explanatory name that
> differentiates it from others in the group. Use distinct names for the
> app, the subscription group, and each subscription to avoid
> confusion.*

**Note:** [Apple Documentation for Auto-renewing
subscriptions](https://developer.apple.com/app-store/subscriptions/#:~:text=the%20recovery%20date.-,Creating%20subscriptions,-You%E2%80%99ll%20configure%20your)

#### *Summary:*

*Subscription setup is structured as the following:*

- ***Subscription group:** A set of subscription products with varying
  levels and durations. Users can subscribe to one subscription product
  per group at a time.*

- ***Subscription:** A product that lets users purchase dynamic content
  for a set period. Auto-renewable subscriptions renew automatically,
  unless cancelled by the user. Subscription duration and price is
  configured in App Store Connect.*

- ***Subscription levels:** A ranking system of subscriptions within a
  subscription group that determines the upgrade, downgrade, and
  crossgrade path available to subscribers. Levels make it possible to
  offer varying access (basic, premium) of the same service.*

- ***Subscription duration:** The length of time before the subscription
  renews and the subscriber is charged. Possible durations are 1 week, 1
  month, 2 months, 3 months, 6 months, and 1 year.*

### Duration and Pricing

1.  Possible values for Subscription Duration: 1 week, 1, 2, 3, 6
    Months, and 1 Year

2.  Pricing (INR):

    1.  Minimum: INR 9.00

    2.  Maximum: INR 100,000.00

    3.  Steps: 9, 10 (+1), 15 (+5), 19 (+4), 20 (+1) and repeats
        until 500. 39 and 199 are available. Larger steps after 500.

[https://developer.apple.com/help/app-store-connect/manage-subscriptions/manage-pricing-for-auto-renewable-subscriptions](https://developer.apple.com/help/app-store-connect/manage-subscriptions/manage-pricing-for-auto-renewable-subscriptions){card-appearance="inline"}

### Creating Subscriptions in a group via App Store Connect API:

[https://developer.apple.com/documentation/appstoreconnectapi/app_store/auto-renewable_subscriptions/managing_auto-renewable_subscriptions](https://developer.apple.com/documentation/appstoreconnectapi/app_store/auto-renewable_subscriptions/managing_auto-renewable_subscriptions){card-appearance="inline"}

### Offers

[Subscription pricing and offer
types](https://developer.apple.com/help/app-store-connect/reference/pricing-and-availability/)

### Pricing type

+-----------------------+---+
| 1.  **Pay as you go** |   |
+-----------------------+---+
| 2.  **Pay upfront**   |   |
+-----------------------+---+
| 3.  **Free**          |   |
+-----------------------+---+
