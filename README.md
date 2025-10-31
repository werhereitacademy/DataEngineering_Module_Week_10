# DataEngineering_Module_Week_10

# Real-Time Data Streaming with Kafka (Python + Docker)

## 1. Requirements

- [Docker Desktop](https://www.docker.com/products/docker-desktop)
- Python 3.9+
- Python libraries:
  ```bash
  pip install kafka-python requests
2. Docker Setup
Create a folder named kafka_demo.

Copy the provided docker-compose.yml file into this folder.

Open terminal and navigate to the folder:

bash
cd Desktop/kafka_demo
Start Kafka and UI:

bash
docker compose up -d
Kafka Services
Kafka Broker: localhost:9092

Kafka UI: http://localhost:8081

Kafka Public Broker: localhost:9093

To stop services:

bash
docker compose down
3. WeatherAPI Settings
Endpoint:

Code
http://api.weatherapi.com/v1/current.json?key={API_KEY}&q=Amsterdam&aqi=no
Replace {API_KEY} with your own key from WeatherAPI

4. Public Access with Ngrok
Create an account: Ngrok Dashboard

Install Ngrok

Run:

bash
ngrok tcp 9093
⚠️ TCP tunnels require credit card verification (no charges).

Example address:

Code
tcp://6.tcp.eu.ngrok.io:17090
Update KAFKA_ADVERTISED_LISTENERS in docker-compose.yml with this address.

5. Tasks
🧩 Producer (Python)
Create producer.py

Fetch every 60 seconds:

City

Temperature

Humidity

Wind speed

Local time

Last updated

Send to Kafka topic.

🖥️ Consumer 1 – Python
Create consumer.py

Read from Kafka

Print wind speed to console

⚡ Consumer 2 – Spark (Fabric Notebook)
Start Spark session

Use Structured Streaming via Ngrok

Add timestamp to each record

Calculate average temperature:

5-minute window

Slide every 1 minute

Save to Lakehouse in Delta format:

Code
Table name: avg_temperature
