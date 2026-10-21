> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Refactor Code

> Restructure code without changing what it does

Start here when the code works but the structure needs to change - extract services, consolidate modules, or modernize patterns.

## How it works in Blitzy

**1. Describe the target state**

Tell Blitzy what the code should look like when the refactor is done. "Split utils.js into focused modules organized by domain" is a target state. "Clean up utils.js" is a wish.

> [!NOTE]
>
> For refactor and custom flows, the source and destination are always the same repository. Blitzy applies all changes within the originating repo.

**2. Review the Agent action plan**

Blitzy maps every file it will change and every new module it will create. This is where you verify it preserves external behavior - APIs, response formats, performance characteristics.

**3. Generate and review**

Blitzy restructures the code and runs your existing tests to confirm behavioral equivalence. Review the PR for architectural correctness.

**4. Merge or refine**

If the restructured code is clean, merge it. If Blitzy changed too much or too little, narrow the scope and run again.

## What makes a good prompt?

A good refactor prompt describes the end state, not the process. What should the code look like when Blitzy is done?

**Name what must not break.** Refactoring means changing structure while preserving behavior. List the APIs, response formats, and performance characteristics that must stay identical. Use absolute language: "DO NOT change the public API of the payments module."

**Point to the code that already does it right.** If one part of your codebase already follows the pattern you want everywhere, show Blitzy: "Restructure the user module to match the pattern in `src/services/orders/`."

**Set measurable success criteria.** "Reduce utils.js to zero lines" is measurable. "Improve code quality" is not.

> [!TIP]
>
> Read the [Golden Rules](../prompt_golden_rules.md) before writing your first refactor prompt. They cover the structural patterns that consistently produce the best results.

## Prompt template

> **Refactor prompt template**
>
> ```
> Refactor [component/module] in [Project Name] to [target state].
> Make only the changes necessary to achieve the target architecture.
>
> TARGET STATE
>
> - What should the code look like when this refactor is done?
>   [Describe the end-state architecture, module structure, or pattern.]
> - What problem does this refactor solve?
>   [The pain point - slow builds, fragile dependencies, tech debt.]
>
> BEHAVIORAL CONTRACTS (must not change)
>
> - What APIs, interfaces, or response formats must stay identical?
>   [List public contracts that downstream consumers depend on.]
> - What performance characteristics must be preserved?
>   [Latency, throughput, resource usage.]
>
> SCOPE
>
> - What files or modules are in scope?
>   [List specific paths.]
> - What is explicitly out of scope?
>   [Prevent the refactor from expanding beyond its target.]
>
> TECHNICAL PREFERENCES (optional)
>
> - What pattern should the refactored code follow?
>   [Point to existing code that demonstrates the target pattern.]
> - What design patterns or architectural styles?
>   [Strategy, Factory, module extraction, etc.]
>
> TESTING REQUIREMENTS
>
> - What tests validate behavioral equivalence?
>   [Existing test suites, or new tests to write.]
> - What coverage target?
>   [Framework, test types, coverage threshold.]
>
> CONSTRAINTS
>
> - Make only the minimal necessary changes to achieve the target state.
> - Do not modify code outside the refactor scope.
> - Do not change existing interfaces or behaviors unless specified.
> ```

## What if something goes wrong?

> **Refactored code breaks existing tests**
>
> Tests may be validating implementation details rather than behavior. Update tests to focus on public interfaces and observable behavior while ensuring refactored code maintains identical outputs.

> **Performance degrades after refactoring**
>
> Benchmark before and after refactoring. Add the [Analyze Performance Impact](https://docs.blitzy.com/templates/rules/analyze-performance-impact) rule to your project on the platform and specify performance targets explicitly (latency, throughput, resource usage).

> **Behavior changes subtly after refactoring**
>
> Add characterization tests before refactoring that capture current behavior, including edge cases. Verify all tests pass identically with refactored code before deployment.

> **Refactoring scope grows uncontrollably**
>
> Break into smaller incremental changes. Each refactoring should touch minimal files and be independently deployable. Use feature flags for gradual rollout.

> **Dependent systems break after refactoring**
>
> Map all dependencies before refactoring. Verify API contracts remain unchanged. Add integration tests validating interactions with dependent services remain identical.


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.