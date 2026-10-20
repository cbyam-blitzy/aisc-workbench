---
name: blitzy-draft-pov-map
description: Draft or update a Blitzy POV Mutual Action Plan from an account evaluation and the shared MAP template. Use to turn evaluation scope into milestones, dates, responsibilities, approval gates and visible open decisions for customer review; not for a general account strategy memo or final POV results report.
---

# Draft a POV Mutual Action Plan

Turn the account evaluation into a customer-reviewable MAP using the current shared template. The Evaluation Memo defines scope, success criteria and measurement; the MAP tracks when work and decisions occur and who is responsible. Preserve that distinction and the customer's actual commitments.

## Resolve inputs

Resolve the account, workstream and existing MAP from the request and workspace. Locate the account evaluation in `accounts/<account>/`, including older filename conventions. Use the user-selected evaluation or the latest relevant revision after checking its date, evidence cutoff and scope. Ask only when competing inputs or workstreams would materially change the plan; otherwise state the selected scope.

Read the current working repository files, including when this skill is loaded from a plugin cache:

- `shared_context/blitzy_pov_templates/blitzy_pov_map_template.md`
- `shared_context/blitzy_writing_style_guide.md`
- `shared_context/file_naming_directives.md`
- `shared_context/blitzy_pov_playbook.md`
- `shared_context/blitzy_overview/blitzy_intro.md`

Find the repository through the workspace and parent directories; do not hardcode a machine path. Follow account instructions. Read any relevant Evaluation Memo, approved scope, baseline worksheet, existing MAP or written changes supplied in the account folder. An Evaluation Memo is useful but not required to produce a discussion draft: flag its absence and leave approval-dependent fields pending. Do not create or revise a separate Evaluation Memo unless requested.

If a required shared reference is unavailable, identify the missing path and qualify provisional output. Do not invent a structure and present it as the shared template. Establish the selected workstream's engagement stage; preserve an active evaluation rather than substituting early-stage sales positioning or expanding it into broader adoption work.

## Blitzy reference context

Read the relevant pages in `shared_context/blitzy_overview/` when tailoring milestones: `ingestion_prompts.md` for optional context and branch/spec inheritance, `tech_spec.md` for specification review, `agent_action_plan.md` for plan approval/refinement, `project_guide.md` for delivery and review, and `environment_config.md` for setup and validation. Use `glossary.md` for terminology. Match milestones to the selected workflow and agreed validation depth; documentation does not prove readiness or completion. Consult task-matching prompt/rule templates in `shared_context/blitzy_prompt_templates/` and `shared_context/blitzy_rule_templates/` only when needed to define proposed inputs or rules.

Use `shared_context/blitzy_overview/project_setup.md` to tailor entry/preparation milestones for provisioning, repository/submodule permissions, branch isolation and the intended project audience. Read `chat_with_code.md` in that directory when planning source exploration or Build prompt drafting. Schedule that assistance within the relevant step; AAP-stage chat cannot review or edit the plan, and advisory prompt scoring does not complete an approval milestone.

## Separate evidence from proposed planning

Use the evaluation as the main context without rerunning the entire account assessment. Its recommendations are proposals, not customer agreements. Track material milestone fields against their source, date and status: recorded agreement, discussed direction, proposal or missing/conflicting input.

Use actual agreements to establish approved scope, dates, owners and gates. Surface discrepancies between the evaluation, memo, existing MAP and shared guidance rather than silently changing commitments. For material disputed statements, inspect the cited meeting evidence when available. Wispr Flow MCP is the authoritative meeting source when notes are available; otherwise use the matching local transcript in `accounts/<account>/transcripts/` and identify the fallback. Never substitute another meeting or claim verification of inaccessible evidence. If relying only on the account evaluation, cite its relevant sections in the internal notes.

Keep different teams' targets, capacity, reviewers and commercial decisions separate. For multiple tracks, use separate plans or clearly identify track-specific rows and dependencies without ambiguous milestone IDs. Do not assume a sponsor's title establishes authority, legal/security progress authorizes source access, or a planned meeting or run has happened.

## Populate the shared MAP template

Preserve the current template's header fields, phases, milestone IDs, completion conditions, six milestone-table columns, status definitions, progress notes and agreed-changes structure. Tailor descriptions to the selected scope without dropping approval or validation requirements. Mark the plan **DRAFT FOR DISCUSSION — NOT YET AGREED** unless approval is established. Link the Evaluation Memo by actual filename/version and identify a draft as a draft; otherwise mark the reference as missing.

Carry forward these planning distinctions:

- **Entry:** P1–P5 cover scope/target/validation agreement, approved baseline, required authorizations, signed Evaluation Memo and agreed MAP, and confirmed inputs. K1 confirms entry, checkpoints, final readout and escalation contacts. Record gaps; do not imply entry is complete merely because this draft exists.
- **Preparation:** retain the current template order: **R1 — Source-control access verified; R2 — Source-control repository set up for Blitzy ingestion; R3 — Ingestion context confirmed.** Verify access and repository inputs, then confirm scope, domain context, exclusions and specification inheritance or regeneration. An ingestion prompt is optional platform functionality; prepare one when needed or agreed. Preserve any prompt requirement in an existing agreed MAP, and flag differences rather than silently changing it. Keep “Before ingestion” references consistent with the milestone IDs.
- **Specification:** X1 is ingestion and automatically generated Technical Specification delivery. X2 is its human readout; X3 is customer validation. Do not schedule ingestion and automatic specification generation as separate platform runs.
- **Generation readiness:** X4 verifies reproducible environment setup and required dependencies/data; X5 prepares build intent and the AAP; X6 records joint AAP approval. Customer spec validation, verified environment readiness and AAP approval precede generation. Environment preparation may run in parallel with specification work after entry approval.
- **Delivery and review:** X7 delivers the generated code/PR and accompanying Project Guide, with automated validation in the configured environment. X8 accepts successful build evidence and reproducibility. X9 reviews tests and functional/parity evidence, including failures and limits. Do not turn the Project Guide into a separate generation run or treat generated tests as tests executed successfully.
- **Evaluation and next decision:** E1 is the delivery readout, E2 the baseline comparison, E3 the final technical acceptance decision and N1 the sponsor's next-step decision. A completed review can record unmet or unverified criteria; milestone completion does not itself establish POV success. Commercial kickoff or broader work requires its own agreement.

Use the current shared template as the source of truth for future revisions. Flag differences with an existing agreed plan instead of silently renumbering its historical references. For greenfield work, adapt code-ingestion preparation to the agreed requirements and repository needs; use Not applicable only with recorded joint agreement and rationale.

Populate expected completion dates and responsible contacts on both sides from evidence. If names, authority, review availability or dates are unknown, mark them pending. A role may be proposed, but do not assign a person by inference or turn an unscheduled action into a commitment. Explicitly label suggested dates as proposals and preserve them as unagreed until approved. Do not invent fixed week estimates or use a broader roadmap deadline as the POV readout date.

Start milestones as **Not started** unless evidence supports another template status. Unknown progress remains unverified in drafting notes; the default is not a verified historical claim. Use **Scheduled** only for confirmed scheduling and **Blocked** only for an actual impediment to progress, not merely an open drafting field. A security report alone cannot complete P3 while required evaluation terms or access authorization remain unresolved. Future spec/AAP approvals, builds, tests and results do not need to exist to agree their planned milestones.

P2 and E2 must refer to the same approved scope and measurement boundaries as the Evaluation Memo. Keep any playbook acceleration target proposed until accepted. Compare matched elapsed durations, separate human person-hours, and do not infer delivery acceleration from compute time or aggregate agent-hours.

## Make open inputs and reviews visible

Use **BOLD UPPERCASE (LOUDCASE)** markers throughout the draft:

- **INPUT REQUIRED — CONFIRM CUSTOMER TECHNICAL OWNER** for missing information.
- **REVIEW REQUIRED — APPROVE PROPOSED READOUT DATE** for supplied proposals or decisions needing approval.

Add a specific callout at the start of each section needing input or further review. In the milestone table, put markers directly in the affected date, owner or completion-condition cell. Add a short phase-level review summary above the table, keyed to milestone IDs, when it helps identify unresolved gates. Keep status cells within the template's status vocabulary; put qualifications in the milestone text or internal notes. The document-wide draft label alone is insufficient.

Keep settled content and explanatory detail in normal case. Distinguish missing inputs from approval of a proposal; do not flag future execution evidence as missing at entry. Remove or revise markers when decisions are resolved.

For an initial plan, leave the progress and agreed-change logs empty rather than inventing updates, actual dates or approvals. Put drafting gaps in the review callouts and internal notes. For updates, preserve original dates, actual history and existing IDs; record supported changes and their approvals in the agreed-changes log. Do not backdate approvals, erase missed milestones or assume an extension.

## Deliver and verify

Save a Markdown MAP by default in the ignored account folder using `shared_context/file_naming_directives.md` and a title such as `pov-map`, including the project when useful. Preserve an existing filename for updates. Honor a requested destination or format.

Save separate concise internal drafting notes in the account folder under the same naming convention. Include source links/sections and evidence cutoff, material field references keyed to milestone IDs, scope assumptions, conflicting commitments, proposed owners/dates and decisions blocking entry or generation. Keep internal strategy and negotiation commentary out of the customer-review MAP. If a single file is requested, use a clearly labeled internal appendix and identify it before any customer use.

Read back the MAP and notes. Check milestone IDs and order, R1–R3 references, gates and dependencies, memo consistency, both owner columns, expected versus actual dates, statuses supported by evidence, preserved history and source links. Verify that every unresolved section or field has the required bold uppercase marker and that future evidence has not been treated as an entry requirement. Confirm the skill and other reusable files contain no customer details; keep account artifacts out of version control.

Return clickable links to the MAP and internal notes, plus the few decisions that block agreement. Drafting does not authorize sending, publishing, scheduling meetings, changing external records, signing, committing or pushing.
