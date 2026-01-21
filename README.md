# docker-kafka-pipeline

A lightweight Apache Kafka setup running inside Docker containers using Docker Compose.  
This project demonstrates how to start Kafka locally and exchange messages between a producer and a consumer using Kafka CLI commands.

It is useful for learning event streaming concepts, testing Kafka configurations, and building scalable messaging pipelines.

---

## 🛠 Tech Stack

- Apache Kafka  
- Zookeeper  
- Docker  
- Docker Compose  

---

## ⚙️ Prerequisites

Make sure the following are installed and running:

```bash
docker --version
docker compose version
```
## Run Kafka
### Step 1: Create docker-compose.yml
Create a file named docker-compose.yml and add the following services:
 - Zookeeper
 - Kafka

### Step 2: Start Kafka Services

docker compose up -d

Output:

<img width="737" height="109" alt="Docker up" src="https://github.com/user-attachments/assets/3601117a-d8f4-429b-ad3d-555580e8a1b9" />

### Step 3: Verify Containers

docker ps

Output:
<img width="975" height="99" alt="image" src="https://github.com/user-attachments/assets/d48d426f-60ae-40dd-b400-8d589d55c11e" />


### Step 4: Create Kafka Topic

docker exec -it kafka \
kafka-topics --create \
--topic kafka-basic \
--bootstrap-server localhost:29092 \
--partitions 1 \
--replication-factor 1


📌 kafka-basic is the topic name.

Output:
<img width="975" height="142" alt="Topic created" src="https://github.com/user-attachments/assets/b503942a-2d7c-4965-9d72-c464205b0aaa" />

### Step 5: List Topics

docker exec -it kafka \
kafka-topics --list \
--bootstrap-server localhost:29092

### Step 6: Start Producer (Terminal 1)

docker exec -it kafka \
kafka-console-producer \
--topic kafka-basic \
--bootstrap-server localhost:29092


Type messages and press Enter to send.

Output:

<img width="952" height="193" alt="Producer" src="https://github.com/user-attachments/assets/4c28bf95-fe3d-4268-97e1-125273ec0bc5" />

### Step 7: Start Consumer (Terminal 2)

Open a new terminal window and run:

docker exec -it kafka \
kafka-console-consumer \
--topic kafka-basic \
--from-beginning \
--bootstrap-server localhost:29092


Messages sent by the producer will appear here.

Output:
<img width="945" height="176" alt="Consumer" src="https://github.com/user-attachments/assets/3e9933aa-ae1b-4c50-a2ee-e3919f88c018" />

### Step 8: Stop Kafka Services

docker compose down
