Got requirment to get all Projects LBs max rps , below script helps

Error handling for null not considered\

Provide projects in txt file and run command to get all

projects.txt\
\

cat projects.txt et-gcp-news-prod et-gcp-analytics-prod dh-gcp-ads-prod
et-gcp-aiml-prod-v2 et-gcp-news-qa dh-gcp-networking-hub
et-gcp-aiml-prod dh-gcp-networking-prod dh-gcp-ads-qa
dh-gcp-news-content-ftp dh-gcp-gpu-overcommit et-gcp-analytics-qa
et-gcp-aiml-sandbox et-gcp-news-stage

script to collect metrics

#!/bin/bash projectid=\"\$1\" #Global LB
global_lb_response_bytes=\$(curl -s -X GET
\"https://monitoring.googleapis.com/v3/projects/\$projectid/timeSeries?filter=metric.type%3D%22loadbalancing.googleapis.com%2Fhttps%2Fresponse_bytes_count%22&interval.startTime=2025-09-03T14:23:14.656Z&interval.endTime=2025-09-04T14:23:14.656Z&aggregation.alignmentPeriod=60s&aggregation.perSeriesAligner=ALIGN_MAX&aggregation.crossSeriesReducer=REDUCE_MAX\"
-H \"Authorization: Bearer \$ACCESS_TOKEN\" -H \"Content-Type:
application/json\" \| jq \'\[.timeSeries\[\].points\[\].value.int64Value
\| tonumber\] \| max\') echo
\$projectid,global_lb_response_bytes,\$global_lb_response_bytes
global_lb_request_bytes=\$(curl -s -X GET
\"https://monitoring.googleapis.com/v3/projects/\$projectid/timeSeries?filter=metric.type%3D%22loadbalancing.googleapis.com%2Fhttps%2Frequest_bytes_count%22&interval.startTime=2025-09-03T14:23:14.656Z&interval.endTime=2025-09-04T14:23:14.656Z&aggregation.alignmentPeriod=60s&aggregation.perSeriesAligner=ALIGN_MAX&aggregation.crossSeriesReducer=REDUCE_MAX\"
-H \"Authorization: Bearer \$ACCESS_TOKEN\" -H \"Content-Type:
application/json\" \| jq \'\[.timeSeries\[\].points\[\].value.int64Value
\| tonumber\] \| max\') echo
\$projectid,global_lb_request_bytes,\$global_lb_request_bytes
global_lb_request_count=\$(curl -s -X GET
\"https://monitoring.googleapis.com/v3/projects/\$projectid/timeSeries?filter=metric.type%3D%22loadbalancing.googleapis.com%2Fhttps%2Frequest_count%22&interval.startTime=2025-09-03T14:23:14.656Z&interval.endTime=2025-09-04T14:23:14.656Z&aggregation.alignmentPeriod=60s&aggregation.perSeriesAligner=ALIGN_MAX&aggregation.crossSeriesReducer=REDUCE_MAX\"
-H \"Authorization: Bearer \$ACCESS_TOKEN\" -H \"Content-Type:
application/json\" \| jq \'\[.timeSeries\[\].points\[\].value.int64Value
\| tonumber\] \| max\') echo
\$projectid,global_lb_request_count,\$global_lb_request_count #Internal
LB: internal_lb_response_bytes=\$(curl -s -X GET
\"https://monitoring.googleapis.com/v3/projects/\$projectid/timeSeries?filter=metric.type%3D%22loadbalancing.googleapis.com%2Fhttps%2Finternal%2Fresponse_bytes_count%22&interval.startTime=2025-09-03T14:23:14.656Z&interval.endTime=2025-09-04T14:23:14.656Z&aggregation.alignmentPeriod=60s&aggregation.perSeriesAligner=ALIGN_MAX&aggregation.crossSeriesReducer=REDUCE_MAX\"
-H \"Authorization: Bearer \$ACCESS_TOKEN\" -H \"Content-Type:
application/json\" \| jq \'\[.timeSeries\[\].points\[\].value.int64Value
\| tonumber\] \| max\') echo
\$projectid,internal_lb_response_bytes,\$internal_lb_response_bytes
internal_lb_request_bytes=\$(curl -s -X GET
\"https://monitoring.googleapis.com/v3/projects/\$projectid/timeSeries?filter=metric.type%3D%22loadbalancing.googleapis.com%2Fhttps%2Finternal%2Frequest_bytes_count%22&interval.startTime=2025-09-03T14:23:14.656Z&interval.endTime=2025-09-04T14:23:14.656Z&aggregation.alignmentPeriod=60s&aggregation.perSeriesAligner=ALIGN_MAX&aggregation.crossSeriesReducer=REDUCE_MAX\"
-H \"Authorization: Bearer \$ACCESS_TOKEN\" -H \"Content-Type:
application/json\" \| jq \'\[.timeSeries\[\].points\[\].value.int64Value
\| tonumber\] \| max\') echo
\$projectid,internal_lb_request_bytes,\$internal_lb_request_bytes
internal_lb_request_count=\$(curl -s -X GET
\"https://monitoring.googleapis.com/v3/projects/\$projectid/timeSeries?filter=metric.type%3D%22loadbalancing.googleapis.com%2Fhttps%2Finternal%2Frequest_count%22&interval.startTime=2025-09-03T14:23:14.656Z&interval.endTime=2025-09-04T14:23:14.656Z&aggregation.alignmentPeriod=60s&aggregation.perSeriesAligner=ALIGN_MAX&aggregation.crossSeriesReducer=REDUCE_MAX\"
-H \"Authorization: Bearer \$ACCESS_TOKEN\" -H \"Content-Type:
application/json\" \| jq \'\[.timeSeries\[\].points\[\].value.int64Value
\| tonumber\] \| max\') echo
\$projectid,internal_lb_request_count,\$internal_lb_request_count
#Internal L3: internal_l3_egress_bytes=\$(curl -s -X GET
\"https://monitoring.googleapis.com/v3/projects/\$projectid/timeSeries?filter=metric.type%3D%22loadbalancing.googleapis.com%2Fl3%2Finternal%2Fegress_bytes_count%22&interval.startTime=2025-09-03T14:23:14.656Z&interval.endTime=2025-09-04T14:23:14.656Z&aggregation.alignmentPeriod=60s&aggregation.perSeriesAligner=ALIGN_MAX&aggregation.crossSeriesReducer=REDUCE_MAX\"
-H \"Authorization: Bearer \$ACCESS_TOKEN\" -H \"Content-Type:
application/json\" \| jq \'\[.timeSeries\[\].points\[\].value.int64Value
\| tonumber\] \| max\') echo
\$projectid,internal_l3_egress_bytes,\$internal_l3_egress_bytes
internal_l3_ingress_bytes=\$(curl -s -X GET
\"https://monitoring.googleapis.com/v3/projects/\$projectid/timeSeries?filter=metric.type%3D%22loadbalancing.googleapis.com%2Fl3%2Finternal%2Fingress_bytes_count%22&interval.startTime=2025-09-03T14:23:14.656Z&interval.endTime=2025-09-04T14:23:14.656Z&aggregation.alignmentPeriod=60s&aggregation.perSeriesAligner=ALIGN_MAX&aggregation.crossSeriesReducer=REDUCE_MAX\"
-H \"Authorization: Bearer \$ACCESS_TOKEN\" -H \"Content-Type:
application/json\" \| jq \'\[.timeSeries\[\].points\[\].value.int64Value
\| tonumber\] \| max\') echo
\$projectid,internal_l3_ingress_bytes,\$internal_l3_ingress_bytes
internal_l3_egress_packet_count=\$(curl -s -X GET
\"https://monitoring.googleapis.com/v3/projects/\$projectid/timeSeries?filter=metric.type%3D%22loadbalancing.googleapis.com%2Fl3%2Finternal%2Fegress_packets_count%22&interval.startTime=2025-09-03T14:23:14.656Z&interval.endTime=2025-09-04T14:23:14.656Z&aggregation.alignmentPeriod=60s&aggregation.perSeriesAligner=ALIGN_MAX&aggregation.crossSeriesReducer=REDUCE_MAX\"
-H \"Authorization: Bearer \$ACCESS_TOKEN\" -H \"Content-Type:
application/json\" \| jq \'\[.timeSeries\[\].points\[\].value.int64Value
\| tonumber\] \| max\') echo
\$projectid,internal_l3_egress_packet_count,\$internal_l3_egress_packet_count
internal_l3_ingress_packet_count=\$(curl -s -X GET
\"https://monitoring.googleapis.com/v3/projects/\$projectid/timeSeries?filter=metric.type%3D%22loadbalancing.googleapis.com%2Fl3%2Finternal%2Fingress_packets_count%22&interval.startTime=2025-09-03T14:23:14.656Z&interval.endTime=2025-09-04T14:23:14.656Z&aggregation.alignmentPeriod=60s&aggregation.perSeriesAligner=ALIGN_MAX&aggregation.crossSeriesReducer=REDUCE_MAX\"
-H \"Authorization: Bearer \$ACCESS_TOKEN\" -H \"Content-Type:
application/json\" \| jq \'\[.timeSeries\[\].points\[\].value.int64Value
\| tonumber\] \| max\') echo
\$projectid,internal_l3_ingress_packet_count,\$internal_l3_ingress_packet_count
#External L3: external_l3_egress_packet_count=\$(curl -s -X GET
\"https://monitoring.googleapis.com/v3/projects/\$projectid/timeSeries?filter=metric.type%3D%22loadbalancing.googleapis.com%2Fl3%2Fexternal%2Fegress_packets_count%22&interval.startTime=2025-09-03T14:23:14.656Z&interval.endTime=2025-09-04T14:23:14.656Z&aggregation.alignmentPeriod=60s&aggregation.perSeriesAligner=ALIGN_MAX&aggregation.crossSeriesReducer=REDUCE_MAX\"
-H \"Authorization: Bearer \$ACCESS_TOKEN\" -H \"Content-Type:
application/json\" \| jq \'\[.timeSeries\[\].points\[\].value.int64Value
\| tonumber\] \| max\') echo
\$projectid,external_l3_egress_packet_count,\$external_l3_egress_packet_count
external_l3_ingress_packet_count=\$(curl -s -X GET
\"https://monitoring.googleapis.com/v3/projects/\$projectid/timeSeries?filter=metric.type%3D%22loadbalancing.googleapis.com%2Fl3%2Fexternal%2Fingress_packets_count%22&interval.startTime=2025-09-03T14:23:14.656Z&interval.endTime=2025-09-04T14:23:14.656Z&aggregation.alignmentPeriod=60s&aggregation.perSeriesAligner=ALIGN_MAX&aggregation.crossSeriesReducer=REDUCE_MAX\"
-H \"Authorization: Bearer \$ACCESS_TOKEN\" -H \"Content-Type:
application/json\" \| jq \'\[.timeSeries\[\].points\[\].value.int64Value
\| tonumber\] \| max\') echo
\$projectid,external_l3_ingress_packet_count,\$external_l3_ingress_packet_count

command to run

for projectid in \$(cat projects.txt); do ./lb_rps.sh \"\$projectid\"
done

output will come like below and some will error if lb not configured.

dh-gcp-ads-prod,global_lb_response_bytes,2658094933
dh-gcp-ads-prod,global_lb_request_bytes,4748001084
dh-gcp-ads-prod,global_lb_request_count,355953
dh-gcp-ads-prod,internal_lb_response_bytes,654984658
dh-gcp-ads-prod,internal_lb_request_bytes,1653661458
dh-gcp-ads-prod,internal_lb_request_count,502297
dh-gcp-ads-prod,internal_l3_egress_bytes,3215354
dh-gcp-ads-prod,internal_l3_ingress_bytes,2001020
dh-gcp-ads-prod,internal_l3_egress_packet_count,3903

exported to excel and with pivot got below result

  ---------------------------------- -------------
  external_l3_egress_packet_count    2103
  external_l3_ingress_packet_count   1233
  global_lb_request_bytes            19090868423
  global_lb_request_count            4062048
  global_lb_response_bytes           13794407107
  internal_l3_egress_bytes           18262208785
  internal_l3_egress_packet_count    13319522
  internal_l3_ingress_bytes          167911915
  internal_l3_ingress_packet_count   740098
  internal_lb_request_bytes          6142356904
  internal_lb_request_count          542837
  internal_lb_response_bytes         5712931205
  ---------------------------------- -------------
