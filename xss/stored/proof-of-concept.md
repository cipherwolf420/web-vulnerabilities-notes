## Step 6 – Confirm JavaScript execution

To confirm exploitability, I tested a minimal payload.

Payload submitted:

<script>alert(document.domain)</script>

Steps:
- Submit payload via comment field
- Log in as a different user
- Visit the affected page

Result:
- Payload executed automatically
- No user interaction required
- Execution happens on page load

This confirms stored XSS.
## Step 7 – Impact reasoning

Because the payload:
- Is stored permanently
- Executes for every viewer

An attacker can:
- Execute JavaScript in victim sessions
- Access sensitive data available via JS
- Perform authenticated actions as victims
- Chain with CSRF or UI manipulation

Stored nature makes this more severe
than reflected XSS.
## Step 8 – Root cause (simple)

User-controlled input is:
- Stored server-side
- Rendered inside HTML body
- Not encoded during output

This allows executable HTML and JavaScript
to run in other users’ browsers.
