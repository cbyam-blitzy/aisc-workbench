> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Preparing Your Codebase

> Set up your repository and environment so Blitzy can build and test your code

Blitzy works with both single and multi-repository projects. Choose your repository structure first, then configure the environment Blitzy needs to build and test your code.

> [!NOTE]
>
> **Jump to:** [Repository Structures](#repository-structures) | [Environment](#understanding-your-environment) | [What Blitzy Needs](#what-blitzy-needs)

[Wistia video player](https://fast.wistia.net/embed/iframe/afq5po68oa?videoFoam=true)

## Repository Structures

**Single Repository**

For projects in a single repository, Blitzy clones your codebase, creates an isolated `blitzy` branch, and generates code that integrates with your existing architecture.

**Best for:** Monolithic applications, standalone services, or projects with all code in one repository.

**Multi-Repository**

For projects split across repos, Blitzy uses **Git submodules** to read code from all your repositories at once.

**Best for:** Microservice architectures, shared internal libraries, or projects where code generation requires context from multiple repositories.

See the **[Git Submodules Integration Guide](git_submodules.md)** for configuration instructions.

***

## Understanding Your Environment

The more environment access you give Blitzy, the more it can validate - from basic compilation checks to full end-to-end testing with databases and external APIs.

### Why Environment Configuration Matters

When generating code, Blitzy compiles and tests your codebase in isolated environments before creating pull requests. This catches errors early and ensures code builds successfully.

**1. Source Code Only**

Static analysis of your codebase

**2. + Compiler Access**

Compilation checks and build validation

**3. + Runtime Access**

Internal component testing with mocks/stubs

**4. + Database**

Full database integration testing

**5. + API Schema & 1P/3P API Access**

End-to-end workflows with all external dependencies

### What Blitzy Needs

To enable runtime validation, configure:

> **Build Instructions**
>
> Commands to install dependencies, compile, and run tests

> **Environment Variables**
>
> Required variables and secrets (stored securely)

> **Connected Repositories**
>
> Which codebases Blitzy can access and modify

See the **[Environment Configuration](environment_config.md)** guide for detailed setup instructions and security protocols.

> [!WARNING]
>
> All internal dependencies must be active before running a project. Blitzy builds around the dependencies it finds at generation time - Refine PR cannot add missing ones later.

***

## Next Step

> **[Set Up Your Project](../../platform/project_lifecycle/project_setup.md)**
>
> Ready to go? Set up your first project and start generating code with Blitzy.


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.