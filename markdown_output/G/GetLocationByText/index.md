## **Get City Detail for CITY**

For searching details (id/lat/long) you can make a post api-call with
the city, state & country details. It will search pelias with the given
text combination and will return the detailed info as per input. Post
body will support list upto 100 entries at one time. Also, requests are
getting cached at service level so location service won't make call to
pelias each time.

curl \--location
\'https://locationservice.dailyhunt.in/global/v1/search\' \\ \--header
\'Content-Type: application/json\' \\ \--data \'\[ { \"city\":
\"vadodara\", \"state\": \"gujarat\", \"country\" : \"India\" }, {
\"city\": \"bangalore\", \"state\": \"karnataka\", \"country\" :
\"India\" } \]\'

sample response of above curl:

> \[\
> {\
> \"source\": \"\",\
> \"city\": \"vadodara\",\
> \"cityId\": \"c12_270\",\
> \"state\": \"gujarat\",\
> \"stateId\": \"s12\",\
> \"country\": \"india\",\
> \"countryId\": \"85632469\",\
> \"isPreferred\": false,\
> \"countryCode\": \"IN\",\
> \"latitude\": 22.171234,\
> \"longitude\": 73.30657\
> },\
> {\
> \"id\": \"102030819\",\
> \"source\": \"\",\
> \"city\": \"bangalore\",\
> \"cityId\": \"c17_407\",\
> \"state\": \"karnataka\",\
> \"stateId\": \"s17\",\
> \"country\": \"india\",\
> \"countryId\": \"85632469\",\
> \"locality\": \"bangalore\",\
> \"localityId\": \"102030819\",\
> \"isPreferred\": false,\
> \"placetype\": \"locality\",\
> \"countryCode\": \"IN\",\
> \"name\": \"bangalore\",\
> \"continent\": \"asia\",\
> \"continentId\": \"102191569\",\
> \"label\": \"bangalore, ka, india\",\
> \"latitude\": 12.9656,\
> \"longitude\": 77.6063\
> }\
> \]
