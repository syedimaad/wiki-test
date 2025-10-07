Wallet SN

1.  KYC\
    Eligibility condition: user diamonds \> min diamonds needed && (bank
    details added \|\| kyc not done)\
    Eligible -\> wallet, scheduler\
    Success/Failure -\> wallet, api\
    Social notification event\
    {\
    \"app_id\":\"JOSH\",\
    \"target_user\":{\
    \"user_id\":\"\",\
    \"client_id\":\"\"\
    },\
    \"activity_type\":\"KYC\",\
    \"activity_sub_type\":\"KYC_Eligible/KYC_Verified/KYC_Failed\",\
    \"notification_destination\":\"TRAY_AND_INBOX\",\
    \"event_time\":\"\",\
    \"meta\":{\
    \"icon_url\":\"\",\
    \"deeplink_url\":\"\"\
    }\
    }

Wallet kinesis event\
{\
\"user_id\":\"\",\
\"activity_type\":\"KYC\",\
\"activity_sub_type\":\"KYC_Eligible/KYC_Verified/KYC_Failed\"\
}

-\> **[drop off can\'t be handled at
backend]{style="color: rgb(191,38,0);"}**

1.  Payment method addition\
    Eligibility condition: user diamonds \> min diamonds needed && kyc
    done**[(seems incorrect)]{style="color: rgb(191,38,0);"}**\
    Eligible -\> wallet, scheduler\
    Success -\> wallet, api\
    Social notification\
    {\
    \"app_id\":\"JOSH\",\
    \"target_user\":{\
    \"user_id\":\"\",\
    \"client_id\":\"\"\
    },\
    \"activity_type\":\"Account\",\
    \"activity_sub_type\":\"Account_Eligible/Account_Verified\",\
    \"notification_destination\":\"TRAY_AND_INBOX\",\
    \"event_time\":\"\",\
    \"meta\":{\
    \"icon_url\":\"\",\
    \"deeplink_url\":\"\"\
    }\
    }\
    **[-\> failure is not mentioned in
    figma]{style="color: rgb(191,38,0);"}**

2.  KYC and payment\
    Eligibility condition: user diamonds \> min diamonds needed && kyc
    done && payment method addedSocial notification\
    Eligible -\> wallet, scheduler\
    {\
    \"app_id\":\"JOSH\",\
    \"target_user\":{\
    \"user_id\":\"\",\
    \"client_id\":\"\"\
    },\
    \"activity_type\":\"Account\",\
    \"activity_sub_type\":\"Account_Redeem\",\
    \"notification_destination\":\"TRAY_AND_INBOX\",\
    \"event_time\":\"\",\
    \"meta\":{\
    \"icon_url\":\"\",\
    \"deeplink_url\":\"\",\
    \"left_icon_url\":\"\"\
    }\
    }

3.  Redemption\
    Eligibility condition: user diamonds \> min diamonds needed every n
    days(We need to use sort key to check this)\
    Eligible -\> wallet, scheduler\
    Success -\> wallet, api\
    {\
    \"app_id\":\"JOSH\",\
    \"target_user\":{\
    \"user_id\":\"\",\
    \"client_id\":\"\"\
    },\
    \"activity_type\":\"Redemption\",\
    \"activity_sub_type\":\"Redemption_Success/Redemption_Failure/Redemption_Eligible\",\
    \"notification_destination\":\"TRAY_AND_INBOX\",\
    \"event_time\":\"\",\
    \"meta\":{\
    \"icon_url\":\"\",\
    \"deeplink_url\":\"\"\
    }\
    }

4.  Milestones\
    Trigger -\> wallet,api\
    {\
    \"app_id\":\"JOSH\",\
    \"target_user\":{\
    \"user_id\":\"\",\
    \"client_id\":\"\"\
    },\
    \"activity_type\":\"Reward\",\
    \"activity_sub_type\":\"Reward_Milestone_100/Reward_Milestone_500/Reward_Milestone_1000\",\
    \"notification_destination\":\"TRAY_AND_INBOX\",\
    \"event_time\":\"\",\
    \"meta\":{\
    \"icon_url\":\"\",\
    \"deeplink_url\":\"\"\
    }\
    }

5.  Creator payout info\
    When creator payout is enabled for any user -\> from onboard, API\
    {\
    \"app_id\":\"JOSH\",\
    \"target_user\":{\
    \"user_id\":\"\",\
    \"client_id\":\"\"\
    },\
    \"activity_type\":\"Info\",\
    \"activity_sub_type\":\"Info_payout\",\
    \"notification_destination\":\"TRAY_AND_INBOX\",\
    \"event_time\":\"\",\
    \"meta\":{\
    \"icon_url\":\"\",\
    \"deeplink_url\":\"\"\
    }\
    }

when performance payout gift is given to a content and is greater than n
diamonds on a given day\
**[Doubt: will we send for all contents as for a given user, multiple
contents can get creator payout gifts]{style="color: rgb(191,38,0);"}**\
Trigger -\> Wallet,api\
{\
\"app_id\":\"JOSH\",\
\"target_user\":{\
\"user_id\":\"\",\
\"client_id\":\"\"\
},\
\"activity_type\":\"Reward\",\
\"activity_sub_type\":\"Reward_Video\",\
\"notification_destination\":\"TRAY_AND_INBOX\",\
\"event_time\":\"\",\
\"meta\":{\
\"icon_url\":\"\",\
\"deeplink_url\":\"\"\
}\
}

EOD for users who have got fan gift today\
Trigger -\> wallet, scheduler\
{\
\"app_id\":\"JOSH\",\
\"target_user\":{\
\"user_id\":\"\",\
\"client_id\":\"\"\
},\
\"activity_type\":\"Reward\",\
\"activity_sub_type\":\"Reward_EOD\",\
\"notification_destination\":\"TRAY_AND_INBOX\",\
\"event_time\":\"\",\
\"meta\":{\
\"icon_url\":\"\",\
\"deeplink_url\":\"\"\
}\
}
