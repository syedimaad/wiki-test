Parms & Naming tags in Mail Report :

CR1 Report and Parms mapping:

full-widthInHouse inhouseApp: impressions_inhouse_app inhouseMWeb
default : impressions_inhouse_wap not empty ( impressions_inhouse_appweb
& impressions_inhouse_mweb) : impressions_inhouse_mweb inhouseAppWeb not
empty ( impressions_inhouse_appweb & impressions_inhouse_mweb) :
impressions_inhouse_appweb AdNetwork adnetworkApp:
impressions_adnetwork_app adnetworkMWeb: default :
impressions_adnetwork_wap not empty (impressions_adnetwork_appweb &
impressions_adnetwork_mweb) : impressions_adnetwork_mweb
adnetworkAppWeb: not empty (impressions_adnetwork_appweb &
impressions_adnetwork_mweb) : impressions_adnetwork_appweb SelfServe
selfServeApp: impressions_selfserve_app selfServeMWeb: default :
impressions_selfserve_wap not empty (impressions_selfserve_appweb &
impressions_selfserve_mweb) : impressions_selfserve_mweb
selfServeAppWeb: not empty (impressions_selfserve_appweb &
impressions_selfserve_mweb) : impressions_selfserve_appweb Direct
directApp: impressions_direct_app directMWeb: default:
impressions_direct_wap not empty (impressions_direct_appweb &
impressions_direct_mweb) : impressions_direct_mweb directAppWeb: not
empty (impressions_direct_appweb & impressions_direct_mweb) :
impressions_direct_appweb

Params & source Mapping:

full-widthimpressions_inhouse_app : Query : select
sum(impressions),zone_id,partner_id from
oads.ox_data_intermediate_ad_zone where interval_start like \'\" +
date + \"%\' and \" \\ \"ad_id in (select id from
daedalus.dhx_daedalus_banners where campaign_id in (select id from
daedalus.dhx_requirements where host_app_id=\'\"+hostAppId+\"\' and
order_id in (select id from daedalus.dhx_orders where order_type_v2=1)
\" \\ \"and id not in (-2))) group by zone_id,partner_id; \-- Remove
Impressions from above numbers \-- select
sum(impressions),zone_id,partner_id from
oads.ox_data_intermediate_ad_zone where interval_start like \'\" +
date + \"%\' and (host_app_id=\'\" + hostAppId + \"\' or host_app_id is
NULL) and ad_id in (\" + bannerid_supplement_noncommercial + \") and
zone_id=10164 group by partner_id; Only For : for zone_id NOT IN
\[8012,8007,8008,8009,12014,12015,12016,12017,12018,12019,12020\] (web
zone ids) impressions_inhouse_wap : Query : Query same as
\"impressions_inhouse_app\" Only For : for zone_id in
\[8012,8007,8008,8009,12014,12015,12016,12017,12018,12019,12020\] (web
zone ids) impressions_inhouse_mweb : Query : \"select
sum(properties_impression_count),properties_partner_id from
default.nrt_ads_events_view where properties_et_day=%s \\ and
properties_et_month=%s and properties_et_year=%s and
properties_placement in (%s) and properties_order_type_v2=1 \\ and
properties_campaign_id not in (\'-2\') \\ and length(client_id)\>10 and
properties_host_app_id =\'%s\' group by properties_partner_id;\"\"\" %
(day, month, year, zone_names,hostAppId)\" impressions_inhouse_appweb :
Query : \"select sum(properties_impression_count),properties_partner_id
from default.nrt_ads_events_view where properties_et_day=%s \\ and
properties_et_month=%s and properties_et_year=%s and
properties_placement in (%s) and properties_order_type_v2=1 \\ and
properties_campaign_id not in (\'-2\') \\ and length(client_id)\<=10 and
properties_host_app_id =\'%s\' group by properties_partner_id;\"\"\" %
(day, month, year, zone_names,hostAppId)\" impressions_adnetwork_app :
Query : \"select sum(impressions),zone_id,partner_id from
oads.ox_data_intermediate_ad_zone where interval_start like \'\" +
date + \"%\' \" \\ \"and ad_id in (select id from
daedalus.dhx_daedalus_banners where campaign_id in \" \\ \"(select id
from daedalus.dhx_requirements where host_app_id=\'\" + hostAppId + \"\'
and order_id in (select id from daedalus.dhx_orders where order_type_v2
in (2,3)))) \" \\ \"and ad_id not in (\" + exclude_bannerid + \") group
by zone_id,partner_id;\" Only for : for zone_id NOT IN
\[8012,8007,8008,8009,12014,12015,12016,12017,12018,12019,12020\] (web
zone ids) impressions_inhouse_wap : Query: Same as above Add Adx numbers
Only For : for zone_id IN
\[8012,8007,8008,8009,12014,12015,12016,12017,12018,12019,12020\] (web
zone ids) impressions_adnetwork_mweb : Query : \"select
sum(properties_impression_count),properties_partner_id from
default.nrt_ads_events_view where properties_et_day=%s \\ and
properties_et_month=%s and properties_et_year=%s and
properties_placement in (%s) and properties_order_type_v2 in (2,3) \\
and properties_banner_id not in (%s) \\ and length(client_id)\>10 and
properties_host_app_id =\'%s\' group by properties_partner_id;\"\"\" %
(day, month, year, zone_names, exclude_bannerid,hostAppId)\"\"
impressions_inhouse_appweb : Query : \"select
sum(properties_impression_count),properties_partner_id from
default.nrt_ads_events_view where properties_et_day=%s \\ and
properties_et_month=%s and properties_et_year=%s and
properties_placement in (%s) and properties_order_type_v2=1 \\ and
properties_campaign_id not in (\'-2\') \\ and length(client_id)\<=10 and
properties_host_app_id =\'%s\' group by properties_partner_id;\"\"\" %
(day, month, year, zone_names,hostAppId)\" impressions_selfserve_app :
clicks_selfserve_app : Query : \"select
sum(impressions),sum(clicks),zone_id,partner_id from
oads.ox_data_intermediate_ad_zone where interval_start like \'\" +
date + \"%\'\" \\ \" and ad_id in (select id from
daedalus.dhx_daedalus_banners where campaign_id in (select id from
daedalus.dhx_requirements where \" \\ \"host_app_id= \'\"+hostAppId+\"\'
and order_id in (select id from daedalus.dhx_orders where
order_type_v2=0) and is_selfserve=1)) group by zone_id,partner_id;\"
Only For : for zone_id NOT IN
\[8012,8007,8008,8009,12014,12015,12016,12017,12018,12019,12020\] (web
zone ids) impressions_selfserve_wap : clicks_selfserve_wap : Query :
\"select sum(impressions),sum(clicks),zone_id,partner_id from
oads.ox_data_intermediate_ad_zone where interval_start like \'\" +
date + \"%\'\" \\ \" and ad_id in (select id from
daedalus.dhx_daedalus_banners where campaign_id in (select id from
daedalus.dhx_requirements where \" \\ \"host_app_id= \'\"+hostAppId+\"\'
and order_id in (select id from daedalus.dhx_orders where
order_type_v2=0) and is_selfserve=1)) group by zone_id,partner_id;\"
Only For : for zone_id IN
\[8012,8007,8008,8009,12014,12015,12016,12017,12018,12019,12020\] (web
zone ids) impressions_selfserve_mweb : Query : \"select
sum(properties_impression_count),properties_partner_id from
default.nrt_ads_events_view where properties_et_day=%s \\ and
properties_et_month=%s and properties_et_year=%s and
properties_placement in (%s) and properties_order_type_v2=0 and
properties_is_selfserve=1 \\ and length(client_id)\>10 and
properties_host_app_id =\'%s\' group by properties_partner_id;\"\"\" %
(day, month, year, zone_names,hostAppId)\" impressions_selfserve_appweb
: Query : \"select
sum(properties_impression_count),properties_partner_id from
default.nrt_ads_events_view where properties_et_day=%s \\ and
properties_et_month=%s and properties_et_year=%s and
properties_placement in (%s) and properties_order_type_v2=0 and
properties_is_selfserve=1 \\ and length(client_id)\<=10 and
properties_host_app_id =\'%s\' group by properties_partner_id;\"\"\" %
(day, month, year, zone_names,hostAppId)\" impressions_direct_app :
clicks_direct_app : Query : \"select
sum(impressions),sum(clicks),zone_id,partner_id from
oads.ox_data_intermediate_ad_zone where interval_start like \'\" +
date + \"%\' \" \\ \" and ad_id in (select id from
daedalus.dhx_daedalus_banners where campaign_id in (select id from
daedalus.dhx_requirements where \" \\ \"host_app_id=\'\"+hostAppId+\"\'
and order_id in (select id from daedalus.dhx_orders where
order_type_v2=0) and is_selfserve=0)) group by zone_id,partner_id;\"
Only For : for zone_id NOT IN
\[8012,8007,8008,8009,12014,12015,12016,12017,12018,12019,12020\] (web
zone ids) impressions_direct_wap : clicks_direct_wap : Query : \"select
sum(impressions),sum(clicks),zone_id,partner_id from
oads.ox_data_intermediate_ad_zone where interval_start like \'\" +
date + \"%\' \" \\ \" and ad_id in (select id from
daedalus.dhx_daedalus_banners where campaign_id in (select id from
daedalus.dhx_requirements where \" \\ \"host_app_id=\'\"+hostAppId+\"\'
and order_id in (select id from daedalus.dhx_orders where
order_type_v2=0) and is_selfserve=0)) group by zone_id,partner_id;\"
Only For : for zone_id IN
\[8012,8007,8008,8009,12014,12015,12016,12017,12018,12019,12020\] (web
zone ids) impressions_direct_mweb : Query : \"select
sum(properties_impression_count),properties_partner_id from
default.nrt_ads_events_view where properties_et_day=%s \\ and
properties_et_month=%s and properties_et_year=%s and
properties_placement in (%s) and properties_order_type_v2=0 and
properties_is_selfserve=0 \\ and length(client_id)\>10 and
properties_host_app_id =\'%s\' group by properties_partner_id ;\"\"\"
%(day,month,year,zone_names,hostAppId)\" impressions_direct_appweb :
Query : \"select sum(properties_impression_count),properties_partner_id
from default.nrt_ads_events_view where properties_et_day=%s \\ and
properties_et_month=%s and properties_et_year=%s and
properties_placement in (%s) and properties_order_type_v2=0 and
properties_is_selfserve=0 \\ and length(client_id)\<=10 and
properties_host_app_id =\'%s\' group by properties_partner_id ;\"\"\"
%(day,month,year,zone_names,hostAppId)\"

Q:Need to web verify zone ids

Q: Client id length for mweb and appweb.
