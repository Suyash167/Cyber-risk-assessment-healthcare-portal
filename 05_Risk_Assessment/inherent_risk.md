# Inherent Risk Assessment

Inherent risk is assessed **before** considering the effect of the failed controls — i.e., given the threat landscape and the vulnerability as it actually exists. (The MFA control is treated as not operating for the affected population, because it was not.)

## R-01 — Credential-based takeover of legacy-policy accounts

**Threat.** Customer-facing authentication endpoints attract continuous credential-stuffing and password-spraying activity across the industry. In this assessment's evidence, 14,820 failed login attempts were logged in a two-month window, with 312 accounts showing ≥5 consecutive failures. This is consistent with automated probing. Intent behind any single attempt is not established, but the volume establishes that the threat is active against this portal, not theoretical.

**Vulnerability.** 247 active accounts authenticate without the MFA barrier policy requires. Single-factor (password-only) authentication is the vulnerability — it reduces account takeover to a credential-guessing problem.

**Likelihood: High.** Both halves of the equation are observed: a real exposed population and real probing activity.

**Impact: High.** The portal serves healthcare customers. Unauthorized access risks exposure of customer personal information, with downstream regulatory scrutiny and loss of customer trust. Impact is assessed on the data and context, not on any observed breach (none occurred).

**Inherent risk: High.**

## R-02 — Undetected additional accounts outside policy

**Threat / vulnerability.** The 247 accounts were found in the available extract, but the total active population was never reconciled against an authoritative source. The vulnerability is the absence of a detective control, which means the true non-compliant population could be larger.

**Likelihood: Medium.** One undetected gap of significant size was already found; a second undetected gap is plausible but not evidenced.

**Impact: High.** Same exposure as R-01 for any such accounts.

**Inherent risk: High.**

## R-03 — Online guessing against customer accounts

**Threat.** Observed: sustained failed-login activity including concentrated consecutive failures against 312 accounts.

**Vulnerability.** Lockout/throttling operating effectiveness could not be confirmed (C-03). Password policy settings were confirmed (C-02), which partially mitigates guessing success.

**Likelihood: Medium.** Probing is observed, but successful guessing must also defeat the enforced password policy, and the MFA gap is confined to the R-01 population.

**Impact: High.** Account takeover exposes the same customer data.

**Inherent risk: High.**

## Cross-cutting note

All three risks share the same impact driver (healthcare customer data) and the same threat actor class (external credential attackers). Treatments therefore overlap: closing the MFA gap and instituting reconciliation reduces R-01 and R-02 together, and MFA plus confirmed lockout reduces R-03 to Low likelihood.
