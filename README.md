# DataEngineering_Module_Week_10

# 📘 Instructions: Real-Time Data Streaming with Kafka (Python + Docker)

## 1. Requirements

- 🐳 Docker Desktop must be installed  
  👉 [Download Docker Desktop](https://www.docker.com/products/docker-desktop)

- 🐍 Python 3.9 or higher must be installed on your computer

- 📦 Required Python libraries:
  ```bash
  pip install kafka-python requests

⚙️ Setting Up the Docker Environment
These steps will start your Kafka Broker and its user interface.

Create a folder named kafka_demo on your desktop.

Copy the docker-compose.yml file (given by your instructor) into this folder.

Open the command line and go to this folder:

Bash

cd Desktop\kafka_demo
Start Kafka and its user interface:

Bash

docker compose up -d
✅ Kafka Broker: localhost:9092

✅ Kafka UI: http://localhost:8081 → Interface for Kafka settings

✅ Kafka Public Broker: localhost:9093

To stop the services:

Bash

docker compose down
