\

\

- [**KEY TUNING PARAMETERS IN APACHE :**]{style="color: rgb(128,0,0);"}\
  [**\**
  ]{style="color: rgb(0,51,102);"}
  1.  [**Timeout** : Amount of time server waits before failing a
      request.]{style="color: rgb(0,51,102);"}

  2.  [**KeepAlive** : Provide long-lived http sessions which allow
      multiple requests to be sent over the same tcp connection, hence
      increasing performance.]{style="color: rgb(0,51,102);"}

  3.  [**MaxKeepAliveRequest** : Sets Upper limit on
      KeepAlive.]{style="color: rgb(0,51,102);"}

  4.  [**KeepAliveTimeout** : It represents the number of seconds Apache
      will wait for subsequent request before closing
      connection.]{style="color: rgb(0,51,102);"}

  5.  [**StartServers** : Controls number of child processes/threads
      created on startup.]{style="color: rgb(0,51,102);"}

  6.  [**ThreadsPerChild** : Mentions the number of threads created by
      each child process.]{style="color: rgb(0,51,102);"}

  7.  [**ThreadLimit** : Sets upper limit on ThreadsPerChild
      process.]{style="color: rgb(0,51,102);"}

  8.  [**MaxClient** : It directly impacts the number of concurrent
      connections that can be
      established.]{style="color: rgb(0,51,102);"}

  9.  [**ServerLimit** : Sets maximum configured value for MaxClient.
      (For example : if ServerLimit = 10; ThreadLimit = 10; MaxClient =
      100).]{style="color: rgb(0,51,102);"}

  10. [**MaxRequestPerChild** : Limits number of requests that an
      individual child server process
      handles.]{style="color: rgb(0,51,102);"}

      \

- [**APACHE BENCHMARKING TOOL(AB) :\**
  ]{style="color: rgb(128,0,0);"}

  [Apache Bench (ab) is a common tool for measuring the performance of
  HTTP servers in a Linux environment. It works by generating a flood of
  requests to a given URL and returns some easily digestible performance
  related metrics to the screen. This simplicity makes it appealing for
  running quick and dirty load tests, and a nice benefit to uncovering
  limits in your web stack or a service bottleneck that you did not
  anticipate.]{style="color: rgb(0,51,102);"}

  [This tool would help us answer some questions like below
  :]{style="color: rgb(0,51,102);"}

  [**What is my application's average response time at a large number of
  simultaneous users or connections?**]{style="color: rgb(0,51,102);"}

  [**What is the maximum number of requests-per-second that my
  application can handle?**]{style="color: rgb(0,51,102);"}

  [[Example query :]{.underline}[ ab -n 1000 -c 10
  http://\<ip_address\>]{style="text-decoration: none;"}]{style="color: rgb(0,51,102);"}

  [Here, n : number of requests]{style="color: rgb(0,51,102);"}

  [c : concurrency in serving the
  requests]{style="color: rgb(0,51,102);"}

  \

- [**VIRTUAL HOSTS APACHE :**]{style="color: rgb(128,0,0);"}

  [Virtual hosting is a method for hosting multiple websites (domains)
  on a single server. You can host multiple websites on a single machine
  with a single IP using virtual hosting. All domains on that server
  will be sharing a single IP. Virtual hosting is very useful in shared
  web hosting environments, where hundreds of websites are hosted on a
  single dedicated server.]{style="color: rgb(0,51,102);"}

  [[**HOW TO CONFIGURE VIRTUAL HOSTS IN APACHE
  ;**]{.underline}]{style="color: rgb(0,51,102);"}

  [**[\]{.underline}**
  ]{style="color: rgb(0,51,102);"}

  1.  [[Create the directory structure (which will hold the web pages)
      in the Apache document root directory, which by default is
      ]{style="text-decoration: none;"}[/var/www/html/]{style="text-decoration: none;"}]{style="color: rgb(0,51,102);"}

      [**[mkdir -p
      /]{style="text-decoration: none;"}[usr]{style="text-decoration: none;"}[/]{style="text-decoration: none;"}[local]{style="text-decoration: none;"}[/]{style="text-decoration: none;"}[apache2]{style="text-decoration: none;"}[/]{style="text-decoration: none;"}[htdocs]{style="text-decoration: none;"}[/[[www.vhost1.com]{style="color: rgb(0,51,102);"}](http://www.vhost1.com)]{style="text-decoration: none;"}**]{style="color: rgb(0,51,102);"}

  2.  [Now, create the test web page for the virtual host
      created]{style="color: rgb(0,51,102);"}

      [**[vi
      //]{style="text-decoration: none;"}[usr]{style="text-decoration: none;"}[/]{style="text-decoration: none;"}[local]{style="text-decoration: none;"}[/]{style="text-decoration: none;"}[apache2]{style="text-decoration: none;"}[/]{style="text-decoration: none;"}[htdocs]{style="text-decoration: none;"}[/[[www.vhost1.com/]{style="color: rgb(0,51,102);"}](http://www.vhost1.com/)]{style="text-decoration: none;"}[index.html]{style="text-decoration: none;"}**]{style="color: rgb(0,51,102);"}

      [And design the test web page in
      html]{style="color: rgb(0,51,102);"}

  3.  [Now set the required ownership and
      permissions]{style="color: rgb(0,51,102);"}

      [[ ]{style="text-decoration: none;"}[**chown -R apache:apache
      /**]{style="text-decoration: none;"}[**usr**]{style="text-decoration: none;"}[**/**]{style="text-decoration: none;"}[**local**]{style="text-decoration: none;"}[**/**]{style="text-decoration: none;"}[**apache2**]{style="text-decoration: none;"}[**/**]{style="text-decoration: none;"}[**htdocs**]{style="text-decoration: none;"}[**/[[www.vhost1.com]{style="color: rgb(0,51,102);"}](http://www.vhost1.com)**]{style="text-decoration: none;"}]{style="color: rgb(0,51,102);"}

      [[ **chmod -**]{style="text-decoration: none;"}[**R**
      ]{style="text-decoration: none;"}[**755
      /**]{style="text-decoration: none;"}[**usr**]{style="text-decoration: none;"}[**/**]{style="text-decoration: none;"}[**local**]{style="text-decoration: none;"}[**/**]{style="text-decoration: none;"}[**apache2**]{style="text-decoration: none;"}[**/**]{style="text-decoration: none;"}[**htdocs**]{style="text-decoration: none;"}]{style="color: rgb(0,51,102);"}

  4.  [Now, create the virtual host configuration
      files]{style="color: rgb(0,51,102);"}

      [**vi
      /usr/local/apache2/conf/vhosts/[[vhost1.com]{style="color: rgb(0,51,102);"}](http://vhost1.com).conf**]{style="color: rgb(0,51,102);"}

      [Add the following content to it :]{style="color: rgb(0,51,102);"}

      [**\<VirtualHost \*:80\>**]{style="color: rgb(0,51,102);"}

      [**ServerName
      [[www.vhost1.com]{style="color: rgb(0,51,102);"}](http://www.vhost1.com)**]{style="color: rgb(0,51,102);"}

      [**ServerAlias
      [[vhost1.com]{style="color: rgb(0,51,102);"}](http://vhost1.com)**]{style="color: rgb(0,51,102);"}

      [**[DocumentRoot
      ]{style="text-decoration: none;"}[/]{style="text-decoration: none;"}[usr]{style="text-decoration: none;"}[/]{style="text-decoration: none;"}[local]{style="text-decoration: none;"}[/]{style="text-decoration: none;"}[apache2]{style="text-decoration: none;"}[/]{style="text-decoration: none;"}[htdocs]{style="text-decoration: none;"}[/[[www.vhost1.com]{style="color: rgb(0,51,102);"}](http://www.vhost1.com)]{style="text-decoration: none;"}**]{style="color: rgb(0,51,102);"}

      [**[ErrorLog
      ]{style="text-decoration: none;"}[/]{style="text-decoration: none;"}[usr]{style="text-decoration: none;"}[/]{style="text-decoration: none;"}[local]{style="text-decoration: none;"}[/]{style="text-decoration: none;"}[apache2]{style="text-decoration: none;"}[/]{style="text-decoration: none;"}[htdocs]{style="text-decoration: none;"}[/[[www.vhost1.com/]{style="color: rgb(0,51,102);"}](http://www.vhost1.com/)]{style="text-decoration: none;"}[error.log]{style="text-decoration: none;"}**]{style="color: rgb(0,51,102);"}

      [**[CustomLog
      ]{style="text-decoration: none;"}[/]{style="text-decoration: none;"}[usr]{style="text-decoration: none;"}[/]{style="text-decoration: none;"}[local]{style="text-decoration: none;"}[/]{style="text-decoration: none;"}[apache2]{style="text-decoration: none;"}[/]{style="text-decoration: none;"}[htdocs]{style="text-decoration: none;"}[/[[www.vhost1.com]{style="color: rgb(0,51,102);"}](http://www.vhost1.com)]{style="text-decoration: none;"}[/access.log
      common]{style="text-decoration: none;"}**]{style="color: rgb(0,51,102);"}

      [**\</VirtualHost\>**]{style="color: rgb(0,51,102);"}

  5.  [Also, mention the ip address of server and the domain name on the
      machine where you want to access the hosts in /etc/hosts
      file]{style="color: rgb(0,51,102);"}

  6.  [Restart httpd service and load the virtual hosts on the web
      server]{style="color: rgb(0,51,102);"}

::: {}
[\
]{style="color: rgb(0,51,102);"}
:::

::: {}
[\
]{style="color: rgb(0,51,102);"}
:::

::: {}
[-Seren Jhanwar]{style="color: rgb(0,51,102);"}
:::

\

\

\

\
