## Step 1 – Find input that gets stored

While browsing the application, I looked for places where user input
is saved and shown later.

I focused on:
- Comment sections
- Message fields
- Profile fields

I tested the comment feature because:
- Input is accepted from users
- Content is visible after submission
- Content appears again after page reload

This suggests server-side storage.
## Step 2 – Check if input persists

I submitted a simple test value:

stored_test_123

Then I:
- Reloaded the page
- Logged in using a different account
- Viewed the same page again

Result:
- The value was still visible
- The value was shown to other users

This confirms the input is stored server-side
and not reflected only once.
## Step 3 – Check where the value is rendered

Next, I inspected how the stored value is rendered in the HTML.

I checked:
- Page source
- DevTools → Elements tab

Observed rendering:

<div class="comment">
    USER_INPUT_HERE
</div>

The input is placed directly inside the HTML body.
## Step 4 – Check for output encoding

I tested whether special characters are escaped.

I submitted:
<test>

Result:
- Angle brackets were not escaped
- Browser interpreted them as HTML

This confirms:
- No output encoding
- HTML injection is possible
## Step 5 – Determine XSS type

At this point:
- Input is stored server-side
- Input is rendered for other users
- Input is placed in HTML body
- No output encoding is applied

This rules out:
- Self-XSS
- Reflected XSS

This strongly indicates stored XSS.
