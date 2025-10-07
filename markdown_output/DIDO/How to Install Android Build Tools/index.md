Login into Jenkins Machine(192.168.10.70) and become root user.

1\. Enter into android tools directory and List all available builds.

bash# cd /opt/android-sdk-linux/tools \# android list sdk \--all

\

[2. Choose number which version you want to install. For example, to
install version 27.0.3, 27.0.2 and 27.0.1, follow the below
steps.]{style="color: rgb(85,85,85);"}

bash# android update sdk -a -u -t 4,5,6

[3. [Verify whether the tools is installed or not in the build-tools
directory.]{style="color: rgb(85,85,85);"}]{style="color: rgb(85,85,85);"}

bash# cd /opt/android-sdk-linux/build-tools \# ls \[root@build1
build-tools\]# ls 17.0.0 18.1.0 19.0.0 19.0.2 19.1.0 21.0.0 21.0.2
21.1.1 22.0.0 23.0.1 23.0.3 24.0.1 25.0.0 25.0.3 26.0.2 27.0.2 18.0.1
18.1.1 19.0.1 19.0.3 20.0.0 21.0.1 21.1.0 21.1.2 22.0.1 23.0.2 24.0.0
24.0.2 25.0.2 26.0.1 27.0.1 27.0.3

[\
]{style="color: rgb(85,85,85);"}
