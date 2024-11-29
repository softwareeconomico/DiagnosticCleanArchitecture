# Clean Architecture Project Template

A template for implementing **Clean Architecture**, designed to separate concerns, enhance scalability, and facilitate testing and maintenance.

---

## **Table of Contents**
- [Introduction](#introduction)
- [Principles of Clean Architecture](#principles-of-clean-architecture)
- [Project Structure](#project-structure)
- [Layer Descriptions](#layer-descriptions)
- [Getting Started](#getting-started)
- [Tests](#tests)
- [Why Use This Architecture?](#why-use-this-architecture)

---

## **Introduction**

Clean Architecture, introduced by **Robert C. Martin**, is a design paradigm focused on creating systems that are:
- **Independent of frameworks**: No framework dictates the architecture.
- **Testable**: Business rules can be tested without external dependencies.
- **Independent of UI**: Changes in UI should not affect the core logic.
- **Independent of databases**: The business logic doesn't depend on specific database implementations.
- **Independent of external systems**: Systems are built to be adaptable and resilient to changes.

This repository provides a clear structure and guidelines for organizing a project according to these principles.

---

## **Principles of Clean Architecture**

1. **Dependency Rule**: Code dependencies must point inward, toward the higher-level policies (Core/Business Logic).
2. **Separation of Concerns**: Each layer handles specific responsibilities without overlapping.
3. **Testability**: Business logic should be testable in isolation.

---

## **Project Structure**

```
/myapp
  /core
    /entities         # Core Layer: Domain entities representing business concepts
    /usecases         # Core Layer: Application-specific business rules and workflows
  /application
    /interfaces       # Application Layer: Defines contracts for communication between the Core and external systems
  /infrastructure
    /data             # Infrastructure Layer: Handles data access logic, such as interacting with databases
    /frameworks       # Infrastructure Layer: Framework-specific configurations and tools
    /services         # Infrastructure Layer: External system integrations, such as email, APIs, and payment processors
  /presentation
    /forms            # Presentation Layer: User interface elements such as forms or web pages
    /adapters         # Presentation Layer: Translates data between the UI and the business logic layer
  /tests
    /core
      /entities       # Tests for core layer entities and business logic
      /use_cases      # Tests for core use cases and workflows
    /application      # Tests for application interfaces and business rules
    /infrastructure   # Tests for infrastructure services, data access, and external integrations
    /presentation     # Tests for presentation layer components, such as forms and adapters
```

---

## **Layer Descriptions**

1. Core
This layer contains the business logic and rules. It is completely isolated from frameworks, databases, and UI.

- Entities: Represent core objects with attributes and methods that define the system's domain.
- Use Cases: Contain the application-specific business rules and workflows.

2. Application
Defines the contracts (interfaces) for interactions between the Core and external systems.

- Interfaces: Abstract contracts for repositories, services, or any external dependency.

3. Infrastructure
Contains the implementations of the interfaces defined in the Application layer. This layer is specific to the technologies used.

- Data: Implementations for interacting with the database or any data source.
- Frameworks: Framework-specific configurations or tools.
- Services: External systems like email services, APIs, or caching mechanisms.

4. Presentation
Handles the interaction with users, either through graphical interfaces, CLI, or API endpoints.

- Forms: UI components or input handlers for user interactions.
- Adapters: Bridges between the presentation layer and use cases.

---

## **Getting Started**

1. Clone the repository:

```bash
git clone https://github.com/your-username/clean-architecture-template.git
cd clean-architecture-template
```

2. Set up the dependencies and tools required for your specific framework or technology stack.

3. Start implementing features by defining:

- Entities in the Core layer.
- Use Cases for your application logic.
- Interfaces to connect Core with external systems.
- Infrastructure implementations for data handling or services.
- Presentation components to interact with the user.

---

## **Tests**

Testing is a fundamental part of Clean Architecture, ensuring that each layer behaves as expected while maintaining its independence.

**Test Structure**
```
/tests
  /core
    /entities       # Unit tests for entities (e.g., domain objects)
    /usecases       # Unit tests for use case logic
  /application
    /interfaces     # Tests for contracts and interface implementations
  /infrastructure
    /data           # Integration tests for data access logic
    /services       # Tests for external service integrations
  /presentation
    /forms          # Tests for UI forms or handlers
    /adapters       # Tests for adapters connecting UI to use cases
```

**Types of Tests**

1. Unit Tests:
- Validate the behavior of isolated components such as entities and use cases.
- Ensure the business logic works independently of external systems.

2. Integration Tests:
- Test interactions between the application and infrastructure layers, such as database access or service API calls.

3. End-to-End (E2E) Tests:
- Simulate user interactions with the presentation layer and verify the entire system's behavior.

---

## **Why Use This Architecture?**

- Maintainability: Changes in one layer have minimal impact on others.
- Scalability: New features can be added without affecting existing logic.
- Flexibility: Easy to switch technologies or frameworks.
- Testability: The isolated layers allow for independent testing.

---