![][image1]

**Security FAQs INTERNAL USE**

**Platform Isolation & Multi-Tenancy**

**What is the exact tenant isolation model for embeddings and metadata?**

Customer data is isolated using unique tenant identifiers, with access controls enforced at the application layer to prevent cross-customer data access. Blitzy supports SAML SSO on all tiers, and MFA via the customer IdP, RBAC, and SCIM provisioning. Segregation is implemented at the database schema level, with separate storage buckets for artifacts. For customers requiring dedicated infrastructure, we offer VPC and On-Premise deployment options where your embedding store resides entirely within your own environment.

**Are vector stores physically isolated per customer, logically isolated, or shared with tenant-level controls?**

In our standard Cloud deployment, vector stores are logically isolated with tenant-level controls. For customers with stricter isolation requirements, our Dedicated VPC, Black-box VPC, and On-Premise tiers provide fully physically isolated infrastructure.

**What safeguards prevent cross-tenant embedding leakage or semantic retrieval across tenants?**

We enforce tenant validation at the API and authentication layer, active monitoring for insecure direct object reference (IDOR) vulnerabilities, network-level anti-spoofing controls, role-based access control with least-privilege defaults, and quarterly access reviews. Tenant identifiers are never exposed to end users, removing an entire class of client-side tampering risk.

**How are AI agents isolated when thousands of agents collaborate on a customer project?**

Each unit of work runs in its own ephemeral, hardened container that is provisioned for that job, executes it, and is destroyed on completion with no persistent state and no administrative access outside the sandbox.

**Are agents executed in separate containers, VMs, Kubernetes namespaces, or another isolation boundary?**

Agents execute as isolated Kubernetes pods, one per job, providing container-level isolation with no shared state between runs.

**AI Runtime Architecture**

**Is there an orchestration framework used for the agentic architecture?**

Yes. Blitzy uses a proprietary Multi-Model Orchestration layer that dynamically assigns each subtask to the best-suited model across Anthropic, OpenAI, and Google based on task type and complexity, with many agents working in parallel.

**What controls exist to prevent prompt injection between cooperating agents?**

End users and external systems never interact with the underlying models directly. All prompts are generated from internally managed, controlled templates, so untrusted external input cannot reach a model directly. Dedicated oversight agents continuously verify that generation stays aligned with the approved project specification, catching drift before it compounds.

**How is agent decision-making audited and reconstructed after execution?**

Every change Blitzy makes is delivered as a version-controlled pull request, giving you a complete, auditable record of what was generated and why. Execution activity is logged with timestamps, user identifiers, and action types.

**Can customers access execution traces, reasoning chains, or agent activity logs, including for incident response?**

Customers can see the system logs if contractually agreed upon. However, execution traces, reasoning chains, and agent activity are proprietary and not shared with customers.

Instead, customers review and explicitly approve the detailed scope, design, and specification of the intended work (agent action plan); as well as the evidence of completion and validation (project guide).

**Is model routing dynamic, and how are models selected for processing customer data?**

Yes. Model selection is performed algorithmically at runtime based on task type and complexity. Enterprise customers can scope which providers and regions are used as part of a dedicated VPC or On-Premise deployment, and can supply their own model provider API keys if desired.

**Does Blitzy Store source code? Also, does Blitzy learn from the code it reads?**

We never store code and only work with embeddings. Our architecture stores only embeddings during processing \- never your actual source code. Temporary files in ephemeral storage are automatically purged when processes complete. We do not maintain code checkpoints or copies beyond what's necessary for active processing sessionsBlitzy's Teams and Enterprise tiers, customer code is not used to train any AI model. Blitzy doesn't train its own models at all; it calls out to third-party foundation models (Anthropic, OpenAI, Google), and per Blitzy's contractual/product policy those inputs aren't used for training at the higher tiers.

**Network Architecture**

**Can you elaborate on the "Inbound-only VPC architecture" with no publicly exposed endpoints?**

Blitzy's code-generation environment operates as an inbound-only, VPC-based system. Access is brokered through a single secure gateway; there are no publicly exposed administrative endpoints, which significantly reduces the platform's attack surface. All cross-boundary communication is encrypted (HTTPS/TLS 1.2+) and authenticated.

**What controls enforce that no outbound requests are initiated from the platform?**

Network segmentation and firewall policy enforce this boundary at the infrastructure level. We're happy to walk your security team through the specific controls as part of a formal architecture review.

**Are build systems, package repositories, and dependency-fetch services fully internalized?**

Our build and validation environment resolves publicly available packages (npm, PyPI, Maven Central, and similar public registries) directly from their standard sources as part of compiling and testing generated code. We do not have access to your private or internal package registries. If your project depends on internally published packages, those are supplied as local packages within your repository rather than fetched live, so your build succeeds without requiring us to have credentials or connectivity to your internal systems.

**How are software dependencies updated without outbound connectivity?**

Software dependencies are updated via the knowledge graph, which continuously grows as you develop software.

**What transport-layer security patterns are followed?**

All data in transit is encrypted using TLS 1.2+. Data at rest is encrypted using AES-256, with encryption keys managed via FIPS 140-2/140-3 validated methods.

**Cloud SaaS GCP Architecture**

**Air-Gapped Code Generation**

**Is "air-gapped code generation" physically isolated or logically segregated? What definition is used?**

Our code-generation environment is logically air-gapped: it is not accessible via our user-facing interface and has no public internet exposure, isolating it from the surfaces most commonly targeted in an attack. For customers requiring physical separation, our On-Premise and Black-box On-Premise deployment options place the entire environment within your own infrastructure boundary.

**How is code promoted between ingestion, analysis, generation, QA, and delivery stages?**

Your code is analyzed to build a knowledge graph, a detailed implementation plan (the Agent Action Plan) is generated for your team's review and approval, code generation proceeds against that approved plan, automated security validation runs on every output, and the result is delivered as a pull request into your branch for final review. Nothing merges without your explicit approval at two separate checkpoints.

**Are there one-way transfer mechanisms between environments?**

Isolation between environments is enforced through network segmentation and ephemeral, single-use execution environments rather than physical one-way transfer hardware. Happy to go deeper on this with your architecture team if useful.

**Data Protection**

**Which encryption algorithms are used for data at rest and in transit?**

AES-256 at rest, TLS 1.2+ in transit.

**Who manages encryption keys?**

Encryption keys are managed through enterprise-grade key management services using cryptographic controls aligned with NIST SP 800-57.

**Are customer-specific encryption keys supported?**

Yes, for our VPC and On-Premise deployments, where the key management infrastructure resides entirely within your environment. For our standard Cloud offering, we're glad to confirm the specific configuration for your use case during technical scoping.

**Is Bring Your Own Key (BYOK) available?**

BYOK can be scoped as part of a dedicated VPC or On-Premise deployment.

**How often are keys rotated?**

Transport keys are rotated quarterly; data encryption keys are rotated annually. Access tokens used for repository integration are short-lived (one-hour lifetime) and rotate automatically.

**What data is retained after project completion?**

Blitzy data retention periods — customer data deleted within 90 days of termination; system logs 60-day retention; DB backups 45-day with point-in-time recovery; AI-vendor API logs 90 days per DPAs.

**Secrets Management**

**Where are secrets stored?**

Secrets and environment variables are stored in HashiCorp Vault. In VPC deployments, this is your own Vault instance, entirely within your control. Blitzy has no access to it.

**Are secrets visible to AI models?**

No. Secrets are automatically detected and redacted before any content is transmitted to a model.

**How are secrets masked in logs, outputs, and generated code?**

Secrets are never written to disk, container images, or logs in plaintext. They are loaded directly into application memory at runtime only. We do not use environment variables as a mechanism for secret distribution.

**Are ephemeral credentials supported instead of long-lived secrets?**

Yes. Repository access tokens are short-lived (one hour) with automatic rotation, delivered over encrypted channels, and held only in memory during execution.

**Is integration available with HashiCorp Vault, CyberArk, AWS Secrets Manager, Azure Key Vault, or similar platforms?**

HashiCorp Vault is natively supported today. For customers standardized on other enterprise vault platforms, our solutions team can scope integration as part of your deployment.

**SDLC Security**

**What automated security testing is performed on generated code?**

Every output undergoes SAST and DAST scanning, along with dependency and CVE checks, before a pull request is ever raised. Code that doesn't meet validation criteria is flagged and remediated within the same generation cycle.

**Are SAST, DAST, dependency scans, SBOM generation, and secrets scanning included?**

SAST, DAST, dependency scanning, and secrets scanning are all included as standard. SBOM generation is on our roadmap. We're happy to update you on timing.

**What percentage of generated code vulnerabilities are detected before delivery?**

Autonomously generated code undergoes the same security testing as human code prior to delivery. Blitzy can also perform security audits of the code on demand. Additionally, support for autonomous and proactive security audits will be available shortly in our next release. We'd be happy to discuss this functionality coming soon.

**How do QA agents validate security defects?**

Dedicated validation agents check every output against your approved specification and against integrated security tooling, iterating automatically until defined standards are met — before anything reaches human review.

**Can security findings be exported into enterprise tooling such as SonarQube or Checkmarx?**

Yes for SonarQube, and we support integrating additional scanners like Aikido so your existing security policies apply automatically to every generated pull request. We can confirm specific tooling compatibility, including Checkmarx, during technical scoping.

**AI Security**

**How is model output poisoning prevented?**

All generated code passes through automated security validation and sandboxed compilation before delivery, and nothing reaches production without two separate human approval checkpoints: one before generation begins, one before merge.

**How is training data provenance verified?**

Blitzy does not train or fine-tune any models on customer or third-party data. The underlying frontier models we orchestrate are developed and maintained independently by Anthropic, OpenAI, and Google under their own enterprise data protection terms.

**Can customers restrict specific models from processing data?**

Yes, for our dedicated VPC and On-Premise deployments, where provider and region can be scoped to your requirements. We can confirm options for other deployment tiers during scoping. This is typically not recommended as it can impact the quality of generated code, as Blitzy agents dynamically determine the model best suited for the current sub-task.

**Are model providers contractually prohibited from retaining data?**

Yes. Our enterprise agreements with Anthropic, OpenAI, and Google contractually prohibit using customer input to train or improve their models.

**Certifications**

**Are current SOC 2 Type II and ISO 27001 reports available under NDA?**

Yes, both are available upon request under NDA through our trust center. ISO 27001 certificate IS-IA-2025-12-11-01, issued Dec 11, 2025, valid through Dec 2028\.

**What controls are in scope for SOC 2?**

We're glad to share the detailed scope as part of the report itself.

**What systems are excluded from scope?**

Covered in the full SOC 2 report.

**When were the most recent audits completed?**

Our SOC 2 Type II examination covers the period of June 2025 through May 2026\. We maintain continuity between annual audit cycles through bridge letters — our most recent, dated June 29, 2026, confirms no material changes to our control environment since the audit period. Our ISO/IEC 27001:2022 certification is maintained on an ongoing basis through annual surveillance audits conducted by our certification body. We're happy to provide the current SOC 2 report, the bridge letter, and the ISO 27001 certificate directly under NDA as part of your due diligence process.

**Financial Services Alignment**

**Has the platform undergone banking or financial services risk reviews?**

Yes. Blitzy has completed security and data-protection diligence processes with several regulated financial services and insurance customers, including formal DPA and security review cycles. Blitzy also has independent pen-test reports that can be made available under NDA.

**Can customer data remain within a specified geographic region?**

Yes. Our standard deployment is US-based, and our VPC and On-Premise options let you control the hosting region entirely.

**How do you support data residency requirements?**

Through deployment model choice — VPC or On-Premise deployments keep data within your specified region and infrastructure — combined with region-appropriate data processing terms in our agreements.

**Is there support for GDPR, CCPA, DORA, banking regulatory expectations, and data sovereignty mandates?**

We support GDPR and CCPA today through dedicated data processing agreements, including Standard Contractual Clauses, a UK Addendum, and a Swiss FADP amendment where applicable. For DORA and specific banking regulatory frameworks, we're glad to work directly with your compliance team to confirm alignment for your engagement.

**Third-Party Risk**

**What external AI providers or cloud providers process customer content?**

Anthropic, OpenAI, and Google act as our AI processing partners, receiving only the minimal context needed to complete a given task. Our infrastructure runs on Google Cloud Platform.

**Is a complete subprocessor list available?**

Yes, our current subprocessor list is available as part of our standard data processing agreement.

**Identity & Access Management**

**How is privileged or administrative access to Blitzy's own infrastructure controlled and monitored?**

Administrative access to production infrastructure is role-based, granted on a least-privilege basis, and requires SSO with MFA. All privileged actions are logged and subject to periodic access review. \[TO CONFIRM: specific IAM tooling and review cadence with Security/IT before sharing.\]

**Is just-in-time or break-glass access used for engineer access to production systems?**

Standing access to production is minimized in favor of time-boxed, approval-gated access for the specific task at hand, with break-glass procedures reserved for incident response. \[TO CONFIRM: exact JIT tooling and approval workflow.\]

**What does employee or contractor offboarding and access revocation look like?**

Access is tied to identity provider group membership, so offboarding an employee or contractor in the IdP revokes downstream access across connected systems. \[TO CONFIRM: revocation SLA — e.g., same business day — with IT/HR.\]

**Business Continuity & Disaster Recovery**

**What are your RTO/RPO targets and disaster recovery architecture?**

\[TO CONFIRM WITH INFRA/SRE: specific RTO/RPO figures and DR architecture (e.g., multi-AZ, backup region) before including in a customer-facing response.\]

**What is the incident response process and customer notification SLA for a security incident?**

Blitzy maintains a documented incident response process covering detection, containment, eradication, and recovery. \[TO CONFIRM WITH SECURITY/LEGAL: customer notification SLA — banks typically expect notification within 24–72 hours of confirmed impact — and whether this is already codified in the DPA/MSA.\]

**Is there a documented, tested business continuity plan?**

\[TO CONFIRM: whether a formal BCP exists and the cadence of tabletop or failover testing. If not yet formalized, flag as a roadmap item rather than leaving unanswered.\]

**What are your uptime and availability commitments?**

\[TO CONFIRM WITH CS/LEGAL: any contractual SLA percentage, and whether a status/incident-history page is publicly available.\]

**Vulnerability & Patch Management**

**What is the SLA for patching critical vulnerabilities in Blitzy's own infrastructure?**

Blitzy runs continuous vulnerability scanning across its infrastructure, with critical findings prioritized for expedited remediation. \[TO CONFIRM: specific patch SLA by severity — e.g., critical within 7 days, high within 30 — this is distinct from the SAST/DAST scanning already described for customer-generated code.\]

**Do you run a bug bounty program or scheduled third-party penetration testing?**

Blitzy commissions independent penetration tests, with reports available under NDA as noted under Financial Services Alignment. \[TO CONFIRM: cadence (e.g., annual) and whether a public or private bug bounty program is currently active.\]

**Logging, Monitoring & SIEM**

**Is there centralized security logging and SIEM coverage, and how long are security logs retained?**

\[TO CONFIRM WITH SECURITY: whether infrastructure security events are centralized in a SIEM, and the retention period for security logs specifically — note this is distinct from the system-log and DB-backup retention figures already provided under Data Protection.\]

**Is there 24/7 monitoring or a managed detection and response (MDR) capability?**

\[TO CONFIRM: whether monitoring is in-house, via a managed SOC/MDR provider, or a hybrid model, and expected alert-to-triage time.\]

**Personnel & Insider Risk**

**Are background checks and security awareness training required for employees and contractors with customer data access?**

\[TO CONFIRM WITH HR/SECURITY: background check policy and frequency of required security awareness training — this is a standard line item in financial-services vendor reviews.\]

**What separation-of-duties controls exist internally?**

Production access, code review/approval, and deployment responsibilities are held by different roles to avoid a single individual controlling an entire change end to end. \[TO CONFIRM: specifics for how this maps to Blitzy's own release process.\]

**Data Deletion & Portability**

**Can a customer request immediate, on-demand data deletion ahead of the standard retention window, and is deletion verifiable?**

Standard retention periods are outlined under Data Protection. \[TO CONFIRM WITH LEGAL/SECURITY: whether on-demand/early deletion is supported today, and whether deletion confirmation (e.g., a certificate of destruction) can be provided — banks frequently require this.\]

**Are backups purged in line with the same retention policy as primary data?**

\[TO CONFIRM: whether the 45-day DB backup retention already cited fully supersedes primary data once a deletion request is processed, or whether backups persist independently for their own window.\]

**Platform Resilience (Agent Execution)**

**If an agent container fails mid-task, is partial or inconsistent state prevented from reaching the customer's codebase?**

Each unit of work executes in an ephemeral, single-use container with no persistent state; a failed job does not produce a partial commit, since nothing is written back to the customer's repository until the job completes and passes validation.

**Is there multi-region failover for the orchestration layer itself?**

\[TO CONFIRM WITH INFRA: whether the Multi-Model Orchestration layer has multi-region failover, or is currently single-region with a documented recovery path.\]

**Insurance**

**What cyber liability insurance coverage does Blitzy carry?**

\[TO CONFIRM WITH LEGAL/FINANCE: current cyber liability coverage amount. Banks commonly require proof of a minimum coverage level (often \$5M+) as part of vendor onboarding — this figure should come from Legal/Risk, not be estimated here.\]

**Additional Regulatory & Framework Coverage**

**Do you hold or are you pursuing FedRAMP or StateRAMP authorization?**

\[TO CONFIRM: current status. Likely not applicable unless the customer's use case touches public-sector-adjacent workloads — flag as not-yet-pursued if accurate rather than leaving open.\]

**Is PCI-DSS applicable given any potential exposure to cardholder data?**

Blitzy is not designed to ingest or process cardholder data as part of normal operation. \[TO CONFIRM WITH SECURITY/LEGAL: formal PCI-DSS applicability determination if any customer codebase or test data could contain card data, e.g., CardDemo-style reference repos.\]

**How does the platform align with FFIEC guidance?**

\[TO CONFIRM WITH COMPLIANCE: this sits alongside the DORA/GDPR/CCPA answer already provided under Financial Services Alignment — FFIEC is the US-specific banking framework counterpart and the customer's security team may expect an explicit answer rather than a general regulatory-alignment statement.\]

**Before sending externally: the sections above marked \[TO CONFIRM\] are drafted in the voice of the existing answers but contain no verified internal figures (RTO/RPO, insurance coverage, patch SLAs, FedRAMP/PCI status, etc.). Route these to Security, Legal, and Infra/SRE for sign-off before they go into any customer-facing document.**

**Links:**

Obtain the current SOC 2 report through the approved internal process. Share it externally only under the applicable NDA.

**Before sending externally: the sections above marked \[TO CONFIRM\] are drafted in the voice of the existing answers but contain no verified internal figures (RTO/RPO, insurance coverage, patch SLAs, FedRAMP/PCI status, etc.). Route these to Security, Legal, and Infra/SRE for sign-off before they go into any customer-facing document.**

[image1]: <data:image/png;base64,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>
