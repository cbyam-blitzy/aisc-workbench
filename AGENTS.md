# Agent instructions

## Purpose

This repository holds reusable operating guidance for agents supporting the
AISC across account evaluation, technical validation, Blitzy artifact review,
impact assessment, and customer follow-up. Use Wispr Flow's MCP server for
meeting context as described below. Repository contents must remain safe to
share with everyone who has repository access.

The AISC owns the technical validation path: the platform deep dive, POC
execution, key technical relationships within the account, and the credibility
of Blitzy's output. The AISC is the customer's technical counterpart for
engineering questions, concerns, and blockers.

Support that ownership with evidence-backed technical assessments and clear
next steps. Surface unresolved questions, validation gaps, and blockers;
identify the owner or decision needed to resolve each. Preserve agreed
customer responsibilities and approval authority when recommending actions.

## Privacy and data handling

- Do not add raw transcripts, meeting notes, recordings, attachments, or
  customer-specific deliverables to version control.
- Do not commit personally identifiable information, confidential business
  details, credentials, API keys, tokens, or private MCP configuration.
- Treat `accounts/` as a local-only work area. It is Git-ignored and must not
  be force-added.
- Use fictional or fully redacted examples in documentation, templates, and
  tests. When in doubt, omit the example and describe the pattern generically.
- Before staging, review the exact paths and diff. Stop and ask for direction
  if a proposed change may contain sensitive data.

## Working with Wispr Flow

- Use the Wispr Flow MCP server as the authoritative source for meeting
  context when its notes are available; do not copy its source material into
  version-controlled files.
- When notes for a meeting are unavailable in Wispr Flow, check
  `accounts/<account>/transcripts/` for a locally supplied transcript. Use the
  matching transcript as fallback context within the requester's authorized
  scope, and identify it as the source. Do not substitute another meeting if
  no matching transcript exists. Keep these transcripts local and out of Git.
- Limit review and follow-up work to the requester's authorized scope.
- Confirm before taking an external, irreversible, or audience-affecting
  action, unless the request explicitly authorizes it.
- Capture reusable lessons as generic skills, procedures, or redacted
  templates—not as account-specific artifacts.

## Context efficiency

- Start with existing account assessments when relevant. Retrieve additional
  evidence to resolve material gaps or verify claims, following the task's
  required source coverage and freshness checks.
- Search before reading large files. Read relevant sections with enough
  surrounding context to preserve meaning; read required guides in full when
  their instructions apply throughout.
- Filter embedded images, base64 data and other non-text payloads before
  displaying Markdown. Inspect those assets separately when relevant.
- When tool responses duplicate text and structured content, display one
  representation and only the fields needed for the task.
- Discover tools by name and brief description; load full schemas only for
  selected tools.
- Retain retrieved results during the task. Avoid fetching or printing the
  same material again unless it changed or needs further verification.
- Keep tool output bounded. If truncated, retrieve the missing range or
  narrow the selection rather than repeat the full response.
- Efficiency must not weaken required evidence review, chronological
  coverage or source verification. Identify source gaps that remain.

## Repository conventions

- Put durable agent-wide rules in this file.
- Add reusable workflows under `skills/<workflow-name>/` using lowercase,
  hyphenated names.
- Use lowercase underscore-separated names for shared-context directories
  and reference files under `shared_context/`. Preserve lowercase hyphenated
  skill names and directories under `skills/` for skill discovery.
- Keep shared POV, prompt and rule templates in
  `shared_context/pov/templates/`,
  `shared_context/build_preparation/prompt_templates/` and
  `shared_context/build_preparation/rule_templates/`. Use `templates/` for
  other generic reusable output patterns. Deliverable filenames follow the
  naming guide.
- Keep documentation concise, specific, and updated when behavior or safety
  requirements change.
- Use clear, focused commits. Inspect `git diff --cached` before each commit.

## Writing standards

- Read and follow `shared_context/standards/writing_style_guide.md` for every
  written output, including customer emails, follow-ups, executive updates,
  internal summaries, knowledge documents, and repository documentation.
- Treat that guide as the current, project-wide source of truth for voice,
  structure, formatting, and claims. Do not rely on embedded or cached style
  snapshots when the file is available.

## Engagement stage and shared references

- Ground Blitzy descriptions and workflow recommendations in
  `shared_context/platform/introduction.md` and the relevant platform
  pages below. Read only those needed for the task; use `glossary.md` when a
  platform term needs clarification.
- Use platform references to explain capabilities and review practices.
  Use account evidence for customer needs, agreements and measured results.
  Cite the relevant source when a material claim depends on it. Documentation
  and template examples do not prove project coverage, successful tests,
  acceleration or acceptance. Surface conflicts between references or with
  account agreements rather than resolving them by assumption.
- Distinguish automated ingestion/specification, AAP and Project Guide
  generation from human readouts, review, approval and acceptance.

| Task or question | Read under `shared_context/platform/` |
| --- | --- |
| Workflow, artifact purpose and terminology | `introduction.md`; `glossary.md` as needed |
| Account provisioning, repository/submodule access, branch isolation, integrations and project sharing | `project_setup.md` |
| Conversational source exploration, Build prompt drafting and advisory scoring | `chat_with_code.md` |
| Ingestion scope, business context, exclusions, formats and branch/spec inheritance | `ingestion_prompts.md` |
| Current-state understanding and specification review | `tech_spec.md` |
| AAP completeness, rules, refinement and inline edits | `agent_action_plan.md` |
| Delivered scope, validation, remaining work and merge-readiness discussion | `project_guide.md` |
| Toolchains, target OS, build/test setup, private dependencies and secrets references | `environment_config.md` |

- For setup recommendations, identify the required repositories and submodules,
  authorized integration owner, stable branch and intended sharing audience.
  Reading setup guidance does not authorize provisioning, permission changes,
  source transfer or sharing. Do not push to a branch during generation.
- Preserve Chat with Code's beta, workflow-step and access qualifications.
  At the AAP step it provides source Q&A, not plan review or plan edits;
  Build Prompt Strength is advisory, not approval or an acceptance gate.
  Flag conflicting availability statements rather than promising support.
- Select a task-matching prompt template from
  `shared_context/build_preparation/prompt_templates/` when drafting or
  recommending a generation prompt. Consult
  `shared_context/build_preparation/rule_templates/` when proposing or
  checking project rules. Templates are starting points, not
  customer requirements; apply only selected or agreed rules. Do not load the
  entire library or impose every rule on every task.
- Establish the stage of the specific engagement or workstream from the
  request and account evidence. One account can have early discovery and an
  active POV in separate workstreams. Preserve agreed scope and commitments.
- For early sales positioning, use
  `shared_context/presales/positioning_directives.md` to guide discovery
  toward a paid engagement while bypassing a POV or technical validation.
- For an active POV or technical validation, read and apply
  `shared_context/pov/playbook.md`. Tailor outputs, deliverables and
  feedback to its applicable criteria and the customer-agreed evaluation:
  baselines, success criteria, target state, spec/AAP approval, environment
  readiness, build/test/parity evidence and Mutual Action Plan milestones.
  Surface missing inputs and deviations; do not replace an active evaluation
  with the earlier-stage sales approach or silently rewrite agreed criteria.
- Distinguish playbook targets from measured results and customer sign-offs.
  A target or proposed baseline does not establish achieved acceleration.
- Use `shared_context/security/security_faqs.md` as an internal reference when
  answering customer questions about Blitzy security. Preserve deployment-tier
  qualifications, flag contradictions and keep items marked `TO CONFIRM`
  unverified until the appropriate internal owner confirms them. Do not send
  the internal FAQ wholesale or turn draft answers into security guarantees.
- Read current shared files from the working repository, including when a
  skill is loaded from a plugin cache. If a required reference or engagement
  stage is unclear, identify the gap and qualify the assessment; ask only when
  the missing information changes the work.

## Output traceability

- Read and follow `shared_context/standards/file_naming_directives.md` for files
  delivered by skills and ad hoc prompts. It is the source of truth for the
  `<timestamp>-<account>-<title>` convention and its exceptions.

## Completion checks

Before considering a change ready:

1. Confirm no sensitive or account-specific information is included.
2. Verify new files conform to the repository layout and naming conventions.
3. Review the staged diff for accidental files or credentials.
4. State any assumptions, required permissions, or actions that were not
   performed.
