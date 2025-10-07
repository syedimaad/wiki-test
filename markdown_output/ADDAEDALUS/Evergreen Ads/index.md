- Add a field on table `dhx_requirements`: category as tinyint. Possible
  values: category = {0:REGULAR, 1:EVERGREEN}

- Add validation to not group campaigns with different categories

- For evergreen category, restrict configurable options as below:

Restrict configuration of fields basis below

**[Configurable Options on Campaign creation screen:]{.underline}**

- Campaign Name

- AdPlacement

- Campaign Classification (only for reporting)

- Delivery Modes

- **Is Content Campaign?** - **[Confirm from
  Chacko]{style="color: rgb(0,102,68);"}**

- Start Date/End Date

- Campaign Execution Plan [- Not allowed
  ]{style="color: rgb(255,86,48);"}

- Creatives Type: [only "display"
  option]{style="color: rgb(76,154,255);"}

- Bill On: no change

- Billing Type: [only "CPM" option]{style="color: rgb(76,154,255);"}

- Optimization Type [- Not allowed ]{style="color: rgb(255,86,48);"}

- Number of Impressions

- Billing Rate (Per 1000 Impressions)

- Total Value

- Is PG Campaign? -[ Not allowed -
  value:off]{style="color: rgb(255,86,48);"}

- Is PD Campaign? [- Not allowed -
  value:off]{style="color: rgb(255,86,48);"}

- is Adjunct Campaign? **[Discuss with
  Siva]{style="color: rgb(0,102,68);"}**

- Is Value Add (Campaign will not be billed)

- Delivery Type: [Only Contract Exclusive option
  allowed]{style="color: rgb(76,154,255);"}

- Stop Campaign After Inventory Is Met? - [Not allowed -
  value:off]{style="color: rgb(255,86,48);"}

- Impression UUs Minimum Requirement - [Not allowed -
  value:blank]{style="color: rgb(255,86,48);"}

- Enable Custom Bidding Rate - [Not allowed -
  value:off]{style="color: rgb(255,86,48);"}

- Allow Roll Up - [Not allowed -
  value:off]{style="color: rgb(255,86,48);"}

- Context Targeting - [Not allowed ]{style="color: rgb(255,86,48);"}

- Estimated Audience Reach / Targeting: [Allowed options:
  ]{style="color: rgb(76,154,255);"}`countries,states,languages,os-versions`

**[Configurable Options on Campaign \> Manage screen:]{.underline}**

- Sub Targeting: [Allowed options:
  ]{style="color: rgb(76,154,255);"}`countries,states,languages,os-versions`

- Soft Tag - [Not allowed ]{style="color: rgb(255,86,48);"}

- Tracker Configs

- Frequency Cap

- Version Frequency Cap - [Not allowed ]{style="color: rgb(255,86,48);"}

<!-- -->

- [Add OR ]{style="color: rgb(255,255,255);"}
