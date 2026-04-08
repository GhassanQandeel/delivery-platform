# API Gateway

## Overview

The API Gateway serves as the single entry point for all client requests. It handles:
- Routing to microservices
- JWT authentication
- Security (CORS, rate-limiting)
- Logging and monitoring

## Technologies

- Java / Spring Cloud Gateway
- Docker

## Setup

1. Install Java 17+
2. Configure `application.yml` with microservice URLs
3. Build with Maven:
```bash
mvn clean package
```
4. Run with Docker:
```bash
docker build -t api-gateway .
docker run -p 8080:8080 api-gateway
```

## Notes

- All frontend requests must go through this gateway.
- JWT validation is centralized here.
