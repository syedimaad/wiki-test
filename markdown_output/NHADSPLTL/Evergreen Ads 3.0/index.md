## Daedalus:

1.  Add param `eg_eligible` in order table (`dhx_orders`).

    1.  `eg_eligible` will have 3 values.

        1.  1 → Inherit

        2.  2 → Eg Eligible

        3.  3 → Eg not Eligible

2.  Add param `eg_eligible` in campaign table (`dhx_requirements`).

    1.  `eg_eligible` will have 3 values.

        1.  1 → Inherit

        2.  2 → Eg Eligible

        3.  3 → Eg not Eligible

3.  Add param `eg_eligible_based_targeting.`

    1.  `eg_eligible_based_targeting` will have 2 values.

        1.  1 → Eg Eligible

            1.  If only below are configured in `Targeting` and
                `SubTargeting`

                1.  `languages` , `states`, `countries` and `os`

            2.  Context targeting is not configured.

        2.  2 → Eg not Eligible

## Ad-Serving:

1.  Don't send empty campaign in evergreen ad response.

2.  Incorporate `eg_eligible`

3.  Select Regular ads for serving in evergreen path based on
    [this](https://docs.google.com/spreadsheets/d/1cxOzZFoNi3poomaxYxboTKRX9CogdFJ2xRF0CHm8dws/edit#gid=0)
    logic.

4.  Implement priority and weight.

5.  Cap Evergreen ad Response to 50 items.

6.  Platform level `eg_eligible` will be a config.
