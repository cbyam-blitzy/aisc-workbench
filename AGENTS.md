# Agent instructions

## Purpose

Support the AISC with evidence-backed account assessments, technical validation,
Blitzy artifact review, impact analysis, customer follow-up, and platform guidance.
The AISC owns the platform deep dive, POV execution, technical relationships,
and credibility of Blitzy's output. Preserve customer responsibilities, agreed
scope, and approval authority; identify gaps and the owner or decision needed.
Use POV (proof of value) in authored work; preserve original raw source wording.

## Privacy and authorization

- Keep transcripts, notes, recordings, attachments, customer deliverables,
  personal information, confidential business details, credentials, and private
  MCP configuration out of version control.
- Use the Git-ignored `accounts/` area for local customer work; never force-add it.
- Use fictional or fully redacted reusable examples; omit uncertain examples.
- Before staging, review exact paths and diff. Stop and ask for direction if
  proposed changes may contain sensitive information.
- Work within authorized scope. Confirm external, irreversible, or
  audience-affecting actions unless the request already authorizes them.
- Capture reusable lessons only as generic guidance or redacted templates.

## Meeting evidence

Use Wispr Flow MCP as the authoritative meeting source when notes are available.
Otherwise use the matching local transcript under
`accounts/<account>/transcripts/` and identify the fallback. Never substitute
another meeting. Keep source material out of version-controlled files.

## Shared output standards

For every written output, read the current checkout's files under
`shared_context/standards/`: `writing_style_guide.md`,
`readability_directives.md`, and `file_naming_directives.md`.
They govern voice/claims, layout/final citation appendices, and delivered names.
Use live files even when a skill runs from a plugin cache. Reusable assets keep
stable names; customer deliverables stay in the ignored local work area.

## Primary coordinator and delegation

The main agent is the primary coordinator: own scope, source selection, task
coverage, conflict resolution, final synthesis, and authorization boundaries.
For substantial independent workstreams, delegate bounded tasks to:

| Specialist | Responsibility |
| --- | --- |
| `account_evidence` | Meeting chronology, stakeholders, needs, commitments, and evidence gaps |
| `technical_review` | Specification, AAP, or Project Guide review against matching authoritative inputs |
| `verification` | Independent checks of material claims, source traceability, scope, and unresolved gaps |

Read `shared_context/agent_operations/delegation.md` when delegating or creating,
updating, or resuming an account checkpoint. It defines assignments, handoffs,
coverage checks, and checkpoint refresh rules. Give specialists only relevant
context, source paths, and the applicable skill; prefer fresh context when the
runtime supports it. Specialists must follow applicable repository rules and
required guides. Delegation does not waive full-document or chronological review.
Keep short tasks and dependent steps in the main agent. Use available runtime
limits; start only useful specialists. Specialists return findings without
editing files or spawning further agents. The coordinator owns checkpoints and
final files. If delegation is unavailable, perform the same bounded work locally
and disclose that limitation; do not claim a specialist ran.

## Context efficiency

- Start with the relevant account checkpoint and assessment; verify freshness
  and resolve material gaps under the task's coverage requirements.
- Search before reading large files. Read relevant sections with context and
  required guides in full when instructions apply throughout.
- Filter embedded images, base64, and non-text payloads before displaying
  Markdown; inspect relevant assets separately.
- Discover tools by name and brief description before loading selected schemas.
  Display one representation of duplicate responses and only needed fields.
- Retain retrieved evidence. Re-fetch when changed or needed for verification.
  Bound output; retrieve a missing range instead of repeating truncated output.
- Preserve required source review and chronological coverage; state gaps.

## Task-specific guidance

Load only the references needed for the task; honor explicit source restrictions.

| Work | Required routing |
| --- | --- |
| Platform claims, workflows, setup, or artifact review | `shared_context/agent_operations/platform_reference_routing.md`; select applicable guides and follow its qualifications |
| Account strategy, positioning, discovery, POV planning/review, or security questions | `shared_context/agent_operations/engagement_guidance.md`; establish the workstream stage and select applicable references |
| Delegation, handoffs, or account checkpoints | `shared_context/agent_operations/delegation.md` |

Platform guidance describes capabilities; account evidence establishes needs,
commitments, approvals, and measured results. Templates are proposals unless
agreed. Preserve role/tier/project/IdP qualifications and flag conflicts.
Do not push to a project branch during generation. For Blitzy security answers,
use the internal security FAQ with its tier qualifications; keep `TO CONFIRM`
items unverified and do not send the FAQ wholesale. If a required reference or
stage is unclear, qualify the assessment; ask only when it changes the work.

## Repository conventions and completion

- Keep durable universal rules here, workflows in `skills/<hyphenated-name>/`,
  and task-specific guidance under `shared_context/`. Shared-context directories
  and files use lowercase underscores; skill names use lowercase hyphens.
- Keep POV templates in `shared_context/pov/templates/`, prompt templates in
  `shared_context/build_preparation/prompt_templates/`, project rules in
  `shared_context/build_preparation/rule_templates/`, and other generic patterns
  in `templates/`.
- Maintain instructions and references when behavior changes. Before completion,
  check reusable files for sensitive/account-specific material, filenames,
  layout, and affected references. Before every commit inspect staged paths
  and `git diff --cached`; keep commits focused.
- State assumptions, permissions still needed, and actions not performed.
