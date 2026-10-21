> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Document Code

> Generate API docs, inline comments, or developer guides

Start here when your codebase needs API specifications, inline comments, or developer guides.

## How it works in Blitzy

**1. Describe what needs documenting**

Name the modules, the format, and the audience. "Generate OpenAPI 3.0 specs for all endpoints in `src/routes/api/`" is specific. "Document the codebase" is too broad.

**2. Review the Agent action plan**

Blitzy shows you which files it will document, what format each will use, and how it will organize cross-references.

**3. Generate and review**

Blitzy produces the documentation and integrates it with your existing tooling. Review for technical accuracy - Blitzy gets the structure right, but domain context sometimes needs a human pass.

**4. Merge or refine**

If the docs are accurate, merge them. If terminology or cross-references need adjustment, update your prompt with a glossary or style examples and run again.

## What makes a good prompt?

A good documentation prompt describes what your team needs to understand, not just which files to annotate.

**Name the format and the audience.** "Generate JSDoc for all public methods in `src/services/`, targeting developers who will consume these services via the internal API." Format tells Blitzy how to write. Audience tells Blitzy what to explain.

**Provide a glossary for domain terms.** If your codebase uses terms like "reconciliation" or "fulfillment" in domain-specific ways, define them. Blitzy documents code structure accurately but cannot infer business meaning.

**Point to documentation your team already likes.** If one module has great docs, reference it: "Follow the style and depth of the documentation in `src/services/auth/README.md`."

> [!TIP]
>
> Read the [Golden Rules](../prompt_golden_rules.md) before writing your first documentation prompt. They cover the structural patterns that consistently produce the best results.

## Prompt template

> **Documentation prompt template**
>
> ```
> Document [modules/components] in [Project Name]. Add [documentation type]
> that helps [target audience] understand the code.
>
> DOCUMENTATION SCOPE
>
> - What modules need documentation?
>   [List specific paths and files.]
> - What type of documentation?
>   [Inline comments, JSDoc/docstrings, OpenAPI specs, module READMEs.]
> - Who is the audience?
>   [New hires, API consumers, future maintainers.]
>
> FORMAT & STYLE
>
> - What documentation standard?
>   [JSDoc 3.6+, Sphinx, OpenAPI 3.0, Google style guide, etc.]
> - What existing docs should new docs match?
>   [Point to a file with documentation your team likes.]
>
> DOMAIN CONTEXT
>
> - What domain terms need defining?
>   [Glossary of business-specific terminology the code uses.]
> - What architectural context matters?
>   [How this module fits into the broader system.]
>
> CONSTRAINTS
>
> - Add documentation only - do not modify code logic.
> - Comments explain WHY, not WHAT. No narration of obvious code.
> - Do not refactor or restructure code during documentation.
> ```

## What if something goes wrong?

> **Generated documentation is technically inaccurate**
>
> Code analysis may miss domain context. Provide domain glossaries, link to architecture documentation, and review generated docs with subject matter experts for technical accuracy.

> **Documentation format doesn't match standards**
>
> Style guide may not be specified. Reference existing documentation files showing preferred style, specify validation tools (ESLint jsdoc, sphinx-build), and include format examples in prompt.

> **Cross-references are broken or missing**
>
> Linking strategy may be unclear. Define explicit cross-reference patterns, specify how to link related sections, and validate all links resolve correctly after generation.

> **Documentation duplicates existing content**
>
> Scope may overlap with existing docs. Audit current documentation before requesting new docs, define clear boundaries for what should be documented, and specify single-source-of-truth for each topic.

> **Code examples don't compile or run**
>
> Examples may lack proper context. Add the [Enforce Code Style Patterns](../rule_templates/enforce_code_style_patterns.md) rule to your project on the platform, validate all examples in actual environment, and include complete imports and setup in examples.


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.