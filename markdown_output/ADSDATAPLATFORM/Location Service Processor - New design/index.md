**[Spark Process to write to Mongo, Redis and Analytics
Kafka]{.underline}**

**Source:** Kafka topic - req_messages

**Writes to:**

- Mongo collection - DhUsers, DhApps

- Redis keys

- Analytics Kafka

**Steps:**

1.  Read events from Kafka in dataframe (df).

2.  Filter out the records if any of the conditions are satisfied:

    1.  Client id is empty or null

    2.  Partner_id is affiliate

    3.  Placement is supplement or affiliate

3.  Generate 3 boolean columns - mobile_network_params_validity,
    gps_params_validity, ip_params_validity based on the conditions:

    1.  mobile_network_params_validity - mcc, mnc, lac, cellid (If any
        of these is empty or null, it is marked invalid)

    2.  gps_params_validity: latitude, longitude (If any of these is
        empty or null, it is marked invalid)

    3.  ip_params_validity: IP (If it is empty or null, it is marked
        invalid)

4.  Filter out the records if all of the columns -
    mobile_network_params_validity, gps_params_validity and
    ip_params_validity are null/false.

5.  Call Location Service URL after building the params (using
    mobile_network_params, gps_params, ip_params) with flatMap function
    and add response as columns to df. (Caching will be done here).

6.  *Gpscity, Gpsstate, Gpscountry, location_source, dfp location (
    dfp_city, dfp_state, dfp_country ), last_updated_redis, cityId,
    stateId, countryId* from Redis will be sent by ad engine in the same
    Kafka event (which will be used as the last location available, say
    current_location, currrent_city, current_state, current_country,
    current_source)

7.  df has columns (new_source, current_source) which will be compared.
    Update new_source column in df based on the following conditions:

    1.  Update location with new location if new location source has
        higher precedence

    2.  Update location with new location if new location source has
        lower precedence if old location is older than x days

    3.  If new_source is IP_DFP or IP, then check DFP validity and IP
        validity. If invalid, replace new_source with current_source.

8.  Add new column 'ip' to joined_df with ip_params.IP when new_source
    in (IP, IP_DFP, IP_PRECISE).

9.  Set df (new_city, new_state, new_country) columns to dfp_city,
    dfp_state, dfp_country when kafka_source is IP_DFP.

10. Set new_source to current_source when new_source is IP and
    ((current_country is **'india'** and new_country not in **(\'united
    arab emirates\'**, **\'bahrain\'**, **\'kuwait\'**, **\'oman\'**,
    **\'qatar\'**, **\'saudi arabia\')**) or (new_city is
    **'hingoli'**))  \## Don't change location in redis if new city is
    hingoli and new source is IP.

11. If last_updated_redis is yesterday , and new_location and
    current_location are the same , then send data to analytics kafka
    and set last_updated in redis to current timestamp.

12. If new_location and current_location are different, then update to
    mongo (location in DhUsers, only last_seen with current_timestamp in
    DhApps), redis and send event to analytics kafka.
