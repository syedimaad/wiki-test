notification → if possible, prefetch and cache evergreen campaigns
(independent of zones) for all users → store campaign-zone map for such
evergreen campaigns → render for thin users and low network users

1.  Communicate to app to identify thin/regular user

2.  With every request for evergreen ads, CDN to respond back with a
    list of evergreen ads with a permissible refresh interval for the
    whole snapshot and priority to rotate ads within the same zone.

    1.  Client to make the adrequest for evergreen campaigns only after
        the cache TTL expires.

3.  Write a process that periodically refreshes the CDN snapshot with
    evergreen campaign details.

4.  Client-side regeneration of dynamic parameters on top of static cdn
    response during the render time - eg: client_id, md5, etc.

5.  Client can reuse the same snapshot by rotating the ads using the
    priority field sent back by adengine until the TTL.

6.  Ads tech to come up with priority calculations for evergreen ads.
