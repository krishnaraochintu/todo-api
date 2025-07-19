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

## Local Development

1. Clone the repository and install Java 21+ and Gradle.
2. Build and run with the default in-memory database:
   ```bash
   ./gradlew bootRun
   ```
   or
   ```bash
   java -jar build/libs/todo-api-0.0.1-SNAPSHOT.jar
   ```
3. For PostgreSQL/MySQL, set the profile and environment variables as shown above.

## Production Deployment

1. Build the JAR:
   ```bash
   ./gradlew build
   ```
2. Set up a production database (PostgreSQL/MySQL) and configure environment variables.
3. Run the JAR with the appropriate profile and environment variables:
   ```bash
   SPRING_PROFILES_ACTIVE=postgres DB_HOST=prod-db-host DB_PORT=5432 DB_NAME=prod_db DB_USERNAME=prod_user DB_PASSWORD=prod_pass java -jar build/libs/todo-api-0.0.1-SNAPSHOT.jar
   ```
   or for MySQL:
   ```bash
   SPRING_PROFILES_ACTIVE=mysql DB_HOST=prod-db-host DB_PORT=3306 DB_NAME=prod_db DB_USERNAME=prod_user DB_PASSWORD=prod_pass java -jar build/libs/todo-api-0.0.1-SNAPSHOT.jar
   ```

## Containerization

1. Create a `Dockerfile` in the project root:
   ```dockerfile
   FROM eclipse-temurin:21-jre
   WORKDIR /app
   COPY build/libs/todo-api-0.0.1-SNAPSHOT.jar app.jar
   EXPOSE 8080
   ENTRYPOINT ["java", "-jar", "app.jar"]
   ```
2. Build the Docker image:
   ```bash
   docker build -t todo-api .
   ```
3. Run the container (in-memory DB):
   ```bash
   docker run -p 8080:8080 todo-api
   ```
4. For PostgreSQL/MySQL, pass environment variables:
   ```bash
   docker run -p 8080:8080 -e SPRING_PROFILES_ACTIVE=postgres -e DB_HOST=host -e DB_PORT=5432 -e DB_NAME=db -e DB_USERNAME=user -e DB_PASSWORD=pass todo-api
   ```
