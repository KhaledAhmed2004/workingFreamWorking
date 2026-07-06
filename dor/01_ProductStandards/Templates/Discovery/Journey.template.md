---
Title: [Product Name] Journey Maps
Artifact Version: 1.0
Status: Draft
Phase: Product Discovery
Sprint: [Sprint Number/Name]
Owner: [Owner Name]
Reviewer: [Reviewer Name]
Approver: [Approver Name]
Created: [YYYY-MM-DD]
Updated: [YYYY-MM-DD]
Artifact ID: [Unique ID]
Depends On: [Problem Artifact ID], [Principles Artifact ID], [Persona Artifact ID], [JTBD Artifact ID]
Next Artifact: [Requirements Document]
---

<!-- SECTION GROUP: Discovery Core -->

# 1. Executive Summary
[A high-level summary of the critical journeys mapped in this document, highlighting the core transition from Current State frictions to Future State resolutions.]

# 2. Purpose
[Define the intent of this Journey Document. How does it bridge the gap between JTBD and technical requirements?]

# 3. Scope
[Define which JTBDs are being mapped. Note any boundaries or specific touchpoints explicitly excluded.]

<!-- SECTION GROUP: Journey Mapping -->

# 4. Current State Journeys
[Maps of how the Personas currently accomplish their Jobs, highlighting existing frictions.]

## [Journey Name] (e.g., Current Manual Shift Handoff)
- **Journey ID**: [e.g., JRN-001]
- **Journey Version ID**: [e.g., v1.0]
- **Journey Status**: [Active / Candidate / Merged / Archived]
- **Parent JTBD**: [e.g., JTBD-001]
- **Performed By**: [e.g., PER-001]
- **State**: Current State
- **Trigger**: [What initiates this journey?]
- **Outcome**: [How it concludes today]

### Phase 1: [Domain-Specific Phase Name, e.g., Preparation]
- **Step**: [e.g., Nurse manually transcribes notes]
  - **Touchpoint**: [e.g., Paper clipboard]
  - **Emotional Valence**: [Negative]
  - **Friction**: [High risk of transcription error, takes 15 mins]
  - **Moment of Truth**: [Yes/No]

### Phase 2: [Domain-Specific Phase Name, e.g., Execution]
- **Step**: [...]
  - **Touchpoint**: [...]
  - **Emotional Valence**: [...]
  - **Friction**: [...]
  - **Moment of Truth**: [...]

*(Repeat for each Current State Journey)*


# 5. Future State Journeys
[Maps of the envisioned experience, demonstrating how the product resolves current frictions.]

## [Journey Name] (e.g., Automated Digital Shift Handoff)
- **Journey ID**: [e.g., JRN-002]
- **Journey Version ID**: [...]
- **Journey Status**: [...]
- **Parent JTBD**: [e.g., JTBD-001]
- **Performed By**: [e.g., PER-001]
- **State**: Future State
- **Trigger**: [What initiates this journey in the new product?]
- **Outcome**: [How it concludes, MUST satisfy JTBD Success Metric]

### Phase 1: [Domain-Specific Phase Name, e.g., Preparation]
- **Step**: [e.g., Nurse taps 'Generate Handoff' on tablet]
  - **Touchpoint**: [e.g., Mobile App - Dashboard]
  - **Emotional Valence**: [Positive]
  - **Friction**: [None]
  - **Moment of Truth**: [Yes]

### Phase 2: [Domain-Specific Phase Name]
- **Step**: [...]
  - **Touchpoint**: [...]
  - **Emotional Valence**: [...]
  - **Friction**: [...]
  - **Moment of Truth**: [...]

*(Repeat for each Future State Journey)*

<!-- SECTION GROUP: Journey Analysis -->

# 6. Moments of Truth Matrix
[A consolidated list of all the make-or-break steps identified across the Future State Journeys. These MUST be protected during development.]

# 7. Touchpoint Inventory
[A summary of all channels/interfaces where the user interacts with the product (e.g., Mobile App, Web Portal, API, Email).]

# 8. Resolved Frictions
[A traceability map showing exactly how the frictions identified in the Current State (or in `106_JTBD`) are eliminated in the Future State.]

<!-- SECTION GROUP: Governance -->

# 9. Traceability
[Link each Journey explicitly back to `JTBD-ID`, `PER-ID`, and `103_Principles` trade-offs.]

# 10. AI Context
[Special instructions for downstream AI agents reading this file. Example: "When generating Requirements from this artifact, ensure every 'Moment of Truth' is translated into a mandatory Epic."]
