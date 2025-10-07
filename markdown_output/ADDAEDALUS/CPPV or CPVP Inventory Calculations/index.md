## CPPV → Cost Per Page View , CPVP → Cost Per Video Plays

so first of all we find if any campaign has `hasContentBillingType` then
it will come under either CPPV or CPVP

- there is function `getDateWiseAttributionsForContentCampaign` to get
  datewise inventory

- public function getDateWiseAttributionsForContentCampaign(\$startDate
  = null, \$endDate = null) { \$response = \[\]; \$metricsData =
  \$this-\>getHiveMetricsDateMapForDateRange(\$startDate, \$endDate,
  false); foreach (\$metricsData as \$date =\> \$metricData){
  if(\$this-\>isCampaignCPPV()){ \$response\[\$date\] =
  \$metricData\[\'articleViews\'\]; } if(\$this-\>isCampaignCPVP()){
  \$response\[\$date\] = \$metricData\[\'videoPlays\'\]; } } return
  \$response; }

<!-- -->

- we use to call getHiveMetricsDateMapForDateRange for getting reports

- so for each requirement, we go to every banner and if a banner is
  billable we call getArticleIdsForBanner

- public function getArticleIdsForBanner() {
  if(\$this-\>isBannerTypeSinglePost()){ return
  \[\$this-\>getArticleIdForSingleContentBanner()\]; }elseif
  (\$this-\>isBannerTypeCarouselPost()){ return
  \$this-\>getArticleIdsForCarouselContentBanner(); }else{ \$articleId =
  \$this-\>getNewsItemId(); if(!empty(\$articleId)){ return
  \[\$articleId\]; } } return \[\]; }

<!-- -->

- in short, if a banner type a single post we go found the post id and
  then the article id related to it,

- if it's a carousel then we go to each and every carousel item find
  their post id and then go and get the article id

- otherwise, we go to get the news id, we get from landing URL

- now we have an article id wego and find the report

- public static function
  getArticleReportsDateMapForDateRange(\$articleIds, \$startDate = null,
  \$endDate = null) { \$response = \[\]; \$articleIdsReport =
  self::getReportsCollectionForDateRange(\$articleIds, \$startDate,
  \$endDate); \$dateMap =
  self::getDatesMapForCollection(\$articleIdsReport, \$startDate,
  \$endDate); foreach (\$dateMap as \$date =\> \$data) {
  \$response\[\$date\] = self::\$defaultResponseFormatUnit; } foreach
  (\$articleIdsReport as \$articleIdReport) { \$date =
  \$articleIdReport-\>getDate();
  \$response\[\$date\]\[\'articleViews\'\] +=
  \$articleIdReport-\>getArticleViews();
  \$response\[\$date\]\[\'totalArticleTimeSpent\'\] +=
  \$articleIdReport-\>getTotalArticleTimeSpentBasisMultiplierFlag();
  \$response\[\$date\]\[\'videoPlays\'\] +=
  \$articleIdReport-\>getVideoPlays();
  \$response\[\$date\]\[\'totalVideoTimeSpent\'\] +=
  \$articleIdReport-\>getTotalVideoTimeSpent();
  \$response\[\$date\]\[\'videoBeforeFirstQuartile\'\] +=
  \$articleIdReport-\>getVideoBeforeFirstQuartile();
  \$response\[\$date\]\[\'videoFirstQuartileCompletion\'\] +=
  \$articleIdReport-\>getVideoFirstQuartileCompletion();
  \$response\[\$date\]\[\'videoSecondQuartileCompletion\'\] +=
  \$articleIdReport-\>getVideoSecondQuartileCompletion();
  \$response\[\$date\]\[\'videoThirdQuartileCompletion\'\] +=
  \$articleIdReport-\>getVideoThirdQuartileCompletion();
  \$response\[\$date\]\[\'videoFourthQuartileCompletion\'\] +=
  \$articleIdReport-\>getVideoFourthQuartileCompletion();
  \$response\[\$date\]\[\'videoFiveSecondCompletion\'\] +=
  \$articleIdReport-\>getVideoFiveSecondCompletion();
  \$response\[\$date\]\[\'videoTenSecondCompletion\'\] +=
  \$articleIdReport-\>getVideoTenSecondCompletion();
  \$response\[\$date\]\[\'shares\'\] += \$articleIdReport-\>getShares();
  \$response\[\$date\]\[\'likes\'\] += \$articleIdReport-\>getLikes();
  \$response\[\$date\]\[\'comments\'\] +=
  \$articleIdReport-\>getComments(); } return \$response; }

<!-- -->

- if we have to find unique we call one more function
  `$uniquesDateMap = ArticleDailyUsersHLL::getArticlesUniquesDateMapForDateAndTillDate($articleIds, $startDate, $endDate);`

- so if `$uniquesFlag` key is on so we get only those in the report
  which have common

- \$uniquesDateMap =
  ArticleDailyUsersHLL::getArticlesUniquesDateMapForDateAndTillDate(\$articleIds,
  \$startDate, \$endDate); foreach (\$articleReports as \$date =\>
  \$articleReport) { \$response\[\$date\] = \$articleReport; if
  (isset(\$uniquesDateMap\[\$date\])) { \$response\[\$date\] =
  array_merge(\$response\[\$date\], \$uniquesDateMap\[\$date\]); } }

<!-- -->

- so for cppv we get article views for cpvp we get video plays

- foreach (\$metricsData as \$date =\> \$metricData){
  if(\$this-\>isCampaignCPPV()){ \$response\[\$date\] =
  \$metricData\[\'articleViews\'\]; } if(\$this-\>isCampaignCPVP()){
  \$response\[\$date\] = \$metricData\[\'videoPlays\'\]; } }
