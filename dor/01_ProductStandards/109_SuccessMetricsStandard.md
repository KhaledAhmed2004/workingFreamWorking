---
Title: 109_SuccessMetricsStandard
Artifact Version: 1.0
Framework Version: 1.0
Supersedes: N/A
Status: Frozen
Phase: Product Standards Infrastructure
Sprint: N/A
Owner: Product Architecture Board
Reviewer: Enterprise Architecture Review Board
Approver: Executive Board
Created: 2026-07-06
Updated: 2026-07-06
Approval Date: 2026-07-06
Last Reviewed: 2026-07-06
Review Status: Approved
Artifact ID: PS-109
Depends On: 102_ProductGoalStandard.md, 103_ProductPrinciplesStandard.md, 107_JourneyStandard.md, 108_RequirementsStandard.md
Extends: 050_ProductStandardContract.md
Base Contract: 050_ProductStandardContract.md
Template Path: 01_ProductStandards/Templates/Discovery/SuccessMetrics.template.md
Next Artifact: 110_AssumptionsAndRisksStandard.md
---

# Success Metrics Standard

## 1. Definition
The `109_SuccessMetricsStandard` establishes the quantitative and qualitative governance for the product. It translates abstract goals and capabilities into measurable KPIs.

**Crucial Enterprise Architectural Rule:**
- **Success Metric = Measurable evidence that a Goal (`102`), Requirement (`108`), or Moment of Truth (`107`) is actually working in production.**

## 2. Validation & Quality Gates
Artifacts following this standard MUST pass these checks:

### Validation Rules
- No vanity metrics (e.g., "Total registered users" without context). Every metric MUST be actionable.
- Every metric MUST trace to at least one upstream artifact (`102`, `107`, or `108`).
- The North Star Metric MUST trace directly to the North Star Metric defined in `100_VisionStandard`.
- Every metric MUST have a defined baseline, target, and measurement method.

### Quality Gates
- **QG-MET-001**: Reject if a metric cannot be objectively measured using an identified data source or research method.
- **QG-MET-002**: Reject if the metric contradicts the `103_ProductPrinciplesStandard` (e.g., maximizing engagement when the principle is 'minimize time-in-app').
- **QG-MET-003**: Reject if a Guardrail Metric is missing for any Primary KPI that poses a safety, compliance, or severe UX risk if over-optimized.
- **QG-MET-004**: Reject if any Primary KPI has no Guardrail Metric.
- **QG-MET-005**: Reject if Measurement Method exists but Data Source is undefined.

## 3. Core Components

### 3.1 Metrics Taxonomy
1. **North Star Metric**: The single metric that best captures the core value delivered to customers.
2. **Primary KPI**: Direct leading/lagging indicators mapping to Product Goals (`102`).
3. **Capability / Journey Metric**: Granular signals ensuring a specific capability (`108`) or Moment of Truth (`107`) is functioning as intended.
4. **Guardrail Metric**: A counter-metric ensuring we do not achieve success at the expense of system health, safety, or compliance (e.g., "Increase speed" guarded by "Error rate must not increase").

### 3.2 Metric Metadata Schema (The Metric Card)
Every Metric MUST be modeled with this strict schema:
- **Metric ID**: (e.g., MET-001)
- **Metric Version ID**: (e.g., v1.0)
- **Status**: (Active / Deprecated / Candidate)
- **Category**: (North Star / Primary KPI / Capability Metric / Guardrail)
- **Metric Type**: (Leading / Lagging)
- **Name**: (e.g., "Handoff Error Rate")
- **Description**: (What is being measured and why it matters)
- **Baseline**: (Current state value. Use '0' or 'Unknown' if net-new)
- **Target**: (The threshold for success)
- **Measurement Method**: (How data is collected, e.g., Auto-tracking, Monthly Survey)
- **Collection Frequency**: (Real-time / Daily / Weekly / Monthly / Quarterly)
- **Data Source**: (System Logs / Survey / Analytics / Manual Audit / Research)
- **Owner**: (Who is accountable for monitoring this? e.g., Clinical PM)
- **Risk of Misuse**: (How this metric could be gamed or misinterpreted)
- **Traces To**: (Array of IDs from `100`, `102`, `107`, or `108`)
- **Guarded By**: (Array of `MET-ID`s, if this is a Primary KPI)

## 4. Output Contract
To guarantee deterministic AI orchestration, this artifact explicitly produces the following machine-readable assets for downstream nodes:
- **Metrics Registry** (Used by Data Engineering to build telemetry pipelines)
- **Guardrail Matrix** (Used by `110_AssumptionsAndRisks` to manage operational risk)
- **Measurement Plan** (Used by Product Operations)

## 5. Traceability
Every Metric MUST trace back to its strategic or operational origin:
- **Parent Vision**: (`VIS-ID` from `100_VisionStandard.md`)
- **Parent Goal**: (`GOAL-ID` from `102_ProductGoalStandard.md`)
- **Parent Moment of Truth**: (`STEP-ID` from `107_JourneyStandard.md`)
- **Parent Requirement**: (`REQ-ID` from `108_RequirementsStandard.md`)

## 6. Context & AI Prompts
### Hydration Rules
- AI Swarms MUST parse the Acceptance Criteria of Critical Capabilities (`108`) to generate corresponding Capability Metrics.
- AI MUST ensure every Product Goal (`102`) has at least one matching Primary KPI.
- AI MUST automatically propose Guardrail metrics for any KPI that risks compromising system stability or compliance.

### Memory TTL
- `Permanent` for the duration of the Discovery Phase.

## 7. Anti-Patterns
- **The Unmeasurable Metric**: Defining a target like "Improve user happiness" without defining the survey instrument or proxy metric (e.g., NPS, Task Success Rate).
- **The Siloed Metric**: Creating a KPI that doesn't trace back to a Goal or Requirement, indicating scope creep.
- **The Metric Explosion**: Defining 50 Primary KPIs instead of focusing on the critical few that drive the North Star.

## 8. Section Registry (Template Contract)
Every Success Metrics artifact MUST use these exact headings.

<!-- SECTION GROUP: Discovery Core -->
- # 1. Executive Summary
- # 2. Purpose
- # 3. Scope

<!-- SECTION GROUP: Metrics Registry -->
- # 4. The North Star Metric
- # 5. Primary KPIs
- # 6. Capability & Journey Metrics
- # 7. Guardrail Metrics

<!-- SECTION GROUP: Governance -->
- # 8. Measurement Plan
- # 9. Traceability Matrix
- # 10. AI Context
