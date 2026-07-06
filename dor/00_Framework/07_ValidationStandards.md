---
Title: 07_ValidationStandards
Artifact Version: 1.0
Framework Version: 1.0
Supersedes: N/A
Status: Frozen
Phase: Framework Core
Sprint: N/A
Owner: Framework Maintainer
Reviewer: Architecture Review Board
Approver: Executive Board
Created: 2026-07-06
Updated: 2026-07-06
Approval Date: 2026-07-06
Last Reviewed: 2026-07-06
Review Status: Approved
Artifact ID: ART-007
Depends On: 03_FrameworkWorkflow.md, 04_DocumentStandards.md, 05_ArtifactStandards.md, 06_ReviewStandards.md
Previous Artifact: 06_ReviewStandards.md
Decision IDs: N/A
Related Decisions: N/A
Related Risks: N/A
Reference Documents: N/A
Next Artifact: 08_QualityGates.md
---

# Enterprise Validation Standards

## 1. Executive Statement
This document establishes the enterprise meta-standard for deterministic artifact validation. It defines how artifacts are objectively tested for structural correctness, completeness, and schema adherence. Validation is a prerequisite layer that strictly precedes subjective human review, ensuring that only structurally sound artifacts consume review bandwidth.

## 2. Scope & Ownership Boundaries
This artifact establishes a profound and highly necessary enterprise boundary between testing, reviewing, and enforcing:
- **This Document (`07_ValidationStandards.md`)**: Owns *how to construct a deterministic test* (e.g., Schema matching, Link resolution).
- **Review Standards (`06_ReviewStandards.md`)**: Owns *Subjective / Qualitative Evaluation* (e.g., Is the strategy sound? Is the architecture scalable?).
- **Quality Gates (`08_QualityGates.md`)**: Owns the *Enforcement Thresholds* (e.g., "The artifact cannot progress to Review unless it passes 100% of Critical Validations").

**Framework Definition Order:**
`03` Workflow → `04` Document → `05` Artifact → `06` Review → `07` Validation → `08` Quality Gates → `09` Governance

**Operational Pipeline:**
`Author` → `Validation` (07) → `Quality Gates` (08) → `Review` (06) → `Workflow Transition` (03)

## 3. Validation Principles
Every validator constructed within this framework MUST adhere to the following core philosophy:
- **Deterministic**: Validation outcomes must be 100% reproducible. Given the same artifact state, the validation result must be identical.
- **Automated by Default**: Validation should require zero human intervention.
- **Binary Outcomes**: Validations do not yield opinions; they yield absolute `Pass` or `Fail` signals.
- **Traceable Errors**: A failed validation must explicitly point to the line, field, or missing dependency causing the failure.
- **Context-Free**: Validators must not require deep domain knowledge to execute.

## 4. Validation Taxonomy
To categorize automated checks, every Validation Standard MUST declare its taxonomy classification:
- **Schema Validation**: Ensures the artifact implements the exact structural template mandated by `05_ArtifactStandards.md`.
- **Metadata Validation**: Ensures all frontmatter and required tags (e.g., Owner, Status, Artifact ID) are present and correctly formatted (`04_DocumentStandards.md`).
- **Dependency Validation**: Verifies that all declared upstream and downstream links (`Depends On`, `Produces`) exist and are reachable.
- **Lifecycle Validation**: Confirms the artifact's current state aligns with the allowed transitions in `03_FrameworkWorkflow.md`.
- **Markdown / Syntax Linter**: Checks formatting, heading hierarchies, and broken links.
- **Semantic Validation**: Verifies the meaning or contextual correctness of elements.
- **Cross-Artifact Validation**: Ensures consistency between artifacts (e.g., verifying that a Vision references a Strategy that actually exists and has identical unique IDs).

## 5. Validation Standard Contract
To prevent fragmented or ad-hoc scripting, the enterprise employs a "Standard of Validators" model.
- **The Contract**: This document establishes the universal `Validation Standard Contract`.
- **The Template**: Every specific validation tool, script, or AI instruction set MUST implement the `Validation Standard Contract Template`.
- **Validation Rules**: A single Validation Standard may contain multiple `Validation Rules` (e.g., a "Markdown Validation Standard" may contain rules for heading hierarchy, link resolution, and bold formatting).

## 6. Validation Standard Contract Template
Every dedicated Validation Standard MUST declare the following structural skeleton:
1. **Validation Purpose**: The deterministic objective of the check.
2. **Validation Taxonomy**: The classification (from Section 4).
3. **Target Artifacts**: The specific artifacts or directories subjected to this validation.
4. **Trigger Condition**: When the validation executes (e.g., Manual, Scheduled, Event Driven, Pipeline, AI Invocation).
5. **Evaluation Logic**: The explicit rule, regex, or logic used to determine correctness.
6. **Pass Condition**: The exact state that yields a `Pass` signal.
7. **Failure Output**: The standardized error message or machine exit code emitted upon failure.

## 7. Validation Invariants
The following rules are immutable and cannot be overridden by any validation script:
- Every Validation MUST fully implement the Validation Standard Contract Template.
- Every Validation MUST execute without requiring human input.
- Every Validation MUST emit a deterministic `Pass` or `Fail` state.
- Every Validation MUST produce machine-readable Deliverables.

## 8. Validation Execution Lifecycle
Validators operate within a strict execution lifecycle, wholly separate from the workflow state of the artifact itself:
- **Pre-Flight**: Running locally in the author's IDE (e.g., Markdown linting).
- **Pre-Commit**: Running as a hook before code/documentation is committed.
- **Pipeline Execution**: Running in a CI/CD environment or AI Agent Orchestrator.
- **Post-Flight**: Yielding the final Validation Deliverables for consumption by `08_QualityGates.md`.

## 9. Validation Deliverables
The output of a Validation is a formalized data payload. A Validation MUST standardly emit:
- **Validation Result**: The binary or categorized outcome state (`PASS`, `FAIL`, `WARNING`, `SKIPPED`).
- **Validation Report**: A human-readable summary of what was checked and what failed.
- **Machine Exit Code**: Standard UNIX exit codes (`0` for success, non-zero for failure).
- **Linter Log**: Granular, line-by-line output of schema violations.
- **Validation Metadata**: `Validator ID`, `Target Artifact ID`, `Execution Timestamp`, and `Execution Duration`.

## 10. Validation Evidence
A validation deliverable alone is not enough; the validator MUST produce explicit evidence proving *why* the decision was reached. Accepted evidence types include:
- **Schema Definition**: The exact versioned schema used for evaluation.
- **Artifact Metadata**: The raw tags parsed during validation.
- **Dependency Graph**: The resolved paths of all linked artifacts.
- **Markdown AST**: The Abstract Syntax Tree used for structural linting.
- **Link Resolver Output**: Ping results for external or internal references.
- **Lint Results**: Line-by-line violation outputs.

## 11. Validation Relationship Model
Validation Standards form an interconnected dependency graph. Validations MUST declare relationships using canonical types:
- **Consumes**: Validation A utilizes the output of Artifact B.
- **Produces**: Validation A produces validation deliverables consumed by downstream artifacts, quality gates, or automation systems.
- **Validates**: Validation A confirms adherence to the rules established in Artifact/Standard B.
- **Depends On**: Validation A cannot execute until Validation B completes.
- **References**: Validation A utilizes context from Validation B without a strict dependency.
- **Supersedes**: Validation A replaces a prior, deprecated Validation B.

## 11. Validation Standard Versioning Compatibility
To ensure the framework remains backward compatible as it evolves, every individual Validation Standard MUST declare a `Minimum Framework Version` and a `Maximum Tested Framework Version` requirement in its payload or metadata. This guarantees that an older validation script can still be safely processed by newer iterations of the enterprise framework architecture.

## 12. Validation Naming Convention Compliance
Every Validation Standard and Validation Rule MUST comply with `12_NamingConvention.md` to ensure programmatic discoverability and execution logging.

## 13. Extension Mechanism
- Validation standards may specify "Extension Points" where product teams can append customized, domain-specific validation rules.
- These extensions must not override or contradict the core Validation Invariants.

## 14. AI Validator Compatibility
To prepare the enterprise for AI-agent orchestration, Validation Standards MUST be natively compatible with LLM processing:
- **JSON/YAML Output**: All Validation Deliverables must be emitted in structured formats alongside markdown.
- **Prompt-Ready Rules**: The `Evaluation Logic` defined in the Contract Template must be written clearly enough that an AI Agent can act as the validator without a hardcoded script.
- **Deterministic Prompt Contract**: Validators must provide versioned, strictly structured prompt definitions to guarantee identical AI evaluations across different runs.
- **Headless Execution**: Validators must not rely on UI prompts or interactive shells.

## 15. Success Criteria
This artifact is successful when:
- 100% of Validation Standards implement the Validation Standard Contract Template.
- 100% of defined validations produce machine-readable Deliverables.
- 100% of validation failures produce deterministic remediation information.
- 0 validations require subjective human interpretation.
- 0 validations attempt to block pipeline progression directly (deferring enforcement to Quality Gates).

## 16. Validation Standard Compliance Matrix
To enable automated governance, Validation Standards must adhere to this invariant matrix:

| Contract Element | Mandatory | Source |
| :--- | :--- | :--- |
| Validation Purpose | Yes | Validation Standard Contract |
| Validation Taxonomy | Yes | Validation Standard Contract |
| Target Artifacts | Yes | Validation Standard Contract |
| Trigger Condition | Yes | Validation Standard Contract |
| Evaluation Logic | Yes | Validation Standard Contract |
| Pass Condition | Yes | Validation Standard Contract |
| Failure Output | Yes | Validation Standard Contract |
| Binary Outcome | Yes | Validation Invariants |
| Machine Deliverable| Yes | Validation Invariants |

## 17. Exit Criteria
*(Note: Completion Criteria defines the Definition of Done for a specific artifact, whereas Exit Criteria defines when this document itself is ready to freeze.)*

This artifact may transition to Frozen only if:
- [x] Formal Review Passed
- [x] Dependency Validation Passed
- [x] Boundary Validation Passed
- [x] Manifest Alignment Verified
- [x] Principle Alignment Verified
- [x] Workflow Alignment Verified
- [x] Document Standards Alignment Verified
- [x] Artifact Standards Alignment Verified
- [x] Review Standards Alignment Verified
- [x] Contract completeness verified
- [x] Template compliance verified
- [x] No duplicated responsibility
- [x] No dependency cycle
- [x] Executive Approval Granted
