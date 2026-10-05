# Finding F-01 — Required MFA Not Enforced on 247 Active Customer Accounts

**Severity:** High · **Status:** Open · **Date identified:** September 2026

## Condition

247 active customer accounts remained associated with the legacy authentication policy and did not have the multi-factor authentication (MFA) configuration required by the current authentication policy.

## Criteria

The current authentication policy requires MFA for all active customer accounts. The legacy-to-current migration was required to transition every active account to the current policy.

## Cause

The legacy authentication-policy migration did not fully transition affected accounts: 247 active accounts remained on the legacy policy after the migration was treated as complete. The migration process had no population-reconciliation step that would have identified accounts left behind. (See [root cause analysis](../04_Root_Cause/root_cause_analysis.md).)

## Contributing factors

- The legacy authentication policy remained available/assignable after migration, so non-migrated accounts continued to function instead of failing visibly.
- No detective control (reconciliation or compliance reporting) flagged the remaining legacy-policy population.
- The point at which each account missed migration (initial wave, later provisioning, or reactivation) was not tracked, so the gap had no natural owner.

## Consequence / risk

The 247 accounts authenticate at a lower assurance level than policy requires and are exposed to credential-based attack (password guessing, credential stuffing, phishing-derived credential reuse) without the MFA barrier the organization requires. In a healthcare customer portal, compromise of these accounts could expose customer personal information and create regulatory and reputational consequences. See [risk register](../05_Risk_Assessment/risk_register.md) (R-01) and [business impact analysis](../08_Executive_Output/business_impact_analysis.md).

No compromise of any of the 247 accounts is established by the evidence. The risk is **potential**, not observed.

## Evidence

| Element | Evidence | Classification |
|---|---|---|
| 247 active accounts on legacy policy | E-02 account-to-policy extract | PROVED |
| Required MFA not configured on those accounts | E-03 MFA configuration evidence | PROVED |
| Policy requires MFA for these accounts | E-01 current authentication policy | PROVED |
| Migration treated as complete with accounts remaining | E-07 migration records vs. E-02 | SUPPORTED |
| No reconciliation step in migration process | Absence of reconciliation records; gap undetected | SUPPORTED (inference) |
| Any account compromised | — | NOT PROVED (no evidence identified) |

## Recommendation

1. Reconcile the full current portal population against the required authentication policy and identify every account remaining on the legacy policy. (Owner: IAM Team)
2. Enforce required MFA on all identified accounts, or document a formal risk-accepted exception for any account that cannot be migrated. (Owner: IAM Team, Application Engineering)
3. Fix the migration/provisioning process so accounts cannot remain on or revert to the legacy policy without detection. (Owner: Application Engineering)
4. Implement recurring reconciliation/compliance reporting over the account-to-policy population. (Owner: Security / GRC)
5. Perform independent validation that remediation is complete before closing this finding. (Owner: GRC)

Full plan with priorities, target states, and validation evidence: [remediation plan](../07_Remediation/remediation_plan.md).

## Management acceptance criteria

Closure of this finding requires **all** of the following (testable criteria in [acceptance_criteria.md](../07_Remediation/acceptance_criteria.md)):

- AC-01: 100% of active accounts reconciled against the current authentication policy; no active account remains on the legacy policy without documented, approved exception.
- AC-02: 100% of in-scope active accounts have the required MFA configuration enforced and verified.
- AC-03: The migration/provisioning process demonstrably prevents silent legacy-policy assignment (failed migration is identifiable and actionable).
- AC-04: Independent validation confirms remediation completeness, with evidence retained for audit.
