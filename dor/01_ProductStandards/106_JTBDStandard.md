---
Title: 106_JTBDStandard
Artifact Version: 1.0
Framework Version: 1.0
Supersedes: N/A
Status: Draft
Phase: Product Standards Infrastructure
Sprint: N/A
Owner: Product Architecture Board
Reviewer: Enterprise Architecture Review Board
Approver: Executive Board
Created: 2026-07-06
Updated: 2026-07-06
Approval Date: N/A
Last Reviewed: N/A
Review Status: N/A
Artifact ID: PS-106
Depends On: 101_ProblemStandard.md, 105_PersonaStandard.md
Extends: 050_ProductStandardContract.md
Base Contract: 050_ProductStandardContract.md
Template Path: 01_ProductStandards/Templates/Discovery/JTBD.template.md
Next Artifact: 107_JourneyStandard.md
---

# Jobs-To-Be-Done (JTBD) Standard

## 1. Definition
The `106_JTBDStandard` dictates how to define solution-agnostic user needs. It separates the *underlying need* from the *proposed solution*. 

**Crucial Enterprise Architectural Rule:**
- **Personas do NOT own Jobs.** 
- **Jobs are independent entities.** 
- **Personas *perform* Jobs.**

By modeling Jobs independently, the framework allows multiple Personas to share the same JTBD, drastically improving scalability and reducing duplication in `107_Journey` and `108_Requirements`.

## 2. Validation & Quality Gates
Artifacts following this standard MUST pass these checks:

### Validation Rules
- No orphan Jobs. Every Job MUST trace back to a root cause in `101_ProblemStandard`.
- Every Job MUST be mapped to at least one Persona ID (`PER-ID`) from `105`.
- Every Job MUST have a unique `JTBD-ID` (e.g., JTBD-001).

### Quality Gates
- **QG-JTBD-001**: Reject if a Job statement contains a specific feature, technology, or UI solution (e.g., "I want a dashboard" vs "I want to see my patient's status at a glance").
- **QG-JTBD-002**: Reject if a Job lacks clear emotional or social dimensions.
- **QG-JTBD-003**: Reject if the Job is phrased from the Persona's explicit identity rather than the situational context (e.g., use "When preparing medication..." NOT "Clinical Clara needs...").

## 3. Core Components

### 3.1 JTBD Metadata Schema (The Job Card)
Every Job MUST be modeled with this strict schema:
- **JTBD ID**: (e.g., JTBD-001)
- **Job Version ID**: (e.g., v1.0, v1.1)
- **Job Status**: (Active / Candidate / Merged / Archived)
- **Performed By**: (Array of `PER-ID`s, e.g., PER-001, PER-002)
- **Job Statement**: The core syntax -> "When [situation], I want to [motivation], so I can [expected outcome]."
- **Functional Need**: (What practical task must be accomplished)
- **Emotional Need**: (How the persona wants to feel while doing it)
- **Social Need**: (How the persona wants to be perceived by others)
- **Current Friction**: (Why is this hard today? Mapped from `105` Frictions)
- **Success Metric**: (How we objectively know the job is done well)

## 4. Output Contract
To guarantee deterministic AI orchestration, this artifact explicitly produces the following machine-readable assets for downstream nodes:
- **JTBD Registry** (Used by `107_Journey` and `108_Requirements`)
- **Functional Needs Matrix** (Used by `108_Requirements`)
- **Success Metrics Baseline** (Used by `109_SuccessMetrics`)

## 5. Traceability
Every JTBD MUST trace back to:
- **Performed By**: (`PER-ID` from `105_PersonaStandard.md`)
- **Problem Root Cause**: (Which pain point from `101` does this job address?)

## 6. Context & AI Prompts
### Hydration Rules
- AI Swarms MUST NOT invent Jobs that do not explicitly solve a `101` Problem or serve a `105` Persona's goals.
- AI MUST write the Job Statement strictly in the "When... I want to... So I can..." format.
- AI MUST enforce the separation of Job and Persona. 

### Memory TTL
- `Permanent` for the duration of the Solution Context Layer generation.

## 7. Anti-Patterns
- **The Solution in Disguise**: Writing "When I want to export to CSV..." instead of "When I need to share data with compliance...".
- **The Empty Emotion**: Writing "I want to feel good" instead of "I want to feel confident that I haven't made a clinical error."
- **Persona-Centric Naming**: Calling a job "Nurse's Morning Routine" instead of "Shift Handoff Status Review".

## 8. Section Registry (Template Contract)
Every JTBD artifact MUST use these exact headings.

<!-- SECTION GROUP: Discovery Core -->
- # 1. Executive Summary
- # 2. Purpose
- # 3. Scope

<!-- SECTION GROUP: JTBD Registry -->
- # 4. Primary Jobs
- # 5. Secondary Jobs
- # 6. Related Jobs

<!-- SECTION GROUP: Needs Analysis -->
- # 7. Functional Needs Summary
- # 8. Emotional & Social Needs Summary

<!-- SECTION GROUP: Governance -->
- # 9. Traceability
- # 10. AI Context
