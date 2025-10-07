\

- [**USING RESTRICTED SHELL :\**
  ]{style="color: rgb(0,51,102);"}

  [Restricted Shell is. It is not a separate shell like Bash, Korn Shell
  etc. If you start any existing shell using "rbash", "--restricted",
  "-r" options, then it will become Restricted shell. For instance, the
  Bourne shell can be started as a restricted shell with the command bsh
  -r, and the Korn shell with the command ksh
  -r.]{style="color: rgb(0,51,102);"}

  [The Restricted Shell will limit the users from executing most
  commands and from changing the current working
  directory.]{style="color: rgb(0,51,102);"}\
  \
  [ **STEPS TO GRANT USER LIMITED
  ACCESS:**]{style="color: rgb(0,51,102);"}

  1.  [ln -s /bin/bash /bin/rbash]{style="color: rgb(0,51,102);"}
  2.  [useradd \<username\> -s
      /bin/rbash]{style="color: rgb(0,51,102);"}
  3.  [passwd \<username\>]{style="color: rgb(0,51,102);"}
  4.  [mkdir /home/\<username\>/bin]{style="color: rgb(0,51,102);"}
  5.  [ln -s /bin/\<command_name\>
      /home/\<username\>/bin/\<command_name\>]{style="color: rgb(0,51,102);"}
  6.  [chown root .
      /home/\<username\>/.bash_profile]{style="color: rgb(0,51,102);"}
  7.  [chmod 755
      /home/\<username\>/.bash_profile]{style="color: rgb(0,51,102);"}
  8.  [vi
      /home/\<username\>/.bash_profile]{style="color: rgb(0,51,102);"}
  9.  [Set PATH=\$HOME/bin]{style="color: rgb(0,51,102);"}
  10. [Now log in to the user by verifying
      commands.]{style="color: rgb(0,51,102);"}\
      [\
      ]{style="color: rgb(0,51,102);"}

- [**BY EDITING ETC/SUDOERS FILE:**]{style="color: rgb(0,51,102);"}\
  [**\**
  ]{style="color: rgb(0,51,102);"}[The sudoers file is a file Linux and
  Unix administrators use to allocate system rights to system users.
  This allows the administrator to control who does what. Remember,
  Linux is built with security in mind. When you want to run a command
  that requires root rights, Linux checks your username against the
  sudoers file.]{style="color: rgb(0,51,102);"}\
  [\
  **STEPS TO GRANT USER LIMITED ACCESS:**\
  ]{style="color: rgb(0,51,102);"}
  1.  [Edit /etc/sudoers file using visudo
      command.]{style="color: rgb(0,51,102);"}
  2.  [Group the commands that you want the user to have access to using
      :**Cmnd_Alias DIRECTORY_COMMANDS =
      /usr/bin/yum**]{style="color: rgb(0,51,102);"}
  3.  [Now to specify the user having the access to those specific
      commands :**\<username\> ALL=(ALL) NOPASSWD:
      DIRECTORY_COMMANDS**]{style="color: rgb(0,51,102);"}
  4.  [Save and exit the file.]{style="color: rgb(0,51,102);"}

[\
]{style="color: rgb(0,51,102);"}

[-Seren Jhanwar]{style="color: rgb(0,51,102);"}

[\
]{style="color: rgb(0,51,102);"}
