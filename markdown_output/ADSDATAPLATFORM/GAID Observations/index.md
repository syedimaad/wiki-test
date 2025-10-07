- Android Request DAU(avg 9 days) \~17M

- \% DAU with GAID(avg 9 days) - 96%

- \% DAU without GAID(avg 9 days) - 4%

- \% DAU without GAID (**across 9 days**) -

GAID based issues and observations

1.  Multiple GAIDs -\> one Client ID\
    % Users with multiple GAIDs - 0.011%

    1.  User resets GAID manually.

    2.  Multiple Users/Profiles on the same device.

    3.  QA team testing resulting in multiple GAIDs for the same client.

2.  One GAID -\> multiple Client Ids\
    When a user switches device, a new client_id is assigned but GAID is
    the same resulting in this scenario.\
    One other scenario occurring because of this\
    Multiple GAIDs for Client 'A\' in Kudu but GAID belongs to some
    other Client \'B' in Mongo

    1.  User switched device and was assigned a different client_id but
        gaid is same.

    2.  The old user resets GAID and it was reassigned.

3.  Mismatch due to Update Frequency\
    Our process updates client profile(fields such as device_info, gaid,
    gpsLocation) once a day. So if a user resets GAID, the new GAID will
    reflect once the user opens the app in the future.

4.  Client Switching GAID (From A -\> B and then again back to A)\
    % Users - 0.002%\
    User switching accounts on the same device and same profile.
