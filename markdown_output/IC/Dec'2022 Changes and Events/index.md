+-----------------+---------------------------------------------------------------------------+
| **Dec\' 2022**  | **Changes/Events/Incidents**                                              |
+-----------------+---------------------------------------------------------------------------+
| 1-Dec-2022      | 1.  Public DNS modification.                                              |
|                 |     CDN-1524e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
+-----------------+---------------------------------------------------------------------------+
| 2-Dec-2022      | 1.  5xx on data.myjosh.in                                                 |
|                 |                                                                           |
|                 | 2.  5xx on josh-vod                                                       |
|                 |                                                                           |
|                 | 3.  Usage increased on Josh-vod while hits remains same.                  |
|                 |     CDN-1526e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
|                 |                                                                           |
|                 | 4.  Hits increased on DH-VOD.                                             |
|                 |     CDN-1527e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
+-----------------+---------------------------------------------------------------------------+
| 3-Dec-2022      | 1.  0xx on [data.dailyhunt.in](http://data.dailyhunt.in) due to crunch in |
|                 |     instances. CDN-1541e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA    |
|                 |                                                                           |
|                 | 2.  0xx on [api-news.dailyhunt.in](http://api-news.dailyhunt.in).         |
|                 |     CDN-1543e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
|                 |                                                                           |
|                 | 3.  Dip in overall josh traffic.                                          |
|                 |     CDN-1544e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
|                 |                                                                           |
|                 | 4.  Error spike on [data.myjosh.in](http://data.myjosh.in)                |
|                 |     CDN-1546e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
|                 |                                                                           |
|                 | 5.  Error spike on feed-josh domain                                       |
|                 |                                                                           |
|                 | 6.  Created 3 RTMP feed for josh-event stream.                            |
|                 |     CDN-1530e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
+-----------------+---------------------------------------------------------------------------+
| 4-Dec-2022      | 1.  0xx on api-news.dailyhunt.in.                                         |
|                 |     CDN-1543e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
|                 |                                                                           |
|                 | 2.  Error spike on [data.myjosh.in](http://data.myjosh.in).               |
|                 |     CDN-1546e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
|                 |                                                                           |
|                 | 3.  Error spike on feed-josh domain                                       |
+-----------------+---------------------------------------------------------------------------+
| 5-Dec-2022      | 1.  isMidgress activated on                                               |
|                 |     [api-news.dailyhunt.in](http://api-news.dailyhunt.in)                 |
|                 |     CDN-1540e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
|                 |                                                                           |
|                 | 2.  Edit access on Edge DNS has been provided to                          |
|                 |     <vishal.prakash@verse.in>                                             |
|                 |     CDN-1539e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
|                 |                                                                           |
|                 | 3.  0xx on [api-news.dailyhunt.in](http://api-news.dailyhunt.in)          |
|                 |     CDN-1543e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
|                 |                                                                           |
|                 | 4.  5xx on [data.dailyhunt.in](http://data.dailyhunt.in).                 |
|                 |     CDN-1550e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
+-----------------+---------------------------------------------------------------------------+
| 6-Dec-2022      | 1.  TCP Connection Timed Out on live channels.                            |
|                 |     CDN-1555e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
|                 |                                                                           |
|                 | 2.  CDN Change in election-proxy property.                                |
|                 |     CDN-1557e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
|                 |                                                                           |
|                 | 3.  Election caching changes for                                          |
|                 |     [api-news.dailyhunt.in](http://api-news.dailyhunt.in)                 |
|                 |     CDN-1558e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
+-----------------+---------------------------------------------------------------------------+
| 7-Dec-2022      | 1.  Added [api-news.dailyhunt.in](http://api-news.dailyhunt.in) MPE       |
|                 |     -/api/v1/news(1414635) in live monitoring for MPE path                |
|                 |     CDN-1564e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
+-----------------+---------------------------------------------------------------------------+
| 8-dec-2022      | 1.  SQL injection on                                                      |
|                 |     [api-news.dailyhunt.in](http://api-news.dailyhunt.in)                 |
|                 |     CDN-1567e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
|                 |                                                                           |
|                 | 2.  404 spike on api-news story cluster.                                  |
|                 |     CDN-1568e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
|                 |                                                                           |
|                 | 3.  5xx on [api-news.dailyhunt.in](http://api-news.dailyhunt.in)          |
|                 |     CDN-1570e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
|                 |                                                                           |
|                 | 4.  404 on                                                                |
|                 |     [assets-news-bcdn.dailyhunt.in](http://assets-news-bcdn.dailyhunt.in) |
|                 |     CDN-1571e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
+-----------------+---------------------------------------------------------------------------+
| 9-Dec-2022      | 1.  Caching Rule change on qa-dcads and dcads.                            |
|                 |     CDN-1528e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
+-----------------+---------------------------------------------------------------------------+
| 12-Dec-2022     | 1.  Caching rule change on qa-api and stage-api-news.                     |
|                 |     CDN-1563e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
+-----------------+---------------------------------------------------------------------------+
| 13-Dec-2022     | 1.  5xx on [api-news.dailyhunt.in](http://api-news.dailyhunt.in)          |
|                 |     CDN-1597e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
|                 |                                                                           |
|                 | 2.  400 on                                                                |
|                 |     [assets-news-bcdn.dailyhunt.in](http://assets-news-bcdn.dailyhunt.in) |
|                 |     CDN-1595e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
|                 |                                                                           |
|                 | 3.  5xx on [data.dailyhunt.in](http://data.dailyhunt.in)                  |
|                 |     CDN-1601e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
+-----------------+---------------------------------------------------------------------------+
| 14-Dec-2022     | 1.  Moved DS2 logs from S3 to GCS for                                     |
|                 |     [abof.myjosh.in](http://abof.myjosh.in)                               |
|                 |     CDN-1606e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
|                 |                                                                           |
|                 | 2.  5xx on [data.dailyhunt.in](http://data.dailyhunt.in)                  |
|                 |     CDN-1607e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
|                 |                                                                           |
|                 | 3.  DNS update for Network LB traffic migration activity.                 |
|                 |     CDN-1603e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
+-----------------+---------------------------------------------------------------------------+
| 15-Dec-2022     | 1.  4xx on api-proxy. CDN-1611e55da6ef-1840-3475-9293-310ba48d502dSystem  |
|                 |     JIRA                                                                  |
|                 |                                                                           |
|                 | 2.  5xx on [feed.coolfie.io](http://feed.coolfie.io).                     |
|                 |                                                                           |
|                 | 3.  Increase in 4xx on PV-VOD.                                            |
|                 |     CDN-1613e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
|                 |                                                                           |
|                 | 4.  Josh-VOD traffic further going down.                                  |
|                 |                                                                           |
|                 | 5.  5xx on [data.dailyhunt.in](http://data.dailyhunt.in). Problem in one  |
|                 |     of the Akamai server.                                                 |
|                 |     CDN-1607e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
|                 |                                                                           |
|                 | 6.  Akamai Netstorage for [newshunt.com](http://newshunt.com) assets      |
|                 |     CDN-1516e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
+-----------------+---------------------------------------------------------------------------+
| 16-Dec-2022     | 1.  5xx on [data.dailyhunt.in](http://data.dailyhunt.in) due to crunch in |
|                 |     instances. They are further increasing the no. of instance.           |
|                 |                                                                           |
|                 | 2.  5xx on feed.coolfie.io                                                |
|                 |                                                                           |
|                 | 3.  503 on api-news.dailyhunt.in                                          |
|                 |                                                                           |
|                 | 4.  A small spike in origin traffic for stream.coolfie.io.josh. Checked   |
|                 |     with Ankit and it is expected.                                        |
|                 |                                                                           |
|                 | 5.  5xx on [data.dailyhunt.in](http://data.dailyhunt.in) due to BSNL ISP  |
|                 |     level issue from Akamai side.                                         |
|                 |                                                                           |
|                 | 6.  Visionular transcoding went live on 16th                              |
|                 |                                                                           |
|                 |     on h.265 so we can expect a drop in usage on joshvod from dec 17th.   |
+-----------------+---------------------------------------------------------------------------+
| 19-Dec-2022     | - Rule change on [api-news.dailyhunt.in](http://api-news.dailyhunt.in).   |
|                 |   CDN-1630e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                 |
|                 |                                                                           |
|                 | - Receiving less logs in DS2 since Dec 18th.                              |
|                 |   CDN-1632e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                 |
|                 |                                                                           |
|                 | - TTL change from 1 min to 5 min for                                      |
|                 |   [cache-api.myjosh.in](http://cache-api.myjosh.in).                      |
|                 |   CDN-1636e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA                 |
|                 |                                                                           |
|                 | - 5xx on api-news.dailyhunt.in.                                           |
|                 |                                                                           |
|                 | - 5xx on [data.dailyhunt.in](http://data.dailyhunt.in) due to same BSNL   |
|                 |   cluster issue.                                                          |
|                 |                                                                           |
|                 | - Origin TAT and reconnect changes completed for below domains:           |
|                 |                                                                           |
|                 |   - [bcdn.newshunt.com](http://bcdn.newshunt.com) v32                     |
|                 |     \[Logging Origin TAT\]                                                |
|                 |                                                                           |
|                 |   - [api.newshuntads.com](http://api.newshuntads.com) v48                 |
|                 |     \[Logging Origin TAT\]                                                |
|                 |                                                                           |
|                 |   - [samsung.dailyhunt.in](http://samsung.dailyhunt.in) v24               |
|                 |     \[Logging Origin TAT\]                                                |
|                 |                                                                           |
|                 |   - [newshunt.com](http://newshunt.com) v57 \[Logging Origin TAT+         |
|                 |     Reconnect\]                                                           |
|                 |                                                                           |
|                 |   - [ads.newshunt.in](http://ads.newshunt.in) v9 \[Logging Origin TAT +   |
|                 |     Reconnect\]                                                           |
+-----------------+---------------------------------------------------------------------------+
| 20-Dec-2022     | 1.  5xx on                                                                |
|                 |     [assets-news-bcdn.dailyhunt.in](http://assets-news-bcdn.dailyhunt.in) |
|                 |     due to NFS mount went to hung state and nodes were                    |
|                 |     down.CDN-1642e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA          |
|                 |                                                                           |
|                 | 2.  5xx on data.dailyhunt.in                                              |
|                 |                                                                           |
|                 | 3.  Visionular transcoding went live on 20th 100%                         |
+-----------------+---------------------------------------------------------------------------+
| 21-Dec-2022     | 1.  403 on stream josh.                                                   |
|                 |     CDN-1649e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA               |
+-----------------+---------------------------------------------------------------------------+
| **22-Dec-2022** | - Origin TAT and reconnect changes completed for Verse domains as phase 2 |
|                 |   deployment:                                                             |
|                 |                                                                           |
|                 |   - [feed.myjosh.in](http://feed.myjosh.in) v11                           |
|                 |                                                                           |
|                 |   - [share.myjosh.in](http://share.myjosh.in) v47                         |
|                 |                                                                           |
|                 |   - [gateway.myjosh.in](http://gateway.myjosh.in) v12                     |
|                 |                                                                           |
|                 |   - [data.myjosh.in](http://data.myjosh.in) v11                           |
+-----------------+---------------------------------------------------------------------------+
|                 |                                                                           |
+-----------------+---------------------------------------------------------------------------+
|                 |                                                                           |
+-----------------+---------------------------------------------------------------------------+
|                 |                                                                           |
+-----------------+---------------------------------------------------------------------------+
