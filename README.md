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
| `skills/` | Reusable workflow-specific skills, added as they are developed. |
| `templates/` | Generic, fully redacted output templates. |
| `accounts/` | Local, Git-ignored workspace for sensitive meeting-derived material. |

## Working with Wispr Flow

Use Wispr Flow's MCP server as the source of meeting context. Keep the work
scoped to the requester's authorization, and confirm any external or
irreversible action before performing it. Turn patterns that are useful across
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
