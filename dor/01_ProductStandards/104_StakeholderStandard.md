---
Title: 104_StakeholderStandard
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
Artifact ID: PS-104
Depends On: 100_VisionStandard.md, 101_ProblemStandard.md, 102_ProductGoalStandard.md, 103_ProductPrinciplesStandard.md
Extends: 050_ProductStandardContract.md
Base Contract: 050_ProductStandardContract.md
Template Path: 01_ProductStandards/Templates/Discovery/Stakeholder.template.md
Next Artifact: 105_PersonaStandard.md
---

# Stakeholder Standard

## 1. Definition
The `104_StakeholderStandard` is the root node of the Human Context Layer. It defines a rigid, enterprise-grade governance structure for cataloging every human, system, and regulatory entity impacted by the product. This standard prevents downstream duplication in `105_Persona` and `107_Journey` by acting as the single source of truth for the Stakeholder Registry, Influence Model, and Conflict Matrix.

## 2. Validation & Quality Gates
Artifacts following this standard MUST pass these checks:

### Validation Rules
- No orphan stakeholder.
- No duplicated stakeholder roles.
- Every stakeholder MUST have measurable success criteria.
- Every stakeholder MUST have an influence classification (Power/Interest).
- Every stakeholder MUST have at least one downstream consumer (e.g., a Persona or JTBD).

### Quality Gates
- **QG-STAKE-001**: Reject if any stakeholder cannot trace back to the Problem or Goals.
- **QG-STAKE-002**: Reject if the Power/Interest Matrix is incomplete for identified Primary stakeholders.
- **QG-STAKE-003**: Reject if the stakeholder registry contains duplicate roles or undefined ownership/authority.

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
- **Name**: (e.g., Clinical Auditor)
- **Category**: (from Taxonomy above)
- **Description**: (Brief summary of their role)
- **Goals**: (What they want to achieve)
- **Pain Points**: (What currently blocks them)
- **Influence**: (Low/Medium/High)
- **Power**: (Low/Medium/High)
- **Interest**: (Low/Medium/High)
- **Decision Authority**: (Can they block the product?)
- **Consumes**: (What data/value they need)
- **Produces**: (What data/value they provide)
- **Depends On**: (Other stakeholders)
- **Success Definition**: (Measurable outcome)

## 4. Traceability
To guarantee alignment with the core strategy layer, every stakeholder MUST trace to:
- **Vision Segment**: Which part of `100_Vision` do they serve?
- **Problem Impact**: Which root cause in `101_Problem` affects them?
- **Goal Ownership**: Which KPI in `102_ProductGoals` do they influence?
- **Principle Alignment**: Which trade-off in `103_Principles` protects them?

## 5. Context & AI Prompts
### Hydration Rules
- AI Swarms MUST NOT invent stakeholders simply because they commonly exist in similar industries.
- Every stakeholder must be strictly justified by the hydrated Vision, Problem, Goals, or explicit domain research.

### Memory TTL
- `Permanent` for the duration of the Human Context Layer generation.

## 6. Anti-Patterns
- **The Generic User**: Using "The User" instead of specific, classified stakeholder cards.
- **The Empty Stakeholder**: A stakeholder with no Success Definition or Traceability.
- **Ignoring Adversaries**: Failing to map malicious actors who stress the system.

## 7. Section Registry (Template Contract)
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
- # 15. Acceptance Criteria
- # 16. Traceability
- # 17. AI Context
