# What is event streaming?

Event streaming is the digital equivalent of the human body's central nervous system. It is the technological foundation for the 'always-on' world where businesses are increasingly software-defined and automated, and where the user of software is more software.

Technically speaking, event streaming is the practice of capturing data in real-time from event sources like databases, sensors, mobile devices, cloud services, and software applications in the form of streams of events; storing these event streams durably for later retrieval; manipulating, processing, and reacting to the event streams in real-time as well as retrospectively; and routing the event streams to different destination technologies as needed. Event streaming thus ensures a continuous flow and interpretation of data so that the right information is at the right place, at the right time.


/Users/vinodkumar/Documents/Technologies/Kafka/kafka_2.12-3.0.0/libs/kafka-connect-cassandra-3.0.0-2.5.0-all.jar


./bin/connect-distributed.sh config/connect-distributed.properties cassandra-sink-distributed-orders.properties



./bin/kafka-console-producer.sh --broker-list localhost:9092 --topic orders-topic \
 --property value.schema='{"type":"record","name":"myrecord","fields":[{"name":"id","type":"int"},{"name":"created","type":"string"},{"name":"product","type":"string"},{"name":"price","type":"double"}, {"name":"qty", "type":"int"}]}'



CREATE KEYSPACE blog WITH REPLICATION = {'class' : 'SimpleStrategy', 'replication_factor' : 3};
use blog;
create table orders (id int, created varchar, product varchar, qty int, price float, PRIMARY KEY (id, created))
WITH CLUSTERING ORDER BY (created asc);


./bin/kafka-console-producer.sh --broker-list localhost:9092 --topic orders --property value.schema='{"type":"record","name":"myrecord","fields":[{"name":"id","type":"int"}, {"name":"created", "type": "string"}, {"name":"product", "type": "string"}, {"name":"price", "type": "double"}]}'


./bin/kafka-topics.sh \
  --delete --topic orders \
  --bootstrap-server localhost:9092
  
./bin/kafka-topics.sh --create --topic basic_topic --bootstrap-server localhost:9092 --partitions 1 --replication-factor 1



./bin/kafka-console-producer.sh --broker-list localhost:9092 --topic basic_topic --property parse.key=true --property key.separator=: < data.txt

./bin/kafka-topics.sh \
  --delete --topic basic_topic \
  --bootstrap-server localhost:9092
  
  
  curl -X DELETE http://localhost:8083/connectors/cassandra-sink-basic_topic

["cassandra-sink-basic_topic-1","cassandra-sink-orders-2","cassandra-sink-2","cassandra-sink","cassandra-sink-orders-3","packs2","packs","packs3","cassandra-sink-orders","cassandra-sink-basic_topic"]


  curl http://localhost:8083/connector-plugins
  curl localhost:8083/connectors
  
  curl -X GET "http://localhost:8083/connectors/cassandra-sink-basic_topic/status"
  
  export KAFKA_CONNECT_REST=http://localhost:8083
  
{"id": 2, "created": "mention data", "product": "mention name of product", "price": "mention price"}
{"id": 3, "created": "mention data", "product": "mention name of product", "price": “mention price”}


"key.converter": "org.apache.kafka.connect.storage.StringConverter", #use string converter for key
      "value.converter": "org.apache.kafka.connect.storage.StringConverter", #use string converter for values
      "key.converter.schemas.enable": false,  #no schema in data for the key
      "value.converter.schemas.enable": false  #no schema in data for value

nohup curl -X POST -H "Content-Type: application/json" \
-d "@/Users/vinodkumar/Documents/Technologies/Kafka/cassandra-sink-distributed-orders.json" \
 "http://localhost:8083/connectors"


curl -X POST -H "Content-Type: application/json" -d @connect-cassandra-source.json localhost:8083/connectors
curl -X POST -H "Content-Type: application/json" -d @connect-cassandra-orders.json localhost:8083/connectors



./bin/kafka-console-producer.sh \
 --broker-list localhost:9092 --topic orders \
 --property value.schema='{"type":"record","name":"myrecord","fields":[{"name":"id","type":"int"},{"name":"created","type":"string"},{"name":"product","type":"string"},{"name":"price","type":"double"}, {"name":"qty", "type":"int"}]}'




./bin/kafka-console-producer.sh --broker-list localhost:9092 --topic orders --property parse.key=true --property key.separator=: < data.txt
{
  "name": "cassandra-sink-basic_topic",
  "config": {
    "tasks.max": "1",
      "topics": "basic_topic", 
    "connector.class": "com.datamountaineer.streamreactor.connect.cassandra.sink.CassandraSinkConnector",
    "connect.cassandra.contact.points": "localhost",
    "connect.cassandra.port": 9042,
    "connect.cassandra.username": "cassandra",
    "connect.cassandra.password": "cassandra",
    "connect.cassandra.key.space": "blog",
      "topic.basic_topic.blog.basic_table.mapping": "userid=key, username=value", 
      "key.converter": "org.apache.kafka.connect.storage.StringConverter", 
      "value.converter": "org.apache.kafka.connect.storage.StringConverter", 
      "key.converter.schemas.enable": false,  
      "value.converter.schemas.enable": false,  
    "connect.cassandra.kcql": "INSERT INTO basic_table SELECT * FROM basic_topic"
    
  }
}


{"id": 1, "created": "2016-05-06 13:53:00", "product": "OP-DAX-P-20150201-95.7", "price": 94.2, "qty":100}

./bin/kafka-topics.sh --list --bootstrap-server localhost:9092



https://digitalis.io/blog/apache-cassandra/getting-started-with-kafka-cassandra-connector/



./bin/kafka-run-class.sh kafka.tools.GetOffsetShell  --topic test_topic --bootstrap-server localhost:9092 --group testgroup

./bin/kafka-topics.sh --describe --bootstrap-server localhost:9092 --topic test_topic
./bin/kafka-topics.sh --describe --bootstrap-server localhost:9092 --topic connect-configs
./bin/kafka-topics.sh --describe --bootstrap-server localhost:9092 --topic connect-offsets
./bin/kafka-topics.sh --describe --bootstrap-server localhost:9092 --topic connect-status



./bin/kafka-topics.sh \
  --delete --topic connect-configs \
  --bootstrap-server localhost:9092

./bin/kafka-topics.sh \
  --delete --topic connect-offsets \
  --bootstrap-server localhost:9092
  
  ./bin/kafka-topics.sh \
  --delete --topic connect-status \
  --bootstrap-server localhost:9092

./bin/kafka-topics.sh --create --topic test_topic --bootstrap-server localhost:9092 --replication-factor 1 --partitions 3

./bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --topic connect-configs --replication-factor 1 --partitions 1 --config cleanup.policy=compact
./bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --topic connect-offsets --replication-factor 1 --partitions 50 --config cleanup.policy=compact
./bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --topic connect-status --replication-factor 1 --partitions 10 --config cleanup.policy=compact




./bin/kafka-topics.sh --create --topic quickstart-events --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1
./bin/kafka-topics.sh --describe --bootstrap-server localhost:9092 --topic quickstart-events
./bin/kafka-console-producer.sh --topic quickstart-events --bootstrap-server localhost:9092

./bin/kafka-console-consumer.sh --topic test_topic --from-beginning --bootstrap-server localhost:9092 

CREATE KEYSPACE blog WITH REPLICATION = {'class' : 'SimpleStrategy', 'replication_factor' : 3};
use blog;
CREATE TABLE IF NOT EXISTS "pack_events" (
    event_id TEXT,
    event_data TEXT,
PRIMARY KEY ((event_id)));


INSERT INTO pack_events (event_id, event_data)
VALUES ('500', '{"foo":"bar"}');