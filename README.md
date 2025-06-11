# Projet ETL Kafka avec Intégration Cassandra

Ce projet démontre comment mettre en place un pipeline de données utilisant Apache Kafka pour l'ingestion de données en temps réel, effectuer un traitement ETL sur les données, et stocker les résultats dans Apache Cassandra. Le pipeline se compose d'un **producteur Kafka**, d'un **consommateur Kafka** et d'une **intégration avec Cassandra**.

---

## Table des Matières

- [Prérequis](#prérequis)  
- [Structure du Projet](#structure-du-projet)  
- [Configuration et Installation](#configuration-et-installation)  
- [Exécution du Producteur Kafka](#exécution-du-producteur-kafka)  
- [Exécution du Consommateur Kafka](#exécution-du-consommateur-kafka)  
- [Vérification des Données dans Cassandra](#vérification-des-données-dans-cassandra)  
- [Notes Complémentaires](#notes-complémentaires)  
- [Exemple de Données](#exemple-de-données)

---

## Prérequis

Avant de commencer, assurez-vous d’avoir les éléments suivants installés :

- Docker et Docker Compose  
- Python 3.x  
- Bibliothèques Python :
  ```bash
  pip install confluent-kafka cassandra-driver
