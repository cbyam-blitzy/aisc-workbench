> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Prevent Security Vulnerabilities

> Ensure generated code follows security best practices and never introduces common vulnerability patterns

## When to Use

Add this to enforce secure coding practices across all code generation for a project, preventing common vulnerability patterns from being introduced.

## Rule Definition

**Name** — Prevent Security Vulnerabilities

**Description** — paste this into the rule description field on the platform:

```
All generated code must follow security best practices. Never introduce code that contains known vulnerability patterns.

Requirements:
- Use parameterized queries or prepared statements for all database access — never concatenate user input into SQL, NoSQL, or ORM queries
- Use environment variables or a secrets manager for all credentials, tokens, API keys, and connection strings — never hardcode secrets
- Validate and sanitize all external input (user input, API parameters, file uploads, webhook payloads) before processing
- Use the framework's built-in escaping for all rendered output to prevent XSS — never insert raw user content into HTML, templates, or DOM
- Apply the principle of least privilege for all authentication and authorization checks — never grant broad access when narrow access is sufficient
- Use strong, current cryptographic algorithms and proper key management — never use deprecated algorithms (MD5, SHA1 for security, DES, RC4)
- Pin dependency versions and avoid adding dependencies with known CVEs
- Set timeouts, rate limits, and size limits on all external service calls and user-facing endpoints

Forbidden Patterns:
- String concatenation or interpolation in SQL, command-line, or template expressions that include external input
- Hardcoded passwords, tokens, API keys, or connection strings anywhere in source code
- Rendering user-supplied content without escaping or sanitization
- Disabled or bypassed authentication/authorization checks, even temporarily
- Catching and silently discarding security-related exceptions
- Using `eval()`, `exec()`, or equivalent dynamic code execution with external input
- Storing sensitive data (passwords, tokens, PII) in logs, error messages, or client-facing responses

Validation Gate: Generated code that introduces any forbidden pattern fails review. Every database query must use parameterized access. Every credential must reference an environment variable or secrets manager. Every endpoint accepting external input must validate that input before processing.
```

## How It Works

1. Add this rule to your project on the platform
2. All generated code automatically follows secure coding practices
3. Database queries use parameterized access, secrets are externalized, input is validated
4. Forbidden vulnerability patterns are never introduced in generated code
5. Code review validates that security constraints are met across all generated files


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.