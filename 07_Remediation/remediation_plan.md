# Remediation Plan — Finding F-01

## RP-01 — Reconcile the portal population against the required authentication policy

- **Owner:** IAM Team
- **Priority:** P1 (blocks everything else — the true affected population is unknown until this is done)
- **Target state:** A complete, authoritative list of active customer accounts, each mapped to its current authentication policy.
- **Validation evidence:** Reconciliation report showing account source(s), matching logic, and disposition of every account (compliant / legacy / exception).
- **Acceptance criteria:** AC-01

## RP-02 — Enforce required MFA on all identified legacy-policy accounts

- **Owner:** IAM Team (execution); Application Engineering (technical enablement)
- **Priority:** P1
- **Target state:** Every in-scope active account has the required MFA configuration enforced; any account that cannot be migrated has a documented, approved exception (see RP-08 notes on acceptance).
- **Validation evidence:** Post-remediation configuration extract proving MFA enforcement per account; exception register with approvals where applicable.
- **Acceptance criteria:** AC-01, AC-02

## RP-03 — Fix the migration/provisioning process

- **Owner:** Application Engineering
- **Priority:** P1
- **Target state:** The process that moves accounts to the current policy includes a reconciliation/verification step, and failures are identifiable and actionable (logged, alerted, queued for resolution) rather than silent.
- **Validation evidence:** Updated process documentation; test evidence showing a deliberately failed migration is detected and flagged.
- **Acceptance criteria:** AC-03

## RP-04 — Implement recurring authentication-policy compliance monitoring

- **Owner:** Security (detection); GRC (reporting)
- **Priority:** P2
- **Target state:** Automated, recurring reporting of account-to-policy compliance (accounts outside the required policy, MFA coverage) reviewed on a defined cadence.
- **Validation evidence:** Monitoring job configuration; sample reports; evidence of review cadence.
- **Acceptance criteria:** AC-05

## RP-05 — Tune authentication-activity monitoring and alerting

- **Owner:** Security
- **Priority:** P2
- **Target state:** Alerting on anomalous consecutive-failure patterns (building on the 312-account analysis method), with defined triage thresholds so probing is noticed while it is happening.
- **Validation evidence:** Alert rule definitions; evidence of alerts firing on test patterns; triage runbook.
- **Acceptance criteria:** AC-05

## RP-06 — Close the C-03 evidence gap: validate account lockout

- **Owner:** IAM Team
- **Priority:** P2
- **Target state:** The configured lockout threshold is documented and lockout event evidence confirms it engages as designed.
- **Validation evidence:** Threshold configuration record; sample of lockout events correlated to consecutive-failure sequences.
- **Acceptance criteria:** AC-06

## RP-07 — Independent validation of remediation

- **Owner:** GRC (independent of the remediation executors)
- **Priority:** P1 (before finding closure)
- **Target state:** An independent party re-performs the key tests — population reconciliation completeness, MFA enforcement on the remediated population, and process-fix effectiveness — and concludes on each acceptance criterion.
- **Validation evidence:** Independent validation workpaper with procedures, evidence references, and per-criterion conclusion.
- **Acceptance criteria:** AC-04

## RP-08 — Retain remediation evidence

- **Owner:** GRC
- **Priority:** P3
- **Target state:** All remediation evidence (reconciliation reports, configuration extracts, validation workpapers, exception approvals) retained per the organization's record-retention requirements and available for future audit or testing.
- **Validation evidence:** Evidence inventory with retention locations and periods.
- **Acceptance criteria:** AC-04 (evidence-retention clause)

## Sequencing

```text
RP-01 (reconcile) → RP-02 (enforce MFA) → RP-03 (fix process)
        ↓
RP-04/RP-05/RP-06 (monitoring + lockout) in parallel
        ↓
RP-07 (independent validation) → RP-08 (retain evidence) → finding closure
```
