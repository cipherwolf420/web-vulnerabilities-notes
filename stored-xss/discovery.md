# Stored Cross-Site Scripting (XSS)

## Summary

A stored Cross-Site Scripting (XSS) vulnerability was identified in a user-controlled
input field that persists data server-side and renders it without sufficient
output encoding.

The issue allows arbitrary JavaScript execution in the context of other users
viewing the affected content.

---

## Vulnerability Details

During testing, it was observed that user-supplied input submitted through
the comment functionality is stored in the backend database and rendered
whenever the associated page is viewed.

No contextual output encoding was applied at render time.

Example rendering:

```html
<div class="comment">
    USER_INPUT_HERE
</div>
