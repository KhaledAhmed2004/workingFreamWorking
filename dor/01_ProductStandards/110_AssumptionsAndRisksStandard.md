---
Title: 110_AssumptionsAndRisksStandard
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
- Every Risk MUST define an Initial Risk Score (Impact × Likelihood) and a Residual Risk Score.

### Quality Gates
- **QG-RISK-001**: Reject if a High-Impact, High-Likelihood Risk lacks a documented Mitigation Plan.
- **QG-RISK-002**: Reject if an Assumption is stated without a measurable Validation Plan.
- **QG-RISK-003**: Reject if a Risk is purely speculative without tracing to a specific Discovery artifact (e.g., tracing a privacy risk to a specific Requirement).
- **QG-RISK-004**: Reject if a High Risk has no Trigger.
- **QG-RISK-005**: Reject if a High Impact Risk has no Owner.

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
- **Category**: (Adoption / Regulatory / Privacy / Integration / Clinical / Operational / Technical / Dependency / Vendor / Third Party / Legal)
- **Description**: (What we assume, or what could go wrong)
- **Impact**: (Numeric 1-5 scale)
- **Likelihood**: (Numeric 1-5 scale) *[For Risks Only]*
- **Initial Risk Score**: (Impact × Likelihood, e.g., 25 - Critical) *[For Risks Only]*
- **Confidence**: (Validated / High / Medium / Low / Unknown) *[For Assumptions Only]*
- **Trigger**: (What event activates this risk?) *[For Risks Only]*
- **Early Warning Indicators**: (Signals before the risk materializes, e.g., "Retention drops below 50%") *[For Risks Only]*
- **Owner**: (Who is responsible for validation/mitigation?)
- **Validation / Mitigation Plan**: (Actionable steps to prove the assumption or prevent the risk)
- **Residual Risk Score**: (Score after mitigation is applied) *[For Risks Only]*
- **Status**: (Open / Validated / Invalidated / Mitigated / Accepted)
- **Last Reviewed Date**: (YYYY-MM-DD)
- **Next Review Date**: (YYYY-MM-DD)
- **Traces To**: (One or more source IDs from `100`, `101`, `102`, `103`, `104`, `105`, `106`, `107`, `108`, `109`)

## 4. Output Contract
To guarantee deterministic AI orchestration, this artifact explicitly produces the following machine-readable assets for downstream nodes:
- **Assumption Register** (Used by Research & Design)
- **Architecture Risk Register** (Used by Architecture & Compliance)
- **Validation Plan** (Used by Product Operations)
- **Mitigation Plan** (Used by Engineering)
- **Decision Log Inputs**
- **Release Gates** (Conditions that block release if residual risk is too high)

## 5. Traceability
Every Risk and Assumption MUST trace back to the Discovery artifact it impacts:
- MUST trace to one or more source IDs from: `100`, `101`, `102`, `103`, `104`, `105`, `106`, `107`, `108`, `109`.

## 6. Context & AI Prompts
### Hydration Rules
- AI Swarms MUST scan the entire `100-109` corpus to identify implicit assumptions (e.g., assuming a user has cellular data in a Journey) and force them to be explicitly registered in `110`.
- AI MUST automatically flag any Regulatory or Privacy risks based on the domain (e.g., Healthcare data requirements).
- AI MUST calculate the Initial Risk Score by multiplying Impact and Likelihood.

### Memory TTL
- `Permanent` for the duration of the entire Product Lifecycle (Risks persist into Delivery).

## 7. Anti-Patterns
- **The Empty Risk**: "The app might fail" (Too broad, no specific trigger or warning indicator).
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
