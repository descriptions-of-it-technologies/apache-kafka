# Kafka Terminal Commands.

## Topic.
* `/bin/kafka-topics.sh --bootstrap-server localhost:9092 --list`
* `/bin/kafka-topics.sh --bootstrap-server localhost:9092 --create --topic Orders`
* `/bin/kafka-topics.sh --bootstrap-server localhost:9092 --create --topic Orders --config max.message.bytes=10485760`
* `kafka-topics --bootstrap-server localhost:9092 --create --topic aa2 --partitions 3 --replication-factor 3`
* `/bin/kafka-topics.sh --bootstrap-server localhost:9092 --describe`
* `/bin/kafka-topics.sh --bootstrap-server localhost:9092 --describe --topic Order`
* `/bin/kafka-topics.sh --bootstrap-server localhost:9092 --delete --topic Order`
* `kafka-topics --bootstrap-server localhost:9092 --create --topic compaction-topic --partitions 1 --replication-factor 1 --config cleanup.policy=compact --config min.cleanable.dirty.ratio=0.001 --config segment.ms=5000`



## Topics. Deprecated option `--zookeeper`
* `/bin/kafka-topics.sh --create --zookeeper [zookeeperHost:port, zookiperHost:port] --replication-factor 3 --partitions 3 --topic hello-world` - create topic
* `/bin/kafka-topics.sh --list --zookeeper [zookeeperHost:port, zookiperHost:port]` - list topics
* `/bin/kafka-topics.sh --describe --topic hello-world --zookeeper [zookeeperHost:port, zookiperHost:port]` - describe topic
* `/bin/kafka-topics.sh --zookeeper [zookeeperHost:port, zookiperHost:port] --delete --topic hello-world` - delete topic



## Producer.
* `/bin/kafka-console-producer --broker-list [kafkaHost:port;kafkaHost:port] --topic hello-world` - create producer
* `/bin/kafka-console-producer --bootstrap-server localhost:9092 --topic hello-world JSON`

* `/bin/kafka-console-producer --broker-list [kafkaHost:port;kafkaHost:port] --topic hola-mundo --property parse.key=true --property key.separator=":"`
* `kafka-console-producer --broker-list 127.0.0.1:9092 --topic first_topic --property parse.key=true --property key.separator=","`

* `kafka-console-producer --broker-list localhost:9092 --topic aaa --producer-property acks=all` 



## Consumer.
* `/bin/kafka-console-consumer --bootstrap-server [kafkaHost:port;kafkaHost:port] --topic hello-world` - create consumer
* `/bin/kafka-console-consumer --bootstrap-server localhost:9092 --topic hello-world`
* `/bin/kafka-console-consumer --bootstrap-server localhost:9092 --topic hello-world --from-beginning`
* `/bin/kafka-console-consumer --bootstrap-server localhost:9092 --topic hello-world --group nameGroup`

* `/bin/kafka-console-consumer --bootstrap-server [kafkaHost:port;kafkaHost:port] --topic hola-mundo --property print-timestamp=true --partition=2 `
* `/bin/kafka-console-consumer --topic hola-mundo --property print-timestamp=true --property print.key=true --property key.separator=":" --partition=2 --bootstrap-server [kafkaHost:port;kafkaHost:port]`
* `kafka-console-consumer --bootstrap-server 127.0.0.1:9092 --topic first_topic --from-beginning --property print.key=true --property key.separator=","`
* `bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 \
  --topic streams-wordcount-output \
  --from-beginning \
  --formatter kafka.tools.DefaultMessageFormatter \
  --property print.key=true \
  --property print.value=true \
  --property key.deserializer=org.apache.kafka.common.serialization.StringDeserializer \
  --property value.deserializer=org.apache.kafka.common.serialization.LongDeserializer`



## Consumer groups.
* `kafka-consumer-groups --bootstrap-server localhost:9092 --list`
* `kafka-consumer-groups --bootstrap-server localhost:9092 --describe --group nameGroup`
* `kafka-consumer-groups --bootstrap-server localhost:9092 --describe --all-groups`
* `kafka-consumer-groups --bootstrap-server localhost:9092 --topic topicName --group groupName --execute --reset-offsets --to-earliest`
* `kafka-consumer-groups --bootstrap-server localhost:9092 --topic topicName --group groupName --execute --reset-offsets --shift-by 2`
* `kafka-consumer-groups --bootstrap-server localhost:9092 --topic topicName --group groupName --execute --reset-offsets --shift-by -2`



## Configs.
* `/bin/kafka-configs.sh --bootstrap-server localhos:9092 --entiry-type topics --entity-name topicName --alter --add-config max.message.bytes=10485760`



## Zookeeper.
* `zookeeper-server-start.sh ~/Programs/kafka_2.13-2.7.0/config/zookeeper.properties`
* `zookeeper-server-start.sh -deamon ~/Programs/kafka_2.13-2.7.0/config/zookeeper.properties`



## Kafka.
* `kafka-server-start.sh ~/Programs/kafka_2.13-2.7.0/config/server.properties`



## Configs 
* Add/Remove entity config for a topic, client, user or broker.
* `kafka-configs --zookeeper localhost:2181 --entity-type topics --entity-name configured-topic --describe`
* `kafka-configs --zookeeper localhost:2181 --entity-type topics --entity-name configured-topic --alter --add-config min.insync.replicas=2`
* `kafka-configs --zookeeper localhost:2181 --entity-type topics --entity-name configured-topic --alter --delete-config min.insync.replicas`

