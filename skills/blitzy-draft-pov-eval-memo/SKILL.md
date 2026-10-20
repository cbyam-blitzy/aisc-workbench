---
name: blitzy-draft-pov-eval-memo
description: Draft or update a Blitzy pre-POV evaluation memo from the shared POV memo template and an account evaluation. Use to document proposed or agreed scope, baseline, success criteria, responsibilities and timeline for customer review; not for a final results readout or a general account strategy memo.
---

# Draft a POV evaluation memo

Turn the account evaluation into a customer-reviewable draft using the current shared template. Preserve the customer's actual commitments and make the decisions still needed before signing explicit. This is the entry agreement; execution results belong in the Project Guide and final readout.

## Resolve inputs

Resolve the account, workstream and existing memo from the request and workspace. Locate the account evaluation in `accounts/<account>/`; filenames may use older conventions. Use the user-selected evaluation, or the latest relevant revision after checking its date, evidence cutoff and scope. Do not assume the newest filename covers every workstream. Ask only if competing inputs or workstreams would materially change the draft; otherwise state the selected scope.

Read these current files from the working repository, even when this skill is loaded from a plugin cache:

- `shared-context/blitzy-pov-templates/blitzy_pov_eval_memo_template.md`
- `shared-context/blitzy_writing_style_guide.md`
- `shared-context/file_naming_directives.md`
- `shared-context/blitzy_pov_playbook.md`
- `shared-context/blitzy_intro.md`

Find the repository through the workspace and its parent directories; do not hardcode a machine path. Read account instructions and any existing scope agreement, memo or MAP relevant to the requested work. If a required reference is unavailable, identify the missing path and qualify any provisional output; do not present an invented structure as the shared template.

The account evaluation supplies context, not proof that its recommendations were accepted. Establish the selected workstream's stage and preserve any existing evaluation commitment. Do not replace an active conversion or implementation evaluation with analysis-only discovery or broader adoption work. Read the pre-sales positioning directives only if an early-stage commercial question is relevant; they do not override agreed POV terms.

## Separate evidence from decisions

Map material fields to the account evaluation's cited evidence and any actual agreements. Keep a compact working record of the source, date, workstream, proposed wording and status:

- **Recorded agreement:** supported by an explicit agreement or commitment, with attribution and date.
- **Discussed direction:** a stated preference or candidate scope that still needs approval.
- **Proposal:** a recommendation from the account evaluation or the drafting agent.
- **To confirm:** missing, conflicting, stale or ambiguous information.

Use the supplied evaluation without rerunning the entire account assessment. For material disputed commitments, check its referenced source when available. Use Wispr Flow MCP as the authoritative meeting source when notes are available; otherwise use the matching local transcript in `accounts/<account>/transcripts/` and identify it as the fallback. Never substitute another meeting or claim to have verified an inaccessible source. If relying only on the evaluation, cite its section and disclose that boundary in the internal notes.

Distinguish later changes from unresolved disagreement. Do not infer a sponsor's authority from title, a fee from a discount discussion, purchase authorization from security clearance or MSA progress, or customer approval from a Blitzy proposal. Keep separate teams' target languages, architecture choices, capacity and acceptance owners separate. Do not add parallel workstreams, API/UI work, portfolio analysis or broader process changes without supporting agreement.

## Populate the shared template

Preserve its eight sections, tables, measurement method and agreement structure. Replace placeholders with supported account details. Honor explicit user edits and recorded customer agreements; identify conflicts with the template or playbook for resolution rather than silently rewriting them.

Mark the document **Draft for discussion — not yet agreed** unless its approval status is established. Keep agreement dates and signature fields pending until supported. Proposed terms and unresolved fields must remain visibly labeled even under headings such as “Agreed scope.” Use bold uppercase (LOUDCASE) markers for open items: **INPUT REQUIRED — TECHNICAL OWNER** for missing information and **REVIEW REQUIRED — APPROVE PROPOSED SCOPE** for decisions or terms needing review. Follow the marker with concise supporting detail in normal case. Do not leave generic instructional placeholders that could be mistaken for completed terms. Do not fill unknown fees with $0, dates with invented deadlines, or unknown owners with inferred names.

At the start of each section with unresolved items, add a specific **BOLD UPPERCASE** callout naming the additional inputs and/or review needed. Mark the affected fields and table cells inline as well, so a reader scanning either the section or the table can see what remains open. Distinguish missing inputs from review of supplied proposals; do not mark future execution evidence as missing at entry. Preserve ordinary casing for settled content and explanatory prose. Remove or revise markers when an item is resolved; the document-wide draft label alone is insufficient.

Address the following within the corresponding template sections:

1. **Purpose and goals:** name the bounded evaluation and business decision. State the fee only when established. Keep any future commercial engagement separate from this evaluation.
2. **Scope and target outcome:** specify the application/input boundary, repositories and snapshots where known, included change, stack and architecture, functional acceptance, environment, dependencies, tests/data, exclusions and roadmap relationship. Label candidate targets as proposals. Preserve required implementation and validation; do not let broad production exclusions weaken agreed functional acceptance.
3. **Baseline:** record duration and units, estimation basis, normal team and tools (including existing AI tools), equivalent starting/completion events, included review/retry/rework time, waits/exclusions and approvers. A customer-reported test count, analysis estimate or generic benchmark is not an approved delivery baseline. Retain the template's 5× target as a proposed target until accepted, unless the evidence establishes a different agreed target; surface that difference. Never claim achieved acceleration in an entry memo.
4. **Readiness:** separate approvals required before ingestion from those required before generation. Record access/setup owners and dates as known or pending. A future Technical Specification or AAP does not need approval at memo drafting time; its review gate must be planned. Reference the secure credential process without including secret values.
5. **Success criteria:** retain the template's six criteria and tailor acceptance requirements, planned evidence and customer review roles to the selected increment. Record applicability and exceptions explicitly. Define any percentage threshold's denominator, quality standard and verification method before treating it as an acceptance rule. For modernization, specify parity scenarios, expected results/tolerances and coverage limits. Do not confuse a successful build, test count or sample conversion with proven parity or production readiness.
6. **Working model and timeline:** assign only supported responsibilities and dates. Separate automated ingestion/specification, AAP and Project Guide generation from human validation, approval, readout and acceptance. Preserve the template's Blitzy-led POV model unless a different arrangement was agreed; flag conflicting expectations for resolution. Reference the MAP and schedule review availability, dependencies and the final readout without inventing a window or extension.
7. **Final evaluation:** describe the future evidence-based decision and treatment of unmet or unverified criteria. Preserve customer technical acceptance and sponsor investment decisions. Intent to discuss a purchase is not a purchase commitment.
8. **Agreement:** retain unsigned fields and identify only existing pre-POV attachments by title/version. Do not require generated execution artifacts or result links as attachments at entry.

Keep acceleration as approved baseline elapsed duration divided by actual Blitzy elapsed duration, using matched units, scope, quality and measurement boundaries. Track human person-hours separately; aggregate agent-hours or compute time alone cannot establish delivery acceleration. Define the future evidence collection without inventing results or backfilling approvals for work already underway.

## Deliver and verify

Save a Markdown memo by default in the ignored account folder using the shared naming directives and a title such as `pov-evaluation-memo`, including the project when useful. Preserve an existing filename when updating it. Honor a requested destination or format.

Keep the memo suitable for customer review. Save a separate, concise internal drafting-notes file in the account folder, following the same naming directives, with:

- The evaluation and supporting sources used, dates/evidence cutoff and material field references.
- Unresolved decisions and conflicts, the affected memo section, a known or proposed decision owner, and the milestone they block.
- Proposals requiring approval and any source limitation that changes confidence.

Keep candid strategy, inferred objections and negotiation commentary in those internal notes. If the user requests a single file, place the notes in a clearly labeled internal appendix and identify that appendix before any customer use. Do not copy raw notes or transcripts into reusable assets or version control.

Read back both files. Check all eight template sections; every material commitment, owner, fee, date and approval; the distinction between agreed and proposed criteria; baseline comparability; approval sequencing; workstream boundaries; links; and unsigned fields. Verify every section needing input or further review has a specific bold uppercase callout, with inline markers on affected fields and cells. Ensure missing information is visible without treating it as a reason to abandon an otherwise useful draft. Confirm no account-specific material entered the skill or other reusable files.

Return clickable links to the memo and internal notes, plus the few decisions that block agreement. Drafting does not authorize sending, publishing, signing, changing CRM records, committing or pushing.
