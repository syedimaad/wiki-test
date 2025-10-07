\

1.  [**SUID :**]{.underline}

    SUID is a special permission assigned to a file. These permissions
    allow the file being executed to be executed with the privileges of
    the owner. For example, if a file was owned by the root user and has
    the setuid bit set, no matter who executed the file it would always
    run with root user privileges.

    Command : **chmod u+s \<filename\> OR chmod 4777 \<filename\>**

    To give execute permissions as well : **chmod u+x \<filename\>**

    To check : **ls -l \<filename\>** : 's' bit will appear in the
    permissions section indicating the suid bit is set

    [**\**]{.underline}

2.  [**SGID**]{.underline} **:**\

    When the Set Group ID bit is set, the executable is run with the
    authority of the group. For example, if a file was owned by the
    users' group, no matter who executed that file it would always run
    with the authority of the user's group.

    Command : **chmod g+s \<filename\> OR chmod 2777 \<filename\>**

    To give execute permissions as well : **chmod g+x \<filename\>**

    To check : **ls -l \<filename\>** : 's' bit will appear in the
    permissions section indicating the sgid bit is set

    **This can be set on directories as well. In this case, all files
    created within said directory inherit the group ownership of that
    directory**

    **\**

3.  [**STICKY BIT :**]{.underline}

    When the sticky bit is set on a directory, only the root user, the
    owner of the directory, and the owner of a file can remove files
    within said directory.

    Command : **chmod a+t \<directory_name\> OR chmod 1777
    \<directory_name\>**

    Finding files with SUID **: find / -perm +4000**

    Finding files with SGID **: find / -perm +2000**

    Finding files with SUID and SGID : **find / -type f \\\\( -perm
    -4000 -o -perm -2000 \\\\) -exec ls -l {} \\\\;**

::: {}
**\**
:::

::: {}
**\**
:::

::: {}
**\**
:::

::: {}
**\**
[-Seren Jhanwar]{style="color: rgb(0,51,102);"}
:::

::: {}
**\**
:::
