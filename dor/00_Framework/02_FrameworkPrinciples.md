---
Title: 02_FrameworkPrinciples
Version: 1.0
Artifact Version: 1.0
Framework Version: 1.0
Supersedes: N/A
Status: Frozen
Phase: Framework Core
Sprint: N/A
Owner: Enterprise Product Governance Board
Reviewer: Architecture Review Board
Approver: Executive Board
Created: 2026-07-06
Updated: 2026-07-06
Approval Date: N/A
Last Reviewed: N/A
Review Status: N/A
Artifact ID: ART-002
Depends On: 01_FrameworkManifest.md
Previous Artifact: 01_FrameworkManifest.md
Decision IDs: DEC-002
Principle IDs: PRN-001 - PRN-010
Related Decisions: N/A
Related Risks: N/A
Reference Documents: N/A
Next Artifact: 03_FrameworkWorkflow.md
---

# Enterprise Framework Principles

## Executive Statement
Methodologies fail not from a lack of rules, but from a lack of philosophical alignment. When a product team faces intense pressure to deliver rapidly, written rules are often discarded as bureaucratic overhead. 

The purpose of this document is to establish the non-negotiable mental models and philosophies that govern the Enterprise Product Discovery Framework. These principles exist to eliminate directional ambiguity. When a conflict arises between speed and strategy, or between assumption and evidence, these principles dictate the resolution.

## Principle Applicability

These principles **apply to**:
- Product Discovery
- Framework Documents
- Product Artifacts
- AI Generated Documents
- Review Activities
- Governance Decisions

These principles **do NOT apply to**:
- Software implementation
- Coding conventions
- CI/CD pipelines
- DevOps
- Runtime architecture

## Principle Directory

| ID | Name |
| :--- | :--- |
| **PRN-001** | Think before Design |
| **PRN-002** | Discovery before Delivery |
| **PRN-003** | Evidence over Assumption |
| **PRN-004** | Alignment over Speed |
| **PRN-005** | Quality over Quantity |
| **PRN-006** | Governance over Preference |
| **PRN-007** | Traceability by Default |
| **PRN-008** | Freeze before Expansion |
| **PRN-009** | Extensibility by Design |
| **PRN-010** | Absolute Auditability |

## Core Operating Principles

### PRN-001: Think before Design
**Purpose:** Prevent premature solutioning.
**Intent:** Enforce strict sequential dependency across all product phases.
**Rationale:** Every design decision carries a long-term technical and operational debt. No downstream design activity may begin until the required discovery artifacts are validated and frozen.

### PRN-002: Discovery before Delivery
**Purpose:** Minimize wasted implementation effort.
**Intent:** Protect implementation capital by validating early.
**Rationale:** Solution implementation is typically the most expensive and difficult phase to reverse. We do not build to discover if an idea is viable. We discover viability through artifact-driven validation before a single line of code is written.

### PRN-003: Evidence over Assumption
**Purpose:** Anchor decisions in reality.
**Intent:** Eliminate subjectivity from strategic planning.
**Rationale:** Assumptions are inevitable in enterprise planning, but they are liabilities until validated. Product decisions must be anchored in documented evidence, user behavior, and domain reality. Unverified assumptions must be tracked explicitly as risks.

### PRN-004: Alignment over Speed
**Purpose:** Prevent systemic organizational debt.
**Intent:** Maintain strategic consensus across all stakeholders.
**Rationale:** Moving fast in the wrong direction is a failure of governance. Rapid generation of artifacts is secondary to achieving stakeholder and architectural alignment. We willingly sacrifice short-term velocity to prevent long-term systemic debt.

### PRN-005: Quality over Quantity
**Purpose:** Maximize artifact utility.
**Intent:** Elevate structural signal over superficial noise.
**Rationale:** The framework forbids the mass generation of shallow documentation. A single, highly concentrated artifact with deep domain insight is infinitely more valuable than twenty pages of superficial feature lists.

### PRN-006: Governance over Preference
**Purpose:** Ensure methodological consistency.
**Intent:** Standardize product execution universally.
**Rationale:** Individual opinions and preferences are subordinate to the framework's governance model. Artifacts must adhere strictly to their mandated scope and quality gates, regardless of the author's preferred working style.

### PRN-007: Traceability by Default
**Purpose:** Ensure justification for all downstream decisions.
**Intent:** Guarantee that every feature maps to a frozen objective.
**Rationale:** No feature, capability, or user requirement exists in a vacuum. Every decision must be explicitly traceable back to a frozen goal. "Orphaned" decisions are automatically rejected.

### PRN-008: Freeze before Expansion
**Purpose:** Establish stable baselines.
**Intent:** Prevent cascading failures caused by shifting foundations.
**Rationale:** A phase or artifact must be formally frozen before any dependent downstream work can begin. Modifying a frozen artifact requires a formal resolution process, preventing cascading instability across the product ecosystem.

## Enterprise-Grade Extensions

### PRN-009: Extensibility by Design
**Purpose:** Support cross-domain scaling.
**Intent:** Ensure universal applicability across distinct business verticals.
**Rationale:** The framework must remain product-agnostic. While it supports domain-specific extensions, the core principles must scale across any enterprise domain without requiring structural modification.

### PRN-010: Absolute Auditability
**Purpose:** Enable compliance and historical context.
**Intent:** Protect organizational memory and decision history.
**Rationale:** Every strategic decision, review resolution, and phase freeze must leave a permanent, immutable footprint. In regulated environments, the history of *why* a decision was made is as critical as the decision itself.

## Principle Priority

When conflict resolution is required, principles are prioritized by their tier:

**Tier 1 (Non-Negotiable Supremacy)**
- Think before Design (PRN-001)
- Governance (PRN-006)
- Evidence (PRN-003)
- Traceability (PRN-007)

**Tier 2 (Strategic Anchors)**
- Alignment (PRN-004)
- Discovery (PRN-002)
- Freeze (PRN-008)

**Tier 3 (Operational Values)**
- Quality (PRN-005)
- Extensibility (PRN-009)
- Auditability (PRN-010)

## Decision Hierarchy

Conflicts between principles must be resolved according to the Framework Workflow. Detailed conflict resolution hierarchy is fully delegated to `03_FrameworkWorkflow.md`.

## Principle Compliance

Compliance with these principles is evaluated according to:
- `07_ReviewStandards.md`
- `08_QualityGates.md`

and governed by:
- `09_Governance.md`

## Document Non-Goals

This document explicitly does NOT:
- Define workflow
- Define review lifecycle
- Define governance process
- Define AI prompts
- Define versioning
- Define quality gates

## Document Ownership

**Owns:**
- Framework Philosophy
- Operating Principles
- Decision Hierarchy

**Explicitly Out of Scope:**
- Workflow
- Review
- Governance
- Quality Gates
- Versioning
- Prompt Engineering
- Metadata
- Naming
- Decision Register

## Revision Policy
This document acts as a core Framework Baseline and may only be modified through:
1. Formal Framework Change Request
2. Architecture Review
3. Executive Approval
4. Version Update

## Document Exit Criteria

This artifact may be frozen only when:
- [ ] Architecture Review Passed
- [ ] Dependency Validation Passed
- [ ] Boundary Validation Passed
- [ ] No Scope Leakage Detected
- [ ] No Principle Conflicts Exist
- [ ] Manifest Alignment Verified
- [ ] Executive Approval Granted

---

## Appendix A: Principle Interaction Matrix

The following matrix maps how principles natively support one another within the framework.

| Principle | Supports |
| :--- | :--- |
| **PRN-001** (Think before Design) | PRN-002, PRN-004 |
| **PRN-002** (Discovery before Delivery) | PRN-003, PRN-008 |
| **PRN-003** (Evidence over Assumption) | PRN-007, PRN-010 |
| **PRN-004** (Alignment over Speed) | PRN-006, PRN-008 |
| **PRN-005** (Quality over Quantity) | PRN-004, PRN-010 |
| **PRN-006** (Governance over Preference) | PRN-004, PRN-005 |
| **PRN-007** (Traceability by Default) | PRN-003, PRN-010 |
| **PRN-008** (Freeze before Expansion) | PRN-001, PRN-010 |
| **PRN-009** (Extensibility by Design) | PRN-006 |
| **PRN-010** (Absolute Auditability) | PRN-003, PRN-007 |
