note

Original Author:

:::: {.panel .conf-macro .output-block style="background-color: rgb(234,230,255);border-color: rgb(153,141,217);border-width: 1.0px;"}
::: {.panelContent style="background-color: rgb(234,230,255);"}
Original Author: [Deepak
Gupta](https://evp.atlassian.net/wiki/people/61f3a660e4a724006af83554?ref=confluence){.confluence-userlink
.user-mention}
:::
::::

Contents

1.  [Image quality
    header](https://evp.atlassian.net/wiki/spaces/IE/pages/722108739/iOS+Engineering#Image-quality-header)

## Image quality header

`imageq` - header to be passed in image url request, for BE to send
appropriate images based on this quality.

The quality is deduced via
`ImageSettings quality map in handshake static config`, where the key is
our current network quality, which is calculated via the Bandwidth
meter.

**Findings :-**

#F4F5F7

1.  Using ASNetworkImageNode directly, which internally uses URLSession,
    but does not provide any public APIs to added additional headers

<!-- -->

2.  Using NetworkImageNode, which is a overridden class of
    ASNetworkImageNode, where we provide a cache module which is
    DHCacheManager, which download the images basis SDImageCache
    callbacks, but does not provide any public APIs to added additional
    headers

3.  Using DHCacheManager.downloadImage, which download the image via
    NetworkManager. Here, we do have a provision to add Header.

To make this work across, we would need to streamline image download via
NetworkManager for all cases 1,2 & 3. Where we can add the header.
