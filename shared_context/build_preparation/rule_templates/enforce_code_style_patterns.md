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