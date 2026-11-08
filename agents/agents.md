
# Repository Guide for AI Agents

## Project
This repository contains four Spring Boot microservices,
one Liquibase migration module, and one Helm chart module.

## Source of truth
- OpenSpec specs: accepted behavioral requirements.
- Active OpenSpec change: scope and requirements of the current task.
- design.md: approved implementation approach and trade-offs.
- tasks.md: implementation checklist.
- Source code and tests: current implementation and executable behavior.
- ADRs: durable architectural decisions.

If these sources conflict, do not silently choose one.
Identify the conflict and ask for clarification when it affects
requirements, compatibility, data integrity, or deployment safety.

## Before implementing
1. Read this file and the relevant module-level AGENTS.md.
2. Inspect the active OpenSpec change and its tasks.
3. Read relevant specs, design decisions, and affected code/tests.
4. Identify cross-service, database, API, and Helm impacts.
5. Update the plan if implementation reveals missing requirements.

## Architecture
- Read docs/architecture/system-overview.md.
- Read docs/architecture/service-catalog.md.
- Read docs/architecture/data-ownership.md when data is affected.
- Read docs/architecture/integration-contracts.md for integrations.

## Engineering rules
- Follow existing patterns unless the approved design says otherwise.
- Do not introduce dependencies without justification.
- Preserve API and event compatibility unless explicitly approved.
- Never edit an applied Liquibase changeset to change its history.
- Consider expand/migrate/contract for breaking database changes.
- Keep Helm values and Kubernetes resource settings consistent.
- Never commit secrets, credentials, or environment-specific secrets.

## Validation
- Discover and run the relevant module's build and tests.
- Run cross-module validation for shared contracts and migrations.
- Validate Helm templates and OpenSpec artifacts when applicable.
- Report commands executed, results, and any unverified behavior.

## Scope control
- Do not modify unrelated modules.
- Do not mark tasks complete without evidence.
- Flag ambiguous requirements and unsafe migrations before proceeding.
