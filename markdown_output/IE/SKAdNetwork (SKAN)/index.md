1.  SKAN helps validate advertisement-driven app installations

2.  The ad network API helps advertisers measure the success of ad
    campaigns while maintaining user privacy.

3.  [https://developer.apple.com/documentation/storekit/skadnetwork/](https://developer.apple.com/documentation/storekit/skadnetwork/){card-appearance="inline"}

## Components

- Ad Network (Google, FB, DH): that sign ads and receive
  install-validation postbacks after ads result in conversions

  - DH will need to be registered as an ad network

- Source App - display ads from the ad networks, or websites that
  display the ads in Safari

- Advertised Apps - that update conversion values as people engage with
  the app

  - Advertised apps need to implement postback

## Dailyhunt's use-cases

### 1. As an app platform

- **As a source app:**

  - Dailyhunt is the source app for Direct and SDK Ads

  - SDKs like Google have their guidelines on how to enable attribution
    for app installs via GMA -

    - [https://support.google.com/google-ads/answer/14892597?hl=en](https://support.google.com/google-ads/answer/14892597?hl=en){card-appearance="inline"}

    - [https://developers.google.com/admob/ios/privacy/strategies](https://developers.google.com/admob/ios/privacy/strategies){card-appearance="inline"}

  - For Direct ads\' attribution, Dailyhunt needs to be registered as an
    Ad Network with Apple. More details
    [here](https://evp.atlassian.net/wiki/spaces/IE/pages/990183429/SKAdNetwork#2.-As-an-ad-network).

  - Refer [[Configuring a source
    app]{.underline}](https://developer.apple.com/documentation/storekit/configuring-a-source-app)
    for details and steps on how to configure DH as a source app with
    SKAN

  - **Support for Third party SDKs (by adding network identifiers in
    info.plist)**

    - Google:
      <https://developers.google.com/admob/ios/privacy/strategies#skadnetwork>

    - Meta (FBAdsSdk):
      [https://developers.facebook.com/docs/setting-up/platform-setup/ios/SKAdNetwork](https://developers.facebook.com/docs/setting-up/platform-setup/ios/SKAdNetwork){card-appearance="inline"}

- **As an advertised App:**

  - This path will be useful to attribute DH app install from other
    source apps.

  - Refer [[Configuring an advertised
    app]{.underline}](https://developer.apple.com/documentation/storekit/configuring-an-advertised-app)
    for steps on how to configure DH as an advertised app

### 2. As an ad network

- To be able to leverage SKAdNetwork's postback validation of direct
  Ads, Dailyhunt needs to register as an Ad Network with Apple.

- Guide for the same:
  [https://developer.apple.com/documentation/storekit/registering-an-ad-network](https://developer.apple.com/documentation/storekit/registering-an-ad-network){card-appearance="inline"}

> **Important**\
> Lowercase the ad network ID string; otherwise, the system doesn't
> recognize it as valid.

## Future: Ad Attribution Kit (AAK)

- AdAttributionKit is the successor to SKAdNetwork introduced in iOS 17

- [https://developer.apple.com/documentation/adattributionkit](https://developer.apple.com/documentation/adattributionkit){card-appearance="inline"}

- Ad Attribution kit is not yet supported by Ad Networks like Google,
  Meta, and Amazon. Hence, advisable to get started with SKAN now and
  migrate to AAK later when relevant third party networks start
  supporting it as well.
