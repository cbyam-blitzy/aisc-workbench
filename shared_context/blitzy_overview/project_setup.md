> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Project Setup

> Set up a Blitzy project from account provisioning through repository configuration, branch isolation, source control integration, and project creation

This guide walks you through setting up your environment and creating a new Blitzy project, from initial account provisioning through to project creation on the platform.

> [!NOTE]
>
> **Jump to:** [Account Provisioning](#phase-1-account-provisioning) | [Repository Structure](#phase-2-repository-structure-configuration) | [Branch Configuration](#phase-3-branch-configuration) | [Source Control Integration](#phase-4-source-control-integration) | [Codebase Context](#phase-5-codebase-context-configuration) | [Project Creation](#phase-6-project-creation) | [Sharing Your Project](#sharing-your-project)

Before beginning, ensure you have:

* **Administrative access** - to your source control organization (required to install the Blitzy integration)
* **Team member list** - for account provisioning
* **Target repositories** - identified
* **Build documentation** - ready

## Phase 1: Account Provisioning

Submit a list of email addresses for all users requiring platform access to your Blitzy technical contact. When submitting the list, categorize users by their required role level:

* **Users** - Standard user access for code generation workflows
* **Admins** - Project and workflow management capabilities
* **Super Admins** - Platform configuration and organizational settings

Account creation is handled by Blitzy. Users receive email invitations upon completion of the provisioning process.

**Role Permissions:** For detailed specifications on capabilities and restrictions for each role type, refer to the [Teams & Role Configuration guide](/administration/teams).

## Phase 2: Repository Structure Configuration

**Single Repository**

If you are onboarding a single repository, no additional configuration is required for this phase. Proceed directly to Phase 3: Branch Configuration.

**Multiple Repositories**

For multi-repository projects (microservices, monorepo decomposition, shared libraries), Blitzy uses Git submodules to maintain context across related codebases and understand inter-repository dependencies.

**To implement:** Create a parent repository, add child repositories as submodule references, and configure tracking branches. See the **[Git Submodules Guide](/administration/submodules)** for complete setup instructions with Git commands and configuration examples.

## Phase 3: Branch Configuration

Create a dedicated branch for Blitzy operations from your target base branch (typically `main` or `dev`):

```bash theme={null}
git checkout main
git checkout -b blitzy
git push origin blitzy
```

### Rationale for Branch Isolation

Blitzy requires a stable reference point during code ingestion. Using an inactive branch prevents synchronization issues caused by frequent commits to active development branches. This isolation ensures that the AI has a consistent view of your codebase during analysis and generation.

### Blitzy Workflow

The isolated branch workflow follows this pattern:

**1. Ingestion**

Blitzy ingests code from the `blitzy` branch to build its understanding of your codebase

**2. Generation**

Generated code and modifications are committed to the `blitzy` branch

**3. Review**

Changes are reviewed via standard pull request process

**4. Integration**

Approved changes are merged to active branches (`dev`, `main`) through your existing CI/CD pipeline

> [!WARNING]
>
> **Do not push changes to the `blitzy` branch while code generation is in progress.** Pushing commits during generation causes conflicts, lost work, or broken builds. Wait until generation completes and the pull request is delivered before pushing any changes to the branch.

This isolation ensures generated code undergoes your existing review and CI/CD processes before integration into your codebase. All generated code is subject to the same quality gates, automated testing, and human review as manually written code.

## Phase 4: Source Control Integration

Connect your source control provider to enable repository access for the Blitzy platform.

> [!NOTE]
>
> For organization-owned repositories, a workspace or organization admin may need to authorize the Blitzy integration before individual users can connect their accounts.

### Connecting a Provider

**1. Log In**

Log into the Blitzy platform

**2. Navigate to Integrations**

Go to **Settings > Integrations**

**3. Connect Provider**

Select your source control provider and complete the connection flow it presents. An OAuth provider opens an authorization page for approval. [Azure DevOps Server](/integrations/azure-devops-server) asks for a collection URL and a personal access token without leaving Blitzy.

**4. Confirm Repository Access**

Confirm Blitzy reaches every repository that will be ingested (see below)

**5. Choose Sharing**

Keep the connection private with **Just me**, or make it available to your team with **Share with team**, then click **Done**. See [Managing](/integrations/managing) to change the choice later.

### Repository Access Configuration

Blitzy must reach **all repositories that will be ingested onto the platform**, including submodule and shared-library repositories. How you arrange that depends on how your provider grants access:

* **Repository-level selection** - GitHub and GitHub Enterprise Server ask which repositories the Blitzy app may use. Choose between the two configurations below.
* **Credential-level access** - Azure DevOps Server, Azure DevOps, GitLab, GitLab Self-Managed, Bitbucket and Bitbucket Data Center give Blitzy exactly what the connected credential reaches, with no per-repository choice in Blitzy. Connect with an account whose own permissions cover every repository Blitzy will ingest.

**All Repositories**

Granting access to all repositories is the simplest approach and ensures no access issues during ingestion. This is the recommended configuration for most organizations.

**Selected Repositories**

If you choose to grant access to specific repositories only, include every repository Blitzy will ingest: parent repositories, each submodule individually, and any shared dependency repositories.

> [!WARNING]
>
> **Submodule access is not inherited.** Granting access to a parent repository does not automatically include its submodules. Each must be explicitly authorized.

For additional information on configuring environment-specific access and credentials, refer to the [Environment Configuration guide](/administration/environments).

## Phase 5: Codebase Context Configuration

### Environment Setup

Create a Blitzy environment configuration containing the information necessary to build and run your codebase. This enables Blitzy to understand your development environment and generate code that integrates with your existing build processes.

#### Build Instructions

Provide complete build and runtime setup steps that a developer would need to get your project running locally:

* **Dependency installation commands** - e.g., `npm ci`, `mvn clean install`, `pip install -r requirements.txt`
* **Build tool invocations** - required flags and configuration
* **Pre-build script execution** - any setup scripts that must run first
* **Compilation steps** - build order for multi-module projects
* **Local development server** - startup commands

See the **[Environment Configuration Guide](/administration/environments)** for detailed examples.

#### Secrets and Environment Variables

Document all required configuration values: API keys, PATs for private registries, service endpoints, feature flags, and authentication credentials. Use placeholder syntax with curly braces (e.g., `${DATABASE_PASSWORD}`, `${API_KEY}`) to reference secrets in your build instructions. Actual credential values are encrypted and stored separately.

See the **[Environment Configuration Guide](/administration/environments)** for complete details on variables vs. secrets, encryption, and configuration best practices.

### Ingestion Prompt (Optional)

The ingestion prompt provides architectural and domain-specific context beyond what can be derived from code analysis alone. While optional, providing this information significantly improves code generation accuracy and quality.

#### Recommended Content

* **Architectural Patterns** - "Services follow a three-tier architecture: Controllers handle HTTP, Services contain business logic, Repositories manage data access"
* **Code Organization** - "Feature modules are organized by domain entity; shared utilities reside in `/core`"
* **Framework Patterns** - "All database access uses the Repository pattern with Specification objects for complex queries"
* **Domain Terminology** - "In this codebase, 'instruments' refer to financial securities; 'positions' represent holdings"
* **Technical Constraints** - "All API responses must include correlation IDs for distributed tracing"
* **Testing Requirements** - "Generated code must include unit tests following the Arrange-Act-Assert pattern"

## Phase 6: Project Creation

With your environment fully configured, create your project on the Blitzy platform.

**1. Open Workspace**

Navigate to your **Workspace** (homepage)

**2. Create Project**

Click **Create new project**

**3. Select Project Type**

Choose between **New Product** or **Existing Product** based on your use case

> **[New Product](/quickstart#new-product)**
>
> Starting from scratch. Skip ingestion and go straight to writing a generation prompt.

> **[Existing Product](/quickstart#existing-product)**
>
> Working with an existing codebase. Blitzy ingests your repository before code generation begins.

## Sharing Your Project

When an administrator turns on project-sharing enforcement, every project must be shared, either with your whole organization (an organization-wide share) or with one or more teams (a team share). Private, owner-only projects are not allowed while enforcement is active, so a shared project is any project other members can reach and a private project is one only its owner can see. Enforcement applies at two moments: creating a new project and opening a project that is still private.

### Create a project under enforcement

When enforcement is active, the create-project form adds a mandatory "Share your project" section, and the "Create project" button stays disabled until you choose a share target.

**1. Open the Share your project section**

The create form shows a "Share your project" section with the helper text "Your admin requires all projects to be shared".

**2. Choose a share target**

Select one of the two options:

* **Share with org** - Everyone in your org gets access
* **Share with teams** - Choose one or more teams

**3. Select teams if sharing with teams**

If you choose "Share with teams", pick one or more destination teams from the team selector.

**4. Create the project**

After you select a share target, the "Create project" button becomes available. Select it to create the shared project.

### Open a private project under enforcement

If you open a project that is still private while enforcement is active, a blocking forced-share prompt appears and must be resolved before the project opens.

**1. Review the prompt**

The prompt is titled Share ‘ProjectName’ to continue, where your project's actual name appears in single quotes (for example, Share ‘Acme API’ to continue). Its subtitle reads "Your admin requires all projects to be shared".

**2. Choose a share target**

Select "Share with org" or "Share with teams", and pick one or more teams if you share with teams.

**3. Share or go back**

Select "Share" to share the project and open it; the "Share" button stays disabled until you select a target. Select "Go back" to leave without opening the project.

> [!WARNING]
>
> Sharing a project with one or more teams gives every member of those teams full access to the project. If the project was still private and enforcement is active, sharing it to a team also transfers ownership permanently to the team, exactly as the prompt states: "Ownership transfers permanently to the team, and you continue as a member with full access". You stay on the project as a member with full access, so it remains in your projects list and you can open it, rename it, and change who it is shared with. Sharing with your organization instead makes the project visible to every member of the organization and does not transfer ownership. While enforcement is active, a shared project cannot be reverted to a private (owner-only) project.

## Related Guides

> **[Teams](/administration/teams)**
>
> Configure the admin setting that requires project sharing

> **[Workspace](/platform/workspace)**
>
> Filter projects by visibility and read sharing badges

## Technical Support

Contact your assigned Blitzy AI Solutions Consultant for configuration validation or troubleshooting during project setup.


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.