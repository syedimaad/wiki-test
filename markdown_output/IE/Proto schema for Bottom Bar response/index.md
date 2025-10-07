### Current JSON Response

{ \"code\": 200, \"data\": { \"version\": \"693\", \"bgColor\":
\"#f8f8f8\", \"bgColorNight\": \"#1e1e1e\", \"sections\": \[ {
\"restrictedToMenubar\": false, \"activeIconUrlNight\":
\"https://assets-news-bcdn.dailyhunt.in/cmd/resize/#DH_EMB_IMG_REP#\_\_DHQ\_/fetchdata16/images/96/f2/24/96f2242b027b9060631410482ab5bfcc85a3f5a965e57f7288f0c75e3b9dd545.png?src=gateway\",
\"inactiveIconUrl\":
\"https://assets-news-bcdn.dailyhunt.in/cmd/resize/#DH_EMB_IMG_REP#\_\_DHQ\_/fetchdata16/images/8b/4a/ef/8b4aefa7df6c84fff4159473a79c4f166cbdd4bea9189a18cacc03f23960b30c.png?src=gateway\",
\"refreshIconUrlNight\":
\"http://acdn.newshunt.com/fetchdata/bottombar/icons/night/active/news/news_rfrsh\_#DH_EMB_IMG_REP#.png?src=newsbe\",
\"highlightColor\": \"#000000\", \"activeIconUrl\":
\"https://assets-news-bcdn.dailyhunt.in/cmd/resize/#DH_EMB_IMG_REP#\_\_DHQ\_/fetchdata16/images/a7/70/ab/a770ab6ceb63b21feabc4e98f336049612240d233f62d68de2c168da3cd0b8be.png?src=gateway\",
\"type\": \"NEWS\", \"bgColorNight\": \"\", \"bgColor\": \"\", \"id\":
\"news\", \"refreshIconUrl\":
\"http://acdn.newshunt.com/fetchdata/bottombar/icons/active/news/news_rfrsh\_#DH_EMB_IMG_REP#.png?src=newsbe\",
\"title\": \"News\", \"applicableForThinUsers\": true,
\"excludeStates\": { \"india\": \"\" }, \"highlightColorNight\":
\"#D9D9D9\", \"bgType\": \"\", \"contentUrl\": \"\",
\"inactiveIconUrlNight\":
\"https://assets-news-bcdn.dailyhunt.in/cmd/resize/#DH_EMB_IMG_REP#\_\_DHQ\_/fetchdata16/images/a1/1e/4b/a11e4be00583bef73db49da139bd1091267aafe487bdfacf3c694d3a8e6d92a5.png?src=gateway\",
\"supportedDevice\": \"ipad\", \"langfilter\": \"\", \"strokeColor\":
\"\", \"strokeColorNight\": \"\", \"userRegistrationRequired\": false,
\"isReplaceable\": false, \"menubarPriority\": 10,
\"pressedStateColor\": \"#f2f2f2\", \"persistContainer\": false,
\"activeTextColor\": \"#000000\", \"inactiveTextColor\": \"#545454\",
\"activeTextColorDark\": \"#FFFFFF\", \"inactiveTextColorDark\":
\"#999999\", \"uniTitle\": \"News\", \"globalPriority\": \"0\" } \...
more sections \... \], \"icons\": { \"HOME\": { \"inactiveIconUrl\":
\"https://assets-news-bcdn.dailyhunt.in/cmd/resize/#DH_EMB_IMG_REP#\_\_DHQ\_/fetchdata16/images/23/9a/2b/239a2b5bbd1b63654473895001dbd97d0f9a3d8ce974b228b3ce53c49ae484b0.png?src=gateway\",
\"activeIconUrlNight\":
\"https://assets-news-bcdn.dailyhunt.in/cmd/resize/#DH_EMB_IMG_REP#\_\_DHQ\_/fetchdata16/images/bd/a6/c2/bda6c22cab30096bfd989e409d355d2f8b2e378a0e962055d2b797aac9a06060.png?src=gateway\",
\"inactiveIconUrlNight\":
\"https://assets-news-bcdn.dailyhunt.in/cmd/resize/#DH_EMB_IMG_REP#\_\_DHQ\_/fetchdata16/images/b5/55/45/b555458f8840028c1e8e64f9b8cfe29ea6b50ec412af0610406b1eb7e0c5b14f.png?src=gateway\",
\"activeIconUrl\":
\"https://assets-news-bcdn.dailyhunt.in/cmd/resize/#DH_EMB_IMG_REP#\_\_DHQ\_/fetchdata16/images/ba/57/35/ba57356c6de18c67b3a88d5ad88fd03d9c59e2af261e7fde3dc8f3b2f1ecdbb4.png?src=gateway\",
\"activeTextColor\": \"#000000\", \"inactiveTextColor\": \"#545454\",
\"activeTextColorDark\": \"#FFFFFF\", \"inactiveTextColorDark\":
\"#999999\", \"title\": \"Home\", \"uniTitle\": \"Home\" } \... more
sections \... } } }

### Proto Schema (syntax=proto3)

note

1.  The "optional" keyword is used to make a property nullable. It is
    only available in the "proto3" syntax.

:::: {.panel .conf-macro .output-block style="background-color: rgb(234,230,255);border-color: rgb(153,141,217);border-width: 1.0px;"}
::: {.panelContent style="background-color: rgb(234,230,255);"}
1.  The "optional" keyword is used to make a property nullable. It is
    only available in the "proto3" syntax.
:::
::::

syntax = \"proto3\"; package api; message BottomBar { message Sections {
optional bool restrictedToMenubar = 1; optional string
activeIconUrlNight = 2; optional string inactiveIconUrl = 3; optional
string refreshIconUrlNight = 4; optional string highlightColor = 5;
optional string activeIconUrl = 6; optional string type = 7; optional
string bgColorNight = 8; optional string bgColor = 9; optional string id
= 10; optional string refreshIconUrl = 11; optional string title = 12;
optional bool applicableForThinUsers = 13; optional map\<string,
string\> excludeStates = 14; optional string highlightColorNight = 15;
optional string bgType = 16; optional string contentUrl = 17; optional
string inactiveIconUrlNight = 18; optional string supportedDevice = 19;
optional string langfilter = 20; optional string strokeColor = 21;
optional string strokeColorNight = 22; optional bool
userRegistrationRequired = 23; optional bool isReplaceable = 24;
optional uint32 menubarPriority = 25; optional string pressedStateColor
= 26; optional bool persistContainer = 27; optional string
activeTextColor = 28; optional string inactiveTextColor = 29; optional
string activeTextColorDark = 30; optional string inactiveTextColorDark =
31; optional string uniTitle = 32; optional string globalPriority = 33;
} message Icon { optional string inactiveIconUrl = 1; optional string
activeIconUrlNight = 2; optional string inactiveIconUrlNight = 3;
optional string activeIconUrl = 4; optional string activeTextColor = 5;
optional string inactiveTextColor = 6; optional string
activeTextColorDark = 7; optional string inactiveTextColorDark = 8;
optional string title = 9; optional string uniTitle = 10; } message
Icons { optional Icon HOME = 1; optional Icon MORE = 2; optional Icon
PROFILE_RED = 3; optional Icon HOME_XPRESSO = 4; optional Icon
NOTIFICATION_RED = 5; } message Data { optional string version = 1;
optional string bgColor = 2; optional string bgColorNight = 3; optional
repeated Sections sections = 4; optional Icons icons = 5; } optional
uint32 code = 1; optional Data data = 2; }
