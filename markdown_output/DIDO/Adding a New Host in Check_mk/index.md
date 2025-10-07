\

\

**The following steps can be performed only by the admin user\**

**Step1:** Browse through the Check_mk below and login with your LDAP
credentials

URL: <http://192.168.2.35/dailyhunt/check_mk/login.py>

\

\

**Step 2:** The Home page appears after login. For adding a new host
into check_mk go to ***Hosts*** option under  ***WATO-
configuration**** *section

**\**

**Step 3**:

- Choose a directory in which you want to create a new host \
  Eg: Here a New host is been added to the Analytics directory

  \
  \

<!-- -->

- Now go to *****New host***** option\

\

**Step 4:**

- In ***Host name *** option give a specific host name according to the
  requirement\
  Eg: Here The hostname is ***dh-reporting.dailyhunt.in***
- Tick the ***Permissions*** option and specify the contact groups you
  want to contact regarding the host  services.\
  \
  [**(Note: For every host select the two contacts groups
  \"Newshunt-Admins and Eben-Notification\" without fail)**]{.underline}

**Step 5:**

- Tick ***Add these contact groups as contacts to all hosts in this
  folder*** option
- Tick  ***Alias*** option and give the same as **host name**option
- Tick ***IP address*** option  and specify the IP address accordingly\
  Eg: The Ip Address is 192.168.56.101

\

**Step 6:** Tick on the ***Monitored on site*** option and select a
required site that you want to monitor it. The following are the
monitoring sites available

\

**Step 7:** In the ***Host tags*** section

- Tick on the ***Agent type***
- Tick on ***Criticality***

\

\

**Step 8:** Click on the ***Save& Finish*** option

\

[**Step 9:** Activate the changes  by clicking on the highlighted
option.]{.confluence-embedded-file-wrapper
.confluence-embedded-manual-size}

[[**]{.confluence-embedded-file-wrapper
.confluence-embedded-manual-size}]{.confluence-embedded-file-wrapper
.confluence-embedded-manual-size}

[\
]{.confluence-embedded-file-wrapper .confluence-embedded-manual-size}

\

[\
]{.confluence-embedded-file-wrapper .confluence-embedded-manual-size}

[\
]{.confluence-embedded-file-wrapper .confluence-embedded-manual-size}

[\
]{.confluence-embedded-file-wrapper .confluence-embedded-manual-size}

\

***Hurray..!! your new host has been added to check_mk***

\

\

-Nitin Raj
