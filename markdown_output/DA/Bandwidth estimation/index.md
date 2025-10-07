Copied from the
doc[https://docs.google.com/document/d/1Z5e9XaYmelmqs3laCm6NgYnIrZpta1B_FZ7rdbI36c4/edit](https://docs.google.com/document/d/1Z5e9XaYmelmqs3laCm6NgYnIrZpta1B_FZ7rdbI36c4/edit){card-appearance="inline"}

16falselistfalse

## **Bandwidth estimation logic 20.0.34 to 25.0.37**

### **Inputs**

1.  coldstart_network_provider_mapping from
    [](https://qa-gateway.coolfie.io/api/v1/upgrade/version/info/JOSH_STATIC_CONFIG/105)
    static config API

2.  bandwidthEstimate received from BandwidthMeter - latestExoEstimate

3.  bandwidth estimate from networkSDK - networkSDKEstimate

#### **Other configs from static config API**

1.  coldstart_transition_threshold_sec - controls how long app will
    defer switching to measured estimate.

2.  lifetime_bitrate_capture_window_sec - used to discard older
    estimates from lifetime_cq calculation

3.  speed_quality_map_v2 - client uses this to convert numeric-bitrate
    value to quality(slow, average etc.)

4.  bitrate_expression_v2 - the formula where fb and exo bitrates are
    substituted and executed.

#### **Static config API:**

1.  DH :
    [[ http://api-news.dailyhunt.in/api/v2/upgrade/config ]{.underline}](http://api-news.dailyhunt.in/api/v2/upgrade/config)

2.  Josh:
    [[https://qa-gateway.coolfie.io/api/v1/upgrade/version/info/JOSH_STATIC_CONFIG/105]{.underline}](https://qa-gateway.coolfie.io/api/v1/upgrade/version/info/JOSH_STATIC_CONFIG/105)[ ]{.underline}

### **Usage scenarios**

- **cold start (very first launch of user) or switch to a new network**
  Client picks quality by matching network and provider in the map.Exact
  or partial(network or operator) match is supported. It uses this value
  for atleast coldstart_transition_threshold_sec after which will switch
  to measured value, if available. It will take upto 5min for
  *lifetime\_*\* measurements to start flowing.

- **non-cold start (2nd launch onwards)** Client will use aggregated
  lifetime_cq of this network for atleast
  coldstart_transition_threshold_sec after which will switch to measured
  value, if available

### **Calculations**

- lifetime_cq - *EMA* (Exponential Moving Average) over *hourly-mean* of
  exo-estimates captured after time System.currentTimeMillis() -
  lifetime_bitrate_capture_window_sec\*1000 . When there is not enough
  data to compute this value (1st 5min in a new network), current_cq
  value is used as default.

- current_cq (measured; formula is configurable) - bitrate_expression_v2
  is evaluated with latestExoEstimate and networkSDKEstimate. If not
  available, bitrate_expression is the fallback. If that is not
  available or there is an exception, numeric weights(exoWeightage =
  1.1, networkWeightage = 2.0) are used. When the inputs are
  unavailable, \'good\' is used as default. maxQuality(from the
  coldstart_network_provider_mapping) for the current network/operation
  combination is used as upper cap for this value. This capping is
  applicable only for 2G,3G and 4G.

- lifetime_cq_distribution - aggregate exo-estimates captured after time
  System.currentTimeMillis() - lifetime_bitrate_capture_window_sec\*1000
  into a map\<quality, count\>. Eg: {\"good\":5, \"fast\": 6}

### **Numeric-bitrate to quality conversion**

For below values \"speed_quality_map_v2\": { \"200\": \"slow\",
\"1000\": \"average\", \"2500\": \"good\", \"5000\": \"fast\",
\"10000\": \"veryfast\" }

- -1 is \"unknown\"

- 0 to 200 is \"slow\"

- 201 to 1000 is \"average\"

- 1001 to 2500 is \"good\"

- 2501 to 5000 is fast

- \> 5000 is \"veryfast\"

### **Code**

- [[com.bwutil.BwEstRepo]{.underline}](https://git.newshunt.com/coolfie/coolfie-commons/blob/master/dailyhunt-common/src/main/java/com/bwutil/BitrateCalculations.kt)

- [[com.bwutil.BitrateCalculations]{.underline}](https://git.newshunt.com/coolfie/coolfie-commons/blob/master/dailyhunt-common/src/main/java/com/bwutil/BitrateCalculations.kt)

- [[com.bwutil.util.SpeedToQualityTest]{.underline}](https://git.newshunt.com/coolfie/coolfie-android/blob/master2/app/src/testDebug/java/com/bwutil/util/SpeedToQualityTest.kt)

### **External Links**

- [[facebook
  connectionclass]{.underline}](https://mvnrepository.com/artifact/com.facebook.network.connectionclass/connectionclass)

+-------------------------------------+-------------------------------+-----------------------+
| **Config**                          | **Current value in prod**     | **Purpose**           |
+-------------------------------------+-------------------------------+-----------------------+
| speedQualityMapV2                   | \"speed_quality_map_v2\": {   | bucketize the number  |
|                                     |                               | (bandwidth in kbps)   |
|                                     |         \"200\": \"slow\", // |                       |
|                                     | upto 200 is slow              |                       |
|                                     |                               |                       |
|                                     |         \"2000\":             |                       |
|                                     | \"average\", // upto 2000 is  |                       |
|                                     | avg                           |                       |
|                                     |                               |                       |
|                                     |         \"4000\":             |                       |
|                                     | \"betteraverage\",            |                       |
|                                     |                               |                       |
|                                     |         \"6000\": \"good\",   |                       |
|                                     |                               |                       |
|                                     |         \"8000\": \"fast\",   |                       |
|                                     |                               |                       |
|                                     |         \"16000\":            |                       |
|                                     | \"veryfast\" //upto 1600 &    |                       |
|                                     | above is veryfast             |                       |
|                                     |                               |                       |
|                                     |       }                       |                       |
|                                     |                               |                       |
|                                     | **\[from 25.1.5\]**           |                       |
|                                     |                               |                       |
|                                     | *\"speedQualityMapV2\"*: {    |                       |
|                                     |                               |                       |
|                                     |         \"200\": \"slow\", // |                       |
|                                     | upto 200 is slow              |                       |
|                                     |                               |                       |
|                                     |         \"2000\":             |                       |
|                                     | \"average\", // upto 2000 is  |                       |
|                                     | avg                           |                       |
|                                     |                               |                       |
|                                     |         \"4000\":             |                       |
|                                     | \"betteraverage\",            |                       |
|                                     |                               |                       |
|                                     |         \"6000\": \"good\",   |                       |
|                                     |                               |                       |
|                                     |         \"8000\": \"fast\",   |                       |
|                                     |                               |                       |
|                                     |         \"16000\":            |                       |
|                                     | \"veryfast\" //upto 1600 &    |                       |
|                                     | above is veryfast             |                       |
|                                     |                               |                       |
|                                     |       }                       |                       |
+-------------------------------------+-------------------------------+-----------------------+
| exo_weightage_double                | 0.8                           | This is fallback2 .   |
|                                     |                               | used when app         |
|                                     |                               | couldn\'t execute     |
|                                     |                               | both the formulas. it |
|                                     |                               | is just a weighted    |
|                                     |                               | sum                   |
+-------------------------------------+-------------------------------+-----------------------+
| network_weightage_double            | 0.2                           | This is fallback2 .   |
|                                     |                               | used when app         |
|                                     |                               | couldn\'t execute     |
|                                     |                               | both the formulas. it |
|                                     |                               | is just a weighted    |
|                                     |                               | sum                   |
+-------------------------------------+-------------------------------+-----------------------+
| bitrate_expression                  | \"formula\":                  | This is fallback1.    |
|                                     | \"(e\*0.8)+(n\*2)\"           | legacy formula. Used  |
|                                     |                               | when main forumla     |
|                                     |                               | throws.               |
+-------------------------------------+-------------------------------+-----------------------+
| bitrate_expression_exception        | \"formula\":                  | formula to be used    |
|                                     | \"(e\*0.8)+(n\*0.7)\"         | when fbbitrate \>     |
|                                     |                               | exobitrate            |
+-------------------------------------+-------------------------------+-----------------------+
| bitrate_expression_v2               | \"formula\": \"function       | This is the main      |
|                                     | f42(e,n){ \\n if(e\<n) return | formula this is used  |
|                                     | e\*0.8+n\*0.7; \\n else { var |                       |
|                                     | wa=e\*e/(e+n)+n\*n/(e+n);     |                       |
|                                     | return                        |                       |
|                                     | Math.min(wa,e);};\\n};\"      |                       |
+-------------------------------------+-------------------------------+-----------------------+
| lifetime_bitrate_capture_window_sec | 604800                        | =7days. entries older |
|                                     |                               | than this num will be |
|                                     |                               | deleted from DB and   |
|                                     |                               | not be used in        |
|                                     |                               | lifetime_cq           |
|                                     |                               | calculation.          |
+-------------------------------------+-------------------------------+-----------------------+
| coldstart_transition_threshold_sec  | 10                            | ignore the exo        |
|                                     |                               | estimates for the     |
|                                     |                               | first 10 sec. because |
|                                     |                               | they could be         |
|                                     |                               | unstable.             |
+-------------------------------------+-------------------------------+-----------------------+
| exo_sliding_percentile_max_weight   | 1000                          | this impacts the      |
|                                     |                               | recency of samples    |
|                                     |                               | kept for exo          |
|                                     |                               | estimation. lower the |
|                                     |                               | value, lesser samples |
|                                     |                               | are kept (older ones  |
|                                     |                               | will be deleted)      |
+-------------------------------------+-------------------------------+-----------------------+
| sliding_percentile_percentile       | 0.5\                          | this impacts the      |
|                                     | **\[from 25.1.5\]**           | estimate reported by  |
|                                     |                               | exoplayer. higher the |
|                                     | 0.8                           | value, higher the     |
|                                     |                               | estimate              |
+-------------------------------------+-------------------------------+-----------------------+
| coldstart_network_provider_mapping  | \<big object - open the API   | this is used to pick  |
|                                     | link above to check\>         | an bucket based on    |
|                                     |                               | user network and      |
|                                     | **\[From 25.1.5\]**           | operator, if we       |
|                                     |                               | don\'t have any       |
|                                     | ` [`                          | estimates from exo    |
|                                     |                               | player                |
|                                     | `  {`                         |                       |
|                                     |                               |                       |
|                                     | `    "network": "5G",`        |                       |
|                                     |                               |                       |
|                                     | `    "provider": "Any",`      |                       |
|                                     |                               |                       |
|                                     | `    "quality": "average"`    |                       |
|                                     |                               |                       |
|                                     | `  },`                        |                       |
|                                     |                               |                       |
|                                     | `  {`                         |                       |
|                                     |                               |                       |
|                                     | `    "network": "4G",`        |                       |
|                                     |                               |                       |
|                                     | `    "provider": "Any",`      |                       |
|                                     |                               |                       |
|                                     | `    "quality": "average"`    |                       |
|                                     |                               |                       |
|                                     | `  },`                        |                       |
|                                     |                               |                       |
|                                     | `  {`                         |                       |
|                                     |                               |                       |
|                                     | `    "network": "3G",`        |                       |
|                                     |                               |                       |
|                                     | `    "provider": "Any",`      |                       |
|                                     |                               |                       |
|                                     | `    "quality": "average",`   |                       |
|                                     |                               |                       |
|                                     | `    "maxQuality": "good"`    |                       |
|                                     |                               |                       |
|                                     | `  },`                        |                       |
|                                     |                               |                       |
|                                     | `  {`                         |                       |
|                                     |                               |                       |
|                                     | `    "network": "2G",`        |                       |
|                                     |                               |                       |
|                                     | `    "provider": "Any",`      |                       |
|                                     |                               |                       |
|                                     | `    "quality": "slow",`      |                       |
|                                     |                               |                       |
|                                     | `    "maxQuality": "average"` |                       |
|                                     |                               |                       |
|                                     | `  },`                        |                       |
|                                     |                               |                       |
|                                     | `  {`                         |                       |
|                                     |                               |                       |
|                                     | `    "network": "w",`         |                       |
|                                     |                               |                       |
|                                     | `    "provider": "Any",`      |                       |
|                                     |                               |                       |
|                                     | `    "quality": "good"`       |                       |
|                                     |                               |                       |
|                                     | `  },`                        |                       |
|                                     |                               |                       |
|                                     | `  {`                         |                       |
|                                     |                               |                       |
|                                     | `    "network": "Any",`       |                       |
|                                     |                               |                       |
|                                     | `    "provider": "Any",`      |                       |
|                                     |                               |                       |
|                                     | `    "quality": "good"`       |                       |
|                                     |                               |                       |
|                                     | `  }`                         |                       |
|                                     |                               |                       |
|                                     | `  ],`                        |                       |
+-------------------------------------+-------------------------------+-----------------------+

**Note:** 

1.  (Until 25x) Exo player estimate is essential for calculations. Else,
    app uses values from static map or lifetime_cq and does not do any
    calculation.

2.  We are already using the latest version of fbconnectionclass and it
    is no longer actively maintained.

3.  If we do not get the update from exo, the re-calculation is not
    quick enough.

### Sliding Percentile logic 

------------------------------------------------------------------------

## Changes in 25.1.5

Jira: <https://jira.newshunt.com/browse/DHANDROID-4120>

### Summary

1.  Replace *fbconnectionclass-estimate* with app\'s
    *okhttp-derived-estimate* due to below reasons 

    1.  *fbconnectionclass* calculates the estimates by polling the
        system for bytes transferred, which includes data transfers from
        other apps. To get a **more** **accurate** estimate, we need to
        consider app\'s network activity only (some app doing sync in
        the bg may report good bandwidth, but if our app make a network
        request at the same time, it would observe lesser speed as both
        are sharing same channel) 

    2.  If no data is being transmitted, the estimate gradually
        **decreases** and becomes **close to 0**. This is a limitation
        of the *fbconnectionclass* approach. 

    3.  fbconnectionclass project [[is no longer
        maintained]{.underline}](http://okhttp-interceptor-measured-estimate/)
        and it is **archived**.

2.  App\'s *okhttp-derived-estimate* would be calculated as below 

    1.  Using OkHttp event listener, measure the time taken for each
        request. 

        1.  Consider only **network-responses**

        2.  Skip responses that transferred a very **low number**(X -
            configurable) of bytes. Reason: connection time in the
            overall time would be higher. They would not add much value

        3.  Ignore **video** related requests (.m3u8, .mp4, .ts) as they
            are already factored into calculation by
            exo-player-estimates.

        4.  Generate estimate **only** after having **considered
            Y(configurable) number of bytes**. Until then, it can be
            null. 

    2.  **Feed this** information into a **sliding percentile** and
        calculate the estimate

    3.  **Use** the resulting value **in-place of**
        ***fbconnectionclass-esitmate*** for all the calculations.

    4.  If exo-estimate is absent, directly use
        *okhttp-derived-estimate*

3.  Print realtime bandwidth updates on the screen, for easier testing
    in logged builds 

4.  As exo\'s estimate very high, skip exo in estimation logic by
    `  "nw_est_exo_stale_discard_threshold_sec":0,` and
    make`  "sliding_percentile_percentile":0.8` (as it is giving better
    estimate), `coldstart_network_provider_mapping` can be simplified to
    remove operator-specific entries (which are anyways same values,
    currently and never customized). 

5.  There is discrepancy in the variable name - client is using
    `speedQualityMapV2 `. BE to change it only for android (even for
    older clients)

6.  Network SDK uses speed buckets for things like allocating threads -
    make the speed values configurable
    (`"nsdk_speed_buckets": [0, 200, 4000, 6000, 2147483647])`

**New configs introduced: **

  ---------------------------------------- ------------------------------------ ------------------------------------------------------------------------------------------------------------------------
  **Config**                               **Current value in prod**            **Purpose**
  nw_est_min_bytes_to_consider_sample      100                                  any bandwidth sample whose size less than this will be excluded from estimation logic
  nw_est_min_millis_to_consider_sample     10                                   any bandwidth sample whose transfer duration less than this will be excluded from estimation logic
  nw_est_exo_stale_discard_threshold_sec   0                                    if last estimate from exo is older than this, it will be discarded and direct networksdk estimate will be used
  nw_est_ignore_file_extensions            \[\]                                 used to exclude files from bandwidth estimation (url*String.contains()* will be tested against each item in this arry)
  nsdk_speed_buckets                       \[0, 200, 4000, 6000, 2147483647\]   for configuring bitrates for pre-defined buckets used in networksdk (for thread allocation & other tasks)
  ---------------------------------------- ------------------------------------ ------------------------------------------------------------------------------------------------------------------------

### BE config changes:

**In bwEstCfg**

+-----------------------------------------------------------------------+
| `"speedQualityMapV2":{`                                               |
|                                                                       |
| `"200":"slow",`                                                       |
|                                                                       |
| `"2000":"average",`                                                   |
|                                                                       |
| `"4000":"betteraverage",`                                             |
|                                                                       |
| `"6000":"good",`                                                      |
|                                                                       |
| `"8000":"fast",`                                                      |
|                                                                       |
| `"16000":"veryfast"`                                                  |
|                                                                       |
| `}`                                                                   |
+-----------------------------------------------------------------------+

**In network_config**

+-----------------------------------------------------------------------+
| `"network_config" : {`                                                |
|                                                                       |
| `  "coldstart_network_provider_mapping": [`                           |
|                                                                       |
| `  {`                                                                 |
|                                                                       |
| `    "network": "5G",`                                                |
|                                                                       |
| `    "provider": "Any",`                                              |
|                                                                       |
| `    "quality": "average"`                                            |
|                                                                       |
| `  },`                                                                |
|                                                                       |
| `  {`                                                                 |
|                                                                       |
| `    "network": "4G",`                                                |
|                                                                       |
| `    "provider": "Any",`                                              |
|                                                                       |
| `    "quality": "average"`                                            |
|                                                                       |
| `  },`                                                                |
|                                                                       |
| `  {`                                                                 |
|                                                                       |
| `    "network": "3G",`                                                |
|                                                                       |
| `    "provider": "Any",`                                              |
|                                                                       |
| `    "quality": "average",`                                           |
|                                                                       |
| `    "maxQuality": "good"`                                            |
|                                                                       |
| `  },`                                                                |
|                                                                       |
| `  {`                                                                 |
|                                                                       |
| `    "network": "2G",`                                                |
|                                                                       |
| `    "provider": "Any",`                                              |
|                                                                       |
| `    "quality": "slow",`                                              |
|                                                                       |
| `    "maxQuality": "average"`                                         |
|                                                                       |
| `  },`                                                                |
|                                                                       |
| `  {`                                                                 |
|                                                                       |
| `    "network": "w",`                                                 |
|                                                                       |
| `    "provider": "Any",`                                              |
|                                                                       |
| `    "quality": "good"`                                               |
|                                                                       |
| `  },`                                                                |
|                                                                       |
| `  {`                                                                 |
|                                                                       |
| `    "network": "Any",`                                               |
|                                                                       |
| `    "provider": "Any",`                                              |
|                                                                       |
| `    "quality": "good"`                                               |
|                                                                       |
| `  }`                                                                 |
|                                                                       |
| `  ],`                                                                |
|                                                                       |
| `  "nw_est_min_bytes_to_start_estimating": 1000,`                     |
|                                                                       |
| `  "nw_est_min_bytes_to_consider_sample" : 100,`                      |
|                                                                       |
| `  "nw_est_min_millis_to_consider_sample" : 10,`                      |
|                                                                       |
| `  "nw_est_exo_stale_discard_threshold_sec":0,`                       |
|                                                                       |
| `  "nw_est_ignore_file_extensions":[],`                               |
|                                                                       |
| `  "nsdk_speed_buckets": [0, 200, 4000, 6000, 2147483647],`           |
|                                                                       |
| `  "sliding_percentile_percentile":0.8,`                              |
|                                                                       |
| }                                                                     |
+-----------------------------------------------------------------------+

### Observations on QA

1.  Observed estimate from exo player is always very high

2.  We can use networksdk measurement for video streaming as well by
    changing conifgs\
    `"nw_est_ignore_file_extensions":[],`\
    `"nw_est_exo_stale_discard_threshold_sec":0`

3.  Overall estimate from nsdk is a bit low. Value 0.8 percentile seem
    better (older was 0.5)\
    `"sliding_percentile_percentile":.0.8 `

4.  For normal videos, we are getting a ts file fetch every 8 sec. For
    live videos, neither exo, nor nsdk measurement is updating 

------------------------------------------------------------------------

## Changes for 25.2.x

Jira: <https://jira.newshunt.com/browse/DHANDROID-4176> 

1.  Lifetime measurement should be calculated over the final derived
    estimate and not exo-player alone

2.  Lifetime measurement can be used as the 3rd step, regardless of
    whether exo-estimate is considered or not.

3.  Comment out *fallback to lifetime measurement*, because there are
    edge cases during network-switch (requests starting in one network
    and finishing in another network would be counted in finishing
    network), that can lead to higher estimates. It is being tracked for
    next-release.

4.  Optimize re-calculation: refresh only when networksdk/exo estimate
    changes (remove from other places) 

5.  BE config changes: **make coldstart_transition_threshold_sec 0**

** **` `**a) Summary: **

`coldstart_transition_threshold_sec` determines how long to wait before
switching to the detected-value

**current value = 10**

**proposed value = 0**

**[Pros:]{.underline}** 

- For slow networks, it is beneficial to switch to detected-value as
  soon as possible. If detected-value is lower than current - say,
  detected=slow, current-from-static-map=average - it would be
  beneficial to switch to slow immediately, rather than wait for 10 sec.

- For fast networks, switching immediately increase the chances of
  serving higher quality content

**[Cons:]{.underline}**

- If, at that point, the network is very unstable, it would be better to
  wait for 10 sec (giving it some more time to stabilize, which may/may
  not happen in 10 sec) before taking its value. 

**b) Tech Notes: **

1.  What are the data sources / inputs ?

`measured_1` : estimate derived from app\'s network activity

`coldstart_network_provider_mapping` *:* static map coming from BE

1.  How does the app derive a final estimate from these 2 sources?

`finalEstimate` =  if( `measured_1`  is available 

    and `coldstart_transition_threshold_sec` has passed since the 1st
measurement) 

             use `measured_1 `

     else, use `coldstart_network_provider_mapping` 

1.  What is impact of making

`coldstart_transition_threshold_sec=0 ?`

App will use `measured_1 `estimate as soon as it is available

Consider the scenario: User is on 4G network, and it took 3 sec to get
`measured_1=SLOW` estimate

  ---------------- ------------------------------------------------------------- -------------------------------------------------------------
  **Time**         **estimate (*****coldstart_transition_threshold_sec = 0)***   **estimate(*****coldstart_transition_threshold_sec = 10)***
  0-3sec           `AVERAGE(`source=`map`)                                       `AVERAGE(`source=`map`)
  3-10 sec         `SLOW(`source=`measured_1`)                                   `AVERAGE(`source=`map`)
  11 sec onwards   `SLOW(`source=`measured_1`)                                   `SLOW(`source=`measured_1`)
  ---------------- ------------------------------------------------------------- -------------------------------------------------------------

Same switch will happen for switching to higher(map=average,
detected=fast) as well, but it is more crucial to switch to lower as
soon as possible (to prevent more requests) 

------------------------------------------------------------------------

## Meeting notes 

### #1 

(date: 26-1-2023: [[Amit
Kankani]{.underline}](mailto:amit.kankani@eternoinfotech.com) [[Srikanth
Ramaswamy]{.underline}](mailto:srikanth.ramaswamy@verse.in) [[Santosh
Kumar Dhanyamraju]{.underline}](mailto:satosh.dhanyamraju@verse.in)
[[Shubham Agarwal]{.underline}](mailto:shubham.agarwal@verse.in))

- Say estimates exo=A, networksdk=B,

○ average out (moving window) and then apply the current formula?
Averaging formulas should be configurable.

○ They will not have info about the absolute bytes transferred to add
weight based formula

○ Delete entries older than 10(configurable) sec

○ B is fallback (use directly), when A= 0

- Measure values at different percentiles, totalWeights to remove
  spikes(should we do it? )

<!-- -->

- Delete bucketing code from network SDK - just report estimated bitrate
  (float)

<!-- -->

- Measuring bandwidth every sec across samples - though realistic of
  bw - may not be desired, as if a new request made wouldn\'t observe
  aggregated bw.

<!-- -->

- 

~~We could get TxBytes per UID form system, but they still have the
problem of being 0 when not consuming (is it fine? Because, if not
consuming, we don\'t actually know the bandwidth - should it be another
input-source for bw calculation?)~~

### #2

(date: 27-1-2023: [[Bapu Kota]{.underline}](mailto:bapu.kota@verse.in)
[[Amit Kankani]{.underline}](mailto:amit.kankani@eternoinfotech.com)
[[Santosh Kumar
Dhanyamraju]{.underline}](mailto:satosh.dhanyamraju@verse.in))

- Response header should be used? not just body (exo uses body)

<!-- -->

- All paths images should be considered - verify 

<!-- -->

- Syncup with PV: optimisation 

<!-- -->

- Followup: use GCDN instead of LB ips 

### #N

Suggestions

1.  5G reported 2G by the system (fixed by client)

2.  reduce totalWeight to make it it more adaptive (BE)

3.  change slow to 500 (client)

To evaluate further

1.  All bandwidth meter measures should account for pre-fetch vs real
    time streaming differently

2.  Plugin for webview enabled video format consumption/exchange

3.  Needs to be right balanced for *performance now* vs *quality of
    content/destination promise*

4.  Start with degraded variant and as soon as same item/slide is ready
    with better quality, if user is in view on same item/slide - prompt
    for user to refresh

5.  PV bandwidth meter patch review

------------------------------------------------------------------------
