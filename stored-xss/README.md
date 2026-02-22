

# Stored Cross-Site Scripting (XSS)

## Summary

A stored Cross-Site Scripting (XSS) vulnerability was identified in a user-controlled
input field that persists data server-side and renders it without sufficient
output encoding.

The issue allows arbitrary JavaScript execution in the context of other users
viewing the affected content.

---

## Vulnerability Details

During testing, it was observed that user-supplied input submitted through
the comment functionality is stored in the backend database and rendered
whenever the associated page is viewed.

No contextual output encoding was applied at render time.

Example rendering:

```html
<div class="comment">
    USER_INPUT_HERE
</div>

The application does not sanitize or encode angle brackets,
allowing injection of executable HTML elements.

Proof of Concept

The following payload was submitted via the comment field:

<script>alert(document.domain)</script>

Upon viewing the page from a separate authenticated account,
the script executed automatically without additional interaction.

This confirms that the issue is not self-XSS and impacts other users.

Impact

Successful exploitation allows:

Execution of arbitrary JavaScript in victim sessions

Session token theft (if cookies are accessible)

Account takeover via authenticated request execution

CSRF chaining

Phishing or UI manipulation

Because the payload persists and executes for all viewers,
the severity is higher than reflected XSS.

Root Cause

The application stores user-controlled input and renders it in
an HTML body context without applying proper output encoding.

## Folder Structure

```text
stored-xss/
├── README.md
├── discovery.md
├── context-analysis.md
└── exploitation.md
