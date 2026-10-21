> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Quickstart

> Complete your first Blitzy workflow in minutes

Get from zero to a Blitzy pull request. On first sign-in, Blitzy plays a short walkthrough, then opens the Workspace with a Concierge sidebar that tracks your setup progress. The Concierge stays visible until your first generation is complete. To replay the walkthrough, click **Replay the intro** at the bottom-right of the Workspace. The Concierge is a guide, not a gate. Close it or ignore it and work at your own pace.

> **Is your stack ready?**
>
> The more you confirm, the deeper Blitzy validates your output. You do not need to complete all six to start.
>
> | Checkpoint | What it means |
> | :- | :- |
> | **Source control connected** | Your estate lives in a supported [integration](https://docs.blitzy.com/integrations/integrations-welcome), cloud or self-hosted |
> | **Every repository authorized** | Access is granted per repository. [Submodules](../../build_preparation/setup/git_submodules.md) and private registries may need their own configuration |
> | **Build instructions written down** | The commands to install, compile, and test. Blitzy builds around what it finds. [Configure environments](../../build_preparation/setup/environment_config.md) |
> | **Dependencies live, not stubbed** | Internal libraries and custom packages are active and reachable at generation time |
> | **Environment access decided** | From source-only to runtime, database, and API access: the more you grant, the deeper the [validation](../../build_preparation/setup/environment_testing.md) |
> | **A consequential target** | Blitzy is for large codebases: refactors, migrations, remediations that would take quarters by hand |

> [!NOTE]
>
> **Sandbox accounts** start with 1,000,000 lines of code onboarding and 100,000 lines of code generation. Both are hard caps: when an allowance is spent, that activity pauses until you [upgrade](https://blitzy.com/customsoftwarebooking). See [Usage Metering](../admin/usage_metering.md) for how lines are counted.

Prefer a visual walkthrough? Watch the Blitzy Sandbox Overview below:

[Sandbox Onboarding 4 mins walkthrough\_v3 Video](https://fast.wistia.net/embed/iframe/dgibpzg9v9?web_component=true\&seo=true)

## Create a Project

**1. Go to Workspace**

**2. Create a new project**

Click [**Create new project**](https://platform.blitzy.com/workspace/project-name).

**3. Select your path**

Choose **Existing Product** or **New Product**.

> [!TIP]
>
> **Start with an existing codebase when possible.** The Existing Product path gives Blitzy full context of your architecture, patterns, and source code adjacent business logic, which produces higher-quality output.

**Existing Product**

**1. Configure environment**

Add build instructions and environment variables in project settings.

**Optional:** Create a `blitzy` branch for high-activity repos.

**2. Write ingestion prompt**

Describe your domain terminology, acronyms, and any in-progress migrations.

**Template:** [Codebase Ingestion](../../build_preparation/ingestion_prompts.md)

**3. Review Tech spec**

Blitzy generates a specification of your codebase.

**4. Write generation prompt**

Describe the feature or changes to add.

**Templates:** [New Feature](../../build_preparation/prompt_templates/add_feature.md), [Refactor](../../build_preparation/prompt_templates/refactor_code.md), [Bug Fix](../../build_preparation/prompt_templates/fix_bugs.md)

**Optional:** Add [Rules](https://docs.blitzy.com/prompt-engineering/rules)

**5. Review Agent action plan (AAP)**

Blitzy generates a structured plan showing the files it will create/modify and its overall approach before any code is written.

**Actions:** Approve, Refine, Discard, or Edit inline.

> [!TIP]
>
> Use **Refine** for implementation approach adjustments. For broad rework, **Discard and regenerate** with an updated prompt. Inline edits are best reserved for small, targeted corrections.

**6. Generate**

Blitzy creates code and opens a PR to your target branch.

**7. Review Project Guide**

Documentation of changes and how they integrate with existing code.

> [!NOTE]
>
> After merging, return to Step 3 for your next generation.

**New Product**

**1. Write prompt**

Describe what to build: objective, tech stack, key features, success criteria.

**Template:** [New Product](../../build_preparation/prompt_templates/greenfield.md)

**2. Review Agent action plan (AAP)**

Blitzy generates a structured plan showing the files it will create and its overall approach before any code is written.

**Actions:** Approve, Refine, Discard, or Edit inline.

**3. Generate**

Blitzy creates code and opens a PR to your target branch.

**4. Review Project Guide**

Documentation of what was built and how to extend it.

## Next Steps

> **[Test](../project_lifecycle/code_review.md)**
>
> Check out the branch and verify functionality

> **[Merge](../project_lifecycle/pr_review.md#merge)**
>
> Follow your review process and merge

> **[Refine](../project_lifecycle/pr_review.md#refine)**
>
> Iterate with follow-up prompts


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.