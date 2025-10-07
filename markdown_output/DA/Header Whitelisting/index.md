[Original
Post](https://docs.google.com/document/d/1mXPgYkP-LK0xQ3GqZ46Jl6UySjfyCi-a4v5xfecHNLU/edit#heading=h.gcuir86bakkh)\

Header whitelisting is a feature to filter (keep/remove) some headers
that are not required for certain hosts/domains/subdomains.

[Note]{.underline}: *[Whitelisting]{.underline} is used for whitelisting
headers per matching domain/subdomain/*host-suffix *among the group of
modifiable headers (i.e. Request URL is matched again these headers). In
simple words, only headers that are marked in configuration for
whitelisting will be filtered (Kept or removed) on the basis of
domain/subdomain/*host-suffix *to header configured mapping.*

## [Why Need this?]{.underline}

Header whitelisting helps in the management of headers sent by the
application which has the benefit of reducing header payload and
reducing security risk.

## [How does it work?]{.underline}

Header whitelisting depends on a versioned API to fetch the required
configuration. This configuration allows filtering headers.

## [Is there any default configuration for cases when the application/ process is started but version API is yet to be called?]{.underline}

In order to prevent filtering the header, we haven't made any preload
configuration for the same. Thus, Header whitelisting will only be
enabled once the version API is configured.

##  [How to configure header whitelisting? What does configuration look like?]{.underline}

[Sample Api Endpoint:]{.underline}
[[https://qa-news.newshunt.com/api/v2/upgrade/dynamic/version?entity=WHITE_LISTED_HEADERS&version=]{.underline}](https://qa-news.newshunt.com/api/v2/upgrade/dynamic/version?entity=WHITE_LISTED_HEADERS&version=)

[Parameters:]{.underline}\
[entity]{.underline}: Static key for this versioned api\
[version]{.underline}: Local saved existing version for this
configuration or empty

[Sample Response:]{.underline}

json{ \"code\": 200, \"data\": { \"version\": \"2\",
\"whiteListedHeadersPerDomain\": { \"dailyhunt.in \": \[ \"dhdc\",
\"dhsc\", \"dhfdc\", \"dhdl\" \], \".in\": \[ \"dhsc\" \], \".com\": \[
\"dhdl\" \] }, \"modifiableHeaders\": \[ \"dhdc\", \"dhsc\", \"dhfdc\",
\"dhdl\" \] } }

## [How to read the configuration?]{.underline}

In the above .json sample response, a successful response body data
contains the following keys e.g. [version]{.underline},
[whiteListedHeadersPerDomain]{.underline} and
[modifiableHeaders]{.underline}. 

[version]{.underline}: Current version of configuration obtained from
server/ backend.

[modificableHeaders]{.underline}: Headers that are marked to keep or
remove. The header value present in this key is used in
domain/subdomain/host-suffix to header configured mapping.

[whiteListedHeadersPerDomain]{.underline}: Domain/subdomain/host-suffix
to header mapping. This map contains the **[end text]{.underline}** of
the domain which can be applied to subgroups as well. Also, please note
the order of this domain to the header map is important as well.

##  [How end text filtering is applied via whiteListedHeadersPerDomain configuration?]{.underline}

As we know, ordering in configuration is important. This is done along
with end text filtering to group similar sets of subdomains or
substrings into a single map. Eg.

- Use [.in]{.underline} / [.com]{.underline} for all **.in** / **.com**
  top-level domains/subdomains ending with the same.

- Use `dailyhunt.in` for all `abc.xyz.dailyhunt.in`

- From
  [https://evp.atlassian.net/wiki/spaces/DA/pages/422641665/27.5.x+Ad+Mon-release-notes](https://evp.atlassian.net/wiki/spaces/DA/pages/422641665/27.5.x+Ad+Mon-release-notes){card-appearance="inline"}
  onwards, we will update the matching logic to fix the end matching
  logic. Today, [bc.com](http://bc.com) will match
  [abc.com](http://abc.com) which is not correct. Only exact match or
  subdomains need to be match for particular host i.e.
  [xyz.bc.com](http://xyz.bc.com) and [abc.bc.com](http://abc.bc.com)
  instead of [xyzbc.com](http://xyzbc.com) or [abc.com](http://abc.com).
  \[<https://chat.google.com/room/AAAAhnuzexw/smNQ-LdQCzI/smNQ-LdQCzI?cls=10>\]

## [How modificableHeaders is used in header whitelisting?]{.underline}

As documented earlier [modificableHeaders]{.underline} contains all the
headers in action on which filter (keep or remove logic is applied).
Thus, [whiteListedHeadersPerDomain]{.underline} mapping logic will only
be applied to the headers present in [modificableHeaders.]{.underline}

##  [Does this mean any header which is not present in the modificableHeaders will be sent?]{.underline}

Yes, this is true. Only headers present in
[modificableHeaders]{.underline} are in action. Thus, If anything is not
present in [modificableHeaders]{.underline} will be sent automatically.

##  [What if whiteListedHeadersPerDomain is empty?]{.underline}

As per the logic, all the requests will filter/ remove all the headers
present in [modificableHeaders]{.underline}.

## [If the modificableHeaders and whiteListedHeadersPerDomain maps contain the same header. Does that mean this header will be available for all the matching hosts mentioned in whiteListedHeadersPerDomain?]{.underline}

[modificableHeaders]{.underline} specifies keep and remove rules. Thus,
it doesn't guarantee that if something is mentioned in
[modificableHeaders]{.underline} will be available in matching
[whiteListedHeadersPerDomain.]{.underline} That is
[modificableHeaders]{.underline} are used to decide whether to keep or
remove the header - not ***\'add\'*** any header if not already present
in the request.

## [What if there is a mapping of a domain suffix key to an empty dataset or no headers are present for a certain domain suffix key in whiteListedHeadersPerDomain?]{.underline}

As per the logic, all the requests with domain suffix match will not
send the headers present in [modificableHeaders]{.underline}.

## [What if the whiteListedHeadersPerDomain map contains a header but it is not defined in modificableHeaders?]{.underline}

Headers that are not defined in [modificableHeaders]{.underline} will be
sent automatically. Thus, it is important to configure
[modificableHeaders]{.underline} before updating
[whiteListedHeadersPerDomain]{.underline} mapping.

## [Why ordering in whiteListedHeadersPerDomain is important?]{.underline}

It is important to apply the same configuration to multiple subdomains.
In order to achieve this, ordering is important. Anything which comes
first in [whiteListedHeadersPerDomain]{.underline} will be matched
(end-suffix-matched) first for any request's host address.

## [Understanding a sample configuration]{.underline}

Let\'s review the below sample response

json{ \"code\": 200, \"data\": { \"version\": \"2\",
\"whiteListedHeadersPerDomain\": { \"dailyhunt.in \": \[ \"dhdc\",
\"dhsc\", \"dhfdc\", \"dhdl\" \], \".in\": \[ \"dhsc\" \], \".com\": \[
\"dhdl\" \] }, \"modifiableHeaders\": \[ \"dhdc\", \"dhsc\", \"dhfdc\",
\"dhdl\" \], \"orderedDomains\": \[ \"dailyhunt.in \", \".in\", \".com\"
\], \"omitHeaders\": { \"data.dailyhunt.in\": \[ \"Cookie\" \] } } }

In the above response, the modifiable headers are *dhdc*, *dhsc*,
*dhfdc* and *dhdl* which means only these headers will be part of the
filtering logic. All the other headers which are not mentioned here will
be sent automatically.

If we review [whiteListedHeadersPerDomain]{.underline} mapping. Ordering
will take action and the request host address will be matched against
with end suffix entries i.e. [dailyhunt.in](http://dailyhunt.in) then
**.in** and finally **.com**

Here, all the dailyhunt.in will contain all modifiable headers (
\"*dhdc*\", \"*dhsc*\", \"*dhfdc*\", \"*dhdl*\"). However .in and .com
will contain only "*dhsc*" and "*dhdl*" respectively. Also, for other
domains which are not mapped here e.g. .net will filter or remove all
modifiable headers ( \"*dhdc*\", \"*dhsc*\", \"*dhfdc*\", \"*dhdl*\")

Demo:
[https://drive.google.com/file/d/11gQBXPfBa6aUg3WcScVMbHvuAgxOlS0j/view?usp=share_link](https://drive.google.com/file/d/11gQBXPfBa6aUg3WcScVMbHvuAgxOlS0j/view?usp=share_link){card-appearance="inline"}

## [How to reset the existing saved configuration?]{.underline}

Clearing [modifiableHeaders]{.underline} in the version API is enough to
reset the configuration to default (i.e. send all headers).

##  Change logs

\
DHANDROID-113e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA
