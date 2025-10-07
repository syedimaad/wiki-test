As part of security compliance we need to log every user activity and
hence perform below.

Add below line to file\
\
vi */etc/bash.bashrc* -- Ubuntu

or

*vi /etc/bashrc* -- Cenos/redhat

export PROMPT_COMMAND=\'RETRN_VAL=\$?;logger -t SSHCommandsDHUsers -p
local6.debug \"User \$(whoami) \[\$\$\]: \$(history 1 \| sed \"s/\^\[
\]\*\[0--9\]\\+\[ \]\*//\" )\"\'

Create new file and add below entry

*vi /etc/rsyslog.d/bash.conf*

`local6.* /var/log/commands.log`

then

vi */etc/rsyslog.d/50-default.conf*

change

`*.*;auth,authpriv.none -/var/log/syslog`

to

`*.*;auth,authpriv.none,local6.none -/var/log/syslog`

`systemctl restart rsyslog`

logout and login, all commands are visible\
\
cat */var/log/commands.log*

2024-10-21T17:23:19.517898+05:30 et-gcp-networking-hub-ldap-master-n1
LinuxCommandsDHDEVOPS: User root \[2221684\]: 2006 systemctl restart
rsyslog 2024-10-21T17:23:19.517898+05:30
et-gcp-networking-hub-ldap-master-n1 LinuxCommandsDHDEVOPS: User root
\[2221684\]: 2006 systemctl restart rsyslog
2024-10-21T17:23:19.978658+05:30 et-gcp-networking-hub-ldap-master-n1
LinuxCommandsDHDEVOPS: User root \[2221684\]: 2006 systemctl restart
rsyslog 2024-10-21T17:23:19.978658+05:30
et-gcp-networking-hub-ldap-master-n1 LinuxCommandsDHDEVOPS: User root
\[2221684\]: 2006 systemctl restart rsyslog
2024-10-21T17:23:19.978658+05:30 et-gcp-networking-hub-ldap-master-n1
LinuxCommandsDHDEVOPS: User root \[2221684\]: 2006 systemctl restart
rsyslog 2024-10-21T17:23:20.141650+05:30
et-gcp-networking-hub-ldap-master-n1 LinuxCommandsDHDEVOPS: User root
\[2221684\]: 2006 systemctl restart rsyslog
2024-10-21T17:23:20.141650+05:30 et-gcp-networking-hub-ldap-master-n1
LinuxCommandsDHDEVOPS: User root \[2221684\]: 2006 systemctl restart
rsyslog 2024-10-21T17:23:20.141650+05:30
et-gcp-networking-hub-ldap-master-n1 LinuxCommandsDHDEVOPS: User root
\[2221684\]: 2006 systemctl restart rsyslog
2024-10-21T17:23:20.290222+05:30 et-gcp-networking-hub-ldap-master-n1
LinuxCommandsDHDEVOPS: User root \[2221684\]: 2006 systemctl restart
rsyslog 2024-10-21T17:23:20.290222+05:30
et-gcp-networking-hub-ldap-master-n1 LinuxCommandsDHDEVOPS: User root
\[2221684\]: 2006 systemctl restart rsyslog
2024-10-21T17:23:20.290222+05:30 et-gcp-networking-hub-ldap-master-n1
LinuxCommandsDHDEVOPS: User root \[2221684\]: 2006 systemctl restart
rsyslog 2024-10-21T17:27:02.097602+05:30
et-gcp-networking-hub-ldap-master-n1 LinuxCommandsDHDEVOPS: User root
\[2221684\]: 2006 systemctl restart rsyslog

Add logrotate.

vi /etc/logrotate.d/rsyslog and then add `/var/log/commands.log` file to
list as below

/var/log/syslog /var/log/mail.log /var/log/kern.log /var/log/auth.log
/var/log/user.log /var/log/cron.log /var/log/commands.log { rotate 4
weekly missingok notifempty compress delaycompress sharedscripts
postrotate /usr/lib/rsyslog/rsyslog-rotate endscript }

systemctl restart logrotate

All in single command for ubuntu.

if \[ -f /etc/centos-release \]; then echo \"export
PROMPT_COMMAND=\'RETRN_VAL=\\\$?;logger -t SSHCommandsDHUsers -p
local6.debug \\\"User \\\$(whoami) \[\\\$\\\$\]: \\\$(history 1 \| sed
\\\"s/\^\[ \]\*\[0-9\]\\+\[ \]\*//\\\")\\\"\'\" \| sudo tee -a
/etc/bashrc; elif \[ -f /etc/lsb-release \] && grep -q \"Ubuntu\"
/etc/lsb-release; then echo \"export
PROMPT_COMMAND=\'RETRN_VAL=\\\$?;logger -t SSHCommandsDHUsers -p
local6.debug \\\"User \\\$(whoami) \[\\\$\\\$\]: \\\$(history 1 \| sed
\\\"s/\^\[ \]\*\[0-9\]\\+\[ \]\*//\\\")\\\"\'\" \| sudo tee -a
/etc/bash.bashrc; else echo \"Unsupported distribution.\"; fi echo
\"local6.\* /var/log/commands.log\" \>\>/etc/rsyslog.d/bash.conf
systemctl restart rsyslog sudo sed -i \'s/\*.\*;auth,authpriv.none
-\\/var\\/log\\/syslog/\*.\*;auth,authpriv.none,local6.none
-\\/var\\/log\\/syslog/\' /etc/rsyslog.d/50-default.conf systemctl
restart rsyslog echo \"/var/log/commands.log\" \| cat -
/etc/logrotate.d/rsyslog \| sudo tee /etc/logrotate.d/rsyslog systemctl
restart logrotate

Reference Doc
[https://medium.com/@damscarlos/logging-all-commands-executed-by-any-user-in-linux-to-wazuh-c17d8fb35aec](https://medium.com/@damscarlos/logging-all-commands-executed-by-any-user-in-linux-to-wazuh-c17d8fb35aec){card-appearance="inline"}

Varaprasad N

Oct 10 2024
