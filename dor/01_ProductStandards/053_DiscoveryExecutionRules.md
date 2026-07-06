---
Title: 053_DiscoveryExecutionRules
Artifact Version: 1.0
Framework Version: 1.0
Supersedes: N/A
Status: Draft
Phase: Product Standards Infrastructure
Sprint: N/A
Owner: Enterprise Architecture Review Board
Reviewer: Chief Product Officer
Approver: Executive Board
Created: 2026-07-06
Updated: 2026-07-06
Approval Date: N/A
Last Reviewed: N/A
Review Status: N/A
Artifact ID: PS-053
Depends On: 052_DiscoveryArchitectureManifest.md
Next Artifact: 104_StakeholderStandard.md
---

# Discovery Execution Rules Manifest

## 1. Executive Statement
While `052_DiscoveryArchitectureManifest.md` dictates *what* the Discovery Layer is and *how* its nodes depend on each other, this document (`053_DiscoveryExecutionRules.md`) dictates exactly *how* humans and AI Agent Swarms execute that graph. It is the orchestration playbook that guarantees deterministic generation, parallelization, and error recovery for the entire Product Discovery phase.

## 2. Execution Principles
- **No Orphan Execution**: No artifact can be executed in isolation. Every execution must be aware of its upstream context.
- **Fail Fast**: If an artifact fails validation, execution halts immediately. Downstream nodes are not attempted until the failure is resolved.
- **Stateless Agents**: AI Agents must not rely on hidden memory. All context must be explicitly hydrated from frozen upstream artifacts.

## 3. Generation Order
All discovery artifacts MUST be generated in the following strict topological order to satisfy architectural dependencies:

1. `100_VisionStandard`
2. `101_ProblemStandard`
3. `102_ProductGoalStandard`
4. `103_ProductPrinciplesStandard`
5. `104_StakeholderStandard`
6. `105_PersonaStandard`
7. `106_JTBDStandard`
8. `107_JourneyStandard`
9. `108_RequirementsStandard`
10. `109_SuccessMetricsStandard`
11. `110_AssumptionsAndRisksStandard`
12. `111_DiscoveryFreezeStandard`

## 4. AI Execution Modes
AI Swarms operating within this layer must support the following execution modes:
- **Sequential**: Generating artifacts one-by-one, waiting for Human/System approval before proceeding.
- **Parallel**: Generating decoupled downstream artifacts simultaneously (see Section 5).
- **Incremental**: Updating a specific section of an existing Draft artifact without rewriting the entire file.
- **Recovery**: Attempting to fix a Validation/Quality Gate failure automatically based on the error output.
- **Re-validation**: Scanning the entire DAG after a breaking change to mark downstream nodes as `Status: In Review`.
- **Freeze Validation**: The final deterministic scan triggered by `111` to ensure absolute compliance before locking Layer 2.

## 5. Parallel Generation Rules
To optimize execution time, the following parallel generation lanes are permitted once their upstream blockers are `Status: Frozen`:

- **Lane 1**: After `103` is frozen, `104_Stakeholder` and `105_Persona` can technically be drafted concurrently, though `105` cannot be *validated* until `104` is complete.
- **Lane 2**: After `107` is frozen, `108_Requirements` and `109_SuccessMetrics` may be drafted concurrently by separate specialized agents (e.g., a PM Agent for 108, a Data Agent for 109).

## 6. Retry & Recovery Rules
If an AI Agent or Human encounters an error during execution:
- **Validation Failure (Syntax/Structure)**: 
  - *Retry Rule*: AI automatically retries up to 3 times, explicitly targeting the failed section.
  - *Rollback*: If 3 retries fail, revert to the last valid state and flag for Human Intervention.
- **Quality Gate Failure (Semantic/Logic)**:
  - *Retry Rule*: AI halts immediately. Quality Gate failures imply a logic flaw that requires human reasoning or a Gate Owner waiver. Do not brute-force.
- **Upstream Invalidation (Feedback Loop)**:
  - *Scenario*: `110_Assumptions` discovers a risk that invalidates `101_Problem`.
  - *Recovery*: AI halts all downstream execution. AI reverts `101` through `110` to `Status: Draft/In Review`. AI prompts the Human PM to rewrite `101`.

## 7. AI Hydration Pipeline
Before an AI Agent generates an artifact, it MUST hydrate its context window following this exact pipeline:

```text
[Hydration Start]
   ↓
Load Base Contracts (050, 051)
   ↓
Load Execution Rules (053)
   ↓
Load Target Artifact Standard (e.g., 104)
   ↓
Query 052 Context Matrix for Mandatory Upstream Artifacts
   ↓
Load Upstream Artifact Instances (e.g., Vision.md, Problem.md)
   ↓
[Execute Generation]
```

## 8. Execution Checkpoints
To prevent cascading errors in massive enterprise products, execution is grouped into three mandatory human-review checkpoints.

- **Checkpoint A (Strategic Alignment)**: `100` through `103`.
  - *Gate*: Executive Board must sign off before any human-centric discovery begins.
- **Checkpoint B (Human Empathy)**: `104` through `107`.
  - *Gate*: Design Leadership must sign off on Journeys before technical requirements are drafted.
- **Checkpoint C (Solution Mechanics)**: `108` through `111`.
  - *Gate*: Enterprise Architecture Review Board must sign off to seal the Discovery Layer.
