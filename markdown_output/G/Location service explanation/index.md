Some of the main responsibility of location service:

1.  **Search Location:**

    1.  <https://locationservice.dailyhunt.in/global/v1/location/search>

    2.  <https://locationservice.dailyhunt.in/v2/location>

    3.  [https://locationservice.dailyhunt.in/v1/locatio](https://locationservice.dailyhunt.in/v2/location)n

All above three api are currently being used to resolve location based
on:

i\. GPS (lat/long)

ii\. cell-id (mnc-mcc-id)

iii\. ip

**note:** If anyone pass clientId and Ip only, then in that case if we
have any city resolved with GPS previously for that client, GPS location
will be returned(bcz gps has the higher priority)

2\. To get the **location history of a client** in x-days interval based
upon RFM formula

[http://](http://10.50.0.38:8080/v1/location/history?clientId=dh.RXR3bnpZZUVPTU9AGN3l0QnQvVjFNdz09A&startDate=2022-10-05&endDate=2022-11-05)[locationservice.dailyhunt.in](https://locationservice.dailyhunt.in/global/v1/location/search)[/v1/location/history?clientId=dh.RXR3bnpZZUVPTU9AGN3l0QnQvVjFNdz09A&startDate=2022-10-05&endDate=2022-11-05](http://10.50.0.38:8080/v1/location/history?clientId=dh.RXR3bnpZZUVPTU9AGN3l0QnQvVjFNdz09A&startDate=2022-10-05&endDate=2022-11-05)

###### \[ { \"clientId\": \"dh.RXR3bnpZZUVPTU9AGN3l0QnQvVjFNdz09A\", \"date\": \"2022-11-02-13\", \"locationSource\": \"CELL\", \"locationSourceConfidence\": \"0.8\", \"city\": \"anantapuram\", \"eventCount\": 2 }, { \"clientId\": \"dh.RXR3bnpZZUVPTU9AGN3l0QnQvVjFNdz09A\", \"date\": \"2022-11-02-13\", \"locationSource\": \"GPS\", \"locationSourceConfidence\": \"0.9\", \"city\": \"anantapuram\", \"eventCount\": 9 }, { \"clientId\": \"dh.RXR3bnpZZUVPTU9AGN3l0QnQvVjFNdz09A\", \"date\": \"2022-11-01-20\", \"locationSource\": \"CELL\", \"locationSourceConfidence\": \"0.8\", \"city\": \"anantapuram\", \"eventCount\": 4 } \]

3\. Get **UserLocation computed by RFM formula and understanding of
different systems:**
<https://locationservice.dailyhunt.in/global/v1/user/location?appId=DH_APP&clientId=dh.cC9AWQkVINmpDL0lZZDlSMG1POFRZUT09A>

###### {

###### \"status\": 200, \"locations\": { \"adsLocation\": { \"source\": \"LOCATION_IP_MODEL\", \"city\": \"krishnagiri\", \"cityId\": \"c31_770\", \"constituency\": \"thalli\", \"constituencyId\": \"CN2457_S31\", \"state\": \"tamil nadu\", \"stateId\": \"s31\", \"country\": \"india\", \"isPreferred\": true, \"confidence\": 0.5, \"countryCode\": \"IN\", \"pincode\": \"635116\", \"latitude\": 12.489, \"longitude\": 78.0327 } }, \"topCities\": { \"cities\": \[ { \"city\": \"davanagere\", \"state\": \"karnataka\", \"country\": \"india\", \"score\": 210.6, \"sources\": \[ { \"source\": \"LOCATION_IP_MODEL\", \"score\": 210.6 } \] }, { \"city\": \"bengaluru\", \"state\": \"karnataka\", \"country\": \"india\", \"score\": 140, \"sources\": \[ { \"source\": \"IP\", \"score\": 140 } \] }, { \"city\": \"krishnagiri\", \"state\": \"tamil nadu\", \"country\": \"india\", \"score\": 54, \"sources\": \[ { \"source\": \"LOCATION_IP_MODEL\", \"score\": 54 } \] } \], \"updatedAt\": \"2022-12-09T10:52:30+05:30\" } }

**Different Type Location Source:**

In clientProfile data and location service response we can have five
different type of source. Which are listed below:

  ------------ --------- ----------------------- ------------------------------------------ ------------------------------------------------------ --------
  **source**   **GPS**   **CELL**                **IP_DFP**                                 **LOCATION_IP_MODEL**                                  **IP**
  score        0.9       0.7                     0.6                                        0.5                                                    0.4
  data-set     pelias    cell-centric learning   google DFP data managed by DhUserProfile   ip-learning data managed by location-learning server   MMDB
  ------------ --------- ----------------------- ------------------------------------------ ------------------------------------------------------ --------
