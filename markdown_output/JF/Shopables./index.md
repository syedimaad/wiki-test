1.  **[Implementation details:]{.underline}**

    - The request response will be same as Foryou/feed

    - The Shopables feed will only serve item for which
      **shoppable_content = true** and **ads_attached = true**. This
      field will be populated for content by Add team.

    - The information for shoppable is shoppable_meta in response as
      below.\"shoppable_meta\":

The shoppable meta present in packet -\>

json\"shoppable_meta\": { \"show_widget\": true, \"is_shoppable\": true,
\"enable_distance\": true, \"purchase_count\": 500 }

- Define an Arm for shoppables and cache the data in query cache for
  this Arm. Use query cache from Foryou to populate the cache for
  shoppables arm. during feed serve the data from foryou query cache
  will be served.

- The min max for Arm will be same as feed size(10) as we are only
  defining one group. The selection config and min max, query cache
  elastic query are controlled from dsl.

- Need generic must filter which will be applied post selection from
  elastic : List of filter required **(mustFilters) → Amit** ex: active
  content and ctr \> 60. A subset from Foryou should suffice.

- In future we can have multiple Arm/Group to gain more fine gain
  control on serving(Depend on content clusters).

- History should be applied from USerProfile and Recent action to remove
  duplicates(Discuss for current implementation) - Amit.

- The global distribution should be used for coldstart and user
  distribution once the User distribution crossed defined threshold.

- **Non function performance Requirement :** The response time for feed
  should be below 50 ms as the serving is happening from memory.
