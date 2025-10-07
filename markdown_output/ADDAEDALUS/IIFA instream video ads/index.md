### Table Structure (taken from adload)

> +\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--+\-\-\-\-\-\-\-\-\-\-\-\-\--+\-\-\-\-\--+\-\-\-\--+\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--+\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--\
> \| Field \| Type \| Null \| Key \| Default \| Extra \|\
> +\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--+\-\-\-\-\-\-\-\-\-\-\-\-\--+\-\-\-\-\--+\-\-\-\--+\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--+\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--\
> \| id \| int(11) \| NO \| PRI \| NULL \| auto_increment \|\
> \| name \| varchar(255) \| NO \| \| NULL \| \|\
> \| host_app_id \| varchar(255) \| NO \| \| DH_APP \| \|\
> \| start_date \| datetime \| NO \| \| NULL \| \|\
> \| end_date \| datetime \| NO \| \| NULL \| \|\
> \| data \| text \| NO \| \| NULL \| \|\
> \| videoId \| varchar(255) \| NO \| \| NULL \| \|\
> \| created_by \| int(11) \| NO \| \| NULL \| \|\
> \| approved_by \| int(11) \| YES \| \| NULL \| \|\
> \| is_active \| tinyint(4) \| NO \| \| 0 \| \|\
> \| created_at \| datetime \| NO \| \| CURRENT_TIMESTAMP \| \|\
> \| updated_at \| datetime \| NO \| \| CURRENT_TIMESTAMP \| on update
> CURRENT_TIMESTAMP \|\
> +\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--+\-\-\-\-\-\-\-\-\-\-\-\-\--+\-\-\-\-\--+\-\-\-\--+\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--+\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--

// Data field schema \"data\": \[ { \"id\": \"mid1_1\", \"campaignId\":
\"\", \"bannerId\": \"\", \"timeOffset\": \"\" }, { \"id\": \"mid1_1\",
\"campaignId\": \"\", \"bannerId\": \"\", \"timeOffset\": \"\" }, {
\"id\": \"mid1_1\", \"campaignId\": \"\", \"bannerId\": \"\",
\"timeOffset\": \"\" }, \]

### Notes

1.  Multi-select banner at any segments

2.  Same videoId configuration should not be exist during the period.
