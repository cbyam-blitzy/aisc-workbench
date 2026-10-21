> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Greenfield Development

> Build a new product or service from scratch

Start here when there is no existing codebase - you are building a new product from zero.

New product projects follow the same workflow as existing product projects: Tech spec, Agent action plan, code generation, and PR Review.

## How it works in Blitzy

**1. Describe what you want to exist**

Start with the business need and the user experience. What should this product do? Who uses it? Then layer in your technical preferences - stack, architecture, deployment target.

**2. Review the Agent action plan**

Blitzy shows you the full technical blueprint - every file it will create, every architectural decision - before writing a line of code. Edit the plan, challenge the choices, or reject it entirely.

**3. Generate and review**

Blitzy generates the codebase and opens a pull request. Review it like you would any code from a new team member.

**4. Ship or extend**

If the foundation is solid, ship it. Then use [Add a Feature](add_feature.md) to build on top of it, one feature at a time.

## What makes a good prompt?

A good greenfield prompt describes the product that should exist when Blitzy is done.

**Start with who uses it and why.** "Our support team needs an internal dashboard to see customer subscription status, recent tickets, and payment history in one view." That tells Blitzy what to build. The technical decisions follow from there.

**Add stack and architecture preferences when your team has them.** Blitzy makes reasonable choices on its own. But if your team wants Next.js, or needs a specific database, or has opinions about the folder structure, say so. Technical preferences steer the output toward something your team already knows how to maintain.

**Describe the key user flows.** Walk through what a user does from login to their first meaningful action. Entry points, steps, success state. Blitzy turns these flows into real routes, components, and data models.

> [!TIP]
>
> Read the [Golden Rules](../prompt_golden_rules.md) before writing your first greenfield prompt. They cover the structural patterns that consistently produce the best results.

## Prompt template

> **Greenfield prompt template**
>
> ```
> Build a new [product type] for [Project Name].
>
> TARGET STATE
>
> - What should this product do?
>   [Describe the end state a user would see.]
> - Who uses it?
>   [Target users and their primary goals.]
> - What are the key user flows?
>   [Walk through 2-3 core interactions from start to finish.]
>
> STACK & ARCHITECTURE
>
> - What tech stack?
>   [Frontend framework, backend language, database, infrastructure.]
> - What architectural patterns?
>   [Monolith, microservices, serverless, etc.]
> - What deployment target?
>   [Cloud provider, container orchestration, hosting platform.]
>
> SCOPE
>
> - What features are in the MVP?
>   [Must-have features only.]
> - What is explicitly out of scope for the first generation?
>   [Nice-to-have features for follow-up iterations.]
>
> AUTHENTICATION & ACCESS
>
> - What user types exist?
>   [Roles and permission levels.]
> - What authentication method?
>   [OAuth, JWT, session-based, SSO.]
> - What access control rules?
>   [What each role can see and do.]
>
> TESTING REQUIREMENTS
>
> - What test types and coverage target?
>   [Unit, integration, E2E - framework and thresholds.]
>
> CONSTRAINTS
>
> - Generate a complete, runnable codebase.
> - Include error handling, input validation, and security basics.
> - Structure the codebase for future extension via the Add Feature workflow.
> ```

## What if something goes wrong?

> **Generated architecture doesn't match expectations**
>
> Be more specific about stack choices and architectural patterns. Name the exact frameworks, libraries, and design patterns you want. Reference documentation or examples when possible.

> **Too many features in first generation**
>
> Narrow your MVP scope. Use priority tiers (must-have, nice-to-have, future) and move non-essential features to follow-up generations using the [Add Feature](add_feature.md) workflow.

> **Missing authentication or authorization**
>
> Add explicit auth requirements to your prompt. Specify user types, authentication method (OAuth, JWT, session-based), and access control rules for each feature area.

> **Generated code lacks test coverage**
>
> Add the [Require Test Coverage](../rule_templates/require_test_coverage.md) rule to your project on the platform and specify which test types (unit, integration, e2e) and coverage thresholds you expect.

> **Unclear how to extend after first generation**
>
> Use the [Add Feature](add_feature.md) workflow for subsequent iterations. Each follow-up generation builds on the existing codebase with scoped feature additions.


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.