**Install Development Tools**\
yum groupinstall \'Development Tools\'\
\
**NIC :**\
**if kernal matching OS version then copy rpm package or copy source
package**\
exctract the driver and copy to /tmp folder\
if rpm package then install using rpm else compile\
**or comiple **\
cd /tmp/firmware/Intel_LAN_18.8.0_Linux_Source_A00.tar/Intel_LAN_18.8.0_Linux_Source_A00/Source/base_driver/ixgbe-5.3.8/src/\
make make install\
rmmod ixgbe; modprobe ixgbe   -- **perform this from console not from
ssh**\
reboot \
\
**Raid Card:**\
**Copy the file to /tmp folder and extrace folder.**\
compile if kernal version is higher than defualt kernal.\
uname -a -- find kernal version modinfo megaraid_sas\|more -- find raid
card version version: 07.700.00.00-rc1 rpm -qa \| grep -i kernal-devel
-- to check installed yum \--showduplicates list kernel-devel \--if show
present kernal then install or download and install kernal-devel if not
found download rpm from
link [[{+}]{style="color: rgb(0,0,238);"}](http://vault.centos.org/6.10/updates/Source/SPackages/)[http://vault.centos.org/6.10/updates/Source/SPackages/+](http://vault.centos.org/6.10/updates/Source/SPackages/+){.external-link
rel="nofollow"} or [[{+}]{style="color: rgb(0,0,238);"}](http://vault.centos.org/6.9/updates/x86_64/Packages/)[http://vault.centos.org/6.9/updates/x86_64/Packages/+](http://vault.centos.org/6.9/updates/x86_64/Packages/+){.external-link
rel="nofollow"} \
\
rpm -ivh kernel-devel-2.6.32-696.10.1.el6.x86_64.rpm \--install kernel
devel cd /tmp/firmware/UnifiedDriver_7.703.06.00_RHEL6
(1).tar/UnifiedDriver_7.703.06.00_RHEL6 -- change to source package rpm
-ivvvh megaraid_sas-07.703.06.00-1.src.rpm -- build package ls
/root/rpmbuild/SPECS/ \--check file created cd /root/rpmbuild/SPECS/
rpmbuild -ba megaraid_sas.spec rpm -ivh \--test
/root/rpmbuild/RPMS/x86_64/kmod-megaraid_sas-07.703.06.00-1.x86_64.rpm
-- to test rpm is fine\
**If kernel is matching then install the rpm package under os folder.**\
\[root@dh-hw-m1d24 rpms-1\]# pwd
/tmp/UNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00/rhel6.10/rpms-1
\[root@dh-hw-m1d24 rpms-1\]# ls
kmod-megaraid_sas-07.705.05.00_el6.10-1.x86_64.rpm\
rpm -ivh kmod-megaraid_sas-07.705.05.00_el6.10-1.x86_64.rpm\
perform reboot and check everything fine.\
++++++++++[sample
server]{style="text-decoration: underline;"}++++++++++++\
root@dh-hw-m1d11 firmware\]# ls [l total 14108
-rw-r]{style="text-decoration: line-through;"}[r]{style="text-decoration: line-through;"}-
1 root root 1334 Jun 23 19:23 fstab
[rw-r]{style="text-decoration: line-through;"}[r]{style="text-decoration: line-through;"}-
1 root root 12924908 Jun 17 12:02
Intel_LAN_18.8.0_Linux_Binary_RPMs_A00.tar.gz
[rw-r]{style="text-decoration: line-through;"}[r]{style="text-decoration: line-through;"}-
1 root root 1511710 Jun 11 11:39
RHEL_6_10_SourceUNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00.tar.gz
\[root@dh-hw-m1d11 firmware\]# uname [a Linux
[[[dh-hw-m1d11.dbp.dailyhunt.in]{style="text-decoration: underline;"}]{style="color: rgb(0,0,238);"}](http://dh-hw-m1d11.dbp.dailyhunt.in)
2.6.32-754.el6.x86_64 #1 SMP Tue Jun 19 21:26:04 UTC 2018 x86_64 x86_64
x86_64 GNU/Linux \[root@dh-hw-m1d11 firmware\]# tar -xvf
Intel_LAN_18.8.0_Linux_Binary_RPMs_A00.tar.gz RHEL6.10_KMOD/
RHEL6.10_KMOD/default/
RHEL6.10_KMOD/default/kmod-i40e-2.6.12_b-1.el6.x86_64.rpm
RHEL6.10_KMOD/default/kmod-igb-5.3.5.20-1.x86_64.rpm
RHEL6.10_KMOD/default/kmod-ixgbe-5.3.8-1.el6.x86_64.rpm
RHEL6.10_KMOD/default/license_gpl.txt
RHEL6.10_KMOD/kmod-i40e-2.6.12_b-1.el6.x86_64.rpm
RHEL6.10_KMOD/kmod-i40evf-3.5.14-1.el6.x86_64.rpm
RHEL6.10_KMOD/kmod-igb-5.3.5.20-1.x86_64.rpm
RHEL6.10_KMOD/kmod-ixgbe-5.3.8-1.el6.x86_64.rpm
RHEL6.10_KMOD/kmod-ixgbevf-4.3.6-1.el6.x86_64.rpm
RHEL6.10_KMOD/kmodhelp.txt RHEL6.10_KMOD/license_gpl.txt RHEL7.5_KMOD/
RHEL7.5_KMOD/default/
RHEL7.5_KMOD/default/kmod-i40e-2.6.12_b-1.el7.x86_64.rpm
RHEL7.5_KMOD/default/kmod-igb-5.3.5.20-1.x86_64.rpm
RHEL7.5_KMOD/default/kmod-ixgbe-5.3.8-1.el7.x86_64.rpm
RHEL7.5_KMOD/default/license_gpl.txt
RHEL7.5_KMOD/kmod-i40e-2.6.12_b-1.el7.x86_64.rpm
RHEL7.5_KMOD/kmod-i40evf-3.5.14-1.el7.x86_64.rpm
RHEL7.5_KMOD/kmod-igb-5.3.5.20-1.x86_64.rpm
RHEL7.5_KMOD/kmod-ixgbe-5.3.8-1.el7.x86_64.rpm
RHEL7.5_KMOD/kmod-ixgbevf-4.3.6-1.el7.x86_64.rpm
RHEL7.5_KMOD/kmodhelp.txt RHEL7.5_KMOD/license_gpl.txt SLES15_KMP/
SLES15_KMP/default/ SLES15_KMP/default/intel-i40e-2.6.12-18.1.x86_64.rpm
SLES15_KMP/default/intel-i40e-kmp-default-2.6.12_k4.12.14_23-18.1.x86_64.rpm
SLES15_KMP/default/intel-igb-5.3.5.20-5.1.x86_64.rpm
SLES15_KMP/default/intel-igb-kmp-default-5.3.5.20_k4.12.14_23-5.1.x86_64.rpm
SLES15_KMP/default/intel-ixgbe-5.3.8-3.1.x86_64.rpm
SLES15_KMP/default/intel-ixgbe-kmp-default-5.3.8_k4.12.14_23-3.1.x86_64.rpm
SLES15_KMP/default/license_gpl.txt
SLES15_KMP/intel-i40e-2.6.12-18.1.src.rpm
SLES15_KMP/intel-i40e-2.6.12-18.1.x86_64.rpm
SLES15_KMP/intel-i40e-kmp-default-2.6.12_k4.12.14_23-18.1.x86_64.rpm
SLES15_KMP/intel-i40evf-3.5.14-2.1.src.rpm
SLES15_KMP/intel-i40evf-3.5.14-2.1.x86_64.rpm
SLES15_KMP/intel-i40evf-kmp-default-3.5.14_k4.12.14_23-2.1.x86_64.rpm
SLES15_KMP/intel-igb-5.3.5.20-5.1.src.rpm
SLES15_KMP/intel-igb-5.3.5.20-5.1.x86_64.rpm
SLES15_KMP/intel-igb-kmp-default-5.3.5.20_k4.12.14_23-5.1.x86_64.rpm
SLES15_KMP/intel-ixgbe-5.3.8-3.1.src.rpm
SLES15_KMP/intel-ixgbe-5.3.8-3.1.x86_64.rpm
SLES15_KMP/intel-ixgbe-kmp-default-5.3.8_k4.12.14_23-3.1.x86_64.rpm
SLES15_KMP/intel-ixgbevf-4.3.6-4.1.src.rpm
SLES15_KMP/intel-ixgbevf-4.3.6-4.1.x86_64.rpm
SLES15_KMP/intel-ixgbevf-kmp-default-4.3.6_k4.12.14_23-4.1.x86_64.rpm
SLES15_KMP/kmp_help.txt SLES15_KMP/license_gpl.txt bootutil/
bootutil/bootutil.txt bootutil/bootutil64e bootutil/install
bootutil/iqvlinux.tar.gz bootutil/license.pdf \[root@dh-hw-m1d11
firmware\]# ls -l total 14124 drwxr-xr-x 2 1362881 1049089 4096 Oct 3
2018 bootutil
-rw-r]{style="text-decoration: line-through;"}[r]{style="text-decoration: line-through;"}-
1 root root 1334 Jun 23 19:23 fstab
[rw-r]{style="text-decoration: line-through;"}[r]{style="text-decoration: line-through;"}-
1 root root 12924908 Jun 17 12:02
Intel_LAN_18.8.0_Linux_Binary_RPMs_A00.tar.gz drwxr-xr-x 3 1362881
1049089 4096 Oct 3 2018 RHEL6.10_KMOD
[rw-r]{style="text-decoration: line-through;"}[r]{style="text-decoration: line-through;"}-
1 root root 1511710 Jun 11 11:39
RHEL_6_10_SourceUNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00.tar.gz
drwxr-xr-x 3 1362881 1049089 4096 Oct 3 2018 RHEL7.5_KMOD drwxr-xr-x 3
1362881 1049089 4096 Oct 3 2018 SLES15_KMP \[root@dh-hw-m1d11
firmware\]# cd RHEL6.10_KMOD \[root@dh-hw-m1d11 RHEL6.10_KMOD\]# ls [l
total 2232 drwxr-xr-x 2 1362881 1049089 4096 Oct 3 2018 default
-rw-r]{style="text-decoration: line-through;"}[r]{style="text-decoration: line-through;"}-
1 1362881 1049089 1537 Oct 6 2017 kmodhelp.txt
[rw-r]{style="text-decoration: line-through;"}[r]{style="text-decoration: line-through;"}-
1 1362881 1049089 1307280 Aug 1 2018 kmod-i40e-2.6.12_b-1.el6.x86_64.rpm
[rw-r]{style="text-decoration: line-through;"}[r]{style="text-decoration: line-through;"}-
1 1362881 1049089 610512 Aug 16 2018 kmod-i40evf-3.5.14-1.el6.x86_64.rpm
[rw-r]{style="text-decoration: line-through;"}[r]{style="text-decoration: line-through;"}-
1 1362881 1049089 111808 Aug 16 2018 kmod-igb-5.3.5.20-1.x86_64.rpm
[rw-r]{style="text-decoration: line-through;"}[r]{style="text-decoration: line-through;"}-
1 1362881 1049089 165904 Aug 10 2018 kmod-ixgbe-5.3.8-1.el6.x86_64.rpm
[rw-r]{style="text-decoration: line-through;"}[r]{style="text-decoration: line-through;"}-
1 1362881 1049089 46316 Aug 10 2018 kmod-ixgbevf-4.3.6-1.el6.x86_64.rpm
[rw-r]{style="text-decoration: line-through;"}[r]{style="text-decoration: line-through;"}-
1 1362881 1049089 18954 Jul 12 2018 license_gpl.txt \[root@dh-hw-m1d11
RHEL6.10_KMOD\]# ethtool [i em1 driver: ixgbe version: 4.2.1-k
firmware-version: 0x8000095c bus-info: 0000:01:00.0 supports-statistics:
yes supports-test: yes supports-eeprom-access: yes
supports-register-dump: yes supports-priv-flags: no \[root@dh-hw-m1d11
RHEL6.10_KMOD\]# ethtool -i em3 driver: igb version: 5.3.0-k
firmware-version: 1.67, 0x80000fab, 18.8.9 bus-info: 0000:06:00.0
supports-statistics: yes supports-test: yes supports-eeprom-access: yes
supports-register-dump: yes supports-priv-flags: no \[root@dh-hw-m1d11
RHEL6.10_KMOD\]# rpm -ivh kmod-ixgbe-5.3.8-1.el6.x86_64.rpm
Preparing\... \########################################### \[100%\]
1:kmod-ixgbe \########################################### \[100%\]
\[root@dh-hw-m1d11 RHEL6.10_KMOD\]# \[root@dh-hw-m1d11 RHEL6.10_KMOD\]#
\[root@dh-hw-m1d11 RHEL6.10_KMOD\]# \[root@dh-hw-m1d11 RHEL6.10_KMOD\]#
rpm -ivh kmod-igb-5.3.5.20-1.x86_64.rpm Preparing\...
\########################################### \[100%\] 1:kmod-igb
\########################################### \[100%\] \[root@dh-hw-m1d11
RHEL6.10_KMOD\]# \[root@dh-hw-m1d11 RHEL6.10_KMOD\]# \[root@dh-hw-m1d11
RHEL6.10_KMOD\]# \[root@dh-hw-m1d11 RHEL6.10_KMOD\]# cd /tmp/firmware/
\[root@dh-hw-m1d11 firmware\]# \[root@dh-hw-m1d11 firmware\]#
\[root@dh-hw-m1d11 firmware\]# \[root@dh-hw-m1d11 firmware\]#
\[root@dh-hw-m1d11 firmware\]# \[root@dh-hw-m1d11 firmware\]# cd
/tmp/firmware/ \[root@dh-hw-m1d11 firmware\]# \[root@dh-hw-m1d11
firmware\]# \[root@dh-hw-m1d11 firmware\]# \[root@dh-hw-m1d11
firmware\]# ls -l total 14124 drwxr-xr-x 2 1362881 1049089 4096 Oct 3
2018 bootutil
-rw-r]{style="text-decoration: line-through;"}[r]{style="text-decoration: line-through;"}-
1 root root 1334 Jun 23 19:23 fstab
[rw-r]{style="text-decoration: line-through;"}[r]{style="text-decoration: line-through;"}-
1 root root 12924908 Jun 17 12:02
Intel_LAN_18.8.0_Linux_Binary_RPMs_A00.tar.gz drwxr-xr-x 3 1362881
1049089 4096 Oct 3 2018 RHEL6.10_KMOD
[rw-r]{style="text-decoration: line-through;"}[r]{style="text-decoration: line-through;"}-
1 root root 1511710 Jun 11 11:39
RHEL_6_10_SourceUNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00.tar.gz
drwxr-xr-x 3 1362881 1049089 4096 Oct 3 2018 RHEL7.5_KMOD drwxr-xr-x 3
1362881 1049089 4096 Oct 3 2018 SLES15_KMP \[root@dh-hw-m1d11
firmware\]# tar [xvf
RHEL_6_10_SourceUNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00.tar.gz
UNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00/
UNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00/rhel6.10/
UNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00/rhel6.10/disks-1/
UNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00/rhel6.10/disks-1/megaraid_sas-07.705.05.00_el6.10-1.x86_64.iso.gz
UNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00/rhel6.10/rpms-1/
UNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00/rhel6.10/rpms-1/kmod-megaraid_sas-07.705.05.00_el6.10-1.x86_64.rpm
UNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00/RHEL_Release_Notes_7.705.05.00.txt
UNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00/Source/
UNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00/Source/kmod_srpm/
UNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00/Source/kmod_srpm/megaraid_sas-07.705.05.00-1.src.rpm
UNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00/Source/megaraid_sas-07.705.05.00-src.tar.gz
UNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00/Source/README_mr7.5.pdf
\[root@dh-hw-m1d11 firmware\]# \[root@dh-hw-m1d11 firmware\]#
\[root@dh-hw-m1d11 firmware\]# \[root@dh-hw-m1d11 firmware\]# ls -l
total 14128 drwxr-xr-x 2 1362881 1049089 4096 Oct 3 2018 bootutil
-rw-r]{style="text-decoration: line-through;"}[r]{style="text-decoration: line-through;"}-
1 root root 1334 Jun 23 19:23 fstab
[rw-r]{style="text-decoration: line-through;"}[r]{style="text-decoration: line-through;"}-
1 root root 12924908 Jun 17 12:02
Intel_LAN_18.8.0_Linux_Binary_RPMs_A00.tar.gz drwxr-xr-x 3 1362881
1049089 4096 Oct 3 2018 RHEL6.10_KMOD
[rw-r]{style="text-decoration: line-through;"}[r]{style="text-decoration: line-through;"}-
1 root root 1511710 Jun 11 11:39
RHEL_6_10_SourceUNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00.tar.gz
drwxr-xr-x 3 1362881 1049089 4096 Oct 3 2018 RHEL7.5_KMOD drwxr-xr-x 3
1362881 1049089 4096 Oct 3 2018 SLES15_KMP drwxrwxrwx 4 root root 4096
Oct 2 2018 UNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00 \[root@dh-hw-m1d11
firmware\]# cd UNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00/
\[root@dh-hw-m1d11 UNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00\]#
\[root@dh-hw-m1d11 UNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00\]#
\[root@dh-hw-m1d11 UNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00\]#
\[root@dh-hw-m1d11 UNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00\]# ls -l
total 12 drwxrwxrwx 4 root root 4096 Sep 28 2018 rhel6.10 -rwxrwxrwx 1
root root 1851 Oct 2 2018 RHEL_Release_Notes_7.705.05.00.txt drwxrwxrwx
3 root root 4096 Oct 2 2018 Source \[root@dh-hw-m1d11
UNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00\]# \[root@dh-hw-m1d11
UNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00\]# \[root@dh-hw-m1d11
UNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00\]# \[root@dh-hw-m1d11
UNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00\]# \[root@dh-hw-m1d11
UNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00\]# \[root@dh-hw-m1d11
UNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00\]# \[root@dh-hw-m1d11
UNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00\]# \[root@dh-hw-m1d11
UNIFIED_DRVR_RHEL6_P1FJJ_A00_7.705.05.00\]# cd rhel6.10/
\[root@dh-hw-m1d11 rhel6.10\]# ls -l total 8 drwxrwxrwx 2 root root 4096
Sep 28 2018 disks-1 drwxrwxrwx 2 root root 4096 Sep 28 2018 rpms-1
\[root@dh-hw-m1d11 rhel6.10\]# cd rpms-1/ \[root@dh-hw-m1d11 rpms-1\]#
ls -l total 440 -rwxrwxrwx 1 root root 449744 Jun 26 2018
kmod-megaraid_sas-07.705.05.00_el6.10-1.x86_64.rpm \[root@dh-hw-m1d11
rpms-1\]# rpm -ivh kmod-megaraid_sas-07.705.05.00_el6.10-1.x86_64.rpm
Preparing\... \########################################### \[100%\]
1:kmod-megaraid_sas \###########################################
\[100%\]\
++++++++++++++++++++++++++++++++++\
R740XD\
\
\
\
\
\
\
\
\
\
**+++++++++++++++++++++++++++++++**\
**Perform below as a one time check during upgrades.**\
**check NIC bonding working, if not break bondign and create single NIC
with IP and udpate sheet.**\
\[root@dh-hw-m1d10 \~\]# cat /proc/net/bonding/bond0 Ethernet Channel
Bonding Driver: v3.7.1 (April 27, 2011)\
Bonding Mode: fault-tolerance (active-backup) Primary Slave: None
Currently Active Slave: p5p2 MII Status: up MII Polling Interval (ms):
100 Up Delay (ms): 0 Down Delay (ms): 0\
Slave Interface: p5p2 MII Status: up Speed: 10000 Mbps Duplex: full Link
Failure Count: 0 Permanent HW addr: f4:e9:d4:92:5a:22 Slave queue ID: 0
\[root@dh-hw-m1d10 \~\]# \[root@dh-hw-m1d10 \~\]#\
**check UUIDs are undated in fstab for all mounts, if not modify
fstab**\
**check fsck is enabled on all disks duirng boot if not enable fsck
check during boot.**\
\
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_*Varaprasad
June 18th 2020*\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
