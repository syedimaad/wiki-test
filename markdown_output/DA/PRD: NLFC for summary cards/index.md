  --------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Document Status**   READYGreen
  **Collaborators**     
  **jira**              DHANDROID-252e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA
  **protocol**          [https://evp.atlassian.net/wiki/spaces/NEWSBE/pages/429424901/Xpresso+2.0+NBE+-+Client+protocol#Xpresso-config-in-Handshake](https://evp.atlassian.net/wiki/spaces/NEWSBE/pages/429424901/Xpresso+2.0+NBE+-+Client+protocol#Xpresso-config-in-Handshake){card-appearance="inline"}
  --------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

------------------------------------------------------------------------

------------------------------------------------------------------------

# 1. Xpr section

Implementation is same as prev AMPs

# 2. LR feed

## a. Configs

+-----------------------+-----------------------+-----------------------+
| **name**              | **usage**             | **default**           |
+-----------------------+-----------------------+-----------------------+
| V                     | percentage of card    | 70 (70%)              |
|                       | that should be        |                       |
|                       | visible for it to be  |                       |
|                       | eligible for nlfc.    |                       |
|                       |                       |                       |
|                       | Note: *this is        |                       |
|                       | different from SCV    |                       |
|                       | timespent timer, and  |                       |
|                       | is applicable only to |                       |
|                       | summary-cards, for    |                       |
|                       | NLFC purpose only*    |                       |
+-----------------------+-----------------------+-----------------------+
| R                     | ts duration to        | 15 (15 seconds)       |
|                       | trigger with nlfc     |                       |
|                       | request               |                       |
+-----------------------+-----------------------+-----------------------+
| D                     | ts duration to insert | 20 (20 seconds)       |
|                       | fetched nlfc          |                       |
+-----------------------+-----------------------+-----------------------+

note

Note:

1.  V -\> should be minimum 70%, to make sure 2 timers don't run at the
    same time

2.  (D - R) should be atleast 5sec; allow enough time for API call to
    complete

:::: {.panel .conf-macro .output-block style="background-color: rgb(234,230,255);border-color: rgb(153,141,217);border-width: 1.0px;"}
::: {.panelContent style="background-color: rgb(234,230,255);"}
Note:

1.  V -\> should be minimum 70%, to make sure 2 timers don't run at the
    same time

2.  (D - R) should be atleast 5sec; allow enough time for API call to
    complete
:::
::::

## b. Behaviour

1.  if \>V% of a (summary)card (say [S1]{style="color: rgb(191,38,0);"})
    is visible, start a timer

    1.  if and when visibility becomes \<V% (card is scrolled away) =\>
        pause the timer. if again visibility becomes \>V%, resume timer

2.  When timer reaches [R]{style="color: rgb(191,38,0);"}, trigger
    NLFC-API-call, & keep it ready

3.  When timer reaches [D]{style="color: rgb(191,38,0);"}, & nlfc is
    ready → this can happen when card is visible; insert nlfc below the
    card

    1.  ~~if feed is not scrolling; say~~
        [~~C1~~]{style="color: rgb(191,38,0);"} ~~is the
        last-visible-card~~

        1.  ~~if
            absolutePositionOf(~~[~~C1~~]{style="color: rgb(191,38,0);"}~~)
            \>
            absolutePositionOf(~~[~~S1~~]{style="color: rgb(191,38,0);"}~~)
            =\>~~ **~~insert before C1~~**

        2.  ~~else~~ **~~insert after S1~~**

    2.  ~~if feed is scrolling; do #3a after it settles down.~~

4.  If timer never reaches [D]{style="color: rgb(191,38,0);"}, discard
    the fetched card

# 3. LR Detail

1.  Click on summary card in feed → shows LR detail; here nlfc is same
    as existing

2.  Swipe to summary card in detail page → here nlfc is same as xpresso
    section.

3.  3rd level, no nlfc
