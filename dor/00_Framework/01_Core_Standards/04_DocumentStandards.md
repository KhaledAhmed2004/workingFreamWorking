---
Title: 04_DocumentStandards
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
Artifact ID: ART-004
Depends On: 01_FrameworkManifest.md, 02_FrameworkPrinciples.md, 03_FrameworkWorkflow.md
Previous Artifact: 03_FrameworkWorkflow.md
Decision IDs: N/A
Related Decisions: N/A
Related Risks: N/A
Reference Documents: N/A
Next Artifact: 05_ArtifactStandards.md
---

# Enterprise Document Standards

This document establishes the mandatory structural and formatting requirements for all artifacts within the Enterprise Product Discovery Framework. It ensures cross-document consistency, simplifies automation, and maintains a governance-grade professional tone.

## 1. Document Metadata Standard
Every official framework artifact MUST begin with a standardized YAML frontmatter block. This block acts as the system-readable state for the document.

### Canonical Metadata Schema
To ensure enterprise automation reliability and prevent diff noise, the canonical metadata schema for Core Framework artifacts consists of the following 23 fields. Governance artifacts determine which fields are mandatory for each lifecycle state. Supporting Documentation shall conform to the metadata profile defined for Supporting Documentation in Section 2:

**Core Identity & State Fields**
1. `Title`: The exact file name without the `.md` extension.
2. `Artifact Version`: Semantic version of the specific document (e.g., `1.0`).
3. `Framework Version`: The version of the overarching framework this complies with.
4. `Supersedes`: The ID or name of the document this replaces, or `N/A`.
5. `Status`: Must be exactly one of: `Draft`, `In Review`, `Frozen`, `Archived`.
6. `Phase`: The framework phase the artifact belongs to.
7. `Sprint`: Current sprint identifier, or `N/A`.

**Ownership & Authority Fields**
8. `Owner`: The responsible role or group.
9. `Reviewer`: The review board or role.
10. `Approver`: The final sign-off authority.
*(Note: Governance artifacts may extend these into specialized roles such as Security Reviewer or Compliance Approver.)*

**Temporal & Governance Fields**
11. `Created`: ISO-8601 format (`YYYY-MM-DD`).
12. `Updated`: ISO-8601 format (`YYYY-MM-DD`).
13. `Approval Date`: ISO-8601 format (`YYYY-MM-DD`), or `N/A`.
14. `Last Reviewed`: ISO-8601 format (`YYYY-MM-DD`), or `N/A`.
15. `Review Status`: Current standing of the review, or `N/A`.
16. `Artifact ID`: The unique identifier (e.g., `ART-004`).

**Relationship & Traceability Fields**
17. `Depends On`: Comma-separated list of requisite artifacts, or `N/A`.
18. `Previous Artifact`: The immediate upstream artifact in the workflow sequence, or `N/A`.
19. `Decision IDs`: Comma-separated list of architectural decisions, or `N/A`.
20. `Related Decisions`: Links to relevant decisions, or `N/A`.
21. `Related Risks`: Links to identified risks, or `N/A`.
22. `Reference Documents`: Links to supporting documents, or `N/A`.
23. `Next Artifact`: The next logical artifact in the workflow sequence, or `N/A`.

### Metadata Rules
- **Formatting**: Keys must use Title Case (e.g., `Artifact Version`). Must be separated by a colon and a single space.
- **Ordering**: Metadata Ordering is normative. Metadata fields SHALL NOT be reordered. Automation may assume canonical ordering.
- **Empty Values**: If a field does not apply, it MUST be explicitly set to `N/A`. Do not leave fields blank.
- **Date Format**: All dates MUST use ISO-8601 (`YYYY-MM-DD`).

## 2. Document Classification Standard
Documents are classified into three primary tiers, which dictate their lifecycle and mandatory metadata:

### Core Framework
- **Criteria**: Defines the fundamental rules, standard operating procedures, and architectural constraints.
- **Typical Owner**: Architecture Review Board / Enterprise Architect.
- **Canonical Metadata Profile**: Full Metadata Schema

### Product Artifacts
- **Criteria**: Execution deliverables created during the product lifecycle (e.g., Vision, Strategy, PRD).
- **Typical Owner**: Product Managers / Feature Leads.
- **Canonical Metadata Profile**: Full Metadata Schema

### Supporting Documentation
- **Criteria**: Appendices, diagrams, meeting notes, and logs (e.g., Changelog).
- **Typical Owner**: Varied.
- **Canonical Metadata Profile**: Abbreviated Schema (Title, Created, Updated, Owner).

## 3. Document Naming Standard
The document title (H1) MUST be clear, professional, and unambiguously represent the document's purpose.
- Format: `# [Subject] [Type]` (e.g., `# Enterprise Document Standards`).
- Must not contain version numbers in the H1 (versioning is handled in metadata).

## 4. Directory Structure Conventions
To ensure long-term scalability and prevent repository sprawl, directory structures must be standardized.
- This artifact defines documentation directory naming conventions.
- Repository topology is defined by Repository Standards.

## 5. File Naming Convention
File names must be machine-readable, predictably ordered, and correspond directly to the Title metadata.
- Format: `[SequenceNumber]_[PascalCaseName].md` (e.g., `04_DocumentStandards.md`).
- Sequence numbers must be zero-padded to two digits (e.g., `01`, `02`).

## 6. Artifact Naming Convention
When referencing an artifact in prose, it must be referred to by its exact file name or a formalized title.
- Do not use colloquial names (e.g., "The Doc Standards").
- Always format the filename as inline code (e.g., `04_DocumentStandards.md`) when used in text.

## 7. Heading Hierarchy Standard
Documents must follow a strict heading hierarchy to ensure readability and parsability:
- **Only One H1**: `#` Used exactly once at the top of the document for the title.
- **H2 Numbering**: `##` Used for major sections. These MUST be numbered sequentially (e.g., `## 1. Introduction`).
- **Consistency**: Do not skip heading levels (e.g., do not jump from H2 to H4).
- **No Empty Headings**: Every heading must have accompanying content or explicit placeholder text.
- **No Orphan Headings**: A heading must not be left dangling at the bottom of a block without content.

## 8. Section Ordering Standard
Information must flow logically:
1. Universal Required Sections (Context & Scope).
2. Core Content (The primary payload).
3. Closing Metadata (e.g., Risk Assessment, Exit Criteria, Open Questions).

## 9. Structural Integrity Rules
Measurable structural standards that must be met for validation:
- **Mandatory Sections**: All universal required sections must be present.
- **No Missing Metadata**: All required metadata keys must exist.
- **Consistent Ordering**: Sections must follow the logical flow.
- **No Duplicated Headings**: Identical heading names at the same level are prohibited.

## 10. Universal Required Sections
Regardless of classification, all official Core Framework and Product Artifacts MUST contain the following structural elements in order:
1. **Metadata Block**: YAML frontmatter.
2. **Title**: The single H1.
3. **Executive Statement**: A brief, high-level summary of the document's purpose.
4. **Scope / Objectives**: What the document covers.
5. **Ownership**: Explicit declaration of the owning role.
6. **Dependencies**: Upstream and downstream links.
7. **Document Non-Goals**: Explicit statement of what the document does NOT cover.

*(Note: Domain-specific sections are governed by `05_ArtifactStandards.md`.)*

## 11. Universal Optional Sections
Depending on the artifact's domain or complexity, the following structural sections may be included:
- Risk Assessment
- Open Questions
- Success Criteria
- Exit Criteria

## 12. Markdown Rules
All documents MUST strictly adhere to standard GitHub Flavored Markdown (GFM).
- **Whitespace / Blank Lines**: Maintain exactly one blank line before and after headings, lists, tables, and code blocks.
- **Emphasis**: Use `**bold**` for critical terms and `*italics*` for nuanced emphasis. Do not over-format.
- **Inline Code**: Use backticks (`` ` ``) for file names, identifiers, and inline commands.
- **Images**: Must use absolute or relative paths with descriptive alt text (`![Alt Text](./path/to/image.png)`).
- **Links**: Must use descriptive link text. Do not use raw URLs in body text.
- **Footnotes**: Use standard syntax (`[^1]`) if referencing external sources or deep technical caveats.
- **Task Lists**: Use `- [ ]` and `- [x]` for actionable checklists (e.g., Exit Criteria).
- **Horizontal Rules**: Use `---` sparingly to separate major conceptual boundaries, surrounded by empty lines.

## 13. Lists
- **Unordered Lists**: Use hyphens (`-`) consistently. Do not mix hyphens and asterisks.
- **Ordered Lists**: Use numbers (`1.`, `2.`) for sequential steps or ranked priorities.

## 14. Tables
Use tables to present structured, comparative, or matrix data.
- Headers must be bolded.
- Column alignment should be explicitly defined (e.g., `:---`, `:---:`, `---:`).
- Avoid overly complex tables that break horizontally; use lists if data exceeds 4 columns.

## 15. Callouts
Use standard blockquotes (`>`) to emphasize critical rules, warnings, or executive summaries.
- Keep callouts brief and impactful.
- Avoid using third-party HTML admonitions unless they are officially supported by the enterprise rendering engine.

## 16. Code Blocks
- Use fenced code blocks (\`\`\`) for all code, JSON, YAML, or command-line examples.
- Always specify the language identifier for syntax highlighting (e.g., \`\`\`yaml).

## 17. Cross References
- **Canonical Rule**: When linking to another framework document, you MUST use relative Markdown links with the exact filename as the link text.
- **Format**: `[`05_ArtifactStandards.md`](./05_ArtifactStandards.md)` (if in the same directory) or `[`05_ArtifactStandards.md`](../05_ArtifactStandards.md)` (if in a parent directory). Do not use ambiguous natural language links (e.g., "click here" or "see the standards").

## 18. Ownership Metadata Standard
- The `Owner` metadata field must represent a role or group (e.g., `Architecture Review Board`, `Product Manager`), not an individual person's name, to ensure long-term maintainability.

## 19. Document Non-Goals
This standard explicitly does NOT define:
- Domain-specific artifact structures (e.g., Vision, PRD), which are owned by `05_ArtifactStandards.md`.
- Workflow rules, quality gates, version policy, or revision policy (which are deferred to dedicated Governance and Version Policy artifacts).

## 20. Success Criteria
The artifact will be considered successful when:
- Every framework document follows one consistent structure.
- Metadata requirements and field ordering are perfectly standardized.
- Heading hierarchy is standardized.
- Markdown usage is standardized.
- Naming conventions are standardized.
- Structural rules are independent of review rules.
- No governance logic exists within this document.

## 21. Exit Criteria
This artifact may be frozen only if:
- [x] Formal Review Passed
- [x] Dependency Validation Passed
- [x] Boundary Validation Passed
- [x] Manifest Alignment Verified
- [x] Principle Alignment Verified
- [x] Workflow Alignment Verified
- [x] No Scope Leakage Detected
- [x] Executive Approval Granted
