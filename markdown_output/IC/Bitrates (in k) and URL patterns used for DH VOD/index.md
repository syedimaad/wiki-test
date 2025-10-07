**Possible patterns of the URLs for the live channel.**

1.  Supports ABR  -  If the url is a master m3u8 (Does not have {1}.m3u8
    pattern)

<https://dh.tv9.net/hlslive/Admin/px0219933/live/News_Nine/master_1.m3u8>

Live video starts playing with the first variant in master_1.m3u8 file
and than ABR comes in picture

2\. No ABR Support  -  If the url does have a pattern {1}.m3u8

EX:
<https://feed-btimes.dailyhunt.in/eternowsa/live/feedbtimes/playlist_%7B1%7D.m3u8>

Client will replace {1} based on users connection speed - If h

EX:
<https://feed-btimes.dailyhunt.in/eternowsa/live/feedbtimes/playlist_h.m3u8>

Live video for h variant is played Speed to variant mapping is done
based on the following map

\"200\" to \"slow\", //from 0 to 200Kbps

\"1000\" to \"average\", //from 200 to 1Mbps

\"2500\" to \"good\", //from 1 to 2.5Mbps

\"5000\" to \"fast\", //from 2.5 to 5Mbps

\"10000\" to \"veryfast\" //from 5 to 10Mbps

**In production, For live TV, #1 is being served . i.e Client only loads
the ABR url**
