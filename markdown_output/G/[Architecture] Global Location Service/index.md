# Aim

The aim of the document is to capture the architecture of Global
Location Service. Captures rationale behind taking decision w.r.t it
along with data-backed tradeoffs

# Requirements

1.  Location service should support location resolution based on geo
    locations, cell towers, and IP based.

2.  Location service currently handles 2000 RPS and as we move Global
    this will increase.

3.  Location service is at the hot code pass hence needs to be highly
    available, consistent, and should be a low latency system

4.  Location Ids are being used at multiple places in Content, location
    feed, Ads, Daedalus, etc. Hence, we need to make sure of backward
    compatibility

5.  As we move geographies Location service should quickly adapt to it
    and provide a seamless experience to its clients (App BE, Ads BE,
    Daedalus, etc)

6.  Follow a standardized approach to the Global Hierarchy of locations
    and make it functionally scalable

# Architecture components wise

# Highlights

## Pelias

**Link**:
[https://pelias.io](https://pelias.io){card-appearance="inline"}

- Pelias is backed by an elastic search which has a response time of
  around 100ms

- Pelias supports location detection at much granularity till the venue
  as well. However, as we go more gradually accuracy becomes a function
  of how accurately data is curated.

## Capacity Estimates and Constraints

- Top 100,000 Lat long combinations contribute to around 99% of the
  traffic

- Location data for all the latitude and longitude combinations for
  India is around 7 GB

- TTL can be figured smartly using data. Extracted the data using window
  functions to come up with a TTL of 15 Days. Since location data is
  constant this can be handy

## Local Cache

- We are optimizing the storage cost by shortening the keys of JSON
  while storing in the cache. This reduced the cache requirements by 35%

- We are having a 2-level TTL. One of 15 days another of 14 days. Cache
  gets updated in the background when 14 days have passed. This way we
  can avoid calling Pelias during real requests. We used Hue to come up
  with this number using `Window functions`

- We would be relying on the NFS cache to replicate the cache during
  autoscale. We first want to measure the miss rate and prefer to take a
  call on this strategy based on that. We are thinking of a better way
  for this but are waiting to get some real-time feedback first

# Challenges

1.  Disputed regions territory. Being solved using a wrapper on top of
    service response.

2.  IP location accuracy is correlated to MaxMind database accuracy. We
    need to build heuristics around it to come to a confidence score.
    This has an impact on the content recommendation as well.

3.  Smooth onboarding of the clients (App backend, AdEngine, Daedalus,
    Reco) as it is at Hot code path of location feed and Location
    targeting is of high importance.
