This doc is to track the plutus ad select progress.

# Validation Tests

+-----------+-------------------------------------------------------------------------+---------------------------------------+------------------+
| **Owner** | **Tests**                                                               | **status**                            | **Notes**        |
+-----------+-------------------------------------------------------------------------+---------------------------------------+------------------+
|           | self::validateCampaignAndPlacementsLimitations(\$campaigns)             | 2 complete [In                        |                  |
|           |                                                                         | Progress]{.placeholder-inline-tasks}  |                  |
|           |                                                                         |                                       |                  |
|           |                                                                         | 3 complete                            |                  |
|           |                                                                         | [Complete]{.placeholder-inline-tasks} |                  |
+-----------+-------------------------------------------------------------------------+---------------------------------------+------------------+
|           | self::validateAdContext(\$campaignsBBFiltered)                          | 4 complete [In                        |                  |
|           |                                                                         | Progress]{.placeholder-inline-tasks}  |                  |
|           |                                                                         |                                       |                  |
|           |                                                                         | 5 incomplete                          |                  |
|           |                                                                         | [Complete]{.placeholder-inline-tasks} |                  |
+-----------+-------------------------------------------------------------------------+---------------------------------------+------------------+
|           | DeliveryHelper::validateDeliveryLimitations(\$campaignsVariantFiltered) | 6 complete [In                        |                  |
|           |                                                                         | Progress]{.placeholder-inline-tasks}  |                  |
|           |                                                                         |                                       |                  |
|           |                                                                         | 7 incomplete                          |                  |
|           |                                                                         | [Complete]{.placeholder-inline-tasks} |                  |
+-----------+-------------------------------------------------------------------------+---------------------------------------+------------------+
|           | DeliveryHelper::filterBlockedCampaigns(\$campaignsFCFiltered)           | 8 complete [In                        |                  |
|           |                                                                         | Progress]{.placeholder-inline-tasks}  |                  |
|           |                                                                         |                                       |                  |
|           |                                                                         | 9 complete                            |                  |
|           |                                                                         | [Complete]{.placeholder-inline-tasks} |                  |
+-----------+-------------------------------------------------------------------------+---------------------------------------+------------------+
|           | DeliveryHelper::flywheelValidation(\$campaignsCPFiltered)               | 10 complete [In                       |                  |
|           |                                                                         | Progress]{.placeholder-inline-tasks}  |                  |
|           |                                                                         |                                       |                  |
|           |                                                                         | 11 complete                           |                  |
|           |                                                                         | [Complete]{.placeholder-inline-tasks} |                  |
+-----------+-------------------------------------------------------------------------+---------------------------------------+------------------+
|           | DeliveryHelper::filterExcludedCampaigns()                               | 12 complete [In                       | **Need           |
|           |                                                                         | Progress]{.placeholder-inline-tasks}  | discussion**     |
|           |                                                                         |                                       |                  |
|           |                                                                         | 13 complete                           | Dedup campaigns  |
|           |                                                                         | [Complete]{.placeholder-inline-tasks} | across the       |
|           |                                                                         |                                       | incoming subslot |
|           |                                                                         |                                       | enabled          |
|           |                                                                         |                                       | placement logic  |
|           |                                                                         |                                       | need to be in    |
|           |                                                                         |                                       | adEngine itself. |
|           |                                                                         |                                       | We can't move it |
|           |                                                                         |                                       | to adselect yet. |
+-----------+-------------------------------------------------------------------------+---------------------------------------+------------------+
|           | Fallback to normal flow if adSelect fails/no data                       | 14 complete [In                       |                  |
|           |                                                                         | Progress]{.placeholder-inline-tasks}  |                  |
|           |                                                                         |                                       |                  |
|           |                                                                         | 15 complete                           |                  |
|           |                                                                         | [Complete]{.placeholder-inline-tasks} |                  |
+-----------+-------------------------------------------------------------------------+---------------------------------------+------------------+
|           | RollUP Logic                                                            | 16 complete [In                       |                  |
|           |                                                                         | Progress]{.placeholder-inline-tasks}  |                  |
|           |                                                                         |                                       |                  |
|           |                                                                         | 17 incomplete                         |                  |
|           |                                                                         | [Complete]{.placeholder-inline-tasks} |                  |
+-----------+-------------------------------------------------------------------------+---------------------------------------+------------------+
|           | AdResponse Properties / XML/JSON Sanity Checking                        | 18 incomplete [In                     |                  |
|           |                                                                         | Progress]{.placeholder-inline-tasks}  |                  |
|           |                                                                         |                                       |                  |
|           |                                                                         | 19 incomplete                         |                  |
|           |                                                                         | [Complete]{.placeholder-inline-tasks} |                  |
+-----------+-------------------------------------------------------------------------+---------------------------------------+------------------+
|           | Ranking Service Call                                                    | 20 incomplete [In                     |                  |
|           |                                                                         | Progress]{.placeholder-inline-tasks}  |                  |
|           |                                                                         |                                       |                  |
|           |                                                                         | 21 incomplete                         |                  |
|           |                                                                         | [Complete]{.placeholder-inline-tasks} |                  |
+-----------+-------------------------------------------------------------------------+---------------------------------------+------------------+
|           | VMAP/Vast Check                                                         | 22 complete [In                       |                  |
|           |                                                                         | Progress]{.placeholder-inline-tasks}  |                  |
|           |                                                                         |                                       |                  |
|           |                                                                         | 23 incomplete                         |                  |
|           |                                                                         | [Complete]{.placeholder-inline-tasks} |                  |
+-----------+-------------------------------------------------------------------------+---------------------------------------+------------------+
|           | self::filterCampaignsByPartners(\$campaignsCPCFiltered)                 | 24 complete [In                       |                  |
|           |                                                                         | Progress]{.placeholder-inline-tasks}  |                  |
|           |                                                                         |                                       |                  |
|           |                                                                         | 25 complete                           |                  |
|           |                                                                         | [Complete]{.placeholder-inline-tasks} |                  |
+-----------+-------------------------------------------------------------------------+---------------------------------------+------------------+
|           | DeliveryHelper::validateCampaignVariant(\$campaignsContextFiltered,     | 26 complete [In                       |                  |
|           | \$campaignVariant)                                                      | Progress]{.placeholder-inline-tasks}  |                  |
|           |                                                                         |                                       |                  |
|           |                                                                         | 27 complete                           |                  |
|           |                                                                         | [Complete]{.placeholder-inline-tasks} |                  |
+-----------+-------------------------------------------------------------------------+---------------------------------------+------------------+
|           | DeliveryHelper::validateFrequencyCapping(\$campaignsDLFiltered)         | 28 complete [In                       |                  |
|           |                                                                         | Progress]{.placeholder-inline-tasks}  |                  |
|           |                                                                         |                                       |                  |
|           |                                                                         | 29 complete                           |                  |
|           |                                                                         | [Complete]{.placeholder-inline-tasks} |                  |
+-----------+-------------------------------------------------------------------------+---------------------------------------+------------------+
|           | DeliveryHelper::validateCampaignProperties(\$campaignsBLKFiltered)      | 30 complete [In                       | Some logics are  |
|           |                                                                         | Progress]{.placeholder-inline-tasks}  | removed as it is |
|           |                                                                         |                                       | not needed       |
|           |                                                                         | 31 complete                           | anymore.         |
|           |                                                                         | [Complete]{.placeholder-inline-tasks} |                  |
+-----------+-------------------------------------------------------------------------+---------------------------------------+------------------+
|           | AdEngine Campaign Obect Properties Validation                           | 32 complete [In                       |                  |
|           |                                                                         | Progress]{.placeholder-inline-tasks}  |                  |
|           |                                                                         |                                       |                  |
|           |                                                                         | 33 complete                           |                  |
|           |                                                                         | [Complete]{.placeholder-inline-tasks} |                  |
+-----------+-------------------------------------------------------------------------+---------------------------------------+------------------+
|           | Data Instrumentation ( Data logging )                                   | 34 complete [In                       |                  |
|           |                                                                         | Progress]{.placeholder-inline-tasks}  |                  |
|           |                                                                         |                                       |                  |
|           |                                                                         | 35 complete                           |                  |
|           |                                                                         | [Complete]{.placeholder-inline-tasks} |                  |
+-----------+-------------------------------------------------------------------------+---------------------------------------+------------------+
|           | banner selection/banner object creation Sanity                          | 36 complete [In                       |                  |
|           |                                                                         | Progress]{.placeholder-inline-tasks}  |                  |
|           |                                                                         |                                       |                  |
|           |                                                                         | 37 complete                           |                  |
|           |                                                                         | [Complete]{.placeholder-inline-tasks} |                  |
+-----------+-------------------------------------------------------------------------+---------------------------------------+------------------+
|           | S2S validation                                                          | 38 complete [In                       |                  |
|           |                                                                         | Progress]{.placeholder-inline-tasks}  |                  |
|           |                                                                         |                                       |                  |
|           |                                                                         | 39 complete                           |                  |
|           |                                                                         | [Complete]{.placeholder-inline-tasks} |                  |
+-----------+-------------------------------------------------------------------------+---------------------------------------+------------------+
|           | AdLoad                                                                  | 40 complete [In                       |                  |
|           |                                                                         | Progress]{.placeholder-inline-tasks}  |                  |
|           |                                                                         |                                       |                  |
|           |                                                                         | 41 complete                           |                  |
|           |                                                                         | [Complete]{.placeholder-inline-tasks} |                  |
+-----------+-------------------------------------------------------------------------+---------------------------------------+------------------+
|           | multi tenancy check                                                     | 42 complete [In                       | Fcap is          |
|           |                                                                         | Progress]{.placeholder-inline-tasks}  | validated.       |
|           |                                                                         |                                       |                  |
|           |                                                                         | 43 complete                           | campaigns are    |
|           |                                                                         | [Complete]{.placeholder-inline-tasks} | getting fetched. |
+-----------+-------------------------------------------------------------------------+---------------------------------------+------------------+
|           | response time/errors/monitoring                                         | 44 incomplete [In                     |                  |
|           |                                                                         | Progress]{.placeholder-inline-tasks}  |                  |
|           |                                                                         |                                       |                  |
|           |                                                                         | 45 incomplete                         |                  |
|           |                                                                         | [Complete]{.placeholder-inline-tasks} |                  |
+-----------+-------------------------------------------------------------------------+---------------------------------------+------------------+
|           | AdEngine Properties like n/w settings \[ less priority \]               | 46 incomplete [In                     |                  |
|           |                                                                         | Progress]{.placeholder-inline-tasks}  |                  |
|           |                                                                         |                                       |                  |
|           |                                                                         | 47 incomplete                         |                  |
|           |                                                                         | [Complete]{.placeholder-inline-tasks} |                  |
+-----------+-------------------------------------------------------------------------+---------------------------------------+------------------+
