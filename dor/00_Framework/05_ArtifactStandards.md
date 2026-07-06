---
Title: 05_ArtifactStandards
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
Artifact ID: ART-005
Depends On: 01_FrameworkManifest.md, 02_FrameworkPrinciples.md, 03_FrameworkWorkflow.md, 04_DocumentStandards.md
Previous Artifact: 04_DocumentStandards.md
Decision IDs: N/A
Related Decisions: N/A
Related Risks: N/A
Reference Documents: N/A
Next Artifact: 06_ReviewStandards.md
---

# Enterprise Artifact Standards

## Executive Statement
This document establishes the generic structural meta-contract for all Product Artifacts within the Enterprise Product Discovery Framework. It dictates how domain-specific artifact standards (e.g., Vision Standard, PRD Standard) are defined, classified, related, and structurally validated, ensuring maximum modularity and discoverability at an enterprise scale.

```text
Enterprise Framework Hierarchy:

01_FrameworkManifest
        ↓
04_DocumentStandards
        ↓
05_ArtifactStandards       (← You are here: defines how to write a standard)
        ↓
Vision Standard            (Defines how to write a Vision artifact)
        ↓
Vision.md                  (The actual Product Vision payload)
```

## Scope / Objectives
This artifact defines the universal meta-standard that every individual artifact standard must implement. It explicitly does NOT define the actual domain payloads of individual artifacts, nor does it redefine document formatting or workflow states.

## Stakeholders
- **Owner**: Architecture Review Board / Enterprise Architect
- **Stakeholders**: Enterprise Architects, Governance Board
- **Consumers**: Product Managers, Engineering Leads, Framework Maintainers

## Terminology
Terminology follows Framework Vocabulary.

## Framework Context
- **Consumes**: `04_DocumentStandards.md` (Provides the base document structure)
- **Produces**: N/A
- **Influences**: Every individual artifact standard (e.g., `VisionStandard.md`)

## Document Non-Goals
This meta-standard explicitly does NOT define:
- Domain-specific artifact payloads (e.g., Product Vision, PRD, Roadmap), which must be owned by their respective dedicated standard documents.
- Universal document structures, markdown conventions, or metadata formatting (owned by `04_DocumentStandards.md`).
- Workflow states, approval gates, or artifact lifecycles (owned by `03_FrameworkWorkflow.md`).

---

## 1. Artifact Standard Contract
To prevent the framework from degrading into an unmaintainable monolith, the enterprise employs a "Standard of Standards" model. 
- **The Contract**: This document establishes the universal `Artifact Standard Contract`.
- **The Template**: The contract dictates that every future artifact standard MUST implement the `Artifact Standard Contract Template` (defined in Section 3).
- **The Rules**: The template sections MUST be implemented according to strict `Contract Rules` (defined in Section 4).

*(Contract → defines → Template → implemented via → Rules)*

## 2. Artifact Classification Taxonomy
To ensure organization and discoverability at scale, every individual artifact standard MUST explicitly declare its classification. An artifact may possess a Primary Classification and a Secondary Classification.
- **Strategic**: Artifacts that define long-term direction and investment (e.g., Vision, Strategy).
- **Analytical**: Artifacts that synthesize data or research (e.g., Market Analysis).
- **Planning**: Artifacts that schedule delivery or allocate resources (e.g., Roadmap).
- **Governance**: Artifacts that establish compliance, security, or enterprise rules (e.g., Framework Core).
- **Research**: Artifacts that capture raw user feedback or exploratory data (e.g., User Interviews).
- **Decision**: Artifacts that record explicit architectural or product choices (e.g., ADRs, Decision Logs).
- **Validation**: Artifacts that prove hypotheses or test functionality (e.g., Usability Test Results).

## 3. Artifact Standard Contract Template
Every dedicated artifact standard document MUST contain the following structural skeleton (in addition to the universal sections mandated by `04_DocumentStandards.md`):

1. **Purpose**: The primary objective of the artifact type.
2. **Artifact Type**: The fundamental nature of the artifact (e.g., Mandatory, Optional, Generated, Supporting, Reference).
3. **Scope**: What the artifact covers and does not cover.
4. **Consumers**: The downstream roles or artifacts that consume this output.
5. **Producers**: The roles responsible for generating this artifact.
6. **Required Inputs**: Upstream data or artifacts explicitly required to begin drafting.
7. **Guaranteed Outputs**: The expected tangible deliverables produced by the artifact.
8. **Assumptions**: Baseline facts considered true for the context of this artifact.
9. **Constraints**: Limitations (technical, business, or regulatory) restricting the artifact.
10. **Dependencies**: Upstream and downstream structural links.
11. **Validation**: The mechanisms used to structurally and logically validate the payload.
12. **Acceptance Criteria**: Measurable conditions that must be met for approval.
13. **Extension Points**: Permitted areas where teams can add domain-specific customization.

## 4. Contract Invariants
The following rule is immutable and cannot be overridden by any artifact standard:
- Every Artifact Standard MUST fully implement the Artifact Standard Contract Template without omitting any mandatory component. The Compliance Matrix governs this validation.

## 5. Contract Rules
When filling out the Template, artifact standards MUST adhere to the following implementation constraints:

### 5.1 Payload Rules
- Standards must explicitly define the mandatory sections (the payload) that the artifact requires.
- Standards must not prescribe strict page lengths, but rather focus on semantic completeness.

### 5.2 Dependency Rules
- Inputs and Outputs must be explicitly named (e.g., "Requires Approved Product Strategy").
- Avoid circular dependencies between artifacts.

### 5.3 Validation Rules
- Standards must define structural validation (e.g., "All checklist items must be filled").
- Qualitative review methodologies are deferred to Governance artifacts.

### 5.4 Completion Rules
- Completion rules must be binary and measurable, leaving no ambiguity as to whether an artifact is "done."

## 6. Artifact Dependency & Relationship Model
Artifact Standards do not exist in isolation. They form a massive interconnected graph. When a standard declares a relationship to another artifact, it MUST use one of the following canonical relationship types, specifying directionality for graph automation:

| Relationship | Direction | Meaning |
| :--- | :--- | :--- |
| **Depends On** | Incoming | Artifact A cannot be started/completed until Artifact B is available. |
| **Produces** | Outgoing | Artifact A directly generates Artifact B as an output. |
| **Consumes** | Incoming | Artifact A requires Artifact B as an input. |
| **Refines** | Bidirectional | Artifact A takes Artifact B and adds a deeper level of granular detail. |
| **Derived From** | Incoming | Artifact A is a subset or byproduct of Artifact B. |
| **References** | Weak | Artifact A utilizes context from Artifact B without a strict dependency. |
| **Validates** | Outgoing | Artifact A exists to prove or disprove hypotheses established in Artifact B. |
| **Justifies** | Outgoing | Artifact A provides the rationale for decisions made in Artifact B. |
| **Complements** | Bidirectional | Artifact A enhances Artifact B without directly modifying it. |
| **Conflicts With**| Bidirectional | Artifact A establishes constraints incompatible with Artifact B. |
| **Constrains** | Outgoing | Artifact A establishes boundaries or rules that Artifact B must obey. |
| **Owned By** | Incoming | Artifact A is a sub-component governed by Artifact B. |
| **Implements** | Outgoing | Artifact A executes or operationalizes the strategy or requirements of Artifact B. |
| **Supersedes** | Outgoing | Artifact A replaces an older or deprecated Artifact B. |

## 7. Artifact Standard Versioning Compatibility
To ensure the framework remains backward compatible as it evolves, every individual Artifact Standard MUST declare a `Minimum Framework Version` requirement in its payload or metadata. This guarantees that an older standard (e.g., `VisionStandard.md v1.0`) can still be safely processed by newer iterations of the enterprise framework architecture.

## 8. Artifact Naming Convention Compliance
Every Artifact Standard MUST comply with `12_NamingConvention.md`.

## 9. Extension Mechanism
- Individual artifact standards may specify "Extension Points" where product teams can append customized, domain-specific sections.
- These extensions must not override or contradict the mandatory payload defined by the standard.

## 10. Unknown Artifact Protocol
- If a product team produces a deliverable that lacks a formally defined standard in the framework, it is classified as an "Unknown Artifact."
- Unknown Artifacts must still conform to the universal structure in `04_DocumentStandards.md`.
- **Promotion Process**: Unknown Artifacts follow a strict lifecycle toward standardization:
  1. `Temporary`: Allowed for localized team use.
  2. `Reviewed`: Logged and assessed by the Architecture Review Board.
  3. `Approved`: Endorsed for enterprise-wide adoption.
  4. `Official Standard`: A dedicated Artifact Standard is authored and frozen.
- **Enterprise Rule**: Unknown Artifacts MUST NOT become enterprise dependencies until promoted to Official Standard.

## 11. Success Criteria
This artifact is successful when:
- 100% of Artifact Standards implement the Contract Template.
- 100% of Artifact Standards declare their Category and Artifact Type.
- 100% of Artifact Standards declare Required Inputs and Guaranteed Outputs.
- 100% of Artifact Standards declare Relationship Types.
- 0 duplicated payload definitions exist across standards.
- 0 orphan artifact standards exist.
- Every artifact standard is reachable from the Framework Manifest.

## 12. Artifact Standard Compliance Matrix
To enable AI and automated validation, standards must adhere to this invariant matrix:

| Contract Element | Mandatory | Source |
| :--- | :--- | :--- |
| Owner | Yes | Metadata / Stakeholders |
| Category | Yes | Artifact Contract |
| Artifact Type | Yes | Artifact Contract |
| Purpose | Yes | Artifact Contract |
| Scope | Yes | Artifact Contract |
| Required Inputs | Yes | Artifact Contract |
| Guaranteed Outputs | Yes | Artifact Contract |
| Dependencies | Yes | Artifact Contract |
| Validation | Yes | Artifact Contract |
| Acceptance Criteria | Yes | Artifact Contract |
| Extension Points | Yes | Artifact Contract |

## 13. Exit Criteria
*(Note: Completion Criteria defines the Definition of Done for a specific artifact, whereas Exit Criteria defines when this document itself is ready to freeze.)*

This artifact may transition to Frozen only if:
- [x] Formal Review Passed
- [x] Dependency Validation Passed
- [x] Boundary Validation Passed
- [x] Manifest Alignment Verified
- [x] Principle Alignment Verified
- [x] Workflow Alignment Verified
- [x] Document Standards Alignment Verified
- [x] Contract completeness verified
- [x] Template compliance verified
- [x] No duplicated responsibility
- [x] No dependency cycle
- [x] Executive Approval Granted
