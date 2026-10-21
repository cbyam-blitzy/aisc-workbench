> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Add a Feature

> Add new functionality to an existing codebase

Start here when you have a working codebase and want to add new functionality to it.

## How it works in Blitzy

**1. Write your prompt**

Describe the feature, the files it should touch, and the boundaries it should respect. Be specific about what should NOT change - Blitzy treats your constraints as hard rules.

**2. Review the Agent action plan**

Blitzy shows you exactly which files it will create or modify before writing any code. This is your control point - edit the plan, narrow the scope, or reject it entirely.

**3. Generate and review**

Blitzy generates the implementation, runs it against your environment if configured, and opens a pull request. Review the code like you would any PR from a teammate.

**4. Merge or refine**

If the code is right, merge it. If it's close, tell Blitzy what to change and it generates a revision. If it missed the mark, tighten your prompt and run again.

## What makes a good prompt?

A good prompt describes the target state. What should exist when Blitzy is done, and why it matters to your users or your business.

**Start with intent and business requirements.** "Our customers need to pay with credit cards at checkout. The payment flow should handle failed charges gracefully and send a confirmation email on success." That sentence tells Blitzy what to build and what success looks like. The technical decisions follow from there.

**Add technical guidance when your team has preferences.** Blitzy makes reasonable technical choices on its own. But if your team wants Stripe specifically, or needs the service in Go instead of TypeScript, or requires a particular database schema, say so. Technical requirements steer the implementation toward solutions your team already knows how to maintain.

**Say what must not change.** Blitzy respects boundaries you set explicitly. "DO NOT modify the authentication module" is a hard constraint. "Try not to change auth" is a suggestion it may ignore. Use absolute language.

**Point to code that already does something similar.** If your codebase has a service class pattern, point Blitzy at an example: "Follow the pattern in `src/services/users/index.ts`." This is the single most effective way to get code that matches your conventions.

> [!TIP]
>
> Read the [Golden Rules](../prompt_golden_rules.md) before writing your first feature prompt. They cover the structural patterns that consistently produce the best results.

## Prompt template

> **Feature prompt template**
>
> ```
> Add a new feature to [Project Name]. Make only the changes necessary
> to deliver this feature.
>
> TARGET STATE
>
> - What should exist when this is done?
>   [Describe the end state a user or stakeholder would see.]
> - What user problem or business need does it solve?
>   [The reason this feature matters.]
> - What are 1-2 key user flows it enables?
>   [Concrete interactions or workflows.]
>
> SCOPE
>
> - What is in scope and out of scope?
>   [Prevent scope creep with clear boundaries.]
> - What must remain completely untouched?
>   [Critical features, workflows, or interfaces that cannot change.]
>
> TECHNICAL PREFERENCES (optional - include when your team has opinions)
>
> - Where should new code live?
>   [e.g., "add files in /src/features" or "limit changes to the UI layer"]
> - What existing code should this feature follow?
>   [Point to specific files that demonstrate your team's patterns.]
> - What code elements need to be created or modified?
>   [New files, classes, functions, or existing components requiring changes.]
>
> TESTING REQUIREMENTS
>
> - What test cases must be covered?
>   [Primary scenarios for functionality validation.]
> - What edge cases matter?
>   [Failure modes, boundary conditions, unusual inputs.]
> - What framework and coverage target?
>   [Jest/Pytest/etc., unit/integration/e2e, coverage threshold.]
>
> DEPENDENCIES & BUILD
>
> - Internal dependencies or packages needed?
>   [Provide them in the repo and reference here.]
> - Environment variables or configs required?
>   [List non-sensitive configs. Share sensitive ones with your Blitzy consultant.]
>
> CONSTRAINTS
>
> - Make only the minimal necessary changes to implement this feature.
> - Do not modify code that is not directly related to this feature.
> - Do not change existing interfaces or behaviors unless specified.
> ```

## What if something goes wrong?

> **The generated code doesn't match my codebase style**
>
> Add the [Enforce Code Style Patterns](../rule_templates/enforce_code_style_patterns.md) rule to your project on the platform. It extracts patterns from your existing code and enforces them during generation. This is the most common fix for style mismatches.

> **The feature touches too many files**
>
> Your scope is too broad. Break the feature into smaller pieces - a backend-only generation first, then a frontend generation that builds on it. Add explicit CONSTRAINTS listing files that should NOT change.

> **Integration points don't connect properly**
>
> Blitzy needs more specificity at the boundaries. Name the exact file paths, function signatures, and data contracts where the new feature connects to existing code. Vague integration guidance is the top cause of misaligned implementations.

> **Tests are missing or too shallow**
>
> Add the [Require Test Coverage](../rule_templates/require_test_coverage.md) rule and specify exact test scenarios in your prompt. "Include tests" is not enough - name the test types, the framework, the coverage threshold, and the critical paths.

> **Worried about security in the new feature**
>
> Add the [Catalog Security Vulnerabilities](https://docs.blitzy.com/templates/rules/catalog-security-vulnerabilities) rule and call out security requirements explicitly: authentication checks, authorization boundaries, input validation, data encryption. Blitzy treats these as hard constraints when you name them.


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.