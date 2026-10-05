# Remediation Acceptance Criteria — Finding F-01

These criteria are written to be **testable**: each one can be answered yes or no from evidence. Finding F-01 closes only when all applicable criteria are met and independently validated.

## AC-01 — Population fully reconciled

100% of active customer accounts are reconciled against the current authentication policy. No active account remains associated with the legacy authentication policy unless it is recorded in the exception register with documented approval (owner, rationale, compensating controls, review date).

*Test:* independent re-performance of the reconciliation from the authoritative account source; every account dispositioned.

## AC-02 — MFA enforced on the full in-scope population

100% of active accounts subject to the MFA requirement have the required MFA configuration enforced, verified by post-remediation configuration evidence — not by process completion reports alone.

*Test:* configuration extract reviewed against the reconciled population; zero in-scope accounts without enforced MFA.

## AC-03 — Migration failures are identifiable and actionable

The migration/provisioning process demonstrably detects and flags accounts that fail to transition: failures generate an identifiable record (log entry, queue item, or alert) that routes to an owner for resolution.

*Test:* controlled test of a failed transition produces the expected detection record; process documentation describes the handling path.

## AC-04 — Independent validation confirms completeness

An independent party (GRC, separate from remediation executors) has re-performed the key procedures, concluded on AC-01 through AC-03 (and AC-05/AC-06 where applicable), and retained the validation workpaper and all supporting evidence for future audit.

*Test:* validation workpaper exists with per-criterion conclusions and evidence references.

## AC-05 — Ongoing monitoring in place

Recurring compliance reporting over account-to-policy association and MFA coverage is operational with a defined review cadence, and alerting on anomalous consecutive-failure patterns is tuned with a triage runbook.

*Test:* monitoring configuration and sample outputs reviewed; review cadence evidenced.

## AC-06 — Lockout effectiveness evidenced

The account-lockout threshold is documented and lockout event evidence confirms throttling engages as designed (closes the C-03 evidence limitation).

*Test:* threshold record plus correlated lockout events reviewed.

## Closure rule

F-01 status moves to **Closed** when AC-01, AC-02, AC-03, and AC-04 are met. AC-05 and AC-06 may close on a tracked timeline after F-01 closure only if leadership documents the deferral as a risk acceptance with a committed date — otherwise they remain open alongside the finding.
