> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Knowledge Base

> Your codebase, mapped and searchable — organized by repository and branch

The technical specifications represents Blitzy's detailed understanding of each codebase's architecture, patterns, conventions, domain terminology, and technical constraints. Toggle to [Workspace](workspace.md) to write generation prompts or [Proactive Insights](proactive_insights.md) to find and remediate vulnerabilities.

## Why the Knowledge Base Matters

Every project Blitzy runs draws from the Knowledge Base — your codebase mapped into structured context so the platform builds with your architecture, patterns, and conventions instead of generic assumptions.

**Key capabilities:**

* Live documentation that automatically syncs with code changes
* Repository and branch organization using `{repo_name}/{branch_name}` format
* Structured [specification format](../project_lifecycle/technical_specification.md) covering architecture to infrastructure
* Seamless workspace integration for context review and code generation

**Team Productivity**

* **Accelerates onboarding** - New team members gain instant understanding of codebase architecture and conventions
* **Living documentation** - Always-current docs that evolve with your codebase, replacing months of manual effort
* **Facilitates code reviews** - Reviewers reference specs to validate that code follows established patterns

**Business Value**

* **Rapid legacy understanding** - Comprehensive documentation of undocumented codebases created in days, not months
* **Supports compliance** - Documents security patterns, audit requirements, and regulatory constraints
* **Accelerates delivery** - Engineers spend less time understanding context and more time building features

**Multi-Repository Management**

* **Organized by repo and branch** - Clean separation using `{repo_name}/{branch_name}` format
* **VCS integration** - Filter by one of our supported [integrations](https://docs.blitzy.com/integrations/integrations-welcome) to focus on specific platforms
* **Cross-repository understanding** - See how microservices and shared libraries relate across your organization

## Using the Knowledge Base

### Sidebar Organization

The Knowledge Base sidebar displays your complete technical specifications library with powerful filtering and organization. Filtering covers every version-control platform you have connected, including Azure DevOps Server:

> **Tech specs Count**
>
> Total number of specifications you have access to, updating dynamically as you apply filters.

> **Filters**
>
> Narrow by VCS platform (GitHub, GitLab, Bitbucket), project name, or teams with access.

> **Naming Format**
>
> Each spec follows `{repo_name}/{branch_name}` format for instant context on repository and branch.

### When to Use the Knowledge Base

**Before Generation**

Review specifications before writing prompts to ensure you understand:

* Current architectural patterns you should follow
* Existing conventions for file organization and naming
* Domain terminology to use in your requests
* Technical constraints that must be respected

**During Code Review**

Reference specifications when reviewing generated code to verify:

* Code follows documented architectural patterns
* Naming conventions match existing standards
* Domain terminology is used correctly
* Technical constraints are respected

**Team Onboarding**

Share specifications with new team members to accelerate onboarding:

* Comprehensive codebase overview
* Documented architectural decisions and rationale
* Domain-specific terminology explanations
* Code organization patterns

**Architectural Planning**

Consult specifications when planning new features to:

* Understand existing architectural patterns
* Identify integration points
* Evaluate consistency with current conventions
* Plan changes that align with established patterns

### Getting Started

**1. Access Knowledge Base**

Toggle from Workspace to Knowledge Base using the UI toggle in the platform.

**2. View Your Specifications Library**

The sidebar shows your total tech specs count and all specifications in `{repo_name}/{branch_name}` format.

**3. Apply Filters (Optional)**

Use filters to narrow down by VCS, project name, or teams with access to find relevant specifications.

**4. Select a Specification**

Click any `{repo_name}/{branch_name}` entry to view its complete technical specification.

**5. Review the Specification**

Browse through the sections such as Product Requirements, Technology Stack, Process Flowcharts, and System Architecture.

**6. Navigate to Relevant Sections**

Jump directly to sections like "System Architecture" (Section 5) for patterns or "Appendices" (Section 9) for glossary terms.

**7. Search Within Specifications**

Use search to find specific patterns, classes, or architectural decisions across all sections.

**8. Apply Knowledge in Workspace**

Toggle back to Workspace to create generation requests informed by your specification review.

## Troubleshooting

> **Specification appears incomplete**
>
> * Verify you're viewing the correct branch (`{repo_name}/{branch_name}`)
> * Check that relevant files aren't excluded by `.blitzyignore`
> * Use an [ingestion prompt](../../build_preparation/ingestion_prompts.md) to provide business context and domain knowledge beyond static analysis
> * For submodules, ensure they are [correctly synced](../../build_preparation/setup/git_submodules.md) with proper access granted

> **Specification quality needs improvement**
>
> Use an [ingestion prompt](../../build_preparation/ingestion_prompts.md) to improve specification quality by providing:
>
> * Business context and domain terminology
> * Architectural rationale and evolution
> * Guidance on what code patterns to focus on or ignore

> **Can't find a repository**
>
> * Verify repository access in [Integration settings](https://docs.blitzy.com/integrations/managing)
> * Confirm correct VCS organization/account is connected
> * For submodules, see the [Git Submodules guide](../../build_preparation/setup/git_submodules.md)

> **Branch not showing**
>
> * Confirm branch exists in source control and is synced to remote
> * Verify you have access permissions for the branch
> * Check that branch isn't excluded by repository configuration

**Need help?** Contact support at [support@blitzy.com](mailto:support@blitzy.com) or consult your Blitzy AI Solutions Consultant for Knowledge Base configuration assistance.


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.