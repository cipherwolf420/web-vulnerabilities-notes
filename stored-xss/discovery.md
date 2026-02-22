# Input Discovery for Stored XSS

This phase focuses on identifying user-controllable input points that are **persisted by the application** and later rendered to other users.

Unlike reflected XSS, the goal at this stage is **not exploitation**, but understanding **where data enters the system and is stored for future use**.

---

## Objective

- Identify input fields whose values are **saved server-side**
- Determine whether the stored data is later **retrieved and rendered**
- Avoid premature payload injection
- Build a clear picture of potential stored XSS entry points

---

## Identified Storage Candidates

During application mapping and interaction testing, the following input vectors were identified as potential storage points:

- Comment or reply fields
- User profile data (username, display name, bio)
- Product or service reviews
- Support tickets or feedback forms
- Messaging or chat inputs
- Admin-facing notes or moderation fields

These inputs share a common characteristic:  
**data is submitted once but displayed multiple times**.

---

## Initial Testing Approach

To safely confirm storage behavior, a **non-malicious unique marker** was used instead of JavaScript payloads.

Example marker:



storedtest_12345


This marker helps verify persistence without triggering execution or filters.

---

## Storage Confirmation Technique

1. Submit the marker into the identified input field
2. Navigate away from the submission page
3. Reload or access a different page where the input may appear
4. Inspect:
   - Page source
   - Rendered HTML
   - Different user roles or sessions (if applicable)

The goal is to answer one key question:

> **Is the input stored and rendered later by the application?**

---

## Key Observation Criteria

An input is considered a valid stored XSS candidate if:

- The value is saved server-side
- The value appears in future responses
- The rendering occurs without strict output encoding
- The value is visible to other users or roles

At this stage, **no assumptions are made** about exploitability.

All findings are carried forward to the next phase:  
**storage flow and context analysis**.

---

## Outcome

Multiple input points were confirmed to persist user-supplied data across requests and sessions, making them valid candidates for further stored XSS analysis.

No payload execution was attempted during this phase.
