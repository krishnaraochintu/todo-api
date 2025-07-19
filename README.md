# TODO API Spring Boot

This is a backend-only REST API for managing TODO items, built with Spring Boot. Supports H2 (in-memory, default), PostgreSQL, and MySQL databases via Spring profiles.

## Features
- CRUD operations for TODO items
- PostgreSQL database integration

## Getting Started

### Build & Run

**Local build:**
```bash
./gradlew build
```

**Run locally:**
- H2 (default, in-memory):
  ```bash
  java -jar build/libs/todo-api-0.0.1-SNAPSHOT.jar
  ```
- PostgreSQL:
  ```bash
  SPRING_PROFILES_ACTIVE=postgres DB_HOST=localhost DB_PORT=5432 DB_NAME=tododb DB_USERNAME=youruser DB_PASSWORD=yourpass java -jar build/libs/todo-api-0.0.1-SNAPSHOT.jar
  ```
- MySQL:
  ```bash
  SPRING_PROFILES_ACTIVE=mysql DB_HOST=localhost DB_PORT=3306 DB_NAME=tododb DB_USERNAME=root DB_PASSWORD=yourpass java -jar build/libs/todo-api-0.0.1-SNAPSHOT.jar
  ```

**Docker build:**
```bash
docker build -t todo-api .
```

**Run with Docker:**
- H2 (default, in-memory):
  ```bash
  docker run -p 8080:8080 todo-api
  ```
- PostgreSQL:
  ```bash
  docker run -p 8080:8080 -e SPRING_PROFILES_ACTIVE=postgres -e DB_HOST=host -e DB_PORT=5432 -e DB_NAME=db -e DB_USERNAME=user -e DB_PASSWORD=pass todo-api
  ```
- MySQL:
  ```bash
  docker run -p 8080:8080 -e SPRING_PROFILES_ACTIVE=mysql -e DB_HOST=host -e DB_PORT=3306 -e DB_NAME=db -e DB_USERNAME=user -e DB_PASSWORD=pass todo-api
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
2. Build the JAR:
   ```bash
   ./gradlew build
   ```
3. Run with the desired profile:
   - H2 (default, in-memory):
     ```bash
     java -jar build/libs/todo-api-0.0.1-SNAPSHOT.jar
     ```
   - PostgreSQL:
     ```bash
     SPRING_PROFILES_ACTIVE=postgres DB_HOST=localhost DB_PORT=5432 DB_NAME=tododb DB_USERNAME=youruser DB_PASSWORD=yourpass java -jar build/libs/todo-api-0.0.1-SNAPSHOT.jar
     ```
   - MySQL:
     ```bash
     SPRING_PROFILES_ACTIVE=mysql DB_HOST=localhost DB_PORT=3306 DB_NAME=tododb DB_USERNAME=root DB_PASSWORD=yourpass java -jar build/libs/todo-api-0.0.1-SNAPSHOT.jar
     ```

## Production Deployment


## Container Deployment


To deploy with Docker:

1. **Build the app JAR:**

   ```bash
   ./gradlew build
   ```

2. **Prepare a Dockerfile** in the project root:

   ```dockerfile
   FROM eclipse-temurin:21-jre
   WORKDIR /app
   COPY build/libs/todo-api-0.0.1-SNAPSHOT.jar app.jar
   EXPOSE 8080
   ENTRYPOINT ["java", "-jar", "app.jar"]
   ```

3. **Build the Docker image:**

   ```bash
   docker build -t todo-api .
   ```

4. **Run the container:**
   - For in-memory H2 (default):

     ```bash
     docker run -p 8080:8080 todo-api
     ```

   - For PostgreSQL:

     ```bash
     docker run -p 8080:8080 \
       -e SPRING_PROFILES_ACTIVE=postgres \
       -e DB_HOST=prod-db-host \
       -e DB_PORT=5432 \
       -e DB_NAME=prod_db \
       -e DB_USERNAME=prod_user \
       -e DB_PASSWORD=prod_pass \
       todo-api
     ```

   - For MySQL:

     ```bash
     docker run -p 8080:8080 \
       -e SPRING_PROFILES_ACTIVE=mysql \
       -e DB_HOST=prod-db-host \
       -e DB_PORT=3306 \
       -e DB_NAME=prod_db \
       -e DB_USERNAME=prod_user \
       -e DB_PASSWORD=prod_pass \
       todo-api
     ```
