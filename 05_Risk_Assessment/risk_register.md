# Risk Register

## Methodology (working method for this assessment)

Ratings are qualitative and apply the scales below, documented here so the ratings are reproducible. This is the assessment's working methodology for a simulated case. An operational engagement would apply the organization's defined risk methodology (cf. NIST CSF 2.0 GV.RM-06: a standardized method for calculating, documenting, categorizing, and prioritizing cybersecurity risks).

**Likelihood** — probability of the risk event occurring within 12 months given the control environment:
- **High:** conditions for the event already exist and threat activity is observed
- **Medium:** conditions partially exist or threat activity is plausible but not observed
- **Low:** conditions do not currently exist; event would require multiple new failures

**Impact** — worst credible business consequence:
- **High:** customer data exposure at scale, regulatory action, or major reputational harm
- **Medium:** limited data exposure, operational disruption, manageable compliance findings
- **Low:** minimal data or operational consequence

**Risk level matrix:**

| Likelihood \ Impact | Low | Medium | High |
|---|---|---|---|
| High | Medium | High | High |
| Medium | Low | Medium | High |
| Low | Low | Low | Medium |

## Register

### R-01 — Credential-based takeover of legacy-policy accounts

| Field | Detail |
|---|---|
| Risk statement | Because 247 active customer accounts authenticate without required MFA, a threat actor using stolen or guessed credentials could gain unauthorized access to those accounts, exposing customer information. |
| Condition | 247 active accounts on legacy policy without required MFA (F-01) |
| Risk event | Unauthorized access to one or more customer accounts via credential-based attack |
| Threat | External attackers using credential stuffing, password spraying, or phishing-derived credentials; 14,820 failed logins in the period indicate ongoing authentication probing (threat activity observed, intent not established per attempt) |
| Vulnerability / control gap | Missing required MFA on 247 accounts; no reconciliation detecting the gap |
| Likelihood | **High** — exposed population exists and probing activity is observed |
| Impact | **High** — healthcare customer accounts; confidentiality exposure with regulatory and reputational consequences |
| Inherent risk | **High** |
| Treatment | Enforce MFA on all 247 accounts; reconcile full population; fix migration process; add recurring compliance monitoring; independent validation (see remediation plan) |
| Residual likelihood | **Low** — MFA enforced and monitored; migration gap closed |
| Residual impact | **High** — data sensitivity unchanged |
| Residual risk | **Medium** |
| Risk owner | Product Owner (accountable); IAM Team (remediation) |
| Acceptance criteria | AC-01 through AC-04 — 100% reconciliation, MFA enforced, process fixed, independently validated |

### R-02 — Undetected additional accounts outside policy

| Field | Detail |
|---|---|
| Risk statement | Because the account population was never fully reconciled, additional accounts beyond the identified 247 may sit outside the required authentication policy without anyone knowing. |
| Condition | No complete population reconciliation performed (evidence limitation) |
| Risk event | Unknown accounts remain non-compliant with MFA requirements |
| Threat | Same credential-based threats as R-01 |
| Vulnerability / control gap | Absence of detective reconciliation control |
| Likelihood | **Medium** — a gap of 247 was already found; the population boundary is unconfirmed |
| Impact | **High** — same data exposure as R-01 if such accounts exist |
| Inherent risk | **High** |
| Treatment | Full population reconciliation against authoritative account source; recurring automated compliance reporting |
| Residual likelihood | **Low** — reconciliation complete and recurring |
| Residual impact | **High** |
| Residual risk | **Medium** |
| Risk owner | IAM Team |
| Acceptance criteria | AC-01, AC-04 |

### R-03 — Online guessing against customer accounts

| Field | Detail |
|---|---|
| Risk statement | Attackers may continue probing customer credentials (14,820 failed attempts observed; 312 accounts with ≥5 consecutive failures), and without confirmed lockout effectiveness, sustained guessing could eventually succeed against weak passwords. |
| Condition | Observed authentication probing; lockout operating effectiveness not established (C-03 evidence limitation) |
| Risk event | Successful account takeover via sustained password guessing |
| Threat | External attackers conducting password spraying / brute force |
| Vulnerability / control gap | Unconfirmed throttling effectiveness |
| Likelihood | **Medium** — probing observed, but password policy is enforced (C-02) and no MFA gap exists outside F-01 |
| Impact | **High** — same account/data exposure |
| Inherent risk | **High** |
| Treatment | Confirm lockout threshold and validate lockout event evidence (follow-up testing); tune monitoring/alerting on consecutive-failure patterns; enforce MFA population-wide per R-01 treatment |
| Residual likelihood | **Low** — with MFA enforced (R-01) and lockout confirmed, guessing alone cannot reach accounts at scale |
| Residual impact | **High** |
| Residual risk | **Medium** |
| Risk owner | Security (monitoring); IAM Team (lockout validation) |
| Acceptance criteria | Lockout effectiveness evidenced; alerting in place; AC-02 |

## Notes

- No risk is rated on the basis of a confirmed incident — none was established.
- Likelihood for R-01 is High because the vulnerable condition and threat activity are both observed, not because compromise is assumed.
- If leadership accepts any residual risk (e.g., documented exceptions under AC-01), the acceptance decision, rationale, and review date must be recorded — see residual risk.
