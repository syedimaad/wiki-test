**Objective: To understand the flow and how we calculate partner
revenue**

- Partner data i.e impression, clicks, date, campaign_id,partner_id
  these all stored in a table
  daedalus_reports.`ads_partner_count_by_zone`

- we have two other tables related to partner which store some info

  - daedalus.`dhx_partner_properties` store all info related to partner

  - daedalus.`dhx_partner_groups` stores partners groups i.e
    \[partner_properties\]

**Flow to get partner data**

- First of all we send three parameter entity Id (partner id) ,
  reportType which decide what you want in reports by default it is
  \'`partnerRevenue`\' and date-range for you want the report

- through the help of reportType we decide which function we need to
  call in ReportGenerator.`renderReport`

- now with help of partner id (entity id) we calculate the data(i.e
  impression, click,campaign_id ) for the given date range and stored it

- In the Next step, we go and extract all campaign id from the previous
  data found the related requirement groups,billing group and use the
  same core function to calculate revenue

- Now we have two reports one with help of revenue core function which
  contain dailyhunt no and other partner no we call function
  ReportGenerator.`calculateRevenueShare` to calculate final revenue

- we use below logic to calculate revenue

  \$factor = round((float) \$report\[\$dimension\]\[\$date\] /
  \$fullReport\[\$dimension\]\[\'during\'\]\[\$date\],6); if(\$factor \>
  1){ \$factor = 1; } \$response\[\'deliveryFactor\'\]\[\$date\] =
  \$factor; \$revenueToMultiply =
  \$fullReport\[\"revenue\"\]\[\'during\'\]\[\$date\];
  \$response\[\'revenue\'\]\[\$date\] = round(\$revenueToMultiply \*
  \$factor \* \$revenueShareFactor, 2);
  \$response\[\'consumption\'\]\[\$date\] = round(\$revenueToMultiply \*
  \$factor, 2); \$currentDate = new Carbon(\$date); if((\$lockedTillDate
  && \$currentDate-\>lte(\$lockedTillDate)) \|\|
  \$fullReport\[\'order\'\]-\>hasExternalRevenue()){
  \$response\[\'confirmedRevenue\'\]\[\$date\] =
  \$response\[\'revenue\'\]\[\$date\]; }

- here report is partner report ,fullReport → calulcated by DH
  revenueShareFactor already created factor

- now we again store this info for each requirements and then send out
  the reports

**References**

1.  Link to view partner reports:
    <https://direct.dailyhunt.in/partner-reports/list-groups>

2.  Function to find out which function needs to call to generate
    reports ReportGenerator.`renderReport`

3.  Function to calculate report for a partner
    `ReportGeneratot. getRevenueReportForPartner($property,$dates)`

4.  Function to get DH reports

    \$organizedReports =
    ReportsGenerator::fetchAndOrganizeCampaignsForRevenueReportNew(\$requirementsMap,\$requirementGroupsMap,\$billingGroupsMap,\$allOrdersMap);
    \$data =
    ReportsGenerator::processRevenueReportForAllCampaignsNew(\$organizedReports,\$dates,false);

5.  RevenueCalculator.`calculateRevenueShare(&$fullReport,$report,$dateMap = [],$revenueShare = 0)`
    for calculating shared Revenue / reprot\--\> partnerReport ,
    fullReport\--\> DH report

6.  DB info:

    - daedalus_reports.`ads_partner_count_by_zone` → stores partner
      inventory

    - daedalus.`dhx_partner_properties` store all info related to
      partner

    - daedalus.`dhx_partner_groups` stores partners groups i.e
      \[partner_properties\]
