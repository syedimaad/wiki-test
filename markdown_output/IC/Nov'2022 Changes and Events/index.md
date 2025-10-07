+----------------+--------------------------------------------------------------------------------------------------------------------------+
| **Nov\' 2022** | **Changes/Events/Incidents**                                                                                             |
+----------------+--------------------------------------------------------------------------------------------------------------------------+
| 1-Nov-2022     | 1.  AWS traffic was updated to 50% using GTM (CDN-1216e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA)                   |
+----------------+--------------------------------------------------------------------------------------------------------------------------+
| 3-Nov-2022     | 1.  [dcads-meta.dailyhunt.in](http://dcads-meta.dailyhunt.in/) started receiving live traffic                            |
|                |     (CDN-1118e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA)                                                            |
|                |                                                                                                                          |
|                | 2.  AWS traffic was updated to 80% using GTM (CDN-1232e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA)                   |
+----------------+--------------------------------------------------------------------------------------------------------------------------+
| 4-Nov-2022     | 1.  AWS traffic was updated to 100% using GTM (CDN-1242e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA)                  |
+----------------+--------------------------------------------------------------------------------------------------------------------------+
| 9-Nov-2022     | 1.  Cache exclusion for below paths on [poll-services-entity.dailyhunt.in](http://poll-services-entity.dailyhunt.in):\   |
|                |     /api/vi/user/pollResponse?pollResponse=\                                                                             |
|                |     /api/vi/user/getCookies?pollIds= (CDN-1291e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA)                           |
|                |                                                                                                                          |
|                | 2.  5xx on [api-news.dailyhunt.in](http://api-news.dailyhunt.in) CDN-1310e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA |
+----------------+--------------------------------------------------------------------------------------------------------------------------+
| 10-Nov-2022    | 1.  Offload decrease and increase in origin traffic for [eg.money.dai](http://eg.money.dailyhunt.in)lyhunt.in            |
|                |     (CDN-1366e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA )\                                                          |
|                |     On Nov 9th, there was a sync issue with the backend server and due to which the offload numbers are lower            |
+----------------+--------------------------------------------------------------------------------------------------------------------------+
| 11-Nov-2022    | 1.  DH Apps SQLi attack group is moved to deny (Akamai KSD)                                                              |
+----------------+--------------------------------------------------------------------------------------------------------------------------+
| 12-Nov-2022    | 1.Through put issue while accessing content from GCP CDN CDN-1352e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA         |
+----------------+--------------------------------------------------------------------------------------------------------------------------+
| 13-Nov-2022    | 1.  Error on [http://api-news.dailyhunt.in](http://api-news.dailyhunt.in){card-appearance="inline"} (Engg. team is       |
|                |     checking.) CDN-1348e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                   |
+----------------+--------------------------------------------------------------------------------------------------------------------------+
| 14-Nov-2022    | 1.  [samsung.dailyhunt.in](http://samsung.dailyhunt.in) reported issue with Akamai Ref# 128.x, raised a case             |
|                |     (F-CS-6538453) - Issue is reported with one of the Akamai clusters which was taken out of service                    |
|                |                                                                                                                          |
|                | 2.  DS2 enabled for [share-qa-az.myjosh.in](http://share-qa-az.myjosh.in)                                                |
|                |                                                                                                                          |
|                | 3.  [data.myjosh.in](http://data.myjosh.in) origin hostname updated to AWS endpoint replacing GTM                        |
|                |     (CDN-1361e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA)                                                            |
+----------------+--------------------------------------------------------------------------------------------------------------------------+
| 15-Nov-2022    | 1.  5xx on [api-news.dailyhunt.in](http://api-news.dailyhunt.in) in morning around 08:50 AM and 09:30 AM IST.            |
|                |                                                                                                                          |
|                | 2.  Validated staging environment for PV VOD migration (CDN-1362e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA) and     |
|                |     shared migration steps with Bapu for sign-off                                                                        |
+----------------+--------------------------------------------------------------------------------------------------------------------------+
| 16-Nov-2022    | 1.  Reconnect change was deployed for [samsung.dailyhunt.in](http://samsung.dailyhunt.in) and negative ttl is reduced to |
|                |     10sec (CDN-1376e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA)                                                      |
+----------------+--------------------------------------------------------------------------------------------------------------------------+
| 17-Nov-2022    | 1.  We see a slight drop in josh api traffic from Nov 10th.                                                              |
|                |                                                                                                                          |
|                | 2.  [samsung.dailyhunt.in](http://samsung.dailyhunt.in) 500 errors after cluster removal of Akamai had reduce but, trend |
|                |     continued for 500 errors due to server to server calls for beacon traffic which cannot be mitigated and should be    |
|                |     expected (F-CS-6538453) (CDN-1400e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA)                                    |
+----------------+--------------------------------------------------------------------------------------------------------------------------+
| 18-Nov-2022    | 1.  Verse configs updated with negative TTL value in expected range (CDN-1379e55da6ef-1840-3475-9293-310ba48d502dSystem  |
|                |     JIRA)                                                                                                                |
|                |                                                                                                                          |
|                | 2.  Handed over the [prod-cricket-service-c50.dailyhunt.in](http://prod-cricket-service-c50.dailyhunt.in) domain setup   |
|                |     on Akamai for testing (CDN-1339e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA)                                      |
|                |                                                                                                                          |
|                | 3.  DS2 Enabled for below domains:\                                                                                      |
|                |     [media.publicvibe.com](http://media.publicvibe.com)                                                                  |
|                |     ([https://evp.atlassian.net/browse/CDN-1417)](https://evp.atlassian.net/browse/CDN-1417)){card-appearance="inline"}\ |
|                |     [prod-cricket-service-c50.dailyhunt.in](http://prod-cricket-service-c50.dailyhunt.in)                                |
|                |     ([https://evp.atlassian.net/browse/CDN-1404)](https://evp.atlassian.net/browse/CDN-1404)){card-appearance="inline"}\ |
|                |     [poll-services-entity.dailyhunt.in](http://poll-services-entity.dailyhunt.in)                                        |
|                |     ([https://evp.atlassian.net/browse/CDN-1385)](https://evp.atlassian.net/browse/CDN-1385)){card-appearance="inline"}\ |
|                |     [election-proxy-service.dailyhunt.in](http://election-proxy-service.dailyhunt.in)                                    |
|                |     ([https://evp.atlassian.net/browse/CDN-1335)](https://evp.atlassian.net/browse/CDN-1335)){card-appearance="inline"}  |
|                |                                                                                                                          |
|                | 4.  Disabled DS2 for [[qa-cricket-service-c50.dailyhunt.in]{.underline}](http://qa-cricket-service-c50.dailyhunt.in) and |
|                |     [[stage-cricket-service-c50.dailyhunt.in]{.underline}](http://stage-cricket-service-c50.dailyhunt.in).               |
|                |     (CDN-1419e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA)                                                            |
|                |                                                                                                                          |
|                | 5.  Disabled volumetric SOCC alerts for [share.myjosh.in](http://share.myjosh.in)                                        |
|                |     (CDN-1356e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA)                                                            |
+----------------+--------------------------------------------------------------------------------------------------------------------------+
| 20-Nov-2022    | 1.  4xx spike on [api-news.dailyhunt.in](http://api-news.dailyhunt.in)                                                   |
|                |     CDN-1426e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                              |
+----------------+--------------------------------------------------------------------------------------------------------------------------+
| 21-Nov-2022    | 1.  5xx spike on [api-news.dailyhunt.in](http://api-news.dailyhunt.in).                                                  |
|                |     CDN-1433e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA\                                                             |
+----------------+--------------------------------------------------------------------------------------------------------------------------+
| 24-Nov-2022    | 1.  Ads campaign is complete for [[dcads-meta.dailyhunt.in]{.underline}](https://evp.atlassian.net/browse/CDN-1441) -    |
|                |     disabled DS2 alerts (CDN-1441e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA)                                        |
|                |                                                                                                                          |
|                | 2.  Deployed the change for logging midgress for dh-domains.                                                             |
|                |                                                                                                                          |
|                | 3.  5xx spike on multiple DH domains because we enabled the mid-gress logging last evening, route optimisations logs     |
|                |     started contributing to existing streams and resulted in the error count increase.                                   |
|                |     CDN-1453e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                              |
|                |                                                                                                                          |
|                | 4.  401 on ugc-social. CDN-1458e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                           |
|                |                                                                                                                          |
|                | 5.  400 on assets-news-bcdn CDN-1457e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                      |
|                |                                                                                                                          |
|                | 6.  5xx on josh-gateway CDN-1450e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                          |
+----------------+--------------------------------------------------------------------------------------------------------------------------+
| 25-Nov-2022    | 1.  Reverted the change for logging midgress. CDN-1453e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                    |
|                |                                                                                                                          |
|                | 2.  4xx on josh stream domain. CDN-1459e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                   |
|                |                                                                                                                          |
|                | 3.  Adding cdn_cache_key setting available in [api.myjosh.in](http://api.myjosh.in) akamai config to                     |
|                |     [cache-api.myjosh.in](http://cache-api.myjosh.in) CDN-1461e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA            |
|                |                                                                                                                          |
|                | 4.  5xx on [data.myjosh.in](http://data.myjosh.in) due to reduction in instances.                                        |
+----------------+--------------------------------------------------------------------------------------------------------------------------+
| 26-Nov-2022    | 1.  0xx on [api-news.dailyhunt.in](http://api-news.dailyhunt.in) at 06:45 AM IST.                                        |
|                |     CDN-1471e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                              |
+----------------+--------------------------------------------------------------------------------------------------------------------------+
| 27-Nov-2022    | 1.  5xx on [assets-news-bcdn.dailyhunt.in](http://assets-news-bcdn.dailyhunt.in) 04:30 PM IST.                           |
|                |     CDN-1470e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                              |
|                |                                                                                                                          |
|                | 2.  Offload drop on Josh-VOD at 03:15 AM IST. CDN-1469e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                    |
+----------------+--------------------------------------------------------------------------------------------------------------------------+
| 29-Nov-2022    | 1.  5xx on [api-news.dailyhunt.in](http://api-news.dailyhunt.in) CDN-1498e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA |
+----------------+--------------------------------------------------------------------------------------------------------------------------+
| 30-Nov-2022    | 1.  Onboarded domain [prod-cricket-service-c50.dailyhunt.in](http://prod-cricket-service-c50.dailyhunt.in)               |
|                |     (CDN-1339e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA)                                                            |
+----------------+--------------------------------------------------------------------------------------------------------------------------+
