**Step1:** login to the machine with your LDAP credentials

**Step2:** Go to ***/etc/hosts/*** file and change the name beside the
IP address and save the file

[command]{.underline} \# **vi /*****etc/*****hosts**

**Step3:** Go to */**etc/sysconfig/network*** file and change the name
beside the IP address and save the file

[command]{.underline} \# **vi /etc/sysconfig/network**

**Step4:** Execute the command **hostname** ***newhostname***

*** *** Note: replace ***newhostname***  according to your requirement

 example for newhostname : change from
*dh-hw-spark-analytics.dailyhunt.in * to
*dh-hw-spark-n3-analytics.dailyhunt.in*\

\

[command:]{.underline} **hostname** *[**newhostname**]{.underline}*

**In this case the hostname is changed to
dh-hw-spark-n3-analytics.dailyhunt.in**

**\**

**\**

-Nitin Raj**\**
