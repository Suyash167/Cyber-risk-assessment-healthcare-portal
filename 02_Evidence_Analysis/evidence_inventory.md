# Evidence Inventory

| ID | Evidence | Source | Period | Form |
|---|---|---|---|---|
| E-01 | Current authentication policy (MFA, password, lockout requirements) | Policy repository (simulated) | Current at assessment | Document |
| E-02 | Account-to-authentication-policy association extract | Identity/authentication system (simulated) | Aug–Sep 2026 | Data extract |
| E-03 | MFA configuration evidence for legacy-policy accounts | Authentication system (simulated) | Aug–Sep 2026 | Data extract |
| E-04 | Authentication logs (failed login attempts) | Portal authentication logging (simulated) | Aug–Sep 2026 | Log data |
| E-05 | Consecutive-failed-login analysis (312 accounts ≥5 consecutive failures) | Analyst working paper derived from E-04 | Aug–Sep 2026 | Analysis output |
| E-06 | Password policy configuration settings | System configuration (simulated) | Point-in-time (Sep 2026) | Configuration evidence |
| E-07 | Legacy migration completion records | Migration run records (simulated) | Migration window | Document |
| E-08 | Account status data (active vs. inactive) | Identity/authentication system (simulated) | Aug–Sep 2026 | Data extract |

## Evidence not available

| Missing | Why it matters |
|---|---|
| Configured account-lockout threshold and per-account lockout event records | Operating effectiveness of C-03 cannot be concluded (see control assessment) |
| Confirmed total active portal account population | Affected accounts can only be reported as a count, not a rate |
| Per-account timeline of when each of the 247 accounts missed migration | Root-cause timing (initial wave vs. later provisioning) not established |
| Evidence of actual unauthorized access or compromise | No compromise conclusion can be drawn in either direction |
