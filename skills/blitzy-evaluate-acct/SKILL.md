---
name: blitzy-evaluate-acct
description: Evaluate a Blitzy pre-sales account from its meeting history and create an evidence-based memo covering discussion threads, stakeholder goals, adoption readiness, evaluation questions, commercial status, and next steps. Use for account strategy, reverse engineering POV planning, or positioning a paid adoption pilot; not for a single-call recap or technical deliverable audit.
---

# Blitzy account evaluation

Create an internal account memo that explains what each stakeholder wants, how the discussions connect, and what evidence and decisions could support adoption of Blitzy across software initiatives. Apply the shared guidance for each workstream's engagement stage while preserving the customer's actual scope, commitments and commercial history.

## Establish scope and sources

Resolve the account from the request and the workspace. Ask only if the account or requested scope remains ambiguous. Follow account-specific instructions and use an existing account memo when the user asks to update one.

Read and follow the repository's current shared guidance before drafting. These files are the source of truth for writing, positioning and file naming; keep their rules in shared context rather than duplicating them in this skill:

- `shared-context/blitzy_writing_style_guide.md`
- `shared-context/file_naming_directives.md`

Establish each workstream's stage using the engagement-stage rules in `AGENTS.md`. For early positioning, read `shared-context/blitzy_presales_positioning_directives.md`. For active POV/technical validation work, read `shared-context/blitzy_pov_playbook.md`. Read both when the account spans both stages, keeping their assessments separate. Use `shared-context/blitzy_security_faqs.md` only when a Blitzy security question is relevant; preserve its qualifications and unconfirmed items.

Locate these in the working repository when the installed skill is in a plugin cache. Do not substitute an embedded style or positioning snapshot. If a required guide cannot be found, identify that gap and distinguish a provisional account assessment from a completed review against the missing guidance.

Use Wispr Flow MCP meeting context when available. When the user names local transcripts, use those; otherwise use `accounts/<account>/transcripts/` as the fallback for meetings whose Wispr notes are unavailable. Identify the actual source. Do not require an unavailable connector when the supplied local evidence is sufficient.

Build a dated inventory of relevant meetings and supporting account material. Read substantive passages in context, including the end of each relevant discussion; use keyword search to locate passages, not as a substitute for reading them. Cover the evolution of each material thread rather than relying only on the latest call. Use participant lists to resolve names. Do not browse public sources for private account context or transmit customer details in research queries.

Track a compact working evidence ledger: date, speaker, initiative or team, claim or commitment, source location, and any later qualification. Keep these distinctions clear:

- Customer statements and recorded commitments.
- Blitzy proposals and descriptions of capabilities.
- Analyst interpretations and recommended actions.
- Missing or unresolved decisions.

Resolve changes chronologically where the later statement clearly supersedes the earlier one. Preserve disagreements and scope uncertainty when it does not. Do not infer funding, authority, pricing, acceptance or deployment from enthusiasm, a job title, security clearance or MSA negotiation.

## Build the account assessment

Preserve the technical needs of individual teams rather than combining them into one migration or treating one team's target architecture as an account-wide decision.

Organize the material into the discussion threads the evidence supports. Do not force a fixed number or copy stakeholders, initiatives or architecture from another account. For each thread, capture:

1. **Discussion so far:** the need, business consequence, decisions, changes over time and unresolved issue, with dated source references.
2. **Questions to answer:** specific questions for reverse engineering, discovery or implementation, as appropriate to the thread.
3. **Evidence and decision:** the artifact or observation needed, the decision it supports, and the person or role who should review it. Mark proposed reviewers as proposals.
4. **Adoption relevance:** how the thread could improve planning, coordination, implementation, validation or reuse across subsequent initiatives.

Choose questions that can change a decision. Link system understanding to an actual business request, architecture choice, interface dependency, release sequence or acceptance requirement. Separate current behavior from desired behavior; code cannot establish customer intent or business priority by itself.

Respect teams' accounts of what already works. Do not invent poor documentation, broken QA, staffing shortages or resistance to change to strengthen the positioning. Where stakeholders disagree about the bottleneck, propose a way to test the competing explanations.

## Apply guidance for the engagement stage

For early positioning, evaluate the relevant workstreams against `shared-context/blitzy_presales_positioning_directives.md` as read for this task. For each directive, identify the relevant account evidence, an unresolved question or mismatch, and any recommended adjustment. Refer to the current directive number or heading so the review remains traceable when the shared guidance changes.

Use this assessment to shape the recommended engagement and next conversation. Distinguish the position supported by customer discussions from the position recommended by the guidance. If they differ, explain the gap and the decision needed; do not rewrite customer commitments to make them fit. Do not reproduce the directive list or maintain a second positioning policy here.

For an active POV or technical validation, assess progress and gaps against the playbook and the customer-agreed scope, success criteria, signed-off baseline, target state, spec/AAP reviews, environment access, validation evidence and MAP. Record each applicable criterion as met, unmet, unverified or not applicable, with evidence and the next owner/decision. Flag differences between the playbook and the agreed evaluation for resolution rather than changing the commitment. Keep expansion recommendations separate from the active evaluation's deliverables and acceptance decision.

## Design evidence and measures

For each initial initiative, connect the business outcome to required inputs, a useful artifact, reviewers and a decision. Include representative shared dependencies when the decision requires them. Match conclusions to the supplied source coverage; isolated samples cannot establish estate-wide understanding.

Distinguish what a reverse engineering activity can establish from what requires implementation or production evidence:

| Analysis can assess | Implementation or production evidence must assess |
| --- | --- |
| Accuracy of current behavior and dependency findings | Functional parity and maintainability of generated changes |
| Proposed architecture, interfaces and release sequence | Runtime performance, correctness and resilience |
| Validation plan and environment prerequisites | Tests actually executed, defects corrected and release acceptance |
| Usefulness of findings for scope and requirements | Complete delivery interval and actual human effort |
| Identified security or dependency concerns | Successful remediation and operational outcomes |
| Ability to review and reuse context on another question | Sustainable adoption across successive initiatives |

Derive measures from the stage-appropriate shared guidance and the account's agreed outcomes. For an active evaluation, preserve its agreed baseline and measurement boundary; identify missing sign-offs or changes needed. Keep person-hours separate from elapsed time; analysis findings alone do not establish delivery acceleration, labor savings or ROI.

Separate actions already committed on a call from newly proposed actions. If an owner is unknown, mark the role or owner to confirm rather than assigning a person by inference.

## Write and deliver the memo

Save a Markdown memo by default under the account's ignored local folder. Follow `shared-context/file_naming_directives.md` for its filename. Honor an explicitly requested destination or format. Do not put account names, source excerpts or deliverables into reusable skill assets or version control.

Use a structure appropriate to the account, normally:

1. **Recommended direction and immediate decision.** State the business outcome, current position, recommended engagement and material condition.
2. **Sponsor discovery and readiness.** Distinguish known sponsorship, authority and participation from what needs confirmation.
3. **Priority initiatives and the path to adoption.** Preserve each team's goals, evidence, open questions and connection to adoption.
4. **Proposed engagement and operating model.** Define initial initiatives, minimum process changes, bounded evaluation if needed, artifacts and measures.
5. **Next conversation and actions.** Give the sponsor decision and proposed or committed owners.
6. **Stage-specific review.** For early positioning, map every shared directive to account evidence, gaps and recommended adjustments. For active POV/technical validation, map applicable playbook criteria and agreed evaluation milestones to evidence, status and next decisions. Separate these reviews for mixed-stage accounts; do not manufacture a numeric readiness score.
7. **Source references.** Link meetings or local files with dates and timestamps or section locations. Keep analysis recommendations distinct from customer commitments.

Keep the opening concise and the question bank proportional to the decisions at hand. Avoid repeating the same qualification across sections. Write the memo for internal account and solutions planning unless the user specifies a customer-facing audience; exclude candid internal commentary from customer-facing material.

Read back the saved memo. Verify material claims and commitments against their sources, links, chronology, reviewer attribution and the analysis/implementation boundary. Check recommendations against the stage-appropriate shared guidance and the customer's existing commitments. Confirm that reusable changes contain no customer material.

Return a clickable memo link and the main strategic takeaway. Do not print the full memo in chat. Do not send messages, change CRM records, publish, commit or push merely because an account evaluation was requested.
