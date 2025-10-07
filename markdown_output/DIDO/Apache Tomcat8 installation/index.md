\

1.  [Update your centos system using :]{style="color: rgb(0,51,102);"}

    [**yum install epel-release && sudo yum update
    -y**]{style="color: rgb(0,51,102);"}

2.  [Install java version 7 or above using
    :]{style="color: rgb(0,51,102);"}

    [**yum install
    java-1.8.0-openjdk.x86_64**]{style="color: rgb(0,51,102);"}

3.  [Create a dedicated non root user "tomcat" in group "tomcat" using
    :]{style="color: rgb(0,51,102);"}

    [**sudo groupadd tomcat**]{style="color: rgb(0,51,102);"}

    [**sudo mkdir /opt/tomcat**]{style="color: rgb(0,51,102);"}

    [**sudo useradd -g tomcat -d /opt/tomcat
    tomcat**]{style="color: rgb(0,51,102);"}

4.  [Download and install the latest tomcat version using
    :]{style="color: rgb(0,51,102);"}

    [**wget
    [[http://www-us.apache.org/dist/tomcat/tomcat-8/v8.0.33/bin/apache-tomcat-8.0.33.tar.gz]{style="color: rgb(0,51,102);"}](http://www-us.apache.org/dist/tomcat/tomcat-8/v8.0.33/bin/apache-tomcat-8.0.33.tar.gz)**]{style="color: rgb(0,51,102);"}

    [**tar -zxvf apache-tomcat-8.0.33.tar.gz -C
    /opt/tomcat**]{style="color: rgb(0,51,102);"}

5.  [Setup proper permissions :]{style="color: rgb(0,51,102);"}

    [**cd /opt/tomcat**]{style="color: rgb(0,51,102);"}

    [**sudo chgrp -R tomcat conf**]{style="color: rgb(0,51,102);"}

    [**sudo chmod g+rwx conf**]{style="color: rgb(0,51,102);"}

    [**sudo chmod g+r conf/\***]{style="color: rgb(0,51,102);"}

    [**sudo chown -R tomcat logs/ temp/ webapps/
    work/**]{style="color: rgb(0,51,102);"}

    [**sudo chgrp -R tomcat bin**]{style="color: rgb(0,51,102);"}

    [**sudo chgrp -R tomcat lib**]{style="color: rgb(0,51,102);"}

    [**sudo chmod g+rwx bin**]{style="color: rgb(0,51,102);"}

    [**sudo chmod g+r bin/\***]{style="color: rgb(0,51,102);"}

6.  [To start the tomcat service, move to the bin folder inside tomcat
    directory and then execute
    : **./startup.sh**]{style="color: rgb(0,51,102);"}

7.  [To stop the tomcat service, move to the bin folder inside tomcat
    directory and then execute
    : **./shutdown.sh**]{style="color: rgb(0,51,102);"}

8.  [[That's it. You can now load the ip address along with mentioning
    correct port on the browser, which by default is
    8080]{style="color: rgb(0,51,102);"}\
    ]{style="color: rgb(0,51,102);"}

[    ]{style="color: rgb(0,51,102);"}

- #### [[**SSL Certificate installation on Apache Tomcat8 :**]{.underline}]{style="color: rgb(0,51,102);"}

1.  [We first change the current directory to the directory Java is
    installed. Inside the Java Home directory, cd to the bin folder.
    Inside the bin folder there is a file named keytool. This guy is
    responsible for generating the keystore file for us, using the
    command :]{style="color: rgb(0,51,102);"}

    [**keytool -genkey -keyalg RSA -alias tomcat -keystore
    selfsigned.jks -validity \<days\> -keysize
    2048**]{style="color: rgb(0,51,102);"}

    [where days : specify the number of days for which the certificate
    stays valid. It will create a .**keystore** file on your user home
    directory. On Windows, it will be on: C:Documents and
    Settings\[username\]; on Mac it will be on /Users/\[username\] and
    on Linux will be on
    /home/\[username\].]{style="color: rgb(0,51,102);"}

2.  [Enter a password for the keystore. Note this password as you
    require this for configuring the
    server.]{style="color: rgb(0,51,102);"}

3.  [Fill in the required details for generating the
    certificate.]{style="color: rgb(0,51,102);"}

4.  [Run the following command to check the contents of the keystore
    :]{style="color: rgb(0,51,102);"}

    [**keytool -list -v -keystore
    selfsigned.jks**]{style="color: rgb(0,51,102);"}

5.  [Now, edit the server.xml file with the following details
    :]{style="color: rgb(0,51,102);"}

    [**\<Connector port=\"8443\" protocol=\"HTTP/1.1\"
    SSLEnabled=\"true\"**]{style="color: rgb(0,51,102);"}

    [**maxThreads=\"150\" scheme=\"https\"
    secure=\"true\"**]{style="color: rgb(0,51,102);"}

    [**keystoreFile=\"/root/.keystore\"
    keystorePass=\"your-key-password\"**]{style="color: rgb(0,51,102);"}

    [**clientAuth=\"false\" sslProtocol=\"TLS\"
    /\>**]{style="color: rgb(0,51,102);"}

6.  [That's it, After restarting tomcat service, you van now you load
    the ip with "https"on your web browser with the appropriate port,
    8443 being the default.]{style="color: rgb(0,51,102);"}

\

\

- #### [[**Changing location of logs in Tomcat8:**]{.underline} ]{style="color: rgb(0,51,102);"}

1.  [Tomcat's main log file :
    **catalina.out**]{style="color: rgb(0,51,102);"}

    [Get into the tomcat's directory where it is installed. Get into bin
    folder and edit catalina.sh and change the environment variable path
    there.]{style="color: rgb(0,51,102);"}

2.  [Tomcat's HTTP Access Logs :
    **localhost_access_log.year-month-date.log**]{style="color: rgb(0,51,102);"}

    [Get into the tomcat's directory where it is installed. Get into
    conf directory and edit server.xml file.Edit the directory inside
    \<valve classname\> section and mention the desired directory
    there.]{style="color: rgb(0,51,102);"}

3.  [Tomcat's historical logs : **catalina.year-month-date.log**
    ]{style="color: rgb(0,51,102);"}

    [Get into the tomcat's directory where it is installed. Get into
    conf directory and edit logging.properties.Edit the directory ahead
    of \${catalina_case} inside directory section.
    ]{style="color: rgb(0,51,102);"}

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

[ ]{style="color: rgb(0,51,102);"}
