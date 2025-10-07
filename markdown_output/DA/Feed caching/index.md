Status: DRAFTYellow

# Intro

1.  Client has an additional cache-layer for feed calls (because feeds
    calls could be `POST` & [OkHttp does not cache POST
    calls](https://github.com/square/okhttp/blob/1ed8308feae1cf2f61950a993aa43116f2a50fc7/okhttp/src/jvmMain/kotlin/okhttp3/Cache.kt#L210)).
    This cache is referred as **feed-cache** in the rest of the page
    below

2.  feed-cache is based on`LRU` (url is the key) and can\'t be
    controlled by `Cache-Control` headers

3.  Client does not cache error responses (204 is treated as error)

# 1st page

1.  Cache and Network are hit in parallel and responses are merged (Rx
    `mergeDelayError`)

2.  Some configurable delay is added before using cached-response, so
    that, if network-response comes by that time, there is no need to
    show cache (and then immediately replace with network-response)

# Next page

1.  Always served from feed-cache, if available. Else, network call will
    be made.

2.  BE may add a `salt` in the `nextPageUrl` as way to control whether
    to use or skip cache.

# Misc

- Proposal to process `Cache-Control` headers for feed-cache:
  [DHANDROID-4896](https://jira.newshunt.com/browse/DHANDROID-4896)
