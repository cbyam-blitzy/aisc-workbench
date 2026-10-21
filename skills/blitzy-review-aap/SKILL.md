---
name: blitzy-review-aap
description: Review an Agent Action Plan (AAP) against its build prompt and authoritative tech spec. Produce a human-readable briefing that identifies scope changes, directive coverage, factual conflicts, executability risks, and a gating verdict for each conflict. Use when the user asks to review, validate, sanity-check, or QA an AAP or agent_action_plan.md; asks whether it matches the build prompt or tech spec; asks whether the plan can run; or asks what must be fixed before a Blitzy build starts.
---

# AAP Reviewer

Read and follow `shared_context/standards/file_naming_directives.md` when delivering files. Locate it in the working repository when this skill is loaded from a plugin cache.

An Agent Action Plan is the contract a build will execute. It is generated
from a build prompt (what the user asked for) and grounded in a tech spec
(what is true about the system). Tell the user, in plain language, whether the
plan can run as written and, if not, exactly what must change first.

You are looking for conflicts: anywhere the AAP cannot be reconciled with the
build prompt or the tech spec, or quietly changes what the user asked for. For
every conflict, say whether it **gates** execution of the plan as stated. That
verdict is the most important output.

## The three documents and who wins

- **Build prompt:** The user's intent and directives: scope, format,
  exclusions, phasing, and rules. The AAP must honor it. If the AAP drops,
  softens, reverses, or extends a directive, that is a conflict even if the
  AAP version sounds reasonable.
- **AAP:** The document under review.
- **Tech spec:** The authoritative source of facts about the system: counts,
  components, behavior, what exists, and what is absent. Use it to settle
  factual disagreements, not to second-guess scope. If the AAP and build
  prompt disagree on a fact, the spec decides which is right. If the build
  prompt contradicts the spec, the spec still wins on the fact, but raise the
  conflict so the user can correct the prompt.

Directive questions—what to do, how much, and in what order—are settled by the
build prompt, not the spec. The spec cannot tell you what the user wanted.

## Blitzy reference context

Unless the user restricts the review to the three supplied documents, read `shared_context/platform/agent_action_plan.md` for completeness, custom-rule verification and refinement options. Consult `environment_config.md` in that directory for execution prerequisites, `tech_spec.md` for current-state context, and `glossary.md` for terminology as needed. Check selected custom rules by intent; use `shared_context/build_preparation/rule_templates/` and the task-matching template in `shared_context/build_preparation/prompt_templates/` only when relevant to supplied rules or a requested correction. Template defaults are not omitted customer directives. Keep platform guidance distinct from document conflicts. For recommended fixes, distinguish Refine, prompt regeneration and inline edits; preserve all existing AAP headings when proposing inline edits. A restriction to the three documents also excludes these platform references.

For permitted setup/readiness checks, consult `shared_context/platform/project_setup.md` on repository/submodule access and branch isolation. Read `chat_with_code.md` in that directory when recommending conversational help: at the AAP step, chat answers source questions and does not discuss or edit the plan. Use the AAP refinement paths for plan changes; an advisory Build Prompt Strength score does not replace this review or approval.

## Inputs

- The AAP, typically `agent_action_plan.md`; the build prompt, such as
  `build_prompt.md`; and the tech spec. If any is missing or ambiguous, ask
  which document to use before starting. A review against the wrong prompt is
  worse than none.
- If the user says to use only these documents, use nothing else. Otherwise,
  account context can help name owners, but it never overrides the three
  documents.

Read all three in full. For large documents, read by section. Where parallel
review is permitted, it can help to divide AAP section groups and separately
extract build-prompt directives. Verify every reported conflict directly
against the source documents. A false conflict wastes the user's time.

## What to check

For an active POV or technical validation, read the current
`shared_context/pov/playbook.md` from the working repository. Assess
the plan against its applicable criteria and the customer-agreed target,
baseline, success criteria, validation approach, environment access and MAP.
Identify missing evidence or approvals before generation. Keep playbook
readiness gaps distinct from prompt/spec conflicts; do not change the build
prompt's scope or assume customer sign-off. If the user limits the review to
the three documents, honor that limit and state that playbook alignment was
not assessed. Early-stage pre-sales positioning does not replace this review.

1. **Scope change from prompt to AAP.** Compare what the build prompt scopes
   in and out with what the AAP commits to. Capture every added, deferred,
   dropped, reinterpreted, tightened, or loosened item, even if it is sensible.
   State what the prompt says, what the AAP says, how the work changes, whether
   it crosses an explicit exclusion or constraint, and whether the user should
   accept it. A scope change that crosses an explicit exclusion or constraint
   is a conflict and needs a gating verdict.
2. **Directive coverage.** Extract every build-prompt directive: requirements,
   prohibitions, exclusions, format rules, phasing, volume or readability
   limits, and named deliverables. Mark each as honored, partly honored,
   dropped, contradicted, or extended beyond the prompt. Find work the AAP adds
   that the prompt never requested, especially work the prompt deferred or
   excluded.
3. **Fact fidelity.** Compare the AAP's claims about counts, components,
   versions, dependencies, and what exists or is absent with the tech spec.
   Flag stale numbers, invented components, steps that assume an unavailable
   script, library, environment, or network path, and plans that treat
   declared-but-unapplied items as operational.
4. **Internal consistency.** Check the AAP against itself: phases depending on
   outputs created later, inconsistent deliverable counts, steps without an
   owner or input, estimates that do not add up, and success criteria the
   stated steps cannot satisfy.
5. **Executability.** Determine whether an agent can carry out each step with
   the inputs provided. Flag missing inputs, access, approvals, decisions, and
   unbounded or untestable instructions.
6. **Prompt-to-spec conflicts.** Raise directives in the build prompt that
   rest on facts the tech spec contradicts. The user owns the prompt fix.

### Checklist completeness review

Unless the user restricts the review to the three supplied documents, read
`shared_context/artifact_review/aap_validation_checklist.md` from the
working repository, including when this skill is loaded from a plugin cache.
Use its current review areas to identify missing specificity in the prompt
and AAP. Consider every area, scaling review depth to the task's complexity
and risk; mark irrelevant areas not applicable with a brief reason.

For each applicable area, assess whether the supplied documents provide
enough detail to execute and validate the work. Record supporting evidence,
missing detail, and the clarification or document edit needed. Do not invent
technology versions, coverage thresholds, architecture choices, or other
requirements to fill gaps. Checklist questions guide review; they do not
override the prompt or spec or establish customer requirements.

Keep completeness gaps distinct from prompt/spec conflicts. Apply the gating
verdicts below to material gaps based on their execution impact; a missing
detail does not automatically block the build. If the review is restricted
to the three documents, skip this reference and state that checklist
alignment was not assessed.

## Gating verdicts

Give every conflict exactly one verdict and a one-sentence reason:

- **Gates execution:** Running the plan as written would produce the wrong
  output, violate an explicit directive, hit an impossible step, or depend on
  something that does not exist. Fix it before the plan runs.
- **Gates part of the plan:** Only a named phase or deliverable is affected;
  the rest can proceed. Name the affected part.
- **Does not gate:** The plan can run as stated. Explain the cosmetic,
  documentation, or downstream cost of leaving the conflict unresolved.
- **Needs a decision:** The right answer depends on a choice only the user or
  customer can make. Name the decision-maker and say whether work can proceed
  while waiting.

Be conservative about calling a conflict non-gating when an agent would act on
it literally. An agent follows what the plan says, not what it meant.

Before assigning verdicts, define what execution means and state it in the
verdict section. Usually distinguish the build (writing artifacts and running
local tests) from operation (running the result against real systems). A
conflict can leave the build untouched and still stop operation; say which
level it gates.

Treat a declared deviation from the prompt as a conflict even if the AAP
discloses it. Mark it **Needs a decision** and credit the plan for disclosing
it.

When the AAP cites legacy files, workbooks, or source outside the supplied
documents, say those citations are unverified. Limit conclusions to the AAP,
prompt, and spec for document conflicts; keep permitted checklist-completeness
and playbook-readiness assessments separate.

## How to write it

Follow `shared_context/standards/writing_style_guide.md` for the briefing's
voice, structure, formatting, and claims.

- Explain the why for every conflict: what the AAP says, what the prompt or
  spec says, why both cannot be true, and what happens at execution if left
  unresolved.
- Use plain language. Do not use line numbers, section IDs, or long quotes.
  Name the document to edit and the relevant area.
- Lead with the point in every section. State confidence precisely: “the spec
  states,” “the prompt says,” “the AAP implies,” or “I could not tell.” Never
  present an inference as a fact.
- Do not pad. If a section has no findings, say “No conflicts found.”

## Structure of the briefing

1. **Verdict.** State whether the plan can run as written; the number of
   conflicts that gate execution, gate part of the plan, need a decision, or do
   not gate; and the two or three fixes to make first.
2. **What changed in scope.** List or table every change from build prompt to
   AAP, marked Added, Deferred or dropped, Reinterpreted, or Tightened or
   loosened. Say why it matters and whether the user should accept it. State
   “No scope change” explicitly when applicable.
3. **Section-by-section walkthrough.** For each top-level AAP section, give a
   headline takeaway, summarize its commitment, state alignment with the
   build prompt and tech spec, and tag each conflict with its gating verdict.
   Target roughly 100–200 words per section.
4. **Directive check.** Use a compact table of build-prompt directives with a
   status and short note. Group related directives to keep it readable.
5. **Conflict register.** Rank conflicts, gating items first. Include the
   conflict, the AAP claim, the source of truth, which document is right and
   why, the gating verdict, what happens if unresolved, and the document to
   edit.
6. **Decisions needed.** List unresolved questions, options, and your
   recommended option with a reason.
7. **What I could not check.** State dependencies on information outside the
   three documents and claims that were not independently verified.

When checklist review is permitted, include a compact completeness table
covering the checklist's current areas: area, status (sufficient, needs
clarification, or not applicable), evidence or gap, and recommended fix or
decision owner. Cross-reference existing findings to avoid duplication.
Reflect material gaps and their gating verdicts in the opening verdict,
separately from the prompt/spec conflict counts.

For active evaluations where the review scope permits it, include a compact
playbook-alignment table: applicable criterion, evidence, status, gap and
owner/decision. Reflect material readiness gaps in the verdict without
mislabeling them as prompt/spec conflicts.

## Delivery

- Produce a readable document rather than a data dump. If the session offers a
  shareable page or document type, use it; otherwise save Markdown alongside
  the supplied files, for example `<aap-name>-review.md`. Follow a requested
  format when the user specifies one.
- In chat, give three or four lines: whether the plan can run, the number of
  gating conflicts, and the top fix.
- If the AAP, prompt, or spec is mismatched or from a different run, say so
  first and ask before continuing.
