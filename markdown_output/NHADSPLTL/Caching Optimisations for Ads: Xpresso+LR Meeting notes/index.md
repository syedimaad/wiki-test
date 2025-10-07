##  Date

##  Participants

List meeting participants using their @ mention names

- 
- 
- 
- 
- 
- 
- 
- 
- 
- 
- 
- 

##  Goals

To discuss the list of action items for the requirement of optimising
the first content of the Xpresso tab.

##  Action items

Android:

1.  Ads BE to honour `homeTab` param in the cacheRefresh to send only
    one Ad of the non-homeTab zones.

2.  App to add 3 new params `section` and `subSlot` to the cacheRefresh
    call based on where the user is browsing currently.

3.  Ads BE to honour `section` and `subslot` to respond with more of the
    current tab Ads.

4.  Ads BE can respond with one Ad for the first zone of each section,
    for the BG call.

5.  Ads BE to validate if we can send out a SDK Ad for non-current
    section zone. Because it might lead to increased requests without
    impressions.

6.  Ads BE to respond with Xpresso Ads only for 25.0.0 and above.

7.  Ads BE to respond with relevant section\'s adSpecs in each response.

IOS:

1.  App to prefetch `card-p0` if the homeTab is XPR.

##  Decisions

TBD

ba0cce9e-0a4a-438a-b835-79e8b016da83DECIDED7b51862b-44e5-4bca-a573-c4c65ca2a8e5
