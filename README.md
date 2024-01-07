---
title: 'Kafka with Spring Boot 101'
disqus: hackmd
---

Kafka with Spring Boot 101
===

## Table of Contents

[TOC]

## Kafka 101
### 安裝與啟停
#### 安裝與設定
> 下載 https://kafka.apache.org/downloads
```gherkin=
mkdir -p $HOME/workspace/kafka
cd $HOME/workspace/kafka
tar zxvf $HOME/Downloads/kafka_2.13-3.6.1.tgz
cd kafka_2.13-3.6.1/
```
> 設定不重複的 server id
```gherkin=
cd $HOME/workspace/kafka/kafka_2.13-3.6.1

export KAFKA_CLUSTER_ID="$(bin/kafka-storage.sh random-uuid)"

bin/kafka-storage.sh format -t $KAFKA_CLUSTER_ID -c config/kraft/server.properties
```
#### 啟動
```gherkin=
cd $HOME/workspace/kafka/kafka_2.13-3.6.1

bin/kafka-server-start.sh config/kraft/server.properties
```
#### 停止
```gherkin=
cd $HOME/workspace/kafka/kafka_2.13-3.6.1

bin/kafka-server-stop.sh
```

### cli 使用
#### Consumer 
```gherkin=
bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic my.first.topic
```
#### Producer
```gherkin=
bin/kafka-console-producer.sh --bootstrap-server localhost:9092 --topic my.first.topic
```

#### Topic
```gherkin=
bin/kafka-topics.sh --bootstrap-server localhost:9092 --list


bin/kafka-topics.sh --bootstrap-server localhost:9092 --create --topic my.new.topic


bin/kafka-topics.sh --bootstrap-server localhost:9092 --describe --topic my.new.topic

bin/kafka-topics.sh --bootstrap-server localhost:9092 --alter --topic my.new.topic --partitions 3

bin/kafka-topics.sh --bootstrap-server localhost:9092 --delete --topic my.new.topic
```

#### Consumer Group
```gherkin=
bin/kafka-consumer-groups.sh --bootstrap-server localhost:9092 --list

bin/kafka-consumer-groups.sh --bootstrap-server localhost:9092 --topic cg.demo.topic --group my.new.group

bin/kafka-consumer-groups.sh --bootstrap-server localhost:9092 --describe --group my.new.group

bin/kafka-consumer-groups.sh --bootstrap-server localhost:9092 --describe --group my.new.group --members
```


###### tags: `Kafka` `Documentation`
