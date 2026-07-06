---
Title: 11_MetadataStandards
Artifact Version: 1.0
Framework Version: 1.0
Supersedes: N/A
Status: Draft
Phase: Framework Core Infrastructure
Sprint: N/A
Owner: Framework Maintainer
Reviewer: Architecture Review Board
Approver: Executive Board
Created: 2026-07-06
Updated: 2026-07-06
Approval Date: N/A
Last Reviewed: N/A
Review Status: N/A
Artifact ID: ART-011
Depends On: 03_FrameworkWorkflow.md, 04_DocumentStandards.md, 05_ArtifactStandards.md, 06_ReviewStandards.md, 07_ValidationStandards.md, 08_QualityGates.md, 09_Governance.md, 10_AIStandards.md
Previous Artifact: 10_AIStandards.md
Decision IDs: N/A
Related Decisions: N/A
Related Risks: N/A
Reference Documents: N/A
Next Artifact: 12_NamingStandards.md
---

# Enterprise Metadata Standards

## 1. Executive Statement
This document establishes the definitive enterprise meta-standard governing Metadata Architecture within the Enterprise Product Discovery Framework. Metadata is the universal, machine-readable nervous system of the enterprise. It dictates how artifacts, pipelines, AI agents, and governance entities deterministically communicate. This standard guarantees that every unit of information within the framework is identifiable, typed, versioned, and perfectly decoupled from qualitative document content.

## 2. Scope & Ownership Boundaries
To maintain rigorous enterprise Separation of Concerns, this artifact strictly enforces the following ownership model:
- **`04_DocumentStandards.md`**: Owns the human-readable formatting and markdown syntax of files.
- **`12_NamingStandards.md`**: Owns how IDs and files are named (e.g., prefixing, casing).
- **`10_AIStandards.md`**: Owns the execution logic of autonomous agents.
- **This Document (`11_MetadataStandards.md`)**: Owns **the structural schema, identity model, typing, serialization, and inheritance rules of the data payload itself**.

**Crucial Invariant:** This standard acts as the Enterprise Data Contract. No future standard may redefine metadata properties already owned by this document. Metadata strictly describes the system state; it never contains operational business logic.

## 3. Metadata Principles
Every metadata schema deployed within this framework MUST adhere to the following principles:
- **Machine Readable First**: Metadata must be natively parsable by software without regex or NLP scraping.
- **Deterministic**: Data typing must be strict (e.g., ISO-8601 for timestamps, boolean arrays).
- **Immutable Identity**: Once generated, a core identity (ID) can never change.
- **Minimal Duplication**: Metadata must reference existing properties via the Relationship Model rather than duplicating values.
- **Single Source of Truth**: The schema dictates exactly where a piece of state lives.
- **Version Aware**: Schemas must include migration paths for legacy data.
- **Extensible & Composable**: Schemas must support appending custom key-value pairs without breaking core validation.
- **Vendor Neutral & AI Ready**: Schemas must rely on universal standards (JSON/YAML) and explicit keys to guarantee LLM agnosticism.

## 4. Metadata Taxonomy
Metadata payloads are classified into the following canonical domains:
- **Artifact Metadata**: Describes the identity, phase, and state of a static document.
- **Review Metadata**: Describes the qualitative human evaluation of an artifact.
- **Validation Metadata**: Describes the deterministic execution results of compliance checks.
- **Quality Gate Metadata**: Describes the automated block/pass enforcement thresholds.
- **Governance Metadata**: Describes exception waivers, directives, and authority escalations.
- **AI Metadata**: Describes the agent executing a task, prompt hashes, and confidence vectors.
- **Relationship Metadata**: Describes the graph edges (Depends On, Consumes) between nodes.
- **Version Metadata**: Describes the iteration history and backward compatibility limits.
- **Execution Metadata**: Describes timestamps, runtimes, and CI/CD context.
- **Repository Metadata**: Describes the physical file location, commit hash, and branch.

## 5. Metadata Standard Contract
To prevent fragmented JSON/YAML structures across the enterprise, the framework employs a "Standard of Schemas" model.
- **The Contract**: This document establishes the universal `Metadata Standard Contract`.
- **The Template**: Every explicit JSON/YAML definition used in the framework MUST implement the `Metadata Standard Contract Template`.

## 6. Metadata Standard Contract Template
Every formally recognized Metadata Definition MUST declare the following structural skeleton:
1. **Metadata Purpose**: The exact domain this schema governs.
2. **Metadata Owner**: The specific framework tier responsible for generating this payload.
3. **Metadata Scope**: Whether this metadata applies globally or to a specific artifact class.
4. **Required Fields**: Keys that must exist for the schema to be structurally valid.
5. **Optional Fields**: Keys that enhance context but do not break schema validation.
6. **Inheritance Rules**: Defines which parent fields are automatically mapped to this schema.
7. **Validation Rules**: Type constraints (e.g., Integer >= 0, Enum limits).
8. **Extension Points**: The designated `custom_metadata` objects allowing unstructured local injection.
9. **Compatibility Rules**: Min/Max schema versions supported.
10. **Consumers**: The specific tools, agents, or Quality Gates that rely on reading this schema.

## 7. Metadata Invariants
The following rules are immutable:
- Every entity (Artifact, Gate, Review, Exe) MUST possess a globally unique identity.
- Metadata MUST NEVER duplicate or embed the qualitative text of the document it describes.
- Metadata MUST be natively serialized into valid JSON or YAML.
- Metadata MUST NOT contain executable code or business logic instructions.
- Metadata MUST be version-aware (explicitly declaring its schema version).
- Metadata MUST guarantee traceability back to its originating trigger (human or AI).

## 8. Metadata Identity Model
The enterprise requires a unified identification architecture that guarantees zero collisions.
- **Global IDs**: Every ID must utilize a universal format (to be formally standardized in `12_NamingStandards.md`), such as UUIDv4 or deterministic semantic concatenation.
- **Artifact IDs**: Identifies the static resource (e.g., `ART-001`).
- **Execution IDs**: Identifies the runtime event (e.g., `Review Execution`, `Validation Run`).
- **Relationship IDs**: Identifies the explicit edge connecting two node IDs.
- **Hash References**: Cryptographic hashes (e.g., SHA-256) MUST be utilized to identify the precise snapshot of data an AI consumed (`Context Hash`).
- **Stable Identifiers**: An ID remains constant even if the file is moved to a new repository.

## 9. Metadata Inheritance Model
Metadata properties propagate hierarchically to minimize duplication:
- **Inheritance**: A child artifact automatically inherits the `Phase` and `Sprint` metadata of its parent epic unless explicitly overridden.
- **Overrides**: An explicit local metadata declaration takes precedence over an inherited value.
- **Composition**: Larger schemas (e.g., `Gate Execution Record`) are constructed by composing smaller schemas (`Gate Rule Schema` + `Validation Payload Schema`).
- **Default Values**: The schema dictates hardcoded fallbacks if an optional key is omitted.

## 10. Metadata Relationship Model
Metadata enables Knowledge Graph traversal. Every explicit relationship MUST use a canonical edge definition:
- **Parent / Child**: Structural hierarchy (e.g., Epic → User Story).
- **References**: Non-blocking contextual linkage.
- **Depends On**: Hard execution blocker (Target cannot progress if Dependency is unapproved).
- **Consumes**: Data input edge (Quality Gate reads Validation Payload).
- **Produces**: Data output edge (Validation yields Payload).
- **Derived From**: AI extraction edge (Summary derived from Meeting Notes).
- **Supersedes**: Replaces an older, deprecated entity.
- **Version Of**: Identifies iteration chains.
- **Implements**: Structural realization of an abstract contract.

## 11. Metadata Versioning Model
Schemas must evolve without breaking existing CI/CD pipelines.
- **Compatibility**: All schema updates MUST be backward compatible within a major Framework Version.
- **Evolution**: Introducing new required fields is a breaking change and requires a major schema version bump.
- **Forward Compatibility**: Parsers MUST ignore unrecognized optional keys to prevent execution halts.
- **Deprecation**: Deprecated keys must remain in the schema for a minimum of one major version iteration.

## 12. Metadata Validation Model
Metadata validation is strictly structural.
- **Structural Validation Only**: Validates that keys exist and match type constraints (e.g., `Status` must be an Enum of `[Draft, In Review, Frozen]`).
- **No Business Validation**: Metadata validation does NOT check if `Status: Frozen` is legally allowed (that is a `08_QualityGates` responsibility).
- **No Review Logic**: Metadata validation does NOT assess qualitative depth.

## 13. Metadata Lifecycle
Metadata properties transition through specific states:
- **Creation**: Instantiated as a blank structural template when an artifact is drafted.
- **Modification**: Fields mutate as the artifact traverses workflow states.
- **Deprecation**: Legacy schemas flagged during enterprise framework updates.
- **Archiving**: Metadata snapshotted into read-only graph storage.
- **Retirement**: Permanent purging of non-compliant schema entries.

## 14. Metadata Traceability
Every execution metadata payload MUST provide an unbreakable lineage trail:
- **Identity**: Who (User ID) or What (AI Agent ID) generated the metadata payload.
- **Origin**: Which specific framework standard mandated the generation of this payload.
- **Timestamp**: ISO-8601 UTC execution time.
- **Version**: The schema version utilized.
- **Lineage**: The array of preceding Execution IDs that resulted in this state change.

## 15. Metadata Interoperability
Enterprise metadata MUST be instantly consumable across the entire tech stack:
- **Serialization**: 100% compliant with JSON and YAML formats.
- **Storage Strategy**: Artifact metadata persists as YAML Frontmatter; execution/audit metadata persists as detached JSON sidecar records.
- **API Readiness**: Schemas must map 1:1 with REST/GraphQL payload definitions.
- **Knowledge Graph**: Every Metadata ID and Relationship Edge must natively map to standard graph database schemas (e.g., Neo4j, Gremlin).

## 16. Metadata Extension Mechanism
- Product teams may inject domain-specific keys into the designated `custom_metadata` JSON object.
- Extension metadata MUST NOT override or conflict with globally required keys.
- Automation parsers must be configured to pass-through extension metadata without validating its internal structure.

## 17. AI Metadata Compatibility
To support `10_AIStandards`, metadata schemas must explicitly accommodate autonomous agents:
- **Schema Legibility**: Key names must be verbose and semantically clear to reduce LLM prompt ambiguity (e.g., use `approval_timestamp_utc` instead of `app_ts`).
- **Context Injection**: Schemas must provide designated fields for `Agent Confidence Contract` and `Context Hash`.
- **System Prompt Hashing**: Any metadata payload generated by an AI MUST include the hash of the system prompt used to generate it.

## 18. Success Criteria
This artifact is successful when:
- 100% of framework execution payloads implement the Metadata Standard Contract Template.
- 0 structural JSON/YAML schemas are defined outside of this standard.
- 100% of relationships utilize the canonical Edge Definitions.
- AI Agents can parse the enterprise graph without requiring regex text extraction.

## 19. Metadata Compliance Matrix
To enable automated governance, Metadata Standards must adhere to this invariant matrix:

| Contract Element | Mandatory | Source |
| :--- | :--- | :--- |
| Metadata Purpose | Yes | Metadata Standard Contract |
| Metadata Owner | Yes | Metadata Standard Contract |
| Required Fields | Yes | Metadata Standard Contract |
| Validation Rules | Yes | Metadata Standard Contract |
| Inheritance Rules| Yes | Metadata Standard Contract |
| Compatibility Rules| Yes | Metadata Standard Contract |
| JSON/YAML Strict | Yes | Metadata Invariants |
| Zero Business Logic| Yes | Metadata Invariants |

## 20. Exit Criteria
*(Note: Completion Criteria defines the Definition of Done for a specific artifact, whereas Exit Criteria defines when this document itself is ready to freeze.)*

This artifact may transition to Frozen only if:
- [ ] Formal Review Passed
- [ ] Dependency Validation Passed
- [ ] Boundary Validation Passed
- [ ] Manifest Alignment Verified
- [ ] Principle Alignment Verified
- [ ] Workflow Alignment Verified
- [ ] Document Standards Alignment Verified
- [ ] Artifact Standards Alignment Verified
- [ ] Review Standards Alignment Verified
- [ ] Validation Standards Alignment Verified
- [ ] Quality Gate Alignment Verified
- [ ] Governance Alignment Verified
- [ ] AI Standards Alignment Verified
- [ ] Contract completeness verified
- [ ] Template compliance verified
- [ ] No duplicated responsibility
- [ ] No dependency cycle
- [ ] Executive Approval Granted
