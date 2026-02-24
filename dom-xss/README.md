# DOM XSS – Testing Notes

This folder documents my step-by-step testing approach for identifying
DOM-based Cross-Site Scripting (XSS).

The focus is on understanding how user-controlled data flows inside
client-side JavaScript and how it reaches dangerous sinks.

These notes are written to clearly explain:
- where the data comes from
- how it is processed in the browser
- why execution becomes possible
🔍 What This Covers

Identifying DOM XSS sources

Tracking data flow in JavaScript

Identifying dangerous sinks

Confirming execution without server-side involvement

Classifying the issue as DOM XSS

🧪 Testing Methodology (High-Level)

The testing process followed this order:

Identify JavaScript-controlled input sources

Observe how the data is used in client-side code

Track the flow from source to sink

Identify missing sanitization or encoding

Confirm JavaScript execution using a minimal payload

Each step is documented clearly in the files below.



README.md
Overview of DOM XSS testing approach.

analysis.md
Step-by-step investigation showing how data flows from source to sink.

proof-of-concept.md
Confirms JavaScript execution and explains impact.


This issue occurs entirely on the client side.

No server-side reflection or storage is involved.

Payload execution depends on JavaScript logic in the browser.
