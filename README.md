# learn_kafka

## the udemy course i was following
- https://github.com/dilipsundarraj1/kafka-for-developers-using-spring-boot/blob/master/SetUpKafka.md

# commands

### start the docker compose
docker-compose -f docker-compose.yml up -d
docker exec -it kafka /bin/sh
cd /opt/kafka_2.13-2.8.1/bin

### create Topic
./kafka-topics.sh --create --topic test-topic -zookeeper localhost:2181 --replication-factor 1 --partitions 4
./kafka-topics.sh --create --topic test-topic --replication-factor 1 --partitions 4 --bootstrap-server localhost:9092

### console producer and consumer
./kafka-console-producer.sh --broker-list localhost:9092 --topic test-topic
./kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test-topic --from-beginning
./kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test-topic --group alvin-test

### console consumer and consumer with key 
./kafka-console-producer.sh --broker-list localhost:9092 --topic test-topic --property "key.separator=-" --property "parse.key=true"
./kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test-topic --from-beginning -property "key.separator= - " --property "print.key=true"


### List topics in cluster
./kafka-topics.sh --bootstrap-server localhost:9092 --list

### view consumer groups
./kafka-consumer-groups.sh --bootstrap-server localhost:9092 --list

### view commit log
./kafka-run-class.sh kafka.tools.DumpLogSegments --deep-iteration --files /kafka/kafka-logs-787847534d1d/test-topic-0/00000000000000000000.log