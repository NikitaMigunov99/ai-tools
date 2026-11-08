# Task: AI context reconnaissance

Inspect this repository to prepare a verified architecture and AI-context baseline.

The repository contains six modules:
- Four Spring Boot microservices
- One Liquibase migration module
- One Helm charts module

The team uses OpenSpec for Specification-Driven Development.

## Rules
- Read files before drawing conclusions.
- Do not modify, create, or delete any files.
- Do not assume module names, build tools, databases, messaging systems, or runtime topology.
- Distinguish verified facts, inferences, and unknowns.
- Cite repository-relative file paths for important findings.
- Do not print secrets or credentials. Report only the presence of potentially sensitive configuration.

## Inspect
1. Root directory, build files, CI workflows, and existing documentation.
2. Module directories, dependencies, and Spring Boot application entry points.
3. Controllers, API clients, messaging producers/consumers, and security configuration.
4. Persistence configuration, entities, repositories, and Liquibase changelog inclusion.
5. Helm charts, values files, templates, and environment overlays.
6. OpenSpec configuration, current specs, active changes, and representative archived changes if present.
7. Existing test suites and actual build, test, migration-validation, and chart-validation commands.

## Produce a report in the conversation

### A. Repository map
List all six modules, their paths, build technologies, and responsibilities.

### B. Architecture
Describe verified service-to-service communication and external dependencies. Include database boundaries and deployment relationships only where evidence supports them.

### C. Ownership
Identify known domain, API, event, and database ownership. Flag ambiguous ownership.

### D. Validation
List commands found in project configuration, CI, scripts, or documentation. Do not invent commands.

### E. Evidence
For each significant finding, provide the repository-relative path and relevant class, configuration key, or section.

### F. Unknowns and conflicts
List missing information, contradictory evidence, and assumptions requiring team confirmation.

### G. Documentation plan
Recommend which AI-context files should be created first, which can link to existing documentation, and which are not yet justified.

Stop after presenting the report and wait for review.