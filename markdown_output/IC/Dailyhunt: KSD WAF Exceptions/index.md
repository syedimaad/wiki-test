+-------------------+------------------+-------------------------------------------+-------------------------------------------+
| **Configuration** | **Policy**       | **Attack Groups**                         | **Exceptions**                            |
+-------------------+------------------+-------------------------------------------+-------------------------------------------+
| **API-NEWS**      | **API-NEWS**     | Command Injection                         | - **Cookies:** nhLocationInfoV1,          |
|                   |                  |                                           |   nhConnectionInfoV1, nhClientInfoV1      |
|                   |                  |                                           |                                           |
|                   |                  |                                           | - **URL-encoded body and query string     |
|                   |                  |                                           |   parameters**: params, amp;id            |
|                   |                  |                                           |                                           |
|                   |                  |                                           | - **Path:**                               |
|                   |                  |                                           |   /api/v2/search/posts/autocomplete,      |
|                   |                  |                                           |   /api/v2/post/handshake,                 |
|                   |                  |                                           |   /api/v2/registerdevice,                 |
|                   |                  |                                           |   /api/v2/posts/related/feed/n466499454   |
|                   |                  |                                           |                                           |
|                   |                  |                                           | - **JSON parameter**: androidId,          |
|                   |                  |                                           |   clientInfo.gaid, clientInfo.androidId,  |
|                   |                  |                                           |   uniqueIdentifier.buildId,               |
|                   |                  |                                           |   clientInfo.udid, connectionInfo.cellid, |
|                   |                  |                                           |   referrer, connectionInfo.apnName,       |
|                   |                  |                                           |   locationInfo.lat,                       |
|                   |                  |                                           |   uniqueIdentifier.androidId,             |
|                   |                  |                                           |   uniqueIdentifier.googleAdId             |
|                   |                  +-------------------------------------------+-------------------------------------------+
|                   |                  | Cross Site Scripting                      | - **Path:** /api/v2/post/create/repost/\* |
|                   |                  +-------------------------------------------+-------------------------------------------+
|                   |                  | SQL Injection                             | - **Cookies:** nhLocationInfoV1,          |
|                   |                  |                                           |   nhConnectionInfoV1, nhClientInfoV1      |
|                   |                  |                                           |                                           |
|                   |                  |                                           | <!-- -->                                  |
|                   |                  |                                           |                                           |
|                   |                  |                                           | - **URL-encoded body and query string     |
|                   |                  |                                           |   parameters**: params, amp;id            |
|                   |                  |                                           |                                           |
|                   |                  |                                           | <!-- -->                                  |
|                   |                  |                                           |                                           |
|                   |                  |                                           | - **Paths:**                              |
|                   |                  |                                           |   /api/v100/sendInstrumentation,          |
|                   |                  |                                           |   /api/v2/post/create/repost/\*           |
|                   |                  |                                           |                                           |
|                   |                  |                                           | <!-- -->                                  |
|                   |                  |                                           |                                           |
|                   |                  |                                           | - **JSON parameter**:                     |
|                   |                  |                                           |   connectionInfo.cellid, referrer,        |
|                   |                  |                                           |   connectionInfo.apnName                  |
|                   |                  +-------------------------------------------+-------------------------------------------+
|                   |                  | Web Attack Tool                           | - **URL-encoded body and query string     |
|                   |                  |                                           |   parameters:** cellid                    |
+-------------------+------------------+-------------------------------------------+-------------------------------------------+
| **Eterno Infotech | **API**          | Command Injection                         | - **Cookies:** nhLocationInfoV1,          |
| KSD**             |                  |                                           |   nhConnectionInfoV1, nhClientInfoV1      |
|                   |                  |                                           |                                           |
|                   |                  |                                           | <!-- -->                                  |
|                   |                  |                                           |                                           |
|                   |                  |                                           | - **URL-encoded body and query string     |
|                   |                  |                                           |   parameters:** params                    |
|                   |                  |                                           |                                           |
|                   |                  |                                           | <!-- -->                                  |
|                   |                  |                                           |                                           |
|                   |                  |                                           | - **JSON parameter:** androidId           |
|                   |                  +-------------------------------------------+-------------------------------------------+
|                   |                  | SQL Injection                             | - **Cookies:** nhLocationInfoV1,          |
|                   |                  |                                           |   nhConnectionInfoV1, nhClientInfoV1      |
|                   |                  |                                           |                                           |
|                   |                  |                                           | <!-- -->                                  |
|                   |                  |                                           |                                           |
|                   |                  |                                           | - **URL-encoded body and query string     |
|                   |                  |                                           |   parameters:** params                    |
|                   |                  +-------------------------------------------+-------------------------------------------+
|                   |                  | Web Attack Tool                           | - **URL-encoded body and query string     |
|                   |                  |                                           |   parameters:** cellid                    |
|                   +------------------+-------------------------------------------+-------------------------------------------+
|                   | **Web**          | Command Injection                         | - **Cookies:** nhLocationInfoV1,          |
|                   |                  |                                           |   nhConnectionInfoV1, nhClientInfoV1      |
|                   |                  +-------------------------------------------+-------------------------------------------+
|                   |                  | SQL Injection                             | - **Cookies:** nhLocationInfoV1,          |
|                   |                  |                                           |   nhConnectionInfoV1, nhClientInfoV1      |
+-------------------+------------------+-------------------------------------------+-------------------------------------------+
| **Eterno          | **APIs**         | Command Injection                         | - **Cookies:** nhConnectionInfoV1,        |
| Onboardings**     |                  |                                           |   nhClientInfoV1                          |
|                   |                  |                                           |                                           |
|                   |                  |                                           | - **JSON parameter:** androidId           |
|                   +------------------+-------------------------------------------+-------------------------------------------+
|                   | **Non-Prod**     | **[None]{style="color: rgb(191,38,0);"}** | **[None]{style="color: rgb(191,38,0);"}** |
+-------------------+------------------+-------------------------------------------+-------------------------------------------+
| **New Eterno      | **Ads and        | Command Injection                         | - **Cookies:** nhLocationInfoV1,          |
| MSC**             | Webstories**     |                                           |   nhConnectionInfoV1, nhClientInfoV1      |
|                   |                  |                                           |                                           |
|                   |                  |                                           | - **URL-encoded body and query string     |
|                   |                  |                                           |   parameters:** gaid, udid, cellid, lat,  |
|                   |                  |                                           |   long, feedLong, feedLat,                |
|                   |                  |                                           |   feedConstituencyId, feedStateId,        |
|                   |                  |                                           |   feedDistrictId, adRequestParams         |
|                   |                  +-------------------------------------------+-------------------------------------------+
|                   |                  | Cross Site Scripting                      | - **Cookies:** nhClientInfoV1             |
|                   |                  +-------------------------------------------+-------------------------------------------+
|                   |                  | SQL Injection                             | - **Cookies:** nhLocationInfoV1,          |
|                   |                  |                                           |   nhConnectionInfoV1, nhClientInfoV1      |
|                   |                  |                                           |                                           |
|                   |                  |                                           | - **URL-encoded body and query string     |
|                   |                  |                                           |   parameters:** udid, cellid, lat, long   |
|                   |                  +-------------------------------------------+-------------------------------------------+
|                   |                  | Web Attack Tool                           | - **Cookies:** commonDH                   |
|                   |                  |                                           |                                           |
|                   |                  |                                           | - **URL-encoded body and query string     |
|                   |                  |                                           |   parameters:** cellid                    |
|                   +------------------+-------------------------------------------+-------------------------------------------+
|                   | **Poll-UGC-WAP** | Command Injection                         | - **Cookies:** nhLocationInfoV1,          |
|                   |                  |                                           |   nhConnectionInfoV1, nhClientInfoV1      |
|                   |                  |                                           |                                           |
|                   |                  |                                           | - **URL-encoded body and query string     |
|                   |                  |                                           |   parameters:** udid, cellid, lat         |
|                   |                  +-------------------------------------------+-------------------------------------------+
|                   |                  | SQL Injection                             | - **Cookies:** nhLocationInfoV1,          |
|                   |                  |                                           |   nhConnectionInfoV1, nhClientInfoV1      |
|                   |                  |                                           |                                           |
|                   |                  |                                           | - **URL-encoded body and query string     |
|                   |                  |                                           |   parameters:** udid, cellid, lat         |
+-------------------+------------------+-------------------------------------------+-------------------------------------------+

> **Refer below hostnames based on associated configuration and policy
> name.**

+-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
| **Configuration**     | **Policy**            | **Hostnames**                                                                                 |
+-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
| **API-NEWS**          | **API-NEWS**          | - [api-news.dailyhunt.in](http://api-news.dailyhunt.in)                                       |
+-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
| **Eterno Infotech     | **API**               | - [api-dailytv.dailyhunt.in](http://api-dailytv.dailyhunt.in)                                 |
| KSD**                 |                       |                                                                                               |
|                       |                       | - [api.newshuntads.com](http://api.newshuntads.com)                                           |
|                       +-----------------------+-----------------------------------------------------------------------------------------------+
|                       | **Web**               | - [contest.dailyhunt.in](http://contest.dailyhunt.in)                                         |
|                       |                       |                                                                                               |
|                       |                       | - [data.dailyhunt.in](http://data.dailyhunt.in)                                               |
|                       |                       |                                                                                               |
|                       |                       | - [feed.dailyhunt.in](http://feed.dailyhunt.in)                                               |
|                       |                       |                                                                                               |
|                       |                       | - [account.dailyhunt.in](http://account.dailyhunt.in)                                         |
|                       |                       |                                                                                               |
|                       |                       | - [samsung.dailyhunt.in](http://samsung.dailyhunt.in)                                         |
|                       |                       |                                                                                               |
|                       |                       | - [stage-api-news.dailyhunt.in](http://stage-api-news.dailyhunt.in)                           |
+-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
| **Eterno              | **APIs**              | - [internal-zone-proxy-service.dailyhunt.in](http://internal-zone-proxy-service.dailyhunt.in) |
| Onboardings**         |                       |                                                                                               |
|                       |                       | - [lucretia.dailyhunt.in](http://lucretia.dailyhunt.in)                                       |
|                       |                       |                                                                                               |
|                       |                       | - [election-service.dailyhunt.in](http://election-service.dailyhunt.in)                       |
|                       |                       |                                                                                               |
|                       |                       | - [dailyhunt.co](http://dailyhunt.co)                                                         |
|                       |                       |                                                                                               |
|                       |                       | - [gadget-proxy-service.dailyhunt.in](http://gadget-proxy-service.dailyhunt.in)               |
|                       |                       |                                                                                               |
|                       |                       | - [api-books.dailyhunt.in](http://api-books.dailyhunt.in)                                     |
|                       |                       |                                                                                               |
|                       |                       | - [library.dailyhunt.in](http://library.dailyhunt.in)                                         |
|                       |                       |                                                                                               |
|                       |                       | - [tecno.dailyhunt.in](http://tecno.dailyhunt.in)                                             |
|                       |                       |                                                                                               |
|                       |                       | - [pwa.dailyhunt.in](http://pwa.dailyhunt.in)                                                 |
|                       |                       |                                                                                               |
|                       |                       | - [central.dailyhunt.in](http://central.dailyhunt.in)                                         |
|                       |                       |                                                                                               |
|                       |                       | - [indus.dailyhunt.in](http://indus.dailyhunt.in)                                             |
|                       |                       |                                                                                               |
|                       |                       | - [eg-money.dailyhunt.in](http://eg-money.dailyhunt.in)                                       |
|                       |                       |                                                                                               |
|                       |                       | - [adspecs.dailyhunt.in](http://adspecs.dailyhunt.in)                                         |
|                       |                       |                                                                                               |
|                       |                       | - [daecdn1.dailyhunt.in](http://daecdn1.dailyhunt.in)                                         |
|                       |                       |                                                                                               |
|                       |                       | - [acq-news.dailyhunt.in](http://acq-news.dailyhunt.in)                                       |
|                       |                       |                                                                                               |
|                       |                       | - [img-books.dailyhunt.in](http://img-books.dailyhunt.in)                                     |
|                       |                       |                                                                                               |
|                       |                       | - [prod-cricket-service-c50.dailyhunt.in](http://prod-cricket-service-c50.dailyhunt.in)       |
|                       |                       |                                                                                               |
|                       |                       | - [test.newshunt.com](http://test.newshunt.com)                                               |
|                       |                       |                                                                                               |
|                       |                       | - [www.dailyhuntapp.in](http://www.dailyhuntapp.in)                                           |
|                       |                       |                                                                                               |
|                       |                       | - [adengine.dailyhunt.in](http://adengine.dailyhunt.in)                                       |
|                       |                       |                                                                                               |
|                       |                       | - [www.dailyhunt.com](http://www.dailyhunt.com)                                               |
|                       |                       |                                                                                               |
|                       |                       | - [direct1.dailyhunt.in](http://direct1.dailyhunt.in)                                         |
|                       |                       |                                                                                               |
|                       |                       | - [central.verseinnovation.com](http://central.verseinnovation.com)                           |
|                       |                       |                                                                                               |
|                       |                       | - [static-dhtv.dailyhunt.in](http://static-dhtv.dailyhunt.in)                                 |
|                       |                       |                                                                                               |
|                       |                       | - [web.dailyhunt.in](http://web.dailyhunt.in)                                                 |
|                       |                       |                                                                                               |
|                       |                       | - [dailyhunt.com](http://dailyhunt.com)                                                       |
|                       |                       |                                                                                               |
|                       |                       | - [www.dailyhunt.co](http://www.dailyhunt.co)                                                 |
|                       |                       |                                                                                               |
|                       |                       | - [www.dailyhunt.io](http://www.dailyhunt.io)                                                 |
|                       |                       |                                                                                               |
|                       |                       | - [www.dailyhunt.in](http://www.dailyhunt.in)                                                 |
|                       |                       |                                                                                               |
|                       |                       | - [www.dailyhunt.me](http://www.dailyhunt.me)                                                 |
|                       |                       |                                                                                               |
|                       |                       | - [dailyhunt.in](http://dailyhunt.in)                                                         |
|                       |                       |                                                                                               |
|                       |                       | - [vivo.dailyhunt.in](http://vivo.dailyhunt.in)                                               |
|                       |                       |                                                                                               |
|                       |                       | - [tcdn.newshunt.com](http://tcdn.newshunt.com)                                               |
|                       |                       |                                                                                               |
|                       |                       | - [xiaomi.dailyhunt.in](http://xiaomi.dailyhunt.in)                                           |
|                       |                       |                                                                                               |
|                       |                       | - [assets-money.dailyhunt.in](http://assets-money.dailyhunt.in)                               |
|                       |                       |                                                                                               |
|                       |                       | - [election-proxy-service.dailyhunt.in](http://election-proxy-service.dailyhunt.in)           |
|                       |                       |                                                                                               |
|                       |                       | - [prod-pullnotification.dailyhunt.in](http://prod-pullnotification.dailyhunt.in)             |
|                       |                       |                                                                                               |
|                       |                       | - [daecdn2.dailyhunt.in](http://daecdn2.dailyhunt.in)                                         |
|                       |                       |                                                                                               |
|                       |                       | - [money.dailyhunt.in](http://money.dailyhunt.in)                                             |
|                       |                       |                                                                                               |
|                       |                       | - [origin-ro-api-dhtv.dailyhunt.in](http://origin-ro-api-dhtv.dailyhunt.in)                   |
|                       |                       |                                                                                               |
|                       |                       | - [ads.newshunt.in](http://ads.newshunt.in)                                                   |
|                       |                       |                                                                                               |
|                       |                       | - [deals.newshuntads.com](http://deals.newshuntads.com)                                       |
|                       |                       |                                                                                               |
|                       |                       | - [h2i.dailyhunt.in](http://h2i.dailyhunt.in)                                                 |
|                       |                       |                                                                                               |
|                       |                       | - [itel.dailyhunt.in](http://itel.dailyhunt.in)                                               |
|                       |                       |                                                                                               |
|                       |                       | - [www.dailyhuntapp.com](http://www.dailyhuntapp.com)                                         |
|                       |                       |                                                                                               |
|                       |                       | - [cdn.publicvibe.com](http://cdn.publicvibe.com)                                             |
|                       |                       |                                                                                               |
|                       |                       | - [campaign-edge.dailyhunt.in](http://campaign-edge.dailyhunt.in)                             |
|                       |                       |                                                                                               |
|                       |                       | - [perf-news.dailyhunt.in](http://perf-news.dailyhunt.in)                                     |
|                       |                       |                                                                                               |
|                       |                       | - [nearme.dailyhunt.in](http://nearme.dailyhunt.in)                                           |
|                       |                       |                                                                                               |
|                       |                       | - [order.dailyhunt.in](http://order.dailyhunt.in)                                             |
|                       |                       |                                                                                               |
|                       |                       | - [pre.dailyhunt.in](http://pre.dailyhunt.in)                                                 |
|                       |                       |                                                                                               |
|                       |                       | - [social.dailyhunt.in](http://social.dailyhunt.in)                                           |
|                       |                       |                                                                                               |
|                       |                       | - [acdn.newshunt.net.in](http://acdn.newshunt.net.in)                                         |
|                       |                       |                                                                                               |
|                       |                       | - [central.eternoinfotech.com](http://central.eternoinfotech.com)                             |
|                       |                       |                                                                                               |
|                       |                       | - [pwa-api.dailyhunt.in](http://pwa-api.dailyhunt.in)                                         |
|                       |                       |                                                                                               |
|                       |                       | - [infinix.dailyhunt.in](http://infinix.dailyhunt.in)                                         |
|                       |                       |                                                                                               |
|                       |                       | - [developer.dailyhunt.in](http://developer.dailyhunt.in)                                     |
|                       +-----------------------+-----------------------------------------------------------------------------------------------+
|                       | **Non-Prod**          | - [qa-data.dailyhunt.in](http://qa-data.dailyhunt.in)                                         |
|                       |                       |                                                                                               |
|                       |                       | - [qa-pullnotification.dailyhunt.in](http://qa-pullnotification.dailyhunt.in)                 |
|                       |                       |                                                                                               |
|                       |                       | - [qa-profile.dailyhunt.in](http://qa-profile.dailyhunt.in)                                   |
|                       |                       |                                                                                               |
|                       |                       | - [bg.qa-money.newshunt.com](http://bg.qa-money.newshunt.com)                                 |
|                       |                       |                                                                                               |
|                       |                       | - [qa-cricket-service-c50.dailyhunt.in](http://qa-cricket-service-c50.dailyhunt.in)           |
|                       |                       |                                                                                               |
|                       |                       | - [qa-dcads-meta.dailyhunt.in](http://qa-dcads-meta.dailyhunt.in)                             |
|                       |                       |                                                                                               |
|                       |                       | - [stage-dhtv.dailyhunt.in](http://stage-dhtv.dailyhunt.in)                                   |
|                       |                       |                                                                                               |
|                       |                       | - [qa-social.newshunt.com](http://qa-social.newshunt.com)                                     |
|                       |                       |                                                                                               |
|                       |                       | - [stage-account.dailyhunt.in](http://stage-account.dailyhunt.in)                             |
|                       |                       |                                                                                               |
|                       |                       | - [stage-pwabe.dailyhunt.in](http://stage-pwabe.dailyhunt.in)                                 |
|                       |                       |                                                                                               |
|                       |                       | - [qa-news.newshunt.com](http://qa-news.newshunt.com)                                         |
|                       |                       |                                                                                               |
|                       |                       | - [qa-poll-service.dailyhunt.in](http://qa-poll-service.dailyhunt.in)                         |
|                       |                       |                                                                                               |
|                       |                       | - [stage-feed.dailyhunt.in](http://stage-feed.dailyhunt.in)                                   |
|                       |                       |                                                                                               |
|                       |                       | - [eg.qa-money.newshunt.com](http://eg.qa-money.newshunt.com)                                 |
|                       |                       |                                                                                               |
|                       |                       | - [pwaqa.dailyhunt.in](http://pwaqa.dailyhunt.in)                                             |
|                       |                       |                                                                                               |
|                       |                       | - [stage-cdn.publicvibe.com](http://stage-cdn.publicvibe.com)                                 |
|                       |                       |                                                                                               |
|                       |                       | - [eg-stage-money.dailyhunt.in](http://eg-stage-money.dailyhunt.in)                           |
|                       |                       |                                                                                               |
|                       |                       | - [eg-qa-money.dailyhunt.in](http://eg-qa-money.dailyhunt.in)                                 |
|                       |                       |                                                                                               |
|                       |                       | - [qa-be-load-m.dailyhunt.in](http://qa-be-load-m.dailyhunt.in)                               |
|                       |                       |                                                                                               |
|                       |                       | - [stage-order.dailyhunt.in](http://stage-order.dailyhunt.in)                                 |
|                       |                       |                                                                                               |
|                       |                       | - [dhshare-stage-api-news.dailyhunt.in](http://dhshare-stage-api-news.dailyhunt.in)           |
|                       |                       |                                                                                               |
|                       |                       | - [webqa.dailyhunt.in](http://webqa.dailyhunt.in)                                             |
|                       |                       |                                                                                               |
|                       |                       | - [stage-gadget-proxy-service.dailyhunt.in](http://stage-gadget-proxy-service.dailyhunt.in)   |
|                       |                       |                                                                                               |
|                       |                       | - [qa-fe-load-m.dailyhunt.in](http://qa-fe-load-m.dailyhunt.in)                               |
|                       |                       |                                                                                               |
|                       |                       | - [stage-cricket-service-c50.dailyhunt.in](http://stage-cricket-service-c50.dailyhunt.in)     |
|                       |                       |                                                                                               |
|                       |                       | - [stage-acq-news.dailyhunt.in](http://stage-acq-news.dailyhunt.in)                           |
|                       |                       |                                                                                               |
|                       |                       | - [stage-social.dailyhunt.in](http://stage-social.dailyhunt.in)                               |
+-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
| **New Eterno MSC**    | **Ads and             | - [eg.money.dailyhunt.in](http://eg.money.dailyhunt.in)                                       |
|                       | Webstories**          |                                                                                               |
|                       |                       | - [eg-money.dailyhunt.in](http://eg-money.dailyhunt.in)                                       |
|                       |                       |                                                                                               |
|                       |                       | - [bg.money.dailyhunt.in](http://bg.money.dailyhunt.in)                                       |
|                       |                       |                                                                                               |
|                       |                       | - [direct.dailyhunt.in](http://direct.dailyhunt.in)                                           |
|                       |                       |                                                                                               |
|                       |                       | - [dcads-meta.dailyhunt.in](http://dcads-meta.dailyhunt.in)                                   |
|                       |                       |                                                                                               |
|                       |                       | - [webstories.dailyhunt.in](http://webstories.dailyhunt.in)                                   |
|                       +-----------------------+-----------------------------------------------------------------------------------------------+
|                       | **Poll-UGC-WAP**      | - [ugc-social.dailyhunt.in](http://ugc-social.dailyhunt.in)                                   |
|                       |                       |                                                                                               |
|                       |                       | - [poll-services-entity.dailyhunt.in](http://poll-services-entity.dailyhunt.in)               |
|                       |                       |                                                                                               |
|                       |                       | - [m.dailyhunt.in](http://m.dailyhunt.in)                                                     |
+-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
