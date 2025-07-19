# TODO API Spring Boot

This is a backend-only REST API for managing TODO items, built with Spring Boot and PostgreSQL.

## Features
- CRUD operations for TODO items
- PostgreSQL database integration

## Getting Started
1. Configure your PostgreSQL database in `src/main/resources/application.properties` (or use environment variables).
2. Build the JAR file:
   ```bash
   ./gradlew build
   ```
3. Run the application with environment variables:
   ```bash
   DB_HOST=localhost DB_PORT=5432 DB_NAME=tododb DB_USERNAME=youruser DB_PASSWORD=yourpass java -jar build/libs/todo-api-0.0.1-SNAPSHOT.jar
   ```
   Replace values as needed for your setup.

## API Endpoints
- `GET /todos` - List all TODOs
- `POST /todos` - Create a new TODO
- `GET /todos/{id}` - Get a TODO by ID
- `PUT /todos/{id}` - Update a TODO
- `DELETE /todos/{id}` - Delete a TODO

## Requirements
- Java 17+
- PostgreSQL
- Gradle
