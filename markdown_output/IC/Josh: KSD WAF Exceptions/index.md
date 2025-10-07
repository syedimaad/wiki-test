+-------------------+------------------+-------------------------------------------+-------------------------------------------+
| **Configuration** | **Policy**       | **Attack Groups**                         | **Exceptions**                            |
+-------------------+------------------+-------------------------------------------+-------------------------------------------+
| **New Verse MSC** | **Cache-API**    | Cross Site Scripting                      | - **Cookies:** sign_info                  |
|                   |                  +-------------------------------------------+-------------------------------------------+
|                   |                  | Web Attack Tool                           | - **Cookies:** sign_info                  |
+-------------------+------------------+-------------------------------------------+-------------------------------------------+
| **Verse -         | **Gateway-Feed** | Web Attack Tool                           | - **JSON parameter:**                     |
| mypjosh**         |                  |                                           |   connection_info.apn_name                |
+-------------------+------------------+-------------------------------------------+-------------------------------------------+
| **Verse - New     | **New Policy**   | **[None]{style="color: rgb(191,38,0);"}** | **[None]{style="color: rgb(191,38,0);"}** |
| Onboarding**      |                  |                                           |                                           |
|                   +------------------+-------------------------------------------+-------------------------------------------+
|                   | **Non-Prod**     | **[None]{style="color: rgb(191,38,0);"}** | **[None]{style="color: rgb(191,38,0);"}** |
+-------------------+------------------+-------------------------------------------+-------------------------------------------+
| **Verse --        | **Data**         | **[None]{style="color: rgb(191,38,0);"}** | **[None]{style="color: rgb(191,38,0);"}** |
| Primary**         |                  |                                           |                                           |
|                   +------------------+-------------------------------------------+-------------------------------------------+
|                   | **Josh Policy**  | **[None]{style="color: rgb(191,38,0);"}** | **[None]{style="color: rgb(191,38,0);"}** |
+-------------------+------------------+-------------------------------------------+-------------------------------------------+
| **Verse --        | **Gateway-Feed** | Web Attack Tool                           | - **JSON parameter:**                     |
| Secondary**       |                  |                                           |   connection_info.apn_name                |
+-------------------+------------------+-------------------------------------------+-------------------------------------------+

> **Refer below hostnames based on associated configuration and policy
> name.**

+-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
| **Configuration**     | **Policy**            | **Hostnames**                                                                           |
+-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
| **New Verse MSC**     | **Cache-API**         | - [cache-api.myjosh.in](http://cache-api.myjosh.in)                                     |
+-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
| **Verse - mypjosh**   | **Gateway-Feed**      | - [gateway.mypjosh.in](http://gateway.mypjosh.in)                                       |
|                       |                       |                                                                                         |
|                       |                       | - [feed.mypjosh.in](http://feed.mypjosh.in)                                             |
+-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
| **Verse - New         | **New Policy**        | - [jot.myjosh.in](http://jot.myjosh.in)                                                 |
| Onboarding**          |                       |                                                                                         |
|                       |                       | - [analytics.verse.in](http://analytics.verse.in)                                       |
|                       |                       |                                                                                         |
|                       |                       | - [api.myjosh.in](http://api.myjosh.in)                                                 |
|                       |                       |                                                                                         |
|                       |                       | - [josh-lib.myjosh.in](http://josh-lib.myjosh.in)                                       |
|                       |                       |                                                                                         |
|                       |                       | - [www.verse.in](http://www.verse.in)                                                   |
|                       |                       |                                                                                         |
|                       |                       | - [support.myjosh.in](http://support.myjosh.in)                                         |
|                       +-----------------------+-----------------------------------------------------------------------------------------+
|                       | **Non-Prod**          | - [qa-share.myjosh.in](http://qa-share.myjosh.in)                                       |
|                       |                       |                                                                                         |
|                       |                       | - [api-qa-az.myjosh.in](http://api-qa-az.myjosh.in)                                     |
|                       |                       |                                                                                         |
|                       |                       | - [qa-abof.myjosh.in](http://qa-abof.myjosh.in)                                         |
|                       |                       |                                                                                         |
|                       |                       | - [share-qa-az.myjosh.in](http://share-qa-az.myjosh.in)                                 |
|                       |                       |                                                                                         |
|                       |                       | - [feed-qa-az.myjosh.in](http://feed-qa-az.myjosh.in)                                   |
|                       |                       |                                                                                         |
|                       |                       | - [qa-josh-sticky-notification.myjosh.in](http://qa-josh-sticky-notification.myjosh.in) |
|                       |                       |                                                                                         |
|                       |                       | - [qa-api.myjosh.in](http://qa-api.myjosh.in)                                           |
|                       |                       |                                                                                         |
|                       |                       | - [stage-josh-notif-sticky.myjosh.in](http://stage-josh-notif-sticky.myjosh.in)         |
|                       |                       |                                                                                         |
|                       |                       | - [gateway-qa-az.myjosh.in](http://gateway-qa-az.myjosh.in)                             |
|                       |                       |                                                                                         |
|                       |                       | - [stage-share.myjosh.in](http://stage-share.myjosh.in)                                 |
+-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
| **Verse -- Primary**  | **Data**              | - [data.myjosh.in](http://data.myjosh.in)                                               |
|                       +-----------------------+-----------------------------------------------------------------------------------------+
|                       | **Josh Policy**       | - [api.coolfie.io](http://api.coolfie.io)                                               |
|                       |                       |                                                                                         |
|                       |                       | - [share.myjosh.in](http://share.myjosh.in)                                             |
|                       |                       |                                                                                         |
|                       |                       | - [webitem-share.myjosh.in](http://webitem-share.myjosh.in)                             |
|                       |                       |                                                                                         |
|                       |                       | - [share.coolfie.io](http://share.coolfie.io)                                           |
+-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
| **Verse --            | **Gateway-Feed**      | - [gateway.myjosh.in](http://gateway.myjosh.in)                                         |
| Secondary**           |                       |                                                                                         |
|                       |                       | - [gateway.coolfie.io](http://gateway.coolfie.io)                                       |
|                       |                       |                                                                                         |
|                       |                       | - [abof.myjosh.in](http://abof.myjosh.in)                                               |
|                       |                       |                                                                                         |
|                       |                       | - [feed.coolfie.io](http://feed.coolfie.io)                                             |
|                       |                       |                                                                                         |
|                       |                       | - [feed.myjosh.in](http://feed.myjosh.in)                                               |
+-----------------------+-----------------------+-----------------------------------------------------------------------------------------+
