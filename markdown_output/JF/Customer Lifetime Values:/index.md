Three type of profile are available.

YDay. 7Day and 30Day.

We are only using clv for last 14 days.

vlc1 : user_consum_type and agg_date = d+1 a and agg = \'Yday\'

Vlc2 : YDA

P+ : 800

p- : 700

G+ : 200

G-: 180

S+ : 100

S-: 70

I+ : 40

I- : 20

L+ : 10

L-: 5

ways to calculate avg = max(avg)

CLV5 = max(Avg(5 Yday), VLC1C = 7days)

OR

CLV5 = max(weighted Avg(5 Yday), CLV1C = 7days). where Days 1,2,3,4,5
weights : 5,4,3,2,1.

Ex : CLV1 : 800 and CLV2 : 700 and CLV3 : 200. weighted Average =
(800\*3 + 700\*2,200\*1)/3 \> 800

packet for Unified_user_profile

"clv_profile"{

"last_install_date": "20220607",

"client_id": "sdfsgdghfshfs",

`"profiles" : "hi" :{`

`"Yday" : {`

` "Yday1" : "Gold+",`

` "yday3" : "Platinum+",`

` "yday4" : "Platinum+" `

`},`

`"7day" :{`

` "7day1" : "GOld - ",`

` "7day3" : "GOld - ",`

` "7day4" : "GOld - "`

` }`

}

}
