# Reflected Cross-Site Scripting (XSS)

This folder documents my structured approach to identifying and validating
reflected Cross-Site Scripting (XSS) vulnerabilities.

The focus of this write-up is **how the vulnerability was found**, not just the final payload.

---

## 📌 What is Reflected XSS?

Reflected XSS occurs when:
- User-controlled input is sent to the server
- The server reflects that input in the HTTP response
- The input is rendered in the browser **without proper output encoding**
- Malicious JavaScript executes in the victim’s browser

The payload is **not stored** and requires user interaction (e.g., clicking a crafted link).

---

## 🧠 Methodology Followed

Instead of blindly injecting payloads, the following structured approach is used:

1. **Input Discovery**
2. **Reflection Confirmation**
3. **Context Identification**
4. **Context-aware Payload Selection**
5. **Exploitation & Impact Analysis**

Each step is documented separately for clarity and learning purposes.

---

