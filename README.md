# kafka-storm-compose
docker compose for apache kafka + apache storm

# Goal
To have infrastructure containing Apache Kafka and Apache Storm with all their dependencies (Zookeeper etc) managed by one docker compose.

# Usage
`docker-compose up`

# Manual Test
## Kafka and Zookeeper
1. Enter to kafkas container bash
`docker exec -it <your_kafka_container_name> bash`
2. Create topic
`$KAFKA_HOME/bin/kafka-topics.sh --create --topic topic --partitions 4 --zookeeper zk:2181 --replication-factor 1`
3. Double check created topic
`$KAFKA_HOME/bin/kafka-topics.sh --describe --topic topic --zookeeper zk:2181`
4. Start console message producer
`$KAFKA_HOME/bin/kafka-console-producer.sh --topic=topic --broker-list=`broker-list.sh``
5. Open another shell (repeat point 1) and in this shell attach a console consumer to the created topic
`$KAFKA_HOME/bin/kafka-console-consumer.sh --topic=topic --zookeeper=zk:2181`