# CDC Pipeline

## Install Kafka on Ubuntu 22


## **Prerequisites**:
   - Ensure you have Ubuntu 22.04 installed and updated.
   - Install Java Development Kit (JDK) version 8 or later.

## **Install Java**:
    
     sudo apt update

     sudo apt install default-jdk -y 
	 sudo apt install openjdk-17-jdk -y

     java -version
     

## **Download Kafka**:
   
     wget https://downloads.apache.org/kafka/3.9.1/kafka_2.12-3.9.1.tgz
       
     tar -xzf kafka_2.12-3.9.1.tgz
     

## **Set Up Kafka**:
   
     cd kafka_2.12-3.9.1/
     

## **Install Zookeeper**:
   
     sudo apt-get install -y zookeeperd
     

## **Start Zookeeper**:
   
     bin/zookeeper-server-start.sh config/zookeeper.properties
     

## **Start Kafka**:
   
     bin/kafka-server-start.sh config/server.properties
     

## **Create a Kafka Topic**:
   
     bin/kafka-topics.sh --create --topic test-topic --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1
     

## **Produce Messages**:
   
     bin/kafka-console-producer.sh --topic test-topic --bootstrap-server localhost:9092
    

## **Consume Messages**:
    
      bin/kafka-console-consumer.sh --topic test-topic --bootstrap-server localhost:9092 --from-beginning
      



## Starting Zookeeper

	./zookeeper-server-start.sh ../config/zookeeper.properties 


## Staring Kafka Server

	./kafka-server-start.sh ../config/server.properties 

## Create Topic

	./kafka-topics.sh --create --topic testtopic --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1

## Listing all the topics

	./kafka-topics.sh --list --bootstrap-server localhost:9092


## Create Kafka Console Producer:

	./kafka-console-producer.sh --topic testtopic --bootstrap-server localhost:9092

## Create Kafka Console Consumer:

	./kafka-console-consumer.sh --topic testtopic_output --from-beginning --bootstrap-server localhost:9092

## Starting Apache Link

	./start-cluster.sh

	Localhost:8081