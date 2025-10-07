1.  Confirm below mapping:

  ----------------- ----------------- -----------------
  **host_app_id**   **partner_ids**   **Destination**
  DH_APP            DH_APP            app
  DH_APP            DH_APP_PWA        web
  DH_APP            DH_APP_WEBITEM    app
  DH_APP            DH_APP_DESKTOP    web
  DH_MENA           DH_MENA           app
  DH_MENA           DH_MENA_PWA       web
  DH_MENA           DH_MENA_WEBITEM   app
  DH_MENA           DH_MENA_DESKTOP   web
  JOSH_APP                            
  DAN                                 
  ----------------- ----------------- -----------------

Revenue sources:

**Requirements**

1.  [Flow partner ID]{style="color: rgb(191,38,0);"} data in
    oads.ox_data_intermediate_ad_zone - Chetan

    1.  Calculations for CPC, CPM,CPI, CPV

2.  [Flow partner ID]{style="color: rgb(191,38,0);"} data in
    daedalus_reports.`dhx_event_postbacks`

    1.  This table has partner_id column, but values seem to be of
        host_app_id

3.  Requirements that have delivery - Flow partner ID in
    `daedalus_reports.dhx_performance_reports` and
    `daedalus_reports.dhx_performance_zone_wise` for - DD

4.  Check calculation for CPPV or CPVP - DD

5.  Requirements that have ad Network Revenue:
    `daedalus.dhx_requirement_prebilling_plan`

    1.  Find who updates this table

    2.  [Add Partner ID column]{style="color: rgb(191,38,0);"}

    3.  Update queries on DD

6.  Requirements that have REP(prebilling or brand presence) in the
    billing group: `daedalus_reports.dhx_report_groups_rep`

    1.  Will not require a change

**Requirement Group**

Can use same logic as requirements. Add filters on addition of new
fields (if any)

**Billing Group**

1.  Has Requirements/Requirement Groups

    1.  Use same logic as Requirments

2.  Doesn\'t have requirement attached - prebilling/Brand presence

    1.  Add field at Billing group for tagging destination

------------------------------------------------------------------------

## **DD Interface Changes**

**Sales Leads Flow**

1.  Introduce option of selecting host_app_id

2.  Introduce Billing from

**Proposal Creation**

1.  Introduce option of selecting partner Id - list of partner IDs
    should be based on host app ID

**Proposal \> Order\*campaigns**

1.  Import host_app_id, from sales Lead

2.  When creating line items,

    1.  add host_app_id, Billing from from sales leads \[these options
        exist at campaign level, billing group level\]

    2.  add partner ID from Proposal. Keep it editable at campaign level

    3.  For billing groups, editing metadata is not possible

**New/edit Order Flow**

1.  Import from sales leads. If not created via sales leads or it is
    null, allow selection of host_App_id.

2.  host_App_id cannot be edited

**New/edit Campaign Flow**

1.  Restrict creation of campaigns to order's host App Id, if it is not
    null

**Campaign Group**

1.  Check if added campaign has same billing from / host app id /
    partner id

**Billing Group**

1.  Check if added campaign has same billing from / host app id /
    partner id
