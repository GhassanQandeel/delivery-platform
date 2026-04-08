# Order Service

## Overview

Handles the complete order lifecycle:
- Create orders
- Track status: Pending, Accepted, Picked, Delivered
- Event-driven communication with Delivery, Store, and Subscription services

## Technologies

- Java / Spring Boot
- PostgreSQL
- RabbitMQ / Kafka
- Docker

## Setup

1. Configure DB and message broker credentials
2. Build and run:
```bash
mvn clean package
```
3. Build Docker image and run:
```bash
docker build -t order-service .
docker run -p 8084:8084 order-service
```

## Notes

- Publishes events for order status changes.
- Subscribed by Delivery and Store services.
