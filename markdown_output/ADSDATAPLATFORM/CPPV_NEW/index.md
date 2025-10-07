- Billing_type **CPPV_NEW:12**

- **Inventory_to_deliver** will be total pageviews to deliver in
  **dhx_requirements** table.

- Will need to create new table for CPPV campaigns delivery data

  - Columns: Date_time, name, article_id, post_id, campaign_id,
    pageviews, partner_id, host_app_id

- Will query half hourly on external table which content team will
  provide and store that data in newly created CPPV table

  - Query to find display articles data

    `select properties_item_id, client_id, time_spent_sec, properties_epoch_time_millis, properties_referrer_flow, properties_user_app_ver from (select properties_item_id, client_id, ROUND(CAST(properties_timespent/1000 AS DECIMAL(38,10)),2) as time_spent_sec, properties_epoch_time_millis, properties_referrer_flow, properties_user_app_ver from orc_news_timespent_pvactivity where properties_et_year = 2022 and properties_et_month = 7 and properties_et_day = 14 and properties_pv_activity = 'story_detail' and properties_item_id in ("1", "2") and versionLT(properties_user_app_ver,'16.2.0') union all select properties_item_id, client_id, ROUND(CAST(properties_timespent/1000 AS DECIMAL(38,10)),2) as time_spent_sec, properties_epoch_time_millis, properties_referrer_flow, properties_user_app_ver from orc_news_story_page_view where properties_et_year = 2022 and properties_et_month = 7 and properties_et_day = 14 and properties_pv_activity = 'story_detail' and properties_item_id in ("1", "2") and versionGTE(properties_user_app_ver,'16.2.0')) as x`

- **dhx_content_campaign_articles**

  - ~+\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--+\-\-\-\-\-\-\-\-\-\-\-\-\--+\-\-\-\-\--+\-\-\-\--+\-\-\-\-\-\-\-\--+\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--+~

    ~\|\ Field \  \  \  \  \  \ \|\ Type\  \  \  \  \ \|\ Null\ \|\ Key\ \|\ Default\ \|\ Extra \  \  \  \  \ \|~

    ~+\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--+\-\-\-\-\-\-\-\-\-\-\-\-\--+\-\-\-\-\--+\-\-\-\--+\-\-\-\-\-\-\-\--+\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--+~

    ~\|\ id\  \  \  \  \  \  \  \ \|\ int(11) \  \  \ \|\ NO\  \ \|\ PRI\ \|\ NULL \  \ \|\ auto_increment\ \|~

    ~\|\ name\  \  \  \  \  \  \ \|\ varchar(255)\ \|\ NO\  \ \|\ UNI\ \|\ NULL \  \ \| \  \  \  \  \  \  \  \ \|~

    ~\|\ article_id\  \  \  \ \|\ varchar(255)\ \|\ NO\  \ \|\ UNI\ \|\ NULL \  \ \| \  \  \  \  \  \  \  \ \|~

    ~\|\ post_id \  \  \  \  \ \|\ varchar(255)\ \|\ YES \ \|\  \  \ \|\ NULL \  \ \| \  \  \  \  \  \  \  \ \|~

    ~\|\ type_id \  \  \  \  \ \|\ tinyint(4)\  \ \|\ NO\  \ \|\ MUL\ \|\ NULL \  \ \| \  \  \  \  \  \  \  \ \|~

    ~\|\ hub_id\  \  \  \  \  \ \|\ int(11) \  \  \ \|\ YES \ \|\ MUL\ \|\ NULL \  \ \| \  \  \  \  \  \  \  \ \|~

    ~\|\ requirement_id\  \ \|\ int(11) \  \  \ \|\ YES \ \|\  \  \ \|\ NULL \  \ \| \  \  \  \  \  \  \  \ \|~

    ~\|\ start_date\  \  \  \ \|\ date\  \  \  \  \ \|\ NO\  \ \|\  \  \ \|\ NULL \  \ \| \  \  \  \  \  \  \  \ \|~

    ~\|\ end_date\  \  \  \  \ \|\ date\  \  \  \  \ \|\ NO\  \ \|\  \  \ \|\ NULL \  \ \| \  \  \  \  \  \  \  \ \|~

    ~\|\ updated_at\  \  \  \ \|\ datetime\  \  \ \|\ NO\  \ \|\  \  \ \|\ NULL \  \ \| \  \  \  \  \  \  \  \ \|~

    ~\|\ created_at\  \  \  \ \|\ datetime\  \  \ \|\ NO\  \ \|\  \  \ \|\ NULL \  \ \| \  \  \  \  \  \  \  \ \|~

    ~\|\ is_video_present\ \|\ tinyint(2)\  \ \|\ YES \ \|\  \  \ \|\ 0\  \  \  \ \| \  \  \  \  \  \  \  \ \|~

    ~+\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--+\-\-\-\-\-\-\-\-\-\-\-\-\--+\-\-\-\-\--+\-\-\-\--+\-\-\-\-\-\-\-\--+\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--+~

- One article can have multiple banners

- One article can not be used in multiple campaigns unless it is grouped
  campaigns

lets first start with 50% pacing via ads and 50% via organic delivery.

then compute delivery via ads and organic, based on that pace for
delivery via ads for that perticular campaign.
