# Summary of changes

First read:
[https://evp.atlassian.net/wiki/spaces/NEWSBE/pages/404127757/Cricket+Zone+V2+-+Client-+News+BE+Protocol+Doc#Infinite-commentary](https://evp.atlassian.net/wiki/spaces/NEWSBE/pages/404127757/Cricket+Zone+V2+-+Client-+News+BE+Protocol+Doc#Infinite-commentary){card-appearance="inline"}

1.  Ball-by-ball commentary section content:

    1.  paginate as the user scrolls (new)

    2.  refresh the cards on the top (existing)

2.  Support any type of card

    1.  2 specific cards are asked

3.  Ads will be restricted in the **ball by ball commentary** section.
    Once the commentary starts, only moment marketing ads will be
    allowed.

    1.  BE will send a marker along with content- it marks beginning of
        commentary

4.  While user is on the page, refresh happens periodically and nothing
    will be missed

5.  If user returns after the sometimes, there could be gap of few overs
    from current to what is available. In those cases, discard the
    old-data and paginate fresh (on the latest page). Other approaches -

    1.  If he returns after longer, auto pullToRefresh may be triggered
        (suggested by, not confirmed)

    2.  Also we can find any good way to fill up the missing cards (not
        mandatory)

6.  Stream-update should allow adding/modify/delete content

    1.  currently only modify is supported

7.  Current collection (ball-by-ball commentary) will continue to be
    supported.

    1.  BE should be able to serve either of them. Client supports both

8.  Nudge to scrollToTop when new content is fetched to be built. It
    needs to be shown when user scrolled few cards. It is not a CTA to
    refresh.

9.  recentBalls array could be used to detect if page needs to be
    refreshed and user to be sent to top of commentary on resume. Same
    could also be used to nudge the user to go to top as well.

# Implementation

1.  We always delete cards and insert (just modify will not suffice, as
    they want to change the order)

2.  When we need to insert/delete cards - `fetch_data` table

    1.  starting from commentary marker delete till last matching card.

    2.  if no matching card, delete everything after marker

    3.  insert new cards

3.  When replacing full-page, it npUrl is used. Once pagination begins,
    it takes priority

## New UI asks

Card to deeplink to comments page

Header card. Can reuse new header card we developed?

Nudge to scroll to top

## scroll issue caused by StickyHeaderImplementation

1.  after few pages, it resets scroll to some position

2.  reverted sticky header layout manager changes

3.  created another recycler view to stickycards; existing one will
    render them invisible

4.  <https://jira.newshunt.com/browse/DHANDROID-4931>
