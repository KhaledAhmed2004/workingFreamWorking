---
Title: 053_DiscoveryExecutionRules
Artifact Version: 1.0
Framework Version: 1.0
Supersedes: N/A
Status: Frozen
Phase: Product Standards Infrastructure
Sprint: N/A
Owner: Enterprise Architecture Review Board
Reviewer: Chief Product Officer
Approver: Executive Board
Created: 2026-07-06
Updated: 2026-07-06
Approval Date: 2026-07-06
Last Reviewed: 2026-07-06
Review Status: Approved
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

## 3. Execution Preconditions
Before an execution may begin, ALL of the following must be true:
- All mandatory upstream artifacts are `Status: Frozen`.
- The target standard is `Status: Frozen`.
- The target template exists and matches the standard version.
- Required AI Context has been successfully hydrated.
- No unresolved Quality Gate failures exist upstream.

## 4. Generation Order
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

## 5. AI Execution Modes
AI Swarms operating within this layer must support the following execution modes:
- **Sequential**: Generating artifacts one-by-one, waiting for Human/System approval before proceeding.
- **Parallel**: Generating decoupled downstream artifacts simultaneously (see Section 6).
- **Incremental**: Updating a specific section of an existing Draft artifact without rewriting the entire file.
- **Recovery**: Attempting to fix a Validation/Quality Gate failure automatically based on the error output.
- **Re-validation**: Scanning the entire DAG after a breaking change to mark downstream nodes as `Status: In Review`.
- **Freeze Validation**: The final deterministic scan triggered by `111` to ensure absolute compliance before locking the Product Discovery artifact set.

## 6. Parallel Generation Rules
To optimize execution time, the following parallel generation lanes are permitted once their upstream blockers are `Status: Frozen`:

- **Lane 1**: After `103` is frozen, `104_Stakeholder` and `105_Persona` can technically be drafted concurrently, though `105` cannot be *validated* until `104` is complete.
- **Lane 2**: `109_SuccessMetrics` may be pre-drafted from `102_ProductGoalStandard`, but cannot be validated or frozen until `108_RequirementsStandard` is frozen.

## 7. Retry & Recovery Rules
If an AI Agent or Human encounters an error during execution:
- **Validation Failure (Syntax/Structure)**: 
  - *Retry Rule*: AI automatically retries up to 3 times, explicitly targeting the failed section.
  - *Rollback*: If 3 retries fail, revert to the last valid state and flag for Human Intervention.
- **Quality Gate Failure (Semantic/Logic)**:
  - *Retry Rule*: AI halts immediately. Quality Gate failures imply a logic flaw that requires human reasoning or a Gate Owner waiver. Do not brute-force.
- **Upstream Invalidation (Feedback Loop)**:
  - *Scenario*: `110_Assumptions` discovers a risk that invalidates `101_Problem`.
  - *Recovery*: AI halts all downstream execution. AI reverts `101` through `110` to `Status: Draft/In Review`. AI prompts the Human PM to rewrite `101`.

## 8. AI Hydration Pipeline & Context Loading Strategy
Before an AI Agent generates an artifact, it MUST hydrate its context window following this exact pipeline and priority load order:

**Context Priority Map:**
- **Priority 1**: Base Contracts (`050`, `051`)
- **Priority 2**: Architecture & Execution Manifests (`052`, `053`)
- **Priority 3**: Target Standard
- **Priority 4**: Upstream Artifacts
- **Priority 5**: User Prompt

```text
[Hydration Start]
   ↓
Load Priority 1, 2, and 3
   ↓
Query 052 Context Matrix for Mandatory Upstream Artifacts
   ↓
Load Priority 4 and 5
   ↓
[Execute Generation]
```

## 9. Context Optimization (Token Budget Strategy)
If the total context exceeds the LLM context limit:
1. Never compress Required Context.
2. Compress Optional Context first.
3. Preserve all Traceability IDs.
4. Preserve all Metrics verbatim.
5. Never summarize Principles.

## 10. Execution Checkpoints
To prevent cascading errors in massive enterprise products, execution is grouped into three mandatory human-review checkpoints.

- **Checkpoint A (Strategic Alignment)**: `100` through `103`.
  - *Gate*: Executive Board must sign off before any human-centric discovery begins.
- **Checkpoint B (Human Empathy)**: `104` through `107`.
  - *Gate*: Design Leadership must sign off on Journeys before technical requirements are drafted.
- **Checkpoint C (Solution Mechanics)**: `108` through `111`.
  - *Gate*: Enterprise Architecture Review Board must sign off to seal the Discovery Layer.

## 11. Execution Inputs & Outputs
- **Inputs**: Absolute file paths to all upstream dependencies mapped in `052`, plus user prompts.
- **Outputs**: A successfully linted markdown file adhering to the target `.template.md`.

## 12. Execution State Model
Every generative task follows this lifecycle:
- `Queued` -> `Context Hydrated` -> `Generating` -> `Validating` -> `Awaiting Review` -> `Complete`.

## 13. Human Intervention Rules
If an AI agent triggers a Quality Gate failure or exceeds 3 structural retry limits, the agent MUST pause execution and request human intervention. The human must resolve the conflict manually in the markdown file or update the prompt context before resuming the swarm.

## 14. Waiver Handling
If a strict architectural rule must be broken (e.g., bypassing a Quality Gate for an urgent experiment), the waiver MUST be documented in the Git commit message and approved by the Gate Owner defined in the standard. AI cannot grant waivers.

## 15. Execution Event Log
AI Agents MUST emit deterministic logs for every execution step. The logs must record: Agent ID, Artifact ID, Timestamp, Upstream nodes loaded, Token count, and Validation result. 

## 16. Execution Metadata Contract
When an artifact passes execution validation, the AI MUST automatically update the `Updated: [Date]` and `Status: In Review` metadata fields in the YAML frontmatter.

## 17. Agent Role Matrix
To maintain high quality, execution should be distributed among specialized agent personas:

| Role | Responsibility | Reads | Writes |
| :--- | :--- | :--- | :--- |
| **Strategy Agent** | Vision/Goals | 100-102 | 100-103 |
| **Research Agent** | Personas/Journeys | 100-104 | 104-107 |
| **Product Agent** | Requirements | 100-108 | 108-110 |
| **Validation Agent** | QA/Traceability | All | 111 |

## 18. Failure Classification
- **Transient Error**: LLM syntax hallucination (Auto-retry).
- **Semantic Error**: Quality Gate blocked by poor logic (Human intervention).
- **Fatal Error**: Upstream dependency was unexpectedly deleted or invalidated (Halt execution).

## 19. Timeout / Stale Execution Rules
If an artifact remains in `Status: In Review` for more than 14 days, the execution is considered Stale. The artifact MUST be re-validated against upstream dependencies before final freezing, in case upstream data shifted during the wait.

## 20. Completion Criteria
An execution job is complete when the artifact is successfully written to disk, passes the `050` validation contract, and is elevated to `Status: In Review` or `Frozen`.

## 21. Success Criteria
AI swarms can execute `100` through `111` for a net-new product with less than a 5% human intervention rate due to logical conflict.

## 22. Exit Criteria
This manifest may transition to Frozen only if:
- [x] Execution flow verified
- [x] Hydration pipeline verified
- [x] Retry model verified
- [x] Failure model verified
- [x] Parallel execution verified
- [x] Human intervention rules verified
- [x] Architecture Board approval
