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
Depends On: 00_ProductStandardsManifest
Next Artifact: 101_ProblemStandard.md
---

# Enterprise Vision Standard

## 1. Executive Statement
This standard defines the absolute root node of the Enterprise Product Discovery process. The Product Vision acts as the "North Star" for all downstream discovery and definition artifacts. Without a formalized, frozen Vision, product teams drift into scope creep and disjointed architectures. This document enforces the structural rules for creating an enterprise-grade Vision artifact.

## 2. Purpose
To ensure every product built within the enterprise shares a unified, structurally consistent articulation of its ultimate goal, target audience, and business value.

## 3. Scope
This standard governs the creation, validation, and lifecycle of the `Vision.md` artifact for any product or ecosystem. It does NOT govern the actual solution architecture or the detailed PRD.

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
- Executive Mandates

## 8. Outputs
- A `Vision.md` artifact compliant with this standard.

## 9. Dependencies
- **Produces**: Boundaries for `101_ProblemStandard.md`.
- **References**: Corporate goals and market research.
- **Validates**: Ultimate strategic alignment.

## 10. Artifact Classification
- **Layer**: Implementation Layer (`02_ProductDiscovery`)
- **Domain**: Product Discovery
- **Type**: Foundational Root Node

## 11. Required Sections
Every `Vision.md` artifact MUST implement the following specific headers:
1. **Executive Summary**: 30-second read for executives.
2. **Purpose**: The "Why".
3. **Scope**: The boundaries of the vision.
4. **Vision Statement**: A concise 1-2 sentence pitch.
5. **Vision Narrative**: Long-form description of the future state.
6. **Business Opportunity**: Why the enterprise cares.
7. **Customer Problem**: The core pain point being solved.
8. **Target Audience**: Who benefits directly.
9. **Value Proposition**: Business vs. User value.
10. **Strategic Alignment**: How this fits into corporate goals.
11. **Differentiation**: Why we are uniquely positioned to win.
12. **North Star Metric**: The single metric of success.
13. **Success Criteria**: Macro-level milestones.
14. **Out of Scope**: Explicitly what we are NOT building.
15. **Constraints**: Budget, timeline, or technology limits.
16. **Assumptions**: What must be true for this to succeed.
17. **Dependencies**: External blockers.
18. **Acceptance Criteria**: What proves this vision is valid.
19. **Traceability**: Graph linkages to upstream goals.
20. **AI Context**: Special instructions for agents.

## 12. Template Contract
- **Template Name**: Discovery Vision Template
- **Template Version**: 1.0
- **Template Path**: `01_ProductStandards/Templates/Discovery/Vision.template.md`
- **Template Owner**: Product Architecture Board
- **Compatibility**: All Enterprise Products (v1.0+)
- **Required Metadata**: Title, Artifact Version, Status, Phase, Owner, Approver, Artifact ID.

## 13. Validation
To pass validation (`07_ValidationStandards`), a Vision MUST comply with:
- **Structural**: Exact match of all 20 required markdown headers.
- **Semantic**: Vision Statement must be under 3 sentences. Exactly ONE North Star Metric must be defined.
- **Relationship**: Must trace to an overarching corporate strategy.
- **Traceability**: No orphaned dependencies allowed.
- **Consistency**: Narrative must logically align with the North Star Metric.

## 14. Acceptance Criteria
- Stakeholder consensus achieved.
- Traceability graph fully hydrated.

## 15. Quality Gates
- **Gate ID**: `QG-VIS-001`
  - **Severity**: High
  - **Blocking**: Yes
  - **Consumed Evidence**: `Strategic Alignment` and `North Star Metric` sections.
  - **Decision**: Reject if the North Star Metric contradicts the corporate strategy.
- **Gate ID**: `QG-VIS-002`
  - **Severity**: Critical
  - **Blocking**: Yes
  - **Consumed Evidence**: Complete Document.
  - **Decision**: Reject if UI features, technical architecture, or database schemas are leaked into the Vision.

## 16. Traceability
- **Consumes**: Corporate Strategy, Market Research.
- **Produces**: Boundaries for `101_ProblemStandard`.
- **References**: Competitor Analysis.
- **Validates**: Alignment with Executive Mandate.
- **Constrained By**: Budget limitations and regulatory constraints.

## 17. AI Context
- **Context Priority**: High (Must be preserved in long-term memory).
- **Required Context**: `Vision Statement`, `North Star Metric`, `Out of Scope`.
- **Optional Context**: `Vision Narrative`, `Assumptions`.
- **Forbidden Context**: Ignore any tactical implementation hints buried in the narrative.
- **Compression Rules**: When summarizing, retain verbatim the `North Star Metric`.
- **Hydration Rules**: Inject into all downstream Definition and Architecture tasks.

## 18. Extension Points
- Organizations may append custom `Compliance Validation` blocks for regulated domains (e.g., HIPAA mapping).

## 19. Success Criteria
The standard is successful when 100% of enterprise products have a machine-readable `Vision.md` that perfectly hydrates downstream PRD generation.

## 20. Exit Criteria
- [ ] Review by Enterprise Architecture Board
- [ ] Compliance with `00_ProductStandardsManifest.md`
- [ ] Template `Vision.template.md` verified
- [ ] Ready for Freeze

## 21. AI Contract
- **AI Generation Rules**: The agent MUST recursively query stakeholders until all 20 Required Sections are populated. It MUST NOT hallucinate business strategy.
- **AI Validation Rules**: The agent MUST reject the artifact if any technical architecture or UI/UX implementation details are present.
- **AI Review Rules**: The Review Agent MUST map the `Vision Narrative` against the `North Star Metric` and flag logical disconnections.
- **AI Consumption Rules**: Downstream agents MUST strictly inherit the `Target Audience` and `Customer Problem` sections as immutable context.
- **AI Constraints**: The AI MUST NOT invent North Star Metrics; they must be negotiated. The AI MUST NOT overwrite `Strategic Alignment` without explicit executive overrides.
