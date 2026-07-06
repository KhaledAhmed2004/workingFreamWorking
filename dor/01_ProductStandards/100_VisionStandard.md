---
Title: 100_VisionStandard
Artifact Version: 2.0
Framework Version: 1.0
Supersedes: 100_VisionStandard.md v1.0
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

## 11. Section Registry
Every `Vision.md` artifact MUST implement the following grouped sections:

**Discovery Core**
- Executive Summary
- Purpose
- Scope

**Vision Mechanics**
- Vision Statement
- Vision Narrative
- Business Opportunity
- Customer Problem
- Target Audience

**Strategic Value**
- Value Proposition
- Strategic Alignment
- Differentiation
- North Star Metric
- Success Criteria

**Boundaries**
- Out of Scope
- Constraints
- Assumptions
- Dependencies

**Governance & Execution**
- Acceptance Criteria
- Traceability
- AI Context

## 12. Validation Overrides
- **Semantic**: Vision Statement must be under 3 sentences. Exactly ONE North Star Metric must be defined.
- **Consistency**: Narrative must logically align with the North Star Metric.
- **Completeness**: Strategic Alignment MUST map to a verifiable corporate objective.
- **Relationship**: The "Customer Problem" section must directly act as the input seed for `101_ProblemStandard`.

## 13. Acceptance Criteria
- Stakeholder consensus achieved.
- Traceability graph fully hydrated to corporate goals.

## 14. Quality Gate Overrides
- **Gate ID**: `QG-VIS-001`
  - **Severity**: High
  - **Blocking**: Yes
  - **Evidence Required**: `Strategic Alignment` and `North Star Metric` sections.
  - **Owner**: Executive Board
  - **Automation**: CI/CD Regex check for Corporate OKR tags.
  - **Decision**: Reject if the North Star Metric contradicts corporate strategy.
- **Gate ID**: `QG-VIS-002`
  - **Severity**: Critical
  - **Blocking**: Yes
  - **Evidence Required**: Complete Document.
  - **Owner**: Enterprise Architecture Review Board
  - **Automation**: AI Semantic Validator.
  - **Decision**: Reject if UI features or technical schemas are leaked into the Vision.

## 15. Traceability Overrides
- **Consumes**: Corporate Strategy, Market Research.
- **Produces**: Boundaries for `101_ProblemStandard`.
- **Validates**: Alignment with Executive Mandate.

## 16. AI Context Overrides
- **Hydration Priority**: Critical
- **Memory TTL**: Permanent (for the duration of the Epic generation).
- **Required Context**: `Vision Statement`, `North Star Metric`, `Out of Scope`.
- **Forbidden Context**: Ignore any tactical implementation hints buried in the narrative.
- **Summarization**: Keep the `Vision Statement` completely verbatim.
- **Compression**: Do NOT compress the `North Star Metric`.

## 17. Extension Points
- **Reserved Extension IDs**: `VIS-EXT-001` to `VIS-EXT-099`.
- E.g., Custom `Compliance Validation` blocks for regulated domains (e.g., HIPAA mapping).

## 18. Success Criteria
100% of enterprise products have a machine-readable `Vision.md` that perfectly hydrates downstream PRD generation.

## 19. AI Contract Overrides
- **Generation**: MUST recursively ask stakeholders to validate the `North Star Metric`.
- **Validation**: MUST reject artifact if technical architecture or UI/UX implementation details are present.
- **Review**: MUST map the `Vision Narrative` against the `North Star Metric` and flag logical disconnections.
- **Consumption**: Downstream agents MUST strictly inherit the `Target Audience`.
- **Reasoning**: Log why the `North Star Metric` was chosen over alternatives.
- **Output**: MUST respect the `<!-- SECTION GROUP: ... -->` HTML comments for the Section Registry.
