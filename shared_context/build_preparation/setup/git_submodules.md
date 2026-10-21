> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Git Submodules

> Configure Git submodules for multi-repository projects in Blitzy

Git submodules embed one repository inside another while keeping separate version histories, giving Blitzy unified access to your full multi-repo architecture.

> [!NOTE]
>
> **Jump to:** [Why Submodules](#why-use-submodules) | [Setup](#setup) | [Updating](#keeping-submodules-updated) | [Read-Only Submodules](#read-only-submodules) | [Troubleshooting](#troubleshooting)

## Why Use Submodules

* **Unified context** - Blitzy sees all your repositories as one codebase
* **Modular architecture** - Keep separate repos while enabling coordinated changes
* **Cross-repo awareness** - Blitzy understands dependencies and relationships across your system

## Setup

**1. Grant Blitzy access**

Grant Blitzy access to the parent repository **and** every repository in your `.gitmodules` file through your source control integration settings.

**2. Add submodules**

```bash theme={null}
git submodule add <repo-url> <path>
```

Use absolute HTTPS URLs, not SSH. Skip this step if submodules are already configured.

**3. Verify .gitmodules**

Confirm entries use absolute HTTPS URLs with branch tracking:

```
[submodule "shared-lib"]
  path = shared-lib
  url = https://your-host.com/your-org/shared-lib.git
  branch = main
```

> [!NOTE]
>
> Azure DevOps uses `https://dev.azure.com/your-org/your-project/_git/shared-lib`

**4. Initialize, commit, and push**

Populate submodule directories and commit to the parent:

```bash theme={null}
git submodule update --init --recursive
git add .gitmodules <submodule-path>
git commit -m "chore: add <submodule-name> submodule"
git push
```

> [!WARNING]
>
> Without the init command, submodule directories stay empty and Blitzy has no code to ingest.

**5. Re-sync in Blitzy**

Re-sync your project and verify submodule files appear in your Technical Specification.

## Keeping Submodules Updated

The parent repo does not automatically track new submodule commits. To pick up upstream changes:

```bash theme={null}
git submodule sync --recursive
git submodule update --init --recursive
git add <submodule-path>
git commit -m "chore: update <submodule-name> to latest"
git push
```

Then re-sync in Blitzy.

> [!WARNING]
>
> Run `git submodule sync` before `git submodule update`. Skipping it causes fetches from stale URLs if a remote was renamed or moved.

## Read-Only Submodules

Some submodules point to repos the user can read but not write to - shared libraries, vendor SDKs, archived repos. Blitzy ingests and indexes these for context but **cannot push code changes to them**.

* **Ingestion** - read-only submodules are indexed like any other, giving agents full cross-repo context
* **Setup** - same `git submodule add` flow; your integration needs at least **read** access to the submodule repo
* **Writable submodules** - when Blitzy has write access, it pushes branches and opens PRs against the submodule directly

> [!WARNING]
>
> Do not request code changes to a read-only submodule. Blitzy agents will attempt to push and throw an error when rejected. Modify the upstream repo separately.

* **Pinned commits** - the parent pins each submodule to a specific commit. Pull latest and commit the updated pointer (see [Keeping Submodules Updated](#keeping-submodules-updated))

## Troubleshooting

> **Submodule folders appear empty / Blitzy cannot diff**
>
> Check initialization status locally:
>
> ```bash theme={null}
> git submodule status
> ```
>
> A `-` prefix (e.g., `-abc1234 shared-lib`) means the submodule is uninitialized. Run the [init, commit, and push](#setup) sequence from Setup step 4.
>
> If submodules are initialized locally but Blitzy can't see them, verify Blitzy has access to every repo in `.gitmodules` - not just the parent.

> **Blitzy can't access or modify a read-only submodule**
>
> **Access issues:** Verify your integration grants Blitzy **read** access to the submodule repo - not just the parent. Confirm the `.gitmodules` URL uses HTTPS, not SSH:
>
> ```
> [submodule "vendor-sdk"]
>   path = vendor-sdk
>   url = https://github.com/third-party/vendor-sdk.git
> ```
>
> If the submodule is in a different organization, fork it into your org and point the URL at the fork.
>
> **Push errors:** Blitzy agents cannot push to repos without write access. Do not request code changes to read-only or archived submodules. Modify the upstream repo separately, then update the pointer in the parent (see [Keeping Submodules Updated](#keeping-submodules-updated)).

> **Is submodule setup complex?**
>
> Add the submodule, init, commit, push, and re-sync. No special configuration needed beyond repo access.

## Related Guides

> **[Managing Integrations](https://docs.blitzy.com/integrations/managing)**
>
> View, share, and troubleshoot integrations

> **[Project Setup](../../platform/project_lifecycle/project_setup.md)**
>
> Set up projects with multi-repository architectures


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.