
# Cross-Site Request Forgery (CSRF) – Testing Notes

This folder documents my practical testing approach for identifying
and validating Cross-Site Request Forgery (CSRF) vulnerabilities.

These notes focus on **how CSRF issues are discovered during real testing**,
not just what CSRF is or how payloads look.

The goal is to clearly explain:
- how state-changing requests are identified
- how authentication is handled by the browser
- how CSRF protections are evaluated
- how exploitation is confirmed
- how impact is assessed

---

## What This Covers

- Identifying CSRF-relevant endpoints
- Understanding cookie-based authentication behavior
- Evaluating CSRF protections (tokens, SameSite, Origin/Referer)
- Confirming cross-origin request execution
- Classifying the issue correctly

---

## Testing Methodology (High-Level)

The testing process followed this order:

1. Identify state-changing functionality
2. Analyze authentication mechanism
3. Check for CSRF protections
4. Test cross-origin request behavior
5. Confirm exploitation
6. Assess impact and classification

Each step is documented in detail inside `analysis.md`.

---



