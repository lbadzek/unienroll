
# UniEnroll – University Course Enrolment System

## Project Information

- **Project:** P02 – University Course Enrolment
- **Course:** Rapid Development of Java Applications Using Programming Frameworks
- **Academic Year:** 2026/2027
- **Student:** Luka Badžek

## Project Description

UniEnroll is a web application for managing university
course enrolments.

Students will be able to browse available courses,
check prerequisites, enrol in courses and monitor
their enrolment status.

University administrators will manage courses,
prerequisites, enrolment periods and course capacity.

## Technology Stack

- Java 25
- Spring Boot 4.1.2
- Maven
- Thymeleaf
- Spring Data JPA / Hibernate
- PostgreSQL 17
- Flyway
- Docker Compose
- Bootstrap (planned)
- Spring Security (planned)

## Main Features (Planned)

- Student course enrolment
- Course prerequisite validation
- Circular prerequisite detection
- Configurable enrolment windows
- Maximum ECTS credits per semester
- Course capacity management
- Waiting lists with automatic promotion
- AI-assisted prerequisite explanations
- Croatian and English language support

## Architecture

The application follows a layered architecture:

- Controller layer
- Service layer
- Repository layer
- Database layer

Spring Data JPA will be used for database access.

Flyway will manage database schema migrations.

## Database

Database: PostgreSQL 17

Database name: unienroll

The database runs locally using Docker Compose.

Start the database:

```bash
docker compose up -d
```

Check running containers:

```bash
docker ps
```

## Running the Application

Requirements:
- Java 25
- Docker Desktop
- Maven Wrapper (included in the project)

Start PostgreSQL:

```bash
docker compose up -d
```

Run the Spring Boot application:

```powershell
.\mvnw.cmd spring-boot:run
```

The application starts at:

http://localhost:8080

Note: Application screens and business features
are not yet implemented.

## Figma Design

The UI/UX design was created using Figma.

**Figma project:**

https://www.figma.com/design/M8ZcCAaGFDiMqd6wpmKTU0/UniEnroll-%E2%80%93-University-Course-Enrolment-System

The Figma project contains three pages:

1. 01 Wireframes
2. 02 Components
3. 03 High-Fidelity Screens

The interactive prototype will be completed later.

## Planned Hosting and AI Integration

- **Application hosting:** Render
- **Managed database:** Neon PostgreSQL
- **AI provider:** OpenAI API

The AI feature will explain missing course prerequisites
and suggest a valid study plan for the next two semesters.

Enrolment eligibility will always be determined by
application business rules, not by AI.

## Documentation

- [Entity Diagram](docs/entity-diagram.md)
- [ADR-001: Database Choice](docs/adr/001-database-choice.md)

## Milestone M1

- [x] Project topic selected
- [x] Spring Boot project created
- [x] Java 25 and Maven configured
- [x] PostgreSQL running in Docker
- [x] Spring Boot connected to PostgreSQL
- [x] Initial entity diagram prepared
- [x] First architecture decision record prepared
- [x] Low-fidelity Figma wireframes created
- [x] Hosting platform and AI provider selected
- [ ] GitHub repository created

## Current Limitations

This is the initial project setup for Milestone M1.

The application does not yet implement user
authentication, enrolment functionality, REST APIs,
scheduled jobs or AI integration.

These features will be developed in later milestones.
