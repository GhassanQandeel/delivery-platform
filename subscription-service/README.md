# Subscription Service

## Overview

Manages subscription plans for stores and drivers:
- Plan management
- Subscription activation/deactivation
- Restrict access based on subscription status

## Technologies

- Java / Spring Boot
- PostgreSQL
- Docker

## Setup

1. Configure DB credentials
2. Build:
```bash
mvn clean package
```
3. Run Docker container:
```bash
docker build -t subscription-service .
docker run -p 8086:8086 subscription-service
```

## Notes

- Subscription status affects order processing and driver/store visibility.
