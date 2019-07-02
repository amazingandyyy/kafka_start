# Kafka

Kafka needs to work with zookeeper

## Installation

### download [kafka](https://kafka.apache.org/downloads)

### install java8 and kafka to bin

```shell
brew install kafka
```

## Start

```shell
cd /Users/andy/Projects/kafka_start/kafka_2.12-2.3.0
// update dataDir in config/zookerper.properties
zookeeper-server-start config/zookeeper.properties
// update log.dirs in config/server.properties
kafka-server-start config/server.properties
```

## Commands

kafka-topics

```shell
❯ kafka-topics --zookeeper 127.0.0.1:2181 --topic first_topic --create --partitions 3 --replication-factor 1
❯ kafka-topics --zookeeper 127.0.0.1:2181 --list
❯ kafka-topics --zookeeper 127.0.0.1:2181 --topic first_topic --describe
❯ kafka-topics --zookeeper 127.0.0.1:2181 --topic second_topic --create --partitions 6 --replication-factor 1
❯ kafka-topics --zookeeper 127.0.0.1:2181 --topic second_topic --delete
```

kafka-console-producer/kafka-console-consumer

```shell
❯ kafka-console-consumer --bootstrap-server 127.0.0.1:9092 --topic first_topic
❯ kafka-console-producer --broker-list 127.0.0.1:9092 --topic first_topic
❯ kafka-console-consumer \
    --bootstrap-server 127.0.0.1:9092 \
    --topic first_topic \
    --from-beginning \
    --group my-first-application
❯ kafka-console-producer --broker-list 127.0.0.1:9092 --topic first_topic --property parse.key=true --property key.separator=,
> key,value
> another key,another value

❯ kafka-console-consumer --bootstrap-server 127.0.0.1:9092 --topic first_topic --from-beginning --property print.key=true --property key.separator=,
```

consumer groups

```shell
❯ kafka-consumer-groups --bootstrap-server localhost:9092 --list
❯ kafka-consumer-groups --bootstrap-server localhost:9092 --describe --group my-second-application
# switch offset
❯ kafka-consumer-groups --bootstrap-server localhost:9092 --group my-second-application -reset-offsets --to-earliest --execute --all-topics
```
