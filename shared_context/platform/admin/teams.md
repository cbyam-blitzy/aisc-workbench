> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Teams

> Manage teams, roles, and member access permissions in Blitzy

Blitzy uses role-based access control to manage team collaboration, permissions, and project sharing. The system includes four roles - Super Admin, Admin, Member, and Viewer - each with distinct capabilities designed for enterprise environments.

> [!NOTE]
>
> **Jump to:** [Roles](#roles) | [Permissions](#permissions) | [Project Sharing](#project-sharing) | [Require Project Sharing](#require-project-sharing)

## Roles

**Super Admin**

The highest level of administrative access within the organization.

* **Full team visibility** - See and manage all teams across the enterprise
* **Team lifecycle** - Create, modify, and delete teams
* **Member management** - Add or remove members from any team
* **Connection overrides** - Override individual user connections and settings
* **Integration sharing** - Share integrations organization-wide, including GitHub, Azure DevOps, Azure DevOps Server, and GitLab

> [!WARNING]
>
> At least one Super Admin must exist at all times. The first user added to an enterprise account automatically becomes the Super Admin — transfer the role before leaving the organization.

**Admin**

Team-level administrative access within assigned teams.

* **Member management** - Add or remove members within assigned teams
* **Team settings** - Manage team-specific settings and configurations
* **Integration sharing** - Share integrations with team members
* **Project access** - Full project access within their team's scope

**Member**

Standard user role with project collaboration capabilities.

* **Project participation** - Full access to team project features
* **Project sharing** - Share projects with their teams
* **Code generation** - Trigger code generation and other project actions
* **Team settings** - Read-only view

**Viewer**

Read-only access for stakeholders, auditors, or observers who need visibility without the ability to modify resources.

* **Read-only access** - View projects, environments, rules, knowledge base, CVE findings, and integrations
* **Personal view state** - Pin knowledge base branches and select CVE branches for personal filtering
* **No writes** - Cannot create, edit, delete, or share any resource
* **No profile editing** - Cannot modify their own user profile

> [!NOTE]
>
> Viewer is available on Teams and Enterprise tiers. Personal actions like pinning use a read grant, so Viewers can personalize their view without modifying shared data.

> [!TIP]
>
> Maintain at least two Super Admins for redundancy. Assign Admin roles to department leads so they can manage their own teams.

## Permissions

| Operation | Super Admin | Admin | Member | Viewer |
| - | - | - | - | - |
| **Create** team | Yes | No | No | No |
| **View** teams | All teams | Assigned teams only | Member teams only | Member teams only |
| **Manage** members | All teams | Assigned teams only | No | No |
| **Delete** team | Yes | No | No | No |
| **Share** projects | Yes | Yes | Yes | No |
| **Share** integrations | Organization-wide | Team-level only | No | No |
| **Share** rules | No | Yes | Yes | No |
| **Team settings** | Full control | Full control | Read-only | Read-only |
| **Lock** or unlock [projects](locked_projects.md) | Yes | Yes | No | No |
| **View** [usage statistics](usage_metering.md) | Yes | Yes | No | No |
| **Edit** own profile | Yes | Yes | Yes | No |

## Project Sharing

Super Admins, Admins, and Members can share projects with teams. When a project is shared, all team members gain access. Viewers have read-only access to shared projects but cannot share them. Manage project sharing through **Project Settings**.

| Share type | Reversible | Ownership | When it applies |
| - | - | - | - |
| **Team share** | Yes - remove the team to revoke | Unchanged | Any time |
| **Organization-wide share** | Yes - turn off to revoke | Unchanged | Any time |
| **Forced team share** | No | Transfers permanently to the team | Only while Require project sharing is active, and only for still-private projects |

> [!WARNING]
>
> A forced team share transfers ownership permanently. You keep full access as a member, but the project cannot revert to private while enforcement is active.

## Require Project Sharing

Require project sharing is an organization-level control that mandates every newly created project be shared, either organization-wide or with at least one team. While active, it prevents members from creating or keeping new private (owner-only) projects, and it requires members to share an existing private project the next time they open it. Existing private projects are not shared in bulk: a dormant private project stays private until someone opens it. Toggle it on the Settings > Team surface.

* **Who can toggle** - Administrators only (Super Admin and Admin). Members and Viewers cannot change this setting.
* **Card title** - "Require project sharing"
* **Card description** - "When enabled, all members must share every project they create"

**Enable enforcement**

Turning enforcement on opens an acknowledgment confirmation modal that you must acknowledge before it takes effect.

**1. Open the toggle**

Go to Settings > Team and switch "Require project sharing" on.

**2. Review the confirmation modal**

The modal explains the impact:

* "Enabling this will require all members to share every project they create."
* "Existing private projects will prompt members to share them the next time they are opened."

**3. Acknowledge and enable**

Select the acknowledgment checkbox labelled "I understand this affects all members and cannot be undone for projects already shared", then choose "Enable". The "Enable" button stays disabled until the checkbox is selected. Choose "Cancel" to dismiss without enabling.

**Disable enforcement**

Turning enforcement off takes effect immediately. There is no confirmation modal, and a lightweight toast confirms the change.

> [!NOTE]
>
> Already-shared projects stay shared. Disabling enforcement does not revert or unshare any project.

While enforcement is active, members see two changes:

* **New projects** - Members must choose a share target (organization-wide or at least one team) before they can create a project. See [Project Sharing](../project_lifecycle/project_setup.md) for the create flow.
* **Existing private projects** - Opening a still-private project prompts a forced share before the project can be opened.

> [!NOTE]
>
> Forced sharing transfers ownership as described in [Project Sharing](#project-sharing) above. Organization-wide and already-shared projects do not transfer ownership.

## Related Guides

> **[SSO Configuration](sso.md)**
>
> Enterprise Single Sign-On setup

> **[Environments](../../build_preparation/setup/environment_config.md)**
>
> Role-based access to environment configuration

> **[Managing Integrations](https://docs.blitzy.com/integrations/managing)**
>
> Team-level integration configuration

> **[Project Sharing](../project_lifecycle/project_setup.md)**
>
> Project sharing and visibility

> **[Workspace](../intro/workspace.md)**
>
> Filter projects by visibility and read sharing badges


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.