# Dell Hadoop Servers Disk Replacement and VD creation.

\
When Drive failure happens in Server we see status as failed in below
IDRAC view.\
\
\
Once the Engineer replaced disk, status changes to Ugood;/Ready.\
\
Since Raid0 is configured and VD got deleted, so disk is idle.\
To create new VD, we need server downtime from BIOS create VD or install
perccli and perform online.\
**online option to create VD**\
download perccli from
path [[{+}]{style="color: rgb(0,0,238);"}](https://www.dell.com/support/article/en-us/sln283135/how-to-use-the-poweredge-raid-controller-perc-command-line-interface-cli-utility-to-manage-your-raid-controller?lang=en)[https://www.dell.com/support/article/en-us/sln283135/how-to-use-the-poweredge-raid-controller-perc-command-line-interface-cli-utility-to-manage-your-raid-controller?lang=en+](https://www.dell.com/support/article/en-us/sln283135/how-to-use-the-poweredge-raid-controller-perc-command-line-interface-cli-utility-to-manage-your-raid-controller?lang=en+){.external-link
rel="nofollow"}\
or \
[[{+}]{style="color: rgb(0,0,238);"}](https://dl.dell.com/FOLDER06507823M/1/PERCCLI_D6YWP_7.1327.00_A09_Linux.tar.gz?uid=cd8bd747-fc8c-40d6-1703-43e7666af0f7&fn=PERCCLI_D6YWP_7.1327.00_A09_Linux.tar.gz)[https://dl.dell.com/FOLDER06507823M/1/PERCCLI_D6YWP_7.1327.00_A09_Linux.tar.gz?uid=cd8bd747-fc8c-40d6-1703-43e7666af0f7&fn=PERCCLI_D6YWP_7.1327.00_A09_Linux.tar.gz+](https://dl.dell.com/FOLDER06507823M/1/PERCCLI_D6YWP_7.1327.00_A09_Linux.tar.gz?uid=cd8bd747-fc8c-40d6-1703-43e7666af0f7&fn=PERCCLI_D6YWP_7.1327.00_A09_Linux.tar.gz+){.external-link
rel="nofollow"} \
**SCP file to /tmp folder., **\
**\[root@dh-hw-m1n1 tmp\]# tar -xvf perccli_7.1-007.0127_linux.tar.gz**
EFI/ EFI/perccli.efi license.txt Linux/
Linux/perccli-007.0127.0000.0000-1.noarch.rpm\
\[root@dh-hw-m1n1 tmp\]# cd Linux/ **\[root@dh-hw-m1n1 Linux\]# rpm -ivh
\--test perccli-007.0127.0000.0000-1.noarch.rpm** Preparing\...
\################################# \[100%\] \[root@dh-hw-m1n1 Linux\]#
rpm -ivh perccli-007.0127.0000.0000-1.noarch.rpm Preparing\...
\################################# \[100%\] Updating / installing\...
1:perccli-007.0127.0000.0000-1 \#################################
\[100%\] \[root@dh-hw-m1n1 Linux\]#\
\
[**cd /opt/MegaRAID/perccli**]{style="color: rgb(68,68,68);"}\
\[root@dh-hw-m1d15 perccli\]# ./perccli64 /c0 show Generating detailed
summary of the adapter, it may take a while to complete.\
CLI Version = 007.1327.0000.0000 July 27, 2020 Operating system = Linux
3.10.0-1127.el7.x86_64 Controller = 0 Status = Success Description =
None\
Product Name = PERC H730 Mini Serial Number = 6CA00FN SAS Address =
51866da0922a1300 PCI Address = 00:02:00:00 System Time = 11/17/2020
17:12:26 Mfg. Date = 12/14/16 Controller Time = 11/17/2020 11:42:27 FW
Package Build = 25.5.6.0009 BIOS Version =
6.33.01.0_4.16.07.00_0x06120304 FW Version = 4.300.00-8352 Driver Name =
megaraid_sas Driver Version = 07.710.50.00-rh1 Current Personality =
RAID-Mode Vendor Id = 0x1000 Device Id = 0x5D SubVendor Id = 0x1028
SubDevice Id = 0x1F49 Host Interface = PCI-E Device Interface = SAS-12G
Bus Number = 2 Device Number = 0 Function Number = 0 Domain ID = 0 Drive
Groups = 12\
TOPOLOGY : ========\
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--
DG Arr Row EID:Slot DID Type State BT Size PDC PI SED DS3 FSpace TR
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--
0 - - - - RAID1 Dgrd N 278.875 GB dflt N N dflt N N 0 0 - - - RAID1 Dgrd
N 278.875 GB dflt N N dflt N N 0 0 0 32:12 12 DRIVE Rbld Y 278.875 GB
dflt N N dflt - N 0 0 1 32:13 13 DRIVE Onln N 278.875 GB dflt N N dflt -
N 1 - - - - RAID0 Optl N 3.637 TB dflt N N dflt N N 1 0 - - - RAID0 Optl
N 3.637 TB dflt N N dflt N N 1 0 0 32:0 0 DRIVE Onln Y 3.637 TB dflt N N
dflt - N 2 - - - - RAID0 Optl N 3.637 TB dflt N N dflt N N 2 0 - - -
RAID0 Optl N 3.637 TB dflt N N dflt N N 2 0 0 32:1 1 DRIVE Onln Y 3.637
TB dflt N N dflt - N 3 - - - - RAID0 Optl N 3.637 TB dflt N N dflt N N 3
0 - - - RAID0 Optl N 3.637 TB dflt N N dflt N N 3 0 0 32:2 2 DRIVE Onln
Y 3.637 TB dflt N N dflt - N 4 - - - - RAID0 Optl N 3.637 TB dflt N N
dflt N N 4 0 - - - RAID0 Optl N 3.637 TB dflt N N dflt N N 4 0 0 32:3 3
DRIVE Onln Y 3.637 TB dflt N N dflt - N 5 - - - - RAID0 Optl N 3.637 TB
dflt N N dflt N N 5 0 - - - RAID0 Optl N 3.637 TB dflt N N dflt N N 5 0
0 32:6 6 DRIVE Onln Y 3.637 TB dflt N N dflt - N 6 - - - - RAID0 Optl N
3.637 TB dflt N N dflt N N 6 0 - - - RAID0 Optl N 3.637 TB dflt N N dflt
N N 6 0 0 32:7 7 DRIVE Onln Y 3.637 TB dflt N N dflt - N 7 - - - - RAID0
Optl N 3.637 TB dflt N N dflt N N 7 0 - - - RAID0 Optl N 3.637 TB dflt N
N dflt N N 7 0 0 32:8 8 DRIVE Onln Y 3.637 TB dflt N N dflt - N
8 - - - - RAID0 Optl N 3.637 TB dflt N N dflt N N 8 0 - - - RAID0 Optl N
3.637 TB dflt N N dflt N N 8 0 0 32:9 9 DRIVE Onln Y 3.637 TB dflt N N
dflt - N 9 - - - - RAID0 Optl N 3.637 TB dflt N N dflt N N 9 0 - - -
RAID0 Optl N 3.637 TB dflt N N dflt N N 9 0 0 32:10 10 DRIVE Onln Y
3.637 TB dflt N N dflt - N 10 - - - - RAID0 Optl N 3.637 TB dflt N N
dflt N N 10 0 - - - RAID0 Optl N 3.637 TB dflt N N dflt N N 10 0 0 32:11
11 DRIVE Onln Y 3.637 TB dflt N N dflt - N 11 - - - - RAID0 Optl N 3.637
TB dflt N N dflt N N 11 0 - - - RAID0 Optl N 3.637 TB dflt N N dflt N N
11 0 0 32:4 4 DRIVE Onln Y 3.637 TB dflt N N dflt - N
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--\
DG=Disk Group Index\|Arr=Array Index\|Row=Row Index\|EID=Enclosure
Device ID DID=Device ID\|Type=Drive
Type\|Onln=Online\|Rbld=Rebuild\|Optl=Optimal\|Dgrd=Degraded
Pdgd=Partially degraded\|Offln=Offline\|BT=Background Task Active PDC=PD
Cache\|PI=Protection Info\|SED=Self Encrypting Drive\|Frgn=Foreign
DS3=Dimmer Switch 3\|dflt=Default\|Msng=Missing\|FSpace=Free Space
Present TR=Transport Ready\
Virtual Drives = 12\
VD LIST : =======\
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--
DG/VD TYPE State Access Consist Cache Cac sCC Size Name
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--
0/0 RAID1 Dgrd RW Yes RWBD - OFF 278.875 GB 1/1 RAID0 Optl RW Yes RWBD -
OFF 3.637 TB Data 2/2 RAID0 Optl RW Yes RWBD - OFF 3.637 TB Data1 3/3
RAID0 Optl RW Yes RWBD - OFF 3.637 TB Data2 4/4 RAID0 Optl RW Yes RWBD -
OFF 3.637 TB Data3 11/5 RAID0 Optl RW Yes RWBD - OFF 3.637 TB data4 5/7
RAID0 Optl RW Yes RWBD - OFF 3.637 TB Data6 6/8 RAID0 Optl RW Yes RWBD -
OFF 3.637 TB Data7 7/9 RAID0 Optl RW Yes RWBD - OFF 3.637 TB Data8 8/10
RAID0 Optl RW Yes RWBD - OFF 3.637 TB Data9 9/11 RAID0 Optl RW Yes
RWBD - OFF 3.637 TB Data10 10/12 RAID0 Optl RW Yes RWBD - OFF 3.637 TB
Data11
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--\
VD=Virtual Drive\| DG=Drive Group\|Rec=Recovery
Cac=CacheCade\|OfLn=OffLine\|Pdgd=Partially Degraded\|Dgrd=Degraded
Optl=Optimal\|dflt=Default\|RO=Read Only\|RW=Read
Write\|HD=Hidden\|TRANS=TransportReady\|B=Blocked\|
Consist=Consistent\|R=Read Ahead Always\|NR=No Read
Ahead\|WB=WriteBack\| AWB=Always WriteBack\|WT=WriteThrough\|C=Cached
IO\|D=Direct IO\|sCC=Scheduled Check Consistency\
Physical Drives = 14\
PD LIST : =======\
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--
EID:Slt DID State DG Size Intf Med SED PI SeSz Model Sp Type
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--
32:0 0 Onln 1 3.637 TB SAS HDD N N 512B MG04SCA40EN U - 32:1 1 Onln 2
3.637 TB SAS HDD N N 512B MG04SCA40EN U - 32:2 2 Onln 3 3.637 TB SAS HDD
N N 512B MG04SCA40EN U - 32:3 3 Onln 4 3.637 TB SAS HDD N N 512B
MG04SCA40EN U - 32:4 4 Onln 11 3.637 TB SAS HDD N N 512B MG04SCA40ENY
U - **32:5 5 UGood - 3.637 TB SAS HDD N N 512B ST4000NM0295 U -** 32:6 6
Onln 5 3.637 TB SAS HDD N N 512B MG04SCA40EN U - 32:7 7 Onln 6 3.637 TB
SAS HDD N N 512B MG04SCA40EN U - 32:8 8 Onln 7 3.637 TB SAS HDD N N 512B
MG04SCA40EN U - 32:9 9 Onln 8 3.637 TB SAS HDD N N 512B MG04SCA40EN U -
32:10 10 Onln 9 3.637 TB SAS HDD N N 512B MG04SCA40EN U - 32:11 11 Onln
10 3.637 TB SAS HDD N N 512B MG04SCA40EN U - 32:12 12 Rbld 0 278.875 GB
SAS HDD N N 512B AL15SEB030NY U - 32:13 13 Onln 0 278.875 GB SAS HDD N N
512B AL14SEB030N U -
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--\
EID=Enclosure Device ID\|Slt=Slot No.\|DID=Device ID\|DG=DriveGroup
DHS=Dedicated Hot Spare\|UGood=Unconfigured Good\|GHS=Global Hotspare
UBad=Unconfigured
Bad\|Sntze=Sanitize\|Onln=Online\|Offln=Offline\|Intf=Interface
Med=Media Type\|SED=Self Encryptive Drive\|PI=Protection Info
SeSz=Sector Size\|Sp=Spun\|U=Up\|D=Down\|T=Transition\|F=Foreign
UGUnsp=UGood Unsupported\|UGShld=UGood shielded\|HSPShld=Hotspare
shielded CFShld=Configured shielded\|Cpybck=CopyBack\|CBShld=Copyback
Shielded UBUnsp=UBad Unsupported\|Rbld=Rebuild\
Enclosures = 1\
Enclosure LIST : ==============\
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--
EID State Slots PD PS Fans TSs Alms SIM Port# ProdID VendorSpecific
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--
32 OK 14 14 0 0 0 0 1 00 & 00 x8 BP13G+EXP \~
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--\
EID=Enclosure Device ID \|PD=Physical drive count \|PS=Power Supply
count\| TSs=Temperature sensor count \|Alms=Alarm count \|SIM=SIM Count
\|\|ProdID=Product ID\
BBU_Info : ========\
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--
Model State RetentionTime Temp Mode MfgDate
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--
BBU Optimal 0 hour(s) 34C - 0/00/00
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--\
**To find disk mapping to OS disk :**\
from the disk, VG check  vx values \
**./perccli64 /c0 /v5 show all** CLI Version = 007.1327.0000.0000 July
27, 2020 Operating system = Linux 3.10.0-1127.el7.x86_64 Controller = 0
Status = Success Description = None\
/c0/v5 : ======\
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--
DG/VD TYPE State Access Consist Cache Cac sCC Size Name
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--
13/5 RAID0 Optl RW Yes RWBD - OFF 3.637 TB VD NEW
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--\
Cac=CacheCade\|Rec=Recovery\|OfLn=OffLine\|Pdgd=Partially
Degraded\|Dgrd=Degraded Optl=Optimal\|dflt=Default\|RO=Read
Only\|RW=Read Write\|HD=Hidden\|TRANS=TransportReady\|B=Blocked\|
Consist=Consistent\|R=Read Ahead Always\|NR=No Read
Ahead\|WB=WriteBack\| FWB=Force WriteBack\|WT=WriteThrough\|C=Cached
IO\|D=Direct IO\|sCC=Scheduled Check Consistency\
PDs for VD 5 : ============\
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--
EID:Slt DID State DG Size Intf Med SED PI SeSz Model Sp Type
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--
64:4 4 Onln 13 3.637 TB SAS HDD N N 512B MG04SCA40ENY U -
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--\
EID=Enclosure Device ID\|Slt=Slot No.\|DID=Device ID\|DG=DriveGroup
DHS=Dedicated Hot Spare\|UGood=Unconfigured Good\|GHS=Global Hotspare
UBad=Unconfigured
Bad\|Sntze=Sanitize\|Onln=Online\|Offln=Offline\|Intf=Interface
Med=Media Type\|SED=Self Encryptive Drive\|PI=Protection Info
SeSz=Sector Size\|Sp=Spun\|U=Up\|D=Down\|T=Transition\|F=Foreign
UGUnsp=UGood Unsupported\|UGShld=UGood shielded\|HSPShld=Hotspare
shielded CFShld=Configured shielded\|Cpybck=CopyBack\|CBShld=Copyback
Shielded UBUnsp=UBad Unsupported\|Rbld=Rebuild\
VD5 Properties : ============== Strip Size = 256 KB Number of Blocks =
7812939776 Span Depth = 1 Number of Drives Per Span = 1 Write
Cache(initial setting) = WriteBack Disk Cache Policy = Disabled
Encryption = None Data Protection = None Active Operations = None
Exposed to OS = Yes **OS Drive Name = /dev/sdf** Creation Date =
12-01-2021 Creation Time = 07:32:56 AM Emulation type = default
Cachebypass size = Cachebypass-64k Cachebypass Mode = Cachebypass
Intelligent Is LD Ready for OS Requests = Yes SCSI NAA Id =
64cd98f0610fa40027900d28d69888f7 Unmap Enabled = N/A\
\
\
\
Create new Virtual disk based on failed disk as per below.\
**./perccli64 /c0 add vd type=r0 size=7451.50gb  name=VD_8 drives=32:5
wb ra strip=64**\
 vd type=r0  \--raid type Raid0\
size=7451.50gb  -- size of disk VD\
name=VD_8 -- name \
drives=32:7    -- **exact driver to format and create partition  be
careful while selecting disk**\
wb    -- options write back\
ra    -- option read ahead\
strip=64  -- stripe size ..select based on existing formatted type..some
are 64k and some are 256K\
 or \
++++\
\[root@dh-hw-m1d15 perccli\]# **./perccli64 /c0 add vd type=r0
size=3637gb name=Data5 drives=32:5 wb ra strip=64** CLI Version =
007.1327.0000.0000 July 27, 2020 Operating system = Linux
3.10.0-1127.el7.x86_64 Controller = 0 Status = Success Description = Add
VD Succeeded.\
\[root@dh-hw-m1d15 perccli\]#\
**if any error  with cache related.**\
[\[root@dh-hw-m1d13 perccli\]# ./perccli64 /c0 add vd type=r0
size=3.637gb name=grid7 drives=32:6 wb ra
strip=64]{style="color: rgb(32,33,36);"}\
[CLI Version = 007.1327.0000.0000 July 27,
2020]{style="color: rgb(32,33,36);"}\
[Operating system = Linux
3.10.0-1127.el7.x86_64]{style="color: rgb(32,33,36);"}\
[Controller = 0 Status = Failure Description = controller has data in
cache for offline or missing virtual
disks]{style="color: rgb(32,33,36);"}\
[Detailed Status : ===============
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--
VD ErrCd Status Description
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--
3.636 GB 84 Failed controller has data in cache for offline or missing
virtual disks
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--]{style="color: rgb(32,33,36);"}\
[\[root@dh-hw-m1d13 perccli\]# **./perccli64/c0/v7 delete
preservedCache**   (find v7 number which is volume number of failed
disk)]{style="color: rgb(32,33,36);"}\
[then ]{style="color: rgb(32,33,36);"}\
[**./perccli64 /c0 add vd type=r0 size=3637gb name=Data5 drives=32:5 wb
ra strip=64**]{style="color: rgb(32,33,36);"}\
+++\
Check dmesg to find new disk id \
**dmesg **\
\[Wed Feb 24 20:47:34 2021\] sd 0:2:1:0: Attached scsi generic sg1 type
0 \[Wed Feb 24 20:47:34 2021\] sd 0:2:1:0: \[sdo\] Write Protect is off
\[Wed Feb 24 20:47:34 2021\] sd 0:2:1:0: \[sdo\] Mode Sense: 1f 00 00 08
\[Wed Feb 24 20:47:34 2021\] sd 0:2:1:**0: \[sdo\] Write cache:
disabled, read cache: enabled, doesn\'t support DPO or FUA** \[Wed Feb
24 20:47:34 2021\] sd 0:2:1:0: \[sdo\] Attached SCSI disk\
\[root@dh-hw-m1n1 perccli\]# **parted /dev/sdo** GNU Parted 3.1 Using
/dev/sdo Welcome to GNU Parted! Type \'help\' to view a list of
commands. (parted) **mklabel gpt** (parted) **mkpart primary 0GB
3990GB** (parted) **quit** Information: You may need to update
/etc/fstab.\
\[root@dh-hw-m1n1 perccli\]# **mkfs.ext4 /dev/sdo1** mke2fs 1.42.9
(28-Dec-2013) Filesystem label= OS type: Linux Block size=4096 (log=2)
Fragment size=4096 (log=2) Stride=0 blocks, Stripe width=0 blocks
225837056 inodes, 903320064 blocks 45166003 blocks (5.00%) reserved for
the super user First data block=0 Maximum filesystem blocks=3051356160
27568 block groups 32768 blocks per group, 32768 fragments per group
8192 inodes per group Superblock backups stored on blocks: 32768, 98304,
163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 4096000,
7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 102400000,
214990848, 512000000, 550731776, 644972544\
Allocating group tables: done Writing inode tables: done Creating
journal (32768 blocks): done Writing superblocks and filesystem
accounting information: done\
\
**systemctl daemon**[-]{style="color: rgb(32,33,36);"}**reload    --- to
clear any old mount info**\
\[root@dh-hw-m1n1 perccli\]# blkid /dev/sda1: SEC_TYPE=\"msdos\"
UUID=\"5053-86FB\" TYPE=\"vfat\" PARTLABEL=\"EFI System Partition\"
PARTUUID=\"4738a535-3657-4d9f-ab30-2fb0c5d9a5fe\" /dev/sda2:
UUID=\"d9ad1e80-0ecc-4b87-b084-d3888c4442d1\" TYPE=\"xfs\"
PARTUUID=\"5573f220-224f-4f0c-ac17-c3ebb5814790\" /dev/sda3:
UUID=\"XOE8pg-TP1H-88n2-FVqg-xssA-sTx1-0KhAfs\" TYPE=\"LVM2_member\"
PARTUUID=\"ed840822-4e8e-41c9-b8c1-4f9323c77aff\" /dev/sdc1:
UUID=\"3d91935e-e2a2-49a1-a90d-3116ea5a0ea8\" TYPE=\"ext4\"
PARTLABEL=\"primary\" PARTUUID=\"fa51cf12-2e1b-4d18-afd4-7c2263bed95a\"
/dev/sdd1: UUID=\"7b07454b-be37-45ae-b8a4-68280982335e\" TYPE=\"ext4\"
PARTLABEL=\"primary\" PARTUUID=\"3f1f7958-7da5-4194-b75d-d47516f7778b\"
/dev/sde1: UUID=\"a256db58-a6cd-4504-8553-c9a0f6753021\" TYPE=\"ext4\"
PARTLABEL=\"primary\" PARTUUID=\"c0c7aa2f-7690-480e-8f7a-b0d7cd0cfb2f\"
/dev/sdf1: UUID=\"b0bc0170-af54-4171-8d89-eb8dabdfa46c\" TYPE=\"ext4\"
PARTLABEL=\"primary\" PARTUUID=\"21dd9cef-a1c1-4ea5-b3c1-5b198d941f45\"
/dev/sdg1: UUID=\"5ca4012c-5652-4999-8466-b3ffefeddb2a\" TYPE=\"ext4\"
PARTLABEL=\"primary\" PARTUUID=\"acfa2c0c-1743-41c0-b388-96e019278202\"
/dev/sdh1: UUID=\"5b1ebad6-d342-4eb8-8c94-a83a614e896b\" TYPE=\"ext4\"
PARTLABEL=\"primary\" PARTUUID=\"77e62450-fbd0-44f2-beec-72bd2b0fe525\"
/dev/sdi1: UUID=\"fa9819f5-99dd-40b0-a7db-1821363e879b\" TYPE=\"ext4\"
PARTLABEL=\"primary\" PARTUUID=\"5eff7c13-c567-4979-8b64-5c9509472d67\"
/dev/sdj1: UUID=\"23b34745-733a-4013-9ebe-282f0487468b\" TYPE=\"ext4\"
PARTLABEL=\"primary\" PARTUUID=\"790753b2-1f08-4340-a750-c3bf947220d1\"
/dev/sdk1: UUID=\"70fe158b-438a-4af1-acb9-4c5b17d89ed4\" TYPE=\"ext4\"
PARTLABEL=\"primary\" PARTUUID=\"dcbf831c-f44f-41de-85b9-a111d449cda1\"
/dev/sdl1: UUID=\"f01ca562-c738-4535-8aae-7f13ec320620\" TYPE=\"ext4\"
PARTLABEL=\"primary\" PARTUUID=\"30cbc6f8-523a-4a8f-b14d-7c3e8b855216\"
/dev/sdm1: UUID=\"37fe3789-b344-4786-a64a-c1f716cac1d2\" TYPE=\"ext4\"
PARTLABEL=\"primary\" PARTUUID=\"fa19d00d-9335-45bf-a91a-a0f4c3163631\"
/dev/mapper/centos-root: UUID=\"bfa9e017-013a-4afe-9763-d1ace14449d5\"
TYPE=\"xfs\" /dev/mapper/centos-swap:
UUID=\"b2d177fb-0781-46cd-a88d-59c9d2fd170a\" TYPE=\"swap\"
/dev/mapper/centos-home: UUID=\"7892e374-beb8-4a43-8933-7535ddd8f91d\"
TYPE=\"xfs\" /dev/sdo1: UUID=\"4c7264b7-d08d-4997-9ff1-edd33aecb569\"
TYPE=\"ext4\" PARTLABEL=\"primary\"
PARTUUID=\"875a5c92-b4c8-43f6-80c3-07d329d47fe3\" \[root@dh-hw-m1n1
perccli\]# vi /etc/fstab\
once done, login to OS and perform below.\
edit fstab and mount.\
mount -a\
+++++++++++++\
hadoop script to bring back disk to rotation.\
mkdir /grid/x/hadoop\
[sh /root/tuning/\*.sh]{style="color: rgb(32,33,36);"}\
\
\
\
\
