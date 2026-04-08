# Delivery Service

## Overview

Manages drivers and delivery assignments:
- Driver availability
- Accept/reject orders
- Delivery tracking

## Technologies

- Java / Spring Boot
- PostgreSQL
- RabbitMQ / Kafka
- Docker

## Setup

1. Configure DB and broker credentials
2. Build:
```bash
mvn clean package
```
3. Run Docker container:
```bash
docker build -t delivery-service .
docker run -p 8085:8085 delivery-service
```

## Notes

- Subscribes to Order events.
- Updates order status for customers and stores.
