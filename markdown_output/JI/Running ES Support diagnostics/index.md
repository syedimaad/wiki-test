Tool
[https://github.com/elastic/support-diagnostics](https://github.com/elastic/support-diagnostics){card-appearance="inline"}
is shared by Elasticsearch Support team to run diagnostics on ES
clusters. This diagnostics data is useful for knowing Elasticsearch
license usage.

This document describe how to run this tool and collect the diagnostics
data:

### Pre-Requisites for running the tool:

- JDK - Oracle or OpenJDK, 1.8-13.

  - The IBM JDK is not supported due to JSSE related issues that can
    cause TLS errors.

  - **Important Note For Elasticsearch Version 7:** Elasticsearch now
    includes a bundled JVM that is used by default. For the diagnostic
    to retrieve thread dumps via `Jstack` it must be executed with the
    same JVM that was used to run Elasticsearch. The diagnostic utility
    will attempt to find the location of the JVM that was used to run
    the process it is interrogating. If it is unable to do so, you may
    need to manually configure the location by setting `JAVA_HOME` to
    the directory containing the `/bin` directory for the included JDK.
    For example,
    `<path to Elasticsearch 7 deployment>/jdk/Contents/Home`.

- The system user account for that host(not the elasticsearch login)
  must have sufficient authorization to run these commands and access
  the logs (usually in `/var/log/elasticsearch`) in order to obtain a
  full collection of diagnostics.

- If you are authenticating using the built in Security, the supplied
  user id must have permission to execute the diagnostic URL\'s. The
  superuser role is recommended unless you are familiar enough with the
  calls being made to tailor your own accounts and roles.

### Instructions

We run this tool from outside the Elasticsearch cluster (i.e. remotely).

1.  Login to a server with Java installed or install Java on the machine
    where this tool needs to be run.

2.  Download and unzip the latest version of the tool to a directory
    path. Please use the zip file names `-dist.zip` when downloading the
    latest version from
    [https://github.com/elastic/support-diagnostics/releases](https://github.com/elastic/support-diagnostics/releases){card-appearance="inline"}\

    bashwget
    \"https://github.com/elastic/support-diagnostics/releases/download/v8.4.1/diagnostics-8.4.1-dist.zip\"
    unzip diagnostics-8.4.1-dist.zip

3.  Execute the diagnostics script as follows:\

    bashsudo ./diagnostics.sh \--host qa-eck.myjosh.in \--port 9200 -u
    \"elastic\" -p \--ssl

4.  This will create a zip file package with diagnostics data\

    bashArchiving diagnostic results. Archive:
    /root/diagnostics-8.4.1/local-diagnostics-20230215-100603.zip was
    created Deleted directory:
    /root/diagnostics-8.4.1/local-diagnostics. \[root@ip-10-14-8-69
    diagnostics-8.4.1\]# ls -ltrh
    /root/diagnostics-8.4.1/local-diagnostics-20230215-100603.zip
    -rw-r\--r\-- 1 root root 1.4M Feb 15 10:06
    /root/diagnostics-8.4.1/local-diagnostics-20230215-100603.zip

5.  Copy the file to share for the cluster.
