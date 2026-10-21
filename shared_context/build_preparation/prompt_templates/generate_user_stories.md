> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Generate User Stories

> Turn a business objective into sprint-ready tickets

Start here when you have a business objective and need it broken into sprint-ready tickets before building.

## How it works in Blitzy

**1. Describe the objective**

State the business goal, the target users, and what success looks like. "Add multi-language support for our customer portal" is an objective. "Internationalization" is a label.

**2. Review the Agent action plan**

Blitzy shows you the proposed epic/feature/story hierarchy before generating anything. Verify the breakdown matches how your team thinks about the work.

**3. Generate and review**

Blitzy produces ticket files with acceptance criteria in Given/When/Then format. Review each story for scope, specificity, and testability.

**4. Refine or merge**

If the stories are ready, merge them to your repo. They become references for subsequent Blitzy development runs - you can tell Blitzy "Implement FEATURE-001-01 per the acceptance criteria in `tickets/`" and it builds exactly what the ticket describes.

## What makes a good prompt?

A good user story prompt describes the business outcome, not the ticket format.

**Start with what should change for the user.** "Customers should be able to use the product in Spanish, French, and German - including all transactional emails and error messages." That tells Blitzy what the stories need to deliver.

**Set size constraints.** "Each story should be completable in 2-3 days by one engineer, max 5 story points." Without size guidance, Blitzy generates stories that are too large for a single sprint.

**Define the scope boundary.** "In scope: customer-facing UI and transactional emails. Out of scope: admin dashboard, marketing pages, PDF exports." Scope prevents stories from drifting into adjacent work.

> [!TIP]
>
> Read the [Golden Rules](../prompt_golden_rules.md) before writing your first story generation prompt. They cover the structural patterns that consistently produce the best results.

## Prompt template

> **User story generation prompt template**
>
> ```
> Generate user stories for [Project Name] based on the following objective.
>
> OBJECTIVE
>
> - What is the business goal?
>   [One clear statement of what should change for users.]
> - Who are the target users?
>   [Specific roles - not "users" but "customer support agents."]
> - What does success look like?
>   [Measurable outcome.]
>
> SCOPE
>
> - What is in scope for this epic?
>   [Features and capabilities to include.]
> - What is explicitly out of scope?
>   [Adjacent work to exclude.]
>
> STORY STRUCTURE
>
> - Sprint duration and story size limits?
>   [e.g., "2-week sprints, max 5 story points per story"]
> - How many features per epic?
>   [Typically 2-4.]
> - How many stories per feature?
>   [Typically 3-8.]
>
> OUTPUT FORMAT
>
> - Save all files to tickets/ directory at repository root.
> - Organize as: EPIC > FEATURE > STORY hierarchy.
> - Each story uses WHO/WHAT/WHY format with Given/When/Then
>   acceptance criteria.
> - Include: sub-tasks, edge cases, dependencies, estimation guidance.
> - Each story must satisfy INVEST principles (Independent, Negotiable,
>   Valuable, Estimable, Sized appropriately, Testable).
>
> CONSTRAINTS
>
> - Stories must be completable within a single sprint.
> - Acceptance criteria must have clear pass/fail determination.
> - No vague terms: approximately, several, various, adequate,
>   properly, efficiently.
> ```

## What if something goes wrong?

> **Stories are too large**
>
> Add size constraints to prompt: "Break down into stories completable in 2-3 days" or "Each story should be 3 story points or less". Review epic/feature breakdown and split large features.

> **Acceptance criteria lack specificity**
>
> Add to prompt: "Include specific values, thresholds, and measurable outcomes in acceptance criteria. Avoid vague terms like approximately, various, properly, or efficiently."

> **Epic breakdown doesn't match architecture**
>
> Provide architecture context in prompt: "Feature boundaries should align with microservices: auth-service, user-service, notification-service" or "Group stories by backend vs. frontend work".

> **Missing edge cases**
>
> Specify domain scenarios in prompt: "Include edge cases for concurrent user sessions, network timeouts, and data race conditions" and reference system constraints like database limits or API rate limiting.

> **Stories lack quality structure**
>
> Add explicit validation instruction: "Ensure each story is Independent, Negotiable, Valuable, Estimable, Sized appropriately, and Testable" and review generated stories against checklist.


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.