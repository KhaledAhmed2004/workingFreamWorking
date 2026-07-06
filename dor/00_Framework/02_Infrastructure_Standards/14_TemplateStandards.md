---
Title: 14_TemplateStandards
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
Artifact ID: ART-014
Depends On: 03_FrameworkWorkflow.md, 04_DocumentStandards.md, 05_ArtifactStandards.md, 06_ReviewStandards.md, 07_ValidationStandards.md, 08_QualityGates.md, 09_Governance.md, 10_AIStandards.md, 11_MetadataStandards.md, 12_NamingStandards.md, 13_PromptStandards.md
Previous Artifact: 13_PromptStandards.md
Decision IDs: N/A
Related Decisions: N/A
Related Risks: N/A
Reference Documents: N/A
Next Artifact: 15_TraceabilityStandards.md
---

# Enterprise Template Standards

## 1. Executive Statement
This document establishes the definitive enterprise meta-standard governing Template Architecture within the Enterprise Product Discovery Framework. Templates are first-class enterprise assets. They are reusable, parameter-driven structural blueprints used to instantiate artifacts, configure AI models, and scaffold pipelines. This standard guarantees that every template within the framework ensures consistency, prevents structural drift, supports automated machine expansion, and seamlessly integrates with autonomous AI agents.

## 2. Scope & Ownership Boundaries
To maintain rigorous enterprise Separation of Concerns, this artifact strictly enforces the following ownership model:
- **`05_ArtifactStandards.md`**: Owns the structural requirements of the *instantiated artifact* (the output).
- **`11_MetadataStandards.md`**: Owns the schemas and data contracts.
- **`12_NamingStandards.md`**: Owns how template files and variables are named.
- **`13_PromptStandards.md`**: Owns the architecture of LLM prompts.
- **This Document (`14_TemplateStandards.md`)**: Owns **Template Architecture, Variables, Logic, Composition, Inheritance, and Expansion Execution**.

**Crucial Invariant:** This standard governs *how* templates are designed and expanded. It NEVER dictates the business content of the template, nor does it redefine validation logic, review methodology, or workflow states.

## 3. Template Principles
Every template engineered within this framework MUST adhere to the following principles:
- **Single Responsibility**: A template must generate exactly one cohesive structural outcome.
- **Reusability**: Templates must abstract away project-specific hardcoding in favor of dynamic variables.
- **Parameterization**: Everything dynamic must be explicitly declared as an injectable parameter.
- **Separation of Content and Structure**: The template dictates layout, headers, and metadata bindings; the user (or AI) provides the content.
- **Deterministic Expansion**: Given the same variable payload, a template must always expand into the exact same structural output.
- **Composability**: Large templates must be assembled by combining smaller atomic templates.
- **AI Readiness**: Templates must be natively parseable and populated by LLMs without regex guesswork.
- **Maintainability**: Templates must be versioned, testable, and independently upgradable.

## 4. Template Taxonomy
Templates are classified into the following canonical categories:
- **Document Template**: Blueprints for markdown files (e.g., Vision Document, PRD).
- **Artifact Template**: Blueprints for executable system components.
- **Prompt Template**: The structural skeleton of an AI instruction (managed structurally here, execution managed by `13`).
- **Metadata Template**: Blueprints for JSON/YAML schemas (e.g., standard review record).
- **YAML Template**: Blueprints for CI/CD pipeline definitions.
- **Checklist Template**: Blueprints for human-in-the-loop task lists.
- **Decision Template**: Blueprints for architectural decision records (ADRs).
- **Report Template**: Blueprints for aggregated analysis outputs.
- **Configuration Template**: Blueprints for environment-specific variables.

## 5. Template Capability Model
Orthogonal to its taxonomy category, every template is classified by its operational capability:
- **Generate**: Create a net-new file or structure.
- **Scaffold**: Build a directory tree with placeholder artifacts.
- **Transform**: Reformat existing content into a new layout.
- **Compose**: Assemble multiple disparate inputs into a unified document.
- **Extend**: Inject new sections into a previously instantiated baseline.
- **Validate**: Provide the structural regex for deterministic checking.
- **Populate**: Fill variable slots with external API data.
- **Normalize**: Standardize varying inputs into a canonical enterprise layout.

## 6. Template Standard Contract
To prevent fragmented boilerplate sprawl, the framework employs a "Standard of Templates" model.
- **The Contract**: This document establishes the universal `Template Standard Contract`.
- **The Template**: Every explicit Template Asset deployed in the enterprise MUST implement the `Template Standard Contract Template`.

## 7. Template Standard Contract Template
Every formally recognized Template Asset MUST declare the following structural skeleton (stored as YAML frontmatter or sidecar metadata):
1. **Template Purpose**: The exact objective of the template blueprint.
2. **Template Category**: The taxonomy classification (from Section 4).
3. **Template Capability**: The explicit operational capability (from Section 5).
4. **Required Variables**: Keys that MUST be provided for successful expansion.
5. **Default Values**: Hardcoded fallbacks if optional variables are omitted.
6. **Optional Variables**: Keys that enhance the structure but are not strictly required.
7. **Constraints**: Absolute limitations (e.g., "Cannot exceed 3000 tokens").
8. **Preconditions**: States that must be true before instantiation.
9. **Postconditions**: Guaranteed structural states of the output artifact.
10. **Expected Output**: The `11_MetadataStandards` schema of the resulting artifact.
11. **Dependencies**: Base templates this template extends.
12. **Extension Points**: Explicit locations where custom blocks can be injected.
13. **Acceptance Criteria**: The conditions under which the template is considered valid.

## 8. Template Invariants
The following rules are immutable:
- Every Template MUST be strictly deterministic.
- Every Template MUST explicitly declare all injectable variables.
- Every Template MUST support semantic versioning.
- Every Template MUST explicitly declare its output artifact type.
- Every Template MUST explicitly declare its required inputs.
- Every Template MUST NOT contain embedded, highly-coupled business content.
- Every Template MUST remain modular and reusable across the enterprise.

## 9. Template Variable & Logic Model
Templates parameterize state via explicit variables and control structures:
- **Variable Types**:
  - **Required Variables**: Must be provided by the invoker (e.g., `{{PROJECT_NAME}}`).
  - **Optional Variables**: Can be omitted without breaking expansion.
  - **Computed Variables**: Derived at runtime (e.g., `{{CURRENT_UTC_TIMESTAMP}}`).
  - **Inherited Variables**: Passed down from a parent Base Template.
  - **Runtime Variables**: Injected by the CI/CD pipeline (e.g., `{{EXECUTION_ID}}`).
  - **Environment Variables**: Injected by the deployment target (e.g., `{{STAGING_URL}}`).
- **Conditional Logic**: Enterprise template engines MUST support non-Turing-complete logic:
  - **IF / ELSE**: Conditional rendering based on boolean or null-check variables.
  - **SWITCH**: Value-based multi-branch execution.
  - **LOOP**: Array iteration for dynamic lists (e.g., iterating through multiple API endpoints).
  - **OPTIONAL SECTION**: Blocks that only render if an associated object is populated.

## 10. Template Composition Model
Enterprise templates are built hierarchically to maximize reuse, following the instance generation pattern:
- **Atomic Template**: A single, indivisible structural block (e.g., a standard `Metadata Header`).
- **Composable Template**: A modular template formed by combining Atomic blocks.
- **Module Template**: A collection of composable templates focused on a single domain.
- **Bundle Template**: A massive scaffold combining multiple Modules (e.g., a `New Product Blueprint`).
- **Template Instance**: The intermediate in-memory expansion state before file generation (`Vision Template` -> `Vision Instance` -> `Vision.md`).

## 11. Template Engine Compatibility
Templates MUST NOT be tightly coupled to proprietary string-replace scripts. They must be compatible with standard, vendor-neutral enterprise templating engines, explicitly declaring support for formats such as:
- Mustache
- Handlebars
- Jinja2
- Liquid
- Go Templates
- Nunjucks

## 12. Template Inheritance Model
To minimize duplication, templates utilize a strict inheritance hierarchy:
- **Base Template**: The root blueprint containing enterprise-wide requirements.
- **Derived Template**: Inherits the Base Template and adds domain-specific blocks.
- **Extension Template**: Ad-hoc additions injected into a Base Template's explicit `Extension Points`.
- **Override Rules**: A Derived Template may selectively overwrite a Base Template's optional blocks.
- **Merge Rules**: Arrays of constraints are concatenated; singular values are overwritten.
- **Conflict Resolution**: In the event of a variable collision, the most explicitly derived template wins.

## 13. Template Packaging & Registry
To manage scale, discoverability, and deployment, templates are strictly packaged:
- **Template Registry**: The API-addressable central index governing discovery and access.
  - **Registry ID**: Globally unique identifier mapping to `12_NamingStandards`.
  - **Registry Metadata**: Traceability and lifecycle tracking.
  - **Registry Discovery**: Queryable index of template capabilities and version compatibility.
- **Packaging Hierarchy**:
  - `Template Package`: A zipped collection of related modules (e.g., `Security Compliance Package`).
  - `Template Module`: A directory containing the template, its metadata contract, and its test assertions.
  - `Template Asset`: The specific `.template` file containing the blueprint.
  - `Template Version`: The immutable historical snapshot of the asset.

## 14. Template Lifecycle
Template Assets transition through formalized states mimicking standard framework execution:
- **Draft**: Engineering and local testing.
- **Validated**: Passes automated deterministic tests and variable resolution checks.
- **Reviewed**: Passes qualitative evaluation by Architecture Review Board.
- **Approved**: Semantically locked and merged into the main branch.
- **Released**: Actively deployed to the Template Registry for production CI/CD consumption.
- **Deprecated**: Slated for removal, retaining backward compatibility for active sprints.
- **Retired**: Permanently removed from instantiation pipelines.

## 15. Template Testing & Validation
Enterprise templates require rigorous testing before Release:
- **Golden File Test**: Asserts that a specific variable payload consistently yields a byte-for-byte exact known output file.
- **Expansion Test**: Validates that all conditional logic (IF/LOOP) expands without engine crashes.
- **Snapshot Test**: Verifies visual layout stability.
- **Variable Resolution Test**: Ensures all Required and Optional variables are mapped correctly.
- **Regression Test**: Guarantees legacy variable payloads continue to expand successfully in new template versions.

## 16. Template Versioning
Templates MUST adhere to Semantic Versioning (`v[MAJOR].[MINOR].[PATCH]`):
- **Major**: Required variables added, output schema changed, or breaking structural changes.
- **Minor**: Non-breaking additions (e.g., new optional variables or extension points).
- **Patch**: Typo fixes or minor formatting tweaks.
- **Compatibility**: The framework tracks which CI/CD engines and AI Agents are certified for which template version.

## 17. Template Dependency Graph
Templates form an explicitly declared execution graph mapping their interactions.
- **Relationship Edges**:
  - **Consumes**: Ingests an existing artifact to generate a derived structure.
  - **Produces**: Yields a specific instantiated artifact type.
  - **Requires**: Needs a specific template or variable module.
  - **Extends**: Inherits and modifies a parent template.
  - **Implements**: Fulfills a standard structural contract.
  - **Composes**: Embeds a child template.
  - **References**: Links to standard documentation.
  - **Supersedes**: Replaces a deprecated template.

## 18. Template Execution Contract
Every template expansion MUST abide by:
- **Input Contract**: The exact payload of variables injected.
- **Expansion Contract**: The deterministic rules engine resolving conditionals and loops.
- **Output Contract**: The schema and layout the template is expected to return.
- **Error Contract**: The precise failure states triggered when required variables are missing.
- **Validation Contract**: The post-expansion structural checks ensuring the generated output is compliant.

## 19. Template Performance & Optimization
For frameworks handling thousands of concurrent scaffolding operations, template engines must strictly monitor:
- **Expansion Time**: Millisecond latency limits per instantiation.
- **Expansion Memory**: Ceiling limits on memory buffers for massive document compilations.
- **Expansion Complexity**: Constraints on deep nesting in conditional statements.
- **Recursive Depth**: Protection against infinite recursion loops (e.g., Template A embedding Template B embedding Template A).

## 20. AI Compatibility
Templates MUST natively support autonomous integration:
- **LLM Readiness**: LLMs must be able to inject JSON payloads into template expansion engines seamlessly.
- **CI/CD Execution**: Templates must be expandable via headless pipeline scripts without human GUI interaction.
- **Agent Swarms**: Orchestrator agents must be able to request standard templates from the Registry dynamically.
- **Structured Outputs**: AI-generated templates must adhere strictly to `11_MetadataStandards`.

## 21. Success Criteria
This artifact is successful when:
- 100% of newly created framework artifacts are instantiated from a version-controlled Template.
- 0 templates contain hardcoded business data or logic that should be passed as variables.
- 100% of Template definitions explicitly declare their Expected Outputs mapping to `05_ArtifactStandards`.
- AI agents can successfully discover, parse, and populate templates via the Registry.

## 22. Template Compliance Matrix
To enable automated governance, Template Standards must adhere to this invariant matrix:

| Contract Element | Mandatory | Source |
| :--- | :--- | :--- |
| Template Purpose | Yes | Template Standard Contract |
| Required Variables | Yes | Template Standard Contract |
| Expected Output | Yes | Template Standard Contract |
| Extension Points | Yes | Template Standard Contract |
| Determinism | Yes | Template Invariants |
| Single Responsibility| Yes | Template Invariants |
| Strict Isolation | Yes | Template Invariants |
| Vendor Neutrality | Yes | AI Compatibility |

## 23. Exit Criteria
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
- [x] Naming Standards Alignment Verified
- [x] Prompt Standards Alignment Verified
- [x] Contract completeness verified
- [x] Template compliance verified
- [x] No duplicated responsibility
- [x] No dependency cycle
- [x] Executive Approval Granted
