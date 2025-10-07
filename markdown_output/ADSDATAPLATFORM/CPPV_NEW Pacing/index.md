setup cron to update article delivery data fetch.

inform content team about delivery met.

## Pacing

- start with cppv_pacing_factor = 0

- required_pageviews_for_OI = required_pageviews \* cppv_pacing_factor

- cppv_pacing_factor = (today_required_pageviews -
  today_organic_pageviews) / today_required_pageviews

## Delayed delivery data handing

delayed delivery needs to be counted.

- delay = now - last_timestamp_of_data (in seconds)

- boosted_delivered_data = delivered_data +
  (today_delivered_data/time_till_now_in_seconds)\*delay

## Grouped Campaigns

- campaign_dict\[\'group_delivery_ratio\'\] =
  float(10.0/float(campaign_dict\[\'previous_oi_priority_factor\'\])) \*
  float(float(campaign_dict\[\'previous_oi_delivered_impressions\'\]) /
  float(campaign_dict\[\'hard_stop_seconds_since_mpe_finish\'\]))

- total_hard_stop_number += campaign_dict\[\'group_delivery_ratio\'\]

- campaign_perf = float(float(total_pageviews /
  total_impressions)/all_campaigns_perf)

- new_delivery_ratio = 0.25\*campaign_perf +
  0.75\*float(campaign_dict\[\'group_delivery_ratio\'\]/total_hard_stop_number))

- campaign_dict\[\'required_impressions\'\] =
  int(group_dict\[\'required_impressions\'\] \* new_delivery_ratio
