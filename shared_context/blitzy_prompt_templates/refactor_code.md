Refactor [component/module] in [Project Name] to [target state].
Make only the changes necessary to achieve the target architecture.

TARGET STATE

- What should the code look like when this refactor is done?
  [Describe the end-state architecture, module structure, or pattern.]
- What problem does this refactor solve?
  [The pain point - slow builds, fragile dependencies, tech debt.]

BEHAVIORAL CONTRACTS (must not change)

- What APIs, interfaces, or response formats must stay identical?
  [List public contracts that downstream consumers depend on.]
- What performance characteristics must be preserved?
  [Latency, throughput, resource usage.]

SCOPE

- What files or modules are in scope?
  [List specific paths.]
- What is explicitly out of scope?
  [Prevent the refactor from expanding beyond its target.]

TECHNICAL PREFERENCES (optional)

- What pattern should the refactored code follow?
  [Point to existing code that demonstrates the target pattern.]
- What design patterns or architectural styles?
  [Strategy, Factory, module extraction, etc.]

TESTING REQUIREMENTS

- What tests validate behavioral equivalence?
  [Existing test suites, or new tests to write.]
- What coverage target?
  [Framework, test types, coverage threshold.]

CONSTRAINTS

- Make only the minimal necessary changes to achieve the target state.
- Do not modify code outside the refactor scope.
- Do not change existing interfaces or behaviors unless specified.