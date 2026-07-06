---
Title: 101_ProblemStandard
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

## 11. Required Sections
Every `Problem.md` artifact MUST implement:
1. **Executive Summary**
2. **Purpose**
3. **Scope**
4. **Problem Statement**
5. **Current State**
6. **Desired State**
7. **Gap Analysis**
8. **User Impact**
9. **Business Impact**
10. **Root Cause Analysis**
11. **Evidence** (Quantitative & Qualitative)
12. **Market Context**
13. **Affected Stakeholders**
14. **Risk of Inaction**
15. **Out of Scope**
16. **Constraints**
17. **Assumptions**
18. **Dependencies**
19. **Acceptance Criteria**
20. **Traceability**
21. **AI Context**

## 12. Validation Overrides
- **Semantic**: Zero solutionizing. No features, UI components, or technical stacks may be proposed.
- **Consistency**: The Business Impact must logically align with the Vision's North Star Metric.

## 13. Acceptance Criteria
- Problem validated by quantitative data or qualitative research.
- Artifact peer-reviewed and frozen.

## 14. Quality Gate Overrides
- **Gate ID**: `QG-PROB-001`
  - **Severity**: Critical
  - **Blocking**: Yes
  - **Decision**: Reject immediately if the document proposes a feature or technical solution.
- **Gate ID**: `QG-PROB-002`
  - **Severity**: High
  - **Blocking**: Yes
  - **Decision**: Reject if the problem is based purely on assumption without verifiable evidence in the `Evidence` section.

## 15. Traceability Overrides
- **Consumes**: `Vision.md`
- **Produces**: Context for `102_ProductGoalStandard` and `104_PersonaStandard`.
- **Validates**: Vision viability.

## 16. AI Context Overrides
- **Context Priority**: High (Critical for empathy and requirement generation).
- **Required Context**: `Problem Statement`, `Gap Analysis`, `User Impact`, `Business Impact`.
- **Forbidden Context**: Any implicit solutions hidden in the text.
- **Compression Rules**: Retain exact metrics from the `Evidence` section.

## 17. Extension Points
- Teams may append specific `Data Queries` (e.g., SQL snippets) used to generate Evidence.

## 18. Success Criteria
100% of product initiatives are traced back to a clearly documented, data-backed Problem artifact that contains zero solution bias.

## 19. AI Contract Overrides
- **AI Generation Rules**: Agent MUST enforce the "5 Whys" methodology for Root Cause Analysis and structure the `Gap Analysis` as Current vs Desired.
- **AI Validation Rules**: MUST flag the artifact if it detects verbs like "build", "create", "implement", or UI terminology.
- **AI Review Rules**: MUST verify that `Risk of Inaction` logically connects to `Business Impact`.
- **AI Constraints**: MUST NOT invent data or metrics for the `Evidence` section. If missing, it must output a placeholder and prompt the human.
