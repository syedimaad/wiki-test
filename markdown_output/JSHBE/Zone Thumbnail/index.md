#### First time generation

1.  When the status changes to IN_REVIEW, push to an SQS

2.  Lambda would pick and generated banner and profile images for the
    zone

3.  Expose callback to update in Dynamo and ES

4.  CMS to incorporate a review flow with DTA to select one profile
    picture from the list and one/many banners from the list.

5.  Move the zone status to published once selected.

6.  Create was AWS scheduler to run another lambda to keep regenerating
    banners for the approved templates.

#### Add the below attributes in the zone

1.  generated_banner : Generate based templates. Add the templates here

    1.  json\[ { \"thumbnail\":
        \"https://stream.myjosh.in/stream/prod-ugc-contents/zone/925540cbd73d4e55/b81a1c2c5d8ebaa0/b117c82d-9ec6-45c5-97d3-984dd4af0c3e_1655435593_hi_thumbnail.webp\",
        \"id\": \"b117c82d-9ec6-45c5-97d3-984dd4af0c3e\",
        \"template_id\": \"collage_1\" \"status\": \"APPROVED\" } \]

2.  generated_profile_images :

    1.  Pre add level 0 / level 1 images if exists

    2.  Use thumbnail of the most popular 3 items

    3.  Show the first letter of the title

    4.  json\[ { \"thumbnail\":
        \"https://stream.myjosh.in/stream/prod-ugc-contents/zone/925540cbd73d4e55/b81a1c2c5d8ebaa0/b117c82d-9ec6-45c5-97d3-984dd4af0c3e_1655435593_hi_thumbnail.webp\",
        \"id\": \"b117c82d-9ec6-45c5-97d3-984dd4af0c3e\",
        \"template_id\": \"profile_template_1\" \"status\": \"APPROVED\"
        } \]

3.  status : Add new status → IN_REVIEW

4.  reviewed_by :

5.  reviewed_on

\
