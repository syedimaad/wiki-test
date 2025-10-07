URL Protection feature is designed to protect compute heavy URLs/API
endpoints against highly distributed application layer DDoS attacks. It
tracks the request velocity to the origin and enforces global rate
limits to protect such critical resources. This feature provides our
customers a way to set maximum allowed request rate to their origin and
denies excessive requests above allowed Request Per Second rate.
Further, the Intelligent Load Shedding option can be enabled to minimize
real user impact by selectively dropping requests from malicious sources
such as bots, Tor exit nodes etc first.

With this feature, you can:

- Define which resources need to be protected by using Host and path or
  API match criteria.

- Configure the overall maximum request per second (RPS) limit allowed
  to these resources.

- Use Load shedding categories to preselect sources of traffic they want
  to block first as the request rate nears the configured RPS limit.

URL protection is primarily useful when setting an overall limit on the
number of RPS you want to allow to your origin resources through Akamai
CDN. When this limit is breached further requests are denied until
request rate is back under the limits defined. Also Allows traffic
prioritization while RPS nears the maximum rate by blocking clients in
specific categories(low reputation IPs).

This feature is primarily designed to protect specific URLs / API
endpoints that are compute heavy. We do not recommend enabling this for
the entire site/application.

With Intelligent Load Shedding, as the traffic load increases on your
origin, you can select what kind of traffic to deny first in an effort
to prioritize real user traffic before it reaches the maximum RPS limit.
You decide when to start blocking the traffic while setting the URL
Protection rules -- you can specify the percentage of the allowed
request rate or the number of hits per second.

Customers can select from the following client categories:

- Cloud providers -- To block traffic from cloud providers. Currently
  only includes Amazon Web Services and Google Cloud.

- Proxies -- To block traffic from open proxies tracked by Akamai.

- TOR exit nodes

- Basic bots \* -- Leverages the transparent bot detections and browser
  impersonator detections from the Bot Manager product suite.

- Low Reputation IPs \*\* -- To block traffic from clients with a high
  client reputation score for one or more categories.

Note: Basic bots and Low Reputation IPs categories would only work when
respective product features are on the contract and enabled.
