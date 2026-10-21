> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Usage Metering

> Understand how platform usage is tracked and billed across projects, teams, and organizations

Blitzy meters two activities for billing: code generation and codebase onboarding.

> [!NOTE]
>
> **Jump to:** [Metered Activities](#metered-activities) | [Delta Ingestion](#delta-ingestion) | [Aggregation](#usage-aggregation-by-subscription) | [Team Attribution](#team-attribution) | [Quotas](#quotas--overages) | [Summary](#usage-summary)

> [!NOTE]
>
> Usage and quota statistics are visible to **Super Admins** and **Admins** only. See [Teams](teams.md) for role permissions.

## Metered Activities

### Code Generation

The billable event for code generation is **pull request creation**. The moment Blitzy opens a PR, that PR is recorded as usage.

| Metric | Description |
| - | - |
| **Lines Generated** | Total lines of code added, edited, or removed |
| **Files Touched** | Number of files modified during generation |
| **Hours Saved** | Estimated developer time saved |

**Last state wins** - If you refine a PR or fix merge conflicts, the usage record updates to reflect the final line count. You are billed for the last completed state of the PR:

* A 50,000-line PR refined to 25,000 lines is billed at 25,000 lines
* A 50,000-line PR where the refinement is abandoned (never finishes) is billed at 50,000 lines

Failed or incomplete operations where no PR is created are not billed.

### Code Onboarding

Usage is recorded when you successfully onboard an existing codebase:

| Metric | Description |
| - | - |
| **Lines Onboarded** | Total lines of code imported into the system |
| **Files Onboarded** | Number of files processed during onboarding |

**When it counts** - Usage is recorded upon successful onboarding completion and project graph updates.

## Delta Ingestion

Blitzy ingests code as a delta - only the lines that changed since the last ingested commit are counted. Forking a branch, renaming a branch, or creating a new project on a different branch of the same repository does not re-count existing code. Only new or modified lines contribute to your LoC total.

This means two projects on different branches of the same repo share a common baseline. Each project is billed only for what it changes, not for the full codebase.

> [!WARNING]
>
> Rebasing or force-pushing rewrites commit history. The next ingestion may re-count previously ingested lines, temporarily inflating your LoC total.

## Usage Aggregation by Subscription

Usage visibility and aggregation differ by subscription tier:

| Subscription | Project | User | Team | Company |
| - | - | - | - | - |
| **Enterprise** | Yes | Yes | Yes | Yes |
| **Sandbox** | Yes | Yes | No | Yes |

Every subscription records project-level and user-level usage. Enterprise subscriptions also record team-level and company-level usage.

## Team Attribution

### Attribution Requirements

On the subscriptions that keep team-level records - Teams, Enterprise and Sandbox - usage is attributed to teams when both conditions are met:

1. The user is a member of the team
2. The team has access to the project

If either condition is false, usage is tracked only at the project and user levels.

### Multiple Team Membership

When a user belongs to multiple teams with access to the same project:

* Usage is attributed to each qualifying team independently
* Each team's metrics reflect the full usage amount
* This enables accurate tracking for shared project scenarios

**Example:** A developer on both "Frontend Team" and "Platform Team" generates code on a shared project. The usage appears in both teams' metrics.

### Attribution Hierarchy

Usage flows through the following levels:

```
Project → User → Team(s) → Company
```

| Level | What It Tracks |
| - | - |
| **Project** | All activity on a specific project |
| **User** | All activity by a specific user across projects |
| **Team** | All activity by team members on team-accessible projects |
| **Company** | All activity across the entire organization |

### No Team Access Scenarios

| Scenario | Result |
| - | - |
| User has no team membership | Usage tracked at project and user level only |
| User's teams lack project access | Usage tracked at project and user level only |
| Organization-metered subscription with no qualifying team | Company-level tracking uses user's company |

## Quotas & Overages

### Subscription Quotas

Each subscription includes quotas for:

* **Lines Generated** - Maximum code generation capacity
* **Lines Onboarded** - Maximum codebase size for onboarding

The two are independent: the generation quota governs code generation, the onboarding quota governs ingestion. Remaining allowance is the quota less the usage already recorded against the subscription, and a queued run's estimated lines are held against the generation allowance until that run finishes, whether it succeeds or fails.

### Overage Handling

Usage is always recorded. What differs by subscription is what happens once an allowance is spent:

| Subscription | Generation allowance spent | Onboarding allowance spent |
| - | - | - |
| **Enterprise** | Generation continues; the excess is recorded as an overage for billing | Further ingestion is refused |
| **Sandbox** | Further code generation is refused - the allowance is a cap, not a billable overage | Further ingestion is refused |

When recorded usage passes a quota, an overage record is created - or the open one increased - categorized by type (generation vs. onboarding) and tracked with payment status. An overage record suspends nothing on its own: the refusals above are checks made on the next request, and work already in flight is unaffected.

If a subscription has no recorded quota, requests are refused - a missing quota is not an unlimited one.

> [!NOTE]
>
> Ingestion is refused once the **Lines Onboarded** allowance is used up. The onboarding allowance is a hard limit, not a billable overage.

### Credits & Refunds

Credits and refunds apply to your usage totals immediately, not at end-of-month.

## Excluded Activities

The following activities are not metered:

* Failed or incomplete operations
* File mapping and analysis
* Internal processing steps

Only completed code generation and onboarding operations count toward quotas.

## Usage Summary

| Activity | Metered? | Quota Applies? |
| - | - | - |
| Completed code generation | Yes | Yes |
| Completed code onboarding | Yes | Yes |
| Failed operations | No | No |
| File analysis | No | No |

## Related Guides

> **[Teams & Roles](teams.md)**
>
> Team membership and access control

> **[Project Sharing](../project_lifecycle/project_setup.md)**
>
> Project access and team collaboration


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.