# User Service

## Overview

Manages user profiles and data:
- Customer, Driver, and Store profiles
- Profile updates and management
- Integration with Auth Service

## Technologies

- Java / Spring Boot
- PostgreSQL
- Docker

## Setup

1. Configure DB credentials in `.env`
2. Build and run:
```bash
mvn clean package
```
3. Build Docker image and run:
```bash
docker build -t user-service .
docker run -p 8082:8082 user-service
```

## Notes

- Exposes REST API for profile management.
- Communicates with Auth Service for authentication.
