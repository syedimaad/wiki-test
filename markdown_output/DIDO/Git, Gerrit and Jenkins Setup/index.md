\

### **Gerrit:**

Gerrit is a git-based open source code review system that has a
web-based interface that lets you push changes from a git client, review
changes and auto-merge with the master code.

It also has the option to add feedback or review on specific lines, or
on the entire patch. Reviewers can rate the changes with one from below:

  ---- --------------------------------------------------
  +2   Looks good to me, approved.
  +1   Looks good to me, but someone else must approve.
  0    No score.
  -1   I would prefer that you didn't submit this.
  -2   Block submit.
  ---- --------------------------------------------------

A +2 review implies the code can be submitted to the master by default.
This can be configured as required.

### **Jenkins:**

[When Jenkins and Gerrit are used together, the builds will have
success/failure mark to indicate if they have passed the tests. Jenkins
will run the test regression after performing a build. Once complete, it
will publish the test results just like one of the reviewers. In case
the build fails, it will reject the patch. You can set either a -1 or a
-2 depending on the quality of your CI in an event of test
failure.]{style="color: rgb(85,85,85);"}

##### **Workflow:**

**\**

###### **Gerrit Setup:**

**                     \**

[http://devops.dailyhunt.in/gerrit](http://devops.dailyhunt.in/gerrit){style="letter-spacing: 0.0px;"} 
                            Nginx                                       
           Gerrit:8080

                                                                       
                (192.168.7.56)                                       
 (192.168.7.18)

\

                                

                                                                       
      

<ssh://devops-gerrit.dailyhunt.in:29418>                        Git Repo

                                                                       
                      (192.168.7.18)

\

###### Gerrit InitSetup:

[1) Sign in into our gerrit web
portal([[http://]{style="color: rgb(85,85,85);"}[devops.dailyhunt.in/gerrit]{.wikiexternallink
style="color: rgb(85,85,85);"}](http://devops.dailyhunt.in/gerrit/)) using
the ldap credential.]{style="color: rgb(85,85,85);"}

\

[2) Add your ssh public key in gerrit
portal]{style="color: rgb(85,85,85);"}

[\
]{style="color: rgb(85,85,85);"}

3) [Once you added your public key, please inform to administrator about
 your new sign up and ask add into dh-sysadmin
group.]{style="color: rgb(85,85,85);"}

[]{style="color: rgb(85,85,85);"}

[4) [Download clone_git_repo.sh from our http
repo <http://devops.dailyhunt.in/repo/scripts/clone_git_repo.sh> and [run
it on your laptop with your user name and email
address. ]{style="color: rgb(85,85,85);"}]{style="color: rgb(85,85,85);"}]{style="color: rgb(85,85,85);"}

[[[ ./clone_git_repo.sh -u \<ldap_user_name\> -e \<verse_email_address\>
-p \<project_name\>(defaults, dh-sysadmin) -d
\<directory_path_to_clone\>]{style="color: rgb(85,85,85);"}]{style="color: rgb(85,85,85);"}]{style="color: rgb(85,85,85);"}

**[[Example:]{style="color: rgb(85,85,85);"}]{style="color: rgb(85,85,85);"}**[[ [./clone_git_repo.sh
-u selvam.mariappn -e
<selvam.mariappan@verse.in>]{style="color: rgb(85,85,85);"}]{style="color: rgb(85,85,85);"}]{style="color: rgb(85,85,85);"}

###### [[**Git Re[view Flow:]{style="color: inherit;"}**]{style="color: rgb(85,85,85);"}]{style="color: rgb(85,85,85);"}

- We will use Git Commands Easy(gce) script to create new branch and
  push our changes. Before that add this below alias in your bashrc
  file.

             *alias gce=\"\~/dh-sysadmin/gce\"*

- Once you ran the clone_git_repo.sh script, move to \~/dh-sysadmin or
  the repo path and create new branch using ***gce n*** command option.
- Then make the changes whatever you need to be done.
- Once done your changes, add the files to commit using ***gce
   a*****\<file1\> \<file2\> or gce a .**
- Now It is time to commit your changes. To do that, just run ***gce
  d  ***and add your comments about the changes. 
- If it is successful, You will get the URL to review your changes
  like [<http://devops.dailyhunt.in/gerrit/#/c/20/>]{.wikiexternallink} .
- Now send this links to team to review your changes.
- When you get the required review points, the submit button will be
  enabled automatically.
- Now good to go and merge your changes.
- When next time, you need to make another change, go to your repo path
  and create new branch***gce ***with ***n*** command and follow the
  above steps.

\

\~\> SELVAM

\

\

\

\

please use this link to re-download the new clone_git_repo.sh file and
before cloning add your SSH Key to the new Gerrit.\
<http://devops2.dailyhunt.in/repo/scripts/clone_git_repo.sh>

\

Current LIVE Urls

<http://devops2.dailyhunt.in/jenkins/> - Jenkins\
<http://devops2.dailyhunt.in/gerrit> - Gerrit\
\
**                                 Restart gerrit service:**

/mnt/vol1/gerrit/bin\
./gerrit.sh restart\
Stopping Gerrit Code Review:

\

root@dh6-admin-gerrit bin\]# ./gerrit.sh status\
Checking arguments to Gerrit Code Review:\
GERRIT_SITE = /mnt/vol1/gerrit\
GERRIT_CONFIG = /mnt/vol1/gerrit/etc/gerrit.config\
GERRIT_PID = /mnt/vol1/gerrit/logs/gerrit.pid\
GERRIT_TMP = /mnt/vol1/gerrit/tmp\
GERRIT_WAR = /mnt/vol1/gerrit/bin/gerrit.war\
GERRIT_FDS = 1024\
GERRIT_USER = gerrit\
GERRIT_STARTUP_TIMEOUT = 90\
JAVA = /mnt/vol1/jdk-15.0.2/bin/java\
JAVA_OPTIONS =
-Dflogger.backend_factory=com.google.common.flogger.backend.log4j.Log4jBackendFactory#getInstance
-Dflogger.logging_context=com.google.gerrit.server.logging.LoggingContext#getInstance\
RUN_EXEC = /usr/bin/perl -e \'\$x=\$ENV{JAVA};exec \$x \@ARGV;die \$!\'
\-- GerritCodeReview\
RUN_ARGS =
-Dflogger.backend_factory=com.google.common.flogger.backend.log4j.Log4jBackendFactory#getInstance
-Dflogger.logging_context=com.google.gerrit.server.logging.LoggingContext#getInstance
-jar /mnt/vol1/gerrit/bin/gerrit.war daemon -d /mnt/vol1/gerrit

Gerrit running pid=164485\
\[root@dh6-admin-gerrit bin\]# ./gerrit.sh restart\
Stopping Gerrit Code Review: OK\
Starting Gerrit Code Review: OK\
\[root@dh6-admin-gerrit bin\]#

\

\

\

\
