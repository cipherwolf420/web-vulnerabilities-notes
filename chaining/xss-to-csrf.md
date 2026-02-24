# XSS → CSRF Chaining

This document explains how a Cross-Site Scripting (XSS) vulnerability
can be chained with a Cross-Site Request Forgery (CSRF) issue
to perform authenticated actions without user consent.

The focus is on **reasoning and attack flow**, not payload tricks.

---

## Step 1 – Identify existing XSS

During testing, an XSS vulnerability was identified that allows
arbitrary JavaScript execution in the context of an authenticated user.

Important observations:
- JavaScript executes in the victim’s browser
- Execution occurs under the target origin
- Session cookies are automatically accessible to requests

This establishes a strong client-side execution primitive.

---

## Step 2 – Identify CSRF-prone functionality

Separately, a state-changing endpoint was identified that:
- relies on cookie-based authentication
- lacks effective CSRF protection
- performs sensitive user actions

Under normal conditions, exploitation would require
a cross-origin request.

---

## Step 3 – Understand why CSRF protections fail under XSS

CSRF defenses are designed to stop **external origins**.

However, with XSS:
- JavaScript executes on the same origin
- Requests appear fully legitimate
- CSRF tokens (if present) can be read or reused
- SameSite cookie protections are bypassed

This changes the threat model completely.

---

## Step 4 – Execute same-origin forged request

Using the XSS execution context, a forged request is sent
directly to the vulnerable endpoint.

Characteristics:
- Same origin as the application
- Authentication cookies included automatically
- No cross-origin restrictions apply

The request succeeds without user awareness.

---

## Step 5 – Confirm impact

Observed results:
- Sensitive action completed successfully
- No user interaction required
- No security warning triggered

This confirms successful chaining.

---

## Step 6 – Impact escalation

By chaining XSS with CSRF, the attacker gains:

- Forced state changes
- Account takeover paths
- Privilege abuse
- Full user action impersonation

Issues that were previously medium severity
now combine into a high-impact attack scenario.

---

## Final Classification

This is not a standalone CSRF or XSS issue.

It is a **vulnerability chain** where:
- XSS provides execution
- CSRF provides action
- Combined impact is significantly higher
