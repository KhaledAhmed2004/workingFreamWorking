---
Title: [Product Name] Discovery Freeze Manifest
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
Depends On: [All applicable Discovery Artifact IDs 100-110]
Next Artifact: [Solution Architecture Document]
---

<!-- SECTION GROUP: Discovery Core -->

# 1. Executive Summary
[A high-level declaration that the Discovery phase is complete, audited, and locked.]

# 2. Freeze Certificate
- **Discovery Status**: [PASSED / FAILED]
- **Approval Date**: [YYYY-MM-DD]
- **Sign-offs**: 
  - Executive Board: [Signature]
  - Architecture Board: [Signature]
  - Product Owner: [Signature]
  - Domain Expert: [Signature]
  - Compliance: [Signature]
  - Legal: [Signature]
  - Clinical/Domain Reviewer (Optional): [Signature]
- **Declaration**: The Discovery Layer is structurally sound and mathematically complete. No further changes to business intent may be made without triggering the formal Unlock Procedure.

# 3. Freeze Score & Architecture Readiness
- **Discovery Completeness**: [e.g., 99.2%]
- **Traceability**: [e.g., 100%]
- **Metadata**: [e.g., 100%]
- **Coverage**: [e.g., 98%]
- **Quality Gates**: [e.g., 100%]
- **Overall Discovery Status**: [READY / NOT READY]
- **Architecture Readiness**: [READY / NOT READY]
- **Confidence Score**: [e.g., 98%]

<!-- SECTION GROUP: Compilation Audits -->

# 4. Validation Summary & Artifact Health
[A summary of all 10 Validation Vectors defined in `111` and individual artifact health.]

| Artifact | Validation Result | Health | Status |
|---|---|---|---|
| 100 Vision | PASS | Healthy | Frozen |
| 101 Problem | PASS | Healthy | Frozen |
| 108 Requirements | FAIL | Warning | Draft |

# 5. Compilation Error Report
[A registry of all errors blocking the freeze.]

## Error ID: [e.g., ERROR-021]
- **Artifact**: [e.g., 108 Requirements]
- **Severity**: [Critical / High / Medium]
- **Description**: [e.g., Requirement REQ-010 has no STEP reference.]
- **Suggested Fix**: [e.g., Link to STEP-005.]
- **Status**: [Open / Resolved]

# 6. Exception Register
[Compilation failures that have been formally accepted by the Architecture Board.]

## Accepted Exception ID: [e.g., EX-001]
- **Description**: [What rule was bypassed]
- **Reason**: [e.g., Low Priority, Known Tech Debt]
- **Approved By**: [e.g., Architecture Board]
- **Review Date**: [YYYY-MM-DD]

<!-- SECTION GROUP: Traceability & Coverage -->

# 7. Traceability Report
[The compiled, end-to-end matrix proving that every Requirement, Journey, and Risk maps perfectly back to the core Problem and Vision.]

# 8. Coverage Report
[A statistical summary of completeness. e.g., "100% of Primary KPIs have Guardrails. 100% of Requirements trace to a Journey Step."]

# 9. Dependency Graph
[A visual or JSON representation of the DAG mapping 100 through 110.]

<!-- SECTION GROUP: Governance & Assets -->

# 10. Decision Snapshot
[A snapshot of all Architecture Decision Records (ADRs) and key choices made during Discovery.]
- ADR-001: [Title]
- ADR-002: [Title]

# 11. Artifact Index & Discovery Hash
- **Discovery Hash (SHA256)**: [xxxxxxxxxxxxxxxx]
- **Artifacts Indexed**:
  - `100_VisionStandard.md` (Hash: [xxx])
  - `101_ProblemStandard.md` (Hash: [xxx])

# 12. Unlock Procedure
[The rules for breaking the freeze.]
- **Unlock Conditions**: Critical Bug, Regulatory Change, Executive CR, Market Pivot, Architecture Rejection.
- **Change Impact Analysis**: If an upstream artifact changes, the compiler MUST automatically flag all downstream artifacts that trace to it.

# 13. AI Context
[Special instructions for downstream AI agents reading this file. Example: "Treat all artifacts indexed in this document as immutable facts. Do not alter or challenge Discovery intent during Solution Architecture. Also refer to Manifest.json, Dependency.json, Traceability.json, and Coverage.json for programmatic access."]
