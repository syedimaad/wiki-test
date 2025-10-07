\
Install required packages: yum-utils provides the yum-config-manager
utility, and device-mapper-persistent-data and lvm2 are required by the
devicemapper storage driver:\
[\$]{style="color: rgb(0,104,139);"}
[sudo]{style="color: rgb(101,139,0);"} [yum
install]{style="color: rgb(51,51,51);"}
[-y]{style="color: rgb(139,0,139);"}
[yum-utils]{style="color: rgb(51,51,51);"} [{color}
device-mapper-persistent-data]{style="color: rgb(205,85,85);"} [{color}\
  Lvm2]{style="color: rgb(205,85,85);"}\
Install from the repository\
a. Install the latest patch release, or go to the next step to install a
specific version:\
[\$]{style="color: rgb(0,104,139);"}
[sudo]{style="color: rgb(101,139,0);"} [yum install docker-ce
docker-ce-cli]{style="color: rgb(51,51,51);"}
[[[containerd.io]{style="text-decoration: underline;"}]{style="color: rgb(0,0,238);"}](http://containerd.io)\
b. Install a specific version by its fully qualified package name, which
is the package name (docker-ce) plus the version string (2nd column)
starting at the first colon (, up to the first hyphen, separated by a
hyphen . For example, docker-ce-19.03.11\
[\$]{style="color: rgb(0,104,139);"}
[sudo]{style="color: rgb(101,139,0);"} [yum install
docker-ce-\<VERSION_STRING\>
docker-ce-cli-\<VERSION_STRING\>]{style="color: rgb(51,51,51);"}
[[[containerd.io]{style="text-decoration: underline;"}]{style="color: rgb(0,0,238);"}](http://containerd.io)\
Example: yum install docker-ce-19.03.11 docker-ce-cli-19.03.11
[[[containerd.io]{style="text-decoration: underline;"}]{style="color: rgb(0,0,238);"}](http://containerd.io)\
Docker is installed but not started. The docker group is created, but no
users are added to the group.\
c.Start Docker. [\$]{style="color: rgb(0,104,139);"}
[sudo]{style="color: rgb(101,139,0);"} [systemctl start
docker]{style="color: rgb(51,51,51);"}\
[\$ systemctl enable docker]{style="color: rgb(0,104,139);"}\
Docker Daemon JSON \
You have to create a docker daemon json file as
/etc/docker/daemon.json:\
{\
\"insecure-registries\": \[\
\"[[[docker.dailyhunt.in]{style="text-decoration: underline;"}]{style="color: rgb(0,0,238);"}](http://docker.dailyhunt.in)\",\
\"172.20.8.62:8083\"\
\]\
}\
Now restart the docker and then login with the credentials of the Nexus
repository .
