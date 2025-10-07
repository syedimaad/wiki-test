- **Platform:** Firebase

**Status**: This will deprecate on Aug 25th, 2025

**Link:**
[https://firebase.google.com/docs/dynamic-links](https://firebase.google.com/docs/dynamic-links){card-appearance="inline"}

**Usage:** When a user opens one of your Dynamic Links, if your app
isn\'t yet installed, the user is sent to the Play Store or App Store to
install your app (unless you specify otherwise), and your app opens. You
can then retrieve the link that was passed to your app and handle the
deep link as appropriate for your app.

**Outcome:** Suggestion is not to use, since this is going to be
deprecated.

- **Platform:** Branch iO

**Link:**
[https://help.branch.io/docs/nativelink-deferred-deep-linking?highlight=deferred%20deep](https://help.branch.io/docs/nativelink-deferred-deep-linking?highlight=deferred%20deep){card-appearance="inline"}

**Usage:** User clicks a Branch Link.

Once they click on the Link/CTA, the URL location is copied to the
clipboard.

The user is then brought to the App Store to download the app.

After installation, NativeLink™ will check the clipboard for the URL and
process it 

for deep linking. The user is then routed to their final destination in
the app.

**Outcome:** Suggestion is not to use, since this needs pasteboard
permission,  and pasteboard permission is mandatory from iOS 14 onwards.

- **Platform**: Adjust

**Link:**
[https://dev.adjust.com/en/sdk/ios/features/deep-links/deferred/](https://dev.adjust.com/en/sdk/ios/features/deep-links/deferred/){card-appearance="inline"}

**Usage:** The user clicks on an Adjust deep link.

           Adjust's servers redirect the user to the App Store.

The user installs your app and opens it.

           Adjust's servers perform attribution and send the deep link
to the Adjust SDK.

The app retrieves the deep link from the Adjust SDK and handles the deep
link.

**Outcome:** Uses pasteboard

- **Platform:** Safari cookies

**Link:**
[https://innovationm.co/deferred-deep-linking-in-ios-with-universal-link/](https://innovationm.co/deferred-deep-linking-in-ios-with-universal-link/){card-appearance="inline"}

**Usage:** To share the data between Safari and Mobile App we will use 

SFSafariViewController. It supports sharing of web page data like
cookies 

between applications. So what we are gonna do is to store the url in the
cookie 

when user open the url in web browser and he/she launches the
application we 

will open a simple page which will check the cookie and if cookie is
present it 

will launch our application by using URL Scheme so that we can make a 

Decision.

**Outcome:** Cookie sharing can be disabled from setting from iOS 11, so
not suggested to use it.

- **Platform:** Appsflyer

**Link:**
[https://dev.appsflyer.com/hc/docs/dl_ios_ocds_ddl](https://dev.appsflyer.com/hc/docs/dl_ios_ocds_ddl){card-appearance="inline"}

**Usage:** Extended deferred deep linking allows deep linking for new
users with 

attributes that we set in consol\

**Link**:
[https://dev.appsflyer.com/hc/docs/dl_ios_private_relay](https://dev.appsflyer.com/hc/docs/dl_ios_private_relay){card-appearance="inline"}

**Usage:** With the launch of iOS 15, Apple provides iCloud+ users with
a feature 

called Private Relay, which gives them the option to encrypt their
web-browsing 

traffic and hide their exact location, IP address, and the contents of
their browsing 

traffic. If users opt-in to Private Relay, this could interfere with
attribution and 

deferred deep linking. Meaning, once a new user without the app goes to
the App 

Store, and installs and launches the app, Private Relay could prevent
them from 

being sent to a specific page in the app.

There are 2 types of flow

- \[Recommended\] App Clip-based solution: Create an App Clip that gives
  you user attribution data, and directs users to a customized App Clip
  experience similar to the one you want DDL to achieve. The app clip
  can also include a flow to direct users from your App Clip to your
  full app.

- Clipboard-based solution: Create a web landing page that copies the
  deferred deep linking data from the URL and correctly redirects the
  user to the app. Note: This solution does not help with attribution.

Script to pass the custom data
<https://appsflyersdk.github.io/appsflyer-onelink-smart-script/examples/onelink_custom_parameters.html?inmedia=email&dp_dest=apples&pageid=2g4f&productid=shirt12&partner=bigagency>

**Outcome:** We can use DDL to install the app and navigate to a
specific page with help of deeplink value, also we can use a custom
param to send the auth token and carry forward the login status of the
web(which comes with cost of 7\$ / conversion), For this script to be
written from webpage to pass the token. From iOS 15 onwards cloud+ user
has provision to privacy relay, which restricts the web page details
sharing due encryption. Recommended to use APP clip.    
