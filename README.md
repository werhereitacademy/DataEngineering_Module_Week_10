# DataEngineering_Module_Week_10

📘 Instructions: Real-Time Data Streaming with Kafka (Python + Docker)
1. Requirements

Docker Desktop must be installed → https://www.docker.com/products/docker-desktop

Python 3.9 or higher must be installed on your computer

You need to install these Python libraries:

pip install kafka-python requests

2. Setting Up the Docker Environment

Create a folder named kafka_demo on your desktop.

Copy the docker-compose.yml file (given by your instructor) into this folder.

Open the command line and go to this folder:

cd Desktop\kafka_demo


Start Kafka and its user interface:

docker compose up -d


✅ Kafka Broker: localhost:9092
✅ Kafka UI: http://localhost:8081
 → Interface for Kafka settings
✅ Kafka Public Broker: localhost:9093

To stop the services:

docker compose down

3. WeatherAPI Settings

The API endpoint to use:

http://api.weatherapi.com/v1/current.json?key={API_KEY}&q=Amsterdam&aqi=no


Replace {API_KEY} with your own API key.

You can get a free API key from: https://www.weatherapi.com/

4. Public Access with Ngrok

(We use this to make data readable from Fabric by making it public)

Create an Ngrok account → https://dashboard.ngrok.com

Install Ngrok on your computer

Run this command in the terminal:

ngrok tcp 9093


⚠️ Note: To use TCP tunnels, you must enter your credit card info in
Settings > Account on your Ngrok dashboard. You won’t be charged — it’s only for identity verification.

Ngrok will give you an address like this:

tcp://<ngrok-host>:<ngrok-port>
Example: tcp://6.tcp.eu.ngrok.io:17090


You can connect to your local Kafka producer from the outside (for example, from Fabric Spark) using this address.
You also need to add this address to the KAFKA_ADVERTISED_LISTENERS section in your Docker setup file.

5. Tasks
🧩 Producer

Create a Python file.

Get the following data from WeatherAPI:

City

Temperature

Humidity

Wind speed

Local time

Last updated

Send this data to Kafka every 60 seconds.

🖥️ Consumer 1 – Python

Create another Python file.

It should read real-time data from Kafka and show the current wind speed on the console.

⚡ Consumer 2 – Spark

In the Fabric portal, create a new Notebook.

Start a Spark session.

Use Structured Streaming to read the data coming from Ngrok.

Add a timestamp to each record automatically.

Calculate the average temperature in a 5-minute window.

Move the window every 1 minute (so the average updates each minute).

Save the results to your Lakehouse in Delta format under the table name avg_temperature.
