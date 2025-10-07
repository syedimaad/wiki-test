+-----------------+-----------------------------------------------------------+
| **Nov\' 2023**  | **Changes/Events/Incidents**                              |
+-----------------+-----------------------------------------------------------+
| **1-Nov-2023**  | 1.  Created new WAF policy User-Social and deployed to    |
|                 |     prod -                                                |
|                 |     CDN-3060e55da6ef-1840-3475-9293-310ba48d502dSystem    |
|                 |     JIRA                                                  |
+-----------------+-----------------------------------------------------------+
| **5-Nov-2023**  | 1.  Low offload on api-news-proxy                         |
|                 |     CDN-3073e55da6ef-1840-3475-9293-310ba48d502dSystem    |
|                 |     JIRA                                                  |
+-----------------+-----------------------------------------------------------+
| **6-Nov-2023**  | 1.  Enabled Origin Error rate policy for ugc-social for   |
|                 |     trend review -                                        |
|                 |     CDN-3060e55da6ef-1840-3475-9293-310ba48d502dSystem    |
|                 |     JIRA                                                  |
|                 |                                                           |
|                 | 2.  Updated OHD to default settings for                   |
|                 |     [data.dailyhunt.in](http://data.dailyhunt.in) -       |
|                 |     CDN-3066e55da6ef-1840-3475-9293-310ba48d502dSystem    |
|                 |     JIRA                                                  |
|                 |                                                           |
|                 | 3.  Fallback Impletation on                               |
|                 |     [api-news.dailyhunt.in](http://api-news.dailyhunt.in) |
|                 |     CDN-3076e55da6ef-1840-3475-9293-310ba48d502dSystem    |
|                 |     JIRA                                                  |
+-----------------+-----------------------------------------------------------+
| **7-Nov-2023**  | 1.  Akamai managed cert prod deployment on slot# 151878 - |
|                 |     CDN-3078e55da6ef-1840-3475-9293-310ba48d502dSystem    |
|                 |     JIRA                                                  |
+-----------------+-----------------------------------------------------------+
| **8-Nov-2023**  | 1.  Reconnect override from Advanced Override removed for |
|                 |     [data.dailyhunt.in](http://data.dailyhunt.in) -       |
|                 |     CDN-3066e55da6ef-1840-3475-9293-310ba48d502dSystem    |
|                 |     JIRA                                                  |
+-----------------+-----------------------------------------------------------+
| **9-Nov-2023**  | 1.  Started ASE evaluation for both DH and Josh           |
|                 |     policies -                                            |
|                 |     CDN-3087e55da6ef-1840-3475-9293-310ba48d502dSystem    |
|                 |     JIRA                                                  |
|                 |     CDN-3088e55da6ef-1840-3475-9293-310ba48d502dSystem    |
|                 |     JIRA                                                  |
+-----------------+-----------------------------------------------------------+
| **10-Nov-2023** | 1.  Verse Akamai managed certs renewed and deployed to    |
|                 |     prod -                                                |
|                 |     CDN-3090e55da6ef-1840-3475-9293-310ba48d502dSystem    |
|                 |     JIRA                                                  |
+-----------------+-----------------------------------------------------------+
| **17-Nov-2023** | 1.  Discussed with Ritvik and Abhishek on latest trend    |
|                 |     and analysis on ugc-social and finalised the plan to  |
|                 |     block the traffic by Monday next week -               |
|                 |     CDN-3060e55da6ef-1840-3475-9293-310ba48d502dSystem    |
|                 |     JIRA                                                  |
+-----------------+-----------------------------------------------------------+
| **19-Nov-2023** | 1.  POST response caching enabled on api-news -           |
|                 |     IO-6257e55da6ef-1840-3475-9293-310ba48d502dSystem     |
|                 |     JIRA                                                  |
+-----------------+-----------------------------------------------------------+
| **20-Nov-2023** | 1.  POST response caching reverted on api-news -          |
|                 |     IO-6257e55da6ef-1840-3475-9293-310ba48d502dSystem     |
|                 |     JIRA                                                  |
|                 |                                                           |
|                 | 2.  Rate limit policies for UGC-Social set to Deny -      |
|                 |     CDN-3060e55da6ef-1840-3475-9293-310ba48d502dSystem    |
|                 |     JIRA                                                  |
|                 |                                                           |
|                 |     1.  Change trend recorded here: UGC-Social Rate       |
|                 |         Limiting Trend                                    |
+-----------------+-----------------------------------------------------------+
| **23-Nov-2023** | 1.  Enabled MPE on api-news proxy pattern -               |
|                 |     CDN-3086e55da6ef-1840-3475-9293-310ba48d502dSystem    |
|                 |     JIRA                                                  |
+-----------------+-----------------------------------------------------------+
| **24-Nov-2023** | 1.  api-news and proxy services alerted with Origin       |
|                 |     Connection Failure -                                  |
|                 |     CDN-3121e55da6ef-1840-3475-9293-310ba48d502dSystem    |
|                 |     JIRA                                                  |
|                 |                                                           |
|                 |     1.  Issue was due to an ISP's network glitch          |
+-----------------+-----------------------------------------------------------+
| **28-Nov-2023** | 1.  Updated Caching Rule: \*/election-share_img/\* on     |
|                 |     assets-news-bcdn.dailyhunt.in                         |
|                 |     IO-6388e55da6ef-1840-3475-9293-310ba48d502dSystem     |
|                 |     JIRA                                                  |
|                 |                                                           |
|                 | 2.  High Latency on one of the API of                     |
|                 |     [api-news.dailyhunt.in](http://api-news.dailyhunt.in) |
|                 |     <https://evp.atlassian.net/browse/CDN-3126>           |
|                 |                                                           |
|                 | 3.  Concerns Regarding High RPS and MPE Functionality on  |
|                 |     [api-news.dailyhunt.in](http://api-news.dailyhunt.in) |
|                 |     IO-6404e55da6ef-1840-3475-9293-310ba48d502dSystem     |
|                 |     JIRA                                                  |
+-----------------+-----------------------------------------------------------+
| **29-Nov-2023** | 1.  Proxy LB rule separation -                            |
|                 |     IO-6416e55da6ef-1840-3475-9293-310ba48d502dSystem     |
|                 |     JIRA                                                  |
+-----------------+-----------------------------------------------------------+
