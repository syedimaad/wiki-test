  ----------------------- ------------------
  **Document Status**     READYGreen
  **Android Sprint**      
  **iOS Sprint**          
  **Product Owners**      
  **Product Designers**    
  **Android Leads**       
  **Android Devs**        
  **iOS Leads**           
  **iOS Devs**            
  **QA Devs**             
  **Josh Lite**           YESGreen / NORed
  ----------------------- ------------------

## ** Executive Summary**

Giving users more relevant content has always been a primary goal. With
nearby, we're giving them a way to see location-relevant content. This
is meant to increase engagement and time spent on the app.

##  Objective

Increase engagement and time spent on Josh driven by more relevant and
relatable content.

##  Functional Specifications

#### **OVERVIEW**

1.  Addition of a new tab on home to the left of the 'Following' tab for
    users to discover content posted around their location (serving
    basis content location, **not** user location). 

    1.  Users will also be able to select another location and view
        content from there.

    2.  Location list will only display towns with available content

2.  New screen elements added to existing ones on the current feed

    1.  Nearby tab with the name of the location as the title

        1.  ~~Location tag~~ The location name will appear on the
            'Nearby' tab itself with an edit option to switch locations.

        2.  Distance tag

            1.  Up to 5 kms away - "Closeby"

            2.  5 to 8 kms away - "In your area"

            3.  8 to 12 kms - "Few kilometers away"

            4.  12 to 20 kms - "In your region"

            5.  20 to 35 kms - "Around your region"

            6.  35+ kms away - "Other regions"

    2.  New nudge on the home feed

3.  Tab Management

    1.  Nearby tab to appear only on this version forward

    2.  Configurability to hide the tab/show/hide configuration for the
        tab

4.  UI specs are
    [[here]{.underline}](https://www.figma.com/file/QhCVcztHB559r2DCcBIU8o/Home?node-id=6791%3A18277).

#### **2. NEW FLOWS**

1.  **Activation, exploration and consumption**

    1.  Nudge users to go to the 'Nearby' tab

    2.  Obtain location permissions

        1.  Draw the user's attention to the 'Allow Location
            Permissions' button

        2.  Prompt the user with the OS location permission dialog box

            1.  If location permissions are temporarily denied, return
                to the default view

            2.  If location permissions are denied permanently, show
                another view that prompts the user to give location
                permissions from their device settings.

                1.  Elaborated below in 3.1.b

    3.  Show a feed with videos that users can swipe through (same as
        existing feeds)

        1.  Show content from users' location

            1.  Users can use the location tag/edit option to choose
                another location to view videos from that location

        2.  Additional metadata around location and distance is shown to
            the user

        3.  Follow the sequencing logic from section 6 below

    4.  Users can switch between all 3 tabs

2.  **Creation: Create Post**

    1.  Location prompt to have updated subtitle: "Adding location to
        your video will get it more views"

    2.  Allow user to tag a location to a video \-- use the same
        location list as in Nearby tab change location API. On tap,
        trigger the same location picker screen w/ search. Default to
        lat-long location 

3.  **Nudges**

4.  Primary nudge: "Watch videos near you!"

5.  Hierarchy: based on user-freshness

    1.  New users: 'Nearby' nudge to be the latest after the existing
        set of nudges

    2.  Existing users ('Nearby' as a new feature for them)

        1.  Show 'Nearby' nudge to users as soon as they open the
            updated app and land on the feed

        2.  Deeplinks can take the user directly to the 'Nearby' tab on
            appropriate versions of the Josh app

#### **3. FUNCTIONALITY**

1.  **Location Permission (in the 'Nearby' tab)**

    1.  This is a prerequisite for the page/tab to function 

    2.  Appropriate messaging to nudge the user to turn on location
        permission 

        1.  Not yet given or temporary denial

            1.  Title: Watch awesome videos near your location

            2.  Subtitle: Allow Josh to access your location to begin

            3.  CTA: Allow Location Permissions

        2.  Permanent Denial

            1.  Title: Watch awesome videos near your location

            2.  Subtitle: Give Josh permission to know your location

            3.  CTA: Go to Settings

    3.  If location permission has been denied previously (temporarily
        or permanently), handle dialog appropriately.

    4.  Once permission is given, make a call to get the content to be
        served here

        1.  Intermediate loading screen

            1.  To start with, let's use the default loading screen with
                the black background

2.  **Geo-location, selection and logic**

    1.  Once location permissions are obtained, default to GPS
        determined location (city-level)

        1.  As per the current DH location framework

    2.  A user has the option to change the location by tapping on the
        location or distance tags.

        1.  If changed, this should only persist for the session (until
            the splash screen is visible again)

    3.  Depending on the selected location, fetch the appropriate feed

    4.  Tapping on the icon to change location will trigger a
        chronological list of pre decided locations 

3.  **Sequencing logic**

    1.  Reuse logic from DH

    2.  In case there's no content available for the identified
        location:

        1.  Show messaging indicating "No videos available for
            \<location 1\>. Showing videos from \<location 2\>.

        2.  Show videos from a location with available content. The
            location should be chosen based on proximity to the
            geo-located location. 

4.  **Deeplink**

5.  Allow deeplink to nearby tab to nudge users 

6.  Deeplink to nearby tab will contain location identifier as a param

    1.  If this param is present, on landing, use this location to
        request for the feed

    2.  Ignore GPS location

        1.  Bypass location permission if location permission is not
            given in case this param is present

            1.  Land user to the 'Nearby' tab with the param defined
                location

            2.  For a user who's never been to the 'Nearby' tab, nudge
                them into giving location permissions

                1.  "Give Josh location permissions to watch videos
                    close to you"

    3.  If location is not recognised or if there's no content for the
        location or there's an API failure

        1.  If location permission is given

            1.  Show a screen with a CTA to refresh the feed ("Try
                Again"). 

            2.  Upon tapping this CTA:

                1.  In case of no content for deep-linked location:

                    1.  Load geo-located content (following sequencing
                        logic)

                2.  In case location-based content is now available

                    1.  Load content as usual

        2.  If location permission is not given: show location
            permission state

#### **4. FEED**

1.  New metadata added to a video:

    1.  Distance as item meta aka 'distance tag' (shown only for current
        locations) 

    2.  Currently selected location (for the location tag)

2.  Feed building

    1.  Distance as a factor while building the feed 

    2.  A less rigid rule for language as a filtering param in this feed

3.  Location list: All available to be shown \-- backfill will nearby
    locations

4.  BE control for filtering skmnlco creators

5.  Handle error states and ads appropriately as in any other feed

6.  End of Feed: Elastic swipe behaviour (Android default) \-- user will
    need to go to a different tab or select a different location (no
    nudge to do this in this phase)

7.  Distance tag: rounding-off

    1.  Up to 10 km: show 1 decimal place

        1.  Example: 9.8 km

    2.  10 - 99 km: round-off to the nearest whole number

        1.  Example: 56 km (for 55.7 km)

    3.  99 to 9999 km: round-off to the nearest multiple of 5 (?)

        1.  Example: 365 km (for 364.2 km)

#### **5. OTHERS**

1.  **Location master-data**

    1.  The list of all possible locations should be configurable

    2.  Source of data should sit in the BE DB editable by Product

2.  **Discovery**

    1.  Add a location carousel to prompt users to land to the nearby
        tab

    2.  On choosing a location, deeplink to a feed with the chosen
        location

3.  **Settings / Opt-out**

    1.  Allow creators to opt-out of location share

    2.  Configurable setting

##  Figma

https://www.figma.com/file/QhCVcztHB559r2DCcBIU8o/Home?node-id=6791%3A18277

## Instrumentation
