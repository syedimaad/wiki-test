group_id column relations to other tables:

  ---------------------- ----------------- --------------
  **Table**              **Model**         **Relation**
  `dhx_access_control`   `AccessControl`   `hasMany`
  `dhx_roles`            `Roles`           `hasOne`
  ---------------------- ----------------- --------------

Changes Need to be handled:

User.php

`getGroupName`

`getAllUserFromGroupAsAdmin`

`getAllUserFromGroup`

`getUserFromGroupIdsAndSearchTextAsQuery`

`accessControl`

`group`

`getGroupAccessControlObjects`

AccessControlLayer.php

`getInstanceForUser`

Altering Relation with Queries (INT datatype column to json):

passing array of values to remove dependency on hasMany relation keyword

**AccessControl Class Relation**

\$groupIds = explode(\',\', \$this-\>getGroupIds()); return
\\App\\Models\\AccessControl::whereIn(\'role_id\' , \$groupIds)-\>get();

**Roles Class Relation**

\$groupIds = explode(\',\', \$this-\>getGroupIds()); return
\\App\\Models\\Roles::whereIn(\'id\' , \$groupIds)-\>get();

Note: This is not a relation , more as a wherein clause (can not be used
with "**with**").

**Alternate Joins**

since group_ids column has comma separated values ,can't directly
usefully as join columns. find_in_set can be used to search in a row.

-\>join(\$accessctrlTable, \$accessctrlTable . \'.role_id\',\'=\',
\$userModelTable . \'.group_id\') To -\>join(\$accessctrlTable
,DB::raw(\"find_in_set(\".\$accessctrlTable.\".role_id,
\".\$userModelTable.\".group_ids)\") , \"\>\" , DB::raw(\"\'0\'\"))

Note: find_in_set will only work for the single entry search in comma
separated values. for multiple search find_in_set needs to be looped
(bit costly).

**Where clauses**

where(\$this-\>table . \'.group_id\',\'=\',Roles::SELF_SERVE_GROUP); To
whereRaw(\'FIND_IN_SET(\"\'.Roles::SELF_SERVE_GROUP.\'\",
\'.\$this-\>getTable().\'.group_ids)\');
