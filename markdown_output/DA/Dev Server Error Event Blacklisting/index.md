## Problem Statement:

Today, for some scenarios like no-fill Ads, HTTP 204 is served. BE
tracks such response at BE itself and dev_server_request_error is
redundant - it processing, and storage can be avoided.

## Solution:

Client gets `devServerRequestErrorBlacklist` configuration from the
backend to exclude firing events for certain domains.

e.g. In below mentioned sample JSON

- A `204` on `money.dailyhunt.in` or its subdomain will not fire
  dev_server_request error

- A `204/404` on `ads.newshunt.in` or its subdomain will not fire
  dev_server_request error

## Definition of Success

An HTTP response is successful if its status code is in the range \[200,
400) excluding 204.

java private boolean isSuccessful(Response response) { return
response.code() \>= 200 && response.code() \< 400 && response.code() !=
204; }

API Endpoint: `api/v2/upgrade/config`

Sample JSON:

json\"devServerRequestErrorBlacklist\": { \"money.dailyhunt.in\": \[ 204
\], \"ads.newshunt.in\": \[ 204, 404 \] }

## Notes

- For host matching logic, please refer to [Header Whitelisting \| How
  end text filtering is applied via whiteListedHeadersPerDomain
  co\...](https://evp.atlassian.net/wiki/spaces/DA/pages/426672181/Header+Whitelisting#%5BhardBreak%5DHow-end-text-filtering-is-applied-via-whiteListedHeadersPerDomain-configuration%3F)

- BE Protocol:
  [https://evp.atlassian.net/wiki/spaces/NEWSBE/pages/423264312/Ads+mon+release+protocol+doc#Dev-Error-Event-Blacklist](https://evp.atlassian.net/wiki/spaces/NEWSBE/pages/423264312/Ads+mon+release+protocol+doc#Dev-Error-Event-Blacklist){card-appearance="inline"}

- Known use problem: Blacklisted event might get trigger during app
  upgrade (i.e. one from pre feature version). Until config is synched,
  previous config (i.e. no blacklisting) will be honoured.\
  <https://chat.google.com/room/AAAAPFQs0Nk/FnvE69RyNaM/FnvE69RyNaM?cls=10>

## Release wise changes

  ------------------------------------------------------------------------------------------------------------------------------------------------ ----------------- --
  **Release**                                                                                                                                      **summary**       
  [https://evp.atlassian.net/wiki/spaces/DA/pages/422641665](https://evp.atlassian.net/wiki/spaces/DA/pages/422641665){card-appearance="inline"}   initial changes   
                                                                                                                                                                     
  ------------------------------------------------------------------------------------------------------------------------------------------------ ----------------- --

## Future Scope

- For dev error event tracked by news be team, today 204 is considered
  as error when content is not available/ consumed. In case when error
  screen is viewed, we might need to ignore such event. Please note:
  From client perspective it might require some different handling given
  event is being triggered from Interceptor (network layer) while error
  screen viewed happened at UI Layer.

- BE to send `404` whenever they require dev error event to be posted.

- In case BE team send `204` with event blacklist enable for the host,
  we might need to provide url in `errorscreen_viewed` event.\
