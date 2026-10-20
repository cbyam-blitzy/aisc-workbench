When generating or modifying user-facing features, ensure every user workflow is complete from entry point to exit point, with all decision branches and error paths handled.

Requirements:
- Every user-facing route, endpoint, or UI action must have a defined entry point and at least one success exit point
- Every decision branch (conditional paths based on user input, permissions, feature flags, or state) must lead to a handled outcome — no dead ends
- Every user action that can fail (form submission, API call, state transition) must have an error path that provides feedback to the user
- Multi-step workflows must handle partial completion — if step 3 of 5 fails, the user must see feedback and have a recovery path
- Shared workflow steps (authentication, authorization, logging) must be implemented consistently across all journeys that use them
- When modifying an existing workflow, verify that all existing entry points, branches, and exit paths still function

Forbidden Patterns:
- Creating a UI action or route that triggers no backend handler
- Implementing a route or endpoint with a stub or empty response body
- Adding a form submission or API call with no success or error feedback to the user
- Creating state transitions that lead to unreachable or undefined states
- Removing or breaking an existing workflow path without providing an alternative
- Silently swallowing errors in user-facing flows (catch blocks that neither log nor notify the user)

Validation Gate: Every user-facing route must connect to a handler. Every handler must return a meaningful response for both success and error cases. Every multi-step flow must handle failure at each step. Generated code that introduces dead-end paths or unhandled error states fails review.