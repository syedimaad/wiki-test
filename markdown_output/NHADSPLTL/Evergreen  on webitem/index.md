# Requirements

supports evergreen ads on web-items.

# Client Changes

client need to expose below functions

1.  getEvergreenImpressionTimout()

    1.  returns timeout for regular ad request

2.  getEvergreenAd(zone, subSlot = DEFAULT)

    1.  returns ad for given zone and subslots

3.  onAdViewed(adId)

    1.  Increment fcap counter at client

4.  onAdInserted(adId)

    1.  increase soft counter

5.  isFcapMet(adId)

    1.  Check if fcap is met or not for given adId.

# AdTag Changes

adTag will wait for response till **evergreen timeout**. Once it's reach
timeout, adTag will call **getEvergreenAd(zone, subSlot = DEFAULT)** and
tries to render ad. Before inserting into DOM, adtag will check whether
fcap is met or not using **isFcapMet(adId)**. If fcap is not met then
adtag will insert ad into DOM and call **onAdInserted(adId)**. If
evergreen ad is viewed, adTag will call **onAdViewed(adId)**.

# Daedalus Changes

DD allow webzone for evergreen campaign.
