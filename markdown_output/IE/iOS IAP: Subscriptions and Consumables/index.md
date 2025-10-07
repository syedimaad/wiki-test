1.  **Accept the Paid Apps Agreement**\
    To offer in-app purchases, your membership Account Holder will need
    to [accept the Paid Apps
    Agreement](https://developer.apple.com/help/app-store-connect/manage-agreements/sign-and-update-agreements)
    in the Business section of App Store Connect.

2.  **Design your in-app purchase**\
    To ensure your in-app purchase experience fits well with the rest of
    your app and effectively showcases your products, review the [Human
    Interface
    Guidelines](https://developer.apple.com/design/human-interface-guidelines/technologies/in-app-purchase)
    and [App Review
    Guidelines](https://developer.apple.com/app-store/review/guidelines/).

3.  **Configure in-app purchases in App Store Connect**

    [Create in-app
    purchases](https://developer.apple.com/help/app-store-connect/manage-consumable-and-non-consumable-in-app-purchases/create-in-app-purchases)
    and add metadata, such as product name, description, price, and
    availability. You'll also need to [generate in-app purchase
    keys](https://developer.apple.com/help/app-store-connect/configure-in-app-purchase-settings/generate-keys-for-in-app-purchases)
    and [set a tax
    category](https://developer.apple.com/help/app-store-connect/configure-in-app-purchase-settings/set-a-tax-category-for-in-app-purchases),
    which will allow Apple to calculate the appropriate tax on customer
    transactions.

4.  **Implement StoreKit**

    Add the [in-app purchase
    capability](https://developer.apple.com/documentation/xcode/adding-capabilities-to-your-app)
    to your app in Xcode, making sure that the bundle identifier and
    product identifiers in Xcode match the identifiers for your app and
    in-app purchases in App Store Connect.

5.  **Test your in-app purchases**

    Apple provides a testing environment, called sandbox, which allows
    you to [test in-app
    purchases](https://developer.apple.com/documentation/storekit/in-app_purchase/testing_at_all_stages_of_development_with_xcode_and_the_sandbox)
    without incurring charges using [test
    accounts](https://developer.apple.com/help/app-store-connect/test-in-app-purchases/create-a-sandbox-apple-account).
    Test each part of your code to verify that you've implemented it
    correctly by using your app to make in-app purchases.

    You can further test your app and in-app purchases using
    [TestFlight](https://developer.apple.com/help/app-store-connect/test-a-beta-version/testflight-overview),
    or in
    [Xcode](https://developer.apple.com/documentation/xcode/setting-up-storekit-testing-in-xcode).

6.  **Use App Store Server Notifications**

    [App Store Server
    Notifications](https://developer.apple.com/documentation/appstoreservernotifications)
    provide near real-time updates about transaction status and key
    events related to in-app purchases, such as a refund or a change in
    subscription status or Family Sharing access. To leverage these
    notifications, you'll need to [enter URLs for your production and
    sandbox server
    environments](https://developer.apple.com/help/app-store-connect/configure-in-app-purchase-settings/enter-server-urls-for-app-store-server-notifications)
    in App Store Connect.

7.  **Submit your in-app purchases for review**

    Before you publish your in-app purchase on the App Store it must be
    [submitted for
    review](https://developer.apple.com/help/app-store-connect/manage-submissions-to-app-review/submit-for-review).
    If you're submitting your first in-app purchase, you must submit it
    with a new version of your app. Make sure you aren\'t missing any
    [required
    information](https://developer.apple.com/help/app-store-connect/reference/required-localizable-and-editable-properties)
    before submitting. Monitor [in-app purchase
    statuses](https://developer.apple.com/help/app-store-connect/reference/in-app-purchase-statuses)
    to understand if your in-app purchase is available or if it needs
    your attention.

#### Source: [https://developer.apple.com/help/app-store-connect/configure-in-app-purchase-settings/overview-for-configuring-in-app-purchases/](https://developer.apple.com/help/app-store-connect/configure-in-app-purchase-settings/overview-for-configuring-in-app-purchases/){card-appearance="inline"}
