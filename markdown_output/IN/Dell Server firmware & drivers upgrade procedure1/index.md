Following is the procedure of Dell Rack servers firmware and drivers
upgrade.\
**Pre-checks:**

- Find Model and service Tag
- Download tech support as a backup
- Note down the hardware details like Model, BIOS, NIC,Raid card and
  drives
- Download IDRAC life cycle, BIOS, firmware of Raid cards, NICs, HDDs,
  (CPLD for R740XD model) etc as per Dell shared POA
- Download the NIC,raid card drivers and copy inside OS
- Compile  driver if not matching kernel version

\
**Upgrade of R730/R730XD :**

- Reboot server to check system come up without any known issues then
  shutdown
- update IDRAC life cycle manager
- update all NIC,raid,firmware,etc all in single update
- system will come up once upgrades are over
- install NIC driver
- Install Raid card
- reboot server and check

\
**Upgrade of R740xd :**

- Reboot server to check system come up without any known issues then
  shutdown
- update IDRAC life clycle manager
- upload and update CPLD
- update all NIC,raid,drive,etc all in single
- system will come up once upgrades are over
- install NIC driver
- Install Raid card firmware
- reboot server and check

\
**Note** : we may need to check fstab to see UUID is added if not add it
and enable option to perform fsck during boot\
Login to idrac and find model and other detials.\
Collect tech support.\
\
ex :server  m1d19.. find IP of Idrac from document.

  -------------------------------------------------------------------------------------------------------------------------------------------- --------------- --------- ------------------ -------------- ---------------------------
  [[[dh-hw-m1d19.dbp.dailyhunt.in]{style="text-decoration: underline;"}]{style="color: rgb(0,0,238);"}](http://dh-hw-m1d19.dbp.dailyhunt.in)   192.168.3.187   BHT6T72   PowerEdge R730xd   10.10.13.134   2.6.32-754.2.1.el6.x86_64
  -------------------------------------------------------------------------------------------------------------------------------------------- --------------- --------- ------------------ -------------- ---------------------------

\
\
\
\
\
Download firmware based on model from dell portal or from Dell provided
PDF. re-check from portal as some models may miss in Dell engineer
provided pdf.\
\
[[{+}]{style="color: rgb(0,0,238);"}](https://www.dell.com/support/home/en-us/product-support/product/poweredge-r730xd/drivers)[https://www.dell.com/support/home/en-us/product-support/product/poweredge-r730xd/drivers+](https://www.dell.com/support/home/en-us/product-support/product/poweredge-r730xd/drivers+){.external-link
rel="nofollow"}\
\
click on  view ***full driver details*** and download windows 64bit
firmware.\
\
\
\
Download the similar way Raid & NIC OS drivers.  If kernal version
higher than redhat version then download source bundle and compile
driver.\
find Centos to kernal version from link. check uname -a output to find
current installed OS kernal version\
[[{+}]{style="color: rgb(0,0,238);"}](https://access.redhat.com/articles/3078)[https://access.redhat.com/articles/3078+](https://access.redhat.com/articles/3078+){.external-link
rel="nofollow"}\
Find the current version from OS.\
\
\
\
\

  ------------- -------------------------------------------------------------------------------------------------------------------------------------------- -------------- ------------------ ------------------------------- --------------- -------- ------------------- ------------ ---------------- -------------------- ------------------- -------------- -------------- --------------
                Server                                                                                                                                       IDRAC IP       Model              os version and kernal           Idrac version   BIOS     raid card model 1   Backplane    Back plane 13G   NIC model1           NIC model12         Disk model 1   Disk model 2   Disk model 3
  Model         [[[dh-hw-m1d19.dbp.dailyhunt.in]{style="text-decoration: underline;"}]{style="color: rgb(0,0,238);"}](http://dh-hw-m1d19.dbp.dailyhunt.in)   10.10.13.134   PowerEdge R730xd   cent os 6.10  &2.6.32-754.2.1                            PERC H730 Mini                                     10G 4P X520/I350    P X520/I350 rNDC    MG03SCA400     ST300MM0008    MG03SCA400
  version                                                                                                                                                                                                                      2.21.21.21      2.9.1    25.3.0.0016         2.23         3.03             17.0.12              17.0.12             DG09           TT31           DJ01
  upgrade                                                                                                                                                                                                                      2.70.70.70      2.11.0   25.5.6.0009         2.25, A00-    3.35, A00-00    18.8.9                                   DG09           TT31           DS07
  OS driver                                                                                                                                                                                                                                                                              07.700.00        4.2.1-k                                                                 
  New driver                                                                                                                                                                                                                                                                             7.705.05         18.8.0                                                                  
  ------------- -------------------------------------------------------------------------------------------------------------------------------------------- -------------- ------------------ ------------------------------- --------------- -------- ------------------- ------------ ---------------- -------------------- ------------------- -------------- -------------- --------------

\
\
+++\
Shutdown server and perform upgrade. IDRAC can be perform when server is
power on but reset need server to be down.\
\
\
\
\
**check jobs status and if rdrac filed then provide extracted file.**\
\
once IDRAC is over then proceed with others.\
\
\
check the status from idrac console\
\
\
once file is uploaded , click on install or install and reboot based on
package added.\
**Upgrade of R730/R730XD :**

- Reboot server to check system come up without any known issues then
  shutdown
- update IDRAC life clycle manager
- update all NIC,raid, disk firmware,etc all at once
- system will comeup once upgrades are over

**Upgrade of R740xd :**

- Reboot server to check system come up without any known issues then
  shutdown
- update IDRAC life clycle manager
- upload and update CPLD
- update all NIC,raid, disk firmware,etc all at once
- system will comeup once upgrades are over

\
\
