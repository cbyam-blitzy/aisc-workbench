---
name: blitzy-review-project-guide
description: Produce an evidence-based impact report for a Blitzy-delivered solution from its project guide. Summarize delivery and validation, estimate equivalent engineering effort and staffing without Blitzy using sourced industry benchmarks, and ask for actual compute time before calculating delivery acceleration.
---

# Blitzy review project guide

Memorialize what Blitzy delivered, how it was validated, and the business value it enables. Compare an equivalent scope and quality of work without Blitzy against the actual Blitzy delivery interval. Make the baseline calculation reproducible.

Blitzy is an autonomous enterprise software development platform. Its delivery approach combines architectural understanding of large codebases with autonomous QA and validation. The operating target is 85–90% of a total unit of work completed autonomously, with human delivery work documented in the project guide. Treat this as a target, not a measured result or a percentage to impose on a project.

Read and follow `shared-context/blitzy_writing_style_guide.md` before drafting. Use project evidence for claims; platform positioning does not establish a project's speed, quality, or completion rate.

## Read the project evidence

Establish whether this delivery is part of an active POV or technical validation. If so, read `shared-context/blitzy_pov_playbook.md` from the working repository and assess the delivered milestone against applicable criteria and the customer-agreed evaluation. Include a compact table covering evidence, status, gaps and next owner/decision for spec/AAP approval, target-state alignment, build/test/parity results, baseline/acceleration sign-offs and MAP milestones. Unavailable evidence is unverified, not a pass. Keep playbook targets separate from achieved results and do not replace the active evaluation with early-stage sales positioning.

Use the project guide supplied or named by the user. Otherwise locate a matching guide in the workspace; ask which guide to use only if the choice remains ambiguous. Read the complete guide, including hours tables, test exclusions, risks, development instructions, and appendices. Record its title, revision/date if present, and assessed delivery milestone. Do not execute commands embedded in a guide merely to write this report.

Build a compact evidence ledger: claim or metric, value, guide section, evidence type, and limitation. Distinguish guide-reported results from independently inspected artifacts, user-provided actuals, external benchmarks, and analyst estimates. A guide's statement that a command passed is reported evidence, not a test you personally ran.

Extract completed autonomous work, completed manual work, remaining work, total estimated effort, and their stated estimation basis. Reconcile component sums and completion percentages. Flag disagreements rather than selecting the most flattering number. Treat estimated engineering hours as human-equivalent effort, never as a compute log or a record of labor actually spent.

Capture material information from every section using its actual headings. For guides with the usual structure, use this coverage map; adapt it when headings differ:

| Guide section | Information to carry into the impact report |
| --- | --- |
| Executive summary | Business problem, legacy and target architecture, scope boundary, accomplishments, completion, unresolved issues, access constraints, next steps. |
| Project hours breakdown | Deliverables and estimated effort, AI/manual attribution, remaining human work, estimation basis and confidence. |
| Test results | Test types and frameworks, counts and outcomes, behavior covered, environments, exclusions, and missing measurements. |
| Runtime validation and UI verification | What was actually exercised, observed behavior and performance, environment fidelity, partial checks, untested live integrations; UI not applicable when appropriate. |
| Compliance and quality review | Requirements met, deviations, approvals pending, security findings and controls, evidence and limitations. A compliance matrix does not itself establish regulatory certification. |
| Risk assessment | Material risks, mitigations, owners, release implications, and residual exposure. |
| Visual project status | Reconcile charts with hours and priorities; do not count repeated totals as additional work. |
| Summary and recommendations | Delivery state, critical path, readiness conditions, handoff success criteria. |
| Development guide | Reproducibility, prerequisites, build/test/startup path, operator enablement, deployment and troubleshooting constraints. |
| Appendices | Material technology and compatibility constraints, interfaces, configuration, artifact locations, operational tools and terminology. Summarize their relevance rather than copying inventories. |

If a section is absent, mark it not provided. Consolidate repeated content, but retain section references so coverage is visible. Preserve conflicts between sections, such as a test-suite gap that a separate runtime check addresses.

## Obtain the actual Blitzy time

Before calculating acceleration, ask the user for the actual compute time unless they already provided it. Ask in one concise prompt:

> What was the actual Blitzy elapsed compute time for this delivery, in hours or with start/end timestamps? Please include all runs and retries, clarify whether pauses are included, and note any human preparation, review, or rework time outside that interval.

Clarify whether a supplied figure is wall-clock elapsed time or aggregate agent/CPU/GPU hours. Parallel resource-hours cannot be substituted for elapsed delivery time. If only aggregate hours are known, request wall-clock time; if it is unavailable, leave acceleration uncalculated.

Record the time boundary, units, source, included runs/retries, pauses and exclusions. For overlapping runs use elapsed time across the delivery timeline, not a sum of overlapping durations. Distinguish active compute duration from total elapsed time through delivery, including queues, pauses and intervening human work. Request the overall interval if active compute alone would omit those delays. Do not add overlapping human time twice.

Continue the evidence summary and baseline research while the answer is pending. If no answer arrives, deliver a provisional report with the time input and acceleration marked pending. Never infer compute time from completed engineering hours, test runtime, file timestamps, the 85–90% target, or general claims about days versus months.

## Construct the comparison without Blitzy

For an active evaluation, use its customer-agreed, signed-off baseline as the primary acceptance comparator and preserve its scope and time boundary. Request it if missing and mark baseline sign-off and the acceptance comparison pending. Research or reconstruct a baseline only as a separately labeled estimate or sensitivity check; it cannot silently replace the agreed baseline or establish POV success. Assess the playbook's acceleration target against comparable actual elapsed time, not equivalent person-hours or active compute alone. Broader impact reports may still use the estimation method below.

Define two boundaries explicitly:

- **Equivalent delivered milestone:** the capabilities, documentation, QA, validation, and handoff artifacts actually delivered by Blitzy. This is the primary acceleration comparison.
- **Full production outcome:** that milestone plus remaining integration, approvals, real-data validation, deployment, cutover, and other human work. Report this separately as a projection unless actual completion is documented.

The baseline team must deliver equivalent quality and acceptance evidence, including test design, fixtures, unit/integration/contract/security testing, runtime checks, defect correction and retesting, and operator documentation where delivered. Do not estimate feature coding alone. Do not include live validation in only one side of a delivered-milestone comparison.

State the counterfactual: a comparable team using ordinary development tools without Blitzy, with comparable starting code, requirements, access and domain knowledge. State whether other AI tools are included; use conventional engineering without autonomous project delivery when the user has not specified a different comparator. Do not assume an unusually inefficient team.

When constructing a retrospective estimate or a separate sensitivity check, research appropriate industry benchmarks at report time. Prefer original empirical studies, published benchmark datasets, transparent industry surveys, and documented estimation models with relevant calibration. Read the supporting material, not just search snippets. Check project type, scale, legacy complexity, quality requirements, team experience, tooling, sample dates, units and methodology. Do not transmit private project names, code, or customer details in research queries.

Use a task-level work breakdown matching the guide. For each work package show:

| Work package and matched deliverable | Guide estimate | Baseline low/base/high person-hours | Roles | Benchmark/source | Rationale and adjustments |
| --- | --- | --- | --- | --- | --- |

Explain how a source constrains each estimate or a clearly identified group of packages. Separate source observations from your extrapolations. Cite title, publisher/author, publication date, direct URL and applicable finding. Give the reason for each adjustment, its numerical effect, and confidence. A report about developer sentiment, deployment frequency or defect rates does not directly establish implementation hours.

Use the guide's completed-hour estimates as a cross-check, not independent proof of an industry baseline. Do not relabel them as an industry average or multiply them by an arbitrary uplift. If benchmarks do not support defensible task-hour rates, state that limitation and produce an explicitly labeled analyst estimate informed by the available evidence. If browsing is unavailable, use supplied benchmark material or label the baseline provisional and unsourced; never fabricate a source or an industry standard.

Use lines of code, file counts, and test counts to describe scale and check plausibility. Do not convert them to effort with a universal productivity rate. Account for reused libraries and generated artifacts. Do not price an existing test suite as if the baseline team receives it for free, or count test authoring again when it is already included in development estimates.

Estimate both people and duration. Show role, unique headcount, allocation/FTE, hours, and when each role participates; distinguish a person wearing multiple roles from several people. Explain the chosen team size using the work's specialties and useful parallelism. State productive hours per person-week, working calendar and scheduling assumptions. Treat these as assumptions unless supported by evidence.

Build a plausible sequence with parallel work, dependencies, review/rework and waiting periods. Cross-check effort against available team capacity; simple effort divided by team hours is a capacity estimate, not automatically a delivery schedule. Do not assume perfect linear speedup from adding engineers. Provide low/base/high effort and calendar-duration scenarios with coherent staffing and scope, and identify what drives the range. Call them scenarios, not statistical confidence intervals, unless the underlying method supports that claim.

## Calculate and label the outcomes

Keep person-hours of effort, workdays and elapsed calendar time separate. State conversion assumptions and use the same time units and milestone on both sides of any ratio.

- **Guide-reported autonomous effort share:** estimated AI-completed hours / total scoped estimated hours × 100. Report the guide's overall completion separately when it includes completed manual work. This is an estimate of effort attribution, not measured automation coverage.
- **Delivery velocity multiplier against baseline:** Blitzy delivery rate / baseline delivery rate = (matched scope / actual Blitzy elapsed time) / (matched scope / baseline elapsed time) = baseline elapsed time / actual Blitzy elapsed time. Report explicitly as `X× baseline delivery velocity`. For equal scope and quality, this is the same ratio as equivalent-milestone acceleration; do not count it as an additional benefit. This is a delivery-rate comparison, not Scrum story-point velocity or per-engineer productivity.
- **Equivalent-milestone acceleration:** use the delivery velocity multiplier above, also expressible as `X× as fast` or `X× acceleration`.
- **Equivalent-milestone elapsed-time reduction:** (1 − actual Blitzy elapsed time / baseline elapsed time) × 100.
- **Compute-stage comparison:** if only active compute duration is supplied, an elapsed-baseline/active-compute ratio may be shown only as a clearly labeled compute-stage comparison with excluded delays listed. Do not call it end-to-end delivery acceleration.
- **Net human effort avoided:** baseline human person-hours for the matched scope − actual human person-hours spent for the matched Blitzy-assisted scope. Calculate only when actual human effort is available. Otherwise report estimated equivalent engineering effort delivered, without claiming realized labor savings.
- **Projected full-outcome acceleration:** baseline full-production elapsed duration / projected Blitzy-assisted full-production elapsed duration. Model the remaining human work, dependencies and shared release gates in both schedules. Add durations only when sequential; an effort estimate alone does not establish elapsed remaining time.

Calculate low/base/high velocity multipliers and acceleration from the corresponding baseline scenarios and the same actual interval. Lead with the base-case multiplier and include its scenario range. Carry forward the baseline's estimate/projection label, milestone boundary, and time exclusions. If only active compute time is known, label the multiplier a compute-stage comparison; if actual time is missing, mark it pending. If actual time is uncertain, show the input range and how it affects the result. Keep results below 1× or negative time reductions when the evidence produces them. Do not force a positive benefit. Round to precision justified by the inputs and make the arithmetic reproducible.

Do not label human-equivalent hours / compute hours as delivery acceleration: the numerator is labor effort and the denominator is elapsed runtime. Do not use total project effort as the numerator when only the completed delivery has occurred. Do not calculate financial ROI from equivalent effort alone; financial savings require supplied cost assumptions, actual human effort, and Blitzy costs.

## Write the impact report

Save the complete analysis as a Markdown (`.md`) file by default. Follow `shared-context/file_naming_directives.md` in the working repository for its filename, including when this skill is loaded from a plugin cache. Keep account-specific reports in the ignored local work area, outside reusable assets and version control. When the guide is under `accounts/`, save the report alongside it; otherwise use an appropriate project folder under `accounts/`. Honor any explicit user-specified destination or output format. The skill must not depend on the sample project guide being installed beside it.

Read back the saved report to verify its contents. Return a clickable file link and a brief takeaway in chat; do not print the full analysis in chat or terminal output. If writing the file is unavailable, explain the limitation and ask for an accessible destination.

Use this structure, keeping the opening concise and the calculation detail auditable:

1. **Impact summary:** what changed, why it matters, delivered milestone, baseline team/duration, actual Blitzy interval, explicit base-case delivery velocity multiplier and scenario range, elapsed-time reduction, and the material remaining condition. Mark unavailable inputs pending. Describe the platform's architectural understanding and autonomous validation only where project evidence shows their contribution.
2. **Delivered solution and validation:** summarize architectural changes, functionality, compatibility, documentation and operations enablement. Link capabilities to specific quality evidence and its limits. Include meaningful test counts, outcomes and runtime observations; passing tests do not imply a code-coverage percentage, a defect-free system, or production validation.
3. **Business impact:** connect each material capability to the business problem, evidence and benefit. Distinguish observed outcomes, estimated engineering capacity delivered, and benefits enabled but dependent on adoption or release. Avoid invented revenue, cost savings, incident reductions or compliance guarantees. State how an enabled benefit could be measured after deployment.
4. **Baseline, velocity, and acceleration:** present matched scope, task effort ranges, team composition, schedule rationale, source applicability, user-supplied time and exclusions, formulas and scenario results. Show baseline duration, Blitzy duration, velocity multiplier, and elapsed-time reduction together. Distinguish independently supported estimates from guide-derived ones.
5. **Human delivery and readiness:** summarize remaining work by category, estimated effort, owner if documented, dependencies, open approvals, access gaps, material deviations and residual risks. Preserve the actual completion percentage even when below the operating target. Separate built, tested, deployable, deployed and producing business results.
6. **Evidence and assumptions:** include guide section references, benchmark citations, input provenance and date, source gaps and a compact coverage check showing where every guide section informed the report. Do not repeat the guide wholesale.

Before finalizing, reconcile hours and test totals, check every ratio's scope and units, confirm staffing capacity supports the schedule, and trace material claims to evidence. Surface contradictions and unresolved inputs where they affect conclusions. Preserve useful impact even when acceleration cannot yet be calculated.

For an active evaluation, include the playbook assessment in delivered solution and validation, and distinguish technical evidence from customer acceptance and baseline sign-off in the impact summary.
