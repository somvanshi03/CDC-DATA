# Install Debezium on Ubuntu


## Prerequisites**  

  sudo apt-get install openjdk-8-jdk

  wget https://archive.apache.org/dist/kafka/2.6.3/kafka_2.12-2.6.3.tgz
  tar -xvzf kafka_2.12-2.6.3.tgz
  mv kafka_2.12-2.6.3 kafka


## Download Debezium Connector**  

  wget https://repo1.maven.org/maven2/io/debezium/debezium-connector-mysql/1.8.0.Final/debezium-connector-mysql-1.8.0.Final-plugin.tar.gz
  tar -xvzf debezium-connector-mysql-1.8.0.Final-plugin.tar.gz
  mv debezium-connector-mysql-1.8.0.Final-plugin plugins
  

## Configure Kafka Connect**  

  vi kafka/config/connect-standalone.properties
 
	- Add the following line to the end of the file:


  plugin.path=/path/to/kafka/plugins
  

## Create Connector Configuration** 
 
	- Create a new properties file named `connect-debezium-mysql.properties` in the Kafka config directory:

  ```properties
  name=mysql-connector
  connector.class=io.debezium.connector.mysql.MySqlConnector
  tasks.max=1
  database.hostname=localhost
  database.port=3306
  database.user=debezium
  database.password=dbz
  database.server.id=223344
  database.history.kafka.topic=msql.history
  database.server.name=mysql-connector
  ```

## Start Zookeeper and Kafka**  

  bin/zookeeper-server-start.sh kafka/config/zookeeper.properties
  
  bin/kafka-server-start.sh kafka/config/server.properties
  

## Start Kafka Connect with Debezium Connector**  

  kafka/bin/connect-standalone.sh kafka/config/connect-standalone.properties kafka/config/connect-debezium-mysql.properties
  

## Verify the Setup**  

  curl -s localhost:8083/connectors/mysql-connector/status | jq
  
  bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic msql.history --from-beginning
 

