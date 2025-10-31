# DataEngineering_Module_Week_10

# 📘 Real-Time Data Streaming with Kafka (Python + Docker)

## 1. Requirements
- [Docker Desktop](https://www.docker.com/products/docker-desktop) must be installed  
- Python **3.9+** must be installed  
- Install required Python libraries:
  ```bash
  pip install kafka-python requests
2. Docker Environment Setup
Create a folder named kafka_demo on your desktop.

Copy the docker-compose.yml file (provided by your instructor) into this folder.

Open a terminal and navigate to the folder:

bash
Copy code
cd Desktop/kafka_demo
Start Kafka and its UI:

bash
Copy code
docker compose up -d
Services:

🧩 Kafka Broker → localhost:9092

🌐 Kafka UI → http://localhost:8081

🔗 Kafka Public Broker → localhost:9093

To stop services:

bash
Copy code
docker compose down
3. WeatherAPI Settings
API Endpoint:

pgsql
Copy code
http://api.weatherapi.com/v1/current.json?key={API_KEY}&q=Amsterdam&aqi=no
Replace {API_KEY} with your own API key.

Get a free API key from WeatherAPI.

4. Public Access with Ngrok
To make data readable by Fabric (public access):

Create an account at Ngrok Dashboard.

Install Ngrok on your computer.

Run this command:

bash
Copy code
ngrok tcp 9093
⚠️ Note:
To use the TCP tunnel, you must add your credit card info under
Settings → Account in your Ngrok dashboard. This is only for identity verification — you won’t be charged.

Ngrok will provide an address like:

cpp
Copy code
tcp://<ngrok-host>:<ngrok-port>
Example: tcp://6.tcp.eu.ngrok.io:17090
Use this address in your Docker configuration under:

nginx
Copy code
KAFKA_ADVERTISED_LISTENERS
5. Tasks
🧩 Producer
Create a Python file.

Fetch data from WeatherAPI including:

City

Temperature

Humidity

Wind speed

Local time

Last updated

Send this data to Kafka every 60 seconds.

🖥️ Consumer 1 – Python
Create another Python file.

It should read real-time data from Kafka and display the current wind speed in the console.

⚡ Consumer 2 – Spark
In Fabric, create a new Notebook.

Start a Spark session.

Use Structured Streaming to read data from Ngrok.

Add an automatic timestamp to each record.

Calculate the average temperature within a 5-minute window.

Slide the window every 1 minute to update the average dynamically.

Save the results in Delta format to the Lakehouse table named:

nginx
Copy code
avg_temperature
🧠 Summary
This project demonstrates:

Real-time data streaming using Kafka

Data ingestion from WeatherAPI

Public data access with Ngrok

Real-time analytics in Spark Structured Streaming

🧩 Folder Structure Example
Copy code
kafka_demo/
│
├── docker-compose.yml
├── producer.py
├── consumer_python.py
├── consumer_spark_notebook.ipynb
└── README.md
✨ Author
Prepared as part of a Kafka Real-Time Streaming Demo (Python + Docker + Spark).
