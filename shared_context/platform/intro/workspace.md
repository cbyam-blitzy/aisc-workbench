> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Workspace

> Where projects move from prompt to pull request

The Workspace is where projects move from prompt to pull request. Write your requirements, review the implementation plan, and manage each generation through to merge. Toggle to [Knowledge Base](knowledge_base.md) to explore your technical specifications or [Proactive Insights](proactive_insights.md) to surface vulnerabilities across your codebase.

## Why the Workspace Matters

**You control every decision** - Write prompts, review implementation plans, and approve or refine before any code is written.

**Plan before you build** - Use the platform's full codebase context to debug issues, plan features, and sharpen requirements before generation starts.

**One surface, end to end** - From the first prompt to the final merge, the entire project workflow lives in one place.

## What the Workspace Contains

### Core Development Activities

> **[Prompt Writing & Submission](../../build_preparation/generation_prompts.md)**
>
> Write generation requests using templates or the Golden Rules

> **[Technical Specification Review](../project_lifecycle/technical_specification.md)**
>
> Review specs generated from ingestion

> **[Agent action plan review](../project_lifecycle/agent_action_plan.md)**
>
> Review implementation plans before code generation

> **[Project Guide Review](../project_lifecycle/project_guide.md)**
>
> Review generated documentation

> **[Code Review & Merge](../project_lifecycle/code_review.md)**
>
> Review and merge pull requests

> **[Refine Pull Request](../project_lifecycle/pr_review.md#refine)**
>
> Request targeted improvements to generated code

### Project Visibility

Filter the projects list by visibility to focus on the projects you need:

* **All** - every project you can access
* **Shared** - projects shared organization-wide or with a team
* **Private** - projects only you can access

Each project shows a badge that reflects its visibility:

* **Organization** - shared organization-wide and with no team, shown with a globe icon
* **Team name** - shared with one or more teams, shown as a single team tag naming the first team plus a "+N" count for any others. Hover the tag to list every team. A project shared both organization-wide and with a team shows this tag rather than the Organization badge
* **Private** - owner-only, shown with a lock icon

> [!NOTE]
>
> When an administrator enables **Require project sharing**, every new project must be shared organization-wide or with a team, and opening a private project prompts a forced share before it opens. Already-shared projects stay shared. See [Sharing](../project_lifecycle/project_setup.md) and [Teams](../admin/teams.md).

## Troubleshooting

> **How do I write an effective prompt?**
>
> * Start with a [prompt template](https://docs.blitzy.com/templates) for your use case
> * Follow the [Golden Rules](../../build_preparation/prompt_golden_rules.md) for prompt engineering
> * Review the [Prompt Generation guide](../../build_preparation/generation_prompts.md) for detailed guidance
> * Toggle to [Knowledge Base](knowledge_base.md) to understand your codebase architecture before writing prompts

> **What if the Agent action plan isn't right?**
>
> * Request refinements through the [Agent action plan process](../project_lifecycle/agent_action_plan.md)
> * Provide specific feedback on what needs to change
> * Reference architectural patterns from your [technical specifications](knowledge_base.md)
> * If major changes are needed, consider refining your original prompt

> **How do I share projects with my team?**
>
> * See the [Sharing guide](../project_lifecycle/project_setup.md) for step-by-step instructions
> * Enterprise users can manage team access through [Team Management](../admin/teams.md)
> * Configure repository access through [Integration Management](https://docs.blitzy.com/integrations/managing)
> * Admins can require all projects to be shared through the [Require project sharing setting](../admin/teams.md)

> **How do I filter projects by visibility?**
>
> * **All** - shows every project you can access
> * **Shared** - shows projects shared organization-wide or with a team
> * **Private** - shows projects that are owner-only, marked with a lock icon
> * See the [Sharing guide](../project_lifecycle/project_setup.md) for how sharing and enforcement work

> **Generated code doesn't meet requirements**
>
> * Review the Project Guide to understand what was built
> * Use [Refine](../project_lifecycle/pr_review.md#refine) for specific, targeted changes
> * Use [Close](../project_lifecycle/pr_review.md#close) to restart with an improved prompt
> * See the [Prompt Refinement guide](../../build_preparation/prompt_golden_rules.md) for improving your prompts

**Need help?** Contact support at [support@blitzy.com](mailto:support@blitzy.com) or consult your Blitzy AI Solutions Consultant for Workspace assistance.


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.