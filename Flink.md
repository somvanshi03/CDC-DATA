# Install Flink on Ubuntu


## **Prerequisites**:

   - Ensure you have Java installed on your system. Flink requires Java 8 or later.

## **Install Java**:
   
     sudo apt update
     sudo apt install default-jdk
     sudo apt install openjdk-17-jdk -y
   
     java -version
    

## **Download Flink**:
  
     
     wget https://dlcdn.apache.org/flink/flink-1.18.0/flink-1.18.0-bin-scala_2.12.tgz
     

## **Extract Flink**:
   
     tar -xzf flink-1.18.0-bin-scala_2.12.tgz
    

## **Start Flink Cluster**:
   
     cd flink-1.18.0
   
     ./bin/start-cluster.sh
     

## **Access Flink Dashboard**:
   
     http://localhost:8081
     
   - You should see the Flink dashboard, indicating that the installation was successful.

## **Run a Sample Job**:
   
     ./bin/flink run examples/streaming/WordCount.jar
     

