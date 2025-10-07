We can get location details starting from country to their localities
present using Location Service.

The hierarchy followed is

Country -\> state/region -\> city/county -\> localities

The endpoint used for getting location is
[here](https://locationservice.dailyhunt.in/global/v1/countries/?iso_code=in&appId=dh_mena).

queryParam Description:

- id: Used in location service which refers to locations by id from
  whosonfirstdb

- appId: optional to pass, we pass appId for debugging purposes
  currently

- children: will fetch the children details if set to yes otherwise no

We can take an example and see the sample responses which comes from it.

Sample request:

`https://locationservice.dailyhunt.in/global/v1/locations?id=85632469&appId=dh_mena&children=true`

json{ \"status\": 200, \"results\": \[ { \"id\": \"85632469\", \"name\":
\"India\", \"latitude\": 22.687581, \"longitude\": 79.370366,
\"countryCode\": \"IN\", \"locationUrl\":
\"https://locationservice.dailyhunt.in/global/v1/locations?id=85632469&appId=dh_mena&children=true\",
\"hasChildren\": true, \"title\": { \"bn\": \"ভারত\", \"bh\": \"भारत\",
\"en\": \"India\", \"gu\": \"ભારત\", \"hi\": \"भारत\", \"kn\": \"ಭಾರತ\",
\"ml\": \"ഇന്ത്യ\", \"mr\": \"भारत\", \"ar\": \"الهند\", \"or\": \"ଭାରତ\",
\"pa\": \"ਭਾਰਤ\", \"ta\": \"இந்தியா\", \"te\": \"ఇండియా\", \"ur\":
\"ہندوستان\" }, \"children\": \[ { \"id\": \"s13\", \"name\":
\"haryana\", \"latitude\": 29.143027, \"longitude\": 76.342784,
\"countryCode\": \"IN\", \"locationUrl\":
\"https://locationservice.dailyhunt.in/global/v1/locations?id=85672133&appId=dh_mena&children=true\",
\"hasChildren\": true, \"title\": { \"bn\": \"হরিয়াণা\", \"bh\":
\"हरियाणा\", \"en\": \"Haryana\", \"gu\": \"હરિયાણા\", \"hi\":
\"हरियाणा\", \"kn\": \"ಹರ್ಯಾಣ\", \"ml\": \"ഹരിയാന\", \"mr\": \"हरयाणा\",
\"ar\": \"هاريانا\", \"or\": \"ହରିୟାଣା\", \"pa\": \"ਹਰਿਆਣਾ\", \"ta\":
\"ஹரியானா\", \"te\": \"హర్యానా\", \"ur\": \"ہریانہ\" } },
\...\...\...\...\...\.... { \"id\": \"s27\", queryParam \"name\":
\"puducherry\", \"latitude\": 10.943987, \"longitude\": 79.796105,
\"countryCode\": \"IN\", \"locationUrl\":
\"https://locationservice.dailyhunt.in/global/v1/locations?id=85672241&appId=dh_mena&children=true\",
\"hasChildren\": true, \"title\": { \"bn\": \"পুদুচেরি\", \"bh\":
\"पदुच्चेरी\", \"en\": \"Puducherry\", \"gu\": \"પુડુચેરી\", \"hi\":
\"पुडुचेरी\", \"kn\": \"ಪುದುಚೆರಿ\", \"ml\": \"പുതുച്ചേരി\", \"mr\": \"पुडुचेरी\",
\"ar\": \"إقليم بودوتشيري\", \"or\": \"ପୁଡୁଚେରୀ\", \"pa\": \"ਪਾਂਡੂਚਰੀ\",
\"ta\": \"புதுச்சேரி\", \"te\": \"పుదుచేర్రీ\", \"ur\": \"پڈوچیری\" } } \] }
\] }

As you can see, we will get all the states here. Now, if we pick on
state from here.

We will pick Haryana whose id is `s13`.

Sample request would be

`https://locationservice.dailyhunt.in/global/v1/locations?id=s13&appId=dh_mena&children=true`

json{ \"status\": 200, \"results\": \[ { \"id\": \"s13\", \"name\":
\"haryana\", \"latitude\": 29.143027, \"longitude\": 76.342784,
\"countryCode\": \"IN\", \"locationUrl\":
\"https://locationservice.dailyhunt.in/global/v1/locations?id=85672133&appId=dh_mena&children=true\",
\"hasChildren\": true, \"title\": { \"bn\": \"হরিয়াণা\", \"bh\":
\"हरियाणा\", \"en\": \"Haryana\", \"gu\": \"હરિયાણા\", \"hi\":
\"हरियाणा\", \"kn\": \"ಹರ್ಯಾಣ\", \"ml\": \"ഹരിയാന\", \"mr\": \"हरयाणा\",
\"ar\": \"هاريانا\", \"or\": \"ହରିୟାଣା\", \"pa\": \"ਹਰਿਆਣਾ\", \"ta\":
\"ஹரியானா\", \"te\": \"హర్యానా\", \"ur\": \"ہریانہ\" }, \"children\": \[ {
\"id\": \"c13_278\", \"name\": \"fatehabad\", \"latitude\": 29.56593,
\"longitude\": 75.553866, \"countryCode\": \"IN\", \"aliases\": \[
\"fatehabad\" \], \"locationUrl\":
\"https://locationservice.dailyhunt.in/global/v1/locations?id=1108695759&appId=dh_mena&children=true\",
\"hasChildren\": true, \"title\": { \"bn\": \"ফতেহাবাদ জেলা\", \"bh\":
\"फतेहाबाद जिला\", \"en\": \"Fatehabad\", \"gu\": \"ફતેહબાદ\", \"hi\":
\"फतेहाबाद\", \"kn\": \"ಫತೇಹಾಬಾದ್\", \"ml\": \"ഫത്തേഹാബാദ്\", \"mr\":
\"फतेहाबाद\", \"ar\": \"فاتح أباد\", \"pa\": \"ਫਤੇਹਾਬਾਦ\", \"ta\":
\"ஃபதேஹாபாத்\", \"te\": \"పతేహాబాద్\", \"ur\": \"فتح آباد\" } },
\...\...\..... { \"id\": \"c13_300\", \"name\": \"sonepat\",
\"latitude\": 29.01947, \"longitude\": 76.968205, \"countryCode\":
\"IN\", \"aliases\": \[ \"sonipat\" \], \"locationUrl\":
\"https://locationservice.dailyhunt.in/global/v1/locations?id=890509439&appId=dh_mena&children=true\",
\"hasChildren\": true, \"title\": { \"bn\": \"সোনিপাত জেলা\", \"bh\":
\"सोनीपत जिला\", \"en\": \"Sonepat\", \"gu\": \"સોનીપટ\", \"hi\":
\"सोनीपत\", \"kn\": \"ಸೋನಿಪತ್\", \"ml\": \"സോണിപത്\", \"mr\": \"सोनीपत\",
\"ar\": \"سونيبات\", \"pa\": \"ਸੋਨੀਪੱਤ\", \"ta\": \"சோனிபட்\", \"te\":
\"సోనిపట్\", \"ur\": \"سونی پت\" } } \] } \] }

We got all of their cities/county.

Taking Sonipat now, whose id is `c13_300`, and seeing the response and
we will get all the localities.

Sample request:
`https://locationservice.dailyhunt.in/global/v1/locations?id=c13_300&appId=dh_mena&children=true`

json{ \"status\": 200, \"results\": \[ { \"id\": \"c13_300\", \"name\":
\"sonepat\", \"latitude\": 29.01947, \"longitude\": 76.968205,
\"countryCode\": \"IN\", \"aliases\": \[ \"sonipat\" \],
\"locationUrl\":
\"https://locationservice.dailyhunt.in/global/v1/locations?id=890509439&appId=dh_mena&children=true\",
\"hasChildren\": true, \"title\": { \"bn\": \"সোনিপাত জেলা\", \"bh\":
\"सोनीपत जिला\", \"en\": \"Sonepat\", \"gu\": \"સોનીપટ\", \"hi\":
\"सोनीपत\", \"kn\": \"ಸೋನಿಪತ್\", \"ml\": \"സോണിപത്\", \"mr\": \"सोनीपत\",
\"ar\": \"سونيبات\", \"pa\": \"ਸੋਨੀਪੱਤ\", \"ta\": \"சோனிபட்\", \"te\":
\"సోనిపట్\", \"ur\": \"سونی پت\" }, \"children\": \[ { \"id\":
\"1327018435\", \"name\": \"Akbarpur Barota\", \"latitude\": 28.90776,
\"longitude\": 77.06564, \"countryCode\": \"IN\", \"locationUrl\":
\"https://locationservice.dailyhunt.in/global/v1/locations?id=1327018435&appId=dh_mena\",
\"title\": {} }, \...\.... { \"id\": \"102028575\", \"name\":
\"Sonīpat\", \"latitude\": 29.009128, \"longitude\": 77.078234,
\"countryCode\": \"IN\", \"locationUrl\":
\"https://locationservice.dailyhunt.in/global/v1/locations?id=102028575&appId=dh_mena\",
\"title\": { \"bn\": \"সোনিপাত\", \"bh\": \"सोनीपत\", \"en\":
\"Sonipat\", \"gu\": \"સોનિપત\", \"hi\": \"सोनीपत\", \"kn\": \"ಸೋನಿಪತ್\",
\"mr\": \"सोनीपत\", \"ar\": \"سونيبات\", \"or\": \"ସୋନିପତ\", \"pa\":
\"ਸੋਨੀਪਤ\", \"ta\": \"சோனிபத்\", \"te\": \"సోనిపట్\", \"ur\": \"سونی پت\" } }
\] } \] }

We have gotten all the localities present in Sonipat now.

Now taking one locality we will observe that we will not get any
children if we refer to the hierarchy above.

Sample request:
`https://locationservice.dailyhunt.in/global/v1/locations?id=1327018435&appId=dh_mena&children=true`

json{ \"status\": 200, \"results\": \[ { \"id\": \"1327018435\",
\"name\": \"Akbarpur Barota\", \"latitude\": 28.90776, \"longitude\":
77.06564, \"countryCode\": \"IN\", \"locationUrl\":
\"https://locationservice.dailyhunt.in/global/v1/locations?id=1327018435&appId=dh_mena\",
\"title\": {} } \] }
