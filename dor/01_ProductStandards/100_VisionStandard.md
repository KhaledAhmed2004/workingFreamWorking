---
Title: 100_VisionStandard
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
1. **Purpose**: The "Why".
2. **Scope**: The boundaries of the vision.
3. **Vision Statement**: A concise 1-2 sentence pitch.
4. **Vision Narrative**: Long-form description of the future state.
5. **Business Opportunity**: Why the enterprise cares.
6. **Customer Problem**: The core pain point being solved.
7. **Target Audience**: Who benefits directly.
8. **Value Proposition**: Business vs. User value.
9. **Strategic Alignment**: How this fits into corporate goals.
10. **Differentiation**: Why we are uniquely positioned to win.
11. **North Star Metric**: The single metric of success.
12. **Success Criteria**: Macro-level milestones.
13. **Out of Scope**: Explicitly what we are NOT building.
14. **Constraints**: Budget, timeline, or technology limits.
15. **Assumptions**: What must be true for this to succeed.
16. **Dependencies**: External blockers.
17. **Acceptance Criteria**: What proves this vision is valid.
18. **Traceability**: Graph linkages to upstream corporate goals.
19. **AI Context**: Special instructions for downstream AI agents.

## 12. Template Reference
The raw execution template is located at:
`01_ProductStandards/Templates/Discovery/Vision.template.md`

## 13. Validation
To pass validation (`07_ValidationStandards`), a Vision MUST:
- Contain exactly one North Star Metric.
- Define at least one explicit "Out of Scope" item.
- Contain a Vision Statement no longer than 3 sentences.

## 14. Acceptance Criteria
- Stakeholder consensus achieved.
- Traceability graph fully hydrated.

## 15. Quality Gates
- `QG-VIS-001`: Does the North Star Metric align with the Strategic Alignment section?
- `QG-VIS-002`: Are there any architectural implementation details leaked into the vision? (Must be flagged as Failure).

## 16. Traceability
- **Parent**: None (Root Node).
- **Children**: `Problem.md`, `Goals.md`, `Principles.md`.

## 17. AI Context
When injecting `Vision.md` into an AI's context window for downstream tasks (like PRD generation), instruct the AI to prioritize the `Vision Statement` and `Out of Scope` sections to prevent hallucinated scope creep.

## 18. Extension Points
- Organizations may append custom `Compliance Validation` blocks for regulated domains (e.g., HIPAA mapping).

## 19. Success Criteria
The standard is successful when 100% of enterprise products have a machine-readable `Vision.md` that perfectly hydrates downstream PRD generation.

## 20. Exit Criteria
- [ ] Review by Enterprise Architecture Board
- [ ] Compliance with `00_ProductStandardsManifest.md`
- [ ] Template `Vision.template.md` created
- [ ] Ready for Freeze

---

# AI Generation Rules

## AI Generation
When an AI agent is tasked with generating a `Vision.md`, it MUST recursively query the user/stakeholder until it has sufficient data to fill all 19 Required Sections without hallucinating business strategy.

## AI Validation
An AI Validation Agent MUST read the generated `Vision.md` and explicitly reject it if any UI/UX features or database schemas are mentioned. Visions are about "Why", not "How".

## AI Review
The Review Agent MUST map the `Vision Narrative` against the `North Star Metric` and flag if they are logically disconnected.

## AI Consumption
When consuming this document to generate a `101_ProblemStandard` artifact, the AI MUST strictly inherit the `Target Audience` and `Customer Problem` sections as immutable context.

## AI Constraints
- AI MUST NOT invent North Star Metrics; it must extract or negotiate them with human stakeholders.
- AI MUST NOT overwrite the `Strategic Alignment` without explicit executive context.
