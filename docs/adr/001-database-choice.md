
# ADR-001: Use PostgreSQL as the Primary Database

**Status:** In progress

**Date:** 2026-11-01

## Context

UniEnroll is a university course enrolment system built
with Spring Boot.

The application manages students, courses, enrolments,
course prerequisites, semester limits and waiting lists.

The database must support relationships between entities,
data consistency and concurrent enrolment requests.

The project also requires a relational database,
database migrations and deployment to a free
hosting service.

## Decision

It is decided to use PostgreSQL 17 as the primary database.

During development, PostgreSQL runs inside a Docker
container using Docker Compose.

Spring Data JPA and Hibernate are used to map Java
entities to database tables.

Flyway manages database schema migrations instead
of Hibernate automatically creating the tables.

## Alternatives Considered

### H2 Database

H2 is lightweight and easy to configure.

However, it is not suitable as the final database
because the project requires PostgreSQL or MySQL.

It may still be useful for quick development tests.

### MySQL

MySQL is a relational database with good Spring Boot
support and would also satisfy the assignment.

However, PostgreSQL was selected because of its
strong support for constraints, transactions and
complex relational queries.

## Consequences

### Positive

- PostgreSQL supports relational integrity.
- Transactions help maintain consistent enrolment data.
- Docker makes the development environment reproducible.
- Flyway provides version-controlled database migrations.
- PostgreSQL can later be hosted using Neon.

### Negative

- Docker must be installed and running during development.
- Database migrations require additional maintenance.
- PostgreSQL configuration is more complex than H2.
- Concurrent enrolments still require carefully
  implemented transaction and locking strategies.

## Conclusion

PostgreSQL provides a reliable foundation for UniEnroll.

It supports the relational model and consistency
requirements of the application and satisfies
the database requirements of the course.
