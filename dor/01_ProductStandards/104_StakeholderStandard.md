---
Title: 104_StakeholderGovernanceStandard
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
Artifact ID: PS-104
Depends On: 100_VisionStandard.md, 101_ProblemStandard.md, 102_ProductGoalStandard.md, 103_ProductPrinciplesStandard.md
Extends: 050_ProductStandardContract.md
Base Contract: 050_ProductStandardContract.md
Template Path: 01_ProductStandards/Templates/Discovery/Stakeholder.template.md
Next Artifact: 105_PersonaStandard.md
---

# Stakeholder Governance Standard

## 1. Definition
The `104_StakeholderGovernanceStandard` is the root node of the Human Context Layer. It defines a rigid, enterprise-grade governance structure for cataloging every human, system, and regulatory entity impacted by the product. This standard prevents downstream duplication in `105_Persona` and `107_Journey` by acting as the single source of truth for the Stakeholder Registry, Influence Model, and Conflict Matrix.

## 2. Validation & Quality Gates
Artifacts following this standard MUST pass these checks:

### Validation Rules
- No orphan stakeholder.
- No duplicated stakeholder roles.
- Every stakeholder MUST have measurable success criteria.
- Every stakeholder MUST have an influence classification (Power/Interest).
- Every Primary Stakeholder MUST trace to a minimum of one downstream Persona (`105`).
- Every downstream Persona MUST map back to exactly one Primary or Secondary Stakeholder defined here.

### Quality Gates
- **QG-STAKE-001**: Reject if any stakeholder cannot trace back to the Problem or Goals.
- **QG-STAKE-002**: Reject if the Power/Interest Matrix is incomplete for identified Primary stakeholders.
- **QG-STAKE-003**: Reject if the stakeholder registry contains duplicate roles or undefined ownership/authority.
- **QG-STAKE-004**: Reject if any Primary Stakeholder has no measurable objective.

## 3. Core Components

### 3.1 Stakeholder Classification Taxonomy
Every stakeholder must be strictly classified into one of these types:
1. **Primary**: Direct users or buyers.
2. **Secondary**: Admins, support, or internal operators.
3. **Tertiary**: Indirect beneficiaries.
4. **Adversarial**: Fraudsters, malicious actors.
5. **Operational**: Maintenance, DevOps, infrastructure teams.
6. **Strategic**: Executives, investors, sponsors.
7. **Regulatory**: Government bodies, compliance auditors.
8. **External Partner**: Integrated vendors, API consumers.
9. **System Actor**: Automated downstream/upstream non-human systems.

### 3.2 Stakeholder Metadata Schema (The Stakeholder Card)
Every stakeholder MUST be modeled with this strict schema:
- **Stakeholder ID**: (e.g., STK-001) - Stable reference for all downstream artifacts.
- **Name**: (e.g., Clinical Auditor)
- **Lifecycle Status**: (Potential / Validated / Active / Deprecated)
- **Category**: (from Taxonomy above)
- **Priority**: (Critical / High / Medium / Low)
- **Health Status**: (Healthy / At Risk / Misaligned / Blocked)
- **Description**: (Brief summary of their role)
- **Goals**: (What they want to achieve)
- **Pain Points**: (What currently blocks them)
- **Influence**: (Low / Medium / High)
- **Power**: (Low / Medium / High)
- **Interest**: (Low / Medium / High)
- **Decision Authority**: (Can they block the product?)
- **Relationship Types**: (Depends, Approves, Consumes, Produces, Regulates, Collaborates)
- **Communication Owner**: (e.g., Product Manager, Compliance Lead)
- **Success Definition**: (Measurable outcome)

## 4. Output Contract
To guarantee deterministic AI orchestration, this artifact explicitly produces the following machine-readable assets for downstream nodes:
- **Stakeholder Registry** (Used by `105_Persona`)
- **Influence Matrix** (Used by `104` Governance)
- **Authority Matrix** (Used by `108_Requirements`)
- **Conflict Matrix** (Used by `110_Assumptions`)
- **Communication Matrix** (Used by `104` Governance)

## 5. Traceability
To guarantee alignment with the core strategy layer, every stakeholder MUST trace to:
- **Vision Segment**: Which part of `100_Vision` do they serve?
- **Problem Impact**: Which root cause in `101_Problem` affects them?
- **Goal Ownership**: Which KPI in `102_ProductGoals` do they influence?
- **Principle Alignment**: Which trade-off in `103_Principles` protects them?

## 6. Context & AI Prompts
### Hydration Rules
- AI Swarms MUST NOT invent stakeholders simply because they commonly exist in similar industries.
- Every stakeholder must be strictly justified by the hydrated Vision, Problem, Goals, or explicit domain research.

### AI Boundary Rule
- **AI MUST NOT infer Personas.** AI only identifies Stakeholders here. Persona synthesis belongs exclusively to `105_PersonaStandard`.

### Memory TTL
- `Permanent` for the duration of the Human Context Layer generation.

## 7. Anti-Patterns
- **The Generic User**: Using "The User" instead of specific, classified stakeholder cards.
- **The Empty Stakeholder**: A stakeholder with no Success Definition or Traceability.
- **Ignoring Adversaries**: Failing to map malicious actors who stress the system.

## 8. Section Registry (Template Contract)
Every Stakeholder artifact MUST use these exact headings.

<!-- SECTION GROUP: Discovery Core -->
- # 1. Executive Summary
- # 2. Purpose
- # 3. Scope

<!-- SECTION GROUP: Stakeholder Landscape -->
- # 4. Stakeholder Registry
- # 5. Stakeholder Classification
- # 6. Stakeholder Objectives
- # 7. Stakeholder Success Criteria

<!-- SECTION GROUP: Influence Analysis -->
- # 8. Power / Interest Matrix
- # 9. Influence Map
- # 10. Decision Authority
- # 11. Communication Priority

<!-- SECTION GROUP: Relationship Mapping -->
- # 12. Stakeholder Dependencies
- # 13. Conflict Matrix
- # 14. Alignment Risks

<!-- SECTION GROUP: Governance -->
- # 15. Ownership Rules
- # 16. Review Cadence
- # 17. Lifecycle
- # 18. Escalation Path
- # 19. Acceptance Criteria
- # 20. Traceability
- # 21. AI Context
