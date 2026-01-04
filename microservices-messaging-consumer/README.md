# Microservices Messaging Consumer

## Overview
This is a Spring Boot application acting as a **Consumer** for RabbitMQ. It listens to a queue and persists received user messages into a MySQL database.

## Prerequisites
- **Java 17** or higher
- **Maven**
- **RabbitMQ** running on `localhost:5672`
- **MySQL** running on `localhost:3306`

## Configuration
The application is configured in `src/main/resources/application.yml`:
- **Server Port**: `8080`
- **Database**: `testdb` (ensure this exists)
- **Queue**: `user.queue`

## How to Run
1. Ensure RabbitMQ and MySQL are running.
2. Create the database `testdb` in MySQL if it doesn't exist.
3. Run the application using Maven:
   ```bash
   mvn spring-boot:run
   ```

## Behavior
- The application automatically connects to RabbitMQ and creates the necessary Exchange, Queue, and Binding.
- It listens for messages on `user.queue`.
- When a message is received, it is saved to the `user` table in the MySQL database.
- You can verify the data by querying the database:
  ```sql
  SELECT * FROM testdb.user;
  ```
