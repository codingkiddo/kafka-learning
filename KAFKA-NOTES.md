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









-- 


# Start the ZooKeeper service
./bin/zookeeper-server-start.sh config/zookeeper.properties

# Start the Kafka broker service
./bin/kafka-server-start.sh config/server.properties

# CREATE the Kafka topic
./bin/kafka-topics.sh --create --topic basic_table --bootstrap-server localhost:9092 --partitions 3 --replication-factor 1

# DESCRIBE the Kafka topic
./bin/kafka-topics.sh --describe --bootstrap-server localhost:9092 --topic basic_table

# DELETE the Kafka topic
./bin/kafka-topics.sh --delete --topic basic_table --bootstrap-server localhost:9092

# Kafka Producer
./bin/kafka-console-producer.sh --broker-list localhost:9092 --topic basic_table

# Kafka Consumer
./bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic basic_table  --from-beginning






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
 --broker-list localhost:9092 --topic basic_table \
 --property value.schema='{"type":"record","name":"basic_table","fields":[{"name":"userid","type":"string"},{"name":"username","type":"string"}]}'




./bin/kafka-console-producer.sh --broker-list localhost:9092 --topic basic_topic --property parse.key=true --property key.separator=: < data.txt
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

./bin/kafka-topics.sh --create --topic basic_table --bootstrap-server localhost:9092 --replication-factor 1 --partitions 3

https://digitalis.io/blog/apache-cassandra/getting-started-with-kafka-cassandra-connector/

export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_311.jdk/Contents/Home

export KAFKA_CONNECT_REST=http://localhost:8083



./bin/kafka-topics.sh --describe --bootstrap-server localhost:9092 --topic basic_table

./bin/kafka-consumer.sh ---bootstrap-server localhost:9092 --topic basic_table


CREATE KEYSPACE blog WITH REPLICATION = {'class' : 'SimpleStrategy', 'replication_factor' : 3};
USE blog;
CREATE TABLE basic_table (userid text PRIMARY KEY, username text);
INSERT INTO basic_table (userid, username) VALUES ("1", "Vinod");
INSERT INTO basic_table ("userid", "username") VALUES ("1", "Vinod");
SELECT * FROM basic_table;

SELECT * FROM blog.basic_table;



{"userid": "2", "username": "mention data"}

./bin/kafka-console-producer.sh --broker-list localhost:9092 --topic basic_table --property parse.key=true --property key.separator=: < data.txt


./bin/kafka-console-consumer.sh --topic basic_table --from-beginning --bootstrap-server localhost:9092

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





https://www.google.com/search?q=reactjs+firebase+authentication&rlz=1C5CHFA_enIN987IN987&oq=reactjs+fire&aqs=chrome.0.35i39j69i57j35i39j0i512l4j69i60.15267j0j7&sourceid=chrome&ie=UTF-8
https://www.freecodecamp.org/news/react-firebase-authentication-and-crud-operations/
https://blog.logrocket.com/user-authentication-firebase-react-apps/
https://www.google.com/search?q=reactjs+nodejs+authentication&rlz=1C5CHFA_enIN987IN987&oq=reactjs+nodejs+authentication&aqs=chrome..69i57j0i390l4.6137j0j7&sourceid=chrome&ie=UTF-8
https://www.google.com/search?q=writing+from+kafka+to+cassandra&rlz=1C5CHFA_enIN987IN987&oq=writing+from+kafka+to+ca&aqs=chrome.1.69i57j33i160.7025j0j7&sourceid=chrome&ie=UTF-8
https://docs.lenses.io/5.0/integrations/connectors/stream-reactor/sinks/cassandrasinkconnector/
https://docs.confluent.io/kafka-connect-cassandra/current/cassandra_sink_connector_config.html
https://lenses.io/blog/2018/03/cassandra-to-kafka/
https://lenses.io/blog/2018/03/cassandra-to-kafka-part-2/
https://hevodata.com/learn/kafka-and-cassandra/
https://lenses.io/blog/2018/03/cassandra-to-kafka/
https://docs.lenses.io/5.0/integrations/connectors/stream-reactor/sinks/cassandrasinkconnector/
https://github.com/lensesio/stream-reactor/releases
https://theagilejedi.wordpress.com/2018/01/23/using-the-kafka-connect-cassandra-source-part-1/
https://cassandra.apache.org/_/quickstart.html
https://www.tutorialspoint.com/cassandra/cassandra_installation.htm
https://docs.scala-lang.org/getting-started/index.html
https://kafka.apache.org/downloads
https://docs.datastax.com/en/dse/5.1/cql/cql/cql_reference/refDateTimeFormats.html
https://www.google.com/search?q=Error+while+fetching+metadata+with+correlation+id+3+%3A+%7Borders%3DLEADER_NOT_AVAILABLE%7D+&rlz=1C5CHFA_enIN987IN987&sxsrf=APq-WBuOxy3wyrMgArCzJiU551VnDabtFQ%3A1649706295345&ei=N4VUYrXYFK6Y4-EP6eGAyA8&ved=0ahUKEwj1z97t4oz3AhUuzDgGHekwAPkQ4dUDCA4&uact=5&oq=Error+while+fetching+metadata+with+correlation+id+3+%3A+%7Borders%3DLEADER_NOT_AVAILABLE%7D+&gs_lcp=Cgdnd3Mtd2l6EANKBAhBGAFKBAhGGABQtw5Ytw5g3BBoAXAAeACAAZQBiAGUAZIBAzAuMZgBAKABAcABAQ&sclient=gws-wiz
https://www.google.com/search?q=Kafka+Cassandra+connector+example&rlz=1C5CHFA_enIN987IN987&oq=kafka+cass&aqs=chrome.2.69i59l3j69i57j69i60l3j69i65.13490j0j7&sourceid=chrome&ie=UTF-8
https://digitalis.io/blog/apache-cassandra/getting-started-with-kafka-cassandra-connector/
https://www.google.com/search?q=kafka+remove+all+connectors&rlz=1C5CHFA_enIN987IN987&oq=kafka+remove+all+connectors&aqs=chrome..69i57j0i22i30.9969j0j4&sourceid=chrome&ie=UTF-8
https://www.google.com/search?q=kafka+ksldb&rlz=1C5CHFA_enIN987IN987&oq=kafka+ksldb&aqs=chrome..69i57j0i13l4j0i10i13i30l2j0i5i13i30l3.7801j0j4&sourceid=chrome&ie=UTF-8
https://ksqldb.io/quickstart.html
https://www.baeldung.com/ksqldb
https://docs.confluent.io/4.1.0/ksql/docs/installation/installing.html
https://docs.datastax.com/en/kafka/doc/kafka/kafkaStringJson.html
