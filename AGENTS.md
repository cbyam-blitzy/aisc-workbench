# Agent instructions

## Purpose

This repository holds reusable operating guidance for agents that work with
Wispr Flow through its MCP server. Its contents must remain safe to share with
everyone who has repository access.

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

## Repository conventions

- Put durable agent-wide rules in this file.
- Add reusable workflows under `skills/<workflow-name>/` using lowercase,
  hyphenated names.
- Put generic reusable output patterns under `templates/`.
- Keep documentation concise, specific, and updated when behavior or safety
  requirements change.
- Use clear, focused commits. Inspect `git diff --cached` before each commit.

## Writing standards

- Read and follow `shared-context/blitzy_writing_style_guide.md` for every
  written output, including customer emails, follow-ups, executive updates,
  internal summaries, knowledge documents, and repository documentation.
- Treat that guide as the current, project-wide source of truth for voice,
  structure, formatting, and claims. Do not rely on embedded or cached style
  snapshots when the file is available.

## Output traceability

- Prefix every file delivered to a user with its creation timestamp in US
  Eastern time (EST or EDT, as applicable), using the filename format
  `YYYYMMDDTHHMMSS±HHMM_<descriptive-name>`. For example:
  `20261015T102530-0400_aap-review.md`.
- Do not add delivery timestamps to reusable repository assets such as skills,
  templates, or shared guidance. Apply the prefix when producing a user-facing
  deliverable file.

## Completion checks

Before considering a change ready:

1. Confirm no sensitive or account-specific information is included.
2. Verify new files conform to the repository layout and naming conventions.
3. Review the staged diff for accidental files or credentials.
4. State any assumptions, required permissions, or actions that were not
   performed.
