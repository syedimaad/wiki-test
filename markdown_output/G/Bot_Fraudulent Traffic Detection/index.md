### Common Methods to detect

- Using databases to check if IP has been used by bot or not

  - MaxMind Database

  - Project Honeypot

  - AbuseIPDB (Free)

- Checking ASN of the IP if it belongs to a cloud service provider

  - MaxMind Database provides this

- Geo IP Anomalies

  - Frequent changes in city/state/country

- High number of IP requests per second

- Many sessions coming from the **same IP or /24 subnet**.

- Some bots leak **proxy headers** (like `X-Forwarded-For`, `Via`) or
  non-standard ports.

- Anomalous ports (e.g., not 443 or 80) can indicate botnets or custom
  tools.

- Various other paid APIs provide services included

  - **IP2Proxy**

  - CloudFlare

  - IPQS

  - DataDome

### ML Training Feature Set Sample

- Features from MMDB

  ------------------------ ---------- -----------------------------------------------------
  Feature Name             Type       Description
  `ip_address`             string     Raw IP (used only for mapping, not in training)
  `ip_reputation_score`    numeric    From AbuseIPDB, Project Honey Pot, etc. (0--100)
  `asn`                    category   Autonomous system number (ISP identity)
  `is_datacenter`          boolean    IP from cloud/data center (AWS, GCP, Hetzner, etc.)
  `country_code`           category   Country of IP address
  `request_rate_per_min`   numeric    Total requests from IP per minute
  `distinct_user_agents`   numeric    Number of unique UAs from IP over time window
  ------------------------ ---------- -----------------------------------------------------

- request features

  ------------------------- ---------- ---------------------------------------
  Feature Name              Type       Description
  `hour_of_day`             numeric    Request hour (0--23)
  `weekday`                 category   Day of week
  `burst_requests_in_10s`   numeric    Number of requests in last 10s
  `first_seen_timestamp`    datetime   Timestamp of IP or session first seen
  `last_seen_timestamp`     datetime   Timestamp of latest activity
  ------------------------- ---------- ---------------------------------------

- behaviour features

  ------------------------- --------- ------------------------------------------------
  Feature Name              Type      Description
  `click_interval_mean`     numeric   Average time between user clicks
  `mouse_movements_count`   numeric   Number of mouse movements (if captured via JS)
  `scroll_events_count`     numeric   Number of scroll events
  `form_fills`              numeric   Forms filled on page (0 = suspicious)
  `time_on_page`            numeric   Time spent on page/session
  `pages_visited`           numeric   Number of unique pages visited
  ------------------------- --------- ------------------------------------------------

### Frequency of training the ML model

3-5 days

### How recent should the IPs data be used?

3-14 days

If you train weekly, you can **weight recent sessions higher** or use
**time-decay functions** to emphasize newer behaviors

py# Simple decay weight function import math from datetime import
datetime def decay_weight(event_time, now, half_life=3): delta_days =
(now - event_time).days lambda\_ = math.log(2) / half_life return
math.exp(-lambda\_ \* delta_days)
