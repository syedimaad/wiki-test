Basis our UU analysis exercise, we discovered that a lot of users drop
off before we get to show them a valid ad impression. Some numbers for
reference below:

(Exercise conducted on Mar 16th)

  --- -------------------------------------------- ------------
      **Content UU**                               \~24mn
  1   **Ad-request UU**                            20,186,570
  2   **Ad-impression UU (any impression)**        15,793,357
  3   **Ad-impression UU (any non-empty)**         12,895,870
  4   **Ad-impression UU (empty only)**            2,579,762
  5   **Ad-impression UU (new user empty only)**   353,811
  --- -------------------------------------------- ------------

As the ads-tech team, we should be tracking the number in row 4 - these
are the users we **monetised** succesfully. (assuming that at least one
of the impressions these users saw was a direct or a network ad)

The opportunity for us lies in the following buckets:

1.  **Drop off from row 1 to row 2:** Users for whom we didn't even
    receive an ad request.

2.  **Drop off from row 2 to row 3:** Users for whom we received ad
    requests but couldn't fire any impression.

3.  **Row 5:** Users for whom we only showed empty impressions.

Upon digging deeper, we found that a huge chunk (**\>90%**) of such
users are very low activity users and we're now devising solutions to be
able to show ads to such users too - running evergreen campaigns in
various ad slots is one such solution.

For any of those solutions, we need to be able to identify such **thin
users**, so as to apply the said solutions only to them rather than all
users. Following is a proposal for the same.

**Ad-activity buckets**

1.  **Monetised users:** Users who gave \>0 impressions for **any
    non-evergreen** direct/network ad.

2.  **Inhouse-only users:** Users who gave \>0 impressions **only** for
    inhouse ads.

3.  **Empty-only users:** Users who gave \>0 impressions **only** for
    the non-new user empty banner.

4.  **New users:** Users who gave \>0 impressions **only** for the
    new-user-empty banner.

5.  **No-impression users:** Users who gave 0 impressions but requests.

*Action items:*

1.  We run a one-time job to place every one of our monthly active users
    in one of these categories.

2.  We write a daily cron that updates the categorisation of last day's
    users. Note that a user's category gets updated only upwards, never
    downwards.

**Content-activity buckets**

The content team also has buckets of users based on content event
numbers from the last 30 days. We should leverage that and store
content-categories of all users.

1.  **Gold users:** Users with at least one content event per day for
    \>15 days in the last 30 days. (Currently labeled as ***platinum***
    users).

2.  **Silver users:** Users with at least one content event per day for
    8-15 days in the last 30 days. (Currently labeled as
    ***non-platinum*** users).

3.  **Bronze users:** Users with at least one content event per day for
    1-7 days in the last 30 days. (Currently labeled as
    ***non-platinum*** users).

*Note:* **86%** of the \~2.5mn users who only saw empty impressions on
the day of our UU stress test belonged to buckets 2 and 3 above
(non-platinum).

*Action items:*

1.  We run a one-time job to place every one of our monthly active users
    in one of these categories.

2.  We write a daily cron that updates the categorisation of last day's
    users.

3.  Users for whom we receive no category from the content side should
    directly be labelled as **bronze.**

**Definition of a thin user:**

1.  Any user who is not in buckets (monetised, inhouse-only or new-user)
    according to ads-activity **and** not a platinum user according to
    content-activity should get treated as a thin user.

2.  Any user who is not in any ad bucket, is not a new user, and is not
    a platinum user according to content-activity should get treated as
    a thin user.

**Action items:**

1.  Classify your ads MAU into thin or non-thin users based on the
    solution here.

    1.  Run a check on the next day to find out how many thin users
        actually gave any impressions or not.

    2.  Of the users who didn't give any impressions, how many got
        classified as thin.

2.  Identify regular users from your MAU using:

    1.  **Gold users:** Users with at least one non-empty impression
        event for \>15 days in the last 30 days.

    2.  **Silver users:** Users with at least one non-empty impression
        event for 8-15 days in the last 30 days.

    3.  **Bronze users:** Users with at least one non-empty impression
        event for 1-7 days in the last 30 days.

    4.  Not-thin user = Gold-ads AND Gold-content OR new-user-empty

    5.  Check the coverage of the two points above.

3.  Fetch Gautham categories for our MAU and identify regular users as:

    1.  Not-thin user = Top category AND Gold-content OR new-user-empty

    2.  Check the coverage of the two points above.

Reference docs:\
[Monetizable UU
reporting](https://docs.google.com/document/d/1Ai4yH-VqJHHquvfMatEOoeYoM-KLW1r9lRB3Hm5uGMg/edit#)

[Stress test
analysis](https://docs.google.com/spreadsheets/d/10KQ-idbeglRfHoD-oeC8dflX24ErjWpO_EPDgl9m2wM/edit#gid=0)
