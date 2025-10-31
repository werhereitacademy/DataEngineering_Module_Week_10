# DataEngineering_Module_Week_10

🚀 Real-Time Data Streaming with Kafka (Python + Docker)
This project is a real-time data streaming solution. It collects current weather data from the WeatherAPI using Python, publishes this data to a Kafka Broker running in Docker, and then processes the stream using both a Python consumer and Spark Structured Streaming (via Fabric).

1. 📋 Requirements
You need the following tools to run the project:

Docker Desktop (Installation: https://www.docker.com/products/docker-desktop)

Python 3.9 or higher

Python Libraries: You need to install these:

Bash

pip install kafka-python requests
2. ⚙️ Setting Up the Docker Environment
These steps will start your Kafka Broker and its user interface.

Create a folder named kafka_demo on your desktop.

Copy the docker-compose.yml file (from your instructor) into this folder.

Open your command line and go to the folder:

Bash

cd Desktop\kafka_demo
Start Kafka and its user interface in the background:

Bash

docker compose up -d
✅ Kafka Broker: localhost:9092

✅ Kafka UI: http://localhost:8081 (Interface for Kafka settings)

✅ Kafka Public Broker: localhost:9093

To stop the services:

Bash

docker compose down
3. ☁️ WeatherAPI Setup
You will use this API endpoint to get the current weather data:

http://api.weatherapi.com/v1/current.json?key={API_KEY}&q=Amsterdam&aqi=no
Please replace {API_KEY} with your own API key.

You can get a free API key here: https://www.weatherapi.com/

4. 🌐 Public Access with Ngrok (For Fabric)
We use Ngrok to make our local Kafka Broker (port 9093) public so that services like Fabric Spark can read the data.

Create an Ngrok account: https://dashboard.ngrok.com

Install Ngrok on your computer.

Run this command in your terminal to create a TCP tunnel:

Bash

ngrok tcp 9093
⚠️ Note: Ngrok may require credit card information for identity verification to use TCP tunnels. You will not be charged.

Ngrok will give you an external address like this:

tcp://<ngrok-host>:<ngrok-port>
Example: tcp://6.tcp.eu.ngrok.io:17090
You must also add this Ngrok address to the KAFKA_ADVERTISED_LISTENERS section in your docker-compose.yml file.

5. 🛠️ Tasks
🧩 Producer - (producer.py)
Create a Python file.

Get the following data from WeatherAPI:

City

Temperature

Humidity

Wind speed

Local time

Last updated

Send this data to Kafka every 60 seconds.

🖥️ Consumer 1 – Python - (consumer_python.py)
Create a second Python file.

It should read the real-time data from Kafka.

Show the current wind speed on the console.

⚡ Consumer 2 – Spark (Fabric) - (consumer_spark_fabric.ipynb)
In the Fabric portal, create a new Notebook.

Start a Spark session.

Use Structured Streaming to read the data coming from the Ngrok address.

Add a timestamp to each record automatically.

Calculate the average temperature in a 5-minute window.

Move the window every 1 minute (so the average updates each minute).

Save the results to your Lakehouse in Delta format under the table name avg_temperature.
