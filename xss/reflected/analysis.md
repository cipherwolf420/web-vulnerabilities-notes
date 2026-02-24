## Step 1 – Identify user-controlled input

While testing the application, I looked for places where
user input is sent to the server and immediately reflected back.

I focused on:
- Search parameters
- Filter parameters
- URL query values

I selected a search parameter for further testing.
## Step 2 – Check for reflection

To confirm reflection, I injected a harmless test value:

reflection_test_123

Then I:
- Submitted the request
- Observed the response
- Viewed the page source

Result:
The value appeared in the response without modification.

This confirms the input is reflected by the server.


## Step 3 – Identify reflection context

After confirming that the input is reflected,
I checked **where exactly** the value is placed in the response.

I inspected:
- Page source
- DevTools → Elements tab

Observed rendering:

<div class="search-result">
    USER_INPUT_HERE
</div>

The reflected value is placed directly inside the HTML body.

It is:
- Not inside an HTML attribute
- Not inside a JavaScript string
- Not inside a JSON structure

This confirms the reflection occurs in a **standard HTML body context**.

## Step 4 – Map context to payload strategy

After identifying the reflection context,
the next step is to decide **what kind of payload makes sense**.

The reflection occurs in a standard HTML body context.
This directly affects payload choice.

Context observed:
- HTML body
- No attribute boundaries
- No JavaScript string context

Based on this context:

- HTML tags will be parsed by the browser
- <script> tags are valid in this location
- Event handlers and inline scripts are possible
- No need to break out of quotes or strings

This rules out:
- Attribute-breaking payloads
- JavaScript string escape payloads
- JSON context payloads

At this stage, a simple script-based payload
is sufficient to confirm execution.



## Step 5 – Check for output encoding

I tested special characters to see if encoding is applied.

Test input:
<test>

Result:
- Angle brackets were not escaped
- Browser interpreted them as HTML

This indicates missing output encoding.

## Step 6 – Classify XSS type

At this stage:
- Input is reflected immediately
- Input is not stored server-side
- Execution depends on user interaction (URL visit)

This rules out:
- Stored XSS
- Self-XSS

This confirms the issue as **Reflected XSS**.
