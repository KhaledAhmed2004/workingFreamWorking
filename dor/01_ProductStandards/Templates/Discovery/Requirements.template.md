---
Title: [Product Name] Requirements Document
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
Depends On: [Principles Artifact ID], [JTBD Artifact ID], [Journey Artifact ID]
Next Artifact: [Success Metrics Document]
---

<!-- SECTION GROUP: Discovery Core -->

# 1. Executive Summary
[A high-level summary of the core capabilities required to build the Future State Journeys defined in this product ecosystem.]

# 2. Purpose
[Define the intent of this Requirements document. How will it be used by Engineering and Product Management?]

# 3. Scope
[Define the boundaries. Which Capability Groups or systems are explicitly included or excluded from this scope?]

<!-- SECTION GROUP: Requirements Hierarchy -->

# 4. Capability Groups Overview
[A high-level list of the major capability clusters that map to the Journey Phases.]

## [Capability Group Name] (e.g., Capability Group 1: Automated Shift Handoff)
- **Description**: [Summary of the Capability Group]
- **Target Journey Phase**: [Map to a phase in `107`]

# 5. Functional Capabilities
[The specific functional requirements needed to resolve frictions and enable the Journeys. Grouped by Capability Group.]

## Capability Group: [Capability Group Name]

### [Capability Title] (e.g., Secure Handoff Generation)
- **Requirement ID**: [e.g., REQ-001]
- **Requirement Version ID**: [e.g., v1.0]
- **Status**: [Draft / Refined / Approved / Deprecated]
- **Type**: Functional
- **Priority**: [Critical / High / Medium / Low]
- **Description**: [What the capability allows the persona to achieve]
- **Resolves Friction**: [Explicitly state the `107` friction this solves, or 'None']
- **Protects Moment of Truth**: [Yes / No]
- **Acceptance Criteria**: 
  - [Condition 1 that must be met]
  - [Condition 2 that must be met]
- **Parent Journey ID**: [e.g., JRN-FUT-001]
- **Parent Step ID**: [e.g., STEP-003]
- **Parent JTBD ID**: [e.g., JTBD-001]
- **Parent Persona ID**: [e.g., PER-001]
- **Principle Constraint**: [e.g., "Must prioritize security over speed"]

*(Repeat Capability Card for each functional requirement)*

# 6. Non-Functional Capabilities (NFRs)
[The specific constraints regarding performance, security, and compliance needed to protect the system.]

## [NFR Title] (e.g., Confidential and Auditable Data Workflows)
- **Requirement ID**: [e.g., REQ-050]
- **Requirement Version ID**: [e.g., v1.0]
- **Status**: [Draft / Refined / Approved / Deprecated]
- **Type**: [Non-Functional / Compliance / Security / Data / Operational / Accessibility]
- **Priority**: [Critical / High / Medium / Low]
- **Description**: [e.g., Protected health data must remain confidential, auditable, and access-controlled across all relevant workflows.]
- **Resolves Friction**: [None]
- **Protects Moment of Truth**: [Yes / No]
- **Acceptance Criteria**: 
  - [Condition 1 that must be met]
  - [Condition 2 that must be met]
- **Parent Journey ID**: [System-wide or JRN-FUT-001]
- **Parent Step ID**: [System-wide or STEP-003]
- **Parent JTBD ID**: [e.g., JTBD-001]
- **Parent Persona ID**: [e.g., PER-001]
- **Parent STK-ID**: [e.g., STK-005]
- **Principle Constraint**: [Which Principle governs this?]

*(Repeat Capability Card for each NFR)*

<!-- SECTION GROUP: Governance -->

# 7. Traceability Matrix
[A summary table mapping `REQ-ID` -> `STEP-ID` (Journey) -> `JTBD-ID` (Job) to prove no orphan requirements exist.]

# 8. AI Context
[Special instructions for downstream AI agents reading this file. Example: "When generating Success Metrics from this artifact, focus heavily on the Acceptance Criteria of Critical Priority Capabilities."]
