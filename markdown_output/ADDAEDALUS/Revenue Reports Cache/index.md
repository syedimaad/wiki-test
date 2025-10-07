### Objective

To understand the purpose and use of revenue report cache in Daedalus

Revenue Reports Cache is used to store revenue information datewise so
that we don\'t need to recalculate it.

table structure

  ------------------- ------------------------- ----------------------- -----------------------------
  **DATABASE**        **TABLE**                 **Model In Daedalus**   **Controller In Daedalus**
  daedalus_superset   `revenue_reports_cache`   `RevenueReportCache`    `ProcessRevenueReportCache`
  ------------------- ------------------------- ----------------------- -----------------------------

### In simple words, it use to do the following things

- For the given date range it uses to calculate the revenue with the
  very core function

  \$performanceMonitor = new RevenueMonitor(); \$orderResult =
  \$performanceMonitor-\>getResultByDate(\$startDT,\$endDT,\$filters,null,true);

- now first it will empty the table with the function

  protected function deleteOrderDateWise(\$startDT, \$endDT, \$orderId)
  { \$startDate = \$startDT-\>format(\'Y-m-d\'); \$endDate =
  \$endDT-\>format(\'Y-m-d\'); \$query = RevenueReportCache::query()
  -\>where(\'order_id\',\'=\',\$orderId) -\>whereBetween(\'date\',
  \[\$startDate, \$endDate\]);
  if(!empty(\$this-\>filters\[\'campaignIds\'\])) { \$campaignIds =
  explode(\',\', \$this-\>filters\[\'campaignIds\'\]);
  \$query-\>whereIn(\'campaign_id\', \$campaignIds); }
  \$query-\>delete(); }

- it will fill it again with all updated values

- so it use to fill with function`bruteForceProcess`

  - it first fill for the direct orders without selfserve with the
    following filters

    echo \"Started DailySync for Direct Orders for today - Daedalus
    \\n\"; \$this-\>filters = \[ \'showAdPlacement\' =\> 1,
    \'removeNonBooked\' =\> 1, \'orderType\' =\> \'direct\',
    \'sourceId\' =\> \'daedalus\', \'includeOtherPublishers\' =\> 1,
    \'captureChildEntities\' =\> 1 \]; \$this-\>bruteForceProcess();

  - then for selfserve orders

    echo \"Started DailySync for Direct Orders for today - SelfServe
    \\n\"; \$this-\>filters = \[ \'showAdPlacement\' =\> 1,
    \'removeNonBooked\' =\> 0, \'orderType\' =\> \'direct\',
    \'sourceId\' =\> \'self-serve\', \'includeOtherPublishers\' =\> 1,
    \'captureChildEntities\' =\> 0 \]; \$this-\>bruteForceProcess(); /

- - then for ad networks

    echo \"Started DailySync for AdNetwork Orders for today \\n\";
    \$this-\>filters = \[ \'showAdPlacement\' =\> 1, \'removeNonBooked\'
    =\> 0, \'orderType\' =\> Orders::ORDER_TYPE_AD_NETWORK,
    \'includeOtherPublishers\' =\> 1, \'captureChildEntities\' =\> 0 \];
    \$this-\>bruteForceProcess();

- - then for the S2S and inhouse

    echo \"Started DailySync for S2S Orders for today \\n\";
    \$this-\>filters = \[ \'showAdPlacement\' =\> 1, \'removeNonBooked\'
    =\> 0, \'orderType\' =\> Orders::ORDER_TYPE_S2S_BIDDING,
    \'includeOtherPublishers\' =\> 1, \'captureChildEntities\' =\> 0 \];
    \$this-\>bruteForceProcess(); echo \"Started DailySync for INHOUSE
    Orders for today \\n\"; \$this-\>filters = \[ \'showAdPlacement\'
    =\> 1, \'removeNonBooked\' =\> 0, \'orderType\' =\>
    Orders::ORDER_TYPE_INHOUSE, \'includeOtherPublishers\' =\> 1,
    \'captureChildEntities\' =\> 0 \]; \$this-\>bruteForceProcess();
    echo \"Done\\n\";

The controller(`ProcessRevenueReportCache`) has mainly four functions
with different purposes

1.  `oneTimeSync`

    - it is there to use when we have sync data for a very long time
      like from last financial year to today

    - Used in very rare cases as it will take a very long time to run
      and all processes related to that table will stop

    - signature to run this `process:revenue-cached-reports`

2.  `dailySync`

    - it is there to sync data from the last financial
      year(`2021-04-01`) to today

    - the cronjob is set it run at 1:30 p.m daily

    - signature to run this `process:daily-revenue-cached-reports`

3.  `syncTodayData`

    - it is sync data for today\'s date

    - the cron job is set to run every 10 min

    - signature to run this
      `process:daily-revenue-cached-reports-for-today`

4.  `updateSync`

    - help to update for particular date range with given filter

    - public function updateSync(\$startDT, \$endDT, \$filters) {
      \$this-\>insertDataWithCheckExisting = true;
      \$this-\>totalStartDate = \$startDT; \$this-\>totalEndDate =
      \$endDT; \$this-\>filters = \$filters;
      \$this-\>bruteForceProcess(); }

- `this function is only used by forceCacheUpdateByOrderAPI to update direct order for one particular id`

## Bugs

1.  so there is one bug i.e on the deletion part let's understand with
    help of an example

    - our delete function takes orderId and date range and deletes the
      entry. Now, what happened if some orders come in different date
      ranges when we update the revenue cache table again it will not
      delete the previous entry so it will add there

    <!-- -->

    - we have a billing groupREP for 25th July → 100rs enter for
      orderId - 123,now let's say someone change the rep date from 25th
      July to 15th July so when our cronjob run to update the revenue
      cache table. Calculation come orderId 123 come b/w 10-20 date
      range for that there were no pre-entries so it will not delete
      just add it now we have two entries one on 25th July and other on
      15th July but for date-range 20-30 orderId 123 not come as
      currently in our system no entries for REP on orderId 123 and as
      our delete code work as orderId = \$orderId and date b/w
      (startDate and end Date) so 25th July will not delete and add it
      to it making your value increase

2.  solution :

    - so whenever we go for delete we should not take the date range as
      a chunk because it may miss we need to take the root start date
      and end Date so for ex - we need to run for dateRange: 10 - 30,

    - instead of using 10-20,20-30 always use 10-30 for deletion as we
      use to take one order Id at one time, it will not delete the
      previous entry (need to test once !!)

### Quieres :

If you need to find out the total_revenue for each host_app_id, for a
particular order_type and given date range query is

select host_app_id, sum(total_dh_revenue) from revenue_reports_cache
where date between \$startDate and \$endDate and order_type_v2 =
\$orderType group by 1 order by 1;
