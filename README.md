# 🎮 GameSphere — Java Microservices Gaming Platform

**A scalable, cloud-native gaming backend built with Java and Spring Boot.**

GameSphere is a backend engineering project designed to demonstrate how gaming platforms can manage player profiles, game sessions, leaderboards, and service health through REST APIs and modular backend services.

The project focuses on clean code, microservices architecture, database integration, automated testing, containerization, and observability — core engineering practices for building reliable, high-performance software platforms.

## 🚀 Project Objectives

- Build RESTful backend APIs for common gaming platform operations.
- Apply object-oriented programming, data structures, and clean-code principles.
- Design modular services that can evolve toward a distributed microservices architecture.
- Persist player and game-session data using PostgreSQL.
- Improve reliability through automated tests and continuous integration.
- Monitor application health and performance using observability tools.

## ✨ Key Features

### 👤 Player Management
- Create and retrieve player profiles.
- Validate incoming requests and handle invalid data.
- Support updating player information.
- Use unique identifiers to manage player records.

### 🎯 Game Session Management
- Create and retrieve game sessions.
- Track session status and player participation.
- Record session timestamps and relevant game metadata.
- Handle invalid session requests with meaningful API responses.

### 🏆 Leaderboard
- Store player scores and retrieve rankings.
- Sort players by score.
- Support pagination for leaderboard results.
- Use database queries to retrieve ranking data efficiently.

### 🩺 Application Health and Observability
- Expose application health information using Spring Boot Actuator.
- Add structured application logging.
- Measure selected application metrics.
- Prepare the service for integration with monitoring tools such as Prometheus and Grafana.

### 🧪 Testing and Code Quality
- Write unit tests using JUnit 5 and Mockito.
- Test request validation and error-handling scenarios.
- Verify API behavior with integration tests.
- Run automated tests through GitHub Actions.

### 🐳 Containerization
- Package the application using Docker.
- Configure PostgreSQL for local development.
- Use environment variables for application configuration.
- Document how to run the application locally.

## 🏗️ Architecture

The initial implementation can start as a modular Spring Boot application, with clear boundaries between player management, game sessions, and leaderboard functionality.

The modules can later be extracted into independent microservices.

```text
                 Client / API Consumer
                          |
                          v
                  REST API Layer
                          |
             +------------+------------+
             |            |            |
             v            v            v
        Player Module  Session Module  Leaderboard Module
             |            |            |
             +------------+------------+
                          |
                          v
                      PostgreSQL
                          |
                          v
                Logging and Metrics
```

**Future distributed architecture:**

```text
             API Gateway
                  |
       +----------+----------+
       |          |          |
       v          v          v
   Player      Session   Leaderboard
   Service     Service     Service
       |          |          |
       +----------+----------+
                  |
           Database Layer
                  |
          Monitoring Stack
```

The distributed architecture is a planned extension unless the individual services have already been implemented.

## 🛠️ Technology Stack

| Category | Technology |
|---|---|
| Language | Java 17+ |
| Backend | Spring Boot |
| API | REST, JSON, HTTP |
| Database | PostgreSQL |
| Data Access | Spring Data JPA, Hibernate |
| Testing | JUnit 5, Mockito |
| Build Tool | Maven |
| Containerization | Docker |
| CI/CD | GitHub Actions |
| Observability | Spring Boot Actuator, Micrometer |
| Version Control | Git, GitHub |

## 📋 Prerequisites

Install the following tools before running the application:

- Java Development Kit (JDK) 17 or later.
- Maven, or use the Maven Wrapper included in the project.
- PostgreSQL.
- Git.
- Docker (optional, for containerized execution).

## ⚙️ Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/mallikarjun-git7/gamesphere-java-microservices.git
cd gamesphere-java-microservices
```

### 2. Configure the database

Create a PostgreSQL database:

```sql
CREATE DATABASE gamesphere;
```

Configure the database connection using environment variables or your local Spring Boot configuration.

Example environment variables:

```bash
export DB_URL=jdbc:postgresql://localhost:5432/gamesphere
export DB_USERNAME=postgres
export DB_PASSWORD=your_local_password
```

Use your own local credentials. Never commit real passwords, API keys, or other secrets to GitHub.

### 3. Build the application

For a project using the Maven Wrapper:

```bash
./mvnw clean package
```

On Windows:

```bash
mvnw.cmd clean package
```

If the Maven Wrapper is not included, install Maven and run:

```bash
mvn clean package
```

### 4. Run the application

```bash
./mvnw spring-boot:run
```

The application will typically start at:

```text
http://localhost:8080
```

The actual port and available endpoints depend on your application configuration.

## 🔌 API Design

The following is the proposed API design. Implement the endpoints before treating them as available.

| Method | Endpoint | Purpose |
|---|---|---|
| POST | `/api/players` | Create a player |
| GET | `/api/players/{id}` | Retrieve a player |
| GET | `/api/players` | List players |
| PUT | `/api/players/{id}` | Update a player |
| POST | `/api/sessions` | Create a game session |
| GET | `/api/sessions/{id}` | Retrieve a game session |
| GET | `/api/leaderboard` | Retrieve ranked scores |
| GET | `/actuator/health` | Check application health |

Example player creation request:

```json
{
  "username": "player_one",
  "displayName": "Player One"
}
```

Example successful response:

```json
{
  "id": 1,
  "username": "player_one",
  "displayName": "Player One"
}
```

These JSON examples illustrate the intended API contract; actual responses depend on your implementation.

## 🧪 Running Tests

Run the automated test suite:

```bash
./mvnw test
```

Recommended test coverage includes:

- Player creation and retrieval.
- Invalid request validation.
- Missing player and session handling.
- Leaderboard sorting and pagination.
- Database repository behavior.
- REST API integration tests.

## 🐳 Docker

Once a Dockerfile and the required configuration are implemented, build the application image:

```bash
docker build -t gamesphere:latest .
```

Run the image:

```bash
docker run --rm -p 8080:8080 gamesphere:latest
```

Database connectivity and environment variables must be configured for the containerized application to work correctly.

## 🔄 Continuous Integration

Configure GitHub Actions to automatically:

1. Check out the repository.
2. Set up the required JDK.
3. Build the application using Maven.
4. Run automated tests.
5. Report build and test results.

A successful CI workflow helps catch regressions before changes are merged.

## 📈 Performance and Reliability Goals

GameSphere is intended to explore practical backend engineering concerns, including:

- Efficient database access and pagination.
- Input validation and predictable error responses.
- Stateless REST API design where appropriate.
- Service health checks and useful application metrics.
- Automated testing and repeatable builds.
- Containerized deployment and configuration management.

Performance improvements should be measured through repeatable tests rather than assumed from the architecture alone.

## 🗺️ Roadmap

- [ ] Implement the Spring Boot application structure.
- [ ] Add player management APIs.
- [ ] Add game-session APIs.
- [ ] Integrate PostgreSQL and Spring Data JPA.
- [ ] Implement leaderboard ranking and pagination.
- [ ] Add request validation and global exception handling.
- [ ] Write unit and integration tests.
- [ ] Add a GitHub Actions CI workflow.
- [ ] Containerize the application with Docker.
- [ ] Add health checks, logging, and metrics.
- [ ] Explore service discovery and an API gateway.
- [ ] Evaluate caching and distributed service communication.

## 🎯 Relevance to Backend Engineering

This project provides a practical setting for learning and demonstrating:

- Java and object-oriented programming.
- REST API development.
- SQL databases and data modeling.
- Automated testing and code maintainability.
- Docker and CI/CD fundamentals.
- Application monitoring and troubleshooting.
- Microservices and distributed-system design.

These skills align with responsibilities commonly found in Java backend engineering and cloud-platform internships, including the EA Digital Platform internship.

## 🤝 Contributing

Contributions and suggestions are welcome.

1. Fork the repository.
2. Create a feature branch.
3. Make your changes and add tests.
4. Submit a pull request describing the changes.

## 📄 License

Choose and add an appropriate open-source license if you intend to distribute the project under its terms. Until a license is added, the repository should not be assumed to grant general reuse permissions.

## 👨‍💻 Author

**Mallikarjun**

GitHub: [@mallikarjun-git7](https://github.com/mallikarjun-git7)

---

*Built as a hands-on project to explore Java backend engineering, gaming platform services, software quality, and cloud-native development.*
