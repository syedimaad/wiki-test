# Assumptions

1.  User has just installed the app.

2.  There is a campaign `c1` targeted to `card-p0`, `card-pp1` and
    `storypage`.

# Workflow

1.  User launches the app and lands into the `ForYou` section.

2.  `card-p0` and `card-pp1` requests are made in parallel.

3.  AdsBE will -

    1.  Select the same campaign `c1` for both the placements.

    2.  Generate an `adHashId` for both the campaign selections.
        Essentially the `adHashId` will be the same.

    3.  Add the `adHashId` into the response as one of the new fields.

4.  App will receive the response and render `card-p0` and find that the
    `card-pp1` has the same campaign `c1` with the same `adHashId`.

5.  Based on the active dedup logics provided in the Ads Handshake, the
    app will discard the `card-pp1` Ad (if required) and request for the
    new Ad by sending campaign `c1`\'s details in the `adHashInfo`
    object in the post body of the Ad request.

    1.  The App will add the information into `adHashInfo` object as
        soon as the impression for the Ad has happened.

6.  AdsBE will find the information about the `adHashInfo` and does the
    deduplication of the campaign `c1` and finally respond with some
    other campaign.

# Handshake

1.  Ads handshake to contain the information about the dedup logics to
    activate at the App side. The logics can be -

    1.  Dedup in the same zone in the same topic.

    2.  Dedup in the same zone in the across topic.

    3.  Dedup across the zones in the same topic.

    4.  Dedup across the zones across the topics.

    5.  Dedup based on the impression time of the previous same Ad.

json{ \"dedup\": { \"logics\": { \"SZST\": { \"enabled\": true,
\"distance\": 1 }, \"SZAT\": { \"enabled\": false, \"distance\": 1 },
\"AZST\": { \"enabled\": false, \"distance\": 1 }, \"AZAT\": {
\"enabled\": false, \"distance\": 1 }, \"AZAT-TB\": { \"enabled\": true,
\"time\": 300 } }, \"enabledZones\": \[\"card-p1\|DEFAULT\",
\"card-pp1\|pp1_1,pp1_2,pp1_3\", \"storypage\", \"supplement\|ALL\"\],
\"adHashInfoCountPerZone\": 10 } }

# AdHashInfo Object

1.  Contains the information consisting of the `adHashId` of last `x`
    Ads rendered on the App.

    1.  The value of `x` per zone will be provided in the Ads Handshake.

2.  This information will be indexed based on AdPlacement and
    ImpressionTime.

3.  The object contains the `entityId` and the `adHashId` information.

json{ \"card-p0\": { \"DEFAULT\": { \"1234567\": { \"enitityId\":
\"111\", \"adHashId\": \"gstwgg\" } } }, \"card-p1\": { \"DEFAULT\": {
\"1234567\": { \"enitityId\": \"111\", \"adHashId\": \"gstwgg\" } } },
\"supplement\": { \"sp1\": { \"1234567\": { \"enitityId\": \"111\",
\"adHashId\": \"gstwgg\" } } } }
