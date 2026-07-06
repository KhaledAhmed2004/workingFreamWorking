---
Title: [Product Name] Jobs-To-Be-Done Registry
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
Depends On: [Problem Artifact ID], [Persona Artifact ID]
Next Artifact: [Journey Document]
---

<!-- SECTION GROUP: Discovery Core -->

# 1. Executive Summary
[A high-level summary of the critical jobs the product is being hired to do.]

# 2. Purpose
[Define the intent of this JTBD Registry. How does it shift focus from features to outcomes?]

# 3. Scope
[Define which problem spaces are covered by these jobs and which are intentionally excluded.]

<!-- SECTION GROUP: JTBD Registry -->

# 4. Primary Jobs
[The core, non-negotiable tasks the product must accomplish to be considered successful.]

## [Job Name] (e.g., Shift Handoff Status Review)
- **JTBD ID**: [e.g., JTBD-001]
- **Job Version ID**: [e.g., v1.0]
- **Job Status**: [Active / Candidate / Merged / Archived]
- **Performed By**: [e.g., PER-001, PER-002] (Must map to `105`)
- **Job Statement**: When [situation], I want to [motivation], so I can [expected outcome].
- **Functional Need**: [What practical task must be accomplished]
- **Emotional Need**: [How the persona wants to feel while doing it]
- **Social Need**: [How the persona wants to be perceived by others]
- **Current Friction**: [Why is this hard today?]
- **Success Metric**: [How we objectively know the job is done well]

*(Repeat Job Card for each Primary Job)*

# 5. Secondary Jobs
[Supporting tasks that improve the primary job experience but are not the main driver of adoption.]

## [Job Name]
- **JTBD ID**: [e.g., JTBD-002]
- **Job Version ID**: [...]
- **Job Status**: [...]
- **Performed By**: [...]
- **Job Statement**: When [situation], I want to [motivation], so I can [expected outcome].
- **Functional Need**: [...]
- **Emotional Need**: [...]
- **Social Need**: [...]
- **Current Friction**: [...]
- **Success Metric**: [...]

*(Repeat Job Card for each Secondary Job)*

# 6. Related Jobs
[Adjacent tasks that the persona performs but that our product may intentionally choose not to solve (useful for scoping and partnerships).]

## [Job Name]
- **JTBD ID**: [e.g., JTBD-003]
- **Job Version ID**: [...]
- **Job Status**: [...]
- **Performed By**: [...]
- **Job Statement**: When [situation], I want to [motivation], so I can [expected outcome].
- **Reason for Exclusion**: [Why are we not building this?]

<!-- SECTION GROUP: Needs Analysis -->

# 7. Functional Needs Summary
[A synthesized view of the top macro functional requirements across all jobs. e.g., "Real-time sync is required across 80% of Primary Jobs."]

# 8. Emotional & Social Needs Summary
[A summary of the core emotional drivers that UX/UI must address. e.g., "Confidence and risk-aversion dominate the emotional needs."]

<!-- SECTION GROUP: Governance -->

# 9. Traceability
[Link each Job explicitly back to `PER-ID`s and the Problem Statement root causes.]

# 10. AI Context
[Special instructions for downstream AI agents reading this file. Example: "When generating Journeys from this artifact, ensure the steps map directly to resolving the Current Friction listed in the Primary Jobs."]
