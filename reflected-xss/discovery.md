Step 1: Identify input points

URL parameters

Search boxes

Filters

Headers (User-Agent, Referer)

Example:

GET /search?q=test

Step 2: Reflection test (NO payload)

q=reflectiontest123

Check response:

HTML source view

DevTools → Network → Response

❓ Question:

Is my input reflected anywhere in the response?

If NO → XSS NO
If YES → continue
