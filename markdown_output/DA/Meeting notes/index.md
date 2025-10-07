# #1: Cricket Phase2: Infinite commentary and pre/post match feed

Wednesday, October 4**⋅**3:30 -- 4:30pm

## Pre/Post match feed

1.  when ingesting, BE will mark the card as

    1.  HTML (twitter embeds, images): client need to show in `Webview`
        or

    2.  Rich Text(bold, para etc.): client can show in `TextView`

2.  The whole card will be sent as HTML. Client will support
    `removePadding`attr similar to other cards

## infinite commentary

1.  Client supports mix of ball-by-ball commentary and pre/post update
    cards

2.  Client gets feed pre-sorted(ids) from BE, including c*ommunity
    discussion* and other cards

3.  For reverse sorting, client may have to convert float to int by
    multiplying -1000

# #2: Cricket Phase2: Infinite commentary and pre/post match feed

1.  Replace cards after the bottom match. For flexibility

    1.  solves for FP content only

    2.  NP urls will be cached on URL

    3.  If all the cards matched (order could be diff), so still
        clearAndReplace. Corner case.

    4.  Whenever some cards is inserted in-between, from that point on,
        BE need to send all the cards that happened after that
