There was a problem on `dh-gcp-ads-analyticsnrt-kafka-n2.dailyhunt.in`
VM kafka server process in the morning, starting 5:55 AM. These were the
ERROR logs during the time.

`[2022-05-03 05:55:59,025] ERROR [ReplicaFetcher replicaId=2, leaderId=6, fetcherId=0] Found invalid messages during fetch for partition appsProcessingQueue-20 offset 1372775496 (kafka.server.ReplicaFetcherThread)`\
`org.apache.kafka.common.errors.CorruptRecordException: Record is corrupt (stored crc = 89914008) in topic partition appsProcessingQueue-20.`

`[2022-05-03 06:01:56,590] ERROR [ReplicaFetcher replicaId=2, leaderId=8, fetcherId=0] Found invalid messages during fetch for partition oxImpQueue-3 offset 42911177258 (kafka.server.ReplicaFetcherThread)`\
`org.apache.kafka.common.errors.CorruptRecordException: Record is corrupt (stored crc = 2482765824) in topic partition oxImpQueue-3.`

`[2022-05-03 06:03:38,083] ERROR [ReplicaFetcher replicaId=2, leaderId=4, fetcherId=0] Unexpected error occurred while processing data for partition reqmessages-3 at offset 5661575540 (kafka.server.ReplicaFetcherThread)`\
`org.apache.kafka.common.errors.OffsetOutOfRangeException: Cannot increment the log start offset to 8459296551737491457 of partition reqmessages-3 since it is larger than the high watermark 5661545061`

`[2022-05-03 06:03:38,086] WARN [ReplicaFetcher replicaId=2, leaderId=4, fetcherId=0] Partition reqmessages-3 marked as failed (kafka.server.ReplicaFetcherThread)`

`[2022-05-03 06:05:39,917] ERROR Closing socket for 10.50.16.4:9092-10.50.0.78:51094-2677341 because of error (kafka.netwo`\
`rk.Processor)`\
`org.apache.kafka.common.errors.InvalidRequestException: Error parsing request header. Our best guess of the apiKey is: 0`\
`Caused by: java.nio.BufferUnderflowException`\
`        at java.nio.HeapByteBuffer.get(HeapByteBuffer.java:151)`\
`        at java.nio.ByteBuffer.get(ByteBuffer.java:715)`

`...`

There was some transient error (mostly network related, but
unconfirmed). Most of the topic-partitions recovered automatically, but
due to the size of reqmessages topic-partition, it could not recover in
time, because the high watermark threshold hit. So the partition was
marked as failed, and the kafka server did not attempt to recover it.
Manually running the *kafka-reassign-partitions tool* fixed the
under-replication.

Nothing abnormal from the system monitoring side (saluber grafana, GCP),
so no clue on what caused it.
