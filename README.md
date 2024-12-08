# Real-Time Stock Market Data Processing with Kafka on AWS

This project simulates real-time stock market data processing using Apache Kafka and AWS. In the absence of a live stock market API, historical stock market data from a CSV file is used to mimic a real-time data stream. The data flows through a Kafka-based architecture, where it is ingested by a Kafka Producer, processed, and consumed by a Kafka Consumer.

The Kafka Producer reads records from the CSV file, converts them into JSON format, and sends them to a Kafka topic at one-second intervals to simulate live data streaming. The Kafka Consumer, running on a separate process, subscribes to the same Kafka topic, consumes the data, and uploads it to an Amazon S3 bucket for long-term storage and further analysis.

This project demonstrates how to:

  Set up an end-to-end data pipeline for real-time data ingestion and processing.
  Deploy Apache Kafka on an AWS EC2 instance for scalable message streaming.
  Use Kafka topics to decouple data producers and consumers.
  Leverage Amazon S3 for scalable, cost-effective cloud storage of processed data.
  This setup is ideal for real-world applications such as monitoring stock prices, processing IoT sensor data, or building scalable real-time analytics pipelines. It provides a foundation for handling live data streams in distributed systems, offering insights into data engineering principles like message streaming, cloud storage integration, and real-time processing.

---

## Features
- **Data Simulation:** Streams stock market data from a historical CSV file.
- **Real-Time Processing:** Uses Apache Kafka for data production and consumption.
- **Cloud Storage:** Stores processed data in an Amazon S3 bucket.
- **AWS Integration:** Deploys Kafka on an EC2 instance and interacts with S3 for data storage.

---

## Architecture
1. **Kafka Producer** streams simulated real-time stock market data from a CSV file.
2. **Kafka Consumer** reads the data and uploads it as JSON files to an S3 bucket.
3. **AWS EC2 Instance** hosts the Kafka broker and ZooKeeper.
4. **Amazon S3** stores processed data for downstream analytics or visualization.

---

## Installation and Setup

### Prerequisites
- AWS account with permissions to create and manage EC2 instances and S3 buckets.
- EC2 instance (Linux-based) with public IP access.
- Python 3.8+ installed on your local machine.
- Java 1.8 installed on your EC2 instance.

### Kafka Installation on EC2
1. Download and extract Kafka:
   ```bash
   wget https://downloads.apache.org/kafka/3.3.1/kafka_2.12-3.3.1.tgz
   tar -xvf kafka_2.12-3.3.1.tgz
2. Install Java:
  sudo yum install java-1.8.0-openjdk
  java -version
3. Start ZooKeeper:
  cd kafka_2.12-3.3.1
  bin/zookeeper-server-start.sh config/zookeeper.properties
4. Start Kafka server:
  export KAFKA_HEAP_OPTS="-Xmx256M -Xms128M"
  bin/kafka-server-start.sh config/server.properties
5. Create a Kafka topic:
  bin/kafka-topics.sh --create --topic demo_test --bootstrap-server <PUBLIC_IP>:9092 --replication-factor 1 --partitions 1

Project Setup
1. Clone the repository:
    git clone https://github.com/your-username/real-time-stock-market-kafka.git
    cd real-time-stock-market-kafka
2. Install dependencies:
    pip install -r requirements.txt
3. Update the IP address in producer.py and consumer.py to match your EC2 instance’s public IP.
