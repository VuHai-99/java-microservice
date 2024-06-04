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

![System Architecture](https://drive.google.com/uc?export=view&id=11RUahBS5cdprsIZ-vO9XDZCabSefA0-b)

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

### Code structure
- **Common**: A common module which shared/used between child module.
- **Module**: Each service is contains of several part:
    - ***Application***: For public rest APIs.
    - ***Order Container***: For initialize service and infrastructure configurations.
    - ***Order Access***: Create data access of all other microservices entity. Each sub-module contains:
        - ***Adapter***: Implementation of <u><em><strong>Output Port</strong></em></u>. 
        - ***Entity***: Business level entity.
        - ***Mapper***: Mapper from Core Entity to Domain Level Entity 
        - ***Repository***: Direct read/write to DB
    - ***Order Domain***: Control core logic & core entity. Each sub-module contains:
        - ***Order Application***: 
            - ***Config***: Constant value for config
            - ***Dto***: Dto for input & output port of the service
            - ***Mapper***: Mapper from input DTO into Core Entity to handlig
            - ***Port***: Declare interface for input & output port function
        - ***Order Domain Core***: Controls ObjectValue and Core Entity
    - ***Order Messaging***: Implement event-driven function. Each sub-module contains:
        - ***Mapper***: Mapping Domain Level Entity, Core Entity to Event Data Entity
        - ***Publisher/Consumer***: Implementation of <u><em><strong>Port (Order Application)</strong></em></u> to handle event-based request.
- **Infrastructure**: K8s configurations for all services in the system. Contains:
    - Postgres
    - ZooKeeper
    - Kafka