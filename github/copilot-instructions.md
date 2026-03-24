## Main Goal

This project aims to build a web application that compares two truck freight options and returns the best one based on a calculated index.

## Business Rule
The comparison must follow this formula:

freightIndex = freightPrice / (freightWeight * distanceInKilometers)


The system must:
- Accept two freight inputs
- Calculate the index for both
- Return the best (highest index = better cost-efficiency)

## Tech Stack (Non-negotiable)
- Java 21 + Spring Boot 3.5.12
- PostgreSQL
- Static frontend don't use frameowrks
- Google Maps API (mandatory for distance calculation)

## Architecture Principles

- Layered architecture (Controller → Service → Domain → Repository)
- **Do NOT bypass the service layer**
- Domain must contain business rules, not controllers
- Avoid anemic domain models
- Prefer explicit code over magic
- External integrations must be isolated (client package)

## Suggested Design Patterns
- Strategy Pattern → for freight comparison logic (future extensibility)
- Factory Pattern → for creating freight calculation strategies
- DTO Pattern → for input/output isolation
- Repository Pattern → persistence abstraction

## Project Structure (Monorepo)

Rota-Certa/
├── docker-compose.yml
├── README.md
├── backend/
│ ├── pom.xml
│ ├── src/
│ │ ├── main/java/com/miranda_gs/rotacerta/
│ │ │ ├── RotacertaApplication.java
│ │ │ ├── controller/ # HTTP layer (no business logic)
│ │ │ ├── service/ # orchestration layer
│ │ │ ├── model/ # domain entities
│ │ │ ├── repository/ # data access
│ │ │ ├── dto/ # request/response objects
│ │ │ ├── client/ # external APIs (Google Maps)
│ │ │ └── exception/ # error handling
│ │ ├── resources/
│ │ │ ├── application.yaml
│ │ │ ├── static/
│ │ │ └── templates/
│ │ └── test/java/com/miranda_gs/rotacerta/
│ │ └── RotacertaApplicationTests.java
│
├── frontend/
│ └── src/
│
└── github/
└── copilot-instructions.md

## TDD Guidelines

- Write tests **before** implementation
- Unit test all domain rules (freight calculation is mandatory)
- Integration test critical flows (API + database)
- Mock external dependencies (Google Maps API)
- Prefer small, deterministic tests

## Engineering Rules

- No business logic inside controllers
- No direct database access outside repositories
- Services orchestrate, domain decides
- Always validate input via DTOs
- Keep methods small and intention-revealing
- Fail fast on invalid data
