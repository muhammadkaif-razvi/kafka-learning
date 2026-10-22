PS C:\projects\kafka-learning\day1> docker compose up -d
[+] up 3/3
✔ Network day1_default Created                                                                     0.1s
✔ Container kafka      Started                                                                     1.1s
✔ Container kafka-ui   Started                                                                     1.3s
PS C:\projects\kafka-learning\day1> docker compose ps
NAME       IMAGE                    COMMAND                  SERVICE    CREATED          STATUS          PORTS
kafka      apache/kafka:4.3.1       "/__cacert_entrypoin…"   kafka      12 seconds ago   Up 11 seconds   0.0.0.0:9092->9092/tcp, [::]:9092->9092/tcp
kafka-ui   kafbat/kafka-ui:latest   "/bin/sh -c 'java --…"   kafka-ui   12 seconds ago   Up 10 seconds   0.0.0.0:8080->8080/tcp, [::]:8080->8080/tcp
PS C:\projects\kafka-learning\day1> docker exec -it kafka /opt/kafka/bin/kafka-topics.sh --bootstrap-server localhost:9092 --create --topic hello-kafka --partitions 3 --replication-factor 1
Created topic hello-kafka.

What's next:
Try Docker Debug for seamless, persistent debugging tools in any container or image → docker debug kafka
Learn more at https://docs.docker.com/go/debug-cli/
PS C:\projects\kafka-learning\day1> docker exec -it kafka /opt/kafka/bin/kafka-topics.sh --bootstrap-server localhost:9092 --list
hello-kafka

What's next:
Try Docker Debug for seamless, persistent debugging tools in any container or image → docker debug kafka
Learn more at https://docs.docker.com/go/debug-cli/
PS C:\projects\kafka-learning\day1> docker exec -it kafka /opt/kafka/bin/kafka-topics.sh --bootstrap-server localhost:9092 --describe --topic hellp-kafka
Error while executing topic command : Topic 'hellp-kafka' does not exist as expected
[2026-10-22 08:12:56,863] ERROR java.lang.IllegalArgumentException: Topic 'hellp-kafka' does not exist as expected
at org.apache.kafka.tools.TopicCommand.ensureTopicExists(TopicCommand.java:207)
at org.apache.kafka.tools.TopicCommand$TopicService.describeTopic(TopicCommand.java:547)
at org.apache.kafka.tools.TopicCommand.execute(TopicCommand.java:111)
at org.apache.kafka.tools.TopicCommand.mainNoExit(TopicCommand.java:90)
at org.apache.kafka.tools.TopicCommand.main(TopicCommand.java:85)
(org.apache.kafka.tools.TopicCommand)

What's next:
Try Docker Debug for seamless, persistent debugging tools in any container or image → docker debug kafka
Learn more at https://docs.docker.com/go/debug-cli/
PS C:\projects\kafka-learning\day1> docker exec -it kafka /opt/kafka/bin/kafka-topics.sh --bootstrap-server localhost:9092 --describe --topic hello-kafka
Topic: hello-kafka      TopicId: 1n_ZCgiDRqGshTz6i_FRwA PartitionCount: 3       ReplicationFactor: 1   Configs: min.insync.replicas=1
Topic: hello-kafka      Partition: 0    Leader: 1       Replicas: 1     Isr: 1  Elr:    LastKnownElr:
Topic: hello-kafka      Partition: 1    Leader: 1       Replicas: 1     Isr: 1  Elr:    LastKnownElr:
Topic: hello-kafka      Partition: 2    Leader: 1       Replicas: 1     Isr: 1  Elr:    LastKnownElr:

What's next:
Try Docker Debug for seamless, persistent debugging tools in any container or image → docker debug kafka
Learn more at https://docs.docker.com/go/debug-cli/
PS C:\projects\kafka-learning\day1> docker exec -it kafka /opt/kafka/bin/kafka-console-producer.sh --bootstrap-server localhost:9092 --topic hello-kafka
>biryani order from tolichowki
>irani chai X2 from chairminar
>mandi pre-order
>^C^C
What's next:
Try Docker Debug for seamless, persistent debugging tools in any container or image → docker debug kafka
Learn more at https://docs.docker.com/go/debug-cli/
PS C:\projects\kafka-learning\day1> docker exec -it kafka /opt/kafka/bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic hello-kafka
The consumer rebalance protocol (KIP-848) is production-ready! Set group.protocol=consumer to try it out. See https://kafka.apache.org/documentation/#consumer_rebalance_protocol
l
kfakl
mandi
biryani
qurbani ka meetha
sawarma
campa
2 waterbotel


PS C:\WINDOWS\system32> docker exec -it kafka /opt/kafka/bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic hello-kafka --from-beginning --property print.partition=true --property print.offset=true
Option --property is deprecated and will be removed in a future version. Use --formatter-property instead.
The consumer rebalance protocol (KIP-848) is production-ready! Set group.protocol=consumer to try it out. See https://kafka.apache.org/documentation/#consumer_rebalance_protocol
Partition:1     Offset:0        biryani order from tolichowki
Partition:1     Offset:1        irani chai X2 from chairminar
Partition:1     Offset:2        mandi pre-order
Partition:0     Offset:0        kfakl
Partition:0     Offset:1        mandi
Partition:0     Offset:2        biryani
Partition:0     Offset:3        qurbani ka meetha
Partition:0     Offset:4        sawarma
Partition:0     Offset:5        campa
Partition:0     Offset:6        2 waterbotel
S C:\WINDOWS\system32> docker exec -it kafka /opt/kafka/bin/kafka-consumer-groups.sh --bootstrap-server localhost:9092 --list
console-consumer-77674
console-consumer-88625

What's next:
Try Docker Debug for seamless, persistent debugging tools in any container or image → docker debug kafka
Learn more at https://docs.docker.com/go/debug-cli/
PS C:\WINDOWS\system32> docker run -d --name kafka-ui -p 8080:8080 -e KAFKA_CLUSTERS_0_NAME=local -e KAFKA_CLUSTERS_0_BOOTSTRAPSERVERS=host.docker.internal:9092 kafbat/kafka-ui:latest
docker: Error response from daemon: Conflict. The container name "/kafka-ui" is already in use by container "842b306afcdf447fa769628ddc18799ced34785ec5ab131625ed86563c0fd8d9". You have to remove (or rename) that container to be able to reuse that name.

Run 'docker run --help' for more information

What's next:
Debug this container error with Gordon → docker ai "help me fix this container error"
PS C:\WINDOWS\system32> docker exec -it kafka /opt/kafka/bin/kafka-console-producer.sh --bootstrap-server localhost:9092 --topic hello-kafka
kf>akl
>mandi
>biryani
>qurbani ka meetha
>sawarma
>campa
>2 waterbotel
>


