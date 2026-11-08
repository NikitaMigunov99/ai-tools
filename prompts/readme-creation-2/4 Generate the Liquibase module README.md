# Task: Create a Comprehensive README.md for the Liquibase Module

Act as a Senior Database Engineer, Liquibase Expert, and Technical Documentation Engineer.

Analyze this repository's Liquibase module and create a README.md in its root directory.

The documentation must help developers and AI coding agents understand the database schema, migration history, migration conventions, and safe database evolution practices.

## 1. Module overview

Explain:
- Purpose of the module.
- Databases supported.
- Database ownership.
- Which microservices depend on its schema.
- How migrations are executed.
- Its role in local development and deployment.

## 2. Technology and configuration

Document:
- Liquibase version.
- Database engine and supported versions.
- JDBC drivers.
- Master changelog location.
- Configuration files.
- Contexts and labels.
- Schema and catalog configuration.
- Migration execution mechanism.

## 3. Changelog organization

Explain:
- Directory structure.
- Master changelog.
- Included changelogs.
- Naming conventions.
- Organization by domain, feature, service, or release.
- SQL versus XML/YAML/JSON changelog usage.

Include a Mermaid diagram if useful.

## 4. Database schema overview

Document the actual database objects:
- Tables.
- Relationships.
- Indexes.
- Constraints.
- Sequences.
- Views.
- Stored procedures and functions, if present.

Group database objects logically.

Explain which microservice uses which tables, only where this can be verified.

## 5. Changeset conventions

Document:
- Changeset ID conventions.
- Author conventions.
- File naming.
- Preconditions.
- Contexts and labels.
- Rollback strategy.
- SQL conventions.
- Naming conventions for database objects.

## 6. How to create a new migration

Provide a practical step-by-step guide.

Include:
1. How to identify the correct changelog location.
2. How to create a new changelog.
3. How to include it in the master changelog.
4. How to write changesets.
5. How to add preconditions where necessary.
6. How to define rollback logic.
7. How to validate the migration.
8. How to test it against the supported database.
9. How to coordinate it with affected microservices.

Include real examples based on existing repository conventions.

## 7. Migration safety and compatibility

This section is especially important.

Explain:
- Why applied changesets must remain immutable.
- How to handle corrections to existing migrations.
- Forward-only versus rollback migrations.
- Expand-and-contract migration strategy.
- Backward compatibility between old and new service versions.
- Handling large tables and potentially locking operations.
- Data migration considerations.
- Deployment sequencing.
- Recovery strategy.

Do not claim that rollback is always safe.

## 8. Execution instructions

Provide verified commands for:
- Applying migrations.
- Generating SQL.
- Validating changelogs.
- Checking migration status.
- Rolling back, if supported.
- Running migrations locally.

Include required environment configuration without exposing secrets.

## 9. Testing and validation

Document:
- Migration testing approach.
- Supported databases.
- Schema validation.
- Preconditions.
- Test data requirements.
- CI validation, if configured.

## 10. Guidelines for AI coding agents

Include explicit instructions:

- Never edit an already-applied changeset.
- Prefer a new changeset for every schema modification.
- Inspect existing conventions before adding migrations.
- Consider all affected microservices.
- Preserve backward compatibility where deployment requires it.
- Avoid destructive changes without explicit authorization.
- Add rollback logic where supported and meaningful.
- Test migrations against the actual database engine.
- Never assume a migration is safe merely because Liquibase accepts it.
- Coordinate changes with service entity mappings and SQL queries.
- Document data transformations and non-obvious migration behavior.

Add a pre-migration checklist.

## 11. Troubleshooting

Include common migration failures and debugging procedures.

## Final requirements

- Create README.md in the Liquibase module root.
- Use real changelog examples from this repository.
- Link to important changelog files.
- Never invent schema objects or migration commands.
- Mark unknown information explicitly.
- Make the README useful as a long-term operational reference for AI agents.