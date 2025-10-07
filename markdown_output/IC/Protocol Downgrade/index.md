Given that we have opted to proceed with the implementation of full
HTTPS traffic for [api-news.dailyhunt.in](http://api-news.dailyhunt.in),
certain adjustments need to be made within the Akamai platform. These
modifications are aimed at preventing the need for extra expenses
associated with provisioning new infrastructure to accommodate HTTPS
traffic. The overarching strategy involves managing all HTTPS
connections from the client through the CDN. Subsequently, the CDN will
be responsible for forwarding requests to the origin server, with the
communication between the CDN and the origin occurring exclusively over
HTTP

The decision is founded upon the anticipation of upcoming events and the
projected surges in traffic that are foreseen for that period. The
forthcoming adjustments within the Akamai platforms have the following:

1.  Deployment of the Akamai network to facilitate protocol downgrade
    and elevate the presence of Akamai Points of Presence (PoPs) across
    the network. This phase of implementation is estimated to span over
    a duration of 10 days.

2.  Implementation of a URL pattern hashing mechanism to impliment
    protocol downgrade for specific URL patterns. A gradual transition
    of all URLs to function over HTTP will also be executed, and this
    phase is anticipated to be completed within 7 days.

**[Benefits ]{.underline}**

1.  Load Balancer will only receive HTTP requests from CDN after the
    change reducing the secure communication overhead.

2.  Akamai cache keys will be shared for both HTTP and HTTPs
    requests.(less origin request to generate multiple cache key)

3.  Size of the request will be reduced and compute to process the
    request will be reduced 

**Steps for  implementation **

1.  Config set-up to support ETLS to STLS migration logic. (Protocol
    Downgrade only works on STLS network, Akamai internal naming for
    their networks).

2.  We need to set up the GTM property to enable the shifting of traffic
    between ETLS to STLS.

3.  Initially, we will roll out STLS to 1% of the traffic and monitor
    its performance closely.

4.  We will gradually increase the STLS rollout in increments,
    progressively moving closer to 100% of the traffic.

5.  Once we have reached 100% on STLS, we will remove GTM and point
    directly.

6.  We will have to change the Network Endpoint Group for
    [api-news-dailyhunt-in-akamai](https://console.cloud.google.com/net-services/loadbalancing/advanced/backendServices/details/api-news-dailyhunt-in-akamai?project=et-gcp-cdn&organizationId=502619609313)
    on GCP(for fallback ip).

7.  We will decommission the ETLS slots.

8.  Additionally, we need to perform cleanup tasks on the migration
    metadata, ensuring that everything is in order. We will then
    activate the api-news protocol downgrade feature version for
    production.

9.  During the traffic shift from ETLS to STLS, the number of
    connections will be increased compared to current numbers.

**[Monitoring the activity]{.underline}**

1.  We are implementing a **custom header** in Akamai to distinguish
    between traffic flowing through the STLS or ETLS network. This
    custom header will help us identify the network through which the
    traffic is passing.

2.  Once we modify the metadata on the property, we can utilize the
    **Event Center** and Akamai custom header to monitor the changes.
    This will enable us to track and analyze the impact of the
    modifications made.

3.  Upon completing the setup of the GTM (Global Traffic Management), we
    can monitor the changes by leveraging GTM metrics and the custom
    header. These metrics will provide valuable insights into the
    performance and behavior of the traffic.

    1.  GTM Property Report

        1.  \% DNS Requests per Traffic Target

        2.  DNS Requests per Second, per Traffic Target

4.  After the completion of the protocol downgrade, we can rely on
    Akamai Protocol metrics and Origin-side metrics to validate that the
    origin is only receiving HTTP requests. This validation ensures that
    the desired protocol downgrade has been successfully implemented.

    1.  Traffic Report by Akamai

        1.  Traffic by HTTP version

        2.  Edge hits/sec by HTTP version

        3.  To monitor Error rates, we have Edge/Origin hits/sec by
            response class

        4.  On Grafana, we do have specific dashboard to validate the
            change from origin side.

5.  Currently, the offload percentage for
    [api-news.dailyhunt.in](http://api-news.dailyhunt.in) stands at 79%.
    This indicates that a significant portion of the traffic is being
    offloaded to Akamai servers, reducing the load on the origin server.

6.  Additionally, the average latency for
    [api-news.dailyhunt.in](http://api-news.dailyhunt.in) is as
    follows: 

    1.  p95: 10.8 seconds (480K)

    2.  p90: 10.4 seconds (1.1M)

    3.  p85: 9.3 seconds (1.7M)

    4.  p75: 8.2 seconds (6.6M)

    5.  p50: 5.4 seconds (15M)

    6.  p25: 2.7 seconds (35M)

    7.  p10: 1 second (753M)

\*\*

Protocol downgrade is not recommended practice. We are doing now to
control cost on origin. Benefits added here by compromising the end to
end secure path.
