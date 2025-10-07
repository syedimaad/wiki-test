+-------------------+----------------+--------------------------------------+-----------------------------------------------+
| **Domain**        | **Response     | **Error String**                     | **Causing factor**                            |
|                   | code**         |                                      |                                               |
+-------------------+----------------+--------------------------------------+-----------------------------------------------+
| data.dailyhunt.in | 0xx            | ERR_CLIENT_ABORT\|clientReadPostBody | Error message                                 |
|                   |                |                                      | \"ERR_CLIENT_ABORT\|clientReadPostBody\"      |
|                   |                |                                      | occurs mainly when the Akamai Server keeps    |
|                   |                |                                      | waiting for the POST body from the client.    |
|                   |                |                                      | When the timeout value is reached and still   |
|                   |                |                                      | no request body is received, the connection   |
|                   |                |                                      | is terminated with this error message.        |
|                   |                |                                      |                                               |
|                   |                |                                      | isMidgress = 0                                |
|                   |                |                                      |                                               |
|                   |                |                                      | Reference:                                    |
|                   |                |                                      | [data.dailyhunt.in](http://data.dailyhunt.in) |
|                   |                |                                      | v40 has Read Timeout set as 200 sec so Akamai |
|                   |                |                                      | edge will wait for 200sec to receive a POST   |
|                   |                |                                      | body from Client. In this case, Origin hit    |
|                   |                |                                      | would be false.                               |
+-------------------+----------------+--------------------------------------+-----------------------------------------------+
| data.dailyhunt.in | 503            | ERR_FRP_DENIED\|fwdFRPDeny           | This error indicates there is an issue going  |
|                   |                |                                      | on with the customer\'s origin or ghost to    |
|                   |                |                                      | ghost which has triggered the ghost Forward   |
|                   |                |                                      | Robustness Protection Feature. This feature   |
|                   |                |                                      | operates on each ghost and is showing that    |
|                   |                |                                      | ghost has reached a high number of            |
|                   |                |                                      | connections to this origin or a peer and is   |
|                   |                |                                      | limiting any additional connections to the    |
|                   |                |                                      | origin and it is done on a per hostname basis |
|                   |                |                                      | (not IP like OHD would). At the time of the   |
|                   |                |                                      | issue, additional connections to ghost will   |
|                   |                |                                      | likely fail, and impact ghost itself which is |
|                   |                |                                      | why ghost has decided to stop additional      |
|                   |                |                                      | connections. Once the number of connections   |
|                   |                |                                      | has reduced and the number of connection/read |
|                   |                |                                      | timeouts have subsided, new connections will  |
|                   |                |                                      | resume.                                       |
+-------------------+----------------+--------------------------------------+-----------------------------------------------+
