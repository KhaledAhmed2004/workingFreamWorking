---
Title: 107_JourneyStandard
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
Artifact ID: PS-107
Depends On: 101_ProblemStandard.md, 103_ProductPrinciplesStandard.md, 105_PersonaStandard.md, 106_JTBDStandard.md
Extends: 050_ProductStandardContract.md
Base Contract: 050_ProductStandardContract.md
Template Path: 01_ProductStandards/Templates/Discovery/Journey.template.md
Next Artifact: 108_RequirementsStandard.md
---

# Journey Standard

## 1. Definition
The `107_JourneyStandard` maps how a Persona currently performs a Job (Current State) or how they will perform it (Future State). It acts as the bridge between abstract user needs (`106`) and concrete product capabilities (`108`).

**Crucial Enterprise Architectural Rule:**
- **Journey = Persona performs JTBD over time across touchpoints.**

## 2. Validation & Quality Gates
Artifacts following this standard MUST pass these checks:

### Validation Rules
- No orphan Journeys.
- Every Journey Pair MUST map to exactly one `JTBD-ID`.
- Every Journey MUST be performed by exactly one primary `PER-ID`.
- Every step within the journey MUST have a stable `STEP-ID` and define an emotional valence (Positive / Negative / Neutral).
- Every Journey MUST identify at least one "Moment of Truth".

### Quality Gates
- **QG-JRN-001**: Reject if a Journey introduces a new macro-goal or motivation not found in the parent `JTBD-ID`.
- **QG-JRN-002**: Reject if a Future State Journey contains Current State frictions defined in `106` without explicitly proposing a resolution.
- **QG-JRN-003**: Reject if the Journey steps contradict the constraints established in `103_ProductPrinciplesStandard`.
- **QG-JRN-004**: Reject if the Journey lacks touchpoint definitions (e.g., ignoring whether a step happens physically or digitally).
- **QG-JRN-005**: Reject if a Future State Journey includes UI-specific or implementation-specific details (e.g., button names, dashboard screens). Wording must remain solution-neutral.
- **QG-JRN-006**: Reject if any journey step lacks a `Step ID`.

## 3. Core Components

### 3.1 Journey Metadata Schema (The Journey Header)
Every Journey MUST be modeled with this strict schema:
- **Journey Pair ID**: (e.g., JPAIR-001) - Links the Current and Future state of the same flow.
- **Current Journey ID**: (e.g., JRN-CUR-001)
- **Future Journey ID**: (e.g., JRN-FUT-001)
- **Journey Version ID**: (e.g., v1.0, v1.1)
- **Journey Status**: (Active / Candidate / Merged / Archived)
- **Parent JTBD**: (`JTBD-ID`)
- **Performed By**: (`PER-ID`)
- **Trigger**: (The specific event that initiates this journey)
- **Outcome**: (How it concludes, which MUST map to the JTBD Success Metric)
- **Evidence Source**: (e.g., Observational Study, Support Ticket Logs)
- **Confidence Level**: (Validated / High / Medium / Low)

### 3.2 Phase & Step Schema
Journeys are divided into domain-flexible Phases (e.g., rather than forcing generic "Awareness/Consideration", healthcare might use "Admission/Triage/Treatment"). Each Phase contains sequential Steps with the following schema:
- **Step ID**: (e.g., STEP-001) - Stable reference for downstream `108` Requirements tracing.
- **Step Name**: (e.g., "Nurse verifies patient ID")
- **Touchpoint**: (Where this happens, e.g., Kiosk, Mobile App, Physical Desk)
- **Emotional Valence**: (Positive / Negative / Neutral)
- **Friction**: (Any blockers experienced at this specific step)
- **Moment of Truth**: (Boolean: Yes/No. Is this step make-or-break for adoption?)

## 4. Output Contract
To guarantee deterministic AI orchestration, this artifact explicitly produces the following machine-readable assets for downstream nodes:
- **Journey Steps Array** (Used by `108_Requirements` to generate Epics/Features)
- **Moments of Truth Matrix** (Used by `109_SuccessMetrics` for SLA definition)
- **Touchpoint Inventory** (Used by Architecture for system mapping)
- **Friction Log** (Used by `110_AssumptionsAndRisks`)

## 5. Traceability
Every Journey MUST trace back to:
- **Parent JTBD**: (`JTBD-ID` from `106_JTBDStandard.md`)
- **Persona**: (`PER-ID` from `105_PersonaStandard.md`)
- **Principle Constraint**: (Which Trade-off in `103` governed the Future State design?)

## 6. Context & AI Prompts
### Hydration Rules
- AI Swarms MUST synthesize Future State journeys by logically resolving the "Current Friction" from the hydrated `106` Job Card.
- AI MUST ensure the Journey's "Outcome" directly satisfies the "Success Metric" of the parent Job.
- AI MUST NOT hallucinate steps that require capabilities explicitly forbidden by the `103_ProductPrinciplesStandard`.
- AI MUST maintain strict solution-neutrality in Future State wording.

### Memory TTL
- `Permanent` for the duration of the Solution Context Layer generation.

## 7. Anti-Patterns
- **The Feature Pitch**: Using the Journey to prematurely list UI buttons and APIs instead of user actions and experiences (that belongs in `108`).
- **The Emotionless Map**: Focusing purely on physical clicks and ignoring the cognitive/emotional load of the Persona.
- **The Omnipresent Persona**: Creating a Journey where one Persona performs steps that actually belong to a Secondary Persona (e.g., blending Patient and Doctor actions into one flow).

## 8. Section Registry (Template Contract)
Every Journey artifact MUST use these exact headings.

<!-- SECTION GROUP: Discovery Core -->
- # 1. Executive Summary
- # 2. Purpose
- # 3. Scope

<!-- SECTION GROUP: Journey Mapping -->
- # 4. Current State Journeys
- # 5. Future State Journeys

<!-- SECTION GROUP: Journey Analysis -->
- # 6. Moments of Truth Matrix
- # 7. Touchpoint Inventory
- # 8. Resolved Frictions

<!-- SECTION GROUP: Governance -->
- # 9. Traceability
- # 10. AI Context
