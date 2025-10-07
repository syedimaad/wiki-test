**[Log Rotation:]{.underline}**

It is one thing to create logs; it is quite another to cope with them. A
log file grows without bound unless action is taken and this can cause
problems.

Problems with growing log files Larger files are harder to
manipulate.File systems run out of space.The information you log may
constitute personal data.

A solution to this generic problem of log file growth is log rotation.

This involves the regular (nightly or weekly, typically) moving of an
existing log file to some other file name and starting fresh with an
empty log file. After a period the old log files get thrown away.

Once each night the logrotate program reads in its configuration files
telling it which logs to rotate and how to do it. One of these files
tells it to rotate Apache\'s log files.

The main configuration file sets up the defaults and then reads in a
directory of instructions for specific sets of log files from the
/etc/logrotate.d directory.

**Steps:**

1.  Login to the particular virtual machine , and login with user (
    example : root user, dh-ads , etc.)  and go to the logrotate.d 
    directory .

cd  /etc/logrotate.d

2\. Then create a file  like

vim logs-app 

 3. we can change the ownership for  editing and saving the file.

chown -R dh-ads:dh-tech-prod ./\*

(previously we login with the user dh-ads 

 cmd : 

 sudo -i -u dh-ads

 ls -al 

 \-- where we can get the user to login and user-group like that 

drwx\-\-\-\-\--. 13 dh-ads dh-tech-prod      4096 Sep  9 17:42 .

drwxr-xr-x.  4 root   dh-tech-prod        40 May 25 17:19 ..

Here,

dh-ads :- in where we can login with user

dh-tech-prod :- user-group 

4\. Then, Go into the file and paste the below line , You can change it
as per as your requirement.

vim logs-app

5\. The lines to write in that file  

/mnt/vol1/dh-ads/logs/app/\*.log /mnt/vol1/dh-ads/logs/data/\*.log
/mnt/vol1/dh-ads/logs/\*.log { daily rotate 31 dateext compress
copytruncate missingok notifempty maxage 30 }

6\. Save and Quit the file . Log rotation will be activated.

**[Definition : ]{.underline}**

- /mnt/vol1/dh-ads/logs/app/\*.log  

  - It is the path of log file , from where developer team want to
    remove the logs

- Daily

  -  Each file should be rotated Daily. The log rotation job runs
    nightly, though, so this can be changed to daily for a specific log
    file if desired.

- rotate 31

  - Delete old log files once they have been rotated 31 times.

- dateext

  - Archive old versions of log files adding a date extension like
    YYYYMMDD to the filename.

- compress

  - Storing a log file in a way that reduces the amount of storage space
    needed for the file without altering the meaning of its
    contents.Rotated log files should be compressed. 

Logfiles, which can be very large, typically compress very well.

- copytruncate

  - The copytruncate directive, on the other hand, instructs logrotate
    to first create a copy of the original log file and then delete the
    original file\'s contents in order to reduce its size (i.e.,
    truncate)

- missingok

  - This is the instruction not to return an error if a particular log
    file is not present.

- notifempty

  - This command instructs the system not to rotate the logs if the
    current main log file is empty. See the discussion below about
    whether this is a good idea or not.

- maxage 30

  - Remove rotated logs older than 30 days. The age is only checked if a
    logfile is to be rotated.
