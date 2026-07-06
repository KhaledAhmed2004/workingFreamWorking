---
Title: 101_ProblemStandard
Artifact Version: 2.0
Framework Version: 1.0
Supersedes: 101_ProblemStandard.md v1.0
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
Artifact ID: PS-101
Depends On: 100_VisionStandard.md
Extends: 050_ProductStandardContract.md
Standard Type: Derived Product Standard
Base Contract: 050_ProductStandardContract.md
Template Path: 01_ProductStandards/Templates/Discovery/Problem.template.md
Next Artifact: 102_ProductGoalStandard.md
---

# Enterprise Problem Standard

## 1. Executive Statement
This standard enforces the rigorous definition of the Customer Problem space. A product built on a misunderstood or shallow problem is an architectural liability. It guarantees absolute clarity before any solution design begins.

## 2. Purpose
To ensure all product teams deeply investigate, validate, and document the core customer pain points before ideating solutions.

## 3. Scope
Governs the creation and validation of the `Problem.md` artifact within the Product Discovery phase. It strictly prohibits solutionizing.

## 4. Ownership
- **Standard Owner**: Product Architecture Board
- **Artifact Owner**: Senior Product Manager / UX Researcher

## 5. Consumers
- Product Managers (to write `102_ProductGoalStandard`)
- Designers (for empathy and user journeys)
- Engineers (for domain context)
- AI Agent Swarms (for requirements hydration)

## 6. Producers
- Product Managers
- User Researchers
- Product Discovery Agents (AI)

## 7. Inputs
- Approved `Vision.md`
- User Interviews & Data Analytics
- Market Research

## 8. Outputs
- A `Problem.md` artifact compliant with this standard.

## 9. Dependencies
- **Produces**: Foundational boundaries for `102_ProductGoalStandard.md`.
- **References**: Raw user data and analytics reports.

## 10. Artifact Classification
- **Layer**: Implementation Layer (`02_ProductDiscovery`)
- **Domain**: Product Discovery
- **Type**: Core Discovery Node

## 11. Section Registry
Every `Problem.md` artifact MUST implement the following grouped sections:

**Discovery Core**
- Executive Summary
- Purpose
- Scope

**Problem Analysis**
- Problem Statement
- Current State
- Desired State
- Gap Analysis

**Impact & Evidence**
- User Impact
- Business Impact
- Root Cause Analysis
- Evidence (Quantitative & Qualitative)
- Market Context

**Stakeholders & Risk**
- Affected Stakeholders
- Risk of Inaction

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
- **Semantic**: Zero solutionizing. No features, UI components, or technical stacks may be proposed.
- **Completeness**: Gap Analysis MUST explicitly connect the Current State to the Desired State.
- **Relationship**: The Root Cause Analysis MUST be proven by the Evidence section.
- **Consistency**: The Business Impact must logically align with the Vision's North Star Metric.

## 13. Acceptance Criteria
- Problem validated by quantitative data or qualitative research.
- Artifact peer-reviewed and frozen.

## 14. Quality Gate Overrides
- **Gate ID**: `QG-PROB-001`
  - **Severity**: Critical
  - **Blocking**: Yes
  - **Evidence Required**: Complete Document.
  - **Owner**: Enterprise Architecture Review Board
  - **Automation**: AI Semantic Validator to scan for solutionizing verbs.
  - **Decision**: Reject immediately if the document proposes a feature or technical solution.
- **Gate ID**: `QG-PROB-002`
  - **Severity**: High
  - **Blocking**: Yes
  - **Evidence Required**: `Evidence` section.
  - **Owner**: Product Leadership
  - **Automation**: Check if `Evidence` is populated with actual data metrics.
  - **Decision**: Reject if the problem is based purely on assumption without verifiable evidence.

## 15. Traceability Overrides
- **Consumes**: `Vision.md`
- **Produces**: Context for `102_ProductGoalStandard`.
- **Validates**: Vision viability.

## 16. AI Context Overrides
- **Hydration Priority**: High
- **Memory TTL**: Permanent (for the duration of Epic and Story generation).
- **Required Context**: `Problem Statement`, `Gap Analysis`, `User Impact`, `Business Impact`.
- **Forbidden Context**: Any implicit solutions hidden in the text.
- **Summarization**: Keep the `Root Cause Analysis` verbatim.
- **Compression**: Do NOT compress the `Evidence` metrics.

## 17. Extension Points
- **Reserved Extension IDs**: `PROB-EXT-001` to `PROB-EXT-099`.
- E.g., Specific `Data Queries` (e.g., SQL snippets) used to generate Evidence.

## 18. Success Criteria
100% of product initiatives are traced back to a clearly documented, data-backed Problem artifact that contains zero solution bias.

## 19. AI Contract Overrides
- **Generation**: Agent MUST enforce the "5 Whys" methodology for Root Cause Analysis.
- **Validation**: MUST flag the artifact if it detects verbs like "build", "create", "implement", or UI terminology.
- **Review**: MUST verify that `Risk of Inaction` logically connects to `Business Impact`.
- **Consumption**: Downstream PRD agents MUST link every feature directly to the `Problem Statement`.
- **Reasoning**: Log the mapping between Evidence and Root Cause.
- **Output**: MUST respect the `<!-- SECTION GROUP: ... -->` HTML comments for the Section Registry.
