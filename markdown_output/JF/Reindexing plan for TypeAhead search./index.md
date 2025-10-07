Below is index information

+-----------------+-----------+----------+-------------+----------+-----------------+
| **index Alias** | **Primary | **Total  | **Approx    | **Approx | **Plan to       |
|                 | Shard     | size**   | Disk space  | Extra    | change on       |
|                 | size**    |          | required    | memory   | prod.**         |
|                 |           |          | for         | required |                 |
|                 |           |          | Reindex**   | on Heap  |                 |
|                 |           |          |             | for      |                 |
|                 |           |          |             | FST**    |                 |
+-----------------+-----------+----------+-------------+----------+-----------------+
|                 |           |          |             |          |                 |
+-----------------+-----------+----------+-------------+----------+-----------------+
| - `ugc-users`   | 96GB      | 200Gb    | 300Gb (100  | 5-6 GB   | - increase size |
|                 |           |          | gb extra    |          |   of cluster in |
|                 |           |          | for         |          |   running mode. |
|                 |           |          | temporary   |          |                 |
|                 |           |          | space       |          | - Stop Write on |
|                 |           |          | requirement |          |   elastic       |
|                 |           |          | for         |          |   cluster.      |
|                 |           |          | reindexing) |          |                 |
|                 |           |          |             |          | - Reindex data  |
|                 |           |          |             |          |   to new index. |
|                 |           |          |             |          |                 |
|                 |           |          |             |          | - change alias. |
|                 |           |          |             |          |                 |
|                 |           |          |             |          | - start write   |
|                 |           |          |             |          |   on new index  |
|                 |           |          |             |          |   from back     |
|                 |           |          |             |          |   store(dynamo) |
|                 |           |          |             |          |                 |
|                 |           |          |             |          | - start write   |
|                 |           |          |             |          |   and read to   |
|                 |           |          |             |          |   new index.    |
|                 |           |          |             |          |                 |
|                 |           |          |             |          | - if things are |
|                 |           |          |             |          |   fine, Drop    |
|                 |           |          |             |          |   the old       |
|                 |           |          |             |          |   index.        |
+-----------------+-----------+----------+-------------+----------+-----------------+
| - ugc-hashtag   | 10.31 GB  | 21GB     | 30GB        | 400MB    | As above        |
+-----------------+-----------+----------+-------------+----------+-----------------+
| - josh-zones    |           |          |             |          |                 |
+-----------------+-----------+----------+-------------+----------+-----------------+
| - ugc-challenge | 1.40GB    | approx 3 | 4.5 GB      |          |                 |
|                 |           | GB       |             |          |                 |
+-----------------+-----------+----------+-------------+----------+-----------------+
| - ugc-contests  |           |          |             |          |                 |
+-----------------+-----------+----------+-------------+----------+-----------------+
