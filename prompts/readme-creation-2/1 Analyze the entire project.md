# Task: Analyze the Entire Repository Before Writing Documentation

Act as a Senior Software Architect and Technical Documentation Engineer.

Your task is to thoroughly analyze this repository and build an accurate understanding of its architecture, implementation, dependencies, and operational workflows.

## Project structure

The project consists of six modules:

1. Four independent Spring Boot microservices.
2. One module containing Liquibase database changelogs.
3. One module containing Helm charts for Kubernetes deployment.

## Instructions

Do NOT create or modify any README.md files yet.

First, inspect the repository systematically.

### 1. Repository structure

Identify:
- All modules and their responsibilities.
- Main directories and their purposes.
- Build system and build configuration.
- Parent-child module relationships, if applicable.
- Shared libraries and common configurations.
- Important configuration and infrastructure files.

### 2. Spring Boot microservices

For each microservice, investigate:

- Application entry point.
- Spring Boot and Java versions.
- Build configuration and dependencies.
- Architectural patterns and design principles.
- REST API endpoints and their responsibilities.
- Controllers, services, repositories, and domain models.
- Database access and persistence strategy.
- Database schemas and Liquibase dependencies.
- Messaging systems and integrations.
- Communication with other microservices.
- Authentication and authorization.
- Configuration properties and environment variables.
- Profiles and configuration precedence.
- Scheduled jobs and asynchronous processing.
- Exception handling and logging.
- Health checks and observability.
- Unit, integration, and end-to-end tests.
- Docker configuration.
- CI/CD integration.

Only document functionality that can be verified from the repository.

### 3. Liquibase module

Investigate:

- Changelog organization.
- Master changelog.
- Included changelog files.
- Naming conventions.
- Changeset identifiers and authorship conventions.
- Database objects managed.
- Database compatibility requirements.
- Migration execution strategy.
- Rollback support.
- Relationships between database changes and microservices.
- How developers add new changesets.
- How migrations are tested and validated.

### 4. Helm module

Investigate:

- Chart structure.
- Chart dependencies.
- Chart.yaml metadata.
- values.yaml and environment-specific values.
- Templates and helper templates.
- Deployments, Services, Ingress, ConfigMaps, Secrets, and other resources.
- Configuration shared between services.
- Image naming and tagging conventions.
- Resource requests and limits.
- Health probes.
- Autoscaling.
- Security contexts.
- Service accounts and RBAC.
- Environment-specific deployment configuration.
- Installation, upgrade, rollback, and debugging procedures.

### 5. Cross-module architecture

Identify:

- Communication between microservices.
- Database ownership and access patterns.
- Which services depend on which infrastructure.
- How Liquibase migrations are executed.
- How Helm deploys the microservices.
- External systems and integrations.
- Important runtime dependencies.
- Startup and deployment order, if applicable.

Create a dependency map.

### 6. Development and operational workflows

Determine how to:

- Build the project.
- Run individual microservices.
- Run the complete system locally.
- Execute tests.
- Apply database migrations.
- Package Docker images.
- Deploy to Kubernetes.
- Configure environments.
- Troubleshoot common problems.

Distinguish verified commands from inferred or suggested commands.

### 7. Analysis output

Produce a structured analysis report containing:

1. Repository overview.
2. Module inventory.
3. Detailed description of each module.
4. System architecture.
5. Inter-module dependencies.
6. Technology stack.
7. Configuration inventory.
8. Development workflows.
9. Testing strategy.
10. Deployment strategy.
11. Important conventions and constraints.
12. Missing information and ambiguities.

For every important finding, provide the relevant file path as evidence.

## Documentation quality requirements

- Never invent functionality.
- Never assume conventional Spring Boot behavior is necessarily used.
- Distinguish confirmed facts from assumptions.
- Identify inconsistencies between modules.
- Prefer source code and actual configuration over outdated documentation.
- Do not expose secrets or sensitive configuration values.

At the end, provide a concise list of questions that cannot be answered from the repository itself.