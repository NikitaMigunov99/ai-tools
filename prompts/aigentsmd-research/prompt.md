# Task: Create a Comprehensive Project-Wide AGENTS.md

Act as a principal software architect with extensive experience in Java, Spring Boot microservices, Liquibase, Kubernetes, Helm, and AI-assisted software development.

Using the repository and the analysis produced in the previous step, create a single, high-quality `AGENTS.md` file in the repository root.

The file must serve as the primary instruction manual for AI coding agents working on this project.

## 1. Main objective

Create instructions that allow an AI agent to:

- Understand the overall project architecture.
- Navigate all six modules efficiently.
- Understand module responsibilities and boundaries.
- Implement features consistently with existing architecture.
- Make safe changes across multiple modules.
- Write and execute appropriate tests.
- Modify database changelogs safely.
- Modify Helm charts correctly.
- Validate its changes before declaring a task complete.

The instructions must be practical, concise, specific, and actionable.

## 2. Required AGENTS.md structure

Organize the document using the following sections.

### A. Project overview

- Brief project description.
- Repository architecture.
- Six-module inventory.
- Responsibilities of each module.
- Relationships between modules.

### B. Repository structure

- Important directories and files.
- Where to find application code.
- Where to find tests.
- Where to find configuration.
- Where to find database migrations.
- Where to find deployment resources.

Include actual repository paths.

### C. Technology stack

Document discovered technologies and versions, including:

- Java.
- Spring Boot.
- Build tools.
- Database technologies.
- Liquibase.
- Helm.
- Kubernetes.
- Testing frameworks.
- Relevant supporting libraries and tools.

Only document versions verified in the repository.

### D. Architecture and design principles

Describe:

- Microservice boundaries.
- Module responsibilities.
- Dependency rules.
- Inter-service communication.
- API contract conventions.
- Configuration management.
- Error handling.
- Logging and observability.
- Existing design patterns.

Explain what an AI agent must preserve when modifying the architecture.

### E. Development workflow

Provide actual commands for:

- Building the project.
- Building individual modules.
- Running services.
- Running tests.
- Running integration tests.
- Formatting and static analysis.
- Packaging applications.

Use commands verified against the repository.

### F. Coding guidelines

Document project-specific conventions for:

- Java code.
- Spring Boot components.
- Dependency injection.
- REST APIs.
- DTOs and validation.
- Exception handling.
- Logging.
- Configuration properties.
- Dependency management.
- Naming and package organization.

Prefer existing conventions over introducing new standards.

### G. Testing guidelines

Specify:

- Required tests for new functionality.
- Unit and integration testing conventions.
- Test naming and organization.
- Test data management.
- Mocking conventions.
- How to execute tests.
- What validation is expected before completing a task.

Agents must not claim that tests passed unless they actually executed them successfully.

### H. Liquibase guidelines

Provide explicit instructions for database changes:

- Changelog organization.
- Naming conventions.
- Changeset structure.
- Changeset identifiers and authors.
- Preconditions.
- Rollback requirements.
- Database compatibility.
- Forward-only migration considerations.
- Safe handling of existing changesets.
- Migration validation.

Emphasize that existing applied changesets must not be modified or deleted unless explicitly requested and the consequences are understood.

### I. Helm and Kubernetes guidelines

Document:

- Chart structure.
- Template organization.
- Values conventions.
- Environment-specific configuration.
- Naming conventions.
- Resource configuration.
- Secrets handling.
- Image configuration.
- Dependencies between charts.
- Helm validation and rendering commands.

Require validation of modified templates and values.

### J. Security guidelines

Include rules for:

- Secrets and credentials.
- Authentication and authorization.
- Input validation.
- Dependency vulnerabilities.
- Sensitive logging.
- Configuration security.
- Container and deployment security.

Never hardcode credentials or expose secrets.

### K. Cross-module change guidelines

Explain how agents should approach changes involving multiple modules.

For example:

- Changing an API contract may require changes in multiple microservices.
- Changing a database schema may require corresponding application changes and Liquibase migrations.
- Changing application configuration may require corresponding Helm values or templates.
- Changing service deployment configuration may affect multiple charts or environments.

Require agents to identify all affected modules before implementing cross-module changes.

### L. AI agent execution rules

Define an explicit workflow that agents should follow:

1. Understand the user request.
2. Explore relevant modules and existing implementations.
3. Identify affected components and dependencies.
4. Prepare a minimal implementation plan for non-trivial changes.
5. Implement changes following existing conventions.
6. Add or update tests.
7. Validate affected modules.
8. Review the final diff for unrelated or unintended changes.
9. Report completed work, validation results, and known limitations.

Additional rules:

- Do not modify unrelated modules.
- Do not introduce new dependencies without justification.
- Do not perform unnecessary refactoring.
- Do not silently change public contracts.
- Do not introduce architectural changes without explicit justification.
- Do not create documentation that contradicts the repository.
- Do not claim successful validation without evidence.

### M. Definition of done

Define the minimum requirements before an agent considers a task complete:

- Implementation follows existing conventions.
- Relevant tests are added or updated.
- Applicable validation commands are executed.
- No unintended changes are introduced.
- Cross-module impacts are addressed.
- Known limitations and failed checks are reported.

## 3. Writing quality requirements

The generated AGENTS.md must follow these principles:

**Specificity**
- Use real directory names, module names, technologies, and commands.
- Avoid generic statements that could apply to any Java project.

**Actionability**
- Write instructions that tell agents what to do and what to avoid.
- Prefer explicit rules over vague recommendations.

**Conciseness**
- Avoid repeating the same instruction in multiple sections.
- Do not turn AGENTS.md into a complete technical architecture document.
- Include only information that materially improves agent behavior.

**Accuracy**
- Every project-specific statement must be supported by repository evidence.
- Do not invent commands or versions.
- Distinguish established conventions from recommendations.

**Maintainability**
- Keep the document easy to update.
- Avoid duplicating large sections of existing documentation.
- Reference existing documentation where appropriate.

## 4. Important constraints

- Create exactly one AGENTS.md file.
- Place it in the repository root.
- Do not create nested AGENTS.md files.
- Do not modify application code or configuration.
- Do not modify existing documentation.
- Do not introduce new dependencies.
- Do not change the project architecture.
- Do not expose secrets or sensitive information.

## 5. Final verification

After creating the file:

1. Verify that exactly one AGENTS.md exists in the repository.
2. Verify that it covers all six modules.
3. Verify that all referenced paths exist.
4. Verify that all documented commands are supported by the repository.
5. Verify that no unsupported assumptions are presented as facts.
6. Check for contradictory or duplicated instructions.
7. Ensure the document is concise enough to be useful in every coding session.

## 6. Final response

Report:

- The path of the generated AGENTS.md.
- Its major sections.
- How all six modules are covered.
- Any assumptions or unresolved questions.
- Any validation that could not be performed.

The deliverable is the root-level AGENTS.md file, not merely a proposal or an outline.