+-----------------+-----------------------------------------------------------------------------------------------------------------+
| **Feb\' 2023**  | **Changes/Events/Incidents**                                                                                    |
+-----------------+-----------------------------------------------------------------------------------------------------------------+
| **1-Feb-2023**  | 1.  Phase 6 and phase 7 changes for Origin TAT changes deployed -                                               |
|                 |     CDN-1878e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                     |
|                 |                                                                                                                 |
|                 | 2.  WAF SQLi events reported on API-NEWS due to incorrect URL formation -                                       |
|                 |     CDN-1881e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                     |
|                 |                                                                                                                 |
|                 | 3.  Origin TAT and Reconnect changes (phase 6 and 7) deployment:                                                |
|                 |                                                                                                                 |
|                 |     - **Phase 6**                                                                                               |
|                 |                                                                                                                 |
|                 |       [prod-pullnotification.dailyhunt.in](http://prod-pullnotification.dailyhunt.in) v6 \[Logging Origin TAT + |
|                 |       Max reconnect\]\                                                                                          |
|                 |       [newshunt.net.in](http://newshunt.net.in) v13 \[Logging Origin TAT\]\                                     |
|                 |       [eg-money.dailyhunt.in](http://eg-money.dailyhunt.in) v7 \[Logging Origin TAT\]\                          |
|                 |       [itel.dailyhunt.in](http://itel.dailyhunt.in) v17 \[Logging Origin TAT + Max reconnect\]\                 |
|                 |       [tecno.dailyhunt.in](http://tecno.dailyhunt.in) v5 \[Logging Origin TAT + Max reconnect\]\                |
|                 |       [acq-news.dailyhunt.in](http://acq-news.dailyhunt.in) \[Logging Origin TAT\]\                             |
|                 |       [infinix.dailyhunt.in](http://infinix.dailyhunt.in) \[Logging Origin TAT + Max reconnect\]\               |
|                 |       [pwa-api.dailyhunt.in](http://pwa-api.dailyhunt.in) \[Logging Origin TAT\]\                               |
|                 |       [indus.dailyhunt.in](http://indus.dailyhunt.in) \[Logging Origin TAT + Max reconnect\]                    |
|                 |                                                                                                                 |
|                 |     - **Phase 7**                                                                                               |
|                 |                                                                                                                 |
|                 |       [money.dailyhunt.in](http://money.dailyhunt.in) v19 \[Logging Origin TAT + Max Reconnect\]\               |
|                 |       [perf-news.dailyhunt.in](http://perf-news.dailyhunt.in) v3 \[Logging Origin TAT + Max Reconnect\]\        |
|                 |       [3w.dailyhunt.com](http://3w.dailyhunt.com) v16 \[Logging Origin TAT + Max Reconnect\]\                   |
|                 |       [deals.newshuntads.com](http://deals.newshuntads.com) v10 \[Logging Origin TAT + Max Reconnect\]\         |
|                 |       [m.yoapp.ai](http://m.yoapp.ai) v5  \[Logging Origin TAT + Max Reconnect\]\                               |
|                 |       [campaign-edge.dailyhunt.in](http://campaign-edge.dailyhunt.in) v20 \[Logging Origin TAT\]\               |
|                 |       [h2i.dailyhunt.in](http://h2i.dailyhunt.in) v4 \[Logging Origin TAT + Max Reconnect\]\                    |
|                 |       [webqa.dailyhunt.in](http://webqa.dailyhunt.in) v4 \[Logging Origin TAT + Max Reconnect\]\                |
|                 |       [contest.dailyhunt.in](http://contest.dailyhunt.in) v14 \[Logging Origin TAT + Max Reconnect\]\           |
|                 |       [developer.dailyhunt.in](http://developer.dailyhunt.in) v5 \[Logging Origin TAT\]                         |
+-----------------+-----------------------------------------------------------------------------------------------------------------+
| **2-Feb-2023**  | 1.  /webview/podcast served stale from Akamai during deployment when app was unreachable -                      |
|                 |     CDN-1894e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                     |
|                 |                                                                                                                 |
|                 | 2.  DNS negative TTL reduced to 1sec on api-news - F-CS-6735075 (Akamai Case#)                                  |
|                 |                                                                                                                 |
|                 | 3.  Removed AAAA (IPv6) record removed from Edge DNS for api-news FQDN -                                        |
|                 |     IO-275e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                       |
+-----------------+-----------------------------------------------------------------------------------------------------------------+
| **3-Feb-2023**  | 1.  Rate limits for ugc-social, feed, and poll-services-entity deployed to production -                         |
|                 |     CDN-1888e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                     |
|                 |                                                                                                                 |
|                 | 2.  Completed ASE version upgrade for API-NEWS - CDN-1904e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA        |
+-----------------+-----------------------------------------------------------------------------------------------------------------+
| **7-Feb-2023**  | 1.  Origin TAT and Reconnect changes deployed to production: CDN-1878e55da6ef-1840-3475-9293-310ba48d502dSystem |
|                 |     JIRA\                                                                                                       |
|                 |     [pwaqa.dailyhunt.in](http://pwaqa.dailyhunt.in) v7 \[Logging origin TAT\]                                   |
|                 |                                                                                                                 |
|                 |     [central.verseinnovation.com](http://central.verseinnovation.com) v7 \[Logging origin TAT\]                 |
|                 |                                                                                                                 |
|                 |     [origin-api-dhtv.dailyhunt.in](http://origin-api-dhtv.dailyhunt.in) v10 \[Logging origin TAT+ Reconnect\]   |
|                 |                                                                                                                 |
|                 |     [vivo.dailyhunt.in](http://vivo.dailyhunt.in) v7 \[Logging origin TAT+ Reconnect\]                          |
|                 |                                                                                                                 |
|                 |     [xiaomi.dailyhunt.in](http://xiaomi.dailyhunt.in) v14 \[Logging origin TAT+ Reconnect\]                     |
|                 |                                                                                                                 |
|                 |     [daecdn1.dailyhunt.in](http://daecdn1.dailyhunt.in) v9 \[Logging origin TAT+ Reconnect\]                    |
|                 |                                                                                                                 |
|                 |     [network-cacti.dailyhunt.in](http://network-cacti.dailyhunt.in) \[not an active config\]                    |
|                 |                                                                                                                 |
|                 |     [adengine.dailyhunt.in](http://adengine.dailyhunt.in) v10 \[Logging origin TAT+ Reconnect\]                 |
|                 |                                                                                                                 |
|                 |     [dhtvcdn.newshunt.com](http://dhtvcdn.newshunt.com) v12 \[Logging origin TAT\]                              |
|                 |                                                                                                                 |
|                 |     [web.dailyhunt.in](http://web.dailyhunt.in) v10 \[Logging origin TAT+ Reconnect\]                           |
|                 |                                                                                                                 |
|                 |     [lucretia.dailyhunt.in](http://lucretia.dailyhunt.in) v7 \[Logging origin TAT+ Reconnect\]                  |
|                 |                                                                                                                 |
|                 |     [assets-money.dailyhunt.in](http://assets-money.dailyhunt.in) v19 \[Logging origin TAT+ Reconnect\]         |
|                 |                                                                                                                 |
|                 |     [library.dailyhunt.in](http://library.dailyhunt.in) v7 \[Logging origin TAT\]                               |
|                 |                                                                                                                 |
|                 |     [3w.dailyhunt.co](http://3w.dailyhunt.co) v11 \[Logging origin TAT+ Reconnect\]                             |
|                 |                                                                                                                 |
|                 |     [account.dailyhunt.in](http://account.dailyhunt.in) v19 \[Logging origin TAT\]                              |
|                 |                                                                                                                 |
|                 |     [img-books.dailyhunt.in](http://img-books.dailyhunt.in) v6  \[Logging origin TAT\]\                         |
|                 |     [[campaign-edge.dailyhunt.in]{.underline}](https://campaign-edge.dailyhunt.in)                              |
|                 |                                                                                                                 |
|                 | 2.  Multiple alerts received on live tv (TCL) channels - CDN-1924e55da6ef-1840-3475-9293-310ba48d502dSystem     |
|                 |     JIRA                                                                                                        |
+-----------------+-----------------------------------------------------------------------------------------------------------------+
| **8-Feb-2023**  | 1.  ASN and Midgress logging for api-news and Evergreen Ads are deployed -                                      |
|                 |     CDN-1930e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                     |
|                 |                                                                                                                 |
|                 | 2.  Eterno Infotech KSD v76 for ASE upgrade deployed to production -                                            |
|                 |     CDN-1935e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                     |
|                 |                                                                                                                 |
|                 | 3.  Verse - Primary v42 for ASE upgrade deployed to production -                                                |
|                 |     CDN-1936e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                     |
+-----------------+-----------------------------------------------------------------------------------------------------------------+
| **10-Feb-2023** | 1.  Updated few domains to use Standard TLS certs and updated DNS CNAMEd EHNs:                                  |
|                 |     CDN-1960e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                     |
|                 |                                                                                                                 |
|                 | 2.  ASE upgrade completed for Verse - Secondary v12 - CDN-1963e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA   |
|                 |                                                                                                                 |
|                 | 3.  5xx on live channels. CDN-1954e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                               |
|                 |                                                                                                                 |
|                 | 4.  Provisioned non-prod standard TLS cert on Eterno account -                                                  |
|                 |     CDN-1962e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                     |
+-----------------+-----------------------------------------------------------------------------------------------------------------+
| **12-Feb-2023** | 1.  [data.dailyhunt.in](http://data.dailyhunt.in) edge DNS TTL was increased to 1 day.                          |
|                 |     CDN-1759e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                     |
+-----------------+-----------------------------------------------------------------------------------------------------------------+
| **13-Feb-2023** | 1.  Prefetch feature on eg.money and bg.money was removed. CDN-1916e55da6ef-1840-3475-9293-310ba48d502dSystem   |
|                 |     JIRA                                                                                                        |
|                 |                                                                                                                 |
|                 | 2.  The static IP TTL for [feed.dailyhunt.in](http://feed.dailyhunt.in) has been increased to 1 day.            |
|                 |     CDN-1758e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                     |
+-----------------+-----------------------------------------------------------------------------------------------------------------+
| **14-Feb-2023** | 1.  Origin TAT and Reconnect changes deployed to production: CDN-1878e55da6ef-1840-3475-9293-310ba48d502dSystem |
|                 |     JIRA\                                                                                                       |
|                 |     [ai-lab-stream-data.coolfie.io](http://ai-lab-stream-data.coolfie.io)\                                      |
|                 |     [webitem-share.myjosh.in](http://webitem-share.myjosh.in)\                                                  |
|                 |     [website-verse.in](http://website-verse.in)\                                                                |
|                 |     [jot.myjosh.in](http://jot.myjosh.in)\                                                                      |
|                 |     [support.myjosh.in](http://support.myjosh.in)\                                                              |
|                 |     [josh-lib.myjosh.in](http://josh-lib.myjosh.in)\                                                            |
|                 |     [api.myjosh.in](http://api.myjosh.in)\                                                                      |
|                 |     [cache-api.myjosh.in](http://cache-api.myjosh.in)\                                                          |
|                 |     [nearme.dailyhunt.in](http://nearme.dailyhunt.in)                                                           |
|                 |                                                                                                                 |
|                 | 2.  Eterno domains [api-cool.dailyhunt.in](http://api-cool.dailyhunt.in) and                                    |
|                 |     [widgets.dailyhunt.in](http://widgets.dailyhunt.in) were removed from KSD analysis:\                        |
|                 |     CDN-1976e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                     |
|                 |                                                                                                                 |
|                 | 3.  503 on [m.dailyhunt.in](http://m.dailyhunt.in) due to deployment from engg side.                            |
|                 |     IO-462e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                       |
+-----------------+-----------------------------------------------------------------------------------------------------------------+
| **15-Feb-2023** | 1.  Cache bypass on [acdn.newshunt.com](http://acdn.newshunt.com).                                              |
|                 |     IO-423e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                       |
|                 |                                                                                                                 |
|                 | 2.  Akamai certs on slots 26575, 30712 and 153414 deployed to production:\                                      |
|                 |     CDN-1958e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA\                                                    |
|                 |     CDN-1957e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA\                                                    |
|                 |     CDN-1959e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                     |
|                 |                                                                                                                 |
|                 | 3.  Removed CNAME record for [m.yoapp.ai](http://m.yoapp.ai) and deactivated Akamai config -                    |
|                 |     CDN-1014e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                     |
+-----------------+-----------------------------------------------------------------------------------------------------------------+
| **16-Feb-2023** | 1.  Updated LB IPs for multiple DNS records for network troubleshooting -                                       |
|                 |     IO-490e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                       |
|                 |                                                                                                                 |
|                 | 2.  Azure Origin changes for Josh streams deployed to production -                                              |
|                 |     CDN-1987e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                     |
|                 |                                                                                                                 |
|                 | 3.  503 on [api-news.dailyhunt.in](http://api-news.dailyhunt.in)                                                |
|                 |     CDN-2000e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                     |
+-----------------+-----------------------------------------------------------------------------------------------------------------+
| **17-Feb-2023** | 1.  Cert cleanup activity complete on Akamai Verse contract:\                                                   |
|                 |     CDN-1982e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA\                                                    |
|                 |     CDN-1983e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA\                                                    |
|                 |     CDN-1984e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                     |
|                 |                                                                                                                 |
|                 | 2.  cache Bypass on [api-news.dailyhunt.in](http://api-news.dailyhunt.in).                                      |
|                 |     IO-528e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                       |
|                 |                                                                                                                 |
|                 | 3.  Cleanup of [m.yoapp.ai](http://m.yoapp.ai) complete - CDN-1014e55da6ef-1840-3475-9293-310ba48d502dSystem    |
|                 |     JIRA                                                                                                        |
|                 |                                                                                                                 |
|                 | 4.  Setup [saz-g.myjosh.in](http://saz-g.myjosh.in) on Media CDN.                                               |
|                 |     IO-542e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                       |
|                 |                                                                                                                 |
|                 | 5.  Completed Akamai onboarding of [agency.dailyhunt.in](http://agency.dailyhunt.in) -                          |
|                 |     CDN-2002e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                     |
|                 |                                                                                                                 |
|                 | 6.  ASN + Midgress logging + Origin TAT - CDN-2003e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA\              |
|                 |     Enabling ASN                                                                                                |
|                 |                                                                                                                 |
|                 |     ============                                                                                                |
|                 |                                                                                                                 |
|                 |     [data.dailyhunt.in](http://data.dailyhunt.in) v43\                                                          |
|                 |     \                                                                                                           |
|                 |     Log ASN + Enable Midgress Logging Only for Errors\[0xx,5xx\]                                                |
|                 |                                                                                                                 |
|                 |     =================================================                                                           |
|                 |                                                                                                                 |
|                 |     ugc-social.dailyhunt.in  v30                                                                                |
|                 |                                                                                                                 |
|                 |     feed.dailyhunt.in  v58                                                                                      |
|                 |                                                                                                                 |
|                 |     [bg.money.dailyhunt.in](http://bg.money.dailyhunt.in) v11                                                   |
|                 |                                                                                                                 |
|                 |     share.myjosh.in  v50                                                                                        |
|                 |                                                                                                                 |
|                 |     [gateway.coolfie.io](http://gateway.coolfie.io) v42                                                         |
|                 |                                                                                                                 |
|                 |     [gateway.myjosh.in](http://gateway.myjosh.in) v13                                                           |
|                 |                                                                                                                 |
|                 |     [feed.myjosh.in](http://feed.myjosh.in) v12                                                                 |
|                 |                                                                                                                 |
|                 |     [data.myjosh.in](http://data.myjosh.in) v12                                                                 |
|                 |                                                                                                                 |
|                 |     [feed.cooflie.io](http://feed.cooflie.io) v22                                                               |
|                 |                                                                                                                 |
|                 |     [cache-api.myjosh.in](http://cache-api.myjosh.in) v9                                                        |
|                 |                                                                                                                 |
|                 |     Log ASN + Enable Midgress Logging Only for Errors\[0xx,5xx\] + Origin TAT                                   |
|                 |                                                                                                                 |
|                 |     ===========================================================                                                 |
|                 |                                                                                                                 |
|                 |     stream.coolfie.io_AMD v41                                                                                   |
|                 |                                                                                                                 |
|                 |     saz.myjosh.in_AMD v12                                                                                       |
+-----------------+-----------------------------------------------------------------------------------------------------------------+
| **22-Feb-2023** | 1.  OHD set to platform deafult for [feed.myjosh.in](http://feed.myjosh.in).                                    |
|                 |     CDN-2021e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                     |
|                 |                                                                                                                 |
|                 | 2.  Added Downstream Cacheability and Cache HTTP error Response Behaviour on                                    |
|                 |     share.myjpsh.inCDN-2014e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                      |
+-----------------+-----------------------------------------------------------------------------------------------------------------+
| **23-Feb-2023** | 1.  ASN and Midgress Error Logging is enabled in following Phase 2 configs -                                    |
|                 |     CDN-2003e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                     |
|                 |                                                                                                                 |
|                 |     Enabling ASN                                                                                                |
|                 |                                                                                                                 |
|                 |     ============                                                                                                |
|                 |                                                                                                                 |
|                 |     [dmk-assets.dailyhunt.com](http://dmk-assets.dailyhunt.com) v4                                              |
|                 |                                                                                                                 |
|                 |     [bcdn.newshunt.com](http://bcdn.newshunt.com) v35                                                           |
|                 |                                                                                                                 |
|                 |     [assets-videos.dailyhunt.in](http://assets-videos.dailyhunt.in) v17                                         |
|                 |                                                                                                                 |
|                 |     [prod-pullnotification.dailyhunt.in](http://prod-pullnotification.dailyhunt.in) v7                          |
|                 |                                                                                                                 |
|                 |     Log ASN + Enable Midgress Logging Only for Errors\[0xx,5xx\]                                                |
|                 |                                                                                                                 |
|                 |     =================================================                                                           |
|                 |                                                                                                                 |
|                 |     [newshuntads.com](http://newshuntads.com) v37                                                               |
|                 |                                                                                                                 |
|                 |     [newshunt.com](http://newshunt.com) v64                                                                     |
|                 |                                                                                                                 |
|                 |     [media.publicvibe.com](http://media.publicvibe.com) v10                                                     |
|                 |                                                                                                                 |
|                 |     [stream.dailyhunt.io](http://stream.dailyhunt.io) v29                                                       |
+-----------------+-----------------------------------------------------------------------------------------------------------------+
| **24-Feb-2023** | 1\. Enabled cookie logging on Verse DS2 domains. CDN-2040e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA        |
+-----------------+-----------------------------------------------------------------------------------------------------------------+
| **27-Feb-2023** | 1.  Enabled cookie logging on DH DS2 domains and move from S3 to GCS.                                           |
|                 |     CDN-2041e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                                                     |
|                 |                                                                                                                 |
|                 | 2.  Default platform OHD setting for josh domain.CDN-2021e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA        |
|                 |                                                                                                                 |
|                 | 3.  Remove sureroute on [eg.money.dailyhunt.in](http://eg.money.dailyhunt.in) &                                 |
|                 |     [bg.money.dailyhunt.in](http://bg.money.dailyhunt.in). CDN-1916e55da6ef-1840-3475-9293-310ba48d502dSystem   |
|                 |     JIRA                                                                                                        |
+-----------------+-----------------------------------------------------------------------------------------------------------------+
