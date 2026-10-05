# Business Impact Analysis — Healthcare Customer Portal

## Scope of this BIA

This analysis considers the **potential** business impact if the risks identified in this assessment (R-01 through R-03) materialized — i.e., if credential-based attack succeeded against the under-protected accounts. **No impact described here was observed.** No compromise was established, no customer data was confirmed exposed, and no operational disruption occurred. Potential impact and observed impact are kept strictly separate throughout.

## Asset and process context

- **Asset:** Customer authentication and account access for a healthcare customer portal.
- **Data at stake:** Customer account information and whatever personal information the portal exposes post-login. In a healthcare context, customer data carries heightened confidentiality expectations and regulatory attention.
- **Business process:** Customer self-service access — availability and trust in this channel directly affect customer experience.

## Potential impacts (if account takeover occurred)

**Confidentiality exposure.** Unauthorized access to customer accounts could expose personal information belonging to the affected customers. With 247 accounts known to be under-protected — and the true population unconfirmed pending reconciliation — the exposure boundary is uncertain, which itself complicates impact estimation.

**Operational impact.** A confirmed compromise would require forced password/MFA resets, customer notification, account review, and likely temporary service restrictions — diverting engineering, support, and security capacity from planned work.

**Regulatory and compliance implications.** A breach involving healthcare customer data invites regulatory scrutiny (breach notification obligations and sector-specific requirements would need legal determination). The documented MFA gap would complicate any assertion that reasonable safeguards were in place.

**Reputational impact and customer trust.** Customers entrust a healthcare portal with sensitive information. A breach traceable to a known-but-unremediated authentication gap damages trust disproportionately — the narrative would be that the gap was identified and not yet closed.

## Observed impact

**None.** This assessment found a control deficiency and quantified exposure. It did not find, and does not claim, any realized impact.

## Impact-informed priorities

Because impact is High while likelihood is reducible, the remediation sequence prioritizes **likelihood reduction first** (reconcile → enforce MFA → fix process), which is the fastest path to lowering business risk. The BIA supports treating RP-01 through RP-03 as P1: every week the population remains unreconciled, the business carries High-rated inherent risk on an unconfirmed exposure boundary.
