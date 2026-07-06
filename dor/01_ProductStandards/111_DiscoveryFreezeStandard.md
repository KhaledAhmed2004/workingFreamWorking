---
Title: 111_DiscoveryFreezeStandard
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
Artifact ID: PS-111
Depends On: 100_VisionStandard.md, 101_ProblemStandard.md, 102_ProductGoalStandard.md, 103_ProductPrinciplesStandard.md, 104_StakeholderStandard.md, 105_PersonaStandard.md, 106_JTBDStandard.md, 107_JourneyStandard.md, 108_RequirementsStandard.md, 109_SuccessMetricsStandard.md, 110_AssumptionsAndRisksStandard.md
Extends: 050_ProductStandardContract.md
Base Contract: 050_ProductStandardContract.md
Next Artifact: 200_SolutionArchitectureStandard.md
---

# Discovery Freeze Standard

## 1. Definition
The `111_DiscoveryFreezeStandard` acts as the definitive "Compiler" for the entire Product Discovery Layer. It generates absolutely no new domain knowledge. Its sole purpose is to cryptographically, structurally, and semantically validate that standards `100` through `110` have been executed correctly, traced fully, and are ready to be locked as the unchangeable foundation for Solution Architecture (`200`).

**Crucial Enterprise Architectural Rule:**
- **No new requirements, goals, or metrics may be introduced during or after the Discovery Freeze. To change Discovery intent after the Freeze, a formal Change Request (CR) must unlock the DAG.**

## 2. Validation & Quality Gates
Artifacts following this standard MUST pass these rigorous compilation checks:

### Strict Validation Vectors
1. **Metadata Validation**: Ensure every artifact `100-110` has valid YAML frontmatter matching `050_ProductStandardContract`.
2. **Dependency Validation**: Ensure no circular dependencies exist and all `Depends On` declarations resolve to valid files.
3. **Traceability Validation**: Traverse the DAG to ensure every downstream requirement traces to an upstream goal/problem (no orphans).
4. **Naming Validation**: Ensure all IDs (`PER-001`, `REQ-002`, `MET-005`) strictly follow the nomenclature standards.
5. **Template Validation**: Ensure no required section from the `Template Contract` was deleted or skipped.
6. **Section Validation**: Ensure the structural grouping of sections remains intact across all artifacts.
7. **Quality Gate Validation**: Ensure every individual `QG-` rule across `100-110` has been demonstrably satisfied.
8. **AI Context Validation**: Ensure the AI instructions are clear and present in every artifact.
9. **Machine Readability**: Ensure the markdown is perfectly formatted for AI parsing.
10. **Freeze Readiness**: Ensure every artifact's status is `Status: Frozen` or `Status: Approved`.

### Quality Gates
- **QG-FRZ-001**: Reject the Freeze if a single validation vector fails. The Discovery phase remains Open.
- **QG-FRZ-002**: Reject the Freeze if any artifact has `Status: Draft` or `Status: In Progress`.

## 3. Core Components

### 3.1 The Freeze Certificate
A formal declaration signed by the Executive Board and Enterprise Architecture Review Board that the Discovery phase is locked and Solution Architecture may begin.

### 3.2 The Traceability Report
A compiled, end-to-end matrix proving that every Requirement (`108`), Journey (`107`), and Risk (`110`) maps perfectly back to the core Problem (`101`) and Vision (`100`).

## 4. Output Contract
To guarantee deterministic AI orchestration for the downstream Delivery layers, this artifact explicitly produces the following machine-readable assets:
- **Discovery Manifest** (The canonical map of the frozen state)
- **Freeze Certificate** (The governance lock)
- **Artifact Index** (A registry of all generated files and their hashes)
- **Dependency Graph** (Visual/Data model of the DAG)
- **Coverage Report** (Showing % of requirements with metrics, % of journeys with risks, etc.)
- **Traceability Report** (The unified matrix)
- **Quality Report** (The audit log of all QG- checks passing)

## 5. Traceability
- Depends upon and validates `100_VisionStandard` through `110_AssumptionsAndRisksStandard`.

## 6. Context & AI Prompts
### Hydration Rules
- AI Swarms MUST run as a strict compiler. They MUST NOT attempt to "fix" missing traceability by hallucinating links. If traceability is broken, AI MUST fail the freeze and generate an Error Log.
- AI MUST generate a mathematically complete Dependency Graph.

### Memory TTL
- `Permanent` for the duration of the entire Product Lifecycle (This is the immutable foundation).

## 7. Anti-Patterns
- **The Sneaky Requirement**: Trying to slip in a final requirement into the Freeze document itself.
- **The Soft Freeze**: Allowing the Freeze to pass while artifacts remain in `Draft` state "to be finished later."
- **Manual Overrides**: Forcing the Freeze Certificate to generate without passing the 10 Validation Vectors.
