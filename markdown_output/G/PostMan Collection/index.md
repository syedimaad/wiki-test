wide{ \"info\": { \"\_postman_id\":
\"21fb4192-6955-44ac-9ce6-2cd26d01cb71\", \"name\": \"global-location\",
\"schema\":
\"https://schema.getpostman.com/json/collection/v2.1.0/collection.json\"
}, \"item\": \[ { \"name\": \"qa\", \"item\": \[ { \"name\": \"api
manipulate location Copy 2\", \"request\": { \"method\": \"GET\",
\"header\": \[\], \"url\": { \"raw\":
\"http://10.52.0.17:8080/api/manipulateLocation?client=dh.Y05ZMFVuRzh3L2hiYjVLSkdqTGxyZz09A&city=gurgaon&cityId=c13_278&stateId=s13&countryId=85632469&state=haryana&country=india\",
\"protocol\": \"http\", \"host\": \[ \"10\", \"52\", \"0\", \"17\" \],
\"port\": \"8080\", \"path\": \[ \"api\", \"manipulateLocation\" \],
\"query\": \[ { \"key\": \"client\", \"value\":
\"dh.Y05ZMFVuRzh3L2hiYjVLSkdqTGxyZz09A\" }, { \"key\": \"city\",
\"value\": \"gurgaon\" }, { \"key\": \"cityId\", \"value\": \"c13_278\"
}, { \"key\": \"stateId\", \"value\": \"s13\" }, { \"key\":
\"countryId\", \"value\": \"85632469\" }, { \"key\": \"state\",
\"value\": \"haryana\" }, { \"key\": \"country\", \"value\": \"india\" }
\] } }, \"response\": \[\] }, { \"name\": \"healthcheck\", \"request\":
{ \"method\": \"GET\", \"header\": \[\], \"url\": { \"raw\":
\"http://10.52.64.4:8080/global/v1/healthcheck?appId=dh_mena\",
\"protocol\": \"http\", \"host\": \[ \"10\", \"52\", \"64\", \"4\" \],
\"port\": \"8080\", \"path\": \[ \"global\", \"v1\", \"healthcheck\" \],
\"query\": \[ { \"key\": \"appId\", \"value\": \"dh_mena\" } \] } },
\"response\": \[\] }, { \"name\": \"getCountryByIso\", \"request\": {
\"method\": \"GET\", \"header\": \[\], \"url\": { \"raw\":
\"http://10.52.0.17:8080/global/v1/countries/?iso_code=ae&appId=dh_mena\",
\"protocol\": \"http\", \"host\": \[ \"10\", \"52\", \"0\", \"17\" \],
\"port\": \"8080\", \"path\": \[ \"global\", \"v1\", \"countries\", \"\"
\], \"query\": \[ { \"key\": \"iso_code\", \"value\": \"ae\" }, {
\"key\": \"appId\", \"value\": \"dh_mena\" } \] } }, \"response\": \[\]
}, { \"name\": \"getCountryByIso Copy\", \"request\": { \"method\":
\"GET\", \"header\": \[\], \"url\": { \"raw\":
\"http://10.52.0.17:8080/global/v1/countries/?iso_code=ae&appId=dh_mena\",
\"protocol\": \"http\", \"host\": \[ \"10\", \"52\", \"0\", \"17\" \],
\"port\": \"8080\", \"path\": \[ \"global\", \"v1\", \"countries\", \"\"
\], \"query\": \[ { \"key\": \"iso_code\", \"value\": \"ae\" }, {
\"key\": \"appId\", \"value\": \"dh_mena\" } \] } }, \"response\": \[\]
}, { \"name\": \"SearchByGPS\", \"request\": { \"method\": \"GET\",
\"header\": \[\], \"url\": { \"raw\":
\"http://10.52.64.4:8080/global/v1/location/search?appId=dh_mena&atitude=24.0759571&longitude=74.7653445\",
\"protocol\": \"http\", \"host\": \[ \"10\", \"52\", \"64\", \"4\" \],
\"port\": \"8080\", \"path\": \[ \"global\", \"v1\", \"location\",
\"search\" \], \"query\": \[ { \"key\": \"appId\", \"value\":
\"dh_mena\" }, { \"key\": \"atitude\", \"value\": \"24.0759571\" }, {
\"key\": \"longitude\", \"value\": \"74.7653445\" } \] } },
\"response\": \[\] }, { \"name\": \"SearchByIp\", \"request\": {
\"method\": \"GET\", \"header\": \[\], \"url\": { \"raw\":
\"http://10.50.1.113:8080/global/v1/location/search?ip=205.253.59.37\",
\"protocol\": \"http\", \"host\": \[ \"10\", \"50\", \"1\", \"113\" \],
\"port\": \"8080\", \"path\": \[ \"global\", \"v1\", \"location\",
\"search\" \], \"query\": \[ { \"key\": \"ip\", \"value\":
\"205.253.59.37\" } \] } }, \"response\": \[\] }, { \"name\": \"Search
bY Ip and GPS\", \"request\": { \"method\": \"GET\", \"header\": \[\],
\"url\": { \"raw\":
\"http://10.52.64.4:8080/global/v1/location/search?approx-lac-city=true&latitude=17.101&longitude=81.794\",
\"protocol\": \"http\", \"host\": \[ \"10\", \"52\", \"64\", \"4\" \],
\"port\": \"8080\", \"path\": \[ \"global\", \"v1\", \"location\",
\"search\" \], \"query\": \[ { \"key\": \"approx-lac-city\", \"value\":
\"true\" }, { \"key\": \"latitude\", \"value\": \"17.101\" }, { \"key\":
\"longitude\", \"value\": \"81.794\" } \] } }, \"response\": \[\] }, {
\"name\": \"prom\", \"request\": { \"method\": \"GET\", \"header\": \[\]
}, \"response\": \[\] }, { \"name\": \"New Request\", \"request\": {
\"method\": \"GET\", \"header\": \[\] }, \"response\": \[\] }, {
\"name\": \"pelias gps\", \"request\": { \"method\": \"GET\",
\"header\": \[\], \"url\": { \"raw\":
\"http://10.52.64.4:4000/v1/reverse?size=1&point.lon=81.79&point.lat=17.101\",
\"protocol\": \"http\", \"host\": \[ \"10\", \"52\", \"64\", \"4\" \],
\"port\": \"4000\", \"path\": \[ \"v1\", \"reverse\" \], \"query\": \[ {
\"key\": \"size\", \"value\": \"1\" }, { \"key\": \"point.lon\",
\"value\": \"81.79\" }, { \"key\": \"point.lat\", \"value\": \"17.101\"
} \] } }, \"response\": \[\] }, { \"name\": \"getBytext\", \"request\":
{ \"method\": \"GET\", \"header\": \[\], \"url\": { \"raw\":
\"http://10.50.1.141:8080/global/v1/search?city=varanasi\",
\"protocol\": \"http\", \"host\": \[ \"10\", \"50\", \"1\", \"141\" \],
\"port\": \"8080\", \"path\": \[ \"global\", \"v1\", \"search\" \],
\"query\": \[ { \"key\": \"city\", \"value\": \"varanasi\" } \] } },
\"response\": \[\] }, { \"name\": \"user location\", \"request\": {
\"method\": \"GET\", \"header\": \[\] }, \"response\": \[\] }, {
\"name\": \"searchbyText\", \"request\": { \"method\": \"POST\",
\"header\": \[\], \"body\": { \"mode\": \"raw\", \"raw\": \"\[\\n {\\n
\\\"city\\\": \\\"pune\\\",\\n \\\"state\\\": \\\"maharasthra\\\",\\n
\\\"country\\\": \\\"india\\\"\\n }\\n\]\", \"options\": { \"raw\": {
\"language\": \"json\" } } }, \"url\": { \"raw\":
\"http://10.52.64.4:8080/global/v1/search\", \"protocol\": \"http\",
\"host\": \[ \"10\", \"52\", \"64\", \"4\" \], \"port\": \"8080\",
\"path\": \[ \"global\", \"v1\", \"search\" \] } }, \"response\": \[\] }
\] }, { \"name\": \"prod\", \"item\": \[ { \"name\": \"healthcheck\",
\"request\": { \"method\": \"GET\", \"header\": \[\], \"url\": {
\"raw\":
\"https://locationservice.dailyhunt.in/global/v1/healthcheck?appId=adengine\",
\"protocol\": \"https\", \"host\": \[ \"locationservice\",
\"dailyhunt\", \"in\" \], \"path\": \[ \"global\", \"v1\",
\"healthcheck\" \], \"query\": \[ { \"key\": \"appId\", \"value\":
\"adengine\" } \] } }, \"response\": \[\] }, { \"name\":
\"getCountryByIso\", \"request\": { \"method\": \"GET\", \"header\":
\[\], \"url\": { \"raw\":
\"https://locationservice.dailyhunt.in/global/v1/countries/?iso_code=in&appId=dh_mena\",
\"protocol\": \"https\", \"host\": \[ \"locationservice\",
\"dailyhunt\", \"in\" \], \"path\": \[ \"global\", \"v1\",
\"countries\", \"\" \], \"query\": \[ { \"key\": \"iso_code\",
\"value\": \"in\" }, { \"key\": \"appId\", \"value\": \"dh_mena\" } \] }
}, \"response\": \[\] }, { \"name\": \"getLocationByID\", \"request\": {
\"method\": \"GET\", \"header\": \[\], \"url\": { \"raw\":
\"https://locationservice.dailyhunt.in/global/v1/locations?id=421172075&appId=dh_mena&children=false\",
\"protocol\": \"https\", \"host\": \[ \"locationservice\",
\"dailyhunt\", \"in\" \], \"path\": \[ \"global\", \"v1\", \"locations\"
\], \"query\": \[ { \"key\": \"id\", \"value\": \"421172075\" }, {
\"key\": \"appId\", \"value\": \"dh_mena\" }, { \"key\": \"children\",
\"value\": \"false\" } \] } }, \"response\": \[\] }, { \"name\":
\"getLocationByID\", \"request\": { \"method\": \"GET\", \"header\":
\[\], \"url\": { \"raw\":
\"https://locationservice.dailyhunt.in/global/v1/locations?id=85632573&children=true&appId=dh_mena\",
\"protocol\": \"https\", \"host\": \[ \"locationservice\",
\"dailyhunt\", \"in\" \], \"path\": \[ \"global\", \"v1\", \"locations\"
\], \"query\": \[ { \"key\": \"id\", \"value\": \"85632573\" }, {
\"key\": \"children\", \"value\": \"true\" }, { \"key\": \"appId\",
\"value\": \"dh_mena\" } \] } }, \"response\": \[\] }, { \"name\":
\"SearchByGPS\", \"request\": { \"method\": \"GET\", \"header\": \[\],
\"url\": { \"raw\":
\"https://locationservice.dailyhunt.in/global/v1/location/search?appId=PV_APP&latitude=25.58&longitude=75.42\",
\"protocol\": \"https\", \"host\": \[ \"locationservice\",
\"dailyhunt\", \"in\" \], \"path\": \[ \"global\", \"v1\", \"location\",
\"search\" \], \"query\": \[ { \"key\": \"ip\", \"value\":
\"106.206.19.0\", \"disabled\": true }, { \"key\": \"clientId\",
\"value\": \"1430717945\", \"disabled\": true }, { \"key\": \"appId\",
\"value\": \"PV_APP\" }, { \"key\": \"latitude\", \"value\": \"25.58\"
}, { \"key\": \"longitude\", \"value\": \"75.42\" } \] } },
\"response\": \[\] }, { \"name\": \"SearchByIp\", \"request\": {
\"method\": \"GET\", \"header\": \[\], \"url\": { \"raw\":
\"https://locationservice.dailyhunt.in/global/v1/location/search?ip=27.63.18.226\",
\"protocol\": \"https\", \"host\": \[ \"locationservice\",
\"dailyhunt\", \"in\" \], \"path\": \[ \"global\", \"v1\", \"location\",
\"search\" \], \"query\": \[ { \"key\": \"/v2/location?clientId\",
\"value\": \"dh.SStVZGdJQ2FITU1PaHc5UVhuYit1UT09A\", \"disabled\": true
}, { \"key\": \"ip\", \"value\": \"27.63.18.226\" } \] } },
\"response\": \[\] }, { \"name\": \"Search bY Ip and GPS\", \"request\":
{ \"method\": \"GET\", \"header\": \[\], \"url\": { \"raw\":
\"https://locationservice.dailyhunt.in/global/v1/location/search?ip=49.249.89.150&clientId=1567146529&latitude=17.38&longitude=74.7653445\",
\"protocol\": \"https\", \"host\": \[ \"locationservice\",
\"dailyhunt\", \"in\" \], \"path\": \[ \"global\", \"v1\", \"location\",
\"search\" \], \"query\": \[ { \"key\": \"ip\", \"value\":
\"49.249.89.150\" }, { \"key\": \"clientId\", \"value\": \"1567146529\"
}, { \"key\": \"latitude\", \"value\": \"17.38\" }, { \"key\":
\"longitude\", \"value\": \"74.7653445\" } \] } }, \"response\": \[\] },
{ \"name\": \"cellid\", \"request\": { \"method\": \"GET\", \"header\":
\[\], \"url\": { \"raw\":
\"https://locationservice.dailyhunt.in/global/v1/location/search?appId=dh_mena&mnc=862&appId=gcp&cellid=205817857&mcc=405&longitude=76.400774&lac=3075\",
\"protocol\": \"https\", \"host\": \[ \"locationservice\",
\"dailyhunt\", \"in\" \], \"path\": \[ \"global\", \"v1\", \"location\",
\"search\" \], \"query\": \[ { \"key\": \"appId\", \"value\":
\"dh_mena\" }, { \"key\": \"mnc\", \"value\": \"862\" }, { \"key\":
\"appId\", \"value\": \"gcp\" }, { \"key\": \"cellid\", \"value\":
\"205817857\" }, { \"key\": \"mcc\", \"value\": \"405\" }, { \"key\":
\"longitude\", \"value\": \"76.400774\" }, { \"key\": \"lac\",
\"value\": \"3075\" } \] } }, \"response\": \[\] }, { \"name\":
\"v2/state-to-lang-sync\", \"request\": { \"method\": \"GET\",
\"header\": \[\], \"url\": { \"raw\":
\"https://locationservice.dailyhunt.in/v2/state-to-lang-sync\",
\"protocol\": \"https\", \"host\": \[ \"locationservice\",
\"dailyhunt\", \"in\" \], \"path\": \[ \"v2\", \"state-to-lang-sync\" \]
} }, \"response\": \[\] }, { \"name\": \"v2/lang-to-state-sync\",
\"request\": { \"method\": \"GET\", \"header\": \[\], \"url\": {
\"raw\": \"https://locationservice.dailyhunt.in/v2/lang-to-state-sync\",
\"protocol\": \"https\", \"host\": \[ \"locationservice\",
\"dailyhunt\", \"in\" \], \"path\": \[ \"v2\", \"lang-to-state-sync\" \]
} }, \"response\": \[\] }, { \"name\": \"v1 state to lang\",
\"request\": { \"method\": \"GET\", \"header\": \[\], \"url\": {
\"raw\": \"https://locationservice.dailyhunt.in/v1/state-to-lang-sync\",
\"protocol\": \"https\", \"host\": \[ \"locationservice\",
\"dailyhunt\", \"in\" \], \"path\": \[ \"v1\", \"state-to-lang-sync\" \]
} }, \"response\": \[\] }, { \"name\": \"v1/lang-to-state-sync\",
\"request\": { \"method\": \"GET\", \"header\": \[\], \"url\": {
\"raw\": \"https://locationservice.dailyhunt.in/v1/lang-to-state-sync\",
\"protocol\": \"https\", \"host\": \[ \"locationservice\",
\"dailyhunt\", \"in\" \], \"path\": \[ \"v1\", \"lang-to-state-sync\" \]
} }, \"response\": \[\] }, { \"name\": \"v2 location\", \"request\": {
\"method\": \"GET\", \"header\": \[\], \"url\": { \"raw\":
\"https://locationservice.dailyhunt.in/v2/location?mnc=31&latitude=22.622779999999995&ip=2401:4900:110b:8235:0:50:6e6d:9501&cellid=2740770&mcc=404&longitude=88.42248833333333&lac=6\",
\"protocol\": \"https\", \"host\": \[ \"locationservice\",
\"dailyhunt\", \"in\" \], \"path\": \[ \"v2\", \"location\" \],
\"query\": \[ { \"key\": \"mnc\", \"value\": \"31\" }, { \"key\":
\"latitude\", \"value\": \"22.622779999999995\" }, { \"key\": \"ip\",
\"value\": \"2401:4900:110b:8235:0:50:6e6d:9501\" }, { \"key\":
\"cellid\", \"value\": \"2740770\" }, { \"key\": \"mcc\", \"value\":
\"404\" }, { \"key\": \"longitude\", \"value\": \"88.42248833333333\" },
{ \"key\": \"lac\", \"value\": \"6\" } \] } }, \"response\": \[\] }, {
\"name\": \"v1 location\", \"request\": { \"method\": \"GET\",
\"header\": \[\], \"url\": { \"raw\":
\"https://locationservice.dailyhunt.in/v1/location?approx-lac-city=true&&mcc=405&mnc=52&lac=8125&cellid=233927959&latitude=26.8485306&longitude=84.6232207&ip=171.51.169.30\",
\"protocol\": \"https\", \"host\": \[ \"locationservice\",
\"dailyhunt\", \"in\" \], \"path\": \[ \"v1\", \"location\" \],
\"query\": \[ { \"key\": \"approx-lac-city\", \"value\": \"true\" }, {
\"key\": null, \"value\": null }, { \"key\": \"mcc\", \"value\": \"405\"
}, { \"key\": \"mnc\", \"value\": \"52\" }, { \"key\": \"lac\",
\"value\": \"8125\" }, { \"key\": \"cellid\", \"value\": \"233927959\"
}, { \"key\": \"latitude\", \"value\": \"26.8485306\" }, { \"key\":
\"longitude\", \"value\": \"84.6232207\" }, { \"key\": \"ip\",
\"value\": \"171.51.169.30\" } \] } }, \"response\": \[\] }, { \"name\":
\"pelias gps\", \"request\": { \"method\": \"GET\", \"header\": \[\],
\"url\": { \"raw\":
\"http://dh-location-pelias.dailyhunt.in/v1/reverse?size=1&point.lon=81.79&point.lat=17.101\",
\"protocol\": \"http\", \"host\": \[ \"dh-location-pelias\",
\"dailyhunt\", \"in\" \], \"path\": \[ \"v1\", \"reverse\" \],
\"query\": \[ { \"key\": \"size\", \"value\": \"1\" }, { \"key\":
\"point.lon\", \"value\": \"81.79\" }, { \"key\": \"point.lat\",
\"value\": \"17.101\" } \] } }, \"response\": \[\] }, { \"name\":
\"location history\", \"request\": { \"method\": \"GET\", \"header\":
\[\] }, \"response\": \[\] }, { \"name\": \"getIpsOfmig\", \"request\":
{ \"method\": \"GET\", \"header\": \[\] }, \"response\": \[\] }, {
\"name\": \"grafana\", \"request\": { \"method\": \"GET\", \"header\":
\[\] }, \"response\": \[\] }, { \"name\": \"user/location\",
\"request\": { \"method\": \"GET\", \"header\": \[\], \"url\": {
\"raw\":
\"https://locationservice.dailyhunt.in/global/v1/user/location?appId=DH_APP&clientId=1297546146\",
\"protocol\": \"https\", \"host\": \[ \"locationservice\",
\"dailyhunt\", \"in\" \], \"path\": \[ \"global\", \"v1\", \"user\",
\"location\" \], \"query\": \[ { \"key\": \"appId\", \"value\":
\"DH_APP\" }, { \"key\": \"latitude\", \"value\": \"15.03\",
\"disabled\": true }, { \"key\": \"longitude\", \"value\":
\"74.0//global/v1/user/location?appId=DH_APP\", \"disabled\": true }, {
\"key\": \"clientId\", \"value\": \"1297546146\" } \] } }, \"response\":
\[\] }, { \"name\": \"getConstituencyByPincode\", \"request\": {
\"method\": \"GET\", \"header\": \[\] }, \"response\": \[\] }, {
\"name\": \"getBytext Copy 2\", \"request\": { \"method\": \"POST\",
\"header\": \[\], \"body\": { \"mode\": \"raw\", \"raw\": \"\[\\n {\\n
\\\"city\\\": \\\"berhampore\\\",\\n \\\"state\\\": \\\"west
bengal\\\",\\n \\\"country\\\" : \\\"India\\\"\\n }\\n\]\", \"options\":
{ \"raw\": { \"language\": \"json\" } } }, \"url\": { \"raw\":
\"https://locationservice.dailyhunt.in/global/v1/search\", \"protocol\":
\"https\", \"host\": \[ \"locationservice\", \"dailyhunt\", \"in\" \],
\"path\": \[ \"global\", \"v1\", \"search\" \] } }, \"response\": \[\]
}, { \"name\": \"New Request\", \"request\": { \"method\": \"GET\",
\"header\": \[\] }, \"response\": \[\] }, { \"name\": \"gps latest\",
\"request\": { \"method\": \"GET\", \"header\": \[\] }, \"response\":
\[\] } \] }, { \"name\": \"stage\", \"item\": \[ { \"name\":
\"healthcheck\", \"request\": { \"method\": \"GET\", \"header\": \[\],
\"url\": { \"raw\":
\"http://10.52.0.17:8080/global/v1/healthcheck?appId=dh_mena\",
\"protocol\": \"http\", \"host\": \[ \"10\", \"52\", \"0\", \"17\" \],
\"port\": \"8080\", \"path\": \[ \"global\", \"v1\", \"healthcheck\" \],
\"query\": \[ { \"key\": \"appId\", \"value\": \"dh_mena\" } \] } },
\"response\": \[\] }, { \"name\": \"getCountryByIso\", \"request\": {
\"method\": \"GET\", \"header\": \[\], \"url\": { \"raw\":
\"http://10.52.0.17:8080/global/v1/countries/?iso_code=ae&appId=dh_mena\",
\"protocol\": \"http\", \"host\": \[ \"10\", \"52\", \"0\", \"17\" \],
\"port\": \"8080\", \"path\": \[ \"global\", \"v1\", \"countries\", \"\"
\], \"query\": \[ { \"key\": \"iso_code\", \"value\": \"ae\" }, {
\"key\": \"appId\", \"value\": \"dh_mena\" } \] } }, \"response\": \[\]
}, { \"name\": \"SearchByGPS\", \"request\": { \"method\": \"GET\",
\"header\": \[\], \"url\": { \"raw\":
\"http://10.52.0.17:8080/v2/location?clientId=1358478461&latitude=22.9361383&appId=DH_APP&cellid=290325&mcc=405&longitude=86.7004092&lac=15\",
\"protocol\": \"http\", \"host\": \[ \"10\", \"52\", \"0\", \"17\" \],
\"port\": \"8080\", \"path\": \[ \"v2\", \"location\" \], \"query\": \[
{ \"key\": \"mnc\", \"value\": \"861\", \"disabled\": true }, { \"key\":
\"clientId\", \"value\": \"1358478461\" }, { \"key\": \"latitude\",
\"value\": \"22.9361383\" }, { \"key\": \"ip\", \"value\":
\"172.30.33.87\", \"disabled\": true }, { \"key\": \"appId\", \"value\":
\"DH_APP\" }, { \"key\": \"cellid\", \"value\": \"290325\" }, { \"key\":
\"mcc\", \"value\": \"405\" }, { \"key\": \"longitude\", \"value\":
\"86.7004092\" }, { \"key\": \"lac\", \"value\": \"15\" } \] } },
\"response\": \[\] }, { \"name\": \"SearchByIp\", \"request\": {
\"method\": \"GET\", \"header\": \[\], \"url\": { \"raw\":
\"http://10.52.0.17:8080/global/v1/location/search?appId=dh_mena&ip=104.166.173.233\",
\"protocol\": \"http\", \"host\": \[ \"10\", \"52\", \"0\", \"17\" \],
\"port\": \"8080\", \"path\": \[ \"global\", \"v1\", \"location\",
\"search\" \], \"query\": \[ { \"key\": \"appId\", \"value\":
\"dh_mena\" }, { \"key\": \"ip\", \"value\": \"104.166.173.233\" } \] }
}, \"response\": \[\] }, { \"name\": \"Search bY Ip and GPS\",
\"request\": { \"method\": \"GET\", \"header\": \[\], \"url\": {
\"raw\":
\"http://10.52.0.17:8080/global/v1/location/search?appId=dh_mena&ip=104.166.173.233&latitude=25.1567&longitude=56.3356&ip=43.247.156.26\",
\"protocol\": \"http\", \"host\": \[ \"10\", \"52\", \"0\", \"17\" \],
\"port\": \"8080\", \"path\": \[ \"global\", \"v1\", \"location\",
\"search\" \], \"query\": \[ { \"key\": \"appId\", \"value\":
\"dh_mena\" }, { \"key\": \"ip\", \"value\": \"104.166.173.233\" }, {
\"key\": \"latitude\", \"value\": \"25.1567\" }, { \"key\":
\"longitude\", \"value\": \"56.3356\" }, { \"key\": \"ip\", \"value\":
\"43.247.156.26\" } \] } }, \"response\": \[\] }, { \"name\": \"prom\",
\"request\": { \"method\": \"GET\", \"header\": \[\], \"url\": {
\"raw\": \"\" } }, \"response\": \[\] }, { \"name\": \"New Request\",
\"request\": { \"method\": \"GET\", \"header\": \[\], \"url\": {
\"raw\": \"\" } }, \"response\": \[\] }, { \"name\": \"getBytext Copy
3\", \"request\": { \"method\": \"POST\", \"header\": \[\], \"body\": {
\"mode\": \"raw\", \"raw\": \"\[\\n {\\n \\\"city\\\":
\\\"bengaluru\\\",\\n \\\"state\\\": \\\"karnataka\\\",\\n
\\\"country\\\": \\\"india\\\"\\n }\\n\]\", \"options\": { \"raw\": {
\"language\": \"json\" } } }, \"url\": { \"raw\":
\"http://10.52.0.17:8080/global/v1/search\", \"protocol\": \"http\",
\"host\": \[ \"10\", \"52\", \"0\", \"17\" \], \"port\": \"8080\",
\"path\": \[ \"global\", \"v1\", \"search\" \] } }, \"response\": \[\]
}, { \"name\": \"pelias stage\", \"request\": { \"method\": \"GET\",
\"header\": \[\], \"url\": { \"raw\": \"\" } }, \"response\": \[\] }, {
\"name\": \"user location\", \"request\": { \"method\": \"GET\",
\"header\": \[\], \"url\": { \"raw\":
\"http://10.52.0.17:8080/global/v1/user/location?appId=dh_mena&clientId=674999\",
\"protocol\": \"http\", \"host\": \[ \"10\", \"52\", \"0\", \"17\" \],
\"port\": \"8080\", \"path\": \[ \"global\", \"v1\", \"user\",
\"location\" \], \"query\": \[ { \"key\": \"appId\", \"value\":
\"dh_mena\" }, { \"key\": \"clientId\", \"value\": \"674999\" } \] } },
\"response\": \[\] }, { \"name\": \"fastget\", \"request\": {
\"method\": \"GET\", \"header\": \[\], \"url\": { \"raw\":
\"http://localhost:8080/global/v3/search/?ip=\", \"protocol\": \"http\",
\"host\": \[ \"localhost\" \], \"port\": \"8080\", \"path\": \[
\"global\", \"v3\", \"search\", \"\" \], \"query\": \[ { \"key\":
\"ip\", \"value\": \"\" } \] } }, \"response\": \[\] }, { \"name\":
\"api manipulate location Copy\", \"request\": { \"method\": \"GET\",
\"header\": \[\], \"url\": { \"raw\":
\"http://10.52.0.17:8080/api/manipulateLocation?client=dh.Y05ZMFVuRzh3L2hiYjVLSkdqTGxyZz09A&city=gurgaon&cityId=c13_278&stateId=s13&countryId=85632469&state=haryana&country=india\",
\"protocol\": \"http\", \"host\": \[ \"10\", \"52\", \"0\", \"17\" \],
\"port\": \"8080\", \"path\": \[ \"api\", \"manipulateLocation\" \],
\"query\": \[ { \"key\": \"client\", \"value\":
\"dh.Y05ZMFVuRzh3L2hiYjVLSkdqTGxyZz09A\" }, { \"key\": \"city\",
\"value\": \"gurgaon\" }, { \"key\": \"cityId\", \"value\": \"c13_278\"
}, { \"key\": \"stateId\", \"value\": \"s13\" }, { \"key\":
\"countryId\", \"value\": \"85632469\" }, { \"key\": \"state\",
\"value\": \"haryana\" }, { \"key\": \"country\", \"value\": \"india\" }
\] } }, \"response\": \[\] } \] }, { \"name\": \"dev\", \"item\": \[ {
\"name\": \"healthcheck\", \"request\": { \"method\": \"GET\",
\"header\": \[\], \"url\": { \"raw\":
\"http://localhost:8000/healthcheck\", \"protocol\": \"http\", \"host\":
\[ \"localhost\" \], \"port\": \"8000\", \"path\": \[ \"healthcheck\" \]
} }, \"response\": \[\] }, { \"name\": \"getLocationByID\", \"request\":
{ \"method\": \"GET\", \"header\": \[\], \"url\": { \"raw\":
\"http://localhost:8080/global/v1/locations?id=85632573&children=true\",
\"protocol\": \"http\", \"host\": \[ \"localhost\" \], \"port\":
\"8080\", \"path\": \[ \"global\", \"v1\", \"locations\" \], \"query\":
\[ { \"key\": \"id\", \"value\": \"85632573\" }, { \"key\":
\"children\", \"value\": \"true\" } \] } }, \"response\": \[\] }, {
\"name\": \"getByip\", \"request\": { \"method\": \"GET\", \"header\":
\[\] }, \"response\": \[\] }, { \"name\": \"search by gps\",
\"request\": { \"method\": \"GET\", \"header\": \[\], \"url\": {
\"raw\":
\"https://locationservice.dailyhunt.in/global/v1/location/search?appId=gcp&longitude=81.9&latitude=25.2&\",
\"protocol\": \"https\", \"host\": \[ \"locationservice\",
\"dailyhunt\", \"in\" \], \"path\": \[ \"global\", \"v1\", \"location\",
\"search\" \], \"query\": \[ { \"key\": \"appId\", \"value\": \"gcp\" },
{ \"key\": \"longitude\", \"value\": \"81.9\" }, { \"key\":
\"latitude\", \"value\": \"25.2\" }, { \"key\": \"\", \"value\": null }
\] } }, \"response\": \[\] }, { \"name\": \"prometheus\", \"request\": {
\"method\": \"GET\", \"header\": \[\] }, \"response\": \[\] }, {
\"name\": \"pelias\", \"request\": { \"method\": \"GET\", \"header\":
\[\] }, \"response\": \[\] }, { \"name\": \"caceMetrics\", \"request\":
{ \"method\": \"GET\", \"header\": \[\] }, \"response\": \[\] }, {
\"name\": \"New Request\", \"request\": { \"method\": \"GET\",
\"header\": \[\] }, \"response\": \[\] }, { \"name\": \"pelias\",
\"request\": { \"method\": \"GET\", \"header\": \[\] }, \"response\":
\[\] }, { \"name\": \"getBytext\", \"request\": { \"method\": \"POST\",
\"header\": \[\], \"body\": { \"mode\": \"raw\", \"raw\": \"\[\\n {\\n
\\\"city\\\": \\\"bengaluru\\\",\\n \\\"state\\\": \\\"karnataka\\\",\\n
\\\"country\\\": \\\"india\\\"\\n }\\n\]\", \"options\": { \"raw\": {
\"language\": \"json\" } } }, \"url\": { \"raw\":
\"http://localhost:8080/global/v1/search\", \"protocol\": \"http\",
\"host\": \[ \"localhost\" \], \"port\": \"8080\", \"path\": \[
\"global\", \"v1\", \"search\" \] } }, \"response\": \[\] }, { \"name\":
\"getBytext Copy\", \"request\": { \"method\": \"POST\", \"header\":
\[\], \"body\": { \"mode\": \"raw\", \"raw\": \"\[\\n {\\n \\\"city\\\":
\\\"bengaluru\\\",\\n \\\"state\\\": \\\"karnataka\\\",\\n
\\\"country\\\": \\\"india\\\"\\n }\\n\]\", \"options\": { \"raw\": {
\"language\": \"json\" } } }, \"url\": { \"raw\":
\"http://localhost:8080/global/v1/search\", \"protocol\": \"http\",
\"host\": \[ \"localhost\" \], \"port\": \"8080\", \"path\": \[
\"global\", \"v1\", \"search\" \] } }, \"response\": \[\] }, { \"name\":
\"api manipulate location\", \"request\": { \"method\": \"GET\",
\"header\": \[\], \"url\": { \"raw\":
\"http://10.52.0.20:6193/api/manipulateLocation\", \"protocol\":
\"http\", \"host\": \[ \"10\", \"52\", \"0\", \"20\" \], \"port\":
\"6193\", \"path\": \[ \"api\", \"manipulateLocation\" \] } },
\"response\": \[\] } \] } \] }
