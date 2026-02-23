# Content Security Policy (CSP) Impact Analysis

This section evaluates how Content Security Policy (CSP)
affects the exploitability of identified XSS vulnerabilities.

CSP does not prevent the injection itself,
but may restrict JavaScript execution paths.
Step 1 – Check if CSP is present
## Step 1 – Identify CSP

Checked CSP via:
- Response headers
- DevTools → Network → Response Headers

Result:
Content-Security-Policy header is present.
Step 2 – Review relevant directives
## Step 2 – Analyze CSP directives

Focus was placed on:

- script-src
- default-src
- unsafe-inline
- unsafe-eval
- nonce / hash usage
- strict-dynamic

Goal:
Determine which execution methods are permitted.
Step 3 – Test execution under CSP
## Step 3 – Payload execution test

Tested minimal payload:

<script>alert(document.domain)</script>

Observed behavior:
- Executed / Blocked

If blocked, CSP violation errors were reviewed
in the browser console.
Step 4 – Identify restriction reason
## Step 4 – Reason for blocking

Inline script execution is blocked because:
- 'unsafe-inline' is not allowed
OR
- nonce / hash enforcement is enabled

This indicates CSP is actively restricting execution.
Step 5 – Test alternative execution paths
## Step 5 – Alternate execution vectors

Tested alternate payloads depending on context:

- Event handlers
- SVG-based execution
- Existing script gadget injection
- DOM-based sinks

Objective:
Identify whether CSP fully mitigates or partially restricts XSS.
Step 6 – Final CSP assessment
## Step 6 – CSP effectiveness assessment

One of the following outcomes was determined:

1. Fully exploitable – CSP misconfigured
2. Partially exploitable – Requires bypass or chaining
3. Effectively mitigated – Strong CSP configuration

Regardless of CSP,
the underlying XSS flaw remains valid.
