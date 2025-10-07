# Aim

The aim of the document is to capture the current state of the problem
with location service and the way ahead for the service going forward

#  Problems with location service

- Client connections reaching limits issues with Redis. The number of
  client connections gets increased because of the uneven distribution
  of the data and Redis not being behind a sentinel. There is a
  one-to-one mapping of VMs to Redis.

- One-to-one mapping of location service VM to Redis nodes. **TODO**:  
  Request you to list down the mapping of the VMs to the Redis instance

Currently, we have 5 Redis nodes and it is not behind a sentinel. There
is a one-to-one mapping of serving VM to Redis nodes and this causes
multiple problems like uneven distribution of data, inefficient use of
Redis, and increased client connections on few nodes resulting in
alerts.

- We are facing a problem with location discrepancy which requires data
  to be updated with existing granularity

- With new requirements w.r.t Public Vibe we might want to enhance the
  granularity of the location service by adding Display Name, name in
  multiple languages, etc.

- Limitations in terms of traffic handling. Currently, location service
  handles an RPS of 1600 being handled by 8 VMs. This looks suboptimal
  keeping in mind we are just doing lookups in Redis under the hood

- Location service just uses 1 CPU, since it runs as one process with
  multiple threads to service the request and we are not utilizing the
  machine properly. CPU utilization is under 7-10% almost all of the
  time. We are not using the memory of the machine and have allocated
  good enough memory as well.

# Future Potential requirements

- We have a requirement to pass on location details with more
  granularity like Pincode, the display name of a city, name of the city
  in multiple languages.

- Since we have kept all location data non-normalized, it is a costly
  operation to update the name of the city in the underlying database.
  (It is manageable though but not optimal). Example: Recently there is
  a change in 13 City/District names in AP

- \[Minor\] Location service is implemented in Java 1.7 and Gradel 2.3.
  It might require maintenance over the near to long term. Since we are
  moving towards Go for serving layers, the team has an inclination to
  have the same stack. This will help the utilization of resources if
  needed. We now also have experience with Go given for S2S we are
  already in production.

# Decision w.r.t rewrite

Based on the above problems and future requirements we think that it is
better to rewrite location service. We are favoring GoLang over Java,
the reason for that is s2s devs are very familiar with GoLang and we
have implemented it at scale in S2S so we can say that it is
battle-tested at scale for us and we think that it is better to re-write
in GoLang than to refactor in Java.

\
