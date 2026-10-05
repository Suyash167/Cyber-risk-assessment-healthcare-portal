# Evidence Evaluation

Classifications: **PROVED** · **SUPPORTED** · **LIKELY** · **NOT PROVED** · **CONTRADICTED** · **MISSING EVIDENCE**

## Evaluation matrix

| Evidence | What it establishes | Classification | What it does NOT establish (limitation) |
|---|---|---|---|
| E-02 Account-to-policy extract | 247 active customer accounts were associated with the legacy authentication policy | PROVED | Whether the extract captured the entire population — completeness requires reconciliation |
| E-03 MFA configuration evidence | Those 247 accounts did not have the required MFA configuration | PROVED | When each account lost (or never gained) MFA coverage |
| E-04 Authentication logs | 14,820 failed login attempts occurred in the assessment period | PROVED | Malicious intent behind any specific attempt; whether attempts were human or automated |
| E-05 Consecutive-failure analysis | 312 accounts experienced ≥5 consecutive failed logins | PROVED | That lockout failed (threshold unknown); that any account was compromised |
| E-01 + E-06 Policy vs. configuration | Configured password settings matched documented requirements at review | SUPPORTED | That no weak customer password exists; point-in-time only |
| E-07 Migration records | A migration was executed and treated as complete | SUPPORTED | That all accounts were migrated (contradicted by E-02 for 247 accounts) |
| Compromise indicators | No evidence of confirmed account compromise was identified | NOT PROVED (no evidence identified) | That compromise did not occur — absence of evidence is not evidence of absence |
| Lockout operating effectiveness | — | MISSING EVIDENCE | Threshold and lockout event records were not available |

## Evidence vs. inference — worked examples

1. **Evidence:** 14,820 failed login attempts (E-04). **Established:** a high volume of failed authentication activity occurred during the period (PROVED). **Inference:** the volume and patterns are consistent with automated probing or guessing activity (LIKELY — but benign causes such as forgotten passwords and misconfigured clients also produce failed logins, so attack activity is not established). **Not established:** that any specific attempt was malicious or that any account was breached.
2. **Evidence:** 247 accounts on the legacy policy without MFA (E-02, E-03). **Inference:** these accounts were exposed to credential-based attack at lower assurance than policy requires (SUPPORTED — follows directly from the control requirement). **Not established:** that any of the 247 accounts was actually attacked or compromised.
3. **Evidence:** 312 accounts with ≥5 consecutive failures (E-05). **Inference:** none drawn about lockout effectiveness — the threshold is unknown, so concluding either "lockout worked" or "lockout failed" would be inventing a conclusion. Recorded as MISSING EVIDENCE with follow-up recommended.

## Rules applied

- A count is not a rate: without a confirmed total population, findings are reported as counts.
- Failed authentication is not compromise: no incident is declared on the basis of failed logins.
- An undetected condition is not proof of a missing control: the migration gap is evidenced by the 247 remaining accounts and the absence of reconciliation records, stated as supported inference.
