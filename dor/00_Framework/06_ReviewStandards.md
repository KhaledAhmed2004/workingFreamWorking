---
Title: 06_ReviewStandards
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
Artifact ID: ART-006
Depends On: 03_FrameworkWorkflow.md, 04_DocumentStandards.md, 05_ArtifactStandards.md
Previous Artifact: 05_ArtifactStandards.md
Decision IDs: N/A
Related Decisions: N/A
Related Risks: N/A
Reference Documents: N/A
Next Artifact: 08_QualityGates.md
---

# Enterprise Review Standards

## 1. Executive Statement
This document establishes the enterprise meta-standard for how framework components and product artifacts are formally reviewed, validated, and approved. It ensures that every review conducted within the Enterprise Product Discovery Framework is objective, traceable, and rigorously standardized by treating reviews themselves as formalized contracts.

## 2. Scope & Ownership Boundaries
To guarantee extreme enterprise scalability, this artifact strictly enforces the following responsibility boundaries:
- **This Document (`06_ReviewStandards.md`)**: Owns *how* reviews are performed, review contracts, review templates, and traceability.
- **Workflow (`03_FrameworkWorkflow.md`)**: Owns the state transitions (e.g., Draft → In Review → Approved).
- **Artifact Contract (`05_ArtifactStandards.md`)**: Owns the structural payload of the artifact being reviewed.
- **Quality Gates (`08_QualityGates.md`)**: Owns the specific testing criteria that must pass *before* review.
- **Governance (`09_Governance.md`)**: Owns authority matrices, security policies, enforcement, and compliance mandates.

## 3. Review Principles
Every review conducted within this framework MUST adhere to the following core philosophy:
- **Evidence-based Review**: Decisions must be justified by data, established standards, or explicit framework principles.
- **Scope-bound Review**: Reviewers must constrain their evaluation to the explicit scope of the artifact. Out-of-scope feedback must be logged separately.
- **Objective Evaluation**: Artifacts are measured against predefined Acceptance Criteria.
- **Constructive Feedback**: Feedback must be actionable, clear, and professional.
- **Traceable Decisions**: Every review outcome, comment, and resolution must be permanently recorded.
- **Review Independence**: Reviewers must evaluate the artifact independently of undue influence.
- **Conflict of Interest**: Reviewers must recuse themselves if they lack required impartiality.

## 4. Review Taxonomy (Classification)
To ensure organization and prioritization at scale, every individual review standard MUST explicitly declare its classification:
- **Mandatory Review**: Required for all framework/product progression (e.g., Architecture Review).
- **Optional Review**: Triggered at the discretion of the Owner (e.g., Peer Review).
- **Conditional Review**: Triggered only if specific risk thresholds are crossed (e.g., Compliance Review).
- **Periodic Review**: Time-based review independent of workflow progression (e.g., Quarterly Governance Review).
- **Continuous Review**: Automated or ongoing evaluation (e.g., Code Quality Scanning).
- **Emergency Review**: Expedited process for hotfixes or critical mitigations.

## 5. Review Standard Contract
To prevent chaotic, unstandardized feedback loops, the enterprise employs a "Standard of Reviews" model.
- **The Contract**: This document establishes the universal `Review Standard Contract`.
- **The Template**: Every specific review process (e.g., Architecture Review Standard) MUST implement the `Review Standard Contract Template`.

## 6. Review Standard Contract Template
Every dedicated Review Standard document MUST contain the following structural skeleton:
1. **Review Purpose**: The primary objective of the review type.
2. **Review Classification**: The taxonomy classification (from Section 4).
3. **Target Artifacts**: The specific artifacts subjected to this review.
4. **Required Participants**: Roles required to execute the review (Owner, Reviewer, Approver).
5. **Review Preconditions**: Gates that must be satisfied before starting.
6. **Review Execution Activities**: Standardized actions (separated by role) taken during evaluation.
7. **Required Evidence**: Specific data or artifacts required to justify the decision.
8. **Review Deliverables**: The expected outputs (e.g., Review Report, Decision Record).
9. **Decision Matrix**: Rules for arriving at Approved/Rejected.

## 7. Review Invariants
The following rules are immutable and cannot be overridden by any review standard:
- Every Review MUST fully implement the Review Standard Contract Template.
- Every Review MUST produce a formal Decision (Approved, Rejected, etc.).
- Every Review MUST produce traceable Evidence.
- Every Review MUST permanently record the Reviewer, Approver, and Timestamp.
- Every Review MUST yield a logged Approval Record.

## 8. Review Roles & Responsibilities
- **Owner**: The individual responsible for authoring the artifact and resolving review feedback.
- **Reviewer**: Subject matter experts tasked with evaluating the artifact and producing Review Deliverables.
- **Approver**: The designated authority who makes the final Review Decision based on Reviewer evidence.

## 9. Review Preconditions
An artifact MUST NOT enter a formal review execution state until:
- The artifact satisfies all required `08_QualityGates.md`.
- The artifact contains 100% of mandatory metadata.
- All declared Upstream Dependencies are in a `Frozen` or `Approved` state.

## 10. Review Execution Lifecycle
While `03_FrameworkWorkflow.md` defines the artifact's state, the review process itself has an internal execution lifecycle:
- **Scheduled**: The review is logged and pending Reviewer availability.
- **In Progress**: Reviewers are actively analyzing evidence and producing comments.
- **Completed**: The review has yielded a final Review Decision and Approval Record.
- **Cancelled**: The review was aborted prior to completion.

## 11. Review Execution Activities
During execution, responsibilities are strictly divided by role:
- **Owner Activities**: Provide requested clarifications, resolve Action Items, and supply missing evidence.
- **Reviewer Activities**: Evaluate the artifact payload against its defined Purpose, document all identified gaps or violations as traceable Action Items, and engage in dialogue with the Owner.
- **Approver Activities**: Validate that Reviewers have completed their tasks, assess the evidence, and issue the final formal Review Decision.

## 12. Review Evidence
All decisions must be backed by evidence. A Review Standard MUST explicitly define accepted Evidence Types:
- **Objective Evidence**: Code analysis, linting passes, quantitative telemetry, or checklist completion.
- **Subjective Evidence**: Expert testimony, heuristic evaluations, or UX critiques.
- **Historical Evidence**: Prior ADRs, post-mortems, or linked decisions used as precedent.
- **Derived Evidence**: Models or calculations built specifically to test the artifact's claims.
- **External Evidence**: Reference documents, regulatory laws, or third-party market research.

## 13. Review Deliverables
The output of a review is not a single binary, but a formalized set of deliverables. These may include:
- **Review Report**: A synthesized summary of the artifact's strengths, weaknesses, and risks.
- **Decision Record**: The formal outcome declared by the Approver.
- **Action Register**: A logged ledger of all mandatory corrections required.
- **Approval Record**: A permanent cryptographic or version-controlled log of sign-off.
- **Review Log**: Raw comments and dialogue from the review process.

### Review Metadata Contract
Any Review Deliverable MUST contain the following minimum machine-readable metadata:
`Review ID`, `Review Type`, `Target Artifact ID`, `Target Artifact Version`, `Started Timestamp`, `Completed Timestamp`, `Reviewer Identity`, `Approver Identity`, and `Final Outcome`.

## 14. Review Traceability
Enterprise-level reviews require absolute traceability. Every review record MUST mathematically link to answer:
- **Who**: Identities of the Reviewer and Approver.
- **What**: Which exact Action Items or comments were generated.
- **When**: Precise timestamp of the review initiation and completion.
- **Why (Decision Rationale)**: The explicit justification for the Decision, linking directly to the Evidence.
- **Which Version**: The exact version hash or number of the Target Artifact evaluated.

## 15. Review Relationship Model
Review Standards form an interconnected dependency graph. Reviews MUST declare relationships using canonical types:
- **Depends On**: Review A cannot begin until Review B is completed.
- **Consumes**: Review A utilizes the Deliverables of Review B as evidence.
- **Validates**: Review A confirms adherence to the rules established in Review B.
- **References**: Review A utilizes context from Review B without a strict dependency.
- **Supersedes**: Review A replaces a prior, deprecated Review B.
- **Escalates To**: Review A triggers Review B upon deadlock.

## 16. Review Standard Versioning Compatibility
To ensure the framework remains backward compatible as it evolves, every individual Review Standard MUST declare a `Minimum Framework Version` and a `Maximum Tested Framework Version` requirement in its payload or metadata. This guarantees that an older review standard can still be safely processed by newer iterations of the enterprise framework architecture.

## 17. Review Decision Matrix & Rules
Review Standards MUST declare how decisions are reached:
- **Decision Type**: Consensus, Majority Vote, or Authoritative Veto.
- **Authority**: The specific role holding final sign-off power.
- **Required Reviewers**: Minimum quorum required to validate the decision.

## 18. Review Outcomes
Every formal review MUST conclude with one of the following standardized states:
- **Approved**: Satisfies all criteria; authorized to proceed.
- **Conditionally Approved**: Approved subject to minor, listed Action Items being resolved (no secondary review needed).
- **Requires Refinement**: Contains significant gaps. Owner must resolve Action Items and resubmit.
- **Rejected**: Fundamentally violates framework principles. Work is halted.

## 19. Review Escalation
If an unresolvable deadlock occurs regarding Action Items or Scope:
1. **Peer Mediation**: A neutral SME is consulted.
2. **Governance Escalation**: The dispute is formally escalated to the Architecture Review Board for a binding decision.

## 20. Review Timeliness Principles
To prevent workflow bottlenecks:
- **SLA Adherence**: Reviews should be completed within organization-defined Service Level Agreements (SLAs).
- **Stale Review Protocol**: Artifacts blocked in review beyond SLA thresholds are subject to automatic escalation.

## 21. AI Review Compatibility
To prepare the enterprise for AI-agent orchestration, Review Standards MUST be machine-readable:
- **Structured Outputs**: All Review Deliverables must be parsable (e.g., JSON/YAML logs alongside markdown).
- **Review Schema**: Action items and decisions must map to a deterministic schema.
- **Automation Readiness**: Review Preconditions must be explicitly queryable by CI/CD pipelines.

## 22. Extension Mechanism
- Review standards may specify "Extension Points" for domain-specific evaluation criteria.
- Extensions must not override or contradict the Review Invariants.

## 23. Success Criteria
This artifact is successful when:
- 100% of Review Standards implement the Review Standard Contract Template.
- 100% traceability is mathematically achievable for every review.
- 100% of decisions have explicitly linked decision rationale and evidence.
- 0 orphan review standards exist.
- 0 reviews are conducted without a documented Approver.

## 24. Review Standard Compliance Matrix
To enable automated validation, Review Standards must adhere to this invariant matrix:

| Contract Element | Mandatory | Source |
| :--- | :--- | :--- |
| Review Purpose | Yes | Review Standard Contract |
| Review Classification | Yes | Review Standard Contract |
| Target Artifacts | Yes | Review Standard Contract |
| Participants | Yes | Review Standard Contract |
| Preconditions | Yes | Review Standard Contract |
| Execution Activities | Yes | Review Standard Contract |
| Required Evidence | Yes | Review Standard Contract |
| Deliverables | Yes | Review Standard Contract |
| Decision Matrix | Yes | Review Standard Contract |
| Review Decision | Yes | Review Invariants |
| Review Evidence | Yes | Review Invariants |
| Review Traceability | Yes | Review Invariants |
| Review Metadata | Yes | Review Invariants |

## 25. Exit Criteria
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
- [x] Contract completeness verified
- [x] Template compliance verified
- [x] No duplicated responsibility
- [x] No dependency cycle
- [x] Executive Approval Granted
