# NIST CSF 2.0 Mapping

## How this mapping was built

NIST CSF 2.0 is used here as an **outcomes framework**, not as a set of organizational controls. Each mapping connects a finding to the CSF outcome it relates to, with a rationale explaining *why* the outcome fits — not a keyword match. All subcategory codes and outcome statements were verified against the official NIST CSF 2.0 core (NIST.CSWP.29, February 2024).

## Mappings

### M-01 — MFA not enforced (F-01) → PR.AA-03

| Element | Detail |
|---|---|
| Finding | F-01: 247 active accounts without required MFA |
| Control objective | Customers authenticate at the assurance level the organization requires |
| Function | **Protect (PR)** — safeguards to manage cybersecurity risk are used |
| Category | **PR.AA — Identity Management, Authentication, and Access Control** |
| Subcategory | **PR.AA-03** — "Users, services, and hardware are authenticated" |
| Rationale | MFA is how this organization implements its required authentication strength for customers. MFA was required for the affected customer population, but 247 active accounts remained under a legacy authentication policy without the required MFA protection. The accounts were still authenticated; the deficiency was that the organization's required authentication method was not enforced for this population. That is distinct from the NIST outcome itself — "Users, services, and hardware are authenticated" — which describes authentication occurring, not the specific method an organization requires. |

### M-02 — Legacy population not managed → PR.AA-01

| Element | Detail |
|---|---|
| Finding | F-01 (population-management aspect) |
| Control objective | The organization knows which authentication policy each identity is subject to |
| Function | **Protect (PR)** |
| Category | **PR.AA — Identity Management, Authentication, and Access Control** |
| Subcategory | **PR.AA-01** — "Identities and credentials for authorized users, services, and hardware are managed by the organization" |
| Rationale | 247 identities were not managed to the current credential standard. The gap is a failure of identity/credential lifecycle management, which is exactly the PR.AA-01 outcome. |

### M-03 — Migration gap / policy not enforced → GV.PO-01

| Element | Detail |
|---|---|
| Finding | F-01 (governance aspect); C-04 design gap |
| Control objective | Authentication policy is enforced, not just written |
| Function | **Govern (GV)** — risk management strategy, expectations, and policy are established, communicated, and monitored |
| Category | **GV.PO — Policy** |
| Subcategory | **GV.PO-01** — "Policy for managing cybersecurity risks is established based on organizational context, cybersecurity strategy, and priorities and is communicated and enforced" |
| Rationale | The MFA policy was established and communicated but not *enforced* for the legacy population. GV.PO-01 explicitly includes enforcement, so the finding maps to the enforcement clause of this outcome. |

### M-04 — Failed-login analysis → DE.CM-03 and DE.AE-02

| Element | Detail |
|---|---|
| Finding | Supporting analysis for F-01 (threat context); C-03 observation |
| Control objective | Authentication abuse is monitored and analyzed |
| Function | **Detect (DE)** — possible attacks and compromises are found and analyzed |
| Category | **DE.CM — Continuous Monitoring** |
| Subcategory | **DE.CM-03** — "Personnel activity and technology usage are monitored to find potentially adverse events" |
| Rationale | Customer login attempts are technology usage. The 14,820 failed attempts were captured through monitoring of authentication activity — the DE.CM-03 outcome in practice. |
| Second mapping | **DE.AE-02** — "Potentially adverse events are analyzed to better understand associated activities" (Category: DE.AE — Adverse Event Analysis). The consecutive-failure analysis (312 accounts) is analysis of potentially adverse events to understand them — while explicitly stopping short of declaring an incident. |

### M-05 — Risk assessment and treatment → ID.RA-05 and ID.RA-06

| Element | Detail |
|---|---|
| Finding | Assessment process itself |
| Control objective | Risks are understood and responded to systematically |
| Function | **Identify (ID)** — the organization's current cybersecurity risks are understood |
| Category | **ID.RA — Risk Assessment** |
| Subcategories | **ID.RA-05** — "Threats, vulnerabilities, likelihoods, and impacts are used to understand inherent risk and inform risk response prioritization"; **ID.RA-06** — "Risk responses are chosen, prioritized, planned, tracked, and communicated" |
| Rationale | The risk register applies ID.RA-05 (documented likelihood/impact reasoning per risk) and the remediation plan applies ID.RA-06 (chosen, prioritized, owned treatments). |

### M-06 — Legacy accounts as unmanaged exceptions → ID.RA-07

| Element | Detail |
|---|---|
| Finding | F-01 (exception-management aspect) |
| Function | **Identify (ID)** |
| Category | **ID.RA — Risk Assessment** |
| Subcategory | **ID.RA-07** — "Changes and exceptions are managed, assessed for risk impact, recorded, and tracked" |
| Rationale | The 247 accounts functioned as an unmanaged population outside the current MFA requirement; there is no evidence that this population was formally recorded, assessed, or tracked as an exception. Against the ID.RA-07 outcome, the gap is in the "recorded, and tracked" clause — the non-compliant population was never brought under exception management. Marked as a supporting mapping: the primary mappings for F-01 are M-01 through M-03. |

## Deliberately not mapped

- **Respond (RS) and Recover (RC):** No incident was declared — correctly, since no compromise was established. Mapping failed logins to incident response subcategories would overstate the evidence.
- **PR.AA-05** (access permissions, least privilege): the finding concerns authentication strength, not authorization scope. Not mapped.
- **DE.CM-01** (network monitoring): the evidence is authentication-log analysis, not network monitoring. Not mapped.

## Verification note

Subcategory IDs and outcome statements above were checked against the NIST CSF 2.0 core (NIST.CSWP.29). Note that CSF 2.0 uses **PR.AA** (not PR.AC, which is the CSF 1.1 identifier) for Identity Management, Authentication, and Access Control. Any future framework updates should be re-verified before reuse.
