## Cloud Marketplace

Cloud Marketplace is a personal project focused on building and evolving a microservices-based application using the
Java ecosystem.

The project explores backend architecture, distributed systems, service integration, and cloud-native development
practices through practical implementation.

### Architecture

The application is organized as a set of independently developed services, each responsible for a specific business
capability.

The current architecture includes synchronous HTTP communication between services, separate persistence layers, and
containerized local development environments.

#### Services

| Service                                                                            | Technology Stack                                           | Description                                                                       |
|------------------------------------------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------------------------------|
| [Menu Service](https://github.com/AlekseyBykov/cloud-marketplace-menu-service)     | Spring Boot, Spring MVC, Spring Data JPA, PostgreSQL       | Manages menu items and provides pricing information to other services.            |
| [Orders Service](https://github.com/AlekseyBykov/cloud-marketplace-orders-service) | Spring Boot, Spring WebFlux, Spring Data R2DBC, PostgreSQL | Handles order creation, retrieves menu information, and persists order snapshots. |

#### Service Communication

Orders Service communicates with Menu Service through a synchronous HTTP API using Spring WebClient.

During order creation:

1. Orders Service receives an order request.
2. Menu Service resolves the requested menu items and their prices.
3. Orders Service validates the resolved information.
4. The order is persisted with a snapshot of its items and prices.

This approach keeps order history independent of subsequent menu price changes.

### Technology Stack

- **Language:** Java 21
- **Framework:** Spring Boot
- **Web:** Spring MVC, Spring WebFlux
- **Persistence:** Spring Data JPA, Spring Data R2DBC
- **Database:** PostgreSQL
- **Database migrations:** Flyway
- **Build:** Gradle
- **Testing:** JUnit 5, Testcontainers, WireMock, MockWebServer
- **Infrastructure:** Docker, Docker Compose
- **CI:** GitHub Actions (Menu Service)

The services intentionally use different persistence and web programming models to explore their characteristics and
trade-offs.

### Development

Cloud Marketplace is an evolving project. Development is organized around GitHub Issues, pull requests, and documented
architectural decisions.

**[Development Board](https://github.com/users/AlekseyBykov/projects/2)** — current tasks, completed work, and planned
improvements.

#### Planned Improvements

- Strengthen validation and error handling across service boundaries.
- Introduce order lifecycle management.
- Implement asynchronous communication and event-driven workflows.
- Explore reliable event publishing and idempotent processing.
- Add centralized observability and distributed tracing.
- Improve automated testing and CI/CD workflows.

These are planned directions rather than implemented features.

### Project Background

The project was initially inspired by the [JavaOps](https://javaops.ru/) training program and is being developed further
as an independent learning and engineering initiative.

Its primary goal is to gain practical experience in designing, implementing, testing, and operating modern Java backend
systems.

### License

License information will be added separately.
