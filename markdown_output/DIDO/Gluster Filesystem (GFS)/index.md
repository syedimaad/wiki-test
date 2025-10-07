Gluster FS is a Open source file system for storage to store large scale
files. Gfs is different from normal file systems , it is a hash tag
based file system which produces speed of file reclamation when we're
actually read a file or do something with the file we get the file very
quickly.

\

GFS is a open source scale-out distribution file system which provides
client -server architecture. Where one can Scale-up or Scale-out.
Scale-up means adding some more disks for one server & Scale-out means
we have one server previously and we are adding some more servers .It
can scale up-to multiple petabytes

\

It combines the free space on the servers and gives the single unified
name space in which we can store the data. It has a layered on disk file
systems that support extended attributes.

\

**Where to use GFS..?**

GFS is based storage can be used in physical, virtual, and cloud servers
over the network.

It is used in firms to store large number of files that serve the
Internet users.

\

**Working of GFS in short.**

\

When ever a file is stored a hash tag is created and the hash tag stores
the file and when ever the file is required again by the application .
It runs the hash tag through an algorithm very quickly generally in
picoseconds or milliseconds.

\

**Gluster FS Concepts**

- ****Brick****-- Brick is basically any directory that is meant to be
  shared among the trusted storage pool.

- ****Trusted Storage Pool****-- is a collection of these shared
  files/directories, which are based on the designed protocol.

- ****Block Storage****-- They are devices through which the data is
  being moved across systems in the form of blocks.

- ****Cluster****-- In Red Hat Storage, both cluster and trusted storage
  pool convey the same meaning of collaboration of storage servers based
  on a defined protocol.

- ****Distributed File System****-- A file system in which data is
  spread over different nodes where users can access the file without
  knowing the actual location of the file. User doesn't experience the
  feel of remote access.

- ****FUSE****-- It is a loadable kernel module which allows users to
  create file systems above kernel without involving any of the kernel
  code.

- ****POSIX****-- Portable Operating System Interface (POSIX) is the
  family of standards defined by the IEEE as a solution to the
  compatibility between Unix-variants in the form of an Application
  Programmable Interface (API)

- ****Volume****-- A volumes is a logical collection of bricks. All the
  operations are based on the different types of volumes created by the
  user.

  ## Architecture {#architecture .western}

  \

  **Different types of Volumes that can be configured using Gluster FS**

  \

  - ****Distribute Volumes****:It is the default volume which is created
    when no option is specified while creating volume. In this type of
    volume files will be distributed across the the bricks using elastic
    hash algorithm

    \

  \
  \
  \

  - ****Replicate Volumes****: As the name suggests in this type of
    volume files will replicated or mirrored across the bricks , In
    other words a file which is written in one brick will also be
    replicated to another bricks

    \
    \
    \

  - ****S********triped Volumes :****In this type of volume larger files
    are cut or split into chunks and then distributed across the bricks.

    \
    \
    \
    \
    \

  - ****Distribute Replicate Volumes****: As the name suggest in type of
    volume files will be first distributed among the bricks and then
    will be replicated to different bricks.

    \

\

## TRANSLATOR {#translator .western}

[ A translator is that piece of code which performs the basic actions
initiated by the user from the mount point. It connects one or more sub
volumes.]{style="text-decoration: none;"}

## FUSE {#fuse .western}

One of the difficulties in writing code in user-space is interacting
with the kernel. In particular, a file system will likely have to
interact with the kernel VFS (Virtual File System) at some point to
access the hardware. So how does a user-space file system access the
VFS?

For a long time this was basically impossible. Any file system code had
to live in kernel space (i.e. part of the kernel or a module) and that
was the end of the story. But what do you do if, for example, you want
to automatically encrypt/decrypt the data in a file system? Or if you
want to compress/uncompress the data on a file system automatically
(this is really deduplication) giving users the ability to see the data
inside a tar file without untarring the data? Or perhaps you want to
present the data in an SQL table as a directory with associated files?
All of these things are great ideas but were unlikely to make it into
the kernel. Ideally, these file systems should live in user-space but
they still need to interact with the kernel.

Several developers decided they wanted to develop file systems or
really, virtual file systems, such as those previously mentioned, in
user space but needed some "help" from the kernel to get there. So they
created something called FUSE (**F**ile System in **USE****R**space).
The concept is to create a simple kernel module that interacts with the
kernel, particularly the VFS, on behalf of non-privileged user
applications and has an API that can be accessed from userspace.

This shows at a high level the "hello world" file system is compiled to
create a binary called "hello". This binary is executed in the upper
right hand corner of the illustration with a file system mount point of
/`tmp/fuse`{.western}. Then the user executes an
`ls -l `{.western}command against the mount point
(`ls -l /tmp/fuse`{.western}). This commands goes through *glibc* to the
VFS. The VFS then goes to the FUSE module since the mount point
corresponds to a FUSE based file system. The FUSE kernel module then
goes through *glibc* and *libfuse*(libfuse is the FUSE library in user
space) and contacts the actual file system binary ("hello"). The file
system binary returns the results back down the stack to the FUSE kernel
model, back through the VFS, and finally back to the
`ls -l `{.western}command.

\

### Overall working of GlusterFS {#overall-working-of-glusterfs .western}

As soon as GlusterFS is installed in a server node, a gluster management
daemon(glusterd) binary will be created. This daemon should be running
in all participating nodes in the cluster. After starting glusterd, a
trusted server pool(TSP) can be created consisting of all storage server
nodes (TSP can contain even a single node). Now bricks which are the
basic units of storage can be created as export directories in these
servers. Any number of bricks from this TSP can be clubbed together to
form a volume.

\

Once a volume is created, a glusterfsd process starts running in each of
the participating brick. Along with this, configuration files known as
vol files will be generated inside /var/lib/glusterd/vols/. There will
be configuration files corresponding to each brick in the volume. This
will contain all the details about that particular brick. Configuration
file required by a client process will also be created. Now our file
system is ready to use. We can mount this volume on a client machine
very easily as follows and use it like we use a local storage:

\

***mount.glusterfs \`\<IP or hostname\>\`:\`\<volume_name\>\`
\`\<mount_point\>***

\

IP or hostname can be that of any node in the trusted server pool in
which the required volume is created.

\

When we mount the volume in the client, the client glusterfs process
communicates with the servers' glusterd process. Server glusterd process
sends a configuration file (vol file) containing the list of client
translators and another containing the information of each brick in the
volume with the help of which the client glusterfs process can now
directly communicate with each brick's glusterfsd process. The setup is
now complete and the volume is now ready for client\'s service.

When a system call (File operation or Fop) is issued by client in the
mounted filesystem, the VFS (identifying the type of filesystem to be
glusterfs) will send the request to the FUSE kernel module. The FUSE
kernel module will in turn send it to the GlusterFS in the userspace of
the client node via /dev/fuse (this has been described in FUSE section).
The GlusterFS process on the client consists of a stack of translators
called the client translators which are defined in the configuration
file(vol file) sent by the storage server glusterd process. The first
among these translators being the FUSE translator which consists of the
FUSE library(libfuse). Each translator has got functions corresponding
to each file operation or fop supported by glusterfs. The request will
hit the corresponding function in each of the translators. Main client
translators include:

\

- FUSE translator

- DHT translator- DHT translator maps the request to the correct brick
  that contains the file or directory required.

- AFR translator- It receives the request from the previous translator
  and if the volume type is replicate, it duplicates the request and
  passes it on to the Protocol client translators of the replicas.

- Protocol Client translator- Protocol Client translator is the last in
  the client translator stack. This translator is divided into multiple
  threads, one for each brick in the volume. This will directly
  communicate with the glusterfsd of each brick.

\

In the storage server node that contains the brick in need, the request
again goes through a series of translators known as server translators,
main ones being:

\

- Protocol server translator

- POSIX translator

The request will finally reach VFS and then will communicate with the
underlying native filesystem. The response will retrace the same path.

\

\

\

-Nitin Raj

\
