
Step 1: Context breaking tests

First, harmless characters test :

<
>
"
'

Test result:

< rendered as <

No HTML encoding observed

➡️ HTML injection possible

Step 2: Payload logic for HTML body

HTML body-la:

<script> tag valid

JavaScript execution direct

Payload requirements:

No user interaction

Simple execution proof

Reliable

Selected payload:
<script>alert(1)</script>
WHY this payload?
Reason	Explanation
Context match	HTML body
Execution	Browser executes <script>
Proof	Alert box
Reliability	Works across browsers

No bypass needed yet — basic reflected XSS confirmed
