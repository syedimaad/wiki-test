- No caching involved , Fetch from cache is missing.

- ~~No config file similar to settings.php.~~

- No sanitizeparmaccessor directly accessing.

- Removing old location service calls and using new location endpoint
  (decison needs to be taken).

+-------------------------------------------------------------------+-----------------------------------------------------------------+----------------------+-----------------------------------------+
| **adengine php classes**                                          | **php logics**                                                  | **status in          |                                         |
|                                                                   |                                                                 | preadselect and      |                                         |
|                                                                   |                                                                 | todos.**             |                                         |
+-------------------------------------------------------------------+-----------------------------------------------------------------+----------------------+-----------------------------------------+
| 1 incomplete [prepare adengine config]{.placeholder-inline-tasks} | Fetching config from DB and setting to Adengine object.         | not built            | 12 incomplete                           |
|                                                                   |                                                                 |                      | [InProgress]{.placeholder-inline-tasks} |
|                                                                   |                                                                 |                      |                                         |
|                                                                   |                                                                 |                      | 13 incomplete                           |
|                                                                   |                                                                 |                      | [Done]{.placeholder-inline-tasks}       |
|                                                                   |                                                                 |                      |                                         |
|                                                                   |                                                                 |                      | 14 incomplete                           |
|                                                                   |                                                                 |                      | [Review]{.placeholder-inline-tasks}     |
+-------------------------------------------------------------------+-----------------------------------------------------------------+----------------------+-----------------------------------------+
| 2 incomplete [getheaders]{.placeholder-inline-tasks}              | getting headers and setting them to adengine object.            | need bit             | 15 complete                             |
|                                                                   |                                                                 | modification         | [Inprogress]{.placeholder-inline-tasks} |
|                                                                   |                                                                 |                      |                                         |
|                                                                   |                                                                 |                      | 16 complete                             |
|                                                                   |                                                                 |                      | [Done]{.placeholder-inline-tasks}       |
|                                                                   |                                                                 |                      |                                         |
|                                                                   |                                                                 |                      | 17 incomplete                           |
|                                                                   |                                                                 |                      | [Review]{.placeholder-inline-tasks}     |
+-------------------------------------------------------------------+-----------------------------------------------------------------+----------------------+-----------------------------------------+
| 3 incomplete [santizeinput]{.placeholder-inline-tasks}            | - `patchBannerCount`                                            | - Not                | 18 complete                             |
|                                                                   |                                                                 |   removing/filtering | [InProgress]{.placeholder-inline-tasks} |
|                                                                   | - `mapOSforIOSandWindows`                                       |   html tags for few  |                                         |
|                                                                   |                                                                 |   parms.             | 19 incomplete                           |
|                                                                   | - `patchNewspaperByPagetype`                                    |                      | [Done]{.placeholder-inline-tasks}       |
|                                                                   |                                                                 | - Parsing Adextras.  |                                         |
|                                                                   | - `parseParams`                                                 |                      | 20 incomplete                           |
|                                                                   |                                                                 | - Language setting   | [Review]{.placeholder-inline-tasks}     |
|                                                                   | - `parseContext`                                                |   logic change.      |                                         |
|                                                                   |                                                                 |                      |                                         |
|                                                                   | - `extractOsMajorVersion`                                       | - Getting topicId    |                                         |
|                                                                   |                                                                 |   from sharedDD      |                                         |
|                                                                   | - `renameKeys`                                                  |   data.              |                                         |
|                                                                   |                                                                 |                      |                                         |
|                                                                   | - `overrideParamsByCookieValue`                                 |                      |                                         |
|                                                                   |                                                                 |                      |                                         |
|                                                                   | - `setPremiumP1Eligibility`                                     |                      |                                         |
|                                                                   |                                                                 |                      |                                         |
|                                                                   | - `getTabIdForPremiumP1`                                        |                      |                                         |
|                                                                   |                                                                 |                      |                                         |
|                                                                   | - `mapSocialParamsToPreSocialParams`                            |                      |                                         |
|                                                                   |                                                                 |                      |                                         |
|                                                                   | - `getSubSlotsFromAdIndices`                                    |                      |                                         |
+-------------------------------------------------------------------+-----------------------------------------------------------------+----------------------+-----------------------------------------+
| 4 incomplete [cookieparsing]{.placeholder-inline-tasks}           | renaming cookies and setting excludededup cookie if its josh.   | not built            | 21 complete                             |
|                                                                   |                                                                 |                      | [InProgress]{.placeholder-inline-tasks} |
|                                                                   |                                                                 |                      |                                         |
|                                                                   |                                                                 |                      | 22 complete                             |
|                                                                   |                                                                 |                      | [Done]{.placeholder-inline-tasks}       |
|                                                                   |                                                                 |                      |                                         |
|                                                                   |                                                                 |                      | 23 incomplete                           |
|                                                                   |                                                                 |                      | [Review]{.placeholder-inline-tasks}     |
+-------------------------------------------------------------------+-----------------------------------------------------------------+----------------------+-----------------------------------------+
| 5 incomplete [adrejection]{.placeholder-inline-tasks}             | - [validateAdsBlocked]{style="color: rgb(191,38,0);"}           | - need to maintain a | 24 incomplete                           |
|                                                                   |                                                                 |   config file        | [InProgress]{.placeholder-inline-tasks} |
|                                                                   | - Fillrate                                                      |   similar to         |                                         |
|                                                                   |                                                                 |   adengines, and     | 25 incomplete                           |
|                                                                   | - validatezone                                                  |   read from them     | [Done]{.placeholder-inline-tasks}       |
|                                                                   |                                                                 |   currently all are  |                                         |
|                                                                   | - `validateNoAdCategory`                                        |   null.              | 26 incomplete                           |
|                                                                   |                                                                 |                      | [Review]{.placeholder-inline-tasks}     |
|                                                                   | - `validateAdsBlockedInNP`                                      | - Random number      |                                         |
|                                                                   |                                                                 |   genration for      |                                         |
|                                                                   | - `validateNewUser`                                             |   fillrate.          |                                         |
|                                                                   |                                                                 |                      |                                         |
|                                                                   |                                                                 | - clientid based     |                                         |
|                                                                   |                                                                 |   adblocking.        |                                         |
+-------------------------------------------------------------------+-----------------------------------------------------------------+----------------------+-----------------------------------------+
| 6 incomplete [session based rejector]{.placeholder-inline-tasks}  |                                                                 | not built            | 27 incomplete                           |
|                                                                   |                                                                 |                      | [InProgress]{.placeholder-inline-tasks} |
|                                                                   |                                                                 |                      |                                         |
|                                                                   |                                                                 |                      | 28 incomplete                           |
|                                                                   |                                                                 |                      | [Done]{.placeholder-inline-tasks}       |
|                                                                   |                                                                 |                      |                                         |
|                                                                   |                                                                 |                      | 29 incomplete                           |
|                                                                   |                                                                 |                      | [Review]{.placeholder-inline-tasks}     |
+-------------------------------------------------------------------+-----------------------------------------------------------------+----------------------+-----------------------------------------+
| 7 incomplete [getclientprofiledata]{.placeholder-inline-tasks}    | - `processClientProfile($client_id, $user_agent)`               | - setting ttl for    | 30 incomplete                           |
|                                                                   |                                                                 |   redis object is    | [InProgress]{.placeholder-inline-tasks} |
|                                                                   | - `validateAndSetDynamicASIntoIncomingAS`                       |   missing.           |                                         |
|                                                                   |                                                                 |                      | 31 incomplete                           |
|                                                                   | - `decryptRSABasedParams`                                       | - Fetching from      | [Done]{.placeholder-inline-tasks}       |
|                                                                   |                                                                 |   redis and setting  |                                         |
|                                                                   | - `proactiveLocationUpdates`                                    |   them to cache.     | 32 incomplete                           |
|                                                                   |                                                                 |                      | [Review]{.placeholder-inline-tasks}     |
|                                                                   | - `validateGPSAvailability`                                     | - Need to test       |                                         |
|                                                                   |                                                                 |   thoroughly.        |                                         |
|                                                                   | - `validateCellAvailability`                                    |                      |                                         |
|                                                                   |                                                                 |                      |                                         |
|                                                                   | - `backFillData`                                                |                      |                                         |
|                                                                   |                                                                 |                      |                                         |
|                                                                   | - `mergeAndSetAsToAdEngineData`                                 |                      |                                         |
|                                                                   |                                                                 |                      |                                         |
|                                                                   | - `setUserDetailsToAdEngineData`                                |                      |                                         |
|                                                                   |                                                                 |                      |                                         |
|                                                                   | - `have_location_params_changed`                                |                      |                                         |
|                                                                   |                                                                 |                      |                                         |
|                                                                   | - `parse_location_data_for_cookie`                              |                      |                                         |
|                                                                   |                                                                 |                      |                                         |
|                                                                   | - `get_from_redis($redisObj, $keys, $hash_sub_keys, $hash_key)` |                      |                                         |
|                                                                   |                                                                 |                      |                                         |
|                                                                   | - `getClientProfileFromRedis($uid, $redisObj)`                  |                      |                                         |
|                                                                   |                                                                 |                      |                                         |
|                                                                   | - `getProfileAndAppKeys()`                                      |                      |                                         |
|                                                                   |                                                                 |                      |                                         |
|                                                                   | - `getModelFromUA($ua)`                                         |                      |                                         |
|                                                                   |                                                                 |                      |                                         |
|                                                                   | - `getBrandPriceRangeAndDeviceType($ua)`                        |                      |                                         |
+-------------------------------------------------------------------+-----------------------------------------------------------------+----------------------+-----------------------------------------+
| 8 incomplete [contentcreation]{.placeholder-inline-tasks}         | - `ContentCreationForOldApp`                                    | built need to        | 33 incomplete                           |
|                                                                   |                                                                 | verify,test.\        | [InProgress]{.placeholder-inline-tasks} |
|                                                                   | - `ContentCreationForSocialApp`                                 |                      |                                         |
|                                                                   |                                                                 |                      | 34 incomplete                           |
|                                                                   |                                                                 |                      | [Done]{.placeholder-inline-tasks}       |
|                                                                   |                                                                 |                      |                                         |
|                                                                   |                                                                 |                      | 35 incomplete                           |
|                                                                   |                                                                 |                      | [Review]{.placeholder-inline-tasks}     |
+-------------------------------------------------------------------+-----------------------------------------------------------------+----------------------+-----------------------------------------+
| 9 incomplete [`UpdateMetadata`]{.placeholder-inline-tasks}        | `updateContentContextForCookieBasedPp1`                         | built need to        | 36 incomplete                           |
|                                                                   |                                                                 | verify,test.         | [InProgress]{.placeholder-inline-tasks} |
|                                                                   |                                                                 |                      |                                         |
|                                                                   |                                                                 |                      | 37 incomplete                           |
|                                                                   |                                                                 |                      | [Done]{.placeholder-inline-tasks}       |
|                                                                   |                                                                 |                      |                                         |
|                                                                   |                                                                 |                      | 38 incomplete                           |
|                                                                   |                                                                 |                      | [Review]{.placeholder-inline-tasks}     |
+-------------------------------------------------------------------+-----------------------------------------------------------------+----------------------+-----------------------------------------+
| 10 incomplete                                                     | similar to prepare adengine config.                             | not built            | 39 incomplete                           |
| [`PrepareAndFilterVmapConfigurations`]{.placeholder-inline-tasks} |                                                                 |                      | [InProgress]{.placeholder-inline-tasks} |
|                                                                   |                                                                 |                      |                                         |
|                                                                   |                                                                 |                      | 40 incomplete                           |
|                                                                   |                                                                 |                      | [Done]{.placeholder-inline-tasks}       |
|                                                                   |                                                                 |                      |                                         |
|                                                                   |                                                                 |                      | 41 incomplete                           |
|                                                                   |                                                                 |                      | [Review]{.placeholder-inline-tasks}     |
+-------------------------------------------------------------------+-----------------------------------------------------------------+----------------------+-----------------------------------------+
| 11 incomplete [ABselector]{.placeholder-inline-tasks}             | not needed                                                      | not needed but       | 42 incomplete                           |
|                                                                   |                                                                 | useful               | [InProgress]{.placeholder-inline-tasks} |
|                                                                   |                                                                 |                      |                                         |
|                                                                   |                                                                 |                      | 43 incomplete                           |
|                                                                   |                                                                 |                      | [Done]{.placeholder-inline-tasks}       |
|                                                                   |                                                                 |                      |                                         |
|                                                                   |                                                                 |                      | 44 incomplete                           |
|                                                                   |                                                                 |                      | [Review]{.placeholder-inline-tasks}     |
+-------------------------------------------------------------------+-----------------------------------------------------------------+----------------------+-----------------------------------------+
