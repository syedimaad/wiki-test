**Step1: Daedalus**

- To add 3 fields on `dhx_daedalus_banners`: start_date, end_date,
  delivery_status

- start_date, end_date to be Optional fields under creative creation -
  with NULL as default

  - At time of (campaign activation) or (banner deactivation), check if
    there is any missing range within campaign start/end dates by
    comparing all active banner's start/end date, or a NULL value banner
    exists.

- delivery_status will be updated by Ad Engine. The default value can be
  0

- DB Update for existing values:

  - Banner start/end dates to be the same as campaign start/end dates

**Step2: Ad Engine**

- Additional filter for creatives - check for the current time to be
  between creative start_date, end_date

  - If a creative start/end date is NULL, then use respective values
    from campaign.

- Update delivery_status=1 if true, 2 if false

**Challenges**

1.  To discuss: Ad Engine doesn\'t have write access on DB. MPE already
    changes status for campaigns, so may update delivery status as well.
