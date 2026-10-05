# Executive Summary — Cyber Risk Assessment, Healthcare Customer Portal

**Assessment period:** August – September 2026 · **Classification:** Simulated academic case study (Northeastern University)

## What happened

We assessed whether authentication controls on the customer portal — MFA, password policy, account lockout, and a legacy authentication-policy migration — were designed well and operating as required. The migration from the legacy authentication policy to the current policy did not fully complete: **247 active customer accounts** remained on the legacy policy without the MFA configuration the current policy requires. The migration was treated as finished, and nothing in the process flagged the remainder.

## How many accounts were affected

247 active customer accounts. The total portal population was not confirmed in the available evidence, so this is reported as a count, not a percentage.

## What the evidence showed

- 247 active accounts on the legacy policy without required MFA (confirmed).
- 14,820 failed login attempts in the assessment period, including 312 accounts with five or more consecutive failures (confirmed).
- Password policy settings matched requirements; no misconfiguration found.
- Whether account lockout operated as designed could not be confirmed — the threshold and event records were not in evidence (a testing gap, not a proven failure).

## What the evidence does NOT establish

The failed-login activity shows the portal is being probed. It does **not** establish that any specific attempt was malicious, and it does **not** establish that any account — including the 247 — was compromised. No incident is declared. Treating failed logins as a breach would overstate the evidence; ignoring them would understate the risk.

## Why it matters

The 247 accounts authenticate at a lower assurance level than policy requires, in a portal serving healthcare customers. Credential-based attack (phishing-derived passwords, credential stuffing, password spraying) is the most likely way this gap gets exploited, and the observed probing shows attackers are already knocking. The business exposure is customer-data confidentiality, regulatory scrutiny, and customer trust.

## What management should do

1. Reconcile the full account population and enforce MFA on every in-scope account (immediate).
2. Fix the migration process so silent failures cannot recur, and add recurring compliance monitoring (near term).
3. Validate lockout effectiveness and tune alerting on probing patterns (near term).
4. Have GRC independently validate all of the above before the finding is closed.

## Residual risk

After the remediation plan is fully implemented and independently validated, residual risk for each identified risk is **Medium** (Low likelihood × High impact). The impact side cannot be engineered away for a customer-data system; the likelihood side is what remediation reduces. Any MFA exceptions require documented risk acceptance with an owner, rationale, compensating controls, and a review date.

## Decision required

Management is asked to (a) approve the remediation plan and resourcing, (b) acknowledge the Medium residual risk on completion, and (c) decide the review cadence for the recurring compliance monitoring. Finding F-01 stays open until the acceptance criteria are met and validated — not when the work is merely reported complete.

---
*Supporting detail: [finding](../03_Findings/authentication_policy_finding.md) · [risk register](../05_Risk_Assessment/risk_register.md) · [remediation plan](../07_Remediation/remediation_plan.md) · [business impact analysis](business_impact_analysis.md)*
