IDEA: To build a service which keeps the location-understanding of all
host_app based on the gaid. For dedup purpose.

Data will look like:

{ \"currentLocation\": { \"city\": \"CITY_NAME\", \"cityId\":
\"CITY_ID\", \"state\": \"STATE_NAME\", \"stateId\": \"STATE_ID\",
\"source\": \"GPS/IP/CELL/IP-DFP/LOCATION-IP-MODEL\", \"hostAppId\":
\"DH/JOSH/APP\", \"clientId\" : \"dh123/J123/PV123\", \"gaid\"
:\"abcd-1234-asfe\", \"lastUpdated\": \"2022-12-21\" }, \"locations\": {
\"adsLocation\": { \"source\": \"LOCATION_IP_MODEL\", \"city\":
\"krishnagiri\", \"cityId\": \"c31_770\", \"constituency\": \"thalli\",
\"constituencyId\": \"CN2457_S31\", \"state\": \"tamil nadu\",
\"stateId\": \"s31\", \"country\": \"india\", \"isPreferred\": true,
\"confidence\": 0.5, \"countryCode\": \"IN\", \"pincode\": \"635116\",
\"latitude\": 12.489, \"longitude\": 78.0327 }, \"pvLocation\": {
\"source\": \"PV_FEED\", \"city\": \"krishnagiri\", \"cityId\":
\"c31_770\", \"constituency\": \"thalli\", \"constituencyId\":
\"CN2457_S31\", \"state\": \"tamil nadu\", \"stateId\": \"s31\",
\"country\": \"india\", \"isPreferred\": true, \"confidence\": 0.9,
\"countryCode\": \"IN\", \"pincode\": \"635116\", \"latitude\": 12.489,
\"longitude\": 78.0327 }, \"joshLocation\": { \"source\": \"JOSH_FEED\",
\"city\": \"krishnagiri\", \"cityId\": \"c31_770\", \"constituency\":
\"thalli\", \"constituencyId\": \"CN2457_S31\", \"state\": \"tamil
nadu\", \"stateId\": \"s31\", \"country\": \"india\", \"isPreferred\":
true, \"confidence\": 0.9, \"countryCode\": \"IN\", \"pincode\":
\"635116\", \"latitude\": 12.489, \"longitude\": 78.0327 },
\"dhLocation\": { \"source\": \"DH_FEED\", \"city\": \"krishnagiri\",
\"cityId\": \"c31_770\", \"constituency\": \"thalli\",
\"constituencyId\": \"CN2457_S31\", \"state\": \"tamil nadu\",
\"stateId\": \"s31\", \"country\": \"india\", \"isPreferred\": true,
\"confidence\": 0.9, \"countryCode\": \"IN\", \"pincode\": \"635116\",
\"latitude\": 12.489, \"longitude\": 78.0327 } }, \"topCities\": {
\"cities\": \[ { \"city\": \"davanagere\", \"state\": \"karnataka\",
\"country\": \"india\", \"score\": 210.6, \"sources\": \[ { \"source\":
\"LOCATION_IP_MODEL\", \"appSource\" : \"DH\", \"score\": 210.6 } \] },
{ \"city\": \"bengaluru\", \"state\": \"karnataka\", \"country\":
\"india\", \"score\": 140, \"sources\": \[ { \"source\": \"IP\",
\"score\": 140 } \] }, { \"city\": \"krishnagiri\", \"state\": \"tamil
nadu\", \"country\": \"india\", \"score\": 54, \"sources\": \[ {
\"source\": \"LOCATION_IP_MODEL\", \"score\": 54 } \] } \],
\"updatedAt\": \"2022-12-09T10:52:30+05:30\" } }
