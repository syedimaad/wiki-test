**new endpoint:**

`/global/v1/location/search?mnc=15&clientId=981485795&latitude=52.204264&ip=185.69.144.244&appId=DH_APP&cellid=2158090&mcc=234&longitude=-3.0274569&lac=57414`

**Functionality :**

Location service will resolve the **best understanding of location
based** on the input params as in order :

1.  lat/long

2.  cell_id

3.  clientId

4.  ip

*lat/long will have the highest priority where as ip will have the least
property. Also, if clientId will have the IP as source we can ignore
that and use the location resolved via IP in request.*

→ Move the update in redis task to locationItself.

\*if request Param contains `multiget=true` then we can return list of
location object resolved via all set of input params.

**Use cases:**\
1. If any consumer wants the location understanding of any user, they
can send only clientId in request param.

2\. If any consumer wants the best location of any user, they can send
all available params at their end.

3\. If any consumer wants the list location for any user, they can send
all available params at their end, with **multiget=true**. (mostly debug
case).

This will bring the location intelligence at one place, removing the
location identification/learning job away from different teams and it
can act as a single source of truth.
