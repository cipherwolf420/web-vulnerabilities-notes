## Payload Selection and Execution Strategy

Based on prior analysis, the input is reflected directly within the HTML body
without output encoding of angle brackets.

Given this context, arbitrary HTML injection is possible at the reflection
point.

### Injection Constraints

The following observations were made during testing:

- The application does not encode `<` or `>` characters.
- No server-side filtering of basic HTML tags was observed.
- The reflection occurs in a standard HTML body context (not inside an attribute or JavaScript string).

These conditions allow direct insertion of executable HTML elements.

---

### Payload Selection Rationale

Since the reflection occurs in an HTML body context and no encoding is applied,
a `<script>` tag provides the most direct and reliable method of confirming
JavaScript execution.

Selected payload:

```html
<script>alert(1)</script>
```

This payload was chosen because:

- `<script>` is valid in an HTML body context
- It requires no user interaction
- It provides immediate execution confirmation
- It does not rely on event handlers or browser quirks

---

### Execution Confirmation

The injected script executed successfully in the browser, confirming that
the reflection point permits arbitrary JavaScript execution.

This validates the presence of a reflected XSS vulnerability.
