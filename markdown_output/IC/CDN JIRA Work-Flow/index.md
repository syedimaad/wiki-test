**Parent onboarding ticket for application hostname:**

- Application use-case.

- Hostname to be onboarded (Public URL)

- Origin Endpoint to route the traffic to (Existing LB IP address or
  connect with network team to setup)

- Application content-type (helps deciding the cost implications for the
  onboarding)

- Traffic scheme: HTTP or HTTPS?

- Request methods to be supported? (GET is supported by default)

- Caching strategy: (If we should honor the origin cache settings or
  implement different caching TTLs for static assets such as html, css,
  js, images, fonts etc.)

- Does app traffic contain PII (Personal Identifiable Information)?

- Any specific use-case to be considered from CDN setup perspective

- Valid test URL and expected response code

- Go-live date\

**Non-Prod Hostname onboarding:**

Please provide similar details as above, in 1st step, for non-prod
domains so that configuration is validated before routing live traffic
via CDN.

- Application use-case.

- Testing hostname to be onboarded (Public URL)

- Origin Endpoint to route the traffic to (existing DNS record or IP
  address)

- Traffic scheme: HTTP or HTTPS?

- Request methods to be supported? (GET is supported by default)

- Caching strategy: (If we should honor the origin cache settings or
  implement different caching TTLs for static assets such as html, css,
  js, images, fonts etc.)

- Does app traffic contain PII (Personal Identifiable Information)?

- Application content-type (helps deciding the cost implications for the
  onboarding)

- Valid test URL and expected response code

- Go-live date

**Change request:**

- Descriptive request for the change to be made

- Deployment window

- Infra team dependency such as Network, GCP, Josh, DH etc.

**Reports and analysis:**

- Timeframe

- Hostname or CP Code

- Any pattern to extract such as URL, status code etc.?

- Use-case for which report is required

**System incidents:**

- Timeframe

- Hostname or CP Code

- Trend review and insights

- Any pattern to extract such as URL, status code etc.?

- Use-case for which report is required

**Improvements:**

- Description of the request such product update or upgrade

- Cost optimization specifics

**POC** (varies based on product type):

- Application use-case.

- Hostname to be onboarded (Public URL)

- Origin Endpoint to route the traffic to (existing DNS record or IP
  address)

- Traffic scheme: HTTP or HTTPS?

- Content handling specs

- Does app traffic contain PII (Personal Identifiable Information)?

- Application content-type (helps deciding the cost implications for the
  onboarding)

- End goal

- Timeframe for POC completion (can be based on product trial contract)

**Tasks for CDN team for onboarding requests**

**DSA and OD onboarding:**

- Requirements and onboarding steps (sub-tasks listed below)

  - Create Origin endpoint to be configured with CDN

  - Public DNS CNAME entry -

  - Private DNS CNAME entry -

  - Test cases based on URLs -

- Monitoring and Alerts setup: -

  - Update documents (sql table and CDN Hosts sheets) and add CP Code to
    the table and mark rt1

  - Configure DS2 and if live streaming is needed, set to live column to
    True/False accordingly

  - Add CP Code for DS2 alerts threshold - Assign this to

  - Update monitoring script for real-time logging - Assign this to

  - Traffic review for a week post onboarding to understand the trend
    and should be reviewed with product owner

  - Configure ACC alerts for the new onboarding -

- KSD Onboarding -

**TCL onboarding:**

- Refer doc:
  [https://docs.google.com/document/d/1OLkpB3r4itBVA0p9_VNHYH0h3ae1rrS13fYbINQa8kM/edit](https://docs.google.com/document/d/1OLkpB3r4itBVA0p9_VNHYH0h3ae1rrS13fYbINQa8kM/edit){card-appearance="inline"}
