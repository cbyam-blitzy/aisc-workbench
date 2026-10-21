> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Assess Change Risks

> Require inline risk documentation for any change that modifies public contracts, schemas, or infrastructure

## When to Use

Add this to ensure every code generation that touches public interfaces, data schemas, or infrastructure includes risk documentation alongside the code.

## Rule Definition

**Name** — Assess Change Risks

**Description** — paste this into the rule description field on the platform:

```
When generated code modifies public APIs, data schemas, infrastructure configuration, or external-facing contracts, document the associated risks inline as code comments and in a summary block at the end of the output.

Requirements:
- For every modification to a public API, function signature, data schema, or configuration file, add an inline comment noting: what changed, what could break, and how to mitigate
- When adding a new external dependency, document the version pinned, what it replaces or adds, and any license implications
- When modifying database schemas, document the migration path, whether it is backward-compatible, and what happens to existing data
- When changing authentication, authorization, or access control logic, document what access changes and for which user types
- When a change requires deployment coordination (migrations, config changes, service restarts, ordering), document the deployment steps as comments

Forbidden Patterns:
- Modifying a public API, endpoint, or data contract without an inline comment documenting what consumers are affected
- Adding a database migration without documenting whether it is reversible
- Changing infrastructure or configuration without noting required deployment steps
- Introducing a breaking change without documenting a migration path for existing consumers

Validation Gate: Every modification to a public contract or schema must have an inline comment documenting the risk and mitigation. Changes to infrastructure or deployment configuration must include deployment step documentation. Generated code that modifies external-facing behavior without risk annotations fails review.
```

## How It Works

1. Add this rule to your project on the platform
2. Generated code that modifies public contracts includes inline risk annotations
3. Schema changes document migration paths and backward compatibility
4. Deployment-sensitive changes include step documentation
5. Code review validates that risk annotations accompany all external-facing changes


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.