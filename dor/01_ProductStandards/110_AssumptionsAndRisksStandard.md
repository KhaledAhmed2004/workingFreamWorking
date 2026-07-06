---
Title: 110_AssumptionsAndRisksStandard
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
Artifact ID: PS-110
Depends On: 100_VisionStandard.md, 101_ProblemStandard.md, 102_ProductGoalStandard.md, 103_ProductPrinciplesStandard.md, 104_StakeholderStandard.md, 105_PersonaStandard.md, 106_JTBDStandard.md, 107_JourneyStandard.md, 108_RequirementsStandard.md, 109_SuccessMetricsStandard.md
Extends: 050_ProductStandardContract.md
Base Contract: 050_ProductStandardContract.md
Template Path: 01_ProductStandards/Templates/Discovery/AssumptionsAndRisks.template.md
Next Artifact: 111_DiscoveryFreezeStandard.md
---

# Assumptions & Risks Standard

## 1. Definition
The `110_AssumptionsAndRisksStandard` systematically documents what we believe to be true (Assumptions) and what could threaten the product (Risks) across the entire Discovery DAG. It acts as the final governance check before the Discovery Freeze.

**Crucial Enterprise Architectural Rule:**
- **Assumptions and Risks are NOT features. They are operational, clinical, regulatory, or technical uncertainties that must be validated or mitigated.**

## 2. Validation & Quality Gates
Artifacts following this standard MUST pass these checks:

### Validation Rules
- Every Assumption MUST have a specific Validation Plan.
- Every Risk MUST have a specific Mitigation Plan.
- Every entry MUST have an Owner.
- Every entry MUST define its Impact and Likelihood/Confidence.

### Quality Gates
- **QG-RISK-001**: Reject if a High-Impact, High-Likelihood Risk lacks a documented Mitigation Plan.
- **QG-RISK-002**: Reject if an Assumption is stated without a measurable Validation Plan.
- **QG-RISK-003**: Reject if a Risk is purely speculative without tracing to a specific Discovery artifact (e.g., tracing a privacy risk to a specific Requirement).

## 3. Core Components

### 3.1 Assumptions
Assumptions are foundational hypotheses we are treating as facts to proceed, but which require explicit validation.
*Examples:* "Patients have smartphones", "Hospitals allow digital workflows", "Internet connectivity exists".

### 3.2 Risks
Risks are potential threats to the product's success, safety, or compliance.
*Examples:* Patient adoption risk, Regulatory risk, Privacy risk, Clinical liability, Operational risk, Data quality risk, AI hallucination risk.

### 3.3 Metadata Schema (The Validation Card)
Every Assumption or Risk MUST be modeled with this strict schema:
- **ID**: (e.g., ASM-001 or RISK-001)
- **Type**: (Assumption / Risk)
- **Category**: (Adoption / Regulatory / Privacy / Integration / Clinical / Operational / Technical)
- **Description**: (What we assume, or what could go wrong)
- **Impact**: (High / Medium / Low)
- **Likelihood / Confidence**: (High / Medium / Low) - *Likelihood for Risks, Confidence for Assumptions*
- **Owner**: (Who is responsible for validation/mitigation?)
- **Validation / Mitigation Plan**: (Actionable steps to prove the assumption or prevent the risk)
- **Traces To**: (Array of IDs from ANY previous Discovery artifact, e.g., `REQ-010`, `MET-002`)
- **Status**: (Open / Validated / Invalidated / Mitigated / Accepted)

## 4. Output Contract
To guarantee deterministic AI orchestration, this artifact explicitly produces the following machine-readable assets for downstream nodes:
- **Assumption Register** (Used by Research & Design)
- **Risk Register** (Used by Architecture & Compliance)
- **Validation Plan** (Used by Product Operations)
- **Mitigation Plan** (Used by Engineering)

## 5. Traceability
Every Risk and Assumption MUST trace back to the Discovery artifact it impacts:
- Can trace to ANY node in the DAG (`100` to `109`), using specific IDs (e.g., `GOAL-001`, `PER-002`, `JRN-003`).

## 6. Context & AI Prompts
### Hydration Rules
- AI Swarms MUST scan the entire `100-109` corpus to identify implicit assumptions (e.g., assuming a user has cellular data in a Journey) and force them to be explicitly registered in `110`.
- AI MUST automatically flag any Regulatory or Privacy risks based on the domain (e.g., Healthcare data requirements).

### Memory TTL
- `Permanent` for the duration of the entire Product Lifecycle (Risks persist into Delivery).

## 7. Anti-Patterns
- **The Empty Risk**: "The app might fail" (Too broad, no specific impact or mitigation).
- **The Unowned Assumption**: Documenting a critical business assumption without assigning an owner to validate it.
- **The Hidden Feature**: Using the Mitigation Plan to define a brand new feature instead of tracing back to `108` and adding a new Requirement.

## 8. Section Registry (Template Contract)
Every Assumptions & Risks artifact MUST use these exact headings.

<!-- SECTION GROUP: Discovery Core -->
- # 1. Executive Summary
- # 2. Purpose
- # 3. Scope

<!-- SECTION GROUP: Registers -->
- # 4. Assumption Register
- # 5. Risk Register

<!-- SECTION GROUP: Governance -->
- # 6. Validation & Mitigation Plan
- # 7. Traceability Matrix
- # 8. AI Context
