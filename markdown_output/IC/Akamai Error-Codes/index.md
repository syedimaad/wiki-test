+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| Error code            | Error name                                    | Reason                                                                                                |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `0.x.x.x`             | `ERR_ACCESS_DENIED|rqacCustom`                | The request was denied by a Web Application Firewall or Bot Manager rule configured, and the rule is  |
|                       |                                               | set to use a custom deny page.                                                                        |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `1.x.x.x`             | `ERR_READ_TIMEOUT`                            | The forward connection to the origin server from the edge server timed out.                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `2.x.x.x`             | `ERR_LIFETIME_EXP`                            | The request\'s lifetime was exceeded.                                                                 |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `3.x.x.x`             | `ERR_READ_ERROR`                              | The TCP connection from the edge server to the origin server was broken before the headers and object |
|                       |                                               | were successfully downloaded. If this happens even though the origin is healthy, you can try lowering |
|                       |                                               | the persistent connection timeout to be lower than origin's setting, or you can try disabling the     |
|                       |                                               | persistent connection feature on the edge server.                                                     |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `4.x.x.x`             | `ERR_WRITE_ERROR`                             | Unable to close the socket to the client. The possible variant of this                                |
|                       |                                               | error `pumpServerCopyComplete` happens when connection is closed by the forward server                |
|                       |                                               | before ​Akamai​ could send the complete request.                                                        |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `5.x.x.x`             | `ERR_SHUTTING_DOWN`                           | The edge server received the shutdown order and is shutting down.                                     |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `6.x.x.x`             | `ERR_CONNECT_FAIL`                            | A connection from an edge server to the origin server timed out. The connection was never             |
|                       |                                               | established.                                                                                          |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `7.x.x.x`             | `ERR_INVALID_REQ`                             | The requested URL is malformed and is not RFC compliant. It can be because it contains invalid HTTP   |
|                       |                                               | headers. If this request uses DRM, check the token.                                                   |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `8.x.x.x`             | `ERR_UNSUP_REQ`                               | Unsupported request.                                                                                  |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `9.x.x.x`             | `ERR_INVALID_URL`                             | The multi-domain config feature did a DNS lookup on the host and it timed out.                        |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `9.x.x.x`             | `ERR_INVALID_URL|invalidurlorhost_mdctimeout` | The requested Host header does not have a corresponding configuration on the network.                 |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `9.x.x.x`             | `ERR_INVALID_URL|invalidurlorhost_mdcdeny`    | The multi-domain config feature could not do a DNS lookup on the host because DNS rate limiting was   |
|                       |                                               | exceeded.                                                                                             |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `9.x.x.x`             | `ERR_INVALID_URL|mdc_deny`                    | The multi-domain config feature was not active in the customer config file.                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `10.x.x.x`            | `ERR_SOCKET_FAILURE`                          | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `11.x.x.x`            | `ERR_DNS_FAIL`                                | The origin server IP address couldn\'t be resolved from the origin hostname.                          |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `12.x.x.x`            | `ERR_CANNOT_FORWARD`                          | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `13.x.x.x`            | `ERR_FORWARDING_DENIED`                       | The request was not sent to the origin server. This is expected with SureRoute test objects, when     |
|                       |                                               | some requests are interrupted by the edge server if the fastest path to the origin has already been   |
|                       |                                               | determined.                                                                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `14.x.x.x`            | `ERR_NO_RELAY`                                | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `15.x.x.x`            | `ERR_ZERO_SIZE_OBJECT`                        | A response from the origin server has zero length.                                                    |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `16.x.x.x`            | `ERR_URN_RESOLVE`                             | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `17.x.x.x`            | `ERR_BAD_DEBUG_COOKIE`                        | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED`                           | The client server was not authorized to access requested object or the origin server.                 |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|SHORT_TOKEN_`              | The token generated is not valid. Check the hdnea query string: *st* parameter should be before the   |
|                       |                                               | request time stamp and the *exp* parameter should be after the\                                       |
|                       |                                               | current timestamp                                                                                     |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|*`                         | A string after the bar character that is not listed here likely means that the denial was based       |
|                       |                                               | on `auth:acl.deny` metadata. The string is the first position in the deny list that caused the        |
|                       |                                               | denial.                                                                                               |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|IG*`                       | The request was blocked due to a Request Control Cloudlet.                                            |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED |bad_cn_match`             | The CN on the certificate didn\'t match the host header.                                              |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|bad_update_url`            | The request from mupdater contained invalid characters.                                               |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|connect_loop`              | The CONNECT method detected a loop.                                                                   |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|es_loading`                | The edge server received an updated edgescape database that is still loading.                         |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|ff_v1arl_nomdt`            | The unsupported version 1 of the ARL detected.                                                        |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|fp_auth_failed`            | Fingerprint authentication failed.                                                                    |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|fwd_acl`                   | Connection to forward host is not allowed because the host is not added in the Allowed Origins.       |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|fwd_acl_ssl`               | Connection to forward host is not allowed because the host is not added in the Allowed Origins.       |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|ipa_amplification`         | A client request was received with the internal edge server header.                                   |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|ipv6-client`               | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|legacy_acl`                | Connection to forward host is not allowed because the host is not added in the Allowed Origins.       |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|loop_*`                    | Loop detected.                                                                                        |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|mdt`                       | Access is denied for this transaction per the metadata configuration.                                 |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|mdt_update_failed`         | Mupdater request failed.                                                                              |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|post_not_allowed`          | POST requests are blocked in the metadata configuration.                                              |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|prefetch_push`             | The edge server received a PREFETCH_PUSH request from a peer, but this type of request was blocked in |
|                       |                                               | the metadata configuration.                                                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|ptk_default-deny-reason`   | The request was blocked by the Client IP. Check Allowed and Blocked lists in the configuration.       |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|purge_*`                   | Purge failed.                                                                                         |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|purge_ipcache_*`           | IP cache purge failed.                                                                                |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|reqmod_*`                  | Request-mod failed.                                                                                   |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|reqsat`                    | Request-sat failed.                                                                                   |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|respmod`                   | Response-mod failed.                                                                                  |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|ssl_port_acl`              | Server refused to go forward to a non-standard origin port.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|store_rebuilding`          | Mupdater request was denied because the store is rebuilding.                                          |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|streamauth*`               | Streamauth was not allowed or failed.                                                                 |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|vr`                        | The request was denied due to limits placed in the configuration for blocking requests when the       |
|                       |                                               | overall traffic goes higher than the configured threshold.                                            |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|waf`                       | The request was denied by the configured Web Application Firewall rules.                              |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|Sec_Serve_Alternate`       | The request was denied by the configured Bot Manager rules.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|china_cdn`                 | Request was denied because it was going to a ChinaCDN machine from outside China.                     |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `18.x.x.x`            | `ERR_ACCESS_DENIED|BotMan_Internal`           | Request was considered as Bot Manager Internal Request and denied potentially due to security config  |
|                       |                                               | misconfiguration.                                                                                     |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `19.x.x.x`            | `ERR_CACHE_ACCESS_DENIED`                     | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `20.x.x.x`            | `ERR_CACHE_MGR_ACCESS_DENIED`                 | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `20.x.x.x`            | `ERR_CACHE_MGR_ACCESS_DENIED`                 | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `24.x.x.x`            | `ERR_REFERER_DENIED`                          | The request was denied based on its Referer.                                                          |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `27.x.x.x`            | `ERR_CLIENT_ABORT|Cancel`                     | The client aborted the request, either before an edge server sent the status line in the HTTP         |
|                       |                                               | response headers (indicated by a 000 response code) or before it finished sending the full object.    |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `29.x.x.x`            | `ERR_FWD_SSL_OUT_OF_HANDSHAKES`               | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `30.x.x.x`            | `ERR_FWD_SSL_HANDSHAKE`                       | The SSL certificate verification failed when connecting to the origin.                                |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `31.x.x.x`            | `ERR_FWD_SSL_BAD_CERT`                        | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `32.x.x.x`            | `ERR_NO_ORIGIN_CLIENT_AUTH`                   | The server didn\'t request a certificate which is opposite to what was set in the metadata.           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `33.x.x.x`            | `ERR_DCA_MAX_POST_SIZE`                       | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `34.x.x.x`            | `ERR_DCA_BAD_WAR_REQ`                         | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `35.x.x.x`            | `ERR_DCA_MAX_WAR_SIZE`                        | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `36.x.x.x`            | `ERR_DCA_MAX_ESI_INCLUDE_SIZE`                | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `37.x.x.x`            | `ERR_DCA_CONTAINER`                           | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `38.x.x.x`            | `ERR_FWD_PCONN_SEC_UPGRADE`                   | The PConn is HTTPS but the client expects HTTP. Check if the metadata is not misconfigured. For       |
|                       |                                               | example, the port doesn\'t match the protocol being used.                                             |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `39.x.x.x`            | `ERR_FWD_PCONN_SEC_DOWNGRADE`                 | The PConn is HTTP but the client expects HTTPS. Check if the metadata is not misconfigured. For       |
|                       |                                               | example, the port doesn\'t match the protocol being used.                                             |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `40.x.x.x`            | `ERR_GHOSTMON_CHK_MSG`                        | This request was a liveness check request generated by an edge server.                                |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `41.x.x.x`            | `ERR_CLIENT_ABORT_SLOW_DNS`                   | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `42.x.x.x`            | `ERR_FWD_SSL_BAD_MDT_CIPHERS`                 | The `ssl:security.ssl.forward-ciphers` is not configured correctly.                                   |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `43.x.x.x`            | `ERR_FWD_SAME_REGION`                         | The edge server attempted to contact its own region as the cache-h parent. After this error, it will  |
|                       |                                               | attempt the next forward server, usually the origin.                                                  |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `44.x.x.x`            | `ERR_DANGEROUS_PORT`                          | The edge server couldn\'t go forward to requested port because it\'s in the `deny-port` list.         |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `45.x.x.x`            | `ERR_FWD_RATE_LIMIT_Q_TIMEOUT`                | This request exceeded its allowed wait time in the queue set by `fwd-rate-limit-queue-max-wait-ms`.   |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `46.x.x.x`            | `ERR_FWD_RATE_LIMIT_Q_FILLED_UP`              | The forward request was evicted from the forward queue. The queue had reached its limit and a request |
|                       |                                               | with higher priority or earlier request-header parse time took its spot.                              |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `47.x.x.x`            | `ERR_FWD_RATE_LIMIT_Q_FULL`                   | The forward request couldn\'t be added to the forward queue because it was full.                      |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `48.x.x.x`            | `ERR_FWD_RATE_LIMIT_HOST_HASH_FULL`           | The forward request couldn\'t be handled because the host hash was full and other hosts were handling |
|                       |                                               | their requests.                                                                                       |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `49.x.x.x`            | `ERR_FWD_RATE_LIMIT_NO_FREE_IPS`              | Forward Rate Limiting failed for this request with an unspecified reason. This error excludes the     |
|                       |                                               | following cases:                                                                                      |
|                       |                                               |                                                                                                       |
|                       |                                               | - This request exceeded its allowed wait time in the queue set by                                     |
|                       |                                               |                                                                                                       |
|                       |                                               | `fwd-rate-limit-queue-max-wait-ms`.                                                                   |
|                       |                                               |                                                                                                       |
|                       |                                               | - The request was evicted from the forward queue because the queue had reached its limit and a        |
|                       |                                               |   request with higher priority or earlier request-header parse time took its spot.                    |
|                       |                                               |                                                                                                       |
|                       |                                               | - The request couldn\'t be added to the forward queue because it was full.                            |
|                       |                                               |                                                                                                       |
|                       |                                               | - The request couldn\'t be handled because the host hash was full and other hosts were handling their |
|                       |                                               |   requests.                                                                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `50.x.x.x`            | `ERR_URL_DIS_AUTH`                            | URL-based edge authorization feature rejected this request.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `51.x.x.x`            | `ERR_NO_CLIENT_CERT`                          | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `52.x.x.x`            | `ERR_INVALID_CLIENT_CERT`                     | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `54.x.x.x`            | `ERR_FWD_CERT_MISSING`                        | The certificate has not yet been loaded. Edge servers with no specified client certificate when it\'s |
|                       |                                               | about to go forward, reject the request with a 403 HTTP status code and log one of the following      |
|                       |                                               | error: `ERR_FWD_CERT_SPEC_MISSING`, `ERR_FWD_CERT_MISSING`, `ERR_FWD_CERT_INACTIVE`,                  |
|                       |                                               | or `ERR_FWD_CERT_INVALID`.                                                                            |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `55.x.x.x`            | `ERR_FWD_CERT_INACTIVE`                       | The certificate\'s `auth.ssl-fwd-certs.status` flag was off. Edge servers with no specified client    |
|                       |                                               | certificate when it\'s about to go forward, reject the request with a 403 HTTP status code and log    |
|                       |                                               | one of the following                                                                                  |
|                       |                                               | error: `ERR_FWD_CERT_SPEC_MISSING`, `ERR_FWD_CERT_MISSING`, `ERR_FWD_CERT_INACTIVE`,                  |
|                       |                                               | or `ERR_FWD_CERT_INVALID`.                                                                            |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `56.x.x.x`            | `ERR_FWD_CERT_INVALID`                        | Strict certificate checking was on and the certificate was invalid.Edge servers with no specified     |
|                       |                                               | client certificate when it\'s about to go forward, reject the request with a 403 HTTP status code and |
|                       |                                               | log one of the following                                                                              |
|                       |                                               | error: `ERR_FWD_CERT_SPEC_MISSING`, `ERR_FWD_CERT_MISSING`, `ERR_FWD_CERT_INACTIVE`,                  |
|                       |                                               | or `ERR_FWD_CERT_INVALID`.                                                                            |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `57.x.x.x`            | `ERR_OCSP_NOT_HTTP_OK`                        | The HTTP response code was not 200 OK.                                                                |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `58.x.x.x`            | `ERR_OCSP_BAD_RESP`                           | Parsing of the DER encoded response failed.                                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `59.x.x.x`            | `ERR_OCSP_BAD_BASICRESP`                      | The `basicResponse` within the OCSP response was either not `id-pkix-ocsp-basic` or it couldn\'t be   |
|                       |                                               | parsed.                                                                                               |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `60.x.x.x`            | `ERR_OCSP_STAT_MALFORMEDREQUEST`              | The responder responded with a `malformedRequest` message indicating that edge server\'s message      |
|                       |                                               | didn\'t conform to the OCSP syntax.                                                                   |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `61.x.x.x`            | `ERR_OCSP_STAT_INTERNALERROR`                 | The responder responded with an `internalError` message indicating that it encountered an internal    |
|                       |                                               | error.                                                                                                |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `62.x.x.x`            | `ERR_OCSP_STAT_TRYLATER`                      | The responder responded with the `tryLater` message indicating that the edge server should retry      |
|                       |                                               | later. Edge serves retry against a secondary responder (if any) or when the user makes another        |
|                       |                                               | request.                                                                                              |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `63.x.x.x`            | `ERR_OCSP_STAT_SIGREQUIRED`                   | The responder responded with a `sigRequired` message indicating that the edge server should sign the  |
|                       |                                               | request. Edge servers don\'t support signing of the request at this point.                            |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `64.x.x.x`            | `ERR_OCSP_STAT_UNAUTHORIZED`                  | The responder responded with the `unauthorized` message indicating that the edge server is not        |
|                       |                                               | authorized to make a query against the given responder.                                               |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `65.x.x.x`            | `ERR_OCSP_STAT_UNKNOWN`                       | The responder responded with a message that the edge server didn\'t understand.                       |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `66.x.x.x`            | `ERR_OCSP_NO_NONCE`                           | The edge server sent a nonce to the responder but the responder didn\'t send a nonce.                 |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `67.x.x.x`            | `ERR_OCSP_BAD_NONCE`                          | The edge server sent a nonce to the responder but the responder sent a different nonce.               |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `68.x.x.x`            | `ERR_OCSP_VERIFY`                             | The verification of the `basicResponse` failed. Check `cache.log` for failure details.                |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `69.x.x.x`            | `ERR_OCSP_CERTID_NOT_IN_RESP1`                | One of the certificate IDs that was in edge server\'s request was not in the OCSP response.           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `70.x.x.x`            | `ERR_OCSP_CERTID_NOT_IN_RESP2`                | One of the certificate IDs that was in edge server\'s request was not in the OCSP response.           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `71.x.x.x`            | `ERR_OCSP_CERT_REVOKED_NOSTATUS`              | The certificate was revoked and the responder didn\'t specify why.                                    |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `72.x.x.x`            | `ERR_OCSP_CERT_REVOKED_UNSPECIFIED`           | The certificate was revoked and the responder specifically stated the reason to be `unspecified`.     |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `73.x.x.x`            | `ERR_OCSP_CERT_REVOKED_KEYCOMPROMISE`         | The certificate was revoked and the responder returned the `keyCompromise` reason code.               |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `74.x.x.x`            | `ERR_OCSP_CERT_REVOKED_CACOMPROMISE`          | The certificate was revoked and the responder returned the `caCompromise` reason code.                |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `75.x.x.x`            | `ERR_OCSP_CERT_REVOKED_AFFILIATIONCHANGED`    | The certificate was revoked and the responder returned the `affilicationChanged` reason code.         |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `76.x.x.x`            | `ERR_OCSP_CERT_REVOKED_SUPERSEDED`            | The certificate was revoked and the responder returned the `superseded` reason code.                  |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `77.x.x.x`            | `ERR_OCSP_CERT_REVOKED_CESSATIONOFOPERATION`  | The certificate was revoked and the responder returned the `cessationOfOperation` reason code.        |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `78.x.x.x`            | `ERR_OCSP_CERT_REVOKED_CERTIFICATEHOLD`       | The certificate was revoked and the responder returned the `certifciateHold` reason code.             |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `79.x.x.x`            | `ERR_OCSP_CERT_REVOKED_REMOVEFROMCRL`         | The certificate was revoked and the responder returned the `removeFromCrl` reason code.               |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `80.x.x.x`            | `ERR_OCSP_CERT_REVOKED_STATUS_UNRECOGN`       | The certificate was revoked and the edge server didn\'t recognize the returned reason code.           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `81.x.x.x`            | `ERR_OCSP_CERT_UNKNOWN`                       | The OCSP responder didn\'t recognize the user\'s certificate. The edge server considers the           |
|                       |                                               | certificate invalid.                                                                                  |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `82.x.x.x`            | `ERR_OCSP_CERT_STATUS_UNRECOGN`               | The edge server didn\'t recognize the certificate status given by the responder. The edge server      |
|                       |                                               | considers the certificate invalid.                                                                    |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `83.x.x.x`            | `ERR_OCSP_THIS_UPD_MISSING`                   | The `this-update` field was missing from the response.                                                |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `84.x.x.x`            | `ERR_OCSP_THIS_UPD_INVALID`                   | The `this-update` field couldn\'t be parsed.                                                          |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `85.x.x.x`            | `ERR_OCSP_THIS_UPD_TOO_OLD`                   | The `this-update` field was too old based on                                                          |
|                       |                                               | the `security.essl.slot-assignment.client-cert. ocsp.responder.this-upd-allowed-past-diff` setting.   |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `86.x.x.x`            | `ERR_OCSP_THIS_UPD_TOO_AHEAD`                 | The `this-update` field was way passed the current time based on                                      |
|                       |                                               | the `security.essl.slot-assignment.client-cert. ocsp.responder.this-upd-allowed-future-diff` setting. |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `87.x.x.x`            | `ERR_OCSP_NEXT_UPD_INVALID`                   | The `next-update` field couldn\'t be parsed.                                                          |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `88.x.x.x`            | `ERR_OCSP_NEXT_UPD_TOO_OLD`                   | The `next-update` field was too old based on                                                          |
|                       |                                               | the `security.essl.slot-assignment.client-cert. ocsp.responder.next-upd-allowed-future-diff` setting. |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `89.x.x.x`            | `ERR_OCSP_NEXT_UPD_TOO_AHEAD`                 | The `next-update` field was way passed the current time based on                                      |
|                       |                                               | the `security.essl.slot-assignment.client-cert. ocsp.responder.next-upd-allowed-future-diff` setting. |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `90.x.x.x`            | `ERR_OCSP_THIS_UPD_AHEAD_OF_NEXT`             | The `this-update` field was ahead of the `next-update` field.                                         |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `91.x.x.x`            | `ERR_OCSP_INTERNAL`                           | An internal error occurred in the edge server while validating the response. Check `cache.log` for    |
|                       |                                               | details.                                                                                              |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `92.x.x.x`            | `ERR_OCSP_NOT_DONE`                           | OCSP processing failed. Check `cache.log` for details.                                                |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `93.x.x.x`            | `ERR_PREFETCH_LIMIT`                          | One of the limits on the number of forward requests based on the Prefetching feature was exceeded.    |
|                       |                                               | The error can apply to edge servers or to the customer.                                               |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `94.x.x.x`            | `ERR_FWD_ENTRY_ABORTED`                       | The forward connection to the origin from the edge server was interrupted.                            |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `95.x.x.x`            | `ERR_CLIENT_READ_TIMEOUT`                     | The edge server timed out waiting for data from the client. This is more likely to be seen on POST    |
|                       |                                               | requests.                                                                                             |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `96.x.x.x`            | `ERR_FWD_HASHED_SERIAL_NO_BACKEND_IP`         | Y-map constructed with hashed serial didn\'t yield a backend IP in the response when resolved. The    |
|                       |                                               | response is usually a VIP. The edge server forwards the request normally either to a cache parent or  |
|                       |                                               | the origin.                                                                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `97.x.x.x`            | `ERR_CONNECT_TIMEOUT`                         | Connection to the origin server from the edge server timed out. The connection was never established. |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `98.x.x.x`            | `ERR_SSL_CONNECT_TIMEOUT`                     | The SSL connection to the origin server from the edge server timed out.                               |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `99.x.x.x`            | `ERR_DNS_TIMEOUT`                             | DNS lookup timeout.                                                                                   |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `100.x.x.x`           | `ERR_SUREROUTE_DNS_FAIL`                      | Akaroute RProxy Marker error. The DNS resolution for a parent came back as 0.0.0.1 or 0.0.0.2.        |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `101.x.x.x`           | `ERR_DNS_IN_REGION`                           | This is not an error and doesn't indicate any failure in transaction. This means that an edge server  |
|                       |                                               | contacted a different server in the same location. When this condition occurs, the edge server simply |
|                       |                                               | goes to the origin server to retrieve the content.                                                    |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `102.x.x.x`           | `ERR_NO_GOOD_FWD_IP`                          | This is triggered by the Origin Health Detect feature. This code means that edge server intentionally |
|                       |                                               | didn\'t go forward to the origin because the origin is flagged as bad due to too many failures in     |
|                       |                                               | retrieving content from it. This feature reduces the load on origin and gives some time for the       |
|                       |                                               | origin to recover. As the origin starts to recover and get healthy, these errors go away.             |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `103.x.x.x`           | `ERR_HTTP_CONNECT_FAIL`                       | The HTTP connect failed.                                                                              |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `106.x.x.x`           | `ERR_RSYNC_OBSOLETE`                          | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `107.x.x.x`           | `ERR_WAR_ABORT`                               | The WAR file was interrupted.                                                                         |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `108.x.x.x`           | `ERR_ESI_BUF_ABORT`                           | ASI buffer copy operation was interrupted, most likely due to the client action.                      |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `109.x.x.x`           | `ERR_ESI_RESP`                                | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `110.x.x.x`           | `ERR_STORE_COPY`                              | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `111.x.x.x`           | `ERR_FP_MISMATCH`                             | Read error happened due to fingerprint mismatch.                                                      |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `112.x.x.x`           | `ERR_GZIP`                                    | Read error happened due to compression.                                                               |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `113.x.x.x`           | `ERR_PARTIAL_FWD_REJECT`                      | Read error happened due to partial forward reject.                                                    |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `114.x.x.x`           | `ERR_QUEUE_MKDIR`                             | Write error happened due to the Mkdir in the client queue code failure.                               |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `115.x.x.x`           | `ERR_QUEUE_FOPEN`                             | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `116.x.x.x`           | `ERR_QUEUE_WRITE`                             | Write error happened due to the `write` file in the client queue code failure.                        |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `117.x.x.x`           | `ERR_QUEUE_POST_TOO_BIG`                      | Write error happened due to too big POST body for the client queue.                                   |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `118.x.x.x`           | `ERR_QUEUE_ENQ`                               | Write error happened due to the enqueuing the current request failure.                                |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `119.x.x.x`           | `ERR_NO_FWD_HOSTS`                            | The edge server was unable to resolve any of the potential forward hostnames (origin or cache         |
|                       |                                               | hierarchy parent or SureRoute parent) to an IP address. This indicates either a DNS problem or a      |
|                       |                                               | problem with the map names being misconfigured or nonexistent.                                        |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `121.x.x.x`           | `ERR_OBJ_OUT_OF_DATE`                         | The response object from origin is out of date.                                                       |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `122.x.x.x`           | `ERR_BAD_CHUNKED_ENC`                         | The origin received bad chunked encoding.                                                             |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `123.x.x.x`           | `ERR_WIN32_READ_ERR`                          | The forward connection to the origin server broke.                                                    |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `124.x.x.x`           | `ERR_GM_SUPPRESSED_ERR`                       | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `125.x.x.x`           | `ERR_SSL_POST_RENEG`                          | SSL client-side session renegotiation was requested under a POST request with the feature being       |
|                       |                                               | turned off.                                                                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `126.x.x.x`           | `ERR_FWD_CONTENT_MD5`                         | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `127.x.x.x`           | `ERR_CLIENT_CONTENT_MD5`                      | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `128.x.x.x`           | `ERR_PURGE_SEQ_OUT_OF_DATE`                   | The forward connection to the origin was interrupted due to a purge sequence number mismatch.         |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `129.x.x.x`           | `ERR_POC_MS_FRAG_SIZE_CHANGED`                | The client connection was interrupted because all of the following cases occurred:                    |
|                       |                                               |                                                                                                       |
|                       |                                               | - The master entry the client was attached to became private, the object got purged or revalidated    |
|                       |                                               |   and the TTL expired.                                                                                |
|                       |                                               |                                                                                                       |
|                       |                                               | - More fragments on behalf of the users attached to the private master had to be downloaded.          |
|                       |                                               |                                                                                                       |
|                       |                                               | - The newly created public master had a different fragment size.                                      |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `130.x.x.x`           | `ERR_POC_MS_POC_OFF`                          | The client connection was interrupted because all of the following cases occurred:                    |
|                       |                                               |                                                                                                       |
|                       |                                               | - The master entry the client was attached to became private, the object got purged or revalidated    |
|                       |                                               |   and the TTL expired.                                                                                |
|                       |                                               |                                                                                                       |
|                       |                                               | - More fragments on behalf of the users attached to the private master had to be downloaded.          |
|                       |                                               |                                                                                                       |
|                       |                                               | - The newly created public StoreEntry was not a POC entry.                                            |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `131.x.x.x`           | `ERR_POC_MS_NO_PUBLIC_ENTRY`                  | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `132.x.x.x`           | `ERR_POC_FWD_NOT_206`                         | The HTTP response code was not 206 Partial Content.                                                   |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `133.x.x.x`           | `ERR_POC_FWD_NO_CONTLEN`                      | The response had no `content-length` header.                                                          |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `134.x.x.x`           | `ERR_POC_FWD_DCA_OUTPUT`                      | `X-Akamai-DCA-Output-Maxage` was present in the response.                                             |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `135.x.x.x`           | `ERR_POC_FWD_GZIPPED`                         | The response was compressed.                                                                          |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `136.x.x.x`           | `ERR_POC_FWD_NO_RANGE`                        | The response had no `content-range` header.                                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `137.x.x.x`           | `ERR_POC_FWD_NO_ELEN`                         | The `entity-length` field was not a specific number in the `content-range` response header.           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `138.x.x.x`           | `ERR_POC_FWD_NO_OFFSET`                       | The content-range header had no beginning offset.                                                     |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `139.x.x.x`           | `ERR_POC_FWD_BAD_RLEN`                        | Unexpected length of the range in the `content-range` response header.                                |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `140.x.x.x`           | `ERR_POC_FWD_LEN_MISMATCH`                    | The `content-length` header didn\'t match the number of bytes given with the `content-range` header.  |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `141.x.x.x`           | `ERR_POC_FWD_OFFSET_MISMATCH`                 | The beginning offset of the `content-range` response header didn\'t match the beginning offset of the |
|                       |                                               | range request header.                                                                                 |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `142.x.x.x`           | `ERR_POC_FWD_MS_NONCH`                        | The response to the initial POC range request indicates the object is not cacheable. Either this      |
|                       |                                               | object is misconfigured on the origin or POC shouldn\'t be applied to it.                             |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `143.x.x.x`           | `ERR_POC_FWD_OBJ_TOO_SMALL`                   | The response object is smaller than what is permitted by the configuration settings.                  |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `144.x.x.x`           | `ERR_POC_FWD_OBJ_TOO_BIG`                     | The response object is larger than what is permitted by the configuration settings.                   |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `145.x.x.x`           | `ERR_POC_FWD_ETAG_NONE`                       | `cache.poc2.trust-etag` is on and there was no ETag in the response.                                  |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `146.x.x.x`           | `ERR_POC_FWD_ETAG_WEAK`                       | `cache.poc2.trust-etag` is on and the ETag in the response was tagged as weak.                        |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `147.x.x.x`           | `ERR_POC_FWD_ETAG_BAD`                        | `cache.poc2.trust-etag` is on and the ETag in the response had a non-HTTP compliant format. The value |
|                       |                                               | has to be surrounded by double quotes with an optional \"W/\" indicating weak ETag.                   |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `148.x.x.x`           | `ERR_POC_FWD_LASTMOD_NONE`                    | `cache:poc2.trust-lastmod` is on and there was no `Last-Modified` header in the response.             |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `149.x.x.x`           | `ERR_POC_FWD_LASTMOD_BAD`                     | `cache:poc2.trust-lastmod` is on and the `Last-Modified` header in the response had an incorrect      |
|                       |                                               | format. On the `f` line, they\'re always printed time when the inconsistent fragment was encountered  |
|                       |                                               | and on the `r` line whether the connection was interrupted. Otherwise, the `r` line have a status     |
|                       |                                               | code indicating that possibly an inconsistent object was served.                                      |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `150.x.x.x`           | `ERR_POC_FWD_OBJ_SIZE_CHANGED`                | The object consistency verification failed because the object size is different on the current master |
|                       |                                               | and a fragment.                                                                                       |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `151.x.x.x`           | `ERR_POC_FWD_ETAG_CHANGED`                    | The object consistency verification failed because the ETag is different on the current master and a  |
|                       |                                               | fragment. This may mean that one of the ETags was either different or badly formatted or the ETag was |
|                       |                                               | missing from one of them.                                                                             |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `152.x.x.x`           | `ERR_POC_FWD_LASTMOD_CHANGED`                 | The object consistency verification failed because the last-modified time is different between on the |
|                       |                                               | current master and a fragment. This may mean that one of the last-modified times was different or     |
|                       |                                               | badly formatted or the last-modified time was missing from one of them.                               |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `153.x.x.x`           | `ERR_POC_FWD_AK_GZIPPED`                      | The response had the `X-Ak-Gzip-Downstream` header indicating that a peer or parent edge server       |
|                       |                                               | compressed the response.                                                                              |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `154.x.x.x`           | `ERR_POC_FWD_TR_ENC`                          | The response was transfer-encoded. The edge server retries with a regular forward request.            |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `155.x.x.x`           | `ERR_POC_FWD_G2G_ABORT`                       | The connection had to be interrupted because the in-coming client is another edge server and the      |
|                       |                                               | origin drops the connection after the response was being received.                                    |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `156.x.x.x`           | `ERR_POC_FWD_CANT_CREATE_MS`                  | Failed to establish a master entry due to some error on the forward side. The master is converted to  |
|                       |                                               | a regular entry with a 503 HTTP status code.                                                          |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `157.x.x.x`           | `ERR_POC_FWD_FRAG_ABORT`                      | Failed to fetch a fragment most likely due to forward server breaking off. Check the `f` line for     |
|                       |                                               | details. The fragment\'s status code is set to 503 in this case. This could also occur when an        |
|                       |                                               | incorrect client range makes it to the forward side of the edge server.                               |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `158.x.x.x`           | `ERR_POC_TC_FP`                               | The request was for a TC 2/3 object and POC2 was on and they are not compatible.                      |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `159.x.x.x`           | `ERR_POC_FWD_ABORT`                           | Failed to fetch a fragment most likely due to forward server breaking off. Check the `f` line for     |
|                       |                                               | details. The fragment\'s status code is set to 503 in this case. This could also occur when an        |
|                       |                                               | incorrect client range makes it to the forward side of the connecting client.                         |
|                       |                                               | If `cache:poc2.hide-forward-errs-from-user` is on, this error won\'t show in the logs.                |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `160.x.x.x`           | `ERR_RAW_ABORT`                               | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `161.x.x.x`           | `ERR_DCA_BAD_ECFILE_REQ`                      | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `162.x.x.x`           | `ERR_OCSP`                                    | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `163.x.x.x`           | `ERR_POC`                                     | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `164.x.x.x`           | `ERR_DRM_ACCESS_DENIED`                       | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `166.x.x.x`           | `ERR_HRS_SPACE_IN_HDR_NAME`                   | Possible request smuggling detected. There was a space in the name of a request header.               |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `167.x.x.x`           | `ERR_HRS_EMPTY_CONTINUATION`                  | Possible request smuggling detected. The header ended in CR/LF and the following line contained only  |
|                       |                                               | spaces.                                                                                               |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `168.x.x.x`           | `ERR_HRS_BARE_CRS_IN_HDR`                     | Possible request smuggling detected. There was a bare carriage returned and space within the headers. |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `169.x.x.x`           | `ERR_HRS_DUP_CONTENT_LEN`                     | Possible request smuggling detected. There was a second `content-length` header in the request.       |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `171.x.x.x`           | `ERR_WM_ACCESS_DENIED`                        | Watermark Authentication failed.                                                                      |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `172.x.x.x`           | `ERR_OBJ_TOO_BIG`                             | The response object is larger than what is permitted by the configuration settings.                   |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `173.x.x.x`           | `ERR_SSL_POST_RENEG_TOO_BIG`                  | SSL client-side session renegotiation was requested under a POST request but the POST body size was   |
|                       |                                               | greater than permitted by the configured settings.                                                    |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `174.x.x.x`           | `ERR_METADATA_APPLY_FAILURE`                  | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `175.x.x.x`           | `ERR_FWD_RESIGNED_CERT`                       | A copy or signing operation failed when trying to resign the client certificate for transfer to the   |
|                       |                                               | origin.                                                                                               |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `176.x.x.x`           | `ERR_SSL_RENEG`                               | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `177.x.x.x`           | `ERR_FLV_SEEK`                                | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `178.x.x.x`           | `ERR_CHUNK_INCOMPLETE`                        | The origin didn\'t send the last chunk of a file using Transfer-Encoding and the connection timed     |
|                       |                                               | out. The edge server assumes that it has received the complete file, but treats it as uncacheable and |
|                       |                                               | logs the error. This behavior is controlled by the metadata.                                          |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `179.x.x.x`           | `ERR_NO_STICKY_PCONN`                         | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `180.x.x.x`           | `ERR_ICP_DEADLOCK_DETECT`                     | The request was from another in-region edge server and the current edge server has a pending forward  |
|                       |                                               | request to that edge server for the same object. This request is rejected since it may result in a    |
|                       |                                               | deadlock.                                                                                             |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `181.x.x.x`           | `STREAMING_BAD_REQUEST`                       | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `182.x.x.x`           | `STREAMING_UNAUTHORIZED`                      | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `183.x.x.x`           | `STREAMING_NOT_FOUND`                         | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `184.x.x.x`           | `ICP_PUBLIC_EARLY_RESPONSE`                   | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `185.x.x.x`           | `STORE_ENTRY_LOOP_DETECT`                     | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `186.x.x.x`           | `ERR_FWD_BAD_HEADERS`                         | InvalidForwardReply: The response headers from the origin or the edge server parent were malformed or |
|                       |                                               | too large. The error occurs when the HTTP response status line is missing or malformed or when the    |
|                       |                                               | origin or parent response headers exceed the size limit. This can often occur                         |
|                       |                                               | if `Pragma: akamai-x-get-extracted-values` was specified in the request to perform debugging, and     |
|                       |                                               | there are a large number of `X-Session-Info response` headers.                                        |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `187.x.x.x`           | `ERR_MP4_SEEK`                                | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `188.x.x.x`           | `ERR_STREAMING_VERIFICATION_FAILED`           | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `189.x.x.x`           | `ERR_SSL_INSECURE_RENEGOTIATION`              | Connection interrupted with `HTTP_FORBIDDEN` because of not secure ESSL client-side renegotiation.    |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `190.x.x.x`           | `ERR_SSL_TLS_SECURITY_EXT`                    | Connection interrupted with `HTTP_FORBIDDEN` because                                                  |
|                       |                                               | of `security:enforce-tls-security-extension.*` on and the TLS secure renegotiation extension not in   |
|                       |                                               | effect.                                                                                               |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `191.x.x.x`           | `ERR_POC_FWD_CONTENT_MD5_CHANGED`             | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `192.x.x.x`           | `ERR_POC_FWD_CONTENT_MD5_NONE`                | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `193.x.x.x`           | `ERR_IPTV_BAD_REQUEST`                        | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `194.x.x.x`           | `ERR_IPTV_NOT_FOUND`                          | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `195.x.x.x`           | `ERR_ADOBE_ERROR`                             | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `196.x.x.x`           | `ERR_UITS_BAD_REQUEST`                        | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `197.x.x.x`           | `ERR_ORIGIN_HOST_LOOP`                        | The origin hostname that the edge server was about to go forward to matches the name in the client    |
|                       |                                               | request Host header indicating a loop in the forward logic. This behavior is controlled by the        |
|                       |                                               | metadata tag `network:dns.rollback-origin-host-loop-check`.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `198.x.x.x`           | `ERR_IPV6_SERVICE_UNAVAILABLE`                | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `199.x.x.x`           | `ERR_AUTH_BROWSER_TOKEN_FAILED`               | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `200.x.x.x`           | `ERR_TRANSFORMING`                            | Connection interrupted. The edge server encountered an error in the midst of transforming content     |
|                       |                                               | after it had already sent at least one byte of data to the client. The message after the \'\|\'       |
|                       |                                               | refines the nature of the error.                                                                      |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `201.x.x.x`           | `ERR_SILVERLIGHT`                             | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `202.x.x.x`           | `ERR_ENCRYPT`                                 | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `203.x.x.x`           | `ERR_FWD_CAE_HEADERS`                         | This error indicates that the response headers from CAE failed the verification and forward request   |
|                       |                                               | were treated as failed.                                                                               |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `204.x.x.x`           | `ERR_TPCA`                                    | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `205.x.x.x`           | `ERR_TRANSFORMATION_POOL`                     | Edge server encountered an error related to the thread pool that performs content transformations.    |
|                       |                                               | There should be currently no way for this error to actually occur. Problems with transformed content  |
|                       |                                               | trigger `ERR_TRANSFORMING` instead, the most important types of which are documented above.           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `208.x.x.x`           | `ERR_STREAMING_BAD_CONNECTION`                | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `209.x.x.x`           | `ERR_SWAPMETA_FAIL`                           | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `210.x.x.x`           | `ERR_BAD_SWAPFILE_APPEND`                     | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `211.x.x.x`           | `ERR_SWAPMETA_PARSE_FAIL`                     | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `212.x.x.x`           | `ERR_GETZIP_PROTOCOL_ERROR`                   | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `213.x.x.x`           | `ERR_P2G_AUTH`                                | Partner Authentication failures. The possible refined error messages for this error currently are:    |
|                       |                                               |                                                                                                       |
|                       |                                               | -                                                                                                     |
|                       |                                               |                                                                                                       |
|                       |                                               | `scc_partnerauth_failed`, when an SCC log line POST is rejected because partner authentication        |
|                       |                                               | failed.                                                                                               |
|                       |                                               |                                                                                                       |
|                       |                                               | -                                                                                                     |
|                       |                                               |                                                                                                       |
|                       |                                               | `scc_partnerauth_notenabled`, when an SCC log line POST is rejected because partner authentication is |
|                       |                                               | not enabled.                                                                                          |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `214.x.x.x`           | `ERR_FWD_STORAGE_BAD_RESPONSE`                | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `215.x.x.x`           | `ERR_HT_FAIL`                                 | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `216.x.x.x`           | `ERR_STREAMING_MULTI`                         | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `217.x.x.x`           | `ERR_OUT_OF_RESOURCES`                        | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `218.x.x.x`           | `ERR_CONTENT_POLICY`                          | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `219.x.x.x`           | `ERR_EPD_ACCESS_DENIED`                       | The request was denied due to the Enhanced Proxy Detection feature. The error should include a        |
|                       |                                               | description explaining the reason of the denial.                                                      |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `220.x.x.x`           | `ERR_PLAYLIST_MODIFICATION`                   | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `221.x.x.x`           | `ERR_FIRST_BYTE_TIMEOUT`                      | Connection to the forward server timed out.                                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `222.x.x.x`           | `ERR_DELEGATOR`                               | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `224.x.x.x`           | `ERR_SSL_HTTP2_NO_RENEGOTIATION`              | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `225.x.x.x`           | `ERR_RESOURCE_INTEGRITY_FAILED`               | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `226.x.x.x`           | `ERR_HTTP2_ERROR`                             | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `227.x.x.x`           | `ERR_INVALID_REQ_NOORIGINMDT`                 | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `228.x.x.x`           | `ERR_WEBSOCKET_READ_TIMEOUT`                  | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `229.x.x.x`           | `ERR_WEBSOCKET_PRUNE`                         | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `230.x.x.x`           | `ERR_COMBINED_STORE`                          | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `231.x.x.x`           | `ERR_HRS_HOST_HEADER_MISMATCH`                | Possible request smuggling detected. There were multiple mismatching host headers or a mismatch       |
|                       |                                               | between the host in the URI and a host header in the request.                                         |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `232.x.x.x`           | `ERR_BROTLI`                                  | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `233.x.x.x`           | `ERR_ERR_NETP`                                | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `234.x.x.x`           | `ERR_MANIFEST_MANIPULATION`                   | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `236.x.x.x`           | `ERR_FRP_DENIED`                              | The forward robustness protection feature is active and it denies a forward request.                  |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `237.x.x.x`           | `ERR_MID_HEADER_ABORT`                        | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `238.x.x.x`           | `ERR_OCSP_CERTID_BAD_ALGO_IN_RESP`            | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `239.x.x.x`           | `ERR_POC_MS_OBJ_SIZE_CHANGED`                 | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `240.x.x.x`           | `ERR_STORE_HTTP_STATUS_NONE`                  | The response had no status code.                                                                      |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `241.x.x.x`           | `ERR_OUTPUT_FILTER_EXCEED_MAX_BUF_SIZE`       | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `242.x.x.x`           | `ERR_GRID_INTEGRITY_CREATE_OBJECT`            | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `243.x.x.x`           | `ERR_POC_INTEG_NO_PUBLIC_ORIG_ENTRY`          | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `244.x.x.x`           | `ERR_GRID_INTEG_POC_NOT_MULTIPLE`             | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `245.x.x.x`           | `ERR_GRID_INTEG_POC_SMALL_FRAG`               | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `246.x.x.x`           | `ERR_POC_FWD_COBRA_FIRSTFRAG_ERROR`           | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `247.x.x.x`           | `ERR_DEVPOPS`                                 | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `248.x.x.x`           | `ERR_MANIFEST_MANIPULATION_MASTER_NO_STREAM`  | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `249.x.x.x`           | `ERR_DCV`                                     | Fast Domain Control Validation encountered an error during the communication with DcvManager.         |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `250.x.x.x`           | `ERR_FWD_CONTENT_SHA256`                      | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `251.x.x.x`           | `ERR_HRS_SPACE_AT_HDR_NAME_START`             | Possible request smuggling detected. There is a space at the start of header name of a request.       |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `252.x.x.x`           | `ERR_HRS_STRICT_MODE_HTTP_HDR_PARSING`        | Request interrupted due to violating the strict mode in HTTP header parsing.                          |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `253.x.x.x`           | `ERR_HRS_UNAMBIGUOUS_MODE_HTTP_HDR_PARSING`   | Request interrupted due to violating unambiguous mode in HTTP header parsing.                         |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `254.x.x.x`           | `ERR_HRS_FOLDED_LINE_ABORT`                   | Request interrupted due to folded line detection in header.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
| `255.x.x.x`           | `GET_FILTERED_OBJ`                            | Internal error. For more details, contact the support team.                                           |
+-----------------------+-----------------------------------------------+-------------------------------------------------------------------------------------------------------+
