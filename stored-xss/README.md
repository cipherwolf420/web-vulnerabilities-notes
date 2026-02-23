# Stored Cross-Site Scripting (XSS)

This folder documents my practical testing approach for identifying and
confirming a **Stored Cross-Site Scripting (XSS)** vulnerability.

The goal of this write-up is not just to show a payload,
but to clearly explain **how a tester reaches the conclusion**
that an issue is a stored XSS.

The steps are written in a simple and logical flow so that
anyone reading can understand the reasoning behind each decision.
🔍 What This Write-up Covers

This write-up focuses on answering the following questions:

How to identify input that is stored server-side

How to confirm that stored input affects other users

How to analyze the rendering context

How to verify JavaScript execution

Why the issue is classified as stored XSS and not reflected or self-XSS

🧪 Testing Methodology (High-Level)

The testing process followed this order:

Identify user-controlled input that persists

Confirm that the input is visible across sessions or users

Inspect where and how the input is rendered in HTML

Check for missing output encoding

Confirm JavaScript execution using a minimal payload

Analyze impact and root cause

Each step is documented separately for clarity.

📂 File Structure Explained
stored-xss/
├── README.md            # Overview and testing approach
├── analysis.md          # Step-by-step investigation and reasoning
└── proof-of-concept.md  # Payload execution and impact confirmation


analysis.md
Contains the detailed testing steps and observations made during analysis.

proof-of-concept.md
Demonstrates JavaScript execution and explains why the issue is exploitable.
