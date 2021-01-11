---
title: "Minimal config to start a local kafka"
categories:
  - Blog
tags:
  - Kafka
---

This is a minimal service start for kafka.

Kafka Broker needs ZooKeeper, so sure to start it before and stop after.

Start ZooKeeper

```
zookeeper-server-start.sh -daemon ~/kafka_2.13-2.7.0/config/zookeeper.properties
```

Start Kafka Broker

```
kafka-server-start.sh -daemon ~/kafka_2.13-2.7.0/config/server.properties
```

Create a Topic (only with 1 replication as we are running only one Kafka Broker)

```
kafka-topics.sh --bootstrap-server 127.0.0.1:9092 --topic some-topic --create --partitions 3 --replication-factor 1
```

Start Consumer

```
kafka-console-consumer.sh --bootstrap-server 127.0.0.1:9092 --topic some-topic --group app-consumer-group
```


Start Producer

```
kafka-console-producer.sh --broker-list 127.0.0.1:9092 --topic some-topic
```


To Stop

```
kafka-server-stop.sh -daemon ~/kafka_2.13-2.7.0/config/server.properties
zookeeper-server-stop.sh -daemon ~/kafka_2.13-2.7.0/config/zookeeper.properties
```

Other main commands

```
kafka-topics.sh --bootstrap-server 127.0.0.1:9092 --list
kafka-topics.sh --bootstrap-server 127.0.0.1:9092 --topic some-topic --describe
kafka-topics.sh --bootstrap-server 127.0.0.1:9092 --topic some-topic --delete 
```
