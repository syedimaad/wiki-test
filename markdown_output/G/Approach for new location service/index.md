Below are the steps which seems to be a good way for re writing the
location service:

1.  Collect one time data from different source.

2.  Validate data with different sources

3.  Prepare data in a well defined structure

    1.  define smallest unit of data

    2.  map with lat-long (per 4 km sq.)

        1.  [approach 1 = for all 800,000 sq box in India's
            map]{style="color: rgb(255,86,48);"}

        2.  [approach 2 = only for lat - long coming in
            ad-request]{style="color: rgb(54,179,126);"}

    3.  map cell-ids

        1.  [approach 1 = for all 50 mn call id in current
            DB.]{style="color: rgb(255,86,48);"}

        2.  [approach 2 = only for in coming cell -ids
            ad-request.]{style="color: rgb(54,179,126);"}

    4.  for IP mapping still use max-mind DB

**suggested relational DB schema**
