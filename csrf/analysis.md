# CSRF – Step-by-Step Analysis

This document records the exact reasoning process followed
while testing for CSRF vulnerabilities.

---

## Step 1 – Identify state-changing functionality

While testing the application, I looked for requests that:
- modify user data
- perform sensitive actions
- rely on authenticated sessions

Examples include:
- profile update
- password change
- email update
- role or settings modification

I selected a profile update request for further testing.

---

## Step 2 – Analyze authentication mechanism

I inspected how the application identifies the logged-in user.

Observed behavior:
- Authentication is maintained via cookies
- Cookies are automatically sent by the browser with requests
- No additional user interaction is required

This confirms the application relies on **cookie-based authentication**,
which is a prerequisite for CSRF.

---

## Step 3 – Check for CSRF protections

I analyzed the request for common CSRF defenses:

Checked for:
- CSRF tokens in request parameters
- CSRF tokens in headers
- Origin header validation
- Referer header validation
- SameSite cookie attributes

Observation:
- No CSRF token present in the request
- No Origin or Referer validation enforced
- Authentication cookies are sent cross-site

This indicates missing or ineffective CSRF protection.

---

## Step 4 – Test cross-origin request behavior

To confirm exploitability, I tested whether the request
could be triggered from an external origin.

I created a cross-origin request that:
- targets the same endpoint
- uses the same HTTP method
- relies on the victim’s authenticated session

Result:
- The request was processed successfully
- The action was performed without user interaction

This confirms cross-origin requests are accepted.

---

## Step 5 – Confirm exploitation

I verified the impact by:
- performing the request from an attacker-controlled page
- observing changes in the victim account

Observed result:
- User data was modified successfully
- No CSRF warning or error was triggered

This confirms the vulnerability is exploitable.

---

## Step 6 – Classify CSRF type

At this stage:
- The request is state-changing
- Authentication relies on cookies
- No effective CSRF protection is present
- Exploitation works cross-origin

This confirms the issue as a **valid CSRF vulnerability**.

It is **not**:
- Self-CSRF
- Clickjacking
- User-initiated action abuse
