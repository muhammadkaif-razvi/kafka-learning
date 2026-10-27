PS C:\kafka> .\bin\windows\kafka-server-start.bat config\server.properties
DEPRECATED: A Log4j 1.x configuration file has been detected, which is no longer recommended.
To use a Log4j 2.x configuration, please see https://logging.apache.org/log4j/2.x/migrate-from-log4j1.html#Log4j2ConfigurationFormat for details about Log4j configuration file migration.
You can also use the C:\kafka/config/tool-log4j2.yaml file as a starting point. Make sure to remove the Log4j 1.x configuration after completing the migration.
[2026-10-27 13:27:09,172] INFO Registered `kafka:type=kafka.Log4jController` MBean (kafka.utils.Log4jControllerRegistration$)
[2026-10-27 13:27:09,710] INFO [ControllerServer id=1] Starting controller (kafka.server.ControllerServer)
[2026-10-27 13:27:10,320] INFO Updated connection-accept-rate max connection creation rate to 2147483647 (kafka.network.ConnectionQuotas)
[2026-10-27 13:27:10,436] INFO [SocketServer listenerTyp

PS C:\kafka> .\bin\windows\kafka-topics.bat --bootstrap-server localhost:9092 --create --topic orders --partitions 3 --replication-factor 1
2026-10-27T07:57:57.792047300Z main ERROR Reconfiguration failed: No configuration found for '2c7b84de' at 'null' in 'null'
Created topic orders.
PS C:\kafka> .\bin\windows\kafka-topics.bat --bootstrap-server localhost:9092 --describe --topic orders
2026-10-27T07:58:24.265842300Z main ERROR Reconfiguration failed: No configuration found for '2c7b84de' at 'null' in 'null'
Topic: orders   TopicId: 8ffQxYWWT9usk3fED9OlWA PartitionCount: 3       ReplicationFactor: 1    Configs: min.insync.replicas=1,segment.bytes=1073741824
Topic: orders   Partition: 0    Leader: 1       Replicas: 1     Isr: 1  Elr:    LastKnownElr:
Topic: orders   Partition: 1    Leader: 1       Replicas: 1     Isr: 1  Elr:    LastKnownElr:
Topic: orders   Partition: 2    Leader: 1       Replicas: 1     Isr: 1  Elr:    LastKnownElr:
PS C:\kafka>

PS C:\kafka> .\bin\windows\kafka-console-producer.bat --bootstrap-server localhost:9092 --topic orders --property parse.key=true --property key.separator=:
Warning: --property is deprecated and will be removed in a future version. Use --reader-property instead.
2026-10-27T08:05:23.180931500Z main ERROR Reconfiguration failed: No configuration found for '2c7b84de' at 'null' in 'null'
>cust-1:created
cust-4:created
cust-6:created
cust-42:created
cust-1:paid
cust-4:paid
cust-6:paid
cust-42:paid
>>>>>>>>cust-1:shipped
> PS C:\kafka> .\bin\windows\kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic orders --from-beginning --property print.partition=true --property print.offset=true --property print.key=true
2026-10-27T08:07:20.338291100Z main ERROR Reconfiguration failed: No configuration found for '2c7b84de' at 'null' in 'null'
Option --property is deprecated and will be removed in a future version. Use --formatter-property instead.
The consumer rebalance protocol (KIP-848) is production-ready! Set group.protocol=consumer to try it out. See https://kafka.apache.org/documentation/#consumer_rebalance_protocol
Partition:0     Offset:0        cust-1  created
Partition:0     Offset:1        cust-4  created
Partition:0     Offset:2        cust-6  created
Partition:0     Offset:3        cust-42 created
Partition:0     Offset:4        cust-1  paid
Partition:0     Offset:5        cust-4  paid
Partition:0     Offset:6        cust-6  paid
Partition:0     Offset:7        cust-42 paid
Partition:0     Offset:8        cust-1  shipped


PS C:\kafka> .\bin\windows\kafka-console-producer.bat --bootstrap-server localhost:9092 --topic orders --property parse.key=true --property key.separator=:
Warning: --property is deprecated and will be removed in a future version. Use --reader-property instead.
2026-10-27T08:05:23.180931500Z main ERROR Reconfiguration failed: No configuration found for '2c7b84de' at 'null' in 'null'
>cust-1:created
cust-4:created
cust-6:created
cust-42:created
cust-1:paid
cust-4:paid
cust-6:paid
cust-42:paid
>>>>>>>>cust-1:shipped
>