**The following steps can be performed only by the admin user.\**

**Step1:** Browse through the Check_mk below and login with your LDAP
credentials.

URL:
[http://192.168.2.35/dailyhunt/check_mk/login.py](http://192.168.2.35/dailyhunt/check_mk/login.py){.external-link
rel="nofollow"}

\

[]{.confluence-embedded-file-wrapper .confluence-embedded-manual-size}

[\
]{.confluence-embedded-file-wrapper .confluence-embedded-manual-size}

**Step 2:** The Home page appears after login. For adding a new host
into check_mk go to ***Hosts*** option under  ***WATO-
configuration**** *section.

[]{.confluence-embedded-file-wrapper .confluence-embedded-manual-size}

[\
]{.confluence-embedded-file-wrapper .confluence-embedded-manual-size}

**Step 3**: 

[ Now go to ***New  folder*** option.]{.confluence-embedded-file-wrapper
.confluence-embedded-manual-size}

[]{.confluence-embedded-file-wrapper .confluence-embedded-manual-size}

**[Step 4: ]{.confluence-embedded-file-wrapper
.confluence-embedded-manual-size}**

- [Specify the Folder name accordingly in the ***Title***
  option.]{.confluence-embedded-file-wrapper
  .confluence-embedded-manual-size}

[           Eg: ***Search-1*** is the folder name given here.\
]{.confluence-embedded-file-wrapper .confluence-embedded-manual-size}

[[]{.confluence-embedded-file-wrapper
.confluence-embedded-manual-size}]{.confluence-embedded-file-wrapper
.confluence-embedded-manual-size}

- [[Tick the ***Permissions*** option and specify the contact groups you
  want to contact regarding the host  services.\
  [**(Note: For every host select the two contacts groups
  \"Newshunt-Admins and Eben-Notification\" without
  fail**]{.underline}]{.confluence-embedded-file-wrapper
  .confluence-embedded-manual-size}]{.confluence-embedded-file-wrapper
  .confluence-embedded-manual-size}\
  \
  [[[\]{.underline}
  ]{.confluence-embedded-file-wrapper
  .confluence-embedded-manual-size}]{.confluence-embedded-file-wrapper
  .confluence-embedded-manual-size}\
  \
  \
  \
  \

[[**Step 5**: In the ***Host tags***
section]{.confluence-embedded-file-wrapper
.confluence-embedded-manual-size}]{.confluence-embedded-file-wrapper
.confluence-embedded-manual-size}

- Tick on the ***Agent type***
- Tick on ***Criticality***
- Tick on ***Network segment***

[]{.confluence-embedded-file-wrapper .confluence-embedded-manual-size}

[**Step 6: ** Click on the ***Save and Finish*** button .\
]{.confluence-embedded-file-wrapper .confluence-embedded-manual-size}

[\
]{.confluence-embedded-file-wrapper .confluence-embedded-manual-size}

[**Step 7:** Activate the changes  by clicking on the highlighted
option.]{.confluence-embedded-file-wrapper
.confluence-embedded-manual-size}

[[**]{.confluence-embedded-file-wrapper
.confluence-embedded-manual-size}]{.confluence-embedded-file-wrapper
.confluence-embedded-manual-size}

[\
]{.confluence-embedded-file-wrapper .confluence-embedded-manual-size}

[**Step 8**:  After the changes get activated a New folder with
***Search-1***(according to your specification) will be visible in the
Main directory.]{.confluence-embedded-file-wrapper
.confluence-embedded-manual-size}

[\
]{.confluence-embedded-file-wrapper .confluence-embedded-manual-size}

[]{.confluence-embedded-file-wrapper .confluence-embedded-manual-size}

[\
]{.confluence-embedded-file-wrapper .confluence-embedded-manual-size}

[**Step 9 :** Now go to ***Host & Service Groups*** section
under ***WATO-
configuration**** *section.]{.confluence-embedded-file-wrapper
.confluence-embedded-manual-size}

[]{.confluence-embedded-file-wrapper .confluence-embedded-manual-size}

[**Step 10:** The following page appears after clicking  on  ***Host &
Service Group*** section . Now click on ***New host group***
option.]{.confluence-embedded-file-wrapper
.confluence-embedded-manual-size}

[]{.confluence-embedded-file-wrapper .confluence-embedded-manual-size}

[**Step 11:**  Under the Properties section  specify the ***Name*** and
***Alias*** options same as Folder Name and save.\
]{.confluence-embedded-file-wrapper .confluence-embedded-manual-size}

[Eg: Here the folder name created as ***Search-1*** . so, ***Name*** and
***Alias*** sections are also specified as ***\"Search-1***\".\
]{.confluence-embedded-file-wrapper .confluence-embedded-manual-size}

**

**\**

**\
Step 12:** Now go back to step 9 . Now click on ***Rules*** option .

\

**Step 13: ** Scroll down the page and click on ***Create rule in
folder*** option .

\

**Step 14:** The following page appears , In Conditions section select
the Folder option according to the created folder.

Eg: Here we have selected the folder we created  i.e,
***\"Search-1\".***

- In ***Host tags*** section select the options as shown in below
  picture.

\

- Under the ***Assignment of hosts to host group section*** select the
  host group  you created in the ***step 11***.\
  Eg: Here we created a host group as ***Search-1*** so we selected as
  ***Search-1.***

<!-- -->

- Click on the ***save*** option and ***Activate the changes made.***

\

***Hurray..!! your new  folder has been added to check_mk***

[\
]{.confluence-embedded-file-wrapper .confluence-embedded-manual-size}

[\
]{.confluence-embedded-file-wrapper .confluence-embedded-manual-size}

[-Nitin Raj\
]{.confluence-embedded-file-wrapper .confluence-embedded-manual-size}
