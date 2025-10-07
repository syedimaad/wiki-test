## [Product Doc](https://docs.google.com/document/d/1PkN-FqQHLpLxptVBXRRqQM5oNhG-4MRIp4gp4LNrcE4/edit?usp=sharing) Requirements:

### Image Ads:

- Allow upload of all formats of images \[PNG, JPEG, GIF\]

- Allow upload of images with different file size

- Image resolutions should be configurable

- Configurable header/sponsor text

  - Predefined tags: \[ "Advertisement", "Ad", "Sponsored", 
    "Collaboration",  "Partnership"\]

  - Default tag: Sponsored

- Configurable description(title + hashtag) text

### Video Ads:

- Allow upload of all formats of videos \[.MP4\]

- Allow upload of videos with different file size 

- Video resolutions should be configurable

- Configurable header/sponsor text

  - Predefined tags: \[ "Advertisement", "Ad", "Sponsored", 
    "Collaboration",  "Partnership"\]

  - Default tag: Sponsored

- Configurable description(title + hashtag) text

### **Configurable CTA**

- CTA texts can be\
  \[ `Download`, `Shop Now`, `Watch Now`, `Subscribe`,
  `Get Tickets Now`, `Learn More, ...etc` \]

- Max Length of CTA text = 30 Char long.

- Configurable colour (ARGB value) & Opacity for the CTA button, text

  - Default RGB value for CTA button: White (RGB - 255,255,255)

  - Default RGB value for CTA text: Black (RGB - 000)

  - Default CTA button opacity (%): 100%

- CTA Animation

  1.  A flag to enable/disable CTA Animation

  2.  BE configurable initial and final colour of animation (opacity
      value + hex code)

      - Default initial colour of CTA button = #66FFFFFF

      - Default initial color of CTA text = #FFFFFF

      - Default final colour of CTA button = #FFEA4E60

      - Default final color of CTA text = #FFFFFF

      - Default `initialButtonOpacity` = 40%

      - Default `finalButtonOpacity` = 100%

  3.  BE configurable start and end time of animation

      - Start time of animation (default): 2 sec (for video ad 3 sec)

      - End time of animation (default): 3 sec (for video ad 4 sec)

- Configurable Dimensions, Font Size & Font type (within range defined)

  1.  ~~Maximum width: 328 px (Default)~~

  2.  Default & minimum margin: 16 px

  3.  Default height: 40 px (Not configurable)

  4.  Default font size: 14 px

  5.  Default font type (BOLD/REGULAR): Bold

- Ads shareability

  1.  Includes a link to the app in share text\
      e.g. Download Josh for more videos like this!\
      [https://m.myjosh.in/6OaT/6d76ce25](https://m.myjosh.in/6OaT/6d76ce25){card-appearance="inline"}

- Allow all URLs for CTA\
  ex. Internal app links, external websites, deeplinks, deferred deep
  links etc

- Swipe up animation (Not required for video ads)

  1.  Show a popup from next video to nudge the user to watch more

  2.  The popup includes a part of the next video to be played

  3.  Animation starts after user has watched the ad for 3 sec (This
      time is configurable).

  4.  Applied only to the 1st static ad in the feed

### Ad Response for CTA

{ \"swipeUpDelay\": 3000, // (exclude this for video ads) \"content\": {
\"itemSubtitle2\": { \"color\": \"#FFFFFF\", \"bg-color\": \"#EA4E60\",
\"data\": \"Click Here\", \"isPopupView\": true, \"isAnimated\": true,
\"animationConfig\": { \"initialButtonColor\": \"#66FFFFFF\",
\"finalButtonColor\": \"#FFEA4E60\", \"initialTextColor\": \"#FFFFFF\",
\"finalTextColor\": \"#FFFFFF\", \"startTime\": 2000, \"endTime\": 3000
}, \"dimension\": { \"margin\": \"16\", \"fontSize\": 14, \"fontType\":
\"BOLD\", } } } }

### Additional Changes (Only CTA controllable from ads BE)

1.  Control of visibility of all elements of the screen to be with back
    end

    1.  Default visibility of engagement buttons - ON

    2.  Default visibility of CTA: ON

    3.  Default visibility of header: ON

    4.  Default visibility of description: ON

    5.  Default visibility of 3 dots: ON

    6.  Default visibility of Follow button: ON

    7.  Default visibility of camera icon (on top right): ON

    8.  Default visibility of account name: ON

    9.  Default visibility of Josh icon + 'For you' drop down: ON

    10. Default visibility of mute icon: ON (for video ad)

### Daedalus Changes:

1.  To support diff img extensions (Check with Himanshi)

2.  Allow all video format (Check with Himanshi)

3.  Image upload size threshold set to be 30 MB and create guidelines
    for ads ops =\> DD

4.  Limit max length of CTA text to 30 Char long.

5.  Configurable header/sponsor text

    - Predefined tags: \[ "Advertisement", "Ad", "Sponsored", 
      "Collaboration",  "Partnership"\]

    - Default tag: Sponsored

6.  Configurable colour for the CTA button.

    1.  Introduce colour picker for CTA.

    2.  Right now there are 4 predefined CTA colours, need to allow any
        colour.

    3.  Option to choose opacity

7.  CTA Animation

    1.  Need a flag `isAnimated` to enable/disable CTA animation

        1.  Default false

    2.  Configurable initial and final colour of animation

        - Default `` `initialButtonColor` `` = #66FFFFFF (opacity
          value + hex code)

        - Default `` `finalButtonColor` `` = #FFEA4E60 (opacity value +
          hex code)

        - Default `initialTextColor` = #FFFFFF

        - Default `finalTextColor` = #FFFFFF

        - Default `initialButtonOpacity` = 40%

        - Default `finalButtonOpacity` = 100%

    3.  Configurable start and end time of animation

        - `startTime` of animation (default): 2000 ms

        - `endTime` of animation (default): 3000 ms

8.  Configurable dimensions & Font Size for CTA (within range defined)

    1.  ~~width~~

        - ~~Default & Maximum width: 328 px~~

    2.  `margin`

        - Default and min: 16 px

    3.  `fontSize`

        - Default font size: 14 px

    4.  `fontType` (BOLD/REGULAR)

        1.  Default : `"BOLD"`

9.  Need a flag to show swipe up animation (Not required for video ads)

    1.  `showSwipeUpAnimation` Default value `true`

    2.  If above flag is true then add `"swipeUpDelay": 3000,` Default
        value 3000 ms
