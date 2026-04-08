# Rating Service

## Overview

Manages ratings and reviews:
- Store ratings
- Driver ratings
- Visibility and sorting logic

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
docker build -t rating-service .
docker run -p 8087:8087 rating-service
```

## Notes

- Provides endpoints for customers to submit ratings.
- Used by Store and Delivery services for visibility calculation.
