### Problem Statement

Issues with the scalability of the current index

### DiskANN

DiskANN is a suite of scalable, accurate, and cost-effective approximate
nearest neighbor search algorithms for large-scale vector searches that
support real-time changes and simple filters.

Repo:
[https://github.com/microsoft/DiskANN](https://github.com/microsoft/DiskANN){card-appearance="inline"}

#### Indexes Supported

1.  SSD index

2.  In-memory index

Disk supports a static index to be built without the functionalities of
inserts, updates, and deletions.

In-memory index is a dynamic index that supports inserts, deletes,
updates, and filters.

One of the caveats while building the in-memory index is the need to
specify the maximum vectors the index can hold.

### Index Benchmarks

Server Configuration -

- Ram - 185 gigs

- 48 cores

We tried doing a POC with the in-memory index as we wanted the index to
be dynamic in nature and support inserts, deletes, and filters.

The experiments were run with 15 million vectors of different dimensions
(32,256,1024). For dynamic in memory indices we need to specify maximum
vectors that the index needs to hold. Following are the observations
that were made.

32 dimensions (Capacity of index 100 Million)

- takes \~13.5 minutes to build index.

- takes nearly \~20 gigs in memory.

- Takes 175 seconds to save. Disk Space \~3.4 gigs. takes nearly 20
  seconds to load.

- Batch search of 10k items took \~0.5 seconds.

- Consolidated delete of 10,000 vectors took \~15 secs.

256 dimensions (Capacity of index 100 Million)

- takes \~40 minutes to build index.

- takes nearly \~105 gigs in memory.

- Takes 400 seconds to save. Disk Space \~17 gigs. takes nearly 75
  seconds to load.

- Batch search of 10k items took \~1 seconds.

- Consolidated delete of 10,000 vectors took \~45 secs.

1024 dimensions (Capacity of index 30 Million)

- takes \~85 minutes to build index.

- takes nearly \~120 gigs in memory.

- Takes 690 seconds to save. Disk Space \~60 gigs. takes nearly 551
  seconds to load.

- Batch search of 10k items took \~2.65 seconds.

- Consolidated delete of 10,000 vectors took \~151 secs.
