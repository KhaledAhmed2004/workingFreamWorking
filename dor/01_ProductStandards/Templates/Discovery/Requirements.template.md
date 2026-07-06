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
Depends On: [Principles Artifact ID], [Journey Artifact ID]
Next Artifact: [Success Metrics Document]
---

<!-- SECTION GROUP: Discovery Core -->

# 1. Executive Summary
[A high-level summary of the core capabilities required to build the Future State Journeys defined in this product ecosystem.]

# 2. Purpose
[Define the intent of this Requirements document. How will it be used by Engineering and Product Management?]

# 3. Scope
[Define the boundaries. Which Epics or systems are explicitly included or excluded from this scope?]

<!-- SECTION GROUP: Requirements Hierarchy -->

# 4. Epics Overview
[A high-level list of the major capability clusters (Epics) that map to the Journey Phases.]

## [Epic Name] (e.g., Epic 1: Automated Shift Handoff)
- **Description**: [Summary of the Epic]
- **Target Journey Phase**: [Map to a phase in `107`]

# 5. Functional Capabilities
[The specific functional requirements needed to resolve frictions and enable the Journeys. Grouped by Epic.]

## Epic: [Epic Name]

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
- **Traces To**: [e.g., STEP-003, STEP-004]

*(Repeat Capability Card for each functional requirement)*

# 6. Non-Functional Capabilities (NFRs)
[The specific constraints regarding performance, security, and compliance needed to protect the system.]

## [NFR Title] (e.g., HIPAA Compliant Data Encryption)
- **Requirement ID**: [e.g., REQ-050]
- **Requirement Version ID**: [e.g., v1.0]
- **Status**: [Draft / Refined / Approved / Deprecated]
- **Type**: [Non-Functional / Compliance / Security]
- **Priority**: [Critical / High / Medium / Low]
- **Description**: [What the system must uphold]
- **Resolves Friction**: [None]
- **Protects Moment of Truth**: [Yes / No]
- **Acceptance Criteria**: 
  - [Condition 1 that must be met]
  - [Condition 2 that must be met]
- **Traces To**: [Which Steps or Epics this applies to, or 'System-wide']

*(Repeat Capability Card for each NFR)*

<!-- SECTION GROUP: Governance -->

# 7. Traceability Matrix
[A summary table mapping `REQ-ID` -> `STEP-ID` (Journey) -> `JTBD-ID` (Job) to prove no orphan requirements exist.]

# 8. AI Context
[Special instructions for downstream AI agents reading this file. Example: "When generating Success Metrics from this artifact, focus heavily on the Acceptance Criteria of Critical Priority Capabilities."]
