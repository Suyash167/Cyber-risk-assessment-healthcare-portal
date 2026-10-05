# Control Assessment

Each control is assessed for **design effectiveness** (would it work if operated as designed?) and **operating effectiveness** (did it work during the period?). A control exception is a case where the control did not operate as required. An evidence limitation is a gap in what could be tested — not a control failure. Neither is an incident on its own.

---

## C-01 — Multi-factor authentication (MFA)

**Control objective:** Only authenticated customers access portal accounts, at the authentication strength the organization requires.

**Control requirement:** Every active customer account must have the MFA configuration required by the current authentication policy before being granted access.

**Design effectiveness — Effective.** The current authentication policy defines an MFA requirement applicable to customer accounts. The requirement is documented and specific enough to test against.

**Operating effectiveness — Deficient.** Configuration evidence showed **247 active customer accounts** remained associated with the legacy authentication policy and did not have the required MFA configuration. The MFA requirement was therefore not enforced across the full active population.

**Evidence:** Current authentication policy document; account-to-policy association extract showing 247 active accounts on the legacy policy; MFA configuration evidence for those accounts. Classification: PROVED (the accounts, their active status, and the missing MFA configuration).

**Exception:** F-01 — required MFA not enforced on 247 active customer accounts. See [authentication_policy_finding.md](../03_Findings/authentication_policy_finding.md).

**Limitation:** Point-in-time evidence. It establishes the condition during the assessment period, not the full history of when each account fell out of compliance.

**Conclusion:** Design effective; operating effectiveness deficient due to exception F-01.

---

## C-02 — Password policy

**Control objective:** Customer passwords meet defined strength requirements so that password-only authentication resists guessing attacks to the required degree.

**Control requirement:** Passwords must satisfy the documented complexity, length, and history requirements.

**Design effectiveness — Effective.** Documented password requirements exist and are testable against configuration.

**Operating effectiveness — No exception identified in the evidence reviewed.** Configured password settings were compared to the documented requirements; no misconfiguration was identified.

**Evidence:** Password policy document; system configuration evidence for password settings. Classification: SUPPORTED (settings matched requirements at the point of review).

**Exception:** None identified.

**Limitation:** Configuration review is point-in-time and tests settings, not every password actually chosen by customers. It does not prove that no weak password exists in the population — only that the enforcement settings matched policy when reviewed.

**Conclusion:** Design effective; no operating exception identified within the limits of the evidence.

---

## C-03 — Account lockout

**Control objective:** Repeated failed authentication attempts are throttled so that online guessing attacks cannot proceed unchecked.

**Control requirement:** Accounts lock (or equivalent throttling engages) after the defined number of consecutive failed login attempts.

**Design effectiveness — Effective.** A lockout/throttling requirement is defined.

**Operating effectiveness — Inconclusive from available evidence.** Log analysis identified **312 accounts with five or more consecutive failed login attempts** during the period. Whether this represents lockout operating as designed (attempts stopped at the threshold) or lockout failing to engage cannot be determined, because the evidence provided did not include the configured lockout threshold or per-account lockout event records.

**Evidence:** Authentication logs (14,820 failed login attempts); consecutive-failure analysis identifying 312 accounts. Classification: PROVED (the counts); the conclusion about lockout behavior is MISSING EVIDENCE.

**Exception:** None confirmed. The 312-account observation is **not** a control exception on its own — it is an observation requiring follow-up, not proof of lockout failure.

**Limitation:** Without the defined threshold and lockout event records, operating effectiveness cannot be concluded. This is an evidence limitation, not a control deficiency.

**Conclusion:** Design effective; operating effectiveness not established — follow-up testing recommended (obtain threshold setting and lockout event evidence).

---

## C-04 — Legacy authentication-policy migration

**Control objective:** All active customer accounts are transitioned from the legacy authentication policy to the current policy so that current requirements (including MFA) apply uniformly.

**Control requirement:** The migration process moves every active account to the current authentication policy, and any account that cannot be migrated is identified, tracked, and resolved.

**Design effectiveness — Partially effective.** A migration process existed and transitioned the majority of accounts. However, the process design did not include a complete population reconciliation step that would have identified accounts left behind — a design gap, not just an execution slip.

**Operating effectiveness — Deficient.** 247 active accounts remained on the legacy policy. The migration did not achieve its required outcome for these accounts, and the gap was not detected by the process itself.

**Evidence:** Account-to-policy association extract (247 active accounts on legacy policy); migration completion records showing the migration was treated as complete. Classification: PROVED (the remaining population); SUPPORTED (the process lacked a reconciliation control, inferred from the undetected remainder and absence of reconciliation records — stated as inference, not fact).

**Exception:** F-01 (same condition as C-01, viewed through the migration control).

**Limitation:** The exact point at which each account was missed (initial migration wave, later provisioning, reactivation) is not established by the evidence.

**Conclusion:** Design partially effective (missing reconciliation); operating effectiveness deficient.

---

## Summary

| Control | Design | Operating | Exception |
|---|---|---|---|
| C-01 MFA | Effective | Deficient | F-01 (247 accounts) |
| C-02 Password policy | Effective | No exception identified | — |
| C-03 Account lockout | Effective | Not established (evidence limitation) | — |
| C-04 Legacy migration | Partially effective | Deficient | F-01 |

One confirmed control exception (F-01), one evidence limitation requiring follow-up (C-03), no confirmed security incident.
