## Daily Feed Monitoring

Google Space : <https://chat.google.com/room/AAAAD8bl6HY?cls=7>

Code :
<https://gitlab.dailyhunt.in/josh-ai-labs/feed-monitoring/-/tree/dev>

Cronjob : 6AM everyday

Alert Documentation is available here : Feed Monitoring

Running the code

bash runner.sh

→ This will run two functions/files separately for AWS & GCP

\$THIS_PYTHON /data/prod/feed-monitoring/run_aws.py \$THIS_PYTHON
/data/prod/feed-monitoring/run_gcp.py

### GCP Flow

**[Utils]{style="color: rgb(7,71,166);"}**

***alerts_config.py*** -\> This file has metrics and dimensions along
with thresholds. Any changes to thresholds / messaging is done here.
Everything stored in dict `DICT_ALERTS_CONDITIONS`

***config.py*** → This file has all the basic config like path to
storage, credentials, date calculator and dictionaries for handling
different metrics. Important ones - `QUERY_DICT` , `SUMO_QUERY_DICT` ,
`FUNNEL_COMPS` , `COMBINED_DICT`

***gcp_queris.py*** → This file has list of all GCP & SuMo queries
stored.

***bigquery_helper.py*** → Helps with bq query, takes query as input and
pandas dataframe as output.

***sumo_helper.py*** → Helps with sumo query requests , takes query as
input and pandas dataframe as output.

***delta_helper.py*** → helps in calculating delta for each alert metric

***funnel_helper.py*** → helps with producing funnel data across metrics
as defined in config

***notifier.py*** → Used for sending alerts

**[Main Func (run_gcp.py)]{style="color: rgb(7,71,166);"}**

Inside the main function, a function dict will store all the
dictionaries defined in config and a 'loop' will execute each of these
dictionary values.

function_dict = { run_bq_query: (QUERY_DICT, {}), run_sumo_query:
(SUMO_QUERY_DICT, {}), calculate_n_save_delta: (COMBINED_DICT, {}),
calculate_funnel: ( FUNNEL_COMPS, { \"parent_prefix\":
PARENT_PREFIX_GCP, \"date\_\": TODAY_STR, \"funnel_comps\":
FUNNEL_COMPS, }, ), calculate_funnel_delta: ( \[\], { \"parent_prefix\":
PARENT_PREFIX_GCP, \"date\_\": TODAY_STR, \"metric_date\_\":
METRIC_DATE_STR, }, ), }

**Other func inside the main file**

`run_bq_query` → executes all the queries from the `QUERY_DICT`

`run_sumo_query` → executes all the queries from the `SUMO_QUERY_DICT`

`calculate_n_save_delta` → used for calculating delta for the metrics
from the above two dictionaries.

`calculate_n_send_alerts` → According to the ***alerts_config.py***,
this will check for thresholds and returns alert messages.

send_alert( f\"\*GCP Report is available for DATE:
{TODAY_STR}\*\\n\*Link:\* {\'http://10.10.48.35:8910/\'}\" )
alert_summary = \[\] for alert in DICT_ALERTS_CONDITIONS: alert_summary
+= calculate_n_send_alerts(alert) print(f\"{alert} Alert Done\")
alert_summary = \"\*HIGHLIGHTS\*\" + \"\\n\`\`\`\" +
\"\\n\".join(alert_summary) + \"\`\`\`\" send_alert(alert_summary)

The script here calls the the above func(`calculate_n_send_alerts`) in
loop and sends alert to google space.

### AWS Flow

AWS flow is exactly similar to the flow above. Difference is in
*aws_queries.py* file, with queries corresponding to Athena.

------------------------------------------------------------------------

## Realtime Feed Monitoring

Google Space : <https://chat.google.com/room/AAAAx50jqnw?cls=7>

Code :
<https://gitlab.dailyhunt.in/josh-ai-labs/feed-monitoring/-/tree/dev/realtime>

Cronjob : Every 15 mins

Running the code

bash realtime_runner.sh

→ This will run codes defined in main function.

\$THIS_PYTHON /data/prod/feed-monitoring/realtime/run_gcp.py

### Flow

**[Utils]{style="color: rgb(7,71,166);"}**

***config.py*** → This file has a dictionary for holding variables of
sumo queries - `SUMO_QUERY_DICT`

***gcp_queries.py*** → Has actual queries stored in different variables.

***compare_helper.py*** → compares each metric against thresholds
defined in the same file.

***notifier.py*** → helps in sending alerts

**[Main func (run_gcp.py)]{style="color: rgb(7,71,166);"}**

`run_sumo_query` → runs the sumo query

`compare_n_return_alerts` → compares current results with previous
results

with multiprocessing.Pool(processes=8) as pool:
pool.starmap(run_sumo_query, \[\[current_time, key\] for key in
SUMO_QUERY_DICT.keys()\]) all_alerts=\[\] for key in ALERTS_LIST:
all_alerts+=compare_n_return_alerts(current_time, key) if
len(all_alerts)\>0: alert_summary = \"\*HIGHLIGHTS\*\" + \"\\n\`\`\`\" +
\"\\n\".join(all_alerts) + \"\`\`\`\" send_alert(alert_summary)

The above code runs all the sumo queries, and then compares results and
send the alerts to google space.
