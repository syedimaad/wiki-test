------------------------------------------------------------------------

# **\~ Get Country Details \~** {#get-country-details style="text-align: center;"}

Endpoint For getCountryDetails :
[link](https://locationservice.dailyhunt.in/global/v1/countries/?iso_code=in&appId=dh_mena)

> `https://locationservice.dailyhunt.in/global/v1/countries/?iso_code=in&appId=dh_mena`

queryParams details:

- **iso_code** : iso_code of country ex: **in** for india

- **appId**: for debugging purpose / in future it will be used to
  whitelist the source

response:

json{ \"status\": 200, \"results\": \[ { \"id\": \"85632469\",
\"placetype\": \"country\", \"countryCode\": \"IN\", \"parentId\":
\"102191569\", \"name\": \"India\", \"locationUrl\":
\"https://locationservice.dailyhunt.in/global/v1/locations?id=85632469&appId=dh_mena&children=true\",
\"hasChildren\": true, \"lastModified\": 1618362896, \"title\": {
\"bn\": \"ভারত\", \"bh\": \"भारत\", \"en\": \"India\", \"gu\": \"ભારત\",
\"hi\": \"भारत\", \"kn\": \"ಭಾರತ\", \"ml\": \"ഇന്ത്യ\", \"mr\": \"भारत\",
\"ar\": \"الهند\", \"or\": \"ଭାରତ\", \"pa\": \"ਭਾਰਤ\", \"ta\":
\"இந்தியா\", \"te\": \"ఇండియా\", \"ur\": \"ہندوستان\" } } \] }

From Response `locationUrl` can be used to get hierarchy of location.
This will always give you details of immediate children .

Hierarchy followed by location service is as:

Country → State(region) → City(county) → Locality

# **\~ Get Location Details \~** {#get-location-details style="text-align: center;"}

Endpoint For getCountryDetails :
[link](https://locationservice.dailyhunt.in/global/v1/countries/?iso_code=in&appId=dh_mena)

> `https://locationservice.dailyhunt.in/global/v1/locations?id=85632469&appId=dh_mena&children=true`

queryParams details:

- **id**: this id is only meaningful for locationservice for internal
  conversion (whosonfirst id for sqlite db)

- **appId**: for debugging purpose / in future it will be used to
  whitelist the source

- **children**=true will allow to fetch children, false will restrict to
  get details of children

json{ \"status\": 200, \"results\": \[ { \"id\": \"85632469\",
\"placetype\": \"country\", \"countryCode\": \"IN\", \"parentId\":
\"102191569\", \"name\": \"India\", \"locationUrl\":
\"https://locationservice.dailyhunt.in/global/v1/locations?id=85632469&appId=dh_mena&children=true\",
\"hasChildren\": true, \"lastModified\": 1618362896, \"title\": {
\"bn\": \"ভারত\", \"bh\": \"भारत\", \"en\": \"India\", \"gu\": \"ભારત\",
\"hi\": \"भारत\", \"kn\": \"ಭಾರತ\", \"ml\": \"ഇന്ത്യ\", \"mr\": \"भारत\",
\"ar\": \"الهند\", \"or\": \"ଭାରତ\", \"pa\": \"ਭਾਰਤ\", \"ta\":
\"இந்தியா\", \"te\": \"ఇండియా\", \"ur\": \"ہندوستان\" }, \"children\": \[ {
\"id\": \"s28\", \"placetype\": \"region\", \"countryCode\": \"IN\",
\"parentId\": \"85632469\", \"name\": \"punjab\", \"locationUrl\":
\"https://locationservice.dailyhunt.in/global/v1/locations?id=85672195&appId=dh_mena&children=true\",
\"hasChildren\": true, \"lastModified\": 1599602393, \"title\": {
\"bn\": \"পাঞ্জাব\", \"bh\": \"पंजाब\", \"en\": \"Punjab\", \"gu\":
\"પંજાબ\", \"hi\": \"पंजाब\", \"kn\": \"ಪಂಜಾಬ್\", \"ml\": \"പഞ്ചാബ്\",
\"mr\": \"पंजाब\", \"ar\": \"البنجاب\", \"or\": \"ପଞ୍ଜାବ\", \"pa\":
\"ਪੰਜਾਬ\", \"ta\": \"பஞ்சாப்\", \"te\": \"పంజాబ్\", \"ur\": \"پنجاب\" } },
\...\...\...\...\.... { \"id\": \"s27\", \"placetype\": \"region\",
\"countryCode\": \"IN\", \"parentId\": \"85632469\", \"name\":
\"puducherry\", \"locationUrl\":
\"https://locationservice.dailyhunt.in/global/v1/locations?id=85672241&appId=dh_mena&children=true\",
\"hasChildren\": true, \"lastModified\": 1636505360, \"title\": {
\"bn\": \"পুদুচেরি\", \"bh\": \"पदुच्चेरी\", \"en\": \"Puducherry\", \"gu\":
\"પુડુચેરી\", \"hi\": \"पुडुचेरी\", \"kn\": \"ಪುದುಚೆರಿ\", \"ml\": \"പുതുച്ചേരി\",
\"mr\": \"पुडुचेरी\", \"ar\": \"إقليم بودوتشيري\", \"or\": \"ପୁଡୁଚେରୀ\",
\"pa\": \"ਪਾਂਡੂਚਰੀ\", \"ta\": \"புதுச்சேரி\", \"te\": \"పుదుచేర్రీ\", \"ur\":
\"پڈوچیری\" } } \] } \] }

note: You can use above url to get details all immediate children and
then can be recursed to get details of all id from db upto city levels.
(country's children are state and state's children are cities.)

***Always use id & name field from the response for mapping***

**NOTE:** [While making GET request
"]{style="color: rgb(255,86,48);"}[[https://locationservice.dailyhunt.in/global/v1/locations?id=s17&appId=dh_mena&children=true]{style="color: rgb(255,86,48);"}](https://locationservice.dailyhunt.in/global/v1/locations?id=s17&appId=dh_mena&children=true)[".
the id can be any id either dh-location-service format (s12 or c12_123)
or it can be pelias id. This endpoint will first try to search given id
in static mapping if not present in that it will query spr table of
whosonfirst sqlite.]{style="color: rgb(255,86,48);"}
