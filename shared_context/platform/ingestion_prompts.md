> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Ingestion Prompts

> Refine your technical specification with business context, domain terminology, and architectural decisions

## Overview

Ingestion prompts are an optional way to refine how your codebase is represented in the technical specification. Blitzy automatically analyzes your code to generate a specification. An ingestion prompt allows you to enhance this representation with business context, domain terminology, and architectural decisions that aren't visible in the code itself.

**When to use ingestion prompts:**

* Your codebase has domain-specific terminology that needs definition
* You have compliance requirements that should guide code generation
* You want to document architectural decisions and evolution
* You need to exclude legacy or deprecated code from analysis

You can start code generation immediately without an ingestion prompt and add it later if needed.

> **[Ready to ingest your codebase?](/templates/documentation-onboarding/codebase-ingestion)**
>
> Use the **Ingest Codebase Template** to get started immediately with a structured prompt

***

## Key Sections to Include

**Project Overview** - Product context, primary goals, and core workflows

**Business Context & Domain Knowledge** - Compliance requirements, domain terminology, and architectural rationale

**Current Status & Evolution** - Codebase maturity, architectural shifts, and areas under active development

**Areas to Ignore** - Irrelevant file paths and directories to exclude from analysis

***

## Supported File Formats

Blitzy reads the following file formats in your repository during ingestion and code generation:

| Format | Extensions | Ingestion | Code Generation |
| :- | :- | :- | :- |
| Code and text files | All standard extensions | Yes | Yes |
| PDF | `.pdf` | Yes | Yes |
| CSV | `.csv` | Yes | Yes |
| Excel | `.xls`, `.xlsx` | Yes | Yes |
| OpenDocument Spreadsheet | `.ods` | Yes | Yes |
| Parquet | `.parquet` | Yes | Yes |
| PowerPoint | `.ppt`, `.pptx` | No | No |

> [!NOTE]
>
> Spreadsheet files (CSV, Excel, ODS, Parquet) are read when they exist in your repository. They are **not** supported as prompt attachments. PDF files are supported both in-repo and as prompt attachments.

***

## Using .blitzyignore

For permanent file exclusions, create a `.blitzyignore` file in your repository root using standard `.gitignore` syntax.

**Benefits:**

* Saves quota (excluded files don't count toward subscription usage)
* Improves focus (Blitzy analyzes only relevant patterns)
* Team-wide consistency (exclusions apply automatically when committed)

***

## Branch Behavior

When you create a new Blitzy project on a branch that was forked from an already-ingested branch, the existing technical specification is copied over automatically — you don't start from scratch.

However, if you include an ingestion prompt in the new project, Blitzy will re-ingest the codebase and rewrite the technical specification to match that prompt. The original spec from the parent branch is replaced entirely.

> [!WARNING]
>
> If you fork a branch and create a project **without** an ingestion prompt, you inherit the parent branch's spec as-is. If you create a project **with** an ingestion prompt, the spec is regenerated from scratch based on that prompt. There is no merge — it's one or the other.

To maintain control over your technical specification across branches, include a minimal ingestion prompt every time you create a new project. This ensures the spec is intentionally shaped rather than silently inherited, and gives you a clear path to adjust it if the inherited version doesn't match your needs.

***

## Best Practices

**Dedicated ingestion project** - Create one Blitzy project (e.g., "MyApp - Ingestion") on your main branch exclusively for ingestion and specification updates

**Separate generation projects** - Create new projects on feature branches that inherit the ingested context from your main branch

**Include a minimal ingestion prompt** - Even on feature branches, include at least a brief ingestion prompt to ensure you control the resulting specification rather than silently inheriting one

**Keep specifications current** - Periodically re-sync your ingestion project as your codebase evolves to update the baseline specification


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.