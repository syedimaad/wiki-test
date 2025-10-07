Method To Refer:

`isVisibleToCurrentUser` method in `Requirements` class.

Access Flow

`isOrderTypeInHouse`

`isAdmin`

Provide Campaign Access To **Admin**.

1.Provide Campaign Access To User **IF** **User** **with** **Same role
as Campaign CreatedUser** and has `inhouse-campaign-creation` tag
access.

\[ `isOrderTypeInHouse` , `inhouse-campaign-creation` , \'**Same role as
Campaign CreatedUser**\'\]

2.Provide Campaign Access To User **IF** **User** **with** **Same role
as Campaign CreatedUser** and has `inhouse-josh-campaign-creation` tag
access and Its should be **a Josh Campaign** .

\[`isOrderTypeInHouse` , `inhouse-josh-campaign-creation` , '**A Josh
Campaign'** , \'**Same role as Campaign CreatedUser**\'\]

3.Provide Campaign Access To User where `createdByUser` and User should
not have `isJoshContentNewsOpUser` With either
`inhouse-campaign-creation` OR `inhouse-josh-campaign-creation` AND a
Josh **Campaign** Access.

AnyOne

\[ `isOrderTypeInHouse` , `inhouse-campaign-creation` , "**User
AND**`createdByUser` **Not** **a** `isJoshContentNewsOpUser"` \]

\[ `isOrderTypeInHouse` , `inhouse-josh-campaign-creation` , '**A Josh
Campaign'** , "**User AND**`createdByUser` **Not** **a**
`isJoshContentNewsOpUser"` \]

1.Provide Campaign Access To User **IF Order Does NOT have a**
`hasMutualCampaign`.

2.Provide Campaign Access To User I**F User is a** `isPublisherDH`.

3.Provide Campaign Access To User **IF User** **with** **Same**
`PublisherId` **as** **Campaign** AND a **Campaign** is
`isMutualCampaign` .
