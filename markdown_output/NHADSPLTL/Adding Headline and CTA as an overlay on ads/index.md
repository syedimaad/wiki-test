#### [View Product document](https://evp.atlassian.net/l/cp/2ucfECVh)

#### [Figma](https://www.figma.com/file/hdwp9MwoN1Nvb4ipYzR2tA/Ads-Master-File?node-id=1725%3A24474)

## Requirements:

1.  Allow a configuration in DD to render headline(title & description)
    and CTA as an overlay on the ad

2.  Valid for image/native image creatives only

3.  If Overlay enabled then default values are

    1.  Default Headline \--\> `BOTTOM_OVERLAY_LEFT`

    2.  Default CTA \--\> `BOTTOM_OVERLAY_RIGHT`

    3.  [default position for headline and cta in case overlay is
        disabled will be same as today.]{style="color: rgb(191,38,0);"}

4.  For non evergreen this will be an opt in and disabled by default

5.  For evergreen ads

    1.  If it is story page ad rendering above chunk 1 then

        - Overlay of `ad(i)` icon, `headline` and `CTA` to be enabled by
          default

        - To disable overlay, It will need a product approval

    2.  Otherwise this will be disabled by default

6.  For evergreen story page ad, Default Position of `Ad(i)` icon as
    `TOP_OVERLAY_RIGHT`

    1.  [default position of Ad(i) for other ads will be same as
        today]{style="color: rgb(191,38,0);"}

## Ads BE Changes:

1.  Support native image ads for evergreen

2.  For image creatives, add `position` for `itemSubtitle2` tag.

3.  For Native image creatives, add `position` in `itemTitle` ,
    `itemSubtitle1` , `itemSubtitle2` tag.

    1.  Always position for `itemTitle` & `itemSubtitle1` should be
        same.

## Ads Response

json \"content\": { \"bg-color\": \"#ffffff\", \"bg-color-night\":
\"#000000\", \"language\": \"en\", \"sourceAlphabet\": \"a\",
\"iconLink\":
\"http://qa-money.newshunt.com/daedalus-banners/1562135896/1658836112_41399_990x505.jpg\",
\"itemTitle\": { \"color\": \"#000000\", \"color-night\": \"#ffffff\",
\"data\": \"item title\", \"position\": \"BOTTOM_OVERLAY_LEFT\" },
\"itemSubtitle1\": { \"color\": \"#000000\", \"color-night\":
\"#ffffff\", \"data\": \"description\", \"position\":
\"BOTTOM_OVERLAY_LEFT\" }, \"itemSubtitle2\": { \"color\": \"#4caf79\",
\"color-night\": \"#ffffff\", \"data\": \"click\" \"position\":
\"BOTTOM_OVERLAY_RIGHT\" }, \"reportText\": { \"color\": \"#999999\",
\"color-night\": \"#FFFFFF\", \"background-color\": \"#40000000\",
\"background-color-night\": \"#40000000\", \"data\": \"Ad\" } },

## Daedalus Changes:

1.  Enable native creative types for evergreen camp

2.  DD to add two new fields for Headline and CTA Positions

    1.  Configurable Headline positions (Only applicable for native
        image creatives)

        1.  `BOTTOM_OVERLAY_LEFT`

        2.  same as today (No change)

    2.  Configurable CTA positions (For both image + native image)

        1.  `BOTTOM_OVERLAY_RIGHT`

        2.  same as today (No change)

3.  For evergreen ads

    1.  If it is story page ad rendering above chunk 1 then default
        value will be

        - Headline Position = `BOTTOM_OVERLAY_LEFT`

        - CTA Position = `BOTTOM_OVERLAY_RIGHT`

        - Ad Tag Position = `TOP_OVERLAY_RIGHT`

        - To change above value, It will need a product approval

    2.  Otherwise this will be same as today

4.  For evergreen story page ad, Default Position of `Ad(i)` icon as
    `TOP_OVERLAY_RIGHT`

    1.  [default position of Ad(i) for other ads will be same as
        today]{style="color: rgb(191,38,0);"}

5.  For non evergreen ads, this will be same as today (No change)

## Client Changes:
