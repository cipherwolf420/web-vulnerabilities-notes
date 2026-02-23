```md
## Step 1 – Look for client-side input sources

I started by checking how the application handles input on the client side.

I focused on common DOM XSS sources such as:
- location.search
- location.hash
- document.URL
- document.referrer
- localStorage / sessionStorage

I observed that the application reads data from the URL.
## Step 2 – Identify where the data is used

Next, I searched the JavaScript code to see where this data is used.

I checked:
- Inline scripts
- External JS files
- Event handlers

I found code where user-controlled data is assigned to the DOM.
## Step 3 – Track data flow (source → sink)

I traced how the value flows from the source to its final usage.

Observed flow:

User input → JavaScript variable → DOM update

The value is not validated or sanitized during this process.
## Step 4 – Identify the sink

The user-controlled value is inserted using a dangerous sink such as:

- innerHTML
- document.write
- insertAdjacentHTML
- eval / setTimeout / setInterval

This allows HTML or JavaScript to be interpreted by the browser.
## Step 5 – Confirm missing sanitization

I tested special characters like:
< > " '

The browser interpreted them as executable HTML.

This confirms that no proper client-side sanitization is applied.
## Step 6 – Classify the issue

At this stage:
- Input is not sent to the server
- Execution happens purely in the browser
- JavaScript logic causes the vulnerability

This confirms the issue as DOM-based XSS.
