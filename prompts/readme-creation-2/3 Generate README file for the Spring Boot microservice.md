# Task: Create a High-Quality README.md for a Spring Boot Microservice

Act as a Senior Java Engineer, Spring Boot Architect, and Technical Documentation Engineer.

Analyze this microservice thoroughly and create a README.md in its root directory.

The README must be useful for:
1. Developers who need to understand, build, run, test, and maintain the service.
2. AI coding agents that need to understand the service before making code changes.

Do not write generic Spring Boot documentation. Document the actual implementation in this repository.

## 1. Service overview

Document:
- Service name.
- Main responsibility.
- Business capabilities.
- Responsibilities that explicitly do not belong to this service.
- Its role in the overall system.
- Main architectural patterns.

## 2. Technology stack

Document actual versions and technologies:
- Java.
- Spring Boot.
- Spring Framework components.
- Build tool.
- Database technology and access libraries.
- Messaging technologies.
- Security frameworks.
- External integrations.
- Testing frameworks.
- Other important dependencies.

## 3. Architecture and code organization

Explain the package structure and responsibilities.

Document:
- Application entry point.
- Controllers.
- Services.
- Repositories.
- Domain models.
- DTOs.
- Mappers.
- Configuration.
- Exception handling.
- Integration clients.
- Background processing.

Explain how requests and data flow through the application.

Include a Mermaid diagram if useful.

## 4. API documentation

Identify actual API endpoints from the implementation.

For each endpoint, document:
- HTTP method.
- URL.
- Purpose.
- Request parameters.
- Request body.
- Response.
- Relevant HTTP status codes.
- Authentication requirements.
- Important validation rules.

Use an existing OpenAPI specification if available.

Do not invent endpoints or response structures.

## 5. Inter-service communication

Document:
- Other services this service communicates with.
- Communication mechanisms.
- Client implementations.
- Configuration of service addresses.
- Request/response contracts.
- Timeouts and retry policies.
- Failure handling.
- Important coupling and compatibility considerations.

## 6. Database and persistence

Document:
- Database technology.
- Database/schema ownership.
- Entity and repository organization.
- Transaction boundaries.
- Important persistence conventions.
- Database configuration.
- Liquibase integration.
- How schema changes must be coordinated with the Liquibase module.

Explain whether the service owns its schema or shares database structures with other services, based on evidence.

## 7. Configuration reference

Create a table of important configuration properties.

Include:
- Property name.
- Purpose.
- Default value, if explicitly defined.
- Whether it is required.
- Environment variable equivalent, if supported.
- Example format with no real secrets.

Include Spring profiles and configuration precedence.

Do not expose passwords, tokens, private URLs, or other secrets.

## 8. Running locally

Provide verified instructions for:
- Prerequisites.
- Required infrastructure.
- Configuration.
- Build.
- Application startup.
- Local profiles.
- Debugging.

Include exact commands from the actual build configuration.

## 9. Testing

Explain:
- Unit tests.
- Integration tests.
- Test infrastructure.
- Test profiles.
- External dependencies required for testing.
- Commands for executing tests.

## 10. Observability and operations

Document:
- Logging.
- Health endpoints.
- Metrics.
- Distributed tracing.
- Readiness and liveness probes.
- Operational configuration.

Only document features actually implemented.

## 11. Docker and deployment

Document:
- Dockerfile.
- Image building.
- Runtime requirements.
- Environment configuration.
- Kubernetes deployment relationship.
- Helm chart references.

## 12. Important implementation details

Identify non-obvious implementation details that an AI agent should understand before modifying the code.

Examples:
- Business invariants.
- Validation rules.
- Transactional behavior.
- Idempotency requirements.
- Concurrency considerations.
- Error-handling conventions.
- API compatibility constraints.
- Important architectural decisions.

## 13. Guidelines for AI coding agents

Create a dedicated section containing:

- Read relevant classes and tests before changing implementation.
- Follow established package and naming conventions.
- Reuse existing abstractions.
- Do not introduce new dependencies without justification.
- Maintain API backward compatibility unless explicitly requested otherwise.
- Preserve business invariants.
- Consider transaction boundaries.
- Consider downstream service dependencies.
- Update tests when changing behavior.
- Coordinate database changes with the Liquibase module.
- Coordinate configuration changes with Helm values and templates.
- Update this README when important implementation details change.

Include a short checklist that an AI agent should follow before completing a task.

## 14. Troubleshooting

Document known development and runtime problems, with solutions supported by repository evidence.

## Final requirements

- Create README.md in the microservice root.
- Use accurate Markdown.
- Use tables for configuration and API references.
- Include useful Mermaid diagrams where appropriate.
- Prefer links to actual source files for important implementation details.
- Keep explanations concise but technically meaningful.
- Avoid duplicating root README content.
- Never invent information.
- Explicitly mark unknown or unverified information.
- Optimize the README for retrieval by AI coding agents, not just human readability.