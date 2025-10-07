  --------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Document Status**   READYGreen
  **Collaborators**     
  **jira**              DHANDROID-81e55da6ef-1840-3475-9293-310ba48d502dSystem Jira
  **protocol**          [https://evp.atlassian.net/wiki/spaces/NEWSBE/pages/423264312/Ads+mon+release+protocol+doc#RTT-instrumentation](https://evp.atlassian.net/wiki/spaces/NEWSBE/pages/423264312/Ads+mon+release+protocol+doc#RTT-instrumentation){card-appearance="inline"}
  --------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

16falselistfalse

------------------------------------------------------------------------

Event definition:
[https://docs.google.com/spreadsheets/d/15JHbmAY4g8-ElUicgqEuZa0v2wRjPehKQ2hbjvLdqJ4/edit#gid=109259055](https://docs.google.com/spreadsheets/d/15JHbmAY4g8-ElUicgqEuZa0v2wRjPehKQ2hbjvLdqJ4/edit#gid=109259055){card-appearance="inline"}

# Configuration:

No config to enable/disable. Below properties will be collected and
passed always

# Instrumentation changes

**Definitions:**

SPV: story_page_view event

SLV: story_list_view event

## 1. new properties to be added by client

+----------------------------------+---------------+------------------------------+-----------------------------------+---------------+
| **name**                         | **description | **applicable events (to be   | **existing events (verification   | **not         |
|                                  | / notes**     | added)**                     | needed)**                         | applicable    |
|                                  |               |                              |                                   | events (no    |
|                                  |               |                              |                                   | change        |
|                                  |               |                              |                                   | needed)**     |
+----------------------------------+---------------+------------------------------+-----------------------------------+---------------+
| time_taken_for_network_operation | RTT seen by   | 1.  SPV(news)                | 1.  SLV (news, tv)                | 1.  SPV(xpr): |
|                                  | the client in |                              |                                   |     no 2nd    |
|                                  | milli sec     | 2.  topic_web_item(news)     |                                   |     chunk     |
|                                  |               |                              |                                   |     fetch is  |
|                                  |               | 3.  SCV                      |                                   |     done      |
+----------------------------------+---------------+------------------------------+-----------------------------------+---------------+
| x_request_id                     | client        | 1.  SLV(news, tv)            | `uniqueId` in                     | \-            |
|                                  | generated     |                              | `dev_socket_timeout_error`,       |               |
|                                  | header being  | 2.  SPV(news) - only for 2nd | `dev_server_request_delay_error`, |               |
|                                  | passed to all |     chunk                    | `dev_server_request_error`        |               |
|                                  | APIs to       |                              |                                   |               |
|                                  | uniquely      | 3.  topic_web_item(news)     |                                   |               |
|                                  | identify an   |                              |                                   |               |
|                                  | API call      | 4.  SCV                      |                                   |               |
+----------------------------------+---------------+------------------------------+-----------------------------------+---------------+
| remote_ip                        | remote socket | 1.  SLV(news, tv)            | 1.  `error_route` in              | \-            |
|                                  | address that  |                              |     `dev_server_request_error`    |               |
|                                  | client        | 2.  SPV(news) - only for 2nd |                                   |               |
|                                  | executed the  |     chunk                    |                                   |               |
|                                  | request on    |                              |                                   |               |
|                                  |               | 3.  topic_web_item(news)     |                                   |               |
|                                  |               |                              |                                   |               |
|                                  |               | 4.  SCV                      |                                   |               |
+----------------------------------+---------------+------------------------------+-----------------------------------+---------------+
| ~~webview_load_time~~            | ~~time        | 1.  ~~SPV(news,xpr)~~        |                                   |               |
|                                  | between app   |                              |                                   |               |
|                                  | loading the   | 2.  ~~topic_web_item(news)~~ |                                   |               |
|                                  | page and      |                              |                                   |               |
|                                  | pageLoaded    |                              |                                   |               |
|                                  | callback from |                              |                                   |               |
|                                  | the webview~~ |                              |                                   |               |
+----------------------------------+---------------+------------------------------+-----------------------------------+---------------+
| api_url                          | url(without   | 1.  SLV(news, tv)            | \-                                | \-            |
|                                  | query params) |                              |                                   |               |
|                                  | from which    | 2.  SPV(news) - only for 2nd |                                   |               |
|                                  | this data is  |     chunk                    |                                   |               |
|                                  | fetched       |                              |                                   |               |
|                                  |               | 3.  topic_web_item(news)     |                                   |               |
|                                  |               |                              |                                   |               |
|                                  |               | 4.  SCV                      |                                   |               |
+----------------------------------+---------------+------------------------------+-----------------------------------+---------------+
| network_service_provider         | vodafone,     | 1.  SLV                      |                                   |               |
|                                  | airtel etc.   |                              |                                   |               |
|                                  |               | 2.  SPV                      |                                   |               |
|                                  |               |                              |                                   |               |
|                                  |               | 3.  topic_web_item           |                                   |               |
|                                  |               |                              |                                   |               |
|                                  |               | 4.  dev\_\*\_error events    |                                   |               |
|                                  |               |                              |                                   |               |
|                                  |               | 5.  SCV                      |                                   |               |
+----------------------------------+---------------+------------------------------+-----------------------------------+---------------+

## 2. new properties to be added by BE through headers

Client looks for certain headers, and if present, will send them in
applicable events.
[https://evp.atlassian.net/wiki/spaces/NEWSBE/pages/423264312/Ads+mon+release+protocol+doc#RTT-instrumentation](https://evp.atlassian.net/wiki/spaces/NEWSBE/pages/423264312/Ads+mon+release+protocol+doc#RTT-instrumentation){card-appearance="inline"}

+----------------------+-----------------------+--------------------------+
| **name**             | **description /       | **applicable events (to  |
|                      | notes**               | be added)**              |
+----------------------+-----------------------+--------------------------+
| response_body_size   | compressed size in    | 1.  SLV(news, tv)        |
|                      | bytes                 |                          |
|                      |                       | 2.  SPV(news) - only for |
|                      |                       |     2nd chunk            |
|                      |                       |                          |
|                      |                       | 3.  topic_web_item(news) |
+----------------------+-----------------------+--------------------------+
| response_header_size | size in bytes         | 1.  SLV(news, tv)        |
|                      |                       |                          |
|                      |                       | 2.  SPV(news) - only for |
|                      |                       |     2nd chunk            |
|                      |                       |                          |
|                      |                       | 3.  topic_web_item(news) |
+----------------------+-----------------------+--------------------------+

## 3. Fields to be added by BE through experiments

+--------------+---------------------------+---------------------------+
| feed_latency | delay in milli sec as     | 1.  SLV(news, tv)         |
|              | seen by the BE            |                           |
|              |                           | 2.  SPV(news) - only for  |
|              |                           |     2nd chunk             |
+--------------+---------------------------+---------------------------+

## 4. Additional notes

**a. Summary for topic_web_item :**\
When client is loading a URL -\> latency params will not be present, as
event is fired by the webpage, and client does not make a BE call)\
When client is loading web content (fetched from API) -\> latency params
will be present for 200 OK response. 204 is error.

**b. Events triggered from web_page:**

If SCV or any other triggered through JS on the webpage - RTT params
will not be present (as client did not make the api call to fetch the
card etc.)

**c. cached content:**

Above properties are not applicable(may/maynot be sent - depending on
whether app got killed after that request completed) ***for events
originating from cached content***.

**d. events triggered by non content (like ads)**
