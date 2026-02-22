
# Proof of Concept

The following payload was submitted through the comment field:

```html
<script>alert(document.domain)</script>

After submission, the page was accessed using a separate authenticated account.

The payload executed automatically upon page load,
confirming that the issue affects users other than the original submitter.

The execution occurs without additional interaction,
establishing a valid stored XSS vulnerability.
