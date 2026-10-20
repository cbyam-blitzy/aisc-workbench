# POV Evaluation Memo

*Agreed scope, success criteria and evaluation plan*

Prepared for: **[Client Name]**\
Prepared by: **[Blitzy POV Lead]**\
Agreement date: **[Date]**\
Version: **[Version]**

## 1. Purpose and goals

This memo records the agreement between [Client Name] and Blitzy on the work included in the Proof of Value (POV), how success will be measured, each party's responsibilities and the evaluation timeline.

Both parties complete and sign this memo before the POV begins. All fields capture decisions, owners and planned dates agreed at entry. Blitzy will document execution evidence and results separately in the Project Guide and final POV readout; specification and AAP approvals will be recorded when those deliverables are reviewed.

The POV will demonstrate two capabilities within the agreed scope:

1. **Understand the system and its requirements.** For an existing application, map its structure, behavior and dependencies. For greenfield work, establish an accurate specification from the supplied requirements.
2. **Plan and execute the agreed change.** Turn the requested outcome into a reviewed implementation plan, then execute it autonomously and deliver code with evidence of build, test and functional results.

The POV evaluates a defined increment. Production deployment, operational acceptance and completion of the broader roadmap are excluded unless explicitly included below. These limits do not reduce the agreed build, test or functional acceptance requirements.

**Evaluation fee:** [Agreed amount and currency; enter $0 if agreed]. Any subsequent commercial engagement will be agreed separately.

## 2. Agreed scope and target outcome

Both parties complete and approve this section before ingestion begins. Supporting documents may be linked by title and version.

| Item | Agreement |
|---|---|
| Business outcome | [Problem to address and the useful outcome this evaluation will demonstrate] |
| Selected application and inputs | [Application; repositories, branches and commit IDs; supporting documents, or greenfield requirements] |
| Work included | [Specific conversion, feature, refactor or other change; components and interfaces included] |
| Target stack and architecture | [Language, framework and versions; architecture pattern; required scaffolding and customer standards] |
| Functional acceptance | [Behaviors to preserve or introduce; representative scenarios; expected results and tolerances] |
| Validation environment and dependencies | [Build/runtime environment; database, API and third-party access; approved mocks or stubs and their limits] |
| Test suite and data | [Existing and new tests; test commands; fixtures/data sources; expected results; traceability to requirements] |
| Exclusions and limitations | [Excluded components, behaviors, integrations, production activities and validation limits] |
| Broader roadmap | [How this increment supports the next project or modernization decision] |

Deliverables are the Technical Specification, approved Agent Action Plan (AAP), generated source code and build instructions, and a Project Guide containing validation results, deviations, limitations and remaining work. Record any additional or excluded deliverables here: **[Details / none]**.

For modernization, parity means preservation of the agreed behaviors under the defined scenarios and data. Passing these checks does not establish equivalence for untested behavior or environments.

## 3. Baseline and acceleration measurement

Before ingestion, both parties approve an estimate of the time required to deliver equivalent scope and validation without Blitzy. The estimate reflects the customer's normal team, tools, starting materials and access. Record other AI tools included in that approach.

| Measurement item | Agreement |
|---|---|
| Baseline elapsed duration | [Duration and units] |
| Baseline basis | [Work breakdown or comparable delivery; team capacity, tools, dependencies and scheduling assumptions] |
| Matched starting point | [Exact event and prerequisites from which both approaches are measured] |
| Matched completion point | [Delivery milestone and required acceptance evidence for both approaches] |
| Time included | [Ingestion/analysis, planning, generation, reviews, all runs/retries, rework and validation, as applicable to the agreed boundary] |
| Waiting and exclusions | [Treatment of customer response time, queues, pauses and external dependencies; any agreed exclusions on either side] |
| Approvals | [Customer baseline approver, Blitzy approver and approval dates] |

**Acceleration = approved baseline elapsed duration ÷ actual Blitzy elapsed duration.** Both durations must use the same units and equivalent scope, quality and completion boundaries. The success target is **at least 5×**: Blitzy completes the matched work in no more than one-fifth of the approved baseline duration.

During the POV, Blitzy will track human person-hours separately from elapsed time and report the total evaluation interval and agreed exclusions in the final readout. Aggregate agent-hours and active compute time alone will not establish delivery acceleration. This memo approves the baseline and measurement method; actual timing and the resulting comparison will be recorded separately after execution.

## 4. Readiness and approval milestones

The parties agree now to the following approval sequence. Approvals for deliverables produced during the POV will be recorded separately at the relevant milestone.

| Milestone | Requirements to satisfy at that milestone |
|---|---|
| **Before ingestion** | Named executive sponsor and accountable technical owner; approved scope, target state, validation approach, baseline and success criteria; authorized source/requirements access; agreed Mutual Action Plan (MAP). |
| **Before code generation** | Customer validation of the Technical Specification; joint review and written approval of the AAP; verified environment access and reproducible setup sufficient to build and validate the selected work. |

Environment readiness includes the required toolchain and versions, dependency access, configuration, build/run/test commands and initialization steps. Where validation requires databases, APIs or external services, confirm access or agreed substitutes and document the resulting limitations. Reference secrets through the agreed secure process; do not place credential values in this memo.

**Environment setup plan:** [Required access, responsible owner and planned readiness date; reference existing setup instructions if available].\
**Customer technical owner:** [Name]. **Blitzy technical owner:** [Name].

If a prerequisite is missing, both parties record the blocker, owner and resolution date before proceeding through the affected milestone.

## 5. Agreed success criteria and validation method

The parties agree to assess success using the criteria and evidence below. Confirm applicability and name each customer reviewer before signing. Record any agreed exception and its rationale here: **[Exceptions / none]**. Blitzy will supply the required evidence during the POV; no results or evidence links are required to complete this memo.

| Success criterion | Acceptance requirement | Evidence Blitzy will provide | Customer reviewer |
|---|---|---|---|
| **Inputs ingested** | The agreed source or requirements are ingested. Material omissions are resolved or reflected in an approved scope revision. | Input manifest and ingestion record. | [Name/role] |
| **Technical Specification validated** | The customer confirms the specification accurately describes the in-scope system or requirements; material corrections are resolved. | Technical Specification and record of customer validation. | [Name/role] |
| **Approved AAP followed** | Both parties approve the AAP before generation. Output follows its scope, target stack, architecture, scaffolding and standards. Changes are jointly approved. | AAP, joint approval record and deliverable alignment review. | [Name/role] |
| **Code builds** | Delivered code builds successfully in the designated evaluation environment using the agreed instructions. | Delivered code version, reproducible build instructions and build results. | [Name/role] |
| **Tests and functional checks pass** | All tests in the agreed suite pass, including the defined functional/parity checks. Results identify data, environment, coverage limits and any approved exclusions. | Test results and mapping to agreed requirements and scenarios. | [Name/role] |
| **Acceleration achieved** | The measured elapsed duration meets the 5× target against the approved, equivalent baseline. Both parties confirm the measurement and result. | Actual delivery timeline, calculation against the baseline in this memo and measurement confirmation. | [Name/role] |

The Project Guide will bring this evidence together and identify remaining human work. A test count alone does not establish functional coverage, and a successful build does not establish production readiness.

## 6. Working model, responsibilities and timeline

Blitzy leads preparation, prompting and execution during the POV. The customer supplies domain knowledge and access, validates the specification, reviews and approves the AAP with Blitzy, and evaluates the delivered evidence. Named reviewers must be available at the agreed milestones.

Both parties maintain a MAP with dates, owners, dependencies and the final readout. Weekly progress checkpoints supplement the kickoff, approval milestones and final review; they may be handled asynchronously when both parties agree.

**Evaluation start:** [Date]. **Final readout:** [Date]. **MAP:** [Link/version].

| Milestone | Blitzy responsibility | Customer responsibility | Agreed date |
|---|---|---|---|
| Entry and kickoff | Confirm scope, baseline, criteria and input requirements | Confirm sponsor, technical owner, reviewers and approved inputs | [Date] |
| Ingestion and specification | Ingest agreed inputs; deliver specification; resolve findings | Validate specification accuracy and clarify business requirements | [Date] |
| Environment and AAP approval | Verify build/test setup; prepare prompt and AAP; lead joint review | Provide required access, standards and data; approve AAP | [Date] |
| Generation and validation | Execute approved plan; build and test; document results and rework | Resolve agreed questions and review material deviations | [Date] |
| Final readout | Deliver Project Guide and evidence; present criterion-by-criterion results | Review evidence, record acceptance and agree next decision | [Date] |

Changes to scope, target state, tests or measurement boundaries require written agreement and updates to the affected memo, AAP, baseline and MAP. Neither party changes acceptance criteria retrospectively without recording the change and its effect on comparability.

Delays on either side reduce the time remaining in the agreed window. Record the impact and jointly agree recovery actions or revised scope/dates; an extension is not assumed. Retain the original and revised measurement records.

## 7. Final evaluation and next decision

At the final readout, both parties will record each criterion as **met, not met, unverified or not applicable** in a separate results summary, with evidence and any remaining actions. The POV will be successful when all applicable criteria agreed in this memo are met. The designated customer technical approver will confirm technical acceptance; the executive sponsor will review the outcome and next investment decision.

If criteria remain unmet or unverified, record the evidence needed, responsible owner and agreed next step. Completion of the calendar window alone does not establish success.

On successful completion, both parties intend to discuss the broader commercial engagement and its scope, support and terms. This intent does not itself commit either party to a purchase or authorize additional work.

## 8. Agreement and signatures

By signing, both parties confirm the scope, baseline, success criteria, responsibilities and timeline recorded in this memo and its identified attachments. Signature at entry does not establish that the POV has passed; final results are recorded separately.

| Role | Name and title | Signature | Date |
|---|---|---|---|
| Blitzy POV Lead | [Name/title] | [Signature] | [Date] |
| Customer Executive Sponsor | [Name/title] | [Signature] | [Date] |
| Customer Technical Approver | [Name/title] | [Signature] | [Date] |

**Pre-POV attachments agreed at signing:** [Existing scope/validation plan, baseline worksheet, MAP and setup instructions, with versions; enter none where included in this memo]. Deliverables to be produced during the POV are listed in Section 2 and are not attachments required at signing.
