> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Enforce Code Style Patterns

> Ensure generated code matches existing codebase conventions for naming, structure, error handling, and architecture

## When to Use

Add this when working with established codebases to ensure generated code follows existing architectural patterns, coding conventions, and design standards.

## Rule Definition

**Name** — Enforce Code Style Patterns

**Description** — paste this into the rule description field on the platform:

```
All generated code must match the conventions and architectural patterns already established in the codebase.

Requirements:
- Before writing new code, identify the relevant patterns in the existing codebase: file structure, naming conventions, error handling, dependency management, and code organization
- Match naming conventions exactly (casing, prefixes, suffixes, abbreviation style)
- Follow the same file and directory structure patterns used by similar modules
- Use the same error handling approach (e.g., if the codebase uses Result types, do not use exceptions; if it uses try/catch with custom error classes, follow that pattern)
- Use the same dependency injection, state management, and configuration patterns already in use
- When the codebase has multiple patterns for the same concern, follow the most recent or most prevalent one and note the choice in a code comment

Forbidden Patterns:
- Introducing a new architectural pattern when an existing one already covers the use case
- Using a different naming convention than what exists in the surrounding code
- Adding a new dependency that duplicates functionality already available through an existing dependency
- Mixing coding styles within the same module (e.g., callbacks in a codebase that uses async/await)

Validation Gate: Generated code must be stylistically indistinguishable from code written by the existing team. Any deviation from established patterns requires a code comment explaining why the existing pattern was not suitable.
```

## How It Works

1. Add this rule to your project on the platform
2. Generated code automatically follows the conventions found in the existing codebase
3. Naming, structure, error handling, and architecture match established patterns
4. Deviations from existing patterns require an inline comment explaining the reason
5. Code review validates that generated code is consistent with the surrounding codebase


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.