# Sampling Analysis

## Population definition

The relevant population for the MFA finding is **all active customer accounts** on the portal during August – September 2026. The relevant population for the log analysis is **all authentication events** in the same period.

## What was tested

| Test | Population or sample | Result |
|---|---|---|
| Account-to-policy association review | Full available extract of account-to-policy associations (treated as the population for this test) | 247 active accounts on legacy policy |
| Failed-login log review | Full available log set for the period (14,820 failed attempts treated as the population) | 312 accounts with ≥5 consecutive failures |
| Migrated vs. non-migrated comparison | Accounts grouped by policy association (current vs. legacy) | Non-migrated (legacy) accounts lacked required MFA; no equivalent gap identified in the migrated group within the evidence reviewed |

## What the testing proves — and what it does not

- The **247-account count is proved** for the extract reviewed. It is not extrapolated — no sampling projection was needed because the full available extract was analyzed.
- **No rate is reported** (e.g., "x% of accounts") because the total active portal population was not confirmed in the available evidence. Reporting 247 as a percentage would require a denominator the evidence does not supply.
- The log analysis covered the **available** log set. If logging was incomplete (dropped events, unlogged endpoints), the 14,820 figure understates activity. Completeness of logging itself was not tested — stated as a limitation, not an assumption.
- The migrated vs. non-migrated comparison supports that the MFA gap is **concentrated in the legacy population**, not randomly distributed. It does not prove the migrated population is fully compliant — that would require the same reconciliation the remediation plan calls for.
- **No conclusion about compromise** is drawn from any population or sample: compromise testing (e.g., review of successful logins from anomalous sources, account activity review) was not in evidence.

## Bottom line

Full-population testing was performed on the evidence available, so no sampling error applies to the reported counts. The limits are on **completeness of the underlying evidence** (unconfirmed total population, untested log completeness), and those limits are stated wherever the counts are used.
