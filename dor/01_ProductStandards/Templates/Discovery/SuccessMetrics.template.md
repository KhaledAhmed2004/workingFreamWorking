---
Title: [Product Name] Success Metrics Registry
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
Depends On: [Goal Artifact ID], [Journey Artifact ID], [Requirements Artifact ID]
Next Artifact: [Assumptions & Risks Document]
---

<!-- SECTION GROUP: Discovery Core -->

# 1. Executive Summary
[A high-level summary of how the product will quantitatively and qualitatively measure its success.]

# 2. Purpose
[Define the intent of this Metrics Document. How will it govern the evaluation of delivered capabilities?]

# 3. Scope
[Define the boundaries. Are we measuring a specific pilot phase, or the overall GA launch?]

<!-- SECTION GROUP: Metrics Registry -->

# 4. The North Star Metric
[The single, overarching metric that best captures the core value delivered to customers by this product.]

## [North Star Metric Name]
- **Metric ID**: [e.g., MET-001]
- **Metric Version ID**: [e.g., v1.0]
- **Status**: [Active / Deprecated / Candidate]
- **Category**: North Star
- **Description**: [What is being measured and why it matters]
- **Baseline**: [Current state value. e.g., 'Unknown']
- **Target**: [The threshold for success]
- **Measurement Method**: [How data is collected]
- **Owner**: [Who is accountable?]
- **Traces To**: [e.g., GOAL-001]
- **Guarded By**: [e.g., MET-005, MET-006]

# 5. Primary KPIs
[Direct leading or lagging indicators that map to the specific Product Goals (`102`).]

## [KPI Name]
- **Metric ID**: [e.g., MET-002]
- **Metric Version ID**: [...]
- **Status**: [...]
- **Category**: Primary KPI
- **Description**: [...]
- **Baseline**: [...]
- **Target**: [...]
- **Measurement Method**: [...]
- **Owner**: [...]
- **Traces To**: [e.g., GOAL-002]
- **Guarded By**: [...]

*(Repeat Metric Card for each Primary KPI)*

# 6. Capability & Journey Metrics
[Granular signals ensuring a specific capability (`108`) or Moment of Truth (`107`) is functioning as intended.]

## [Metric Name]
- **Metric ID**: [e.g., MET-003]
- **Metric Version ID**: [...]
- **Status**: [...]
- **Category**: Capability Metric
- **Description**: [...]
- **Baseline**: [...]
- **Target**: [...]
- **Measurement Method**: [...]
- **Owner**: [...]
- **Traces To**: [e.g., STEP-003, REQ-005]
- **Guarded By**: [N/A]

*(Repeat Metric Card for each Capability/Journey Metric)*

# 7. Guardrail Metrics
[Counter-metrics ensuring we do not achieve success at the expense of system health, safety, or compliance.]

## [Guardrail Name]
- **Metric ID**: [e.g., MET-004]
- **Metric Version ID**: [...]
- **Status**: [...]
- **Category**: Guardrail
- **Description**: [e.g., "Error rate must not increase despite faster handoffs"]
- **Baseline**: [...]
- **Target**: [...]
- **Measurement Method**: [...]
- **Owner**: [...]
- **Traces To**: [e.g., REQ-050]
- **Guarded By**: [N/A]

*(Repeat Metric Card for each Guardrail Metric)*

<!-- SECTION GROUP: Governance -->

# 8. Measurement Plan
[A summary of the telemetry, systems, and research cadences required to actually collect this data. Identify any gaps in current data collection capabilities.]

# 9. Traceability Matrix
[A summary table mapping `MET-ID` -> `GOAL-ID` / `REQ-ID` / `STEP-ID` to prove no metric exists in a vacuum.]

# 10. AI Context
[Special instructions for downstream AI agents reading this file. Example: "When generating Risk logs from this artifact, explicitly evaluate the technical feasibility of the Measurement Plan."]
