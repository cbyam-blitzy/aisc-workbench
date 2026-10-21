> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Annotate Performance Impact

> Require complexity annotations, efficient patterns, and documented trade-offs in all generated code

## When to Use

Add this when performance characteristics matter for scalability, user experience, or operational cost. Ensures every generation considers and documents performance implications.

## Rule Definition

**Name** — Annotate Performance Impact

**Description** — paste this into the rule description field on the platform:

```
All generated code must consider performance implications and document them inline. Choose efficient implementations by default and annotate trade-offs.

Requirements:
- For every algorithm or data structure choice, add an inline comment stating time and space complexity in Big O notation
- When choosing between implementation alternatives, document why the chosen approach is appropriate for the expected workload
- Use efficient patterns by default: prefer indexed lookups over linear scans, batch operations over N+1 patterns, lazy loading over eager loading when appropriate
- Avoid unbounded queries — add pagination, limits, or streaming for any operation over collections that could grow
- Set timeouts on all external service calls and database queries
- Use caching where repeated identical lookups occur, with documented invalidation strategy
- When the feature spans multiple layers (server, database, frontend), consider performance at each layer

Forbidden Patterns:
- Implementing an algorithm without stating its time and space complexity in a comment
- Using nested iteration over large or unbounded collections without documenting the complexity cost
- Choosing a less efficient approach in a performance-critical path without a comment explaining why
- Introducing N+1 query patterns (querying inside a loop when a batch query is possible)
- Fetching unbounded result sets without pagination or limits
- Making synchronous blocking calls where async alternatives exist in the framework
- Ignoring scalability when the code operates on user-controlled or growth-prone input sizes

Validation Gate: Every algorithm and data structure choice must have an inline comment stating its complexity. Performance-critical code paths without complexity annotations fail review. Trade-off decisions without documented justification fail review.
```

## How It Works

1. Add this rule to your project on the platform
2. Generated code uses efficient patterns by default across all layers
3. Algorithmic complexity is documented inline using Big O notation
4. Trade-off decisions include comments explaining the rationale
5. Code review validates that complexity annotations and efficiency patterns are present


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.