> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Generation Prompts

> Write the prompt that starts a project

[Wistia video player](https://fast.wistia.net/embed/iframe/g8rsgs7ih4?videoFoam=true)

## Overview

Code generation prompts tell Blitzy what changes to make. The key insight: **you don't need a perfect, detailed specification upfront**. Submit your request, review the Agent action plan (AAP), and iteratively add specificity where needed.

> **[Browse prompt templates](https://docs.blitzy.com/templates)**
>
> Explore ready-to-use templates for common scenarios like features, bug fixes, refactoring, and testing

***

## Creating Your Prompt

**1. Draft Your Initial Request**

Start with the essentials: **Objective** (what you want to accomplish), **Scope** (what's in/out), and **Success Criteria** (how you'll know it's done). Use the [Validation Checklist](../artifact_review/aap_validation_checklist.md) to ensure your initial request covers key areas.

**2. Submit and Review the AAP**

Submit your request and review the generated Agent action plan (AAP). Does it align with your expectations?

**3. Identify Gaps**

Spot misalignments in the AAP and identify which prompt sections are missing or need refinement.

**4. Add Specificity Tactically**

Refine your prompt using [Golden Rules](prompt_golden_rules.md) for clarity and [Rules](https://docs.blitzy.com/templates/rules-overview) for quality dimensions.

**5. Iterate Until Satisfied**

Re-submit your refined prompt and review the updated AAP. Repeat until you're satisfied with the plan.

***

## Key Sections to Include

When structuring your prompt, consider including these sections:

**Objective Statement** - What you want to accomplish

**System Boundaries** - What's in scope, out of scope, and what must not be modified

**Technical Specifications** - Technology preferences and architectural patterns (optional)

**Figma Attachments** - Attach frame URLs for [design-to-code workflows](https://docs.blitzy.com/templates/feature-product-development/figma-to-code) (optional)

**Success Criteria** - Measurable outcomes to validate completion

> [!NOTE]
>
> You can attach up to **10 files** per prompt. Supported attachment formats: code files, text files, Markdown, PDF, and Figma frame URLs. Multiple Markdown files can be attached in a single prompt - useful for providing several specification documents that together inform the Agent action plan.

> [!WARNING]
>
> **Spreadsheet files cannot be attached to prompts.** CSV, Excel (`.xls`, `.xlsx`), ODS, and Parquet files are read from your repository during ingestion and code generation, but they are not supported as prompt attachments. To include tabular data in a prompt, convert it to **Markdown** or **PDF** before attaching.


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.