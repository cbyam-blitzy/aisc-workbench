# Connect Wispr Flow MCP for meeting retrieval

Last updated: 2026-10-22. Refresh when the endpoint, authorization flow,
client configuration, or access policies change.

Connect your authorized Wispr Flow account to Codex, then verify retrieval of
a known meeting. AISC Workbench supplies skills; it does not install or
authenticate the meeting connection.

## Before connecting

Use the account approved for your work and confirm that it has Notetaker and
MCP access. Personal and work accounts contain separate content. Authorization
is account-wide, including existing content; it is not limited to one meeting.

Organization policies and an active HIPAA BAA can block MCP. Ask the account
owner or administrator to resolve restrictions; do not change policy to finish
setup. If prompted about cloud access, follow your organization's policy.

## Register the server in Codex

Use the official remote HTTP endpoint. No API key or local server is needed.
In Wispr Flow, find it under **Settings → MCP → All other apps**:

```text
https://api.wisprflow.ai/connect/mcp
```

1. Check existing registration before adding a duplicate:

   ```sh
   codex mcp list
   ```

2. If `wisprflow` is absent, register it:

   ```sh
   codex mcp add wisprflow --url https://api.wisprflow.ai/connect/mcp
   ```

3. Complete browser authorization with the intended Wispr Flow account.
   If sign-in was not started or remains incomplete, run:

   ```sh
   codex mcp login wisprflow
   ```

4. Review the requested access and finish authorization. Signing in alone
   does not complete the connection.

`wisprflow` is the local server name used in this runbook. If an approved
connection already uses another name, use that name in subsequent commands.

Codex normally stores the entry in `~/.codex/config.toml`; the CLI and desktop
app share configuration. An equivalent user-level entry is:

```toml
[mcp_servers.wisprflow]
url = "https://api.wisprflow.ai/connect/mcp"
```

This entry registers the endpoint; OAuth login is separate. Keep connection
configuration and credentials outside this repository. Do not copy another
person's configuration or tokens. The tracked `.codex/config.toml` is for
project enablement, not private meeting access.

## Verify meeting retrieval

Verify the actual meeting tools and content before relying on the connection.
Registration alone does not establish retrieval access.

1. Restart the desktop app and start a new chat in this checkout.
2. Ask the agent to confirm that `search_meetings` and `get_meeting` are
   available from Wispr Flow. In the Codex terminal UI, `/mcp` shows active
   servers; this is a status command, separate from `$` skill invocation.
3. Use a meeting you are authorized to access. Replace the placeholders in
   this chat request:

   ```text
   Use Wispr Flow to find the meeting titled <known title> on <local date>
   in <time zone>. Retrieve its notes and report the meeting title, local
   date, and a brief description so I can confirm the match. If a transcript
   is available, confirm that it can be retrieved. Do not save any files.
   ```

4. Confirm the returned meeting matches. Search results alone do not verify
   notes or transcript retrieval. Missing transcripts can reflect sharing
   permissions or retention rather than a failed connection.

For repository work, use Wispr Flow as the authoritative meeting source when
notes are available. If unavailable, use only the matching authorized local
transcript under `accounts/<account>/transcripts/` and identify the fallback.
Never substitute a different meeting. Keep all retrieved evidence out of Git.

## Troubleshooting

Resolve the failing layer, then repeat the retrieval check.

| Symptom | Action |
| --- | --- |
| `codex mcp` is unavailable | Check `codex mcp --help` and install an organization-approved CLI with MCP support |
| Registered server, but no tools in chat | Restart the app, start a new chat, and check the active server and any client or managed-policy restrictions |
| Authorization is missing or expired | Run `codex mcp login wisprflow` and complete browser authorization with the intended account |
| Sign-in succeeds but authorization does not finish | Return to the authorization flow; verify completion before retrying retrieval |
| Endpoint connection fails | Confirm the exact URL above, without a trailing slash, and check network access |
| Tools remain blocked after authorization | Ask the administrator to check Notetaker, MCP, cloud-access, and BAA restrictions |
| Expected meeting is absent | Check the authorized account, meeting title, local date/time zone, and existing access; use a supplied shared-note link when applicable |
| Meeting is found but transcript is unavailable | Check permissions and retention; use available notes with that limitation or the matching authorized local transcript |

## Appendix — Sources and evidence

- **Endpoint and OAuth:** Wispr AI, [official Wispr Flow MCP plugin README](https://github.com/Wispr-AI/wispr-flow-plugin), reviewed 2026-10-22. Documents the remote endpoint, browser OAuth, and no API-key requirement.
- **Authorization, policy, and retrieval limits:** Wispr Flow, [Connect Claude, ChatGPT or another MCP client to Wispr Flow](https://docs.wisprflow.ai/articles/9551372685-connect-an-mcp-client-to-wispr-flow-remote-mcp-server), reviewed 2026-10-22. Covers setup, account scope, policy restrictions, and transcript access. The server is read-only.
- **Codex configuration and commands:** OpenAI, [Model Context Protocol](https://learn.chatgpt.com/docs/extend/mcp?surface=cli), reviewed 2026-10-22. Covers shared configuration, HTTP servers, OAuth login, and server status. Local `codex mcp add --help` and `codex mcp login --help` confirm the command syntax.
- **Evidence handling:** [AGENTS.md](../AGENTS.md), “Privacy and authorization” and “Meeting evidence.” The verification prompt follows these repository rules.
- **Verification boundary:** The existing local connection uses this endpoint, and its meeting-tool definitions are available in the current session. Fresh-machine login and live meeting retrieval were not exercised for this documentation change; no connection or credentials were changed.
