# Reflected Cross-Site Scripting (XSS)

This folder contains my step-by-step testing notes for identifying and
confirming a **Reflected Cross-Site Scripting (XSS)** vulnerability.

The goal of this write-up is to clearly document **how a tester approaches
reflected XSS**, starting from input discovery to final classification.

The steps are written in a logical order so that the testing flow
can be easily understood, repeated, and reviewed later.
🔍 What This Covers

This write-up focuses on answering the following questions:

How to identify user-controlled input

How to confirm server-side reflection

How to identify the reflection context

How context influences payload selection

How to verify missing output encoding

How to correctly classify the issue as reflected XSS

🧪 Testing Flow (High-Level)

The reflected XSS testing process followed this sequence:

Identify user-controlled input

Confirm reflection in the server response

Identify the reflection context

Check for output encoding

Map context to payload strategy

Confirm exploitability

Classify the XSS type

Analyze impact and root cause

Each step is documented clearly in the analysis file.




### File Details

- **README.md**  
  Overview of the reflected XSS testing approach and methodology.

- **analysis.md**  
 Contains the complete testing flow with step-by-step reasoning,
including context identification and payload decision logic.

- **proof-of-concept.md**  
Confirms JavaScript execution and explains exploitability and impact.

