Access Flow

For **DH Content** Role

Provide **Order Page Access** to **DH Content** Role only for **non
InHouse** Orders.(event though they don't have `ox-orders` tag access).

For Remaining Roles & Users (Must have `ox-orders` **view tag access**)

1.Provide all Orders Access If Logged user is **ADMIN.**

2.Provide all Orders Access if user has `campaign-management` tag
**create Access**.

3.Provide all Orders Access if user has `live-unlimited-report` tag
**VIEW Access**.

IF User Doesn't have above 3 Access.

4.Show only self serve(`is_selfserve`) Orders to user having
`self-serve-admin` **create access**.

5.Show only those orders having anyone of
(`created_by,ops_assigned_to_id,ops_contact_id,sales_contact_id,agency_user_id,csm_user_id,contributor_ids`)
**as user_id** OR having anyone of
(`created_by,agency_user_id,csm_user_id`) **as user**
`ReporteesUserIds`.

6.Show only Orders having same `publisher_id` as User `publisher_id`
**IF User is** `isPublisherDH`.
