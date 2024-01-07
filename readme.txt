KAFKA_CLUSTER_ID="$(bin/kafka-storage.sh random-uuid)"

bin/kafka-storage.sh format -t $KAFKA_CLUSTER_ID -c config/kraft/server.properties 

bin/kafka-server-start.sh config/kraft/server.properties

bin/kafka-server-stop.sh

#pro
bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic my.first.topic

# producer
bin/kafka-console-producer.sh --bootstrap-server localhost:9092 --topic my.first.topic
# list topics

bin/kafka-topics.sh --bootstrap-server localhost:9092 --list


bin/kafka-topics.sh --bootstrap-server localhost:9092 --create --topic my.new.topic


bin/kafka-topics.sh --bootstrap-server localhost:9092 --describe --topic my.new.topic


bin/kafka-topics.sh --bootstrap-server localhost:9092 --alter --topic my.new.topic --partitions 3



bin/kafka-topics.sh --bootstrap-server localhost:9092 --delete --topic my.new.topic



bin/kafka-consumer-groups.sh --bootstrap-server localhost:9092 --list


bin/kafka-consumer-groups.sh --bootstrap-server localhost:9092 --topic cg.demo.topic --group my.new.group


bin/kafka-consumer-groups.sh --bootstrap-server localhost:9092 --describe --group my.new.group



bin/kafka-consumer-groups.sh --bootstrap-server localhost:9092 --describe --group my.new.group --members


