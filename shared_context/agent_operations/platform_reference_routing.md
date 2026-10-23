# Platform reference routing

Last updated: 2026-10-23. Refresh when platform references or qualifications change.

All paths in the table are relative to `shared_context/` in the working checkout.


Use platform guidance for capabilities and workflows, and account evidence for
needs, commitments, approvals, and measured results. Read only task-relevant
references; start with the introduction when explaining Blitzy and the glossary
when terminology needs clarification.

| Task or question | Read under `shared_context/` |
| --- | --- |
| Workflow, artifact purpose and terminology | `platform/intro/introduction.md`; `platform/intro/glossary.md` |
| First-use walkthrough and sprint/development workflow guidance | `platform/intro/quickstart.md`; `platform/intro/building_with_blitzy.md` |
| Project navigation, codebase exploration and branch-scoped specifications | `platform/intro/workspace.md`; `platform/intro/knowledge_base.md` |
| Vulnerability findings, reachability and remediation-project workflow | `platform/intro/proactive_insights.md` |
| Provisioning, branch isolation, integrations and project sharing | `platform/project_lifecycle/project_setup.md` |
| Repository preparation, submodules and pinned commits | `build_preparation/setup/preparing_your_codebase.md`; `build_preparation/setup/git_submodules.md` |
| Toolchains, target OS, build/test setup, dependencies and secrets references | `build_preparation/setup/environment_config.md` |
| Test Setup execution, results and retesting | `build_preparation/setup/environment_testing.md` |
| Source Q&A, Build prompt drafting and advisory scoring | `platform/project_lifecycle/chat_with_code.md` |
| Ingestion context, exclusions, formats and branch/spec inheritance | `build_preparation/ingestion_prompts.md` |
| Build prompt submission, iteration and attachment formats | `build_preparation/generation_prompts.md` |
| Figma input preparation and design-output issues | `build_preparation/figma/design_with_figma.md`; `build_preparation/figma/avoiding_common_issues.md` |
| Current-state understanding and specification review | `platform/project_lifecycle/technical_specification.md` |
| AAP completeness, rules, refinement and inline edits | `platform/project_lifecycle/agent_action_plan.md` |
| Generation progress and completion | `platform/project_lifecycle/code.md` |
| Delivered scope, validation and remaining-work evidence | `platform/project_lifecycle/project_guide.md` |
| PR Review navigation, review modes, merge/refine/close options | `platform/project_lifecycle/pr_review.md` |
| Intent, dynamic validation and code-level review practices | `platform/project_lifecycle/code_review.md` |
| Teams, roles, project sharing and enforcement | `platform/admin/teams.md` |
| Domain verification, SSO, SCIM and IdP-managed access | `platform/admin/sso.md`; `platform/admin/teams.md` |
| Metered activities, attribution, quotas and overages | `platform/admin/usage_metering.md` |
| Demo discovery and universally read-only behavior | `platform/admin/demo_projects.md` |
| Project locking, role-dependent restrictions and running work | `platform/admin/locked_projects.md`; `platform/admin/teams.md` |

## Applying platform guidance

Preserve each guide's qualifications and distinguish documentation from evidence
that a particular project is configured, validated, or accepted.

- Cite material sourced claims in the final appendix required by the readability
  directives. Templates and platform examples do not prove project coverage,
  test success, acceleration, or acceptance. Surface conflicts with account
  agreements or other references.
- Distinguish automatic ingestion/specification, AAP, and Project Guide
  generation from human readouts, review, approval, and acceptance.
- Use operational guides for practical platform questions. They are not default
  required reading for POV maps or evaluation memos; consult them when an
  operational dependency affects readiness, responsibilities, or milestones.
- Preserve role, subscription-tier, project-type, and IdP-management-mode
  qualifications. Explain sharing/ownership and access effects; documentation
  does not authorize administrative actions. Demos are read-only for everyone;
  ordinary project restrictions depend on roles and project state.
- For setup recommendations, identify required repositories/submodules, the
  authorized integration owner, a stable branch, and the intended audience.
  Guidance does not authorize provisioning, access changes, source transfer,
  or sharing. Do not push to a branch during generation.
- Preserve Chat with Code's beta, access, and workflow-step limits. At the AAP
  step it answers source questions, not plan-review or plan-edit requests.
  Build Prompt Strength is advisory, not approval or an acceptance gate.
  Flag availability conflicts rather than promising support.
- Select task-matching prompt/rule templates only when relevant. Use a prompt
  page's **Prompt template** section or a rule page's **Rule Definition**;
  do not copy an entire guide or impose the whole library. Apply only selected
  or agreed rules; template defaults are not customer requirements.
- Metered hours-saved estimates do not establish delivery acceleration or
  acceptance. Use account subscription evidence for actual quotas and terms.
  The usage-metering guide conflicts on Sandbox team attribution; flag that
  uncertainty rather than promising team-level reporting for that tier.
