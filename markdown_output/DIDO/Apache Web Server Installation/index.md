\

1.  [Install some pre-requisite packages
    :]{style="color: rgb(0,51,102);"}

    [**yum install wget gcc pcre-devel
    openssl-devel**]{style="color: rgb(0,51,102);"}

2.  [Download apache, apr and apr-util source tarball and install
    apache]{style="color: rgb(0,51,102);"}

    [**cd \~**]{style="color: rgb(0,51,102);"}

    [**mkdir sources**]{style="color: rgb(0,51,102);"}

    [**cd sources**]{style="color: rgb(0,51,102);"}

    [**wget
    [[http://ftp.piotrkosoft.net/pub/mirrors/ftp.apache.org//httpd/httpd-2.4.12.tar.bz2]{style="color: rgb(0,51,102);"}](http://ftp.piotrkosoft.net/pub/mirrors/ftp.apache.org//httpd/httpd-2.4.12.tar.bz2)**]{style="color: rgb(0,51,102);"}

    [**wget
    [[http://ftp.ps.pl/pub/apache//apr/apr-1.5.2.tar.bz2]{style="color: rgb(0,51,102);"}](http://ftp.ps.pl/pub/apache//apr/apr-1.5.2.tar.bz2)**]{style="color: rgb(0,51,102);"}

    [**wget
    [[http://ftp.ps.pl/pub/apache//apr/apr-util-1.5.4.tar.bz2]{style="color: rgb(0,51,102);"}](http://ftp.ps.pl/pub/apache//apr/apr-util-1.5.4.tar.bz2)**]{style="color: rgb(0,51,102);"}

    [**tar -xvf httpd-2.4.12.tar.bz2**]{style="color: rgb(0,51,102);"}

    [**tar -xvf apr-1.5.2.tar.bz2**]{style="color: rgb(0,51,102);"}

    [**tar -xvf apr-util-1.5.4.tar.bz2**]{style="color: rgb(0,51,102);"}

    [**cp -r apr-1.5.2
    httpd-2.4.12/srclib/apr**]{style="color: rgb(0,51,102);"}

    [**cp -r apr-util-1.5.4
    httpd-2.4.12/srclib/apr-util**]{style="color: rgb(0,51,102);"}

    [**cd httpd-2.4.12**]{style="color: rgb(0,51,102);"}

    [**./configure \--prefix=/etc/apache2 \--enable-ssl \--enable-so
    \--with-included-apr
    \--with-mpm=event**]{style="color: rgb(0,51,102);"}

    [**make**]{style="color: rgb(0,51,102);"}

    [**make install**]{style="color: rgb(0,51,102);"}

3.  [Some Basic Apache related Configuration before starting
    Apache:]{style="color: rgb(0,51,102);"}

    [**chown -R apache.root
    /etc/apache2**]{style="color: rgb(0,51,102);"}

    [Some changes that needs to be made in "httpd.conf" file
    :]{style="color: rgb(0,51,102);"}

    [**cd /etc/apache2/conf**]{style="color: rgb(0,51,102);"}

    [**cp httpd.conf httpd.conf.bak**]{style="color: rgb(0,51,102);"}

    [**vi httpd.conf**]{style="color: rgb(0,51,102);"}

    [Inside the file, Set the user and group values to apache
    :]{style="color: rgb(0,51,102);"}

    [**User apache**]{style="color: rgb(0,51,102);"}

    [**Group apache**]{style="color: rgb(0,51,102);"}

    [Uncomment the line Server-pool management (MPM specific file)
    :]{style="color: rgb(0,51,102);"}

    [**Include
    conf/extra/httpd-mpm.conf**]{style="color: rgb(0,51,102);"}

    [**Include
    conf/extra/httpd-default.conf**]{style="color: rgb(0,51,102);"}

    [Also, add the below line :]{style="color: rgb(0,51,102);"}

    [**Include conf/vhosts/\*.conf**]{style="color: rgb(0,51,102);"}

    [Save and exit the file]{style="color: rgb(0,51,102);"}

4.  [Next, we will create apache virtual hosts, as defined above in
    httpd.conf file :]{style="color: rgb(0,51,102);"}

    [**cd /etc/apache2/conf**]{style="color: rgb(0,51,102);"}

    [**mkdir vhosts**]{style="color: rgb(0,51,102);"}

    [**cd vhosts**]{style="color: rgb(0,51,102);"}

    [**touch
    [[example.com]{style="color: rgb(0,51,102);"}](http://example.com).conf**]{style="color: rgb(0,51,102);"}

    [**vi
    [[example.com]{style="color: rgb(0,51,102);"}](http://example.com).conf**]{style="color: rgb(0,51,102);"}

    [Enter the following details in the conf file
    :]{style="color: rgb(0,51,102);"}

    [**\<VirtualHost \*:80\>**]{style="color: rgb(0,51,102);"}

    [**ServerName
    [[example.com]{style="color: rgb(0,51,102);"}](http://example.com)**]{style="color: rgb(0,51,102);"}

    [**DocumentRoot
    /etc/apache2/htdocs**]{style="color: rgb(0,51,102);"}

    [**\<Directory
    /etc/apache2/htdocs\>**]{style="color: rgb(0,51,102);"}

    [**AllowOverride All**]{style="color: rgb(0,51,102);"}

    [**Require all granted**]{style="color: rgb(0,51,102);"}

    [**\</Directory\>**]{style="color: rgb(0,51,102);"}

    [**ErrorLog
    \"/var/log/apache/error.log\"**]{style="color: rgb(0,51,102);"}

    [**CustomLog \"/var/log/apache/access.log\"
    common**]{style="color: rgb(0,51,102);"}

    [**\</VirtualHost\>**]{style="color: rgb(0,51,102);"}

5.  [In httpd.conf file we enabled mpm settings. Now it's time to edit
    this file.]{style="color: rgb(0,51,102);"}

    [**cd /etc/apache2/conf/extra** ]{style="color: rgb(0,51,102);"}

    [**vi httpd-mpm.conf**]{style="color: rgb(0,51,102);"}

    [By default apache's pid file httpd.pid is located in logs file,
    let's change it to /var/run
    directory.]{style="color: rgb(0,51,102);"}

    [**PidFile \"/var/run/httpd.pid\"**]{style="color: rgb(0,51,102);"}

6.  [Now, start the server and enable it permanently using
    :]{style="color: rgb(0,51,102);"}

    [**systemctl start httpd**]{style="color: rgb(0,51,102);"}

    [**systemctl enable httpd**]{style="color: rgb(0,51,102);"}

7.  [Browse the web server by
    **https://\<your_ip_address\>**]{style="color: rgb(0,51,102);"}

8.  [If it doesn't opens, just check the firewall status and stop it, if
    it is running and reload the page.]{style="color: rgb(0,51,102);"}

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
[-Seren Jhanwar]{style="color: rgb(0,51,102);"}
:::
