---
title: "Blitzy AI-DLC Positioning Playbook"
type: synthesis
tags: [playbook, sales-enablement, ai-dlc, positioning, enterprise-sales]
sources: []
created: 2026-10-21
updated: 2026-10-23
---

# Blitzy AI-DLC Positioning Playbook

Last updated: 2026-10-23. Refresh when positioning, discovery practices,
product guidance or supporting evidence changes.

## How to use and maintain this playbook

The [positioning directives](positioning_directives.md) establish the rules;
this playbook helps apply them. Use relevant sections for discovery, talk
tracks, objection handling, demo preparation and adoption-pilot design.
Read the current working checkout when needed; the whole playbook is not
required reading for every skill.

Use platform documentation for capabilities, qualified internal security
guidance for security answers, and account evidence for needs, commitments
and measured results. This synthesis does not independently verify its
claims. Confirm supporting evidence before reusing numerical proof points,
architectural or competitive claims, or promises of correctness. Pilot
patterns and qualification thresholds are examples to adapt, not agreed
terms or mandatory acceptance criteria. For an active POV or technical
validation, the [POV playbook](../pov/playbook.md) and customer-agreed
evaluation remain the applicable guidance. Surface conflicts for resolution.

Maintain this canonical file in place as new guidance becomes available.
Update the `updated` metadata and visible revision date on material edits,
and record supporting sources and verification limits in a final
**Appendix — Sources and evidence** when available. Keep private source
material in the ignored account workspace. Update the directives when a
positioning rule changes; keep practical examples here and link to them
rather than copying them into skills or creating parallel playbook copies.

**Audience:** AI solutions consultants running discovery, demos and pilot design with enterprise engineering and technology leaders.

**Purpose:** position Blitzy as the platform that makes an AI-driven development lifecycle real inside a large enterprise, because it produces validated software at scale on codebases other tools cannot hold in their heads.

---

## 1. The position in one paragraph

Enterprises have accepted that software development is being reorganized around AI. The open question is no longer whether to adopt it. It is how to adopt it without losing control of correctness, security and architecture across millions of lines of code. In an AI-driven lifecycle, AI drafts the plan and does the work, and humans approve at defined checkpoints. That model only works if the AI understands the whole system, and if what it produces has been proven correct before a human is asked to approve it. Blitzy is built for exactly that: it builds a deep, queryable understanding of the entire estate, plans before it acts, validates continuously and exhaustively, and hands humans a reviewable result instead of a pile of suggestions.

**The sentence to remember:** Blitzy is the human-in-the-lead platform that turns years of roadmap into quarters of validated code, at the scale of the whole enterprise.

---

## 2. Why now: the enterprise trends that frame the conversation

Open with these trends, and ask which ones the prospect is feeling. They create the "why change" before any product talk.

1. **AI is moving from assistant to driver.** The pattern is shifting from a developer asking for help to AI initiating work while humans approve. Large regulated institutions already report production code that no developer touched directly.
2. **Coding is one of the easiest places to get AI return.** Software is procedural, step-by-step and well documented, and process knowledge can be reverse-engineered from code. That is why development is where many leaders are putting AI first.
3. **Demand for technology outruns supply.** Productivity gains show up as faster time-to-market, in-house builds that replace some purchased software, or reduced development spend. Leaders are funding AI work from those savings.
4. **Build-vs-buy is shifting.** Software licensing costs keep rising while AI makes building cheaper. Enterprises are re-opening "buy" decisions and asking how easily they could exit a vendor.
5. **Trust and risk outrank speed.** CIOs and CTOs are tired and risk-focused. Their main fear is the hidden risk in their own estate: vulnerabilities, unmaintained code, systems nobody fully understands. Governance is now a competitive position, not a tax.
6. **Multi-model is the norm.** Serious enterprises do not expect one winning model. They are routing work across providers, open-weight models and purpose-built models by task, cost and control.
7. **Pilots stall; process change sticks.** Short proofs of value prove a narrow thing and then die. Organizations that change how work gets done are the ones that scale.

**How to use this:** pick the two or three trends that match what the prospect has told you, and tie the rest of the conversation to them.

---

## 3. The AI-DLC in ninety seconds, and where Blitzy fits

An AI-driven development lifecycle replaces "Agile plus a copilot" with a redesign built around AI. The principles worth knowing cold:

- **Reverse the direction of the conversation.** Humans state the intent; AI proposes the plan and the work; humans approve.
- **Plan, validate, execute, recursively.** AI drafts a plan, a human reviews it, and each step is decomposed further under continued oversight.
- **Persistent context.** Artifacts stay linked so AI keeps backward and forward traceability across the lifecycle.
- **Humans stay accountable for validation.** The method is realistic about AI limits.
- **Aimed at complex systems.** Multi-team, regulated, high-architectural-complexity environments are the target. Simple systems are not.
- **Fewer stages, more flow.** Human approval points are placed where they prune the most downstream waste.

### Mapping to the lifecycle phases

| AI-DLC phase | What the method asks for | Where Blitzy is strong | Be honest about |
|---|---|---|---|
| **Inception** (intent to units) | AI decomposes intent into stories, requirements and units; humans refine | Technical specification generated from the existing code; intent supplied as prompts, requirements and org rules | Blitzy works from enterprise-supplied intent. It does not replace the stakeholder workshop that produces it |
| **Brownfield modeling** | AI elevates the existing codebase into reviewable models | The knowledge graph and technical specification of the whole estate: structure, dependencies, business rules, cross-repo relationships | This is the most differentiated part; lean in |
| **Construction** (design, code, test) | AI designs, writes code and tests; humans validate | Back-brief plan reviewed with the customer, then long-running autonomous development with continuous validation, ending in a pull request and project guide | Humans approve the plan and the PR; remaining work (typically under 20%) is handed back with estimated human hours |
| **Operations** (deploy, observe, respond) | AI monitors telemetry and proposes remediation | Not the core. Blitzy works on source code, not production data | Do not claim incident response or runtime telemetry; position as complementary to existing operations tooling |

**Message:** Blitzy covers the part of the lifecycle where enterprises are most stuck: understanding a very large existing estate and changing it safely at scale. It plugs into the rest.

---

## 4. The technical differentiators, translated into buyer value

The theme is **validated software at scale**. Each differentiator exists to make that sentence true.

### 4.1 Whole-estate understanding (infinite code context)

- **What it is:** at onboarding, Blitzy builds a hybrid vector and graph knowledge graph of files, modules, services, dependencies, cross-repo relationships and patterns. It then injects only the context each step needs, prunes for relevance, and shares context between agents.
- **Why it matters:** every model has an effective context window much smaller than advertised, and quality degrades as it fills. Blitzy keeps each agent inside its measured limits and uses the graph as a global map.
- **Scale cues:** typical customers run 1M to 20M lines of code, and the platform supports far more. Onboarding takes roughly one to two days of compute.
- **Buyer translation:** "Changes that touch dozens of repos stop being a coordination problem, because the system already knows what is connected."
- **Contrast:** assistant-class tools work at file level, and task-level agents lose coherence when a change propagates widely.

### 4.2 Validation as architecture

- **What it is:** compile and test checks every time a file is touched, the full existing test suite plus newly generated tests, true end-to-end testing including UI, API and runtime, and algorithms that prevent circular dependencies across millions of lines. A failed step recruits another agent; repeated failure escalates to a human guide.
- **The ratio that tells the story:** in a typical run, only about 1% of time is code generation. About half is end-to-end validation. Blitzy is a validation engine that happens to generate code.
- **Two kinds of correctness:** verifiable correctness (does it compile, run and pass tests) is machine-checkable. Intent correctness (does it reflect this company's constraints and preferences) needs enterprise context, which Blitzy captures through requirements, org rules and learning from human edits.
- **Buyer translation:** "You approve a result that has already been proven, not a draft that still has to be debugged."

### 4.3 Plan before execution

- **What it is:** a plan is produced and reviewed with the customer before long-running autonomous work starts. Specifications are frontloaded and signed off early, which keeps the plan consistent through delivery.
- **Why it matters:** AI is probabilistic and enterprise software expects determinism. The plan is the mechanism that keeps autonomous work as close to deterministic as possible, anchors traceability, and gives humans a real approval point.
- **Buyer translation:** "Nothing large runs until your architects have signed the plan."

### 4.4 Model fusion and dynamic recruitment

- **What it is:** Blitzy uses models from several providers and chooses the best agent per micro-task. If attempts keep failing, it can design a new agent on demand.
- **Why it matters:** frontier model gains help Blitzy rather than threatening it, because the models are inputs to the platform. The durable value is the harness around them: orchestration, context, validation.
- **Buyer translation:** "You are not betting on one model. You are buying the system that gets the best out of all of them."

### 4.5 Enterprise software development memory

- **What it is:** each node in the knowledge graph records why a change happened, patterns, constraints and assumptions. When a human merges generated code, intent is confirmed; when a human edits it, the difference teaches the system.
- **Why it matters:** accuracy for that enterprise compounds with use, and the knowledge becomes a system of record that supports later work, not a one-off output.
- **Buyer translation:** "The tenth project is cheaper and more accurate than the first."

### 4.6 Language and version agnosticism, and parallel pathways

- **What it is:** modernization, brownfield bug-fixing and greenfield building can run side by side, across many languages and versions.
- **Buyer translation:** "One platform for the whole portfolio, not a different tool for each stack."

---

## 5. Position at the process level

The single most important positioning move: do not sell a project.

| Level | Example | Consequence |
|---|---|---|
| Project | Move from one language to another | Invites a short proof-of-value request and caps scope |
| Program | Modernize an entire system | Broader, still bounded |
| **Process** | **Change how the enterprise builds and changes software** | **Supports a paid, 6 to 12 month pilot and cannot be shown in a quick proof** |

**Why this pairs with the AI-DLC:** the AI-DLC argument is itself about reimagining the lifecycle rather than retrofitting AI into the old one. Blitzy as a process change is consistent with what the buyer is already being told by analysts, cloud providers and their own boards.

**Language tips:**
- Say "initiative" or the customer's own business-unit language, not "project."
- Keep the north star on organizational impact. Short-term refactors still happen, and they earn the right to span the whole estate.
- Selling a process change is also why many recent customers bought without a formal proof of value. The early positioning did the work.

---

## 6. Discovery

### 6.1 Open with their thesis

Start by asking for the prospect's view of the AI coding space. This surfaces prior experience, skepticism, past tool failures and whether they care about risk or speed. Stay curious and a little humble; people tell you more. The answer decides whether you lead with trust or acceleration and which objection to prepare for.

### 6.2 Questions by theme

**Strategy and business case (executives)**
- What outcome would make this year's technology plan a success?
- Where is time-to-market costing you the most?
- What risk in your estate keeps you up at night? Which systems does nobody fully understand anymore?
- How do competitors' release cadences compare to yours?
- Are there licensing or vendor costs (for example mainframe or legacy platform fees) that retiring a system would eliminate?
- What would the board want to see to feel confident in AI-driven delivery?

**Technical discovery (architects and engineering leaders)**
- How large are the codebases, how many repos, and how many languages and versions?
- How many teams touch the estate, and over what timeframe does the work need to land?
- What does test coverage look like today?
- Who owns architectural standards, and who signs off a target state?
- What have you already tried, and what happened?
- How do you currently trace a change back to a requirement or policy?

**Adoption and change**
- Who will resist, and why? Whose role changes?
- How do you want developers to experience this: as a threat or as a way to get visible, recognized work done faster?
- What minimal change fits your maturity right now?

**Personal motivation**
- What does success look like for you personally? Recognition, a board-visible win, a career step? Genuine curiosity builds trust that sales tactics cannot.

### 6.3 Qualification

- **Strong fit:** large, complex codebases, ideally 500,000 lines or more, multiple repos, a real modernization or backlog problem, an architect-led target state, and an executive who thinks in strategic leaps.
- **Weak fit:** codebases under about 100,000 lines are likely too small to need the platform. Work that depends on inventing novel proprietary algorithms is not what Blitzy is for. It implements; it does not invent.
- **Readiness signals:** an executive sponsor, an architect who will own the plan, willingness to frontload requirements, and a view that the change is organizational, not a one-off tool trial.

---

## 7. Talk tracks

### 7.1 Thirty seconds
"Blitzy is an autonomous software development platform for the enterprise. It understands your entire codebase, plans the work with your architects, then builds and validates it end to end, so your people review a proven result instead of a draft. Customers use it to turn years of roadmap into quarters."

### 7.2 One minute (executive)
"Most AI coding tools make individual developers faster. Blitzy works on the whole system. It builds a map of your entire estate, tens of millions of lines if needed, then plans a change with your architects and runs long autonomous jobs that compile, test and validate continuously. About half the run is end-to-end validation. Your people stay in the lead: they approve the plan and the pull request. The result is much faster delivery without giving up control, and you finally get a living picture of software you have never fully understood."

### 7.3 Regulated buyers
Avoid leading with "autonomy," which can alarm. Say: "a human-in-the-lead autonomous software development platform," anchored in whole-estate understanding and comprehensive testing. Lead with risk and visibility into the estate, then deliver the acceleration.

### 7.4 Technical audience
"Blitzy builds a deterministic structural graph from parsers and static analysis, so every fact traces to a place in the source. Models then add business meaning on top, and that layer is cross-checked by multiple models and rejected if it breaks the schema. Agents only get the context a step needs, which keeps them inside the window where models stay accurate. Generation is a small fraction of the run; validation is most of it."

### 7.5 The trust-then-speed order
Lead with trust and control. Speed is the result you deliver, not the opening line. A buyer who trusts the process will engage; a buyer sold on speed will ask for a proof first.

---

## 8. Objection handling

| Objection | Response pattern |
|---|---|
| **"How do we know the knowledge graph and spec are accurate?"** | Three layers. Deterministic: parsers and static analysis produce the same graph every time, and every fact traces to the source. Probabilistic: models add business meaning, usage and live-vs-dead judgments, which can be wrong. Validation: multiple models cross-check, a schema rejects malformed entries, the graph refreshes on every merge, and a guess cannot outrank a fact from code. Be candid that a small chance of error remains, then offer the safety nets: chat with the knowledge base to probe it, and customer experts review key parts of the spec. Edits to the spec carry back into the knowledge layer and are remembered |
| **"AI is probabilistic. We need deterministic."** | Agree. The answer is orchestration: a reviewed plan, continuous validation, and humans at the approval points, so the work is as close to deterministic as possible while keeping the generalization that makes AI useful |
| **"Won't the big model providers just do this in a year?"** | They are suppliers, not competitors. Blitzy uses their models inside a multi-model platform and benefits as they improve. The durable work is the harness: whole-estate context, orchestration, validation, and the accumulating enterprise memory. Enterprise-scale development is a different problem from helping one developer |
| **"We will build it ourselves."** | Some enterprises do, and some succeed. Ask about their thesis first. Offer the parallel-track pattern: their internal effort continues while Blitzy handles the hard cases, such as large modernizations, so they learn from both. Language and version agnosticism lets modernization run on one track and new features on another |
| **"Copilots already cover this."** | Complementary. Copilots help a developer inside a file. Blitzy handles system-wide change across repos. Many enterprises run both |
| **"Agents like Devin already do this."** | Task-level agents work well on bounded tasks. They lack a persistent global model of the system and tend to struggle when a change ripples widely. Show a cross-repo change |
| **"Show us a proof of value first."** | Reframe at the process level. A short proof proves a narrow thing and cannot demonstrate a change in how work gets done. Offer a three-track paid pilot instead (see section 9) |
| **"What about our security, PII and secrets?"** | Blitzy operates on source code, not production data. The customer owns what they supply. Scanning can surface identified risks, and guardrails are rules defined at prompt time. Be precise and do not over-claim built-in guardrails for every scenario. Offer documentation on audit trails and logging |
| **"Our developers will resist."** | Frame the change as career advancement. Developers who use Blitzy to finish large pieces of work quickly gain visibility and recognition, and the roles evolve toward architecture, review and validation |
| **"Will it write our proprietary algorithms?"** | Blitzy implements a defined design; it is not an inventor of novel algorithms. Its added value is making visible how business processes live inside the code |
| **"Our code is too small or too messy."** | If under about 100,000 lines, say honestly it may be too small to justify the platform. For messy estates, this is the point: the knowledge graph exists to make poorly understood systems legible |

---

## 9. From conversation to pilot

### 9.1 Demo a new way of working, not a feature
Choose a process the buyer recognizes (a recurring migration, a backlog category, a security remediation) and show the entire loop: ingestion and spec, the reviewed plan, autonomous build with validation, and the pull request with project guide. Narrate where the human is in control at each step. Show the validation proof, not just the output.

### 9.2 The three-track paid pilot
After the customer agrees to a process transformation journey, propose a prescriptive 6 to 12 month paid pilot with three relatively independent tracks, each given to a separate team:

1. **Large-scale modernization**
2. **Brownfield bug-fixing and maintenance**
3. **Greenfield product building**

This mirrors the pathways an AI-driven lifecycle has to handle, and shows impact across distinct kinds of work before scaling. Align on the minimum viable change for the customer's maturity rather than a wholesale shift, and position your team as a trusted partner.

### 9.3 Set expectations early
Tell customers up front how much time requirements gathering takes. Do not assume teams are ready to begin code generation immediately. Early spec work is what keeps iteration cycles short later.

### 9.4 Who to sell to
Buyers who think in strategic leaps respond best to a process pitch. Senior sponsors, enterprise architects and technology leaders who own the target state are the core audience.

---

## 10. Building the supporting assets

Use a repeatable five-step process, each step in its own pass so the AI stays on goal.

1. **Audience analysis.** Build a brief from the buyer's public profile and recent call transcripts. Stay on the primary decision-makers; adding personas dilutes the message.
2. **Core narrative.** Something you can say in 10 to 20 seconds. A spoken brain dump refined with an AI assistant works well.
3. **Slide titles and takeaways.** Titles alone should tell the story, because executives often only read titles. Each slide has a one-sentence takeaway; if it cannot be summarized, cut it. A good arc is the customer's challenge, then Blitzy's value, then the outcome.
4. **Content in small batches.** Two or three slides at a time. Ask where the viewer's eye should land, or for a markdown wireframe, before any design work.
5. **Build.** Generate the deck from the content, an example deck for style, and a screenshot of the product for brand consistency.

**Be candid in the deck.** Include where Blitzy is not a fit and where a project struggled, such as undefined targets. Documenting limits builds credibility with stakeholders and sets realistic expectations.

---

## 11. Proof points and claim hygiene

**Use with confidence**
- A federal science agency proof of value reached 87% autonomy in one to two weeks on work that averaged six months, with more than 5,000 automated tests.
- The run-time profile: roughly 25% planning and context engineering, 1% code generation, 24% in-stride validation, 50% end-to-end validation.
- Typical onboarding of one to two days for very large estates.

**Use carefully**
- **Acceleration multiples.** Some customers have reported 30 to 50 times acceleration. This is client-reported and not tied to a named, citable customer. Offer it as an anecdote and let the trust-first story lead.
- **Benchmarks.** An industry-leading score on a code-understanding benchmark exists, but the team has moved away from relying on benchmarks toward customer outcomes. Mention only if the buyer insists.
- **"Up to 80%+ autonomy."** A ceiling, not an average; pair it with the specific proof point above.
- **Competitive "a decade ahead" language.** Avoid. Prefer the stronger argument that frontier model gains improve the platform.
- **Architecture superiority.** The claim that a vector-graph hybrid beats markdown-driven or hierarchical systems is a team position, not independently demonstrated. Prove it by showing a cross-repo change, not by asserting it.

**Do not say**
- That Blitzy handles production data, incident response or runtime telemetry.
- That guardrails and PII handling are fully built in. The customer owns what it supplies.
- That the knowledge layer is guaranteed correct. Say it is validated, and name the safety nets.

---

## 12. Quick reference

**The five messages**
1. The lifecycle is changing; the question is how to adopt it safely.
2. Blitzy understands the whole estate, then plans before it acts.
3. Validation is the architecture; generation is the small part.
4. Humans stay in the lead and approve a proven result.
5. Change the process, not a project, and prove it across three tracks.

**Do**
- Ask for their thesis before pitching.
- Lead with trust and risk, then deliver speed.
- Position at the process level and use their language.
- Be candid about limits and fit.
- Show a cross-repo change and the validation evidence.

**Don't**
- Lead with speed or "autonomy" to regulated buyers.
- Offer a short proof of value by reflex.
- Over-claim on guardrails, data handling or benchmarks.
- Pitch to codebases that are too small.
- Treat copilots or in-house efforts as enemies; position as complementary or parallel.

**Before every call**
- Audience brief built.
- Two or three trends chosen from section 2.
- One proof point and one honest limit ready.
- A cross-repo demo scenario matched to their stack.
- The paid three-track pilot sketched for their context.
