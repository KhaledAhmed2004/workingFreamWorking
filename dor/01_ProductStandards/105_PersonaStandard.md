---
Title: 105_PersonaStandard
Artifact Version: 1.0
Framework Version: 1.0
Supersedes: N/A
Status: Frozen
Phase: Product Standards Infrastructure
Sprint: N/A
Owner: Product Architecture Board
Reviewer: Enterprise Architecture Review Board
Approver: Executive Board
Created: 2026-07-06
Updated: 2026-07-06
Approval Date: 2026-07-06
Last Reviewed: 2026-07-06
Review Status: Approved
Artifact ID: PS-105
Depends On: 101_ProblemStandard.md, 103_ProductPrinciplesStandard.md, 104_StakeholderStandard.md
Extends: 050_ProductStandardContract.md
Base Contract: 050_ProductStandardContract.md
Template Path: 01_ProductStandards/Templates/Discovery/Persona.template.md
Next Artifact: 106_JTBDStandard.md
---

# Persona Standard

## 1. Definition
The `105_PersonaStandard` dictates how to synthesize representative user archetypes from the validated `104_StakeholderStandard`. While a Stakeholder represents a purely structural and impacted entity in the business ecosystem, a Persona represents the humanized, empathetic model used for downstream Jobs-To-Be-Done (`106`), Journey Mapping (`107`), and UX Architecture. 

## 2. Validation & Quality Gates
Artifacts following this standard MUST pass these checks:

### Validation Rules
- No orphan Personas.
- Every Persona MUST have a unique `PER-ID` (e.g., PER-001).
- Every Persona MUST trace to at least one Stakeholder ID.
- Primary Personas SHOULD trace to one Primary Stakeholder unless justified.
- Every Primary Stakeholder in `104` MUST have at least one mapped Persona in `105`.

### Quality Gates
- **QG-PER-001**: Reject if a Persona introduces macro-goals or organizational pain points not present in the parent Stakeholder Card.
- **QG-PER-002**: Reject if a Persona lacks a distinct psychological or behavioral profile (rendering it just a duplicated stakeholder).
- **QG-PER-003**: Reject if an Anti-Persona is missing for high-risk or adversarial stakeholder types.
- **QG-PER-004**: Reject if persona traits are not backed by stakeholder data, research, interview evidence, or validated assumptions.

## 3. Core Components

### 3.1 Persona Types
1. **Primary Persona**: The main archetype driving core product loops (Derived from Primary Stakeholders).
2. **Secondary Persona**: The archetype assisting or administering the product (Derived from Secondary/Operational Stakeholders).
3. **Anti-Persona**: The archetype the product is explicitly NOT built for, or one that actively acts against it (Derived from Adversarial Stakeholders).

### 3.2 Persona Metadata Schema (The Persona Card)
Every Persona MUST be modeled with this strict schema:
- **Persona ID**: (e.g., PER-001)
- **Persona Version ID**: (e.g., v1.0, v1.1)
- **Persona Status**: (Active / Candidate / Merged / Archived)
- **Stakeholder ID**: (e.g., STK-001, STK-002)
- **Name**: (Archetype Name, e.g., "Clinical Clara")
- **Role / Title**: (e.g., Senior ICU Nurse)
- **Demographics**: (Age, Location, Education - ONLY if it statistically impacts product usage)
- **Behavioral Traits**: (e.g., Tech-savvy, Time-poor, Detail-oriented)
- **Psychographics**: (Motivations, Frustrations, Cognitive Load constraints)
- **Operating Environment**: (Where do they use the product? e.g., Noisy ER, sterile gloves)
- **Tech Fluency**: (Low / Medium / High / Expert)
- **Goals**: (Specific objectives for the persona)
- **Pain Points**: (Current blockers)
- **Needs**: (Must-haves to succeed)
- **Frictions**: (Things that slow them down)
- **Success Definition**: (What constitutes a 'win' for them)
- **Accessibility / Inclusion Needs**: (e.g., colorblindness, large text, screen readers)
- **Evidence Source**: (e.g., 2026 User Interviews, Analytics Data)
- **Research Method**: (Interview / Observation / Survey / Analytics / Shadowing / Diary Study / Support Tickets)
- **Confidence Level**: (Validated / High / Medium / Low)

## 4. Output Contract
To guarantee deterministic AI orchestration, this artifact explicitly produces the following machine-readable assets for downstream nodes:
- **Persona Registry**
- **Empathy Map**
- **Behavioral Constraints**
- **Accessibility Constraints**
- **Operating Environment Constraints**
- **Anti-Persona Definitions**

## 5. Traceability
Every Persona MUST trace back to:
- **Parent Stakeholder(s)** (`STK-ID` from `104_StakeholderStandard.md`).

## 6. Context & AI Prompts
### Hydration Rules
- AI Swarms MUST NOT infer or hallucinate Personas that do not explicitly map to a validated `STK-ID` from `104`.
- AI MUST NOT create demographic details unless they materially affect product behavior, access, risk, or usability.
- AI MUST synthesize behavioral traits logically derived from the Stakeholder's defined pain points and goals.

### Memory TTL
- `Permanent` for the duration of the Human Context Layer generation.

## 7. Anti-Patterns
- **The Stereotype**: Creating personas based on lazy demographic cliches rather than behavioral patterns.
- **The Super User**: Creating a persona that knows how to use every feature perfectly and has unlimited time.
- **The Disconnected Persona**: A persona that has no `STK-ID` trace, essentially inventing a new user type mid-discovery.

## 8. Section Registry (Template Contract)
Every Persona artifact MUST use these exact headings.

<!-- SECTION GROUP: Discovery Core -->
- # 1. Executive Summary
- # 2. Purpose
- # 3. Scope

<!-- SECTION GROUP: Persona Registry -->
- # 4. Primary Personas
- # 5. Secondary Personas
- # 6. Anti-Personas

<!-- SECTION GROUP: Empathy Mapping -->
- # 7. Behavioral Patterns
- # 8. Psychological Profile
- # 9. Operating Environment

<!-- SECTION GROUP: Governance -->
- # 10. Traceability
- # 11. AI Context
