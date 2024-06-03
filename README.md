# Food Ordering System Microservice Backend

Welcome to the Food Ordering System Microservice Backend! This project is designed to provide a scalable, efficient, and robust backend for a food ordering system. Below, you'll find the detailed information about the tech stack, architecture, and key patterns used in this project.

## Tech Stack

- **Java Spring Boot**: A powerful, production-ready framework for building Java applications.
- **Kafka**: A distributed streaming platform for building real-time data pipelines and streaming applications.
- **Postgres**: A powerful, open-source object-relational database system.
- **Saga Pattern**: For managing distributed transactions and ensuring data consistency across services.
- **Domain-Driven Design (DDD)**: For structuring the system around the business domain.
- **Hexagonal Architecture**: For creating maintainable and testable code by separating core business logic from external concerns.
- **Change Data Capture (CDC)**: For tracking changes in the database.
- **Outbox Pattern**: For reliable message delivery in distributed systems.

## Architecture Overview

The system is built following the principles of Domain-Driven Design (DDD) and Hexagonal Architecture. This approach ensures that the core business logic is isolated from external systems like databases and message brokers, promoting better testability and maintainability.

### Key Components

- **Order Service**: Manages the lifecycle of orders, from creation to fulfillment.
- **Payment Service**: Handles payment processing and ensures transaction consistency.

### Communication

- **Event-Driven Architecture**: Services communicate asynchronously through Kafka, ensuring decoupling and scalability.
- **Saga Pattern**: Used for coordinating long-running transactions and handling failures gracefully.

### Data Management

- **Postgres**: Used as the primary database for persisting data.
- **Change Data Capture (CDC)**: Utilized for monitoring and capturing data changes in the database, ensuring data consistency across services.
- **Outbox Pattern**: Ensures reliable message delivery by storing messages in the database and sending them through Kafka.

