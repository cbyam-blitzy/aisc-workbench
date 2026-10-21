> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Project Guide

> Review the auto-generated Project Guide for accuracy and completeness before making a merge decision.

## Overview

After code generation, Blitzy delivers a Project Guide with every pull request - a summary of what was built, which requirements were targeted, and what work remains. Your job is to review it alongside the PR diff and recommend a merge decision.

The **Table of Contents** lets you jump directly to any section of the Project Guide. It is collapsible on narrow screens and appears as a sidebar on wide screens.

> [!NOTE]
>
> Project Guide review happens after code generation and before the merge decision. Review the guide alongside the PR diff, not in isolation.

## What to Review

> **Requirement Coverage**
>
> * Every requirement from the generation prompt appears in the Project Guide
> * No requirements were silently dropped or reinterpreted
> * Scope boundaries match what was requested (nothing added, nothing omitted)
> * Out-of-scope items are explicitly documented

> **Implementation Accuracy**
>
> * Generated code matches what the Project Guide describes
> * File paths, function names, and module structures align with the guide
> * Business logic behaves as specified, not just structurally present
> * Edge cases and error handling match documented behavior

> **Standards Compliance**
>
> * Implementation follows patterns defined in your development guide
> * Naming conventions, architecture layers, and coding standards are respected
> * No unapproved dependencies or architectural deviations introduced

> **Documentation and Tests**
>
> * Unit and integration tests cover the implemented requirements
> * Test cases include both happy paths and edge cases
> * API documentation, inline comments, or README updates are present where needed
> * Any new configuration or environment variables are documented

## Review Workflow

> [!NOTE]
>
> The Project Guide is the first item in [PR Review](/project-lifecycle/pr-review), the step you reach after code generation. Reviewing it there puts the guide and the ordered change sequence in the same surface, and it is what the walkthrough falls back to when the review content is unavailable.

**1. Open the Project Guide and PR together**

Pull up the Project Guide and the PR diff in adjacent views. The Project Guide is your map for the review, the PR diff is the territory.

**2. Run and test changes using the Project Guide**

Follow the Project Guide's setup and run instructions to build and test the changes locally. Verify that the implementation behaves as described, not just that the code compiles.

**3. Review source code guided by declared changes**

Use the Project Guide's list of declared changes and remaining work to focus your code review. Check that completed items are fully implemented and that remaining work items are accurately scoped.

**4. Summarize Findings and identify next steps**

After walking the PR Review sequence, compile your findings. Summarize what was completed, list gaps with specific details, and state your merge recommendation using the decision framework below.

## Decision Framework

| Completion | Gaps | Decision | Action |
| - | - | - | - |
| All or nearly all items done | None or minor | **Merge** | Approve. Document minor items for follow-up. |
| Most items done | No critical gaps | **Merge with follow-ups** | Approve with tickets for remaining items. |
| Several items incomplete | Major gaps | **Refine** | Request changes. List specific items to address. |
| Large portion incomplete | Substantial | **Discard** | Close PR. Revisit prompt or AAP before regenerating. |

> [!WARNING]
>
> Critical gaps override completion. Security vulnerabilities, data integrity issues, or broken core functionality mean Discard regardless of how much else was completed.

## Documenting Gaps

Be specific when documenting gaps. "Authentication needs work" is not actionable. "Token refresh endpoint returns 500 on expired tokens, need refresh logic with exponential backoff" is.

**Template**

```text theme={null}
Requirement: [Project Guide reference]
Status: [Not Started | Partial - X%]
What's Missing:
  - [Specific functionality or behavior not implemented]
  - [Edge cases not handled]
  - [Tests not written]
Impact: [HIGH | MEDIUM | LOW] - [Brief business or technical impact]
Effort: [Estimated hours to complete]
```

**Example**

```text theme={null}
Requirement: REQ-015 User Profile Update
Status: Partial - 60%
What's Missing:
  - No email format validation on update endpoint
  - No handling for concurrent updates (last-write-wins, should return 409)
  - Profile photo upload not implemented (text fields only)
  - No rate limiting on update endpoint
Impact: MEDIUM - Core functionality works but edge cases cause data issues
Effort: 8 hours
```

**Why Document Gaps?**
Documenting Gaps in this manner will help when creating followup tickets, a Refine PR, or rewriting the generation prompts depending which path you take to resolve these gaps.

**Common gap categories:**

* **Missing functionality** - Features specified but not present in the PR
* **Incomplete implementation** - Features partially built, missing edge cases or validation
* **Missing tests** - Code works but lacks adequate test coverage
* **Missing documentation** - No API docs, inline comments, or config documentation
* **Security gaps** - Authentication, authorization, or input validation missing
* **Performance issues** - Requirements with response time or throughput targets not met

## When to Escalate

| Escalate to | When | What to include |
| - | - | - |
| Engineering Lead | Significant incomplete work, 3+ standards deviations, uncertain gap severity | Gap summary, deviation list, your recommendation |
| Product Owner | Requirements conflict with each other, scope changed during generation, ambiguous acceptance criteria | Conflict details, what was implemented vs. expected, proposed resolution |
| Architecture Reviewer | Unapproved architectural changes, new external dependencies, pattern violations | Code locations, relevant development guide sections, concern summary |

## Related Guides

> **[Agent action plan review](/project-lifecycle/aap-review)**
>
> Review and refine the AAP before code generation begins.

> **[Tech spec review](/project-lifecycle/tech-spec-review)**
>
> Verify Blitzy's understanding of your codebase after ingestion.

> **[PR Review](/project-lifecycle/pr-review)**
>
> Review a generated pull request as an ordered, grouped sequence.

> **[Project Setup](/project-lifecycle/sharing)**
>
> Configure your repository, environment, and project on the platform.

> **[PR Review](/project-lifecycle/pr-review)**
>
> Walk the generated pull request, triage by risk, and decide: merge, refine, or close.

> **[Golden Rules](/prompt-engineering/golden-rules)**
>
> Best practices for writing precise generation prompts.


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.