# XSS Research Notes

This repository contains my practical testing notes for identifying,
analyzing, and validating different types of Cross-Site Scripting (XSS)
vulnerabilities.

These notes are written from a **tester / hunter perspective** and focus on
how issues are discovered and reasoned about during real testing,
rather than just showing payloads or definitions.

---

## What This Repository Covers

The repository documents testing approaches for:

- Reflected Cross-Site Scripting (XSS)
- Stored Cross-Site Scripting (XSS)
- DOM-based Cross-Site Scripting (XSS)
- Content Security Policy (CSP) impact on XSS exploitability

Each topic is organized into its own folder for clarity.

---

## How These Notes Are Written

The notes follow a clear, step-by-step testing flow that reflects
how a security tester approaches XSS in real-world applications.

Typical flow followed across folders:

1. Identify user-controlled input
2. Confirm reflection, storage, or client-side usage
3. Identify the execution context
4. Check for missing output encoding or sanitization
5. Map context to payload strategy
6. Confirm JavaScript execution
7. Classify the XSS type
8. Analyze impact and root cause
9. Review CSP as a mitigation layer (when applicable)

The goal is to make the **testing logic and decision-making process clear**.

---

## Repository Structure


xss-research-notes/
├── reflected-xss/ # Reflected XSS testing notes
├── stored-xss/ # Stored XSS testing notes
├── dom-xss/ # DOM-based XSS testing notes
└── csp-analysis.md # Common CSP impact analysis for XSS


---

## Folder Overview

### reflected-xss/
Contains step-by-step notes for identifying and validating
reflected XSS issues, including context identification and
payload reasoning.

### stored-xss/
Documents how stored input is identified, how persistence is confirmed,
and how multi-user impact is validated.

### dom-xss/
Focuses on client-side data flow analysis, including
source → sink tracking and DOM-based execution logic.

### csp-analysis.md
Analyzes how Content Security Policy affects XSS execution.
CSP is treated as a mitigation layer and not as a replacement
for proper input handling and output encoding.

---

