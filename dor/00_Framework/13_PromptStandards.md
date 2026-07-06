---
Title: 13_PromptStandards
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
Artifact ID: ART-013
Depends On: 03_FrameworkWorkflow.md, 04_DocumentStandards.md, 05_ArtifactStandards.md, 06_ReviewStandards.md, 07_ValidationStandards.md, 08_QualityGates.md, 09_Governance.md, 10_AIStandards.md, 11_MetadataStandards.md, 12_NamingStandards.md
Previous Artifact: 12_NamingStandards.md
Decision IDs: N/A
Related Decisions: N/A
Related Risks: N/A
Reference Documents: N/A
Next Artifact: 14_TemplateStandards.md
---

# Enterprise Prompt Standards

## 1. Executive Statement
This document establishes the definitive enterprise meta-standard governing Prompt Architecture within the Enterprise Product Discovery Framework. Prompts are not ad-hoc chat inputs; they are first-class architectural assets. This standard guarantees that every prompt is structured, versioned, governed, validated, composable, deterministic, and AI-executable, enabling scalable execution across thousands of autonomous agents and LLM providers.

## 2. Scope & Ownership Boundaries
To maintain rigorous enterprise Separation of Concerns, this artifact strictly enforces the following ownership model:
- **`10_AIStandards.md`**: Owns AI Agent behavior, execution, invariants, and capabilities.
- **`11_MetadataStandards.md`**: Owns the schemas and data contracts output by the LLM.
- **`12_NamingStandards.md`**: Owns how prompt files and prompt IDs are named.
- **This Document (`13_PromptStandards.md`)**: Owns **Prompt Architecture, Templates, Versioning, Composition, Execution Context, and Lifecycle**.

**Crucial Invariant:** This standard defines *how* prompts are structured and managed. It NEVER defines AI behavior, validation logic, review methodology, or workflow states.

## 3. Prompt Principles
Every prompt engineered within this framework MUST adhere to the following principles:
- **Single Responsibility**: A prompt must execute exactly one logical task (e.g., Review, Validate, Summarize).
- **Deterministic**: The phrasing must minimize probabilistic variance and enforce strict output contracts.
- **Composable**: Prompts must be modular, allowing smaller prompts to be combined into complex orchestrations.
- **Reusable**: Prompts must rely on injected variables, not hardcoded context.
- **Portable & Vendor Neutral**: Prompts must not rely on proprietary model features (e.g., OpenAI functions) unless abstracted.
- **Versioned**: Every prompt iteration must be uniquely versioned.
- **Context Efficient**: Prompts must minimize token waste and explicitly manage context windows.
- **Testable**: Prompts must be verifiable via deterministic CI/CD regression tests.
- **Governable**: Prompt changes must undergo formal review.

## 4. Prompt Taxonomy
Prompts are classified into the following canonical categories:
- **System Prompt**: Defines the persona, bounds, and absolute invariants of the agent.
- **Execution Prompt**: Triggers a specific action (e.g., Draft, Transform, Analyze).
- **Review Prompt**: Instructs the agent to evaluate an artifact against `06_ReviewStandards`.
- **Validation Prompt**: Instructs the agent to perform deterministic structural checks.
- **Governance Prompt**: Instructs the agent to evaluate waivers or compliance exceptions.
- **Planning Prompt**: Decomposes epics into graphs and tasks.
- **Agent Prompt**: The dynamic orchestration prompt used by a multi-agent swarm.
- **Shared Prompt**: Reusable snippets (e.g., standard XML output formatting instructions).
- **Template Prompt**: A parameterized skeleton awaiting context injection.

## 5. Prompt Capability Model
Orthogonal to its taxonomy category, every prompt is classified by its explicit operational capability:
- **Generation**: Creating net-new content from context.
- **Analysis**: Evaluating context to extract metrics or insights.
- **Classification**: Categorizing inputs against predefined taxonomies.
- **Extraction**: Pulling structured data from unstructured text.
- **Planning**: Breaking complex objectives into execution graphs.
- **Reasoning**: Performing logical deductions (e.g., resolving conflicts).
- **Transformation**: Converting data from one schema/format to another.
- **Validation**: Enforcing deterministic structural rules.
- **Review**: Enforcing qualitative human-equivalent standards.
- **Conversation**: Engaging in back-and-forth context refinement.

## 6. Prompt Standard Contract
To prevent unmaintainable prompt sprawl, the framework employs a "Standard of Prompts" model.
- **The Contract**: This document establishes the universal `Prompt Standard Contract`.
- **The Template**: Every explicit Prompt Asset deployed in the enterprise MUST implement the `Prompt Standard Contract Template`.

## 7. Prompt Standard Contract Template
Every formally recognized Prompt Asset MUST declare the following structural skeleton (stored as YAML frontmatter or sidecar metadata):
1. **Prompt Purpose**: The exact objective of the prompt.
2. **Prompt Category**: The classification (from Section 4).
3. **Prompt Capability**: The explicit operational capability (from Section 5).
4. **Expected Inputs**: The required variables (e.g., `{{ARTIFACT_CONTENT}}`, `{{REVIEW_STANDARDS}}`).
5. **Expected Outputs**: The strictly typed schema the prompt must yield (referencing `11_MetadataStandards`).
6. **Execution Context**: The maximum token length or specific RAG requirements.
7. **Dependencies**: Other shared prompts or documents this prompt requires.
8. **Constraints**: Absolute limitations (e.g., "Do not generate markdown, only JSON").
9. **Preconditions**: States that must be true before execution.
10. **Postconditions**: Guaranteed states after execution.
11. **Failure Behaviour**: Instructions for the LLM when it lacks sufficient context.
12. **Acceptance Criteria**: The conditions under which the prompt is considered successful.

## 8. Prompt Invariants
The following rules are immutable:
- Every Prompt MUST have exactly one purpose.
- Prompts MUST be deterministic; they must instruct the model to fail cleanly rather than hallucinate.
- Prompts MUST NOT depend on hidden or out-of-band context.
- Prompts MUST NOT mutate framework rules, principles, or governance models.
- Prompts MUST explicitly declare their required context variables.
- Prompts MUST explicitly declare expected outputs.

## 9. Prompt Composition Model
Enterprise prompts are built hierarchically:
- **Atomic Prompt**: A single, indivisible instruction (e.g., "Format output as JSON").
- **Composable Prompt**: A module formed by combining Atomic Prompts.
- **Workflow Prompt**: An execution-ready prompt mapped to a specific workflow phase.
- **Orchestrated Prompt**: A dynamic prompt generated at runtime by a Planning Agent.
- **Agent Prompt**: The complete synthesized payload (System + Context + Execution) sent to the LLM.

## 10. Prompt Execution Modes
Enterprise AI systems require prompts to support diverse runtime modes. Every prompt MUST declare compatibility with:
- **Interactive**: Real-time back-and-forth execution with human latency thresholds.
- **Batch**: Processing thousands of offline artifacts asynchronously.
- **Pipeline**: Automated execution as a step within CI/CD (e.g., Pre-Commit Validation).
- **Event Driven**: Triggered automatically via Webhooks (e.g., PR opened).
- **Scheduled**: Executing via cron for continuous monitoring.
- **Autonomous**: Looping execution without human oversight.
- **Swarm**: Highly parallelized multi-agent execution.
- **Human in Loop (HITL)**: Halting for cryptographic human sign-off before committing output.

## 11. Prompt Lifecycle
Prompt Assets transition through formalized states mimicking standard framework execution:
- **Draft**: Engineering and initial testing.
- **Validated**: Passes automated deterministic tests and token constraints.
- **Reviewed**: Passes qualitative evaluation by human prompt engineers.
- **Approved**: Semantically locked.
- **Released**: Actively deployed to the Prompt Registry for production CI/CD consumption.
- **Deprecated**: Slated for removal, retaining backward compatibility.
- **Retired**: Permanently removed from execution pipelines.

## 12. Prompt Versioning
Prompts MUST adhere to Semantic Versioning (`v[MAJOR].[MINOR].[PATCH]`):
- **Major**: Output schema changed, variables added/removed, or core behavior altered.
- **Minor**: Non-breaking refinements (e.g., improved few-shot examples).
- **Patch**: Typo fixes or minor instruction tweaks.
- **Compatibility**: The framework must track which models (e.g., GPT-4, Claude-3.5) have been verified for which prompt version.

## 13. Prompt Context Model
Context must be explicitly segregated within the prompt payload to prevent prompt injection and hallucination:
- **System Context**: The immutable rules of engagement.
- **Framework Context**: Injected standards (e.g., Quality Gates).
- **Artifact Context**: The specific data being processed.
- **Domain Context**: RAG-retrieved enterprise knowledge.
- **Execution Context**: CI/CD variables (Timestamps, IDs).
- **Temporary Context**: Scratchpad memory for the LLM's chain-of-thought (which must NOT be in the final output).

## 14. Prompt Dependency Graph
Prompts are not isolated texts; they form an explicitly declared execution graph.
- **Dependency Chaining**: `Base Prompt` -> `Review Prompt` -> `Architecture Review Prompt` -> `Security Review Prompt`.
- **Relationship Edges**:
  - **Consumes**: Ingests an artifact.
  - **Produces**: Yields a metadata schema.
  - **Requires**: Needs a specific variable.
  - **Extends**: Inherits and modifies a parent prompt.
  - **Composes**: Embeds a child prompt.

## 15. Prompt Packaging & Registry
To manage scale and discovery, prompts are strictly packaged and registered:
- **Prompt Registry**: The API-addressable central index governing discovery and access.
  - **Registry ID**: Globally unique identifier for registry tracking.
  - **Registry Metadata**: Traceability and lifecycle tracking.
  - **Registry Discovery**: Queryable index of prompt capabilities.
- **Packaging Hierarchy**:
  - `Prompt Bundle`: A zipped collection of related modules (e.g., `Security AI Swarm Bundle`).
  - `Prompt Module`: A directory containing the template, metadata, and test assertions.
  - `Prompt Asset`: The specific `.prompt` file.
  - `Prompt Version`: The immutable historical snapshot of the asset.

## 16. Prompt Execution Contract
Every prompt execution MUST abide by:
- **Input Contract**: The exact variables injected into the template.
- **Output Contract**: The schema the LLM is expected to return.
- **Error Contract**: The exact JSON structure returned when the LLM identifies `Insufficient Context`.
- **Retry Contract**: Defines whether the prompt is idempotent and safe for automatic CI/CD retries.
- **Timeout Contract**: The maximum acceptable latency for the LLM response.

## 17. Prompt Optimization Principles
- **Context Window Efficiency**: Prompts must inject only the specific sections of standards needed, not entire documents.
- **Token Optimization**: Instructions must be concise and avoid conversational filler.
- **Chunking**: Artifacts exceeding context limits MUST be chunked prior to prompt injection.
- **Memory Usage**: Few-shot examples must be representative but minimal.

## 18. Prompt Traceability
Every AI output MUST trace back to its prompt via:
- **Prompt ID**: The `12_NamingStandards` compliant identifier.
- **Execution ID**: The specific runtime hash.
- **Version**: The SemVer string of the prompt.
- **Model Signature**: The exact LLM version used.
- **Timestamp**: Execution time.

## 19. Prompt Metadata Compatibility
All prompt metadata MUST comply entirely with the JSON/YAML requirements defined in `11_MetadataStandards.md`.

## 20. Prompt Naming Compatibility
All Prompt IDs, variables, and files MUST comply entirely with the rules defined in `12_NamingStandards.md` (e.g., `PRMT-REV-001`).

## 21. AI Compatibility
This standard guarantees prompts are:
- **LLM Neutral**: Utilizing universal instructional techniques (e.g., Markdown/XML delimiters) instead of proprietary APIs.
- **Model Independent**: Prompts define the *intent*; wrappers handle model-specific API mappings.
- **Machine Readable**: Prompt definitions are stored as text with structured metadata headers.
- **Deterministic**: Designed to minimize LLM stochasticity.

## 22. Extension Mechanism
- Sub-organizations may define custom Domain Prompts.
- These extensions MUST implement the Prompt Standard Contract.
- Extensions MUST NOT alter the System Context or Governance invariants.

## 23. Success Criteria
This artifact is successful when:
- 100% of enterprise AI executions use versioned, tracked Prompt Assets.
- 0 prompts contain hardcoded business data.
- 100% of prompts declare their Expected Outputs mapping to `11_MetadataStandards`.
- Prompts can be hot-swapped between different LLM providers without breaking CI/CD pipelines.

## 24. Prompt Compliance Matrix
To enable automated governance, Prompt Standards must adhere to this invariant matrix:

| Contract Element | Mandatory | Source |
| :--- | :--- | :--- |
| Prompt Purpose | Yes | Prompt Standard Contract |
| Expected Inputs | Yes | Prompt Standard Contract |
| Expected Outputs | Yes | Prompt Standard Contract |
| Failure Behaviour | Yes | Prompt Standard Contract |
| Explicit Context | Yes | Prompt Invariants |
| Determinism | Yes | Prompt Invariants |
| Single Responsibility| Yes | Prompt Invariants |
| Vendor Neutrality | Yes | AI Compatibility |

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
- [x] Review Standards Alignment Verified
- [x] Validation Standards Alignment Verified
- [x] Quality Gate Alignment Verified
- [x] Governance Alignment Verified
- [x] AI Standards Alignment Verified
- [x] Metadata Standards Alignment Verified
- [x] Naming Standards Alignment Verified
- [x] Contract completeness verified
- [x] Template compliance verified
- [x] No duplicated responsibility
- [x] No dependency cycle
- [x] Executive Approval Granted
