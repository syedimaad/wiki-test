\

[It is used to create links. By default it creates hard link. To create
soft link(symlinks), we may use -s
option.]{style="color: rgb(0,51,102);"}

[ Command : **ln \<file_name\>
linkname**]{style="color: rgb(0,51,102);"}

[**\**
]{style="color: rgb(0,51,102);"}

[The following EXAMPLE shows the working of hardlink pictorially
:]{style="color: rgb(0,51,102);"}

[echo "This is a file" \> file1.txt]{style="color: rgb(0,0,0);"}

[ln file1.txt file2.txt]{style="color: rgb(0,0,0);"}

[\
]{style="color: rgb(0,51,102);"}

\

[The following EXAMPLE shows the working of softlink pictorially
:]{style="color: rgb(0,51,102);"}

[echo "This is a file" \> file1.txt]{style="color: rgb(0,0,0);"}

[ln -s file1.txt file2.txt]{style="color: rgb(0,0,0);"}

[\
]{style="color: rgb(0,51,102);"}

[]{style="color: rgb(0,51,102);"}

[\
]{style="color: rgb(0,51,102);"}

[[**SOFTLINK :**]{.underline}\
]{style="color: rgb(0,51,102);"}

[[**Symlinks**]{style="letter-spacing: 0.0px;"} has several potential
benefits over **hardlinks**. For one thing, symbolic links can link to
directories. Also, symbolic links can cross file system boundaries, so a
symbolic link to data on one drive or partition can exist on another
drive or partition.]{style="color: rgb(0,51,102);"}

[[The Symlink created to directory(if any), would not be a directory,
it'll be simply a file which can be deleted using rm instead of rmdir.
]{style="letter-spacing: 0.0px;"}[The Restricted Shell imposes following
restrictions
:]{style="letter-spacing: 0.0px;"}]{style="color: rgb(0,51,102);"}

[\
]{style="color: rgb(0,51,102);letter-spacing: 0.0px;"}

1.  > [It will not allow you to execute cd command. So you can't go
    > anywhere. You can simply stay in the current working
    > directory.]{style="color: rgb(0,51,102);"}

2.  > [It will not allow you to modify the values of \$PATH, \$SHELL,
    > \$BASH_ENV, or \$ENV environmental
    > variables.]{style="color: rgb(0,51,102);"}

3.  > [It will not allow you to execute a program that contains a
    > /(slash) character. For example, you can't run /usr/bin/uname or
    > ./uname command. You can however execute uname command. In other
    > words, you are allowed to run the commands in the current path
    > only.]{style="color: rgb(0,51,102);"}

4.  > [You can't redirect the output using '\>', '\>\|', '\<\>', '\>&',
    > '&\>', and '\>\>' redirection
    > operators.]{style="color: rgb(0,51,102);"}

5.  > [It will not allow you to get out of the restricted shell mode
    > within scripts.]{style="color: rgb(0,51,102);"}

6.  > [It will not allow you to turn off restricted shell mode with 'set
    > +r' or 'set +o restricted'.]{style="color: rgb(0,51,102);"}

::: {}
[\
]{style="color: rgb(0,51,102);"}
:::

::: {}
[\
]{style="color: rgb(0,51,102);"}
:::

::: {}
[\
]{style="color: rgb(0,51,102);"}
:::

::: {}
[[-Seren Jhanwar]{style="color: rgb(0,51,102);"}\
]{style="color: rgb(0,51,102);"}
:::
