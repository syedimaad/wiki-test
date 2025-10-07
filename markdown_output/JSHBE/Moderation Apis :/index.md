1.  Rooms shut with or without reason.\

    Request Payload from client : roomIds : \[\] shutReasonRequired :
    true/false Response Payload :\] { \"Response\": \[ { \"id\":
    \"id1\", \"message_host\": \"\", \"message_audience\": \"\",
    \"status\": \"ENDED/MODERATED\", \"title\": \"Live Blocked/Room
    Ended\", \"guidelines_title\" : \"\", \"guidelines_url\" : \"\" }, {
    \"id\": \"id2\", \"message_host\": \"\", \"message_audience\": \"\",
    \"status\": \"ENDED/MODERATED\", \"title\": \"Live Blocked/Room
    Ended\", \"guidelines_title\" : \"\", \"guidelines_url\" : \"\" } \]
    }

2.  Save API changes:

    1.  Save API returning 403 if user was flagged as moderated in his
        previous room.

    2.  If user clicks on I agree, we will let them create the room (A
        flag will come from client side in request payload.)

    3.  We will block the user if last n days , user has been flagged k
        times for moderation.

    4.  User can be blocked temporarily or permanent as per the no of
        times he has been flagged as moderated in past.

    5.  We will use redis key if user is flagged as moderated
        (warning_userId) and will remove it from redis if we get agreed
        flag as true from client side.\

        Respose-\> Case 1- if user is permanently blocked \"status\": {
        \"code\": 403, \"timestamp\": 1674461181033 }, \"data\": {
        \"liveModerationStatus\":\"BLOCKED\", \"message\" : \"Live
        moderator has blocked your live rooms because you violated the
        guidelines., \"title\" : \"Blocked\" } } Case 2- if users\' last
        room was shut by moderation \"status\": { \"code\": 403,
        \"timestamp\": 1674461181033 }, \"data\": {
        \"liveModerationStatus\":\"ALLOW_WITH_WARNING\",
        \"message\":\"Your last live room was shut down due to violation
        of community guidelines. Please make sure that you comply with
        the guidelines., \"title\" : \"Warning\" } }

        \

3.  Warning API (Exposed to CMS as well)\

    { \"userId\":\"\" \"roomId\": \"\", \"level\": \"warning\",
    \"count\":1/2/3 \"message\": \"\" }

    \

4.  Confidence score API : We can use deque to maintain the last 15
    frame's score and calculate the threshold for SNFS .\

    Request Payload : { \"roomId\": \"\", \"frameId\": \"\", \"score\":
    \"\" } Response Payload : { }

5\. Update user details(V2 api) based on confidence score to generate
star rating.
