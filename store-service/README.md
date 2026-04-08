# Store Service

## Overview

Manages stores and products:
- CRUD for store products
- Order management
- Chat support integration

## Technologies

- Java / Spring Boot
- PostgreSQL
- Docker

## Setup

1. Configure DB in `.env`
2. Build:
```bash
mvn clean package
```
3. Run Docker container:
```bash
docker build -t store-service .
docker run -p 8083:8083 store-service
```

## Notes

- Stores receive orders and update product availability.
