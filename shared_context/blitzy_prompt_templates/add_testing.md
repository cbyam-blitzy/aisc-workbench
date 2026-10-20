Add test coverage to [Project Name]. Focus on [specific modules
or coverage goals].

COVERAGE GOALS

- What modules need tests?
  [List specific paths and files.]
- What coverage target?
  [e.g., "80% line coverage, 90% branch coverage for src/services/"]
- What types of tests?
  [Unit, integration, E2E - specify for each module.]

TEST FRAMEWORK & CONVENTIONS

- What framework?
  [Jest, Pytest, JUnit - include assertion and mocking libraries.]
- What existing tests should new tests match?
  [Point to a test file that demonstrates your preferred style.]

SCOPE

- What should be tested?
  [Modules, functions, user flows in scope.]
- What should be excluded?
  [Legacy code, generated files, third-party integrations to skip.]

MOCKING STRATEGY

- What external dependencies should be mocked?
  [APIs, databases, services.]
- What should be tested with real dependencies?
  [Integration points that need live validation.]

CONSTRAINTS

- Add test files only - do not modify code unless
  required for testability.
- Follow existing test file organization and naming conventions.
- Do not refactor code during test implementation.