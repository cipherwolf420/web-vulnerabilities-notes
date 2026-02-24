## Step 7 – Confirm JavaScript execution

To confirm exploitability, I tested a minimal payload.

Payload used:

<script>alert(document.domain)</script>

Steps:
- Inject payload into the reflected parameter
- Load the crafted URL in the browser

Result:
- Payload executed successfully
- Execution occurs on page load
## Step 8 – Impact reasoning

Because the payload:
- Is reflected immediately
- Executes in the victim’s browser
- Requires a crafted URL

An attacker can:
- Execute arbitrary JavaScript in victim sessions
- Steal sensitive data accessible via JavaScript
- Perform actions on behalf of the victim
- Deliver phishing links

The requirement for user interaction
reduces severity compared to stored XSS,
but the issue is still exploitable.
## Step 9 – Root cause (simple)

User-controlled input is:
- Sent to the server
- Reflected back in the response
- Rendered inside the HTML body
- Without proper output encoding

This allows executable JavaScript
to run in the victim’s browser.
