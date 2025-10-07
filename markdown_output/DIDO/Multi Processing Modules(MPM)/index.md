\

Apache 2 introduced Multi-Processing Modules, or MPMs. The MPMs change
the basic functionality of the web server. They do this by modifying how
Apache listens to the network, accepts, and handles requests.

Apache may broadly work in two different ways :

\

- **MPM Prefork :**

  With the Prefork module installed, Apache is a non-threaded,
  pre-forking web server. That means that each Apache child process
  contains a single thread and handles one request at a time. Because of
  that, it consumes more resources than the threaded MPMs: Worker and
  Event.

  Prefork is the default MPM, so if no MPM is selected in EasyApache,
  Prefork will be selected. It still is the best choice if Apache has to
  use non-thread safe libraries such as mod_php (DSO), and is ideal if
  isolation of processes is important.

\

- **MPM Worker :**

  In this mode, Apache works more or less like Nginx.

  This Multi-Processing Module (MPM) implements a hybrid multi-process
  multi-threaded server. By using threads to serve requests, it is able
  to serve a large number of requests with fewer system resources than a
  process-based server.

  **Despite MPM worker being more efficient than MPM prefork, when the
  server is under heavy load, it is usually not installed, because
  mod_php** (helps in live monitoring of web server) **can\'t work with
  MPM worker.**

  **\**

- **MPM Event :**

  Each process under Event also can contain multiple threads but, unlike
  Worker, each is capable of more than one task. Apache has the lowest
  resource requirements when used with the Event MPM.

  MPM Event is supported only on servers running Apache 2.4.

\

\

[-Seren Jhanwar]{style="color: rgb(0,51,102);"}

\
