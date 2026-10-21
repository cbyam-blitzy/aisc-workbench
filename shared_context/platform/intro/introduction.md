> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Introduction

> How Blitzy turns your requirements into reviewed, tested pull requests

<Card title="Get Started" icon="rocket" horizontal href="/introduction">
  Onboard your first repository and generate enterprise-grade code with Blitzy.
</Card>

## What Blitzy Does

Blitzy generates code from your prompts, validates in isolated environments, and opens a pull request for your review. The engineer is in the lead from the implementation plan to the final merge.

<Frame caption="You review every decision before code ships">
  <img src="https://mintcdn.com/blitzy-c2eefe5a/zW1V6gp28Dv1LcG8/images/blitzy-human-in-the-loop.webp?fit=max&auto=format&n=zW1V6gp28Dv1LcG8&q=85&s=ff07fa73b2db833f3784b92605d07eb1" alt="Blitzy Human-in-the-Loop Workflow" width="2196" height="948" data-path="images/blitzy-human-in-the-loop.webp" />
</Frame>

***

## What Makes Blitzy Different

<CardGroup cols={2}>
  <Card title="Codebase Understanding" icon="brain" href="/platform/knowledge-base">
    Learns your architecture, patterns, and domain terminology.
  </Card>

  <Card title="Autonomous Generation" icon="rotate" href="/project-lifecycle/aap-review">
    Generates and validates code continuously until the job is done.
  </Card>

  <Card title="SDLC Integration" icon="clone" href="/sdlc-integration">
    Adapts to your development lifecycle and evolves alongside your processes.
  </Card>

  <Card title="Visual Input" icon="figma" href="/integrations/figma">
    Attach Figma frames directly to prompts for design-aware code generation.
  </Card>

  <Card title="Living Artifacts" icon="book-open" href="/project-lifecycle/tech-spec-review">
    Evolving Tech specs, reviewable action plans, and Project Guides for handoff.
  </Card>

  <Card title="Chat with Knowledge Graph" icon="message" href="/platform/knowledge-base">
    Translate your domain specific language into software estate insights.
  </Card>
</CardGroup>

***

## Who Uses Blitzy

<Tabs>
  <Tab title="Engineering Managers">
    * Large-scale refactoring that would take quarters to complete manually
    * Security vulnerabilities requiring systematic remediation across codebases
    * Architectural improvements that keep getting deprioritized
  </Tab>

  <Tab title="Technical Executives">
    * Modernization projects requiring months of engineering effort
    * Undocumented systems needing comprehensive documentation
    * Pattern migrations across hundreds or thousands of files
  </Tab>

  <Tab title="Product Managers">
    * Adding features without expanding headcount
    * Launching products that wouldn't otherwise be feasible
    * Maintaining consistent code quality across large teams
  </Tab>

  <Tab title="Engineering Leaders">
    * Shipping critical work without pulling senior engineers off roadmap items
    * Compressing development timelines from months to days
    * Freeing teams to focus on high-value problems
  </Tab>
</Tabs>

***

## Key Concepts

Five terms you need to know before using Blitzy:

| Concept | What It Is | When You Use It |
| - | - | - |
| **[Ingestion](../../build_preparation/ingestion_prompts.md)** | Blitzy analyzes your codebase to understand architecture, patterns, and terminology. | Required for existing codebases. Not needed for greenfield projects. |
| **[Technical Specification](../project_lifecycle/technical_specification.md)** | A knowledge base Blitzy generates after ingestion, documenting your architecture and conventions. | Generated automatically. Review it to confirm Blitzy understands your codebase. |
| **[Agent action plan (AAP)](../project_lifecycle/agent_action_plan.md)** | A detailed implementation plan showing which files will be created or modified. | Every generation. This is your primary control point — review, edit, approve, or reject. |
| **[Project Guide](../project_lifecycle/project_guide.md)** | Documentation generated alongside your code, explaining architecture decisions and next steps. | Generated automatically after every code generation. |
| **[Runtime Validation](../../build_preparation/setup/environment_config.md)** | Blitzy compiles and tests generated code in isolated environments before creating a PR. | Automatic when environment configuration is provided. |

See the full [Glossary](glossary.md) for all Blitzy-specific terminology.


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.