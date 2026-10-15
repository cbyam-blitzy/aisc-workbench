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
  context; do not copy its source material into this repository.
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

## Completion checks

Before considering a change ready:

1. Confirm no sensitive or account-specific information is included.
2. Verify new files conform to the repository layout and naming conventions.
3. Review the staged diff for accidental files or credentials.
4. State any assumptions, required permissions, or actions that were not
   performed.
