# Task: Create the Root README.md

Act as a Senior Software Architect and Technical Documentation Engineer.

Using the repository analysis and actual source code, create a comprehensive but concise root-level README.md.

The README must serve as the primary entry point for both developers and AI coding agents.

## Required sections

### 1. Project overview
- What the system does.
- Its primary business or technical purpose.
- High-level architecture.
- Main technologies.

### 2. Repository structure
Show the six modules and explain their responsibilities.

Provide relative links to each module's README.md.

### 3. System architecture
Explain:
- The responsibilities of the four microservices.
- Their communication mechanisms.
- Database architecture.
- Liquibase migration management.
- Helm deployment architecture.
- External dependencies.

Include a Mermaid architecture diagram.

Only include verified relationships.

### 4. Technology stack
List the actual technologies and versions found in the repository.

### 5. Module dependencies
Explain which modules depend on other modules and how they interact.

Include a dependency diagram where useful.

### 6. Getting started
Document:
- Prerequisites.
- Repository checkout.
- Required environment configuration.
- Build instructions.
- Local development setup.
- How to start the system.

### 7. Build and testing
Provide verified commands for:
- Building individual modules.
- Building the complete project.
- Running tests.
- Running integration tests.

### 8. Database setup
Explain:
- Database prerequisites.
- Liquibase migration execution.
- Initial database setup.
- Schema ownership and relevant dependencies.

Link to the Liquibase README.

### 9. Deployment
Explain:
- Docker image building.
- Kubernetes deployment.
- Helm installation and upgrades.
- Environment-specific configuration.

Link to the Helm README.

### 10. Configuration and environments
Explain supported environments, configuration strategy, and how environment-specific settings are managed.

### 11. Development guidelines
Describe:
- Coding conventions.
- Branching or contribution workflow, if present.
- Testing expectations.
- Dependency management.
- Cross-service change considerations.

### 12. Troubleshooting
Include verified common issues and solutions.

### 13. Documentation index
Provide links to all six module READMEs.

## Special requirements for AI agents

Include a section named "Guidelines for AI Coding Agents".

It must explain:

- Read the relevant module README before modifying that module.
- Read the root README to understand cross-module architecture.
- Inspect actual implementation before assuming behavior.
- Follow existing conventions and patterns.
- Avoid introducing unnecessary dependencies.
- Consider API compatibility when changing service contracts.
- Consider database migration implications when changing persistence models.
- Consider Helm configuration when changing runtime configuration.
- Never modify Liquibase changesets that have already been applied in shared environments unless the repository's migration policy explicitly permits it.
- Update relevant documentation when behavior or architecture changes.
- Run relevant tests before considering a task complete.

## Writing style

- Concise and technical.
- Use Markdown headings, lists, tables, and code blocks.
- Prefer actionable instructions over generic descriptions.
- Use relative links.
- Include Mermaid diagrams where they improve understanding.
- Do not duplicate module-specific implementation details.
- Do not invent commands, configuration options, or architectural relationships.

Create the README.md directly in the repository root.