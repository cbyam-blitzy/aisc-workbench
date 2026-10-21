> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Building with Blitzy

> Integrate the platform into your existing sprint workflow, team roles, and development process

> **Before You Start - Prerequisites**
>
> Ensure you have completed these prerequisites:
>
> * **Blitzy Account Setup** - Your team has active Blitzy accounts with appropriate licenses
> * **Repository Connected** - Your codebase is connected to Blitzy and successfully ingested (see [Codebase Ingestion](../../build_preparation/ingestion_prompts.md))
> * **Team Access Configured** - Team members have been granted appropriate permissions based on their roles
> * **Initial Training** - Team members have completed the [Quickstart guide](quickstart.md)

## Introduction

Blitzy adapts to your team's needs with three flexible integration workflows. Whether you're accelerating standard sprint work, tackling large-scale refactors, or improving code quality, Blitzy fits seamlessly into your existing development process.

Choose the workflow that matches your current priority:

* **Parallelize Epics** - Run major refactors or new initiatives alongside current work
* **Accelerate Sprints** - Take 1-2 week user stories and complete them faster
* **Fortify Code** - Add test suites, documentation, or apply architectural patterns

## Getting Started

Choose your workflow and follow the recommended first steps:

**Parallelize Epics**

**Recommended for:** Major refactors, migrations, or new initiatives

* Identify a high-value initiative that requires significant capacity
* Create a detailed technical specification (more detail than sprint work)
* Launch the project and check in weekly while team continues sprint work

**Accelerate Sprints**

**Recommended for:** Regular incremental development work and user story delivery

* **Simple user stories** - Single task user stories work well for full-stack features with small scope
* **Complex user stories** - Use sequential subtask approach (see [Best Practices](#best-practices)) or confine to a single architectural layer (e.g., all frontend, all API, or all data layer)
* Select a user story from your current sprint, break it into sequential subtasks (STORY-001 through STORY-00N)
* Store subtask details in a `user-stories/` folder and execute in order
* Run them through Blitzy as a cohesive body of work, one subtask at a time

**Fortify Code**

**Recommended for:** Technical debt, testing, documentation, and architectural improvements

* Pick one high-value quality improvement (e.g., tests for your most critical module)
* Start small: one module, one pattern application, or one documentation pass
* Launch alongside your next sprint to prove it doesn't impact velocity

> [!NOTE]
>
> **Why this approach works:**
>
> * Easier validation with contained scope
> * More meaningful deliverables
> * Better understanding of Blitzy's capabilities at scale
> * Once comfortable, combine workflows (e.g., sprint work + quality improvements running in parallel)

## Development Workflows

### Workflow Options

> **Workflow 1: Parallelize Epics**
>
> **Best For:** Major refactors, migrations, or new initiatives that would otherwise block the team
>
> **Use Case:** You have a large-scale project (multi-week or multi-month epic) that you want to run in parallel with your team's current sprint work without disrupting velocity.
>
> **The Process:**
>
> 1. **Initial Setup** - Project Lead creates comprehensive technical specification for the large initiative
> 2. **Ongoing Generation** - Blitzy works on the large project while team continues regular sprint work
> 3. **Periodic Review** - Weekly or bi-weekly check-ins on generated code
> 4. **Final Integration** - Team dedicates a sprint to final review, testing, and deployment
>
> **Blitzy Impact:**
>
> * Major initiatives that would be postponed indefinitely now get delivered
> * Epics that would take months complete in weeks
> * Team maintains current sprint commitments without disruption

> **Workflow 2: Accelerate Sprints**
>
> **Best For:** Regular incremental development work and user story delivery
>
> **Use Case:** You have a 1-2 week user story in your sprint backlog that you want to complete faster and with higher quality.
>
> **The Process** (see the Weekly Sprint Flow example below for a visual representation):
>
> 1. **End of Week** - Project Lead creates prompts from user stories and launches Blitzy projects
> 2. **Overnight/Weekend** - Blitzy generates \~80% of the implementation (zero developer time)
> 3. **Following Week** - Developers review, refine final 20%, and deploy
>
> **Blitzy Impact:**
>
> * More tasks completed per sprint
> * Developers focus on code reviews and refinement, not building from scratch
> * Frees up time for technical debt or innovation work

> **Workflow 3: Fortify Code**
>
> **Best For:** Technical debt, testing, documentation, and architectural improvements
>
> **Use Case:** You need to improve code quality, add test coverage, generate documentation, or apply architectural patterns consistently across your codebase.
>
> **The Process:**
>
> 1. **Identify Quality Goals** - Define specific quality improvements (e.g., "increase test coverage to 80%", "add JSDoc to all public APIs")
> 2. **Create Focused Prompts** - Break improvements into logical chunks (by module, feature, or pattern)
> 3. **Launch Alongside Sprints** - Start Blitzy projects for quality improvements while team works on features
> 4. **Asynchronous Review** - Developers review and merge quality improvements between feature work
> 5. **Continuous Integration** - Make quality improvements a regular part of your workflow
>
> **Blitzy Impact:**
>
> * Quality improvements happen without taking sprint capacity
> * Test coverage increases from 40% → 80%+ in weeks
> * Documentation exists and stays current
> * Technical debt decreases continuously

<a id="best-practices"></a>

> **Best Practices For Best Results**
>
> * Epics that take a few weeks to a few months of effort
> * Epics broken into sequential, dependent stories
> * Work with clear, defined scope
> * Stories following your company's standards

> **Ineffective Approaches For Suboptimal Results**
>
> * Tiny tasks (\< half day) - use Copilot instead
> * Mixing unrelated features in one project
> * Vague requirements without clear deliverables
> * Stories without clear sequential dependencies

## Technical Support

Blitzy provides AI Solution Consultants, and some contracts include Forward Deployed Engineers, to assist with:

* SDLC integration planning
* Team role definition and training
* Sprint workflow optimization
* Success metrics tracking
* Scaling Blitzy usage across teams

These resources can help customize this workflow to match your organization's specific SDLC processes and tooling.


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.