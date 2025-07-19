# TODO API Spring Boot

This is a backend-only REST API for managing TODO items, built with Spring Boot. Supports H2 (in-memory, default), PostgreSQL, and MySQL databases via Spring profiles.

## Features
- CRUD operations for TODO items
- PostgreSQL database integration

## Getting Started
1. Build the JAR file:
   ```bash
   ./gradlew build
   ```

2. By default, the app uses an in-memory H2 database (no setup required).
   ```bash
   java -jar build/libs/todo-api-0.0.1-SNAPSHOT.jar
   ```

3. To use PostgreSQL, set the profile and connection details:
   ```bash
   SPRING_PROFILES_ACTIVE=postgres DB_HOST=localhost DB_PORT=5432 DB_NAME=tododb DB_USERNAME=youruser DB_PASSWORD=yourpass java -jar build/libs/todo-api-0.0.1-SNAPSHOT.jar
   ```

4. To use MySQL, set the profile and connection details:
   ```bash
   SPRING_PROFILES_ACTIVE=mysql DB_HOST=localhost DB_PORT=3306 DB_NAME=tododb DB_USERNAME=root DB_PASSWORD=yourpass java -jar build/libs/todo-api-0.0.1-SNAPSHOT.jar
   ```

See `src/main/resources/application-*.properties` for profile-specific settings.

## API Endpoints
- `GET /todos` - List all TODOs
- `POST /todos` - Create a new TODO
- `GET /todos/{id}` - Get a TODO by ID
- `PUT /todos/{id}` - Update a TODO
- `DELETE /todos/{id}` - Delete a TODO

## Requirements
- Java 21+
- Gradle
- H2 (default, in-memory)
- PostgreSQL (optional)
- MySQL (optional)
