---
Title: 100_VisionStandard
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
Artifact ID: PS-100
Depends On: 00_ProductStandardsManifest.md
Extends: 050_ProductStandardContract.md
Standard Type: Derived Product Standard
Base Contract: 050_ProductStandardContract.md
Template Path: 01_ProductStandards/Templates/Discovery/Vision.template.md
Next Artifact: 101_ProblemStandard.md
---

# Enterprise Vision Standard

## 1. Executive Statement
This standard defines the absolute root node of the Enterprise Product Discovery process. The Product Vision acts as the "North Star" for all downstream discovery and definition artifacts.

## 2. Purpose
To ensure every product built within the enterprise shares a unified, structurally consistent articulation of its ultimate goal, target audience, and business value.

## 3. Scope
Governs the creation, validation, and lifecycle of the `Vision.md` artifact. It strictly does NOT govern the actual solution architecture or the detailed PRD.

## 4. Ownership
- **Standard Owner**: Product Architecture Board
- **Artifact Owner**: Product Leadership / Principal Product Manager

## 5. Consumers
- Product Managers (to write `101_ProblemStandard`)
- Enterprise Architects (to design `300` Architecture)
- AI Agent Swarms (for downstream context hydration)

## 6. Producers
- Executive Stakeholders
- Principal Product Managers
- Product Discovery Agents (AI)

## 7. Inputs
- Corporate Strategy
- Market Research (from `02_EcosystemDiscovery`)

## 8. Outputs
- A `Vision.md` artifact compliant with this standard.

## 9. Dependencies
- **Produces**: Boundaries for `101_ProblemStandard.md`.
- **References**: Corporate goals and market research.

## 10. Artifact Classification
- **Layer**: Implementation Layer (`02_ProductDiscovery`)
- **Domain**: Product Discovery
- **Type**: Foundational Root Node

## 11. Required Sections
Every `Vision.md` artifact MUST implement:
1. **Executive Summary**
2. **Purpose**
3. **Scope**
4. **Vision Statement**
5. **Vision Narrative**
6. **Business Opportunity**
7. **Customer Problem**
8. **Target Audience**
9. **Value Proposition**
10. **Strategic Alignment**
11. **Differentiation**
12. **North Star Metric**
13. **Success Criteria**
14. **Out of Scope**
15. **Constraints**
16. **Assumptions**
17. **Dependencies**
18. **Acceptance Criteria**
19. **Traceability**
20. **AI Context**

## 12. Validation Overrides
- **Semantic**: Vision Statement must be under 3 sentences. Exactly ONE North Star Metric must be defined.
- **Consistency**: Narrative must logically align with the North Star Metric.

## 13. Acceptance Criteria
- Stakeholder consensus achieved.
- Traceability graph fully hydrated to corporate goals.

## 14. Quality Gate Overrides
- **Gate ID**: `QG-VIS-001`
  - **Severity**: High
  - **Blocking**: Yes
  - **Decision**: Reject if the North Star Metric contradicts corporate strategy.
- **Gate ID**: `QG-VIS-002`
  - **Severity**: Critical
  - **Blocking**: Yes
  - **Decision**: Reject if UI features or technical schemas are leaked into the Vision.

## 15. Traceability Overrides
- **Consumes**: Corporate Strategy, Market Research.
- **Produces**: Boundaries for `101_ProblemStandard`.
- **Validates**: Alignment with Executive Mandate.

## 16. AI Context Overrides
- **Context Priority**: High (Must be preserved in long-term memory).
- **Required Context**: `Vision Statement`, `North Star Metric`, `Out of Scope`.
- **Forbidden Context**: Ignore any tactical implementation hints buried in the narrative.
- **Compression Rules**: Retain verbatim the `North Star Metric`.

## 17. Extension Points
- Custom `Compliance Validation` blocks for regulated domains (e.g., HIPAA mapping).

## 18. Success Criteria
100% of enterprise products have a machine-readable `Vision.md` that perfectly hydrates downstream PRD generation.

## 19. AI Contract Overrides
- **AI Validation Rules**: MUST reject artifact if technical architecture or UI/UX implementation details are present.
- **AI Review Rules**: MUST map the `Vision Narrative` against the `North Star Metric` and flag logical disconnections.
- **AI Constraints**: MUST NOT invent North Star Metrics; MUST NOT overwrite `Strategic Alignment` without explicit executive overrides.
