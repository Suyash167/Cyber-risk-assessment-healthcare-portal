# Project Scope

## Engagement context

Simulated cyber risk assessment conducted as an academic case study through Northeastern University, August 2026 – September 2026. The subject is a fictional healthcare customer portal — a web application through which customers access account and service information.

## In scope

| Area | Boundary |
|---|---|
| MFA enforcement | Whether active customer accounts carry the MFA configuration required by the current authentication policy |
| Password policy | Documented requirements and configured settings for customer passwords |
| Account lockout | Whether lockout behavior operates as defined after repeated failed logins |
| Authentication activity | Failed-login and authentication event logs for the assessment period |
| Legacy policy migration | Whether the migration from the legacy authentication policy to the current policy fully transitioned affected accounts |

## Out of scope

- Network architecture and segmentation
- Application code vulnerabilities (no code review or penetration testing)
- Third-party and vendor controls
- Physical security controls
- Incident response process maturity
- Employee/administrator access (assessment covers customer accounts)

## Constraints and limitations

- All evidence is simulated for the case study; conclusions demonstrate method, not an opinion on any real system.
- Evidence is point-in-time (August – September 2026) unless a source states otherwise.
- The total active portal account population was not confirmed in the available evidence; affected-account counts are reported as counts, not rates. See [sampling_analysis.md](../02_Evidence_Analysis/sampling_analysis.md).
- Assessment procedures were limited to document review, configuration evidence review, and log analysis. No interviews, walkthroughs, or re-performance beyond the evidence listed in the inventory were conducted.
