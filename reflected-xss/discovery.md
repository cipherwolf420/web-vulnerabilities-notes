## Input Discovery and Reflection Analysis

The application was tested to identify user-controllable input points that are
processed by the server and reflected in the HTTP response.

The following input vectors were observed during initial analysis:
- URL query parameters
- Search input fields
- Filter parameters
- Request headers such as `User-Agent` and `Referer`

---

### Reflection Confirmation

A non-malicious, unique marker was injected to determine whether user input is
reflected in the server response.

Example request:

GET /search?q=reflectiontest123


The response was inspected using:
- Page source review
- Browser developer tools (Network → Response)

The injected value was found to be reflected in the server-generated HTML
response.

This confirms that the application reflects user-controlled input without
eliminating or normalizing the supplied value, making it a valid candidate for
further XSS analysis.
