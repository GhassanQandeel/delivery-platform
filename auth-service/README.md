# Auth Service

## Overview

Handles user authentication and authorization:
- Login / Registration
- JWT token issuance and validation
- Role management: Customer, Store, Driver, Admin

## Technologies

- Java / Spring Boot
- PostgreSQL
- Docker

## Setup

1. Configure `.env` or `application.yml` with DB credentials
2. Build:
```bash
mvn clean package
```
3. Run Docker container:
```bash
docker build -t auth-service .
docker run -p 8081:8081 auth-service
```

## Notes

- Provides JWT tokens for API Gateway.
- Independent DB: `auth_db`.
