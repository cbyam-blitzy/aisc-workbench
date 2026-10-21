> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Add Testing

> Add test coverage to existing code without changing it

Start here when existing code needs test coverage. Blitzy provides unit tests automatically - specify integration, E2E, and functional test requirements explicitly.

## How it works in Blitzy

**1. Describe your coverage goals**

Tell Blitzy which modules need tests, what coverage target you want, and what types of tests matter - unit, integration, E2E. Name the framework: Jest, Pytest, JUnit.

**2. Review the Agent action plan**

Blitzy maps every test file it will create, the scenarios it will cover, and how it will organize them against your existing test structure.

**3. Generate and review**

Blitzy generates the tests and runs them against your code. Review the PR - check that the tests validate real behavior, not implementation details.

**4. Merge or refine**

If the tests are solid, merge them. If coverage gaps remain or the mocking strategy is wrong, update your prompt with specifics and run again.

## What makes a good prompt?

A good testing prompt describes what confidence you need and where you need it.

**Name the modules and the target.** "Bring `src/services/payments/` to 80% line coverage and 90% branch coverage using Jest." That tells Blitzy exactly where to focus and when to stop.

**Specify what to mock and what to test for real.** If external APIs should be mocked but database queries should run against a test database, say so. Mocking strategy is the most common source of test quality issues.

**Point to tests your team already likes.** If you have a test file that follows your preferred style, reference it: "Follow the organization and assertion patterns in `src/services/orders/__tests__/checkout.test.ts`."

> [!TIP]
>
> Read the [Golden Rules](../prompt_golden_rules.md) before writing your first testing prompt. They cover the structural patterns that consistently produce the best results.

## Prompt template

> **Testing prompt template**
>
> ```
> Add test coverage to [Project Name]. Focus on [specific modules
> or coverage goals].
>
> COVERAGE GOALS
>
> - What modules need tests?
>   [List specific paths and files.]
> - What coverage target?
>   [e.g., "80% line coverage, 90% branch coverage for src/services/"]
> - What types of tests?
>   [Unit, integration, E2E - specify for each module.]
>
> TEST FRAMEWORK & CONVENTIONS
>
> - What framework?
>   [Jest, Pytest, JUnit - include assertion and mocking libraries.]
> - What existing tests should new tests match?
>   [Point to a test file that demonstrates your preferred style.]
>
> SCOPE
>
> - What should be tested?
>   [Modules, functions, user flows in scope.]
> - What should be excluded?
>   [Legacy code, generated files, third-party integrations to skip.]
>
> MOCKING STRATEGY
>
> - What external dependencies should be mocked?
>   [APIs, databases, services.]
> - What should be tested with real dependencies?
>   [Integration points that need live validation.]
>
> CONSTRAINTS
>
> - Add test files only - do not modify code unless
>   required for testability.
> - Follow existing test file organization and naming conventions.
> - Do not refactor code during test implementation.
> ```

## What if something goes wrong?

> **Coverage targets not met**
>
> Scope may be insufficient. Run coverage reports to identify untested code paths, add specific test cases for uncovered branches, and request additional tests for low-coverage modules.

> **Tests are flaky and fail intermittently**
>
> Test isolation may be insufficient. Add proper setup/teardown, eliminate shared state between tests, use deterministic test data, and add timeouts for async operations.

> **Mocks don't match real behavior**
>
> Mock implementations may be outdated. Validate mocks against actual API contracts, use contract testing for external services, and add integration tests to verify real interactions.

> **Generated tests import business logic**
>
> Tests may reimplement code. Add the [Require Test Coverage](../rule_templates/require_test_coverage.md) rule to your project on the platform to ensure tests import and use code exclusively.

> **E2E tests are missing**
>
> E2E scope may not be specified. Explicitly request integration and E2E tests in prompt, define user workflows to test, specify API contracts to validate, and include database state requirements.


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.