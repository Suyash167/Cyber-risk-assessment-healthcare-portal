# Residual Risk Assessment

Residual risk is assessed **after** the planned treatments in the [remediation plan](../07_Remediation/remediation_plan.md) are fully implemented and validated against the [acceptance criteria](../07_Remediation/acceptance_criteria.md). Residual ratings assume validation actually occurred — a treatment that is planned but not validated does not reduce risk.

## R-01 — Credential-based takeover of legacy-policy accounts

**Treatments applied:** MFA enforced on all 247 accounts (verified, not just configured); full population reconciled; migration/provisioning process fixed so silent legacy assignment cannot recur; recurring compliance monitoring in place; independent validation completed with evidence retained.

**Residual likelihood: Low.** The vulnerability (password-only authentication on in-scope accounts) is removed, and the detective gap is closed. Credential attacks can still be attempted, but MFA blocks the payoff at scale.

**Residual impact: High.** Data sensitivity does not change with the control fix.

**Residual risk: Medium.**

**Acceptance consideration:** A Medium residual risk driven by High impact is a normal outcome for customer-data systems — it reflects that impact cannot be engineered away, only likelihood. Leadership should formally acknowledge the residual risk. If any account receives a documented exception from MFA (AC-01), that exception is itself a risk acceptance decision requiring owner, rationale, compensating controls, and a review date.

## R-02 — Undetected additional accounts outside policy

**Treatments applied:** Full reconciliation against the authoritative account source; recurring automated compliance reporting on policy association.

**Residual likelihood: Low.** The population boundary is now known and continuously monitored.

**Residual impact: High.** Unchanged.

**Residual risk: Medium.** Same acceptance logic as R-01.

## R-03 — Online guessing against customer accounts

**Treatments applied:** Lockout threshold confirmed and lockout event evidence validated (C-03 follow-up closed); alerting on consecutive-failure patterns; MFA enforced population-wide via R-01 treatment.

**Residual likelihood: Low.** Guessing must now defeat MFA and confirmed throttling.

**Residual impact: High.** Unchanged.

**Residual risk: Medium.**

## What "acceptance" means here

Risk acceptance is a **decision**, not the absence of action. For each residual risk, acceptance requires: the risk owner named, the residual rating understood, the acceptance rationale recorded, and a review trigger (date or event, e.g., next assessment cycle). Accepting residual risk does not close finding F-01 — only meeting AC-01 through AC-04 does that.

## If treatments are not completed

Any treatment left incomplete or unvalidated leaves the corresponding risk at its inherent level. Partial remediation (e.g., MFA enforced but no reconciliation) must be reported as such, not rounded down.
