  ----------------------- -----------------------------------------------------------------------------
  **Ad feature Status**   READYGreen
  **Adtech POC**          / & / & /
  **GTM & Product POC**   @<sandeep.naug@verse.in> & \@sanchit.gupta@verse.in
  **Ad format**           In-Stream video Ad \[Custom Vmap\] \| Masthead \| Swivel card \| Std banner
  ----------------------- -----------------------------------------------------------------------------

**Platform & Ad properties**

+--------------+---------------------------+---------------------------+
| **Platform** | **Ad properties**         | **Zone & Subslot**        |
+--------------+---------------------------+---------------------------+
| **JOSH**     | NA                                                    |
+--------------+---------------------------+---------------------------+
| **DH**       | Masthead                  | Web-5                     |
|              +---------------------------+---------------------------+
|              | Swivel (Live Score card   | Web-3                     |
|              | Ticker)                   |                           |
|              +---------------------------+---------------------------+
|              | STD Banner                | Web-3                     |
|              +---------------------------+---------------------------+
|              | IIFA Live content video   | Web-3                     |
|              +---------------------------+---------------------------+
|              | In-Stream Video           | In-Stream Video \[On Live |
|              |                           | stream via- Server        |
|              |                           | default topic + For You\] |
+--------------+---------------------------+---------------------------+

##  Executive Summary

We have developed a capability to monetise events (Live stream similar
to TV for IIFA screening) for Dailyhunt Platform via integrating custom
Vmap with the Live stream in addition to Ad banners like Masthead,
Standard banner & Swivel.

**Targeted Zone, Topic, supported Dimensions** : refer the document -
[https://docs.google.com/spreadsheets/d/1sjAF6ESMqefXrOo0n6TPly-tAlf_zUZNqgDYvYSICcc/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1sjAF6ESMqefXrOo0n6TPly-tAlf_zUZNqgDYvYSICcc/edit?usp=sharing){card-appearance="inline"}

##  Configuration instructions (for Adops) :

Please refer to the complete campaign configuration -
[https://drive.google.com/file/d/1gObsZzpOZNl2A3lB4Iv6MIDB5BeeVN-I/view?usp=sharing](https://drive.google.com/file/d/1gObsZzpOZNl2A3lB4Iv6MIDB5BeeVN-I/view?usp=sharing){card-appearance="inline"}

##  Note

1.  **For In-stream only (Via custom VMAP)**

    1.  Get the pre-defined Ad marked from the GTM team.

    2.  Create In-stream Video Ads under DD campaign configuration and
        [DO NOT ACTIVATE]{style="color: rgb(191,38,0);"} the
        campaign/creative.

    3.  Build Vmap using path : DD\>\>TOOLS\>\>VMAP Configurations (for
        Video alignment and configuration)

    4.  No Targeting is available, No Fcap, No Impression cap

    5.  Try and avoid adding too many Ads in the single Segment / Ad
        break.

    6.  Each time user visits the Live stream, Stream will be started
        from the beginning (so does the Ads in VMAP).

    7.  Known observation : On IOS, User can seek the stream by going
        into Fullscreen mode (and it is IOS behaviour).

2.  **For Live stream video (IIFA Server default topic)**

    1.  Make sure to create campaign and use updated HTML (with relevant
        Video ID and details),[ failing to do so will not have
        Livestream Video on server default
        topic]{style="color: rgb(191,38,0);"} (and we cant place
        in-stream video Ad). This set up need to be completed well in
        advance.

## Specification

*Article specification :*
[http://adspecs.dailyhunt.in/static_ads/dailyhunt_ad_spec/article.html](http://adspecs.dailyhunt.in/static_ads/dailyhunt_ad_spec/article.html){card-appearance="inline"}
(will be added here)
