Problem Statement: How to use the precise and ads-view of location in
location service.

**Proposed Option:**

To store the location of a user in below format.

{  \"location\":   {     \"city\" : \"sohna\",     \"cityId\" :
\"c12_123\",     \"state\" : \"harayana\",     \"stateId\" : \"s12\",
    \"mappedLocation\" : \[       {         \"city\" : \"gurgaon\",
        \"state\" : \"haryana\"       },       {          \"city\" :
\"delhi\",         \"state\" : \"New delhi\"       }     \]   } }

City/State will always be the best possible location figured out by
location service based out on the params in order (GPS/ CELL/ IP_DFP/
IP_MODEL/ IP)

**Benefits:**

We can provide two types of targeting in daedalus:

a\) Wider view : To be used in mostly tier-1 / tier-2 cities targeting
to cover larger audience base.

b\) Precise view: To be used in precisely detected location to cover
audience very precisely.

a)Wider view :

- We can match the targeted(campaign) location in union of city & mapped
  location.

- Log the matched city to kudu to cover the ad reports which will keep
  the distribution of user higher in tier-1 cities.

b\) Precise-view can be helpful to content targeting along with the
addition of locality.

**Further tasks:**

- Manually / via some script fig out the mappedLocation for each city
  based on some radius algorithm.

- To think the existence of same layering for country outside India.
  (future scope)

- To decide what to log in matched city/state attribute in case of no
  Geo targeting.(to keep tier distribution as desired.)

*[\*if possible we can add distance of mapped location along with their
name & id to give some more control over
distribution]{style="color: rgb(101,84,192);"}*

Questions and suggestions are most welcomed.
