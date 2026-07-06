---
Title: 101_ProblemStandard
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
Artifact ID: PS-101
Depends On: 100_VisionStandard.md
Next Artifact: 102_ProductGoalStandard.md
---

# Enterprise Problem Standard

## 1. Executive Statement
This standard enforces the rigorous definition of the Customer Problem space. A product built on a misunderstood or shallow problem is an architectural liability. This standard guarantees that every problem tackled by the enterprise is explicitly documented, backed by evidence, logically traces back to the approved Product Vision, and provides absolute clarity before any solution design begins.

## 2. Purpose
To ensure all product teams deeply investigate, validate, and document the core customer pain points before ideating solutions.

## 3. Scope
This standard governs the creation and validation of the `Problem.md` artifact within the Product Discovery phase. It strictly prohibits solutionizing.

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
- **Validates**: The assumptions made in the Vision's "Customer Problem" section.

## 10. Artifact Classification
- **Layer**: Implementation Layer (`02_ProductDiscovery`)
- **Domain**: Product Discovery
- **Type**: Core Discovery Node

## 11. Required Sections
Every `Problem.md` artifact MUST implement the following specific headers:
1. **Executive Summary**: 30-second read summarizing the pain and impact.
2. **Purpose**: The intent of this document.
3. **Scope**: The boundaries of the problem space being analyzed.
4. **Problem Statement**: A concise 1-2 sentence definition of the core issue.
5. **Current State**: How users currently attempt to solve or bypass this problem.
6. **User Impact**: The emotional, temporal, or financial toll on the user.
7. **Business Impact**: The cost to the enterprise (e.g., lost revenue, churn, support load).
8. **Root Cause Analysis**: The underlying "Why" (e.g., 5 Whys analysis).
9. **Market Context**: How competitors address this problem.
10. **Key Metrics**: Data proving the problem exists (e.g., 40% drop-off rate).
11. **Out of Scope**: Related problems explicitly NOT being addressed.
12. **Constraints**: Environmental limits affecting the problem space.
13. **Assumptions**: Unverified beliefs about the problem.
14. **Dependencies**: Upstream artifacts required to validate this problem.
15. **Acceptance Criteria**: What proves this problem is validated and ready for solutions.
16. **Traceability**: Graph linkages to the `Vision.md`.
17. **AI Context**: Special instructions for agents parsing this file.

## 12. Template Contract
- **Template Name**: Discovery Problem Template
- **Template Version**: 1.0
- **Template Path**: `01_ProductStandards/Templates/Discovery/Problem.template.md`
- **Template Owner**: Product Architecture Board
- **Compatibility**: All Enterprise Products (v1.0+)
- **Required Metadata**: Title, Artifact Version, Status, Phase, Owner, Approver, Artifact ID, Depends On.

## 13. Validation
To pass validation (`07_ValidationStandards`), a Problem artifact MUST comply with:
- **Structural**: Exact match of all 17 required markdown headers.
- **Semantic**: Zero solutionizing. No features, UI components, or technical stacks may be proposed.
- **Relationship**: Must trace directly to an approved `Vision.md`.
- **Traceability**: Must explicitly consume the Vision artifact.
- **Consistency**: The Business Impact must align with the Vision's North Star Metric.

## 14. Acceptance Criteria
- Problem validated by quantitative data or qualitative research.
- Artifact peer-reviewed and frozen.

## 15. Quality Gates
- **Gate ID**: `QG-PROB-001`
  - **Severity**: Critical
  - **Blocking**: Yes
  - **Consumed Evidence**: Complete Document.
  - **Decision**: Reject immediately if the document proposes a feature or technical solution.
- **Gate ID**: `QG-PROB-002`
  - **Severity**: High
  - **Blocking**: Yes
  - **Consumed Evidence**: `Key Metrics` section.
  - **Decision**: Reject if the problem is based purely on assumption without verifiable data.

## 16. Traceability
- **Consumes**: `Vision.md`
- **Produces**: Context for `102_ProductGoalStandard` and `104_PersonaStandard`.
- **References**: Support tickets, analytics dashboards.
- **Validates**: Vision viability.
- **Constrained By**: Vision Scope.

## 17. AI Context
- **Context Priority**: High (Critical for empathy and requirement generation).
- **Required Context**: `Problem Statement`, `User Impact`, `Business Impact`.
- **Optional Context**: `Root Cause Analysis`.
- **Forbidden Context**: Any implicit solutions hidden in the text.
- **Compression Rules**: Retain the exact metrics from the `Key Metrics` section.
- **Hydration Rules**: Inject into all Definition artifacts (Epic, Story) to ensure user-centricity.

## 18. Extension Points
- Teams may append specific `Data Queries` (e.g., SQL snippets) used to generate the Key Metrics.

## 19. Success Criteria
100% of product initiatives are traced back to a clearly documented, data-backed Problem artifact that contains zero solution bias.

## 20. Exit Criteria
- [ ] Review by Enterprise Architecture Board
- [ ] Template `Problem.template.md` verified
- [ ] Ready for Freeze

## 21. AI Contract
- **AI Generation Rules**: The agent MUST probe the user aggressively for data to fill the `Key Metrics` and `Root Cause Analysis` sections. It must enforce the "5 Whys" methodology.
- **AI Validation Rules**: The validation agent MUST flag the artifact if it detects verbs like "build", "create", "implement", or any UI terminology, as these imply solutionizing.
- **AI Review Rules**: The Review Agent MUST verify that the `Business Impact` logically connects to the upstream Vision's `North Star Metric`.
- **AI Consumption Rules**: Downstream PRD agents MUST link every feature directly to the `Problem Statement`.
- **AI Constraints**: The AI MUST NOT invent data or metrics. If data is missing, it must output a placeholder and prompt the human user.
