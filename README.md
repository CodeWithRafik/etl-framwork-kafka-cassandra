# Pipeline ETL Temps Réel Kafka-Cassandra

## Prérequis
- Docker 20.10+ et Docker Compose 2.0+
- Python 3.8+ avec pip

## Installation
1. Clonez le dépôt : `git clone https://github.com/votre-user/kafka-cassandra-etl.git && cd kafka-cassandra-etl`
2. Installez les dépendances : `pip install confluent-kafka cassandra-driver python-dotenv`
3. Lancez les services : `docker-compose up -d --build`

## Fichiers de Configuration et Code
`docker-compose.yml` :
```yaml
version: '3.8'
services:
  zookeeper:
    image: confluentinc/cp-zookeeper:7.0.1
    ports: ["2181:2181"]
  kafka:
    image: confluentinc/cp-kafka:7.0.1
    depends_on: [zookeeper]
    ports: ["9092:9092"]
    environment:
      KAFKA_ZOOKEEPER_CONNECT: "zookeeper:2181"
      KAFKA_AUTO_CREATE_TOPICS_ENABLE: "true"
  cassandra:
    image: cassandra:4.0
    ports: ["9042:9042"]
  producer:
    build: ./producer
    depends_on: [kafka]
    environment:
      KAFKA_BOOTSTRAP_SERVERS: "kafka:9092"
      TOPIC_NAME: "input_topic"
  consumer:
    build: ./consumer
    depends_on: [kafka, cassandra]
