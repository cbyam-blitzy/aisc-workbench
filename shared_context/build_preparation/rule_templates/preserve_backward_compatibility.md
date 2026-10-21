> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Preserve Backward Compatibility

> Ensure code changes maintain backward compatibility with existing consumers and contracts

## When to Use

Add this when making modifications to existing code, APIs, or interfaces to ensure changes do not break existing consumers or integrations.

## Rule Definition

**Name** — Preserve Backward Compatibility

**Description** — paste this into the rule description field on the platform:

```
Ensure all code changes, API modifications, and interface updates maintain backward compatibility with existing consumers and contracts.

Requirements:
- Before modifying any public interface, function signature, API endpoint, or data contract, identify all existing callers and consumers in the codebase
- Preserve all existing behavior that external or internal code depends on
- When a change to a public contract is necessary:
  - Add the new version alongside the old rather than replacing it
  - Mark the old version as deprecated using the language's deprecation mechanism (annotations, decorators, JSDoc tags, etc.)
  - Include a migration note in the deprecation message explaining what to use instead
  - Add an adapter or wrapper if the old signature must continue to work with the new implementation
- Document in code comments:
  - What existing behavior is preserved
  - What is deprecated and what replaces it
  - How consumers should migrate to the new version

Forbidden Patterns:
- Removing or renaming a public function, method, endpoint, or type without adding a deprecated alias
- Changing a function signature in a breaking way (removing parameters, changing types, altering return types) without preserving the old signature
- Modifying data formats or schemas consumed by other modules without providing a compatibility layer
- Silently changing behavior that existing callers depend on

Validation Gate: Any modification to a public interface must preserve the old contract or provide a deprecated alias with a migration note. Changes that remove or alter an existing public contract without a compatibility path fail review.
```

## How It Works

1. Add this rule to your project on the platform
2. Existing interfaces and contracts are identified before modifications begin
3. Changes are implemented with backward compatibility preserved
4. Deprecated items include migration notes explaining the replacement
5. Code review validates that no breaking changes were introduced without a compatibility path


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.