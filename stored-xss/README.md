
# Stored Cross-Site Scripting (XSS)

This folder documents a structured methodology for identifying, analyzing,
and validating **Stored Cross-Site Scripting (XSS)** vulnerabilities.

Unlike reflected XSS, stored XSS involves user-controlled input that is
**persisted by the application** and later rendered to other users,
making it more impactful and often higher severity.

The focus of this write-up is on **understanding data flow, rendering context,
and execution risk**, rather than simply demonstrating payload execution.

---

## What is Stored XSS?

Stored XSS occurs when:

- User-supplied input is accepted and saved by the application
- The stored data is later retrieved and rendered in an HTML response
- Output encoding is insufficient at render time
- Malicious JavaScript executes in the browser of one or more users

Because execution happens when stored content is viewed,
the attack can affect **multiple users without additional interaction**.

---

## Methodology Followed

The analysis follows a step-by-step approach designed to mirror
real-world application testing and penetration testing workflows:

1. **Input Discovery**  
   Identify user-controllable inputs that are persisted server-side.

2. **Rendering Context Analysis**  
   Determine how and where stored data is embedded in HTML responses.

3. **Exploitability Validation**  
   Confirm whether stored input can lead to JavaScript execution.

4. **Impact Assessment**  
   Evaluate realistic security implications based on victim scope and context.

Each phase is documented separately to clearly demonstrate
the reasoning process behind exploitability decisions.

---

## Folder Structure

```text
stored-xss/
├── README.md
├── discovery.md
├── context-analysis.md
└── exploitation.md
