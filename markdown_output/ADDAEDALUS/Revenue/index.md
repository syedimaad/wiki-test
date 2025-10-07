So as we know revenue system is very large and understanding it on the
one go is very hard. we will break the things down and then understand.

We will break this whole revenue into 3 parts

1.  Which entities are responsible for generating revenue

2.  how entities generated revenue

3.  how has the invoice been generated with revenue

we start with the first part

#### Entities responsible for generating revenue

On the broader level, it is the order on which we do invoicing so
obviously order entity is responsible for revenue but we can\' get a
complete picture from the order. So any order has 3 main entities who
are responsible for the same

- Requirement (Campaign)

  - table → daedalus.dhx_requirements

  - any requirement has three values which play the most important part
    in the revenue

    - billing type: CPI, CPM, etc

      php protected static \$campaignTypes = \[ self::CAMPAIGN_TYPE_CPM
      =\> \"CPM\", self::CAMPAIGN_TYPE_CPC =\> \"CPC\",
      self::CAMPAIGN_TYPE_CPL =\> \"CPL\", self::CAMPAIGN_TYPE_CPA =\>
      \"CPA\", self::CAMPAIGN_TYPE_FIXED =\> \"Fixed\",
      self::CAMPAIGN_TYPE_CPI =\> \"CPI\", self::CAMPAIGN_TYPE_CPE =\>
      \"CPE\", self::CAMPAIGN_TYPE_CPPV =\> \"Content CPPV\",
      self::CAMPAIGN_TYPE_CONTENT_CPVP =\> \"Content CPVP\",
      self::CAMPAIGN_TYPE_CPV =\> \"CPV\", \];

    - billing rate: charged per in all billing types except CPM it is
      per 1000

    - bill for : (tracker type which tracks the activities) dailyhunt
      tracker, third party trackers

- Requirement Group

  - as the name suggests it is a collection of requirements done mostly
    for easy billing, inventory tracking, reporting of the requirements

  - table → daedalus.`dhx_requirements_groups`

  - We cannot just randomly add all the campaigns to a campaign group it
    must satisfy some conditions you can find about the condition in

note

RequirementsGroups.`canBeAdded`()

:::: {.panel .conf-macro .output-block style="background-color: rgb(234,230,255);border-color: rgb(153,141,217);border-width: 1.0px;"}
::: {.panelContent style="background-color: rgb(234,230,255);"}
RequirementsGroups.`canBeAdded`()
:::
::::

- Billing groups

  - table → daedalus.`dhx_report_groups`

  - billing groups are providing aid to invoicing part. We can add
    requirements/requirement groups to this, also
    requirement/requirement groups have many to one relationship with
    the billing group

  - billing group has mainly 2 parts

    1.  bills from

        - delivery → simply you can add requirement, requirement group,
          directly and can use this billing group in the invoice

        - prebilling → when we want to do the billing for any
          requirements/requirements group prior to their completions.
          For example, we have a campaign running worth 100 rs is going
          to end on 30th may but the client wants the bill on 12th may
          so we go make a prebilling billing group add that campaign
          mention date and revenue and then after generating invoice

        - brand presence → As Daedalus should have every invoice
          sometimes few things not happened through Daedalus system like
          if we are charging for notification or extra work in UI we
          create a brand presence billing group and here without adding
          any entities create date and revenue and generate the invoice.

    2.  tracker type

        - Dailyhunt tracker → as the name suggests if tracking is done
          by dailyhunt

        - Third party tracker → when we use tracker of any third party.
          Now when we use third party tracker for any campaign we must
          need to create a billing group add that tracker and mention
          the date, attribution, and revenue (data) we got from the
          third party. After that, we can generate an invoice

    3.  We cannot just add any requirements/requirement groups to the
        billing group there is some rule like both should be of the same
        host app you can see all the required rules in the following
        function

note

ReportsGroups.`canBeAdded`()

:::: {.panel .conf-macro .output-block style="background-color: rgb(234,230,255);border-color: rgb(153,141,217);border-width: 1.0px;"}
::: {.panelContent style="background-color: rgb(234,230,255);"}
ReportsGroups.`canBeAdded`()
:::
::::

### How can we get revenue from these entities

It involves three steps

- Getting all the required entities (requirements, requirement groups,
  billing group)

- Getting inventory for all these

- Convert inventory into revenue

Now we look into these steps one by one we have the main function

> RevenueMonitor.`getResultByDate($startDate,$endDate,$filters = [],$restrictedUserId = null,$includeLiveData = true,$publisherId = null, $isPostEval = false)`

The above function is the root function we call

- Getting all required entities

  - Mainly we use to call function

> `Requirements::getAllRunningOrCompletedRequirementsWithFiltersNew($startDate,$dates['projectionEnd'],$filters,$restrictedUserId,$publisherId, $isPostEval)`

The above function is responsible to find out all the required entities
for a given date range and add filters then return

return \[\'allRequirements\' =\>
\$requirementsMap,\'allRequirementGroups\' =\>
\$requirementGroupsMap,\'allBillingGroups\' =\>
\$billingGroupsMap,\'allOrders\' =\> \$allOrdersMap\];

- Now we look inside the function of how we are getting these entities

  1.  Requirements that have delivery:

      - DB : prod → `oads.ox_data_intermediate_ad_zone` , non-prod →
        `daedalus_reprots.dhx_performance_zonewise_reports`

      - Function :
        `ZonePerformanceReports::getBannerIdsThatHaveDeliveredDuringDatesFromOpenX($startDate->format("Y-m-d"),$endDate->format("Y-m-d"));`

      - Notes : here we get banner Id's from which we get requirement Id

  2.  Requirements that have ad Network Revenue:

      - DB : `daedalus.dhx_requirement_prebilling_plan`

      - Function :
        `RequirementPreBillingPlan::getAllCampaignIdsThatHaveDataDuringDates($startDate->format("Y-m-d"),$endDate->format("Y-m-d"));`

      - Notes : we directly get all the requirement id having revenue
        through ad network.

  3.  Requirements that are not new and fall in a date range:

      - DB: `daedalus.dhx_requirements`

      - Function :
        `Requirements::getCampaignIdsThatAreNotNewAndFallInDateRange($startDate->format("Y-m-d"),$endDate->format("Y-m-d"))`

      - Notes: Basically here we get all requirements with status not
        new and fall in provided date range more and less all required
        requirements should fall in this date range

  4.  Requirements That have atrributions:

      - DB : `.daedalus_thirdparty_attributions`

      - Function:
        `ThirdPartyAttributions::getCampaignIdsThatHaveAttributionsDuringDates($startDate->format("Y-m-d"),$endDate->format("Y-m-d"));`

      - Notes: need to explore

  5.  Requirements that have REP(prebilling or brand presence) in the
      billing group:

      - DB: we get the REP Billing group from →
        `daedalus_reports.dhx_report_groups_rep` now after getting id we
        do join with first dhx_requirements to get all id having
        report_group_id equals REP billing group id and also in
        requirements group we find those id's for the same and then from
        the group we find the individual requirements

      - Function:
        `BillingGroupsREP::getAllCampaignIdsAndBillingGroupIdsThatHaveREPDuringDates($startDate->format("Y-m-d"),$endDate->format("Y-m-d"));`

      - Notes: so basically we are getting billing Group having REP
        getting requirements id through this

  6.  Billing groups that have REP: as defined in the above point we get
      billing group id from table
      `daedalus_reports.dhx_report_groups_rep`

  7.  Now we have two entities requirements and billing group id we do
      join query as follows

      \$billingGroupQuery =
      ReportGroups::join(\$ordersTableName,\$ordersTableName .
      \'.id\',\'=\',\$billingGroupTableName . \'.order_id\')
      -\>leftJoin(\$brandsTableName,\$brandsTableName .
      \'.id\',\'=\',\$ordersTableName . \'.brand_id\')
      -\>whereIn(\$billingGroupTableName .
      \".id\",\$allBillingGroupIdsThatHaveREPInBillingGroup); \$query =
      Requirements::join(\$ordersTableName,\$ordersTableName .
      \'.id\',\'=\',\$requirementsTableName . \'.order_id\'); \$query =
      \$query-\>leftJoin(\$brandsTableName,\$brandsTableName .
      \'.id\',\'=\',\$ordersTableName . \'.brand_id\');

h\. We apply filters now like ad placements, order_type, etc.

i\. Now we go fill up that we have requirements and billing group we go
to every requirement find any requirement group with it add in
requirement group if it has billing group add to the billing group

- Now once we complete this first part to find out the requirements,
  requirements groups, billing group, and all respective orders we are
  calling now the second one to start finding inventory and then getting
  revenue from those.So we are now with previous input going to function
  RevenueMonitor.`start the magic`() this function is mainly calling two
  function

  1.  `RevenueCalculator::fetchAndOrganizeCampaignsForRevenueReportNew($this->runningRequirements,$this->runningRequirementGroups,$this->runningBillingGroups,$this->runningOrders,true);`

      - Let's dive inside the functions

      - we are getting response as following \$response = \[
        \'requirements\' =\> \[\], \'requirementGroups\' =\> \[\],
        \'billingGroups\' =\> \[\],
        \'requirementGroupsIndividualRequirements\' =\> \[\], \];

      - we are getting inventory for all requirements with
        `Requirements::getOverallDateWiseFullfilledInventoryFromObjects($currentRequirements,$includeLiveData);`
        // it gives inventory of all life time

        - Here we need to understand how inventory calculated

        - \$responseUnit = \[ \'requests\' =\> \[\], \'impressions\' =\>
          \[\], \'clicks\' =\> \[\], \'others\' =\> \[\], \'vs\' =\>
          \[\], \'v1\' =\> \[\], \'v2\' =\> \[\], \'v3\' =\> \[\],
          \'v4\' =\> \[\], \'cRevenue\' =\> \[\], \'cOverDelivery\' =\>
          \[\], \];

        - In the first step, we classify all the campaigns basis on
          campaign types like CPL, CPI, etc

        - Also every campaigns come under `$CPCorCPMCampaignIds[]`

        - Other than CPMorCPC everyone will overwrite the others in the
          response unit

        - We get date =\> inventory for all will put in the 'other'
          impression, clicks v1,v2, revenue we all get from
          dhx_performance_reports

+----------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Camapign types**   | **Database table**                              | **Notes**                                                                                                                                                                                             |
+----------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| CPPV or CPVP         | daedalus_reports.`article_reports_hive`         | Requirements::`getHiveMetricsDateMapForDateRange`(`$startDate = null, $endDate = null, $uniquesFlag = false`);                                                                                        |
|                      |                                                 |                                                                                                                                                                                                       |
|                      |                                                 | we first get all article id through banner of cppv and cpvp (billable) then get data from the given table and show articleviews and videoviews datewise map                                           |
+----------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| CPL or Lead          | daedalus_reports.`dhx_event_postbacks`          | `EventPostback::getDatewiseEventCountFromCampaigns($campaignIds, self::EVENT_TYPE_LEAD, self::EVENT_SUB_TYPE_BILLABLE, $startDate, $endDate, $onlyFromMaster);`                                       |
| Optimized            |                                                 |                                                                                                                                                                                                       |
+----------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| CPA or Attribution   | daedalus_reports.`dhx_event_postbacks`          | `EventPostback::getDatewiseEventCountFromCampaigns($campaignIds, [self::EVENT_TYPE_ATTRIBUTION, self::EVENT_TYPE_APP_EVENT] , self::EVENT_SUB_TYPE_BILLABLE, $startDate, $endDate, $onlyFromMaster);` |
| Optimized            |                                                 |                                                                                                                                                                                                       |
+----------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| CPC or CPM           | live data →                                     | `PerformanceReports::getLivePerformanceReportForCampaignsForDate($CPCorCPMCampaignIds, $yesterday->format("Y-m-d"),$onlyFromMaster);`                                                                 |
|                      | daedalus_reports.`ox_data_intermediate_ad_zone` |                                                                                                                                                                                                       |
|                      |                                                 | `PerformanceReports::getOverallPerformanceReportPerBanner($CPCorCPMBannerIds,$onlyFromMaster);`                                                                                                       |
|                      | even if only from master change connectionName  |                                                                                                                                                                                                       |
|                      |                                                 |                                                                                                                                                                                                       |
|                      | `daedalus_reports.dhx_performance_reports`      |                                                                                                                                                                                                       |
+----------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| CPI or optimized For | same as above                                   | if(isset(\$CPICampaignIds\[\$campaignId\]) \|\| isset(\$setOthersToInstalls\[\$campaignId\])){ \$response\[\$campaignId\]\[\'others\'\] = \$item\[\'installs\'\]; }                                   |
| Install ,CPV         |                                                 | if(isset(\$CPVCampaignIds\[\$campaignId\])){ \$response\[\$campaignId\]\[\'others\'\] = \$item\[\'videoBillables\'\]; }                                                                               |
+----------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Now we get the inventory

- Now we get the inventory for requirements still we are in the function
  RevenueCalculator.`fetchAndOrganizeCampaignsForRevenueReportNew($requirements,$requirementGroups,$billingGroups,$orders,$includeLiveData = false,$reports = null,$lockedRevenueReports = null,$thirdPartyReport = null,$REP = null,$adNetworkRevenue = null)`;

- Also we get all the requirements inventory now we are going to find
  out inevntory for others

- 

  ------------------------- --------------------------------------------------------- ---------------------------------------------------------------------------------------------------
  **Entitity**              **Db Table**                                              **Notes**
  `$lockedRevenueReports`   daedalus.dhx_locked_revenue                               `LockedRevenue::getRevenueForRequirementsAndRequirementGroups($requirements,$requirementGroups);`
  `$thirdPartyReport`       `daedalus_reports.dhx_third_party_report_group_billing`   `ThirdPartyReportGroupBilling::getThirdPartyNumbersFromBillingGroupsAsArray($billingGroups);`
  `$REP`                    `daedalus_reports.dhx_report_groups_rep`                  `BillingGroupsREP::getREPFromBillingGroupsAsArray($billingGroups);`
  `$adNetworkRevenue`       `daedalus.dhx_requirement_prebilling_plan`                `Requirements::getREPFromObjects($requirements);`
  ------------------------- --------------------------------------------------------- ---------------------------------------------------------------------------------------------------

Now we make \$unitResponse = \[ \'report\' =\>
\$reports\[\$requirement-\>getId()\], \'object\' =\> \$requirement,
\'order\' =\> \$orderMap\[\$requirement-\>getOrderId()\],
\'lockedRevenue\' =\>
isset(\$lockedRevenueReports\[\'requirements\'\]\[\$requirementId\]) ?
\$lockedRevenueReports\[\'requirements\'\]\[\$requirementId\] : \[\],
\'adNetworkREP\' =\>
isset(\$adNetworkRevenue\[\$requirement-\>getId()\]) ?
\$adNetworkRevenue\[\$requirement-\>getId()\] : \[\], \];

object → requirement, requirement group, billing group

- we go to every requirement and check if the billing group there uses
  it same goes for requirements groups
