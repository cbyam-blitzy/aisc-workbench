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