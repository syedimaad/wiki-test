:dart:1f3af🎯#DEEBFF

Objective

To be able to measure how much engagement in happening on cached-feed?

SCV, SLV

- already `is_cached` param is flowing. No changes needed

SPV

- A new event paam `feed_card_cached=true` should flow when - the feed
  from which the SPV happened is cached.

- if the list was from network or notification/deeplink flow - this
  value will be `false`, and hence not passed (`false` is not explicitly
  passed)

- 1st engagement param full_page_loaded is not flowing correctly. Fixed.
  Below is expected value

  - if article has only 1 chunk -\> true

  - if article has both chunks -\> if 2nd chunk loaded: true, else false
    (should work both for text and rich_text stories)

## How to test

1.  Cached flow

+-----------------------+-----------------------+-------------------------+
| **Flow**              | **event**             | **param**               |
+-----------------------+-----------------------+-------------------------+
| Open without          | SLV                   | `isCached=true`         |
| internet. Shows       |                       |                         |
| cached feed           |                       |                         |
+-----------------------+-----------------------+-------------------------+
| Turn on internet \>   | SPV                   | `feed_card_cached=true` |
| Click on the card \>  |                       |                         |
| Back                  |                       | full_page_loaded=true   |
|                       |                       | (if opened without      |
|                       |                       | internet, it will be    |
|                       |                       | false)                  |
+-----------------------+-----------------------+-------------------------+
| Exit                  | SCV                   | `isCached=true`         |
+-----------------------+-----------------------+-------------------------+

2.  Network flow: Repeat above with internet: is_cached &
    feed_card_cached will be false/null

## Links

1.  [jira](https://jira.newshunt.com/browse/DHANDROID-4959)

2.  [https://docs.google.com/spreadsheets/d/15JHbmAY4g8-ElUicgqEuZa0v2wRjPehKQ2hbjvLdqJ4/edit#gid=753959072](https://docs.google.com/spreadsheets/d/15JHbmAY4g8-ElUicgqEuZa0v2wRjPehKQ2hbjvLdqJ4/edit#gid=753959072){card-appearance="inline"}
    instrumenation sheet
