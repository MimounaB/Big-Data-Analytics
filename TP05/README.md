# TP05 – Real-Time Data Streaming and Processing Using Apache Kafka

## 1. Project Overview

This project demonstrates real-time data streaming and processing using **Apache Kafka**, **Python**, and **Docker Compose**.

The system simulates campus sensor data, including temperature and humidity measurements. A Producer generates sensor events and sends them to a Kafka topic, while Consumers receive and process these events.

## 2. Technologies Used

- Apache Kafka 3.9.1
- Python
- kafka-python 2.0.2
- Docker
- Docker Compose
- JSON

## 3. Project Structure

```text
tp05-kafka/
│
├── compose.yaml
├── producer.py
├── consumer.py
├── consumer2.py
├── requirements.txt
├── README.md
├── report.pdf
│
└── screenshots/
    ├── docker-status.png
    ├── topic-description.png
    ├── producer-output.png
    └── consumer-output.png
```

## 4. System Architecture

The project follows this data flow:

**Producer → Kafka Broker → Topic → Consumer**

- The Producer generates sensor events.
- The Kafka Broker receives and stores the messages.
- The Topic `campus-sensors` organizes the sensor events.
- The Consumer reads and processes the messages.

## 5. Kafka Configuration

The main topic is configured with:

- Topic name: `campus-sensors`
- Number of partitions: 3
- Replication factor: 1

An additional topic named `campus-sensors-one` was created with one partition to compare topic configurations.

## 6. Installation and Execution

### Step 1: Start Kafka

```powershell
docker compose up -d
```

### Step 2: Check the container

```powershell
docker compose ps
```

### Step 3: Create and activate the Python virtual environment

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

### Step 4: Install dependencies

```powershell
pip install -r requirements.txt
```

### Step 5: Run the Producer

```powershell
python producer.py
```

### Step 6: Run the Consumer

In another PowerShell terminal:

```powershell
python consumer.py
```

### Step 7: Run the second Consumer

```powershell
python consumer2.py
```

The second Consumer uses a different consumer group ID and calculates the running average temperature.

## 7. Main Features

- Real-time sensor event generation.
- Sending JSON messages to Kafka.
- Receiving and displaying sensor data.
- Detecting high temperatures (35°C or above).
- Calculating the running average temperature.
- Testing independent consumption using different consumer groups.
- Comparing topics with one and three partitions.

## 8. Cleanup

To stop Kafka containers:

```powershell
docker compose down
```

To remove the stored Kafka data as well:

```powershell
docker compose down -v
```

**Warning:** The second command deletes the stored Kafka data.

## 9. Evidence

Screenshots of the Docker container status, topic description, Producer output, and Consumer output are available in the `screenshots/` directory.