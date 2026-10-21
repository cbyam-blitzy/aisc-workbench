> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Glossary

> Definitions of key terms and concepts used across the Blitzy Platform documentation

A quick reference for Blitzy-specific terminology. Each entry links to the page where the concept is explained in detail.

> [!NOTE]
>
> **Jump to:** [Platform & UI](#platform-%26-ui) | [Prompt & Generation](#prompt-%26-generation) | [Artifacts & Review](#artifacts-%26-review) | [Administration](#administration)

## Platform & UI

> **Blitzy Certified**
>
> The official collection of workflows and standards for working effectively on the Blitzy platform. [Learn more](/administration/blitzy-certified-welcome)

> **Demo Project**
>
> A curated read-only example project that Blitzy provides to every role, preserved at the workflow step it reached. [Learn more](/platform/demo-projects)

> **Knowledge Base**
>
> The UI mode for browsing and reviewing Technical Specifications organized by repository and branch. [Learn more](/platform/knowledge-base)

> **Locked Project**
>
> A project an Admin has made read-only for Members while Admins keep full access. [Learn more](/platform/locked-projects)

> **Workspace**
>
> The primary UI mode for active development: write prompts, review Agent action plans, manage projects, and merge generated code. [Learn more](/platform/workspace)

## Prompt & Generation

> **Generation Prompt**
>
> The prompt you write to tell Blitzy what code to generate or change. After submission, Blitzy produces an Agent action plan for your review. [Learn more](/prompt-engineering/generation)

> **Golden Rules**
>
> Best practices for writing effective prompts that produce high-quality generation results. [Learn more](/prompt-engineering/golden-rules)

> **Ingestion**
>
> The process where Blitzy analyzes your existing codebase to understand its architecture, patterns, and domain terminology. Required for existing codebases, not needed for greenfield projects. [Learn more](/prompt-engineering/ingestion)

> **Ingestion Prompt**
>
> An optional prompt you provide during ingestion to enrich the Technical Specification with business context and architectural decisions not visible in the code. [Learn more](/prompt-engineering/ingestion)

> **Prompt Template**
>
> A ready-to-use prompt for common scenarios such as adding features, fixing bugs, or refactoring. [Learn more](/templates)

> **Rules**
>
> Reusable directives attached to a project that enforce quality standards during every code generation. [Learn more](/prompt-engineering/rules)

> **Runtime Validation**
>
> Blitzy compiles and tests generated code in isolated environments before creating a pull request. Validation depth scales with your environment configuration. [Learn more](/introduction)

## Artifacts & Review

> **Agent action plan (AAP)**
>
> A detailed implementation plan Blitzy produces after you submit a generation prompt. Your primary control point - review, edit, and approve before any code is written. [Learn more](/project-lifecycle/aap-review)

> **Code Review**
>
> The layered review process for generated pull requests: AAP validates intent, runtime validation catches build errors, code-level review covers integration and business logic. [Learn more](/project-lifecycle/code-review)

> **Project Guide**
>
> Documentation automatically generated alongside your code, covering architecture decisions, file structure, and next steps. [Learn more](/project-lifecycle/project-guide-review)

> **PR Review**
>
> An ordered review sequence that groups a generated pull request by purpose so you can walk changes before deciding to merge, refine, or close. [Learn more](/project-lifecycle/pr-review)

> **Technical Specification**
>
> A living knowledge base Blitzy generates after ingesting your codebase, documenting architecture, patterns, and conventions. Updates automatically as your code changes. [Learn more](/project-lifecycle/tech-spec-review)

## Administration

> **.blitzyignore**
>
> A file in your repository root (`.gitignore` syntax) that excludes files from Blitzy's analysis and subscription usage. [Learn more](/prompt-engineering/ingestion)

> **Azure DevOps Server**
>
> Microsoft's Azure DevOps running on a server your organization operates. Blitzy connects to a single collection on that server with the collection URL and a personal access token, rather than the authorization flow the Azure DevOps cloud integration uses. Blitzy supports Azure DevOps Server 2020 and later, and git repositories only. [Learn more](/integrations/azure-devops-server)

> **Environment**
>
> A configuration that tells Blitzy how to build and run your application - target OS, virtualization mode, setup instructions, toolchain versions, variables, and secrets. [Learn more](/administration/environments)

> **Forced Share**
>
> A blocking prompt that requires a member to choose a share target before opening a still-private project while sharing enforcement is active. [Learn more](/project-lifecycle/sharing)

> **Organization-wide Share**
>
> A sharing option that grants every member of your organization access to a project. [Learn more](/project-lifecycle/sharing)

> **Private Project**
>
> A project accessible only to its owner. While sharing enforcement is active, private projects prompt a forced share the next time they are opened. [Learn more](/project-lifecycle/sharing)

> **Project Sharing Enforcement**
>
> An organization-level setting that mandates every newly created project be shared. Dormant private projects are not shared in bulk - they prompt on next open. [Learn more](/administration/teams)

> **SDLC Integration**
>
> Embedding Blitzy into your existing software development lifecycle. Blitzy adapts to your workflow rather than replacing it. [Learn more](/sdlc-integration)

> **Shared Project**
>
> A project made accessible beyond its owner through an organization-wide or team share. [Learn more](/project-lifecycle/sharing)

> **Team Share**
>
> Sharing a project with one or more teams so every team member gains full access. Under enforcement, sharing a private project transfers ownership permanently to the team. [Learn more](/administration/teams)

> **Target OS**
>
> The operating system an environment builds and validates on, selected in **Settings > Environments**. Linux, Windows, and macOS are available, each with one or more virtualization modes. [Learn more](/administration/environments#target-operating-system)

> **Virtualization Mode**
>
> How a build runs on its target OS - Container or Virtual machine. The target OS determines which modes are available. [Learn more](/administration/environments#target-operating-system)


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.