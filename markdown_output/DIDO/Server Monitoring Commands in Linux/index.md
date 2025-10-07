1.  **Top** :

    The top command used to dipslay all the running and active real-time
    processes in ordered list and updates it regularly. It display **CPU
    usage**, **Memory usage**, **Swap Memory**, **Cache Size**, **Buffer
    Size**, **Process PID**, **User**, **Command**s and much more. It
    also shows high **memory** and **cpu** utilization of a running
    processess.\
    \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

2.  **VmStat :**

    Linux **VmStat** command used to display statistics of **virtual
    memory**, **kernerl threads**, **disks**, **system processes**,
    **I/O blocks**, **interrupts**, **CPU activity** and much more.\
    \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

3.  **Lsof :**

    **Lsof** command used in many **Linux/Unix** like system that is
    used to display list of all the open files and the processes. The
    open files included are **disk files**, **network sockets**,
    **pipes**, **devices** and **processes**. One of the main reason for
    using this command is when a disk cannot be unmounted and displays
    the error that files are being used or opened. With this commmand
    you can easily identify which files are in use.\
    \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

4.  **TcpDump :** Network Packet Analyser

    **Tcpdump** one of the most widely used command-line **network
    packet analyzer** or **packets sniffer** program that is used
    capture or filter **TCP/IP** packets that received or transferred on
    a specific interface over a network. It also provides a option to
    save captured packages in a file for later analysis.\
    \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

5.  **NetStat :** Network Statistics

    **Netstat** is a command line tool for monitoring **incoming** and
    **outgoing network** packets statistics as well as interface
    statistics. It is very useful tool for every system administrator to
    monitor network performance and troubleshoot network related
    problems.\
    \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

6.  **Htop :** Linux Processing Monitoring

    **Htop** is a much advanced interactive and real time Linux process
    monitoring tool. This is much similar to Linux **top command** but
    it has some rich features like **user friendly interface to manage
    process**, **shortcut keys**, **vertical and horizontal view of the
    processes** and much more. Htop is a third party tool and doesn't
    included in Linux systems, you need to install it using **YUM**
    package manager tool.

    \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

    \

7.  **Ps :** Process Status

    Linux provides us a utility called ps for viewing information
    related with the processes on a system which stands as abbreviation
    for **"Process Status".**ps command is used to list the currently
    running processes and their PIDs along with some other information
    depends on different options.

    \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

    \

8.  **Du :** Disk Usage

    It can be used to find size of any directory including sub directory
    and files inside it.

    To list the largest directories from the current directory in human
    readable format:\
    du -sh \* \| sort -hr \| head -n 10\
    du -csh \* \| grep G (for GB checking )

    \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

    \

9.  **Df :** Disk Filesystem

    It can be used to find the total size of the filesystem and the used
    space as well.

    \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

    \

10. When we have memory alerts :

    To see what process is eating much RAM/memory(Gives percentage of
    memory)\
    **ps aux \| awk \'{print \$2, \$4, \$11}\' \| sort -k2rn \| head -n
    20**\
    To see only the memory resources occupied by each category of
    processes, such as Apache httpd, MySQL mysqld or Java, use the
    following command:\
    **ps aux \| awk \'{print \$4\"\\t\"\$11}\' \| sort \| uniq -c \| awk
    \'{print \$2\" \"\$1\" \"\$3}\' \| sort -nr**\
    To see which process is using highest cpu usage\
    **watch \"ps aux \| sort -nrk 3,3 \| head -n 5\" ps -Ao
    user,uid,comm,pid,pcpu,tty \--sort=-pcpu \| head -n 6**

    To see the balloon memory : \
    **vmware-toolbox-cmd stat balloon**\
    To drop of the cache memory first check once with :\
    **free -m** or** free -g**

    \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

    **\**

11. Command to check "Number of Threads" :\
    With shell script : **for i in \`pgrep java\`; do echo \"PID: \$i,
    Count - \`ps -eLf \| grep \$i \| wc -l\`\";** done\
    or\
    Without shell script : **ps -eLf \| grep \'java\'\| wc -l**

    \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

    **\**

12. Telnet command :\
    **telnet \<ip_address\> \<port_number\>**

    \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

13. To check CPU Utilization :\
    **ps -eo pid,user,%mem,%cpu,cmd \--sort=-%cpu \| head -n 5 \>\>
    /tmp/\${uniqueid}.txt**

    \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

    **\**

14. To check Memory Utilisation :

    **ps -eo rss,%mem,%cpu,pid,user,command \--sort -rss \| awk \'{
    rss=\$1/1024; printf(\"%13.2f MB \",rss) } { for ( x=2 ; x\<=NF ;
    x++ ) { printf(\"%s \",\$x) } print \"\" }\' \| head -6 **

    \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

    \

15. **ls -lrt :**

    It can be used to list the size of files.

    \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\
