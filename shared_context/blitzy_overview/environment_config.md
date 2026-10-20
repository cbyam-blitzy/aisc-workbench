> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Environment Configuration

> Configure build instructions, secrets, and private registries so Blitzy can build and run your application

Environment configuration tells Blitzy how to build and run your application. Provide the same level of detail you would give a new developer on their first day - toolchain versions, dependency installation commands, environment variable definitions, and startup procedures.

> [!NOTE]
>
> **Jump to:** [Target OS](#target-operating-system) • [Setup Instructions](#setup-instructions) • [Example](#example-setup-instructions) • [Variables & Secrets](#variables-%26-secrets) • [Best Practices](#best-practices) • [Getting Started](#getting-started) • [Cloning](#cloning-an-environment) • [Multiple Environments](#multiple-environments) • [Troubleshooting](#troubleshooting)

![Blitzy Environment Access Insights](https://mintcdn.com/blitzy-c2eefe5a/zW1V6gp28Dv1LcG8/images/blitzy-insights-on-access.webp?fit=max\&auto=format\&n=zW1V6gp28Dv1LcG8\&q=85\&s=0f84928b0b9fc4b0f2994d6a1aa99c86)

## Target Operating System

Choose the OS and virtualization type Blitzy uses to build and run your project.

### Operating System

| OS | When to use |
| :- | :- |
| **Linux** | Most web applications, APIs, and backend services. Default for the majority of projects. |
| **Windows** | .NET Framework, Windows-native desktop applications, or projects that depend on Windows-only toolchains. Required for [Computer Use on Windows](/project-lifecycle/code-review#validation-signals) desktop validation. |
| **macOS** | iOS and macOS application builds that require Xcode, Swift toolchains, or Apple-specific signing. |

### Virtualization Type

| Type | When to use |
| :- | :- |
| **Container** | Stateless, parallelizable workloads where speed and resource efficiency matter most. Containers start faster and cost less. Choose this unless your project needs a full OS. |
| **Virtual Machine** | Workloads that require a full operating system - GUI testing, kernel-level access, system services, or tools that do not run in containers. Required for Computer Use validation. |

> [!TIP]
>
> When in doubt, start with **Linux** and **Container**. Most projects run well in this configuration. Switch to a VM or a different OS only when your toolchain requires it.

## Setup Instructions

Your setup instructions should provide a complete, unambiguous path from a fresh environment to a running application. Write them in **natural language**. Blitzy's agents interpret plain-English instructions, not just shell scripts.

### What to Include

> **Required Toolchain & Runtime**
>
> * Runtime and language version (e.g., Node.js 20, Java 21, Python 3.12)
> * Build tools and package managers (e.g., Maven 3.9, npm, Make)
> * Database systems needed for testing (e.g., PostgreSQL 15, MongoDB 7.0)
> * Container runtime if applicable (e.g., Docker Desktop)

> **Authentication & Access**
>
> * Cloud credential setup (service account keys, credential files)
> * Internal package registries or artifact repositories
> * How to authenticate (PAT, service accounts, credential files)
> * Where credential files should be placed (e.g., `~/.m2/settings.xml`, `.npmrc`)
> * **UI login credentials** for applications gated by a login screen (see warning below)

> **Build & Run Commands**
>
> * Exact commands to install dependencies
> * Build commands with any required flags
> * Database migration or initialization steps
> * Commands to start the application
> * How to run tests (if applicable)

> **File-Based Configuration**
>
> * Configuration files required (e.g., `.env.local`, `application.yml`)
> * Where these files must be located
> * Which secrets or variables they reference

> **Environment Variable Special Handling**
>
> * Variables that need aliasing or renaming at runtime
> * Variables that should NOT be set globally (only per-command)
> * Service URL overrides or internal routing rules

## Example Setup Instructions

The example below demonstrates a multi-service project with natural-language setup instructions, the format Blitzy works best with.

```text theme={null}
Acme Platform: Setup Instructions

Requirements: Python 3.11, Node.js 20

--- API Server ---

To install and build:
  make setup
  make install

--- Variable Aliasing ---

These variables have platform-suffixed names that differ from what the code expects:

  API_GATEWAY_URL_PLATFORM  → used internally as API_GATEWAY_URL
  WORKER_URL_PLATFORM       → used internally as WORKER_URL
  VAULT_URL_PLATFORM        → used internally as VAULT_URL

Use the _PLATFORM variants when configuring your environment. Do not create
the short-name versions. The build handles the mapping.

--- Web Client ---

Start the development server:
  npm run dev

--- Docs Site ---

Create a `.env.local` file in the `docs-site/` directory with these values:

  HEADLESS_CMS_ORG_ID=${HEADLESS_CMS_ORG_ID}
  HEADLESS_CMS_API_KEY=${HEADLESS_CMS_API_KEY}
  HEADLESS_CMS_PREVIEW_KEY=${HEADLESS_CMS_PREVIEW_KEY}
  HEADLESS_CMS_WEBHOOK_SECRET=${HEADLESS_CMS_WEBHOOK_SECRET}

--- Testing ---

Where available, run `make test` and confirm all tests pass before
considering setup complete.
```

> [!TIP]
>
> These instructions are written in plain English with clear section headings, not as a shell script. Tell Blitzy's agents *what to do* and *what to watch out for*; they will figure out the right commands.

## Target Operating System

Set the target operating system in **Settings > Environments**. The target OS controls which platform and virtualization mode build your project.

| Target OS | Virtualization |
| :- | :- |
| Linux | Container only |
| Windows | Container or Virtual machine |
| macOS | Virtual machine only |

* **Linux** - Use it for stateless, parallelizable workloads where speed and resource efficiency matter most.
* **Windows** - Offers both Container and Virtual machine. Select Virtual machine when you need full OS control, nested virtualization, or Computer Use for native desktop apps.
* **macOS** - Use it for macOS desktop apps or Xcode-dependent builds. Runs as a virtual machine.

> [!NOTE]
>
> macOS is available by request. Contact your Blitzy administrator to enable it for your workspace.

> [!TIP]
>
> Choose the target OS before writing setup instructions. The toolchain, package manager, and credential paths you document all depend on it.

## Variables & Secrets

### What's the Difference?

* **Variables** - Non-sensitive configuration (e.g., `NODE_ENV=production`, feature flags, public endpoints). Stored as plaintext.
* **Secrets** - Sensitive credentials (e.g., database passwords, API keys, service account keys). Encrypted at rest, masked in all logs, and never sent to AI agents.

### Configuration Examples

| Configuration | Type | Example | Use Case |
| :- | :- | :- | :- |
| `DB_CONNECTION_STRING` | Secret | `postgresql://user:pass@host:5432/db` | Application connects to database |
| `HEADLESS_CMS_API_KEY` | Secret | `sk_abc123...` | Headless CMS access |
| `API_GATEWAY_URL_PLATFORM` | Variable | `https://gateway.internal.example.com` | Internal service routing |
| `NODE_ENV` | Variable | `production`, `development` | Framework behavior |
| `LOG_LEVEL` | Variable | `info`, `debug`, `error` | Logging verbosity |
| `FEATURE_FLAG_XYZ` | Variable | `true`, `false` | Feature toggles |

### How Secrets Work

1. **Canonical Secret Names** - Define secret references (e.g., `${DB_PASSWORD}`) in your setup instructions or configuration files.
2. **Encrypted Storage** - Actual secret values are stored encrypted and only accessible to authorized users.
3. **Masked Logs** - Any secret value that appears in logs is automatically replaced with `***REDACTED***`.
4. **Not Sent to AI** - Secrets are never included in prompts or sent to AI models. The AI only sees the reference names (e.g., `${DB_PASSWORD}`).

## UI Login Credentials for Auth-Gated Applications

> [!WARNING]
>
> **If your application has a login screen, you must provide Blitzy with valid credentials.** Blitzy validates UI by actively testing the running application. Without login credentials, the platform cannot access screens beyond the login page, resulting in UI that may not match your designs.

Include test credentials as **secrets** in your environment configuration. At minimum, provide:

* **Username / email** and **password** for a test account with access to all relevant screens
* **MFA workarounds** if applicable (e.g., a test account with MFA disabled)
* **Role-specific credentials** if different roles have different UI views that need testing

## Best Practices

1. **Be Explicit** - Assume the reader has never seen your codebase. Specify versions, paths, and commands precisely.
2. **Use Natural Language** - Write instructions the way you would explain them to a new teammate. Blitzy interprets plain English, not just shell commands.
3. **Call Out Gotchas** - If a variable must not be exported globally, or a command needs a specific env var set inline, say so explicitly.
4. **Reference Variables and Secrets Correctly** - Use `${VARIABLE_NAME}` syntax for both variables and secrets so Blitzy can substitute values at runtime.
5. **Test Your Instructions** - The best way to validate setup instructions is to follow them yourself on a clean machine or container.
6. **Document Assumptions** - If your build assumes certain tools are installed or services are running, state that clearly.

## Getting Started

**1. Navigate to Settings > Environments**

Open your Blitzy dashboard and go to the Environments section.

**2. Create a New Environment**

Create an environment for your target (Development, Staging, Production).

**3. Add Setup Instructions**

Write natural-language build and run instructions following the patterns above.

**4. Configure Variables & Secrets**

Add non-sensitive variables as plaintext and sensitive credentials as encrypted secrets.

**5. Save and Test**

Save the configuration and click **Test Setup** to validate it. See the [Environment Testing](/project-lifecycle/environment-testing) guide for details on what the test checks and how to interpret the results.

> [!NOTE]
>
> When beginning Blitzy Projects, you will be prompted to attach the appropriate environment(s) during project setup.

> [!TIP]
>
> Environment links use in-app routing - clicking a link to a specific environment navigates directly without opening a new tab. URLs are shareable; copy one from your browser to send a teammate straight to that environment's configuration.

> [!NOTE]
>
> **Windows desktop validation:** If your project uses [Computer Use on Windows](/project-lifecycle/code-review#validation-signals) to visually validate a desktop application, you need a Windows environment with UI login credentials and desktop-specific setup instructions. See [Computer Use on Windows](/project-lifecycle/code-review#validation-signals) for details.

## Cloning an Environment

Clone an environment to create an independent, editable copy without affecting the original. The clone starts as your private environment so you can make changes safely before sharing or attaching it to a project.

**1. Open the environment**

Go to **Settings > Environments** and select the environment you want to duplicate.

**2. Open the actions menu**

Click the **...** menu for the environment to open its actions.

**3. Select Clone environment**

Choose **Clone environment** from the menu.

**4. Name the copy**

The name dialog opens pre-filled with `Clone-<name>`. Adjust the name if needed - it must be unique within your organization.

**5. Confirm**

Confirm to create the copy. Blitzy selects the new environment with its name ready to edit.

> [!NOTE]
>
> Cloning duplicates the source configuration, but the new environment starts independent of the original:
>
> * **Copied** - the setup instructions, target OS, variables, and secrets are duplicated into the new environment
> * **Private** - the clone is owned only by you
> * **Unlinked** - the clone is attached to no projects and shared with no teams

## Multiple Environments

A project can use more than one environment. Each environment is assigned a **position**, where position 1 is the highest priority.

When a build runs, environments are merged using these rules:

| Field | Merge Rule |
| :- | :- |
| `instructions` | Taken from the highest-priority environment with non-empty instructions |
| `target_os` | Taken from position 1 |
| `variables` | First-writer wins: position 1 sets a key, later positions skip it |
| `secrets` | Same first-writer wins rule |
| `files` | Merged by filename; higher-priority environment wins on conflict |

### Recommended Pattern

**Shared Base + Override**

* **Position 2** - A shared "company base" environment with common build instructions, registry URLs, and shared credentials
* **Position 1** - A project-specific "override" environment for anything that differs from the base

This lets you update shared configuration in one place without editing every project.

**Single Environment**

If all configuration is project-specific, a single environment at position 1 is fine. No layering needed.

### Do You Need a New Environment?

| Question | Recommendation |
| :- | :- |
| Does an existing environment match your OS and tech stack? | Reuse it. Attach it to your project. |
| Does your project need project-specific secrets? | Create a thin override at position 1; attach the shared base at position 2 |
| Is the tech stack or OS different from all existing environments? | Create a new environment |
| Does the build require different instructions (different runtime, toolchain, framework)? | Create a new environment |
| Does your project use Computer Use for Windows desktop validation? | Create a Windows environment with desktop setup instructions and [UI login credentials](#ui-login-credentials-for-auth-gated-applications) |

> [!TIP]
>
> Create a new environment only when no existing environment's `instructions` and `target_os` match your project's build requirements.

## Troubleshooting

> **Build fails with 'variable not found'**
>
> **Cause:** Environment not attached to the project, or sync has not completed.
>
> **Fix:** Check **Project Settings** to verify the environment is attached. Wait 60 seconds and retry - the sync may still be in progress.

> **Variables from a lower-priority environment are ignored**
>
> **Cause:** A higher-priority environment already defines the same key (first-writer wins).
>
> **Fix:** Check the variable names across all attached environments. Rename or remove the duplicate in the higher-priority environment.

> **Build uses the wrong OS**
>
> **Cause:** `target_os` is always taken from the position-1 environment.
>
> **Fix:** Move the environment with the correct OS and virtualization mode to position 1.

> **Environment not visible in the project dropdown**
>
> **Cause:** Environments require explicit or team-based sharing.
>
> **Fix:** Ask the environment owner to share it with you or your team via **Settings > Environments**.

## Related Guides

> **[Environment Testing](/project-lifecycle/environment-testing)**
>
> Validate your environment before starting code generation

> **[Teams & Roles](/administration/teams)**
>
> Role-based access control for environments

> **[Project Setup](/project-lifecycle/sharing)**
>
> Connect environments to projects

> **[Computer Use on Windows](/project-lifecycle/code-review#validation-signals)**
>
> Visual validation using Windows desktop interaction


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.