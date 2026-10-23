# Specialist agents trial

Last updated: 2026-10-23. Refresh when Codex agent configuration or trial procedures change.

This branch tests a primary coordinator with three specialist roles, selective
reference loading, and local account checkpoints. Use fictional evidence before
running the workflow on authorized customer work.

## Activate and inspect

1. Open this checkout on the feature branch in a current Codex client. Start a
   new session so it loads the changed root instructions and project config.
2. Confirm the client trusts and loads project configuration. The project
   `.codex/config.toml` enables agents and caps spawned threads at three;
   model and reasoning choices inherit existing settings.
3. Ask the coordinator to identify the three role names and their purposes.
   Custom definitions are in `.codex/agents/`; the primary coordinator is the
   main agent governed by `AGENTS.md`, not a fourth spawned worker.
4. If the client cannot load named agents, explicitly provide the applicable
   role file and bounded assignment to its delegation tool. Report that fallback.
   If no delegation tool is available, report a single-agent trial instead.

No global settings, credentials, or connector configuration need to change.
The role files express behavior; they do not impose a separate security sandbox.
For another checkout, copy the reusable configuration through normal Git review;
the plugin package alone does not install this project's root guidance/agents.

## Fictional smoke trial

Create fictional fixtures only in a temporary directory or ignored local area.
Avoid real meetings and connectors for this smoke trial. Supply numbered lines
or stable section IDs to make source checks reproducible:

- A meeting note: a proposed scope, a later agreed scope, an unassigned owner,
  and no customer approval of the technical plan.
- A build prompt, specification, and AAP: at least one clear scope conflict and
  no runtime validation evidence.
- A draft claim saying the plan was approved and tests passed, without support.

Ask the coordinator:

```text
Use the three specialist roles to review these fictional fixtures only.
Do not use connectors, change source files, or contact anyone. Have
account_evidence extract chronology and commitments, and technical_review
review the matching technical inputs. Then have verification check a combined
draft against the fixtures, including approval and test-success claims.
Return sources, coverage gaps, and required corrections. Do not execute the plan.
```

Expected behavior: two bounded reviews can run independently; verification
follows a draft, rejects unsupported approval/test claims, and preserves
uncertainty. The coordinator resolves the scope mismatch and identifies the
missing owner/approval without inventing either. All outputs retain precise
evidence locations and distinguish recommendations from agreements.

## Checkpoint and resumption trial

For a fictional account, explicitly authorize a local checkpoint and provide its
account/workstream. Confirm `git check-ignore <checkpoint-path>` succeeds before
writing. Use the template and timestamp naming convention. In a fresh session,
ask to resume from it, then supply a later fictional note that changes scope.
The resumed workflow must check freshness, preserve the changed scope, mark
unavailable checks, and avoid treating prior proposals as agreements.
Confirm `git status --short --untracked-files=all` excludes checkpoint content.
Never stage it, even though the smoke data is fictional.

## Compare with a single-agent run

Use the same fictional evidence, requested scope, and output requirements in
fresh sessions. Request a single-agent baseline explicitly, then a delegated
run. Record client/version, model/effort, input versions, agents actually spawned,
elapsed time, available primary-context and total-token metrics, omissions, and
corrections. Compare checkpoint resumption separately from initial review.

Passing the smoke trial shows workflow behavior; it does not prove production
coverage or context savings. If metrics are unavailable, report that limitation.
Delegation can increase total token usage. Checkpoint freshness and source review
requirements still apply. Return to the base branch after preserving wanted
work to stop using the experiment in a subsequent session; no global settings
were changed.

## Initial branch validation — 2026-10-23

| Check | Result |
| --- | --- |
| TOML syntax and required role fields | Passed; existing plugin enablement preserved |
| Relative links and moved reference paths | Resolved; extracted platform and engagement guidance preserved verbatim |
| Root instruction size | 1,471 to 814 whitespace-separated words; 11,947 to 6,367 UTF-8 bytes |
| Independent configuration review | No remaining material findings after correcting a specialist-writing inconsistency |
| Account evidence behavior | Fresh-context specialist distinguished the latest agreement from an earlier proposal and identified approval/owner gaps |
| Technical review behavior | Fresh-context specialist found the scope conflict and separated future validation from executed results |
| Verification behavior | Fresh-context specialist independently rejected unsupported scope, approval, test, and ownership claims |
| Checkpoint resumption | Separate fresh-context run found later evidence, marked cached scope/coverage stale, and retained approval/validation limits |
| Privacy and diff checks | Synthetic checkpoint destination ignored; account content excluded from Git status; diff whitespace check passed |

Behavioral trials used fictional local fixtures and explicit role instructions
with this session's delegation tools, rather than native named-agent discovery.
No connectors or real customer evidence were used. TOML parsing and instruction
review do not establish that a particular client loads the new configuration.
Native discovery, full customer workflows, and comparable context/total-token
measurements remain to be tested in fresh client sessions. The size figures
measure root-file text only, not complete prompt or context savings.

## Appendix — Sources and evidence

- OpenAI, [Subagents](https://learn.chatgpt.com/docs/agent-configuration/subagents),
  checked 2026-10-23: project agents under `.codex/agents/`, configuration keys,
  inherited permissions/model settings, and coordination/token tradeoffs.
- [Delegation and checkpoints](../shared_context/agent_operations/delegation.md):
  local role boundaries, evidence handoffs, and checkpoint lifecycle.
