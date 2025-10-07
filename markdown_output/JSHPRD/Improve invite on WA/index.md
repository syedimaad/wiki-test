  ----------------------- ---------------------
  **Document Status**     READYGreen
  **Android Sprint**      add release sprint
  **iOS Sprint**          add release sprint
  **Product Owners**      
  **Product Designers**   @ product designers
  **Android Leads**       @ android leads
  **Android Devs**        @ android devs
  **iOS Leads**           @ ios leads
  **iOS Devs**            @ ios devs
  **QA Devs**             @ qa devs
  **Josh Lite**           YEsGreen / NORed
  ----------------------- ---------------------

##  Executive Summary

Build enhanced messaging to generate high-quality WhatsApp template
messages to encourage conversions.

##  Objective

Build enhanced messaging to generate high-quality WhatsApp template
messages to encourage conversions.

##  Functional Specifications

**Set intent link w/ phone number and message prepopulated**

1.  In the invitation flow via WhatsApp, we will have additional data
    present in the pre-populated message.

    1.  The invitation flow can also be initiated via the contacts sync
        feature.

2.  The message will contain:

    1.  The inviter's profile photo and name (in a generated image)

    2.  Custom URL pointing to a Josh Onelink page to download Josh

        1.  Preview of the URL (custom image if possible) to make the
            message branded and more attractive.

    3.  The inviter's profile link

    4.  Inviter's phone number

3.  Flow:

    1.  User Rajiv invites Ankit via WhatsApp message. 

    2.  Ankit is able to download the relevant app build from the
        primary URL in the message.

    3.  Ankit is also able to jump directly to Rajiv's public Josh
        profile via the profile link.

**Actual message templates:**

**Type 1:** Hi, \<sender's name\> wants you to join them on Josh,
India's biggest short-video platform! Check out their Josh profile and
videos they've shared here: \<profile link\>. Open this link to download
Josh: \<link\> and see videos from top creators followed by millions of
users like you.

**Type 2:** Hi, \<sender's name\> (phone number \<sender's number\>)
wants you to join them on Josh, India's biggest short-video platform!
Check out their Josh profile and videos they've shared here: \<profile
link\>. Open this link to download Josh: \<link\> and see videos from
top creators followed by millions of users like you.

In both types, we will have a generated image that contains the
inviter's profile photo, name and user name.
