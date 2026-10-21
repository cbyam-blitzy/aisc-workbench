> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Technical Specification

> Review Blitzy's living knowledge base of your codebase to verify understanding before generating code

> [!NOTE]
>
> **Jump to:** [Review Workflow](#review-workflow) | [Review Checklist](#review-checklist) | [Why This Matters](#why-this-matters)

[Wistia video player](https://fast.wistia.net/embed/iframe/aitg61b8oh?videoFoam=true)

After ingestion, Blitzy produces a technical specification - a living knowledge base of your codebase that continuously updates as your code changes. It is the output of ingestion, not something you write. Your job is to spot-check it and confirm Blitzy's understanding is accurate.

## Review Workflow

The tech spec is a reference document, not something you read cover to cover. Use your domain knowledge to validate the areas you know best.

**1. Go to what you know**

Start with the parts of the codebase you understand deeply. Check whether Blitzy's interpretation of architecture, dependencies, or domain logic matches reality in those areas. Use the [Review Checklist](#review-checklist) to guide where to look.

**2. Check domain-specific language**

Verify that Blitzy correctly interprets acronyms, internal terminology, and DSL keywords used in your codebase. These are the most likely areas where interpretation may differ from your team's intended meaning.

**3. Proceed to code generation**

Once you've validated the areas relevant to your work, move on to writing your [generation prompt](../../build_preparation/generation_prompts.md). Most specs are accurate enough to proceed after a targeted review.

> [!NOTE]
>
> If the tech spec has significant gaps or you want to personalize how Blitzy interprets your codebase, you can create a new Blitzy project on the same branch with an updated [ingestion prompt](../../build_preparation/ingestion_prompts.md). This re-ingests your codebase and produces a new spec. This is rarely needed. Most teams proceed directly to code generation.

## Review Checklist

Use these categories to guide your spot-check:

> **Architecture & Structure**
>
> * System architecture is correctly identified (monolith, microservices, hybrid)
> * Module relationships and boundaries are accurately mapped
> * Data flows between components are documented
> * Layering patterns (controllers, services, repositories) are recognized
> * Custom abstractions or unconventional layering are captured (these often require an ingestion prompt)

> **Dependencies & Integration Points**
>
> * Internal dependencies between modules are captured
> * External libraries, APIs, and services are identified
> * Single points of failure or tightly coupled components are flagged
> * Framework and library versions match your current state
> * Submodules or private registries are included (may require additional access configuration)

> **Domain & Business Logic**
>
> * Domain terminology is correctly interpreted (e.g., "instruments" in finance, "claims" in insurance)
> * Acronyms and DSL keywords match your team's definitions
> * Core business logic flows are understood
> * Domain-specific patterns and conventions are recognized

> **Constraints & Patterns**
>
> * Coding conventions and style patterns are identified
> * Security and compliance constraints are captured (HIPAA, PCI-DSS, GDPR often need explicit ingestion prompt context)
> * Testing patterns and coverage expectations are reflected
> * Build and deployment pipeline details are accurate

## Why This Matters

The tech spec gives your team an always-current, queryable understanding of your technology estate:

* **For developers** - Reduced time spent reverse-engineering legacy systems and maintaining stale documentation
* **For executives** - Unknown liabilities become managed exposures with auditable system lineage produced on demand
* **For the organization** - Modernization scoping based on verified system structure instead of guesswork

> **[Generation Prompts](../../build_preparation/generation_prompts.md)**
>
> Write a generation prompt that translates your development request into a clear build instruction for Blitzy

> **[Prompt Library](https://docs.blitzy.com/templates)**
>
> Browse ready-to-use prompt templates for common use cases

> **[Golden Rules](../../build_preparation/prompt_golden_rules.md)**
>
> Best practices for writing precise, unambiguous prompts

> **[Agent action plan](agent_action_plan.md)**
>
> What happens after your prompt - reviewing the AAP that drives code generation


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.