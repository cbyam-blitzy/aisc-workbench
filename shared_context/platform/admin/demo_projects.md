> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Demo Projects

> Explore curated read-only example projects that Blitzy provides to every role

Demo Projects are curated example projects that Blitzy provides so you can explore how real work is put together. They appear in your Projects grid alongside your own work, open like any other project, and stay read-only for everyone. To make one of your own projects read-only for Members while Admins keep working, see [Locked Projects](locked_projects.md).

> [!NOTE]
>
> **Jump to:** [Access Model](#the-access-model) | [Organization Scope](#organization-and-team-scope) | [Showing Demo Projects](#showing-demo-projects) | [Presentation](#how-a-demo-project-appears) | [Read-Only Behavior](#read-only-behavior) | [Common Questions](#common-questions)

## The Access Model

A Demo Project is read-only for every user, whatever their role. **Super Admin**, **Admin**, and **Member** all see the same read-only project: administrative permissions grant no editing and no project management on a Demo Project. Review how those roles work elsewhere on the platform in [Teams](teams.md).

Every role keeps full access to read a Demo Project:

* **Navigation** - Move through every available workflow step and read its content
* **Existing content** - Review configured values, generated results, and previously added attachments
* **Form fields** - Inputs, selectors, and editors stay visible in the platform's existing read-only state instead of disappearing
* **Links** - Repository links, pull request links, and informational links such as **Prompt Guide** stay active
* **Pinning** - Pin and unpin a Demo Project, because pinning is personal and changes nothing about the project

> [!NOTE]
>
> A [Locked Project](locked_projects.md) is read-only for Members only. A Demo Project is read-only for everyone, including Admins.

## Organization and Team Scope

Demo Projects sit outside the organization and team structure you can see. Blitzy curates them centrally and shares them with every account, so a Demo Project is never associated with one of your teams and its curating details are not shown to you.

* **Teams** - A Demo Project belongs to no team, so [team settings](teams.md) do not govern it
* **Project sharing** - A Demo Project offers no [project sharing](../project_lifecycle/project_setup.md) settings
* **Permission management** - A Demo Project offers no permission management, and no role grants editing on one

No team membership, sharing, or role-management control applies to a Demo Project on your side.

## Showing Demo Projects

The **Blitzy Demo Projects** option joins the existing filter row on the Projects page as the last filter, and it behaves exactly like every other filter there.

**1. Open the Projects page**

Go to [Workspace](../intro/workspace.md) and review the filter row above your projects.

**2. Select Blitzy Demo Projects**

Choose **Blitzy Demo Projects** to show Demo Projects in the grid.

**3. Deselect to hide them**

Choose **Blitzy Demo Projects** again to hide them from the grid.

* **Availability** - The filter appears only when at least one Demo Project is available
* **Default state** - **Blitzy Demo Projects** is active until you change your filter selection, so Demo Projects are visible on your first visit
* **Persistence** - Once you change the selection, it persists like every other filter, so your choice survives a page reload

Demo Projects merge into the same grid as your own projects, with no separate section and no heading. Pin one and it joins your pinned projects like any other pinned project.

> [!TIP]
>
> Open a Demo Project beside the [Golden Rules](../../build_preparation/prompt_golden_rules.md) to compare a well-scoped prompt against the work it produced.

## How a Demo Project Appears

**On the Projects page**

A Demo Project uses the same card as every other project. The workflow status badge, the project name, and the card layout are unchanged, and three details differ:

* **Provided by Blitzy** - Replaces the project's modified date
* **Demo Project** - Appears in the card footer in place of a team name
* **Generation counters** - Not shown

The **...** menu is not shown for any role, because every row in it manages the project. The card carries no lock indicator either. Pinning stays available, and the card opens normally.

**Inside the project**

A **Demo Project** badge sits next to the existing workflow status. The badge is added beside the status and never removes or replaces it, so a Demo Project reports its workflow step exactly as any other project does. A Demo Project shows that badge alone: it never shows a lock badge, whatever your role. No project-level actions are shown.

Header metadata is reduced to these two items, each shown only when the Demo Project has that data:

* **Source + Destination** - Shown when repository data exists, as an active link to that repository
* **Blitzy AI PR** - Shown when pull request data exists

The two items are independent, so a Demo Project shows either one, both, or neither. When a Demo Project has neither, the project-header metadata section is not shown at all.

Those two items are the whole of it. Every other metadata row is absent from a Demo Project, including **Teams shared with**, **Environment**, **Code generation rules**, **View breakdown**, and **Blitzy AI-built**.

> [!NOTE]
>
> Reduced metadata is simply absent. Blitzy leaves no placeholder value, no disabled link, and no empty row in its place.

## Read-Only Behavior

A Demo Project can sit at any workflow step and carry any workflow status. What you see is exactly what Blitzy produced for the step that project has reached - steps beyond it are unavailable. Check the workflow status beside the **Demo Project** badge to see where that is.

Whichever generated artifacts that step has produced render with their presentation unchanged: the [technical specification](../project_lifecycle/technical_specification.md), the [Agent action plan](../project_lifecycle/agent_action_plan.md), the [Project Guide](../project_lifecycle/project_guide.md), and the [generated code](../project_lifecycle/code_review.md) all read exactly as they do on your own projects. A step the project has not reached stays unavailable, exactly as it would on your own project.

Actions that edit, save, start, repeat, advance, or download are not shown, and a Demo Project cannot be renamed, archived, locked, unlocked, or otherwise managed.

> [!NOTE]
>
> Setup controls (**Test setup**, **Manage saved environments in Settings**, **Manage saved rules in Settings**) are removed entirely from Demo Projects. [Locked Projects](locked_projects.md) keep them.

Blitzy sets no limit on the number of Demo Projects available to you.

## Common Questions

> **Can an Admin or Super Admin edit a Demo Project?**
>
> No. A Demo Project is read-only for every role, and administrative permissions grant no editing and no project management on one. This is the difference from a locked project, where an Admin keeps full access. See [Locked Projects](locked_projects.md) for that behavior.

> **Why is there no actions menu on a Demo Project card?**
>
> Every row in that menu manages the project, so Blitzy removes the menu rather than presenting rows no role can use. Pinning stays available from the card, since pinning is personal and leaves the project untouched.

> **Can I rename, archive, lock, or unlock a Demo Project?**
>
> No. A Demo Project is already read-only for every role, so project management actions do not apply to it.

> **Why is the Blitzy Demo Projects filter missing?**
>
> The filter appears only when at least one Demo Project is available. When none is available, Blitzy omits the filter instead of showing an option that would return nothing.

> **Do Demo Projects appear in Teams or in project sharing settings?**
>
> No. Demo Projects sit outside the organization and team structure you can see, so they appear in neither [Teams](teams.md) nor [project sharing](../project_lifecycle/project_setup.md) settings, and none of your teams is associated with them.

> **Why does a Demo Project never show a lock badge?**
>
> A Demo Project is already read-only for every role, so a lock adds nothing to it. Blitzy reports the state once, with the **Demo Project** badge, rather than reporting it twice. See [Locked Projects](locked_projects.md) for the badge that a locked project of your own shows instead.

> **Why does a Demo Project show fewer metadata items than my own projects?**
>
> A Demo Project reports the repository link and the pull request link, each only when that data exists. The rest is omitted rather than replaced, so no placeholder value and no disabled link appears in the header.

## Related Guides

> **[Locked Projects](locked_projects.md)**
>
> Make one of your own projects read-only for Members

> **[Workspace](../intro/workspace.md)**
>
> The projects grid and project page where Demo Projects appear

> **[Teams](teams.md)**
>
> Roles and permissions that apply to your own projects

> **[Glossary](../intro/glossary.md)**
>
> Definitions of Demo Projects and other platform terms


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.