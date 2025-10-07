1.  PhpLdap Admin(PLA)
2.  Ldap Account Manager

\

[ ]{style="text-decoration: none;"}[**INSTALLING AND CONFIGURING
PHPLDAPADMIN(LAM) :**]{.underline}

[P]{style="letter-spacing: 0.0px;"}[hpLDAPAdmin (PLA) is a web
application for administering LDAP servers. It provides an easy way to
manage LDAP servers over a web browser. It is written in PHP language
and is licensed under the GNU
GPL. ]{style="letter-spacing: 0.0px;"}Since it is a web application,
this LDAP browser works on many platforms such as Ubuntu, Debian, Redhat
derivatives, Fedora, openSUSE, FreeBSD, OpenBSD, and Solaris.

PhpLDAPAdmin is the perfect tool for LDAP professionals and entry-level
administrators.

[**\**]{.underline}

1.  yum -y install epel-release

2.  yum install -y phpldapadmin

3.  vi /*etc/*httpd/conf.d/phpldapadmin.conf

    Replace "Require local" with "Require all granted" in the conf file

4.  systemctl restart httpd.service

5.  systemctl stop firewalld.service

6.  vi /*etc*/phpldapadmin/config.php

    \$servers-\>setValue('server','name','\<YOUR OPENLDAP SERVER
    NAME\>');

    \$servers-\>setValue('server','base',array('YOUR DC NAME')');

    \$servers-\>setValue('login','attr','dn');

    Comment this : //\$servers-\>setValue('login','attr','uid');

7.  Access phpldapadmin using : <http://your-ip-address/phpldapadmin>.

REFERENCE :
<https://www.itzgeek.com/how-tos/linux/centos-how-tos/install-configure-phpldapadmin-centos-7-ubuntu-16-04.html>

\

[**INSTALLING AND CONFIGURING LDAP ACCOUNT MANAGER (LAM)
:**]{.underline}

LAM has the following requirements to run:

- Apache/Nginx webserver (SSL recommended) with PHP module (PHP (\>=
  5.6.0) with ldap, gettext, xml, openssl and optional OpenSSL)

- Some LAM plugins may require additional PHP extensions (you will get a
  note on the login page if something is missing)

- Any standard LDAP server (e.g. OpenLDAP, Active Directory, Samba 4,
  OpenDJ, 389 Directory Server, Apache DS, \...)

- A recent web browser that supports CSS2 and JavaScript, at minimum

  \

1.  Install the tar files from LAM Homepage of whichever version you
    want to install using wget command

2.  Cd /*var/www/html/*

3.  Please extract the archive with the following command:\
    tar xjf ldap-account-manager-\<version\>.tar.bz2

4.  Then set the appropriate file permissions inside the LAM directory:\

    sess: write permission for apache/nginx user

    tmp: write permission for apache/nginx user

    tmp/internal: write permission for apache/nginx user

    config (with subdirectories): write permission for apache/nginx user

    lib/lamdaemon.pl set executable

5.  Instead of manually copying files you can also use the included
    configure script to install LAM. Just run these commands in the
    extracted directory:

    ./configure

    make install

    Options for \"./configure\":

    \--with-httpd-user=USER USER is the name of your Apache/Nginx user
    account (default httpd)

    \--with-httpd-group=GROUP GROUP is the name of your Apache/Nginx
    group (default httpd)

    \--with-web-root=DIRECTORY DIRECTORY is the name where LAM should be
    installed (default /usr/local/lam)

6.  Copy config/config.cfg.sample to config/config.cfg

7.  You may open LAM on your browser now
    using <http://your_ip_address/lam>

8.  You may further integrate it with OpenLDAP Server by updating the
    general settings and server settings using the gui.

REFERENCE :
[http](https://www.ldap-account-manager.org/static/doc/manual/ch02.html)[s](https://www.ldap-account-manager.org/static/doc/manual/ch02.html)[://www.ldap-account-manager.org/static/doc/manual/ch02.html](https://www.ldap-account-manager.org/static/doc/manual/ch02.html)

NOTE

The path used in the above installation is random. Ensure to use the
correct/specified/desired location while you install it on your system

\

\

-Seren Jhanwar

\

\

\

\
