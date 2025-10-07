**Introduction:**

- The Dailyhunt-VOD platform currently hosts all its video traffic on
  Google Cloud CDN. However, migration to Akamai CDN is planned to
  achieve several key objectives.

- The primary goal of this migration is to enhance offload and caching
  capabilities, improve overall performance, reduce latency, minimize
  errors, and ultimately achieve cost savings.

**Migration Strategy:**

- For the migration process, we have chosen to utilize Akamai\'s Global
  Traffic Manager (GTM), a product that facilitates traffic migration
  based on load distribution. To ensure a smooth transition, we will
  follow a gradual approach. Initially, we will shift only 1% of the
  traffic to Akamai CDN. This will allow us to perform comprehensive
  checks and validations on the performance.

- Once we have thoroughly verified the performance and ensured there are
  no issues with the 1% traffic shift, we will proceed with migrating
  the rest of the traffic. Our goal is to complete the entire migration
  within a timeframe of 3 days, aiming for a seamless transition without
  any disruptions.

- To minimize the impact on our users and business operations, we have
  strategically planned to shift the majority of the traffic during
  non-business hours. This approach will help avoid any potential
  negative effects on our services and ensure a smooth migration
  process.

- By following this step-by-step migration plan, leveraging GTM for
  load-based distribution, and prioritizing off-peak hours for traffic
  shifts, we are confident in achieving a successful migration to Akamai
  CDN, resulting in improved performance, reduced latency, and
  cost-effectiveness.

**Monitoring:**

- We will be using all the below matrices to monitor the entire
  migration activity and performance.

  - Error Reports on Akamai Control Center and Real-Time Reporting on
    Datalytics

  - Offload Report

  - Latency Report

  - Overall Traffic Report on Akamai, GCP, and Datalytics

**Post Migration Evaluation:**

- On July 31st, we commenced the migration of Dailyhunt-VOD from GCP to
  Akamai.

- Our assessment of metrics like Error Reports, Offload Report indicates
  that the Akamai CDN is performing exceptionally well, providing us
  with better offload capabilities. This is partly attributed to the
  inclusion of the Cloud Wrapper, which has played a crucial role in
  reducing utilization on the origin side. Refer **Origin Utilisation
  trend from July 26th to August 4th graph.**

- Furthermore, we have observed a notable decrease in errors compared to
  our previous setup on GCP. The migration to Akamai has proven to be a
  successful and advantageous move for our Dailyhunt-VOD service. Refer
  **Total Edge Hits by Response Class from July 31st to August
  7th(Akamai) graph.**

- The average offload on GCP was 96.50% whereas in Akamai we see the
  average offload is 98.85% with an increase of 2%. 

<!-- -->

- **Total Edge Hits by Response Class from July 31st to August
  7th(Akamai)**

<!-- -->

- **Total Edge Hits by Response Class from July 24th to July 30th(GCP)**

<!-- -->

- **Origin RPS trend from July 26th to August 4th**

<!-- -->

- **Note: We can clearly see after 2nd August, the load on LB has
  reduced.**

<!-- -->

- **Origin Utilisation trend from July 26th to August 4th**

<!-- -->

- **Note: We can clearly see after 2nd August, the load on LB has
  reduced.**
