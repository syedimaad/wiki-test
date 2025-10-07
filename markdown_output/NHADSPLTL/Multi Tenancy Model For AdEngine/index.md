## Objective

Since we're growing and creating family of verse apps, How to support
multi tenancy model for different apps.

## What is multi tenancy model ?

Multi-tenancy is an architecture in which a single instance of a
software application serves multiple customers/apps. We're creating
family of verse apps, So it'll be single architecture to support all
apps.

## How to enable new apps into multi tenancy model

Below are steps to enable multi tenancy for particular app.

### Step - 1 **Define App-Id**

Every app must needs unique app-id.\
for example, please find below information about app-Id.

  ----------- --------------
  App Name    App-Id
  Dailyhunt   **DH_APP**
  Josh        **JOSH_APP**
  DH-Mena     **DH_MENA**
  YO App      **YO_APP**
  ----------- --------------

### Step - 2 **Whitelist App-Id**

Once app-Id created, we need to whitelist this app-id to certain
places.\
Please find below place to whitelist app-id,

src/Helpers/CommonHelper.php =\> getAppIdFromHeader()
src/Helpers/CommonHelper.php =\> getPartnerAppIdFromQueryString()
public/index.php =\> swtich case statement to pick correct settings file

### Step - 3 **Create a Config File**

Once App-Id whitelisted, we need to create config file under `src`
folder by following naming convention.

App-Id_settings.php

For example,

  ----------- ---------------------------
  App Name    Config File Name
  Dailyhunt   **settings.php**
  Josh        **JOSH_APP_settings.php**
  DH-Mena     **DH_MENA_settings.php**
  YO App      **YO_APP_settings.php**
  ----------- ---------------------------

### Step - 4 **Create a .env File**

Once App-Id whitelisted, we need to create env file under
`ROOT_DOCUMENT` by following naming convention.

.env_App-Id.php

For example,

  ----------- -----------------------
  App Name    Config File Name
  Dailyhunt   **.env.php**
  Josh        **.env_JOSH_APP.php**
  DH-Mena     **.env_DH_MENA.php**
  YO App      **.env_YO_APP.php**
  ----------- -----------------------

### Step - 5 **Setup a Handshake Path**

For handshake setup, We need to follow below steps

- Open handshake google sheet. We've different handshake google sheet
  based on env.

- Create a new tab called `App-Id` under each env.

For example, Josh called \*\*JOSH_APP\*\*.

- Add rules or we can copy from existing tabs.

- Once handshake file created, we need to add below lines into
  `src/Helpers/scripts/handShake/conf.yml`.

App-Id_env: spreadsheet_id: \<spread sheet id for particular env\>
range_names: { \'DH_MENA\': { \'name\': \'items\', \'ref\': \'SubArray\'
} } For example, DH_MENA_prod: spreadsheet_id:
1OwIydwQjViW0J0ybgRcxz4wFzinRBMdLMa2FFAQjlAs range_names:
{\'DH_MENA\':{\'name\':\'items\', \'ref\':\'SubArray\'}} DH_MENA_stage:
spreadsheet_id: 1WzLR62leshdPau4iCOQI5qWBNCciduK3GFkOD50MICk
range_names: { \'DH_MENA\': { \'name\': \'items\', \'ref\': \'SubArray\'
} } DH_MENA_qa: spreadsheet_id:
1WzLR62leshdPau4iCOQI5qWBNCciduK3GFkOD50MICk range_names: { \'DH_MENA\':
{ \'name\': \'items\', \'ref\': \'SubArray\' } }

- After we need to add below line into
  `/usr/local/bin/python3.7 globalConf.py DH_MENA`.

/usr/local/bin/python3.7 globalConf.py App-Id For example,
/usr/local/bin/python3.7 globalConf.py DH_MENA

- For stage and env we need to add below line into
  `public/updateHandShakeReponseStage.php's shell_exec function`.

/bin/python3 globalConf.py App-Id For example, /bin/python3
globalConf.py DH_MENA

**Note:** `Make sure shell_exec input command is correct`.

### Step - 6 **Aggressive Cacher Path**

Since aggressive cacher is based on `settings.php` file so we need to
add `App-Id` into `partnerApps` array and it's zones into
`adPlacements`array.

### Step - 7 **Sanitising Input**

If particular `App-Id` has new incoming params, we need to whitelist
those as well into `src/Services/AdRequest/SanitizeInput.php`.

### Step - 8 **AdHandler & Ad Entity**

If particular `App-Id` needs new ad handlers then we need to create
parent ad handler under `src/Lib/Classes` and it's child ad handler
under `src/Lib/AdHandler/<Add-Id>/` and write code to assign this new ad
handler to it's type into `src/Lib/Entities/Ad.php's getHandler()`.

### Step - 8 **Feature Mask Support**

If particular `Add-Id` support feature mask then we need to add it's
entry into `src/Content/featureMask.json`.\
For example,

{ \....., \"DH_MENA\": { \"android\": { \"1.0\": { \"FeatureMask1\":
\<Any Int\> } }, \"ios\": { \"1.0\": { \"FeatureMask1\": \<Any Int\> } }
} }

Once we added entry into `featureMask.json`, we need to add its
constants into `src/Helpers/FeatureMaskHelper.php`. Once added, we can
use `FeatureMaskHelper::isFeatureSupported(..)`

#### **Notes:**

- We need to search `DeliveryHelper::isDHAppVersion()` and make sure all
  places by default supported new app.l

- For feature mask, we need to add
  `FeatureMaskHelper::isFeatureSupported(..)` to support for new app.

- If particular appId support ad load, then we need to inform DD to
  whitelist that appId for ad load.

- If particular appId support content context, then we need to inform DD
  to whitelist that appId for content context and inform newsBE to pass
  appId into ACRE.
