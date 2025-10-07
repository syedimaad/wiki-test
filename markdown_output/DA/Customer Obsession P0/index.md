  -------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Collaborators**    
  **Status**           PUBLISHEDGreen
  **Feature parent**   App DNS handling logic
  **Meeting notes**    [https://docs.google.com/document/d/1W4q64qFnyITdKyo1HmHYMKh4B6xYurTcUfrBeKazEgk/edit](https://docs.google.com/document/d/1W4q64qFnyITdKyo1HmHYMKh4B6xYurTcUfrBeKazEgk/edit){card-appearance="inline"}
  **Protocol**         [https://evp.atlassian.net/wiki/spaces/NEWSBE/pages/482869268/Election+Native+Revamp#dns-API-changes](https://evp.atlassian.net/wiki/spaces/NEWSBE/pages/482869268/Election+Native+Revamp#dns-API-changes){card-appearance="inline"}
  **Jira**             DHANDROID-321e55da6ef-1840-3475-9293-310ba48d502dSystem Jira
  -------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Spec

1.  If an API returns HTTP 403, client already fires
    `dev_server_request_error` event. Pass below additional params

+-----------------------+-----------------------+-----------------------------------+
| **param name**        | **value**             | **Notes**                         |
+-----------------------+-----------------------+-----------------------------------+
| `akmai_x_ref_error`   | - String              | will be `null` if header is not   |
|                       |                       | present                           |
|                       | - read from response  |                                   |
|                       |   header              |                                   |
|                       |   `X-Reference-Error` |                                   |
+-----------------------+-----------------------+-----------------------------------+
| `http_error_body`     | - String              | - size limited by                 |
|                       |                       |   `maxBytesToReadFromHttp403Body` |
|                       | - parsed response     |   BE config                       |
|                       |   body                |                                   |
|                       |                       | - will be `null` if body is not   |
|                       |                       |   present, or if there is a       |
|                       |                       |   parsing issue                   |
+-----------------------+-----------------------+-----------------------------------+

2\. When doing dns lookup when app is in background, **make Step#1
optional**. BE config`skip1stLevelCacheForBgLookup` controls this.

note

Note: **Step#1** is - if present in 1st_level_cache, return immediately
and do bg-lookup

:::: {.panel .conf-macro .output-block style="background-color: rgb(234,230,255);border-color: rgb(153,141,217);border-width: 1.0px;"}
::: {.panelContent style="background-color: rgb(234,230,255);"}
Note: **Step#1** is - if present in 1st_level_cache, return immediately
and do bg-lookup
:::
::::

3\. Pick `x-e-org` header from the error response and send it in RTT
instrumentation changes for 27.5.x release events and
`dev_server_request error` events.

Param name = `x_e_org`
