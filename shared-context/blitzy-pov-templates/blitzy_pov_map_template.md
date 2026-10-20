# POV Mutual Action Plan

*Shared milestones, dates and responsibilities for the Proof of Value*

**Customer:** [Client Name]\
**Selected application / initiative:** [Name]\
**Blitzy POV Lead:** [Name]\
**Customer Technical Owner:** [Name]\
**Customer Executive Sponsor:** [Name]\
**POV Evaluation Memo:** [Link and agreed version]\
**POV start:** [Month D, YYYY]\
**Final readout:** [Month D, YYYY]\
**Last updated:** [Month D, YYYY]\
**Weekly checkpoint:** [Day/time/time zone or agreed asynchronous update]

## How to use this plan

Before the POV begins, both parties agree the milestones, expected completion dates and named owners below. Start each milestone as **Not started**, unless its completion or current progress has been confirmed. Update status throughout the engagement.

The Evaluation Memo defines scope, success criteria and measurement. This plan tracks when the agreed work and decisions will occur. Supporting evidence and final results will be recorded in the Project Guide and POV readout, with milestone references added to the progress notes as available.

Replace each role placeholder with a name. The Blitzy and customer columns identify the responsible contact on each side; the milestone wording identifies whose delivery or approval completes it. Use **Not applicable** only when both parties agree and record the reason. Dates are customer-specific commitments, not fixed week estimates. Environment setup and specification work may proceed in parallel after entry approval.

For existing codebases, ingestion and automatic Technical Specification generation are one process. The specification readout and customer acceptance are separate review milestones. Code generation also produces the Project Guide; configured environments enable build and runtime validation before PR delivery. The later milestones track review of those outputs and resolution of gaps. Greenfield projects do not require code ingestion: agree which repository preparation steps apply, use the agreed requirements as the starting point and adapt the specification reviews accordingly.

## Milestone plan

| Phase | Milestone / completion condition | Expected completion date | Status | Blitzy responsible party | Customer responsible party |
|---|---|---|---|---|---|
| Pre-kickoff | **P1 — Candidate and scope agreed.** Confirm the business outcome, selected application, inputs, target stack/architecture, validation approach and exclusions. | [Date] | Not started | [Name — POV Lead / AISC] | [Name — Technical Owner] |
| Pre-kickoff | **P2 — Baseline approved.** Both parties approve equivalent scope, baseline duration, measurement boundaries and acceleration target. | [Date] | Not started | [Name — POV Lead] | [Name — Baseline Approver] |
| Pre-kickoff | **P3 — Required authorizations confirmed.** Complete the security, access and evaluation terms required for this engagement. | [Date] | Not started | [Name — Account Lead] | [Name — Approval Coordinator] |
| Pre-kickoff | **P4 — Evaluation Memo signed and MAP agreed.** Confirm success criteria, sponsor, technical reviewers, dates and responsibilities. | [Date] | Not started | [Name — POV Lead] | [Name — Executive Sponsor / Technical Approver] |
| Pre-kickoff | **P5 — Input inventory confirmed.** Identify the approved repositories and source versions, or greenfield requirements and supporting materials, for setup during POV preparation. | [Date] | Not started | [Name — AISC] | [Name — Source / Requirements Owner] |
| Kickoff | **K1 — POV entry confirmed.** Review P1–P5, establish checkpoints and confirm the final readout date and escalation contacts. | [Date] | Not started | [Name — POV Lead] | [Name — Technical Owner] |
| POV — Preparation | **R1 — Source-control access verified.** Connect the agreed source-control system and verify access to the selected repositories, branches and supporting inputs; for greenfield work, confirm access to the agreed requirements. | [Date] | Not started | [Name — AISC] | [Name — Source-Control / Requirements Owner] |
| POV — Preparation | **R2 — Source-control repository set up for Blitzy ingestion.** Prepare the agreed repository or staging repository, including in-scope source, shared dependencies and supporting files; confirm the branch/version to ingest. Use an existing repository where suitable. | [Date] | Not started | [Name — AISC] | [Name — Source-Control / Engineering Owner] |
| POV — Preparation | **R3 — Code ingestion prompt prepared.** Define the ingestion scope, source versions, supporting context and exclusions in the prompt, and confirm alignment with the agreed input inventory. | [Date] | Not started | [Name — AISC] | [Name — Technical Owner] |
| POV — Execution | **X1 — Ingestion and Technical Specification delivered.** Run ingestion using the prepared prompt and share the automatically generated Technical Specification; confirm source coverage and identify material omissions for resolution. | [Date] | Not started | [Name — AISC] | [Name — Technical Owner] |
| POV — Execution | **X2 — Technical Specification readout completed.** Walk through Blitzy's understanding of the system with customer reviewers and capture corrections, questions and required follow-up. | [Date] | Not started | [Name — AISC] | [Name — Technical Reviewer] |
| POV — Execution | **X3 — Technical Specification validated by customer.** Resolve material corrections and record customer approval. | [Date] | Not started | [Name — AISC] | [Name — Technical Approver] |
| POV — Execution | **X4 — Environment ready and verified.** Confirm reproducible setup, toolchain, dependencies, build/run/test commands, required data and integration access or approved substitutes. | [Date] | Not started | [Name — AISC] | [Name — Environment Owner] |
| POV — Execution | **X5 — Build prompt and AAP prepared.** Capture the agreed target, scope, customer standards, validation plan and deliverables. | [Date] | Not started | [Name — AISC] | [Name — Technical Owner] |
| POV — Execution | **X6 — AAP jointly approved.** Both parties approve the plan; confirm spec validation and environment readiness before generation. | [Date] | Not started | [Name — AISC / POV Lead] | [Name — Technical Approver] |
| POV — Execution | **X7 — Generation run completed and PR / Project Guide delivered.** Execute the approved AAP, including automated validation in the configured environment; share the generated code, accompanying Project Guide and available validation results. Identify deviations or validation gaps for review. | [Date] | Not started | [Name — AISC] | [Name — Engineering Reviewer] |
| POV — Execution | **X8 — Build evidence reviewed and accepted.** Confirm the successful build results and reproducible instructions in the designated environment; resolve any build gaps or required reruns before acceptance. | [Date] | Not started | [Name — AISC] | [Name — Engineering Reviewer] |
| POV — Execution | **X9 — Test and functional validation review completed.** Review the generated test results against the agreed suite and parity scenarios; resolve failures or record open gaps and any additional checks, with data, environment and limitations. | [Date] | Not started | [Name — AISC] | [Name — QA / Functional Reviewer] |
| Evaluation | **E1 — Project Guide and delivery readout completed.** Review the delivered code, build/test evidence, AAP alignment, limitations and remaining human work with customer reviewers; capture findings for the final acceptance decision. | [Date] | Not started | [Name — AISC] | [Name — Technical Approver] |
| Evaluation | **E2 — Baseline comparison reviewed.** Both parties confirm actual elapsed time, agreed exclusions, equivalent scope and the acceleration calculation. | [Date] | Not started | [Name — POV Lead] | [Name — Baseline Approver] |
| Evaluation | **E3 — Final readout and technical acceptance decision.** Review every agreed success criterion and record it as met, not met, unverified or not applicable, with remaining actions. | [Date] | Not started | [Name — POV Lead / AISC] | [Name — Technical Approver] |
| Next-step decision | **N1 — Sponsor decision and next actions agreed.** Confirm whether to pursue a commercial engagement, resolve specified gaps or close the evaluation; name owners and dates. | [Date] | Not started | [Name — Account Lead] | [Name — Executive Sponsor] |

**Before ingestion:** P1–P5, K1, source-control/input access (R1), repository setup (R2) and the ingestion prompt (R3) must be complete. **Before generation:** customer spec validation (X3), verified environment readiness (X4) and joint AAP approval (X6) must be complete.

Completing a milestone means its stated work or decision occurred. It does not automatically mean a success criterion passed. For example, X9 can be complete with documented failures, and E3 can be complete with a decision that the POV did not meet the agreed criteria. A blocked build must not be marked complete as a validated build.

## Status definitions

| Status | Meaning |
|---|---|
| Not started | Work has not begun. |
| Scheduled | The activity or review has a confirmed date. |
| In progress | Work is underway and the expected completion date remains achievable. |
| At risk | Work can continue, but the expected completion date is threatened. |
| Blocked | A missing input, dependency or decision prevents progress. |
| Complete | The stated completion condition is satisfied, including any required approval. |
| Not applicable | Both parties have agreed the milestone does not apply and recorded why. |

## Progress notes and blockers

Complete this section during the POV. Leave it empty when agreeing the initial plan. Record actual completion dates and supporting references here so planned dates remain visible.

| Milestone ID | Update date | Actual completion date, if complete | Progress, blocker or decision needed | Next action, named owner and due date | Supporting reference |
|---|---|---|---|---|---|
| [ID] | [Date] | [Date / —] | [Update] | [Action — name — date] | [Link / pending] |

Escalation contacts: **Blitzy:** [Name]. **Customer:** [Name]. Escalate blockers at the next checkpoint, or earlier if they threaten an approval milestone or final readout.

## Agreed changes

Keep original expected dates in the milestone plan. If both parties approve a revised date, record it below with the impact and approvals. Changes affecting scope, criteria, target state or measurement also require updates to the Evaluation Memo, AAP or baseline, as applicable. An extension is not assumed.

| Date agreed | Milestone / document affected | Original commitment | Agreed revision and impact | Blitzy approver | Customer approver |
|---|---|---|---|---|---|
| [Date] | [ID / document] | [Original date or scope] | [New date or scope; effect on readout, validation and comparison] | [Name] | [Name] |

Any commercial kickoff, production deployment or broader training plan will be scheduled separately after the relevant agreement. Completion of this MAP does not authorize that additional work.
