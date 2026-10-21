> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Locked Projects

> Make a project read-only for Members while Admins keep full access

Lock a project to make it read-only for Members while Admins continue working as normal. For projects Blitzy publishes as read-only examples for every role, see [Demo Projects](demo_projects.md).

> [!NOTE]
>
> **Jump to:** [Permissions](#permissions-and-roles) | [How Locking Works](#how-locking-works) | [Lock and Unlock](#locking-and-unlocking-a-project) | [Indicators](#lock-indicators-and-badges) | [Role Behavior](#what-admins-and-members-can-do) | [Common Questions](#common-questions)

## Permissions and Roles

Only Admins lock and unlock projects. Admin covers both the **Admin** and **Super Admin** roles described in [Teams](teams.md).

* **Super Admin** - Locks and unlocks projects across the organization
* **Admin** - Locks and unlocks any project they are authorized to manage, including their own personal projects
* **Member** - Views a locked project and keeps their normal access to the unlocked projects they are already permitted to use

Any Admin can unlock a project, regardless of which Admin originally locked it. Blitzy records no owner for a lock, so no single Admin becomes a bottleneck and no handover is required before a project can be reopened.

A lock applies to one project. It changes no team roles, no project membership, no sharing settings, and no access to any other project. Manage roles and project sharing in [Teams](teams.md).

> [!NOTE]
>
> Locking and unlocking are available on the Teams and Enterprise plans.

## How Locking Works

A lock makes a project read-only for Members and leaves it fully writable for Admins. It sits outside the workflow, so lock any project at any step and in any status.

* **Workflow unchanged** - Locking never changes the current step and never advances or rewinds progress
* **Content unchanged** - Locking never edits prompts, specifications, attachments, or generated output
* **Running work unchanged** - Any operation already in progress continues normally after the project is locked
* **Reversible at any time** - Unlocking restores Member access immediately

Members watching a generation that was already running when the lock landed keep seeing its progress and results update live through to completion.

Locking asks for confirmation. Unlocking does not: it applies the moment an Admin selects it. Blitzy confirms both actions with a success message, headed **Project locked** or **Project unlocked**.

The locked state is reported beside the existing workflow status, never in place of it. A locked project keeps displaying its workflow status exactly as an unlocked project does.

## Locking and Unlocking a Project

Lock and unlock from either surface: the project card on the Projects page, or the project header inside the project. Both surfaces open the same menu with the same rows.

The menu offers these rows, in this order:

* **Rename project** - Always offered to an Admin
* **Lock project / Unlock project** - A single row that swaps both its label and its icon to match the current state
* **Archive project** - Offered under the same conditions as on an unlocked project, so a project that is currently generating does not offer it

Locking adds no row and reorders nothing. The middle row replaces its own previous label rather than appearing alongside it, and the menu's other rows appear exactly as they do on an unlocked project.

### Lock a Project

The **Lock project?** dialog opens first and states: Members will still be able to view this project, but they won’t be able to edit, generate, download, rename, archive, or make any other changes until an admin unlocks it. It offers exactly two buttons, **Cancel** and **Lock project**.

**From the Projects page**

**1. Open the actions menu**

Hover the project card, then click the **...** menu for the project to open its actions.

**2. Select Lock project**

Choose **Lock project** from the menu.

**3. Confirm the lock**

Choose **Lock project** in the dialog to apply the lock. Choose **Cancel** to leave the project completely unchanged.

The card shows its lock indicator and a **Project locked** message confirms the change.

**From inside the project**

**1. Open the actions menu**

Click the **...** menu in the project header to open its actions.

**2. Select Lock project**

Choose **Lock project** from the menu.

**3. Confirm the lock**

Choose **Lock project** in the dialog to apply the lock. Choose **Cancel** to leave the project completely unchanged.

The header shows the locked badge and a **Project locked** message confirms the change. The current workflow step does not change and no navigation occurs.

### Unlock a Project

Unlocking applies immediately, with no confirmation dialog.

**From the Projects page**

**1. Open the actions menu**

Hover the locked project card, then click the **...** menu for the project to open its actions.

**2. Select Unlock project**

Choose **Unlock project** from the menu.

The lock indicator clears and a **Project unlocked** message confirms the change.

**From inside the project**

**1. Open the actions menu**

Click the **...** menu in the project header to open its actions.

**2. Select Unlock project**

Choose **Unlock project** from the menu.

The locked badge clears and a **Project unlocked** message confirms the change. The current workflow step does not change.

## Lock Indicators and Badges

Blitzy reports a lock in two places, and both use the same wording so they can never disagree.

* **Project card** - Every locked project card carries a lock indicator. Hover it to read the current state
* **Project header** - Inside the project, a locked badge sits beside the workflow status

The wording depends on who is reading it:

* **Admin view** - The indicator and the badge read **Locked for members**
* **Member view** - The indicator and the badge read **Locked by admin**

Both report state only. Neither one triggers an action, and neither one removes or replaces the workflow status.

## What Admins and Members Can Do

**Admin**

An Admin keeps unchanged, full access to a locked project. Nothing is dimmed, disabled, or hidden.

* **Editing** - Edit and save prompts, context, and settings exactly as on an unlocked project
* **Generation** - Start, repeat, and advance work with no restriction
* **Downloads** - Download every available artifact
* **Project management** - Rename, archive, and share the project as usual
* **Actions menu** - The **...** menu stays available and offers **Unlock project** in place of **Lock project**

**Member**

A Member keeps full read access to a locked project and cannot change anything in it.

* **Navigation** - Move through every available workflow step
* **Existing content** - Review current values, previously added attachments, and generated results
* **Live progress** - Watch an operation that is already running update through to completion
* **Modifying actions** - Actions that edit, save, start, repeat, advance, download, merge, or refine are not shown
* **Actions menu** - The **...** menu is not shown at all
* **Pinning** - Pin and unpin the project, because pinning is personal and changes nothing about the project
* **Links** - Repository links, pull request links, external resources, and informational links such as **Prompt Guide** stay active

Generated artifacts stay readable for a Member with their presentation unchanged: the [technical specification](../project_lifecycle/technical_specification.md), the [Agent action plan](../project_lifecycle/agent_action_plan.md), the [Project Guide](../project_lifecycle/project_guide.md), and the [generated code](../project_lifecycle/code_review.md) all render exactly as they do on an unlocked project.

Form fields behave differently from top-level actions. Inputs, selectors, and editors stay visible and switch to their existing read-only state instead of disappearing, so a Member can still read every configured value.

> [!NOTE]
>
> Locking keeps all setup controls in place. [Demo Projects](demo_projects.md) remove them entirely.

## Common Questions

> **Can a different Admin unlock a project I locked?**
>
> Yes. Any Admin can unlock a project, regardless of which Admin originally locked it. Blitzy stores no owner for a lock, so every Admin sees the same **Unlock project** row.

> **Why does a Member see no actions menu on a locked project?**
>
> Every row in that menu modifies the project, so Blitzy removes the menu rather than presenting rows a Member cannot use. Pinning stays available from the project card, since pinning is a personal action that leaves the project untouched.

> **Can a Demo Project be locked or unlocked?**
>
> No. A Demo Project is already read-only for every role, so lock and unlock do not apply to it. See [Demo Projects](demo_projects.md) for how those projects behave.

## Related Guides

> **[Demo Projects](demo_projects.md)**
>
> Read-only example projects Blitzy provides to every role

> **[Teams](teams.md)**
>
> Roles and permissions that decide who can lock a project

> **[Workspace](../intro/workspace.md)**
>
> The projects grid and project page where locking applies

> **[Glossary](../intro/glossary.md)**
>
> Definitions of locking and other platform terms


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.