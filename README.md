# Wispr Flow agent playbooks

This repository contains reusable skills, instructions, and templates for agents
that review meeting context, take authorized follow-up actions, and produce
outputs through Wispr Flow's MCP server.

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
| `templates/` | Generic, fully redacted output templates. |
| `accounts/` | Local, Git-ignored workspace for sensitive meeting-derived material. |

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
goals, evaluation questions and adoption readiness to the current pre-sales
positioning directives. Account memos stay in the ignored `accounts/` workspace.

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
