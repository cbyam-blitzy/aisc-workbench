> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Golden Rules

> Structural patterns for prompts that consistently produce strong results

Apply these rules when drafting prompts or refining after AAP review.

## Quick Reference

| # | Rule | Action |
| - | - | - |
| 1 | Objective Clarity | Use clear headers. Front-load constraints. |
| 2 | Scope Boundaries | Label lists as "exhaustive" or "examples". |
| 3 | Success Criteria | Specify measurable thresholds and validation steps. |
| 4 | Technology Stack | Pin versions. Reference specific files. |
| 5 | Constraints & Preservation | Use DO NOT, MUST, NEVER. Add rationale when critical. |
| 6 | Architectural Patterns | Point to existing code examples in your repo. |
| 7 | Error Handling & Edge Cases | Write commands, not suggestions. |
| 8 | File Organization | Make explicit decisions. No fallback options. |
| 9 | Testing Requirements | Define coverage, test types, and critical scenarios. |
| 10 | Dependencies & Build | Pin dependency versions. Document build prerequisites. |

***

## Rules in Detail

> **1. Objective Clarity**
>
> **Use clear headers. Place constraints prominently.**
>
> Start with a clear objective statement. Organize content under distinct headers (OBJECTIVE, IN SCOPE, OUT OF SCOPE, CONSTRAINTS). Front-load critical constraints.
>
> ```
> OBJECTIVE: Migrate payment processing from legacy gateway to Stripe
>
> IN SCOPE:
> - Payment processing and invoice generation
> - Payment confirmation emails
>
> OUT OF SCOPE:
> - Subscription renewal logic
> - Existing invoice data migration
>
> CONSTRAINTS:
> - Use reversible database migrations
> - Implement idempotency for all payment operations
> ```

> **2. Scope Boundaries**
>
> **Use inclusion/exclusion lists. Distinguish exhaustive from example lists.**
>
> Label lists as "exhaustive" when complete or "examples" when illustrative. This prevents ambiguity about whether Blitzy should infer additional scope.
>
> ```
> IN SCOPE (exhaustive):
> - User authentication flow
> - Session management
> - Password reset functionality
>
> OUT OF SCOPE (exhaustive):
> - OAuth integrations
> - SSO configuration
>
> EXAMPLES of affected areas (non-exhaustive):
> - Login form, registration form, password reset form
> ```

> **3. Success Criteria**
>
> **Specify performance thresholds. Include validation steps.**
>
> Define objective criteria that can be verified through testing or measurement.
>
> ```
> SUCCESS CRITERIA:
> - API responds within 500ms at p95
> - Zero raw card data in database
> - All endpoints have integration tests (1 happy path, 2 error cases minimum)
>
> VALIDATION:
> - Run: npm test -- --coverage (80% minimum on new code)
> - Audit: grep -r "card_number\|cvv" src/ (zero results expected)
> ```

> **4. Technology Stack**
>
> **Include version numbers when compatibility matters. Point to specific files when needed.**
>
> Specify exact versions when multiple options exist or breaking changes are present. Use file paths for precision, natural language when sufficient.
>
> ```
> TECHNOLOGY STACK:
> - React Query v4 (not v5 - breaks existing cache invalidation)
> - Stripe SDK v12+ (requires webhook event types from v12)
>
> KEY FILES:
> - Payment service implementation
> - Stripe webhook handler at /src/webhooks/stripe.ts
>
> INTEGRATION POINTS:
> - Stripe webhooks to /api/webhooks/stripe
> - SendGrid for transactional emails
> ```

> **5. Constraints & Preservation**
>
> **Use absolute language (DO NOT, MUST, NEVER). Explain why when crucial.**
>
> Use absolute terms for constraints. Include rationale only when it's essential for understanding business logic or technical decisions.
>
> ```
> CONSTRAINTS:
> - DO NOT modify authentication middleware
>
> - MUST maintain backward compatibility for public API endpoints
>   RATIONALE: 40% of enterprise customers cannot upgrade until Q3
>
> - NEVER expose internal system errors to end users
> ```

> **6. Architectural Patterns**
>
> **Point to code examples. Link to relevant documentation.**
>
> Reference patterns already established in your codebase so Blitzy maintains consistency.
>
> ```
> ARCHITECTURE PATTERNS:
> - Follow error handling in PaymentService (wrap API calls, log errors, return Result type)
> - Use caching strategy from UserCache (Redis with 1hr TTL, cache-aside pattern)
>
> REFERENCE DOCS:
> - Stripe webhook signatures: https://stripe.com/docs/webhooks/signatures
> - Internal payment architecture: /docs/architecture/payments.md
> ```

> **7. Error Handling & Edge Cases**
>
> **Write commands, not suggestions.**
>
> Write commands, not suggestions. Define exact error handling behavior and edge case requirements. Avoid words like "maybe," "try," "consider," "should," or "ideally."
>
> **Weak:** "Add validation if it seems necessary"
>
> **Strong:** "Validate email using RFC 5322 format. Reject invalid emails with 400 status."
>
> **Weak:** "Add error handling as appropriate"
>
> **Strong:** "Catch Stripe errors. Log to Sentry. Return payment\_failed error code."
>
> **Weak:** "The API should be fast"
>
> **Strong:** "API must respond within 500ms at p95. Retry failures 3 times with exponential backoff."

> **8. File Organization**
>
> **Make explicit decisions. No fallback options. State absolute requirements.**
>
> Never give Blitzy choices or conditional logic about where to create files or how to organize code. Make all decisions yourself and state them as absolute requirements.
>
> **Weak:** "Create new files as needed"
>
> **Strong:** "Create new components in /src/components/profile/. Create tests in /src/components/profile/**tests**/"
>
> **Weak:** "Follow existing patterns where possible"
>
> **Strong:** "Follow PaymentService error handling pattern (wrap calls, log errors, return Result type)"
>
> **Weak:** "Organize files logically"
>
> **Strong:** "Place all payment-related services in /src/services/payments/. Each service gets its own file named {ServiceName}.service.ts"

> **9. Testing Requirements**
>
> **Define coverage expectations. Specify test scenarios.**
>
> Provide explicit testing requirements including coverage thresholds, test types, and critical scenarios to cover.
>
> ```
> TESTING REQUIREMENTS:
> - Unit test coverage: >80% for new code
> - Integration tests: All API endpoints (1 happy path, 2 error cases minimum)
> - Test file location: Co-located in __tests__ directories
>
> CRITICAL TEST SCENARIOS:
> - Payment success flow
> - Payment failure with retry
> - Webhook signature validation failure
> - Idempotency key collision
>
> TEST COMMANDS:
> - npm test -- --coverage
> - npm run test:integration
> ```

> **10. Dependencies & Build**
>
> **Highlight important build considerations. Note any critical setup steps.**
>
> Document build phase requirements that affect code generation. Specify dependency versions, environment variables, and build prerequisites.
>
> ```
> BUILD REQUIREMENTS:
> - Node.js 18+ (uses native fetch API)
> - Run database migrations before tests
> - Requires Stripe test API keys in .env.test
>
> DEPENDENCIES:
> - stripe: ^12.0.0 (not v11 - missing webhook event types)
> - @stripe/stripe-js: ^1.54.0
>
> CRITICAL NOTES:
> - Build fails if webhook signature validation is missing
> - Integration tests require running PostgreSQL and Redis instances
> ```

## Related Guides

> **[Validation Checklist](/prompt-engineering/validation-checklist)**
>
> Verify your prompt covers all 10 rules before submitting.

> **[Rules](/prompt-engineering/rules)**
>
> Attach reusable quality directives to enforce standards during generation.

> **[Generation Prompts](/prompt-engineering/generation)**
>
> Write and submit generation prompts for Blitzy.


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.