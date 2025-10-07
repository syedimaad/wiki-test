\

1.  To know the current user : **whoami**

    **\**

2.  To switch from root user to any user : **su - \<username\>**

    **\**

3.  To switch between two non-root users:

    You need to edit /etc/sudoers file. For safe edit, use **visudo**
    command.

    Enter : **\<username\> ALL=(ALL) NOPASSWD:ALL** to grant them
    access.

    Following which you write on terminal : **sudo -iu \<username\>**

    \

4.  To delete any user : **userdel \<username\>** followed by **rm -r
    /*****home/*****username**

    **\**

5.  To list all users : **getent passwd**

\

\

[-Seren Jhanwar]{style="color: rgb(0,51,102);"}
