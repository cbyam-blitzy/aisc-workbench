# AISC Workbench

AISC Workbench provides reusable skills, operating guidance, and templates for
account evaluation, technical validation, Blitzy artifact review, impact
assessment, customer follow-up, and day-to-day platform questions.

The AISC owns the customer's technical validation path and the credibility of
Blitzy's output. These workflows support that work with evidence, clear gaps,
and decisions or actions assigned to the right owner.

## Get started

Follow the [setup and maintenance runbook](runbooks/new_machine_setup.md) to
install, verify, or refresh the local plugin. Keep this checkout available as
the working project so skills can read current shared guidance.

| Component | Current name |
| --- | --- |
| GitHub repository and checkout | `aisc-workbench` |
| Plugin identifier | `aisc-workbench@aisc-workbench` |
| Marketplace display name | AISC Workbench |

The plugin provides skills; follow the [Wispr Flow MCP setup runbook](runbooks/wispr_flow_mcp_setup.md)
to connect and verify meeting access. Customer files under `accounts/` do not
arrive with a clone.

## How to run a skill

Type **`$` followed by the skill name in the chat composer**.
The `/` prefix does not invoke this repository's skills. These are chat
instructions, not terminal commands.

1. Install the plugin, open `aisc-workbench` as the working project, and start
   a new chat. Restart the desktop app after installing or refreshing skills.
2. Type `$` and type or select the exact skill name, such as
   `$blitzy-review-aap`.
3. Add the task, account or workstream, and the relevant document paths or
   attachments. Include any scope restrictions or output preferences.
4. Send the message. Supply any missing inputs the skill identifies; review
   its findings and open decisions before acting on the output.

Copy one of these examples into chat and replace the fictional paths or account:

```text
$blitzy-evaluate-acct Assess Example Account from its available meeting history. Identify technical blockers and next decisions.
```

```text
$blitzy-review-aap Review these matching artifacts:
accounts/example-account/agent_action_plan.md
accounts/example-account/build_prompt.md
accounts/example-account/technical_specification.md
Identify scope changes, execution blockers, and the fixes needed before generation.
```

```text
$blitzy-humanizer Rewrite the text below. Return only the final version:
We would like to schedule a discussion to confirm the remaining technical inputs.
```

## Skill summaries

Choose the workflow that matches the task and supply the inputs listed below.
Customer-specific files and generated reports belong in the ignored `accounts/`
workspace; follow-up emails and rewrites are normally delivered in chat.

| Skill | What it produces | What to provide |
| --- | --- | --- |
| `$blitzy-evaluate-acct` | Account strategy memo connecting stakeholder goals, discussion history, adoption readiness, commercial status, and next steps | Account/workstream and available meeting history or matching local transcripts |
| `$blitzy-draft-pov-questionnaire` | Full customer-facing POV questionnaire tailored to the account evaluation, with evidence-backed prefills and blank unknowns; separate internal source notes | Account evaluation, selected workstream, and any existing questionnaire or scope agreement |
| `$blitzy-draft-pov-eval-memo` | Customer-reviewable pre-POV agreement covering scope, baseline, success criteria, responsibilities, and open approvals; separate internal drafting notes | Account evaluation, proposed or agreed scope, and existing agreements or memo |
| `$blitzy-draft-pov-map` | Mutual Action Plan with milestones, dates, owners, approval gates, and unresolved decisions; separate internal drafting notes | Account evaluation, agreed scope, and any Evaluation Memo or existing MAP |
| `$blitzy-review-tech-spec` | Briefing on the system, architectural findings, missing inputs, blockers, and who should confirm them | Technical specification and review scope; supporting account context if permitted |
| `$blitzy-review-aap` | Plan review identifying scope changes, directive coverage, factual conflicts, and execution-gating verdicts | Matching AAP, build prompt, and authoritative technical specification |
| `$blitzy-review-project-guide` | Delivery and impact report covering validation, remaining work, equivalent engineering effort, and acceleration when comparable elapsed time is available | Project Guide, supporting delivery evidence, actual Blitzy elapsed time, and any agreed evaluation baseline; missing time is requested |
| `$blitzy-write-follow-up-email` | Customer email draft summarizing outcomes and owner-first committed actions, with a separate note for material ambiguities | Meeting name/date and accessible meeting context or the matching transcript |
| `$blitzy-humanizer` | Natural rewrite preserving meaning and facts; a clean final version when requested | Text to edit, audience, and an optional writing sample |

Use [the setup runbook](runbooks/new_machine_setup.md#troubleshooting) if a
skill is missing or unavailable after typing `$`.

## Repository layout

Reusable guidance is version-controlled; customer evidence and deliverables stay local.

| Path | Purpose |
| --- | --- |
| `AGENTS.md` | Compact universal rules, coordinator responsibilities, and task-to-reference routing |
| `.codex/agents/` | Project-scoped account evidence, technical review, and verification specialists |
| `plugin.json`, `.agents/plugins/marketplace.json`, `.codex/config.toml` | Plugin manifest, local marketplace, and project enablement |
| `skills/` | Reusable workflows |
| `runbooks/` | Installation, verification, refresh, and troubleshooting |
| `shared_context/standards/` | Writing style, readability, citation placement, and naming |
| `shared_context/agent_operations/` | On-demand platform routing, engagement guidance, delegation, and checkpoint lifecycle |
| `shared_context/platform/intro/` | Overview, terminology, quickstart, workspace, knowledge base, and insights |
| `shared_context/platform/admin/` | Teams, SSO/SCIM, usage, demos, and locking |
| `shared_context/platform/project_lifecycle/` | Project setup, source Q&A, specification/AAP review, generation, and PR/code review |
| `shared_context/build_preparation/` | Ingestion/generation prompts, Golden Rules, Figma guidance, and prompt/rule templates |
| `shared_context/build_preparation/setup/` | Codebase preparation, submodules, environment configuration, and readiness testing |
| `shared_context/artifact_review/` | Shared review checklists |
| `shared_context/pov/` | Active-evaluation playbook and agreement templates |
| `shared_context/presales/`, `shared_context/security/` | Positioning guidance and qualified internal security answers |
| `templates/` | Other generic output patterns |
| `accounts/` | Git-ignored local customer workspace |

## Specialist agents experiment

The main agent coordinates substantial work and can delegate bounded reviews to
`account_evidence`, `technical_review`, and `verification`. Short tasks stay with
the coordinator. Specialists return traceable findings; the coordinator owns
final writing and local account checkpoints. Model settings inherit existing
preferences; the project configuration caps spawned threads at three.

Start a new session in this checkout to load the experiment. Follow the
[trial runbook](runbooks/specialist_agents_trial.md) for activation, a fictional
smoke trial, checkpoint resumption, and comparison with a single-agent baseline.
The [delegation guide](shared_context/agent_operations/delegation.md) defines
handoffs and freshness checks. Use the
[checkpoint template](templates/account_checkpoint.md) only inside ignored
`accounts/<account>/checkpoints/` for populated account snapshots.

This project configuration is separate from installing the skills plugin.
Runtime availability and configuration loading must be verified in the client;
the experiment does not establish measured context or token savings.

## Working standards

Read [AGENTS.md](AGENTS.md) for operating rules and select only the references
needed for the task. Platform documentation explains capabilities; account
evidence establishes customer commitments and measured results.

- Follow the [writing style guide](shared_context/standards/writing_style_guide.md)
  for voice and claims, [readability directives](shared_context/standards/readability_directives.md)
  for structure and final citation appendices, and
  [naming directives](shared_context/standards/file_naming_directives.md) for files.
- Use Wispr Flow MCP meeting notes when available. Otherwise use the matching
  local transcript under `accounts/<account>/transcripts/` and identify it as
  the fallback source.
- Use the active POV playbook for an agreed evaluation. For early discovery,
  [positioning directives](shared_context/presales/positioning_directives.md)
  establish the rules; the
  [AI-DLC positioning playbook](shared_context/presales/ai_dlc_positioning_playbook.md)
  helps apply them through discovery questions, talk tracks, objections, demos
  and adoption-pilot examples. Read relevant sections from the current checkout
  when needed; the whole playbook is not required for every skill.
- Maintain the positioning playbook in place as guidance evolves, update its
  revision date and source appendix for material changes, and update the
  directives only when positioning rules change. Keep examples in the playbook
  rather than copying them into skills. Operational references are read as
  needed, not loaded into every POV deliverable.
- Treat prompt/rule templates as selectable starting points. Their examples
  are not customer requirements or proof of validation.

## Contributing

Commit reusable instructions and redacted templates; keep customer material,
credentials, and private configuration out of Git.

1. Follow the privacy rules in `AGENTS.md`; never force-add `accounts/`.
2. Check affected references and filenames.
3. Review the exact staged paths and `git diff --cached` before committing.
4. Keep commits focused and update documentation when behavior changes.
