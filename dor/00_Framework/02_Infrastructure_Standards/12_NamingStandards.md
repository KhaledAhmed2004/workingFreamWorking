---
Title: 12_NamingStandards
Artifact Version: 1.0
Framework Version: 1.0
Supersedes: N/A
Status: Frozen
Phase: Framework Core Infrastructure
Sprint: N/A
Owner: Framework Maintainer
Reviewer: Architecture Review Board
Approver: Executive Board
Created: 2026-07-06
Updated: 2026-07-06
Approval Date: 2026-07-06
Last Reviewed: 2026-07-06
Review Status: Approved
Artifact ID: ART-012
Depends On: 03_FrameworkWorkflow.md, 04_DocumentStandards.md, 05_ArtifactStandards.md, 06_ReviewStandards.md, 07_ValidationStandards.md, 08_QualityGates.md, 09_Governance.md, 10_AIStandards.md, 11_MetadataStandards.md
Previous Artifact: 11_MetadataStandards.md
Decision IDs: N/A
Related Decisions: N/A
Related Risks: N/A
Reference Documents: N/A
Next Artifact: 13_PromptStandards.md
---

# Enterprise Naming Standards

## 1. Executive Statement
This document establishes the definitive enterprise meta-standard governing Naming Conventions and Identity Architecture within the Enterprise Product Discovery Framework. Naming is the fundamental basis of addressing, graph linking, AI comprehension, and enterprise scale. This standard guarantees that every file, metadata key, AI agent, repository object, and relationship edge adheres to a deterministic, globally unique, and machine-readable naming taxonomy.

## 2. Scope & Ownership Boundaries
To maintain rigorous enterprise Separation of Concerns, this artifact strictly enforces the following ownership model:
- **`04_DocumentStandards.md`**: Owns markdown structure and formatting.
- **`11_MetadataStandards.md`**: Owns the structural schemas and typing of JSON/YAML data.
- **This Document (`12_NamingStandards.md`)**: Owns **the exact strings, casing, prefixes, and identifier formats** used within those schemas and documents.

**Crucial Invariant:** Naming defines ONLY identity. It NEVER defines behavior, state, ownership, or workflow logic. A file named `draft_feature.md` is an illegal boundary violation because it embeds workflow state into an identifier.

## 3. Naming Principles
Every identifier within this framework MUST adhere to the following principles:
- **Semantic First**: Names should convey immediate meaning without requiring lookup.
- **Consistency**: Identical concepts MUST use identical names across all domains.
- **Uniqueness**: Identifiers must guarantee collision-free resolution globally.
- **Machine Readability**: Names must be regex-friendly, parseable, and scriptable.
- **Determinism**: The same object generated twice must yield the exact same identifier.
- **Immutability of IDs**: Once an ID is assigned and merged, it can NEVER change.
- **Decoupled from State**: Identifiers must survive state changes, re-orgs, and directory moves.

## 4. Naming Taxonomy
The framework classifies names into the following canonical categories:
- **Artifact Names**: Static files and resources.
- **Metadata Keys**: The JSON/YAML property labels (e.g., `artifact_id`).
- **Schema Names**: The titles of data contracts.
- **Repository Objects**: Branches, commits, tags, and pull requests.
- **AI Agents**: The designations of autonomous actors.
- **Execution IDs**: The runtime records for Reviews, Validations, and Gates.
- **Governance IDs**: Waivers, Exceptions, and Escalations.
- **Relationship IDs**: The explicit graph edges connecting nodes.
- **Namespace IDs**: The hierarchical isolation domains.
- **Environment & Release Names**: The CI/CD deployment targets.

## 5. Naming Standard Contract
To prevent chaotic naming sprawl across teams, the framework employs a "Standard of Naming" model.
- **The Contract**: This document establishes the universal `Naming Standard Contract`.
- **The Template**: Every explicit identifier convention deployed in the enterprise MUST implement the `Naming Standard Contract Template`.

## 6. Naming Standard Contract Template
Every formally recognized Naming Convention MUST declare the following structural skeleton:
1. **Target Entity**: The object being named (e.g., "Metadata Key").
2. **Casing Rule**: The exact case convention mandated (e.g., `snake_case`).
3. **Prefix/Suffix Rules**: Required affixes (e.g., `ART-`).
4. **Delimiter**: Allowed separation characters (e.g., `-` or `_`).
5. **Length Constraint**: Minimum and maximum character limits.
6. **Forbidden Characters**: Characters explicitly banned (e.g., whitespace, special symbols).
7. **Regex Contract**: A deterministic regular expression pattern that strictly validates the identifier format.

## 7. Naming Invariants
The following rules are immutable:
- Every enterprise object MUST possess exactly one canonical machine ID.
- Names MUST NOT be ambiguous or rely on folder context to be understood.
- Names MUST NOT encode workflow states (e.g., `V1_final_reviewed`).
- Display Names (Human-readable) may change; Canonical IDs (Machine-readable) NEVER change.
- Identifiers MUST remain stable across framework version upgrades.

## 8. Identifier Model
Identifiers operate on a tiered resolution system:
- **Global IDs (URN/UUIDv4)**: `urn:uuid:123e4567-e89b...` (Used for cryptographic traceability).
- **Semantic IDs**: `[PREFIX]-[SEQ]` (e.g., `ART-012`) (Used for human-machine bridging).
- **Composite IDs**: `[DOMAIN]-[PREFIX]-[SEQ]` (e.g., `SEC-GATE-004`) (Used for context injection).
- **Hash IDs**: `sha256:a1b2c3d4...` (Used for payload execution context).
- **Display Names**: Human-readable strings mapped to IDs via `11_MetadataStandards`.
- **Aliases**: Canonical redirects for backward compatibility during deprecations.

### 8.1 Identifier Registry
To guarantee zero collisions across a massive enterprise, all Semantic IDs and Custom Prefixes MUST be registered in a centralized, machine-readable **Identifier Registry** database prior to deployment.

## 9. Namespace Model
To prevent Semantic ID collisions in a massive enterprise, namespaces MUST be explicitly declared in hierarchical order:
1. **Enterprise**: `corp`
2. **Framework**: `fw`
3. **Domain**: `sec` (Security), `arch` (Architecture)
4. **Project/Product**: `auth` (Authentication)
5. **Module**: `oauth`
*Example Semantic ID:* `corp-fw-sec-auth-oauth-001`

## 10. Case Convention Model
Case conventions are strictly enforced based on the target entity:
- `PascalCase`: Schema Definitions, Class Names, Graph Node Types.
- `camelCase`: JSON payloads, Local Variables.
- `snake_case`: Metadata Keys (e.g., `approval_date`), Database Columns.
- `kebab-case`: File Names (e.g., `01-vision-document.md`), URLs, API Endpoints, Repositories, Branch names.
- `SCREAMING_SNAKE_CASE`: Environment Variables, Global Constants, AI Prompt IDs.
- `lowercase`: Namespace declarations.

## 11. Prefix & Suffix Model
Semantic IDs MUST utilize canonical prefixes to immediately identify the entity class:
- `ART-`: Artifact
- `REV-`: Review Record
- `VAL-`: Validation Payload
- `GATE-`: Quality Gate Definition
- `GOV-`: Governance Directive
- `WAIV-`: Governance Waiver
- `EXC-`: Governance Exception
- `AI-`: Autonomous Agent Profile
- `META-`: Schema Definition
- `REL-`: Release / Baseline
- `PRMT-`: System Prompt

## 12. Reserved Names
The following terms are enterprise-reserved and MUST NOT be used as custom identifiers, local variable names, or ad-hoc file names:
- `system`, `core`, `framework`, `admin`, `root`, `meta`.
- Any exact match to a standard Phase name (e.g., `Draft`, `Frozen`).
- Any exact match to a Canonical Outcome (e.g., `Pass`, `Fail`, `Waived`).

## 13. Relationship Naming
Graph Edges (Relationships) MUST be named as actionable verbs in `PascalCase`:
- `DependsOn`
- `Consumes`
- `Produces`
- `DerivedFrom`
- `Overrides`
- `DelegatesTo`
- `Validates`

## 14. Metadata Key Naming
- Metadata Keys MUST use `snake_case`.
- Keys representing booleans MUST use `is_`, `has_`, or `can_` prefixes (e.g., `is_frozen`).
- Keys representing timestamps MUST explicitly declare the format as a suffix (e.g., `created_at_utc`).
- Keys MUST NOT use abbreviations unless they are globally recognized enterprise acronyms (e.g., `uuid`).

## 15. Version Naming
The framework enforces Semantic Versioning (SemVer 2.0.0) across all objects:
- `v[MAJOR].[MINOR].[PATCH]` (e.g., `v1.2.0`).
- **Major**: Breaking structural changes to a schema or contract.
- **Minor**: Non-breaking additions (e.g., new optional metadata keys).
- **Patch**: Typo fixes or non-structural clarity updates.

## 16. Repository Naming Compatibility
File systems and git repositories impose specific limitations:
- All Markdown and JSON/YAML file names MUST use `kebab-case`.
- Spaces and special characters (`!`, `@`, `#`, etc.) are explicitly forbidden in file paths.
- Branch names MUST follow: `[type]/[issue-id]-[short-description]` (e.g., `feat/ART-012-naming-standards`).

## 17. AI Naming Compatibility
To ensure LLM agents can parse the knowledge graph without ambiguity:
- **No Overloading**: Do not use the word `Review` to mean both "The Document" and "The Action". Use `ReviewRecord` and `ReviewExecution`.
- **Context-Independent Names**: An AI agent reading a file name in isolation must understand its purpose. `config.json` is illegal; `quality_gate_config.json` is required.
- **Prompt Friendly**: Identifiers must not contain complex escape characters that could break JSON parsing inside LLM function calls.

## 18. Naming Evolution Strategy
When a naming convention is updated:
- Existing frozen identifiers are **NEVER** retroactively renamed.
- The `11_MetadataStandards` `Supersedes` relationship is used to link a deprecated ID to the new compliant ID.
- Automation parsers must support resolving both legacy and active identifiers during the migration window.

## 19. Extension Mechanism
- Sub-organizations may define custom namespace prefixes (e.g., `HR-ART-001`).
- Custom prefixes MUST be registered in a central enterprise registry to prevent collisions.
- Extensions MUST NOT alter the Casing Rules or Reserved Words lists.

## 20. Success Criteria
This artifact is successful when:
- 100% of newly generated artifacts pass deterministic regex naming checks.
- 0 file names contain spaces or uppercase letters.
- 100% of Metadata Keys utilize `snake_case`.
- 100% of Semantic IDs guarantee global uniqueness via Namespace or Sequence design.

## 21. Naming Compliance Matrix
To enable automated governance, Naming Standards must adhere to this invariant matrix:

| Contract Element | Mandatory | Source |
| :--- | :--- | :--- |
| Target Entity | Yes | Naming Standard Contract |
| Casing Rule | Yes | Naming Standard Contract |
| Prefix/Suffix Rules | Yes | Naming Standard Contract |
| Delimiter | Yes | Naming Standard Contract |
| Length Constraint | Yes | Naming Standard Contract |
| Forbidden Characters| Yes | Naming Standard Contract |
| Regex Contract | Yes | Naming Standard Contract |
| Zero State Encoding | Yes | Naming Invariants |
| Canonical Edges | Yes | Naming Invariants |

## 22. Exit Criteria
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
- [x] Validation Standards Alignment Verified
- [x] Quality Gate Alignment Verified
- [x] Governance Alignment Verified
- [x] AI Standards Alignment Verified
- [x] Metadata Standards Alignment Verified
- [x] Contract completeness verified
- [x] Template compliance verified
- [x] No duplicated responsibility
- [x] No dependency cycle
- [x] Executive Approval Granted
