1.  **username update**

    1.  check for username moderation

    2.  if yes `moderated_user_name` : "moderated_user_name" ,
        `username_moderation_label` : "nsfw", `username_review` : false

    3.  will set default username

    4.  send mail that has list of moderated usernames , which contains
        a link that redirect to CMS portal\

2.  **CMS username moderation flow**

    1.  CMS portal has list of moderated users with `username_review` :
        false and `username_moderation_label` : "nsfw"

    2.  It has two actions : Restore and Ok

    3.  Restore : it will trigger api : /username-moderation in which
        will pick `moderated_user_name` and restore in that user's
        handle will set `moderated_user_name` : " "
        ,`username_moderation_label` : "sfw" , `username_review` : true

    4.  OK : it will trigger api : /username-moderation only will set
        `username_review` : true
