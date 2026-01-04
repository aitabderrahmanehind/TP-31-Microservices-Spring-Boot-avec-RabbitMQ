# Microservices Messaging Producer

## Overview
This is a Spring Boot application acting as a **Producer** for RabbitMQ. It exposes a REST API to send user messages to a specific RabbitMQ exchange.

## Prerequisites
- **Java 17** or higher
- **Maven**
- **RabbitMQ** running on `localhost:5672`

## Configuration
The application is configured in `src/main/resources/application.yml`:
- **Server Port**: `8081`
- **RabbitMQ Host**: `localhost`
- **Exchange**: `user.exchange`
- **Routing Key**: `user.routingkey`

## How to Run
1. Ensure RabbitMQ is running.
2. Run the application using Maven:
   ```bash
   mvn spring-boot:run
   ```

## Usage
Send a POST request to produce a message:

**Endpoint**: `POST http://localhost:8081/api/produce`

**Body** (JSON):
```json
{
  "userId": "1",
  "userName": "oussama"
}
```

**Response**:
`user sent: User(userId=1, userName=oussama)`
