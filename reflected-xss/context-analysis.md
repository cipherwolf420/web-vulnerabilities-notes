## Context Analysis

The reflected input was identified in the server-generated HTML response.

Example response fragment:
<p>You searched for reflectiontest123</p> ```

The input is rendered directly inside the HTML body, without attribute boundaries
or JavaScript string encapsulation.

This confirms an HTML body context.

No output encoding was observed for angle brackets, indicating that HTML injection
is possible at this location.
