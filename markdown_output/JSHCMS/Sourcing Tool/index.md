Users

1.  All users would login via mobile/email with the OTP sent to their
    mobile/email

2.  For every new user create a user in Josh system with details
    provided on the first login

Content Sourcing UI

1.  Login Screen

    1.  Take mobile/email as an input

    2.  Trigger the otp

    3.  Set the user uuid, client id and auth token in session once
        login is successful

2.  Source Content Screen

    1.  Take the source url from the desk user

    2.  Check if the source url exists in the sourcing system (DB)

        1.  Yes → Give toast that the content exists

        2.  No

            1.  Show the upload content option/dropbox

            2.  Download the content from the source system once
                crawling is enabled for impending systems

    3.  Check for duplicate content via API

        1.  No → Show the provide meta options

        2.  Yes → Say that the content exists

    4.  Show the provide meta form with pre filled data ( ask for yes/no
        )

        1.  User to input some of the details

        2.  Call the ML system for Details like genre, theme etc

        3.  Call the content source system for meta like title, hashtags
            etc

    5.  Create the content in Josh System using the meta provided

        1.  Using the mobile → user uuid mapping

        2.  Using the user → pool of user uuids mapping

3.  System mappings

    1.  User → Zone

        1.  All created content to go to a certain zone

    2.  User → Genre

    3.  User → Hashtags

4.  Meta Captured

    1.  Title

    2.  Hashtags

    3.  Source → { source_url, source_system etc }

    4.  File → Uploaded/Downloaded

    5.  Zone/Genre/Hashtags to be populated from desk user mapping ( if
        any )

    6.  Template

    7.  Stickers

    8.  events

    9.  Misc
