---
Title: 103_ProductPrinciplesStandard
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
Artifact ID: PS-103
Depends On: 100_VisionStandard.md, 101_ProblemStandard.md, 102_ProductGoalStandard.md
Extends: 050_ProductStandardContract.md
Standard Type: Derived Product Standard
Base Contract: 050_ProductStandardContract.md
Template Path: 01_ProductStandards/Templates/Discovery/ProductPrinciples.template.md
Next Artifact: 104_StakeholderStandard.md
---

# Enterprise Product Principles Standard

## 1. Executive Statement
This standard enforces the creation of immutable decision-making rules for the enterprise product. Product Principles are not features, UX specifications, or technical requirements. They are the supreme architectural philosophy that governs every downstream decision. When future engineers, designers, product managers, executives, or AI agents disagree on a tradeoff, the Product Principles act as the ultimate, unambiguous source of truth.

## 2. Purpose
To eliminate decision latency and prevent scope creep by providing a universally agreed-upon framework for resolving conflicting priorities (e.g., speed vs. accuracy, automation vs. human-in-the-loop).

## 3. Scope
Governs the creation and validation of the `ProductPrinciples.md` artifact within the Product Discovery phase. It strictly prohibits solutionizing and feature definition.

## 4. Ownership
- **Standard Owner**: Product Architecture Board
- **Artifact Owner**: Principal Product Manager / Chief Product Officer

## 5. Consumers
- Product Managers (Constrains PRD, Epic, and Story scope)
- Designers (Constrains UX paradigms and interaction patterns)
- Enterprise Architects (Constrains technical architecture decisions)
- AI Agent Swarms (Acts as system-prompt guardrails)

## 6. Producers
- Product Leadership
- Executive Stakeholders
- Product Discovery Agents (AI)

## 7. Inputs
- Approved `Vision.md`
- Approved `Problem.md`
- Approved `ProductGoals.md`

## 8. Outputs
- A `ProductPrinciples.md` artifact compliant with this standard and governed by `051_ProductArtifactContract.md`.

## 9. Dependencies
- **Produces**: Guardrails for `104_StakeholderStandard` through `111_DiscoveryFreezeStandard`.
- **References**: Upstream `100`, `101`, and `102` artifacts.

## 10. Artifact Classification
- **Layer**: Implementation Layer (`02_ProductDiscovery`)
- **Domain**: Product Discovery
- **Type**: Core Discovery Node

## 11. Section Registry
Every `ProductPrinciples.md` artifact MUST implement the following grouped sections:

**Discovery Core**
- Executive Summary
- Purpose
- Scope

**Decision Philosophy**
- Overarching Product Philosophy
- Constraint Impact (Explicitly stating how these principles constrain PRDs, Epics, Stories, UX, and Architecture)

**Core Product Principles**
- Principle 1 Definition
- Principle 2 Definition
- Principle 3 Definition

**Trade-off Rules & Boundaries**
- Principle Hierarchy (Which principle wins in a conflict?)
- Trade-off Matrix (If A vs B, choose X)
- Non-Negotiables (Absolute decision boundaries)

**Governance & Execution**
- Acceptance Criteria
- Traceability
- AI Context

## 12. Validation Overrides
- **Semantic**: Zero solutionizing. A Principle MUST be feature-independent and technology-independent.
- **Completeness**: Every Principle MUST resolve a specific decision conflict.
- **Relationship**: Principles MUST NEVER contradict the `Vision.md` or `ProductGoals.md`.
- **Consistency**: A Principle must be measurable and testable during QA.

## 13. Acceptance Criteria
- Principles are endorsed by all cross-functional department heads (Design, Engineering, Product).
- Artifact peer-reviewed and frozen.

## 14. Quality Gate Overrides
- **Gate ID**: `QG-PRIN-001`
  - **Severity**: Critical
  - **Blocking**: Yes
  - **Evidence Required**: Complete Document.
  - **Owner**: Enterprise Architecture Review Board
  - **Automation**: AI Semantic Validator.
  - **Decision**: Reject immediately if the document describes a feature, user interface, or software architecture component.
- **Gate ID**: `QG-PRIN-002`
  - **Severity**: High
  - **Blocking**: Yes
  - **Evidence Required**: `Trade-off Rules & Boundaries` section.
  - **Owner**: Principal Product Manager
  - **Automation**: AI Logic Validator.
  - **Decision**: Reject if the principles are purely aspirational (e.g., "Make it fast and good") and fail to dictate a clear trade-off (e.g., "Speed over feature completeness").

## 15. Traceability Overrides
- **Consumes**: `Vision.md`, `Problem.md`, `ProductGoals.md`
- **Produces**: Mandatory constraints for all downstream artifacts (`104` to `111`).
- **Validates**: Alignment between Product Goals and Execution Strategy.

## 16. AI Context Overrides
- **Hydration Priority**: Critical
- **Memory TTL**: Permanent (Must be injected into the System Prompt for all downstream generative tasks).
- **Required Context**: `Core Product Principles`, `Trade-off Matrix`, `Non-Negotiables`.
- **Forbidden Context**: Any specific solutions or architectures.
- **Summarization**: Do NOT summarize. Principles must be ingested verbatim.
- **Compression**: Do NOT compress the `Trade-off Rules & Boundaries`.

## 17. Extension Points
- **Reserved Extension IDs**: `PRIN-EXT-001` to `PRIN-EXT-099`.
- E.g., Custom regulatory constraints mapped as unshakeable principles.

## 18. Success Criteria
100% of product initiatives use Product Principles to resolve cross-functional debates, reducing decision latency by >50%.

## 19. AI Contract Overrides
- **Generation**: Agent MUST explicitly force human stakeholders to articulate trade-offs (e.g., "If you want X, you must sacrifice Y. Which do you choose?").
- **Validation**: MUST flag the artifact if a Principle is just a platitude without decision-making utility.
- **Review**: MUST cross-reference principles against `ProductGoals.md` to ensure they do not sabotage the Target Metrics.
- **Consumption**: Downstream UX and Architecture agents MUST justify their design choices by citing a specific Principle.
- **Reasoning**: Log the exact conflicting scenarios that each Principle is designed to resolve.
- **Output**: MUST respect the `<!-- SECTION GROUP: ... -->` HTML comments for the Section Registry.
