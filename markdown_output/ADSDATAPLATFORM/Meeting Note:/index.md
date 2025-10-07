##  Date

##  Participants

List meeting participants using their @ mention names

- 
- 
- 
- 
- 

##  Goals

List goals for this meeting (e.g., Set design priorities for FY19)

- Come up with Ads Architecture to cater to the problem of no Ads for
  thin users

##  Discussion topics

+----------+----------+---------------+--------------------------------+
| **Time** | **Item** | **Presenter** | **Notes**                      |
+----------+----------+---------------+--------------------------------+
|          |          |               | - Add notes for each           |
|          |          |               |   discussion topic             |
+----------+----------+---------------+--------------------------------+
| \        | \        | \             | \                              |
+----------+----------+---------------+--------------------------------+

Every user starts as a thin user

T → 1st impressions → Evergreen Cache impression

→ Subsequent impressions → Wait for y ms for a response if not already
in the regular cache

→ Response received → Regular Ad

→ Timeout → Evergreen Cache Ad

R → Wait for x ms for a response if not already in regular cache

→ Response received → Regular Ad

→ Timeout → Evergreen Cache Ad

On Impression of non-evergreen cache → mark the user as a regular R

Set cookie: regular:1 Expiry time 72 hours

Phase 2: Readiness

We will always have an option to set a cookie with every response.

**Refined Approach**:

1.  The client checks cookie **is_regular_ad_eligible**

    1.  If not set, show evergreen Ad and set the
        **is_regular_ad_eligible** cookie

    2.  If set, show a regular Ad with a timeout of **y ms**. If the
        timeout is passed show Evergreen Ad

2.  On every impression be it Regular Ad **OR** Evergreen Ad set cookie
    **is_regular_ad_eligible** with a revised timeout of **T + x days**

**Note**: We can tune **x days** if more impressions are going to
Evergreen Ad

**Iteration-2 of Refined Approach**

This has the advantage over the above approach to include thin users in
DAU as well rather than in the next x days as per the above approach.
Inspiration from Ajay's solution. the difference is we are trying to
show the regular ad to thin users in subsequent requests within the day.

1.  The client checks cookie two cookies **is_regular_ad_eligible** and
    **is_evergreen_ad_shown**

    1.  If **is_regular_ad_eligible** is set, show regular Ad with a
        timeout of x ms else show evergreen Ad

    2.  if **is_evergreen_ad_shown** is set show regular Ad with a
        timeout of y ms else show evergreen Ad

2.  On impression of an evergreen Ad set cookie
    **is_evergreen_ad_shown** with TTL 1 day.

3.  On impression of a regular Ad set cookie **is_regular_ad_eligible**
    with TTL **z days**

##  Action items

Add action items to close the loop on open questions or discussion
topics:

2 complete [ Get approval from the stakeholders for the different
approaches discussed]{.placeholder-inline-tasks}

##  Decisions

Type /decision to record the decisions you make in this meeting:

e6589366-3d0b-48c7-957e-9aee8dd77095DECIDED08407bda-d989-4e41-b323-e2c785d1a5a0
