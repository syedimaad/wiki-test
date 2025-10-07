- **Splitting chunk2 into a List of chunks**

  - [https://docs.google.com/document/d/1T4S-kn1govJ\--xCVim3BWXKH5A7NEUMX4AmVVaaLwrA/edit](https://docs.google.com/document/d/1T4S-kn1govJ--xCVim3BWXKH5A7NEUMX4AmVVaaLwrA/edit){card-appearance="inline"}

  - [https://docs.google.com/spreadsheets/d/1lZe97cKM9p8KkcUaREflSv1T2PWSaD3-c07diPw74ss/edit#gid=818907836](https://docs.google.com/spreadsheets/d/1lZe97cKM9p8KkcUaREflSv1T2PWSaD3-c07diPw74ss/edit#gid=818907836){card-appearance="inline"}

- **Supplement Ads Zone Enhancement**

  - Story Page and Supplement Ads Revamp

  - Multi story detail zones - Story Page and Supplement Ads Revamp

- **Impression eCPM pingback for Google Sdk**

  - adPaid Beacon comes in SDK Ad response\
    \"adPaidBeaconUrls\": { \"internal\":
    \[\"https://[money.dailyhunt.in](http://money.dailyhunt.in)/beaconEvents?eventType=AD_PAID&adPlacement=storypage&uniqueId=9ddf4347baa893918b53c8d6900305bb\"\]}

  - This beacon fires only when SDK Ad impression has fired and it will
    not fire in case of a No Fill Case

- **Customizable UI for ISV (learn more, Skippable AD)**

  - Learn More and Skip Ad Text both are configurable in DD

  - Background and Text color of both Learn More and Skip Ad Text is
    configurable from AdsBE

  - Both Learn More and Skip AD Text are Case sensitive i.e. they should
    come as it is configured in DD

- **Disable sticky ads fix (ae_v2 in the stream API) - BugFix**

  - Stream API Changes -

    - Replacing the "ae" field with "ae_v2":- This field is intended to
      be used to control sticky ads (enable/disable them). "ae" was
      added in the last release but some issues were observed when "ae"
      was false, hence to avoid using this field new clients will start
      using "ae_v2".

  - Meta API Changes -

    - \"adConfig\": { \"adEnabled\": true/false, //To control whether ad
      request should be triggered for this sticky \"adBaseUrl\":
      \"\<sticky ad base url\>\", //url to be used for fetching ad
      \"refreshIntervalMs\": 20000, //Minimum interval between 2 sticky
      ad request in milliseconds }

- **OM SDK verification**

  - The sanity of OMSDK beacons on the new native ticker-added zones

- **YT Videos Monetization**

  - Support added for Instream Ads in YouTube videos also
