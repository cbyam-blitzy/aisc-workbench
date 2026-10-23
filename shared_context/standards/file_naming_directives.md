# File naming directives

Last updated: 2026-10-23. Refresh when the output naming convention changes.

Name new deliverable files from skills and ad hoc prompts using
`<account>-<title>-<timestamp>.<extension>`.

Put the account and descriptive title first so files are easy to identify in
file explorers. Keep the timestamp at the end, immediately before the extension.

- **Timestamp:** creation time in US Eastern time, using
  `YYYYMMDDTHHMMSS±HHMM` with the applicable EST or EDT offset.
- **Account:** the account's directory name, normalized to lowercase words
  separated by hyphens. Use `general` when no account applies; do not invent
  an account association.
- **Title:** a concise, descriptive title in lowercase words separated by
  hyphens. Include the project name when needed to distinguish deliverables.
- **Extension:** the actual file type, such as `.md`, `.pdf`, or `.docx`.

Fictional example: `example-account-adoption-review-20261019T130000-0400.md`.

Honor an explicit user-requested filename. When updating an existing file,
preserve its filename unless the user requests a new file or a rename; record
the revision date in the document where appropriate. Do not overwrite an
unrelated deliverable when a name collides.

Apply this convention to files being delivered, including exported copies.
It does not require creating a file for a chat-only response. Existing account
outputs were migrated to this convention on October 23, 2026, preserving their
original timestamps and updating affected local references. Preserve original
source filenames for transcripts and supplied project artifacts. Reusable
repository assets such as skills,
templates, and shared guidance retain stable filenames without timestamps.

Keep account deliverables in the ignored `accounts/` work area. Naming does
not authorize adding customer material to version control or sharing it.
