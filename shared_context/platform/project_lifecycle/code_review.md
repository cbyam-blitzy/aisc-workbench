> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Code Review

> Review generated code through intent, validation, and code-level inspection

Blitzy generates code from a reviewed plan, not from a blank branch. By the time a PR opens, the important decisions - scope, file coverage, approach - have already been approved in the Agent action plan. Your review starts there, not in the diff.

> [!NOTE]
>
> **Jump to:** [AAP as Source of Truth](#layer-1---the-aap-as-source-of-truth) | [Dynamic Validation](#layer-2---dynamic-validation) | [Code-Level Review](#layer-3---code-level-review)

## The Core Principle - Review Intent, Not Just Implementation

Traditional code review is reactive: a developer writes code, a reviewer reads the diff. At the scale Blitzy operates, that model breaks.

The most important review work on a Blitzy project happens before a single line of code is generated. Blitzy produces reviewable artifacts *before* execution, and its review model is built on three layers - each catching different classes of issues at the lowest cost.

**1. Ingest codebase**

Blitzy indexes your repository and builds the context every later stage works from.

**2. Generate AAP**

Blitzy writes the Agent Action Plan before any code exists.

**3. Review the AAP (layer 1)**

Approve the plan to continue. Requesting changes sends it back to Blitzy, which regenerates the plan.

**4. Execute tasks**

Blitzy generates code against the approved plan and delivers it as commits and pull requests.

**5. Run dynamic validation (layer 2)**

Passing tests, benchmarks and CI checks advance the pull request. Failures return the work to task execution.

**6. Review the code (layer 3)**

Approve to merge. Requesting changes returns the pull request to Blitzy for refinement.

**7. Merge**

The approved pull request merges to your target branch, and Blitzy's context updates to include it.

## Layer 1 - The AAP as Source of Truth

The **Agent action plan (AAP)** is the authoritative specification Blitzy produces before code generation begins. Drawing from the knowledge graph's map of your codebase, it maps every task to specific files, functions, and change types in plain language a domain expert can evaluate.

Blitzy does not improvise beyond the plan. A thoroughly reviewed AAP gives you confidence in the resulting code *before you read a single line of it*. Reviewing the AAP is, in practice, reviewing the code - at a fraction of the cost.

> [!TIP]
>
> The AAP review is your highest-leverage gate. Issues caught here cost minutes to fix. The same issues caught in a diff cost hours.

### Why the AAP Replaces Traditional Diff Review

<table>
  <thead>
    <tr>
      <th scope="col">Dimension</th>
      <th scope="col">AAP Review</th>
      <th scope="col">Diff Review</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <th scope="row">When it happens</th>
      <td>Before code is written</td>
      <td>After code is written</td>
    </tr>

    <tr>
      <th scope="row">What you're reading</th>
      <td>Intent and approach</td>
      <td>Implementation detail</td>
    </tr>

    <tr>
      <th scope="row">Time to catch a wrong decision</th>
      <td>Minutes</td>
      <td>Hours or days</td>
    </tr>

    <tr>
      <th scope="row">Cost to fix</th>
      <td>Low - no code to change</td>
      <td>High - code must be rewritten</td>
    </tr>

    <tr>
      <th scope="row">Scales with output volume</th>
      <td>Yes</td>
      <td>No</td>
    </tr>
  </tbody>
</table>

### What to Look for in an AAP Review

* **Correct system understanding** - Does the plan reflect an accurate read of the existing system?
* **File coverage** - Are the right files being modified? Are any files conspicuously absent?
* **Change sequence** - Does the sequence of changes make sense given system dependencies?
* **Scope appropriateness** - Is the scope appropriate, or has the plan over- or under-reached?
* **Business logic implications** - Are there business logic implications the plan does not account for?

When your team invests in AAP review, code review becomes confirmation, not discovery. For detailed guidance, see [Agent action plan Review](agent_action_plan.md).

## Layer 2 - Dynamic Validation

Once the AAP is approved and code is generated, the question is not "does this code look right?" but "does this code *work*?" Dynamic validation answers that through automated signals, not human reading. For what happens during generation itself, see [Code](code.md).

Test suites, performance benchmarks, and CI pipelines become your second review layer. A thorough AAP review plus passing dynamic validation gives high confidence without a line-by-line diff review.

### Validation Signals

| Signal | What It Proves | When It Is Sufficient |
| - | - | - |
| **Test suites** | Functional correctness against defined expectations | When test coverage is comprehensive and tests are well-written |
| **Performance benchmarks** | No regressions in throughput, latency, or resource usage | When benchmarks cover critical paths and have established baselines |
| **Build and compile** | Structural integrity, no broken imports or type errors | Always - this is the minimum bar |
| **Linting and static analysis** | Adherence to coding standards and pattern consistency | When rules are configured to match your team's conventions |
| **Integration and E2E tests** | Cross-service behavior and user-facing workflows | When integration coverage exists for the modified paths |
| **Computer Use (Windows)** | Visual correctness, UI accessibility, and desktop application behavior through direct screen interaction | When generated code targets Windows desktop applications or requires visual validation beyond headless testing |
| **CI/CD pipeline results** | End-to-end validation through your existing build, test, and deployment pipelines | When pipelines are configured to trigger during generation (see below) |

### CI and CD Pipeline Timing

CI and CD pipelines validate generated code through your existing workflows. When the pipeline runs determines how Blitzy uses the results. Triggering on PR creation is the recommended path, and [Refine PR](pr_review.md#refine) is the most reliable way to act on what the pipeline reports.

**On commit push**

When your pipeline triggers on each commit push to the Blitzy branch, results feed back into the generation cycle. Blitzy reads the pipeline output, identifies failures, and attempts to self-correct before the job ends.

**Configure this path when:**

* Your pipeline runs on push events to any branch
* You want Blitzy to attempt resolving CI failures automatically during generation
* Build, test, or lint failures should block the PR until fixed

Include passing CI checks as a success criterion in your AAP to ensure Blitzy treats pipeline failures as actionable feedback.

> [!NOTE]
>
> Self-correction depends on pipeline visibility, execution speed, and SCM provider configuration. Results vary by environment. If Blitzy does not self-correct, use [Refine PR](pr_review.md#refine) after the PR is created.

**On PR creation**

**Recommended.** When your pipeline triggers on PR creation, it runs after Blitzy has finished generating code. Blitzy agents do not have SCM access at this point - they cannot read pipeline results or push fixes.

**To address CI failures:**

**1. Review pipeline results**

Check the pipeline output on the PR to identify specific failures.

**2. Submit a Refine PR prompt**

Reference the specific failures in a [Refine PR](pr_review.md#refine) prompt.

**3. Blitzy iterates**

Blitzy updates the PR, which triggers the pipeline again.

This is the most reliable path across all SCM providers, regardless of pipeline configuration or permission models.

> [!TIP]
>
> Regardless of when your pipeline triggers, [Refine PR](pr_review.md#refine) is always available as a fallback. Review the CI results on the PR, reference the failures in your Refine prompt, and Blitzy will iterate.

> [!WARNING]
>
> **Pipeline credentials on Azure DevOps Server, Azure DevOps, GitLab, and Bitbucket:** The credentials Blitzy uses for repository access do not always carry pipeline read access. Azure DevOps Server uses a personal access token, and Azure DevOps cloud uses a Microsoft Entra ID application with a service identity. When Blitzy cannot read pipeline results during generation, configure credentials with pipeline read access in your [environment settings](../../build_preparation/setup/environment_config.md), or use [Refine PR](pr_review.md#refine) after the PR is created.

### When Dynamic Validation Is Enough

**Skip deep review**

**High confidence.** Dynamic validation alone can be sufficient when:

* AAP was thoroughly reviewed and approved
* Test coverage is comprehensive for the modified paths
* All tests, benchmarks, and CI checks pass
* Changes are in well-tested modules with established patterns
* Risk tier is **Light** (boilerplate, config, scaffolding, test generation)

In these cases, a spot-check of the diff is appropriate, but a full line-by-line review is not necessary.

**Proceed to code review**

Dynamic validation is not sufficient when:

* Test coverage is thin or nonexistent for the modified paths
* Changes touch business logic encoding regulatory or contractual rules
* New external integrations or auth flows are introduced
* Benchmarks do not cover the critical paths affected
* Dynamic signals pass but the AAP flagged areas of uncertainty

In these cases, proceed to Layer 3.

> [!NOTE]
>
> Dynamic validation does not replace judgment - it replaces *reading*. When your automated signals are strong enough, the reviewer's job shifts from "verify correctness" to "verify that the right things are being tested."

## Layer 3 - Code-Level Review

Code-level review is the final layer. It catches what the AAP and dynamic validation cannot: nuanced business logic, security-sensitive paths, and gaps in automated coverage.

When reviewing a Blitzy pull request, you are not reviewing human-authored code where you can lean on commit history and author intent. You are reviewing a large generated codebase - a fundamentally different problem. Line-by-line reading of tens of thousands of lines is not the goal.

[PR Review](pr_review.md) is the step you reach after code generation. The knowledge graph powers the review notes and test evidence attached to each file, grouping changes by purpose so you can triage by risk and decide what to do next - [merge](pr_review.md#merge), [refine](pr_review.md#refine), or [close](pr_review.md#close).

### Domain-Assigned Reviewers

Large pull requests become tractable when reviewed by the right people, not the most available. A module owner catches deviations immediately that a generalist might miss entirely.

<table>
  <thead>
    <tr>
      <th scope="col">AAP Task</th>
      <th scope="col">Assigned Reviewer</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <th scope="row">Payments</th>
      <td>Payments team reviewer</td>
    </tr>

    <tr>
      <th scope="row">Auth</th>
      <td>Security team reviewer</td>
    </tr>

    <tr>
      <th scope="row">Reporting</th>
      <td>Data team reviewer</td>
    </tr>
  </tbody>
</table>

Distribute review load by domain ownership, not by availability.

## Summary

| Layer | What It Does | When It Happens |
| - | - | - |
| **AAP Review** | Validates intent and approach before any code is written | Pre-execution |
| **Dynamic Validation** | Proves the implementation works through tests, benchmarks, and CI signals | Post-execution, pre-review |
| **Code-Level Review** | Catches what automated signals cannot: nuanced logic, security, and domain-specific concerns | Post-validation, in [PR Review](pr_review.md) |

> **[AAP Review](agent_action_plan.md)**
>
> Review the Agent action plan before code generation begins

> **[PR Review](pr_review.md)**
>
> Walk the generated pull request, triage by risk, and decide: merge, refine, or close


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.