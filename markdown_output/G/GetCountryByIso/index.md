This is an api to get the details of a country based on the isocode
(2digit) of the country.

*note: It will also give you a locationUrl which can be used to get more
details of the country(as a location)/*

ex:
<https://locationservice.dailyhunt.in/global/v1/countries/?iso_code=qa&appId=dh_mena>

resp:

{ \"status\": 200, \"results\": \[ { \"id\": \"85632299\", \"name\":
\"Qatar\", \"latitude\": 25.208492, \"longitude\": 51.155983,
\"countryCode\": \"QA\", \"locationUrl\":
\"https://locationservice.dailyhunt.in/global/v1/locations?id=85632299&appId=dh_mena&children=true\",
\"hasChildren\": true, \"title\": { \"bn\": \"কাতার\", \"bh\": \"क़तर\",
\"en\": \"Qatar\", \"gu\": \"કતાર\", \"hi\": \"क़तर\", \"kn\": \"ಕಟಾರ್\",
\"ml\": \"ഖത്തർ\", \"mr\": \"कतार\", \"ar\": \"قطر\", \"or\": \"କତର\",
\"pa\": \"ਕਤਰ\", \"ta\": \"கத்தார்\", \"te\": \"కతర్\", \"ur\": \"قطر\" } }
\] }
