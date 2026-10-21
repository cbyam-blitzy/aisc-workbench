---
name: blitzy-review-tech-spec
description: Review a technical specification and produce a plain-language briefing on what it says, why it matters, missing inputs, and who should confirm them. Use for tech specs, TV/POV spec outputs, and requests to summarize, validate, pressure-test, or identify gaps in a technical specification.
---

# Blitzy technical-spec review

Read and follow `shared_context/standards/file_naming_directives.md` when delivering files. Locate it in the working repository when this skill is loaded from a plugin cache.

Turn a long technical specification into a briefing that a deal or delivery lead can understand without reading the source: what the system is, how it behaves, what matters for migration or delivery, what remains unknown, and who needs to weigh in.

The specification already holds the evidence. The review adds interpretation. For every finding, explain the consequence for modernization, estimation, risk, or the customer conversation.

## Blitzy reference context

Unless the user restricts the review to the supplied specification, read `shared_context/platform/tech_spec.md` for the artifact's purpose and platform review workflow. Consult `ingestion_prompts.md` in that directory for missing domain context, exclusions, supported inputs or branch/spec inheritance, `environment_config.md` for build/test prerequisites, and `glossary.md` for unclear platform terms. The platform's targeted customer spot-check does not replace this skill's full-document review. Keep general guidance separate from facts stated in the supplied spec; do not infer complete source coverage or customer validation from the artifact's existence.

When the permitted review raises missing repositories, submodules, source versions or access, consult `shared_context/platform/project_setup.md`. Use `chat_with_code.md` in that directory when suggesting follow-up source exploration at the Tech spec step. Proposed chat queries do not independently verify findings, and source exploration cannot establish the customer's desired behavior.

## Inputs

- Use the named technical specification. If none is named, look in the supplied project materials.
- If the user limits the review to the spec, use nothing else. Otherwise, use permitted account context only to identify owners or avoid re-raising a resolved item; it never overrides the spec.
- Read `shared_context/standards/writing_style_guide.md` before writing. It is the current source of truth for Blitzy voice, structure, formatting, and claims.

Read the entire specification. Map its headings first, then read by section. Later sections often contain the most material dependencies and gaps. When the review permits parallel work, divide large specifications by top-level sections and verify each reported finding against the source.

For an active POV or technical validation, read `shared_context/pov/playbook.md` from the working repository. Tailor feedback to current-state accuracy, customer spec validation, the agreed forward-engineering target, parity approach, baseline, environment prerequisites and MAP. Include a compact assessment of applicable playbook criteria with evidence, status and the owner/decision that closes each gap. Distinguish criteria the spec supports from approvals and runtime results it cannot establish. Honor a spec-only review restriction and state that playbook alignment was not assessed. Do not substitute early-stage sales positioning for active evaluation readiness.

## Writing rules

- Lead with the point, then explain the consequence.
- Use plain language. Define jargon once and name an artifact only when it helps a reader act.
- Keep only scale-setting numbers and numbers a customer will need to verify. Do not turn the review into a citation dump.
- State certainty precisely: “the spec states,” “the spec implies,” or “the spec does not say.”
- Flag contradictions plainly. Do not resolve them by assumption.
- Write short explanatory paragraphs. Use lists and tables for gaps, questions, and ownership.

## Briefing structure

### 1. Short version

Open with a half-page executive summary: what the system is, three to five findings that matter most, readiness for the next step (generation, sizing, or cutover planning), and the largest blockers.

### 2. Section-by-section walkthrough

For every top-level section, write roughly 150–250 words covering:

- **Headline:** the main takeaway.
- **What it covers:** a short plain-language explanation with only essential scale numbers.
- **What it reveals and why it matters:** behaviors, dependencies, coupling, ordering, or failure modes and their delivery consequences.
- **What's missing and how to close it:** up to four specific gaps, each with the blocker, concrete evidence or decision that closes it, and the owner. Say “Nothing material” when applicable.
- **Who should confirm:** the best-fit persona, the question they should answer, and who else cares.

Skip a reference-only section unless its source base is thin, single-sourced, or otherwise material.

### 3. Themes across the spec

Synthesize three to six recurring architectural characteristics, risks, assumptions, and contradictions. This should add insight beyond the specification's own summary.

### 4. Missing inputs, ranked

Use one de-duplicated table with: missing input, why it matters, what closes it, owner, and priority (`Blocker`, `Important`, or `Nice to have`). Lead with the two or three requests that resolve the most blockers.

### 5. Who to ask what

Use a persona table with the confirmation each persona owns, two or three questions for them, and their related gaps. Adapt personas to known names only when account context is permitted.

| Persona | Confirms | Cares about |
| --- | --- | --- |
| Executive sponsor / VP Engineering | Business problem, scope, success criteria | Outcome, risk, timeline, cost |
| Enterprise / solution architect | Target architecture and integration topology | Standards and long-term coherence |
| Application / product owner | Features, rules, and priorities | Functional completeness and user impact |
| Business SME / data steward | Domain rules, data meaning, validation | Correct behavior and data quality |
| Lead developer | Legacy behavior and missing source | Migration difficulty and accuracy |
| ETL / data engineer | Pipeline logic, schedules, dependencies, volumes | Parity, ordering, recovery |
| Database engineer / DBA | Schemas, procedures, storage, sizing | Integrity, performance, cutover |
| Integration engineer | Interfaces and external contracts | Contract stability and ownership |
| Security / compliance architect | Access, secrets, encryption, audit | Controls and exceptions |
| QA / test lead | Test strategy and parity criteria | Evidence of equivalence |
| DevOps / platform engineer | CI/CD, environments, infrastructure as code | Delivery readiness and access |
| Cloud / infrastructure engineer | Runtime, networking, sizing, cost | Landing zone and quotas |
| SRE / operations / support | Monitoring, recovery, ownership | Operability and on-call burden |
| FinOps / procurement | Cost model and licensing | Spend and retirement planning |
| Program / delivery manager | Phasing and cross-workstream dependencies | Plan realism and blockers |
| Blitzy delivery / solutions engineer | Whether inputs can drive generation | Scope clarity and input gaps |

## Delivery

- Produce a readable briefing, not a data dump. Use clear headings, short paragraphs, and generous whitespace.
- If a shareable document type is available, use it; otherwise save Markdown alongside the supplied specification. Follow a user-requested format.
- In chat, give three or four lines naming the headline finding and blocker count.
- State what you did not independently verify.
- If the provided document is not a technical specification, say so and ask whether the user wants this structure adapted rather than forcing it.
