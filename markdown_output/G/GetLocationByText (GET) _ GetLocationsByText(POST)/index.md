This is used to get the details of any location by name. Example You can
search for city Bengaluru under state karnataka - India.

post request can hold maximum of 100 city details to search.\
Also, the result is cached to make it faster and reduce the load on
pelias.

Service flow:

`GetLocationByText. => getStaticMappingResOrSearchAlias `\
else `GetLocationFromPeliasByName` =\> `Pelias2SearchApiResponse`

Request Sample:

\

curl \--location
\'https://locationservice.dailyhunt.in/global/v1/search\' \\ \--header
\'Content-Type: application/json\' \\ \--data \'\[ { \"city\":
\"kochi\", \"state\": \"kerala\", \"country\" : \"India\" }, { \"city\":
\"ernakulam\", \"state\": \"kerala\", \"country\" : \"India\" } \]\'

Sample Response:

\[ { \"source\": \"\", \"city\": \"kochi\", \"cityId\": \"c18_450\",
\"state\": \"kerala\", \"stateId\": \"s18\", \"country\": \"india\",
\"countryId\": \"85632469\", \"isPreferred\": false, \"countryCode\":
\"IN\", \"latitude\": 10.052821, \"longitude\": 76.477806 }, { \"id\":
\"102030301\", \"source\": \"\", \"city\": \"ernakulam\", \"cityId\":
\"c18_450\", \"state\": \"kerala\", \"stateId\": \"s18\", \"country\":
\"india\", \"countryId\": \"85632469\", \"locality\": \"ernakulam\",
\"localityId\": \"102030301\", \"isPreferred\": false, \"placetype\":
\"locality\", \"countryCode\": \"IN\", \"name\": \"ernakulam\",
\"continent\": \"asia\", \"continentId\": \"102191569\", \"label\":
\"ernakulam, kl, india\", \"latitude\": 9.8548, \"longitude\": 76.5266 }
\]
