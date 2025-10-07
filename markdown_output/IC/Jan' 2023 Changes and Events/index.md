+-----------------+----------------------------------------------------------------------------------------------------------+
| **Jan\' 2023**  | **Changes/Events/Incidents**                                                                             |
+-----------------+----------------------------------------------------------------------------------------------------------+
| **2-Jan-2023**  | 1.  Provisioned Akamai managed DV SAN cert for www.pvibe.in                                              |
|                 |                                                                                                          |
|                 | 2.  Started Akamai managed wildcard certs provisioning for [newshunt.com](http://newshunt.com),          |
|                 |     [publicvibe.com](http://publicvibe.com), [verse.in](http://verse.in), and coolfie.io                 |
|                 |                                                                                                          |
|                 | 3.  4xx increase on PV-VOD. (Engg are archiving \~18k PV video items daily. Requests we are seeing like  |
|                 |     above are for archived items.)                                                                       |
|                 |                                                                                                          |
|                 | 4.  400 on assets-news-bcdn.dailyhunt.in.                                                                |
|                 |                                                                                                          |
|                 | 5.  500 on [eg.money.dailyhunt.in](http://eg.money.dailyhunt.in) and                                     |
|                 |     [bg.money.dailyhunt.in](http://bg.money.dailyhunt.in). (Due to increase in traffic.)                 |
+-----------------+----------------------------------------------------------------------------------------------------------+
| **3-Jan-2023**  | 1.  5xx on [data.dailyhunt.in](http://data.dailyhunt.in).                                                |
|                 |     CDN-1678e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                              |
+-----------------+----------------------------------------------------------------------------------------------------------+
| **4-Jan-2023**  | 1.  400 on Image Service \| [assets-news-bcdn.dailyhunt.in](http://assets-news-bcdn.dailyhunt.in).       |
|                 |     CDN-1684e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                              |
|                 |                                                                                                          |
|                 | 2.  502 errors reported on api-news for URL /api/v2/registerdevice due to response headers size greater  |
|                 |     than 8192 bytes - increased limit to 16K in Akamai config -                                          |
|                 |     CDN-1686e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                              |
+-----------------+----------------------------------------------------------------------------------------------------------+
| **5-Jan-2023**  | - DNS TTL for                                                                                            |
|                 |   [fc26bc5f1b4416f81c6f3a95615d3c8c.dailyhunt.in](http://fc26bc5f1b4416f81c6f3a95615d3c8c.dailyhunt.in/) |
|                 |   is updated from 60sec to 5mins - CDN-1693e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
|                 |                                                                                                          |
|                 | - Origin TAT and reconnect changes completed as phase 2 deployment of Eterno configs:                    |
|                 |                                                                                                          |
|                 |   - [adspecs.dailyhunt.in](http://adspecs.dailyhunt.in) v3                                               |
|                 |                                                                                                          |
|                 |   - [widgets.dailyhunt.in](http://widgets.dailyhunt.in) v21                                              |
|                 |                                                                                                          |
|                 |   - [internal-zone-proxy-service.dailyhunt.in](http://internal-zone-proxy-service.dailyhunt.in) v13      |
|                 |                                                                                                          |
|                 |   - [stream.dailyhunt.io](http://stream.dailyhunt.io) v27                                                |
|                 |                                                                                                          |
|                 |   - [api-dailytv.dailyhunt.in](http://api-dailytv.dailyhunt.in) v17                                      |
|                 |                                                                                                          |
|                 |   - [pwa.dailyhunt.in](http://pwa.dailyhunt.in) v19                                                      |
+-----------------+----------------------------------------------------------------------------------------------------------+
| **6-Jan-2023**  | 1.  Added rule Offload_popular/sync on cache-api.myjosh.in                                               |
|                 |     CDN-1461e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                              |
+-----------------+----------------------------------------------------------------------------------------------------------+
| **9-Jan-2023**  | 1.  Added Rule Offload on [cache-api.myjosh.in](http://cache-api.myjosh.in)                              |
|                 |     CDN-1700e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                              |
+-----------------+----------------------------------------------------------------------------------------------------------+
| **10-Jan-2023** | 1.  Reported 504 spikes on [feed.coolfie.io](http://feed.coolfie.io) -                                   |
|                 |     CDN-1709e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                              |
|                 |                                                                                                          |
|                 | 2.  Increase in 403 errors noticed on one of the streams CP Code -                                       |
|                 |     CDN-1713e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                              |
|                 |                                                                                                          |
|                 | 3.  High origin hits ACC alerts on [feed.dailyhunt.in](http://feed.dailyhunt.in) -                       |
|                 |     CDN-1714e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                              |
|                 |                                                                                                          |
|                 | 4.  Origin TAT and reconnect changes completed as phase 4 deployment:                                    |
|                 |                                                                                                          |
|                 | - [share.coolfie.io](http://share.coolfie.io) v18                                                        |
|                 |                                                                                                          |
|                 | - [analytics.verse.in](http://analytics.verse.in) v2                                                     |
|                 |                                                                                                          |
|                 | - [feed.cooflie.io](http://feed.cooflie.io) v21                                                          |
|                 |                                                                                                          |
|                 | - [gateway.coolfie.io](http://gateway.coolfie.io) v41                                                    |
|                 |                                                                                                          |
|                 | - [api.cooflie.io](http://api.cooflie.io) v31                                                            |
+-----------------+----------------------------------------------------------------------------------------------------------+
| **11-Jan-2023** | 1.  5xx reported on api-news (around Jan 10th evening, 8PM - 9:30PM IST) -                               |
|                 |     CDN-1717e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                              |
|                 |                                                                                                          |
|                 | 2.  Origin connection failure reported on [abof.myjosh.in](http://abof.myjosh.in) -                      |
|                 |     CDN-1718e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                              |
+-----------------+----------------------------------------------------------------------------------------------------------+
| **12-Jan-2023** | 1.  Deployed change for Evergreen Ads to serve stale when origin timeout is noticed -                    |
|                 |     CDN-1710e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                              |
|                 |                                                                                                          |
|                 | 2.  Midgress logging is enabled for [abof.myjosh.in](http://abof.myjosh.in) to cover 0xx and 5xx         |
|                 |     errors - CDN-1731e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                     |
+-----------------+----------------------------------------------------------------------------------------------------------+
| **15-Jan-2023** | 1.  404 on [api-news.dailyhunt.in](http://api-news.dailyhunt.in) (update from engg.- 404 is a known      |
|                 |     issue triggered for IOS webitem notifications this will get fixed with the ongoing release).         |
+-----------------+----------------------------------------------------------------------------------------------------------+
| **16-Jan-2023** | 1.  Site Failover to serve stale content for Evergreen Ads reverted due to increasing 503 errors -       |
|                 |     CDN-1710e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                              |
|                 |                                                                                                          |
|                 | 2.  Discussed with Akamai security team to enable ASE Eval Mode and started working on revising Eterno   |
|                 |     KSD config DoS Rate Limits - CDN-1731e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                 |
+-----------------+----------------------------------------------------------------------------------------------------------+
| **17-Jan-2023** | 1.  Enabled live monitoring for [cache-api.myjosh.in](http://cache-api.myjosh.in) -                      |
|                 |     CDN-1755e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                              |
+-----------------+----------------------------------------------------------------------------------------------------------+
| **18-Jan-2023** | 1.  400 on [api-news.dailyhunt.in](http://api-news.dailyhunt.in).                                        |
|                 |     CDN-1771e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                              |
|                 |                                                                                                          |
|                 | 2.  403 on [stream.coolfie.io](http://stream.coolfie.io). (due to wrong/fake URL).                       |
|                 |                                                                                                          |
|                 | 3.  Origin TAT and reconnect changes deployment (phase 5):                                               |
|                 |                                                                                                          |
|                 |     - qa-widgets.dailyhunt.in_OD                                                                         |
|                 |                                                                                                          |
|                 |     - [stage-assets-news-bcdn.dailyhunt.in](http://stage-assets-news-bcdn.dailyhunt.in)                  |
|                 |                                                                                                          |
|                 |     - [dmk-assets.dailyhunt.com](http://dmk-assets.dailyhunt.com)                                        |
|                 |                                                                                                          |
|                 |     - [stage-bcdn.newshunt.com](http://stage-bcdn.newshunt.com)                                          |
|                 |                                                                                                          |
|                 |     - [assets-videos.dailyhunt.in](http://assets-videos.dailyhunt.in)                                    |
|                 |                                                                                                          |
|                 |     - qa-widgets.dailyhunt.in_OD1                                                                        |
|                 |                                                                                                          |
|                 |     - [media.publicvibe.com](http://media.publicvibe.com)                                                |
|                 |                                                                                                          |
|                 |     - [stage-stream.dailyhunt.in](http://stage-stream.dailyhunt.in)                                      |
|                 |                                                                                                          |
|                 |     - [sandbox-media.publicvibe.com](http://sandbox-media.publicvibe.com)                                |
|                 |                                                                                                          |
|                 |     - [stream-vod-ak.dailyhunt.in](http://stream-vod-ak.dailyhunt.in)                                    |
+-----------------+----------------------------------------------------------------------------------------------------------+
| **19-Jan-2023** | 1.  Deployed new rate limits for [data.dailyhunt.in](http://data.dailyhunt.in) -                         |
|                 |     CDN-1752e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                              |
|                 |                                                                                                          |
|                 | 2.  DH live channels 400 issue. CDN-1775e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                  |
+-----------------+----------------------------------------------------------------------------------------------------------+
| **20-Jan-2023** | 1.  Redeployed changes to serve stale during failover for Evergreen Ads -                                |
|                 |     CDN-1710e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                              |
|                 |                                                                                                          |
|                 | 2.  Configured Google SSO integration on akamai portal.                                                  |
|                 |     CDN-1750e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                              |
+-----------------+----------------------------------------------------------------------------------------------------------+
| **21-Jan-2023** | 1.  Load time issue on [acdn.newshuntads.com](http://acdn.newshuntads.com).                              |
|                 |     CDN-1804e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                              |
|                 |                                                                                                          |
|                 | 2.  503 on [api-news.dailyhunt.in](http://api-news.dailyhunt.in).                                        |
|                 |     CDN-1805e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                              |
|                 |                                                                                                          |
|                 | 3.  Multiple Http request failing for live channels. CDN-1801e55da6ef-1840-3475-9293-310ba48d502dSystem  |
|                 |     JIRA                                                                                                 |
+-----------------+----------------------------------------------------------------------------------------------------------+
| **22-Jan-2023** | 1.  503 on [api-news.dailyhunt.in](http://api-news.dailyhunt.in).                                        |
|                 |     CDN-1805e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                              |
|                 |                                                                                                          |
|                 | 2.  Enabled DS2 for assets-money.dailyhunt.in.CDN-1803e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA    |
|                 |                                                                                                          |
|                 | 3.  Enabled DS2 for acdn.newshuntads.com.CDN-1802e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA         |
+-----------------+----------------------------------------------------------------------------------------------------------+
| **23-Jan-2023** | 1.  Disabled SAN cert for PV domains on Akamai - CDN-1668e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA |
+-----------------+----------------------------------------------------------------------------------------------------------+
| **24-Jan-2023** | 1.  503 spike on [api-news.dailyhunt.in](http://api-news.dailyhunt.in) due to story cluster went down.   |
+-----------------+----------------------------------------------------------------------------------------------------------+
| **25-Jan-2023** | 1.  Added uft cookie as cacheKey for /api/v2/upgrade/dynamic/version?entity=EVENT_OPTIN.                 |
|                 |     CDN-1830e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                              |
+-----------------+----------------------------------------------------------------------------------------------------------+
| **30-Jan-2023** | 1.  gateway myjosh and coolfie domains reported 404 and 500 responses due to MySQL connection failure -  |
|                 |     CDN-1850e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                              |
|                 |                                                                                                          |
|                 | 2.  Onboarded [pwa-static.myjosh.in](http://pwa-static.myjosh.in) to Cloud CDN to deliver Tango apk      |
|                 |     file - CDN-1837e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                       |
+-----------------+----------------------------------------------------------------------------------------------------------+
| **31-Jan-2023** | 1.  WAF event reported on API-NEWS - CDN-1868e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA             |
+-----------------+----------------------------------------------------------------------------------------------------------+
