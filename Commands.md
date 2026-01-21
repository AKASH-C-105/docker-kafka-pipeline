# Kafka Docker Commands Reference

This document contains all terminal commands required to run Apache Kafka using Docker Compose and test producer–consumer messaging using Kafka CLI.

Use this as a quick reference during demos, labs, and troubleshooting.

---

## 🔹 Start Docker Services

Start Kafka and Zookeeper containers:

```bash
docker compose up -d
```
Create Kafka Topic

Create a topic named kafka-basic:
```
docker exec -it kafka \
kafka-topics --create \
--topic kafka-basic \
--bootstrap-server localhost:29092 \
--partitions 1 \
--replication-factor 1
```

🔹 List Kafka Topics
```
docker exec -it kafka \
kafka-topics --list \
--bootstrap-server localhost:29092
```

🔹 Start Producer

Open Terminal 1 and run:
```
docker exec -it kafka \
kafka-console-producer \
--topic kafka-basic \
--bootstrap-server localhost:29092
```


Type messages and press Enter to send.

🔹 Start Consumer

Open Terminal 2 and run:
```
docker exec -it kafka \
kafka-console-consumer \
--topic kafka-basic \
--from-beginning \
--bootstrap-server localhost:29092
```

Messages sent by the producer will appear here.

🔹 Stop Docker Services

Stop and remove containers:
```
docker compose down4
```

📝 Notes

Ensure Docker Desktop is running before executing commands.

Kafka container name must be kafka as defined in docker-compose.yml.

Port 29092 should match your Kafka advertised listener configuration.
