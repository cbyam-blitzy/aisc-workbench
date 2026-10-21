> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Prevent Workflow Gaps

> Ensure generated code never introduces incomplete flows, swallowed errors, or undocumented behavior

## When to Use

Add this to ensure every code generation produces complete, robust, and documented workflows with no dead ends, swallowed errors, or missing handling.

## Rule Definition

**Name** — Prevent Workflow Gaps

**Description** — paste this into the rule description field on the platform:

```
All generated code must produce complete workflows with no dead ends, no swallowed errors, and no undocumented behavior.

Completeness Requirements:
- Every UI action must connect to a handler that produces a response
- Every route or endpoint must have a full implementation — no stubs, no empty bodies, no TODO placeholders
- Every state machine or multi-step flow must handle all possible transitions, including edge states
- Every form submission and API call must provide success and error feedback to the user

Error Handling Requirements:
- Every try/catch block must either log the error, notify the user, or re-throw — never silently discard
- Multi-step operations must handle partial failure: if an intermediate step fails, either roll back prior steps or leave the system in a documented, recoverable state
- External service calls must include a timeout, and must handle timeout/failure with a fallback or user-facing error message
- Concurrent operations must account for race conditions (parallel writes, stale reads) with appropriate locking or conflict resolution

Documentation Requirements:
- Complex branching logic must include an inline comment explaining the intent of each branch
- Integration points with external services must document expected error responses and how they are handled
- Configuration-driven behavior must document valid values and defaults in a comment at the configuration site

Forbidden Patterns:
- Generating a route or handler with a stub or empty implementation
- Adding a catch block that swallows an exception without logging or user notification
- Creating a multi-step operation without handling failure at each step
- Making external service calls without a timeout
- Introducing configuration-driven behavior without documenting valid values

Validation Gate: Every generated route must connect to a complete handler. Every catch block must handle the error visibly. Every external call must have a timeout. Every branch must be documented. Generated code that introduces incomplete flows, swallowed errors, or undocumented behavior fails review.
```

## How It Works

1. Add this rule to your project on the platform
2. Generated code produces complete workflows with no dead ends or stubs
3. Error handling is explicit — no silently swallowed exceptions
4. External service calls include timeouts and failure handling
5. Code review validates completeness, error handling, and documentation


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.