**Step1:** Login into a server with your LDAP credentials

**Step2:** Become a root user by executing 

- [ command]{.underline} : ***sudo -i***

**Step3**. Check the java version of the server that is set to default
by executing the either command

- [command 1]{.underline}: **java -version**

  (or)

- [command 2]{.underline}**: cat /*****etc*****/profile.d/jdk.sh**

The output of the command gives the java home variable .

For example

root@192.168.56.102:\~\# **cat /etc/profile.d/jdk.sh**

export JAVA_HOME=***/usr/local/jdk1.8.0_161***

export PATH=\$JAVA_HOME/bin:\$PATH

The default java home variabale is located in ***/usr/local/
jdk1.8.0_161*** in this case

Note: It will be different to all the machines

**Step4** . Go to location where java home is located and go to cacerts
file location

- [command:]{.underline}**  cd** */**usr/local/
  jdk1.8.0_161/jre/lib/security/***

**Step5**. Now check the cacerts file exist or not

- [command]{.underline}**: ls**

The cacerts file is main file where we are installing the certificate.

**Step6.** Taking the backup of the present cacerts file

- [command]{.underline} ***: cp -p cacerts
  cacerts.backup.[date]{.underline}***

  ***Note :*** **date** [**,**]{.underline}*[**it should be changed by
  the present day's date**]{style="text-decoration: none;"}*

[**Step7.**]{style="text-decoration: none;"}[ Downloading the
certificate from a specific website.]{style="text-decoration: none;"}

- Note:( Use firefox browser)

- [Go to website (]{style="text-decoration: none;"}[eg:
  ]{style="text-decoration: none;"}[[www.patrika.com](http://www.patrika.com/)]{.underline}[)
  \-\-\--\> click on the https (green lock visable on the site) symbol
  \-\-\-\--\> more information \-\-\-\--\>view certificate
  \-\-\--\>details \-\-\--\> in certificates field click on certificate
  \-\-\-\--\> export .]{style="text-decoration: none;"}

- [The certificate gets downloaded ]{style="text-decoration: none;"}[in
  .crt format]{style="text-decoration: none;"}

[copy the downloaded .crt file from local machine to the server you want
to install. ([Execute the below mentioned command  from your local
machine.]{style="text-decoration: none;"})\
]{style="text-decoration: none;"}

- [[command:]{.underline}  **scp /Downloads/patrika.crt
  xyz@192.168.25.60 : /home/xyz/**    ]{style="text-decoration: none;"}\
  *General format of SCP : scp location of downloaded file in local
  machine  username@ip address : location of the file to put in the
  server*\
  [Note: Here patrika.crt is the file that has been downloaded & kept in
  the Downloads folder in the local machine. And xyz is the user name
  and ip address (change the ip address (192.168.25.60)accordingly)  &
  /home/xyz/ is the home folder of xyz user on the server\
  ]{style="text-decoration: none;"}

[**Step8** ]{style="text-decoration: none;"}[Installing the new
downloaded certificate in the server.]{style="text-decoration: none;"}

- [** **[command]{.underline} **: cd**
  ]{style="text-decoration: none;"}*[/]{style="text-decoration: none;"}[**usr/local/
  jdk1.8.0_161/jre/lib/security/** ]{style="text-decoration: none;"}*

- [[command]{style="text-decoration: none;"}]{.underline}*[ **: keytool
  -import --** ]{style="text-decoration: none;"}[**noprompt**
  ]{style="text-decoration: none;"}[**-- storepass**
  ]{style="text-decoration: none;"}*[***changeit***]{.underline}
  *[**-**]{style="text-decoration: none;"}[**alias**
  ]{style="text-decoration: none;"}*[***patrika***]{.underline}*[
  **-keystore ./cacerts -file /home/**
  ]{style="text-decoration: none;"}*[***xyz/patrika.crt***]{.underline}

\

\

\

-Nitin Raj
