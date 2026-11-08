# Task: Create a Comprehensive README.md for the Helm Module

Act as a Senior Kubernetes Platform Engineer, Helm Expert, and Technical Documentation Engineer.

Analyze the Helm module and create a README.md in its root directory.

The README must help developers, DevOps engineers, and AI coding agents understand, configure, deploy, upgrade, and troubleshoot the system.

Document actual chart behavior rather than generic Kubernetes concepts.

## 1. Module overview

Explain:
- Purpose of the Helm module.
- Charts included.
- Services deployed.
- Kubernetes environments supported.
- Relationship with the four Spring Boot microservices.
- Relationship with the Liquibase module.

## 2. Chart structure

Document:
- Chart.yaml.
- values.yaml.
- Templates.
- Helpers.
- Dependencies.
- Environment-specific values files.
- Shared templates.
- Subcharts.

Explain the actual directory structure.

## 3. Deployment architecture

Explain how each microservice is deployed.

Document:
- Deployments.
- Services.
- Ingress.
- ConfigMaps.
- Secrets.
- ServiceAccounts.
- RBAC.
- Jobs and CronJobs.
- Persistent storage.
- Autoscaling.
- Network policies.

Only include resources that actually exist.

Include a Mermaid architecture diagram.

## 4. Configuration reference

Create a comprehensive configuration table.

For every important Helm value, document:

- Value path.
- Purpose.
- Default value.
- Expected format.
- Whether it is required.
- Which component consumes it.
- Whether it is environment-specific.

Include:
- Image repository and tag.
- Replica counts.
- Resource requests and limits.
- Environment variables.
- Application profiles.
- Service ports.
- Ingress settings.
- Health probes.
- Autoscaling.
- Secrets and ConfigMaps.
- Service-specific configuration.

Distinguish chart defaults from environment-specific overrides.

## 5. Configuration examples

Provide examples for:
- Default installation.
- Development environment.
- Staging environment.
- Production environment.

Use actual repository values and placeholders for sensitive values.

## 6. Installation and deployment

Provide verified commands for:

- Helm lint.
- Template rendering.
- Dependency updates.
- Dry-run installation.
- Installation.
- Upgrade.
- Rollback.
- Uninstallation.

Explain namespace management and release naming.

## 7. Application configuration

Explain how Helm configuration maps to Spring Boot configuration.

For each microservice, document:
- Environment variables.
- Spring profiles.
- Externalized configuration.
- Secret injection.
- Database configuration.
- External service URLs.

## 8. Database migration deployment

Explain:
- How Liquibase migrations are executed.
- Whether migrations run as a Kubernetes Job, init container, or application startup task.
- How migration execution relates to service deployment.
- How migration failures affect rollout.
- How schema changes should be deployed safely.

Only document the actual implementation.

## 9. Resource and security configuration

Document:
- Resource requests and limits.
- Health probes.
- Security contexts.
- Privilege restrictions.
- Service accounts.
- RBAC.
- Secret management.
- Network policies.
- Pod scheduling constraints.

## 10. Operational troubleshooting

Explain how to investigate:
- Failed deployments.
- CrashLoopBackOff.
- Image pull errors.
- Failed health checks.
- Configuration errors.
- Service connectivity.
- Failed migration Jobs.
- Helm upgrade failures.

Provide useful kubectl and Helm commands.

## 11. Guidelines for AI coding agents

Include explicit instructions:

- Inspect templates before modifying values.
- Keep values.yaml and templates consistent.
- Preserve naming conventions.
- Consider all environments when changing configuration.
- Never hardcode secrets.
- Avoid unnecessary Kubernetes resources.
- Preserve security constraints.
- Maintain correct application configuration mapping.
- Consider deployment sequencing.
- Validate with helm lint and helm template.
- Update documentation whenever chart behavior changes.

Include a Helm change checklist.

## Final requirements

- Create README.md in the Helm module root.
- Use actual chart structure and values.
- Link to important templates and configuration files.
- Include Mermaid diagrams where useful.
- Provide real, verified commands.
- Never invent chart capabilities.
- Clearly distinguish defaults from environment overrides.
- Optimize the README for both human operators and AI coding agents.