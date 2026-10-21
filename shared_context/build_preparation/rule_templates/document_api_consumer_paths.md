> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Document API Consumer Paths

> Ensure every new or modified API endpoint includes inline documentation of its consumer contract and data flow

## When to Use

Add this to ensure every API endpoint generated or modified includes clear documentation of how consumers interact with it, what data flows through it, and what contract it exposes.

## Rule Definition

**Name** — Document API Consumer Paths

**Description** — paste this into the rule description field on the platform:

```
When generating or modifying API endpoints, webhooks, or event handlers, document the consumer contract and data flow inline.

Requirements:
- Every new or modified public endpoint must include a docstring or comment block documenting: HTTP method/route, request parameters and body schema, response status codes and payload structure, and error response format
- Every data transformation between request and response (validation, enrichment, filtering, mapping) must have an inline comment explaining what is transformed and why
- Every side effect triggered by an endpoint (database writes, event emissions, external API calls, cache updates) must be documented in a comment at the call site
- When an endpoint is consumed by a known external system, note the consumer in a comment on the endpoint definition
- Webhook and event handler registrations must document the expected payload schema and the source system

Forbidden Patterns:
- Creating a public endpoint without documenting its request and response contract
- Performing data transformations between request and response without inline comments
- Triggering side effects (writes, events, external calls) without documenting them at the call site
- Changing an endpoint's response shape without noting the breaking change and affected consumers
- Adding a webhook handler without documenting the expected payload format

Validation Gate: Every new or modified public endpoint must have a documented contract (method, parameters, response codes, payload shape). Every data transformation and side effect must have an inline comment. Endpoints missing contract documentation fail review.
```

## How It Works

1. Add this rule to your project on the platform
2. Every generated API endpoint includes contract documentation inline
3. Data transformations and side effects are annotated at the call site
4. Consumer relationships are noted when known
5. Code review validates that all endpoints have complete contract documentation


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.