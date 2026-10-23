---
name: blitzy-draft-pov-questionnaire
description: Draft or update a full customer-facing Blitzy POV questionnaire from an account evaluation and the shared template, with evidence-backed prefills and blank unknowns. Use to collect remaining evaluation inputs before drafting or refining an Evaluation Memo and MAP; not for drafting those agreements or reporting final results.
---

# Draft a POV questionnaire

Start with the full shared questionnaire and tailor it to the selected workstream using the account evaluation. Prefill established facts so the customer can focus on remaining decisions and inputs. Shorten the draft collaboratively when the user requests it. This collects information for the Evaluation Memo and Mutual Action Plan (MAP); it does not replace their agreements or authorize execution.

## Resolve inputs and references

Locate the working repository through the workspace and parent directories, including when loaded from a plugin cache. Follow applicable account instructions. Read the current files from that checkout:

- `shared_context/pov/templates/scoping_questionnaire.md`
- `shared_context/standards/writing_style_guide.md`
- `shared_context/standards/readability_directives.md`
- `shared_context/standards/file_naming_directives.md`
- `shared_context/pov/playbook.md` (filter embedded images and non-text payloads before displaying)

Use the requested account evaluation, or the latest relevant assessment after checking its scope, date and evidence cutoff. Read the supplied questionnaire, agreed scope, Evaluation Memo or MAP when relevant. Resolve the workstream from the request and evidence; ask only if competing choices would materially change the output. Preserve existing evaluation commitments rather than reopening positioning or combining different teams’ targets.

Start with the assessment rather than rerunning account discovery. Verify underlying evidence only for material ambiguity, disputed commitments or stale inputs. Use Wispr Flow as the authoritative meeting source when available; otherwise use the matching local account transcript and identify that fallback. If relying only on the assessment, disclose that limit in internal notes. Its recommendations are not customer agreements.

Read task-relevant platform references when the wording depends on them: `shared_context/platform/project_lifecycle/project_guide.md` for completed versus remaining work; `shared_context/build_preparation/ingestion_prompts.md` for contextual inputs and supported formats; `shared_context/build_preparation/generation_prompts.md` and `shared_context/platform/project_lifecycle/agent_action_plan.md` for forward-engineering intent and plan approval; `shared_context/build_preparation/setup/environment_config.md` for reproducibility. Documentation explains the workflow, not the account’s readiness or acceptance.

## Tailor the questions

The account evaluation determines the content, terminology, examples and technical depth for the selected workstream. Start with the full shared questionnaire by default, covering business outcomes, scope, target solution, functional acceptance, baseline, readiness, owners and approvals. Use the customer-facing title **POV Questionnaire**; account/workstream details belong in the metadata. Do not label outputs “abbreviated,” “compact” or “short-form” unless explicitly requested as a customer-facing title.

Before drafting, distinguish established facts, unresolved inputs and proposals using the evaluation and applicable agreements. Retain relevant questions and prefill their supported answers, including known target languages and decisions. Do not automatically reduce the questionnaire to only unanswered questions or a fixed short list. Exclude questions that genuinely concern another workstream, and add account-specific questions where the evaluation identifies material gaps. If no assessment is available, use supplied evidence and disclose the limitation rather than inventing requirements.

After delivering the full first draft, work with the user to remove or merge questions. Do not proactively trim settled questions merely because they can be prefilled. When shortening is requested, preserve material acceptance, baseline and readiness gaps and record the rationale for omissions in internal notes. The template’s question count is a starting structure, not a required count for every scope.

- Keep the decision and broader milestone questions in the full first draft. Combine them only when the user asks to shorten or merge them. Distinguish roadmap aspirations from the POV readout date or committed deadlines.
- Name the selected increment, inputs, dependencies, exclusions and sample limits. Prefill an evidenced target language in the target-solution question; retain missing versions, architecture/runtime constraints and compatibility details. A known language does not settle the stack.
- Ask where standards, representative code, tests, approved data and reference outputs are maintained. System or document names are sufficient at this stage; do not request internal links, exports, credentials or immediate access by default. Explain that relevant materials can later inform generation and validation. Their location alone is not ingested context, an executed test suite or evidence of compliance; do not imply native wiki/tool integration or automatic adherence.
- Ground acceptance in the actual decision and concerns recorded for this workstream. Ask what must meet the standards and pass agreed tests, acceptable remaining human effort, and blocking defects. When a completion threshold was discussed, retain its qualification and ask for its denominator and verification method. Any suggested definition is a proposal for confirmation, not an agreement. Never import a particular account’s percentage into the generic template or another account.
- Preserve the same-scope baseline question: elapsed duration, staffing, person-hours, normal tools, common start/finish boundaries, preparation/review/retry/rework/testing and separately identified waits. Historical backlog estimates, estate-wide test counts and compute time do not answer this question. Playbook acceleration targets remain proposals until accepted; do not invent agreement or achieved acceleration.
- Ask for sample-specific build/run/test setup, dependencies and validation limits. Historical platform details alone do not answer environment readiness. Confirm the future access/provisioning owner without treating security clearance or contract progress as authorization.
- Retain the optional supporting-documentation question in the full draft where implementation is in scope; prefill a settled answer rather than silently dropping the question. Tailor topics and review audience, but do not recast it as enterprise architecture strategy, language selection or additional implementation scope. Distinguish this requested documentation from the automatically generated specification and Project Guide.
- Ask for review/approval roles and capacity for specification validation, implementation-plan approval and the readout. A department leader is not automatically every evaluation approver. Keep commercial terms and source-release approvals with the appropriate sponsor/owners; record unresolved gates in internal notes even if omitted from the technical questionnaire.

Avoid addressing a single person by name; multiple team members may contribute. Use customer-facing language and keep candid account strategy and sourcing commentary out of the questionnaire. Do not copy memo/MAP loudcase markers or signature blocks into this lightweight information-gathering format.

## Prefill only responsive evidence

Use a simple `**Answer:**` line for each retained question. Prefill one concise line only when the evidence answers that question for the selected workstream and scope. Leave the line blank when no responsive evidence exists. Do not use a nearby fact, an inferred owner or general platform documentation to fill space.

For partial evidence, qualify the supported portion and identify the remaining detail briefly. Preserve historical/proposed status where material. Existing internal standards may be known to exist without their location being established. A team’s automated-test count does not establish sample test coverage. A reported target runtime does not establish reproducible build/test access. Do not fill customer answers with Blitzy proposals; place any proposal explicitly in the question for review.

In the full draft, keep relevant settled questions with supported prefills so the user can review coverage before trimming. When shortening is explicitly requested, merge or omit redundant questions while preserving unresolved technical details. Recheck numbering and cross-references after changes.

## Deliver and verify

Save the customer-facing questionnaire as Markdown in the ignored account folder using the current naming directives and a title such as `pov-scoping-questionnaire`, including the workstream where useful. Preserve the filename for updates and honor requested formats/destinations. Keep the reusable template and skill generic; never include the source account’s names, codebase details, dates, thresholds or commercial history.

Save separate concise internal drafting notes under the same naming convention. Include a question-to-source mapping, evaluation date/evidence cutoff, any underlying sources checked, omissions/merges with their rationale, and material unresolved scope/approval/measurement issues with known decision owners. Put citations in a final **Appendix — Sources and evidence** in those notes, outside the customer-facing questionnaire. Do not silently create an Evaluation Memo, MAP or account reassessment.

Read back both outputs. Check that each retained or added question addresses a material account-specific input or decision, omissions are justified by the evaluation, the first draft covers the full applicable questionnaire unless shortening was requested, questions are clear and relevant, every prefill is responsive and supported, unknowns are blank, target/workstream boundaries are preserved, optional documentation has not expanded build scope, and internal-resource requests match the current collection stage. Check numbering, cross-references and filenames. Ensure no source text or private details entered reusable files.

Return links to the questionnaire and internal notes, plus only material open decisions. Drafting does not authorize sending, publishing, changing external records, provisioning, ingesting customer source, committing or pushing.
