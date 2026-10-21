# Wispr Flow agent playbooks

This repository supports the AISC's work through reusable skills, guidance,
and templates for account evaluation, technical validation planning, Blitzy
artifact review, impact assessment, and customer follow-up. Wispr Flow's MCP
server provides meeting context for workflows that need it.

The AISC owns the technical validation path: the platform deep dive, POC
execution, key technical relationships within the account, and the credibility
of Blitzy's output. The AISC is the customer's technical counterpart—the
person the engineering team calls with a question, concern, or blocker.

These workflows help the AISC prepare technical discussions, assess evidence,
identify gaps, and coordinate next steps with customer engineering teams.

It is an automation and operating-guidance repository—not an archive of meeting
records.

## What belongs here

- Reusable agent instructions and decision rules.
- Skills and playbooks for recurring meeting-review workflows.
- Redacted templates for deliverables, follow-ups, and action plans.
- Documentation for safe, repeatable use of the Wispr Flow MCP server.

## What must not be committed

- Raw transcripts, meeting notes, recordings, or attachments.
- Customer- or person-specific outputs, including summaries and action plans
  that contain identifying or confidential details.
- API keys, tokens, credentials, or private MCP configuration.

The root-level `accounts/` directory is intentionally ignored by Git. It is a
local workspace for any temporary, meeting-derived material needed while
working; it is not a source-controlled deliverable location.

## Repository layout

| Path | Purpose |
| --- | --- |
| `AGENTS.md` | Operating rules and privacy requirements for agents. |
| `plugin.json` | Skills-only plugin manifest for Codex and ChatGPT. |
| `skills/` | Reusable workflow-specific skills, added as they are developed. |
| `shared_context/standards/` | Shared writing style and deliverable naming rules. |
| `shared_context/platform/` | Platform workflow, project setup, Chat with Code, glossary, ingestion, artifact review and environment references. |
| `shared_context/presales/` | Early sales positioning directives. |
| `shared_context/pov/` | Active evaluation playbook and agreement templates under `templates/`. |
| `shared_context/build_preparation/` | Prompt guidance, task-specific `prompt_templates/` and selectable `rule_templates/`. |
| `shared_context/artifact_review/` | Reusable artifact review criteria, including the AAP validation checklist. |
| `shared_context/security/` | Qualified internal security answers. |
| `templates/` | Generic, fully redacted output templates. |
| `accounts/` | Local, Git-ignored workspace for sensitive meeting-derived material. |

Shared-context directory and reference filenames use lowercase words separated
by underscores. Skill names and directories retain hyphens for discovery.
Account deliverables retain the timestamp/account/title convention in
`shared_context/standards/file_naming_directives.md`.

The repository is also exposed as the repo-local **Wispr Flow** plugin. In a
trusted project, restart the ChatGPT desktop app, open the Plugins Directory,
and install or refresh it from the `Wispr Flow` marketplace. Start a new chat
after installation, then invoke a workflow by name, for example
`$blitzy-write-follow-up-email`, `$blitzy-review-aap`,
`$blitzy-review-tech-spec`, `$blitzy-humanizer`, `$blitzy-review-project-guide`,
or `$blitzy-evaluate-acct`.

Use `$blitzy-review-project-guide` with a delivered solution's project guide to
summarize delivery, validation, business impact, and remaining human work. It
researches a comparable engineering baseline and asks for actual Blitzy compute
time before calculating acceleration.

Use `$blitzy-evaluate-acct` with an account name to create an internal strategy
memo from its meeting history. It connects discussion threads, stakeholder
goals, evaluation questions and adoption readiness to the guidance for each
workstream's stage. Account memos stay in the ignored `accounts/` workspace.

Ground platform explanations in `shared_context/platform/introduction.md`
and the relevant overview pages. Use `project_setup.md` for provisioning,
repository access, branches and sharing, and `chat_with_code.md` for source
exploration and Build prompt assistance, preserving its beta and step-specific
limits. `AGENTS.md` maps questions to references;
each skill identifies the pages it needs. Load only relevant material from the
working repository, including when running a cached plugin skill. Use platform
documentation for workflow context and account sources for customer commitments
and measured results. Surface conflicts and cite material supporting evidence.

Prompt templates and rule templates are selectable starting points. Choose the
template for the requested task and apply only relevant, selected or agreed
rules. Their examples and defaults do not become customer requirements.

Use `shared_context/presales/positioning_directives.md` for early sales
positioning toward a paid engagement while bypassing a POV/technical validation.
For an active evaluation, use `shared_context/pov/playbook.md` to guide
outputs, deliverables and feedback against applicable criteria and the agreed
evaluation. `AGENTS.md` defines the stage distinction for all workflows.

Use `$blitzy-draft-pov-eval-memo` to draft a pre-POV agreement and
`$blitzy-draft-pov-map` to draft its Mutual Action Plan from the shared
templates and account evidence. Both workflows mark unresolved inputs and
proposals, preserve agreed commitments, and keep account outputs local.

Use `shared_context/security/security_faqs.md` as an internal reference for
customer security questions. Preserve deployment qualifications and obtain
confirmation for items marked `TO CONFIRM` before using them externally.

## Refresh after changing skills

Last verified: 2026-10-15. Recheck these commands when the Codex CLI changes.

The installed plugin uses a cached copy. After saving changes in this repository:

1. From the repository root, confirm that `codex plugin marketplace list --json`
   resolves `wispr-flow` to this checkout.
2. Refresh the installed copy:

   ```sh
   codex plugin add wispr-flow-agent-playbooks@wispr-flow --json
   ```

3. Use the returned `installedPath` to verify the copied skills:

   ```sh
   diff -qr skills /path/from/installedPath/skills
   ```

   No output and exit status 0 mean the skill directories match. The refresh
   includes saved, uncommitted changes; a commit or push is not required.
4. Restart the desktop app and start a new chat. Type `$` and search for the
   exact `name` from the skill's `SKILL.md` frontmatter, such as
   `blitzy-review-project-guide`.

If the marketplace is missing, register this checkout once with
`codex plugin marketplace add . --json`, then repeat the refresh. Run commands
from the repository root so `.` resolves to the intended checkout.

This process was verified with the local `wispr-flow` marketplace. The installed
CLI's `marketplace upgrade` command refreshes Git marketplace snapshots; use
`plugin add` to refresh this local plugin. Keep customer material in the ignored
`accounts/` workspace and out of reusable plugin assets.

See the [official plugin packaging documentation](https://developers.openai.com/plugins/build/plugins)
for marketplace configuration, cached installs, and desktop restart guidance.

## Working with Wispr Flow

Use Wispr Flow's MCP server as the source of meeting context when notes are
available. When a meeting's notes are unavailable in Wispr Flow, check
`accounts/<account>/transcripts/` for a locally supplied transcript and identify
the matching transcript as the fallback source. Keep transcripts local and out
of Git. Keep the work scoped to the requester's authorization, and confirm any
external or irreversible action before performing it. Turn patterns that are useful across
meetings into generic, redacted playbooks in this repository rather than
checking in an example from a real account.

## Contributing

Before committing:

1. Review `AGENTS.md` and follow its privacy rules.
2. Inspect staged changes with `git diff --cached`.
3. Confirm that all examples use fictional or fully redacted data.
4. Keep changes focused and document new workflow assumptions.

If a file could identify a customer, attendee, meeting, or internal initiative,
keep it out of Git and use the ignored local workspace instead.
