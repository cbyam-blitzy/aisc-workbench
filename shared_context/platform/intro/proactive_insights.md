> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Proactive Insights

> Find vulnerabilities, assess reachability, and create remediation projects across your connected repositories

Proactive Insights shows you every vulnerability in your codebase, tells you which ones an attacker can actually reach, and lets you fix them without leaving the platform. Select a branch to see findings. Select findings to create remediation projects. Toggle to [Knowledge Base](knowledge_base.md) to review specifications or [Workspace](workspace.md) to write generation prompts.

**Testing** and **Documentation** insight tabs are coming soon.

## Selecting a Branch

Pick any `{repo_name}/{branch_name}` from your connected repositories using the branch selector. Once selected, you see the latest commit hash and when the branch was last scanned. Blitzy re-evaluates findings whenever the underlying code context changes: after a merge, newly onboarded code, or a regenerated spec. You never look at stale results.

## Two Kinds of Findings

The findings table is split into two sections.

**Discovered by Blitzy**

Blitzy analyzes your entire codebase to find vulnerabilities that are not in any public CVE database or scanner signature. These use `BLITZY-` prefixed identifiers. No other tool in your stack finds these.

**Publicly Known**

Blitzy reconciles what your existing scanners already flag (Snyk, Mend, Sonatype, GitHub Advanced Security) and adds the one thing they cannot: whether your architecture actually exposes each finding. A CVE that is not reachable is noise.

## What Each Column Tells You

Every row is a single vulnerability.

| Column | What it tells you |
| :- | :- |
| **Severity** | Critical, High, Medium, or Low |
| **CVE** | Identifier and short description. Blitzy-discovered findings use `BLITZY-` prefixed IDs. |
| **Package** | The affected dependency, if any. No package means the vulnerability is in your code. |
| **Confirmed by** | Which external scanners also flagged this finding |
| **Status** | Open or the current remediation state |
| **Reachability** | **Internet** (reachable from an external path) or **Internal** (reachable only within your network) |

Use the search bar to find specific CVEs or descriptions. Use the filter icon to narrow by severity, reachability, or status.

## Remediating Findings

**1. Select findings**

Click **Select recommended** and Blitzy picks the highest-impact findings to fix first, ranked by severity and reachability. Or check individual rows to build your own set.

**2. Create projects**

Blitzy validates each fix is achievable without introducing new vulnerabilities, then plans the implementation. If a fix would cause a new problem, Blitzy tells you before anyone starts work.

**3. Review and merge**

Blitzy generates pre-tested code and opens a pull request. Security review runs against every artifact before the PR is created. Review and merge on your terms.

Findings re-evaluate on every codebase sync, so the table stays current as your team merges.

**Need help?** Contact support at [support@blitzy.com](mailto:support@blitzy.com) or consult your Blitzy AI Solutions Consultant for Proactive Insights assistance.


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.