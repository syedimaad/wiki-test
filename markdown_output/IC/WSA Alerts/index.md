+-------------------+-----------------+-----------------+-----------------+
| **Configuration** | **Policy**      | **Deny Action** | **Alert         |
|                   |                 |                 | Action**        |
+-------------------+-----------------+-----------------+-----------------+
| **New Eterno      | Ads and         | - WAF: Deny     |                 |
| MSC**             | Webstories      |   spike on Ads  |                 |
|                   |                 |   and           |                 |
|                   |                 |   Webstories    |                 |
|                   |                 |                 |                 |
|                   |                 | - DOS: Deny     |                 |
|                   |                 |   spike on Ads  |                 |
|                   |                 |   and           |                 |
|                   |                 |   Webstories    |                 |
|                   +-----------------+-----------------+-----------------+
|                   | Poll-UGC-WAP    | - WAF: Deny     |                 |
|                   |                 |   spike on      |                 |
|                   |                 |   Poll-UGC-WAP  |                 |
|                   |                 |                 |                 |
|                   |                 | - DOS: Deny     |                 |
|                   |                 |   spike on      |                 |
|                   |                 |   Poll-UGC-WAP  |                 |
+-------------------+-----------------+-----------------+-----------------+
