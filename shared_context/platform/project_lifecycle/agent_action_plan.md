> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Agent action plan

> Review and refine the AAP that drives code generation

Use this page when reviewing the Agent action plan (AAP) that Blitzy generates after you submit a generation prompt. The AAP is a structured breakdown of every file change, dependency, and design decision Blitzy will execute - review it before approving it for code generation.

> [!WARNING]
>
> What the AAP says is what the code does. An incomplete AAP produces incomplete code. Fix issues here, not after generation.

> [!NOTE]
>
> **Jump to:** [What to Review](#what-to-review) | [How to Refine](#how-to-refine) | [Decision Framework](#decision-framework)

## What to Review

Check each AAP section for real content. Placeholders like "TBD" or "To be determined" are not acceptable.

> **Intent Clarification**
>
> * Clear statement of what will be built or changed, and why
> * Matches your original prompt intent without reinterpreting scope
> * No ambiguity about the expected outcome

> **Source Analysis**
>
> * Accurately reflects the current state of your codebase
> * References the correct existing files, modules, and patterns
> * Identifies constraints and dependencies that affect implementation

> **Target Design**
>
> * Technical approach and architecture decisions are explicit
> * Specifies methods, libraries, and patterns by name
> * Consistent with your development guide and existing architecture

> **Transformation Mapping**
>
> * Every file to be created or modified is listed with specific changes
> * Logic and behavior changes are described, not just structural changes
> * Edge cases and error handling are addressed

> **Dependency Inventory**
>
> * External libraries, APIs, and internal modules are identified
> * Version constraints are specified where relevant
> * No surprise dependencies that were not in your prompt

> **Scope Boundaries**
>
> * In-scope and out-of-scope items are explicitly listed
> * Matches the scope you intended, nothing silently added or dropped
> * Preservation requirements for existing code are stated

> **Special Instructions**
>
> * Critical constraints and non-negotiable requirements are captured
> * Project-specific conventions or restrictions are reflected
> * Every directive from your prompt is present and unweakened

> **Rules Verification**
>
> * The intent of every custom rule you added appears in the AAP (Blitzy paraphrases rules, so check for intent, not exact wording)
>
> * Blitzy may also surface rules it inferred from your codebase - review these alongside your explicit rules
>
> * No custom rules were omitted entirely
>
> > [!NOTE]
> >
> > A rule may be absent from the AAP if it conflicts with another rule, contradicts a codebase convention, or overlaps with an existing requirement. This is expected, not a bug. Compare your project's rules list on the platform against the AAP. If a rule was dropped and you still need it, add it back through Refine, prompt refinement, or inline editing before approving.

## How to Refine

If the AAP needs changes, choose a refinement path based on the scope of the problem.

**Refine**

**Best for** - Adjusting the implementation approach or making minor scope changes without regenerating the full plan.

Select **Refine** on the AAP review screen and describe what to change. Blitzy adjusts the plan and accounts for all relational changes your refinement touches - dependent files, shared interfaces, and downstream effects.

> [!NOTE]
>
> Refine input accepts a minimum of 30 characters with no maximum limit.

Keep refinements focused on implementation approach: method choices, ordering, patterns, or narrow scope adjustments. For major scope changes, discard the AAP and edit the prompt instead.

**Prompt Refinement**

**Best for** - Broad changes, missing sections, or when multiple sections need rework.

Update your generation prompt to address the gaps, then regenerate the AAP. The entire plan is rebuilt from scratch.

An LLM can help you revise the prompt. Feed it your original prompt and describe what the AAP got wrong:

```
Refine this prompt to fix the Agent action plan issues listed below.
Only change what is needed. Keep the rest of the prompt intact.

ORIGINAL PROMPT:
[Your prompt]

ISSUES:
- [Section name: what is wrong and what it should say]
```

**Inline AAP Editing**

**Best for** - Targeted fixes to a specific detail or section without regenerating everything else.

Download the AAP as a markdown file, edit the content directly, then re-upload.

> [!WARNING]
>
> Do not rename, remove, or reorder any markdown headings. Only edit content under existing headings.

An LLM can help with inline edits. Give it the full AAP markdown and tell it exactly what to change:

```
Edit this Agent action plan markdown. Do NOT rename, remove, or reorder any headings.
Only modify the content under the headings I specify.

CURRENT AAP:
[Your downloaded AAP markdown]

EDITS:
- Under "[heading name]," replace "[current content]" with "[corrected content]"
- Under "[heading name]," add "[missing detail]"
```

Always diff the LLM output against the original before re-uploading. Confirm no headings were renamed or removed.

## Decision Framework

| AAP State | Decision | Action |
| - | - | - |
| All sections complete and accurate | **Approve** | Proceed to code generation |
| Implementation approach needs adjustment | **Refine** | Describe changes in the Refine input; Blitzy adjusts the plan |
| Targeted fixes in 1-2 sections | **Inline edit** | Download, edit content under existing headings, re-upload |
| Broad gaps or missing sections | **Prompt refinement** | Update prompt, regenerate the full AAP |
| Fundamental issues after 2+ iterations | **Discard** | Return to the project status page and start over with a new generation prompt |

> **[Golden Rules](../../build_preparation/prompt_golden_rules.md)**
>
> Best practices for writing precise prompts

> **[Project Guide Review](project_guide.md)**
>
> Next step after AAP approval and code generation

> **[Generation Prompts](../../build_preparation/generation_prompts.md)**
>
> Write generation prompts for Blitzy


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.