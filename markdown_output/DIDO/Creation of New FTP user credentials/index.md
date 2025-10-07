**The following steps need to be performed as a [*root
user*]{.underline}\**

**Step1:** The FTP set up is done in server 192.168.2.200. Login into
the server using your LDAP account.

**Step2: ** Go to the below specified location for the ftp-user
credentials  script

[command :]{.underline} cd /home/scripts/legacy

**Step3**: Run the script using the following command and specify the
***user name*** as per the requirement. Make sure to use all lower case
letters .

**Note: Don\'t provide any spaces in the user name. If a publisher\'s
name is a long string like \" All India Times\"  then the for the user
name just take all lower case letters and include underscore( \"\_ \")
instead of space. Resulting the user name as \" all_india_times\"** .

[command :]{.underline}  ./create_ftp.sh \<username\>

**Step4:**  Verify the user directory 

[command:]{.underline}  ls -l /ftpdata/ftp-partners/\<username\>

**Step5: ** Update the password in the FTP Password Google sheet(below
mentioned)

<https://docs.google.com/spreadsheets/d/1LH2Uc3IXW-aZYeUSZAnYLtF2ZIbJydgZZPVJl63pdS8/edit?usp=sharing>

\

\

**Hurray..!! The credentials have been created**

\

-Nitin Raj
