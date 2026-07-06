---
Title: [Product Name] Assumptions & Risks
Artifact Version: 1.0
Status: Draft
Phase: Product Discovery
Sprint: [Sprint Number/Name]
Owner: [Owner Name]
Reviewer: [Reviewer Name]
Approver: [Approver Name]
Created: [YYYY-MM-DD]
Updated: [YYYY-MM-DD]
Artifact ID: [Unique ID]
Depends On: [All applicable Discovery Artifact IDs 100-109]
Next Artifact: [Discovery Freeze Document]
---

<!-- SECTION GROUP: Discovery Core -->

# 1. Executive Summary
[A high-level summary of the critical assumptions and existential risks governing this product.]

# 2. Purpose
[Define the intent of this document. How will it guide QA, Architecture, and Product Ops?]

# 3. Scope
[Define the boundaries. Which regions, user bases, or technical layers are covered by this risk assessment?]

<!-- SECTION GROUP: Registers -->

# 4. Assumption Register
[Hypotheses we are treating as facts to proceed, but which require explicit validation.]

## [Assumption Title] (e.g., Doctors will review digital reports)
- **ID**: [e.g., ASM-001]
- **Type**: Assumption
- **Category**: [e.g., Adoption]
- **Description**: [Detailed description of the assumption]
- **Impact**: [Numeric 1-5 scale]
- **Confidence**: [Validated / High / Medium / Low / Unknown]
- **Owner**: [Who is responsible for validating this?]
- **Validation Plan**: [How we will prove/disprove this (e.g., User testing in Sprint 2)]
- **Status**: [Open / Validated / Invalidated]
- **Last Reviewed Date**: [YYYY-MM-DD]
- **Next Review Date**: [YYYY-MM-DD]
- **Traces To**: [One or more source IDs from 100-109, e.g., REQ-010, PER-001]

*(Repeat Card for each Assumption)*

# 5. Risk Register
[Potential threats to the product's success, safety, or compliance.]

## [Risk Title] (e.g., PHI Data Leak during Integration)
- **ID**: [e.g., RISK-001]
- **Type**: Risk
- **Category**: [e.g., Privacy / Regulatory / Dependency / Third Party / Legal]
- **Description**: [Detailed description of what could go wrong]
- **Trigger**: [What event activates this risk?]
- **Early Warning Indicators**: [Signals before the risk materializes]
- **Impact**: [Numeric 1-5 scale]
- **Likelihood**: [Numeric 1-5 scale]
- **Initial Risk Score**: [Impact × Likelihood, e.g., 25]
- **Owner**: [Who is responsible for mitigating this?]
- **Mitigation Plan**: [Actionable steps to prevent or minimize the risk]
- **Residual Risk Score**: [Score after mitigation is applied]
- **Status**: [Open / Mitigated / Accepted]
- **Last Reviewed Date**: [YYYY-MM-DD]
- **Next Review Date**: [YYYY-MM-DD]
- **Traces To**: [One or more source IDs from 100-109, e.g., REQ-050]

*(Repeat Card for each Risk)*

<!-- SECTION GROUP: Governance -->

# 6. Validation & Mitigation Plan
[A consolidated summary of the operational actions required. Grouped by Owner or Sprint.]

# 7. Traceability Matrix
[A summary table mapping `ASM-ID` / `RISK-ID` -> Source Artifact ID (e.g., `REQ-ID`, `PER-ID`) to ensure comprehensive coverage.]

# 8. AI Context
[Special instructions for downstream AI agents reading this file. Example: "When generating Solution Architecture from this artifact, ensure all High-Impact Technical Risks have explicit mitigation patterns applied in the system design."]
