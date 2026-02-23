## Step 7 – Confirm JavaScript execution

To confirm exploitability, I tested a minimal payload.

Example payload:

<script>alert(document.domain)</script>

Steps:
- Inject payload through the identified source
- Allow the JavaScript code to process the input
- Observe browser behavior

Result:
- Payload executed successfully
- No server interaction required
- Execution occurs entirely on the client side

This confirms a DOM-based XSS vulnerability.
## Step 8 – Impact reasoning

Because the issue occurs in client-side JavaScript:

- Attackers can execute arbitrary JavaScript
- Sensitive DOM data can be accessed
- Authenticated actions may be triggered
- UI manipulation and phishing are possible

DOM XSS is often harder to detect
because server-side filters do not apply.
## Step 9 – Root cause (simple)

User-controlled input is:
- Read from a DOM source
- Passed through JavaScript logic
- Written to a dangerous sink
- Without proper sanitization or encoding

This allows JavaScript execution in the browser.
