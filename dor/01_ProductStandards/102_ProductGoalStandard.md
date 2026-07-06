---
Title: 102_ProductGoalStandard
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
Artifact ID: PS-102
Depends On: 101_ProblemStandard.md
Extends: 050_ProductStandardContract.md
Standard Type: Derived Product Standard
Base Contract: 050_ProductStandardContract.md
Template Path: 01_ProductStandards/Templates/Discovery/ProductGoal.template.md
Next Artifact: 103_ProductPrinciplesStandard.md
---

# Enterprise Product Goal Standard

## 1. Executive Statement
This standard enforces the rigorous definition of Product Goals. Where the Vision defines "Where we want to go" and the Problem defines "What pain exists", the Product Goal defines "What measurable outcomes we must achieve." This standard ensures that goals are outcome-based, strictly measurable, and entirely devoid of solutionizing or feature roadmapping.

## 2. Purpose
To bridge the gap between abstract Product Vision/Customer Problems and actionable requirements by defining explicit, measurable objectives.

## 3. Scope
Governs the creation and validation of the `ProductGoals.md` artifact within the Product Discovery phase. It strictly prohibits the definition of features, UI implementations, technical architecture, epics, or user stories.

## 4. Ownership
- **Standard Owner**: Product Architecture Board
- **Artifact Owner**: Senior Product Manager / Product Director

## 5. Consumers
- Product Managers (to write `103_ProductPrinciplesStandard` and `PRD.md`)
- Engineering Managers (to define system scale and non-functional goals)
- Design Leads (to validate UX success metrics)
- AI Agent Swarms (for epic and story metric hydration)

## 6. Producers
- Product Managers
- Executive Stakeholders
- Product Discovery Agents (AI)

## 7. Inputs
- Approved `Vision.md`
- Approved `Problem.md`
- Corporate OKRs

## 8. Outputs
- A `ProductGoals.md` artifact compliant with this standard and governed by `051_ProductArtifactContract.md`.

## 9. Dependencies
- **Produces**: Metric boundaries for Epics and PRDs.
- **References**: Corporate OKRs.

## 10. Artifact Classification
- **Layer**: Implementation Layer (`02_ProductDiscovery`)
- **Domain**: Product Discovery
- **Type**: Core Discovery Node

## 11. Section Registry
Every `ProductGoals.md` artifact MUST implement the following grouped sections:

**Discovery Core**
- Executive Summary
- Purpose
- Scope

**Strategic Alignment**
- Corporate OKR Mapping
- Problem Resolution Mapping

**Product Goals**
- Primary Product Goal (The single most important outcome)
- Secondary Product Goals (Supporting outcomes)
- Target Metrics (KPIs defining success)
- Time Horizon (When must this be achieved)

**Constraints & Boundaries**
- Anti-Goals (What we explicitly will NOT try to achieve)
- Goal Dependencies (What must happen externally for these goals to be met)
- Success Risks (Factors that could derail these goals)

**Governance & Execution**
- Acceptance Criteria
- Traceability
- AI Context

## 12. Validation Overrides
- **Semantic**: Zero solutionizing. No features, UI components, or technical stacks may be proposed. Goals must follow the SMART framework (Specific, Measurable, Achievable, Relevant, Time-bound).
- **Completeness**: Every declared Goal MUST have an associated Target Metric.
- **Relationship**: The goals MUST explicitly map to the root cause defined in `Problem.md` and the North Star Metric defined in `Vision.md`.
- **Consistency**: Anti-Goals must not contradict the Primary Product Goal.

## 13. Acceptance Criteria
- Goals validated by executive stakeholders as ambitious yet achievable.
- Artifact peer-reviewed and frozen.

## 14. Quality Gate Overrides
- **Gate ID**: `QG-GOAL-001`
  - **Severity**: Critical
  - **Blocking**: Yes
  - **Evidence Required**: Complete Document.
  - **Owner**: Enterprise Architecture Review Board
  - **Automation**: AI Semantic Validator to scan for solutionizing verbs ("build feature X", "add button Y").
  - **Decision**: Reject immediately if the document proposes a feature or technical solution.
- **Gate ID**: `QG-GOAL-002`
  - **Severity**: High
  - **Blocking**: Yes
  - **Evidence Required**: `Target Metrics` section.
  - **Owner**: Data / Analytics Lead
  - **Automation**: Check if Target Metrics are quantifiable and time-bound.
  - **Decision**: Reject if goals are vague, unmeasurable, or lack a Time Horizon.

## 15. Traceability Overrides
- **Consumes**: `Vision.md`, `Problem.md`
- **Produces**: Success criteria constraints for Epics and PRDs.
- **Validates**: Solvability of the `Problem.md` within the `Vision.md` scope.

## 16. AI Context Overrides
- **Hydration Priority**: High
- **Memory TTL**: Permanent (for the duration of PRD and Epic generation).
- **Required Context**: `Primary Product Goal`, `Target Metrics`, `Anti-Goals`.
- **Forbidden Context**: Any implicit solutions hidden in the text.
- **Summarization**: Keep the `Target Metrics` completely verbatim.
- **Compression**: Do NOT compress the `Anti-Goals`.

## 17. Extension Points
- **Reserved Extension IDs**: `GOAL-EXT-001` to `GOAL-EXT-099`.
- E.g., Custom metric tracking dashboards (e.g., Amplitude/Mixpanel links).

## 18. Success Criteria
100% of product initiatives have clear, quantifiable, outcome-based goals that act as the deterministic measure of success for downstream engineering efforts.

## 19. AI Contract Overrides
- **Generation**: Agent MUST enforce the SMART framework for all goals. If a human user proposes a feature as a goal, the AI must explicitly push back and ask for the underlying *outcome*.
- **Validation**: MUST flag the artifact if it detects roadmap items, epics, or user story structures.
- **Review**: MUST verify that `Corporate OKR Mapping` logically connects to the enterprise strategy.
- **Consumption**: Downstream PRD agents MUST link every proposed feature to at least one metric defined in `Target Metrics`.
- **Reasoning**: Log the justification for selecting the Primary Product Goal over other alternatives.
- **Output**: MUST respect the `<!-- SECTION GROUP: ... -->` HTML comments for the Section Registry.
