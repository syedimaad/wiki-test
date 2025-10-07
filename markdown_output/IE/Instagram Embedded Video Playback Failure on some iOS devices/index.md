### Overview

We are observing issues where Instagram embedded videos, particularly
Reels, do not play on some iOS devices. This occurs across both Safari
and WKWebView implementations. The videos load with the thumbnail and
play button, but freeze or fail to load upon interaction.

This issue is observed in both **in-app WKWebView** and **Progressive
Web App (PWA)** contexts.

------------------------------------------------------------------------

### Debugging Details

When inspecting the behavior using **Safari Develop Tools**, we
encountered the following network-related errors:\
\
\[Error\] Failed to load resource: The network connection was lost.
(logging_client_events, line 0)\
<https://graph.instagram.com/logging_client_events>

\[Error\] Failed to load resource: The network connection was lost. (bz,
line 0)\
<https://www.instagram.com/ajax/bz?__d=dis>\
\
These errors indicate potential **changes in privacy policies or network
handling** between Instagram and iOS. These might relate to App Tracking
Transparency, cookie/session handling, or third-party resource loading.

> 📅 **Reference**: [Apple Developer Forum Thread on iOS 18.5 and
> Instagram Playback](https://developer.apple.com/forums/thread/792964)

### Workarounds Tried

- Disabled **\"Prevent Cross-Site Tracking\"** in Safari: ❌ No effect

- Set `allowsInlineMediaPlayback = true` in WKWebView configuration: ❌
  No effect

### Similar Reported Cases

This issue appears to impact others using Instagram embeds on different
platforms:

URL:

[http://dhunt.in/11gxpw](http://dhunt.in/11gxpw){card-appearance="inline"}
→ DH

[https://www.timesnownews.com/viral/viral-video-shows-snake-playing-dead-on-signal-internet-says-oscar-worthy-performance-article-152361952](https://www.timesnownews.com/viral/viral-video-shows-snake-playing-dead-on-signal-internet-says-oscar-worthy-performance-article-152361952){card-appearance="inline"} -
Times now

[https://zeenews.india.com/telugu/social/snake-acts-as-to-be-dead-funny-video-goes-viral-on-social-media-pa-238746](https://zeenews.india.com/telugu/social/snake-acts-as-to-be-dead-funny-video-goes-viral-on-social-media-pa-238746){card-appearance="inline"} -
Zee news

  ------------------ ---------------- ----------------------
  ** iOS version**   **iPhone**       **Behavior**
  18.5               iPhone 12        ❌ Fails to play
  18.5               iPhone 16        ❌ Fails to play
  18.5               iPhone 15 pro    ❌ Fails to play
  16.2               iPhone X         ✅ Works as expected
  18.5               iPhone 12 mini   ✅ Works as expected
  ------------------ ---------------- ----------------------

- **WordPress Community Reports**:\
  [WordPress Forum - Instagram Embeds Won\'t
  Play](https://wordpress.org/support/topic/instagram-embeds-wont-play/)

### **Conclusion**

These suggest the issue lies deeper within **Instagram\'s embed delivery
on iOS Safari/WebKit**, and not with implementation specifics.

### Suggested Mitigations

- **Add Fallback with Full Instagram URL**\
  Instead of using iframe embeds, provide a thumbnail and a link to open
  the full post directly in the Instagram app or browser. (Recommended)

- **Conditional Serving of Instagram Embeds**\
  Detect iOS version using JavaScript or user agent string and avoid
  embedding Instagram Reels for iOS 18.x. Instead, show a fallback view
  or message.
