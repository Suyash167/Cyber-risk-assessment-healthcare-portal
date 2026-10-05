# Cyber Risk Assessment – Healthcare Customer Portal

**Simulated GRC case study | August – September 2026 | Northeastern University**

> **This repository contains a simulated/academic case study. No real customer information, credentials, production logs, or proprietary organizational data are included.** It does not represent work performed for any actual healthcare organization.

## Executive overview

This project is a control-focused cyber risk assessment of authentication controls for a simulated healthcare customer portal. The objective was to determine whether authentication controls — multi-factor authentication (MFA), password policy, account lockout, and a legacy authentication-policy migration — were designed effectively and operating as required, and to translate the results into risk information leadership could act on.

Testing found one material control exception: **247 active customer accounts remained under a legacy authentication policy and did not have the required MFA configuration**. Authentication logs for the assessment period showed **14,820 failed login attempts**, including **312 accounts with five or more consecutive failures** — activity that warrants attention but does **not** establish that any account was compromised. Root-cause analysis traced the exception to a migration process gap, and the assessment closes with a risk register, NIST CSF 2.0 mapping, remediation plan with measurable acceptance criteria, and an executive summary.

## Project objectives

- Define control objectives and requirements for portal authentication controls
- Distinguish control requirements from observed conditions
- Evaluate evidence and separate evidence from inference
- Assess design effectiveness and operating effectiveness for each control
- Identify control exceptions and distinguish them from evidence limitations and actual incidents
- Perform root-cause analysis, separating root cause from contributing factors
- Assess inherent and residual risk using a documented methodology
- Develop risk treatments and measurable remediation acceptance criteria
- Map findings to NIST CSF 2.0 outcomes (verified against the official framework core)
- Communicate results to technical teams and business leadership

## Scope

**In scope:** Authentication controls for the simulated healthcare customer portal — MFA enforcement, password policy configuration, account lockout behavior, authentication activity logging, and the legacy-to-current authentication-policy migration.

**Out of scope:** Network security, application code vulnerabilities, third-party/vendor controls, physical security, and incident response capability. No penetration testing was performed.

**Period:** August 2026 – September 2026. Evidence is point-in-time unless stated otherwise.

## Methodology

```text
Scope
↓
Control Objectives
↓
Evidence Collection
↓
Evidence Evaluation
↓
Control Assessment
↓
Finding Identification
↓
Root Cause Analysis
↓
Risk Assessment
↓
NIST CSF Mapping
↓
Risk Treatment
↓
Remediation Acceptance Criteria
↓
Residual Risk
↓
Executive Communication
```

Each phase is documented in this repository. Evidence classifications used throughout: **PROVED**, **SUPPORTED**, **LIKELY**, **NOT PROVED**, **CONTRADICTED**, **MISSING EVIDENCE**.

## Key finding

**F-01 — Required MFA not enforced on 247 active customer accounts.** These accounts remained associated with a legacy authentication policy after migration and did not have the required MFA configuration, leaving them exposed to credential-based attack at a lower authentication assurance level than policy requires. See [03_Findings/authentication_policy_finding.md](03_Findings/authentication_policy_finding.md).

## Key evidence

| Evidence | Result |
|---|---|
| Accounts under legacy policy without required MFA | **247** active customer accounts |
| Failed login attempts in assessment-period logs | **14,820** |
| Accounts with ≥5 consecutive failed logins | **312** |
| Confirmed account compromise | **None established** |

The failed-login figures show a high volume of failed authentication activity worth monitoring. They do **not** establish malicious intent for any specific attempt and do **not** establish that any account was compromised. This distinction is maintained throughout the repository.

## Frameworks and methodologies

- **NIST Cybersecurity Framework (CSF) 2.0** — used strictly as an outcomes framework. Every subcategory code in [06_NIST_CSF/nist_csf_mapping.md](06_NIST_CSF/nist_csf_mapping.md) was verified against the official CSF 2.0 core (NIST.CSWP.29, February 2024). Where no subcategory maps directly, that is stated instead of forcing a fit.
- **Qualitative risk assessment** — 3-level likelihood × impact matrix, documented in [05_Risk_Assessment/risk_register.md](05_Risk_Assessment/risk_register.md). Ratings apply this assessment's documented working methodology; an operational engagement would apply the organization's defined method.

## Skills demonstrated

Cyber Risk Assessment · GRC · Control Testing · Evidence Analysis · Root Cause Analysis · Risk Assessment · Residual Risk · NIST CSF 2.0 · IAM / Access Control · Authentication Controls · Sampling Analysis · Remediation Planning · Executive Reporting · Business Impact Analysis

## Repository structure

```text
01_Assessment/          Scope, objectives, control-by-control assessment
02_Evidence_Analysis/   Evidence inventory, evaluation matrix, sampling analysis
03_Findings/            Formal GRC finding (condition → criteria → cause → …)
04_Root_Cause/          Root-cause analysis with reasoning chain
05_Risk_Assessment/     Risk register, inherent and residual risk
06_NIST_CSF/            Verified NIST CSF 2.0 mapping
07_Remediation/         Remediation plan and measurable acceptance criteria
08_Executive_Output/    Executive summary and business impact analysis
```

## How to read this repository

Start with the [executive summary](08_Executive_Output/executive_summary.md) for the one-page version. Workpapers follow the methodology flow above: assessment → evidence → finding → root cause → risk → framework mapping → remediation → executive output.
